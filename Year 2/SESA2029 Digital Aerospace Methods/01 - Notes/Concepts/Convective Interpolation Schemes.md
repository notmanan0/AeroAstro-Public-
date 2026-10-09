---
title: "Convective Interpolation Schemes"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["upwind differencing", "UDS", "CDS", "QUICK", "second-order upwind", "numerical diffusion"]
tags: [sesa2029, concept, finite-volume, numerical-methods]
status: complete
parent_lectures: ["[[SESA2029 A9 - Finite Volume Method]]"]
related_concepts: ["[[Finite Volume Method]]", "[[Finite Difference Approximations]]", "[[Von Neumann Stability Analysis]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L10)", "02 - Sources/CFD/CFD.txt"]
---

# Convective Interpolation Schemes

## Definition

> [!note] Definition
> Rules for estimating a cell-face value $\phi_e$ from nodal values when evaluating convective fluxes in a finite-volume scheme:
> - **upwind (UDS)**: $\phi_e = \phi_P$ if $(\mathbf v\cdot\mathbf n)_e>0$, else $\phi_E$;
> - **central (CDS)**: $\phi_e = \lambda_e\phi_E+(1-\lambda_e)\phi_P$;
> - **second-order upwind**: $\phi_e = \tfrac12(3\phi_P-\phi_W)$;
> - **QUICK**: $\phi_e = \tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W$ (uniform grid, flow left to right).

## Explanation

| Scheme | Order | Behaviour |
|---|---|---|
| UDS | 1 | bounded, very stable, **numerically diffusive** (smears gradients) |
| 2nd-order upwind | 2 | linear extrapolation from the two upstream nodes; less diffusive |
| CDS | 2 | direction-independent; **can oscillate** (unbounded) at high cell Péclet number |
| QUICK | 2–3 | parabola through two upstream nodes and one downstream: $\phi_U+g_1(\phi_D-\phi_U)+g_2(\phi_U-\phi_{UU})$ |

- Upwinding follows the physics of convection: information comes from upstream. It is also the stable choice for explicit schemes (von Neumann).
- **Practice**:
  - start with the solver defaults, typically 2nd order for momentum and pressure;
  - drop the turbulence equations to 1st-order upwind if convergence stalls;
  - avoid 1st order for momentum in final results, because it spoils grid convergence.
- The diffusive-flux gradient uses CDS: $(\partial\phi/\partial x)_e\approx(\phi_E-\phi_P)/(x_E-x_P)$.

## Examples

![[dam_advection_upwind_vs_central.png|560]]

- QUICK check on a uniform grid: $g_1 = \tfrac38$ and $g_2 = \tfrac18$, giving $\phi_e = \phi_P+\tfrac38(\phi_E-\phi_P)+\tfrac18(\phi_P-\phi_W)$.

## Related

- Parent lectures: [[SESA2029 A9 - Finite Volume Method]]
- Related concepts: [[Finite Volume Method]] · [[Finite Difference Approximations]] · [[Von Neumann Stability Analysis]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L10)
- 02 - Sources/CFD/CFD.txt
