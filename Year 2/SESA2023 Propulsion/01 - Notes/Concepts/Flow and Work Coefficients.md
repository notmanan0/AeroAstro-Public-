---
title: "Flow and Work Coefficients"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["flow coefficient", "stage loading coefficient", "work coefficient", "phi", "psi", "Smith chart", "number of stages"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Euler Work Equation]]", "[[Velocity Triangles]]", "[[Dimensional Analysis of Turbomachines]]", "[[Specific Speed]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---
# Flow and Work Coefficients

## Definition

> [!note] Definition
>
> $$\phi = \frac{V_x}{U}\ (\text{flow coefficient}),\qquad\psi = \frac{|\Delta h_0|}{U^2} = \frac{\Delta V_\theta}{U}\ (\text{stage loading / work coefficient})$$

## Explanation
- **$\phi$ and incidence**: $\phi$ fixes the relative inlet angle.
  - At the *design* stage, low $\phi$ means highly staggered blades and high $\phi$ means low stagger.
  - For a *built* blade, $\phi$ below design means positive incidence (towards stall/surge), and above design means negative incidence (towards choke).
  - A machine therefore runs efficiently only in a **narrow $\phi$ band**. Multistage compressors keep $V_x$ about constant by shrinking the blade height as density rises.
- **$\psi$ and turning**:
  - High $\psi$ means more flow turning, so fewer stages (lower cost, weight and complexity) but lower efficiency.
  - Compressor limit $\psi\le0.65$ (typically 0.35–0.5), set by boundary-layer separation and stall.
  - Turbine limit $\psi\le2.5$, set by high Mach numbers and shock losses.
- **Number of stages**: $n\ge\Delta h_{0,overall}/(\psi_{max}U^2)$. **Round up.**
- **Smith chart** (turbines): $\eta$ contours on $(\phi,\psi)$. The peak $\eta$ is around $\phi\approx0.6$, $\psi\approx1$. Increasing $\psi$ roughly halves the stage count, at a few points of efficiency.
- **Blade speed**: set $U$ from $\phi$ and the axial Mach number, e.g. with the data-book flow function $V/\sqrt{c_pT_0}$. Fan tips are held below relative M 1.6 (noise, bird strike, blade-out).

## Examples
- Sea level, M 0.8, M 0.6 into the rotor, $\phi = 0.55$: $U = 380.8$ m/s. With a pressure ratio of 10 and $\psi\le0.4$, $n = 5.24$, so **6 stages**.
- HPC, $r_m = 0.267$ m at 185.6 rev/s, $U = 311$ m/s, $\Delta h_0 = 469$ kJ/kg, $\psi\le0.45$: **11 stages** at $\psi = 0.440$ ([[SESA2023 Problem Sheet 9 Solutions]]).
- LPT at fan speed ($U = 96$ m/s), $\psi = 2.5$: 23 stages. Geared ×3: 3 stages ([[SESA2023 Exam 2020-21 Solutions]] Q4).

## Related
- [[Euler Work Equation]] · [[Velocity Triangles]] · [[Dimensional Analysis of Turbomachines]] · [[Specific Speed]]

## Sources
- Week 9 handout §9.2; Lectures 25–26
