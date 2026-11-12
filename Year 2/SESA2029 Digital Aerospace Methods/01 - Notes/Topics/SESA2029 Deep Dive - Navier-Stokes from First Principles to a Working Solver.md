---
title: "SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 28
tags:
  - sesa2029
  - cfd
  - navier-stokes
  - derivation
  - discretisation
  - deep-dive
aliases: ["Navier-Stokes deep dive", "NS from first principles", "Build a Navier-Stokes solver"]
date: 2026-09-24
status: lectured
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]", "[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]", "[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
next_topics: ["[[SESA2029 A9 - Finite Volume Method]]", "[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]", "[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
key_concepts: ["[[Navier-Stokes Equations]]", "[[Conservation Form of the Governing Equations]]", "[[Newtonian Fluid and Strain-Rate Tensor]]", "[[Convective Interpolation Schemes]]", "[[Pressure-Velocity Coupling and SIMPLE]]", "[[Von Neumann Stability Analysis]]", "[[Mesh Convergence and Grid Independence]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["CFD lectures L2–L12 (finite differences, stability, governing equations, FVM, SIMPLE, V&V)", "Chorin (1968) Math. Comp. 22", "Harlow & Welch (1965) Phys. Fluids 8", "Ghia, Ghia & Shin (1982) J. Comput. Phys. 48", "Own solver: 01 - Notes/Figures/generate_dam_ns_cavity_figures.py"]
---

# SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver

> [!abstract] Summary
> The Navier–Stokes equations follow from Newton's second law and mass conservation applied to a box of fluid, closed by the Newtonian law for viscous stress. Each term of the momentum equation has a different mathematical character (hyperbolic convection, parabolic diffusion, elliptic pressure), and that character fixes how it is discretised. A projection solver on a staggered (MAC) grid, a few dozen lines of NumPy at its core, reproduces the 1982 Ghia lid-driven cavity benchmark at $Re = 100$ with an observed order of about 2. Each discretisation choice follows from the mathematical character of the term it treats: diffusion takes central differences, convection needs upwinding or a bounded central scheme, and the pressure is found by projection on a staggered grid. The solver's observed order is 2.0–2.2 on three grids, and at $N = 64$ its centreline velocities differ from the Ghia values by at most $0.004\,U$ in $u$ and $0.009\,U$ in $v$.

The incompressible Navier–Stokes equations fit on two lines, yet they predict the lift on an A320 and the drag on a golf ball, and whether their three-dimensional solutions always stay smooth is one of the Clay Millennium Prize problems. The same equations sit underneath F1 aerodynamic design, wing design loops, weather forecasting and every Fluent run on campus. Engineers use them every day without that proof, by discretising them carefully and checking the discrete answers, and every option in a commercial code's GUI maps onto one of the discretisation choices of §11–18 (listed in §23). This material goes beyond what was lectured and is optional.

---

# Part I: Deriving the equations

## 1. The continuum hypothesis
Air is made of discrete molecules. At sea level the mean free path is $\lambda \approx 68$ nm, and a 1 mm cube holds about $2.5\times10^{16}$ molecules. Averaging over a volume large compared with $\lambda$ but small compared with the flow gives smooth **fields**:

$$
\rho(\mathbf{x},t), \qquad \mathbf{u}(\mathbf{x},t) = (u, v, w), \qquad p(\mathbf{x},t), \qquad T(\mathbf{x},t).
$$

The test is the **Knudsen number** $Kn = \lambda/L$. For $Kn \ll 1$ (a wing, a pipe, a cavity) the continuum model is excellent. For $Kn \gtrsim 0.1$ (re-entry at 100 km, MEMS devices) it breaks down, and kinetic theory is needed instead.

Everything that follows rests on three conservation laws: mass is conserved, momentum changes only through forces (Newton II), and energy is conserved. Beyond these laws, one piece of physics is needed: how a fluid resists being deformed (§5–6).

## 2. Eulerian and Lagrangian views: the material derivative
The **Lagrangian** view rides along with a fluid particle, like a weather balloon; the **Eulerian** view stays fixed and watches the flow go past, like a weather station. CFD grids are fixed in space, so they are Eulerian, while Newton's law applies to particles, so it is Lagrangian. The chain rule links the two descriptions. Let a particle follow $\mathbf{x}(t)$ with $\dot{\mathbf{x}} = \mathbf{u}$, and carry any property $\phi(\mathbf{x},t)$:

$$
\frac{D\phi}{Dt} \equiv \frac{d}{dt}\,\phi\big(\mathbf{x}(t),t\big) = \frac{\partial \phi}{\partial t} + \frac{\partial \phi}{\partial x}\frac{dx}{dt} + \frac{\partial \phi}{\partial y}\frac{dy}{dt} + \frac{\partial \phi}{\partial z}\frac{dz}{dt}
= \underbrace{\frac{\partial \phi}{\partial t}}_{\text{local change}} + \underbrace{(\mathbf{u}\cdot\nabla)\phi}_{\text{convective change}} .
$$

> [!tip] Convective change without unsteadiness
> A car driven out of a warm city into cold countryside, on a day when the temperature is not changing anywhere ($\partial T/\partial t = 0$), still sees its thermometer fall, because the car **carries it** through a temperature gradient. That is $(\mathbf{u}\cdot\nabla)T$.
>
> The same idea applied to velocity, $(\mathbf{u}\cdot\nabla)\mathbf{u}$, means a fluid particle can accelerate in a perfectly *steady* flow by moving into a region where the velocity is different, e.g. through a nozzle. This nonlinear term is the source of most of the difficulty in fluid dynamics (§8, §10).

## 3. The Reynolds transport and divergence theorems
**Reynolds transport theorem** (RTT). For a *material* volume $V(t)$ whose surface $S$ moves with the flow:

$$
\frac{d}{dt}\int_{V(t)} \phi \, dV = \int_{V} \frac{\partial \phi}{\partial t}\, dV + \oint_{S} \phi\, (\mathbf{u}\cdot\mathbf{n})\, dS .
$$

In words: the total rate of change equals the change inside plus the amount the moving boundary sweeps up.

**Gauss divergence theorem**. A net flux out of a closed surface equals the total "source strength" inside:

$$
\oint_S \mathbf{F}\cdot\mathbf{n}\, dS = \int_V \nabla\cdot\mathbf{F}\, dV .
$$

**Localisation**. If $\int_V f\,dV = 0$ for *every* volume $V$, then $f = 0$ at every point (for continuous $f$). This turns integral laws, which are true for every box, into PDEs, which are true at every point.

## 4. Conservation of mass and the continuity equation
The mass in a material volume never changes:

$$
\frac{d}{dt}\int_V \rho\, dV = 0 \;\overset{\text{RTT}}{\Longrightarrow}\; \int_V \frac{\partial \rho}{\partial t}\,dV + \oint_S \rho\,\mathbf{u}\cdot\mathbf{n}\,dS = 0 \;\overset{\text{Gauss}}{\Longrightarrow}\; \int_V \left[\frac{\partial \rho}{\partial t} + \nabla\cdot(\rho\mathbf{u})\right] dV = 0 .
$$

Localise:

$$
\boxed{\;\frac{\partial \rho}{\partial t} + \nabla\cdot(\rho\,\mathbf{u}) = 0\;}
$$

The same result follows from a fixed box, the form usually expected in exams and the one a finite-volume code uses. For a 2D box of size $\delta x\times\delta y$:
- $\rho u\,\delta y$ flows in on the left;
- $\big(\rho u + \tfrac{\partial(\rho u)}{\partial x}\delta x\big)\delta y$ flows out on the right, a first-order Taylor expansion;
- the same happens top and bottom.

Net outflow $= \big[\partial(\rho u)/\partial x + \partial(\rho v)/\partial y\big]\delta x\,\delta y$. This must equal the rate of loss of the mass $\rho\,\delta x\,\delta y$ inside. Dividing by $\delta x\,\delta y$ gives the same equation.

![[dam_ns_control_volume.png|620]]

Expand the divergence, $\nabla\cdot(\rho\mathbf{u}) = \mathbf{u}\cdot\nabla\rho + \rho\nabla\cdot\mathbf{u}$, and continuity becomes

$$
\frac{D\rho}{Dt} + \rho\,\nabla\cdot\mathbf{u} = 0 .
$$

So **$\nabla\cdot\mathbf{u}$ is the fractional rate at which a fluid parcel's volume grows**. If the density of every parcel stays constant (liquids, or gases at Mach $\lesssim 0.3$), then $D\rho/Dt = 0$ and

$$
\boxed{\;\nabla\cdot\mathbf{u} = 0\;} \qquad \text{(incompressible: parcels change shape, never volume)}
$$

This equation has no time derivative and no pressure. It is not an evolution equation but a **constraint** the velocity must obey at every instant, and enforcing it is the hardest part of the solver (§15).

## 5. Newton's second law for a fluid element: the Cauchy momentum equation
Rate of change of momentum = surface forces + body forces:

$$
\frac{d}{dt}\int_V \rho\,\mathbf{u}\, dV = \oint_S \mathbf{t}\, dS + \int_V \rho\,\mathbf{g}\, dV .
$$

The surface force per unit area is the **traction** $\mathbf{t}$. Cauchy's tetrahedron argument (shrink a tetrahedron to a point; surface forces scale as $\ell^2$ and body forces and inertia as $\ell^3$, so the surface forces must balance on their own) shows that $\mathbf{t}$ depends *linearly* on the surface normal:

$$
\mathbf{t} = \boldsymbol{\sigma}\cdot\mathbf{n}, \qquad \sigma_{ij} = \text{force in direction } j \text{ on a face whose normal points in direction } i .
$$

Applying RTT and Gauss and localising gives

$$
\frac{\partial(\rho\mathbf{u})}{\partial t} + \nabla\cdot(\rho\,\mathbf{u}\mathbf{u}) = \nabla\cdot\boldsymbol{\sigma} + \rho\,\mathbf{g} \qquad \text{(conservative form)}
$$

In index notation, the product rule splits the left-hand side as

$$
\frac{\partial(\rho u_i)}{\partial t} + \frac{\partial(\rho u_i u_j)}{\partial x_j}
= u_i\underbrace{\left[\frac{\partial \rho}{\partial t} + \frac{\partial(\rho u_j)}{\partial x_j}\right]}_{=\,0 \text{ by continuity}} + \rho\left[\frac{\partial u_i}{\partial t} + u_j\frac{\partial u_i}{\partial x_j}\right]
$$

Mass conservation removes the whole first bracket, leaving **mass × acceleration = force** per unit volume:

$$
\rho\,\frac{D\mathbf{u}}{Dt} = \nabla\cdot\boldsymbol{\sigma} + \rho\,\mathbf{g} \qquad \text{(Cauchy momentum equation)}
$$

Angular momentum conservation, applied to a small cube, also forces $\sigma_{ij} = \sigma_{ji}$: the stress tensor is **symmetric**. In the box picture, $\sigma_{yx}$ on the top and bottom faces is what makes a layer of fluid drag the layer beneath it.

The Cauchy equation holds for any continuum (water, honey, steel, toothpaste), but it is **not closed**. In 3D there are four equations (continuity plus three momentum) but 1 + 3 + 6 unknowns: $\rho$, $\mathbf{u}$, and the six independent components of the symmetric $\boldsymbol{\sigma}$. Closing it needs a constitutive law, the one piece of physics that says what kind of material this is.

## 6. The Newtonian closure
A fluid at rest carries no shear stress, only an isotropic pressure, so the first move is to split off pressure:

$$
\boldsymbol{\sigma} = -p\,\mathbf{I} + \boldsymbol{\tau},
$$

where $\boldsymbol{\tau}$ is the **viscous stress** and vanishes when the fluid is at rest.

A solid resists *strain*, meaning how far it has been deformed, whereas a fluid resists **strain rate**, meaning how fast it is being deformed. So $\boldsymbol{\tau}$ must depend on the velocity gradient $\nabla\mathbf{u}$, which splits into a symmetric part and an antisymmetric part:

$$
\frac{\partial u_i}{\partial x_j} = \underbrace{\tfrac{1}{2}\left(\frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i}\right)}_{S_{ij}\text{: strain rate (stretch + shear)}} + \underbrace{\tfrac{1}{2}\left(\frac{\partial u_i}{\partial x_j} - \frac{\partial u_j}{\partial x_i}\right)}_{\Omega_{ij}\text{: pure rotation}}
$$

Water in a bucket spun at a steady rate rotates as a rigid body, with no stress between layers. So $\boldsymbol{\Omega}$ cannot produce stress, and $\boldsymbol{\tau}$ depends only on $\mathbf{S}$ ([[Newtonian Fluid and Strain-Rate Tensor]]).

The **Newtonian** assumption makes $\boldsymbol{\tau}$ linear in $\mathbf{S}$ and isotropic (no preferred direction). The most general such tensor has exactly two constants, the **dynamic viscosity** $\mu$ and the second viscosity coefficient $\lambda$:

$$
\boldsymbol{\tau} = 2\mu\,\mathbf{S} + \lambda\,(\nabla\cdot\mathbf{u})\,\mathbf{I}
$$

**Stokes' hypothesis** (1845) fixes $\lambda$ by requiring the mechanical pressure (minus the average normal stress) to equal the thermodynamic pressure $p$. Then $\operatorname{tr}\boldsymbol{\tau} = 0$, which gives $(2\mu + 3\lambda)\nabla\cdot\mathbf{u} = 0$, so $\lambda = -\tfrac{2}{3}\mu$. In words, the bulk viscosity is zero:

$$
\boxed{\;\tau_{ij} = \mu\left(\frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i}\right) - \frac{2}{3}\,\mu\,\frac{\partial u_k}{\partial x_k}\,\delta_{ij}\;}
$$

In 2D, written out:

$$
\tau_{xx} = 2\mu\frac{\partial u}{\partial x} - \frac{2}{3}\mu\left(\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y}\right), \qquad
\tau_{yy} = 2\mu\frac{\partial v}{\partial y} - \frac{2}{3}\mu\left(\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y}\right), \qquad
\tau_{xy} = \tau_{yx} = \mu\left(\frac{\partial u}{\partial y} + \frac{\partial v}{\partial x}\right).
$$

$\tau_{xy} = \mu\,\partial u/\partial y$ in a simple shear flow is Newton's own viscosity law from 1687. The Newtonian model is excellent for air and water. It fails for ketchup, blood and custard, which are non-Newtonian.

## 7. The Navier–Stokes equations assembled
Substitute $\boldsymbol{\sigma} = -p\mathbf{I} + \boldsymbol{\tau}$ into Cauchy to get the **compressible Navier–Stokes equations**:

$$
\rho\left(\frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u}\cdot\nabla)\mathbf{u}\right) = -\nabla p + \nabla\cdot\left[\mu\left(\nabla\mathbf{u} + \nabla\mathbf{u}^{\mathsf T}\right) - \tfrac{2}{3}\mu(\nabla\cdot\mathbf{u})\mathbf{I}\right] + \rho\,\mathbf{g}
$$

The unknowns are $\rho, u, v, w, p, T$, but continuity and momentum supply only 4 equations. Adding the **energy equation** and an **equation of state** ($p = \rho R T$) closes the system; that full set belongs to SESA3029 and SESA6082. Setting $\mu = 0$ gives the **Euler equations** (see [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]).

Most of Part A, and the solver below, uses the incompressible, constant-viscosity special case. With $\nabla\cdot\mathbf{u} = 0$ and constant $\mu$, the viscous term reduces to a Laplacian:

$$
\frac{\partial \tau_{ij}}{\partial x_j} = \mu\frac{\partial}{\partial x_j}\left(\frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i}\right) = \mu\nabla^2 u_i + \mu\frac{\partial}{\partial x_i}\underbrace{\left(\frac{\partial u_j}{\partial x_j}\right)}_{=\,0} = \mu\,\nabla^2 u_i .
$$

The order of differentiation swaps freely, and the divergence vanishes. Dividing by $\rho$ and writing $\nu = \mu/\rho$ for the **kinematic viscosity** gives the **incompressible Navier–Stokes equations**:

$$
\nabla\cdot\mathbf{u} = 0
$$

$$
\underbrace{\frac{\partial \mathbf{u}}{\partial t}}_{\substack{\text{unsteady}\\\text{acceleration}}} + \underbrace{(\mathbf{u}\cdot\nabla)\mathbf{u}}_{\substack{\text{convective}\\\text{acceleration}}} = \underbrace{-\frac{1}{\rho}\nabla p}_{\substack{\text{pressure}\\\text{force}}} + \underbrace{\nu\nabla^2\mathbf{u}}_{\substack{\text{viscous}\\\text{diffusion}}} + \underbrace{\mathbf{g}}_{\substack{\text{body}\\\text{force}}}
$$

In 3D these are four equations for the four unknowns $(u, v, w, p)$, so the system is closed.

---

# Part II: What each term does

## 8. The terms of the momentum equation
In 2D, conservative form (the form a solver uses), with $\mathbf{g}$ absorbed into the pressure:

$$
\frac{\partial u}{\partial t} + \frac{\partial (u^2)}{\partial x} + \frac{\partial (uv)}{\partial y} = -\frac{1}{\rho}\frac{\partial p}{\partial x} + \nu\left(\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2}\right)
$$

$$
\frac{\partial v}{\partial t} + \frac{\partial (uv)}{\partial x} + \frac{\partial (v^2)}{\partial y} = -\frac{1}{\rho}\frac{\partial p}{\partial y} + \nu\left(\frac{\partial^2 v}{\partial x^2} + \frac{\partial^2 v}{\partial y^2}\right)
$$

$$
\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} = 0
$$

(Conservative and non-conservative forms are equal because $\partial(u^2)/\partial x + \partial(uv)/\partial y = u\,\partial u/\partial x + v\,\partial u/\partial y + u\,(\nabla\cdot\mathbf{u})$, and the last bracket is zero.)

| Term | Name | Physical meaning | Mathematical character | What it demands numerically | What goes wrong if you get it wrong |
|---|---|---|---|---|---|
| $\partial\mathbf{u}/\partial t$ | local acceleration | how the velocity at a fixed point changes in time | first order in time; an initial-value problem | a time-marching scheme and a $\Delta t$ | too big a $\Delta t$ gives instability (explicit) or smeared transients (implicit) |
| $(\mathbf{u}\cdot\nabla)\mathbf{u}$ | convection / advection | momentum carried along by the flow itself | **nonlinear**, hyperbolic: information travels with the flow at speed $\mathbf{u}$ | direction-aware (upwind-biased) differencing; CFL limit $u\Delta t/h \lesssim 1$ | numerical diffusion (upwind) or wiggles (central); the source of turbulence |
| $-\nabla p/\rho$ | pressure gradient | fluid pushed from high to low pressure | in incompressible flow, **elliptic**: $p$ adjusts instantly everywhere to keep $\nabla\cdot\mathbf{u} = 0$ | a global Poisson solve every step (the expensive bit) | checkerboard pressure on collocated grids; mass not conserved |
| $\nu\nabla^2\mathbf{u}$ | viscous diffusion | momentum smoothed out by molecular friction | **parabolic**: smooths, dissipates energy, sets boundary-layer thickness | central differencing; Fourier limit $\nu\Delta t/h^2 \le \tfrac14$ in 2D (explicit) | too coarse near walls means wrong skin friction |
| $\mathbf{g}$ | body force | gravity (or rotation, magnetism) | a source term, no derivatives | usually absorbed: $p \to p - \rho\,\mathbf{g}\cdot\mathbf{x}$ | only matters with a free surface or buoyancy |
| $\nabla\cdot\mathbf{u} = 0$ | continuity | no parcel may change volume | a **constraint**: no $\partial/\partial t$, no $p$ | pressure–velocity coupling (projection or SIMPLE) | the solution drifts off the incompressible manifold |

Convection moves momentum, diffusion smears it out and pressure enforces incompressibility. Convection is the only nonlinear term and the only one that can create smaller and smaller scales; diffusion destroys those scales; and in incompressible flow pressure exists purely to enforce the rule that no parcel is compressed.

## 9. Vorticity and pressure equations derived from Navier–Stokes
**The pressure Poisson equation.** Take the divergence of the momentum equation. The time derivative and viscous terms vanish, because $\nabla\cdot\mathbf{u} = 0$, which leaves

$$
\nabla^2 p = -\rho\,\nabla\cdot\big[(\mathbf{u}\cdot\nabla)\mathbf{u}\big] = -\rho\,\frac{\partial u_i}{\partial x_j}\frac{\partial u_j}{\partial x_i} .
$$

Pressure has no evolution equation of its own; it is set **instantaneously by the whole velocity field**, as if sound travelled infinitely fast. That is the physical meaning of incompressibility, and it is why every incompressible solver has a Poisson solve inside it.

**The vorticity equation.** Take the curl of momentum, with $\boldsymbol{\omega} = \nabla\times\mathbf{u}$. Pressure vanishes completely:

$$
\frac{D\boldsymbol{\omega}}{Dt} = \underbrace{(\boldsymbol{\omega}\cdot\nabla)\mathbf{u}}_{\text{vortex stretching}} + \nu\nabla^2\boldsymbol{\omega} .
$$

A stretched vortex tube spins faster, as a figure skater does on pulling in their arms. That drives the turbulent energy cascade to small scales. In 2D the stretching term is **identically zero**, because $\boldsymbol{\omega}$ is perpendicular to the plane of $\mathbf{u}$. As a result 2D turbulence behaves completely differently, and 2D smoothness has been proven while 3D has not.

## 10. Non-dimensional form and the Reynolds number
Scale everything with a length $L$ and velocity $U$: $\mathbf{x}^* = \mathbf{x}/L$, $\mathbf{u}^* = \mathbf{u}/U$, $t^* = tU/L$, $p^* = p/(\rho U^2)$. Momentum then becomes

$$
\frac{\partial \mathbf{u}^*}{\partial t^*} + (\mathbf{u}^*\cdot\nabla^*)\mathbf{u}^* = -\nabla^* p^* + \frac{1}{Re}\nabla^{*2}\mathbf{u}^*, \qquad Re = \frac{UL}{\nu} = \frac{\text{inertia}}{\text{viscous forces}} .
$$

Every incompressible flow with the same geometry and the same $Re$ is **the same flow**. Wind-tunnel models work for this reason, and the cavity solver below needs only one physical input, $Re$.

| Flow | $U$ | $L$ | $Re$ |
|---|---|---|---|
| swimming bacterium | 30 μm/s | 2 μm | $\sim 10^{-4}$ |
| the solver below (lid-driven cavity) | n/a | n/a | $100$ |
| cyclist | 10 m/s | 0.5 m | $\sim 3\times10^{5}$ |
| car on a motorway | 30 m/s | 4 m | $\sim 8\times10^{6}$ |
| A320 wing at cruise (chord ≈ 4 m) | 230 m/s | 4 m | $\sim 2.5\times10^{7}$ |

The two limits behave very differently. As $Re \to 0$ (Stokes flow) the nonlinear term drops out and the equations become linear and *time-reversible*: G. I. Taylor stirred dye into glycerine between two cylinders, then un-stirred it back into a blob. As $Re \to \infty$ the Euler equations might be expected, but viscosity never really disappears. It retreats into a boundary layer of thickness $\delta/L \sim Re^{-1/2}$, and dropping it entirely predicts zero drag ([[D'Alembert's Paradox]]).

> [!danger] Why these equations are genuinely hard
> 1. Nonlinearity: $(\mathbf{u}\cdot\nabla)\mathbf{u}$ transfers energy to ever-smaller eddies until viscosity dissipates them at the Kolmogorov scale, $\eta/L \sim Re^{-3/4}$. Resolving every eddy in 3D takes $N \sim (L/\eta)^3 \sim Re^{9/4}$ grid points, which for the A320 wing is about $10^{16.6}$ points; industry uses RANS for this reason ([[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] · [[DNS, LES and Scale-Resolving Simulation]]).
> 2. Pressure has no equation of its own. It is a Lagrange multiplier that enforces a constraint (§15).
> 3. Mixed type: in one system, hyperbolic convection, parabolic diffusion and elliptic pressure each want different numerical treatment.
> 4. The \$1M Millennium Prize problem: given smooth initial data in 3D, whether a smooth solution exists for all time or the velocity can blow up to infinity in finite time is unknown. In 2D, global smoothness was proven decades ago.

---

# Part III: Discretising each term

A computer cannot differentiate; it can only add, multiply and store numbers. Discretisation therefore **replaces every derivative with arithmetic on grid values**, and the analysis then shows that the arithmetic converges to the calculus as the grid is refined ([[Finite Difference Approximations]] · [[Taylor Table Method]]).

## 11. The grid and the notation
The grid has uniform spacing $h$ in $x$ and $y$ and time step $\Delta t$, with $f_i^n \approx f(ih,\, n\Delta t)$. Every formula below comes from the **Taylor series**

$$
f_{i\pm1} = f_i \pm h f'_i + \frac{h^2}{2}f''_i \pm \frac{h^3}{6}f'''_i + \frac{h^4}{24}f''''_i \pm \dots
$$

Each term is discretised separately, because each has a different mathematical character (§8).

## 12. The time derivative

| Scheme | Formula | Order | Character |
|---|---|---|---|
| forward (explicit) Euler | $\dfrac{u^{n+1} - u^n}{\Delta t} = \mathcal{R}(u^n)$ | $O(\Delta t)$ | cheap, no matrix solve, conditionally stable |
| backward (implicit) Euler | $\dfrac{u^{n+1} - u^n}{\Delta t} = \mathcal{R}(u^{n+1})$ | $O(\Delta t)$ | matrix solve, unconditionally stable, damps transients |
| Crank–Nicolson | $\dfrac{u^{n+1} - u^n}{\Delta t} = \tfrac12\left[\mathcal{R}(u^n) + \mathcal{R}(u^{n+1})\right]$ | $O(\Delta t^2)$ | matrix solve, stable, can ring |
| RK4 | four explicit stages | $O(\Delta t^4)$ | accurate, larger stability region |

Here $\mathcal{R}$ is the spatial "right-hand side": everything except $\partial\mathbf{u}/\partial t$. The Taylor expansion $\frac{u^{n+1}-u^n}{\Delta t} = u_t + \frac{\Delta t}{2}u_{tt} + O(\Delta t^2)$ shows forward Euler's first-order error. See [[Explicit and Implicit Time Integration]] · [[Runge-Kutta Methods]]. The solver below uses forward Euler: it is the simplest option, and for a steady target it just needs to be stable.

## 13. Viscous diffusion
Add the Taylor series for $f_{i+1}$ and $f_{i-1}$. The odd terms cancel:

$$
f_{i+1} + f_{i-1} = 2f_i + h^2 f''_i + \frac{h^4}{12}f''''_i + \dots \;\;\Longrightarrow\;\; \frac{\partial^2 f}{\partial x^2}\bigg|_i = \frac{f_{i+1} - 2f_i + f_{i-1}}{h^2} - \underbrace{\frac{h^2}{12}f''''_i}_{\text{truncation error}} .
$$

This is second-order accurate. In 2D it becomes the **5-point stencil**:

$$
\nabla^2 f\big|_{i,j} \approx \frac{f_{i+1,j} + f_{i-1,j} + f_{i,j+1} + f_{i,j-1} - 4f_{i,j}}{h^2} .
$$

**Stability.** Diffusion is isotropic and smoothing, so **central differencing is always right** for it. With explicit Euler, von Neumann analysis ([[Von Neumann Stability Analysis]]) substitutes $f_i^n = G^n e^{\mathrm{i}kih}$:

$$
G = 1 - 4F\sin^2\!\left(\tfrac{kh}{2}\right), \quad F = \frac{\nu\Delta t}{h^2} \quad\Longrightarrow\quad \lvert G\rvert \le 1 \iff F \le \tfrac12 \;\;\text{(1D)}, \qquad F \le \tfrac14 \;\;\text{(2D)} .
$$

> [!warning] The explicit diffusion trap
> $\Delta t \le h^2/(4\nu)$. Halving the grid spacing **quarters** the allowable time step, so the work in 2D to reach the same time rises 16×, because there are 4× the cells and 4× as many steps. Production codes treat diffusion implicitly for this reason ([[CFL and Fourier Numbers]]).

## 14. Convection and numerical diffusion
The model problem is $f_t + c f_x = 0$ with $c > 0$, whose exact solution slides a shape to the right *without changing it*.

The **central difference** $\;\dfrac{f_{i+1} - f_{i-1}}{2h}$ is second order, symmetric and has no numerical diffusion. With forward Euler, however, its amplification factor is $G = 1 - \mathrm{i}\,C\sin(kh)$, so $\lvert G\rvert^2 = 1 + C^2\sin^2(kh) > 1$ for every mode except $kh = 0$ and $\pi$: the scheme is **unconditionally unstable** for pure convection. It also ignores the direction the information comes from, and produces **wiggles** next to sharp gradients.

The **first-order upwind** difference $\;\dfrac{f_i - f_{i-1}}{h}$ looks *upstream*, where the information comes from. It is stable for $C = c\Delta t/h \le 1$ and never makes wiggles, but it is only first order. Its error is found from the **modified equation**, the PDE the scheme actually solves. Taylor-expanding upwind with forward Euler gives

$$
\frac{f^{n+1}_i - f^n_i}{\Delta t} + c\,\frac{f^n_i - f^n_{i-1}}{h}
= f_t + \frac{\Delta t}{2}f_{tt} + c f_x - \frac{ch}{2}f_{xx} + O(h^2, \Delta t^2) = 0 .
$$

To leading order $f_t = -c f_x$, so $f_{tt} = c^2 f_{xx}$. Substituting,

$$
\boxed{\; f_t + c f_x = \nu_{num}\, f_{xx}, \qquad \nu_{num} = \frac{ch}{2}\,(1 - C)\;}
$$

So the upwind scheme does not solve the advection equation. It solves an advection–*diffusion* equation, with an artificial viscosity $\nu_{num}$. At exactly $C = 1$ the error vanishes, because the scheme then shifts every value one cell per step, which is exact; as $C \to 0$ the extra viscosity is largest.

![[dam_ns_numerical_diffusion.png|680]]

The figure confirms the algebra. A Gaussian advected once around a periodic domain with upwind ($C = 0.5$, 200 cells) lands **exactly** on the analytic solution of the *diffusion* equation with $\nu_{num} = ch(1-C)/2$. The peaks agree to 4 decimal places (0.6245 vs 0.6247).

For Navier–Stokes, the ratio of numerical to physical viscosity is

$$
\frac{\nu_{num}}{\nu} = \frac{Uh}{2\nu}(1 - C) = \frac{Pe_h}{2}(1 - C), \qquad Pe_h = \frac{Uh}{\nu} \;\;\text{(cell Péclet number)} .
$$

On a coarse mesh at high $Re$, $Pe_h$ can be $10^3$ or more, so a first-order simulation at $Re = 10^6$ might effectively be running at $Re \sim 10^3$. Boundary layers get too thick and separation is suppressed, which is why Fluent recommends switching to second order.

Central convection is safe only in a limited range. Discretising steady convection–diffusion, $u\phi_x = \nu\phi_{xx}$, with central differences for both terms and rearranging gives

$$
\phi_i = \tfrac12\left[\left(1 - \tfrac{Pe_h}{2}\right)\phi_{i+1} + \left(1 + \tfrac{Pe_h}{2}\right)\phi_{i-1}\right] .
$$

If $Pe_h > 2$, the coefficient on $\phi_{i+1}$ goes **negative**. A bigger neighbour then makes $\phi_i$ smaller, which is physically absurd and produces wiggles. So central convection is bounded **only if $Pe_h \le 2$**, meaning the physical viscosity is doing the stabilising. Beyond that, upwind-biased higher-order schemes are needed, such as QUICK or second-order upwind, with limiters (TVD/MUSCL) to stop overshoots.

| Scheme | Order | Numerical diffusion | Bounded? | Where it's used |
|---|---|---|---|---|
| 1st-order upwind (UDS) | 1 | large: $\tfrac{ch}{2}(1-C)$ | always | first iterations, robust startup |
| central (CDS) | 2 | none (dispersive instead) | only if $Pe_h \le 2$ | LES/DNS, low-$Re$, **this solver** |
| 2nd-order upwind / QUICK | 2 / 3 | small | nearly (needs a limiter) | default production RANS |
| TVD / MUSCL with limiter | 2 (1 at extrema) | switched on only near jumps | yes | shocks, sharp interfaces |

See [[Convective Interpolation Schemes]] and [[Truncation Error and Order of Accuracy]].

In Navier–Stokes the advection speed is the velocity itself, which makes the convection term nonlinear. Using the conservative form $\partial(u^2)/\partial x + \partial(uv)/\partial y$ means that what leaves one cell enters its neighbour exactly, so fluxes **telescope**. On a staggered grid the central version also conserves kinetic energy discretely, so it can run without upwinding when $Pe_h < 2$.

## 15. Pressure and the incompressibility constraint
Marching momentum forward in time with any scheme from §12–14 does nothing to force the new velocity to satisfy $\nabla\cdot\mathbf{u} = 0$, and continuity has no $\partial/\partial t$ to march. The fix comes from the **Helmholtz–Hodge decomposition**: any smooth vector field can be split uniquely (given boundary conditions) into a divergence-free part and a gradient,

$$
\mathbf{w} = \underbrace{\mathbf{u}}_{\nabla\cdot\mathbf{u}\,=\,0} + \nabla\phi .
$$

Pressure is the gradient part that removes the divergence, so the pressure gradient acts as the projection that throws away the compressible part of the velocity.

**Chorin's projection method** (1968) uses this in three moves per time step.

1. Predict: advance momentum *ignoring* pressure. The intermediate $\mathbf{u}^*$ is **not** divergence-free.

$$
\mathbf{u}^* = \mathbf{u}^n + \Delta t\left[-(\mathbf{u}^n\cdot\nabla)\mathbf{u}^n + \nu\nabla^2\mathbf{u}^n\right]
$$

2. Solve for pressure, choosing it so that $\nabla\cdot\mathbf{u}^{n+1} = 0$ after step 3:

$$
\nabla^2 p^{n+1} = \frac{\rho}{\Delta t}\,\nabla\cdot\mathbf{u}^*
$$

3. Project (correct):

$$
\mathbf{u}^{n+1} = \mathbf{u}^* - \frac{\Delta t}{\rho}\nabla p^{n+1}
$$

Taking the divergence of step 3 confirms it: $\nabla\cdot\mathbf{u}^{n+1} = \nabla\cdot\mathbf{u}^* - \frac{\Delta t}{\rho}\nabla^2 p^{n+1} = \nabla\cdot\mathbf{u}^* - \nabla\cdot\mathbf{u}^* = 0$. ✓

At a wall the normal velocity is already correct in $\mathbf{u}^*$, so the correction must not change it, which gives the pressure boundary condition $\partial p/\partial n = 0$.

> [!warning] Singular pressure matrix
> With pure Neumann conditions, $p$ is only defined **up to a constant**: the Poisson matrix is singular, since the constant vector is in its null space. **Pin one value** ($p = 0$ in one cell) before factorising. This is the same idea as removing rigid-body modes in FEA ([[Boundary Conditions and Rigid Body Modes]]).

Fluent's default family, SIMPLE ([[Pressure-Velocity Coupling and SIMPLE]]), is the *steady, iterative* counterpart of projection.

| | Projection (Chorin) | SIMPLE |
|---|---|---|
| goal | time-accurate transient | steady state (or inner iterations of a transient step) |
| pressure equation | Poisson for $p^{n+1}$ | Poisson-like equation for a *correction* $p'$ |
| relaxation | none needed | under-relax $p$ and $\mathbf{u}$ (e.g. 0.3 / 0.7) |
| converged when | the time loop reaches steady state | the residuals of mass and momentum drop |

## 16. Collocated and staggered grids: the checkerboard problem
The simplest choice is to store $u$, $v$ and $p$ at the **same** points (a collocated grid) and use central differences:

$$
\frac{\partial p}{\partial x}\bigg|_i \approx \frac{p_{i+1} - p_{i-1}}{2h} .
$$

This stencil **never looks at $p_i$**. For a checkerboard pressure $p_{i,j} = (-1)^{i+j}$ the discrete gradient is **zero everywhere**, so the momentum equation cannot feel it. The solution can be contaminated by a wild, oscillating pressure that the discretisation considers perfectly acceptable.

There are two classic cures. The **staggered (MAC) grid** (Harlow & Welch, 1965) stores $p$ at cell centres and each velocity component on the cell *faces* it points through. The pressure gradient that drives $u_{i+\frac12,j}$ is then $\frac{p_{i+1,j} - p_{i,j}}{h}$: compact, over one $h$, with no gap for a checkerboard to hide in. **Rhie–Chow interpolation** (1983) keeps a collocated grid, which is much easier for unstructured meshes, but adds a pressure-smoothing term to the face velocities. Fluent, OpenFOAM and STAR-CCM+ use this approach, and Fluent's PRESTO! pressure option is a staggered-style scheme.

![[dam_ns_mac_grid.png|640]]

## 17. The complete discrete equations on a MAC grid
Grid indices: $p_{i,j}$ at centres, $u_{i+\frac12,j}$ on vertical faces, $v_{i,j+\frac12}$ on horizontal faces.

**u-momentum predictor** at face $(i+\tfrac12, j)$, using explicit Euler, central conservative convection and a 5-point Laplacian:

$$
u^*_{i+\frac12,j} = u^n_{i+\frac12,j} + \Delta t\Bigg[
-\underbrace{\frac{(u^2)_{i+1,j} - (u^2)_{i,j}}{h} - \frac{(uv)_{i+\frac12,j+\frac12} - (uv)_{i+\frac12,j-\frac12}}{h}}_{\text{convection}}
+ \underbrace{\nu\,\frac{u_{i+\frac32,j} + u_{i-\frac12,j} + u_{i+\frac12,j+1} + u_{i+\frac12,j-1} - 4u_{i+\frac12,j}}{h^2}}_{\text{diffusion}}
\Bigg]^n
$$

Values needed where $u$ does not live are **averaged from neighbours**:

$$
u_{i,j} = \tfrac12\big(u_{i+\frac12,j} + u_{i-\frac12,j}\big), \qquad
(uv)_{i+\frac12,j+\frac12} = \tfrac12\big(u_{i+\frac12,j} + u_{i+\frac12,j+1}\big)\cdot\tfrac12\big(v_{i,j+\frac12} + v_{i+1,j+\frac12}\big) .
$$

The **v-momentum** predictor is the mirror image, with the roles of $x \leftrightarrow y$ and $u \leftrightarrow v$ swapped.

**Pressure Poisson** in cell $(i, j)$:

$$
\frac{p_{i+1,j} + p_{i-1,j} + p_{i,j+1} + p_{i,j-1} - 4p_{i,j}}{h^2} = \frac{\rho}{\Delta t}\left[\frac{u^*_{i+\frac12,j} - u^*_{i-\frac12,j}}{h} + \frac{v^*_{i,j+\frac12} - v^*_{i,j-\frac12}}{h}\right]
$$

**Projection** on each face:

$$
u^{n+1}_{i+\frac12,j} = u^*_{i+\frac12,j} - \frac{\Delta t}{\rho}\,\frac{p_{i+1,j} - p_{i,j}}{h}, \qquad
v^{n+1}_{i,j+\frac12} = v^*_{i,j+\frac12} - \frac{\Delta t}{\rho}\,\frac{p_{i,j+1} - p_{i,j}}{h}
$$

> [!tip] Why the staggered projection is exact
> The discrete divergence (face differences over a cell) of the discrete gradient (centre differences across a face) is **exactly** the 5-point Laplacian used in the Poisson equation. The discrete operators fit together like the continuous ones do ($\nabla\cdot\nabla = \nabla^2$).
>
> So after projection, the discrete divergence is zero **to machine precision**, not merely to truncation error. The solver below reports $\max\lvert\nabla\cdot\mathbf{u}\rvert \approx 9\times10^{-14}$.

The MAC scheme is also a finite-volume method. Integrating $\nabla\cdot\mathbf{u} = 0$ over cell $(i, j)$ and applying Gauss gives

$$
\oint \mathbf{u}\cdot\mathbf{n}\, dS = (u_e - u_w)\,h + (v_n - v_s)\,h = 0 .
$$

That is the discrete continuity equation above, multiplied by $h^2$. The same integration of the momentum equation over a control volume shifted by half a cell recovers the u-momentum update, so on a uniform Cartesian grid MAC finite differences and finite volumes are the **same method** ([[Finite Volume Method]] · [[SESA2029 A9 - Finite Volume Method]]).

Boundary conditions are imposed with ghost cells ([[CFD Boundary Conditions]]). The $v$ values live *on* the top and bottom walls, so $v = 0$ is set there directly, and likewise $u = 0$ on the side walls. The $u$ values, however, live half a cell *away from* the lid. To impose $u = U$ at the lid, a ghost value is added above it so that the *average* equals $U$: $\tfrac12(u_g + u_{int}) = U \;\Rightarrow\; u_g = 2U - u_{int}$. At a stationary wall, $u_g = -u_{int}$.

## 18. Stability limits of the explicit solver
Three dimensionless numbers must be kept in check for this explicit, central scheme ([[CFL and Fourier Numbers]]):

| Constraint | Formula | Limit | Why | Solver value ($N = 64$, $Re = 100$, $\Delta t = 0.004$) |
|---|---|---|---|---|
| CFL (convection) | $C = U\Delta t/h$ | $\lesssim 1$ | information may not jump more than a cell per step | 0.256 ✓ |
| diffusion number | $F = \nu\Delta t/h^2$ | $\le \tfrac14$ (2D) | von Neumann, §13 | 0.164 ✓ |
| cell Péclet | $Pe_h = Uh/\nu$ | $\le 2$ | boundedness of central convection, §14 | 1.56 ✓ |

(Everything is non-dimensional with $U = L = \rho = 1$, so $\nu = 1/Re$.)

---

# Part IV: Building, running and checking a solver

## 19. The solver loop
The complete script is `01 - Notes/Figures/generate_dam_ns_cavity_figures.py` (about 180 lines including plotting and the Ghia comparison; runs in about 3 s). Its core is §17 almost symbol for symbol:

```python
for n in range(n_steps):
    # 1. ghost cells: no-slip walls, lid moving at U   (§17 boundary conditions)
    u[:, 0]  = -u[:, 1]                 # bottom wall
    u[:, -1] = 2*U - u[:, -2]           # lid: average of ghost and interior = U
    v[0, :]  = -v[1, :];  v[-1, :] = -v[-2, :]

    # 2. predictor for u on interior x-faces        (§14 convection + §13 diffusion)
    ue = 0.5*(u[2:, 1:-1] + u[1:-1, 1:-1]);  uw = 0.5*(u[1:-1, 1:-1] + u[:-2, 1:-1])
    un = 0.5*(u[1:-1, 1:-1] + u[1:-1, 2:]);  us = 0.5*(u[1:-1, 1:-1] + u[1:-1, :-2])
    vn = 0.5*(v[1:-2, 1:] + v[2:-1, 1:]);    vs = 0.5*(v[1:-2, :-1] + v[2:-1, :-1])
    conv = (ue**2 - uw**2)/h + (un*vn - us*vs)/h
    lap  = (u[2:, 1:-1] + u[:-2, 1:-1] + u[1:-1, 2:] + u[1:-1, :-2] - 4*u[1:-1, 1:-1])/h**2
    u_star[1:-1, 1:-1] = u[1:-1, 1:-1] + dt*(-conv + nu*lap)
    # ... v_star is the mirror image ...

    # 3. pressure Poisson: lap(p) = div(u*)/dt       (§15, sparse LU factorised once)
    div = (u_star[1:, 1:-1] - u_star[:-1, 1:-1])/h + (v_star[1:-1, 1:] - v_star[1:-1, :-1])/h
    p = lu.solve((div/dt).ravel()).reshape(N, N)

    # 4. projection: u = u* - dt grad p              (§15 step 3)
    u[1:-1, 1:-1] = u_star[1:-1, 1:-1] - dt*(p[1:, :] - p[:-1, :])/h
    v[1:-1, 1:-1] = v_star[1:-1, 1:-1] - dt*(p[:, 1:] - p[:, :-1])/h
```

> [!tip] Two tricks that make it fast
> - The Poisson matrix never changes, so it is **LU-factorised once** (`scipy.sparse.linalg.splu`), and every step is just a cheap back-substitution.
> - All loops over cells are replaced by NumPy array slices. `u[2:, 1:-1]` is "the east neighbour of every interior u-face" in one line.

## 20. Result: the lid-driven cavity at Re = 100
A square box of fluid, closed on three sides, has a lid sliding across the top. It is the standard first test case of CFD: simple geometry, no inflow or outflow, and yet genuinely nonlinear physics.

![[dam_ns_cavity_streamlines.png|600]]

The lid drags fluid to the right; it then dives down the right wall, returns along the bottom and rises up the left wall, forming the **primary vortex**. Its centre sits at $(0.609, 0.734)$ with $\psi_{min} = -0.1032$. Ghia et al. report $(0.6172, 0.7344)$ and $-0.1034$, so the centre agrees to within one cell ($h = 0.0156$). It sits **downstream** of centre ($x > 0.5$) because convection carries it; as $Re \to 0$ it would sit dead centre, since Stokes flow is symmetric.

Small counter-rotating **corner eddies** appear in both bottom corners. Moffatt (1964) proved that a sharp corner holds an **infinite sequence** of ever-smaller, ever-weaker eddies nested into it. In a 90° corner each one is about 16.6× smaller than the last, and its velocities are about 2,200× weaker. These ratios come from the Stokes-flow corner eigenvalue equation $\sin(2\alpha z) = -z\sin 2\alpha$ with $2\alpha = 90°$, whose root is $z \approx 2.74 + 1.12\,\mathrm{i}$: the size ratio is $e^{\pi/1.12} \approx 16.6$ and the velocity ratio is $16.6^{2.74} \approx 2{,}200$. The solver resolves the first eddy; the second would need a grid about 16× finer near the corner.

Steady state is reached at $t \approx 26$, and $\max\lvert\nabla\cdot\mathbf{u}\rvert = 9.3\times10^{-14}$, confirming the machine-precision divergence of the staggered projection (§17).

## 21. Verification: the observed order of convergence
Everything in §13–14 was second order, so errors should fall **4×** each time $h$ halves ([[Mesh Convergence and Grid Independence]]). The solver was run on three grids:

| Quantity | $N = 32$ | $N = 64$ | $N = 128$ | observed order $p$ | Richardson extrapolation | Ghia et al. (1982), 129 × 129 |
|---|---|---|---|---|---|---|
| $u_{min}$ on $x = 0.5$ | −0.2089 | −0.2128 | −0.2137 | 2.1 | −0.2140 | −0.2109 |
| $v_{min}$ on $y = 0.5$ | −0.2487 | −0.2527 | −0.2536 | 2.2 | −0.2539 | −0.2453 |
| $v_{max}$ on $y = 0.5$ | 0.1754 | 0.1785 | 0.1793 | 2.0 | 0.1796 | 0.1753 |

The observed order comes from $p = \ln\!\left(\dfrac{f_{32} - f_{64}}{f_{64} - f_{128}}\right)\big/\ln 2$, and the extrapolated value from $f_{\infty} \approx f_{128} + \dfrac{f_{128} - f_{64}}{2^p - 1}$.

> [!check] Observed order matches design order
> For $u_{min}$: $(-0.2089 + 0.2128)/(-0.2128 + 0.2137) = 0.0039/0.0009 = 4.3$, so $p = \ln 4.3/\ln 2 \approx 2.1$. All three quantities give $p \approx 2$, as the Taylor series in §13–14 predicted. This is the strongest evidence a code can give that it is **solving the equations right**; bugs almost always show up as the wrong order, even when the answer looks plausible ([[Verification and Validation]] · [[Residual vs Solution Error]]).

## 22. Validation against the Ghia benchmark

![[dam_ns_cavity_validation.png|760]]

At $N = 64$ the centreline profiles sit on Ghia's points: the largest pointwise differences are $0.004\,U$ in $u$ and $0.009\,U$ in $v$.

The table in §21 also shows that the three grids converge *past* Ghia's values, to extrapolated extremes about 1.5–3.5% larger in magnitude. Neither result is wrong. Ghia's numbers are a numerical solution too, computed on a 129 × 129 grid with their own discretisation error, and they are tabulated at their grid points, so the tabulated minimum is the value at the nearest point rather than the true extremum.

A benchmark is therefore a reference, not the truth, and how it was computed matters. Comparing code against code (Ghia) is really part of **verification**; **validation** means comparing with physical experiment, which brings its own error bars ([[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]). A grid study with an observed order and a Richardson estimate turns "it looks converged" into a quantified statement such as "the discretisation error is about 0.1%".

## 23. Fluent GUI settings and the choices behind them
Every option in a commercial solver is one of the choices made above.

| What you set in the GUI | What it means mathematically | Section |
|---|---|---|
| Transient: first / second order implicit | the time scheme for $\partial\mathbf{u}/\partial t$ | §12 |
| Momentum: first order upwind → second order upwind / QUICK / MUSCL | the convection scheme and its numerical diffusion | §14 |
| (no option: diffusion is always central) | $\nu\nabla^2\mathbf{u}$ is smoothing, so central is always right | §13 |
| Pressure–velocity coupling: SIMPLE / SIMPLEC / PISO / Coupled | how the $\nabla\cdot\mathbf{u} = 0$ constraint is enforced | §15 |
| Pressure interpolation: Standard / Second order / PRESTO! | how face pressures are built on a collocated grid (checkerboard control) | §16 |
| Under-relaxation factors | damping for SIMPLE's iterative pressure correction | §15 |
| Courant number (density-based / coupled) | the pseudo-time CFL number | §18 |
| Residuals < 1e-6 | the discrete equations are satisfied: **not** that the answer is accurate | §21, [[Residual vs Solution Error]] |
| Mesh refinement study | observed order + Richardson (GCI) | §21 |
| Turbulence model (SA, $k$–$\omega$ SST, ...) | a closure for the Reynolds stresses when you cannot afford $Re^{9/4}$ | §10, [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] |

---

## Summary
> [!summary] Main results
> The derivation applies RTT and Gauss to a control volume and localises:
> - mass: $\partial_t\rho + \nabla\cdot(\rho\mathbf{u}) = 0$;
> - momentum: $\rho\,D\mathbf{u}/Dt = \nabla\cdot\boldsymbol{\sigma} + \rho\mathbf{g}$;
> - Newtonian + Stokes: $\boldsymbol{\sigma} = -p\mathbf{I} + \mu(\nabla\mathbf{u} + \nabla\mathbf{u}^{\mathsf T}) - \tfrac23\mu(\nabla\cdot\mathbf{u})\mathbf{I}$;
> - incompressible: $\nabla\cdot\mathbf{u} = 0$, $\;\partial_t\mathbf{u} + (\mathbf{u}\cdot\nabla)\mathbf{u} = -\nabla p/\rho + \nu\nabla^2\mathbf{u}$.
>
> Convection is hyperbolic and nonlinear, diffusion is parabolic, and pressure is elliptic, a constraint enforcer; non-dimensionally only $Re = UL/\nu$ matters. In discrete form:
> - diffusion: central, $F \le \tfrac14$;
> - convection: upwind adds $\nu_{num} = \tfrac{ch}{2}(1-C)$; central is bounded only if $Pe_h \le 2$;
> - pressure: projection $\nabla^2 p = \tfrac{\rho}{\Delta t}\nabla\cdot\mathbf{u}^*$, $\;\mathbf{u} = \mathbf{u}^* - \tfrac{\Delta t}{\rho}\nabla p$;
> - staggered grid: no checkerboard, and divergence zero to machine precision.
>
> The checks, in order, are observed order ≈ design order, Richardson extrapolation, a benchmark (and its own error), then experiment.

## Test yourself
1. Show that for incompressible flow with constant $\mu$, $\nabla\cdot\boldsymbol{\tau} = \mu\nabla^2\mathbf{u}$.
2. Why does the upwind scheme smear a sharp front, and by how much?
3. Why can't a collocated central-difference scheme "see" a checkerboard pressure field?
4. Prove that the projection step makes the new velocity divergence-free.
5. The solver is run on $N = 128$ at $Re = 100$ with $U = L = 1$. What is the largest stable explicit $\Delta t$, and which limit sets it?
6. A student's second-order code shows errors falling by about 2× per grid halving. What does that tell you?

> [!question]- Answers
> **1.** $\partial_j\tau_{ij} = \mu\,\partial_j\partial_j u_i + \mu\,\partial_j\partial_i u_j = \mu\nabla^2 u_i + \mu\,\partial_i(\partial_j u_j) = \mu\nabla^2 u_i$. The $-\tfrac23\mu(\nabla\cdot\mathbf{u})$ term also vanishes.
>
> **2.** Its modified equation is $f_t + cf_x = \nu_{num}f_{xx}$ with $\nu_{num} = \tfrac{ch}{2}(1-C)$. The leading truncation error is a second derivative, which acts like physical diffusion. Refining $h$ or running closer to $C = 1$ reduces it.
>
> **3.** $(p_{i+1} - p_{i-1})/2h$ skips $p_i$. For $p = (-1)^{i+j}$, the values at $i+1$ and $i-1$ are equal, so the discrete gradient is zero everywhere and the momentum equations get no force from it. The fix is a staggered grid (compact gradient) or Rhie–Chow interpolation.
>
> **4.** $\nabla\cdot\mathbf{u}^{n+1} = \nabla\cdot\mathbf{u}^* - \tfrac{\Delta t}{\rho}\nabla^2 p^{n+1}$, and the Poisson equation sets $\nabla^2 p^{n+1} = \tfrac{\rho}{\Delta t}\nabla\cdot\mathbf{u}^*$. So the result is 0. On a MAC grid this holds exactly in the discrete sense too, because discrete div∘grad equals the discrete Laplacian.
>
> **5.** $h = 1/128$ and $\nu = 0.01$. Diffusion requires $\Delta t \le h^2/(4\nu) = 1.53\times10^{-3}$, while CFL requires $\Delta t \le h/U = 7.8\times10^{-3}$, so the diffusion limit sets $\Delta t$. Refining the grid makes the $h^2$ limit dominate, which is the explicit diffusion trap from §13. The cell Péclet number is $Pe_h = Uh/\nu = 0.78 < 2$ ✓.
>
> **6.** The observed order is $p \approx 1$, not 2. Something is first order, usually a boundary condition (e.g. the wall value set at the wrong location instead of by ghost-cell averaging), an upwind term left in, or an inconsistent interpolation. The order test found a bug that the plots would have hidden.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Derivation background: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[Navier-Stokes Equations]] · [[Conservation Form of the Governing Equations]] · [[Newtonian Fluid and Strain-Rate Tensor]]
- Discretisation tools: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] · [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]] · [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]] · [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Solvers and checks: [[SESA2029 A9 - Finite Volume Method]] · [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]] · [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Practice: [[SESA2029 CFD Worked Examples]] · [[SESA2029 Formula Sheet]]

## Sources
- CFD lectures (finite differences and Taylor tables, stability, governing equations, FVM, SIMPLE, errors and V&V): `02 - Sources/CFD/All_lectures_as_delivered.pdf` and transcript `CFD.txt`
- A. J. Chorin (1968), "Numerical solution of the Navier–Stokes equations", *Math. Comp.* 22, 745–762 (projection method)
- F. H. Harlow & J. E. Welch (1965), *Phys. Fluids* 8, 2182–2189 (MAC staggered grid)
- C. M. Rhie & W. L. Chow (1983), *AIAA J.* 21, 1525–1532 (collocated-grid pressure interpolation)
- U. Ghia, K. N. Ghia & C. T. Shin (1982), *J. Comput. Phys.* 48, 387–411 (cavity benchmark, Re = 100 data used here)
- H. K. Moffatt (1964), "Viscous and resistive eddies near a sharp corner", *J. Fluid Mech.* 18, 1–18
- H. K. Versteeg & W. Malalasekera, *An Introduction to Computational Fluid Dynamics: The Finite Volume Method* (2nd ed.); J. D. Anderson, *Computational Fluid Dynamics: The Basics with Applications*
- Clay Mathematics Institute, Millennium Prize problem statement "Existence and smoothness of the Navier–Stokes equation" (C. Fefferman)
- Own solver and figures: `01 - Notes/Figures/generate_dam_ns_cavity_figures.py` and `generate_dam_deep_dive_figures.py` (all numbers above were produced by these)

## Self-study tasks

This note goes beyond the lectured material; none of it was set. The tasks below are suggested, not lecturer-set, and the questions under [[#Test yourself]] have worked answers.

### Core

- [ ] Derive continuity and the incompressible Navier–Stokes equations from a control volume. → [[#4. Conservation of mass and the continuity equation]] · [[#7. The Navier–Stokes equations assembled]]
- [ ] Explain what each term of the momentum equation does and how it is discretised. → [[#8. The terms of the momentum equation]] · [[#13. Viscous diffusion]] · [[#14. Convection and numerical diffusion]]

### Further practice

- [ ] Run the cavity solver, halve the grid spacing and measure the observed order. → [[#21. Verification: the observed order of convergence]]
- [ ] Explain the checkerboard problem and how the staggered grid removes it. → [[#16. Collocated and staggered grids: the checkerboard problem]]
