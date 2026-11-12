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

A linear variable differential transformer (LVDT) is a displacement sensor made of an AC-excited primary coil, two symmetric secondary coils connected in series opposition, and a movable ferromagnetic core. Its output is proportional to the displacement of the core from the centre.

$$
V_{out} = V_a - V_b\ \propto\ \text{core displacement}
$$

![[ee_e2_lvdt.png|640]]

Moving the core changes the reluctance of the magnetic path, and with it the mutual coupling between the primary and each secondary. At the centre (the null position) the two secondary voltages are equal and cancel, so the output is zero. Moving the core one way raises $V_a$ and lowers $V_b$; moving it the other way does the opposite, so the output phase changes by $180^\circ$ across the null.

The primary is excited at several kilohertz, so the output is an amplitude-modulated carrier rather than a DC level. Phase-sensitive demodulation recovers a signed DC signal that indicates both the size and the direction of the displacement. The core is nickel–iron, slotted to reduce eddy currents, and mounted on a non-ferromagnetic rod.

Because the core does not touch the coils, the LVDT has no friction. It also offers good accuracy and linearity, high sensitivity and, in principle, infinite resolution.

## Related

- [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- [[Ideal Transformer]] · [[Inductance]] · [[Faraday's Law and Lenz's Law]]
- Sources: Transducers lecture 2
