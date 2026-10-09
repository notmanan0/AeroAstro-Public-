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
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf"]
---

# Ohm's Law and Resistivity

## Definition

> [!note] Definition
>
> $$V = IR,\qquad R = \frac{\rho L}{A},\qquad P = I^2R = \frac{V^2}{R}$$

## Explanation
- The voltage drops **in the direction of current**: the terminal where the current enters is +.
- Resistance grows with length, falls with area and rises with temperature for metals (Cu ≈ +0.4 %/K).
- Semiconductors (NTC thermistors) fall with temperature ([[RTDs and Thermistors]]).
- Stretching a wire raises $L$ and cuts $A$: the **strain gauge** principle ([[Gauge Factor]]).

## Examples
- Tutorial 1 Q2(ii): a 2 m copper lead of 20 mΩ ($\rho = 1.678\times10^{-8}$ Ω m) has $d = 2\sqrt{\rho L/\pi R}$ = 1.46 mm.
- Battery ESR from a droop: $(13 - 8)/200$ = 25 mΩ. Use the voltage *across the resistor*, not the source voltage.

## Related
- Topic notes: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- Concepts: [[Kirchhoff's Current and Voltage Laws]] · [[Complex Impedance]] (the AC generalisation)

## Sources
- Recorded lecture 3a; Tutorial Sheet 1
