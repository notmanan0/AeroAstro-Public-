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
sources: ["Statics 1 Lectures 7-8"]
---

# Engineer's Bending Theory

Engineer's bending theory relates the bending moment $M$ on a beam section to the longitudinal stress it causes and to the curvature $1/R$ of the beam:

$$
\frac{M}{I_{zz}}=\frac{\sigma_{xx}}{y}=\frac{E}{R}
$$

with $y$ measured downwards from the neutral axis, which passes through the centroid of the section.

The result rests on one kinematic assumption: plane cross-sections stay plane and normal to the bent axis. A fibre at distance $y$ from the neutral surface then has length $(R+y)\,d\theta$ against $R\,d\theta$ on the neutral surface, so its strain is $\varepsilon_{xx}=y/R$, linear through the depth. With linear elastic material and the same $E$ in tension and compression, the stress is $\sigma_{xx}=Ey/R$.

Two equilibrium conditions finish the derivation. In pure bending there is no axial force, so $\int\sigma_{xx}\,dA=(E/R)\int y\,dA=0$: the neutral axis passes through the centroid. The stresses must add up to the applied moment, so $M=(E/R)\int y^2\,dA=EI_{zz}/R$, which defines the second moment of area and gives the relation above. Dropping $R$ gives the working form $\sigma_{xx}=My/I_{zz}$.

The stress is zero on the neutral axis and largest at the fibre furthest from it. For a section with only one axis of symmetry the two extreme fibres are at different distances, so tension and compression must be checked separately, and for a material weaker in one of them the orientation of the section matters. The theory is derived for pure bending, but it stays accurate for slender beams carrying shear. An axial load adds a uniform $P/A$ on top of $My/I_{zz}$ by superposition. The other half of the result, $1/R=M/EI$, is the [[Moment Curvature Relation]] that turns a bending moment diagram into a deflection.

![[s1_bending_strain_geometry.png|860]]

## Related

- Derivation: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#1. Deformation in pure bending|A4, deformation in pure bending]] and [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#2. Equilibrium of the cross-section|A4, equilibrium of the cross-section]]
- Use: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#4. Strength of a beam of uniform section|A4, strength of a beam]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Moment and curvature|A5, moment and curvature]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]]
- Concepts: [[Parallel Axis Theorem]] · [[Second Moments of Area]] · [[Section Modulus]] · [[Shear Stress Distribution in Beams]]
- Year 2: unsymmetric sections, where the neutral axis is no longer parallel to the moment axis, in [[Unsymmetrical Bending]] ([[SESA2028 S1 - Section Properties and Unsymmetrical Bending]])
