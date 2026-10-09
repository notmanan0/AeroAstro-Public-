---
title: "First-Cell Height and y-plus"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["y+", "y plus", "y1+", "first cell height", "wall function", "inflation layer"]
tags: [sesa2029, concept, turbulence, meshing, boundary-layers]
status: complete
parent_lectures: ["[[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]", "[[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]"]
related_concepts: ["[[Eddy-Viscosity Turbulence Models]]", "[[Law of the Wall]]", "[[Structured, Unstructured and Hybrid Grids]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L2, L9)", "02 - Sources/CFD/CFD.txt"]
---

# First-Cell Height and y-plus

## Definition

> [!note] Definition
> The wall distance of the first cell centre, expressed in wall units:
>
> $$y_1^+ = \frac{y_1u_\tau}{\nu},\qquad u_\tau = \sqrt{\tau_w/\rho}$$
>
> It decides whether the grid **resolves** the viscous sublayer ($y_1^+\lesssim1$–5) or relies on a **wall function** in the log layer ($30<y_1^+\lesssim200$).

## Explanation

**Sizing procedure (before meshing)**:
1. Estimate $Re_x$ and a flat-plate skin friction:
   - laminar: $C_f = 0.664Re_x^{-1/2}$;
   - turbulent: $C_f = 0.059Re_x^{-1/5}$.
2. Compute $\tau_w = \tfrac12C_f\rho U_\infty^2$, then $u_\tau = \sqrt{\tau_w/\rho}$.
3. Choose a target $y_1^+$ (from the model: SA < 5, SST ≈ 1, $k$–$\varepsilon$ with wall functions > 30).
4. Set $y_1 = y_1^+\nu/u_\tau$.
5. Grow the inflation layers gradually (ratio ≈ 1.1–1.2) to get **10–20 cells** across $\delta$ (laminar $4.91xRe_x^{-1/2}$; turbulent $0.38xRe_x^{-1/5}$).
6. **After solving**, plot the actual $y_1^+$ and adjust the grid.

**Avoid the buffer layer** ($8\lesssim y_1^+\lesssim30$): neither the sublayer assumption nor the log law holds there. Too large a $y_1^+$ (≳ 200–300) leaves too few cells inside the boundary layer.

## Examples

- Air at 30 m/s, $x = 1$ m, $\nu = 1.5\times10^{-5}$: $C_f = 0.00324$, $u_\tau = 1.21$ m/s, so $y_1\approx12\,\mu$m for $y_1^+ = 1$, inside a boundary layer about 21 mm thick.

![[dam_law_of_the_wall_y1plus.png|560]]

## Related

- Parent lectures: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] · [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]
- Related concepts: [[Eddy-Viscosity Turbulence Models]] · [[Law of the Wall]] · [[Structured, Unstructured and Hybrid Grids]]
- Wall-unit physics and constants: [[Law of the Wall]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L2, L9)
- 02 - Sources/CFD/CFD.txt
