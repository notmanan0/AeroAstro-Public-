---
title: "FEEG1002 A9 - Shear Stresses in Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 9
tags: [feeg1002, statics, beams, shear-stress, first-moment-of-area, complementary-shear]
aliases: ["Statics 1 Lecture 14", "Shear stress in beams", "sigma_yx = Q A_s y_c / b I", "Shear stress coefficient"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 14 (6 Jan 2025, ll. 10–616: shear stresses as the resultant of the shear force, complementary shear, laminated beams, derivation of the shear stress formula, rectangular section, shear stress coefficient, bending against shear stress, where shear matters); slide deck 14 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]", "[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
next_topics: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
key_concepts: ["[[Shear Stress Distribution in Beams]]", "[[First Moment of Area]]", "[[Shear Flow]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 14 - Shear Stresses in Beams.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 14 - Statics 1 - Shear stresses in beams - January 2025.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress - Solutions.pdf"
---

# FEEG1002 A9 - Shear Stresses in Beams

> [!abstract] Summary
> The shear force $Q$ in a beam is the resultant of shear stresses $\sigma_{yx}$ acting on the cross-section, and moment equilibrium of a small element requires equal complementary shear stresses $\sigma_{xy}$ on horizontal planes. Where the bending moment varies along the beam, the bending stresses on the two ends of a longitudinal strip differ, and only a horizontal shear stress on the strip's inner face can balance them; that equilibrium gives $\sigma_{yx}=QA_sy_c/(bI)$, where $A_sy_c$ is the first moment about the neutral axis of the area beyond the level considered. For a rectangle the distribution is a parabola, zero at the top and bottom and $\tfrac32$ of the average at the neutral axis, exactly where the bending stress is zero. In a slender beam (a rectangular cantilever of length $L$ and depth $d$ under an end load, say) the bending stress is $4L/d$ times larger, so shear matters mainly for glued, riveted or holed members.

> [!summary]- Exam use: quick path
> - **Use it when:** the maximum shear stress in a beam is wanted, or the shear carried by a glue line, weld, rivets or screws joining parts of a beam.
> - **Assumptions:** engineer's bending theory, $\sigma_{xx}=My/I$; section symmetric about the plane of loading; shear stress uniform across the width $b$ at each level; derived for constant shear force but accurate for slender beams where $Q$ varies; free top and bottom surfaces.
> - **Method:** 1. Draw the SF diagram and find $Q$ at the section of interest (usually $Q_{max}$). 2. Locate the neutral axis and find $I$. 3. At the level $y$ of interest, find the area $A_s$ beyond it and the distance $y_c$ of its centroid from the neutral axis. 4. Use $\sigma_{yx}=QA_sy_c/(bI)$ with $b$ the width at that level. 5. For standard shapes use $\sigma_{yx\,max}=K\,Q/A$ directly.
> - **Common mistakes:** taking $y_c$ as the distance to the level $y$ rather than to the centroid of the area beyond it; using the full section width where the cut passes through a narrow web.
> - **Practise:** [[#Worked example - glued timber beam]] · [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q3 - Glued timber beam|Tutorial 6 Q3]]

A slender member can be loaded in four basic ways. Pulling it gives a uniform stress, $\sigma=F/A$. Bending makes the stress vary linearly with distance from the neutral axis, $\sigma=My/I$ ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]]). Twisting makes the shear stress vary linearly with radius, $\tau=Tr/J$ ([[FEEG1002 A8 - Torsion of Circular Shafts|A8]]). The fourth is the shear stress that carries the shear force $Q$ of a beam.

The simplest guess, $Q/A$ spread evenly over the section, is wrong, and the reason is visible in a simple experiment. A solid timber beam loaded at mid-span deflects a little. The same beam cut into horizontal strips with a chainsaw and restacked sags much more under that load, and the strips slide over each other so that their ends become stepped. Plane sections no longer stay plane, and each strip bends on its own about its own neutral axis, so the bottom strip hardly has to stretch. In the solid beam the layers cannot slide, because shear stresses on horizontal planes hold them together, and those stresses are what make it stiff. Leaf springs on horse-drawn carriages and railway wagons exploit the opposite: loose leaves give a flexible spring.

Those horizontal shear stresses are linked to the vertical ones on the cross-section, and both vary over the depth. They are largest at the neutral axis, the plane that has to hold together everything above it against everything below.

---

## 1. Shear stresses from the shear force

### Resultants

The bending moment is the resultant of the bending stresses, tension below the neutral axis and compression above it in a sagging beam, varying linearly and zero at the neutral axis. In the same way, the shear force $Q$ is the resultant of shear stresses acting parallel to the cross-section. On the cut face of the left part of a beam, a positive $Q$ acts downwards, and so do the shear stresses that make it up.

For a cantilever built in at its left end, with a downward force $F$ at its free end, the wall supplies an upward force $F$ and a reaction moment $FL$. The shear force is $+F$ all along the beam, and the bending moment rises linearly from $-FL$ at the wall to zero at the tip. At any cut, the two faces carry equal and opposite shear forces $Q=F$, as if one part were holding the other up by friction.

The average shear stress over the section is

$$
\sigma_{yx\,average}=\frac QA
$$

but that says nothing about how the shear stress is actually distributed over the section.

### Notation

The shear stress is written $\sigma_{yx}$ or $\sigma_{xy}$, the notation of Statics 2 ([[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels|B1]]). Two different indices mean a shear stress, and $\sigma_{xy}$ is the same kind of quantity as the $\tau$ of earlier notes. On the cross-section of the beam, whose normal is along $x$, the shear stress points along $y$ (vertically). On a horizontal plane, whose normal is along $y$, the shear stress points along $x$.

## 2. Complementary shear stresses

Isolate a small rectangular element of the beam, $dx$ long and $dy$ high, with unit thickness. On its vertical faces act the shear stresses $\sigma_{yx}$ from the shear force: downwards on one face and upwards on the other, equal in size so that the element is in vertical equilibrium.

Those two forces, $\sigma_{yx}\,dy$ each, are a distance $dx$ apart and form a couple of size $\sigma_{yx}\,dy\,dx$. With nothing else acting, the element would spin faster and faster. Rotational equilibrium needs an opposite couple, and the only faces left are the horizontal ones: shear stresses $\sigma_{xy}$ along them, one pointing left and one right, forces $\sigma_{xy}\,dx$ a distance $dy$ apart. Moments about the centre of the element:

$$
\sigma_{yx}\,dy\,dx-\sigma_{xy}\,dx\,dy=0
$$

$$
\boxed{\sigma_{xy}=\sigma_{yx}}
$$

Shear stresses on perpendicular planes always come in equal **complementary** pairs. Wherever the cross-section carries a vertical shear stress, the horizontal plane through the same point carries an equal horizontal one, which is the stress that stops the chainsaw-cut strips sliding.

![[s1_shear_stress_derivation.png|900]]

## 3. Derivation of the shear stress formula

### A beam element with varying moment

Consider a short beam element of length $dx$ over which the shear force $Q$ is constant but the bending moment varies, from $M$ on the left face to $M+\frac{dM}{dx}dx$ on the right. By engineer's bending theory the bending stress at height $y$ is

$$
\sigma_{xx}=\frac{My}{I}
$$

on the left face and

$$
\sigma_{xx}+\frac{\partial\sigma_{xx}}{\partial x}dx=\left(M+\frac{dM}{dx}dx\right)\frac yI
$$

on the right face. Because $M$ varies with $x$, so does $\sigma_{xx}$.

### Equilibrium of a strip

The strip at the bottom of the element is everything below a level $y$ (measured downwards from the neutral surface), with cross-sectional area $A_s$ and width $b$ at level $y$. The bending stress pushes on its left end and pulls on its right end, and the totals are different, because the stress is larger on the right. On its own, the strip would not be in horizontal equilibrium. Its bottom face is a free surface, in contact with air only, so it carries no shear stress. The only way to keep the strip in equilibrium is a shear stress $\sigma_{xy}$ acting along its top face, of area $b\,dx$.

The bending stress varies over the strip's end faces with $y$, so the end forces must be integrated over $A_s$. Horizontal equilibrium, with the forces pointing left equal to those pointing right:

$$
\int_{A_s}\sigma_{xx}\,dA+\sigma_{xy}\,b\,dx=\int_{A_s}\left(\sigma_{xx}+\frac{\partial\sigma_{xx}}{\partial x}dx\right)dA
$$

The $\sigma_{xx}$ terms cancel:

$$
\sigma_{xy}\,b\,dx=\int_{A_s}\frac{\partial\sigma_{xx}}{\partial x}dx\,dA
$$

Divide by $b\,dx$:

$$
\sigma_{xy}=\frac1b\int_{A_s}\frac{\partial\sigma_{xx}}{\partial x}dA
$$

### Bringing in the shear force

Differentiate the bending stress along the beam; at a fixed $y$ only $M$ varies:

$$
\frac{\partial\sigma_{xx}}{\partial x}=\frac{dM}{dx}\frac yI
$$

and the slope of the bending moment is the shear force ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Derivation|A3]]), $dM/dx=Q$:

$$
\frac{\partial\sigma_{xx}}{\partial x}=\frac{Qy}{I}
$$

Substitute; $Q$ and $I$ are constants over the strip:

$$
\sigma_{xy}=\frac{Q}{bI}\int_{A_s}y\,dA
$$

By the complementary shear argument, this horizontal stress on the strip's top face equals the vertical shear stress on the cross-section at the same level $y$. The integral is the **first moment of area** of the strip about the neutral axis, which equals its area $A_s$ times the distance $y_c$ of its centroid from the neutral axis:

$$
\int_{A_s}y\,dA=A_s\,y_c
$$

So the shear stress at level $y$ is

$$
\boxed{\sigma_{yx}=\frac{Q}{b\,I}A_s\,y_c}
$$

with $Q$ the shear force at the section, $I$ the second moment of area of the whole section about the neutral axis, $b$ the width at level $y$, and $A_s$, $y_c$ the area beyond level $y$ and the distance of its centroid from the neutral axis. Taking the strip above level $y$ instead gives the same magnitude, because the first moment of the whole section about its centroid is zero.

### Validity

The solution is exact only for a constant shear force along the beam. As long as the cross-section is small compared with the span, the error is small for a varying shear force too, for instance under a uniformly distributed load, where $Q$ varies linearly.

## 4. Rectangular section

### The distribution

For a rectangle $b$ wide and $d$ deep,

$$
I=\frac{bd^3}{12}
$$

The strip below level $y$ has height $d/2-y$, so

$$
A_s=\left(\frac d2-y\right)b
$$

and its centroid is halfway down it:

$$
y_c=y+\frac12\left(\frac d2-y\right)=\frac y2+\frac d4
$$

Substitute into the formula:

$$
\sigma_{yx}=\frac{Q}{b\,bd^3/12}\left(\frac d2-y\right)b\left(\frac y2+\frac d4\right)
$$

The product of the brackets is $\tfrac12\left(\tfrac d2-y\right)\left(\tfrac d2+y\right)=\tfrac12\left(\tfrac{d^2}{4}-y^2\right)$, so

$$
\sigma_{yx}=\frac{12Q}{bd^3}\left(\frac{d^2}{8}-\frac{y^2}{2}\right)
$$

To simplify, use the total cross-sectional area $bd=A$ and the average shear stress $\sigma_{yx\,average}=Q/A$. Take $d^2/8$ out of the bracket:

$$
\sigma_{yx}=\frac{12Q}{bd^3}\cdot\frac{d^2}{8}\left(1-\frac{4y^2}{d^2}\right)=\frac32\cdot\frac{Q}{bd}\left(1-\frac{y^2}{(d/2)^2}\right)
$$

$$
\boxed{\sigma_{yx}=\frac32\,\sigma_{yx\,av}\left(1-\frac{y^2}{(d/2)^2}\right)}
$$

### Checks and shape

At the outer surfaces, $y=\pm d/2$, the bracket is zero and so is the shear stress, as it must be at a free surface. At the neutral axis, $y=0$, it reaches its maximum:

$$
\sigma_{yx\,max}=\frac32\,\sigma_{yx\,av}
$$

The distribution is a parabola: zero shear stress at the outer surfaces, where the bending stresses are largest, and maximum shear stress at the neutral axis, where the bending stresses are zero. The neutral plane carries the most shear because it has to balance the change in bending stress of everything on one side of it.

![[s1_beam_shear_stress.png|900]]

## 5. The shear stress coefficient

It is often convenient to write the maximum shear stress as

$$
\sigma_{yx\,max}=K\,\sigma_{yx\,av}=K\frac QA
$$

where $K$ is the **shear stress coefficient**. Since $K$ is known for common shapes, the maximum shear stress follows from the shear force diagram with no integration:

| Section | $K$ |
|---|---|
| Rectangle | $1\tfrac12$ |
| Solid circle | $\tfrac43$ |
| Thin-walled circular tube ($t\ll R$) | 2 |

For a solid circle of radius $R$, the maximum is at the neutral axis, where the area beyond it is a semicircle, $A_s=\pi R^2/2$, whose centroid is $y_c=4R/3\pi$ from the diameter, so $A_sy_c=2R^3/3$. With $b=2R$ and $I=\pi R^4/4$:

$$
\sigma_{yx\,max}=\frac{Q\,(2R^3/3)}{(2R)(\pi R^4/4)}=\frac{4Q}{3\pi R^2}=\frac43\,\frac QA
$$

For a thin tube of mean radius $R$ and wall $t$, the half-ring beyond the neutral axis has area $\pi Rt$ and centroid $2R/\pi$ from it, so $A_sy_c=2R^2t$. The cut crosses the wall twice, so $b=2t$, and $I=\pi R^3t$:

$$
\sigma_{yx\,max}=\frac{Q\,(2R^2t)}{(2t)(\pi R^3t)}=\frac{Q}{\pi Rt}=2\,\frac{Q}{2\pi Rt}=2\,\frac QA
$$

For more complicated sections, such as an I-beam, the shear stresses in the flanges also have to be considered, (see [[SESA2028 S3 - Shear Flow and Shear Centre]]); only these simple shapes are treated here.

## 6. Bending stress against shear stress

### The cantilever with an end load

Both stresses can be compared for the rectangular cantilever with an end load $F$. The critical section for bending is at the wall, where $M=-FL$:

$$
\sigma_{xx\,max}=\frac{(-FL)(-d/2)}{bd^3/12}=\frac{6FL}{bd^2}
$$

at $y=\pm d/2$. The shear force is $F$ everywhere, so at the neutral axis of any section

$$
\sigma_{yx\,max}=\frac32\sigma_{yx\,av}=\frac32\,\frac{F}{bd}
$$

Divide one by the other:

$$
\frac{\sigma_{xx\,max}}{\sigma_{yx\,max}}=\frac{6FL/bd^2}{3F/2bd}=\frac{4L}{d}
$$

$$
\sigma_{xx\,max}=\frac{4L}{d}\,\sigma_{yx\,max}
$$

The two stress distributions are quite different: the bending stress varies linearly over the depth and changes from section to section along the beam, while the shear stress is parabolic and, here, the same at every section.

![[s1_cantilever_stress_overview.png|900]]

For a slender beam $L\gg d$, so the maximum bending stress is many times the maximum shear stress, and shear stress is unlikely to cause failure. For standard analysis of solid sections, check the bending stress first.

### Where shear stress does matter

Shear stress becomes important wherever the material or the joints are weak in shear, or the section is thin where the shear is largest:

- Composite beams made of layers glued, riveted or screwed together: the glue line or fasteners at the neutral axis must carry the maximum shear stress.
- I-beams with large holes cut through the web to save weight or pass services: what is left of the web must still carry the shear.
- Glued laminated timber: a theatre roof in Eastleigh was built from glulam beams that later split along their middle plane, the plane of maximum shear stress, and was replaced by a truss.

Some materials are more prone to fail in shear than in tension, timber along the grain among them.

---

## Worked examples

### Worked example - timber cantilever

A timber cantilever 1.2 m long, 50 mm wide and 150 mm deep, carries 3 kN at its free end. The maximum bending stress, at the wall, is

$$
\sigma_{xx\,max}=\frac{6FL}{bd^2}=\frac{6(3000)(1.2)}{(0.05)(0.15)^2}=19.2\ \mathrm{MPa}
$$

and the maximum shear stress, at the neutral axis, is

$$
\sigma_{yx\,max}=\frac32\frac{F}{bd}=\frac32\cdot\frac{3000}{(0.05)(0.15)}=0.60\ \mathrm{MPa}
$$

> [!check] The ratio
> $19.2/0.60=32$, and $4L/d=4(1.2)/0.15=32$.

### Worked example - glued timber beam

Tutorial 6 Q3: two timbers, each 50 mm square, are glued one on top of the other to make a beam 50 mm wide and 100 mm deep. It is simply supported over a span $2L$ with $L=1.5$ m and carries $F=2$ kN at mid-span. Find the shear stress in the glue, and the spacing of screws (4 mm core diameter, allowable shear stress 200 MPa, friction ignored) that would do the glue's job.

The reactions are $F/2$ each, so the shear force has magnitude $Q=F/2=1$ kN along the whole span; only its sign changes at the load. The glue line lies on the neutral axis, where the shear stress is largest. For the rectangle $K=\tfrac32$ and $A=bd=(0.05)(0.10)$:

$$
\sigma_{yx}=\frac32\cdot\frac{1000}{(0.05)(0.10)}=0.30\ \mathrm{MPa}
$$

The span does not enter: shear stress depends on $Q$, not on $M$.

The horizontal shear force that the joint must transmit per metre of beam is the stress times the width:

$$
q=\sigma_{xy}\,b=(0.30\times10^6)(0.05)=15\ \mathrm{kN/m}
$$

Each screw, sheared across its core, carries

$$
F_s=\tau\frac{\pi D^2}{4}=(200\times10^6)\frac{\pi(0.004)^2}{4}=2.51\ \mathrm{kN}
$$

so the number needed per metre is $15/2.51=5.97$. Rounding up to 6 per metre gives a spacing of 16.7 cm.

For comparison, the bending moment at mid-span is $M=(F/2)L=1.5$ kN m, and the bending stress at the outer fibres is $6M/(bd^2)=6(1500)/((0.05)(0.10)^2)=18$ MPa, sixty times the glue stress, in line with $4L/d$ with $d=100$ mm. The timber is in no danger from shear; the joint is the part that needs checking.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A8 - Torsion of Circular Shafts]] · Next (Statics 2): [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]
- Concepts: [[Shear Stress Distribution in Beams]] · [[First Moment of Area]] · [[Shear Flow]] · [[Engineer's Bending Theory]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels|B1]] (the stress element and $\sigma_{xy}=\sigma_{yx}$) · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]] and [[FEEG1002 B6 - Yield Criteria|B6]] (combining $\sigma_{xx}$ and $\sigma_{yx}$ at a point)
- Year 2: shear flow in thin-walled sections and the [[Shear Centre]] in [[SESA2028 S3 - Shear Flow and Shear Centre]]

## Sources

- `Lecture 14 - Shear Stresses in Beams.pdf` (S1 Lectures 14a–14c, 28 slides), read in full.
- `FEEG1002 Lecture 14 - Statics 1 - Shear stresses in beams - January 2025.txt` (Lecture 14): recap of the four loading cases (ll. 10–50), shear force as a resultant (ll. 50–64), complementary shear and notation (ll. 65–118), chainsaw-cut beam and leaf springs (ll. 119–172), cantilever example and average stress (ll. 177–228), derivation (ll. 229–392), rectangular section (ll. 393–443), shear stress coefficient (ll. 444–479), overview (ll. 480–501), bending against shear stress (ll. 502–548), where shear matters (ll. 549–604), scope (ll. 605–616).
- Tutorial Sheet 06 and its official solutions: Q3.
- All numbers recomputed in Python; the coefficients $K$ for the circle and the thin tube were derived here (the lecture quotes them).

## Self-study tasks

### Core

- [ ] Explain why horizontal shear stresses must exist in a beam carrying a shear force (class question, L14, ll. 88–109). → [[#2. Complementary shear stresses]]
- [ ] Derive $\sigma_{yx}=QA_sy_c/(bI)$ from equilibrium of a strip, including what stops the strip sliding out sideways (class question, L14, ll. 276–297). → [[#3. Derivation of the shear stress formula]]
- [ ] Derive the parabolic distribution for a rectangle and show $K=1\tfrac12$ (L14, ll. 393–443). → [[#4. Rectangular section]]
- [ ] Decide whether bending or shear stress is larger in a slender cantilever, then derive $4L/d$ (class vote, L14, ll. 502–548). → [[#The cantilever with an end load]]
- [ ] Tutorial 6 Q3: shear stress in the glue and the screw spacing. Targets 0.30 MPa and 16.7 cm. → [[#Worked example - glued timber beam]] · [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q3 - Glued timber beam|Tutorial 6 Q3]]

### Further practice

- [ ] Derive $K=\tfrac43$ for a solid circle and $K=2$ for a thin tube (quoted without derivation, L14, ll. 452–455). → [[#5. The shear stress coefficient]]
- [ ] For the timber cantilever, find the bending and shear stresses and check their ratio (suggested, not lecturer-set). Targets 19.2 MPa, 0.60 MPa, 32. → [[#Worked example - timber cantilever]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 14, ll. 243, 348 and 378–381, 389–391 and 497)
> Where: [[#A beam element with varying moment]] · [[#Bringing in the shear force]] · [[#Validity]] · [[#Checks and shape]].
>
> At l. 243 the change in bending moment across the element is called "delta x"; it is $\delta M$. At l. 113 the first index is defined as the face normal and the second as the direction, but at l. 348 and ll. 378–381 the stress on the strip's horizontal top face is called $\sigma_{xy}$ and the vertical stress on the cross-section $\sigma_{yx}$, the reverse of that definition; the slides use the same labels. Because $\sigma_{xy}=\sigma_{yx}$ the result is unaffected. At l. 389 and l. 391 the derivation is said to hold when "the shear stress isn't constant" and to give "a linear distribution for your shear stress" under a uniform load; both should say shear force. At l. 497 the neutral axis is said to carry the "maximum bending stress"; it carries the maximum shear stress, and the bending stress there is zero.
