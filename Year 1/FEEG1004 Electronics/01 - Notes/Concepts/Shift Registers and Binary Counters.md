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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Shift Registers and Binary Counters

## Definition

> [!note] Definition
> - **Shift register**: D flip-flops in a chain on a **common clock**, $Q_k\to D_{k+1}$. Data moves one stage per clock.
> - **Ripple counter**: each stage has $\overline Q\to D$ (toggle) and its $\overline Q$ (or $Q$) clocks the next stage. Stage $k$ runs at $f/2^{k+1}$ and the outputs count in binary.

## Explanation
- **Serial-in parallel-out**: an $n$-bit word is readable in parallel after $n$ clocks. Serial output needs more clocks.
- An $n$-stage counter counts $0\to2^n - 1$ and wraps. The first stage is the LSB.
- "Ripple" means each stage waits for the previous one, which limits speed. Synchronous counters fix this but are beyond this course.

![[ee_b6_shift_register.png|640]]

## Examples
- A scrolling LED sign uses one shift register per row, looped back to repeat.
- A crystal oscillator divided down by a counter chain gives clock ticks. Counters also time encoder pulses and generate PWM.

## Related
- Topic notes: [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]
- Concepts: [[D-Type Flip-Flop]]
- Year 2: [[Nyquist Sampling and Aliasing]] (clocked sampling)

## Sources
- Mills notes §3.3.4–3.3.5
