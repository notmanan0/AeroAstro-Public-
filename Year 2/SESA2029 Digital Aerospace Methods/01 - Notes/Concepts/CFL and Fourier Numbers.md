---
title: "CFL and Fourier Numbers"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["CFL number", "Courant number", "Fourier number", "viscous CFL", "Courant-Friedrichs-Lewy"]
tags: [sesa2029, concept, numerical-methods, stability]
status: complete
parent_lectures: ["[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]", "[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
related_concepts: ["[[Von Neumann Stability Analysis]]", "[[Explicit and Implicit Time Integration]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L5–L6)", "02 - Sources/CFD/CFD.txt"]
---

# CFL and Fourier Numbers

## Definition

> [!note] Definition
> Dimensionless groups that set the stability of explicit time stepping:
>
> $$C = \mathrm{CFL} = \frac{c\,\Delta t}{h}\ \ (\text{convection}),\qquad F = \frac{\alpha\,\Delta t}{h^2}\ \ (\text{diffusion/heat}),\qquad\mathrm{CFL}_\nu = \frac{\nu\,\Delta t}{h^2}\ \ (\text{viscous})$$

## Explanation

- **CFL** is the number of cells information travels per time step. Explicit upwind (Euler) needs $C\le1$: the numerical domain of dependence must contain the physical one. At $C = 1$ upwind is an exact shift.
- **Fourier number** for FTCS diffusion: $F\le\tfrac12$. Because $\Delta t\propto h^2$, halving the cell size quarters the allowed step, so fine near-wall viscous grids cripple explicit schemes. This is a key reason steady CFD solvers are implicit.
- RK3/RK4 allow somewhat larger CFL numbers and are stable on the imaginary axis (waves).
- Unsteady commercial solvers expose a **Courant number** setting. For time-accurate explicit work keep CFL ≲ 1.

## Examples

- Heat equation with $\alpha = 0.1$ and $h = 0.125$: $\Delta t = 0.07$ gives $F = 0.448$ (stable), while $\Delta t = 0.09$ gives $F = 0.576$ (unstable).
- A flow at $c = 50$ m/s on a 1 mm grid needs $\Delta t\le2\times10^{-5}$ s for $C\le1$.

## Related

- Parent lectures: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]] · [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]
- Related concepts: [[Von Neumann Stability Analysis]] · [[Explicit and Implicit Time Integration]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L5–L6)
- 02 - Sources/CFD/CFD.txt
