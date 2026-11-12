---
title: "FEEG1002 A8 - Torsion of Circular Shafts"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 8
tags: [feeg1002, statics, torsion, shafts, polar-second-moment, shear-stress]
aliases: ["Statics 1 Lecture 13", "Torsion", "T/J = tau/r = G theta/L", "Torsion equations"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 13 (10 Dec 2024, ll. 3–563: torque and shafts, deformation of a circular shaft, angle of twist, shear strain and stress, torque–twist relation, polar second moment of area, torsion equations, solid against hollow shafts); slide deck 13 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]", "[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[FEEG1002 A9 - Shear Stresses in Beams]]"]
key_concepts: ["[[Torsion of Circular Shafts]]", "[[Saint-Venant Torsion]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 13 - Torsion.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 13 - Statics 1 - Torsion - December 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress - Solutions.pdf"
---

# FEEG1002 A8 - Torsion of Circular Shafts

> [!abstract] Summary
> A circular shaft under a torque $T$ twists without warping: cross-sections stay plane and circular, radial lines stay straight, and each section rotates rigidly relative to its neighbours. The material is in pure shear, with a shear strain that grows linearly from the axis, $\gamma=r\theta/L$, so the shear stress $\tau=G\gamma$ grows linearly too. Adding up the torque of these stresses over the section gives $T=GJ\theta/L$, where $J=\pi R^4/2=\pi D^4/32$ is the polar second moment of area, and the torsion equations $T/J=G\theta/L=\tau/r$. Because the core of a solid shaft carries little stress, a hollow shaft of slightly larger diameter carries the same torque at much lower weight.

> [!summary]- Exam use: quick path
> - **Use it when:** a circular shaft or tube carries a torque and its maximum shear stress, angle of twist or required size is wanted.
> - **Assumptions:** circular cross-section, solid or hollow; linear elastic material, $\tau=G\gamma$; small twist angles in radians, so $\tan\varphi\approx\varphi$; constant torque and section along the length $L$.
> - **Method:** 1. Find the torque carried by the length of shaft in question. 2. Compute $J=\pi D^4/32$, or $\pi(D_o^4-D_i^4)/32$ for a tube. 3. The maximum shear stress is at the outer surface, $\tau_{max}=TR/J$. 4. The angle of twist is $\theta=TL/GJ$. 5. For sizing, rearrange $J/R=T/\tau_{allow}$.
> - **Common mistakes:** using the bending second moment $I=\pi D^4/64$ instead of $J=\pi D^4/32$; using the inner radius for the maximum stress of a tube.
> - **Practise:** [[#Worked example - solid steel drive shaft]] · [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q2 - Steel shaft and aluminium tube|Tutorial 6 Q2]]

Moments do not only bend members; applied about a member's own axis, they twist it. A car's drive shaft carries the engine's torque to the wheels, and a ship's propeller shaft carries it to the propeller; with the propeller held still and the engine turning, the shaft twists. Moments about the longitudinal axis are called **torques**, symbol $T$, and a member loaded this way is in **torsion**.

For a circular shaft the deformation is simple. Lines drawn along the shaft and circles drawn around it before loading show the deformation. Under a torque the circles stay circles and stay where they are along the shaft, but each rotates a little relative to its neighbour, so the longitudinal lines become gentle helices. Nothing gets longer or shorter, and the diameter does not change: the material is in pure shear. The analysis then follows the pattern of bending theory: geometry gives a strain that is linear in position, Hooke's law turns it into a stress, and adding up the moments of the stresses relates them to the applied load.

This only works for circular sections, solid or hollow. Other shapes, an I-beam or a rectangular bar, warp out of plane when twisted, which this theory does not cover.

---

## 1. Deformation of a circular shaft

### Internal torque

At any cut along a shaft carrying a torque $T$, each part must stay in equilibrium, so across the cut each part exerts an equal and opposite torque on the other, as if the two faces were glued together or held by friction. Looking at each cut face from outside the part it belongs to, the internal torque turns both faces the same way round.

### Compatibility: sections stay plane, radii stay straight

Two arguments from compatibility fix the deformation. Suppose a cross-section bulged outwards under the torque. Seen from the other side of the cut, the same torque on the other face would have to make it bulge outwards too, by symmetry, and two bulging faces could not fit together. So cross-sections must remain flat. Similarly, if a radial line on the face curved, the matching line on the opposite face would curve the other way and the material would split open. So radial lines stay straight.

The deformation is therefore: cross-sections remain circular and flat, radial lines remain straight, and the shaft deforms only by one cross-section rotating relative to the next. These statements hold only for circular sections.

### Angle of twist

Let the free end of a shaft of length $L$ rotate through an angle $\theta$ (in radians) relative to the fixed end: the **angle of twist**. Each slice rotates a little relative to the next, so the twist accumulates along the shaft and is proportional to $L$.

## 2. Shear strain and shear stress

### Strain at the surface

A small element drawn on the outer surface, originally rectangular, is sheared into a parallelogram as the shaft twists; its length and width do not change. Unwrapping the surface of the shaft like a sheet of paper shows the shear angle: a line originally parallel to the axis, of length $L$, has its far end moved sideways by the arc length $R\theta$, where $R$ is the outer radius. The line is now tilted by a small angle $\varphi$, and the engineering shear strain ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Shear strain and the shear modulus|A1]]) is

$$
\gamma=\tan\varphi=\frac{R\theta}{L}
$$

with $\tan\varphi\approx\varphi$ for the small angles of real shafts.

![[s1_torsion_shear_strain.png|900]]

### Shear stress at the surface

The element is in pure shear, so its shear stress follows from the shear modulus $G$:

$$
\tau=G\gamma
$$

$$
\tau=\frac{GR\theta}{L}
$$

The shear modulus is related to Young's modulus and Poisson's ratio by $G=E/2(1+\nu)$, derived in Statics 2 ([[FEEG1002 B3 - Generalised Hooke's Law|B3]]).

### Inside the shaft

The strain above applies at the outer surface. Because radial lines stay straight, a point at radius $r$ moves through the arc $r\theta$, shorter than at the surface, and the same unwrapping argument on a cylinder of radius $r$ gives

$$
\gamma(r)=\frac{r\theta}{L}
$$

The shear strain is directly proportional to the distance from the axis, and so is the shear stress:

$$
\tau(r)=\frac{Gr\theta}{L}
$$

zero on the axis and largest at the outer surface.

## 3. Torque and the polar second moment of area

### Adding up the torque

The relation between the twist and the torque comes from adding up the contribution of every element of the section. Take an element at radius $r$ with radial width $dr$ and angular width $d\psi$ (in radians), so its area is $r\,d\psi\,dr$. The shear stress $\tau$ acts on it tangentially, producing a force

$$
dF=\tau\,r\,d\psi\,dr
$$

whose moment about the axis is

$$
dT=r\,dF=\tau\,r^2\,d\psi\,dr
$$

The total torque on the section is the sum over all elements:

$$
T=\int_0^R\int_0^{2\pi}\tau\,r^2\,d\psi\,dr
$$

Integrating over $\psi$ first adds up a thin ring of radius $r$ and wall thickness $dr$; integrating over $r$ then adds up the rings, so the shaft can be thought of as a set of thin concentric cylinders.

### Integrating

Substitute $\tau(r)=Gr\theta/L$. The factors $G$, $\theta$ and $L$ are the same for every element and come outside:

$$
T=\frac{G\theta}{L}\int_0^R\int_0^{2\pi}r^3\,d\psi\,dr
$$

The $r^3$ collects one factor of $r$ from the stress, one from the area of the element and one from the lever arm. Integrate over $\psi$:

$$
T=\frac{G\theta}{L}\int_0^R r^3\Big[\psi\Big]_0^{2\pi}dr=\frac{2\pi G\theta}{L}\int_0^R r^3\,dr
$$

and over $r$:

$$
T=\frac{2\pi G\theta}{L}\left[\frac{r^4}{4}\right]_0^R=\frac{\pi G\theta R^4}{2L}
$$

### The polar second moment of area

Collect the geometry into one quantity:

$$
T=\frac{GJ\theta}{L},\qquad J=\frac{\pi R^4}{2}=\frac{\pi D^4}{32}
$$

$J$ is the **polar second moment of area**. In general it is

$$
J=\iint r^2\,dA
$$

which for the solid circle is $\int_0^R r^2\,2\pi r\,dr=\pi R^4/2$, the integral just evaluated. For a hollow shaft of outer radius $R_o$ and inner radius $R_i$, subtract the missing core:

$$
J_{hollow}=\frac{\pi R_o^4}{2}-\frac{\pi R_i^4}{2}=\frac{\pi(R_o^4-R_i^4)}{2}=\frac{\pi(D_o^4-D_i^4)}{32}
$$

### The torsion equations

Combining $T=GJ\theta/L$ with $\tau=Gr\theta/L$ gives three equal ratios, the **torsion equations**:

$$
\boxed{\frac TJ=\frac{G\theta}{L}=\frac\tau r}
$$

The maximum shear stress is at the outer radius, $\tau_{max}=TR/J$, and the angle of twist is $\theta=TL/GJ$. The quantity $GJ/L$ is the shaft's torsional stiffness, the torque per radian of twist. The analysis is valid only for circular shafts; other cross-sections are more complicated.

The results closely resemble engineer's bending theory, term for term:

| Bending ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area\|A4]]) | Torsion |
|---|---|
| $\dfrac MI=\dfrac ER=\dfrac\sigma y$ | $\dfrac TJ=\dfrac{G\theta}{L}=\dfrac\tau r$ |
| normal stress, linear in $y$ | shear stress, linear in $r$ |
| $I=\iint y^2\,dA$ | $J=\iint r^2\,dA$ |
| circle: $I=\pi D^4/64$ | circle: $J=\pi D^4/32$ |

> [!warning] Do not confuse J and I
> For a circle $J=2I$: the 32 and the 64 differ by a factor of two, and using the wrong one doubles or halves the answer. The factor comes from $r^2=y^2+z^2$, so $J=\iint y^2\,dA+\iint z^2\,dA=I_{zz}+I_{yy}=2I$ for a circle, where $I_{yy}=I_{zz}=I$. Neither is the mass moment of inertia of dynamics ([[Mass Moment of Inertia and Radius of Gyration]]); calling $I$ a "moment of inertia", common in American texts, invites exactly that mix-up. Check which quantity a formula needs before using it.

## 4. Solid and hollow shafts

### Why hollow

In a solid shaft the material on the outside carries high shear stresses, while the material near the axis carries very little: the stress is zero on the axis and grows linearly. That core material adds weight without doing much. The material can be used far more efficiently by leaving the centre out and making the shaft hollow.

### Comparing a solid and a hollow shaft

Consider a solid shaft of radius $R_s$ and a hollow shaft of inner radius $R_i$ and outer radius $R_o$. Both must carry the same torque, with the same maximum allowable shear stress in the same material. For both, the maximum shear stress is at the outer surface, so the torsion equations give

$$
\tau_{max}=\frac{TR_s}{J_{solid}}=\frac{TR_o}{J_{hollow}}
$$

and since the torque is the same,

$$
\frac{J_{solid}}{R_s}=\frac{J_{hollow}}{R_o}
$$

The polar second moments are

$$
J_{solid}=\frac{\pi R_s^4}{2},\qquad J_{hollow}=\frac{\pi(R_o^4-R_i^4)}{2}=\frac{\pi R_o^4(1-n^4)}{2}
$$

using the ratio of inner to outer radius,

$$
n=\frac{R_i}{R_o}
$$

($n=0.5$ means the inner radius is half the outer.) Substitute into the equal-stress condition:

$$
\frac{\pi R_s^4}{2R_s}=\frac{\pi R_o^4(1-n^4)}{2R_o}
$$

$$
R_s^3=R_o^3(1-n^4)
$$

$$
R_s=R_o(1-n^4)^{1/3}
$$

### Weight ratio

For shafts of the same length and material, the weight is proportional to the cross-sectional area:

$$
\frac{W_{hollow}}{W_{solid}}=\frac{\pi(R_o^2-R_i^2)}{\pi R_s^2}=\frac{R_o^2}{R_s^2}(1-n^2)
$$

Square the radius relation, $R_o^2/R_s^2=(1-n^4)^{-2/3}$, and substitute:

$$
\boxed{\frac{W_{hollow}}{W_{solid}}=\frac{1-n^2}{(1-n^4)^{2/3}}}
$$

with the outer radius $R_o=R_s(1-n^4)^{-1/3}$.

| $n=R_i/R_o$ | $R_o/R_s$ | $W_{hollow}/W_{solid}$ |
|---|---|---|
| 0.5 | 1.02 | 0.78 |
| 0.8 | 1.19 | 0.51 |
| 0.9 | 1.43 | 0.39 |

A hollow shaft with $n=0.5$ is 22 % lighter and only 2 % larger in outside radius. With $n=0.9$, a wall one-tenth of the outer radius thick, it is 61 % lighter but 43 % larger. The hollow shaft saves a great deal of weight but is less compact: if space is tight or the part must be simple to make, use a solid shaft; if there is room, a larger hollow shaft, like the big tubular drive shaft of a lorry, is far more efficient.

![[s1_torsion_hollow_vs_solid.png|900]]

---

## Worked examples

### Worked example - solid steel drive shaft

A solid steel shaft of diameter 40 mm and length 1.2 m transmits a torque of 1.5 kN m; $G=80$ GPa. Find the maximum shear stress and the angle of twist.

$$
J=\frac{\pi(0.04)^4}{32}=2.513\times10^{-7}\ \mathrm{m^4}
$$

$$
\tau_{max}=\frac{TR}{J}=\frac{(1500)(0.02)}{2.513\times10^{-7}}=119.4\ \mathrm{MPa}
$$

$$
\theta=\frac{TL}{GJ}=\frac{(1500)(1.2)}{(80\times10^9)(2.513\times10^{-7})}=0.0895\ \mathrm{rad}=5.13^\circ
$$

> [!check] Strain at the surface
> $\gamma=R\theta/L=(0.02)(0.0895)/1.2=1.49\times10^{-3}$, and $G\gamma=80\times10^9\times1.49\times10^{-3}=119.4$ MPa, matching $\tau_{max}$. The shear angle is under 0.1°, so $\tan\varphi\approx\varphi$ is excellent.

### Worked example - a hollow replacement

Replace the shaft with a hollow one of $n=0.8$ carrying the same torque at the same maximum stress. Its outer radius is

$$
R_o=R_s(1-n^4)^{-1/3}=20(1-0.4096)^{-1/3}=23.84\ \mathrm{mm}
$$

so the outside diameter is 47.7 mm and the bore 38.1 mm. The weight ratio is

$$
\frac{W_{hollow}}{W_{solid}}=\frac{1-0.64}{(0.5904)^{2/3}}=0.51
$$

about half. Its polar second moment is larger than the solid shaft's, $J/R$ being equal and $R$ larger, so it also twists less: 4.3° against 5.1°.

### Worked example - steel shaft and aluminium tube

Tutorial 6 Q2 joins a solid steel shaft end to end with an aluminium tube of outside diameter 70 mm, transmitting 3 kN m; the shear stress in the aluminium must not exceed 150 MPa. Find the largest bore, and the stress in a steel shaft that just fits it.

Both parts carry the same torque. For the tube, the maximum stress is at the outer radius $R_o=35$ mm:

$$
\tau_{max}=\frac{TR_o}{J}=\frac{2TR_o}{\pi(R_o^4-R_i^4)}
$$

$$
R_o^4-R_i^4=\frac{2TR_o}{\pi\tau_{max}}
$$

$$
R_i=\left(R_o^4-\frac{2TR_o}{\pi\tau_{max}}\right)^{1/4}=\left(0.035^4-\frac{2(3000)(0.035)}{\pi(150\times10^6)}\right)^{1/4}=0.0320\ \mathrm m
$$

so the bore is 64 mm and the wall only 3 mm thick ($n=0.92$). A solid steel shaft of radius 32 mm carries

$$
\tau_{max}=\frac{2T}{\pi R^3}=\frac{2(3000)}{\pi(0.032)^3}=58\ \mathrm{MPa}
$$

The thin aluminium tube has the smaller $J/R$ ($2.0\times10^{-5}$ m³ against $5.2\times10^{-5}$ m³ for the steel), so it works at the higher stress.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A7 - Euler Buckling of Struts]] · Next: [[FEEG1002 A9 - Shear Stresses in Beams]]
- Concepts: [[Torsion of Circular Shafts]] · [[Saint-Venant Torsion]] · [[Stress, Strain and Young's Modulus]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Related: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]] (the bending analogue) · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]] (pure shear has principal stresses $\pm\tau$ at 45°) · [[FEEG1002 D8 - Kinetics of Rigid Bodies|D8]] (the mass moment of inertia, not to be confused with $I$ or $J$)
- Year 2: non-circular sections in [[SESA2028 S4 - Torsion of Thin-Walled Sections]] ([[Open-Section Torsion]], [[Bredt-Batho Torsion]], [[Multi-Cell Torsion]])

## Sources

- `Lecture 13 - Torsion.pdf` (S1 Lectures 13a–13c, 25 slides), read in full.
- `FEEG1002 Lecture 13 - Statics 1 - Torsion - December 2024.txt` (Lecture 13): torque and shafts (ll. 3–33), deformation and compatibility (ll. 34–119), angle of twist and pure shear (ll. 120–146), shear strain at the surface (ll. 147–189), shear modulus (ll. 190–203), strain and stress inside the shaft (ll. 210–240), torque integration (ll. 241–346), polar second moment and the torsion equations (ll. 347–375), $J$ against $I$ (ll. 377–397), solid against hollow shafts (ll. 398–556).
- Tutorial Sheet 06 and its official solutions: Q2.
- All numbers recomputed in Python.

## Self-study tasks

### Core

- [ ] Argue from compatibility why cross-sections of a circular shaft stay plane and radii stay straight (L13, ll. 82–112). → [[#Compatibility: sections stay plane, radii stay straight]]
- [ ] Derive $T=GJ\theta/L$ from the shear stress distribution, and write down the torsion equations (L13, ll. 241–375). → [[#3. Torque and the polar second moment of area]]
- [ ] Find $J$ for a hollow shaft (class question, L13, l. 450), then derive the weight ratio of hollow to solid shafts and check the values for $n=0.5$ and 0.9 (L13, ll. 398–541). Targets 0.78 and 0.39. → [[#4. Solid and hollow shafts]]
- [ ] Tutorial 6 Q2: bore of the aluminium tube and stress in the steel shaft. Targets 64 mm and 58 MPa. → [[#Worked example - steel shaft and aluminium tube]] · [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q2 - Steel shaft and aluminium tube|Tutorial 6 Q2]]

### Further practice

- [ ] Show that $J=2I$ for a circle from $r^2=y^2+z^2$ (the 32 against 64 warning, L13, ll. 363–378). → [[#The torsion equations]]
- [ ] Compute the shear stress and twist of a 40 mm steel shaft under 1.5 kN m, then design a hollow shaft with $n=0.8$ for the same stress (suggested, not lecturer-set). Targets 119 MPa, 5.1° and 47.7 mm outside diameter. → [[#Worked example - solid steel drive shaft]] · [[#Worked example - a hollow replacement]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 13, ll. 205 and 216)
> Where: [[#Shear stress at the surface]] · [[#Inside the shaft]].
>
> At l. 205 $\gamma$ is called the "engineering shear stress"; it is the engineering shear strain, as l. 181 has it. At l. 216, moving inwards, "this radial distance now becomes smaller"; it is the circumferential arc $r\theta$ that becomes smaller, while the radial lines themselves stay straight.
