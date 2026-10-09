---
title: "Shear Stress Distribution in Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["tau = QAy/Ib", "transverse shear stress", "complementary shear", "shear stress coefficient"]
tags: [feeg1002, concept, statics, beams, shear-stress]
status: complete
parent_lectures: ["[[FEEG1002 A9 - Shear Stresses in Beams]]"]
related_concepts: ["[[First Moment of Area]]", "[[Shear Flow]]", "[[Engineer's Bending Theory]]"]
sources: []
---

# Shear Stress Distribution in Beams

## Definition

> [!note] Definition
> The transverse shear stress at level $y$ in a beam carrying shear force $Q$:
>
> $$\tau = \sigma_{xy} = \frac{Q\,A_s\bar y}{I\,b}$$
>
> Here $A_s\bar y$ is the first moment, about the neutral axis, of the area beyond $y$, and $b$ is the width at $y$. For a rectangle:
>
> $$\tau = \tfrac32\frac{Q}{A}\left[1-\left(\frac{y}{d/2}\right)^2\right]$$

## Explanation

- It arises from **longitudinal equilibrium**: when $M$ varies along the beam, the bending stresses on the two ends of a strip differ, and horizontal shear must balance them. Complementary shear makes the vertical and horizontal values equal.
- The stress is zero at free surfaces and largest at the neutral axis, where the bending stress is zero.
- Shear stress coefficient $K = \tau_{max}/\tau_{avg}$:
  - rectangle 3/2;
  - circle 4/3;
  - thin tube 2.
- For slender beams $\sigma_{max}/\tau_{max}\sim4L/d$, so bending governs. Shear governs glue lines, fasteners, thin webs and short beams.
- Fastener spacing: shear flow $q = \tau b$ per unit length, so spacing = fastener capacity / $q$.

## Examples

- Tutorial 6 Q3: glued timber beam, $\tau_{glue} = 0.30$ MPa; screws at 16.7 cm spacing.

![[s1_beam_shear_stress.png|760]]

## Related

- Topic notes: [[FEEG1002 A9 - Shear Stresses in Beams]]
- Concepts: [[First Moment of Area]] · [[Shear Flow]] · [[Engineer's Bending Theory]]
- Year 2: Thin-walled generalisation: $q = \tau t$ and the [[Shear Centre]] in [[SESA2028 S3 - Shear Flow and Shear Centre]]

## Sources

- Statics 1 Lecture 14a–c
