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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Rectification and Smoothing

## Definition

> [!note] Definition
> Diodes convert AC to unidirectional current. A capacitor across the load holds the peak:
>
> $$\Delta V = \frac{I}{2fC}\ \text{(full-wave)},\qquad \Delta V = \frac{I}{fC}\ \text{(half-wave)},\qquad V_{avg} = V_p - \frac{\Delta V}{2}$$

## Explanation
- **Half-wave**: one diode, peak $V_{in} - 0.7$, output at $f$.
- **Full-wave bridge**: four diodes, peak $V_{in} - 1.4$, output at $2f$.
- The ripple formula assumes a nearly linear discharge at the load current between peaks (small ripple, $R_LC\gg T$).
- Design to the **average** output and add the diode drops to find the required input peak.

![[ee_b2_rectifiers.png|640]]

## Examples
- Tutorial 3 Q6: 10 V, 0.2 V ripple, 5 mA, 50 Hz needs $C$ = 250 µF and a 23 V peak-to-peak input.
- W7 bridge: 10 V amplitude gives an 8.6 V peak output.

## Related
- Topic notes: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Concepts: [[Capacitance]] · [[RC Low-Pass and High-Pass Filters]] · [[RMS Value]]
- Maths: the Fourier series of a rectified sine, [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]

## Sources
- Mills notes §1.5.2–1.5.3
