---
title: "FEEG1002 B6 - Yield Criteria"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 15
tags: [feeg1002, statics-2, yield, tresca, von-mises, equivalent-stress, safety-factor]
aliases: ["Statics 2 Lecture 8", "Tresca", "Von Mises", "Equivalent stress", "Limit analysis"]
date: 2026-11-05
status: lectured
coverage: "Statics 2 Lecture 8 (17 Mar 2025, ll. 1–644): the tensile test and the yield stress, the Tresca criterion in 3D and plane stress and its hexagon, the von Mises criterion, equivalent stress, the ellipse, torsion-test evidence, the yield cylinder and hydrostatic stress, limitations, failure load and safety factor; recap in Lecture 9 (12 May 2025, ll. 516–551)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
next_topics: ["[[FEEG1002 C1 - Atoms and Bonding]]"]
key_concepts: ["[[Tresca Yield Criterion]]", "[[Von Mises Yield Criterion]]", "[[Principal Stresses]]", "[[Mohr's Circle]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]]", "[[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 08 - Yield Criteria.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 8 - Statics 2 - Yield criteria - March 2025.txt", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 07 - Yield Criteria.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems.pdf"]
---

# FEEG1002 B6 - Yield Criteria

> [!abstract] Summary
> A tensile test gives one number, the yield stress $\sigma_Y$; a yield criterion condenses a multiaxial stress state into one number that can be compared with it. For ductile metals, which yield by shear, two criteria are standard. Tresca says yield starts when the largest shear stress on any plane reaches $\sigma_Y/2$, that is when $\max(|\sigma_I-\sigma_{II}|,|\sigma_I-\sigma_{III}|,|\sigma_{II}-\sigma_{III}|)=\sigma_Y$. Von Mises uses the root mean square of the three maximum shear stresses, giving the equivalent stress $\sigma_{eq}=\sqrt{\tfrac12[(\sigma_I-\sigma_{II})^2+(\sigma_I-\sigma_{III})^2+(\sigma_{II}-\sigma_{III})^2]}$, which in plane stress is $\sigma_{eq}=\sqrt{\sigma_{xx}^2+\sigma_{yy}^2-\sigma_{xx}\sigma_{yy}+3\sigma_{xy}^2}$. Because the analysis is linear, $SF=\sigma_Y/\sigma_{eq}$ and the load at first yield is $SF$ times the applied load.

> [!summary]- Exam use: quick path
> - **Use it when:** a component carries stresses in more than one direction (combined axial load and torsion, a pressure vessel, a rosette-measured state, an FE result) and you need to know whether it yields, the safety factor or the maximum load.
> - **Assumptions:** ductile, isotropic material with the same yield stress in tension and compression; linear elastic up to first yield, so stresses scale with load; plane stress unless told otherwise, with $\sigma_{III}=0$ normal to the surface.
> - **Method:** 1. Find $\sigma_{xx}$, $\sigma_{yy}$, $\sigma_{xy}$ at the critical point (pressure vessel formulas, torsion, bending, rosette plus Hooke). 2. Von Mises: $\sigma_{eq}=\sqrt{\sigma_{xx}^2+\sigma_{yy}^2-\sigma_{xx}\sigma_{yy}+3\sigma_{xy}^2}$. 3. Or Tresca: principal stresses from Mohr's circle, then the largest of $|\sigma_I-\sigma_{II}|$, $|\sigma_I|$, $|\sigma_{II}|$. 4. $SF=\sigma_Y/\sigma_{eq}$. 5. $F_{max}=SF\cdot F$, or solve $\sigma_{eq}=\sigma_Y/SF$ for the unknown load or pressure.
> - **Common mistakes:** forgetting the out-of-plane shear in Tresca when both in-plane principal stresses have the same sign (a pressure vessel); inverting the safety factor, which must exceed 1 for a safe design.
> - **Practise:** [[#Worked example - shaft under axial load and torque]] · [[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]]

In the simple cases a strength check compares a single stress with an allowable value: $F/A$ in a bar, the surface shear stress in a shaft, the bending stress in a slender beam (Lecture 8, ll. 18–29). The allowable value comes from a tensile test, where the material behaves elastically up to a yield stress and then deforms plastically, leaving a permanent strain after unloading; because the start of yielding is hard to pin down, the 0.2 % offset yield strength is used in practice (Lecture 8, ll. 33–63; [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]). But a pressure vessel wall, a shaft under torque and end load, or the edge of a hole carries several stresses at once, and a rule is needed for combining them into a single quantity to compare with $\sigma_Y$.

There is no single correct answer from theory. A yield criterion is phenomenological: it proposes a combination of the stresses and is judged by how well it matches experiments, and the right choice depends on the material (Lecture 8, ll. 64–96). Ductile metals yield by slip, which is driven by shear stress, so both criteria are built from the maximum shear stresses on the principal planes. Brittle materials fail by normal stress and need different criteria, which are not covered here.

Both criteria are written in terms of principal stresses, which do not depend on how the stress element was oriented. That is essential: rotating the element on paper cannot make a component fail (Lecture 8, ll. 512–523).

---

## 1. The Tresca criterion

### The observation behind it

Ductile metals broken in tension show slip on planes at about 45° to the load; the cup-and-cone fracture of an aluminium tensile specimen has its cone at 45°. From Mohr's circle, 45° is exactly where the shear stress in uniaxial tension is largest, which suggests that shear, not the normal stress, controls yielding (Lecture 8, ll. 97–118). The **Tresca criterion** states that a material yields when the maximum shear stress on any plane reaches a critical value.

### The critical shear stress from a tensile test

In uniaxial tension the circle passes through the origin and $\sigma_{xx}$, so its radius, the maximum shear stress, is half the normal stress ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - element at 45 degrees in a bar|B4]]). At yield, $\sigma_{xx}=\sigma_Y=F_{yield}/A$, so

$$
\sigma_{x'y'}^{max}=\frac{\sigma_Y}{2}
$$

is the largest shear stress the material can carry (Lecture 8, ll. 119–136).

### Maximum shear stress in three dimensions

In a general state, the in-plane maximum shear stress is the radius of Mohr's circle, half the difference of the principal stresses. In 3D a cube can always be rotated so that it carries only normal stresses, the three principal stresses $\sigma_I$, $\sigma_{II}$ and $\sigma_{III}$ on mutually perpendicular faces, not in general aligned with $x$, $y$ and $z$ (Lecture 8, ll. 170–193). Each pair of principal stresses defines a plane with its own Mohr's circle, and the largest shear stress overall is the radius of the largest circle (Lecture 8, ll. 194–223):

$$
\sigma_{x'y'}^{max}=\frac12\max\left(|\sigma_I-\sigma_{II}|,|\sigma_I-\sigma_{III}|,|\sigma_{II}-\sigma_{III}|\right)
$$

No yield requires this to stay below $\sigma_Y/2$, which after cancelling the factor of a half is

$$
\boxed{\max\left(|\sigma_I-\sigma_{II}|,|\sigma_I-\sigma_{III}|,|\sigma_{II}-\sigma_{III}|\right)<\sigma_Y}
$$

### Plane stress and the out-of-plane shear

In plane stress the principal stress normal to the plate is $\sigma_{III}=0$, and the criterion becomes

$$
\max\left(|\sigma_I-\sigma_{II}|,|\sigma_I|,|\sigma_{II}|\right)<\sigma_Y
$$

The two extra terms matter. Seen from the side, a plate stretched along $\sigma_I$ behaves, in the plane containing $\sigma_I$ and the thickness direction, as a bar in tension, and it can slip on a plane at 45° through the thickness, where the shear stress is $\sigma_I/2$, even though there is no stress in $z$ (Lecture 8, ll. 224–249).

Which term is largest depends on the signs (Lecture 8, ll. 250–269). If $\sigma_I$ and $\sigma_{II}$ have the same sign, say $\sigma_I\ge\sigma_{II}\ge0$, then

$$
|\sigma_I-\sigma_{II}|=\sigma_I-\sigma_{II}\le\sigma_I
$$

so the governing term is the larger magnitude, $\max(|\sigma_I|,|\sigma_{II}|)$, and the governing shear acts on an out-of-plane plane. If they have opposite signs, $\sigma_I>0>\sigma_{II}$, then

$$
|\sigma_I-\sigma_{II}|=\sigma_I+|\sigma_{II}|
$$

which exceeds both $|\sigma_I|$ and $|\sigma_{II}|$, so the in-plane term governs:

$$
\text{same sign: }\max\left(|\sigma_I|,|\sigma_{II}|\right)<\sigma_Y,\qquad \text{opposite sign: }|\sigma_I-\sigma_{II}|<\sigma_Y
$$

![[s2_tresca_three_circles.png|900]]

### The Tresca hexagon

Plotted in the plane of $\sigma_I$ against $\sigma_{II}$, the same-sign conditions give a square in the first and third quadrants and the opposite-sign condition gives straight lines $\sigma_I-\sigma_{II}=\pm\sigma_Y$ joining $(\sigma_Y,0)$ to $(0,-\sigma_Y)$ and $(-\sigma_Y,0)$ to $(0,\sigma_Y)$. Together they make a hexagon: inside it the material is elastic, on it yielding begins (Lecture 8, ll. 270–314). Uniaxial tension reaches the hexagon at $\sigma_I=\sigma_Y$; equal biaxial tension at the corner $\sigma_I=\sigma_{II}=\sigma_Y$, and equal biaxial compression at the opposite corner. Pure shear, as in torsion, has $\sigma_I=-\sigma_{II}$, a circle centred on the origin with radius equal to the shear stress, and it reaches the hexagon at

$$
\sigma_I=-\sigma_{II}=\frac{\sigma_Y}{2}
$$

so Tresca predicts a shear yield stress of $0.5\sigma_Y$ (Lecture 8, ll. 315–364).

Tresca connects yielding directly to the shear stress that causes slip, but it is awkward to use, because it requires the principal stresses and a decision about which of three terms governs, and it takes no account of the shear stresses on the other principal planes, however close to the maximum they are (Lecture 8, ll. 365–380).

## 2. The von Mises criterion

### Root mean square of the maximum shear stresses

The **von Mises criterion** takes all three principal planes into account by using the root mean square of their maximum shear stresses, each the radius of a Mohr's circle (Lecture 8, ll. 381–403):

$$
\sigma_{x'y'}^{RMS}=\sqrt{\frac13\left[\left(\frac{\sigma_I-\sigma_{II}}{2}\right)^2+\left(\frac{\sigma_I-\sigma_{III}}{2}\right)^2+\left(\frac{\sigma_{II}-\sigma_{III}}{2}\right)^2\right]}
$$

It can also be associated with the strain energy of distortion, the part of the elastic energy that changes the shape rather than the volume.

### Calibrating against the tensile test

The critical value comes from the tensile test, where at yield $\sigma_I=\sigma_Y$ and $\sigma_{II}=\sigma_{III}=0$ (Lecture 8, ll. 404–418):

$$
\sigma_{x'y'}^{RMS}=\sqrt{\frac13\left[\frac{\sigma_Y^2}{4}+\frac{\sigma_Y^2}{4}+0\right]}
$$

$$
\sigma_{x'y'}^{RMS}=\sqrt{\frac{\sigma_Y^2}{6}}=\frac{\sigma_Y}{\sqrt6}
$$

Equating the general expression to this value at yield:

$$
\frac{1}{12}\left[(\sigma_I-\sigma_{II})^2+(\sigma_I-\sigma_{III})^2+(\sigma_{II}-\sigma_{III})^2\right]=\frac{\sigma_Y^2}{6}
$$

$$
(\sigma_I-\sigma_{II})^2+(\sigma_I-\sigma_{III})^2+(\sigma_{II}-\sigma_{III})^2=2\sigma_Y^2
$$

### Equivalent stress

Dividing by 2 and taking the square root defines the **von Mises equivalent stress**, a single scalar that can be compared directly with the yield stress measured in uniaxial tension (Lecture 8, ll. 419–430):

$$
\boxed{\sigma_{eq}=\sqrt{\frac12\left[(\sigma_I-\sigma_{II})^2+(\sigma_I-\sigma_{III})^2+(\sigma_{II}-\sigma_{III})^2\right]}<\sigma_Y}
$$

In uniaxial tension it reduces to $\sigma_{eq}=\sigma_I$, so the criterion agrees with the test it was calibrated on.

### Plane stress in principal stresses

With $\sigma_{III}=0$:

$$
\sigma_{eq}^2=\frac12\left[(\sigma_I-\sigma_{II})^2+\sigma_I^2+\sigma_{II}^2\right]
$$

$$
\sigma_{eq}^2=\frac12\left[2\sigma_I^2+2\sigma_{II}^2-2\sigma_I\sigma_{II}\right]
$$

$$
\boxed{\sigma_{eq}=\sqrt{\sigma_I^2+\sigma_{II}^2-\sigma_I\sigma_{II}}}
$$

### Plane stress in xy components

The form in $xy$ components is the one used most, because it needs no principal stresses (Lecture 8, ll. 431–447; Lecture 9, ll. 528–530). It follows from the principal form. With $c=\sigma_{average}=(\sigma_{xx}+\sigma_{yy})/2$ and $R$ the radius of Mohr's circle, $\sigma_I=c+R$ and $\sigma_{II}=c-R$, so

$$
\sigma_I^2+\sigma_{II}^2=2c^2+2R^2,\qquad \sigma_I\sigma_{II}=c^2-R^2
$$

$$
\sigma_{eq}^2=2c^2+2R^2-c^2+R^2=c^2+3R^2
$$

Substituting $c$ and $R$:

$$
\sigma_{eq}^2=\frac{(\sigma_{xx}+\sigma_{yy})^2}{4}+3\left[\frac{(\sigma_{xx}-\sigma_{yy})^2}{4}+\sigma_{xy}^2\right]
$$

$$
\sigma_{eq}^2=\frac{\sigma_{xx}^2+2\sigma_{xx}\sigma_{yy}+\sigma_{yy}^2+3\sigma_{xx}^2-6\sigma_{xx}\sigma_{yy}+3\sigma_{yy}^2}{4}+3\sigma_{xy}^2
$$

$$
\boxed{\sigma_{eq}=\sqrt{\sigma_{xx}^2+\sigma_{yy}^2-\sigma_{xx}\sigma_{yy}+3\sigma_{xy}^2}}
$$

### The ellipse and the comparison with Tresca

In the $\sigma_I$–$\sigma_{II}$ plane, $\sigma_I^2+\sigma_{II}^2-\sigma_I\sigma_{II}=\sigma_Y^2$ is an ellipse with its long axis along the line $\sigma_I=\sigma_{II}$. It passes through the six corners of the Tresca hexagon, so the two criteria agree for uniaxial and equal biaxial stress, and everywhere else the ellipse lies outside the hexagon: Tresca is the more conservative (Lecture 8, ll. 448–480).

![[s2_yield_loci.png|800]]

The bulge of the ellipse means that, by von Mises, $\sigma_I$ can exceed $\sigma_Y$ when $\sigma_{II}$ is tensile too. The largest $\sigma_I$ on the ellipse is where $\partial(\sigma_I^2+\sigma_{II}^2-\sigma_I\sigma_{II})/\partial\sigma_{II}=0$:

$$
2\sigma_{II}-\sigma_I=0\ \Rightarrow\ \sigma_{II}=\frac{\sigma_I}{2}
$$

$$
\sigma_I^2+\frac{\sigma_I^2}{4}-\frac{\sigma_I^2}{2}=\sigma_Y^2
$$

$$
\sigma_I=\frac{2}{\sqrt3}\sigma_Y=1.155\sigma_Y
$$

The pull across reduces the strain along $\sigma_I$ through the Poisson effect, and reduces the differences between the principal stresses, which is what drives shear (Lecture 8, ll. 462–480).

The criteria differ most in pure shear. With $\sigma_I=-\sigma_{II}=s$:

$$
s^2+s^2+s^2=\sigma_Y^2\ \Rightarrow\ s=\frac{\sigma_Y}{\sqrt3}=0.577\sigma_Y
$$

against $0.5\sigma_Y$ for Tresca (Lecture 8, ll. 481–501).

### Evidence from torsion tests

The ratio of the shear yield stress in a torsion test to the tensile yield stress decides between the criteria for a given material. For several alloys it is close to the von Mises value of 0.577 (Lecture 8, ll. 502–511):

| Material | $\tau_Y/\sigma_Y$ |
|---|---|
| Al 1100-H14 | 0.579 |
| Al 2014-T6 | 0.575 |
| Al 6061-T6 | 0.583 |
| Steel AISI 302 | 0.577 |

### Hydrostatic stress and the yield surface

With three principal stresses, the von Mises condition $\sigma_{eq}=\sigma_Y$ is a cylinder in $(\sigma_I,\sigma_{II},\sigma_{III})$ space whose axis is the line $\sigma_I=\sigma_{II}=\sigma_{III}$; its section by the plane $\sigma_{III}=0$ is the ellipse above. Points inside are elastic. Along the axis all principal stresses are equal, a hydrostatic state, and every difference in the formula is zero, so no hydrostatic stress, however large, causes yield. Only differences between principal stresses, which produce shear and distortion, do (Lecture 8, ll. 540–553). The block on the ocean floor in [[FEEG1002 B3 - Generalised Hooke's Law#Worked example - a steel block on the ocean floor|B3]] is in exactly this state.

## 3. Using the criteria

### Choosing between them

Both criteria are for ductile materials. Tresca is the more intuitive, tied directly to the maximum shear stress, and the more conservative. Von Mises is more accurate for most ductile metals and easier to use, since $\sigma_{eq}$ follows from one formula without deciding which shear governs; it is also the "von Mises stress" plotted by finite element software (Lecture 8, ll. 531–539; Lecture 9, ll. 518–527). Because both are written in principal stresses, the result is the same whatever orientation the stresses were calculated or measured in, so a rosette can be stuck on at any angle (Lecture 8, ll. 524–530).

### Limitations

Brittle materials fail by normal stress rather than shear, giving flat fracture surfaces instead of 45° shear lips, and many of them, such as cast iron and concrete, are much stronger in compression than in tension. Both assumptions behind these criteria then fail, and other criteria are needed (Lecture 8, ll. 554–559; [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]).

## 4. Failure load and safety factor

### Stresses scale with load

With linear elasticity and small deformations assumed, every stress component, and hence $\sigma_{eq}$, is proportional to the applied load. One analysis at load $F$ is enough: there is no need to repeat a simulation at higher loads to find where yield starts (Lecture 8, ll. 560–605). The load at first yield is

$$
\boxed{F_{max}=\frac{\sigma_Y}{\sigma_{eq}}F}
$$

### Safety factor

The ratio is the **safety factor**:

$$
\boxed{SF=\frac{F_{max}}{F}=\frac{\sigma_Y}{\sigma_{eq}}}
$$

It must be greater than 1, since the material yields when $\sigma_{eq}\ge\sigma_Y$; an $SF$ of 2 means the load can be doubled before yield begins (Lecture 8, ll. 606–618; Lecture 9, ll. 531–551). The value required in design depends on how well the material is known and controlled, how accurate the model, dimensions and loads are, whether failure would endanger life, and whether fatigue under cyclic loading must be considered; for many applications standards prescribe it (Lecture 8, ll. 619–632).

---

## Worked examples

### Worked example - plate with a hole

A high-strength steel plate ($\sigma_Y=500$ MPa), 150 mm wide and 10 mm thick with a 40 mm central hole, carries 150 kN. An FE analysis gives a maximum von Mises stress of 299.5 MPa at the sides of the hole. Find the safety factor and the load at first yield (Lecture 8, ll. 560–612).

$$
SF=\frac{\sigma_Y}{\sigma_{eq}}=\frac{500}{299.5}=1.67
$$

$$
F_{max}=SF\cdot F=1.67\times150=250.4\ \mathrm{kN}
$$

> [!check] Is 299.5 MPa plausible?
> The gross-section stress is $150\times10^3/(0.15\times0.01)=100$ MPa. At the edge of a hole the only stress is the tangential one, so the state there is uniaxial and $\sigma_{eq}$ equals it. For a hole in an infinitely wide plate that stress is three times the remote stress (the Kirsch solution plotted below), and the FE peak of 299.5 MPa is about three times the gross stress, so it is of the expected size.

![[s2_plate_hole_von_mises.png|700]]

### Worked example - shaft under axial load and torque

A 36 mm diameter steel shaft ($\sigma_Y=250$ MPa) carries an axial compressive load of 200 kN. Using von Mises, find the torque at which it yields (Tutorial 7).

Take $x$ round the circumference and $y$ along the shaft. On the outer surface, where the torsional shear stress is largest,

$$
\sigma_{yy}=\frac{F}{A}=\frac{-200\times10^3}{\tfrac\pi4(0.036)^2}=-196.5\ \mathrm{MPa}
$$

$$
\sigma_{xy}=\frac{TR}{J}=\frac{TR}{\tfrac\pi2R^4}=\frac{2T}{\pi R^3}
$$

and $\sigma_{xx}=0$, with no radial stress on the free surface. Von Mises in plane stress reduces to

$$
\sigma_{eq}=\sqrt{\sigma_{yy}^2+3\sigma_{xy}^2}=\sigma_Y
$$

$$
\sigma_{xy}=\sqrt{\frac{\sigma_Y^2-\sigma_{yy}^2}{3}}=\sqrt{\frac{250^2-196.5^2}{3}}=89.2\ \mathrm{MPa}
$$

$$
T=\frac{\pi R^3}{2}\sigma_{xy}=\frac{\pi(0.018)^3}{2}(89.2\times10^6)=817.5\ \mathrm{N\,m}
$$

The principal stresses then have opposite signs, so Tresca uses $|\sigma_I-\sigma_{II}|=2R=\sqrt{\sigma_{yy}^2+4\sigma_{xy}^2}=\sigma_Y$, giving $\sigma_{xy}=77.3$ MPa and $T=708$ N m, 13 % lower. Without the axial load the shaft would carry 1322 N m by von Mises; the compression uses $(196.5/250)^2=62$ % of the squared yield stress and takes 38 % off the torque capacity. Because $\sigma_{yy}$ enters squared, 200 kN of tension would give the same torque limit; in compression, buckling must also be checked ([[FEEG1002 A7 - Euler Buckling of Struts]]).

![[s2_t7_torsion_axial_envelope.png|850]]

### Worked example - hydraulic press frame

The press frame of [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Worked example - hydraulic press frame|B5]] has $\sigma_{xx}=200$, $\sigma_{yy}=115$ and $\sigma_{xy}=-18.4$ MPa under 450 MN, and $\sigma_Y=355$ MPa. What is the maximum load by von Mises? (Tutorial 8 Q1(c).)

$$
\sigma_{eq}=\sqrt{200^2+115^2-(200)(115)+3(-18.4)^2}=177\ \mathrm{MPa}
$$

$$
SF=\frac{355}{177}=2.0,\qquad F_{max}=2.0\times450=900\ \mathrm{MN}=9.0\times10^8\ \mathrm{N}
$$

The principal stresses, 204 and 111 MPa, have the same sign, so Tresca would be governed by the out-of-plane shear, $\sigma_I=204$ MPa, giving $SF=1.74$ and 783 MN.

### Worked example - liquid hydrogen tank

A liquid hydrogen tank is a thin-walled cylinder of radius 0.35 m and wall 1.5 mm, in plane stress, with $\sigma_Y=440$ MPa and a design safety factor of 3. Find the maximum allowable pressure by von Mises (Tutorial 8 Q3(i)).

With $\sigma_{xx}=pR/2t$, $\sigma_{yy}=pR/t$ and $\sigma_{xy}=0$,

$$
\sigma_{eq}=\sqrt{\frac{p^2R^2}{4t^2}+\frac{p^2R^2}{t^2}-\frac{p^2R^2}{2t^2}}=\frac{pR}{t}\sqrt{\frac34}=\frac{\sqrt3}{2}\frac{pR}{t}
$$

Setting $\sigma_{eq}=\sigma_Y/SF$:

$$
p=\frac{2\sigma_Yt}{\sqrt3\,SF\,R}=\frac{2(440\times10^6)(1.5\times10^{-3})}{\sqrt3(3)(0.35)}=7.26\times10^5\ \mathrm{Pa}=7.26\ \mathrm{bar}
$$

The wall stresses are then 84.7 and 169.4 MPa, which give the strains and the strain circle in [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Worked example - strain circle for a hydrogen tank|B5]].

> [!warning] Tresca and the vessel wall
> Both principal stresses in a vessel wall are tensile, so Tresca is governed by the shear on a plane through the thickness, $\sigma_I=pR/t$, not by the in-plane $(\sigma_I-\sigma_{II})/2$. Setting $pR/t=\sigma_Y/SF$ gives 6.29 bar. Using only the in-plane circle would give $pR/2t=\sigma_Y/SF$, twice the allowable pressure, and an unsafe design.

---

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| Tresca criterion | maximum shear stress criterion | yield when $\tau_{max}=\sigma_Y/2$ |
| Von Mises criterion | distortion energy criterion, octahedral shear stress criterion | course derivation uses the RMS of the maximum shear stresses |
| Equivalent stress $\sigma_{eq}$ | von Mises stress, effective stress | the contour usually plotted by FE software |

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]] · Next (Materials): [[FEEG1002 C1 - Atoms and Bonding]]
- Concepts: [[Tresca Yield Criterion]] · [[Von Mises Yield Criterion]] · [[Principal Stresses]] · [[Mohr's Circle]]
- Worked sheets: [[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]] (Q1(c), Q3(i)) · Formula list: [[FEEG1002 Formula Sheet]]
- Statics 1 inputs: [[FEEG1002 A8 - Torsion of Circular Shafts]] (shear stress in shafts) · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] (bending stress)
- Year 2: [[Von Mises and Tresca Yield Criteria]] and FE von Mises contours in [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]] · yield at the bore of thick cylinders in [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] · safety factors and stress concentrations in [[Stress Concentration Factor and Factor of Safety]] · fatigue, which a static safety factor does not cover, in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]

## Sources

- `Lecture 08 - Yield Criteria.pdf`: Lectures 8a–8c, Tresca, maximum shear in 3D and plane stress, hexagon and examples, von Mises, equivalent stress, ellipse, torsion evidence, 3D yield surface, brittle materials, limit analysis and safety factors.
- `FEEG1002 Lecture 8 - Statics 2 - Yield criteria - March 2025.txt` (17 Mar 2025): the problem (ll. 9–96), Tresca (ll. 97–380), von Mises (ll. 381–511), summary and 3D surface (ll. 512–559), failure load and safety factor (ll. 560–632).
- `FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt` (12 May 2025): recap (ll. 516–551), exam advice (ll. 554–632).
- `Tutorial Sheet 07 - Yield Criteria.pdf` and solutions; `Tutorial Sheet 08 - Revision Problems.pdf` and solutions: Q1(c), Q3(i).

## Self-study tasks

### Core

- [ ] Tutorial 7, shaft under axial load and torque. Target 817.5 N m. → [[#Worked example - shaft under axial load and torque]] · [[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]]
- [ ] Tutorial 8 Q1(c) and Q3(i), the revision problems set for the Easter break (Lecture 8, ll. 637–640). Targets $9.0\times10^8$ N and 7.26 bar. → [[#Worked example - hydraulic press frame]] · [[#Worked example - liquid hydrogen tank]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]
- [ ] Rework the plate-with-a-hole limit analysis (Lecture 8, ll. 560–612). Targets 1.67 and 250.4 kN. → [[#Worked example - plate with a hole]]
- [ ] Derive the plane-stress von Mises formula in $xy$ components from the principal form. → [[#Plane stress in xy components]]

### Further practice

- [ ] Show which Tresca term governs for same-sign and opposite-sign principal stresses (Lecture 8, ll. 250–269). → [[#Plane stress and the out-of-plane shear]]
- [ ] Find the pure-shear yield stress by each criterion and the largest $\sigma_I$ on the von Mises ellipse (Lecture 8, ll. 481–501). → [[#The ellipse and the comparison with Tresca]]
- [ ] Set yourself a time limit on a full revision problem from sheet 8, as advised at Lecture 9, ll. 619–628. → [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 8, ll. 286 and 466)
> Where: [[#The Tresca hexagon]] · [[#The ellipse and the comparison with Tresca]].
>
> In the first quadrant "both the first and the principal stress are both positive" means the first and second principal stresses. Explaining why von Mises allows $\sigma_I>\sigma_Y$, "if we don't start applying stress in the second principal direction" should read "if we start applying stress in the second principal direction": it is a tensile $\sigma_{II}$ that lets $\sigma_I$ exceed $\sigma_Y$, as the slide states ($\sigma_I$ can exceed $\sigma_Y$ if $\sigma_{II}>0$).

> [!warning] Transcript slip (Lecture 9, l. 547)
> Where: [[#Safety factor]].
>
> "Safety factor is always larger than 2" should be "larger than 1"; the same passage (ll. 536–541) uses $SF=2$ as an example, and the slide states $SF>1$.
