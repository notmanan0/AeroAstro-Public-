---
title: "Iron-Carbon Phase Diagram"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["Fe–Fe3C diagram", "iron–iron carbide diagram", "austenite", "ferrite", "cementite", "pearlite", "proeutectoid ferrite", "proeutectoid cementite", "eutectoid steel"]
tags: [feeg1002, concept, materials, steels, phase-diagrams]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C7 - Steels and Precipitation Hardening]]"]
related_concepts: ["[[Eutectic and Eutectoid Reactions]]", "[[Tie Lines and Lever Rule]]", "[[Crystal Structures and Atomic Packing Factor]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 10 - Steels.pdf"]
---

# Iron-Carbon Phase Diagram

The iron–iron carbide (Fe–Fe₃C) diagram is the phase diagram used to read the microstructure of a plain-carbon steel from its carbon content and temperature; its key feature is the eutectoid at 0.76 wt% C and 727 °C, where austenite turns into pearlite.

Three phases matter. Austenite, γ, is FCC iron with interstitial carbon, stable at high temperature and able to hold up to 2.14 wt% C. Ferrite, α, is BCC iron that can hold at most 0.022 wt% C, so it is nearly pure, soft and ductile. Cementite, Fe₃C, is a hard, brittle compound of fixed composition, 6.7 wt% C, which forms to take up carbon the iron cannot hold. Pearlite is not a phase but a microconstituent: alternating plates of ferrite and cementite made by the eutectoid reaction.

$$
\gamma(0.76\ \text{wt\% C})\ \xrightarrow{\text{cooling, }727\,^\circ\text{C}}\ \alpha(0.022\ \text{wt\% C})+\mathrm{Fe_3C}(6.7\ \text{wt\% C})
$$

The reaction happens because FCC austenite can dissolve far more carbon than BCC ferrite, so when the iron changes structure the surplus carbon has to go into cementite. The diagram also has a eutectic at 4.30 wt% C and 1147 °C, which matters for cast irons rather than steels.

![[m7_fe_fe3c.png|900]]

Steels below 0.76 wt% C are hypoeutectoid: on slow cooling, proeutectoid ferrite forms first on the austenite grain boundaries, and the remaining austenite turns to pearlite at 727 °C. Steels above it are hypereutectoid, with proeutectoid cementite along the prior grain boundaries instead. The lever rule gives the amounts just above 727 °C,

$$
f_{\alpha,pro}=\frac{0.76-C_0}{0.76-0.022},\qquad f_{Fe_3C,pro}=\frac{C_0-0.76}{6.7-0.76}
$$

with pearlite the remainder, and the total ferrite and cementite just below 727 °C from the tie line from 0.022 to 6.7 wt% C. More carbon means more pearlite (up to the eutectoid) and more ferrite–cementite boundary to block dislocations, so strength and hardness rise and ductility falls: low-carbon steels for wire and nails, medium-carbon for rails and shafts, high-carbon for tools.

## Related

- [[FEEG1002 C7 - Steels and Precipitation Hardening#1. The phases of steel|the phases of steel]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#2. The iron–iron carbide diagram|the Fe–Fe₃C diagram]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#The eutectoid reaction|the eutectoid reaction]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Hypoeutectoid steel|hypoeutectoid steel]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Hypereutectoid steel|hypereutectoid steel]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Amounts of each microconstituent|amounts]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#4. Carbon content and properties|carbon content and properties]]
- [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q3 - Steels|Tutorial 3, Q3]]
- [[Eutectic and Eutectoid Reactions]] · [[Tie Lines and Lever Rule]] · [[Crystal Structures and Atomic Packing Factor]] · [[Ductile-to-Brittle Transition]]
- Year 2: [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]
