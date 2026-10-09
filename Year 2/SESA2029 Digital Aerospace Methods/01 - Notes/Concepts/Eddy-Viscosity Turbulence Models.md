---
title: "Eddy-Viscosity Turbulence Models"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["eddy viscosity", "Spalart-Allmaras", "k-epsilon", "k-omega", "SST", "Reynolds stress model", "turbulence models"]
tags: [sesa2029, concept, turbulence, rans]
status: complete
parent_lectures: ["[[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]"]
related_concepts: ["[[Reynolds Averaging and the Closure Problem]]", "[[First-Cell Height and y-plus]]", "[[Newtonian Fluid and Strain-Rate Tensor]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L9)", "02 - Sources/CFD/CFD.txt", "NASA Langley Turbulence Modeling Resource"]
---

# Eddy-Viscosity Turbulence Models

## Definition

> [!note] Definition
> Models that close RANS by relating the Reynolds stresses to the mean strain rate through a **turbulent (eddy) viscosity** $\nu_t$. For a boundary layer:
> $$-\overline{u'v'} = \nu_t\frac{\partial\bar u}{\partial y}$$
> The model then supplies $\nu_t$ from one or two extra transport equations.

## Explanation

| Model | Extra equations | $\nu_t$ | Use | Near-wall $y_1^+$ |
|---|---|---|---|---|
| Spalart–Allmaras | 1 ($\tilde\nu$) | from $\tilde\nu$ | external aero, attached flow, separation location; robust and cheap | < 5 (wall-function variants > 30) |
| $k$–$\varepsilon$ | 2 | $C_\mu k^2/\varepsilon$, $C_\mu = 0.09$ | general engineering; free-stream insensitive; poor with adverse pressure gradients and separation | > 30 (wall functions) |
| $k$–$\omega$ | 2 | $k/\omega$ | boundary layers with pressure gradient and separation; free-stream sensitive | ≈ 1 |
| SST | 2 | blended | $k$–$\omega$ near the wall + $k$–$\varepsilon$ outside; the most-developed 2-equation model | ≈ 1 |
| Reynolds stress | 7 | none (stresses solved directly) | swirl, strong curvature; expensive, can be unstable | wall-resolved |

- $k = \tfrac12\overline{u_i'u_i'}$ is the turbulence kinetic energy, $\varepsilon$ is its dissipation rate, and $\omega\propto\varepsilon/k$.
- **Never retune the constants**: they are calibrated as a set against canonical flows.
- Different models give different answers for the same flow. Turbulence and transition modelling are the largest physical uncertainties in aerodynamic CFD.

## Examples

- For a wing at cruise, choose SA or $k$–$\omega$ SST with a wall-resolved grid ($y_1^+\approx1$). For a quick industrial estimate on a coarse wall grid, use $k$–$\varepsilon$ with wall functions ($y_1^+>30$).

## Related

- Parent lectures: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- Related concepts: [[Reynolds Averaging and the Closure Problem]] · [[First-Cell Height and y-plus]] · [[Newtonian Fluid and Strain-Rate Tensor]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L9)
- 02 - Sources/CFD/CFD.txt
- NASA Langley Turbulence Modeling Resource
