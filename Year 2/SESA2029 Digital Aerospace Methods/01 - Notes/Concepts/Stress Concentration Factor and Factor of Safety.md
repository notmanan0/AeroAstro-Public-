---
title: "Stress Concentration Factor and Factor of Safety"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["SCF", "Kt", "stress concentration", "factor of safety", "FoS", "Kirsch solution"]
tags: [sesa2029, concept, fea, stress-concentration]
status: complete
parent_lectures: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]", "[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]"]
related_concepts: ["[[Von Mises and Tresca Yield Criteria]]", "[[Stress Singularities]]", "[[Mesh Convergence and Grid Independence]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf", "02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Stress Concentration Factor and Factor of Safety

## Definition

> [!note] Definition
>
> $$K_t = \frac{\sigma_{max}}{\sigma_{bulk}},\qquad FoS = \frac{\sigma_{yield}}{\sigma_{max}}$$
>
> $\sigma_{bulk}$ is the nominal stress far from the discontinuity. $K_t$ quantifies local amplification at holes, fillets and steps. The FoS is the margin against yield (typically ≥ 1.5–2 by code).

## Explanation

- **The amplification depends on** the global configuration, the location of the discontinuity, and its geometry and size. The more abrupt the change, the higher $K_t$. Fillets reduce it.
- **Elliptical hole in an infinite plate** (semi-axis $a$ perpendicular to the load, $b$ parallel): $K_t = 1+2a/b$. A circle gives 3; $a = 2b$ gives 5.
- **Kirsch (circular hole)**: along the net section, $\sigma_{xx}/\sigma_\infty = 1+\tfrac12(a/r)^2+\tfrac32(a/r)^4$. The hoop stress at the hole edge is $\sigma_\infty(1-2\cos2\theta)$, which is $+3\sigma_\infty$ at 90° and $-\sigma_\infty$ at 0°.
- **Finite width**: $K_{t,net}\approx2+(1-d/W)^3$ (Heywood); $K_{t,gross} = K_{t,net}/(1-d/W)$. State which definition you use.
- **FE practice**:
  - take $\sigma_{bulk}$ from the applied traction or the far-edge nodes, never the minimum stress in the plate;
  - converge the peak with local refinement;
  - a *round* hole converges, but a *sharp* corner does not ([[Stress Singularities]]).

## Examples

![[dam_kirsch_hole_stress.png|600]]

- FE model with $a = 2b$: $\sigma_{max} = 503.7$ MPa against a bulk 100 MPa, so $K_t = 5.037$ (analytic 5).

## Related

- Parent lectures: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] · [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]
- Related concepts: [[Von Mises and Tresca Yield Criteria]] · [[Stress Singularities]] · [[Mesh Convergence and Grid Independence]]

**Related (SESA2028 materials):** [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|SESA2028 M1 fracture mechanics]] · [[Stress Intensity Factor]] · [[Fatigue Fracture Surface Features]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf
- 02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf
- 02 - Sources/FEM Lectures/FEA.txt
