---
title: "FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 10
tags: [feeg1002, statics-2, stress-element, stress-tensor, complementary-shear, pressure-vessels, hoop-stress]
aliases: ["Statics 2 Lecture 1", "Stress element", "Hoop stress", "Thin-walled pressure vessel"]
date: 2026-11-05
status: lectured
coverage: "Statics 2 Lecture 1 (27 Jan 2025, ll. 1–676): internal forces on a cut, the stress element and its notation, equilibrium and complementary shear, the 3D stress state, thin-walled cylindrical and spherical pressure vessels; recap in Lecture 9 (12 May 2025, ll. 48–107)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]", "[[FEEG1002 A9 - Shear Stresses in Beams]]"]
next_topics: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
key_concepts: ["[[Stress Tensor and Stress Element]]", "[[Thin-Walled Pressure Vessels]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 01 - Stress in Multiple Dimensions and Pressure Vessels.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 1 - Statics 2 - Stresses in multiple dimesnions and pressure vessels - Jan.txt", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 01 - Stresses in Multiple Dimensions and Pressure Vessels.pdf"]
---

# FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels

> [!abstract] Summary
> At any point in a loaded solid there is one state of stress, but the stresses you write down depend on the surface you choose to cut. The state is captured by a small stress element: three normal and three shear components in 3D, with $\sigma_{xy}=\sigma_{yx}$ forced by moment equilibrium. The first application is the thin-walled pressure vessel, where cutting the vessel together with its contents gives a hoop stress $\sigma_{yy}=pR/t$ and a longitudinal stress $\sigma_{xx}=pR/2t$ in a cylinder, and $pR/2t$ in every direction in a sphere.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives an internal (or external) pressure, a radius and a wall thickness and asks for wall stresses, a maximum pressure, a wall thickness or the load on bolts or welds that hold the vessel together.
> - **Assumptions:** thin wall, $t/R<0.1$, so the radial stress is ignored and the wall is in plane stress; axisymmetric load, so there is no shear on an element aligned with the axis; pressure $p$ is the difference between inside and outside.
> - **Method:** 1. Set up axes on the wall: $x$ along the axis, $y$ round the circumference. 2. Cut the vessel and its contents and draw the free body. 3. Balance the pressure force on the projected area ($2RL$ or $\pi R^2$) against the wall stress times the wall area ($2tL$ or $2\pi Rt$). 4. For a sphere use $pR/2t$ in all directions. 5. Check $t/R<0.1$ and, for bolted joints, balance the pressure force on the projected disc against the bolt forces.
> - **Common mistakes:** dividing by the wrong wall area (two walls of $tL$ in the hoop cut, not one); using a negative gauge pressure under external pressure and then forgetting that the stresses are compressive and buckling may govern.
> - **Practise:** [[#Worked example - bolted spherical vessel]] · [[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]]

For the long slender members of Statics 1, one stress component is enough: $F/A$ in a bar, $My/I$ in a beam, $Tr/J$ in a shaft. Many real components are not like that. A diving cylinder or a pressurised fuselage is pushed outwards round its circumference and along its length at the same time; a crankshaft is twisted and bent together; a gear tooth is too short to be a slender beam, so its shear stresses matter as much as its bending stress; the concrete at the foot of a dam is squeezed by the water on one side and by its own weight from above (Lecture 1, ll. 66–119). To decide whether such things are strong enough, stresses in several directions have to be described together.

Cutting the body and drawing a free-body diagram exposes the internal forces needed for equilibrium on the cut. The force on a cut has components both normal and parallel to the surface, and the split between them changes with the angle of the cut. A point in a solid therefore has one physical state of stress but many sets of stress components, one for each orientation of the surface you look at. The stress element is the device that handles this.

The thin-walled pressure vessel is the first application. A low pressure acting over a large cross-section of fluid is carried by a thin wall with a small cross-section, so the wall stress is much larger than the pressure, by a factor of order $R/t$. Two simple cuts give the two wall stresses, and the cylinder carries twice as much stress round its circumference as along its length.

---

## 1. Internal forces on a cut

### Normal and shear components

A body loaded by external forces that balance each other, cut with a plane, still has each part in equilibrium, so the material on one side of the cut exerts forces on the material on the other side. These forces are internal: the left part pulls on the right part, and the right part pulls back equally and oppositely on the left (Lecture 1, ll. 126–145).

The force $d\vec F$ on a small patch $dA$ of the cut can be split into a component perpendicular to the surface and components parallel to it. Dividing by the area gives the stresses on that patch:

$$
\sigma_{normal}=\frac{dF_{normal}}{dA},\qquad \sigma_{shear}=\frac{dF_{parallel}}{dA}
$$

In 3D the parallel part has two components, so a cut surface carries one normal stress and two shear stresses. Both kinds act equally and oppositely on the two faces of the cut. The shear components act like friction: if one face drags the other to the right, the other drags the first to the left (Lecture 1, ll. 165–180).

### The stress depends on the cut

The stress components depend on where the cut is made and on how it is oriented. A cut perpendicular to the local force vector carries a force that is entirely normal, with no shear at all; tilting the cut turns part of the force into shear. The physical state at the point has not changed, only its description (Lecture 1, ll. 198–216). A stress value is therefore meaningful only together with the surface it acts on, and the stress element of §2 always has a stated orientation. The change of the components with orientation is derived in [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]].

## 2. The stress element

### Notation

A tiny block of material isolated by cuts on all its sides (a square in 2D, a cube in 3D) has its faces normal to the $x$, $y$ and $z$ axes. Normal stresses act perpendicular to each face and shear stresses parallel to it. Because the block is in equilibrium and small enough for the stress to be uniform across it, every stress on one face is matched by an equal and opposite stress on the opposite face (Lecture 1, ll. 225–251).

Each stress needs two indices: one for the direction in which the stress acts, one for the direction of the normal to the face it acts on. In the FEEG1002 convention the **first index is the direction of the stress and the second is the face normal**. So $\sigma_{xx}$ acts in $x$ on the face whose normal is $x$, a normal stress, while $\sigma_{yx}$ acts in $y$ on the face whose normal is $x$, a shear stress. Equal indices mean a normal stress; different indices mean a shear stress (Lecture 1, ll. 296–316). Textbooks swap the two indices or write $\tau$ for shear; once complementary shear is established in [[#Moment balance and complementary shear]] the order no longer changes any value.

![[s2_stress_element_notation.png|900]]

### Sign convention

Normal stresses are positive in tension, pulling outwards on the face, and negative in compression. A shear stress is positive when it points in the positive $x$ or $y$ direction on a face whose outward normal is in the positive $x$ or $y$ direction: upwards on the right-hand face and to the right on the top face (Lecture 1, ll. 252–295). On the left and bottom faces the outward normal is negative, so a positive shear stress there points in the negative direction; two negatives make a positive. The practical rule is to read signs only from the right-hand and top faces.

> [!warning] Read the shear sign from the right-hand face
> An element drawn with the shear arrow pointing down on the right-hand face and left on the top face has a negative $\sigma_{xy}$, even though the arrows look "natural". The sail in Tutorial 5 ($\sigma_{xy}=-1$ MPa) and Tutorial 8 Q4 ($\sigma_{xy}=-15$ MPa) are both drawn this way, and getting the sign wrong puts the principal direction on the wrong side ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]]).

## 3. Equilibrium of the element

### Force balance with uniform stress

If the stress is the same everywhere in a body, each element is surrounded by copies of itself. The normal stress on the right face is then equal and opposite to that on the left, and likewise for the shear stresses and for the top and bottom faces, so the forces on the element cancel in both directions (Lecture 1, ll. 318–339).

### Moment balance and complementary shear

Force balance is not enough; the element must not spin either. Take a 2D element of sides $dx$ and $dy$ and thickness $h$ out of the plane, with uniform stress, and take moments about its centre, anticlockwise positive. The shear stress $\sigma_{yx}$ on the right face acts upwards on area $h\,dy$ at a lever arm $dx/2$; on the left face it acts downwards at lever arm $-dx/2$. Both give anticlockwise moments:

$$
M_{x\text{-faces}}=\sigma_{yx}h\,dy\cdot\frac{dx}{2}+\sigma_{yx}h\,dy\cdot\frac{dx}{2}
$$

$$
M_{x\text{-faces}}=\sigma_{yx}h\,dx\,dy
$$

The shear stress $\sigma_{xy}$ on the top face acts to the right on area $h\,dx$ at height $dy/2$, and on the bottom face to the left at height $-dy/2$. Both give clockwise moments:

$$
M_{y\text{-faces}}=-\sigma_{xy}h\,dx\cdot\frac{dy}{2}-\sigma_{xy}h\,dx\cdot\frac{dy}{2}
$$

$$
M_{y\text{-faces}}=-\sigma_{xy}h\,dx\,dy
$$

Rotational equilibrium requires the sum to vanish:

$$
\sigma_{yx}h\,dx\,dy-\sigma_{xy}h\,dx\,dy=0
$$

$$
\boxed{\sigma_{xy}=\sigma_{yx}}
$$

This is **complementary shear**: the shear stresses on perpendicular faces are equal, and they point either both towards or both away from the corner they share. Only $\sigma_{xy}$ is written, being the value of the shear stress on both the $x$-face and the $y$-face (Lecture 1, ll. 340–376). The same pair occurs in a beam, where the shear stress on a horizontal plane equals that on the vertical section ([[FEEG1002 A9 - Shear Stresses in Beams]]).

### Stress in three dimensions

A cube element has a normal stress on each of its three visible faces and two shear stresses on each. Complementary shear applies in each of the three planes, so $\sigma_{xy}=\sigma_{yx}$, $\sigma_{xz}=\sigma_{zx}$ and $\sigma_{yz}=\sigma_{zy}$, leaving six independent components: three normal stresses $\sigma_{xx}$, $\sigma_{yy}$, $\sigma_{zz}$ and three shear stresses $\sigma_{xy}$, $\sigma_{xz}$, $\sigma_{yz}$ (Lecture 1, ll. 378–397). They can be collected in a symmetric matrix, the stress tensor, whose row and column order matches the index convention above:

$$
\boldsymbol\sigma=\begin{bmatrix}\sigma_{xx}&\sigma_{xy}&\sigma_{xz}\\ \sigma_{xy}&\sigma_{yy}&\sigma_{yz}\\ \sigma_{xz}&\sigma_{yz}&\sigma_{zz}\end{bmatrix}
$$

These six numbers, for one orientation of the axes, describe the stress state at the point completely.

### Non-uniform stress

When the stress varies with position, the stresses on opposite faces differ slightly, and equilibrium becomes a balance of gradients. Take the 2D element again, neglect body forces such as weight, and let $\sigma_{xx}$ change by $(\partial\sigma_{xx}/\partial x)dx$ across the element and $\sigma_{xy}$ change by $(\partial\sigma_{xy}/\partial y)dy$ from bottom to top. The net force in $x$ is

$$
\left(\sigma_{xx}+\frac{\partial\sigma_{xx}}{\partial x}dx\right)h\,dy-\sigma_{xx}h\,dy+\left(\sigma_{xy}+\frac{\partial\sigma_{xy}}{\partial y}dy\right)h\,dx-\sigma_{xy}h\,dx=0
$$

$$
\frac{\partial\sigma_{xx}}{\partial x}h\,dx\,dy+\frac{\partial\sigma_{xy}}{\partial y}h\,dx\,dy=0
$$

$$
\boxed{\frac{\partial\sigma_{xx}}{\partial x}+\frac{\partial\sigma_{xy}}{\partial y}=0}
$$

and the same argument in $y$ gives $\partial\sigma_{xy}/\partial x+\partial\sigma_{yy}/\partial y=0$. A gradient in normal stress along $x$ must be balanced by a gradient in shear stress across $y$. This is the mechanism behind the shear stress in a beam: the bending stress grows along the beam, and the shear stress grows from the free surface inwards to keep each strip in equilibrium (Lecture 1, ll. 398–413).

## 4. Thin-walled pressure vessels

### Axes and the wall element

A pressure vessel is thin-walled when its wall thickness $t$ is small compared with its radius $R$; the working rule is $t/R<0.1$ (Lecture 1, ll. 425–427). Put a 2D stress element on the wall with $x$ along the axis and $y$ round the circumference. Then $\sigma_{xx}$ is the **longitudinal stress** and $\sigma_{yy}$ is the **hoop stress**, named after the metal hoops that stop a wooden barrel bursting (Lecture 1, ll. 446–458). The load is axisymmetric and nothing twists the vessel, so there is no torsion and no shear stress on an element in this orientation: $\sigma_{xy}=0$, and the axial and hoop directions are already principal directions in the sense of [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]].

![[s2_pressure_vessel_stresses.png|900]]

### Hoop stress

The free body is a length $L$ of the cylinder cut along a horizontal diameter: the upper half, together with the fluid inside it. The fluid below pushes up on the flat cut face of the contents with pressure $p$ over the rectangle of area $2RL$. The wall is cut twice, each cut of area $tL$, and the hoop stress pulls down on both (Lecture 1, ll. 471–514). Vertical equilibrium gives

$$
\sum F_v=0:\qquad pA_{h,inside}=\sigma_{yy}A_{h,wall}
$$

$$
p(2RL)=\sigma_{yy}(2tL)
$$

$$
\sigma_{yy}=\frac{2pRL}{2tL}
$$

$$
\boxed{\sigma_{yy}=\frac{pR}{t}}
$$

Because $R/t>10$ for a thin wall, the hoop stress is always more than ten times the pressure.

### Longitudinal stress

For the axial stress the free body is the left-hand part of the vessel cut across the axis, end cap and contents included. The fluid to the right pushes on the cut face of the contents with $p$ over the disc $\pi R^2$; the wall stress $\sigma_{xx}$ acts on the annulus of wall (Lecture 1, ll. 525–554). The exact annulus area is

$$
A_{v,wall}=\pi\left[(R+t)^2-R^2\right]
$$

$$
A_{v,wall}=\pi(2Rt+t^2)
$$

$$
A_{v,wall}=2\pi Rt\left(1+\frac{t}{2R}\right)
$$

For a thin wall the bracket is within 5 % of 1, so the annulus is treated as a straightened strip of length $2\pi R$ and thickness $t$, $A_{v,wall}\approx2\pi Rt$. Horizontal equilibrium then gives

$$
\sum F_h=0:\qquad p(\pi R^2)=\sigma_{xx}(2\pi Rt)
$$

$$
\sigma_{xx}=\frac{p\pi R^2}{2\pi Rt}
$$

$$
\boxed{\sigma_{xx}=\frac{pR}{2t}}
$$

The hoop stress is twice the longitudinal stress, so a cylinder that is overpressurised splits along its length: the crack opens against the larger hoop stress.

### Why only the projected area matters

It can look like a shortcut to replace the pressure on the curved inside wall by a pressure on a flat cut through the contents. Integrating the real pressure gives the same answer. On a strip of the half-cylinder at angle $\phi$ from the horizontal, of width $R\,d\phi$ and length $L$, the pressure force is $pRL\,d\phi$ normal to the wall, with vertical component $pRL\sin\phi\,d\phi$. Over the half-circle,

$$
F_v=\int_0^\pi pRL\sin\phi\,d\phi
$$

$$
F_v=pRL\Big[-\cos\phi\Big]_0^\pi
$$

$$
F_v=2pRL
$$

which is the pressure times the projected area $2RL$ (Lecture 1, ll. 582–600). The same reasoning shows that the shape of the end caps does not affect $\sigma_{xx}$: the axial force on any cap, flat, hemispherical or pointed, is $p\pi R^2$. If a pointed cap pushed harder than a flat one, a sealed bottle would propel itself (Lecture 1, ll. 601–624).

### The radial stress

The inner surface of the wall is pressed by $p$ and the outer surface by nothing, so a radial stress varying from $-p$ to $0$ acts through the thickness, normal to the 2D element. Compared with the hoop stress it is at most

$$
\frac{p}{\sigma_{yy}}=\frac{p}{pR/t}=\frac{t}{R}<0.1
$$

so it is neglected and the wall is treated as being in plane stress (Lecture 1, ll. 565–581). This is what lets the plane-stress form of Hooke's law be used for vessel strains in [[FEEG1002 B3 - Generalised Hooke's Law|B3]].

### Spherical vessels

A sphere looks the same through every diametral cut, so $\sigma_{xx}=\sigma_{yy}$ in any orientation of the wall element. The horizontal balance of a hemisphere and its contents is the same as for the cylinder's end:

$$
p(\pi R^2)=\sigma(2\pi Rt)
$$

$$
\boxed{\sigma_{xx}=\sigma_{yy}=\frac{pR}{2t}}
$$

For the same $p$, $R$ and $t$, the peak stress in a sphere is half the hoop stress in a cylinder, or for the same allowable stress a sphere needs half the wall thickness. That is why deep-diving submersibles use spherical pressure hulls (Lecture 1, ll. 625–667). With equal stresses in every direction, the wall of a sphere carries no shear stress on any plane through the thickness.

### When the thin-wall model holds

The model needs $t/R<0.1$. Inner and outer radii are then nearly equal, and the difference is ignored; using the outer radius gives the larger stress and so is the conservative choice when sizing a wall, while the mean radius is more accurate (Lecture 1, ll. 649–661). Thicker walls need the Lamé thick-cylinder solution of Year 2 ([[SESA2028 S10 - Thick Cylinders and Shrink Fits]], [[Lame Thick-Cylinder Solution]]), whose hoop stress tends to $pR/t$ as $t\to0$. Under external pressure $p$ is negative, the stresses become compressive, and the wall can buckle long before it yields ([[FEEG1002 A7 - Euler Buckling of Struts]]); Tutorial 3 applies this to an acrylic submersible hull ([[FEEG1002 B3 - Generalised Hooke's Law#Worked example - submersible hull at 100 m|B3]]).

---

## Worked examples

### Worked example - bolted spherical vessel

A thin-walled sphere of diameter 400 mm and wall thickness 6 mm is made of two halves held together by 24 bolts of 18 mm diameter. The allowable wall stress is 180 MPa. Find the maximum working pressure and the bolt stress it causes, ignoring any gasket preload (Tutorial 1 Q1).

With $R=0.2$ m, $t/R=0.03$, so the thin-wall model applies. Setting the sphere stress to its allowable value,

$$
\frac{pR}{2t}=\sigma_{allow}
$$

$$
p_{max}=\frac{2t\sigma_{allow}}{R}=\frac{2(6\times10^{-3})(180\times10^6)}{0.2}=10.8\ \mathrm{MPa}
$$

For the bolts, take the upper hemisphere and its contents as the free body and cut through the bolts. The pressure acts upwards on the projected disc and the 24 bolts pull down:

$$
p\pi R^2=24F_{bolt}
$$

$$
F_{bolt}=\frac{(10.8\times10^6)\pi(0.2)^2}{24}=56.5\ \mathrm{kN}
$$

$$
\sigma_{bolt}=\frac{F_{bolt}}{\pi(9\times10^{-3})^2}=222\ \mathrm{MPa}
$$

The bolts are more highly stressed than the wall, so in practice they would be a higher-strength grade, or larger or more numerous, and preloaded beyond the separating force of 1357 kN so that the joint does not open.

### Worked example - aircraft fuselage skin

A narrow-body fuselage has a radius of about 1.98 m, a skin about 1.6 mm thick and a cabin pressure differential at cruise of about 56 kPa (illustrative values, suggested, not lecturer-set). Treating the skin alone as the pressure vessel, ignoring stringers and frames,

$$
\sigma_{yy}=\frac{pR}{t}=\frac{(56\times10^3)(1.98)}{1.6\times10^{-3}}=69.3\ \mathrm{MPa},\qquad \sigma_{xx}=\frac{pR}{2t}=34.7\ \mathrm{MPa}
$$

Here $t/R=8\times10^{-4}$ and $p/\sigma_{yy}$ is the same tiny number, so the radial stress is negligible. The hoop stress is cycled once per flight, which is why fatigue cracks in fuselages tend to run along longitudinal lap joints ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]).

### Worked example - sizing a diving cylinder

A steel diving cylinder of radius 85 mm is charged to 200 bar (20 MPa). What wall thickness keeps the hoop stress at 400 MPa? (Suggested, not lecturer-set; the diving cylinder is the opening example at Lecture 1, ll. 68–74.)

$$
t=\frac{pR}{\sigma_{yy}}=\frac{(20\times10^6)(0.085)}{400\times10^6}=4.25\ \mathrm{mm}
$$

so $t/R=0.05$ and the thin-wall model is acceptable. The longitudinal stress is then $pR/2t=200$ MPa. A spherical bottle of the same radius would need only 2.1 mm, but a sphere is awkward to carry on your back.

> [!check] Equilibrium of the whole end cap
> In the diving cylinder, the axial force on the cap is $p\pi R^2=20\times10^6\times\pi(0.085)^2=454$ kN, and the wall carries $\sigma_{xx}\times2\pi Rt=200\times10^6\times2\pi(0.085)(4.25\times10^{-3})=454$ kN. The two cuts are just force balances.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A9 - Shear Stresses in Beams]] · Next: [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]
- Concepts: [[Stress Tensor and Stress Element]] · [[Thin-Walled Pressure Vessels]]
- Worked sheet: [[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 B3 - Generalised Hooke's Law|B3]] (vessel strains) · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]] (helical welds) · [[FEEG1002 B6 - Yield Criteria|B6]] (vessel yield)
- Year 2: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] ([[Axisymmetric Equilibrium]] is the differential form of the cuts above) · [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] · [[SESA2028 S11 - Spinning Discs]]

## Sources

- `Lecture 01 - Stress in Multiple Dimensions and Pressure Vessels.pdf`: Lectures 1a–1c, internal forces, stress elements, stress definitions, equilibrium, 3D stress state, pressure vessels.
- `FEEG1002 Lecture 1 - Statics 2 - Stresses in multiple dimesnions and pressure vessels - Jan.txt` (27 Jan 2025): motivation (ll. 1–125), internal forces (ll. 126–216), stress element and notation (ll. 217–316), equilibrium and complementary shear (ll. 317–377), 3D state (ll. 378–397), non-uniform stress (ll. 398–413), pressure vessels (ll. 420–667).
- `FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt` (12 May 2025): recap of signs and pressure vessels (ll. 48–107).
- `Tutorial Sheet 01 - Stresses in Multiple Dimensions and Pressure Vessels.pdf` and its solutions: Q1.

## Self-study tasks

### Core

- [ ] Tutorial 1 Q1, bolted spherical vessel (set for the tutorial two weeks after Lecture 1, l. 673). Targets 10.8 MPa and 222 MPa. → [[#Worked example - bolted spherical vessel]] · [[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]]
- [ ] Prove $\sigma_{xy}=\sigma_{yx}$ by taking moments about the centre of an element (Lecture 1, ll. 340–352). → [[#Moment balance and complementary shear]]
- [ ] Derive the hoop and longitudinal stresses from the two cuts, and show how close $2\pi Rt$ is to the exact annulus (Lecture 1, ll. 471–564). → [[#Hoop stress]] · [[#Longitudinal stress]]

### Further practice

- [ ] Integrate the pressure over the curved half-cylinder and show it gives $2pRL$ (Lecture 1, ll. 582–600). → [[#Why only the projected area matters]]
- [ ] Derive $\partial\sigma_{xx}/\partial x+\partial\sigma_{xy}/\partial y=0$ and its $y$ counterpart (Lecture 1, ll. 398–413). → [[#Non-uniform stress]]
- [ ] Size the diving cylinder and repeat for a sphere of the same radius (suggested, not lecturer-set). → [[#Worked example - sizing a diving cylinder]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 1, l. 663; Lecture 9, l. 96)
> Where: [[#Spherical vessels]].
>
> A spherical vessel is said to have "no hoop stress, so we only have that axial stress", and in the revision lecture "only those longitudinal stresses". A sphere has no distinct hoop or axial direction: the stress is $pR/2t$ in every direction in the wall, as the slide states ($\sigma_{xx}=\sigma_{yy}=pR/2t$).
