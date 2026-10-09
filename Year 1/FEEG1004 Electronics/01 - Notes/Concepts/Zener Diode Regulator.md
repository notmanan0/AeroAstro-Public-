---
title: "Zener Diode Regulator"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["zener diode", "shunt regulator", "voltage regulator", "breakdown voltage"]
tags: [feeg1004, concept, diode, regulation]
status: complete
parent_lectures: ["[[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]"]
related_concepts: ["[[P-N Junction Diode]]", "[[Rectification and Smoothing]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf"]
---

# Zener Diode Regulator

## Definition

> [!note] Definition
> A heavily doped diode designed to break down at a precise reverse voltage $V_Z$. Placed across the load with a series resistor:
> $$R_S = \frac{V_{in} - V_Z}{I_L + I_Z},\qquad V_{out} = V_Z\ \text{while } I_Z > 0$$

## Explanation
- In breakdown the V–I curve is almost vertical: the voltage is fixed while the current varies.
- **Feedback action**: a rising $V_{out}$ increases $I_Z$, which increases the drop across $R_S$ and pulls $V_{out}$ back.
- Regulation fails when the load demands more than $(V_{in} - V_Z)/R_S$: the Zener current reaches zero.
- It wastes power at light load. The rating must cover the no-load Zener current.

![[ee_b2_zener_regulator.png|700]]

## Examples
- W7: 10 V, 50 Ω, 6 V Zener: 80 mA through the Zener at no load, 0.8 W total, and at most 80 mA available to a load.

## Related
- Topic notes: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Cross-module: shunt regulation of solar-array power, [[SESA2024 08 - Electrical Power Subsystem]]

## Sources
- Mills notes §1.5.4–1.5.5; Week 7 interactive session
