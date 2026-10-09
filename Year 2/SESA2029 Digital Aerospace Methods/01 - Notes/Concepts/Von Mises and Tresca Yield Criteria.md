---
title: "Von Mises and Tresca Yield Criteria"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["von Mises stress", "Tresca criterion", "equivalent stress", "stress intensity", "yield criterion"]
tags: [sesa2029, concept, fea, yield]
status: complete
parent_lectures: ["[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]"]
related_concepts: ["[[Stress Concentration Factor and Factor of Safety]]", "[[Plane Stress and Plane Strain]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Von Mises and Tresca Yield Criteria

## Definition

> [!note] Definition
> Scalar measures that compare a 3D stress state with the uniaxial yield stress:
>
> $$\text{Tresca: }\max\left(|\sigma_1-\sigma_2|,|\sigma_2-\sigma_3|,|\sigma_3-\sigma_1|\right) = \sigma_Y,\qquad\text{von Mises: }\sqrt{\tfrac12\left[(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2\right]} = \sigma_Y$$

## Explanation

- **Tresca** (maximum shear): usually **conservative** against tests. In ANSYS its measure is "stress intensity" ($2\tau_{max}$).
- **von Mises** (distortion energy): generally **more accurate**, not always conservative. It is the industry default and the usual FE contour (`S,EQV`).
- **Linear scaling**: in a linear elastic analysis stress ∝ load, so the load at first yield follows from one run: $P_Y = P\,\sigma_Y/\sigma_{e,max}$.
- Linear FEA predicts where and when yield **starts**. It cannot model plastic flow beyond that ([[SESA2029 B9 - Nonlinear FE Analysis]]).

## Examples

- Nozzle intersection with $\sigma_Y = 340$ MPa and $P = 2.5$ MPa: von Mises $\sigma_e = 238.6$ MPa gives $P_Y = 3.56$ MPa; Tresca $SI = 256.1$ MPa gives $P_Y = 3.32$ MPa (the slide prints 3.20).
- Uniaxial $\sigma$: both criteria give $\sigma$. Pure shear $\tau$: von Mises gives $\sqrt3\tau$ and Tresca gives $2\tau$.

## Related

- Parent lectures: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]
- Related concepts: [[Stress Concentration Factor and Factor of Safety]] · [[Plane Stress and Plane Strain]]

**Related (SESA2028 materials):** [[Plane Strain Constraint]] · [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|SESA2028 M1]] (yield needs shear; brittle fracture follows maximum opening stress)

## Year 1 foundation
- First derivation and worked examples in [[FEEG1002 B6 - Yield Criteria]].

## Sources

- 02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf
- 02 - Sources/FEM Lectures/FEA.txt
