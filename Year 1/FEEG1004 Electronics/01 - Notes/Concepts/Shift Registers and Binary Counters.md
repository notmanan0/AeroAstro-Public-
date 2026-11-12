---
title: "Shift Registers and Binary Counters"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["shift register", "ripple counter", "binary counter", "frequency divider", "serial to parallel"]
tags: [feeg1004, concept, digital, sequential]
status: complete
parent_lectures: ["[[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]"]
related_concepts: ["[[D-Type Flip-Flop]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §3.3.4–3.3.5"]
---

# Shift Registers and Binary Counters

A **shift register** is a chain of D flip-flops on a common clock, with each output feeding the next input ($Q_k\to D_{k+1}$), so the data move one stage per clock pulse. A **ripple counter** is a chain of toggling D flip-flops ($\overline Q\to D$) in which each stage's $\overline Q$ (or $Q$) clocks the next stage, so stage $k$ runs at $f/2^{k+1}$ and the outputs count in binary.

A shift register converts serial data to parallel: an $n$-bit word fed in one bit per clock can be read in parallel after $n$ clocks, while reading it back out serially takes further clocks. A scrolling LED sign uses one shift register per row, with the last output looped back to the input so the pattern repeats.

An $n$-stage counter counts from 0 to $2^n - 1$ and then wraps to zero, with the first stage as the least significant bit. Because each stage halves the frequency, a counter chain is also a frequency divider: a crystal oscillator divided down this way gives clock ticks, and counters also time encoder pulses and generate PWM signals. In a ripple counter each stage waits for the previous one to change, and this delay limits the speed. Synchronous counters, in which every stage shares the clock, avoid the problem but are beyond this course.

![[ee_b6_shift_register.png|640]]

## Related

- [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]
- [[D-Type Flip-Flop]]
- Year 2: [[Nyquist Sampling and Aliasing]] (clocked sampling)
- Sources: Mills notes §3.3.4–3.3.5
