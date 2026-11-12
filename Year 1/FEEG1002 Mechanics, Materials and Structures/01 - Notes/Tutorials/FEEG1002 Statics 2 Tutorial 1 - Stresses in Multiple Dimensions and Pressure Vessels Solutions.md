---
title: "FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, pressure-vessels]
sheet: "Statics-2 Tutorial problem sheet 1"
theory_notes: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
key_concepts: ["[[Thin-Walled Pressure Vessels]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 01 - Stresses in Multiple Dimensions and Pressure Vessels.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 01 - Stresses in Multiple Dimensions and Pressure Vessels - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions

> [!abstract] Sheet info
> One question: a spherical vessel made of two bolted halves. Both answers match the official solutions (10.8 MPa and 222 MPa), checked numerically.

## Q1 Bolted spherical pressure vessel

*Taught in:* [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#Spherical vessels]] · worked in full at [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#Worked example - bolted spherical vessel]].

Data: diameter 400 mm ($R=0.2$ m), wall $t=6$ mm, allowable wall stress 180 MPa, 24 bolts of 18 mm diameter. Since $t/R=0.03<0.1$, the thin-wall model applies.

**Maximum working pressure.** In a thin sphere the wall stress is $pR/2t$ in every direction, so

$$
p_{max}=\frac{2t\sigma_{allow}}{R}=\frac{2(6\times10^{-3})(180\times10^6)}{0.2}=10.8\ \mathrm{MPa}
$$

**Bolt stress.** Take the upper hemisphere and the gas inside it as the free body, cut through the bolts. The pressure acts on the projected disc $\pi R^2$ and is resisted by the 24 bolts, the wall being assumed to carry nothing across the gasket:

$$
p\pi R^2=24F_{bolt}
$$

$$
F_{bolt}=\frac{(10.8\times10^6)\pi(0.2)^2}{24}=56.5\ \mathrm{kN}
$$

$$
\sigma_{bolt}=\frac{F_{bolt}}{\pi(0.009)^2}=222\ \mathrm{MPa}
$$

This excludes any preload used to compress the gasket, as the question says.

The bolts are more highly stressed than the 180 MPa allowed in the wall, so they would be a higher-strength grade, or larger or more numerous. Their preload must also exceed the total separating force, $p\pi R^2=1357$ kN, or the joint opens and leaks.

## Sources

- `Tutorial Sheet 01 - Stresses in Multiple Dimensions and Pressure Vessels.pdf` and its solutions.
