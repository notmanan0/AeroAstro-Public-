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

> [!abstract] Sheet Info
> One question: a bolted spherical pressure vessel. Answers reproduced ✔ ($p = 10.8$ MPa, $\sigma_{bolt} = 222$ MPa).

## Theory Links
- [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]] · [[Thin-Walled Pressure Vessels]]

---

## Q1: Two hemispheres bolted by 24 × Ø18 mm bolts; $D = 400$ mm, $t = 6$ mm, $\sigma_{allow} = 180$ MPa
**Maximum working pressure.** In a thin sphere the wall stress is equal in every direction:

$$
\sigma_{wall} = \frac{pR}{2t}\;\Rightarrow\; p = \frac{2t\sigma_{wall}}{R} = \frac{2(6\times10^{-3})(180\times10^6)}{0.2} = \mathbf{10.8}\ \text{MPa}\ ✔
$$

$t/R = 0.03 < 0.1$, so the thin-wall assumption is fine.

**Bolt stress.** Take a free body of the upper hemisphere **plus the gas inside it**. The pressure acts on the projected disc $\pi R^2$ and is resisted by the 24 bolts. The wall is assumed to carry nothing across the gasket joint.

$$
p\pi R^2 = 24F_{bolt}\;\Rightarrow\; F_{bolt} = \frac{(10.8\times10^6)\pi(0.2)^2}{24} = 56.5\ \text{kN}
$$

$$
\sigma_{bolt} = \frac{F_{bolt}}{\pi(0.009)^2} = \mathbf{222}\ \text{MPa}\ ✔
$$

This ignores any extra preload used to compress the gasket.

> [!tip] Bolts vs wall
> The bolts carry 222 MPa, **higher** than the 180 MPa wall allowable. In a real design the bolts would be a higher-strength grade, or larger or more numerous. The joint, not the shell, is often the weak point. Bolt preload also has to exceed the separating force, or the joint gapes and leaks.

![[s2_pressure_vessel_stresses.png|860]]

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 1
