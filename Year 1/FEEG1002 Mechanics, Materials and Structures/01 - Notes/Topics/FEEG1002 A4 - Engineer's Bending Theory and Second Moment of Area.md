---
title: "FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 4
tags: [feeg1002, statics, beams, bending-stress, second-moment-of-area, neutral-axis, parallel-axis-theorem]
aliases: ["Statics 1 Lecture 7", "Statics 1 Lecture 8", "Bending stress", "M/I = sigma/y = E/R", "Engineer's bending theory"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 7 (11 Nov 2024, ll. 1–869: pure bending, strain and stress through the depth, neutral axis at the centroid, second moment of area, engineer's bending theory, rectangle and I-section, cantilever stress, superposition) and Lecture 8 (18 Nov 2024, ll. 1–757: general and asymmetric sections, circle, parallel axis theorem, I-beam, practical implications, channel section); slide decks 7 and 8 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
next_topics: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
key_concepts: ["[[Engineer's Bending Theory]]", "[[Parallel Axis Theorem]]", "[[Second Moments of Area]]", "[[First Moment of Area]]", "[[Section Modulus]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 07 - Beams, Stress Due to Bending.pdf"
  - "02 - Sources/Statics 1/Lectures/Lecture 08 - Beams, Second Moment of Area Continued.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 7 - Statics 1 - Stresses due to bending - November 2024.txt"
  - "02 - Sources/Lectures/FEEG1002 Lecture 8 - Statics 1 - Second moment of area continuedNovember 2024.txt"
  - "02 - Sources/Lectures/FEEG1002 Lecture 2020-10-29.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 04 - Beams, Stress and 2nd Moment of Area.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 04 - Beams, Stress and 2nd Moment of Area - Solutions.pdf"
---

# FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area

> [!abstract] Summary
> Under pure bending a beam bends into a circular arc and its plane cross-sections stay plane, so the longitudinal strain grows linearly with distance from a neutral surface, $\varepsilon_{xx}=y/R$, and so does the stress, $\sigma_{xx}=Ey/R$. Zero net axial force puts the neutral axis through the centroid of the section, and the moment of the stresses gives $M=EI/R$, where $I_{zz}=\iint y^2\,dy\,dz$ is the second moment of area. Together these are engineer's bending theory, $M/I=\sigma/y=E/R$, usually used as $\sigma=My/I$. The parallel axis theorem, $I_{z'z'}=I_{zz}+Ab^2$, builds $I$ for composite sections and explains why I-beams and tubes, which put material far from the neutral axis, are so efficient.

> [!summary]- Exam use: quick path
> - **Use it when:** the maximum bending stress in a beam is needed, a section must be sized for an allowable stress, or $I$ of a built-up section is required.
> - **Assumptions:** plane sections remain plane; radius of curvature much larger than the depth; stresses longitudinal only; linear elastic with the same $E$ in tension and compression; section symmetric about the plane of loading; strictly pure bending, but shear has negligible effect on slender beams. $y$ is measured downwards from the neutral axis.
> - **Method:** 1. Draw the BM diagram and find $M_{max}$ with its sign. 2. Locate the centroid, by symmetry or by $A\bar d=\sum A_id_i$. 3. Find $I_{zz}$ about the centroid with $bd^3/12$ for each part plus $Ab^2$. 4. Find the distance to the extreme fibre on each side of the neutral axis. 5. Evaluate $\sigma=My/I$ at each and compare with the allowable stress (separately for tension and compression if they differ).
> - **Common mistakes:** forgetting to square the offset in $Ab^2$; using the mid-height instead of the centroid as the neutral axis for an unsymmetrical section.
> - **Practise:** [[#Worked example - channel section]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Q3 - Inverted-T cantilever hoist|Tutorial 4 Q3]]

The shear force and bending moment of [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams|A3]] are only resultants. Inside the beam they are carried by stresses: normal (longitudinal) stresses produce the bending moment, and shear stresses produce the shear force. The load a beam can carry depends on those stresses, and in particular on the largest of them. The stresses due to bending are derived below, and the shear stresses are in [[FEEG1002 A9 - Shear Stresses in Beams|A9]].

A straight beam bent by equal and opposite moments at its ends, with no shear force, is in pure bending. A grid of lines drawn on its side before loading shows the deformation: the longitudinal lines become concentric arcs and the vertical lines stay straight but tilt towards the centre of curvature. The arcs on the inside of the bend are shorter than they were and those on the outside are longer, so the top of a sagging beam is squeezed and the bottom stretched. Somewhere in between is a surface whose length does not change. Everything in bending theory follows from that picture, plus Hooke's law and equilibrium.

The result has a geometric quantity at its heart, the second moment of area $I$, which measures how much of the cross-section lies far from the neutral axis. Material near the axis is barely stretched and does little; material far from it is stretched a lot, and also acts with a long lever arm. That is why a ruler is easy to bend flat and hard to bend on edge, why steel beams are I-shaped and why bicycle frames are tubes.

---

## 1. Deformation in pure bending

### Assumptions

Consider an initially straight beam with a cross-section of any shape that is symmetric about the plane of loading, subject to pure bending: a constant moment and no shear force. The analysis assumes:

- plane cross-sections remain plane under the loading;
- the beam is bent into a circular arc;
- the radius of curvature is large compared with the depth of the beam (steel beams are not bent double);
- the tensile and compressive stresses are longitudinal;
- the beam is linear elastic, with the same Young's modulus $E$ in tension and compression.

### Neutral surface and neutral axis

Take a short element of the beam with upper surface $A_1B_1$ and lower surface $A_2B_2$. Under a sagging moment the lower surface stretches to $A_2'B_2'$ and is in tension, and the upper surface shortens to $A_1'B_1'$ and is in compression. Somewhere in between there must be a surface whose length stays the same, $A_0'B_0'=A_0B_0$: the **neutral surface**. The **neutral axis** is the line where the neutral surface cuts the cross-section. The distance $y$ is measured from the neutral surface, positive downwards, and the radius of curvature $R$ is measured from the centre of curvature to the neutral surface.

### Longitudinal strain

Let the element subtend a small angle $d\theta$ at the centre of curvature. The neutral surface keeps its length, so

$$
AB=A_0B_0=A_0'B_0'=R\,d\theta
$$

where $AB$ is the original length of any fibre in the element. A fibre a distance $y$ below the neutral surface (further from the centre of curvature) lies on an arc of radius $R+y$, so its new length is

$$
A'B'=(R+y)\,d\theta
$$

Its strain is the change in length over the original length:

$$
\varepsilon_{xx}=\frac{A'B'-AB}{AB}
$$

$$
\varepsilon_{xx}=\frac{(R+y)\,d\theta-R\,d\theta}{R\,d\theta}
$$

$$
\boxed{\varepsilon_{xx}=\frac yR}
$$

The strain varies linearly with $y$ through the depth: zero on the neutral surface, positive (tension) below it in a sagging beam, negative above it, and largest at the outer surfaces.

![[s1_bending_strain_geometry.png|900]]

### Anticlastic curvature

The longitudinal strain is accompanied by a Poisson's ratio effect ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Poisson's ratio|A1]]):

$$
\varepsilon_{yy}=-\nu\varepsilon_{xx},\qquad\varepsilon_{zz}=-\nu\varepsilon_{xx}
$$

The stretched lower fibres contract sideways and the compressed upper fibres expand, so the cross-section itself curves the opposite way to the beam. This secondary curve is **anticlastic curvature**. It matters in bridge design, where it would put camber into the road surface.

### Longitudinal stress

With $\sigma_{yy}=\sigma_{zz}=0$ the stress is uniaxial, and Hooke's law reduces to

$$
\sigma_{xx}=E\varepsilon_{xx}
$$

$$
\sigma_{xx}=\frac{Ey}{R}
$$

The stress varies linearly over the depth and is largest on the outer surfaces. The bending moment $M$ is the resultant of these stresses, exerted on the cut face by the material on the other side.

## 2. Equilibrium of the cross-section

### Force equilibrium: the neutral axis passes through the centroid

Take axes with $x$ along the beam, $y$ downwards and $z$ across the section along the neutral axis. A small element of the section, of area $dy\,dz$, carries a longitudinal force $\sigma_{xx}\,dy\,dz$. In pure bending there is no axial force, so the total over the section must vanish:

$$
F=\iint\sigma_{xx}\,dy\,dz=0
$$

Substitute $\sigma_{xx}=Ey/R$. $E$ and $R$ are the same for every element and come outside:

$$
F=\frac ER\iint y\,dy\,dz=0
$$

Since $E/R\neq0$, the integral itself must be zero:

$$
\iint y\,dy\,dz=0
$$

This integral is the **first moment of area** about the neutral axis. Among parallel axes it is zero only for the one through the centroid (centre of area) of the section. So the neutral axis passes through the centroid. A cross-section cut out of plywood balances on a knife-edge placed along the neutral axis, like a seesaw with the area on each side weighted by its distance.

### Moment equilibrium: the second moment of area

The force on the element, $\sigma_{xx}\,dy\,dz$, acts a distance $y$ from the neutral axis and so contributes a moment $(\sigma_{xx}\,dy\,dz)\,y$ about it. The total must equal the bending moment:

$$
M=\iint\sigma_{xx}\,y\,dy\,dz
$$

Substitute $\sigma_{xx}=Ey/R$:

$$
M=\frac ER\iint y^2\,dy\,dz
$$

The $y^2$ comes from two linear effects multiplied: the stress grows with $y$, and so does its lever arm. The integral depends only on the shape of the section and is the **second moment of area** about the neutral ($z$) axis:

$$
I_{zz}=\iint y^2\,dy\,dz
$$

written $I_{zz}$ or just $I$. It represents the beam's resistance to bending due to the geometry of its section. Then

$$
M=\frac{EI}{R}
$$

### Engineer's bending theory

Combining $M=EI/R$ with $\sigma_{xx}=Ey/R$ gives three equal ratios:

$$
\boxed{\frac MI=\frac\sigma y=\frac ER}
$$

known as **engineer's bending theory**. The most used form is

$$
\sigma=\frac{My}{I}
$$

Strictly the result holds only for pure bending, with zero shear force. Applied to beams where the shear force is not zero, the inaccuracies are negligible for slender beams. With $y$ positive downwards and sagging $M$ positive, a positive $\sigma$ is tensile.

## 3. Second moments of standard sections

### Rectangle

A rectangle of width $b$ (along $z$) and depth $d$ (along $y$) has its centroid at mid-depth. Integrate over $z$ first; $y^2$ does not depend on $z$:

$$
I_{zz}=\int_{-d/2}^{d/2}y^2\Big[z\Big]_{-b/2}^{b/2}dy=b\int_{-d/2}^{d/2}y^2\,dy
$$

This is the area $b\,dy$ of each horizontal strip times its $y^2$, summed. Then

$$
I_{zz}=b\left[\frac{y^3}{3}\right]_{-d/2}^{d/2}=\frac b3\left(\frac{d^3}{8}-\left(-\frac{d^3}{8}\right)\right)
$$

$$
I_{zz}=\frac b3\cdot\frac{d^3}{4}
$$

$$
\boxed{I_{zz}=\frac{bd^3}{12}}
$$

Replacing $y^2$ by 1 in the integral gives $bd$, the area, which is a quick check that the limits are right. Only the dimension perpendicular to the bending axis, $d$, is cubed. A ruler, or a plank 200 mm × 50 mm, is easy to bend flat and hard to bend on edge: turning it from flat to on edge multiplies $I$ by $(200/50)^2=16$.

### I-section by subtraction

An I-section of overall width $b$ and depth $d$, with flanges of thickness $t_f$ and a web of thickness $t_w$, is a full rectangle minus the two rectangles of missing material on either side of the web. Those two have a combined width $b-t_w$ and depth $d-2t_f$ and share the centroid of the full rectangle, so

$$
I_{zz}=\frac{bd^3}{12}-\frac{(b-t_w)(d-2t_f)^3}{12}
$$

### General symmetric section

If the width varies with height, $b(y)$, each horizontal strip has area $b(y)\,dy$ and

$$
I_{zz}=\iint y^2\,dy\,dz=\int_{-c_2}^{c_1}y^2\,b(y)\,dy
$$

where $c_1$ and $c_2$ are the distances from the neutral axis to the bottom and top. For a section that is not symmetric about the neutral axis, such as a trapezium wider at the top, the centroid moves towards the wider side, so $c_1\neq c_2$. The highest stress magnitude occurs at the fibre furthest from the neutral axis:

$$
\sigma_{max}=\left|\frac{M_{max}\,c_1}{I}\right|
$$

if $c_1$ is the larger distance.

### Circle

For a circle of radius $R$ the neutral axis is a diameter, through the centre by symmetry. The boundary is simple in polar coordinates, $r=R$ rather than $y^2+z^2=R^2$, so put

$$
y=r\sin\theta
$$

and the area element $dy\,dz$ becomes $r\,dr\,d\theta$, a small patch of radial width $dr$ and arc length $r\,d\theta$. Then

$$
I_{zz}=\iint r^2\sin^2\theta\;r\,dr\,d\theta=\iint r^3\sin^2\theta\,dr\,d\theta
$$

The $\theta$ integral uses $\sin^2\theta=\tfrac12(1-\cos2\theta)$:

$$
\int_0^{2\pi}\sin^2\theta\,d\theta=\int_0^{2\pi}\tfrac12(1-\cos2\theta)\,d\theta=\left[\frac\theta2-\frac{\sin2\theta}{4}\right]_0^{2\pi}=\pi
$$

So

$$
I_{zz}=\int_0^R\pi r^3\,dr=\pi\left[\frac{r^4}{4}\right]_0^R=\frac{\pi R^4}{4}
$$

and with $R=D/2$,

$$
\boxed{I_{zz}=\frac{\pi D^4}{64}}
$$

Expressions for many other shapes (squares, triangles, ellipses) are tabulated in textbooks, and the parallel axis theorem lets them be combined into more complicated sections without integrating from first principles.

## 4. Strength of a beam of uniform section

### Procedure

For a beam of uniform cross-section, the maximum bending stress occurs at the section of maximum bending moment, at the fibre furthest from the neutral axis:

1. Draw the BM diagram to find the location and value of $M_{max}$.
2. The largest stresses occur at the outer surfaces, furthest from the neutral axis. If the section is not symmetric about the neutral axis, the tensile and compressive extremes differ.
3. Evaluate

$$
\sigma_{max}=\frac{M_{max}\,y_{max}}{I}
$$

and compare with the allowable stress of the material, for instance $\sigma_{yield}=250$ MPa for A36 steel. Some materials have different allowable stresses in tension and compression: concrete is strong in compression and is usually assumed to carry no tension at all, which is why it is reinforced with steel bars on the tension side.

The ratio $I/y_{max}$, the section modulus $Z$ ([[Section Modulus]]), collects the section's whole contribution to bending strength.

### Example: rectangular cantilever with an end load

A cantilever of length $L$, built in at its left end, carries a downward force $F$ at its free end; the section is a rectangle $b$ wide and $d$ deep. The wall supplies an upward reaction $F$ and an anticlockwise reaction moment $FL$. The shear force is $+F$ along the beam; the bending moment rises linearly with slope $F$ from $-FL$ at the wall to zero at the tip, so

$$
M_{max}=-FL
$$

at the root, hogging. At the root section, the upper surface is at $y=-d/2$:

$$
\sigma=\frac{(-FL)(-d/2)}{bd^3/12}=+\frac{6FL}{bd^2}
$$

positive, so tensile. The lower surface is at $y=+d/2$:

$$
\sigma=\frac{(-FL)(d/2)}{bd^3/12}=-\frac{6FL}{bd^2}
$$

compressive. The stress is zero at the neutral axis and varies linearly between. A hogging cantilever has its tension on top, the opposite of a sagging beam.

### Superposition of axial and bending stress

For a linear elastic material, stresses from different loads add. An eccentric load, applied off the beam's axis, produces both an axial force and a bending moment, so the total longitudinal stress is

$$
\sigma_{xx}=\frac FA+\frac{My}{I}
$$

a uniform axial stress plus the linear bending distribution. An open chain link (shackle) pulled apart is the classic case: the load line lies a distance $d$ from the centre of the curved bar, so each section carries tension $F$ and a moment $Fd$. On the inside of the link the bending stress is tensile and adds to the axial tension, so that is where the link breaks.

![[s1_shackle_superposition.png|900]]

## 5. The parallel axis theorem

### Derivation

Suppose $I_{zz}$ is known about an axis $z$ through the centroid of an area, and the second moment is wanted about a parallel axis $z'$ a distance $b$ away. With $y'=y+b$ (and $z'=z+a$, which is not needed for bending about $z'$), $dy'=dy$ and $dz'=dz$, the area element is unchanged, and

$$
I_{z'z'}=\iint y'^2\,dy'\,dz'=\iint(y+b)^2\,dy\,dz
$$

Expand the square:

$$
I_{z'z'}=\iint(y^2+2by+b^2)\,dy\,dz
$$

$$
I_{z'z'}=\iint y^2\,dy\,dz+2b\iint y\,dy\,dz+b^2\iint dy\,dz
$$

The first integral is $I_{zz}$ about the centroidal axis. The second is the first moment of area about the centroid, which is zero by the definition of the centroid. The third is the area $A$. So

$$
\boxed{I_{z'z'}=I_{zz}+Ab^2}
$$

If $I_{zz}$ is known about the axis through the centroid, $I$ about any parallel axis follows at once. The theorem is valid only when $I_{zz}$ is about the area's own centroidal axis. Because $A$ and $b^2$ are never negative, the smallest second moment in any family of parallel axes is the one through the centroid.

### Example: the I-beam revisited

An I-beam is 100 mm deep with 60 × 5 mm flanges and a 5 × 90 mm web (all dimensions in mm). It is symmetric, so the neutral axis is at mid-height. Split it into the web (1) and the two flanges (2) and (3). The web's own centroid lies on the neutral axis:

$$
I_{zz(1)}=\frac{(5)(90)^3}{12}=303\,750\ \mathrm{mm^4}
$$

Each flange has its own centroid 47.5 mm from the neutral axis, so

$$
I_{zz(2)}=\frac{(60)(5)^3}{12}+(60)(5)(47.5)^2=625+676\,875=677\,500\ \mathrm{mm^4}
$$

and $I_{zz(3)}=I_{zz(2)}$. Adding,

$$
I_{zz}=303\,750+2(677\,500)=1\,658\,750\ \mathrm{mm^4}=1.659\times10^{-6}\ \mathrm{m^4}
$$

For each flange the $Ab^2$ term is more than a thousand times its own $bd^3/12$.

> [!check] Subtraction gives the same
> $\dfrac{60(100)^3}{12}-\dfrac{(60-5)(100-10)^3}{12}=5\,000\,000-3\,341\,250=1\,658\,750$ mm⁴.

![[s1_parallel_axis_contributions.png|900]]

### Why the flanges matter

A thin strip bent about its own axis is easy to bend. Move the same strip away from the neutral axis and attach it to the rest of the section, and bending now forces it to stretch or shorten along its whole length, which takes far more moment. Two separate strips slide over each other; joined to a web, they cannot. That is the $Ab^2$ term. An I-beam concentrates most of its material at the greatest distance from the neutral axis to maximise $I_{zz}$, and a hollow tube does the same compared with a solid rod of the same weight, which is why bicycle frames are tubes. The limit is that a very thin wall can buckle locally, like a crushed drinks can.

A beam of varying section can go further. Ideally the section would follow the bending moment,

$$
\frac{I(x)}{y_{max}(x)}=\frac{M(x)}{\sigma_{max}}
$$

so that the extreme fibres reach the allowable stress everywhere, as in the thickened middle of a beam carrying a central load. In practice efficient use of material is traded against ease of manufacture: most beams are bought as standard uniform sections, while weight-critical structures justify the tailoring. For uniform beams the maximum stress is at the maximum moment.

## 6. Sections with one axis of symmetry

### Locating the neutral axis

The I-beam, rectangle and circle have two axes of symmetry, so the centroid is self-evident. A channel or a T-section is symmetric about its vertical axis only, and the centroid has to be found before $I$ can be. Taking moments of area about the neutral axis itself would require knowing where it is; instead take moments about any convenient reference, usually the base. For parts of area $A_i$ whose own centroids are at heights $d_i$ above the base,

$$
A\,d=\sum_iA_i\,d_i,\qquad A=\sum_iA_i
$$

which is the requirement that the first moment of area about the centroidal axis is zero, written relative to the base.

### Example: channel section

A channel 120 mm wide and 50 mm high has walls 5 mm thick: two uprights (1) and (2), each 5 × 50 mm, standing on a base (3) of 110 × 5 mm between them. Find $I_{zz}$ about the centroidal axis.

**Step 1, centroid.** The areas are 250, 250 and 550 mm², a total of 1050 mm². The uprights' centroids are 25 mm above the base and the base's centroid is 2.5 mm above it:

$$
1050\,d=(250)(25)+(250)(25)+(550)(2.5)
$$

$$
d=\frac{13\,875}{1050}=13.21\ \mathrm{mm}
$$

well below mid-height, because the wide base dominates.

**Step 2, parallel axis theorem.** Find each part's $I$ about its own centroid, then shift it to the centroid of the whole section. Each upright is 5 mm wide and 50 mm deep, with its centroid $25-13.21=11.79$ mm above the neutral axis:

$$
I_{zz(1)}=\frac{(5)(50)^3}{12}+(50)(5)(25-13.21)^2=52\,083+34\,751=86\,834\ \mathrm{mm^4}
$$

and $I_{zz(2)}=I_{zz(1)}$. The base is 110 mm wide and only 5 mm deep (the dimension perpendicular to the bending axis), with its centroid $13.21-2.5=10.71$ mm below the neutral axis:

$$
I_{zz(3)}=\frac{(110)(5)^3}{12}+(550)(13.21-2.5)^2=1146+63\,087=64\,233\ \mathrm{mm^4}
$$

Adding,

$$
I_{zz}=2(86\,834)+64\,233=237\,901\ \mathrm{mm^4}=2.379\times10^{-7}\ \mathrm m^4
$$

The extreme fibres are the tops of the uprights, $50-13.21=36.79$ mm from the neutral axis, against 13.21 mm for the underside of the base.

> [!check] Subtraction, with the parallel axis theorem used twice
> The same answer comes from a solid 120 × 50 block minus the 110 × 45 space above the base, but both rectangles have to be shifted to the channel's neutral axis. Solid: $\tfrac{120(50)^3}{12}+6000(25-13.21)^2=2\,083\,418$ mm⁴. Missing area, centroid 27.5 mm above the base: $\tfrac{110(45)^3}{12}+4950(27.5-13.21)^2=1\,845\,517$ mm⁴. Difference: 237 902 mm⁴. Forgetting to shift the solid rectangle is the common error.

![[s1_section_gallery.png|900]]

---

## Worked examples

### Worked example - cantilever bending stress

A timber cantilever 2 m long, with a rectangular section 50 mm wide and 100 mm deep, carries 5 kN at its free end. At the root

$$
\sigma_{max}=\frac{6FL}{bd^2}=\frac{6(5000)(2)}{(0.05)(0.1)^2}=120\ \mathrm{MPa}
$$

tensile on top and compressive underneath. Turning the same section flat ($b=100$, $d=50$ mm) doubles the stress to 240 MPa, because only $d$ is squared in $6FL/bd^2$.

### Worked example - channel section

The channel above, $I_{zz}=2.379\times10^{-7}$ m⁴ with extreme fibres 36.79 mm above and 13.21 mm below the neutral axis, carries a sagging moment of 500 N m. The tops of the uprights are at $y=-36.79$ mm:

$$
\sigma_{top}=\frac{(500)(-0.03679)}{2.379\times10^{-7}}=-77.3\ \mathrm{MPa}
$$

compressive, and the underside of the base at $y=+13.21$ mm:

$$
\sigma_{bottom}=\frac{(500)(0.01321)}{2.379\times10^{-7}}=+27.8\ \mathrm{MPa}
$$

tensile. The unsymmetrical section makes the two extremes differ by a factor of 2.8.

### Worked example - eccentrically loaded link

An open link made from steel bar of 12 mm diameter carries 2 kN with the load line 15 mm from the centre of the bar. The section properties are

$$
A=\frac{\pi(0.012)^2}{4}=1.131\times10^{-4}\ \mathrm{m^2},\qquad I=\frac{\pi(0.012)^4}{64}=1.018\times10^{-9}\ \mathrm{m^4}
$$

The axial stress is $2000/1.131\times10^{-4}=17.7$ MPa and the moment is $M=(2000)(0.015)=30$ N m, so the extreme bending stress is

$$
\frac{My}{I}=\frac{(30)(0.006)}{1.018\times10^{-9}}=176.8\ \mathrm{MPa}
$$

On the inside of the link the two add: $17.7+176.8=194.5$ MPa in tension. On the outside, $17.7-176.8=-159.2$ MPa. The bending stress is ten times the axial stress, so an eccentric load is far more damaging than the same load applied along the axis.

### Worked example - inverted-T hoist

Tutorial 4 Q3 is a cantilever hoist of inverted-T section: a 100 × 10 mm flange at the bottom and a 10 × 90 mm web above it, 100 mm deep overall, loaded 1.0 m from the wall, with an allowable stress of 330 MPa. Find the largest load.

Centroid above the base:

$$
d=\frac{(900)(55)+(1000)(5)}{1900}=28.68\ \mathrm{mm}
$$

Second moment about the neutral axis:

$$
I=\frac{10(90)^3}{12}+900(55-28.68)^2+\frac{100(10)^3}{12}+1000(28.68-5)^2=1.800\times10^{-6}\ \mathrm{m^4}
$$

The moment at the wall is $-F(1.0)$, hogging, so the top is in tension. The top fibre is $100-28.68=71.3$ mm from the neutral axis, much further than the base (28.7 mm), so it governs:

$$
F_{max}L=\frac{\sigma I}{y_{max}}=\frac{(330\times10^6)(1.800\times10^{-6})}{0.0713}=8.33\ \mathrm{kN\,m}
$$

$$
F_{max}=8.33\ \mathrm{kN}
$$

![[s1_bending_stress_tsection.png|900]]

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · Next: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]
- Concepts: [[Engineer's Bending Theory]] · [[Parallel Axis Theorem]] · [[Second Moments of Area]] · [[First Moment of Area]] · [[Section Modulus]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method|A5]] ($1/R=M/EI$ gives the deflection) · [[FEEG1002 A7 - Euler Buckling of Struts|A7]] (the least $I$ sets the buckling load) · [[FEEG1002 A8 - Torsion of Circular Shafts|A8]] (the polar second moment $J=2I$ for a circle) · [[FEEG1002 A9 - Shear Stresses in Beams|A9]] (the first moment of area returns)
- Year 2: unsymmetrical bending, $I_{yz}$ and [[Principal Axes of a Section]] in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]; [[Specific Stiffness and Strength]] for choosing beam materials

## Sources

- `Lecture 07 - Beams, Stress Due to Bending.pdf` (S1 Lectures 7a–7c, 27 slides) and `Lecture 08 - Beams, Second Moment of Area Continued.pdf` (S1 Lectures 8a–8c, 26 slides), read in full.
- `FEEG1002 Lecture 7 - Statics 1 - Stresses due to bending - November 2024.txt` (Lecture 7): assumptions (ll. 29–77), neutral surface and axis (ll. 78–131), strain (ll. 132–246), anticlastic curvature (ll. 247–266), stress (ll. 267–309), force equilibrium and centroid (ll. 310–442), moment equilibrium and $I$ (ll. 443–526), engineer's bending theory (ll. 527–566), rectangle and I-section (ll. 567–744), cantilever stress and allowable stresses (ll. 745–833), superposition (ll. 834–859).
- `FEEG1002 Lecture 8 - Statics 1 - Second moment of area continuedNovember 2024.txt` (Lecture 8): general and asymmetric sections (ll. 51–121), circle (ll. 122–246), parallel axis theorem (ll. 269–386), I-beam and practical implications (ll. 387–557), channel section (ll. 558–741), exam information (ll. 745–755).
- `FEEG1002 Lecture 2020-10-29.txt`: short recording of the four-point bending laboratory (strain gauges on top, sides and bottom of a beam; zero, tare load, then load in increments without unloading).
- Tutorial Sheet 04 and its official solutions: Q1–Q3 and additional Q1–Q3.
- All section properties and stresses recomputed in Python.

## Self-study tasks

### Core

- [ ] Derive $\varepsilon_{xx}=y/R$, then show from force and moment equilibrium that the neutral axis passes through the centroid and that $M=EI/R$ (L7, ll. 132–526). → [[#Longitudinal strain]] · [[#2. Equilibrium of the cross-section]]
- [ ] Derive $I=bd^3/12$ for a rectangle and $I=\pi D^4/64$ for a circle, including the $\sin^2\theta$ integral quoted from a maths book (L7, ll. 584–689; L8, ll. 135–246). → [[#3. Second moments of standard sections]]
- [ ] Redo the channel section by subtracting the missing area from a solid rectangle, applying the parallel axis theorem to both (set in L8, ll. 723–741). Target 237 900 mm⁴. → [[#Example: channel section]]
- [ ] Tutorial 4 Q1: size a square beam with an overhanging UDL for 300 MPa. Target 81.4 mm. → [[#4. Strength of a beam of uniform section]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Q1 - Square beam with an overhanging UDL|Tutorial 4 Q1]]
- [ ] Tutorial 4 Q2: $I_{yy}$ and $I_{zz}$ of an unequal I-section. Targets 1.95 and 2.29 × 10⁻⁶ m⁴. → [[#6. Sections with one axis of symmetry]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Q2 - Unequal I-section|Tutorial 4 Q2]]
- [ ] Tutorial 4 Q3: largest load on the inverted-T hoist. Target 8.33 kN. → [[#Worked example - inverted-T hoist]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Q3 - Inverted-T cantilever hoist|Tutorial 4 Q3]]

### Further practice

- [ ] Compare the own-centroid and parallel-axis contributions for one flange of the I-beam (question posed in L8, ll. 458–474). → [[#Example: the I-beam revisited]]
- [ ] Tutorial 4 additional Q1–Q3: three-rod crane boom, block with two holes, water channel. Targets 0.0019 m⁴; 2.23 and 1.42 × 10⁻⁶ m⁴; 5.63 m. → [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Extra Q1 - Crane boom of three rods|Tutorial 4 Extra Q1]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Extra Q2 - Block with two holes|Extra Q2]] · [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions#Extra Q3 - Sheet-metal water channel|Extra Q3]]
- [ ] Explain why the open link breaks on the inside, with a sketch of the axial, bending and total stress (L7, ll. 834–859). → [[#Superposition of axial and bending stress]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 7, ll. 121, 778–780 and 850–851)
> Where: [[#Neutral surface and neutral axis]] · [[#Example: rectangular cantilever with an end load]] · [[#Superposition of axial and bending stress]].
>
> At l. 121 the neutral axis is called "the plane … that doesn't deform"; that plane is the neutral surface, and the neutral axis is its intersection with the cross-section, as ll. 117–120 say. At ll. 778–780 the cantilever moment is said to rise with "a value of F over length of L … from minus F over L"; it rises with slope $F$ from $-FL$ at the wall to zero. At ll. 850–851 the axial tension in the shackle is said to add to the compressive bending stresses at the bottom; at that side the bending stress is tensile (l. 843), and it is because axial and bending tension add there that the maximum is on the inside (l. 852).

> [!warning] Transcript slip (Lecture 8, ll. 679, 707 and 735)
> Where: [[#Example: channel section]].
>
> Having found the neutral axis 13.2 mm above the base (l. 654), the lecture uses offsets measured from "30 millimeters" for the parallel axis theorem. With 30 mm the total would be 533 750 mm⁴. The slide uses the correct offsets, $25-13.21$ and $13.21-2.5$, giving 237 901 mm⁴.
