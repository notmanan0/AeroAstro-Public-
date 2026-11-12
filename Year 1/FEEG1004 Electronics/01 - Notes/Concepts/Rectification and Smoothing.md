---
title: "Rectification and Smoothing"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["rectifier", "half-wave rectifier", "full-wave bridge", "smoothing capacitor", "ripple", "C = I/(2 f dV)"]
tags: [feeg1004, concept, diode, power-supply]
status: complete
parent_lectures: ["[[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]"]
related_concepts: ["[[P-N Junction Diode]]", "[[Capacitance]]", "[[Zener Diode Regulator]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §1.5.2–1.5.3"]
---

# Rectification and Smoothing

A rectifier uses diodes to turn an alternating supply into a unidirectional current, and a smoothing capacitor across the load holds the output near the peak between charging pulses, leaving a small ripple $\Delta V$.

$$
\Delta V = \frac{I}{2fC}\ \text{(full-wave)},\qquad \Delta V = \frac{I}{fC}\ \text{(half-wave)},\qquad V_{avg} = V_p - \frac{\Delta V}{2}
$$

A half-wave rectifier has one diode, so its output peak is $V_{in} - 0.7$ and the output pulses at the supply frequency $f$. A full-wave bridge has four diodes, two of which conduct on each half-cycle, so the peak is $V_{in} - 1.4$ and the output pulses at $2f$. The doubled pulse rate is why the full-wave ripple formula has $2f$ in it.

The ripple formula assumes that the capacitor discharges almost linearly at the load current between peaks, which holds when the ripple is small and $R_LC\gg T$. A supply is designed to the **average** output: find $V_p$ from $V_{avg}$ and $\Delta V$, then add the diode drops to get the required input peak.

![[ee_b2_rectifiers.png|640]]

In Tutorial 3 Q6 a 10 V, 5 mA output at 50 Hz with 0.2 V ripple needs $C$ = 250 µF and an input of 23 V peak-to-peak. A bridge fed with a 10 V amplitude gives an 8.6 V peak output (W7).

## Related

- [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- [[Capacitance]] · [[RC Low-Pass and High-Pass Filters]] · [[RMS Value]]
- Maths: the Fourier series of a rectified sine, [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]
- Sources: Mills notes §1.5.2–1.5.3
