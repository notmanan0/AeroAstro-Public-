---
title: "Torsion of Circular Shafts"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["torsion equation", "T/J = tau/r = G theta/L", "polar second moment of area", "J = pi D^4/32"]
tags: [feeg1002, concept, statics, torsion, shafts]
status: complete
parent_lectures: ["[[FEEG1002 A8 - Torsion of Circular Shafts]]"]
related_concepts: ["[[Saint-Venant Torsion]]", "[[Stress, Strain and Young's Modulus]]", "[[Engineer's Bending Theory]]"]
sources: []
---

# Torsion of Circular Shafts

## Definition

> [!note] Definition
> For a solid or hollow circular shaft under torque $T$:
> $$\frac{T}{J} = \frac{\tau}{r} = \frac{G\theta}{L},\qquad J = \frac{\pi D^4}{32}\ (\text{solid}),\quad J = \frac{\pi(D_o^4-D_i^4)}{32}\ (\text{hollow})$$
> The shear stress rises linearly with radius; $GJ/L$ is the torsional stiffness.

## Explanation

- Assumptions: circular section (plane sections remain plane, radii stay straight), linear elastic, small twist.
- It is pure shear: no change in length or diameter.
- **Hollow shafts** are far more efficient, because the core carries little stress. At $n = 0.9$ the hollow shaft weighs 39% of the equivalent solid shaft but is 43% larger in diameter.
- **Power**: $P = T\omega$.
- Non-circular sections **warp**, so this formula does not apply ([[Saint-Venant Torsion]], [[Open-Section Torsion]]).
- The surface is in pure shear, which is equivalent to principal stresses $\pm\tau$ at 45°. That explains the helical fracture of brittle shafts.

## Examples

- Tutorial 6 Q2: an aluminium tube with $D_o = 70$ mm at 3 kN m and $\tau = 150$ MPa gives $D_i = 64$ mm. A steel core just fitting it carries 58 MPa.

![[s1_torsion_hollow_vs_solid.png|760]]

## Related

- Topic notes: [[FEEG1002 A8 - Torsion of Circular Shafts]]
- Concepts: [[Saint-Venant Torsion]] · [[Stress, Strain and Young's Modulus]] · [[Engineer's Bending Theory]]
- Year 2: [[SESA2028 S4 - Torsion of Thin-Walled Sections]]: [[Bredt-Batho Torsion]] ($q = T/2A$) for closed cells and $J = \tfrac13\sum bt^3$ for open sections

## Sources

- Statics 1 Lecture 13a–c
