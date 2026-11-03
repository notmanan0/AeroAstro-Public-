---
title: "SESA2028 S1 - Section Properties and Unsymmetrical Bending"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 1
tags: [sesa2028, structures, bending, principal-axes]
date: 2026-10-30
status: lectured
coverage: "SL7 (2026-02-25) and SL8 (2026-02-27, ll. 1–290)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]", "[[SESA2028 S3 - Shear Flow and Shear Centre]]"]
key_concepts: ["[[Second Moments of Area]]", "[[Principal Axes of a Section]]", "[[Unsymmetrical Bending]]", "[[Neutral Axis in Unsymmetrical Bending]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 2 - Bending Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL2 Bending stress and deflection.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-25 - SL7 Asymmetric Beam.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-27.txt"]
---

# SESA2028 S1 - Section Properties and Unsymmetrical Bending

> [!abstract] Summary
> A beam whose cross-section has no axis of symmetry bends in both transverse directions even when the moment acts about one axis only, because the product second moment $I_{yz}$ couples the two planes of bending. Superposing bending in the $x$–$y$ and $x$–$z$ planes gives one stress formula, $\sigma_{xx}=[(M_zI_y-M_yI_{yz})y+(M_yI_z-M_zI_{yz})z]/(I_yI_z-I_{yz}^2)$, whose zero line is the neutral axis, generally tilted to the load, with the extreme stresses at the points furthest from it. Rotating to the principal axes, where $I_{yz}=0$, removes the coupling and gives the maximum and minimum second moments.

> [!summary]- Exam use: quick path
> - **Use it when:** an angle, Z or other unsymmetrical section is loaded in bending and you need the stress, neutral axis, deflection or principal axes.
> - **Assumptions:** linear elastic, small deflection, pure bending (or shear through the shear centre), $y$ downward and $z$ to the right through the centroid, positive moments giving tension on the positive-$y$, positive-$z$ side.
> - **Method:** 1. Centroid and $I_y$, $I_z$, $I_{yz}$ by the parallel-axis theorem. 2. $M_z$ and $M_y$ at the critical section, with signs from the convention. 3. $\sigma_{xx}$ from the general formula at every corner. 4. Neutral axis from $\sigma_{xx}=0$. 5. Deflections by integrating $v''$ and $w''$ twice.
> - **Common mistakes:** checking only the top and bottom fibres; dropping $I_{yz}$ or its sign.
> - **Practise:** [[#Worked example: an angle-section cantilever]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.2 - Bending moment, neutral axis and extreme stress|Tutorial 2 Q1.2]]

Wings, stringers and many optimised aircraft members are not symmetric, and the motivation in the lecture was a simplified wing idealised as a beam with an aerofoil-like section, the kind of model industry uses for preliminary and dynamic analysis (2026-02-25, ll. 1–20).

The physical picture starts with a tilted ruler. Hold a ruler flat and press down on its tip: it bends straight down. Twist it to 45° and press down again: it bends down and sideways, because it is far easier to bend about its thin direction, so the tip slides off towards that direction. An unsymmetrical section behaves the same way without being twisted: its "easy" and "hard" bending directions, the principal axes, are not aligned with the load, so a vertical load produces a sideways deflection too. The neutral axis tilts accordingly, and the most highly stressed fibre is the one furthest from that tilted line, not simply the top or bottom of the section.

## 1. The tilted rectangle

Take a cantilever of length $L$ with a rectangular section rotated by $\theta$ and a vertical tip load $W$ (2026-02-25, ll. 61–140). Resolve the load along the section's own axes, where bending is uncoupled, and use the cantilever result $PL^3/3EI$ for each component, with the second moment about the axis of bending:

$$
\delta_y=\frac{W\cos\theta\,L^3}{3EI_z},
\qquad
\delta_z=\frac{W\sin\theta\,L^3}{3EI_y}.
$$

Resolve these back into the vertical ($u$) and horizontal ($v$) directions:

$$
\delta_u=\delta_y\cos\theta+\delta_z\sin\theta=\frac{WL^3}{3E}\left(\frac{\cos^2\theta}{I_z}+\frac{\sin^2\theta}{I_y}\right),
$$

$$
\delta_v=-\delta_y\sin\theta+\delta_z\cos\theta=\frac{WL^3}{3E}\left(\frac1{I_y}-\frac1{I_z}\right)\sin\theta\cos\theta .
$$

Unless $\theta=0$ or $90°$, or $I_y=I_z$, the sideways deflection $\delta_v$ is not zero. With $A=\frac{WL^3}{6E}\left(\frac1{I_z}+\frac1{I_y}\right)$ and $B=\frac{WL^3}{6E}\left(\frac1{I_z}-\frac1{I_y}\right)$, the double-angle forms are

$$
\delta_u=A+B\cos2\theta,
\qquad
\delta_v=-B\sin2\theta,
$$

so $(\delta_u-A)^2+\delta_v^2=B^2$: plotting the tip deflection as the section is rotated traces a circle of radius $B$ centred at $(A,0)$, a "Mohr's circle" for displacement (ll. 101–140). The lecture writes $\delta_v=B\sin2\theta$; the sign depends only on which way $v$ is taken as positive.

A pure moment on an unsymmetrical section causes no twist; a transverse load causes twist too unless it passes through the shear centre ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]; ll. 21–60).

## 2. Sign convention

The axes are $x$ along the beam, $y$ downward and $z$ across, with the origin at the centroid (2026-02-25, ll. 141–200). A positive bending moment produces tensile (positive) stress on the positive side of the axis: positive $M_z$ gives tension at positive $y$, positive $M_y$ gives tension at positive $z$, so both are positive when the quadrant of positive $y$ and $z$ is in tension. With $y$ downward, a sagging moment is positive and the hogging moment at the root of a downward-loaded cantilever is negative. Double-headed arrows denote moments, single arrows forces.

## 3. The neutral axis passes through the centroid

Bend a beam into an arc of radius $R$ about its neutral axis. A fibre at distance $r$ from the neutral axis, originally of length $R\,d\theta$, becomes $(R+r)\,d\theta$, so its strain and stress are (ll. 221–245)

$$
\varepsilon_{xx}=\frac{(R+r)\,d\theta-R\,d\theta}{R\,d\theta}=\frac rR,
\qquad
\sigma_{xx}=E\frac rR .
$$

In pure bending there is no axial force:

$$
\int_A\sigma_{xx}\,dA=\frac ER\int_Ar\,dA=0
\quad\Longrightarrow\quad
\int_Ar\,dA=0 .
$$

The first moment of area about the neutral axis vanishes, which is the definition of the centroid: the neutral axis passes through the centroid, for any section shape. So the axes are always taken through the centroid.

## 4. The general bending stress

Split the deformation into bending in the $x$–$y$ plane with radius $R_y$ and in the $x$–$z$ plane with radius $R_z$, and superpose, valid for linear elastic, small deformations (ll. 261–340; slides 10–14).

In the $x$–$y$ plane the strain at height $y$ is $y/R_y$, so

$$
\sigma_{xx}=E\frac{y}{R_y}.
$$

The stress resultants are

$$
M_z=\int_A\sigma_{xx}y\,dA=\frac{E}{R_y}\int_Ay^2\,dA=\frac{EI_z}{R_y},
\qquad
M_y=\int_A\sigma_{xx}z\,dA=\frac{E}{R_y}\int_Ayz\,dA=\frac{EI_{yz}}{R_y},
$$

with $I_z=\int y^2\,dA$, $I_y=\int z^2\,dA$ and $I_{yz}=\int yz\,dA$. Curvature in one plane needs moments about both axes unless $I_{yz}=0$. In the $x$–$z$ plane, likewise, $\sigma_{xx}=Ez/R_z$, $M_y=EI_y/R_z$ and $M_z=EI_{yz}/R_z$.

Superpose the two:

$$
M_z=E\left(\frac{I_z}{R_y}+\frac{I_{yz}}{R_z}\right),
\qquad
M_y=E\left(\frac{I_{yz}}{R_y}+\frac{I_y}{R_z}\right).
$$

Solve the pair for the curvatures. Multiply the first by $I_y$ and the second by $I_{yz}$, and subtract:

$$
M_zI_y-M_yI_{yz}=\frac{E}{R_y}\left(I_yI_z-I_{yz}^2\right)
\quad\Longrightarrow\quad
\frac1{R_y}=\frac{M_zI_y-M_yI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)} .
$$

Similarly,

$$
\frac1{R_z}=\frac{M_yI_z-M_zI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)} .
$$

The total stress is $\sigma_{xx}=E(y/R_y+z/R_z)$, so

$$
\boxed{\sigma_{xx}=\frac{\left(M_zI_y-M_yI_{yz}\right)y+\left(M_yI_z-M_zI_{yz}\right)z}{I_yI_z-I_{yz}^2}}
$$

It depends on the position $(y,z)$ from the centroid, the section properties, and both applied moments (slide 15). If either $y$ or $z$ is an axis of symmetry, $I_{yz}=0$ and it reduces to the familiar $\sigma_{xx}=M_zy/I_z+M_yz/I_y$ (slide 18).

## 5. The neutral axis

The neutral axis is where $\sigma_{xx}=0$ (ll. 341–380; slide 17):

$$
\left(M_zI_y-M_yI_{yz}\right)y+\left(M_yI_z-M_zI_{yz}\right)z=0 .
$$

It is a straight line through the centroid at angle $\phi$ to the $z$ axis:

$$
\tan\phi=\frac yz=-\frac{M_yI_z-M_zI_{yz}}{M_zI_y-M_yI_{yz}} .
$$

The beam bends about this line, and the maximum tensile and compressive stresses are at the points furthest from it, which for an unsymmetrical section need not be the top and bottom fibres. In practice, evaluate $\sigma_{xx}$ at every corner of the section ([[Neutral Axis in Unsymmetrical Bending]]).

## 6. Deflection

For a symmetric beam, $d^2v/dx^2=-M_z/EI_z$ with $y$ downward (ll. 381–440; slides 20–23). In general the curvature of each plane is the second derivative of the corresponding displacement, with the same sign:

$$
\frac{d^2v}{dx^2}=-\frac1{R_y}=-\frac{M_zI_y-M_yI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)},
\qquad
\frac{d^2w}{dx^2}=-\frac1{R_z}=-\frac{M_yI_z-M_zI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)} .
$$

Each is integrated twice with the boundary conditions, as for a symmetric beam. With $I_{yz}\neq0$, a moment $M_z$ alone still gives $w''\neq0$: the deflection is coupled. If the section varies along the span, $I_y$, $I_z$ and $I_{yz}$ stay inside the integrals as functions of $x$ (2026-02-27, ll. 246–265).

## 7. Section properties and principal axes

For composite shapes, divide into rectangles, find the centroid in an arbitrary reference frame $(Y,Z)$, re-express each part's centroid in centroidal coordinates $(y_i,z_i)$, and use the parallel-axis theorem (slides 25–27):

$$
I_z=\sum\left(I_z^{(i)}+A_iy_i^2\right),
\qquad
I_y=\sum\left(I_y^{(i)}+A_iz_i^2\right),
\qquad
I_{yz}=\sum\left(I_{yz}^{(i)}+A_iy_iz_i\right),
$$

where a rectangle aligned with the axes has $I_{yz}^{(i)}=0$ ([[Second Moments of Area]]). The sign of $I_{yz}$ follows from the signs of $y_i$ and $z_i$ in the stated axes.

Rotate the axes by $\theta$ (2026-02-27, ll. 41–130; slides 32–33). A point's coordinates in the rotated frame are

$$
y'=y\cos\theta+z\sin\theta,
\qquad
z'=z\cos\theta-y\sin\theta .
$$

Substitute into $I_{z'}=\int y'^2\,dA$:

$$
I_{z'}=I_z\cos^2\theta+I_y\sin^2\theta+2I_{yz}\sin\theta\cos\theta .
$$

With double-angle identities,

$$
I_{z'}=\frac{I_z+I_y}{2}+\frac{I_z-I_y}{2}\cos2\theta+I_{yz}\sin2\theta,
$$

and in the same way

$$
I_{y'}=\frac{I_z+I_y}{2}-\frac{I_z-I_y}{2}\cos2\theta-I_{yz}\sin2\theta,
\qquad
I_{y'z'}=\frac{I_y-I_z}{2}\sin2\theta+I_{yz}\cos2\theta .
$$

Every rotated property depends on all three original ones. The principal axes are where $I_{y'z'}=0$:

$$
\tan2\theta_1=\frac{2I_{yz}}{I_z-I_y},
$$

which gives two angles $90°$ apart, at which the second moments take their extreme values ([[Principal Axes of a Section]]):

$$
I_{max,min}=\frac{I_z+I_y}{2}\pm\sqrt{\left(\frac{I_z-I_y}{2}\right)^2+I_{yz}^2} .
$$

Loading along a principal axis gives deflection only in the load's direction, with no cross-deflection, and bending about the $I_{max}$ axis gives the smallest deflection (ll. 96–130). If unexpected movements are unwanted, use a symmetric section or load along principal axes.

## Worked example: an angle-section cantilever

The lecture's example (slide 37; 2026-02-27, ll. 150–245): a 1 m cantilever of inverted-L section, a 200 × 20 mm web and a flange making 120 mm overall width, carries 10 kN/m downward. Find the maximum bending stress and tip deflections, and the rotation of the section that minimises deflection.

The section properties (slides 28–30): with the reference origin at the top right corner, the flange ($A_1=2000$ mm², centroid $Y_1=10$, $Z_1=-70$) and web ($A_2=4000$ mm², $Y_2=100$, $Z_2=-10$) put the centroid at

$$
Y_c=\frac{2000\times10+4000\times100}{6000}=70\text{ mm},
\qquad
Z_c=\frac{2000\times(-70)+4000\times(-10)}{6000}=-30\text{ mm}.
$$

So the centroid is 70 mm below the top and 30 mm in from the web's outer face, and in centroidal coordinates the flange centroid is at $(y_1,z_1)=(-60,-40)$ and the web's at $(30,20)$. The parallel-axis theorem gives

$$
I_z=\tfrac1{12}\left(20^3\times100+200^3\times20\right)+2000\times60^2+4000\times30^2=24.2\times10^6\text{ mm}^4,
$$

and similarly $I_y=6.6\times10^6$ mm⁴ and $I_{yz}=2000(-60)(-40)+4000(30)(20)=7.2\times10^6$ mm⁴, so

$$
I_yI_z-I_{yz}^2=6.6\times24.2\times10^{12}-7.2^2\times10^{12}=107.9\times10^{12}\text{ mm}^8 .
$$

At the root the hogging moment is $M_z=-wL^2/2=-5\times10^6$ N mm, with $M_y=0$ since all the load is in $y$ (a student asked why; ll. 191–200). The stress reduces to

$$
\sigma_{xx}=\frac{M_z\left(I_yy-I_{yz}z\right)}{I_yI_z-I_{yz}^2}=-0.306\,y+0.334\,z\ \text{MPa}\quad(y,z\text{ in mm}).
$$

At the corners, recomputed in Python: top of the web's outer face P $(-70,30)$, $+31.4$ MPa; bottom of the outer face $(130,30)$, $-29.8$ MPa; bottom of the inner face $(130,10)$, $-36.4$ MPa; flange tip R $(-70,-90)$, $-8.6$ MPa. The maximum tension is 31.4 MPa at P and the maximum compression 36.4 MPa at the bottom inner corner of the web, the corner furthest from the neutral axis $y=1.09z$, which is tilted $47.5°$ from the $z$ axis. The top is in tension and the bottom in compression, as a hogging cantilever should be.

For the tip deflection, $M_z(x)=-w(L-x)^2/2$, so

$$
v''=\frac{wI_y(L-x)^2}{2E\left(I_yI_z-I_{yz}^2\right)},
\qquad
w''=-\frac{wI_{yz}(L-x)^2}{2E\left(I_yI_z-I_{yz}^2\right)} .
$$

With $v=v'=0$ and $w=w'=0$ at the root, integrating $(L-x)^2$ twice gives $L^4/4$ at the tip:

$$
v_{tip}=\frac{wI_yL^4}{8E\left(I_yI_z-I_{yz}^2\right)},
\qquad
w_{tip}=-\frac{wI_{yz}L^4}{8E\left(I_yI_z-I_{yz}^2\right)} .
$$

The slide gives no modulus; for aluminium, $E=70$ GPa, these are $v_{tip}=1.09$ mm down and $w_{tip}=-1.19$ mm sideways: the vertical load moves the tip further sideways than down. For steel ($E=200$ GPa), 0.38 and $-0.42$ mm.

For minimum deflection, align the load with the stiffest principal axis:

$$
\tan2\theta_1=\frac{2\times7.2}{24.2-6.6}=0.818
\quad\Longrightarrow\quad
\theta_1=19.6°,
$$

giving $I_{max}=26.8\times10^6$ and $I_{min}=4.03\times10^6$ mm⁴. Rotating the section by $19.6°$ about $x$ puts the $I_{max}$ axis perpendicular to the load, which gives the least deflection and no sideways deflection (ll. 201–240).

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Next: [[SESA2028 S2 - Beam Deflection and Bending Design]] · [[SESA2028 S3 - Shear Flow and Shear Centre]]
- Concepts: [[Second Moments of Area]] · [[Principal Axes of a Section]] · [[Principal Second Moments of Area]] · [[Unsymmetrical Bending]] · [[Neutral Axis in Unsymmetrical Bending]] · [[Moment Curvature Relation]]
- Year 1 foundation: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] (symmetric bending, parallel-axis theorem) · [[FEEG1002 A9 - Shear Stresses in Beams]]
- Energy methods with this stress field: [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

![[structures_unsymmetric_bending_stress.png|760]]

![[structures_principal_inertia_mohr_circle.png|640]]

## Sources

- Structures slides `SL2 Bending stress and deflection.pdf` (the deck labelled "Lecture 2"; worked example on slides 28–37), with transcripts `SESA2028 Lecture 2026-02-25 - SL7 Asymmetric Beam.txt` and `SESA2028 Lecture 2026-02-27.txt` (ll. 1–290)
- Worked example recomputed in Python; the modulus is assumed because the slide omits it

## Self-study tasks

### Core

- [ ] Derive the general bending stress and the neutral-axis angle by superposing the two planes of bending (2026-02-25, ll. 261–380). → [[#4. The general bending stress]] · [[#5. The neutral axis]]
- [ ] The angle-section cantilever: maximum stress, tip deflections and the minimum-deflection rotation ("Example – have a go first!", slide 37; solved 2026-02-27, ll. 150–245). → [[#Worked example: an angle-section cantilever]]
- [ ] Structures tutorial 2, the Z-section: properties, neutral axis, extreme stress and coupled deflection. → [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.1 - Properties and principal axes of the Z-section|Q1.1]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.3 - Coupled tip deflection|Q1.3]]
- [ ] Structures lab: measure the vertical and horizontal deflections of an unsymmetrical section (announced at 2026-02-25, ll. 61–65). → [[#1. The tilted rectangle]]

### Further practice

- [ ] Derive the rotated second moments and the principal-axis angle ("try to do the simple geometry by yourself", 2026-02-27, ll. 41–60). → [[#7. Section properties and principal axes]]
- [ ] Find the angle-section tip deflection by an energy method using the general stress field (posed as a thought question, 2026-02-27, ll. 265–290). → [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
