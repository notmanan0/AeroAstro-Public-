---
title: "Kirchhoff's Current and Voltage Laws"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["KCL", "KVL", "Kirchhoff's laws", "Kirchoff"]
tags: [feeg1004, concept, dc-circuits, ac-circuits]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A6 - Mesh Analysis]]"]
related_concepts: ["[[Ohm's Law and Resistivity]]", "[[Mesh Current Method]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# Kirchhoff's Current and Voltage Laws

## Definition

> [!note] Definition
> - **KCL**: $\sum_k i_k = 0$ at any node (charge conservation).
> - **KVL**: $\sum_k v_k = 0$ around any closed loop (energy conservation).
>
> Both hold at every instant and, in AC, for **phasors**.

## Explanation
- KCL is the "what goes in comes out" rule. In the hydraulic analogy it is conservation of water.
- KVL is the "walk round and return to the same height" rule.
- Sign discipline: choose a current direction and loop direction, add rises and subtract drops. A negative answer only means the current flows the other way.
- They hold for lumped circuits (negligible radiation). At very high frequency you need Maxwell's equations.

## Examples
- Tutorial 1 Q2(iv): KVL round two batteries and three resistances gives $I$ = −40 A, so the current flows from the 13 V battery into Sam's.
- Tutorial 1 Q4: derive series and parallel resistance from Ohm + KCL + KVL.

## Related
- Topic notes: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- Concepts: [[Mesh Current Method]] · [[Series and Parallel Resistors]] · [[Phasor Representation]]

## Sources
- Recorded lectures 3a–3b; Niu AC notes (Figures 4–5)
