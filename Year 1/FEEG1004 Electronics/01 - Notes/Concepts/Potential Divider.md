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
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf"]
---

# Potential Divider

## Definition

> [!note] Definition
> For two resistors in series across $V_{in}$, with the output taken across $R_1$:
>
> $$V_{out} = V_{in}\frac{R_1}{R_1 + R_2}$$
>
> It is valid only when **negligible current** is drawn from the output node.

## Explanation
- It follows from one KVL loop: $i = V_{in}/(R_1 + R_2)$ and $V_{out} = iR_1$.
- A load $R_L$ on the output sits in parallel with $R_1$ and pulls $V_{out}$ down ([[Loading Effect and Buffering]]). An op-amp follower removes the problem.
- In AC use impedances: $V_{out} = V_{in}Z_1/(Z_1 + Z_2)$. **Every RC filter is a complex potential divider** ([[RC Low-Pass and High-Pass Filters]]).
- Sensor use: a resistive sensor in a divider gives a voltage that is **non-linear** in its resistance.

## Examples
- An NTC thermistor divider feeding a comparator: switching at 40 °C needs the reference divider ratio to match ($R$ = 2.5 kΩ for $R_{40}$ = 5 kΩ, W9).
- Op-amp worked example 2: a 4 V input halved to 2 V, amplified ×3, then halved to 3 V.

![[ee_a3_divider_circuits.png|700]]

## Related
- Topic notes: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Current Divider]] · [[Potentiometric Displacement Sensor]] · [[Loading Effect and Buffering]]

## Sources
- Recorded lecture 3b
