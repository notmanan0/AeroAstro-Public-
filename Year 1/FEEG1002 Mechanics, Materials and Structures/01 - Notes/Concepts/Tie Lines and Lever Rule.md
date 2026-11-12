---
title: "Tie Lines and Lever Rule"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["lever rule", "tie line", "isotherm", "phase compositions", "phase fractions", "mass fraction of a phase"]
tags: [feeg1002, concept, materials, phase-diagrams]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C6 - Phase Diagrams]]", "[[FEEG1002 C7 - Steels and Precipitation Hardening]]"]
related_concepts: ["[[Eutectic and Eutectoid Reactions]]", "[[Iron-Carbon Phase Diagram]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 08 - Phase Diagrams 1 - Solid Solubility.pdf"]
---

# Tie Lines and Lever Rule

In a two-phase field of a binary phase diagram, a tie line is the horizontal line (an isotherm) through the alloy's state point to the phase boundaries on either side; its end points give the compositions of the two phases, and the lever rule turns its segment lengths into the mass fractions of the two phases.

For an alloy of overall composition $C_0$ at a point in the $\alpha+L$ field, the liquid composition $C_L$ is read straight down from where the tie line meets the liquidus, and the solid composition $C_\alpha$ from where it meets the solidus. Mass conservation of the solute, $fC_\alpha+(1-f)C_L=C_0$ with $f$ the mass fraction of $\alpha$, rearranges to

$$
f_\alpha=\frac{C_0-C_L}{C_\alpha-C_L},\qquad f_L=1-f_\alpha=\frac{C_\alpha-C_0}{C_\alpha-C_L}
$$

The two segments are labelled $R=C_0-C_L$ and $S=C_\alpha-C_0$, so $f_\alpha=R/(R+S)$ and $f_L=S/(R+S)$. Each phase's fraction is the length of the segment on the opposite side of the point, divided by the whole tie line: the arm next to the liquidus measures the solid. A quick check is to follow the alloy down its cooling line: at the liquidus the arm next to it has zero length, and there is no solid yet.

![[m6_cu_ni_tie_line.png|900]]

For Cu–35 wt% Ni at 1250 °C the tie line runs from $C_L=32$ to $C_\alpha=43$ wt% Ni, so the alloy is $(35-32)/(43-32)=27.3$ % solid and 72.7 % liquid. The same construction works in every two-phase field: across $\alpha+\beta$ in a eutectic system, and across $\alpha+\mathrm{Fe_3C}$ in steel, where the proeutectoid and total amounts come from tie lines just above and just below the eutectoid temperature. Compositions and amounts are separate readings: end points give compositions, segment lengths give amounts.

## Related

- [[FEEG1002 C6 - Phase Diagrams#Tie lines give the compositions|tie lines]] · [[FEEG1002 C6 - Phase Diagrams#The lever rule gives the amounts|the lever rule]] · [[FEEG1002 C6 - Phase Diagrams#Primary and total amounts|primary and total amounts]] · [[FEEG1002 C6 - Phase Diagrams#Worked example - the lever rule in copper–nickel|copper–nickel example]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Amounts of each microconstituent|amounts in steels]]
- [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]
- [[Eutectic and Eutectoid Reactions]] · [[Iron-Carbon Phase Diagram]]
