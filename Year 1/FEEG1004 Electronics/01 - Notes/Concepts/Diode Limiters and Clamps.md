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

A **limiter** (clipper) uses shunt diodes, optionally with bias batteries, to stop the output exceeding set thresholds such as $\pm0.7\ \mathrm V$ or $V_x+0.7\ \mathrm V$. A **clamp** uses a series capacitor and a shunt diode to shift the whole waveform by $V_p-0.7$ without changing its shape.

A limiter is analysed through its transfer characteristic, $v_{out}$ against $v_{in}$, assuming no output current is drawn. The characteristic is piecewise linear, with a break wherever a diode switches state. Anti-parallel diodes protect sensitive inputs from voltage spikes, and a bias battery in series with a diode moves the knee to a chosen voltage. If the diode branch also contains a series resistor, the output is not held flat beyond the knee but rises with a reduced slope, giving a soft limiter (Tutorial 3 Q3).

A clamp works because the capacitor charges through the diode on one peak of the input and cannot then discharge, since the diode is reverse biased for the rest of the cycle. The capacitor voltage adds to the input as a constant offset.

![[ee_b2_limiters.png|640]]

In Tutorial 3 Q3 the slope is 1 for $|v_{in}|<5\ \mathrm V$, and beyond that $v_{out}=(v_{in}\pm5)/2$. In the Mills clamp example a $5\ \mathrm V$ peak input is shifted up by $4.3\ \mathrm V$.

## Related

- [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- [[P-N Junction Diode]] · [[Capacitance]]
- Sources: Mills notes §1.5.6; Tutorial Sheet 3
