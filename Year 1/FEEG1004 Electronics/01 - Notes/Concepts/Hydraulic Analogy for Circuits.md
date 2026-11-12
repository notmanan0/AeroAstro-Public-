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

The hydraulic analogy maps an electrical circuit onto a network of water pipes, with voltage corresponding to pressure and current to volume flow rate. It holds because the governing equations of the two systems have the same form.

| Electrical | Hydraulic |
|---|---|
| voltage | pressure |
| current | volume flow rate |
| resistance | pipe (laminar) resistance |
| capacitance | elastic membrane (compliance) |
| inductance | inertia of the fluid / a heavy water-wheel |
| KCL, KVL | mass conservation, single-valued pressure |

The analogy is valid only in that formal sense, and other mappings work equally well, such as the force–current analogy for mechanical systems. Its value is the intuition it gives for transients. A membrane cannot stretch instantly, so the pressure across it cannot jump, which is why capacitor voltage is continuous. A heavy water-wheel cannot change speed instantly, which is why inductor current is continuous. Resonance in an LC circuit is the wheel and the membrane passing energy back and forth.

The same picture explains the capacitor–lamp question: at high frequency the flow reverses before the membrane has stretched much, so it barely resists the flow and the lamp is bright.

The correspondence also works in the other direction. Circuit analysis tools solve laminar pipe networks and microfluidic networks directly.

## Related

- [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Cross-module: laminar pipe flow, [[Major and Minor Head Losses]] · the mechanical analogy (mass ↔ L, spring ↔ 1/C) in [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
- Sources: Recorded lecture 3a (after hyperphysics); lectures 4 and 5a
