---
title: "Three-Phase Star and Delta Connections"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["three-phase", "star connection", "wye", "delta connection", "balanced load", "neutral current"]
tags: [feeg1004, concept, machines, ac, power]
status: complete
parent_lectures: ["[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
related_concepts: ["[[Synchronous Speed and Pole Number]]", "[[Active, Reactive and Apparent Power]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "Sharkh notes §3.1, Figs 3.9–3.10", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf"]
---

# Three-Phase Star and Delta Connections

A three-phase supply is three EMFs of equal amplitude 120° apart, connected either in **star** (one end of each phase joined at a common neutral) or in **delta** (the three phases in a closed ring). For a **balanced** load

$$
i_N = i_A + i_B + i_C = 0,\qquad p(t) = 3V_{ph}I_{ph}\cos\phi = \text{constant}
$$

Both results come from sums over the three phases. The first is

$$
\sum_k\sin(\theta - 2\pi k/3) = 0
$$

so a balanced delta has no circulating current and a balanced star needs no neutral. The second is

$$
\sum_k\sin^2(\theta - 2\pi k/3) = \tfrac32
$$

so the total power is steady, with none of the $2\omega$ pulsation of a single phase, and machines see a smooth torque.

In star the line voltage is $\sqrt3V_{ph}$, so a 400 V line voltage corresponds to 230 V per phase (standard background). In Tutorial 5 Q4 a phase voltage of 298.6 V across 5 Ω gives 59.7 A per phase, 53.5 kW in total and zero neutral current.

![[ee_c2_three_phase_power.png|640]]

## Related

- [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- [[Synchronous Speed and Pole Number]] · [[Active, Reactive and Apparent Power]] · [[RMS Value]]
- Sources: Sharkh notes §3.1 (Figs 3.9–3.10); Machines 02 slides
