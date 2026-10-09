---
title: "SESA2028 S1 - Section Properties and Unsymmetrical Bending"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 1
tags: [sesa2028, structures, bending, principal-axes]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
next_topics: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
key_concepts: ["[[Second Moments of Area]]", "[[Principal Axes of a Section]]", "[[Unsymmetrical Bending]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 2 - Bending Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL1 Introduction, motivation & Review.pdf", "02 - Sources/Structures Lectures/SL2 Bending stress and deflection.pdf"]
---

# SESA2028 S1 - Section Properties and Unsymmetrical Bending

> [!abstract] Summary
> Bending is only "simple" when the loading axes are principal axes. For an asymmetric section, the product of inertia couples the two bending directions: a moment about one geometric axis produces curvature about both, the neutral axis is not generally perpendicular to the load, and the beam deflects obliquely.

## 1. Centroid and section properties

For areas $A_i$ with centroids $(y_i,z_i)$,

$$
\bar y=\frac{\sum A_i y_i}{\sum A_i},\qquad
\bar z=\frac{\sum A_i z_i}{\sum A_i}.
$$

About centroidal $y,z$ axes,

$$
I_{yy}=\int_A z^2\,dA,\qquad
I_{zz}=\int_A y^2\,dA,\qquad
I_{yz}=\int_A yz\,dA.
$$

Use the parallel-axis theorem component by component:

$$
I_{yy}=\sum\left(I_{yy,c,i}+A_i\Delta z_i^2\right),\quad
I_{zz}=\sum\left(I_{zz,c,i}+A_i\Delta y_i^2\right),\quad
I_{yz}=\sum\left(I_{yz,c,i}+A_i\Delta y_i\Delta z_i\right).
$$

The sign of $I_{yz}$ depends on the stated $y,z$ directions. Do not copy a sign from a sketch using different axes.

## 2. Principal axes

Principal axes are the centroidal axes for which $I_{12}=0$. Their angle obeys

$$
\tan 2\theta_p=\frac{2I_{yz}}{I_{yy}-I_{zz}},
$$

with principal second moments

$$
I_{1,2}=\frac{I_{yy}+I_{zz}}2
\pm\sqrt{\left(\frac{I_{yy}-I_{zz}}2\right)^2+I_{yz}^2}.
$$

Because $\tan(2\theta)$ repeats every $90^\circ$, use an `atan2` form or verify by transforming $I_{yz}$ back to zero. [[Principal Axes of a Section]] gives the full sign-safe workflow.

![[Figures/structures_principal_inertia_mohr_circle.png]]

## 3. General bending stress

With $\Delta=I_{yy}I_{zz}-I_{yz}^2$, the linear axial-stress field may be written, for the sign convention used in the structures lectures, as

$$
\sigma_{xx}=
-\frac{M_zI_{yy}+M_yI_{yz}}{\Delta}\,y
+\frac{M_yI_{zz}+M_zI_{yz}}{\Delta}\,z.
$$

The important structure of the equation is more memorable than its signs:

- the stress is linear in $y$ and $z$;
- both moments appear in both coefficients when $I_{yz}\ne0$;
- setting $I_{yz}=0$ recovers ordinary bending about principal axes.

For a particular problem, check the signs by asking which side of the section should be in tension under a simple limiting load.

## 4. Neutral axis and extreme stress

The neutral axis is obtained by setting $\sigma_{xx}=0$:

$$
\frac{y}{z}=
\frac{M_yI_{zz}+M_zI_{yz}}
{M_zI_{yy}+M_yI_{yz}}.
$$

It passes through the centroid but is generally not perpendicular to the applied load. Once its direction is known, evaluate $\sigma_{xx}$ at every geometrically extreme corner; the furthest point in $y$ or $z$ alone need not govern.

![[Figures/structures_unsymmetric_bending_stress.png]]

## 5. Curvature and deflection

The moment-curvature equations are coupled:

$$
\begin{bmatrix}M_y\\M_z\end{bmatrix}
=E
\begin{bmatrix}I_{yy}&-I_{yz}\\-I_{yz}&I_{zz}\end{bmatrix}
\begin{bmatrix}\kappa_y\\\kappa_z\end{bmatrix}.
$$

Therefore

$$
\kappa_y=\frac{M_yI_{zz}+M_zI_{yz}}{E\Delta},\qquad
\kappa_z=\frac{M_zI_{yy}+M_yI_{yz}}{E\Delta},
$$

subject to the lecture sign convention. Integrate curvature twice using the boundary conditions to obtain the two deflection components. For a cantilever under a constant-direction tip force, each component has the familiar $L^3/3E$ factor, but the two curvatures remain coupled.

## 6. Exam workflow

1. Resolve the load into $F_y,F_z$ and construct $M_y(x),M_z(x)$.
2. Calculate the centroid and all three section properties.
3. Compute $\Delta$ and check it is positive.
4. Write one stress equation with units shown.
5. Set $\sigma=0$ for the neutral axis.
6. Test all corners for the tensile and compressive extrema.
7. For deflection, invert the moment-curvature matrix before integrating.

> [!warning] Common mistake
> Treating an asymmetric section as if $I_{yz}=0$ can give a plausible-looking answer in the wrong direction. Symmetry is the only safe shortcut: if neither centroidal axis is an axis of symmetry, assume coupling until proved otherwise.

## Year 1 foundation
- [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] derives $M/I = \sigma/y = E/R$, centroids, $I = bd^3/12$ and the parallel axis theorem for **symmetric** sections. This note removes the symmetry assumption. Shear stresses from the same bending start in [[FEEG1002 A9 - Shear Stresses in Beams]].
