---
title: "FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, revision, rosettes, von-mises, thermal-strain, mohrs-circle]
sheet: "Statics-2 Tutorial problem sheet 8 (revision)"
theory_notes: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]", "[[FEEG1002 B6 - Yield Criteria]]"]
key_concepts: ["[[Strain Gauge Rosettes]]", "[[Generalised Hooke's Law]]", "[[Von Mises Yield Criterion]]", "[[Mohr's Circle]]", "[[Thermal Strain]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions

> [!abstract] Sheet info
> Four exam-style questions that chain the Statics 2 topics: rosette, Hooke's law, von Mises and safety factor; restrained thermal expansion; pressure vessel, yield and strain Mohr's circle; stress Mohr's circle. All answers match the official solutions, checked numerically. These were the revision problems set for the Easter break (Lecture 8, ll. 637–640).

## Q1 Rosette on a hydraulic press frame

*Taught in:* [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#The 0/60/120 rosette]], [[FEEG1002 B3 - Generalised Hooke's Law#Stresses from strains]] and [[FEEG1002 B6 - Yield Criteria#4. Failure load and safety factor]] · worked in full at [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Worked example - hydraulic press frame]] and [[FEEG1002 B6 - Yield Criteria#Worked example - hydraulic press frame]].

Data: 0/60/120 rosette with gauges 1, 2 and 3 at 0°, 60° and 120°; $E=207$ GPa, $\nu=0.3$, $\sigma_Y=355$ MPa; load 450 MN; readings 800, 300 and 500 με.

**(a) Strains.**

$$
\varepsilon_{xx}=\varepsilon_1=800\ \mu\varepsilon,\qquad \varepsilon_{yy}=\frac{2(\varepsilon_2+\varepsilon_3)-\varepsilon_1}{3}=267\ \mu\varepsilon,\qquad \varepsilon_{xy}=\frac{\varepsilon_2-\varepsilon_3}{\sqrt3}=-115\ \mu\varepsilon
$$

Putting these back into the transformation equation at 0°, 60° and 120° returns 800, 300 and 500 με.

**(b) Stresses**, in plane stress:

$$
\sigma_{xx}=\frac{E}{1-\nu^2}\left(\varepsilon_{xx}+\nu\varepsilon_{yy}\right)=200\ \mathrm{MPa},\qquad \sigma_{yy}=\frac{E}{1-\nu^2}\left(\varepsilon_{yy}+\nu\varepsilon_{xx}\right)=115\ \mathrm{MPa}
$$

$$
\sigma_{xy}=\frac{E}{1+\nu}\varepsilon_{xy}=-18.4\ \mathrm{MPa}
$$

**(c) Maximum load.**

$$
\sigma_{eq}=\sqrt{200^2+115^2-(200)(115)+3(18.4)^2}=177\ \mathrm{MPa},\qquad SF=\frac{355}{177}=2.0
$$

$$
F_{max}=SF\times450\ \mathrm{MN}=9.0\times10^8\ \mathrm{N}
$$

This relies on linearity: every stress is proportional to the load up to first yield.

## Q2 Microchip held by solder joints

*Taught in:* [[FEEG1002 B3 - Generalised Hooke's Law#6. Adding a thermal strain]] · worked in full at [[FEEG1002 B3 - Generalised Hooke's Law#Worked example - chip held by solder joints]].

Data: $E=140$ GPa, $\nu=0.265$, $\alpha=2.59\times10^{-6}$ K⁻¹; square chip 15 mm by 15 mm, 2 mm thick; 12 joints per side; heated by 30 °C; board rigid.

The board prevents all in-plane expansion, so total strain is zero and the mechanical strains are $\varepsilon_{xx}=\varepsilon_{yy}=-\alpha\Delta T=-7.77\times10^{-5}$. In plane stress,

$$
\sigma_{xx}=\frac{E}{1-\nu^2}\left(\varepsilon_{xx}+\nu\varepsilon_{yy}\right)=-\frac{E\alpha\Delta T}{1-\nu}=-14.8\ \mathrm{MPa}
$$

$$
F_{side}=|\sigma_{xx}|\,dt=(14.8\times10^6)(0.015)(0.002)=444\ \mathrm{N},\qquad F_{joint}=\frac{444}{12}=37\ \mathrm{N}
$$

The factor $1/(1-\nu)$ makes biaxial restraint 36 % more severe than restraint in one direction, because Poisson contraction cannot relieve it.

## Q3 Liquid hydrogen tank

*Taught in:* [[FEEG1002 B6 - Yield Criteria#Plane stress in xy components]], [[FEEG1002 B3 - Generalised Hooke's Law#2. Plane stress]] and [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#4. Mohr's circle for strain]] · worked in full at [[FEEG1002 B6 - Yield Criteria#Worked example - liquid hydrogen tank]] and [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Worked example - strain circle for a hydrogen tank]].

Data: thin-walled cylinder, length 2.5 m, $R=0.35$ m, plane stress.

**(i) Allowable pressure** for $t=1.5$ mm, $\sigma_Y=440$ MPa and a safety factor of 3. With $\sigma_{xx}=pR/2t$, $\sigma_{yy}=pR/t$ and no shear,

$$
\sigma_{eq}=\frac{pR}{t}\sqrt{\frac14+1-\frac12}=\frac{\sqrt3}{2}\frac{pR}{t}=\frac{\sigma_Y}{SF}
$$

$$
p=\frac{2\sigma_Yt}{\sqrt3\,SF\,R}=7.26\times10^5\ \mathrm{Pa}=7.26\ \mathrm{bar}
$$

**(ii) Strains** with $E=120$ GPa and $\nu=0.33$. The stresses are $\sigma_{xx}=84.7$ MPa and $\sigma_{yy}=169$ MPa, so

$$
\varepsilon_{xx}=\frac1E\left(\sigma_{xx}-\nu\sigma_{yy}\right)=240\ \mu\varepsilon,\qquad \varepsilon_{yy}=\frac1E\left(\sigma_{yy}-\nu\sigma_{xx}\right)=1178\ \mu\varepsilon
$$

**(iii) Strain Mohr's circle.** There is no shear in the axial–hoop axes, so these are the principal strains, $\varepsilon_I=1178$ and $\varepsilon_{II}=240$ με. The centre is 709 με and the radius, the maximum shear strain in any orientation, is

$$
\left|\varepsilon_{x'y'}\right|^{max}=\frac{\varepsilon_I-\varepsilon_{II}}{2}=469\ \mu\varepsilon
$$

at ±45° to the axis.

**(iv) Adding torsion.** Torsion adds a shear strain $\varepsilon_{xy}\neq0$. The centre stays at 709 με but the radius grows, so $\varepsilon_I$ increases, $\varepsilon_{II}$ decreases, and the principal directions turn away from the axial and hoop directions.

![[s2_strain_mohr_t8_q3.png|800]]

## Q4 Stress element and Mohr's circle

*Taught in:* [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#5. Principal stresses and maximum shear]] · worked in full at [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - revision element]].

**(a)** $\sigma_{xx}=10$ MPa and $\sigma_{yy}=50$ MPa, both tensile. The shear arrow on the right-hand face points down, a negative direction on a face with positive normal, so $\sigma_{xy}=-15$ MPa. The centre is $(10+50)/2=30$ MPa and the $x$-face point $(10,-15)$ plots above the axis.

**(b)**

$$
R=\sqrt{\left(\frac{10-50}{2}\right)^2+(-15)^2}=25\ \mathrm{MPa}
$$

so the maximum in-plane shear stress is 25 MPa, and $\sigma_I=30+25=55$ MPa, $\sigma_{II}=30-25=5$ MPa.

**(c)** On the planes of maximum shear both normal stresses equal the centre, 30 MPa.

**(d)** The angle between the radius to the $x$-face point and the direction of $\sigma_{II}$ is $\beta=\tan^{-1}(15/20)=36.87^\circ$, so the rotation on the circle from the $x$-face point to $\sigma_I$ is $|2\theta|=180^\circ-36.87^\circ=143.1^\circ$, clockwise (over the top of the circle). Hence $\theta_p=-71.6^\circ$: $\sigma_I$ acts 71.6° clockwise from $x$.

**(e)** The principal element has $x'$ at $-71.6^\circ$ carrying 55 MPa and $y'$ carrying 5 MPa, with no shear.

![[s2_mohr_t8_q4.png|900]]

## Sources

- `Tutorial Sheet 08 - Revision Problems.pdf` and its solutions.
