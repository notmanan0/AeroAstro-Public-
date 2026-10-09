---
title: "FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, revision, rosettes, von-mises, thermal-strain, mohrs-circle]
sheet: "Statics-2 Tutorial problem sheet 8 (revision)"
theory_notes: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]", "[[FEEG1002 B6 - Yield Criteria]]"]
key_concepts: ["[[Strain Gauge Rosettes]]", "[[Generalised Hooke's Law]]", "[[Von Mises and Tresca Yield Criteria]]", "[[Mohr's Circle]]", "[[Thermal Strain]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions

> [!abstract] Sheet Info
> Four exam-style questions that chain every Statics 2 topic together: rosette → Hooke → von Mises → safety factor; constrained thermal strain; a pressure vessel → yield → strain Mohr's circle; stress Mohr's circle. All answers are reproduced ✔.

## Theory Links
- [[FEEG1002 B3 - Generalised Hooke's Law]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]] · [[FEEG1002 B6 - Yield Criteria]]

---

## Q1: 60 000 t hydraulic press, 0/60/120° rosette ($E = 207$ GPa, $\nu = 0.3$, $\sigma_Y = 355$ MPa, load 450 MN); readings 800, 300, 500 με
**(a) Strains** (delta-rosette formulas):

$$
\varepsilon_{xx} = 800,\qquad \varepsilon_{yy} = \frac{2(300+500) - 800}{3} = \mathbf{267},\qquad \varepsilon_{xy} = \frac{300-500}{\sqrt3} = \mathbf{-115}\ \mu\varepsilon
$$

**(b) Stresses** (plane stress):

$$
\sigma_{xx} = \frac{E}{1-\nu^2}(\varepsilon_{xx} + \nu\varepsilon_{yy}) = \mathbf{200}\ \text{MPa},\quad \sigma_{yy} = \frac{E}{1-\nu^2}(\varepsilon_{yy} + \nu\varepsilon_{xx}) = \mathbf{115}\ \text{MPa},\quad \sigma_{xy} = \frac{E}{1+\nu}\varepsilon_{xy} = \mathbf{-18.4}\ \text{MPa}
$$

**(c) Maximum load**:

$$
\sigma_{eq} = \sqrt{200^2 + 115^2 - 200(115) + 3(18.4)^2} = 177\ \text{MPa},\qquad SF = \frac{355}{177} = 2.0
$$

$$
F_{max} = SF\times450\ \text{MN} = \mathbf{9.0\times10^8}\ \text{N}\ ✔
$$

This relies on linearity: stress is proportional to load up to first yield.

## Q2: Microchip on a rigid board ($E = 140$ GPa, $\nu = 0.265$, $\alpha = 2.59\times10^{-6}$/K, $d = 15$ mm, $t = 2$ mm, 12 joints per side, $\Delta T = +30$ °C)
Fully restrained **in plane** in both directions:

$$\varepsilon_{total} = \varepsilon_M + \alpha\Delta T = 0\;\Rightarrow\;\varepsilon_{xx} = \varepsilon_{yy} = -\alpha\Delta T$$

Equibiaxial plane stress:

$$
\sigma_{xx} = \frac{E}{1-\nu^2}(\varepsilon_{xx} + \nu\varepsilon_{yy}) = -\frac{E\alpha\Delta T}{1-\nu} = \mathbf{-14.8}\ \text{MPa}
$$

- Force per side: $F = |\sigma|td = 444$ N.
- Per solder joint: $444/12 = \mathbf{37}$ **N** ✔

Note $1/(1-\nu)$ rather than 1: biaxial restraint gives a **larger** stress than uniaxial, because Poisson contraction cannot relieve it.

## Q3: LH₂ tank, thin cylinder with $L = 2.5$ m, $R = 0.35$ m
**(i) Allowable pressure** for $t = 1.5$ mm, $\sigma_Y = 440$ MPa, SF = 3. With $\sigma_{xx} = pR/2t$, $\sigma_{yy} = pR/t$ and no shear:

$$
\sigma_{eq} = \frac{pR}{t}\sqrt{\tfrac14 + 1 - \tfrac12} = \frac{pR}{t}\sqrt{\tfrac34}\;\Rightarrow\; p = \frac{2\sigma_Yt}{SF\sqrt3R} = \mathbf{7.26\times10^5}\ \text{Pa}\ (7.26\ \text{bar})\ ✔
$$

**(ii) Strains** ($E = 120$ GPa, $\nu = 0.33$): $\sigma_{xx} = 84.7$ MPa and $\sigma_{yy} = 169$ MPa, so

$$
\varepsilon_{xx} = \frac1E(\sigma_{xx} - \nu\sigma_{yy}) = \mathbf{240}\ \mu\varepsilon,\qquad \varepsilon_{yy} = \frac1E(\sigma_{yy} - \nu\sigma_{xx}) = \mathbf{1178}\ \mu\varepsilon
$$

**(iii) Mohr's circle for strain.** There is no shear in $xy$, so these are the principal strains, $\varepsilon_I = 1178$ and $\varepsilon_{II} = 240$ με.
- Centre: 709 με.
- Radius: $|\varepsilon_{x'y'}|^{max} = (\varepsilon_I - \varepsilon_{II})/2 = \mathbf{469}\ \mu\varepsilon$, at ±45°.

**(iv) Add torsion.** This adds $\varepsilon_{xy}\neq0$. The centre stays at 709 με but the radius grows, so $\varepsilon_I$ **increases**, $\varepsilon_{II}$ **decreases**, and the principal directions rotate away from the axes.

![[s2_strain_mohr_t8_q3.png|660]]

## Q4: $\sigma_{xx} = 10$, $\sigma_{yy} = 50$ MPa, shear 15 MPa
**(a)** Shear arrows on the $+x$ face point **down**, so $\sigma_{xy} = \mathbf{-15}$ **MPa**. The centre is 30 MPa and the $x$-face point is $(10, -15)$, above the axis.

**(b)** $R = \sqrt{(-20)^2 + 15^2} = \mathbf{25}$ **MPa** = maximum in-plane shear. So $\sigma_I = \mathbf{55}$ and $\sigma_{II} = \mathbf{5}$ **MPa** ✔

**(c)** On the maximum-shear planes both normal stresses equal $\sigma_{avg} = \mathbf{30}$ **MPa**.

**(d)** From the $x$-face point to $\sigma_I$:
- $\beta = \tan^{-1}\dfrac{2(15)}{|10-50|} = 36.87^\circ$, so $|2\theta| = 180^\circ - 36.87^\circ = 143.1^\circ$ and $|\theta| = 71.6^\circ$.
- The rotation is **clockwise**: $\theta_p = -71.6^\circ$.

**(e)** In the principal element, $x'$ at $-71.6^\circ$ carries 55 MPa and $y'$ carries 5 MPa, with no shear.

![[s2_mohr_t8_q4.png|940]]

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 8 (revision problems)
