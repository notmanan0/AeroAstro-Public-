---
title: "SESA2028 Structures Tutorial 2 - Bending Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Structures"
order: 2
tags: [sesa2028, structures, tutorial, bending, shear-flow]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]", "[[SESA2028 S2 - Beam Deflection and Bending Design]]", "[[SESA2028 S3 - Shear Flow and Shear Centre]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf, pp. 43-44"]
---

# SESA2028 Structures Tutorial 2 - Bending Solutions

## Q1.1 - Properties and principal axes of the Z-section

The section has 180-degree rotational symmetry, so its centroid is at the centre of the web. Split it into two $60\times10$ mm flanges and the remaining $10\times80$ mm web. The flange centroids are at $(y,z)=(-45,-25)$ mm and $(45,25)$ mm.

### $I_{zz}$

$$
I_{zz}=2\left[\frac{60(10)^3}{12}+(60\cdot10)(45)^2\right]
+\frac{10(80)^3}{12}
=\boxed{2.87\times10^6\ \mathrm{mm^4}}.
$$

### $I_{yy}$

$$
I_{yy}=2\left[\frac{10(60)^3}{12}+(60\cdot10)(25)^2\right]
+\frac{80(10)^3}{12}
=\boxed{1.12\times10^6\ \mathrm{mm^4}}.
$$

### $I_{yz}$

The local product of inertia of each rectangle is zero about its own centroid:

$$
I_{yz}=\sum A_i y_i z_i
=2(600)(45)(25)
=\boxed{1.35\times10^6\ \mathrm{mm^4}},
$$

with the sign set by the axes shown in the sheet.

The principal angle is

$$
\theta_p=\frac12\tan^{-1}\left(\frac{2I_{yz}}{I_{yy}-I_{zz}}\right)
=\boxed{28.5^\circ}
$$

after choosing the correct quadrant. The principal values are

$$
I_{max,min}=\frac{I_{yy}+I_{zz}}2
\pm\sqrt{\left(\frac{I_{yy}-I_{zz}}2\right)^2+I_{yz}^2},
$$

so

$$
\boxed{I_{max}=3.60\times10^6\ \mathrm{mm^4}},\qquad
\boxed{I_{min}=3.83\times10^5\ \mathrm{mm^4}}.
$$

![[Figures/structures_principal_inertia_mohr_circle.png]]

## Q1.2 - Bending moment, neutral axis and extreme stress

Resolve the 1 kN tip load:

$$
F_y=1000\cos30^\circ=866\ \mathrm N,\qquad
F_z=1000\sin30^\circ=500\ \mathrm N.
$$

With $x$ in mm from the fixed end,

$$
\boxed{M_z(x)=866(2000-x)\ \mathrm{Nmm}},
$$

$$
\boxed{M_y(x)=-500(2000-x)\ \mathrm{Nmm}}.
$$

Both diagrams are triangular and peak at the fixed end. Let

$$
\Delta=I_{yy}I_{zz}-I_{yz}^2=1.392\times10^{12}\ \mathrm{mm^8}.
$$

Substituting the fixed-end moments into the general unsymmetrical-bending expression gives a linear field $\sigma_{xx}=C_yy+C_zz$. Setting it to zero gives

$$
\boxed{\phi=57.8^\circ}
$$

for the neutral axis. Evaluating the stress at every corner shows that the governing pair is at $(z,y)=(5,50)$ mm and its diametrically opposite point:

$$
\boxed{\sigma_{xx,max}=+138\ \mathrm{MPa}},\qquad
\boxed{\sigma_{xx,min}=-138\ \mathrm{MPa}}.
$$

![[Figures/structures_unsymmetric_bending_stress.png]]

## Q1.3 - Coupled tip deflection

For an unsymmetric cantilever,

$$
\begin{bmatrix}\kappa_y\\\kappa_z\end{bmatrix}
=\frac1{E\Delta}
\begin{bmatrix}I_{zz}&I_{yz}\\I_{yz}&I_{yy}\end{bmatrix}
\begin{bmatrix}M_y\\M_z\end{bmatrix},
$$

with signs adjusted to the axes shown. Because the moments vary as $(L-x)$, integrating twice produces the cantilever factor $L^3/3$.

With $E=200$ GPa and the section properties from Q1.1,

$$
\boxed{v=-15.88\ \mathrm{mm}},\qquad
\boxed{w=25.16\ \mathrm{mm}}.
$$

The resultant is

$$
|\delta|=\sqrt{v^2+w^2}=\boxed{29.75\ \mathrm{mm}}.
$$

Its direction from the positive $z$ axis is

$$
\tan^{-1}\left(\frac{v}{w}\right)=-32.3^\circ.
$$

The neutral axis was at $57.8^\circ$; the two directions differ by $90.1^\circ$, verifying that the deflection is perpendicular to the neutral axis to rounding accuracy.

## Q1.4 - Shear-flow distribution

Differentiate the bending moments:

$$
M_z'=-866\ \mathrm N,\qquad M_y'=+500\ \mathrm N.
$$

Starting at a free edge, define the partial first moments

$$
Q_z(s)=\int_{A^*(s)}y\,dA,\qquad
Q_y(s)=\int_{A^*(s)}z\,dA.
$$

Longitudinal equilibrium gives

$$
q(s)=
\frac{M_z'I_{yy}+M_y'I_{yz}}{\Delta}Q_z(s)
-\frac{M_y'I_{zz}+M_z'I_{yz}}{\Delta}Q_y(s).
$$

Numerically,

$$
q(s)=-(2.119\times10^{-4})Q_z(s)
-(1.910\times10^{-4})Q_y(s),
$$

with $Q$ in $\mathrm{mm^3}$ and $q$ in $\mathrm{N/mm}$. Evaluate the integrals along the top flange, carry the accumulated values down the web, and continue along the lower flange. The distribution returns to zero at the second free edge, providing a strong check.

Dividing by $t=10$ mm gives the maximum wall stress:

$$
\boxed{\tau_{max}=1.29\ \mathrm{MPa}}.
$$

## Q2 - Closed rectangular box under vertical shear

Using non-overlapping plates, the centroid is approximately $206$ mm from the outer face of the thick left wall (shown as 200 mm on the rounded diagram), and

$$
\boxed{I_{zz}\approx1.81\times10^8\ \mathrm{mm^4}}.
$$

Cut the right web at its midpoint and treat the cell as open. Starting from the cut,

$$
q_b(s)=\frac{V_yQ_z(s)}{I_{zz}},\qquad V_y=200\ \mathrm{kN}.
$$

Continue $Q_z$ around the top plate, left web, bottom plate and remaining half of the right web. Closure introduces a constant cell flow $q_0$:

$$
q=q_b+q_0.
$$

Because the applied force passes through the centroid, its external moment about the centroid is zero. Hence

$$
\oint q_b\,\mathbf r\times d\mathbf s+2A_mq_0=0,
$$

which determines $q_0$. The largest stress occurs at mid-height of the thin right web, where the bending flow and redundant cell flow reinforce:

$$
\boxed{\tau_{max}=53.6\ \mathrm{MPa}}
$$

at

$$
\boxed{y=0,\quad z\approx400\ \mathrm{mm}}.
$$

The thin right web governs even though the thick left web carries a substantial shear flow, because $\tau=q/t$.

