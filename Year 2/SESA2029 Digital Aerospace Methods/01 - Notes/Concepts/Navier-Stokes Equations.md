---
title: "Navier-Stokes Equations"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["NSE", "incompressible Navier-Stokes", "Euler equations", "Euler vs Navier-Stokes"]
tags: [sesa2029, concept, governing-equations, navier-stokes]
status: complete
parent_lectures: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
related_concepts: ["[[Conservation Form of the Governing Equations]]", "[[Newtonian Fluid and Strain-Rate Tensor]]", "[[Reynolds Averaging and the Closure Problem]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L8)", "02 - Sources/CFD/CFD.txt"]
---

# Navier-Stokes Equations

## Definition

> [!note] Definition
> The conservation laws of mass and momentum for a Newtonian viscous fluid. For incompressible flow (index notation, summed over $j$):
>
> $$\frac{\partial u_i}{\partial x_i} = 0,\qquad\frac{\partial u_i}{\partial t}+\frac{\partial(u_iu_j)}{\partial x_j}+\frac1\rho\frac{\partial p}{\partial x_i} = \nu\frac{\partial^2u_i}{\partial x_j\partial x_j}$$
>
> Dropping the viscous term gives the **Euler equations**.

## Explanation

- **Incompressible** means $D\rho/Dt = 0$ following a fluid element, so $\nabla\cdot\mathbf u = 0$. Then $u, v, (w), p$ form a closed set without an energy equation. Continuity is a *constraint*, which leads to pressure-based solvers ([[Pressure-Velocity Coupling and SIMPLE]]).
- **Euler vs NS**: Euler has no viscosity, so it cannot satisfy no-slip. There are no boundary layers, skin friction or viscous separation. NS includes $\nu\nabla^2\mathbf u$ and does.
- **Vector form**: $\nabla\cdot\mathbf u = 0$, $\mathbf u_t+\mathbf u\cdot\nabla\mathbf u+\nabla p/\rho = \nu\nabla^2\mathbf u$. It is convenient for other coordinate systems.
- The equations are nonlinear, via the convective term $\partial(u_iu_j)/\partial x_j$. That nonlinearity is the origin of turbulence and of the closure problem in RANS.
- Compressible NS adds the energy equation and an equation of state (SESA3029, SESA6082).

## Examples

- Expanding the $i = 1$ equation in 3D gives $u_t+(uu)_x+(uv)_y+(uw)_z+p_x/\rho = \nu(u_{xx}+u_{yy}+u_{zz})$.
- The Blasius equation is a similarity reduction of the NS boundary-layer equations ([[Shooting Method and the Blasius Solution]]).

## Related

- Parent lectures: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Deep dive (derivation → discretisation → solver): [[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]]
- Related concepts: [[Conservation Form of the Governing Equations]] · [[Newtonian Fluid and Strain-Rate Tensor]] · [[Reynolds Averaging and the Closure Problem]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L8)
- 02 - Sources/CFD/CFD.txt
