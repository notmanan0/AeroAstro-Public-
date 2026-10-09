---
title: "Diode Limiters and Clamps"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["clipper", "limiter", "clamp", "DC restorer", "transfer characteristic"]
tags: [feeg1004, concept, diode, protection]
status: complete
parent_lectures: ["[[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]"]
related_concepts: ["[[P-N Junction Diode]]", "[[Capacitance]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Diode Limiters and Clamps

## Definition

> [!note] Definition
> - **Limiter (clipper)**: shunt diodes (optionally with bias batteries) stop the output exceeding set thresholds, e.g. ±0.7 V or $V_x + 0.7$ V.
> - **Clamp**: a series capacitor and shunt diode shift the whole waveform by $V_p - 0.7$ without changing its shape.

## Explanation
- Draw the **transfer characteristic** $v_{out}$ vs $v_{in}$, assuming no output current. It is piecewise linear with a break wherever a diode switches.
- Anti-parallel diodes protect sensitive inputs from spikes. A bias battery moves the knee.
- With a series resistor inside the diode branch, the output is not held flat but rises with a **reduced slope** (a soft limiter, Tutorial 3 Q3).
- A clamp works because the capacitor charges on one peak and can never discharge through the reversed diode.

![[ee_b2_limiters.png|640]]

## Examples
- Tutorial 3 Q3: slope 1 for $|v_{in}| < 5$ V, then $v_{out} = (v_{in}\pm5)/2$.
- Mills clamp: a 5 V peak input is shifted up by 4.3 V.

## Related
- Topic notes: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Concepts: [[P-N Junction Diode]] · [[Capacitance]]

## Sources
- Mills notes §1.5.6; Tutorial Sheet 3
