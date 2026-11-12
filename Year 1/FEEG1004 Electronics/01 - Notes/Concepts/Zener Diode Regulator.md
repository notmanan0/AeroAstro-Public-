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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §1.5.4–1.5.5", "02 - Sources/S1 Electronics/S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf"]
---

# Zener Diode Regulator

A Zener diode is a heavily doped diode designed to break down at a precise reverse voltage $V_Z$; placed across a load and fed through a series resistor $R_S$, it forms a shunt regulator. The resistor is sized from

$$
R_S = \frac{V_{in} - V_Z}{I_L + I_Z},\qquad V_{out} = V_Z\ \text{while } I_Z > 0
$$

In breakdown the diode's V–I curve is almost vertical, so its voltage stays fixed while its current varies. The regulator works by feedback: a rising $V_{out}$ increases $I_Z$, which increases the drop across $R_S$ and pulls $V_{out}$ back down.

Regulation fails when the load demands more than $(V_{in} - V_Z)/R_S$, because the Zener current has then fallen to zero. At light load the circuit wastes power, since all the current not taken by the load flows through the Zener, whose rating must cover the no-load current. With a 10 V supply, a 50 Ω resistor and a 6 V Zener (Week 7), 80 mA flows through the Zener at no load, the circuit draws 0.8 W in total, and at most 80 mA is available to a load.

![[ee_b2_zener_regulator.png|700]]

## Related

- [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- [[P-N Junction Diode]] · [[Rectification and Smoothing]]
- Cross-module: shunt regulation of solar-array power, [[SESA2024 08 - Electrical Power Subsystem]]
- Sources: Mills notes §1.5.4–1.5.5; Week 7 interactive session
