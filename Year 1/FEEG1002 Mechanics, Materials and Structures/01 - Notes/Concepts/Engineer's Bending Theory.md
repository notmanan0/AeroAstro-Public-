---
title: "Engineer's Bending Theory"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["simple bending theory", "M/I = sigma/y = E/R", "bending stress", "flexure formula", "neutral axis"]
tags: [feeg1002, concept, statics, beams, bending-stress]
status: complete
parent_lectures: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]", "[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
related_concepts: ["[[Parallel Axis Theorem]]", "[[Second Moments of Area]]", "[[Moment Curvature Relation]]", "[[Section Modulus]]", "[[Shear Stress Distribution in Beams]]"]
sources: []
---

# Engineer's Bending Theory

## Definition

> [!note] Definition
> For a straight, linear elastic beam in bending where plane sections remain plane:
>
> $$\frac{M}{I} = \frac{\sigma}{y} = \frac{E}{R},\qquad \sigma_{xx} = \frac{My}{I},\qquad I = \iint y^2\,dA$$
>
> with $y$ measured from the **neutral axis**, which passes through the **centroid** of the section.

## Explanation

- **Kinematics**: $\varepsilon = y/R$, linear through the depth.
- **Force equilibrium**: $\iint y\,dA = 0$, so the neutral axis is at the centroid.
- **Moment equilibrium**: $M = (E/R)\iint y^2\,dA = EI/R$.
- The stress is zero on the neutral axis and largest at the fibres furthest from it. For unsymmetric sections, check tension and compression $y_{max}$ separately.
- $1/R = M/EI$ is the [[Moment Curvature Relation]] used for deflection.
- Validity:
  - pure bending, though accurate with shear for slender beams;
  - small curvature, and bending about a principal axis (symmetric section);
  - equal $E$ in tension and compression, and linear elasticity (no yielding).
- **Superposition**: $\sigma = P/A + My/I$ for combined axial load and bending.

## Examples

- Rectangular cantilever with end load: $\sigma_{max} = \pm6FL/bd^2$.
- Inverted T (Tutorial 4 Q3): the top fibre at 71.3 mm governs, giving $F_{max} = 8.33$ kN.

![[s1_bending_stress_tsection.png|760]]

## Related

- Topic notes: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]
- Concepts: [[Parallel Axis Theorem]] · [[Second Moments of Area]] · [[Moment Curvature Relation]] · [[Section Modulus]] · [[Shear Stress Distribution in Beams]]
- Year 2: Coupled bending of unsymmetric sections, $\sigma = \frac{M_zI_{yy} - M_yI_{yz}}{I_{yy}I_{zz}-I_{yz}^2}y + \dots$, in [[Unsymmetrical Bending]] ([[SESA2028 S1 - Section Properties and Unsymmetrical Bending]])

## Sources

- Statics 1 Lectures 7a–c
