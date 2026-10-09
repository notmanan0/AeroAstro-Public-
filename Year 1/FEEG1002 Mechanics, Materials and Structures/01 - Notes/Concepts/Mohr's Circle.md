---
title: "Mohr's Circle"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["Mohr's circle for stress", "Mohr's circle for strain", "Mohr circle"]
tags: [feeg1002, concept, statics-2, mohrs-circle, principal-stresses]
status: complete
parent_lectures: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Stress Transformation Equations]]", "[[Principal Stresses]]", "[[Strain Gauge Rosettes]]", "[[Principal Axes of a Section]]"]
sources: []
---

# Mohr's Circle

## Definition

> [!note] Definition
> The transformation equations trace a circle in the ($\sigma_{x'x'}$, $\sigma_{x'y'}$) plane:
> $$(\sigma_{x'x'} - \sigma_{avg})^2 + \sigma_{x'y'}^2 = R^2,\qquad \sigma_{avg} = \frac{\sigma_{xx}+\sigma_{yy}}2,\qquad R = \sqrt{\left(\frac{\sigma_{xx}-\sigma_{yy}}2\right)^2 + \sigma_{xy}^2}$$
> **FEEG1002 convention**: shear is plotted **positive downwards**, so a rotation $\theta$ of the element is a rotation $2\theta$ in the **same sense** on the circle.

## Explanation

Construction:
1. Centre at $\sigma_{avg}$.
2. $x$-face point at $(\sigma_{xx}, \sigma_{xy})$; $y$-face point diametrically opposite, at $(\sigma_{yy}, -\sigma_{xy})$.
3. Draw the circle.

Readings:
- principal stresses at the horizontal-axis crossings;
- maximum in-plane shear $R$ at the top and bottom;
- the angle from the $x$-face point to $\sigma_I$ is $2\theta_p$.

Special cases:
- uniaxial: the circle touches the origin;
- pure shear: centred on the origin;
- equibiaxial: a point.

For **strain**, use $\varepsilon_{xy} = \gamma_{xy}/2$ on the vertical axis.

The biggest source of errors is the sign of $\sigma_{xy}$. Read it from the arrow on the **+x face**.

## Examples

- Sail (Statics 2 Tutorial 5): $\sigma_I = 4.3$ and $\sigma_{II} = 0.70$ MPa, at $\theta_p = -16.8^\circ$.
- Revision Q4: $\sigma_I = 55$, $\sigma_{II} = 5$, $\tau_{max} = 25$ MPa, at $\theta_p = -71.6^\circ$.

![[s2_mohr_t5_sail.png|860]]

## Related

- Topic notes: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
- Concepts: [[Stress Transformation Equations]] · [[Principal Stresses]] · [[Strain Gauge Rosettes]] · [[Principal Axes of a Section]]
- Year 2: Mohr's circle for second moments of area ([[Principal Second Moments of Area]], [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]) · principal stresses feed [[Von Mises and Tresca Yield Criteria]]

## Sources

- Statics 2 Lecture 6a–b; Statics 2 Lecture 7b
