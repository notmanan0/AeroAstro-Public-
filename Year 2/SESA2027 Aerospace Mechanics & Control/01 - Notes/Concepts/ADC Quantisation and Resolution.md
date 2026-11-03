---
title: "ADC Quantisation and Resolution"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["ADC", "DAC", "quantisation", "resolution", "LSB", "range mapping", "clipping", "zero-order hold", "quantisation noise"]
tags: [sesa2027, concept, sensors, digitisation]
status: complete
parent_lectures: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[Measurement Chain]]", "[[Nyquist Sampling and Aliasing]]", "[[Loading Effect and Buffering]]"]
sources: ["02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# ADC Quantisation and Resolution

An $n$-bit analogue-to-digital converter maps its input window onto $2^n$ integer codes, so it can only resolve the voltage to within one quantisation step $Q$:

$$
Q = \frac{V_{ADC,max}-V_{ADC,min}}{2^n},\qquad N[k] = \mathrm{round}\!\left(\frac{V_{out}[k]}{Q}\right),\qquad \hat V = NQ,\qquad |e_q|\le\frac Q2 .
$$

Resolution in physical units is $Q$ divided by the sensitivity after conditioning. To get the best resolution the sensor voltage is range-mapped before the ADC, $V_{out} = A_vV_{in}+V_{os}$ with

$$
A_v = \frac{\Delta V_{ADC}}{\Delta V_{in}},\qquad V_{os} = V_{ADC,min}-A_vV_{min},
$$

so that the sensor's span uses all $2^n$ codes without leaving the window. Inputs beyond the window clip at the rails and the peak information is lost for good, which is why designers leave some headroom. In PS C Q7, mapping $[-80,120]$ mV onto $[0,3.3]$ V needs $A_v = 16.5$ and $V_{os} = 1.32$ V, and an input of 150 mV then maps to 3.80 V and clips. In Q8 a 12-bit ADC behind a 0.25 V/N load cell resolves 4.88 mN per code ([[SESA2027 Part C Problem Sheet Solutions]]).

| Bits (5 V range) | $Q$ | Max error |
|---|---|---|
| 8 | 19.5 mV | 9.77 mV |
| 12 | 1.22 mV | 0.610 mV |
| 16 | 76.3 µV | 38.1 µV |

The quantisation error is roughly uniform on $\pm Q/2$, so it behaves like noise of variance $Q^2/12$; coarse resolution looks like a noisy sensor, and differentiating the signal makes it worse. The same thing happens on the output side. A DAC holds each command constant until the next update (a zero-order hold, giving a staircase), and a coarse $Q_{DAC}$ can make the actuator hunt between neighbouring codes.

![[amc_quantisation.png|560]]

## Related

- Derivation of the $Q/\sqrt{12}$ noise level: [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#3. Amplitude transformation: ADC resolution|C3 §3]]
- [[Measurement Chain]] · [[Nyquist Sampling and Aliasing]] · [[Loading Effect and Buffering]]
