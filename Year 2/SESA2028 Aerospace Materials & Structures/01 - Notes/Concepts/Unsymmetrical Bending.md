---
title: "Unsymmetrical Bending"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, bending]
status: complete
parent: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
---

# Unsymmetrical Bending

**When it happens:** the section has no symmetry axis aligned with the moment ($I_{yz}\ne0$), or the moment is inclined to the principal axes. A moment about one axis then produces curvature about **both** axes, and the neutral axis is **not** perpendicular to the moment vector.

## Stress field (module sign convention)

$$
\sigma_x=-\frac{M_zI_y+M_yI_{yz}}{\Delta}\,y+\frac{M_yI_z+M_zI_{yz}}{\Delta}\,z,\qquad \Delta=I_yI_z-I_{yz}^2.
$$

Check: with $I_{yz}=0$ this reduces to $\sigma_x=-M_zy/I_z+M_yz/I_y$, the familiar symmetric result.

## Method (exam routine)

1. Locate the **centroid**; draw the $y,z$ axes on the sketch.
2. Compute $I_y$, $I_z$, $I_{yz}$ (parallel-axis theorem, signed offsets).
3. Resolve the applied moment into $M_y$ and $M_z$ with the correct signs (right-hand rule on the positive-$x$ face).
4. Write $\sigma_x=Cy+Dz$ with numerical coefficients.
5. **Neutral axis**: $\sigma_x=0$, a straight line through the centroid ([[Neutral Axis in Unsymmetrical Bending]]).
6. The field is linear, so the extreme stresses occur at the **vertices furthest from the neutral axis**. Evaluate $\sigma_x$ at every corner.

## Alternative: principal axes

Resolve $M$ onto the principal axes 1 and 2 (axis 1 playing the role of $y$, axis 2 of $z$) and use $\sigma=\dfrac{M_1\eta}{I_1}-\dfrac{M_2\xi}{I_2}$, where $\xi$ is the coordinate along axis 1 and $\eta$ along axis 2. This is the same form as the uncoupled $\sigma=M_yz/I_y-M_zy/I_z$. This is equivalent, but the coordinate transformation adds work in an exam.

![Unsymmetrical stress field](../Figures/structures_unsymmetric_bending_stress.png)

Worked examples: [[FEEG2005 Exam 2013-14 Solutions]] A1, [[FEEG2005 Exam 2018-19 Solutions]] B1, [[FEEG2005 Exam 2024-25 Solutions]] SQ1.
