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
> - **Assumptions:** linear elastic, small deflection, pure bending (or transverse load through the shear centre); $x$ along the beam, $y$ downward and $z$ across, origin at the centroid; positive moments give tension on the positive-$y$, positive-$z$ side.
> - **Method:** 1. Centroid, then $I_y$, $I_z$, $I_{yz}$ by the parallel-axis theorem. 2. $M_z$ and $M_y$ at the critical section, with signs from the convention. 3. $\sigma_{xx}$ from the general formula at every corner. 4. Neutral axis from $\sigma_{xx}=0$. 5. Deflections by integrating $v''$ and $w''$ twice.
> - **Common mistakes:** checking only the top and bottom fibres; dropping $I_{yz}$ or getting its sign wrong.
> - **Practise:** [[#Worked example: an angle-section cantilever]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.2 - Bending moment, neutral axis and extreme stress|Tutorial 2 Q1.2]]

Wings, stringers and many optimised aircraft members are not symmetric. A wing idealised as a beam with an aerofoil-like section is the kind of model used for preliminary and dynamic analysis, and its section has no axis of symmetry, so bending theory that assumes a symmetric section no longer applies directly.

A ruler held flat and pressed down at its tip bends straight down. Turned to 45° and pressed down again, it bends down and sideways, because it is far easier to bend about its thin direction, so the tip slides off that way. An unsymmetrical section behaves like the twisted ruler without being twisted. Its easy and hard bending directions, the principal axes, are not aligned with the load, so a vertical load produces a sideways deflection as well. The neutral axis tilts accordingly, and the most highly stressed fibre is the one furthest from that tilted line, not necessarily the top or bottom of the section.

For linear elastic, small deformations, bending in two perpendicular planes can be superposed, which is what produces the general stress formula. The neutral axis always passes through the centroid, so all section properties are taken about centroidal axes.

## 1. The tilted rectangle

A cantilever of length $L$ has a rectangular section rotated by $\theta$ and carries a vertical tip load $W$. Along the rectangle's own axes $(y,z)$ bending is uncoupled, so resolve the load into those directions and use the cantilever result $PL^3/3EI$ for each component, with the second moment about the axis of bending:

$$
\delta_y=\frac{W\cos\theta\,L^3}{3EI_z},\qquad\delta_z=\frac{W\sin\theta\,L^3}{3EI_y}.
$$

Resolve these back into the vertical ($u$) and horizontal ($v$) directions:

$$
\delta_u=\delta_y\cos\theta+\delta_z\sin\theta=\frac{WL^3}{3E}\left(\frac{\cos^2\theta}{I_z}+\frac{\sin^2\theta}{I_y}\right),
$$

$$
\delta_v=-\delta_y\sin\theta+\delta_z\cos\theta=\frac{WL^3}{3E}\left(\frac1{I_y}-\frac1{I_z}\right)\sin\theta\cos\theta .
$$

Unless $\theta=0$ or $90°$, or $I_y=I_z$, the sideways deflection $\delta_v$ is not zero. Use $\cos^2\theta=\tfrac12(1+\cos2\theta)$, $\sin^2\theta=\tfrac12(1-\cos2\theta)$ and $\sin\theta\cos\theta=\tfrac12\sin2\theta$, and define

$$
A=\frac{WL^3}{6E}\left(\frac1{I_z}+\frac1{I_y}\right),\qquad B=\frac{WL^3}{6E}\left(\frac1{I_z}-\frac1{I_y}\right).
$$

Then

$$
\delta_u=A+B\cos2\theta,\qquad\delta_v=-B\sin2\theta,
$$

and squaring and adding eliminates $\theta$:

$$
(\delta_u-A)^2+\delta_v^2=B^2 .
$$

As the section is rotated, the tip traces a circle of radius $|B|$ centred at $(A,0)$, a Mohr's circle for displacement. The sign of $\delta_v$ depends only on which way $v$ is taken as positive (the course convention writes $+B\sin2\theta$). The sideways deflection is largest at $\theta=45°$, where $|\delta_v|=|B|$.

A pure moment on an unsymmetrical section causes no twist. A transverse load causes twist too unless it passes through the shear centre ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]). A vertical tip load on an unsymmetrical cantilever therefore produces a horizontal as well as a vertical tip deflection, and the two are coupled.

## 2. Sign convention

The axes are $x$ along the beam, $y$ downward and $z$ across, with the origin at the centroid. A positive bending moment produces tensile (positive) stress on the positive side of the axis: positive $M_z$ gives tension at positive $y$, and positive $M_y$ gives tension at positive $z$, so both are positive when the quadrant of positive $y$ and $z$ is in tension. With $y$ downward a sagging moment is positive, and the hogging moment at the root of a downward-loaded cantilever is negative. Double-headed arrows denote moments and single arrows forces.

## 3. The neutral axis passes through the centroid

In a beam bent into an arc of radius $R$ about its neutral axis, a fibre on the neutral axis keeps its length $R\,d\theta$, and a fibre at distance $r$ from it, of the same original length, becomes $(R+r)\,d\theta$, so its strain is

$$
\varepsilon_{xx}=\frac{(R+r)\,d\theta-R\,d\theta}{R\,d\theta}=\frac rR,
$$

and by Hooke's law its stress is

$$
\sigma_{xx}=E\frac rR .
$$

In pure bending there is no axial force on the section:

$$
\int_A\sigma_{xx}\,dA=\frac ER\int_Ar\,dA=0 .
$$

$E/R$ is not zero, so

$$
\int_Ar\,dA=0 .
$$

The first moment of area about the neutral axis vanishes, which is the definition of the centroid. The neutral axis passes through the centroid for any section shape, and the axes are always taken through it.

## 4. The general bending stress

Split the deformation into bending in the $x$–$y$ plane with radius of curvature $R_y$ and bending in the $x$–$z$ plane with radius $R_z$, and superpose the two, which is valid for linear elastic, small deformations.

### Bending in the x–y plane

The strain at height $y$ is $y/R_y$, so

$$
\sigma_{xx}=E\frac{y}{R_y}.
$$

The moments are the stress resultants. About $z$, each element's force $\sigma_{xx}\,dA$ acts at lever arm $y$:

$$
M_z=\int_A\sigma_{xx}y\,dA=\frac{E}{R_y}\int_Ay^2\,dA=\frac{EI_z}{R_y}.
$$

About $y$, the lever arm is $z$:

$$
M_y=\int_A\sigma_{xx}z\,dA=\frac{E}{R_y}\int_Ayz\,dA=\frac{EI_{yz}}{R_y}.
$$

Here $I_z=\int y^2\,dA$, $I_y=\int z^2\,dA$ and $I_{yz}=\int yz\,dA$. Curvature in one plane needs moments about both axes unless $I_{yz}=0$.

### Bending in the x–z plane

Likewise $\sigma_{xx}=Ez/R_z$, and

$$
M_y=\int_A\sigma_{xx}z\,dA=\frac{EI_y}{R_z},\qquad M_z=\int_A\sigma_{xx}y\,dA=\frac{EI_{yz}}{R_z}.
$$

### Superposition

Add the two bending cases:

$$
M_z=E\left(\frac{I_z}{R_y}+\frac{I_{yz}}{R_z}\right),\qquad M_y=E\left(\frac{I_{yz}}{R_y}+\frac{I_y}{R_z}\right).
$$

These are two linear equations for the two curvatures. Multiply the first by $I_y$ and the second by $I_{yz}$:

$$
M_zI_y=E\left(\frac{I_yI_z}{R_y}+\frac{I_yI_{yz}}{R_z}\right),\qquad M_yI_{yz}=E\left(\frac{I_{yz}^2}{R_y}+\frac{I_yI_{yz}}{R_z}\right).
$$

Subtract, and the $1/R_z$ terms cancel:

$$
M_zI_y-M_yI_{yz}=\frac{E}{R_y}\left(I_yI_z-I_{yz}^2\right)\quad\Longrightarrow\quad\frac1{R_y}=\frac{M_zI_y-M_yI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)} .
$$

Multiplying the first equation by $I_{yz}$ and the second by $I_z$ and subtracting in the same way gives

$$
\frac1{R_z}=\frac{M_yI_z-M_zI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)} .
$$

The total stress is the sum of the two planes' contributions:

$$
\sigma_{xx}=E\left(\frac{y}{R_y}+\frac{z}{R_z}\right).
$$

Substitute the curvatures; the $E$ cancels:

$$
\boxed{\sigma_{xx}=\frac{\left(M_zI_y-M_yI_{yz}\right)y+\left(M_yI_z-M_zI_{yz}\right)z}{I_yI_z-I_{yz}^2}}
$$

The stress depends on the position $(y,z)$ from the centroid, on all three section properties and on both moments. If $y$ or $z$ is an axis of symmetry, $I_{yz}=0$ and the denominator is $I_yI_z$, so the formula reduces to the familiar

$$
\sigma_{xx}=\frac{M_zy}{I_z}+\frac{M_yz}{I_y}.
$$

## 5. The neutral axis

The neutral axis is where $\sigma_{xx}=0$. The denominator is positive, so

$$
\left(M_zI_y-M_yI_{yz}\right)y+\left(M_yI_z-M_zI_{yz}\right)z=0 .
$$

This is a straight line through the centroid. Its angle $\phi$ to the $z$ axis follows from $\tan\phi=y/z$ on the line:

$$
\tan\phi=\frac yz=-\frac{M_yI_z-M_zI_{yz}}{M_zI_y-M_yI_{yz}} .
$$

For a moment about $z$ alone ($M_y=0$) this simplifies to

$$
\tan\phi=\frac{I_{yz}}{I_y},
$$

so the neutral axis tilts away from the $z$ axis whenever $I_{yz}\ne0$, even though the moment is about $z$. The beam bends about this line, and the largest tensile and compressive stresses are at the points furthest from it, which for an unsymmetrical section need not be the top and bottom fibres. In practice, evaluate $\sigma_{xx}$ at every corner of the section ([[Neutral Axis in Unsymmetrical Bending]]).

## 6. Deflection

For a symmetric beam, $d^2v/dx^2=-M_z/EI_z$ with $y$ downward. In general the curvature of each plane is the second derivative of the corresponding displacement, with the same sign convention:

$$
\frac{d^2v}{dx^2}=-\frac1{R_y}=-\frac{M_zI_y-M_yI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)},\qquad\frac{d^2w}{dx^2}=-\frac1{R_z}=-\frac{M_yI_z-M_zI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)} .
$$

Each is integrated twice with the boundary conditions, as for a symmetric beam. With $I_{yz}\ne0$, a moment $M_z$ alone still gives $w''\ne0$: the deflection is coupled. If the section varies along the span, $I_y$, $I_z$ and $I_{yz}$ stay inside the integrals as functions of $x$.

For $M_y=0$ the two curvatures are in the ratio

$$
\frac{w''}{v''}=\frac{-M_zI_{yz}}{M_zI_y}=-\frac{I_{yz}}{I_y},
$$

so the deflection $(v,w)$ points along $(I_y,-I_{yz})$. The neutral axis points along $(y,z)\propto(I_{yz},I_y)$, and the dot product of the two is $I_yI_{yz}-I_{yz}I_y=0$: the beam deflects perpendicular to its neutral axis, not in the direction of the load.

## 7. Section properties and principal axes

### Composite sections

Divide the section into rectangles. Find the centroid in an arbitrary reference frame $(Y,Z)$, re-express each part's centroid in centroidal coordinates $(y_i,z_i)$, and use the parallel-axis theorem:

$$
I_z=\sum_i\left(I_z^{(i)}+A_iy_i^2\right),\qquad I_y=\sum_i\left(I_y^{(i)}+A_iz_i^2\right),\qquad I_{yz}=\sum_i\left(I_{yz}^{(i)}+A_iy_iz_i\right),
$$

where a rectangle $b$ wide (along $z$) and $h$ deep (along $y$) has $I_z^{(i)}=bh^3/12$, $I_y^{(i)}=hb^3/12$ and, aligned with the axes, $I_{yz}^{(i)}=0$ ([[Second Moments of Area]]). The sign of $I_{yz}$ comes from the signs of $y_i$ and $z_i$ in the stated axes: parts in the $(+,+)$ and $(-,-)$ quadrants add to it, parts in the mixed quadrants subtract.

### Rotation of axes

Rotate the axes by $\theta$. A point's coordinates in the rotated frame are

$$
y'=y\cos\theta+z\sin\theta,\qquad z'=z\cos\theta-y\sin\theta .
$$

Square the first and integrate over the area:

$$
I_{z'}=\int_Ay'^2\,dA=\cos^2\theta\int_Ay^2\,dA+2\sin\theta\cos\theta\int_Ayz\,dA+\sin^2\theta\int_Az^2\,dA .
$$

So

$$
I_{z'}=I_z\cos^2\theta+2I_{yz}\sin\theta\cos\theta+I_y\sin^2\theta .
$$

Apply the double-angle identities:

$$
I_{z'}=\frac{I_z+I_y}{2}+\frac{I_z-I_y}{2}\cos2\theta+I_{yz}\sin2\theta .
$$

In the same way, $I_{y'}=\int z'^2\,dA$ gives

$$
I_{y'}=\frac{I_z+I_y}{2}-\frac{I_z-I_y}{2}\cos2\theta-I_{yz}\sin2\theta .
$$

For the product, multiply the two coordinates:

$$
y'z'=yz\cos^2\theta-y^2\sin\theta\cos\theta+z^2\sin\theta\cos\theta-yz\sin^2\theta .
$$

Integrate:

$$
I_{y'z'}=I_{yz}\left(\cos^2\theta-\sin^2\theta\right)+\left(I_y-I_z\right)\sin\theta\cos\theta=\frac{I_y-I_z}{2}\sin2\theta+I_{yz}\cos2\theta .
$$

Every rotated property depends on all three original ones, and adding the first two shows that $I_{y'}+I_{z'}=I_y+I_z$ for every $\theta$.

### Principal axes

The principal axes are those for which the product vanishes, $I_{y'z'}=0$:

$$
\frac{I_z-I_y}{2}\sin2\theta_1=I_{yz}\cos2\theta_1\quad\Longrightarrow\quad\tan2\theta_1=\frac{2I_{yz}}{I_z-I_y}.
$$

The same angle makes $I_{z'}$ stationary: $dI_{z'}/d\theta=-(I_z-I_y)\sin2\theta+2I_{yz}\cos2\theta=2I_{y'z'}$, which is zero at $\theta_1$. So the principal axes, two angles $90°$ apart, carry the extreme second moments. At $\theta_1$, with $\rho=\sqrt{\left(\tfrac{I_z-I_y}{2}\right)^2+I_{yz}^2}$, $\cos2\theta_1=\tfrac{I_z-I_y}{2\rho}$ and $\sin2\theta_1=\tfrac{I_{yz}}{\rho}$, and substituting into $I_{z'}$:

$$
I_{max,min}=\frac{I_z+I_y}{2}\pm\sqrt{\left(\frac{I_z-I_y}{2}\right)^2+I_{yz}^2}
$$

([[Principal Axes of a Section]]). Loading along a principal axis gives deflection only in the load's direction, with no cross-deflection, and bending about the $I_{max}$ axis gives the smallest deflection. To avoid sideways movement, use a symmetric section or load along a principal axis.

The rotation formulae have the same form as the stress-transformation equations, so the second moments can be plotted on a Mohr's circle of centre $\tfrac12(I_y+I_z)$ and radius $\rho$: the point $(I_z,I_{yz})$ and the point $(I_y,-I_{yz})$ lie at the ends of a diameter, and the circle crosses the axis at $I_{max}$ and $I_{min}$.

## Worked example: an angle-section cantilever

A 1 m cantilever of inverted-L section carries a uniform load of 10 kN/m downward. The section is a 200 × 20 mm web with a 100 × 20 mm flange along its top, extending to one side, so the overall width is 120 mm. Find the maximum bending stress, the tip deflections, and the rotation of the section that minimises the deflection.

### Section properties

The reference origin is at the top corner on the outer face of the web, with $Y$ downward and $Z$ across, the flange running towards negative $Z$. The flange has $A_1=100\times20=2000$ mm² with its centroid at $(Y_1,Z_1)=(10,-70)$; the web has $A_2=20\times200=4000$ mm² at $(Y_2,Z_2)=(100,-10)$. The centroid is

$$
Y_c=\frac{2000\times10+4000\times100}{6000}=70\text{ mm},\qquad Z_c=\frac{2000\times(-70)+4000\times(-10)}{6000}=-30\text{ mm}.
$$

So the centroid is 70 mm below the top and 30 mm in from the web's outer face. In centroidal coordinates the flange centroid is at $(y_1,z_1)=(10-70,\,-70+30)=(-60,-40)$ and the web's at $(30,20)$.

About $z$ (lever arm $y$):

$$
I_z=\frac{100\times20^3}{12}+2000\times60^2+\frac{20\times200^3}{12}+4000\times30^2=(0.067+7.2+13.333+3.6)\times10^6=24.2\times10^6\text{ mm}^4 .
$$

About $y$ (lever arm $z$):

$$
I_y=\frac{20\times100^3}{12}+2000\times40^2+\frac{200\times20^3}{12}+4000\times20^2=(1.667+3.2+0.133+1.6)\times10^6=6.6\times10^6\text{ mm}^4 .
$$

The product, with both parts' own $I_{yz}^{(i)}=0$:

$$
I_{yz}=2000(-60)(-40)+4000(30)(20)=(4.8+2.4)\times10^6=7.2\times10^6\text{ mm}^4 .
$$

Both parts lie in the $(-,-)$ and $(+,+)$ quadrants, so $I_{yz}$ is positive. The denominator of the stress formula is

$$
I_yI_z-I_{yz}^2=(6.6\times24.2-7.2^2)\times10^{12}=107.9\times10^{12}\text{ mm}^8 .
$$

### Stress at the root

At the root the hogging moment is

$$
M_z=-\frac{wL^2}{2}=-\frac{10\times1000^2}{2}=-5\times10^6\text{ N mm},
$$

with $M_y=0$ since all the load is in $y$. The general formula reduces to

$$
\sigma_{xx}=\frac{M_z\left(I_yy-I_{yz}z\right)}{I_yI_z-I_{yz}^2}.
$$

Substitute the numbers:

$$
\sigma_{xx}=\frac{-5\times10^6\left(6.6\times10^6\,y-7.2\times10^6\,z\right)}{107.9\times10^{12}}=-0.306\,y+0.334\,z\ \text{MPa}\quad(y,z\text{ in mm}).
$$

Evaluate it at the corners:

| Corner | $(y,z)$ (mm) | $\sigma_{xx}$ (MPa) |
|---|---|---|
| P, top of the web's outer face | $(-70,30)$ | $+31.4$ |
| Q, bottom of the outer face | $(130,30)$ | $-29.8$ |
| S, bottom of the inner face | $(130,10)$ | $-36.4$ |
| R, flange tip, top | $(-70,-90)$ | $-8.6$ |
| T, flange tip, underside | $(-50,-90)$ | $-14.7$ |

The maximum tension is 31.4 MPa at P and the maximum compression 36.4 MPa at S, the bottom inner corner of the web. The neutral axis is $-0.306y+0.334z=0$, that is $y=1.09z$, tilted $47.5°$ from the $z$ axis, and S is the corner furthest from it on the compressive side. The top of the web is in tension and its bottom in compression, as for a hogging cantilever, but the flange tip, at the top, is in compression: a symmetric-bending estimate would get its sign wrong.

![[structures_s1_angle_section.png|900]]

### Tip deflection

Measuring $x$ from the root, $M_z(x)=-w(L-x)^2/2$ and $M_y=0$. The deflection equations become

$$
v''=-\frac{M_zI_y}{E\left(I_yI_z-I_{yz}^2\right)}=\frac{wI_y(L-x)^2}{2E\left(I_yI_z-I_{yz}^2\right)},\qquad w''=\frac{M_zI_{yz}}{E\left(I_yI_z-I_{yz}^2\right)}=-\frac{wI_{yz}(L-x)^2}{2E\left(I_yI_z-I_{yz}^2\right)} .
$$

The root is clamped, so $v=v'=w=w'=0$ at $x=0$. Integrating $(L-x)^2$ once with zero slope at the root gives $\tfrac13\left[L^3-(L-x)^3\right]$, and again with zero deflection gives $\tfrac13\left[L^3x+\tfrac14(L-x)^4-\tfrac14L^4\right]$, which at $x=L$ is $\tfrac13\cdot\tfrac34L^4=L^4/4$. So

$$
v_{tip}=\frac{wI_yL^4}{8E\left(I_yI_z-I_{yz}^2\right)},\qquad w_{tip}=-\frac{wI_{yz}L^4}{8E\left(I_yI_z-I_{yz}^2\right)} .
$$

The problem specifies no modulus. For aluminium, $E=70$ GPa:

$$
v_{tip}=\frac{10\times6.6\times10^6\times10^{12}}{8\times70\,000\times107.9\times10^{12}}=1.09\text{ mm},\qquad w_{tip}=-\frac{10\times7.2\times10^6\times10^{12}}{8\times70\,000\times107.9\times10^{12}}=-1.19\text{ mm}.
$$

The vertical load moves the tip further sideways (towards the flange side) than down. For steel ($E=200$ GPa) the values are 0.38 and $-0.42$ mm.

> [!check] Deflection perpendicular to the neutral axis
> $w_{tip}/v_{tip}=-I_{yz}/I_y=-1.09$, so the tip moves along a line $42.5°$ below the $-z$ direction, while the neutral axis has slope $y/z=+1.09$. The two directions are perpendicular, the general result of [[#6. Deflection]]. A symmetric section of the same $I_z$ would deflect only $wL^4/8EI_z=0.74$ mm (aluminium), straight down.

### Minimum-deflection orientation

To minimise the deflection, align the stiffest principal axis so that the load bends the beam about it:

$$
\tan2\theta_1=\frac{2\times7.2}{24.2-6.6}=0.818\quad\Longrightarrow\quad2\theta_1=39.3°,\quad\theta_1=19.6° .
$$

The principal values are

$$
I_{max,min}=\frac{24.2+6.6}{2}\pm\sqrt{\left(\frac{24.2-6.6}{2}\right)^2+7.2^2}=15.4\pm11.37=26.8,\ 4.03\times10^6\text{ mm}^4 .
$$

Rotating the section by $19.6°$ about $x$ puts the $I_{max}$ axis perpendicular to the load. The beam then bends about that axis alone: the deflection is the smallest possible and there is no sideways component.

> [!check] Invariant and limiting values
> $I_{max}+I_{min}=30.8\times10^6=I_y+I_z$, as the rotation formulae require, and $I_{max}=26.8>I_z=24.2$, so the rotation does stiffen the beam. In the principal orientation the aluminium tip deflection would be $wL^4/8EI_{max}=0.67$ mm, down only.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Next: [[SESA2028 S2 - Beam Deflection and Bending Design]] · [[SESA2028 S3 - Shear Flow and Shear Centre]]
- Concepts: [[Second Moments of Area]] · [[Principal Axes of a Section]] · [[Principal Second Moments of Area]] · [[Unsymmetrical Bending]] · [[Neutral Axis in Unsymmetrical Bending]] · [[Moment Curvature Relation]]
- Problems: [[SESA2028 Structures Tutorial 2 - Bending Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Year 1 foundation: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] (symmetric bending, parallel-axis theorem) · [[FEEG1002 A9 - Shear Stresses in Beams]]
- Energy methods with this stress field: [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

## Sources

- Slides: `SL2 Bending stress and deflection.pdf` (the 2025–26 deck for SL7–SL8; derivation on slides 10–23, section properties 25–33, angle-section example 28–37).
- Transcripts: `SESA2028 Lecture 2026-02-25 - SL7 Asymmetric Beam.txt` (tilted rectangle, sign convention, neutral axis, general stress) and `SESA2028 Lecture 2026-02-27.txt` (ll. 1–290: rotation of axes, deflection, the worked example).
- The worked example was recomputed in Python (section properties, corner stresses, deflections, principal values); the modulus is assumed because the slide omits it. Figures: `generate_structures_s1_figures.py` (angle section and its Mohr's circle).

## Self-study tasks

### Core

- [ ] Derive the general bending stress and the neutral-axis angle by superposing the two planes of bending (2026-02-25, ll. 261–380). → [[#4. The general bending stress]] · [[#5. The neutral axis]]
- [ ] The angle-section cantilever: maximum stress, tip deflections and the minimum-deflection rotation (SL2 slide 37, "Example – have a go first!"; solved 2026-02-27, ll. 150–245). → [[#Worked example: an angle-section cantilever]]
- [ ] Structures tutorial 2, the Z-section: properties, neutral axis, extreme stress and coupled deflection. → [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.1 - Properties and principal axes of the Z-section|Q1.1]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.3 - Coupled tip deflection|Q1.3]]
- [ ] Structures lab: measure the vertical and horizontal deflections of an unsymmetrical section and compare with theory (2026-02-25, ll. 61–67; lab video before the session, 2026-02-27, ll. 434–436). → [[#1. The tilted rectangle]] · [[#6. Deflection]]

### Further practice

- [ ] Derive the rotated second moments and the principal-axis angle from the coordinate rotation; the geometry was left to do yourself (2026-02-27, ll. 41–60). → [[#Rotation of axes]] · [[#Principal axes]]
- [ ] Find the angle-section tip deflection by an energy method using the general stress field, posed as a thought question (2026-02-27, ll. 265–290). → [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
- [ ] Show that the tilted-rectangle tip traces a circle, and find the angle of greatest sideways deflection (suggested, not lecturer-set). → [[#1. The tilted rectangle]]
