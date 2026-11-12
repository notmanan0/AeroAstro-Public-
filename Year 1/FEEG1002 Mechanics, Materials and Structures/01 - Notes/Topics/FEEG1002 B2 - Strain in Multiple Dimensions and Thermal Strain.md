---
title: "FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 11
tags: [feeg1002, statics-2, strain, shear-strain, volumetric-strain, thermal-strain, superposition]
aliases: ["Statics 2 Lecture 2", "Statics 2 Lecture 3", "Strain components", "Thermal stress"]
date: 2026-11-05
status: lectured
coverage: "Statics 2 Lecture 2 (3 Feb 2025, ll. 1–578): normal strains in 3D, volumetric strain, strain as a displacement gradient, engineering and tensor shear strain, rigid-body motion; Lecture 3 (10 Feb 2025, ll. 1–662): thermal strain, constrained bars, the rail example, series and parallel compound bars; recap in Lecture 9 (12 May 2025, ll. 108–221)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 B3 - Generalised Hooke's Law]]"]
key_concepts: ["[[Strain Components and Volumetric Strain]]", "[[Thermal Strain]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 02 - Strain in Multiple Dimensions.pdf", "02 - Sources/Statics 2/Lectures/Lecture 03 - Thermal Strains.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2 - Statics 2 - Strains in multiple dimesnions - February 2025.txt", "02 - Sources/Lectures/FEEG1002 Lecture 3 - Statics 2 - Thewrmal Strains - February 2025.txt", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 02 - Strain in Multiple Directions and Thermal Strain.pdf"]
---

# FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain

> [!abstract] Summary
> Strain measures deformation, the movement of points in a solid relative to one another, so it is built from displacement gradients and is zero for rigid-body translation and rotation. In 3D there are three normal strains, $\varepsilon_{xx}=du_x/dx$ and so on, and three shear strains; the engineering shear strain $\gamma_{xy}=du_x/dy+du_y/dx$ is the loss of a right angle and the tensor shear strain is $\varepsilon_{xy}=\gamma_{xy}/2$. For small strains the volume change is $\varepsilon_{vol}=\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}$. A temperature change adds an isotropic thermal strain $\alpha\Delta T$, which causes no stress unless the expansion is prevented; constrained problems are solved by superposing free thermal expansion and a mechanical correction.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives displacements and asks for strains or a volume change, or a bar or assembly is heated or cooled while held between walls, bonded to another material or allowed a limited gap.
> - **Assumptions:** small displacements and strains; uniform temperature (no thermal gradients); linear elastic bars loaded axially, $\delta_F=FL/EA$; lateral expansion ignored in 1D bar problems.
> - **Method:** 1. Release one constraint and let every part expand freely, $\delta_T=\alpha\Delta TL$. 2. Apply unknown forces, taken as tensile, giving $\delta_F=FL/EA$. 3. Write the compatibility condition on the total deformations (sum zero between walls, equal when bonded side by side, equal to the gap). 4. Write the force condition (equal force in series, forces summing to zero in parallel). 5. Solve for $F$, then stresses, strains and displacements.
> - **Common mistakes:** guessing the direction of the forces instead of taking both tensile and letting the sign come out; using $\gamma_{xy}$ where the tensor strain $\varepsilon_{xy}=\gamma_{xy}/2$ is required (Mohr's circle and the transformation equations).
> - **Practise:** [[#Worked example - steel rail with a 3 mm gap]] · [[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]]

When a lump of modelling clay is squeezed, two points inside it move relative to each other: the line joining them stretches or shortens, and it also turns. Strain measures this stretching of lines and the change of angle between them. Moving the whole lump without changing its shape produces no strain at all, so strain is not about displacement but about differences in displacement from one point to the next (Lecture 2, ll. 20–41).

Strain has a practical advantage over stress: it can be observed. Stresses are invisible, but displacements can be measured, and from the displacements the strains follow. The difficulty is that in metals the strains are tiny, a few thousandths at most before yield, which is why strain gauges are needed to measure them ([[FEEG1002 B5 - Strain Measurement and Strain Rosettes|B5]]). Displacements and strains are assumed small throughout, which simplifies the algebra repeatedly (Lecture 2, ll. 42–48).

Temperature gives a second source of strain. Heat a body uniformly and it grows by the same proportion in every direction, like a photographic enlargement, without any stress. Stress appears only when something stops the growth: two pin supports on a beam, a rail butting against the next rail, two bonded materials that want to expand by different amounts. Bridges carry expansion joints and process pipework has U-bends for this reason (Lecture 3, ll. 14–69).

---

## 1. Normal strains

### A bar in tension

A bar of length $L_0$ and width $w_0$ under a tensile force becomes longer and thinner. The **engineering strain** along the bar is the elongation over the original length, and the strain across it is defined in the same way from the change of width:

$$
\varepsilon=\frac{\Delta L}{L_0}>0,\qquad \varepsilon_w=\frac{\Delta w}{w_0}<0
$$

Lengthening is positive and shortening negative. The lateral strain is negative here because of the Poisson effect (Lecture 2, ll. 49–73).

### Normal strains in three directions

For a block of material with sides $L_{x0}$, $L_{y0}$, $L_{z0}$, the three **normal strains** are

$$
\varepsilon_{xx}=\frac{\Delta L_x}{L_{x0}},\qquad \varepsilon_{yy}=\frac{\Delta L_y}{L_{y0}},\qquad \varepsilon_{zz}=\frac{\Delta L_z}{L_{z0}}
$$

The double index says that the elongation and the reference length are both in the same direction, mirroring $\sigma_{xx}$ for stress (Lecture 2, ll. 74–102).

### Volumetric strain

The **volumetric strain** is the relative change of volume. The original and deformed volumes are

$$
V_0=L_{x0}L_{y0}L_{z0}
$$

$$
V=(L_{x0}+\Delta L_x)(L_{y0}+\Delta L_y)(L_{z0}+\Delta L_z)
$$

$$
V=L_{x0}L_{y0}L_{z0}(1+\varepsilon_{xx})(1+\varepsilon_{yy})(1+\varepsilon_{zz})
$$

so

$$
\varepsilon_{vol}=\frac{V-V_0}{V_0}
$$

$$
\varepsilon_{vol}=(1+\varepsilon_{xx})(1+\varepsilon_{yy})(1+\varepsilon_{zz})-1
$$

$$
\varepsilon_{vol}=\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}+\varepsilon_{xx}\varepsilon_{yy}+\varepsilon_{xx}\varepsilon_{zz}+\varepsilon_{yy}\varepsilon_{zz}+\varepsilon_{xx}\varepsilon_{yy}\varepsilon_{zz}
$$

For small strains, $\varepsilon\ll1$, the products are second and third order and are dropped:

$$
\boxed{\varepsilon_{vol}=\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}}
$$

The neglected products are the thin slabs and the small corner cube left over when a block grows in three directions (Lecture 2, ll. 103–195).

> [!check] How small is "small"?
> With $\varepsilon_{xx}=\varepsilon_{yy}=\varepsilon_{zz}=10^{-3}$ the exact volumetric strain is $(1.001)^3-1=0.003003$ against $0.003$ from the sum, an error of 0.1 %. At 5 % strain in each direction it is $0.1576$ against $0.15$, an error of 5 %, which is why the linear result is a small-strain result.

### Local strain and displacement gradients

In most components the strain is not uniform. A rubber sheet with a hole, printed with a grid and stretched, shows squares near the hole stretching far more than squares away from it, the strain counterpart of a stress concentration; near the clamped ends the sheet cannot contract sideways at all (Lecture 2, ll. 196–256). To describe strain at a point, consider a small element of length $dx$ whose left and right sides move by $u_{x,left}$ and $u_{x,right}$:

$$
\varepsilon_{xx}=\frac{u_{x,right}-u_{x,left}}{dx}
$$

$$
\boxed{\varepsilon_{xx}=\frac{du_x}{dx}}
$$

and likewise $\varepsilon_{yy}=du_y/dy$. A **normal strain is a displacement gradient**. A rigid translation, with the same displacement everywhere, has zero gradient and therefore no strain (Lecture 2, ll. 257–306).

### How small strains are

Strains are dimensionless, metres per metre. For an aluminium alloy with $E=70$ GPa and yield stress 250 MPa, uniaxial Hooke's law gives the strain at yield:

$$
\varepsilon=\frac{\sigma}{E}=\frac{250\times10^6}{70\times10^9}=0.0036
$$

A 1 m bar yields after stretching only about 3.6 mm. Such strains are often written as a percentage, 0.36 %, or in **microstrain**, $1\ \mu\varepsilon=10^{-6}$, here 3600 με (Lecture 2, ll. 307–346).

## 2. Shear strain

### The engineering shear strain

Deformation also changes angles. For a block glued to a surface and sheared by a force on its top face, the top moves sideways by $\delta_s$ relative to the bottom over the height $h$, and the **engineering shear strain** is

$$
\gamma=\frac{\delta_s}{h}=\tan\alpha\approx\alpha
$$

with $\alpha$ in radians; the last step is the small-strain approximation. $\gamma$ is the reduction in the originally right angle between the left and bottom faces (Lecture 2, ll. 358–379).

### Shear does not change volume

Unlike normal strain, shear strain changes shape but not volume. A pack of cards pushed sideways slides card over card, and each card keeps its length and thickness, so the pack keeps its volume (Lecture 2, ll. 380–387). In the small-strain formula this appears as the absence of any shear term in $\varepsilon_{vol}$.

### Shear strain from displacement gradients

A free element is not glued to anything, so both of its sides can rotate. For an element of sides $dx$ and $dy$, let the top move sideways by $du_x$ relative to the bottom, and the right-hand side move up by $du_y$ relative to the left. The left side tilts by $\alpha$ and the bottom by $\beta$:

$$
\alpha\approx\tan\alpha=\frac{du_x}{dy},\qquad \beta\approx\tan\beta=\frac{du_y}{dx}
$$

The total loss of right angle is the engineering shear strain:

$$
\boxed{\gamma_{xy}=\alpha+\beta=\frac{du_x}{dy}+\frac{du_y}{dx}}
$$

Like normal strain, it is made of displacement gradients, but now of sideways displacements: $u_x$ changing with $y$ and $u_y$ changing with $x$ (Lecture 2, ll. 388–435).

![[s2_strain_definitions.png|900]]

### Sign of the shear strain

When both gradients are positive, the element becomes "pointier": the angle between the left and bottom faces (and between the top and right faces) falls below 90°, and $\gamma_{xy}>0$. When both gradients are negative the angle opens beyond 90° and $\gamma_{xy}<0$ (Lecture 2, ll. 436–492). The corners that close are the corners where the positive shear stresses of [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#Sign convention|B1]] point towards each other, so positive shear stress produces positive shear strain.

### Rigid rotation produces no strain

Rotate an undeformed square anticlockwise by a small angle. The bottom tilts up by $\beta$, so $du_y/dx=\beta>0$, and the left side tilts to the left by the same angle, so $du_x/dy=-\beta<0$. The two gradients cancel:

$$
\gamma_{xy}=\frac{du_x}{dy}+\frac{du_y}{dx}=-\beta+\beta=0
$$

The definition correctly reports no deformation for a pure rotation (Lecture 2, ll. 493–517).

### The tensor shear strain

Shear strain is also written in the epsilon notation, with different indices marking a shear component. The **tensor shear strain** is half the engineering shear strain:

$$
\boxed{\varepsilon_{xy}=\frac12\gamma_{xy}=\frac12\left(\frac{du_x}{dy}+\frac{du_y}{dx}\right)}
$$

Both measures appear in textbooks, and the factor of 2 between them is a common source of errors (Lecture 2, ll. 518–548).

The meaning of $\varepsilon_{xy}$ comes from separating rotation from deformation. Measure rotations anticlockwise. The bottom edge of the element rotates by $du_y/dx$ and the left edge by $-du_x/dy$, so the average rotation of the element is

$$
\omega=\frac12\left(\frac{du_y}{dx}-\frac{du_x}{dy}\right)
$$

Subtract it from each edge's rotation. The bottom edge is left with

$$
\frac{du_y}{dx}-\omega=\frac12\left(\frac{du_x}{dy}+\frac{du_y}{dx}\right)=\varepsilon_{xy}
$$

anticlockwise, and the left edge with

$$
-\frac{du_x}{dy}-\omega=-\frac12\left(\frac{du_x}{dy}+\frac{du_y}{dx}\right)=-\varepsilon_{xy}
$$

that is, $\varepsilon_{xy}$ clockwise. After the rotation is removed, each face has turned inwards by $\varepsilon_{xy}$, symmetrically about the diagonal, and the two together close the right angle by $2\varepsilon_{xy}=\gamma_{xy}$ (Lecture 2, ll. 549–568; Lecture 9, ll. 148–174).

> [!warning] Which shear strain goes where
> $\tau=G\gamma$ and the torsion formulas use the engineering $\gamma_{xy}$. The strain transformation equations, Mohr's circle for strain and the rosette formulas use the tensor $\varepsilon_{xy}$ ([[FEEG1002 B5 - Strain Measurement and Strain Rosettes|B5]]). Generalised Hooke's law is written with $\varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy}$, which already contains the factor of 2 ([[FEEG1002 B3 - Generalised Hooke's Law|B3]]).

### Six strain components

In 3D there are three normal strains, $\varepsilon_{xx}$, $\varepsilon_{yy}$, $\varepsilon_{zz}$, and three shear strains, $\varepsilon_{xy}$, $\varepsilon_{xz}$, $\varepsilon_{yz}$. All six vanish for rigid translations and rotations; they describe deformation only (Lecture 2, ll. 569–575).

## 3. Thermal strain

### Free thermal expansion

A bar of length $L_{ref}$ at temperature $T_{ref}$, heated to $T$, grows by $\delta_T$. The **thermal strain** is that growth over the reference length, and experiment shows it is proportional to the temperature change:

$$
\boxed{\varepsilon_T=\frac{\delta_T}{L_{ref}}=\alpha(T-T_{ref})=\alpha\,\Delta T}
$$

where $\alpha$ is the coefficient of thermal expansion, in K⁻¹ or °C⁻¹ (Lecture 3, ll. 71–110). Doubling $\Delta T$ doubles the expansion.

### Thermal expansion is isotropic and stress-free

Heating makes a bar longer and also thicker, unlike tension, which makes it thinner. For an isotropic material the thermal strain is the same in every direction,

$$
\varepsilon_{xx}=\varepsilon_{yy}=\varepsilon_{zz}=\varepsilon_T
$$

with no thermal shear strain. The elongations differ, because the same strain over a longer dimension gives a larger change, but the strain does not (Lecture 3, ll. 111–142). A uniformly heated body of any shape is therefore just a scaled-up copy of itself: no angle changes, no part fights another, and there is no stress. Stress appears only when the temperature is not uniform, so that hot regions are held back by cold ones, or when the body is constrained (Lecture 3, ll. 143–162).

### A bar between two walls

A bar fitted between two rigid walls and heated wants to expand, and the walls push back with a reaction force $F$ that keeps its length unchanged. The stress is found by superposition in three steps (Lecture 3, ll. 163–276).

![[s2_thermal_superposition.png|900]]

First, detach the bar from one wall and let it expand freely:

$$
\delta_T=\alpha\,\Delta T\,L
$$

Second, apply the force $F$, taken as tensile, that brings the bar back. From Hooke's law, $\sigma=E\varepsilon$ with $\sigma=F/A$ and $\varepsilon=\delta_F/L$:

$$
\delta_F=\frac{FL}{EA}
$$

Third, impose compatibility. The walls fix the length, so the total deformation is zero:

$$
\delta_T+\delta_F=0
$$

$$
\alpha\,\Delta T\,L+\frac{FL}{EA}=0
$$

$$
F=-EA\,\alpha\,\Delta T
$$

$$
\boxed{\sigma=\frac FA=-E\,\alpha\,\Delta T}
$$

The force and stress are negative because the bar is compressed. The stress depends on the material through $E\alpha$ and not on the length or cross-section of the bar: a stiffer material that wants to expand more builds up more stress.

### Superposition for constrained assemblies

The same steps solve any axially loaded assembly, provided the compatibility and force conditions are written down carefully before any algebra. Always take every unknown force as tensile and let the sign come out of the solution; deciding in advance which part is in compression is the easiest way to get lost (Lecture 3, ll. 584–604).

For two bars **in series** between rigid walls, for example steel of length $L_s$ joined end to end with brass of length $L_b$, the overall length is fixed and the same force passes through both (Lecture 3, ll. 446–561):

$$
\delta_s+\delta_b=0,\qquad F_s=F_b=F
$$

Each deformation is thermal plus mechanical:

$$
\alpha_s\Delta TL_s+\frac{FL_s}{E_sA_s}+\alpha_b\Delta TL_b+\frac{FL_b}{E_bA_b}=0
$$

$$
F\left(\frac{L_s}{E_sA_s}+\frac{L_b}{E_bA_b}\right)=-\Delta T\left(\alpha_sL_s+\alpha_bL_b\right)
$$

$$
\boxed{F=-\frac{\Delta T\left(\alpha_sL_s+\alpha_bL_b\right)}{L_s/(E_sA_s)+L_b/(E_bA_b)}}
$$

Which way the joint moves depends on both $\alpha$ and the stiffness $EA/L$ of each part, which is why no part "wins" by inspection: a thin steel wire barely resists brass, however stiff steel is.

For two parts **in parallel**, bonded side by side such as a rod inside a tube joined to common end plates, the parts must extend equally and, with no external load, their forces cancel (Lecture 3, ll. 562–614):

$$
\delta_1=\delta_2,\qquad F_1+F_2=0
$$

$$
\alpha_1\Delta TL+\frac{F_1L}{E_1A_1}=\alpha_2\Delta TL-\frac{F_1L}{E_2A_2}
$$

$$
\boxed{F_1\left(\frac{1}{E_1A_1}+\frac{1}{E_2A_2}\right)=(\alpha_2-\alpha_1)\Delta T}
$$

The part with the larger $\alpha$ ends up in compression and the other in tension; the common extension lies between the two free expansions.

### Where thermal stresses matter

Compressive thermal stress is rarely high enough to yield a steel rail but can buckle it, which is why rails in hot weather snake sideways ([[FEEG1002 A7 - Euler Buckling of Struts]]). In electronics, a chip or board fixed at both ends and heated buckles in the same way, and repeated heating and cooling fatigues the solder joints; Tutorial 8 Q2 sizes those joints ([[FEEG1002 B3 - Generalised Hooke's Law#Worked example - chip held by solder joints|B3]]). In precision machines such as lithography steppers, temperature is held uniform and mechanisms are designed so that any expansion does not move critical parts (Lecture 3, ll. 618–645).

---

## Worked examples

### Worked example - shear strain from a displacement field

A plate deforms with $u_x=(2\times10^{-4})\,y$ and $u_y=(1\times10^{-4})\,x$, both in metres (suggested, not lecturer-set). The normal strains are $du_x/dx=0$ and $du_y/dy=0$. The shear strains are

$$
\gamma_{xy}=\frac{du_x}{dy}+\frac{du_y}{dx}=2\times10^{-4}+1\times10^{-4}=3\times10^{-4}
$$

$$
\varepsilon_{xy}=\frac12\gamma_{xy}=1.5\times10^{-4}=150\ \mu\varepsilon
$$

and the element also rotates by $\omega=\tfrac12(1\times10^{-4}-2\times10^{-4})=-5\times10^{-5}$ rad, that is, slightly clockwise. The rotation causes no stress; only the 300 με loss of right angle does.

### Worked example - steel rail with a 3 mm gap

Steel rails ($E=200$ GPa, $\alpha=11.7\times10^{-6}$ °C⁻¹) 10 m long are laid at 6 °C with 3 mm gaps. Find the stress at 48 °C (Lecture 3, ll. 277–416).

Each rail can grow 1.5 mm at each end, or equivalently 3 mm in total, before touching its neighbours. Released, it would grow by

$$
\delta_T=\alpha\,\Delta T\,L=(11.7\times10^{-6})(48-6)(10)=4.91\ \mathrm{mm}
$$

which is more than the 3 mm available, so the neighbours push back. Compatibility now sets the total deformation to the gap:

$$
\delta_T+\delta_F=3\ \mathrm{mm}
$$

$$
\delta_F=3-4.91=-1.91\ \mathrm{mm}
$$

and the stress is

$$
\sigma=\frac{F}{A}=\frac{E}{L}\delta_F=\frac{200\times10^9}{10}(-1.91\times10^{-3})=-38.3\ \mathrm{MPa}
$$

![[s2_thermal_rail.png|900]]

The rail is stress-free until the gap closes, at $6+0.003/(11.7\times10^{-6}\times10)=31.6$ °C, and the stress then grows by $E\alpha=2.34$ MPa per °C. Without the gaps it would be $-E\alpha\Delta T=-98.3$ MPa. Neither is close to the 250 MPa yield stress of mild steel, but the compressive force, about 290 kN for a typical 7670 mm² rail section, is enough to buckle a track.

### Worked example - aluminium shell bonded to a brass core

An aluminium shell (outer diameter 60 mm, $E=70$ GPa, $\alpha=23.6\times10^{-6}$ °C⁻¹) is bonded to a brass core (diameter 25 mm, $E=105$ GPa, $\alpha=20.9\times10^{-6}$ °C⁻¹), stress-free at 15 °C. Find the axial stress in the aluminium at 195 °C, ignoring lateral effects (Tutorial 2 Q1).

The parts are in parallel. The areas are $A_{Al}=\tfrac\pi4(0.06^2-0.025^2)=2.337\times10^{-3}$ m² and $A_{br}=\tfrac\pi4(0.025)^2=4.909\times10^{-4}$ m², and $\Delta T=180$ °C. From the parallel result,

$$
F_{Al}\left(\frac{1}{A_{Al}E_{Al}}+\frac{1}{A_{br}E_{br}}\right)=(\alpha_{br}-\alpha_{Al})\Delta T
$$

$$
F_{Al}=\frac{(20.9-23.6)\times10^{-6}\times180}{\dfrac{1}{(2.337\times10^{-3})(70\times10^9)}+\dfrac{1}{(4.909\times10^{-4})(105\times10^9)}}=-19.05\ \mathrm{kN}
$$

$$
\sigma_{Al}=\frac{F_{Al}}{A_{Al}}=-8.15\ \mathrm{MPa},\qquad \sigma_{br}=\frac{-F_{Al}}{A_{br}}=+38.8\ \mathrm{MPa}
$$

The aluminium wants to grow more than the brass, but bonding forces a common length between the two free lengths, so the shell is held back in compression and the core pulled along in tension. With a steel core ($E=200$ GPa, $\alpha=11.7\times10^{-6}$ °C⁻¹) the mismatch is larger and the core stiffer, and $\sigma_{Al}=-56.2$ MPa.

![[s2_t2_bimaterial_thermal.png|800]]

### Worked example - steel and brass in series between walls

A rod is steel from A to B (250 mm, 30 mm diameter, $E=200$ GPa, $\alpha=11.7\times10^{-6}$ °C⁻¹) and brass from B to C (300 mm, 50 mm diameter, $E=105$ GPa, $\alpha=20.9\times10^{-6}$ °C⁻¹), fixed at both ends and heated by 50 °C (Tutorial 2, additional Q1). The series result gives

$$
F=-\frac{50\left[(11.7\times10^{-6})(0.25)+(20.9\times10^{-6})(0.30)\right]}{\dfrac{0.25}{(200\times10^9)(7.069\times10^{-4})}+\dfrac{0.30}{(105\times10^9)(1.963\times10^{-3})}}=-142.6\ \mathrm{kN}
$$

so $\sigma_s=F/A_s=-201.8$ MPa and $\sigma_b=-72.6$ MPa. The total strains are

$$
\varepsilon_s=\alpha_s\Delta T+\frac{\sigma_s}{E_s}=-4.24\times10^{-4},\qquad \varepsilon_b=\alpha_b\Delta T+\frac{\sigma_b}{E_b}=+3.53\times10^{-4}
$$

and B moves by $\varepsilon_sL_s=-0.106$ mm, towards A: the brass expands and squeezes the steel shorter.

> [!check] Compatibility
> $\varepsilon_bL_b=+0.106$ mm, equal and opposite to the steel's change of length, so the total length is unchanged as required.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]] · Next: [[FEEG1002 B3 - Generalised Hooke's Law]]
- Concepts: [[Strain Components and Volumetric Strain]] · [[Thermal Strain]]
- Worked sheet: [[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 B3 - Generalised Hooke's Law|B3]] (strains from stresses, volume change) · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes|B5]] (strain transformation with $\varepsilon_{xy}$)
- Year 2: strain in cylindrical coordinates, [[Polar Strain-Displacement Relations]] and [[Strain Compatibility]], in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] · interference as a compatibility condition in [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] ([[Shrink Fit]]) · coating mismatch in [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]

## Sources

- `Lecture 02 - Strain in Multiple Dimensions.pdf`: Lectures 2a–2b, normal strains, volume change, local strain, shear strain definition, interpretation and notation.
- `Lecture 03 - Thermal Strains.pdf`: Lectures 3a–3b, thermal strain, constrained bar, rail example, series and parallel assemblies.
- `FEEG1002 Lecture 2 - Statics 2 - Strains in multiple dimesnions - February 2025.txt` (3 Feb 2025): deformation (ll. 20–48), bar and 3D normal strains (ll. 49–102), volumetric strain (ll. 103–195), strain field and gradients (ll. 196–306), magnitudes (ll. 307–346), shear strain (ll. 347–517), tensor notation (ll. 518–575).
- `FEEG1002 Lecture 3 - Statics 2 - Thewrmal Strains - February 2025.txt` (10 Feb 2025): motivation (ll. 14–69), thermal strain (ll. 70–162), constrained bar (ll. 163–276), rail example (ll. 277–427), series and parallel problems (ll. 428–617), applications (ll. 618–645).
- `FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt` (12 May 2025): recap of strain measures and thermal problems (ll. 108–221).
- `Tutorial Sheet 02 - Strain in Multiple Directions and Thermal Strain.pdf` and its solutions: Q1 and additional Q1.

## Self-study tasks

### Core

- [ ] Tutorial 2 Q1, aluminium shell on a brass core, and part (b) with a steel core (the main problem set at Lecture 3, ll. 438–444 and 562–614). Targets −8.15 MPa and −56.2 MPa. → [[#Worked example - aluminium shell bonded to a brass core]] · [[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]]
- [ ] Tutorial 2 additional Q1, steel and brass in series (the additional problem, Lecture 3, ll. 438–447). Targets −142.6 kN and 0.106 mm. → [[#Worked example - steel and brass in series between walls]]
- [ ] Rework the rail example and find the temperature at which the gap closes (Lecture 3, ll. 277–416). → [[#Worked example - steel rail with a 3 mm gap]]
- [ ] Derive $\varepsilon_{vol}=\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}$, stating where the small-strain assumption enters (Lecture 2, ll. 134–184). → [[#Volumetric strain]]

### Further practice

- [ ] Show that a small rigid rotation gives $\gamma_{xy}=0$, then split a general deformation into $\omega$ and $\varepsilon_{xy}$ (Lecture 2, ll. 493–568). → [[#Rigid rotation produces no strain]] · [[#The tensor shear strain]]
- [ ] Derive the series and parallel formulas for $F$ from the two conditions (Lecture 3, ll. 505–614). → [[#Superposition for constrained assemblies]]
- [ ] Shear strain and rotation from a displacement field (suggested, not lecturer-set). → [[#Worked example - shear strain from a displacement field]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 3, ll. 392 and 410)
> Where: [[#Worked example - steel rail with a 3 mm gap]].
>
> The rail's final length condition is read out as "delta T minus Df of 3 millimeters"; it is $\delta_T+\delta_F=3$ mm with $\delta_F$ negative, as on the slide. The resulting stress is read out as "compressive stress of 48 megapascal"; the slide gives $-38$ MPa, and the calculation gives $-38.3$ MPa.

> [!warning] Transcript slip (Lecture 9, l. 124)
> Where: [[#Shear strain from displacement gradients]].
>
> The engineering shear strain is described as "the sum of dux dy and dux dx". The second term is $du_y/dx$, as the same passage then says (l. 131).
