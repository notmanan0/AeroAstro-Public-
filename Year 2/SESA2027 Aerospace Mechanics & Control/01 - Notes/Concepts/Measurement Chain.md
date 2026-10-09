---
title: "Measurement Chain"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["sensing system", "measurement system", "sensor vs transducer", "signal chain", "digital bridge"]
tags: [sesa2027, concept, sensors]
status: complete
parent_lectures: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[Accuracy and Precision]]", "[[ADC Quantisation and Resolution]]", "[[Loading Effect and Buffering]]", "[[Nyquist Sampling and Aliasing]]"]
sources: ["02 - Sources/Lectures/Lecture 3.01.pdf", "02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# Measurement Chain

## Definition

> [!note] Definition
> The sequence of elements that turns a physical quantity into data a computer can use:
>
> $$\text{physical quantity}\to\text{sensor}\to\text{signal conditioning}\to\text{data acquisition (ADC)}\to\text{processing/display}$$
>
> The controller only ever sees the chain's output, the **measured** output, never the true one.

## Explanation
- A **sensor** detects the quantity. A **transducer** converts energy, usually into an electrical signal.
- **Conditioning**:
  - amplify, offset (range mapping), buffer (impedance);
  - filter (anti-alias);
  - linearise;
  - protect.
- **DAQ**: sample in time, quantise in amplitude, transmit. The three transformations are $V(t)\to V[k]\to N[k]$.
- Each stage can **add error** (noise, bias, drift, loading), **add delay** (latency) or **destroy information** (clipping, aliasing).
- **Hardware preserves, software refines**: software can calibrate, filter and fuse, but it cannot recover information lost before the ADC.
- **Latency budget**: $T_d = T_{sensor}+T_{filter}+T_{ADC}+T_{buffer}+T_{processor}+T_{comm}$. It subtracts $\omega_{gc}T_d$ from the phase margin.

## Examples
- Pitch-rate chain: MEMS gyro → buffer, gain/offset, RC anti-alias → 12-bit ADC at $f_s$ → FCC pitch-rate damper ([[SESA2027 Part C Problem Sheet Solutions]] Q1).

## Related
- [[Accuracy and Precision]] · [[ADC Quantisation and Resolution]] · [[Loading Effect and Buffering]] · [[Nyquist Sampling and Aliasing]] · [[Digital Filtering]]

## Sources
- Lectures 3.01, 3.07; Bentley, *Principles of Measurement Systems*, Ch. 1
