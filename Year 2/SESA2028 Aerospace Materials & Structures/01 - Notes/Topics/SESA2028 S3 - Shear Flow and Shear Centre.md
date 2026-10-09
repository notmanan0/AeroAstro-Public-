---
title: "SESA2028 S3 - Shear Flow and Shear Centre"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 3
tags: [sesa2028, structures, shear-flow, shear-centre]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
next_topics: ["[[SESA2028 S4 - Torsion of Thin-Walled Sections]]"]
key_concepts: ["[[Shear Flow]]", "[[Shear Centre]]", "[[First Moment of Area]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 2 - Bending Solutions]]", "[[SESA2028 Structures Tutorial 3 - Torsion Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL3 Shear stresses in beams under shear force.pdf", "02 - Sources/Structures Lectures/Structures Additional session-Shear.pdf"]
---

# SESA2028 S3 - Shear Flow and Shear Centre

> [!abstract] Summary
> Shear flow is force per unit length carried along a thin wall. It begins at zero at a free edge, accumulates as wall area is swept up, and must satisfy both the applied shear force and moment equilibrium. The shear centre is the point through which a transverse load produces bending without twist.

## 1. From shear stress to shear flow

For a wall thickness $t$,

$$
q=\tau t.
$$

For loading along a principal direction, the familiar beam formula is

$$
q(s)=\frac{VQ(s)}{I},\qquad Q(s)=\int_{A^*(s)} y\,dA.
$$

For a thin wall, $dA=t(s)\,ds$. The quantity $Q$ is the first moment of the area swept from a free edge to the point of interest.

![[Figures/structures_open_section_shear_flow.png]]

## 2. General unsymmetric-section formula

Let

$$
Q_y(s)=\int_{A^*} z\,dA,\qquad Q_z(s)=\int_{A^*} y\,dA,\qquad
\Delta=I_{yy}I_{zz}-I_{yz}^2.
$$

Then one convenient matrix form is

$$
q(s)=
\frac{Q_y^{(V)}(s)}{\Delta}
$$

where the numerator is assembled from $V_y,V_z,I_{yy},I_{zz},I_{yz}$ and the two first moments according to the lecture sign convention. In an exam, write the full form supplied in the formula sheet, then perform three checks:

1. $q=0$ at every free edge;
2. $\int q\,d\mathbf s$ recovers the resultant applied shear;
3. the moment of the distributed wall force gives the expected torque.

These checks catch most sign errors more reliably than re-reading the algebra.

## 3. Open-section procedure

1. Mark a wall coordinate $s$ starting from a free edge.
2. Find the centroid and $I_{yy},I_{zz},I_{yz}$.
3. Build the first moments segment by segment. Carry the accumulated value through each corner.
4. Calculate $q(s)$ and then $\tau=q/t$.
5. Sketch arrows. The sign determines the direction along the chosen $s$ coordinate.
6. Repeat from every disconnected free edge and join the distributions consistently.

The largest $q$ often occurs in a web near the neutral axis, while the largest $\tau$ can occur in a thinner wall because of the division by $t$.

## 4. Closed sections

Cut a closed cell to create a statically determinate open-section flow $q_b(s)$. Closure adds a constant redundant flow $q_0$:

$$
q(s)=q_b(s)+q_0.
$$

For a cell that is not twisting under a shear load through the shear centre,

$$
\oint\frac{q_b+q_0}{Gt}\,ds=0
\quad\Rightarrow\quad
q_0=-\frac{\displaystyle\oint q_b/(Gt)\,ds}
{\displaystyle\oint 1/(Gt)\,ds}.
$$

## 5. Shear centre

The shear centre $S$ satisfies moment equilibrium between the external force and the internal shear flow:

$$
\mathbf r_S\times\mathbf V=\oint \mathbf r\times q\,d\mathbf s.
$$

Useful symmetry rules:

- one axis of symmetry $\Rightarrow$ the shear centre lies on it;
- two axes of symmetry $\Rightarrow$ shear centre = centroid;
- for channel and angle sections, the shear centre can lie outside the material.

> [!warning] Centroid is not shear centre
> The centroid is an area property. The shear centre is a load-application point defined by zero twist. They coincide only for sections with sufficient symmetry.

## 6. Combined shear and torsion

If a load is applied away from $S$, replace it by the same force through $S$ plus

$$
T=Ve.
$$

Calculate bending shear flow and torsional shear flow separately, preserve their signs around the wall, then superpose them before finding the maximum $|\tau|$.

## Year 1 foundation
- [[FEEG1002 A9 - Shear Stresses in Beams]]: $\tau = QA\bar y/Ib$ for solid rectangular and circular sections. Shear flow $q = \tau t$ is the thin-walled generalisation.
