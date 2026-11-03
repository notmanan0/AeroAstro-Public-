---
title: "Nernst Equation and Galvanic Series"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Nernst equation", "Galvanic series", "Standard electrode potential", "Concentration cell"]
tags: [sesa2028, materials, corrosion, electrochemistry]
status: lectured
parent: ["[[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]"]
related: ["[[Evans Diagram and Passivation]]", "[[Localised Corrosion]]", "[[Corrosion Protection]]"]
---

# Nernst Equation and Galvanic Series

Standard electrode potentials rank metals by how readily they dissolve, measured against the standard hydrogen electrode at 0 V, and the Nernst equation $E=E^0+(0.0592/n)\log_{10}C_{ion}$ corrects a potential for the ion concentration actually present at 25 °C.

In any pair of metals connected through an electrolyte, the one with the more negative potential is the anode and corrodes. Zinc ($-0.76$ V) against copper ($+0.34$ V) gives a cell of 1.10 V with zinc dissolving; the lecture writes it as "most negative minus least negative", $-1.10$ V, while the usual convention $E_{cathode}-E_{anode}=+1.10$ V gives a positive value for a spontaneous reaction, with $\Delta G=-nFE=-212$ kJ/mol. Standard potentials assume pure metals in 1 M solutions of their own ions. The galvanic series ranks real alloys in a real environment such as seawater, including passive stainless steel and titanium, and is the list to use when choosing metals to join.

![[materials_electrode_potentials.png|700]]

The Nernst equation comes from $\Delta G=\Delta G^0+RT\ln Q$ with $\Delta G=-nFE$; the coefficient $RT\ln10/F$ is 0.0592 V at 25 °C (the slide's 0.592 and minus sign are slips, explained in [[SESA2028 M3 - Corrosion, Wear and Surface Engineering#The Nernst equation and concentration cells|M3]]). Its importance is that concentration differences alone create potential differences, so one metal can corrode with no second metal present. In a concentration cell driven by oxygen, the well-aerated region becomes the cathode and the oxygen-starved region the anode. That explains the rust ring under a water drop on steel and the attack inside a crevice ([[Localised Corrosion]]).

## Related

- Topic: [[SESA2028 M3 - Corrosion, Wear and Surface Engineering|M3]]
- Concepts: [[Evans Diagram and Passivation]] · [[Localised Corrosion]] · [[Corrosion Protection]]
