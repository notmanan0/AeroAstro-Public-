---
title: "Potential Divider"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["voltage divider", "potential divider equation"]
tags: [feeg1004, concept, dc-circuits, sensors]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
related_concepts: ["[[Current Divider]]", "[[Loading Effect and Buffering]]", "[[Potentiometric Displacement Sensor]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf", "Recorded lecture 3b"]
---

# Potential Divider

A potential divider is two resistors in series across a supply $V_{in}$, with the output taken across one of them. With the output across $R_1$,

$$
V_{out} = V_{in}\frac{R_1}{R_1 + R_2}
$$

which is valid only when negligible current is drawn from the output node.

The result follows from one KVL loop: the series current is $i = V_{in}/(R_1 + R_2)$ and $V_{out} = iR_1$. A load $R_L$ on the output sits in parallel with $R_1$ and pulls $V_{out}$ down ([[Loading Effect and Buffering]]); an op-amp voltage follower between divider and load removes the problem. In AC circuits the same result holds with impedances, $V_{out} = V_{in}Z_1/(Z_1 + Z_2)$, so every RC filter is a complex potential divider ([[RC Low-Pass and High-Pass Filters]]). A resistive sensor placed in a divider gives an output voltage that is **non-linear** in the sensor's resistance.

An NTC thermistor divider feeding a comparator switches at 40 °C only if the reference divider has the same ratio, so with $R_{40}$ = 5 kΩ the reference needs $R$ = 2.5 kΩ (Week 9). Dividers also appear on both sides of an amplifier: a 4 V input halved to 2 V, amplified ×3 to 6 V and halved again gives 3 V.

![[ee_a3_divider_circuits.png|700]]

## Related

- [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- [[Current Divider]] · [[Potentiometric Displacement Sensor]] · [[Loading Effect and Buffering]] · [[RC Low-Pass and High-Pass Filters]]
- Sources: Recorded lecture 3b
