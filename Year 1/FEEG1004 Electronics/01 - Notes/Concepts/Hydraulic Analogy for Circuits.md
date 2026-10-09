---
title: "Hydraulic Analogy for Circuits"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["hydraulic analogy", "water analogy", "pressure-voltage analogy"]
tags: [feeg1004, concept, analogy]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A4 - Capacitors]]", "[[FEEG1004 A5 - Inductors and Electrical Resonance]]"]
related_concepts: ["[[Capacitance]]", "[[Inductance]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf"]
---

# Hydraulic Analogy for Circuits

## Definition

> [!note] Definition
> | Electrical | Hydraulic |
> |---|---|
> | voltage | pressure |
> | current | volume flow rate |
> | resistance | pipe (laminar) resistance |
> | capacitance | elastic membrane (compliance) |
> | inductance | inertia of the fluid / a heavy water-wheel |
> | KCL, KVL | mass conservation, single-valued pressure |

## Explanation
- It works because the governing equations have the **same form**, and only in that sense. Other mappings are equally valid (e.g. the force–current analogy).
- It builds intuition for transients:
  - a membrane cannot fill instantly, so capacitor voltage is continuous;
  - a heavy wheel cannot change speed instantly, so inductor current is continuous.
- In the analogy, resonance is the wheel and membrane swapping energy.
- Tools transfer too: circuit analysis solves **laminar** pipe and microfluidic networks.

## Examples
- The capacitor–lamp question: at high frequency the membrane barely stretches before the flow reverses, so the lamp is bright.

## Related
- Topic notes: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Cross-module: laminar pipe flow, [[Major and Minor Head Losses]] · the mechanical analogy (mass ↔ L, spring ↔ 1/C) in [[FEEG1002 D6 - Single Degree of Freedom Vibration]]

## Sources
- Recorded lecture 3a (after hyperphysics); lectures 4 and 5a
