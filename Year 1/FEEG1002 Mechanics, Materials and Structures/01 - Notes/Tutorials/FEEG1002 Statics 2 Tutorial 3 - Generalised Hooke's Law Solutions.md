---
title: "FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, hookes-law, plane-stress]
sheet: "Statics-2 Tutorial problem sheet 3"
theory_notes: ["[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
key_concepts: ["[[Generalised Hooke's Law]]", "[[Thin-Walled Pressure Vessels]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 03 - Generalised Hooke's Law.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 03 - Generalised Hooke's Law - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions

> [!abstract] Sheet info
> Pressure-vessel stresses, then plane-stress Hooke's law, then changes of dimension. All answers match the official solutions, checked numerically.

## Q1 Acrylic submersible hull at 100 m

*Taught in:* [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#4. Thin-walled pressure vessels]] and [[FEEG1002 B3 - Generalised Hooke's Law#2. Plane stress]] · worked in full at [[FEEG1002 B3 - Generalised Hooke's Law#Worked example - submersible hull at 100 m]].

Data: length 15 m, diameter 2.2 m ($R=1.1$ m), wall 140 mm, $E=3.2$ GPa, $\nu=0.37$.

**(i) Wall stresses.** Inside and outside both start at atmospheric pressure, so the net internal pressure at 100 m is

$$
p=-\rho gh=-(1000)(9.81)(100)=-9.81\times10^5\ \mathrm{Pa}
$$

and the wall stresses are compressive:

$$
\sigma_{xx}=\frac{pR}{2t}=\frac{(-9.81\times10^5)(1.1)}{2(0.14)}=-3.85\ \mathrm{MPa},\qquad \sigma_{yy}=\frac{pR}{t}=-7.71\ \mathrm{MPa}
$$

**(ii) Changes of length and diameter.** In plane stress,

$$
\varepsilon_{xx}=\frac1E\left(\sigma_{xx}-\nu\sigma_{yy}\right)=-313\ \mu\varepsilon,\qquad \varepsilon_{yy}=\frac1E\left(\sigma_{yy}-\nu\sigma_{xx}\right)=-1963\ \mu\varepsilon
$$

$$
\Delta L=\varepsilon_{xx}L=-4.7\ \mathrm{mm},\qquad \Delta D=\varepsilon_{yy}D=-4.3\ \mathrm{mm}
$$

The hoop strain is also the diameter strain, since $\Delta(\pi D)/(\pi D)=\Delta D/D$. Without the Poisson term the axial strain would be $-1204\ \mu\varepsilon$, nearly four times too large.

**(iii) Validity.** No: $t/R=0.14/1.1=0.127>0.1$, so the thin-wall model is only approximate and a thick-cylinder (Lamé) analysis would be needed ([[Lame Thick-Cylinder Solution]]). A thin acrylic wall would also be prone to buckling, since it is in compression.

## Additional Q1 Spherical vessel with brittle paint

*Taught in:* [[FEEG1002 B3 - Generalised Hooke's Law#2. Plane stress]] · worked in full at [[FEEG1002 B3 - Generalised Hooke's Law#Worked example - painted spherical vessel]].

Data: diameter 480 mm ($R=0.24$ m), wall 8 mm, $E=205$ GPa, $\nu=0.30$; the paint cracks at 150 με. With $\sigma_{xx}=\sigma_{yy}=pR/2t$,

$$
\varepsilon=\frac{1}{E}\frac{pR}{2t}(1-\nu)
$$

$$
p=\frac{2Et\varepsilon}{R(1-\nu)}=\frac{2(205\times10^9)(0.008)(150\times10^{-6})}{(0.24)(0.7)}=2.93\ \mathrm{MPa}
$$

The official solution uses $\varepsilon_{xx}$; $\varepsilon_{yy}$ is the same in a sphere.

## Sources

- `Tutorial Sheet 03 - Generalised Hooke's Law.pdf` and its solutions.
