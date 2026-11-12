---
title: "FEEG1002 B5 - Strain Measurement and Strain Rosettes"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 14
tags: [feeg1002, statics-2, strain-gauges, wheatstone-bridge, strain-transformation, rosettes, principal-strains]
aliases: ["Statics 2 Lecture 7", "Strain gauges", "Strain rosette", "Strain transformation"]
date: 2026-11-05
status: lectured
coverage: "Statics 2 Lecture 7 (10 Mar 2025, ll. 1–666): local strain, electrical strain gauges and the gauge factor, the Wheatstone bridge, orientation dependence, strain transformation, Mohr's circle for strain and principal strains, gauges on a shaft in torsion, 0/45/90 and 0/60/120 rosettes, rosettes in other axes, digital image correlation; recap in Lecture 9 (12 May 2025, ll. 464–516)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
next_topics: ["[[FEEG1002 B6 - Yield Criteria]]"]
key_concepts: ["[[Strain Gauge Rosettes]]", "[[Mohr's Circle]]", "[[Stress Transformation Equations]]", "[[Wheatstone Bridge and Strain Gauges]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]]", "[[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 07 - Strain Measurement.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 7 - Statics 2 - Strain measurement - March 2025.txt", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 06 - Strain Measurement.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems.pdf"]
---

# FEEG1002 B5 - Strain Measurement and Strain Rosettes

> [!abstract] Summary
> Stresses cannot be seen, but strains can be measured. A bonded electrical strain gauge changes resistance in proportion to the normal strain along its axis, $\Delta R/R=k\varepsilon_{xx}$, and a Wheatstone bridge turns the tiny change into a measurable voltage. A gauge reads only one normal strain, and that reading depends on its direction through the strain transformation equation $\varepsilon_{x'x'}=\varepsilon_{xx}\cos^2\theta+\varepsilon_{yy}\sin^2\theta+2\varepsilon_{xy}\sin\theta\cos\theta$, identical to the stress equation with the tensor shear strain $\varepsilon_{xy}=\gamma_{xy}/2$ in place of $\sigma_{xy}$. Three gauges in known directions, a rosette, fix all three in-plane strain components; for a 0/45/90 rosette $\varepsilon_{xy}=\varepsilon_C-\tfrac12(\varepsilon_A+\varepsilon_B)$, and for a 0/60/120 rosette $\varepsilon_{xy}=(\varepsilon_B-\varepsilon_C)/\sqrt3$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives gauge or rosette readings and asks for the strain components, principal strains, stresses or a safety factor, or asks how to measure shear or torque with gauges.
> - **Assumptions:** small strains; gauges read the normal strain along their own line; plane stress at the surface to which they are bonded; isotropic material, so principal strain and stress directions coincide.
> - **Method:** 1. Choose $x$ along one gauge so that its reading is $\varepsilon_{xx}$. 2. Write the transformation equation for each other gauge at its angle from $x$ (or use the standard rosette results). 3. Solve for $\varepsilon_{yy}$ and $\varepsilon_{xy}$. 4. If other axes are wanted, rotate with the transformation equations. 5. Convert to stresses with plane-stress Hooke's law ([[FEEG1002 B3 - Generalised Hooke's Law|B3]]) and check yield with von Mises ([[FEEG1002 B6 - Yield Criteria|B6]]).
> - **Common mistakes:** using $\gamma_{xy}$ instead of $\varepsilon_{xy}$ in the transformation equation or on Mohr's circle; matching the gauge labels to the wrong angles (in the 0/45/90 rosette used here, A is at 0°, C at 45° and B at 90°).
> - **Practise:** [[#Worked example - prosthetic socket rosette]] · [[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]]

Once a structure is designed and built, someone has to check that it behaves as the calculations said. Stresses are invisible, except in transparent models viewed under polarised light, so the practical route is to measure strains and convert them to stresses with Hooke's law (Lecture 7, ll. 1–19). In a tensile test that is easy: the strain is uniform and the extension of a long specimen is millimetres. In a real component the strain varies from point to point, and finding a local strain means measuring the difference in displacement between two points a millimetre apart, which is a few micrometres (Lecture 7, ll. 20–42).

The electrical strain gauge solves this by being bonded to the surface and reading the local strain directly as a change of resistance. Gauges are used on aircraft in flight, on vehicles and ships in service, and on cracked old buildings to see whether the cracks are growing (Lecture 7, ll. 43–63). Each gauge, however, measures only how much the surface stretches along one line. A complete picture of the in-plane strain needs three numbers, so it needs three gauges and the strain transformation equations to combine them, which are the equations of [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|B4]] in a new guise.

---

## 1. Electrical strain gauges

### How a gauge works

A foil strain gauge is in effect a fine wire running back and forth many times along one direction, printed on a thin backing that is glued to the surface. When the surface stretches along the gauge, the wire becomes longer and thinner and its resistance rises; the change is proportional to the strain:

$$
\boxed{\frac{\Delta R}{R}=k\,\varepsilon_{xx}}
$$

where $k$ is the **gauge factor** and $x$ is the gauge direction. A gauge is unidirectional: it measures the local normal strain along its own axis and nothing else (Lecture 7, ll. 64–82).

### Where the gauge factor comes from

For a wire the proportionality follows from $R=\rho L/A$. Taking logarithms and differentiating,

$$
\frac{dR}{R}=\frac{d\rho}{\rho}+\frac{dL}{L}-\frac{dA}{A}
$$

For a wire of diameter $d$, $A\propto d^2$, so $dA/A=2\,dd/d$, and the Poisson effect gives $dd/d=-\nu\varepsilon$ with $dL/L=\varepsilon$:

$$
\frac{dR}{R}=\frac{d\rho}{\rho}+\varepsilon+2\nu\varepsilon
$$

$$
\frac{dR}{R}=\varepsilon(1+2\nu)+\frac{d\rho}{\rho}
$$

The geometric part alone gives $k=1+2\nu\approx1.6$ for $\nu=0.3$; the small change in resistivity with strain brings typical metal-foil gauges to $k\approx2$.

### The Wheatstone bridge

The resistance change is tiny, about 0.24 Ω for a 120 Ω gauge at 1000 με, so it is measured with a **Wheatstone bridge**: four resistors in a diamond, supply voltage $V_S$ across one diagonal and the output $V_G$ across the other, with the gauge as one arm, $R_x$ (Lecture 7, ll. 86–158). Each side of the bridge is a voltage divider. Taking the bottom node C as reference, the two output nodes sit at

$$
V_D=\frac{R_2}{R_1+R_2}V_S,\qquad V_B=\frac{R_x}{R_x+R_3}V_S
$$

so

$$
\boxed{V_G=V_D-V_B=\left(\frac{R_2}{R_1+R_2}-\frac{R_x}{R_x+R_3}\right)V_S}
$$

The bridge can be used in two ways. In the null method, the adjustable resistor $R_2$ is tuned until $V_G=0$:

$$
\frac{R_2}{R_1+R_2}=\frac{R_x}{R_x+R_3}
$$

$$
R_2R_x+R_2R_3=R_1R_x+R_2R_x
$$

$$
R_x=\frac{R_2}{R_1}R_3
$$

so with $R_1=R_3$ the gauge resistance equals $R_2$. More often $V_G$ is measured directly. With all four resistances equal to $R$ when unstrained and $R_x=R(1+k\varepsilon)$, the second fraction is $(1+k\varepsilon)/(2+k\varepsilon)\approx\tfrac12+\tfrac14k\varepsilon$ for small $k\varepsilon$, so

$$
V_G\approx-\frac{V_S}{4}k\,\varepsilon
$$

The output is linear in strain and very sensitive to small changes; resolutions of about 1 με are achieved. A gauge that debonds stops following the surface, and a temperature change makes both the gauge and the substrate expand, so a dummy gauge on an unloaded piece of the same material is used to cancel the thermal strain ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Free thermal expansion|B2]]). Bridges, amplifiers and quarter-, half- and full-bridge arrangements are covered in [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]].

## 2. Strain depends on direction

Like stress, the strain you measure depends on the direction you measure it in. On a bar in uniaxial tension, gauge 1 along the bar reads a positive strain $\varepsilon$ and gauge 2 across it reads $-\nu\varepsilon$, although the strain state in the bar is one and the same (Lecture 7, ll. 160–182). A gauge at an angle in between reads something in between, changing gradually from positive to negative as it is turned. Working out what it reads, and conversely what a set of readings implies, requires strain transformation (Lecture 7, ll. 183–195).

## 3. Strain transformation

### The transformation equations

Strains transform with exactly the same equations as stresses, with $\varepsilon$ in place of $\sigma$ and the tensor shear strain $\varepsilon_{xy}$ in place of $\sigma_{xy}$. For axes $x'y'$ rotated anticlockwise by $\theta$ from $xy$ (Lecture 7, ll. 196–255):

$$
\boxed{\varepsilon_{x'x'}=\varepsilon_{xx}\cos^2\theta+\varepsilon_{yy}\sin^2\theta+2\varepsilon_{xy}\sin\theta\cos\theta}
$$

$$
\varepsilon_{y'y'}=\varepsilon_{xx}\sin^2\theta+\varepsilon_{yy}\cos^2\theta-2\varepsilon_{xy}\sin\theta\cos\theta
$$

$$
\varepsilon_{x'y'}=-(\varepsilon_{xx}-\varepsilon_{yy})\sin\theta\cos\theta+\varepsilon_{xy}\left(\cos^2\theta-\sin^2\theta\right)
$$

The second follows from the first with $\theta+90^\circ$, using $\sin(\theta+90^\circ)=\cos\theta$ and $\cos(\theta+90^\circ)=-\sin\theta$ (Lecture 7, ll. 228–248). The first line is the one used for gauges, since a gauge at angle $\theta$ reads $\varepsilon_{x'x'}$.

### Why strain transforms like stress

The stress equations came from equilibrium of a wedge; the strain equations come from geometry, and the two have the same form because stress and strain are both symmetric tensors. Take a short line element of length $ds$ in the direction $\hat n=(\cos\theta,\sin\theta)$, so that its ends are separated by $dx=ds\cos\theta$ and $dy=ds\sin\theta$. Its far end moves relative to its near end by

$$
du_x=\frac{\partial u_x}{\partial x}dx+\frac{\partial u_x}{\partial y}dy,\qquad du_y=\frac{\partial u_y}{\partial x}dx+\frac{\partial u_y}{\partial y}dy
$$

For small strains the line lengthens by the component of this relative displacement along the line, $du_x\cos\theta+du_y\sin\theta$, so its normal strain is

$$
\varepsilon_{x'x'}=\frac{du_x\cos\theta+du_y\sin\theta}{ds}
$$

$$
\varepsilon_{x'x'}=\frac{\partial u_x}{\partial x}\cos^2\theta+\left(\frac{\partial u_x}{\partial y}+\frac{\partial u_y}{\partial x}\right)\sin\theta\cos\theta+\frac{\partial u_y}{\partial y}\sin^2\theta
$$

$$
\varepsilon_{x'x'}=\varepsilon_{xx}\cos^2\theta+\varepsilon_{yy}\sin^2\theta+2\varepsilon_{xy}\sin\theta\cos\theta
$$

using the definitions of [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#The tensor shear strain|B2]]. Only the sum of the two cross gradients appears, so rigid rotation drops out, and the factor 2 in front of $\varepsilon_{xy}$ is exactly where the factor 2 between $\gamma_{xy}$ and $\varepsilon_{xy}$ comes from. With $\gamma_{xy}$ the equation would read $\gamma_{xy}\sin\theta\cos\theta$, and would no longer match the stress equation.

### A bar in tension seen through the transformation

For the bar, $\varepsilon_{xx}=\varepsilon$, $\varepsilon_{yy}=-\nu\varepsilon$ and $\varepsilon_{xy}=0$, so a gauge at angle $\theta$ reads

$$
\varepsilon_{x'x'}=\varepsilon\left(\cos^2\theta-\nu\sin^2\theta\right)
$$

which falls from $\varepsilon$ along the bar to $-\nu\varepsilon$ across it, passing through zero where $\tan^2\theta=1/\nu$: at 61.3° for $\nu=0.3$.

## 4. Mohr's circle for strain

### Construction

Because the equations are the same, Mohr's circle works for strain exactly as for stress, provided the tensor shear strain $\varepsilon_{xy}=\tfrac12\gamma_{xy}$ is plotted on the shear axis, positive downwards (Lecture 7, ll. 256–285; Lecture 9, ll. 483–486). The centre is

$$
\varepsilon_{average}=\frac{\varepsilon_{xx}+\varepsilon_{yy}}{2},\qquad R=\sqrt{\left(\frac{\varepsilon_{xx}-\varepsilon_{yy}}{2}\right)^2+\varepsilon_{xy}^2}
$$

the point for $\theta=0$ is $(\varepsilon_{xx},\varepsilon_{xy})$, and a rotation $\theta$ of the axes is a rotation $2\theta$ the same way on the circle. It applies to any 2D strain state, plane stress or plane strain.

### Principal strains

The circle crosses the normal-strain axis at the **principal strains**, $\varepsilon_I=\varepsilon_{average}+R$ and $\varepsilon_{II}=\varepsilon_{average}-R$, on two perpendicular directions with no shear strain, where the material is only stretched or compressed (Lecture 7, ll. 286–328). The maximum shear strain in the plane is $\varepsilon_{x'y'}^{max}=R=(\varepsilon_I-\varepsilon_{II})/2$, or $\gamma^{max}=\varepsilon_I-\varepsilon_{II}$ in engineering terms.

For an isotropic material the principal strains lie in the same directions as the principal stresses. In the principal stress axes $\sigma_{x'y'}=0$, and Hooke's law gives $\varepsilon_{x'y'}=\frac{1+\nu}{E}\sigma_{x'y'}=0$ there too, so the same axes are free of shear strain. This is what lets rosette results be converted to principal stresses directly.

## 5. Measuring shear in a shaft

A shaft in torsion is in pure shear: the circles of the shaft rotate relative to one another, so a surface element distorts, but it is not stretched along or across the shaft ($\varepsilon_{xx}=\varepsilon_{yy}=0$). A gauge cannot sense angular distortion, so a gauge along or across the shaft reads nothing (Lecture 7, ll. 329–340). The strain circle is centred on the origin with radius $\varepsilon_{xy}$, so rotating 90° on the circle, 45° on the shaft, reaches the principal strains:

$$
\varepsilon_I=+\varepsilon_{xy}\ \text{at}\ +45^\circ,\qquad \varepsilon_{II}=-\varepsilon_{xy}\ \text{at}\ -45^\circ
$$

Gauges at $\pm45^\circ$ therefore read equal and opposite strains, one diagonal of the distorted element lengthening and the other shortening, and

$$
\boxed{\varepsilon_{xy}=R=\frac{\varepsilon_I-\varepsilon_{II}}{2}}
$$

gives the shear strain, and with $\gamma=2\varepsilon_{xy}$ and $\tau=G\gamma$ the torque (Lecture 7, ll. 341–414). This is how torque transducers work.

![[s2_mohr_pure_shear.png|900]]

## 6. Strain gauge rosettes

### Three gauges for three unknowns

In general there are three unknown in-plane strain components, $\varepsilon_{xx}$, $\varepsilon_{yy}$ and $\varepsilon_{xy}$, and the principal directions are not known in advance, so the gauges cannot be placed along them. Each gauge gives one equation, the transformation equation at its own angle, so three gauges in three independent directions are enough. A **strain gauge rosette** is a single backing carrying three gauges at fixed angles (Lecture 7, ll. 415–440).

![[s2_strain_rosettes.png|900]]

### The 0/45/90 rosette

In the labelling used here, gauge A lies along $x$, C at 45° and B at 90°. A and B read the normal strains directly (Lecture 7, ll. 441–462):

$$
\varepsilon_{xx}=\varepsilon_A,\qquad \varepsilon_{yy}=\varepsilon_B
$$

The shear strain comes from gauge C, using $\cos45^\circ=\sin45^\circ=\tfrac{\sqrt2}{2}$:

$$
\varepsilon_C=\varepsilon_{xx}\cos^245^\circ+\varepsilon_{yy}\sin^245^\circ+2\varepsilon_{xy}\sin45^\circ\cos45^\circ
$$

$$
\varepsilon_C=\frac12\varepsilon_{xx}+\frac12\varepsilon_{yy}+\varepsilon_{xy}
$$

$$
\boxed{\varepsilon_{xy}=\varepsilon_C-\frac12\left(\varepsilon_A+\varepsilon_B\right)}
$$

(Lecture 7, ll. 463–508). Labelling varies between sheets, so match each reading to its angle before substituting (Lecture 9, ll. 505–515).

### A gauge has no direction

A gauge measures stretch along a line, and a line has no head or tail, so a gauge at $\theta$ is the same as one at $\theta\pm180^\circ$. The transformation equation agrees: $\cos^2$, $\sin^2$ and the product $\sin\theta\cos\theta$ are all unchanged when $\theta$ increases by 180°. A gauge drawn at $-120^\circ$ can be treated as $+60^\circ$, and one at $-60^\circ$ as $+120^\circ$ (Lecture 7, ll. 516–527).

### The 0/60/120 rosette

With A along $x$, B at 60° and C at 120°, gauge A gives $\varepsilon_{xx}=\varepsilon_A$ and the other two give two equations in $\varepsilon_{yy}$ and $\varepsilon_{xy}$ (Lecture 7, ll. 509–597). With $\cos60^\circ=\tfrac12$, $\sin60^\circ=\tfrac{\sqrt3}{2}$, $\cos120^\circ=-\tfrac12$ and $\sin120^\circ=\tfrac{\sqrt3}{2}$:

$$
\varepsilon_B=\frac14\varepsilon_A+\frac34\varepsilon_{yy}+\frac{\sqrt3}{2}\varepsilon_{xy}
$$

$$
\varepsilon_C=\frac14\varepsilon_A+\frac34\varepsilon_{yy}-\frac{\sqrt3}{2}\varepsilon_{xy}
$$

Subtracting removes $\varepsilon_{yy}$:

$$
\varepsilon_B-\varepsilon_C=\sqrt3\,\varepsilon_{xy}
$$

$$
\boxed{\varepsilon_{xy}=\frac{\varepsilon_B-\varepsilon_C}{\sqrt3}}
$$

Adding removes $\varepsilon_{xy}$:

$$
\varepsilon_B+\varepsilon_C=\frac12\varepsilon_A+\frac32\varepsilon_{yy}
$$

$$
\boxed{\varepsilon_{yy}=\frac{2(\varepsilon_B+\varepsilon_C)-\varepsilon_A}{3}}
$$

The three gauges are spread evenly, which does not favour any direction.

### Rosettes in other axes

The easiest manual method is to align $x$ with one gauge, which removes one unknown, solve as above, and then use the transformation equations to rotate the strains into whatever axes are wanted. Alternatively, write the transformation equation at all three gauge angles in the wanted axes and solve the three simultaneous equations, which is best done by software (Lecture 7, ll. 598–632). Tutorial 6 uses the first method.

## 7. From strain to stress

The rosette gives the surface strains; the surface is free, so it is in plane stress, and the inverse plane-stress law of [[FEEG1002 B3 - Generalised Hooke's Law#Stresses from strains|B3]] gives $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$. A yield criterion then condenses them into one equivalent stress for comparison with the yield stress ([[FEEG1002 B6 - Yield Criteria|B6]]), and because the criterion is independent of orientation it does not matter how the rosette was stuck on (Lecture 9, ll. 516–530).

## 8. Digital image correlation

Gauges give strains at points and need a lot of wiring when many points are wanted. **Digital image correlation** (DIC) instead sprays a random speckle pattern on the surface, films it as the structure is loaded, and tracks how small patches of the pattern move; differentiating the displacement field gives the strain field everywhere on the surface, and two cameras give 3D displacements by stereo vision. It is less sensitive than a gauge but shows the whole field, revealing, for example, that the strain in a "uniform" tensile test is not uniform near the grips (Lecture 7, ll. 641–661).

---

## Worked examples

### Worked example - gauge and bridge output

A 120 Ω gauge with $k=2$ is strained to 1000 με in a bridge of four equal resistors supplied at 5 V (suggested, not lecturer-set). The resistance change is

$$
\Delta R=kR\varepsilon=2(120)(1000\times10^{-6})=0.24\ \Omega
$$

and the bridge output is

$$
V_G\approx-\frac{V_S}{4}k\varepsilon=-\frac{5}{4}(2)(10^{-3})=-2.5\ \mathrm{mV}
$$

The exact formula gives $-2.4975$ mV, so the linear approximation is good to 0.1 % at this strain. One microstrain gives 2.5 μV, which is why the amplifier matters.

### Worked example - torque transducer on a shaft

A solid steel shaft of diameter 20 mm ($G=80$ GPa) carries a torque of 100 N m (suggested, not lecturer-set). What do gauges at $\pm45^\circ$ to the axis read? The surface shear stress and strain are

$$
\sigma_{xy}=\frac{16T}{\pi d^3}=\frac{16(100)}{\pi(0.02)^3}=63.7\ \mathrm{MPa}
$$

$$
\gamma_{xy}=\frac{\sigma_{xy}}{G}=796\ \mu\varepsilon,\qquad \varepsilon_{xy}=398\ \mu\varepsilon
$$

so the gauges read $+398$ and $-398$ με. Half their difference gives back $\varepsilon_{xy}$, and the torque follows. Wiring the two gauges into adjacent arms of a bridge doubles the output and cancels any axial or thermal strain, which affects both gauges equally.

### Worked example - prosthetic socket rosette

A rosette on a prosthetic socket has gauge 1 at $-15^\circ$, gauge 2 at $+30^\circ$ and gauge 3 at $+75^\circ$ to $x$, reading $\varepsilon_1=480$, $\varepsilon_2=-120$ and $\varepsilon_3=80$ με. Find $\varepsilon_{xx}$, $\varepsilon_{yy}$ and $\varepsilon_{xy}$ (Tutorial 6).

The gauges are 45° apart, so in axes $x^*y^*$ with $x^*$ along gauge 1 the rosette is a 0/45/90 rosette with gauge 2 playing the part of C and gauge 3 of B:

$$
\varepsilon_{x^*x^*}=480,\qquad \varepsilon_{y^*y^*}=80,\qquad \varepsilon_{x^*y^*}=-120-\frac12(480+80)=-400\ \mu\varepsilon
$$

The $x$ axis is 15° anticlockwise from $x^*$, so rotate by $\theta=+15^\circ$:

$$
\varepsilon_{xx}=480\cos^215^\circ+80\sin^215^\circ+2(-400)\sin15^\circ\cos15^\circ=253\ \mu\varepsilon
$$

$$
\varepsilon_{yy}=480\sin^215^\circ+80\cos^215^\circ-2(-400)\sin15^\circ\cos15^\circ=307\ \mu\varepsilon
$$

$$
\varepsilon_{xy}=-(480-80)\sin15^\circ\cos15^\circ+(-400)\left(\cos^215^\circ-\sin^215^\circ\right)=-446\ \mu\varepsilon
$$

The strain circle has centre 280 με and radius $\sqrt{27^2+446^2}=447$ με, so $\varepsilon_I=727$ με and $\varepsilon_{II}=-167$ με; the engineering shear strain is $\gamma_{xy}=-893$ με.

> [!check] Back-substitution
> Putting 253, 307 and $-446$ back into the transformation equation at $-15^\circ$, $30^\circ$ and $75^\circ$ returns 480, $-120$ and 80 με, and $\varepsilon_{xx}+\varepsilon_{yy}=560=\varepsilon_{x^*x^*}+\varepsilon_{y^*y^*}$, the strain invariant.

![[s2_t6_strain_vs_angle.png|850]]

### Worked example - hydraulic press frame

A 0/60/120 rosette on the frame of a hydraulic press ($E=207$ GPa, $\nu=0.3$) reads $\varepsilon_1=800$, $\varepsilon_2=300$ and $\varepsilon_3=500$ με at 0°, 60° and 120° under a 450 MN load. Find the strain and stress components (Tutorial 8 Q1(a)–(b)).

$$
\varepsilon_{xx}=800\ \mu\varepsilon,\qquad \varepsilon_{yy}=\frac{2(300+500)-800}{3}=267\ \mu\varepsilon,\qquad \varepsilon_{xy}=\frac{300-500}{\sqrt3}=-115\ \mu\varepsilon
$$

The frame surface is in plane stress, so

$$
\sigma_{xx}=\frac{E}{1-\nu^2}\left(\varepsilon_{xx}+\nu\varepsilon_{yy}\right)=\frac{207\times10^9}{0.91}(880\times10^{-6})=200\ \mathrm{MPa}
$$

$$
\sigma_{yy}=\frac{E}{1-\nu^2}\left(\varepsilon_{yy}+\nu\varepsilon_{xx}\right)=\frac{207\times10^9}{0.91}(507\times10^{-6})=115\ \mathrm{MPa}
$$

$$
\sigma_{xy}=\frac{E}{1+\nu}\varepsilon_{xy}=\frac{207\times10^9}{1.3}(-115.5\times10^{-6})=-18.4\ \mathrm{MPa}
$$

The principal stresses are 204 and 111 MPa at $\theta_p=-11.7^\circ$, the same angle as the principal strains, as isotropy requires. The safety factor and maximum load are found in [[FEEG1002 B6 - Yield Criteria#Worked example - hydraulic press frame|B6]].

### Worked example - strain circle for a hydrogen tank

A thin-walled cylindrical tank ($R=0.35$ m, $t=1.5$ mm, $E=120$ GPa, $\nu=0.33$) works at the pressure of 7.26 bar found in [[FEEG1002 B6 - Yield Criteria#Worked example - liquid hydrogen tank|B6]]. Find the surface strains, draw the strain circle and say what torsion would add (Tutorial 8 Q3(ii)–(iv)).

$$
\sigma_{xx}=\frac{pR}{2t}=84.7\ \mathrm{MPa},\qquad \sigma_{yy}=\frac{pR}{t}=169.4\ \mathrm{MPa}
$$

$$
\varepsilon_{xx}=\frac{1}{E}\left(\sigma_{xx}-\nu\sigma_{yy}\right)=240\ \mu\varepsilon,\qquad \varepsilon_{yy}=\frac1E\left(\sigma_{yy}-\nu\sigma_{xx}\right)=1178\ \mu\varepsilon
$$

With no shear in the axial–hoop axes these are the principal strains, $\varepsilon_I=1178$ and $\varepsilon_{II}=240$ με. The circle is centred at 709 με with radius

$$
\left|\varepsilon_{x'y'}\right|^{max}=\frac{\varepsilon_I-\varepsilon_{II}}{2}=469\ \mu\varepsilon
$$

on planes at 45° to the axis. Torsion would add a shear strain $\varepsilon_{xy}$: the centre stays at 709 με but the radius grows, so $\varepsilon_I$ increases, $\varepsilon_{II}$ decreases and the principal directions turn away from the axial and hoop directions.

![[s2_strain_mohr_t8_q3.png|800]]

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · Next: [[FEEG1002 B6 - Yield Criteria]]
- Concepts: [[Strain Gauge Rosettes]] · [[Stress Transformation Equations]] · [[Mohr's Circle]] · [[Strain Components and Volumetric Strain]] · [[Wheatstone Bridge and Strain Gauges]]
- Worked sheets: [[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]] (Q1, Q3) · Formula list: [[FEEG1002 Formula Sheet]]
- Year 1 electronics: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
- Year 2: the measurement chain from bridge to digital signal in [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] and [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]] · gauges and DIC as test data for [[SESA2029 B10 - FE Verification, Validation and Model Updating]]

## Sources

- `Lecture 07 - Strain Measurement.pdf`: Lectures 7a–7c, introduction, strain gauges, Wheatstone bridge, strain transformation, Mohr's circle for strain, torsion example, rosettes, DIC.
- `FEEG1002 Lecture 7 - Statics 2 - Strain measurement - March 2025.txt` (10 Mar 2025): motivation and local strain (ll. 1–42), gauges (ll. 43–82), Wheatstone bridge and practical points (ll. 83–158), orientation (ll. 159–195), transformation (ll. 196–255), Mohr's circle and principal strains (ll. 256–328), torsion (ll. 329–414), rosettes (ll. 415–632), DIC (ll. 633–661).
- `FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt` (12 May 2025): recap (ll. 464–530).
- `Tutorial Sheet 06 - Strain Measurement.pdf` and solutions; `Tutorial Sheet 08 - Revision Problems.pdf` and solutions: Q1 and Q3.

## Self-study tasks

### Core

- [ ] Tutorial 6, prosthetic socket rosette (the quiz and tutorial problem at Lecture 7, ll. 661–662). Targets 253, 307 and $-446$ με. → [[#Worked example - prosthetic socket rosette]] · [[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]]
- [ ] Tutorial 8 Q1(a)–(b), press frame rosette. Targets 267 and $-115$ με; 200, 115 and $-18.4$ MPa. → [[#Worked example - hydraulic press frame]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]
- [ ] Derive the 0/45/90 and 0/60/120 rosette formulas (Lecture 7, ll. 441–597). → [[#The 0/45/90 rosette]] · [[#The 0/60/120 rosette]]
- [ ] Tutorial 8 Q3(ii)–(iv), strain circle for the hydrogen tank. Targets 240 and 1178 με, radius 469 με. → [[#Worked example - strain circle for a hydrogen tank]]

### Further practice

- [ ] Derive the strain transformation equation from displacement gradients and explain the factor 2 on $\varepsilon_{xy}$. → [[#Why strain transforms like stress]]
- [ ] Derive the bridge output and its small-strain form (Lecture 7, ll. 127–145). → [[#The Wheatstone bridge]]
- [ ] Gauges on a shaft in torsion (Lecture 7, ll. 329–414; numbers suggested, not lecturer-set). → [[#Worked example - torque transducer on a shaft]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 7, ll. 374–375 and 385–388)
> Where: [[#5. Measuring shear in a shaft]].
>
> Moving from $\varepsilon_I$ to $\varepsilon_{II}$ is described as "180 degrees further, or 90 degrees in Mohr's circle"; it is 90° on the shaft and 180° on the circle. A few lines later "rotate by 90 degrees in reality, or 45 degrees, or 90 degrees in Mohr's circle" is a self-correction; the result is 45° on the shaft, 90° on the circle, as on the slide.
