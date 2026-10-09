---
title: "Reynolds Averaging and the Closure Problem"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["RANS", "Reynolds decomposition", "Reynolds stresses", "turbulence closure problem"]
tags: [sesa2029, concept, turbulence, rans]
status: complete
parent_lectures: ["[[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]"]
related_concepts: ["[[Eddy-Viscosity Turbulence Models]]", "[[Navier-Stokes Equations]]", "[[First-Cell Height and y-plus]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L9)", "02 - Sources/CFD/CFD.txt"]
---

# Reynolds Averaging and the Closure Problem

## Definition

> [!note] Definition
> Split each flow variable into a time mean and a fluctuation, $\phi = \bar\phi+\phi'$, with
>
> $$\bar\phi = \lim_{T\to\infty}\frac1T\int_0^T\phi\,dt$$
>
> Averaging the Navier–Stokes equations produces the **RANS** equations. These contain extra unknowns, the **Reynolds stresses** $-\rho\overline{u_i'u_j'}$. There are more unknowns than equations, and this **closure problem** cannot be removed by deriving further equations.

## Explanation

- **Rules**: $\overline{\phi'} = 0$, $\overline{\bar\phi\psi'} = 0$, and averaging commutes with differentiation. But $\overline{\phi'\psi'}\neq0$ because turbulent fluctuations are correlated.
- Averaging the convective term $\partial(uv)/\partial y$ gives $\partial(\bar u\bar v)/\partial y+\partial\overline{u'v'}/\partial y$. The second term is new.
- In 3D there are **6** independent Reynolds stresses (the tensor is symmetric). Continuity + 3 momentum equations = 4 equations for 10 unknowns.
- Equations for the stresses contain triple correlations, whose equations contain quadruple ones, and so on. The hierarchy never closes, so a **model** is required. This is why turbulence is unsolved in principle, and why CFD needs expert users.
- The averaging interval $T$ must be long compared with the eddy time scale. Spatial averaging in a homogeneous direction is also used.

## Examples

![[dam_reynolds_decomposition.png|560]]

- In a boundary layer the dominant stress is $-\rho\overline{u'v'}$: fluctuations transport momentum towards the wall, which makes turbulent profiles fuller and turbulent skin friction higher than laminar.

## Related

- Parent lectures: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- Related concepts: [[Eddy-Viscosity Turbulence Models]] · [[Navier-Stokes Equations]] · [[First-Cell Height and y-plus]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L9)
- 02 - Sources/CFD/CFD.txt
