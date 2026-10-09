---
title: "Conservation Form of the Governing Equations"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["conservation form", "divergence form", "integral form", "control volume form"]
tags: [sesa2029, concept, governing-equations]
status: complete
parent_lectures: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]", "[[SESA2029 A9 - Finite Volume Method]]"]
related_concepts: ["[[Navier-Stokes Equations]]", "[[Finite Volume Method]]", "[[Newtonian Fluid and Strain-Rate Tensor]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L8, L10)", "02 - Sources/CFD/CFD.txt"]
---

# Conservation Form of the Governing Equations

## Definition

> [!note] Definition
> Writing a conservation law so that every flux term sits **inside** a spatial derivative:
>
> $$\frac{\partial\phi}{\partial t}+\frac{\partial(\phi u)}{\partial x}+\frac{\partial(\phi v)}{\partial y} = \text{sources},\qquad\text{or integrally}\quad\frac{\partial}{\partial t}\int_V\phi\,dV+\oint_S\phi\,\mathbf v\cdot\mathbf n\,dS = \text{sources}$$
>
> with $\phi\in\{\rho,\rho u,\rho v,\rho E\}$.

## Explanation

- **Derivation**: rate of increase of $\phi$ in a small control volume + net flux out = forces and sources. Only the first Taylor term across the cell is needed. One derivation gives mass ($\phi = \rho$), momentum ($\rho u$, $\rho v$) and energy ($\rho E$).
- **Why CFD prefers it**: integrating a derivative leaves only boundary (face) values, so each face flux leaving a cell enters its neighbour. The discrete scheme then conserves mass, momentum and energy **exactly** over the whole domain. This also aids stability and gives correct shock jumps in compressible flow.
- **Non-conservation form**, e.g. $u\,u_x+v\,u_y$, is algebraically equivalent (via continuity) and common in textbooks, but it does not guarantee discrete conservation.
- Gauss's divergence theorem links the integral (finite-volume) form to the differential (finite-difference) form.

## Examples

- The incompressible $x$-momentum conservation form $u_t+(uu)_x+(uv)_y = -p_x/\rho+\nu\nabla^2u$ becomes $u_t+uu_x+vu_y = \dots$ after using $u_x+v_y = 0$.

## Related

- Parent lectures: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[SESA2029 A9 - Finite Volume Method]]
- Related concepts: [[Navier-Stokes Equations]] · [[Finite Volume Method]] · [[Newtonian Fluid and Strain-Rate Tensor]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L8, L10)
- 02 - Sources/CFD/CFD.txt
