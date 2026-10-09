---
title: "Newtonian Fluid and Strain-Rate Tensor"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["Newtonian fluid", "strain rate", "rotation tensor", "vorticity", "viscous stress"]
tags: [sesa2029, concept, governing-equations]
status: complete
parent_lectures: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
related_concepts: ["[[Navier-Stokes Equations]]", "[[Eddy-Viscosity Turbulence Models]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L8)", "02 - Sources/CFD/CFD.txt"]
---

# Newtonian Fluid and Strain-Rate Tensor

## Definition

> [!note] Definition
> A **Newtonian fluid** has internal (viscous) stress proportional to the **strain rate** only:
>
> $$\sigma_{ij} = 2\mu S_{ij},\qquad S_{ij} = \tfrac12\left(\frac{\partial u_i}{\partial x_j}+\frac{\partial u_j}{\partial x_i}\right)$$
>
> (plus pressure, and a bulk term if compressible). It is the fluid analogue of Hooke's law.

## Explanation

- Split the velocity-gradient tensor $\partial u_i/\partial x_j$ into a **symmetric** part (the strain rate, which deforms elements) and an **antisymmetric** part (solid-body rotation, containing the vorticity $\omega_z = v_x-u_y$). Rigid rotation produces no stress, so only $S_{ij}$ appears.
- **Simple shear** $u = ky$ = plane strain at 45° + rigid rotation. The factor $2\mu$ makes $\sigma_{xy} = \mu\,du/dy$ there.
- Substituting into momentum and using continuity gives the viscous term $\nu\nabla^2u_i$, with $\nu = \mu/\rho$ the kinematic viscosity.
- RANS models borrow the same idea: the **eddy viscosity** relates Reynolds stresses to the mean strain rate ([[Eddy-Viscosity Turbulence Models]]).

## Examples

- For $u = ky$ and $v = 0$: $\partial u/\partial y = k$, so $S_{xy} = k/2$ and $\sigma_{xy} = \mu k$. The rotation part $\tfrac12(u_y-v_x) = k/2$ produces no stress.

## Related

- Parent lectures: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Related concepts: [[Navier-Stokes Equations]] · [[Eddy-Viscosity Turbulence Models]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L8)
- 02 - Sources/CFD/CFD.txt
