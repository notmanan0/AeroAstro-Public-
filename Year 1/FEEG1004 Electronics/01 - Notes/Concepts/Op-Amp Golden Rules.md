---
title: "Op-Amp Golden Rules"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["golden rules", "virtual earth", "virtual short", "ideal op-amp", "negative feedback"]
tags: [feeg1004, concept, op-amp, feedback]
status: complete
parent_lectures: ["[[FEEG1004 B4 - Operational Amplifiers]]"]
related_concepts: ["[[Standard Op-Amp Configurations]]", "[[Op-Amp Comparator]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Op-Amp Golden Rules

## Definition

> [!note] Definition
> For an op-amp **with negative feedback**:
> 1. **GR1**: the output does whatever is necessary to make $V_+ = V_-$.
> 2. **GR2**: no current flows into either input.

## Explanation
- GR1 holds because $A_{OL}\sim2\times10^5$: a finite output needs $V_+ - V_- = V_{out}/A_{OL}\approx0$.
- GR2 holds because input bias currents are tiny (<500 nA for the 741, pA for FET inputs).
- If $V_+$ is grounded, GR1 makes $V_-$ a **virtual earth**: at 0 V but not connected to ground.
- **Recipe**: GR1 to find the input-node voltage → Ohm for the input current → GR2 (the same current through the feedback element) → KVL to the output.
- They do **not** apply to comparators (no feedback) or with positive feedback. Always check the output lies within the supply rails.

## Examples
- The inverting amplifier derivation gives $V_{out} = -R_FV_{in}/R_1$.
- Tutorial 4 Q5: the T-network is solved entirely with GR1, GR2 and KCL at $V_x$.

## Related
- Topic notes: [[FEEG1004 B4 - Operational Amplifiers]]
- Concepts: [[Standard Op-Amp Configurations]] · [[Loading Effect and Buffering]]
- Year 2: [[Closed-Loop Transfer Function]]

## Sources
- Mills notes §2.3.1, §2.5
