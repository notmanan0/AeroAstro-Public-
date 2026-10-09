---
title: "FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, von-mises, torsion]
sheet: "Statics-2 Tutorial problem sheet 7"
theory_notes: ["[[FEEG1002 B6 - Yield Criteria]]", "[[FEEG1002 A8 - Torsion of Circular Shafts]]"]
key_concepts: ["[[Von Mises and Tresca Yield Criteria]]", "[[Torsion of Circular Shafts]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 07 - Yield Criteria.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 07 - Yield Criteria - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions

> [!abstract] Sheet Info
> Combined axial load and torsion checked with von Mises. The answer is reproduced ✔ ($T = 817.5$ N m). The Tresca result and the full interaction envelope are added.

## Theory Links
- [[FEEG1002 B6 - Yield Criteria]] · [[FEEG1002 A8 - Torsion of Circular Shafts]] · [[Von Mises and Tresca Yield Criteria]]

---

## Q1: Ø36 mm steel shaft, $\sigma_Y = 250$ MPa, axial compression $F = 200$ kN. Find the torque at first yield.
**Stress state on the surface** ($x$ circumferential, $y$ axial):
- axial load: $\sigma_{yy} = \dfrac{F}{A} = \dfrac{-200\times10^3}{\tfrac\pi4(0.036)^2} = -196.5$ MPa, uniform over the section;
- torque: $\sigma_{xy} = \dfrac{TR}{J} = \dfrac{2T}{\pi R^3}$, maximum on the **outer surface**;
- $\sigma_{xx} = 0$, and there is no radial stress on a free surface.

**von Mises**:

$$
\sigma_{eq} = \sqrt{\sigma_{yy}^2 + 3\sigma_{xy}^2} = \sigma_Y\;\Rightarrow\;\sigma_{xy} = \sqrt{\frac{\sigma_Y^2 - \sigma_{yy}^2}{3}}
$$

$$
T = \frac{\pi R^3}{2}\sqrt{\frac{\sigma_Y^2 - \sigma_{yy}^2}{3}} = \frac{\pi(0.018)^3}{2}\sqrt{\frac{(250\times10^6)^2 - (196.5\times10^6)^2}{3}} = \mathbf{817.5}\ \text{N m}\ ✔
$$

**Tresca, for comparison**: $\sigma_{eq,T} = \sqrt{\sigma^2 + 4\tau^2}$ gives $T = 708$ N m, about 13% lower, i.e. more conservative.

**Without the axial load**, von Mises allows $T = 1321$ N m. The compression uses up $(196.5/250)^2 = 62\%$ of the "yield budget", so the torque capacity drops by 38%.

![[s2_t7_torsion_axial_envelope.png|700]]

> [!tip] Sign of the axial load does not matter
> $\sigma_{yy}$ enters squared, so 200 kN of tension would give the same torque limit. Buckling would still have to be checked separately for the compressive case ([[FEEG1002 A7 - Euler Buckling of Struts]]).

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 7
