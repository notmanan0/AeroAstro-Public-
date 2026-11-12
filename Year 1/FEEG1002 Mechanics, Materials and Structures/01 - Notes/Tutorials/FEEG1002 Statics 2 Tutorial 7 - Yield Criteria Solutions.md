---
title: "FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, von-mises, tresca, torsion]
sheet: "Statics-2 Tutorial problem sheet 7"
theory_notes: ["[[FEEG1002 B6 - Yield Criteria]]", "[[FEEG1002 A8 - Torsion of Circular Shafts]]"]
key_concepts: ["[[Von Mises Yield Criterion]]", "[[Tresca Yield Criterion]]", "[[Torsion of Circular Shafts]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 07 - Yield Criteria.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 07 - Yield Criteria - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions

> [!abstract] Sheet info
> Combined axial compression and torsion checked with von Mises. The answer matches the official solution ($T=817.5$ N m), checked numerically; the Tresca result and the full interaction curve are added.

## Q1 Shaft under axial load and torque

*Taught in:* [[FEEG1002 B6 - Yield Criteria#Plane stress in xy components]] and [[FEEG1002 A8 - Torsion of Circular Shafts]] · worked in full at [[FEEG1002 B6 - Yield Criteria#Worked example - shaft under axial load and torque]].

Data: diameter 36 mm ($R=18$ mm), $\sigma_Y=250$ MPa ($E=200$ GPa and $\nu=0.3$ are not needed), axial compressive load $F=200$ kN.

**Stress state on the surface.** Take $x$ round the circumference and $y$ along the shaft, as in the official solution:

$$
\sigma_{yy}=\frac FA=\frac{-200\times10^3}{\tfrac\pi4(0.036)^2}=-196.5\ \mathrm{MPa}
$$

uniform over the section, and the torsional shear stress is largest at the surface:

$$
\sigma_{xy}=\frac{TR}{J}=\frac{TR}{\tfrac\pi2R^4}=\frac{2T}{\pi R^3}
$$

with $\sigma_{xx}=0$ and no radial stress on the free surface.

**Von Mises.** The plane-stress equivalent stress reduces to

$$
\sigma_{eq}=\sqrt{\sigma_{yy}^2+3\sigma_{xy}^2}=\sigma_Y
$$

$$
\sigma_{xy}=\sqrt{\frac{\sigma_Y^2-\sigma_{yy}^2}{3}}=89.2\ \mathrm{MPa}
$$

$$
T=\frac{\pi R^3}{2}\sqrt{\frac{\sigma_Y^2-\sigma_{yy}^2}{3}}=\frac{\pi(0.018)^3}{2}\sqrt{\frac{(250\times10^6)^2-(196.5\times10^6)^2}{3}}=817.5\ \mathrm{N\,m}
$$

**Tresca, for comparison (added).** The principal stresses have opposite signs, so Tresca uses the in-plane term $|\sigma_I-\sigma_{II}|=2R=\sqrt{\sigma_{yy}^2+4\sigma_{xy}^2}=\sigma_Y$, giving $\sigma_{xy}=77.3$ MPa and $T=708$ N m, 13 % lower and so more conservative.

**Without the axial load**, von Mises allows $T=\pi R^3\sigma_Y/(2\sqrt3)=1322$ N m. The compression uses $(196.5/250)^2=62$ % of $\sigma_Y^2$, so the torque capacity falls by 38 %.

![[s2_t7_torsion_axial_envelope.png|850]]

Because $\sigma_{yy}$ enters squared, 200 kN of tension would give the same torque limit; in compression buckling must also be checked ([[FEEG1002 A7 - Euler Buckling of Struts]]).

## Sources

- `Tutorial Sheet 07 - Yield Criteria.pdf` and its solutions.
