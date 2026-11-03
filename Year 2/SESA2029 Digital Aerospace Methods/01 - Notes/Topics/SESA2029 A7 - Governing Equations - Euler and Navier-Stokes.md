---
title: "SESA2029 A7 - Governing Equations - Euler and Navier-Stokes"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 7
tags: [sesa2029, cfd, governing-equations, navier-stokes]
aliases: ["Governing equations for CFD", "Euler equations", "Navier-Stokes derivation", "CFD Lecture 8"]
date: 2026-10-30
status: lectured
coverage: "Week 4 (2025-10-24)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]", "[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]"]
next_topics: ["[[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]"]
key_concepts: ["[[Conservation Form of the Governing Equations]]", "[[Navier-Stokes Equations]]", "[[Newtonian Fluid and Strain-Rate Tensor]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L8, pp. 101–112)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-24.txt"]
---

# SESA2029 A7 - Governing Equations - Euler and Navier-Stokes

> [!abstract] Summary
> Conservation of mass, momentum and energy for a small control volume all take the same form, rate of increase plus net flux out equals sources, so deriving it once for a generic quantity $\phi$ gives every equation in conservation form, the form CFD discretises. For incompressible flow the mass equation becomes $\nabla\cdot\mathbf u=0$ and the pressure-only momentum equations, the Euler equations, close without any energy equation. Adding viscous stresses proportional to the strain rate, the Newtonian model, gives the incompressible Navier–Stokes equations.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to derive or explain continuity, Euler or Navier–Stokes, to define incompressible or Newtonian, or to expand the index form.
> - **Assumptions:** 2D control volume of unit depth, first Taylor term across the cell, constant $\rho$ and $\mu$ for the incompressible form, Newtonian fluid.
> - **Method:** 1. Write the conservation law in words. 2. Flux in at one face, flux plus $\partial(\cdot)/\partial x\,\delta x$ out at the other. 3. Divide by $\delta x\delta y$ to get $\partial_t\phi+\partial_x(\phi u)+\partial_y(\phi v)$. 4. Put $\phi=\rho,\rho u,\rho v$ and add the pressure and viscous forces. 5. Use $\sigma_{ij}=2\mu S_{ij}$ and continuity to reduce the stress terms to $\nu\nabla^2u$.
> - **Common mistakes:** claiming boundary-layer effects in an Euler solution; letting the rotation part of the velocity gradient generate stress.
> - **Practise:** [[#Worked example: plane Poiseuille flow]] · [[SESA2029 CFD Worked Examples#Q10: Expand the index-notation Navier–Stokes equations|CFD worked examples Q10]]

So far the module has used made-up model equations: the heat equation, the convection equation, $df/dt=\lambda f$. This lecture derives the equations Fluent actually solves, in the form that the finite volume method of [[SESA2029 A9 - Finite Volume Method|A9]] will preserve (2025-10-24, ll. 1–20).

Take a small box fixed in space. Whatever is inside, mass, momentum or energy, can only change because some is carried in or out through the faces or because forces act on the faces. The difference between the flux leaving one face and entering the opposite face is a derivative times the box size, and once that is divided by the volume, the conservation law becomes a partial differential equation. Viscosity enters only through the forces, as stresses on the faces, and the remaining job is to say how those stresses depend on the motion.

## 1. Conservation laws in words

For a fixed control volume (CV) surrounded by a control surface (CS), everything is moved to the left so the three laws share a form (ll. 21–60):

- **Mass:** rate of increase of mass in the CV + net mass flow rate out of the CV = 0.
- **Momentum** (Newton's second law, in each of three directions): rate of increase of momentum in the CV + net momentum flux out = pressure and viscous forces on the CS.
- **Energy:** rate of increase of energy in the CV + net energy flux out = rate of work done on the CS by pressure and viscous forces, plus any heat sources such as conduction.

The conserved quantity is $\phi\in\{\rho,\rho u,\rho v,\rho w,\rho E\}$, where $E$ is the total energy per unit mass, internal energy ($c_vT$ for a calorically perfect gas) plus kinetic (ll. 61–70).

## 2. The generic left-hand side

Take a 2D box $\delta x\times\delta y$ of unit depth (ll. 71–130). It contains $\phi\,\delta x\,\delta y$ of the quantity. Through the left face, $\phi u\,\delta y$ enters per second; through the right face, a distance $\delta x$ away, the first Taylor term gives

$$
\left(\phi u+\frac{\partial(\phi u)}{\partial x}\delta x\right)\delta y
$$

leaving. The next Taylor term is $O(\delta x^2)$ and negligible as the box shrinks. The same holds with $\phi v\,\delta x$ entering at the bottom. The rate of increase plus the net flux out is

$$
\frac{\partial}{\partial t}(\phi\,\delta x\,\delta y)
+\left(\phi u+\frac{\partial(\phi u)}{\partial x}\delta x\right)\delta y-\phi u\,\delta y
+\left(\phi v+\frac{\partial(\phi v)}{\partial y}\delta y\right)\delta x-\phi v\,\delta x .
$$

The $\phi u\,\delta y$ and $\phi v\,\delta x$ terms cancel:

$$
\frac{\partial\phi}{\partial t}\delta x\,\delta y+\frac{\partial(\phi u)}{\partial x}\delta x\,\delta y+\frac{\partial(\phi v)}{\partial y}\delta x\,\delta y .
$$

Divide by $\delta x\,\delta y$ to get the left-hand side per unit volume:

$$
\frac{\partial\phi}{\partial t}+\frac{\partial(\phi u)}{\partial x}+\frac{\partial(\phi v)}{\partial y}.
$$

Deriving it once for $\phi$ saves doing the same job four or five times.

## 3. Mass conservation and incompressibility

Put $\phi=\rho$; the right-hand side is zero because no mass is created (it would not be with chemical reactions, which this module excludes) (ll. 131–140):

$$
\frac{\partial\rho}{\partial t}+\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}=0.
$$

Expand the derivatives of products:

$$
\frac{\partial\rho}{\partial t}+u\frac{\partial\rho}{\partial x}+\rho\frac{\partial u}{\partial x}+v\frac{\partial\rho}{\partial y}+\rho\frac{\partial v}{\partial y}=0.
$$

Group the density derivatives on the left and the velocity derivatives on the right:

$$
\frac{\partial\rho}{\partial t}+u\frac{\partial\rho}{\partial x}+v\frac{\partial\rho}{\partial y}=-\rho\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right).
$$

The left side is the rate of change of density following a fluid element, $D\rho/Dt$; the bracket on the right is the divergence of the velocity, how fast the flow is expanding or compressing (ll. 141–160). Incompressible flow is defined by $D\rho/Dt=0$: a fluid particle travelling round an aerofoil feels no change in density. The right side must then vanish too, leaving the divergence-free condition

$$
\boxed{\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0}
$$

(ll. 161–175). Following a particle is the Lagrangian view, like walking round campus with a thermometer and noticing changes; the CFD grid sits in the fixed Eulerian frame, and $D/Dt$ connects the two (ll. 176–195; [[SESA1016 T9 - Describing Flow and the Material Derivative]]).

The consequence for CFD is that incompressible flow has no equation for density, so a density-based method has nothing to march: Fluent must be set to pressure-based, and continuity becomes a constraint on the velocity ([[Pressure-Velocity Coupling and SIMPLE]]; ll. 196–205).

## 4. Momentum without viscosity: the Euler equations

Put $\phi=\rho u$ and find the pressure force in $x$ (ll. 206–230). Pressure $p$ pushes on the left face with force $p\,\delta y$, and $p+(\partial p/\partial x)\delta x$ pushes back on the right face:

$$
p\,\delta y-\left(p+\frac{\partial p}{\partial x}\delta x\right)\delta y=-\frac{\partial p}{\partial x}\delta x\,\delta y .
$$

Per unit volume that is $-\partial p/\partial x$, so the general (compressible) Euler $x$-momentum equation is

$$
\frac{\partial(\rho u)}{\partial t}+\frac{\partial(\rho uu)}{\partial x}+\frac{\partial(\rho uv)}{\partial y}=-\frac{\partial p}{\partial x}.
$$

If $\rho$ is constant everywhere, a good approximation for flow past a low-speed aircraft, divide through by it. With $\phi=\rho v$ the $y$ equation follows the same way. The incompressible Euler equations are

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0,
$$

$$
\frac{\partial u}{\partial t}+\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}=-\frac1\rho\frac{\partial p}{\partial x},
$$

$$
\frac{\partial v}{\partial t}+\frac{\partial(uv)}{\partial x}+\frac{\partial(vv)}{\partial y}=-\frac1\rho\frac{\partial p}{\partial y}.
$$

Three equations in $u$, $v$ and $p$: a closed set, with no energy equation needed (ll. 231–255). A temperature equation could still be solved, but it would be decoupled: it uses the velocities and has no effect back on $u$, $v$ or $p$. In 3D the pattern fills in, with a $w$ equation and $\partial(\cdot\,w)/\partial z$ terms. These are the equations the wing coursework solves, and since there is no viscosity there is no no-slip condition and no boundary layer (ll. 236–245).

### Conservation and non-conservation forms

Expand the convective terms of the $x$ equation (ll. 256–275):

$$
\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}
=u\frac{\partial u}{\partial x}+u\frac{\partial u}{\partial x}+u\frac{\partial v}{\partial y}+v\frac{\partial u}{\partial y}.
$$

Regroup, pairing the first and last terms and factoring $u$ from the middle two:

$$
=u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+u\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right).
$$

The bracket is zero by continuity:

$$
\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}=u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}.
$$

The right side is the non-conservation form, simpler for pen-and-paper work and the one most fluid mechanics textbooks use. CFD keeps the conservation form, with everything inside a derivative, because integrating a derivative leaves only end-point values (ll. 276–295). The finite volume method mirrors that: every flux leaving one cell enters its neighbour, so no mass, momentum or energy is lost from the calculation ([[Conservation Form of the Governing Equations]]).

## 5. Viscous stresses

The CFD does not compute individual molecules, but their motion in a non-uniform flow carries momentum, and on average that appears as internal stresses, which is where viscosity comes from (ll. 300–310). On the $x$-faces a normal stress $\sigma_{xx}$ pulls the fluid apart, as in solid mechanics; on the $y$-faces a shear stress $\sigma_{xy}$ acts. Repeating the face-by-face bookkeeping, the undifferentiated parts cancel and the net viscous force per unit volume in $x$ is

$$
\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}
$$

(ll. 311–330). The system is not closed until the stresses are related to the velocity, and the model will be stress proportional to strain rate, the fluid version of Hooke's law (ll. 331–340).

### Strain and rotation

A fluid element can distort in four ways in 2D (nine in 3D), one for each velocity derivative (ll. 341–350). For the simple shear flow $u=ky$, $v=0$, only $\partial u/\partial y=k$ is non-zero. Split the velocity-gradient matrix into a symmetric part and an antisymmetric part by adding and subtracting half of $k$:

$$
\begin{pmatrix}0&k\\0&0\end{pmatrix}
=\begin{pmatrix}0&k/2\\k/2&0\end{pmatrix}
+\begin{pmatrix}0&k/2\\-k/2&0\end{pmatrix}.
$$

The symmetric matrix is strain; the antisymmetric one is solid-body rotation (ll. 351–370). Rotating a lump of fluid rigidly does not distort it, so rotation generates no stress; straining it does. In pictures, shear turns a square element into a parallelogram, which is the same as stretching it at 45° and then rotating it back so the base is horizontal (ll. 371–385).

In general the symmetric part is half the matrix plus its transpose and the antisymmetric part half the matrix minus its transpose (ll. 386–395):

$$
\begin{pmatrix}u_x&u_y\\v_x&v_y\end{pmatrix}
=\underbrace{\begin{pmatrix}u_x&\tfrac12(u_y+v_x)\\\tfrac12(u_y+v_x)&v_y\end{pmatrix}}_{\text{strain rate}}
+\underbrace{\begin{pmatrix}0&\tfrac12(u_y-v_x)\\-\tfrac12(u_y-v_x)&0\end{pmatrix}}_{\text{rotation rate}}.
$$

The rotation part contains the vorticity $\omega_z=\partial v/\partial x-\partial u/\partial y$, the curl of the velocity.

> [!warning] Lecture slip (2025-10-24, ll. 391–395)
> The vorticity is read off as "du by dy minus dv dx". That is minus $\omega_z$: with the usual right-handed convention $\omega_z=\partial v/\partial x-\partial u/\partial y$, so the shear flow $u=ky$ has $\omega_z=-k$, clockwise rotation. The sign does not matter for the stresses, which come only from the strain part.

### The Newtonian fluid

A Newtonian fluid has stress proportional to strain rate, with constant of proportionality $2\mu$ (ll. 411–420):

$$
\begin{pmatrix}\sigma_{xx}&\sigma_{xy}\\\sigma_{yx}&\sigma_{yy}\end{pmatrix}
=2\mu\begin{pmatrix}u_x&\tfrac12(u_y+v_x)\\\tfrac12(u_y+v_x)&v_y\end{pmatrix}.
$$

The factor 2 is there so that simple shear gives back $\sigma_{xy}=\mu\,du/dy$ ([[Newtonian Fluid and Strain-Rate Tensor]]). Substitute into the viscous force, done on the visualiser "so you know there's no tricks" (ll. 421–465):

$$
\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}
=\frac{\partial}{\partial x}\left(2\mu\frac{\partial u}{\partial x}\right)+\frac{\partial}{\partial y}\left(\mu\left(\frac{\partial u}{\partial y}+\frac{\partial v}{\partial x}\right)\right).
$$

With constant $\mu$, expand:

$$
=\mu\left(2\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}+\frac{\partial^2v}{\partial y\,\partial x}\right).
$$

Split one of the $u_{xx}$ terms off and swap the order of differentiation in the last:

$$
=\mu\left(\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\right)+\mu\frac{\partial}{\partial x}\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right).
$$

The last bracket is zero by continuity:

$$
\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}=\mu\left(\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\right).
$$

After dividing the momentum equation by $\rho$, the coefficient becomes the kinematic viscosity $\nu=\mu/\rho$, in m²/s.

## 6. The incompressible Navier–Stokes equations

$$
\boxed{\begin{aligned}
&\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0\\
&\frac{\partial u}{\partial t}+\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}+\frac1\rho\frac{\partial p}{\partial x}=\nu\left(\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\right)\\
&\frac{\partial v}{\partial t}+\frac{\partial(uv)}{\partial x}+\frac{\partial(vv)}{\partial y}+\frac1\rho\frac{\partial p}{\partial y}=\nu\left(\frac{\partial^2v}{\partial x^2}+\frac{\partial^2v}{\partial y^2}\right)
\end{aligned}}
$$

Three equations, three unknowns $u$, $v$, $p$: a closed set, solvable "even if it takes us a million elements" (ll. 471–490). In 3D add the $w$ equation, $\partial(uw)/\partial z$ terms and $\partial^2/\partial z^2$ terms by the same pattern.

Two compact notations are in common use (ll. 501–545). The subscript or Einstein notation, where an index repeated in a term is summed over 1, 2, 3, writes all four equations in two lines:

$$
\frac{\partial u_i}{\partial x_i}=0,
\qquad
\frac{\partial u_i}{\partial t}+\frac{\partial(u_iu_j)}{\partial x_j}+\frac1\rho\frac{\partial p}{\partial x_i}=\nu\frac{\partial^2u_i}{\partial x_j\,\partial x_j}.
$$

For $i=1$ the convective term expands to $\partial(uu)/\partial x+\partial(uv)/\partial y+\partial(uw)/\partial z$ and the viscous term to $u_{xx}+u_{yy}+u_{zz}$; $i=2$ and $i=3$ give the $v$ and $w$ equations. Most research papers use this form. The vector form,

$$
\nabla\cdot\mathbf u=0,
\qquad
\frac{\partial\mathbf u}{\partial t}+\mathbf u\cdot\nabla\mathbf u+\frac{\nabla p}{\rho}=\nu\nabla^2\mathbf u,
$$

is the one Navier and Stokes would have recognised, and it is the convenient one for changing coordinates: look up $\nabla\cdot\mathbf u$ in cylindrical polars and the equations follow. The compressible equations with energy come in SESA3029.

### What you need to know

At the end of the lecture Prof Sandham listed what is examinable (ll. 545–569): the difference between compressible and incompressible flow ($D\rho/Dt$ zero or not); the difference between the Euler and Navier–Stokes equations (no viscosity, so no no-slip and no boundary layers, versus viscous terms that produce boundary layers, the source of the Blasius equation of [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation|A6]]); and the definition of a Newtonian fluid. In the coursework, discrepancies in an Euler solution must not be blamed on boundary-layer drag that the model does not contain.

## Worked example: plane Poiseuille flow

Water ($\rho=1000$ kg/m³, $\mu=10^{-3}$ Pa s) flows steadily between plates $h=1$ mm apart, driven by $-\partial p/\partial x=G=100$ Pa/m. Check that $u=\frac{G}{2\mu}y(h-y)$, $v=0$ satisfies the Navier–Stokes equations and find the flow numbers.

Continuity holds, since $u_x=0$ and $v=0$. In the $x$ equation, $\partial_t u=0$, $\partial(uu)/\partial x=0$ and $\partial(uv)/\partial y=0$, so it reduces to

$$
\frac1\rho\frac{\partial p}{\partial x}=\nu\frac{\partial^2u}{\partial y^2}.
$$

Differentiate the profile twice:

$$
\frac{\partial^2u}{\partial y^2}=-\frac{G}{\mu}.
$$

Then the right side is $-G/\rho$ and the left side $-G/\rho$, so the equation holds. The numbers, checked with SymPy:

$$
u_{max}=\frac{Gh^2}{8\mu}=0.0125\text{ m/s},
\qquad
\bar u=\tfrac23u_{max}=0.00833\text{ m/s},
\qquad
\tau_w=\mu\left.\frac{du}{dy}\right|_0=\frac{Gh}{2}=0.05\text{ Pa},
$$

and $Re=\rho\bar uh/\mu=8.3$, comfortably laminar. Here the nonlinear terms vanish identically, which is why this is one of the few exact solutions.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Next: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- Concepts: [[Conservation Form of the Governing Equations]] · [[Navier-Stokes Equations]] · [[Newtonian Fluid and Strain-Rate Tensor]]
- Thermofluids foundation: [[SESA1016 T7 - Fluid Properties and Viscosity]] · [[SESA1016 T9 - Describing Flow and the Material Derivative]] · [[SESA1016 T11 - Conservation of Mass]] · [[SESA1016 T12 - Conservation of Momentum]]
- Finite volumes and solvers: [[SESA2029 A9 - Finite Volume Method]] · [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Longer derivation and a working solver: [[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]]
- Inviscid limit: [[Streamfunction and Velocity Potential]] · [[D'Alembert's Paradox]]

## Sources

- `All_lectures_as_delivered.pdf`, L8, pp. 101–112, with transcript `SESA2029 Lecture 2025-10-24.txt` (Prof N. Sandham)
- Worked example checked with SymPy

## Self-study tasks

### Core

- [ ] Derive the generic left-hand side and the continuity equation for a 2D control volume (2025-10-24, ll. 71–175). → [[#2. The generic left-hand side]] · [[#3. Mass conservation and incompressibility]]
- [ ] Show that the conservation and non-conservation forms of the convective terms are equal for incompressible flow (ll. 256–295). → [[#Conservation and non-conservation forms]]
- [ ] Define a Newtonian fluid and reduce the stress terms to $\nu\nabla^2u$ (ll. 411–465, 545–569). → [[#The Newtonian fluid]]
- [ ] Expand the index-notation equations in 3D (example sheet). → [[SESA2029 CFD Worked Examples#Q10: Expand the index-notation Navier–Stokes equations|Worked examples Q10]]

### Further practice

- [ ] Split other basic flows into strain and rotation, as the end of the example sheet asks (ll. 386–390). → [[#Strain and rotation]]
- [ ] Verify the Poiseuille solution and its numbers. → [[#Worked example: plane Poiseuille flow]]
