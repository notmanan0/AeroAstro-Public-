---
title: "ADC Quantisation and Resolution"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["ADC", "DAC", "quantisation", "resolution", "LSB", "range mapping", "clipping", "zero-order hold"]
tags: [sesa2027, concept, sensors, digitisation]
status: complete
parent_lectures: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[Measurement Chain]]", "[[Nyquist Sampling and Aliasing]]", "[[Loading Effect and Buffering]]"]
sources: ["02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# ADC Quantisation and Resolution

## Definition

> [!note] Definition
> An $n$-bit ADC maps its input window to $2^n$ integer codes:
> $$Q = \frac{V_{ADC,max}-V_{ADC,min}}{2^n},\qquad N[k] = \mathrm{round}\!\left(\frac{V_{out}[k]}{Q}\right),\qquad \hat V = NQ,\qquad |e_q|\le\frac Q2$$
> Before the ADC, the sensor voltage is **range-mapped**: $V_{out} = A_vV_{in}+V_{os}$, with $A_v = \dfrac{\Delta V_{ADC}}{\Delta V_{in}}$ and $V_{os} = V_{ADC,min}-A_vV_{min}$.

## Explanation
- **Resolution in physical units** = $Q$ / sensitivity after conditioning.
- **Why map the range**: to use all $2^n$ codes over the sensor's span (best resolution) without exceeding the window.
- **Clipping**: inputs beyond the window saturate at the rails. Peak information is lost permanently, so leave headroom.
- **Quantisation noise**: the error is roughly uniform on $\pm Q/2$, with variance $Q^2/12$. Coarse resolution looks like noise, and differentiation amplifies it.
- **DAC and zero-order hold**: commands are held constant between updates, forming a staircase. A finite $Q_{DAC}$ can cause **actuator hunting** (the command toggles between neighbouring codes).

| Bits (5 V range) | $Q$ | Max error |
|---|---|---|
| 8 | 19.5 mV | 9.77 mV |
| 12 | 1.22 mV | 0.610 mV |
| 16 | 76.3 µV | 38.1 µV |

## Examples
- PS C Q7: $[-80,120]$ mV → $[0,3.3]$ V needs $A_v = 16.5$ and $V_{os} = 1.32$ V. An input of 150 mV maps to 3.80 V and clips.
- PS C Q8: a 12-bit ADC with 0.25 V/N sensitivity gives 4.88 mN per code ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_quantisation.png|560]]

## Related
- [[Measurement Chain]] · [[Nyquist Sampling and Aliasing]] · [[Loading Effect and Buffering]]

## Sources
- Lecture 3.07
