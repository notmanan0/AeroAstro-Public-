---
title: "SESA2029 A7 - Governing Equations - Euler and Navier-Stokes"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 7
tags:
  - sesa2029
  - cfd
  - governing-equations
  - navier-stokes
aliases: ["Governing equations for CFD", "Euler equations", "Navier-Stokes derivation"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]"]
next_topics: ["[[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]"]
key_concepts: ["[[Conservation Form of the Governing Equations]]", "[[Navier-Stokes Equations]]", "[[Newtonian Fluid and Strain-Rate Tensor]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L8, pp. 101–112)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A7 - Governing Equations - Euler and Navier-Stokes

> [!abstract] Summary
> Apply "rate of increase inside a control volume + net flux out = sources" to a generic conserved quantity $\phi\in\{\rho,\rho u,\rho v,\rho E\}$. This gives mass, momentum and energy conservation in **conservation (divergence) form**, which CFD prefers because it discretises into schemes that conserve exactly.
>
> - **Incompressible** flow has zero density change following a fluid element, so $\nabla\cdot\mathbf u = 0$. The **Euler** equations ($u,v,p$; no viscosity) are then already closed without an energy equation.
> - Adding viscous stresses and a **Newtonian** closure (stress ∝ strain rate, constant $2\mu$) gives the **Navier–Stokes** equations.
> - Consequence for CFD: incompressible flow has no density equation, so it needs **pressure-based** solvers.

## Key Concepts
- [[Conservation Form of the Governing Equations]] · [[Navier-Stokes Equations]] · [[Newtonian Fluid and Strain-Rate Tensor]]

---

## 1. Conservation laws in words (L8)
For a fixed control volume (CV) with control surface (CS):
1. **Mass**: rate of increase of mass in the CV + net mass flow rate out = 0.
2. **Momentum** (Newton II, three components): rate of increase of momentum in the CV + net momentum flux out = pressure and viscous forces on the CS.
3. **Energy**: rate of increase of energy in the CV + net energy flux out = work done on the CS by pressure and viscous forces + heat input.

Here $E$ is internal plus kinetic energy per unit mass.

## 2. The generic left-hand side (L8)
Take a 2D box $\delta x\times\delta y$ (unit depth) containing $\phi\,\delta x\delta y$. The flux in on the left is $\phi u\,\delta y$. Out on the right it is $\left(\phi u+\frac{\partial(\phi u)}{\partial x}\delta x\right)\delta y$ (first Taylor term only, since $\delta x$ is small). The same applies in $y$.

$$
\text{LHS} = \frac{\partial}{\partial t}(\phi\,\delta x\delta y)+\frac{\partial(\phi u)}{\partial x}\delta x\delta y+\frac{\partial(\phi v)}{\partial y}\delta x\delta y\;\Rightarrow\;\frac{\partial\phi}{\partial t}+\frac{\partial(\phi u)}{\partial x}+\frac{\partial(\phi v)}{\partial y}\quad\text{per unit volume}
$$

The $\phi u\,\delta y$ and $\phi v\,\delta x$ terms cancel between opposite faces. Deriving it once for $\phi$ gives every equation.

## 3. Mass conservation (L8)
With $\phi = \rho$ and RHS $= 0$:

$$
\frac{\partial\rho}{\partial t}+\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y} = 0
$$

Expanding the products:

$$
\underbrace{\frac{\partial\rho}{\partial t}+u\frac{\partial\rho}{\partial x}+v\frac{\partial\rho}{\partial y}}_{D\rho/Dt\text{ (following a fluid element)}} = -\rho\underbrace{\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right)}_{\text{divergence of velocity}}
$$

**Incompressible** means $D\rho/Dt = 0$: an observer riding on a fluid particle (the **Lagrangian** view) sees no density change. Therefore

$$
\boxed{\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y} = 0}\qquad\text{(divergence-free / continuity)}
$$

CFD itself works in the fixed (Eulerian) frame. The material derivative $D/Dt$ links the two viewpoints.

> [!important] CFD consequence
> In incompressible flow there is no equation to march density. So there is no "density-based" method; continuity becomes a **constraint** on the velocity. You need **pressure-based** methods such as SIMPLE, SIMPLEC or PISO ([[Pressure-Velocity Coupling and SIMPLE]]).

## 4. Momentum: the Euler equations (L8)
With $\phi = \rho u$: the net pressure force in $x$ per unit volume is $\left[p\,\delta y-\left(p+\frac{\partial p}{\partial x}\delta x\right)\delta y\right]/(\delta x\delta y) = -\partial p/\partial x$.

$$
\frac{\partial(\rho u)}{\partial t}+\frac{\partial(\rho uu)}{\partial x}+\frac{\partial(\rho uv)}{\partial y} = -\frac{\partial p}{\partial x}\qquad\text{(general Euler }x\text{-momentum)}
$$

**Incompressible Euler equations**: three equations in $u, v, p$, closed with no energy equation.

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y} = 0,\qquad
\frac{\partial u}{\partial t}+\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y} = -\frac1\rho\frac{\partial p}{\partial x},\qquad
\frac{\partial v}{\partial t}+\frac{\partial(uv)}{\partial x}+\frac{\partial(vv)}{\partial y} = -\frac1\rho\frac{\partial p}{\partial y}
$$

A temperature equation could still be solved, but it would be one-way coupled: it uses $u$ and $v$ without affecting them.

**Conservation vs non-conservation form.** Using continuity,

$$
\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y} = u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}+u\underbrace{\left(\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}\right)}_{=0}
$$

Textbooks favour the non-conservation form $u\,u_x+v\,u_y$. CFD keeps everything **inside a derivative**, because integrating a derivative leaves only end-point (face) values. Every flux leaving one cell then enters its neighbour, so mass, momentum and energy are conserved exactly over the whole grid ([[Finite Volume Method]]).

> [!warning] The Euler equations have no viscosity
> So they cannot satisfy no-slip and there are **no boundary layers**. An Euler wing calculation has no skin friction and no viscous separation. Differences from experiment in drag or stall must not be attributed to boundary-layer physics the model does not contain.

## 5. Towards Navier–Stokes: viscous stresses (L8)
Unresolved molecular motion in a non-uniform flow transports momentum, and this appears as internal stresses:
- the **normal** stress $\sigma_{xx}$ on the $x$-faces;
- the **shear** stress $\sigma_{xy}$ on the $y$-faces.

The net viscous force per unit volume in $x$ is $\partial\sigma_{xx}/\partial x+\partial\sigma_{xy}/\partial y$. The system is not yet closed, because we still need $\sigma$ in terms of the velocity.

**Strain vs rotation.** Split the velocity-gradient tensor into symmetric and antisymmetric parts (for example the shear flow $u = ky$):

$$
\begin{pmatrix}u_x&u_y\\v_x&v_y\end{pmatrix} = \underbrace{\begin{pmatrix}u_x&\tfrac12(u_y+v_x)\\\tfrac12(u_y+v_x)&v_y\end{pmatrix}}_{\text{strain rate}}+\underbrace{\begin{pmatrix}0&\tfrac12(u_y-v_x)\\-\tfrac12(u_y-v_x)&0\end{pmatrix}}_{\text{solid-body rotation}}
$$

A shear flow turns a square element into a parallelogram. That is **plane strain** (stretched at 45°) **plus rigid rotation**. Only the strain generates stress; spinning a lump of fluid rigidly does not. The rotation part contains the **vorticity** $\omega_z = v_x-u_y$, the curl of the velocity.

**Newtonian fluid**: stress is proportional to strain rate, the fluid analogue of Hooke's law:

$$
\begin{pmatrix}\sigma_{xx}&\sigma_{xy}\\\sigma_{yx}&\sigma_{yy}\end{pmatrix} = 2\mu\begin{pmatrix}u_x&\tfrac12(u_y+v_x)\\\tfrac12(u_y+v_x)&v_y\end{pmatrix}
$$

The factor $2\mu$ is chosen so that $\sigma_{xy} = \mu\,du/dy$ in simple shear. See [[Newtonian Fluid and Strain-Rate Tensor]].

Substituting and using continuity:

$$
\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y} = \mu\left(2u_{xx}+u_{yy}+v_{xy}\right) = \mu\left(u_{xx}+u_{yy}\right)+\mu\frac{\partial}{\partial x}\underbrace{(u_x+v_y)}_{0}
$$

## 6. Incompressible Navier–Stokes equations (L8)
$$
\boxed{\begin{aligned}
&\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y} = 0\\
&\frac{\partial u}{\partial t}+\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}+\frac1\rho\frac{\partial p}{\partial x} = \nu\left(\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\right)\\
&\frac{\partial v}{\partial t}+\frac{\partial(uv)}{\partial x}+\frac{\partial(vv)}{\partial y}+\frac1\rho\frac{\partial p}{\partial y} = \nu\left(\frac{\partial^2v}{\partial x^2}+\frac{\partial^2v}{\partial y^2}\right)
\end{aligned}}\qquad\nu = \frac\mu\rho
$$

These are nonlinear PDEs: three equations in $u, v, p$, closed. In 3D add $w$, $\partial(uw)/\partial z$ and $\partial^2/\partial z^2$ terms, following the obvious pattern.

**Subscript (Einstein) notation**, with repeated indices summed over 1–3:

$$
\frac{\partial u_i}{\partial x_i} = 0,\qquad\frac{\partial u_i}{\partial t}+\frac{\partial(u_iu_j)}{\partial x_j}+\frac1\rho\frac{\partial p}{\partial x_i} = \nu\frac{\partial^2u_i}{\partial x_j\partial x_j}
$$

**Vector form** (convenient in cylindrical or spherical coordinates):

$$
\nabla\cdot\mathbf u = 0,\qquad\frac{\partial\mathbf u}{\partial t}+\mathbf u\cdot\nabla\mathbf u+\frac{\nabla p}{\rho} = \nu\nabla^2\mathbf u
$$

> [!example] Expanding the subscript form (exam skill)
> For $i = 1$ ($x$-momentum), $\partial(u_1u_j)/\partial x_j = \partial(uu)/\partial x+\partial(uv)/\partial y+\partial(uw)/\partial z$ and $\partial^2u_1/\partial x_j\partial x_j = u_{xx}+u_{yy}+u_{zz}$.
>
> For $i = 2$, replace the leading $u$ by $v$ and $\partial p/\partial x$ by $\partial p/\partial y$. The single subscript equation stands for 3 momentum equations and 9 flux terms.

## 7. Need-to-know checklist (L8)
- **Compressible vs incompressible**: whether $D\rho/Dt = 0$, i.e. whether $\nabla\cdot\mathbf u = 0$.
- **Euler vs Navier–Stokes**: no viscous terms, so slip walls and no boundary layers, versus viscous terms with no-slip and boundary layers.
- **Newtonian fluid**: stress linear in strain rate, with constant $2\mu$.
- Explain the CV conservation laws in words, and expand the 3D subscript form.
- Compressible NSE with the energy equation: SESA3029 and SESA6082.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]] · Next: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- Thermofluids foundation: [[SESA1016 T7 - Fluid Properties and Viscosity]] · [[SESA1016 T9 - Describing Flow and the Material Derivative]] · [[SESA1016 T11 - Conservation of Mass]] · [[SESA1016 T12 - Conservation of Momentum]]
- Integral form and finite volumes: [[SESA2029 A9 - Finite Volume Method]] · Solvers: [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Full derivation from first principles, term-by-term discretisation and a working solver: [[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]]
- Potential flow is the irrotational, inviscid limit: [[Streamfunction and Velocity Potential]] · [[D'Alembert's Paradox]]

## Sources
- CFD Lecture 8, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 101–112; transcript `CFD.txt`
