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
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf"]
---

# Three-Phase Star and Delta Connections

## Definition

> [!note] Definition
> Three EMFs of equal amplitude 120° apart. Connected in **star** (one end of each phase at a common neutral) or **delta** (a closed ring). For a **balanced** load:
>
> $$i_N = i_A + i_B + i_C = 0,\qquad p(t) = 3V_{ph}I_{ph}\cos\phi = \text{constant}$$

## Explanation
- $\sum_k\sin(\theta - 2\pi k/3) = 0$, which is why delta has no circulating current and star needs no neutral when balanced.
- $\sum_k\sin^2(\theta - 2\pi k/3) = 3/2$, which is why the total power is steady: no $2\omega$ pulsation, so machines see smooth torque.
- Line voltage in star is $\sqrt3V_{ph}$ (400 V line = 230 V phase). This is standard background not derived in the lectures.

![[ee_c2_three_phase_power.png|640]]

## Examples
- Tutorial 5 Q4: 298.6 V phase into 5 Ω gives 59.7 A per phase, 53.5 kW total, zero neutral current.

## Related
- Topic notes: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- Concepts: [[Active, Reactive and Apparent Power]] · [[RMS Value]]

## Sources
- Sharkh notes §3.1 (Figs 3.9–3.10); Machines 02 slides
