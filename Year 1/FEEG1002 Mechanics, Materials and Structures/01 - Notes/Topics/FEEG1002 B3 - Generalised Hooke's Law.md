---
title: "FEEG1002 B3 - Generalised Hooke's Law"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 12
tags: [feeg1002, statics-2, hookes-law, plane-stress, plane-strain, bulk-modulus, poissons-ratio]
aliases: ["Statics 2 Lecture 4", "Generalised Hooke's law", "Plane stress", "Plane strain", "Bulk modulus"]
date: 2026-11-05
status: lectured
coverage: "Statics 2 Lecture 4 (17 Feb 2025, ll. 1–653): uniaxial recap, assumptions, plane-stress Hooke's law and its inverse, shear strain, 3D Hooke's law and its inverse, volumetric strain, hydrostatic stress and bulk modulus, incompressibility and the range of Poisson's ratio, plane strain; recap in Lecture 9 (12 May 2025, ll. 222–296)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]", "[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
next_topics: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
key_concepts: ["[[Generalised Hooke's Law]]", "[[Plane Stress and Plane Strain]]", "[[Thin-Walled Pressure Vessels]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]]", "[[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 04 - Generalised Hooke's Law.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 4 - Statics 2 - Generalised Hooke's law - February 2025.txt", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 03 - Generalised Hooke's Law.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems.pdf"]
---

# FEEG1002 B3 - Generalised Hooke's Law

> [!abstract] Summary
> In a homogeneous, isotropic, linear elastic solid, each normal stress stretches the material in its own direction and, through Poisson's ratio, contracts it in the other two; superposing the three effects gives $\varepsilon_{xx}=\frac1E[\sigma_{xx}-\nu(\sigma_{yy}+\sigma_{zz})]$ and its two companions, while each shear strain depends only on its own shear stress, $\varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy}$. Only two constants are independent, $E$ and $\nu$; the shear modulus $G=E/2(1+\nu)$ and bulk modulus $K=E/3(1-2\nu)$ follow from them. Two reduced forms are used constantly: plane stress, where $\sigma_{zz}=0$ but the plate thins, and plane strain, where $\varepsilon_{zz}=0$ but a stress $\sigma_{zz}=\nu(\sigma_{xx}+\sigma_{yy})$ is needed to hold it.

> [!summary]- Exam use: quick path
> - **Use it when:** stresses act in more than one direction and you need strains or changes of dimension (vessels, plates, hulls), or strains have been measured and you need stresses (gauges, rosettes), or an expansion is restrained in two directions at once.
> - **Assumptions:** homogeneous, isotropic, linear elastic; small strains; plane stress for thin plates, thin-walled vessels and free surfaces; plane strain for long bodies whose length cannot change.
> - **Method:** 1. Decide which components are zero (plane stress: $\sigma_{zz}=\sigma_{xz}=\sigma_{yz}=0$; plane strain: $\varepsilon_{zz}=\varepsilon_{xz}=\varepsilon_{yz}=0$). 2. Write the strain equations as direct strain minus Poisson terms. 3. If stresses are wanted from strains, use the inverse form ($E/(1-\nu^2)$ in plane stress). 4. Add $\alpha\Delta T$ to each normal strain if the temperature changes. 5. Convert strains to changes of length, diameter or thickness.
> - **Common mistakes:** using $\sigma=E\varepsilon$ in one direction and forgetting the Poisson terms; assuming $\varepsilon_{zz}=0$ in plane stress (the plate thins) or $\sigma_{zz}=0$ in plane strain.
> - **Practise:** [[#Worked example - submersible hull at 100 m]] · [[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]]

The familiar Hooke's law, $\sigma=E\varepsilon$, is a one-stress law. It is what a tensile test measures, just as $\tau=G\gamma$ is what a torsion test measures, so each characterises a material. But a pressure vessel wall is stretched round its circumference and along its length at once, and the two stretches interact: pulling in one direction makes the material contract in the others. A strain in one direction therefore depends on the stresses in all directions, and the one-stress law no longer holds on its own.

The generalised law is the uniaxial law and Poisson's ratio applied once for each stress, with the results added. Superposition is allowed because the material is linear. The result needs no new material constants: for an isotropic material, $E$ and $\nu$ describe everything, including shear and volume change.

The full 3D law is rarely used in its entirety. Most problems are two-dimensional, and the two common simplifications, plane stress and plane strain, differ in which of $\sigma_{zz}$ and $\varepsilon_{zz}$ is zero. Getting that choice right, and remembering that the other one is then not zero, is most of the skill.

---

## 1. Assumptions

Stress–strain relations are empirical: they come from experiments on the material. The material is assumed **homogeneous**, the same throughout the body; **isotropic**, the same in every direction; and **linear elastic**, obeying Hooke's law in each direction. Metals satisfy all three well. Wood, muscle and fibre composites are not isotropic: they are stiffer along their fibres than across them, and need more constants ([[SESA2028 M4 - Polymer Matrix Composites]]). Rubber is not linear at large strains.

## 2. Plane stress

### What plane stress means

**Plane stress** means that all stresses involving the $z$ direction are zero:

$$
\sigma_{zz}=\sigma_{xz}=\sigma_{yz}=0
$$

so only $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$ remain. It describes thin plates loaded in their own plane, such as the skin of an aircraft or a ship, and thin-walled pressure vessels, where the radial stress is of order $p$ and is neglected ([[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#The radial stress|B1]]). It also holds at any free surface.

![[s2_plane_stress_strain.png|900]]

### The effect of each normal stress

Apply $\sigma_{xx}$ alone. The element is in uniaxial tension, so the familiar law gives the strain along $x$, and Poisson's ratio gives the contraction across it:

$$
\varepsilon_{xx}=\frac{\sigma_{xx}}{E},\qquad \varepsilon_{yy}=-\nu\varepsilon_{xx}=-\nu\frac{\sigma_{xx}}{E}
$$

The material behaves the same in every direction, so $\sigma_{yy}$ alone gives

$$
\varepsilon_{yy}=\frac{\sigma_{yy}}{E},\qquad \varepsilon_{xx}=-\nu\frac{\sigma_{yy}}{E}
$$

The stress in $y$ therefore changes the strain in $x$.

### Superposition

Because the material is linear, the strains from the two stresses add:

$$
\varepsilon_{xx}=\frac{\sigma_{xx}}{E}-\nu\frac{\sigma_{yy}}{E}
$$

$$
\boxed{\varepsilon_{xx}=\frac1E\left(\sigma_{xx}-\nu\sigma_{yy}\right)},\qquad \boxed{\varepsilon_{yy}=\frac1E\left(\sigma_{yy}-\nu\sigma_{xx}\right)}
$$

Each normal strain is a direct term from the stress in its own direction minus a Poisson term from the stress across it. Pulling in $y$ reduces the strain in $x$.

### The out-of-plane strain

There is no stress in $z$, but both in-plane stresses make the plate contract through its thickness, so the strain in $z$ is two Poisson terms and no direct term:

$$
\boxed{\varepsilon_{zz}=-\frac{\nu}{E}\left(\sigma_{xx}+\sigma_{yy}\right)}
$$

In plane stress $\sigma_{zz}=0$ but in general $\varepsilon_{zz}\neq0$: a stretched plate gets thinner.

### Shear strain

The shear strain is related to the shear stress exactly as in torsion, $\gamma_{xy}=\sigma_{xy}/G$, where $\gamma_{xy}$ is the decrease of the right angle between the $x$ and $y$ faces ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#The engineering shear strain|B2]]). The shear modulus is not an independent constant:

$$
G=\frac{E}{2(1+\nu)}
$$

Writing the shear strain in tensor form, $\varepsilon_{xy}=\gamma_{xy}/2$:

$$
\varepsilon_{xy}=\frac{\gamma_{xy}}{2}=\frac{\sigma_{xy}}{2G}
$$

$$
\varepsilon_{xy}=\frac{2(1+\nu)}{2E}\sigma_{xy}
$$

$$
\boxed{\varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy}}
$$

Normal stresses cause no shear strain, and shear stress causes no normal strain in the $x$, $y$ or $z$ directions: a shear stress only changes angles. This decoupling is a property of isotropic materials.

### Why G is not independent

The relation $G=E/2(1+\nu)$ can be proved once stress and strain transformation are available ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]], [[FEEG1002 B5 - Strain Measurement and Strain Rosettes|B5]]). Take an element in pure shear, $\sigma_{xy}=\tau$ with no normal stresses. Its Mohr's circle is centred on the origin, so at 45° the element carries principal stresses $\sigma_I=\tau$ and $\sigma_{II}=-\tau$ with no shear. In those axes the plane-stress law gives the principal strain

$$
\varepsilon_I=\frac1E\left(\sigma_I-\nu\sigma_{II}\right)
$$

$$
\varepsilon_I=\frac1E\left(\tau+\nu\tau\right)=\frac{(1+\nu)\tau}{E}
$$

The strain state is pure shear too, $\varepsilon_{xx}=\varepsilon_{yy}=0$, so its Mohr's circle is also centred on the origin with radius $\varepsilon_{xy}$, and the principal strain at 45° is $\varepsilon_I=\varepsilon_{xy}=\gamma_{xy}/2$. Equating the two:

$$
\frac{\gamma_{xy}}{2}=\frac{(1+\nu)\tau}{E}
$$

$$
G=\frac{\tau}{\gamma_{xy}}=\frac{E}{2(1+\nu)}
$$

For steel with $E=210$ GPa and $\nu=0.3$ this gives $G=80.8$ GPa.

### Stresses from strains

Strain gauges measure strains, so the law is often needed the other way round. Multiply the $\varepsilon_{yy}$ equation by $\nu$ and add it to the $\varepsilon_{xx}$ equation:

$$
\varepsilon_{xx}+\nu\varepsilon_{yy}=\frac1E\left(\sigma_{xx}-\nu\sigma_{yy}+\nu\sigma_{yy}-\nu^2\sigma_{xx}\right)
$$

$$
\varepsilon_{xx}+\nu\varepsilon_{yy}=\frac{1-\nu^2}{E}\sigma_{xx}
$$

$$
\boxed{\sigma_{xx}=\frac{E}{1-\nu^2}\left(\varepsilon_{xx}+\nu\varepsilon_{yy}\right)}
$$

and by symmetry

$$
\boxed{\sigma_{yy}=\frac{E}{1-\nu^2}\left(\varepsilon_{yy}+\nu\varepsilon_{xx}\right)},\qquad \boxed{\sigma_{xy}=\frac{E}{1+\nu}\varepsilon_{xy}}
$$

This form is less intuitive than the strain form, and there is no need to memorise it; know where to find it.

## 3. Hooke's law in three dimensions

### Strains from stresses

With a stress in $z$ as well, each normal strain picks up one more Poisson term:

$$
\boxed{\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu(\sigma_{yy}+\sigma_{zz})\right]}
$$

$$
\boxed{\varepsilon_{yy}=\frac1E\left[\sigma_{yy}-\nu(\sigma_{xx}+\sigma_{zz})\right]}
$$

$$
\boxed{\varepsilon_{zz}=\frac1E\left[\sigma_{zz}-\nu(\sigma_{xx}+\sigma_{yy})\right]}
$$

and each shear strain depends only on its own shear stress:

$$
\varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy},\qquad \varepsilon_{xz}=\frac{1+\nu}{E}\sigma_{xz},\qquad \varepsilon_{yz}=\frac{1+\nu}{E}\sigma_{yz}
$$

Setting $\sigma_{zz}=0$ recovers the plane-stress equations.

### Stresses from strains in three dimensions

The inverse follows in a few lines. Write $S=\sigma_{xx}+\sigma_{yy}+\sigma_{zz}$. The first strain equation can be rearranged as

$$
E\varepsilon_{xx}=\sigma_{xx}-\nu(S-\sigma_{xx})
$$

$$
E\varepsilon_{xx}=(1+\nu)\sigma_{xx}-\nu S
$$

Adding the three strain equations gives the volumetric strain, derived in [[#Volumetric strain in terms of stress]]:

$$
\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}=\frac{1-2\nu}{E}S
$$

$$
S=\frac{E}{1-2\nu}\left(\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}\right)
$$

Substitute for $S$:

$$
(1+\nu)\sigma_{xx}=E\varepsilon_{xx}+\frac{\nu E}{1-2\nu}\left(\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}\right)
$$

$$
\sigma_{xx}=\frac{E}{(1+\nu)(1-2\nu)}\left[(1-2\nu)\varepsilon_{xx}+\nu\left(\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}\right)\right]
$$

$$
\boxed{\sigma_{xx}=\frac{E}{(1+\nu)(1-2\nu)}\left[(1-\nu)\varepsilon_{xx}+\nu\left(\varepsilon_{yy}+\varepsilon_{zz}\right)\right]}
$$

with $\sigma_{yy}$ and $\sigma_{zz}$ following by cycling the indices, and $\sigma_{xy}=\frac{E}{1+\nu}\varepsilon_{xy}$ and likewise for the other shear stresses. The factor $(1-2\nu)$ in the denominator blows up as $\nu\to0.5$, a first sign of incompressibility.

> [!tip] Simplify before you solve
> A 3D question almost always tells you something is zero: a stress on a free surface, a strain where a wall prevents movement. Put those zeros in first; the system then collapses to one or two equations.

## 4. Volume change and the bulk modulus

### Volumetric strain in terms of stress

For small strains the volumetric strain is the sum of the normal strains ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Volumetric strain|B2]]). Adding the three 3D equations, each stress appears once with coefficient $1/E$ and twice with $-\nu/E$:

$$
\varepsilon_{vol}=\frac1E\left[\sigma_{xx}+\sigma_{yy}+\sigma_{zz}-2\nu(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})\right]
$$

$$
\boxed{\varepsilon_{vol}=\frac{1-2\nu}{E}\left(\sigma_{xx}+\sigma_{yy}+\sigma_{zz}\right)}
$$

Shear stresses do not appear: they change shape, not volume.

### Hydrostatic stress and the bulk modulus

When all three normal stresses are equal, $\sigma_{xx}=\sigma_{yy}=\sigma_{zz}=\sigma_H$, the state is **hydrostatic**: a solid block sunk in deep water is squeezed equally from every side. Then

$$
\varepsilon_{vol}=\frac{3(1-2\nu)}{E}\sigma_H
$$

$$
\boxed{\varepsilon_{vol}=\frac{\sigma_H}{K},\qquad K=\frac{E}{3(1-2\nu)}}
$$

where $K$ is the **bulk modulus**, the resistance of the bulk material to change of volume. It applies to a solid block, not to a hollow structure: a submarine hull is a thin-walled pressure vessel and deforms by the stresses of [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels|B1]], not by bulk compression.

### Incompressibility and the range of Poisson's ratio

If $\nu=0.5$, then $1-2\nu=0$ and the volume never changes, whatever the stresses; the material is **incompressible**. Rubber ($\nu\approx0.499$) and water-rich biological tissue come close. The admissible range follows from requiring both moduli to be positive:

$$
G=\frac{E}{2(1+\nu)}>0\ \Rightarrow\ \nu>-1,\qquad K=\frac{E}{3(1-2\nu)}>0\ \Rightarrow\ \nu<0.5
$$

so $-1<\nu<0.5$. Ordinary engineering materials sit near 0.3; negative values occur only in specially designed (for example 3D-printed re-entrant) structures, which widen when stretched.

| Material | $E$ | $\nu$ |
|---|---|---|
| Steel | 210 GPa | 0.30 |
| Aluminium | 70 GPa | 0.34 |
| Copper | 130 GPa | 0.33 |
| Titanium | 105 GPa | 0.34 |
| Low-density polymer foam | 30 kPa | 0.35 |
| Natural rubber | 20 MPa | 0.499 (not linear at large strain) |

![[s2_elastic_constants.png|800]]

## 5. Plane strain

### What plane strain means

**Plane strain** is the opposite simplification: all strains involving $z$ are zero,

$$
\varepsilon_{zz}=\varepsilon_{xz}=\varepsilon_{yz}=0
$$

so a cube of material can stretch and shear in the $x$–$y$ plane but cannot get thicker or thinner. It suits long structures loaded uniformly along their length and prevented from changing length: a dam fixed along a valley, a tunnel through rock that cannot lengthen the mountain around it.

### The out-of-plane stress

Setting $\varepsilon_{zz}=0$ in the 3D law:

$$
0=\frac1E\left[\sigma_{zz}-\nu(\sigma_{xx}+\sigma_{yy})\right]
$$

$$
\boxed{\sigma_{zz}=\nu\left(\sigma_{xx}+\sigma_{yy}\right)}
$$

Holding the strain at zero needs a stress: squeeze a cylinder between two walls and it tries to lengthen, so the walls must push back.

### In-plane relations

Substituting $\sigma_{zz}$ into the $\varepsilon_{xx}$ equation:

$$
\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu\sigma_{yy}-\nu^2(\sigma_{xx}+\sigma_{yy})\right]
$$

$$
\varepsilon_{xx}=\frac1E\left[(1-\nu^2)\sigma_{xx}-\nu(1+\nu)\sigma_{yy}\right]
$$

$$
\boxed{\varepsilon_{xx}=\frac{1+\nu}{E}\left[(1-\nu)\sigma_{xx}-\nu\sigma_{yy}\right]}
$$

and likewise for $\varepsilon_{yy}$. The shear relation is unchanged.

### Plane stress against plane strain

The two cases are mirror images, and confusing them is the commonest error in this topic:

| | Plane stress | Plane strain |
|---|---|---|
| Zero in $z$ | $\sigma_{zz}=\sigma_{xz}=\sigma_{yz}=0$ | $\varepsilon_{zz}=\varepsilon_{xz}=\varepsilon_{yz}=0$ |
| Not zero in $z$ | $\varepsilon_{zz}=-\frac\nu E(\sigma_{xx}+\sigma_{yy})$ | $\sigma_{zz}=\nu(\sigma_{xx}+\sigma_{yy})$ |
| Typical case | thin plate, vessel wall, free surface | long dam, tunnel, block between walls |

Both are described by the same two constants, $E$ and $\nu$; the rest of the generalised law is just a systematic way of combining them.

## 6. Adding a thermal strain

A temperature change adds the isotropic thermal strain of [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Free thermal expansion|B2]] to each normal strain and nothing to the shear strains:

$$
\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu(\sigma_{yy}+\sigma_{zz})\right]+\alpha\,\Delta T
$$

The total strain is mechanical plus thermal; the stresses respond only to the mechanical part. Tutorial 8 Q2 uses this for a plate restrained in both in-plane directions.

---

## Worked examples

### Worked example - submersible hull at 100 m

A tourist submersible has an acrylic hull 15 m long, 2.2 m in diameter and 140 mm thick ($E=3.2$ GPa, $\nu=0.37$). Treat it as a thin-walled cylinder in plane stress and find the wall stresses and the changes in length and diameter at 100 m depth (Tutorial 3 Q1).

Inside and outside both start at atmospheric pressure, so the net internal pressure at depth is

$$
p=-\rho gh=-(1000)(9.81)(100)=-9.81\times10^5\ \mathrm{Pa}
$$

With $x$ along the axis and $y$ round the hull, $R=1.1$ m:

$$
\sigma_{xx}=\frac{pR}{2t}=\frac{(-9.81\times10^5)(1.1)}{2(0.14)}=-3.85\ \mathrm{MPa},\qquad \sigma_{yy}=\frac{pR}{t}=-7.71\ \mathrm{MPa}
$$

Plane-stress Hooke's law:

$$
\varepsilon_{xx}=\frac{1}{3.2\times10^9}\left[-3.85\times10^6-0.37(-7.71\times10^6)\right]=-313\ \mu\varepsilon
$$

$$
\varepsilon_{yy}=\frac{1}{3.2\times10^9}\left[-7.71\times10^6-0.37(-3.85\times10^6)\right]=-1963\ \mu\varepsilon
$$

The hoop strain is also the diameter strain, since circumference and diameter are proportional, $\Delta(\pi D)/\pi D=\Delta D/D$. So

$$
\Delta L=\varepsilon_{xx}L=-4.7\ \mathrm{mm},\qquad \Delta D=\varepsilon_{yy}D=-4.3\ \mathrm{mm}
$$

Without the Poisson term the axial strain would be $-1204\ \mu\varepsilon$, nearly four times too large: the hoop compression makes the hull try to lengthen. The thickness strain is $\varepsilon_{zz}=-\frac{\nu}{E}(\sigma_{xx}+\sigma_{yy})=+1337\ \mu\varepsilon$, so the wall gets 0.19 mm thicker.

> [!warning] The thin-wall model is not valid here
> $t/R=0.14/1.1=0.127>0.1$, so the results are only approximate, and a thick-cylinder (Lamé) analysis would be needed ([[Lame Thick-Cylinder Solution]]). A genuinely thin acrylic wall under external pressure would also be prone to buckling (Tutorial 3 Q1(iii)).

### Worked example - painted spherical vessel

A steel sphere (diameter 480 mm, wall 8 mm, $E=205$ GPa, $\nu=0.30$) is coated with a brittle paint that cracks at a strain of $150\ \mu\varepsilon$. At what pressure does the paint crack? (Tutorial 3, additional Q1.)

The wall is in equibiaxial plane stress, $\sigma_{xx}=\sigma_{yy}=pR/2t$, so

$$
\varepsilon_{xx}=\frac1E\left(\sigma_{xx}-\nu\sigma_{yy}\right)=\frac{pR}{2tE}(1-\nu)
$$

$$
p=\frac{2Et\,\varepsilon}{R(1-\nu)}=\frac{2(205\times10^9)(0.008)(150\times10^{-6})}{(0.24)(0.7)}=2.93\ \mathrm{MPa}
$$

The $(1-\nu)$ shows the benefit of biaxial stress: each direction's Poisson contraction partly cancels the other's stretch, so the strain is 30 % less than uniaxial tension at the same stress would give.

### Worked example - chip held by solder joints

A square microchip, 15 mm on each side and 2 mm thick ($E=140$ GPa, $\nu=0.265$, $\alpha=2.59\times10^{-6}$ K⁻¹), is soldered to a rigid board by 12 joints on each side and heated by 30 °C. What force must each joint carry to stop the chip expanding? (Tutorial 8 Q2.)

The free thermal strain is $\varepsilon_T=\alpha\Delta T=7.77\times10^{-5}$. The board stops all in-plane expansion, so the total in-plane strains are zero and the mechanical strains are

$$
\varepsilon_{xx}=\varepsilon_{yy}=-\varepsilon_T
$$

The chip is thin and its faces are free, so it is in plane stress. From the inverse law,

$$
\sigma_{xx}=\frac{E}{1-\nu^2}\left(\varepsilon_{xx}+\nu\varepsilon_{yy}\right)=-\frac{E\varepsilon_T(1+\nu)}{1-\nu^2}
$$

$$
\sigma_{xx}=-\frac{E\varepsilon_T}{1-\nu}=-\frac{(140\times10^9)(7.77\times10^{-5})}{0.735}=-14.8\ \mathrm{MPa}
$$

The force on one side of the chip is the stress times the side's cross-section, and the joints share it:

$$
F_{side}=|\sigma_{xx}|dt=(14.8\times10^6)(0.015)(0.002)=444\ \mathrm{N},\qquad F_{joint}=\frac{444}{12}=37\ \mathrm{N}
$$

Restraint in two directions gives $E\varepsilon_T/(1-\nu)$, about 36 % more than the $E\varepsilon_T=10.9$ MPa of a bar restrained in one direction, because the compression in each direction also expands the material sideways (Poisson), which the restraint in the other direction must cancel as well.

### Worked example - a steel block on the ocean floor

A solid steel block ($E=210$ GPa, $\nu=0.30$) rests at 11 km depth in sea water of density 1025 kg/m³ (suggested, not lecturer-set). The stress is hydrostatic:

$$
\sigma_H=-\rho gh=-(1025)(9.81)(11\,000)=-110.6\ \mathrm{MPa}
$$

$$
K=\frac{E}{3(1-2\nu)}=\frac{210\times10^9}{3(0.4)}=175\ \mathrm{GPa}
$$

$$
\varepsilon_{vol}=\frac{\sigma_H}{K}=-6.32\times10^{-4}
$$

The block loses 0.063 % of its volume, a linear strain of $-211\ \mu\varepsilon$ in each direction, and since all three principal stresses are equal it carries no shear on any plane and cannot yield ([[FEEG1002 B6 - Yield Criteria|B6]]).

### Worked example - plane stress against plane strain

A steel element ($E=210$ GPa, $\nu=0.3$) carries $\sigma_{xx}=-100$ MPa with $\sigma_{yy}=0$ (suggested, not lecturer-set). As a thin plate in plane stress,

$$
\varepsilon_{xx}=\frac{\sigma_{xx}}{E}=-476\ \mu\varepsilon,\qquad \varepsilon_{zz}=-\frac{\nu}{E}\sigma_{xx}=+143\ \mu\varepsilon
$$

As a block held between walls normal to $z$ (plane strain),

$$
\sigma_{zz}=\nu\sigma_{xx}=-30\ \mathrm{MPa}
$$

$$
\varepsilon_{xx}=\frac{1+\nu}{E}(1-\nu)\sigma_{xx}=\frac{(1.3)(0.7)(-100\times10^6)}{210\times10^9}=-433\ \mu\varepsilon
$$

The walls stiffen the block in $x$ by the factor $1/(1-\nu^2)=1.10$, because the material can no longer escape sideways in $z$.

---

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| Generalised Hooke's law | 3D Hooke's law, isotropic constitutive law | The $\mathbf D$ matrix of a finite element is the inverse form |
| $\varepsilon_{xy}$ | tensor shear strain | half of the engineering shear strain $\gamma_{xy}$ |
| Hydrostatic stress $\sigma_H$ | mean stress, (negative) pressure | $\sigma_H=\tfrac13(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})$ in general |

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]] · Next: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]
- Concepts: [[Generalised Hooke's Law]] · [[Plane Stress and Plane Strain]] · [[Thin-Walled Pressure Vessels]] · [[Stress, Strain and Young's Modulus]]
- Worked sheets: [[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]] (Q1(b), Q2, Q3(ii)) · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes|B5]] (stresses from rosette strains) · [[FEEG1002 B6 - Yield Criteria|B6]]
- Year 2: the same law in $(r,\theta,z)$ for thick cylinders and discs, with plane stress or plane strain chosen by geometry ([[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]], [[Lame Equations]]) · element material matrices in [[SESA2029 B6 - 2D and 3D Elements]]

## Sources

- `Lecture 04 - Generalised Hooke's Law.pdf`: Lectures 4a–4b, plane stress, plane-stress summary and inverse, 3D law and inverse, volume change, material table, plane strain.
- `FEEG1002 Lecture 4 - Statics 2 - Generalised Hooke's law - February 2025.txt` (17 Feb 2025): uniaxial recap (ll. 6–70), 3D components (ll. 71–98), assumptions (ll. 99–141), plane stress (ll. 142–418), 3D law (ll. 419–494), volume change, bulk modulus and incompressibility (ll. 495–590), plane strain (ll. 591–646).
- `FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt` (12 May 2025): recap (ll. 222–296).
- `Tutorial Sheet 03 - Generalised Hooke's Law.pdf` and solutions: Q1 and additional Q1. `Tutorial Sheet 08 - Revision Problems.pdf` and solutions: Q2.

## Self-study tasks

### Core

- [ ] Tutorial 3 Q1, submersible hull (tutorial problems set at Lecture 4, ll. 651–652). Targets −3.85 and −7.71 MPa, −4.7 mm and −4.3 mm. → [[#Worked example - submersible hull at 100 m]] · [[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]]
- [ ] Tutorial 3 additional Q1, painted sphere. Target 2.93 MPa. → [[#Worked example - painted spherical vessel]]
- [ ] Tutorial 8 Q2, chip and solder joints. Target 37 N per joint. → [[#Worked example - chip held by solder joints]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]
- [ ] Invert the plane-stress law to get $\sigma_{xx}=\frac{E}{1-\nu^2}(\varepsilon_{xx}+\nu\varepsilon_{yy})$ (Lecture 4, ll. 398–413). → [[#Stresses from strains]]

### Further practice

- [ ] Prove $G=E/2(1+\nu)$ from pure shear (deferred at Lecture 4, ll. 342–347; needs B4 and B5). → [[#Why G is not independent]]
- [ ] Derive the 3D inverse law (results given without derivation at Lecture 4, ll. 469–478). → [[#Stresses from strains in three dimensions]]
- [ ] Derive $\sigma_{zz}=\nu(\sigma_{xx}+\sigma_{yy})$ and the in-plane plane-strain law, then compare with plane stress (Lecture 4, ll. 612–646). → [[#Worked example - plane stress against plane strain]]

## Transcript and slide slips

> [!warning] Transcript slip (Lecture 4, l. 85)
> Where: [[#1. Assumptions]] (the 3D components listed just before it).
>
> In listing the six stress components, $\sigma_{yz}$ is called "the shear strain that acts here". It is the shear stress; the six strain components are introduced separately at ll. 89–93.
