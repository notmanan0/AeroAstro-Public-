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
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]", "[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]", "[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
next_topics: ["[[SESA2029 A9 - Finite Volume Method]]", "[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]", "[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
key_concepts: ["[[Navier-Stokes Equations]]", "[[Conservation Form of the Governing Equations]]", "[[Newtonian Fluid and Strain-Rate Tensor]]", "[[Convective Interpolation Schemes]]", "[[Pressure-Velocity Coupling and SIMPLE]]", "[[Von Neumann Stability Analysis]]", "[[Mesh Convergence and Grid Independence]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["CFD lectures L2–L12 (finite differences, stability, governing equations, FVM, SIMPLE, V&V)", "Chorin (1968) Math. Comp. 22", "Harlow & Welch (1965) Phys. Fluids 8", "Ghia, Ghia & Shin (1982) J. Comput. Phys. 48", "Own solver: scripts/ns_cavity_solver.py"]
---

# SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver

> [!abstract] The plan
> This note starts from **Newton's second law and a box**. From there it:
> 1. derives the Navier–Stokes equations;
> 2. takes them apart term by term to see what each piece *does*;
> 3. turns every derivative into arithmetic a computer can do;
> 4. builds a working solver (a few dozen lines of NumPy at its core);
> 5. checks it against a benchmark from 1982.
>
> The same equations run in every F1 wind tunnel replacement, every wing design loop, every weather forecast and every Fluent licence on campus. By the end you will know exactly what those codes are doing underneath the GUI.
>
> **Act I** Derive (§1–7) · **Act II** Understand (§8–10) · **Act III** Discretise (§11–18) · **Act IV** Build and check (§19–22)

> [!quote] Why bother?
> Here is a system of partial differential equations you could write on the back of a beer mat.
> - It predicts the lift on an A320, the drag on a golf ball and the swirl in your coffee.
> - It is also the subject of one of the seven **\$1,000,000 Millennium Prize Problems**, because nobody can prove that its solutions in 3D stay smooth forever.
>
> Engineers use these equations every day without a proof that they are well behaved. Let's see how that works.

---

# Act I: Deriving the equations

## 1. The continuum leap
Air is molecules, not a smooth goo. At sea level:
- the mean free path is $\lambda \approx 68$ nm;
- a 1 mm cube holds about $2.5\times10^{16}$ molecules.

Average over a volume large compared with $\lambda$ but small compared with the flow, and you get smooth **fields**:

$$
\rho(\mathbf{x},t), \qquad \mathbf{u}(\mathbf{x},t) = (u, v, w), \qquad p(\mathbf{x},t), \qquad T(\mathbf{x},t).
$$

The test is the **Knudsen number** $Kn = \lambda/L$. For $Kn \ll 1$ (a wing, a pipe, a cavity) the continuum model is excellent. For $Kn \gtrsim 0.1$ (re-entry at 100 km, MEMS devices) it breaks down, and you need kinetic theory instead.

> [!tip] Everything below is only three conservation laws
> Mass is conserved; momentum changes only through forces (Newton II); energy is conserved. The rest is bookkeeping, plus **one** piece of physics: how a fluid resists being deformed (§5).

## 2. Two ways to watch a flow: the material derivative
- **Lagrangian**: ride along with a fluid particle, like a weather balloon.
- **Eulerian**: stand still and watch the flow go past, like a weather station.

CFD grids are fixed in space, so they are Eulerian. Newton's law applies to *particles*, so it is Lagrangian. The bridge is the chain rule. Let a particle follow $\mathbf{x}(t)$ with $\dot{\mathbf{x}} = \mathbf{u}$, and carry any property $\phi(\mathbf{x},t)$:

$$
\frac{D\phi}{Dt} \equiv \frac{d}{dt}\,\phi\big(\mathbf{x}(t),t\big) = \frac{\partial \phi}{\partial t} + \frac{\partial \phi}{\partial x}\frac{dx}{dt} + \frac{\partial \phi}{\partial y}\frac{dy}{dt} + \frac{\partial \phi}{\partial z}\frac{dz}{dt}
= \underbrace{\frac{\partial \phi}{\partial t}}_{\text{local change}} + \underbrace{(\mathbf{u}\cdot\nabla)\phi}_{\text{convective change}} .
$$

> [!example] Intuition
> You drive out of a warm city into cold countryside on a day when the temperature is not changing anywhere ($\partial T/\partial t = 0$). Your car thermometer still falls, because you are **carrying it** through a temperature gradient. That is $(\mathbf{u}\cdot\nabla)T$.
>
> Apply the same idea to velocity, $(\mathbf{u}\cdot\nabla)\mathbf{u}$: a fluid particle can accelerate in a perfectly *steady* flow, simply by moving into a region where the velocity is different, e.g. through a nozzle. This term is the troublemaker of fluid dynamics.

## 3. The two theorems that do all the work
**Reynolds transport theorem** (RTT). For a *material* volume $V(t)$ whose surface $S$ moves with the flow:

$$
\frac{d}{dt}\int_{V(t)} \phi \, dV = \int_{V} \frac{\partial \phi}{\partial t}\, dV + \oint_{S} \phi\, (\mathbf{u}\cdot\mathbf{n})\, dS .
$$

In words: the total rate of change equals the change inside plus the amount the moving boundary sweeps up.

**Gauss divergence theorem**. A net flux out of a closed surface equals the total "source strength" inside:

$$
\oint_S \mathbf{F}\cdot\mathbf{n}\, dS = \int_V \nabla\cdot\mathbf{F}\, dV .
$$

**The localisation trick**. If $\int_V f\,dV = 0$ for *every* volume $V$ you can draw, then $f = 0$ at every point. This is how integral laws, which are true for every box, become PDEs, which are true at every point.

## 4. Conservation of mass → continuity
The mass in a material volume never changes:

$$
\frac{d}{dt}\int_V \rho\, dV = 0 \;\overset{\text{RTT}}{\Longrightarrow}\; \int_V \frac{\partial \rho}{\partial t}\,dV + \oint_S \rho\,\mathbf{u}\cdot\mathbf{n}\,dS = 0 \;\overset{\text{Gauss}}{\Longrightarrow}\; \int_V \left[\frac{\partial \rho}{\partial t} + \nabla\cdot(\rho\mathbf{u})\right] dV = 0 .
$$

Localise:

$$
\boxed{\;\frac{\partial \rho}{\partial t} + \nabla\cdot(\rho\,\mathbf{u}) = 0\;}
$$

**The box version.** It gives the same answer and is the one lecturers like to see; it is also exactly what a finite-volume code does. Take a fixed 2D box of size $\delta x\times\delta y$:
- $\rho u\,\delta y$ flows in on the left;
- $\big(\rho u + \tfrac{\partial(\rho u)}{\partial x}\delta x\big)\delta y$ flows out on the right, a first-order Taylor expansion;
- the same happens top and bottom.

Net outflow $= \big[\partial(\rho u)/\partial x + \partial(\rho v)/\partial y\big]\delta x\,\delta y$. This must equal the rate of loss of the mass $\rho\,\delta x\,\delta y$ inside. Divide by $\delta x\,\delta y$ and you get the same equation.

![[dam_ns_control_volume.png|620]]

Expand the divergence, $\nabla\cdot(\rho\mathbf{u}) = \mathbf{u}\cdot\nabla\rho + \rho\nabla\cdot\mathbf{u}$, and continuity becomes

$$
\frac{D\rho}{Dt} + \rho\,\nabla\cdot\mathbf{u} = 0 .
$$

So **$\nabla\cdot\mathbf{u}$ is the fractional rate at which a fluid parcel's volume grows**. If the density of every parcel stays constant (liquids, or gases at Mach $\lesssim 0.3$), then $D\rho/Dt = 0$ and

$$
\boxed{\;\nabla\cdot\mathbf{u} = 0\;} \qquad \text{(incompressible: parcels change shape, never volume)}
$$

> [!warning] Keep an eye on this one
> $\nabla\cdot\mathbf{u} = 0$ has **no time derivative** and **no pressure**. It is not an evolution equation; it is a *constraint* the velocity must obey at every instant. Hold that thought until §15, where it becomes the hardest part of the whole solver.

## 5. Newton II for a blob of fluid → the Cauchy momentum equation
Rate of change of momentum = surface forces + body forces:

$$
\frac{d}{dt}\int_V \rho\,\mathbf{u}\, dV = \oint_S \mathbf{t}\, dS + \int_V \rho\,\mathbf{g}\, dV .
$$

The surface force per unit area is the **traction** $\mathbf{t}$. Cauchy's tetrahedron argument (shrink a tetrahedron to a point; surface forces scale as $\ell^2$ and body forces and inertia as $\ell^3$, so the surface forces must balance on their own) shows that $\mathbf{t}$ depends *linearly* on the surface normal:

$$
\mathbf{t} = \boldsymbol{\sigma}\cdot\mathbf{n}, \qquad \sigma_{ij} = \text{force in direction } j \text{ on a face whose normal points in direction } i .
$$

Now apply RTT and Gauss, and localise:

$$
\frac{\partial(\rho\mathbf{u})}{\partial t} + \nabla\cdot(\rho\,\mathbf{u}\mathbf{u}) = \nabla\cdot\boldsymbol{\sigma} + \rho\,\mathbf{g} \qquad \text{(conservative form)}
$$

> [!example] The satisfying cancellation
> In index notation, expand the left-hand side with the product rule:
> $$
> \frac{\partial(\rho u_i)}{\partial t} + \frac{\partial(\rho u_i u_j)}{\partial x_j}
> = u_i\underbrace{\left[\frac{\partial \rho}{\partial t} + \frac{\partial(\rho u_j)}{\partial x_j}\right]}_{=\,0 \text{ by continuity!}} + \rho\left[\frac{\partial u_i}{\partial t} + u_j\frac{\partial u_i}{\partial x_j}\right]
> $$
> Mass conservation removes a whole bracket, leaving **mass × acceleration = force** per unit volume:
> $$
> \rho\,\frac{D\mathbf{u}}{Dt} = \nabla\cdot\boldsymbol{\sigma} + \rho\,\mathbf{g} \qquad \text{(Cauchy momentum equation)}
> $$

Angular momentum conservation, applied to a small cube, also forces $\sigma_{ij} = \sigma_{ji}$: the stress tensor is **symmetric**. In the box picture, $\sigma_{yx}$ on the top and bottom faces is exactly what makes a layer of fluid drag the layer beneath it.

> [!info] Counting unknowns
> Cauchy is exact for *any* continuum: water, honey, steel, toothpaste. It is also **not closed**. In 3D there are four equations (continuity plus three momentum) but 1 + 3 + 6 unknowns ($\rho$, $\mathbf{u}$, and the six independent components of $\boldsymbol{\sigma}$). To close it we need a constitutive law: the one piece of physics that says what *kind* of material this is.

## 6. What makes a fluid a fluid: the Newtonian closure
**Step 1: split off pressure.** A fluid at rest carries no shear stress, only an isotropic pressure. So write

$$
\boldsymbol{\sigma} = -p\,\mathbf{I} + \boldsymbol{\tau},
$$

where $\boldsymbol{\tau}$ is the **viscous stress** and vanishes when the fluid is at rest.

**Step 2: what can $\boldsymbol{\tau}$ depend on?** A solid resists *strain*, meaning how far it has been deformed. A fluid resists **strain rate**, meaning how fast it is being deformed. So $\boldsymbol{\tau}$ must depend on the velocity gradient $\nabla\mathbf{u}$, which splits into a symmetric part and an antisymmetric part:

$$
\frac{\partial u_i}{\partial x_j} = \underbrace{\tfrac{1}{2}\left(\frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i}\right)}_{S_{ij}\text{: strain rate (stretch + shear)}} + \underbrace{\tfrac{1}{2}\left(\frac{\partial u_i}{\partial x_j} - \frac{\partial u_j}{\partial x_i}\right)}_{\Omega_{ij}\text{: pure rotation}}
$$

Spin a bucket of water at a steady rate and it rotates as a rigid body, with no stress between layers. So $\boldsymbol{\Omega}$ cannot produce stress, and $\boldsymbol{\tau}$ depends only on $\mathbf{S}$ ([[Newtonian Fluid and Strain-Rate Tensor]]).

**Step 3: the Newtonian assumption.** Make $\boldsymbol{\tau}$ linear in $\mathbf{S}$ and isotropic (no preferred direction). The most general such tensor has exactly two constants:

$$
\boldsymbol{\tau} = 2\mu\,\mathbf{S} + \lambda\,(\nabla\cdot\mathbf{u})\,\mathbf{I}
$$

- $\mu$ is the **dynamic viscosity**.
- $\lambda$ is the second viscosity coefficient.

**Step 4: Stokes' hypothesis (1845).** Require the mechanical pressure (minus the average normal stress) to equal the thermodynamic pressure $p$. Then $\operatorname{tr}\boldsymbol{\tau} = 0$, which gives $(2\mu + 3\lambda)\nabla\cdot\mathbf{u} = 0$, so $\lambda = -\tfrac{2}{3}\mu$. In words, the bulk viscosity is zero:

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

## 7. Assemble: the Navier–Stokes equations
Substitute $\boldsymbol{\sigma} = -p\mathbf{I} + \boldsymbol{\tau}$ into Cauchy to get the **compressible Navier–Stokes equations**:

$$
\rho\left(\frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u}\cdot\nabla)\mathbf{u}\right) = -\nabla p + \nabla\cdot\left[\mu\left(\nabla\mathbf{u} + \nabla\mathbf{u}^{\mathsf T}\right) - \tfrac{2}{3}\mu(\nabla\cdot\mathbf{u})\mathbf{I}\right] + \rho\,\mathbf{g}
$$

The unknowns are $\rho, u, v, w, p, T$, but so far we have only 4 equations. Add the **energy equation** and an **equation of state** ($p = \rho R T$) and the system closes. That full set is the subject of SESA3029 and SESA6082. Set $\mu = 0$ and you get the **Euler equations** (see [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]).

**The incompressible, constant-viscosity special case.** This is what most of Part A and the solver below use. With $\nabla\cdot\mathbf{u} = 0$ and constant $\mu$, the viscous term simplifies beautifully:

$$
\frac{\partial \tau_{ij}}{\partial x_j} = \mu\frac{\partial}{\partial x_j}\left(\frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i}\right) = \mu\nabla^2 u_i + \mu\frac{\partial}{\partial x_i}\underbrace{\left(\frac{\partial u_j}{\partial x_j}\right)}_{=\,0} = \mu\,\nabla^2 u_i .
$$

(The order of differentiation swaps freely, and the divergence vanishes.) Divide by $\rho$ and write $\nu = \mu/\rho$ for the **kinematic viscosity**:

> [!important] The incompressible Navier–Stokes equations
> $$
> \nabla\cdot\mathbf{u} = 0
> $$
> $$
> \underbrace{\frac{\partial \mathbf{u}}{\partial t}}_{\substack{\text{unsteady}\\\text{acceleration}}} + \underbrace{(\mathbf{u}\cdot\nabla)\mathbf{u}}_{\substack{\text{convective}\\\text{acceleration}}} = \underbrace{-\frac{1}{\rho}\nabla p}_{\substack{\text{pressure}\\\text{force}}} + \underbrace{\nu\nabla^2\mathbf{u}}_{\substack{\text{viscous}\\\text{diffusion}}} + \underbrace{\mathbf{g}}_{\substack{\text{body}\\\text{force}}}
> $$
> Four equations (in 3D) for four unknowns $(u, v, w, p)$. Closed at last.

---

# Act II: Understanding what every term does

## 8. The anatomy table
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

> [!tip] One sentence per term
> **Convection moves momentum, diffusion smears it, pressure polices it.**
> - Convection is the only nonlinear term and the only one that can create smaller and smaller scales.
> - Diffusion destroys those scales.
> - Pressure exists purely to enforce the rule that nothing gets compressed.

## 9. Two hidden equations inside Navier–Stokes
**The pressure Poisson equation.** Take the divergence of the momentum equation. The time derivative and viscous terms vanish, because $\nabla\cdot\mathbf{u} = 0$, which leaves

$$
\nabla^2 p = -\rho\,\nabla\cdot\big[(\mathbf{u}\cdot\nabla)\mathbf{u}\big] = -\rho\,\frac{\partial u_i}{\partial x_j}\frac{\partial u_j}{\partial x_i} .
$$

Pressure has no evolution equation of its own; it is set **instantaneously by the whole velocity field**, as if sound travelled infinitely fast. That is what "incompressible" really means, and it is why every incompressible solver has a Poisson solve inside it.

**The vorticity equation.** Take the curl of momentum, with $\boldsymbol{\omega} = \nabla\times\mathbf{u}$. Pressure vanishes completely:

$$
\frac{D\boldsymbol{\omega}}{Dt} = \underbrace{(\boldsymbol{\omega}\cdot\nabla)\mathbf{u}}_{\text{vortex stretching}} + \nu\nabla^2\boldsymbol{\omega} .
$$

Stretch a vortex tube and it spins faster, just as a figure skater does by pulling in their arms. That drives the turbulent energy cascade to small scales. **In 2D the stretching term is identically zero**, because $\boldsymbol{\omega}$ is perpendicular to the plane of $\mathbf{u}$. This is why 2D turbulence behaves completely differently, and why 2D smoothness has been proven while 3D has not.

## 10. One number to rule them all: the Reynolds number
Scale everything with a length $L$ and velocity $U$: $\mathbf{x}^* = \mathbf{x}/L$, $\mathbf{u}^* = \mathbf{u}/U$, $t^* = tU/L$, $p^* = p/(\rho U^2)$. Momentum then becomes

$$
\frac{\partial \mathbf{u}^*}{\partial t^*} + (\mathbf{u}^*\cdot\nabla^*)\mathbf{u}^* = -\nabla^* p^* + \frac{1}{Re}\nabla^{*2}\mathbf{u}^*, \qquad Re = \frac{UL}{\nu} = \frac{\text{inertia}}{\text{viscous forces}} .
$$

Every incompressible flow with the same geometry and the same $Re$ is **the same flow**. That is why wind-tunnel models work, and why this note's solver only needs one input: $Re$.

| Flow | $U$ | $L$ | $Re$ |
|---|---|---|---|
| swimming bacterium | 30 μm/s | 2 μm | $\sim 10^{-4}$ |
| the solver below (lid-driven cavity) | n/a | n/a | $100$ |
| cyclist | 10 m/s | 0.5 m | $\sim 3\times10^{5}$ |
| car on a motorway | 30 m/s | 4 m | $\sim 8\times10^{6}$ |
| A320 wing at cruise (chord ≈ 4 m) | 230 m/s | 4 m | $\sim 2.5\times10^{7}$ |

**The two limits.**
- **$Re \to 0$ (Stokes flow).** The nonlinear term drops out and the equations become linear and *time-reversible*. G. I. Taylor famously stirred dye into glycerine between two cylinders, then un-stirred it back into a blob.
- **$Re \to \infty$.** You might expect the Euler equations, but viscosity never really disappears. It retreats into a boundary layer of thickness $\delta/L \sim Re^{-1/2}$. Drop it entirely and you predict zero drag ([[D'Alembert's Paradox]]).

> [!danger] Why these equations are genuinely hard
> 1. **Nonlinearity.** $(\mathbf{u}\cdot\nabla)\mathbf{u}$ transfers energy to ever-smaller eddies until viscosity kills them at the Kolmogorov scale, $\eta/L \sim Re^{-3/4}$.
>    - Resolving every eddy in 3D takes $N \sim (L/\eta)^3 \sim Re^{9/4}$ grid points.
>    - For the A320 wing that is about $10^{16.6}$ points, which is why industry uses RANS ([[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] · [[DNS, LES and Scale-Resolving Simulation]]).
> 2. **Pressure has no equation of its own.** It is a Lagrange multiplier that enforces a constraint (§15).
> 3. **Mixed type.** In one system, hyperbolic convection, parabolic diffusion and elliptic pressure each want different numerical treatment.
> 4. **The \$1M question.** Given smooth initial data in 3D, does a smooth solution exist for all time, or can the velocity blow up to infinity in finite time? Nobody knows. (In 2D, global smoothness was proven decades ago.)

---

# Act III: Teaching a computer to do calculus

A computer cannot differentiate. It can add, multiply and remember numbers. So the whole game is to **replace every derivative with arithmetic on grid values**, then prove that the arithmetic converges to the calculus as the grid is refined ([[Finite Difference Approximations]] · [[Taylor Table Method]]).

## 11. The grid and the notation
- Uniform spacing $h$ in $x$ and $y$, with time step $\Delta t$.
- $f_i^n \approx f(ih,\, n\Delta t)$.
- Everything below comes from **Taylor series**:

$$
f_{i\pm1} = f_i \pm h f'_i + \frac{h^2}{2}f''_i \pm \frac{h^3}{6}f'''_i + \frac{h^4}{24}f''''_i \pm \dots
$$

We discretise **one term at a time**, because each term has a different mathematical personality (§8).

## 12. Term 1: the time derivative $\partial\mathbf{u}/\partial t$

| Scheme | Formula | Order | Character |
|---|---|---|---|
| forward (explicit) Euler | $\dfrac{u^{n+1} - u^n}{\Delta t} = \mathcal{R}(u^n)$ | $O(\Delta t)$ | cheap, no matrix solve, conditionally stable |
| backward (implicit) Euler | $\dfrac{u^{n+1} - u^n}{\Delta t} = \mathcal{R}(u^{n+1})$ | $O(\Delta t)$ | matrix solve, unconditionally stable, damps transients |
| Crank–Nicolson | $\dfrac{u^{n+1} - u^n}{\Delta t} = \tfrac12\left[\mathcal{R}(u^n) + \mathcal{R}(u^{n+1})\right]$ | $O(\Delta t^2)$ | matrix solve, stable, can ring |
| RK4 | four explicit stages | $O(\Delta t^4)$ | accurate, larger stability region |

Here $\mathcal{R}$ is the spatial "right-hand side": everything except $\partial\mathbf{u}/\partial t$. The Taylor expansion $\frac{u^{n+1}-u^n}{\Delta t} = u_t + \frac{\Delta t}{2}u_{tt} + O(\Delta t^2)$ shows forward Euler's first-order error. See [[Explicit and Implicit Time Integration]] · [[Runge-Kutta Methods]]. The solver below uses forward Euler: it is the simplest option, and for a steady target it just needs to be stable.

## 13. Term 2: viscous diffusion $\nu\nabla^2\mathbf{u}$ (the friendly one)
Add the Taylor series for $f_{i+1}$ and $f_{i-1}$. The odd terms cancel:

$$
f_{i+1} + f_{i-1} = 2f_i + h^2 f''_i + \frac{h^4}{12}f''''_i + \dots \;\;\Longrightarrow\;\; \frac{\partial^2 f}{\partial x^2}\bigg|_i = \frac{f_{i+1} - 2f_i + f_{i-1}}{h^2} - \underbrace{\frac{h^2}{12}f''''_i}_{\text{truncation error}} .
$$

This is second-order accurate. In 2D it becomes the famous **5-point stencil**:

$$
\nabla^2 f\big|_{i,j} \approx \frac{f_{i+1,j} + f_{i-1,j} + f_{i,j+1} + f_{i,j-1} - 4f_{i,j}}{h^2} .
$$

**Stability.** Diffusion is isotropic and smoothing, so **central differencing is always right** for it. With explicit Euler, von Neumann analysis ([[Von Neumann Stability Analysis]]) substitutes $f_i^n = G^n e^{\mathrm{i}kih}$:

$$
G = 1 - 4F\sin^2\!\left(\tfrac{kh}{2}\right), \quad F = \frac{\nu\Delta t}{h^2} \quad\Longrightarrow\quad \lvert G\rvert \le 1 \iff F \le \tfrac12 \;\;\text{(1D)}, \qquad F \le \tfrac14 \;\;\text{(2D)} .
$$

> [!warning] The explicit diffusion trap
> $\Delta t \le h^2/(4\nu)$. Halve the grid spacing and the time step must **quarter**. That means 8× the work in 2D, because there are 4× the cells for ¼ the step. This is why production codes treat diffusion implicitly ([[CFL and Fourier Numbers]]).

## 14. Term 3: convection $(\mathbf{u}\cdot\nabla)\mathbf{u}$ (where the drama is)
To see what goes wrong, study the model problem $f_t + c f_x = 0$ with $c > 0$. Its exact solution slides a shape to the right *without changing it*.

**Option A: central difference** $\;\dfrac{f_{i+1} - f_{i-1}}{2h}$. Second order, no numerical diffusion, symmetric. But:
- With forward Euler, $G = 1 - \mathrm{i}\,C\sin(kh)$, so $\lvert G\rvert > 1$ for every mode. It is **unconditionally unstable** for pure convection.
- It ignores the direction the information comes from, and produces **wiggles** next to sharp gradients.

**Option B: first-order upwind** $\;\dfrac{f_i - f_{i-1}}{h}$ (look *upstream*, where the information comes from). It is stable for $C = c\Delta t/h \le 1$ and never makes wiggles. But it is only first order. So what exactly does it get wrong?

> [!important] The modified equation: what the scheme *actually* solves
> Taylor-expand upwind + forward Euler:
> $$
> \frac{f^{n+1}_i - f^n_i}{\Delta t} + c\,\frac{f^n_i - f^n_{i-1}}{h}
> = f_t + \frac{\Delta t}{2}f_{tt} + c f_x - \frac{ch}{2}f_{xx} + O(h^2, \Delta t^2) = 0 .
> $$
> To leading order $f_t = -c f_x$, so $f_{tt} = c^2 f_{xx}$. Substitute:
> $$
> \boxed{\; f_t + c f_x = \nu_{num}\, f_{xx}, \qquad \nu_{num} = \frac{ch}{2}\,(1 - C)\;}
> $$
> **The upwind scheme is not solving the advection equation. It is solving an advection–*diffusion* equation, with a viscosity nobody asked for.**
> - At exactly $C = 1$ the error vanishes: the scheme shifts every value one cell per step, which is exact.
> - As $C \to 0$ the extra viscosity is largest.

![[dam_ns_numerical_diffusion.png|680]]

The figure shows this is not just algebra. A Gaussian advected once around a periodic domain with upwind ($C = 0.5$, 200 cells) lands **exactly** on the analytic solution of the *diffusion* equation with $\nu_{num} = ch(1-C)/2$. The peaks agree to 4 decimal places (0.6245 vs 0.6247).

**What this means for Navier–Stokes.** The ratio of fake to real viscosity is

$$
\frac{\nu_{num}}{\nu} = \frac{Uh}{2\nu}(1 - C) = \frac{Pe_h}{2}(1 - C), \qquad Pe_h = \frac{Uh}{\nu} \;\;\text{(cell Péclet number)} .
$$

On a coarse mesh at high $Re$, $Pe_h$ can be $10^3$ or more. Your first-order simulation at $Re = 10^6$ might then effectively be running at $Re \sim 10^3$. Boundary layers get too thick and separation is suppressed. **This is why Fluent tells you to switch to second order.**

**When is central safe?** Discretise steady convection–diffusion, $u\phi_x = \nu\phi_{xx}$, with central differences for both terms and rearrange:

$$
\phi_i = \tfrac12\left[\left(1 - \tfrac{Pe_h}{2}\right)\phi_{i+1} + \left(1 + \tfrac{Pe_h}{2}\right)\phi_{i-1}\right] .
$$

If $Pe_h > 2$, the coefficient on $\phi_{i+1}$ goes **negative**. A bigger neighbour then makes $\phi_i$ smaller, which is physically absurd and produces wiggles. So central convection is bounded **only if $Pe_h \le 2$**, meaning the physical viscosity is doing the stabilising. Beyond that you need upwind-biased, higher-order schemes such as QUICK or second-order upwind, with limiters (TVD/MUSCL) to stop overshoots.

| Scheme | Order | Numerical diffusion | Bounded? | Where it's used |
|---|---|---|---|---|
| 1st-order upwind (UDS) | 1 | large: $\tfrac{ch}{2}(1-C)$ | always | first iterations, robust startup |
| central (CDS) | 2 | none (dispersive instead) | only if $Pe_h \le 2$ | LES/DNS, low-$Re$, **this solver** |
| 2nd-order upwind / QUICK | 2 / 3 | small | nearly (needs a limiter) | default production RANS |
| TVD / MUSCL with limiter | 2 (1 at extrema) | switched on only near jumps | yes | shocks, sharp interfaces |

See [[Convective Interpolation Schemes]] and [[Truncation Error and Order of Accuracy]].

**The nonlinear twist.** In NS the "advection speed" is the velocity itself. Using the conservative form $\partial(u^2)/\partial x + \partial(uv)/\partial y$ means that what leaves one cell enters its neighbour exactly, so fluxes **telescope**. On a staggered grid, the central version also conserves kinetic energy discretely. That is why it can run without upwinding when $Pe_h < 2$.

## 15. Term 4: pressure and the incompressibility constraint (the boss fight)
Suppose we march momentum forward in time with any scheme from §12–14. Nothing forces the new velocity to satisfy $\nabla\cdot\mathbf{u} = 0$, and continuity has no $\partial/\partial t$ to march. The fix is a beautiful piece of vector calculus.

> [!info] Helmholtz–Hodge decomposition
> Any smooth vector field can be split uniquely into a divergence-free part and a gradient:
> $$
> \mathbf{w} = \underbrace{\mathbf{u}}_{\nabla\cdot\mathbf{u}\,=\,0} + \nabla\phi .
> $$
> Pressure is exactly the gradient part that removes the divergence. **The pressure gradient is the projection that throws away the compressible part of the velocity.**

**Chorin's projection method (1968).** Each time step has three moves:

1. **Predict**: advance momentum *ignoring* pressure. The intermediate $\mathbf{u}^*$ is **not** divergence-free.
$$
\mathbf{u}^* = \mathbf{u}^n + \Delta t\left[-(\mathbf{u}^n\cdot\nabla)\mathbf{u}^n + \nu\nabla^2\mathbf{u}^n\right]
$$
2. **Solve for pressure**: require $\nabla\cdot\mathbf{u}^{n+1} = 0$ in step 3.
$$
\nabla^2 p^{n+1} = \frac{\rho}{\Delta t}\,\nabla\cdot\mathbf{u}^*
$$
3. **Project (correct)**:
$$
\mathbf{u}^{n+1} = \mathbf{u}^* - \frac{\Delta t}{\rho}\nabla p^{n+1}
$$

**Check it works:** $\nabla\cdot\mathbf{u}^{n+1} = \nabla\cdot\mathbf{u}^* - \frac{\Delta t}{\rho}\nabla^2 p^{n+1} = \nabla\cdot\mathbf{u}^* - \nabla\cdot\mathbf{u}^* = 0$. ✓

> [!tip] Pressure boundary conditions come for free
> At a wall, the normal velocity is already correct in $\mathbf{u}^*$, so the correction must not change it. That gives $\partial p/\partial n = 0$.
>
> With pure Neumann conditions, $p$ is only defined **up to a constant**: the matrix is singular, since the constant vector is in its null space. So **pin one value** ($p = 0$ in one cell). This is the same idea as removing rigid-body modes in FEA ([[Boundary Conditions and Rigid Body Modes]]).

**Projection vs SIMPLE.** Fluent's default family, SIMPLE ([[Pressure-Velocity Coupling and SIMPLE]]), is the *steady, iterative* cousin of the same idea.

| | Projection (Chorin) | SIMPLE |
|---|---|---|
| goal | time-accurate transient | steady state (or inner iterations of a transient step) |
| pressure equation | Poisson for $p^{n+1}$ | Poisson-like equation for a *correction* $p'$ |
| relaxation | none needed | under-relax $p$ and $\mathbf{u}$ (e.g. 0.3 / 0.7) |
| converged when | the time loop reaches steady state | the residuals of mass and momentum drop |

## 16. Where do the unknowns live? The checkerboard catastrophe
The obvious choice is to store $u$, $v$ and $p$ at the **same** points (a collocated grid) and use central differences:

$$
\frac{\partial p}{\partial x}\bigg|_i \approx \frac{p_{i+1} - p_{i-1}}{2h} .
$$

This stencil **never looks at $p_i$**. Take a checkerboard pressure $p_{i,j} = (-1)^{i+j}$. Its discrete gradient is **zero everywhere**, so the momentum equation cannot feel it. The solution can be contaminated by a wild, oscillating pressure that the discretisation considers perfectly acceptable.

There are two classic cures:
- **Staggered (MAC) grid** (Harlow & Welch, 1965). Store $p$ at cell centres and each velocity component on the cell *faces* it points through. The pressure gradient that drives $u_{i+\frac12,j}$ is now $\frac{p_{i+1,j} - p_{i,j}}{h}$: compact, over one $h$, with no gap for a checkerboard to hide in.
- **Rhie–Chow interpolation** (1983). Keep a collocated grid (much easier for unstructured meshes) but add a pressure-smoothing term to the face velocities. This is what Fluent, OpenFOAM and STAR-CCM+ do. Fluent's "PRESTO!" pressure option is a staggered-style scheme.

![[dam_ns_mac_grid.png|640]]

## 17. The complete discrete equations on a MAC grid
Everything now fits together. Grid indices: $p_{i,j}$ at centres, $u_{i+\frac12,j}$ on vertical faces, $v_{i,j+\frac12}$ on horizontal faces.

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

> [!important] The staggered-grid magic trick
> Take the discrete divergence (face differences over a cell) of the discrete gradient (centre differences across a face). You get **exactly** the 5-point Laplacian used in the Poisson equation. The discrete operators fit together like the continuous ones do ($\nabla\cdot\nabla = \nabla^2$).
>
> So after projection, the discrete divergence is zero **to machine precision**, not merely to truncation error. The solver below reports $\max\lvert\nabla\cdot\mathbf{u}\rvert \approx 9\times10^{-14}$.

**It is also a finite-volume method.** Integrate $\nabla\cdot\mathbf{u} = 0$ over cell $(i, j)$ and apply Gauss:

$$
\oint \mathbf{u}\cdot\mathbf{n}\, dS = (u_e - u_w)\,h + (v_n - v_s)\,h = 0 .
$$

That is the discrete continuity equation above, multiplied by $h^2$. Do the same with the momentum equation over a control volume shifted by half a cell and you recover the u-momentum update. **On a uniform Cartesian grid, MAC finite differences and finite volumes are the same method** ([[Finite Volume Method]] · [[SESA2029 A9 - Finite Volume Method]]).

**Boundary conditions via ghost cells** ([[CFD Boundary Conditions]]):
- $v$ lives *on* the top and bottom walls, so just set $v = 0$ there. Likewise $u = 0$ on the side walls.
- $u$ lives half a cell *away from* the lid. To impose $u = U$ at the lid, add a ghost value above it so that the *average* equals $U$: $\tfrac12(u_g + u_{int}) = U \;\Rightarrow\; u_g = 2U - u_{int}$. At a stationary wall, $u_g = -u_{int}$.

## 18. The stability budget
Three dimensionless numbers must be kept in check for this explicit, central scheme ([[CFL and Fourier Numbers]]):

| Constraint | Formula | Limit | Why | Solver value ($N = 64$, $Re = 100$, $\Delta t = 0.004$) |
|---|---|---|---|---|
| CFL (convection) | $C = U\Delta t/h$ | $\lesssim 1$ | information may not jump more than a cell per step | 0.256 ✓ |
| diffusion number | $F = \nu\Delta t/h^2$ | $\le \tfrac14$ (2D) | von Neumann, §13 | 0.164 ✓ |
| cell Péclet | $Pe_h = Uh/\nu$ | $\le 2$ | boundedness of central convection, §14 | 1.56 ✓ |

(Everything is non-dimensional with $U = L = \rho = 1$, so $\nu = 1/Re$.)

---

# Act IV: Build it, run it, check it

## 19. The whole solver in 25 lines
The complete script is the module's `scripts/ns_cavity_solver.py` (about 180 lines including plotting and the Ghia comparison; runs in about 3 s). Its core is §17 almost symbol for symbol:

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

## 20. The result: the lid-driven cavity at $Re = 100$
A square box of fluid, closed on three sides, has a lid sliding across the top. It is the "hello world" of CFD: simple geometry, no inflow or outflow, and yet genuinely nonlinear physics.

![[dam_ns_cavity_streamlines.png|600]]

- **Primary vortex.** The lid drags fluid right, it dives down the right wall, returns along the bottom and rises up the left wall. The centre sits at $(0.609, 0.734)$ with $\psi_{min} = -0.1032$. Ghia et al. report $(0.6172, 0.7344)$ and $-0.1034$, so the centre agrees to within one cell ($h = 0.0156$). It sits **downstream** of centre ($x > 0.5$) because convection carries it. At $Re \to 0$ it would sit dead centre, since Stokes flow is symmetric.
- **Corner eddies.** Small counter-rotating eddies appear in both bottom corners. Moffatt (1964) proved something wonderful: in a sharp corner there is an **infinite sequence** of ever-smaller, ever-weaker eddies nested into the corner, In a 90° corner each one is about 16.6× smaller than the last, and its velocities are about 2,200× weaker. (This comes from the Stokes-flow corner eigenvalue equation $\sin(2\alpha z) = -z\sin 2\alpha$ with $2\alpha = 90°$, whose root is $z \approx 2.74 + 1.12\,\mathrm{i}$.) We resolve the first; the second would need a grid about 16× finer near the corner.
- **Diagnostics.** Steady state is reached at $t \approx 26$. $\max\lvert\nabla\cdot\mathbf{u}\rvert = 9.3\times10^{-14}$: the staggered magic trick, confirmed.

## 21. Verification: does it converge at the rate the maths promised?
Everything in §13–14 was second order, so errors should fall **4×** each time $h$ halves ([[Mesh Convergence and Grid Independence]]). The solver was run on three grids:

| Quantity | $N = 32$ | $N = 64$ | $N = 128$ | observed order $p$ | Richardson extrapolation | Ghia et al. (1982), 129 × 129 |
|---|---|---|---|---|---|---|
| $u_{min}$ on $x = 0.5$ | −0.2089 | −0.2128 | −0.2137 | 2.1 | −0.2140 | −0.2109 |
| $v_{min}$ on $y = 0.5$ | −0.2487 | −0.2527 | −0.2536 | 2.2 | −0.2539 | −0.2453 |
| $v_{max}$ on $y = 0.5$ | 0.1754 | 0.1785 | 0.1793 | 2.0 | 0.1796 | 0.1753 |

The observed order comes from $p = \ln\!\left(\dfrac{f_{32} - f_{64}}{f_{64} - f_{128}}\right)\big/\ln 2$, and the extrapolated value from $f_{\infty} \approx f_{128} + \dfrac{f_{128} - f_{64}}{2^p - 1}$.

> [!success] Verification passed
> The observed order is $p \approx 2$, exactly as the Taylor series in §13–14 predicted. This is the strongest evidence a code can give that it is **solving the equations right**. Bugs almost always show up as the wrong order, even when the answer "looks" plausible ([[Verification and Validation]] · [[Residual vs Solution Error]]).

## 22. Comparison with the benchmark (and a lesson about benchmarks)

![[dam_ns_cavity_validation.png|760]]

At $N = 64$ the centreline profiles sit on Ghia's points: the largest pointwise differences are $0.004\,U$ in $u$ and $0.009\,U$ in $v$.

The table in §21 hides a subtlety. Our three grids converge *past* Ghia's values, to extrapolated extremes about 1.5–3.5% larger in magnitude. **Who is wrong?** Probably neither, in any interesting sense:
1. **Ghia's numbers are a numerical solution too.** They were computed on a 129 × 129 grid and carry their own discretisation error.
2. **They are tabulated at their grid points,** so the tabulated "minimum" is the value at the nearest point, not the true extremum.

> [!important] The lessons for real CFD
> - **A benchmark is a reference, not the truth.** Always ask how *it* was computed.
> - Comparing code against code (Ghia) is really part of **verification**. **Validation** means comparing with *physical experiment*, which brings its own error bars ([[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]).
> - A grid study with an observed order and a Richardson estimate turns "it looks converged" into "the discretisation error is about 0.1%". That sentence is what separates a CFD engineer from a CFD user.

## 23. From this note to the Fluent GUI: a dictionary
Every option in a commercial solver is one of the choices made above.

| What you set in the GUI | What it means mathematically | Where in this note |
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

## One-page summary
> [!summary] Everything on a postcard
> - **Derivation**: control volume → RTT + Gauss → localise.
>   - Mass: $\partial_t\rho + \nabla\cdot(\rho\mathbf{u}) = 0$.
>   - Momentum: $\rho\,D\mathbf{u}/Dt = \nabla\cdot\boldsymbol{\sigma} + \rho\mathbf{g}$.
>   - Newtonian + Stokes: $\boldsymbol{\sigma} = -p\mathbf{I} + \mu(\nabla\mathbf{u} + \nabla\mathbf{u}^{\mathsf T}) - \tfrac23\mu(\nabla\cdot\mathbf{u})\mathbf{I}$.
>   - Incompressible: $\nabla\cdot\mathbf{u} = 0$, $\;\partial_t\mathbf{u} + (\mathbf{u}\cdot\nabla)\mathbf{u} = -\nabla p/\rho + \nu\nabla^2\mathbf{u}$.
> - **Characters**: convection is hyperbolic and nonlinear; diffusion is parabolic; pressure is elliptic, a constraint enforcer. Nondimensionally only $Re = UL/\nu$ matters.
> - **Discretise**:
>   - diffusion: central, $F \le \tfrac14$;
>   - convection: upwind adds $\nu_{num} = \tfrac{ch}{2}(1-C)$; central is bounded only if $Pe_h \le 2$;
>   - pressure: projection $\nabla^2 p = \tfrac{\rho}{\Delta t}\nabla\cdot\mathbf{u}^*$, $\;\mathbf{u} = \mathbf{u}^* - \tfrac{\Delta t}{\rho}\nabla p$;
>   - staggered grid: no checkerboard, and divergence zero to machine precision.
> - **Check**: observed order ≈ design order, Richardson extrapolation, benchmark (and its own error), then experiment.

## Test yourself
> [!question]- 1. Show that for incompressible flow with constant $\mu$, $\nabla\cdot\boldsymbol{\tau} = \mu\nabla^2\mathbf{u}$.
> $\partial_j\tau_{ij} = \mu\,\partial_j\partial_j u_i + \mu\,\partial_j\partial_i u_j = \mu\nabla^2 u_i + \mu\,\partial_i(\partial_j u_j) = \mu\nabla^2 u_i$. The $-\tfrac23\mu(\nabla\cdot\mathbf{u})$ term also vanishes.

> [!question]- 2. Why does the upwind scheme smear a sharp front, and by how much?
> Its modified equation is $f_t + cf_x = \nu_{num}f_{xx}$ with $\nu_{num} = \tfrac{ch}{2}(1-C)$. The leading truncation error is a second derivative, which acts like physical diffusion. Refining $h$ or running closer to $C = 1$ reduces it.

> [!question]- 3. Why can't a collocated central-difference scheme "see" a checkerboard pressure field?
> $(p_{i+1} - p_{i-1})/2h$ skips $p_i$. For $p = (-1)^{i+j}$, the values at $i+1$ and $i-1$ are equal, so the discrete gradient is zero everywhere and the momentum equations get no force from it. The fix is a staggered grid (compact gradient) or Rhie–Chow interpolation.

> [!question]- 4. Prove that the projection step makes the new velocity divergence-free.
> $\nabla\cdot\mathbf{u}^{n+1} = \nabla\cdot\mathbf{u}^* - \tfrac{\Delta t}{\rho}\nabla^2 p^{n+1}$, and the Poisson equation sets $\nabla^2 p^{n+1} = \tfrac{\rho}{\Delta t}\nabla\cdot\mathbf{u}^*$. So the result is 0. On a MAC grid this holds exactly in the discrete sense too, because discrete div∘grad equals the discrete Laplacian.

> [!question]- 5. The solver is run on $N = 128$ at $Re = 100$ with $U = L = 1$. What is the largest stable explicit $\Delta t$, and which limit sets it?
> $h = 1/128$ and $\nu = 0.01$.
> - Diffusion: $\Delta t \le h^2/(4\nu) = 1.53\times10^{-3}$.
> - CFL: $\Delta t \le h/U = 7.8\times10^{-3}$.
>
> **Diffusion wins**. Refining the grid makes the $h^2$ limit dominate, which is the explicit diffusion trap from §13. Check the cell Péclet number too: $Pe_h = Uh/\nu = 0.78 < 2$ ✓.

> [!question]- 6. A student's second-order code shows errors falling by about 2× per grid halving. What does that tell you?
> The observed order is $p \approx 1$, not 2. Something is first order, usually a boundary condition (e.g. the wall value set at the wrong location instead of by ghost-cell averaging), an upwind term left in, or an inconsistent interpolation. The order test found a bug that the plots would have hidden.

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
- Own solver and figures: `scripts/ns_cavity_solver.py`, `scripts/make_figures.py` (all numbers above were produced by these)
