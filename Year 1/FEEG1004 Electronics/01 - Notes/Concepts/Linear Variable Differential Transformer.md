---
title: "Linear Variable Differential Transformer"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["LVDT", "differential transformer", "inductive displacement sensor", "RVDT"]
tags: [feeg1004, concept, transducers, displacement, inductance]
status: complete
parent_lectures: ["[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]"]
related_concepts: ["[[Inductance]]", "[[Ideal Transformer]]", "[[Magnetomotive Force and Reluctance]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf"]
---

# Linear Variable Differential Transformer

## Definition

> [!note] Definition
> An AC-excited primary coil with two symmetric secondaries in **series opposition** and a movable ferromagnetic core:
>
> $$V_{out} = V_a - V_b\ \propto\ \text{core displacement}$$
>
> It is zero at the centre (null) and changes phase by 180° across it.

## Explanation
- Moving the core changes the mutual coupling to each secondary (the reluctance of the magnetic path).
- Excitation is at several kHz. The output is amplitude-modulated, so **phase-sensitive demodulation** recovers a signed DC signal.
- The core is NiFe, slotted to reduce eddy currents, and mounted on a non-ferromagnetic rod.
- **Advantages**: no friction, good accuracy and linearity, high sensitivity, infinite resolution.

![[ee_e2_lvdt.png|640]]

## Related
- Topic notes: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Ideal Transformer]] · [[Inductance]] · [[Faraday's Law and Lenz's Law]]

## Sources
- Transducers lecture 2
