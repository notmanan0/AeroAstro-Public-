---
title: "Shear Stress Distribution in Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["sigma_yx = Q A_s y_c / b I", "transverse shear stress", "complementary shear", "shear stress coefficient"]
tags: [feeg1002, concept, statics, beams, shear-stress]
status: complete
parent_lectures: ["[[FEEG1002 A9 - Shear Stresses in Beams]]"]
related_concepts: ["[[First Moment of Area]]", "[[Shear Flow]]", "[[Engineer's Bending Theory]]"]
sources: ["Statics 1 Lecture 14"]
---

# Shear Stress Distribution in Beams

The shear force $Q$ in a beam is carried by shear stresses $\sigma_{yx}$ on the cross-section, and at a level $y$ below the neutral axis they are

$$
\sigma_{yx}=\frac{Q}{b\,I}A_s\,y_c
$$

where $b$ is the width at level $y$, $I$ the second moment of area of the whole section, $A_s$ the area of the section beyond level $y$ and $y_c$ the distance of its centroid from the neutral axis.

The formula comes from longitudinal equilibrium, not from the vertical shear directly. Where the bending moment varies along the beam, the bending stresses $My/I$ on the two ends of a short element differ. A strip cut off below level $y$ is then pushed harder on one end than the other, and only a horizontal shear stress on its top face can balance the difference. Using $dM/dx=Q$ turns that difference into $Q\,A_sy_c/I$, and dividing by the width $b$ gives the horizontal shear stress. Complementary shear stresses on perpendicular faces of an element are equal, so the vertical shear stress on the cross-section at the same level has the same value.

For a rectangle of depth $d$ the distribution is parabolic:

$$
\sigma_{yx}=\frac32\,\sigma_{yx\,av}\left(1-\frac{y^2}{(d/2)^2}\right)
$$

with $\sigma_{yx\,av}=Q/A$. It is zero at the top and bottom surfaces, which are free of shear, and largest on the neutral axis, where the bending stress is zero. The ratio of the peak to the average is the **shear stress coefficient** $K$: 3/2 for a rectangle, 4/3 for a solid circle and 2 for a thin-walled tube.

In slender beams the shear stress is small next to the bending stress; for a rectangular cantilever with an end load their ratio is $4L/d$. It matters where material or joints are weak in shear: glue lines and fasteners on the neutral axis, timber along the grain, thin webs and short, deep beams. A joint along the beam must carry a shear force per unit length of $\sigma_{yx}b$, and dividing one fastener's capacity by that gives the fastener spacing.

![[s1_beam_shear_stress.png|860]]

## Related

- Topic notes: [[FEEG1002 A9 - Shear Stresses in Beams#3. Derivation of the shear stress formula|A9, derivation]] · [[FEEG1002 A9 - Shear Stresses in Beams#4. Rectangular section|A9, rectangular section]] · [[FEEG1002 A9 - Shear Stresses in Beams#5. The shear stress coefficient|A9, shear stress coefficient]] · [[FEEG1002 A9 - Shear Stresses in Beams#6. Bending stress against shear stress|A9, bending against shear]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q3 - Glued timber beam|Tutorial 6 Q3]]
- Concepts: [[First Moment of Area]] · [[Engineer's Bending Theory]] · [[Shear Force and Bending Moment Relations]]
- Year 2: thin-walled sections, [[Shear Flow]] and the [[Shear Centre]] in [[SESA2028 S3 - Shear Flow and Shear Centre]]
