---
title: "Op-Amp Golden Rules"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["golden rules", "virtual earth", "virtual short", "ideal op-amp", "negative feedback", "GR1", "GR2"]
tags: [feeg1004, concept, op-amp, feedback]
status: complete
parent_lectures: ["[[FEEG1004 B4 - Operational Amplifiers]]"]
related_concepts: ["[[Standard Op-Amp Configurations]]", "[[Op-Amp Comparator]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §2.3.1, §2.5"]
---

# Op-Amp Golden Rules

The golden rules are two approximations for an op-amp with negative feedback. By **GR1** the output does whatever is necessary to make $V_+ = V_-$, and by **GR2** no current flows into either input.

GR1 holds because the open-loop gain is about $A_{OL}=2\times10^5$, so any finite output needs $V_+ - V_- = V_{out}/A_{OL}\approx0$. GR2 holds because input bias currents are tiny: below 500 nA for the 741 and of the order of picoamps for FET-input devices. When $V_+$ is grounded, GR1 holds $V_-$ at 0 V without connecting it to ground, and that node is called a **virtual earth**.

Applied to a circuit, the rules give a fixed sequence: GR1 for the input-node voltage, Ohm's law for the input current, GR2 to send that same current through the feedback element, and KVL to reach the output. For the inverting amplifier this gives $V_{out} = -R_FV_{in}/R_1$, and Tutorial 4 Q5 solves a T-network entirely with GR1, GR2 and KCL at the internal node $V_x$.

The rules do not apply to a comparator, which has no feedback ([[Op-Amp Comparator]]), or to a circuit with positive feedback. Even with negative feedback, the answer is valid only if the output it predicts lies within the supply rails.

## Related

- [[FEEG1004 B4 - Operational Amplifiers]]
- [[Standard Op-Amp Configurations]] · [[Op-Amp Comparator]] · [[Loading Effect and Buffering]]
- Year 2: [[Closed-Loop Transfer Function]]
- Sources: Mills notes §2.3.1, §2.5
