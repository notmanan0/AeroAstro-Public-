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

Kirchhoff's current law (KCL) states that the currents into any node sum to zero, which is conservation of charge. Kirchhoff's voltage law (KVL) states that the voltages around any closed loop sum to zero, which is conservation of energy.

$$
\text{KCL: }\sum_k i_k = 0\ \text{at a node},\qquad \text{KVL: }\sum_k v_k = 0\ \text{around a loop}
$$

Both laws hold at every instant, and in AC analysis they hold for phasors as well. KCL says that whatever current flows into a node must flow out again; in the hydraulic analogy it is conservation of water. KVL says that walking round any loop and back to the start returns you to the same potential, just as a closed walk on a hillside returns to the same height.

Using them reliably needs sign discipline. Choose a direction for each unknown current and a direction for each loop, then add voltage rises and subtract drops as you go round. A negative answer only means the current flows opposite to the direction assumed. In Tutorial 1 Q2(iv), KVL round two batteries and three resistances gives $I = -40\ \mathrm A$, so the current flows from the $13\ \mathrm V$ battery into Sam's. Combined with Ohm's law, the two laws also give the series and parallel resistance formulas (Tutorial 1 Q4).

The laws apply to lumped circuits, in which radiation is negligible and each component can be treated as a point. At very high frequency that assumption fails and Maxwell's equations are needed.

## Related

- [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- [[Mesh Current Method]] · [[Series and Parallel Resistors]] · [[Phasor Representation]]
- Sources: Recorded lectures 3a–3b; Niu AC notes (Figures 4–5)
