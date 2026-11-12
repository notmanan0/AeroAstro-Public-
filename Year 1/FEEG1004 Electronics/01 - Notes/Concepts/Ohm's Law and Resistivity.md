---
title: "Ohm's Law and Resistivity"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["Ohm's law", "V = IR", "resistivity", "R = rho L / A"]
tags: [feeg1004, concept, dc-circuits, resistance]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
related_concepts: ["[[Kirchhoff's Current and Voltage Laws]]", "[[Series and Parallel Resistors]]", "[[Gauge Factor]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf", "Recorded lecture 3a", "Tutorial Sheet 1"]
---

# Ohm's Law and Resistivity

Ohm's law states that the voltage across a resistor is proportional to the current through it. The resistance of a uniform conductor is set by its **resistivity** $\rho$, its length $L$ and its cross-sectional area $A$, and the power it dissipates follows from both.

$$
V = IR,\qquad R = \frac{\rho L}{A},\qquad P = I^2R = \frac{V^2}{R}
$$

The voltage drops in the direction of the current, so the terminal where the current enters is the positive one. Resistance grows with length and falls with area. In metals it also rises with temperature (about +0.4 %/K for copper), whereas in semiconductors such as NTC thermistors it falls ([[RTDs and Thermistors]]). Stretching a wire raises $L$ and reduces $A$, so its resistance rises, which is the principle of the strain gauge ([[Gauge Factor]]).

In Tutorial 1 Q2(ii), a 2 m copper lead of 20 mΩ with $\rho = 1.678\times10^{-8}$ Ω m needs a diameter $d = 2\sqrt{\rho L/(\pi R)}$ = 1.46 mm. A battery whose terminal voltage droops from 13 V to 8 V at 200 A has an internal resistance (ESR) of $(13 - 8)/200$ = 25 mΩ. Ohm's law there uses the voltage across the resistor, not the source voltage.

## Related

- [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- [[Kirchhoff's Current and Voltage Laws]] · [[Series and Parallel Resistors]] · [[Complex Impedance]] (the AC generalisation)
- Sources: Recorded lecture 3a; Tutorial Sheet 1
