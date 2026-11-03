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
sources: ["02 - Sources/Lectures/Lecture 3.01.pdf", "02 - Sources/Lectures/Lecture 3.07.pdf", "Bentley, Principles of Measurement Systems, Ch. 1"]
---

# Measurement Chain

The measurement chain is the sequence of elements that turns a physical quantity into data a computer can use:

$$
\text{physical quantity}\to\text{sensor}\to\text{signal conditioning}\to\text{data acquisition (ADC)}\to\text{processing/display}
$$

The controller only ever sees what comes out of the end of the chain, the measured output, never the true one.

The sensor detects the quantity; a transducer converts energy, usually into an electrical signal. Signal conditioning then amplifies and offsets the signal to fit the ADC range, buffers it so the next stage doesn't load the sensor, filters it (the anti-alias filter), linearises it and protects the electronics. Data acquisition samples in time, quantises in amplitude and transmits, the three transformations $V(t)\to V[k]\to N[k]$. A typical example is the pitch-rate chain in PS C Q1: a MEMS gyro, then a buffer, gain and offset stage and an RC anti-alias filter, then a 12-bit ADC sampling at $f_s$, feeding the pitch-rate damper in the flight-control computer ([[SESA2027 Part C Problem Sheet Solutions]]).

Every stage can add error (noise, bias, drift, loading), add delay, or destroy information outright (clipping, aliasing). The lecture's summary is that hardware preserves and software refines: software can calibrate, filter and fuse, but it can't recover information lost before the ADC. The delays add up into a latency budget, $T_d = T_{sensor}+T_{filter}+T_{ADC}+T_{buffer}+T_{processor}+T_{comm}$, which takes $\omega_{gc}T_d$ off the phase margin.

## Related

- [[Accuracy and Precision]] · [[ADC Quantisation and Resolution]] · [[Loading Effect and Buffering]] · [[Nyquist Sampling and Aliasing]] · [[Digital Filtering]]
