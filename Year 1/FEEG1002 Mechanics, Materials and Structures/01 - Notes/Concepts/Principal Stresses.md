---
title: "Principal Stresses"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["principal directions", "maximum shear stress", "sigma_I sigma_II", "principal planes"]
tags: [feeg1002, concept, statics-2, principal-stresses, failure]
status: complete
parent_lectures: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B6 - Yield Criteria]]"]
related_concepts: ["[[Mohr's Circle]]", "[[Stress Transformation Equations]]", "[[Von Mises and Tresca Yield Criteria]]"]
sources: []
---

# Principal Stresses

## Definition

> [!note] Definition
> The normal stresses on the orientations with **zero shear**:
>
> $$\sigma_{I,II} = \frac{\sigma_{xx}+\sigma_{yy}}2 \pm\sqrt{\left(\frac{\sigma_{xx}-\sigma_{yy}}2\right)^2 + \sigma_{xy}^2},\qquad \tan2\theta_p = \frac{2\sigma_{xy}}{\sigma_{xx}-\sigma_{yy}}$$
>
> The principal directions are 90° apart. The maximum in-plane shear $(\sigma_I - \sigma_{II})/2$ acts at 45° to them.

## Explanation

- They are the **eigenvalues** of the stress tensor, and the principal directions its eigenvectors.
- $\sigma_I$ is the largest normal stress on **any** plane. That is what opens cracks, so brittle materials fail by it.
- Yield criteria are written in principal stresses, which makes them orientation-independent.
- In 3D there are three: $\tau_{max,abs} = \tfrac12(\sigma_{max} - \sigma_{min})$. In plane stress $\sigma_{III} = 0$ still counts: two tensile in-plane principals give an out-of-plane $\tau_{max} = \sigma_I/2$.
- For isotropic materials the principal **strains** share the same directions.

## Examples

- Pure shear (torsion): $\sigma_{I,II} = \pm\tau$ at 45°, which explains the helical brittle fracture of shafts.
- Pressure vessel: the axial and hoop directions are already principal.

![[s2_mohr_pure_shear.png|760]]

## Related

- Topic notes: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[FEEG1002 B6 - Yield Criteria]]
- Concepts: [[Mohr's Circle]] · [[Stress Transformation Equations]] · [[Von Mises and Tresca Yield Criteria]]
- Year 2: [[Von Mises and Tresca Yield Criteria]] · [[Stress Intensity Factor]] (mode I opening by the normal stress) · crack-growth direction in fatigue ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]])

## Sources

- Statics 2 Lecture 6b; Statics 2 Lecture 8a
