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

> [!abstract] Sheet Info
> Pressure vessel stresses → plane-stress Hooke's law → dimension changes. All answers are reproduced ✔.

## Theory Links
- [[FEEG1002 B3 - Generalised Hooke's Law]] · [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]

---

## Q1: Acrylic submersible hull, $L = 15$ m, $D = 2.2$ m, $t = 140$ mm, rated to 100 m
### (i) Wall stresses at 100 m
Atmospheric pressure acts both inside and out, so the **net** internal-minus-external pressure is

$$
p = -\rho gh = -(1000)(9.81)(100) = -9.81\times10^5\ \text{Pa}
$$

The negative pressure makes the wall stresses compressive:

$$
\sigma_{xx} = \frac{pR}{2t} = \frac{(-9.81\times10^5)(1.1)}{2(0.14)} = \mathbf{-3.85}\ \text{MPa},\qquad \sigma_{yy} = \frac{pR}{t} = \mathbf{-7.71}\ \text{MPa}\ ✔
$$

### (ii) Changes of length and diameter ($E = 3.2$ GPa, $\nu = 0.37$, plane stress)

$$
\varepsilon_{xx} = \frac1E(\sigma_{xx} - \nu\sigma_{yy}) = \mathbf{-313}\ \mu\varepsilon,\qquad \varepsilon_{yy} = \frac1E(\sigma_{yy} - \nu\sigma_{xx}) = \mathbf{-1963}\ \mu\varepsilon
$$

- $\Delta L = \varepsilon_{xx}L = -4.7$ mm.
- $\Delta D = \varepsilon_{yy}D = -4.3$ mm. The hoop strain is also the diameter strain, because $\pi\Delta D/\pi D = \Delta D/D$.

The Poisson term matters: without it, $\varepsilon_{xx}$ would be $-1203\ \mu\varepsilon$, about 4× too large, because the hoop compression makes the hull try to *lengthen*.

### (iii) Is the thin-wall assumption valid?
**No.** $t/R = 0.14/1.1 = 0.127 > 0.1$. A thin acrylic wall would also be prone to **buckling** under external pressure. Thick-cylinder (Lamé) theory would be needed ([[Lame Thick-Cylinder Solution]]).

---

## Extra Q1: Spherical steel vessel with brittle paint ($D = 480$ mm, $t = 8$ mm, $E = 205$ GPa, $\nu = 0.30$); the paint cracks at 150 με
In a sphere, $\sigma_{xx} = \sigma_{yy} = pR/2t$ (equibiaxial). Then

$$
\varepsilon = \frac1E\left(\frac{pR}{2t}\right)(1-\nu)\;\Rightarrow\; p = \frac{2Et\,\varepsilon}{R(1-\nu)} = \frac{2(205\times10^9)(0.008)(150\times10^{-6})}{(0.24)(0.7)} = \mathbf{2.93}\ \text{MPa}\ ✔
$$

The $(1-\nu)$ factor shows the biaxial benefit: each direction's Poisson contraction partly cancels the other's stretch.

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 3
