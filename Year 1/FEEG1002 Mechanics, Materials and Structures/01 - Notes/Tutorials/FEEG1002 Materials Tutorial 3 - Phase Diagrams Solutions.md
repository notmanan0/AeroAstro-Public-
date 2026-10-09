---
title: "FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, phase-diagrams, steel, precipitation]
sheet: "Materials Tutorial Sheet 3"
theory_notes: ["[[FEEG1002 C6 - Phase Diagrams]]", "[[FEEG1002 C7 - Steels and Precipitation Hardening]]"]
key_concepts: ["[[Tie Lines and Lever Rule]]", "[[Eutectic and Eutectoid Reactions]]", "[[Iron-Carbon Phase Diagram]]", "[[Precipitation Hardening]]"]
status: complete
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 03 - Phase Diagrams.pdf"]
---

# FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions

> [!abstract] Sheet Info
> Four multi-part questions on Ag-Cu and Al-Cu eutectics, steel microstructures and precipitation hardening. Diagram readings are approximate; lever-rule arithmetic is explicit.

## Theory Links
- [[FEEG1002 C6 - Phase Diagrams]] · [[FEEG1002 C7 - Steels and Precipitation Hardening]]

---

## Q1: Ag-Cu, 20 wt% Ag (Cu-rich hypoeutectic)
### (a) Solidification range
The vertical 20 wt% Ag line crosses the liquidus at about **1000°C**. Remaining liquid reaches the eutectic at 779°C, so solidification occurs over approximately
$$\boxed{1000^\circ\text C\ \text{to}\ 779^\circ\text C}$$

### (b) Primary $\alpha$ composition
- at first solid formation (tie line at the liquidus crossing): approximately **5 wt% Ag**;
- just before the eutectic reaction: $C_{\alpha E}=\boxed{8.0\ \text{wt\% Ag}}$.

### (c) Amount of primary $\alpha$
Immediately above 779°C, $C_L=C_E=71.9$ and $C_\alpha=8.0$ wt% Ag:
$$f_{primary\ \alpha}=\frac{C_L-C_0}{C_L-C_\alpha}=\frac{71.9-20}{71.9-8.0}=\boxed{0.812\ (81.2\%)}$$
The remaining 18.8% liquid becomes eutectic $\alpha+\beta$.

## Q2: Al-Cu, 20 wt% Cu hypoeutectic alloy
### (a) First $\alpha$
The 20 wt% Cu line meets the liquidus at about $\boxed{600^\circ\text C}$.

### (b) Liquid composition at first solid
At the instant solid first appears, essentially all material is liquid, so $\boxed{C_L=20\ \text{wt\% Cu}}$.

### (c) Liquid at the eutectic
The liquid follows the liquidus to $\boxed{C_E\approx33\ \text{wt\% Cu}}$ at about 548°C.

### (d) Microstructure at 500°C
Primary $\alpha$ (Al-rich) dendrites surrounded by interdendritic eutectic $\alpha+\theta$ lamellae, where $\theta=CuAl_2$. It is not 100% eutectic because $C_0<C_E$.

## Q3: Steels
### (a) Phase versus microconstituent
A **phase** is chemically/structurally homogeneous. A **microconstituent** is a recognisable morphology and may contain multiple phases; pearlite is lamellar $\alpha+Fe_3C$.

### (b) Hypo- versus hypereutectoid
- hypoeutectoid: $C_0<0.76$ wt% C $\rightarrow$ proeutectoid ferrite + pearlite;
- hypereutectoid: $C_0>0.76$ wt% C $\rightarrow$ proeutectoid cementite + pearlite.

### (c) Eutectoid and proeutectoid ferrite
- Proeutectoid ferrite forms from austenite **above** 727°C, commonly on prior-austenite boundaries.
- Eutectoid ferrite forms **inside pearlite** at 727°C alongside cementite.
- Both are the same $\alpha$ phase and have $\boxed{C_\alpha\approx0.022\ \text{wt\% C}}$ at 727°C.

### (d) 0.35 wt% C: proeutectoid ferrite and pearlite
At 727°C:
$$f_{proeutectoid\ \alpha}=\frac{0.76-0.35}{0.76-0.022}=\boxed{0.556}$$
$$f_P=\frac{0.35-0.022}{0.76-0.022}=\boxed{0.444}$$

### (e) 0.35 wt% C at 500°C: total phases
With $C_\alpha=0.015$ and $C_{Fe_3C}=6.70$ wt% C:
$$f_\alpha=\frac{6.70-0.35}{6.70-0.015}=\boxed{0.950}$$
$$f_{Fe_3C}=\frac{0.35-0.015}{6.70-0.015}=\boxed{0.0501}$$

These are total phase fractions; ferrite exists both proeutectoid and inside pearlite.

### (f) 1.3 wt% C at 600°C
Hypereutectoid structure: pearlite colonies plus a proeutectoid cementite network at prior-austenite boundaries. Fractions at the eutectoid are approximately
$$f_{proeutectoid\ Fe_3C}=\frac{1.3-0.76}{6.70-0.76}=\boxed{9.1\%},\qquad f_P=90.9\%$$

## Q4: Precipitation hardening
### (a) Composition choice
Choose an $\alpha$-rich composition near the right-hand side (roughly a few wt% A) whose vertical line lies:
- inside single-$\alpha$ at a high solution-treatment temperature;
- inside $\alpha+\theta$ at the lower ageing temperature;
- below the solidus during treatment.

This permits dissolution, quench supersaturation and subsequent precipitation.

### (b) Why peak strength at intermediate time?
- under-aged: particles are too small/sparse and can be sheared;
- peak-aged: best combination of number density, size, coherency and small spacing;
- over-aged: coarsening reduces number density, increases spacing and often loses coherency, so bypass becomes easier.

![[m7_ageing_curve.png|720]]

## Sources
- Materials Tutorial Sheet 3; phase-diagram values read directly from the supplied figures.
