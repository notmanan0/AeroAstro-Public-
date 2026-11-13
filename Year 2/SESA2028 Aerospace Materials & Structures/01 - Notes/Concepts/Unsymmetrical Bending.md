---
title: "Unsymmetrical Bending"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, bending]
status: lectured
parent: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
---

# Unsymmetrical Bending

When it happens: the section has no symmetry axis aligned with the moment ($I_{yz}\ne0$), or the moment is inclined to the principal axes. A moment about one axis then produces curvature about both axes, and the neutral axis is not perpendicular to the moment vector.

## Stress field

With $x$ along the beam, $y$ downward and $z$ across, a positive $M_z$ puts the positive-$y$ side in tension and a positive $M_y$ does the same for positive $z$:

$$
\sigma_{xx}=\frac{\left(M_zI_y-M_yI_{yz}\right)y+\left(M_yI_z-M_zI_{yz}\right)z}{\Delta},\qquad \Delta=I_yI_z-I_{yz}^2.
$$

Check: with $I_{yz}=0$ this reduces to $\sigma_{xx}=M_zy/I_z+M_yz/I_y$, the familiar symmetric result.

## Method (exam routine)

1. Locate the centroid; draw the $y,z$ axes on the sketch.
2. Compute $I_y$, $I_z$, $I_{yz}$ (parallel-axis theorem, signed offsets).
3. Resolve the applied moment into $M_y$ and $M_z$ with the signs above: positive where the moment puts the positive side of the axis in tension.
4. Write $\sigma_{xx}=Cy+Dz$ with numerical coefficients.
5. Neutral axis: $\sigma_{xx}=0$, a straight line through the centroid ([[Neutral Axis in Unsymmetrical Bending]]).
6. The field is linear, so the extreme stresses occur at the vertices furthest from the neutral axis. Evaluate $\sigma_{xx}$ at every corner.

## Alternative: principal axes

Resolve $M$ onto the principal axes $y',z'$ (rotated by $\theta_1$ from $y$ towards $z$, as in S1), where $I_{y'z'}=0$, and use the uncoupled form $\sigma_{xx}=\dfrac{M_{z'}y'}{I_{z'}}+\dfrac{M_{y'}z'}{I_{y'}}$ with $I_{z'}=\int y'^2dA$ and $I_{y'}=\int z'^2dA$. It gives the same stress, but the coordinate transformation adds work in an exam.

![[structures_unsymmetric_bending_stress.png|700]]

Worked examples: [[FEEG2005 Exam 2013-14 Solutions]] A1, [[FEEG2005 Exam 2018-19 Solutions]] B1, [[FEEG2005 Exam 2024-25 Solutions]] SQ1.

## Related

- Topic: [[SESA2028 S1 - Section Properties and Unsymmetrical Bending|S1]]
- Concepts: [[Neutral Axis in Unsymmetrical Bending]]
- Elsewhere: [[FEEG2005 Exam 2013-14 Solutions]] · [[FEEG2005 Exam 2018-19 Solutions]]
