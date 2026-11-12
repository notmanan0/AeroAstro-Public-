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
sources: ["Statics 1 Lecture 13"]
---

# Torsion of Circular Shafts

A circular shaft carrying a torque $T$ twists by an angle $\theta$ over its length $L$, with a shear stress $\tau$ that grows linearly with the radius $r$, according to the torsion equations

$$
\frac{T}{J}=\frac{\tau}{r}=\frac{G\theta}{L}
$$

where $G$ is the shear modulus and $J$ the polar second moment of area, $\pi D^4/32$ for a solid shaft and $\pi(D_o^4-D_i^4)/32$ for a hollow one.

The derivation follows the same pattern as bending. By symmetry, cross-sections of a circular shaft stay plane and their radii stay straight as it twists. A line along the surface therefore tilts by a shear strain $\gamma=R\theta/L$, and at radius $r$ inside the shaft the strain is $r\theta/L$, so the shear stress $\tau=G\gamma=Gr\theta/L$ is linear in $r$. Adding up the moment of the stress on each ring, $T=\int\tau r\,dA=(G\theta/L)\int r^2\,dA$, defines $J$ and gives the equations above. The assumptions are a circular section, linear elastic material and small twist.

The largest stress is at the outer surface, $\tau_{max}=TR/J$, and the stiffness against twisting is $GJ/L$. Material near the centre carries little stress and adds little to $J$, so a hollow shaft is much lighter than a solid one of the same strength: with a bore of 0.8 times the outside diameter it weighs about half as much. The same reasoning fails for non-circular sections, whose cross-sections warp; they need [[Saint-Venant Torsion]].

![[s1_torsion_shear_strain.png|860]]

## Related

- Topic notes: [[FEEG1002 A8 - Torsion of Circular Shafts#1. Deformation of a circular shaft|A8, deformation]] · [[FEEG1002 A8 - Torsion of Circular Shafts#3. Torque and the polar second moment of area|A8, torque and J]] · [[FEEG1002 A8 - Torsion of Circular Shafts#The torsion equations|A8, torsion equations]] · [[FEEG1002 A8 - Torsion of Circular Shafts#4. Solid and hollow shafts|A8, solid and hollow shafts]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q2 - Steel shaft and aluminium tube|Tutorial 6 Q2]]
- Concepts: [[Stress, Strain and Young's Modulus]] · [[Engineer's Bending Theory]] · [[Saint-Venant Torsion]]
- Year 2: thin-walled closed and open sections, including [[Bredt-Batho Torsion]], in [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
