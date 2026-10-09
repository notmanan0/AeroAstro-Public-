---
title: "FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 6
tags: [feeg1004, electronics, digital, sequential-logic, flip-flop, shift-register, counter, memory]
aliases: ["EL5 digital logic 2", "Sequential logic", "D flip-flop", "Binary counter", "Shift register"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"]
next_topics: ["[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
key_concepts: ["[[D-Type Flip-Flop]]", "[[Shift Registers and Binary Counters]]"]
tutorial_sheets: []
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W15-EL5 Digital Logic 2 Sequential - Interactive.pdf"]
---

# FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters

> [!abstract] Summary
> **Sequential** logic has **memory**: the output depends on the inputs *and* the past state.
> - The building block is the **flip-flop**. The **D-type** copies its data input $D$ to $Q$ **only at a clock edge**, then holds it.
> - Chains of D flip-flops make **shift registers** (serial ↔ parallel data) and **ripple counters** (each stage divides the frequency by 2).
> - Exam focus: you need **not** memorise the internal gates. You must predict what simple D-flip-flop circuits do.

## Key Concepts
- [[D-Type Flip-Flop]] · [[Shift Registers and Binary Counters]]

---

## 1. From R-S latch to D flip-flop (Mills §3.3.1–3.3.3)
- **R-S flip-flop**: two cross-coupled NOR (or NAND) gates. Set makes Q = 1; Reset makes Q = 0; both inactive holds the state. R = S = 1 is forbidden.
- **Clocked R-S**: gating R and S with a clock means the inputs only act while the clock is active.
- **D-type**: a single data input feeds S and, via an inverter, R, which removes the forbidden state. The design is **edge-triggered**: on the chosen edge (rising or falling), $Q\leftarrow D$; at all other times $Q$ holds.

![[ee_b6_flipflop_counter_timing.png|880]]

## 2. Shift registers (§3.3.4)
- Four D flip-flops share one clock, with each $Q$ feeding the next $D$.
- At every edge each bit moves one place along.
  - **Serial-in, parallel-out**: a 4-bit word is available on the four outputs after 4 clocks. This converts serial data to parallel.
  - **Serial out**: keep clocking to shift the data out one bit at a time.
- **Applications**: serial ↔ parallel conversion (UART, SPI), delay lines, scrolling message signs (one register per LED row, looped back to repeat).

![[ee_b6_shift_register.png|820]]

## 3. Binary ripple counters (§3.3.5)
- Each stage's $\overline Q$ is fed back to its own $D$ (so it **toggles** every edge) **and** clocks the next stage.
- Each stage therefore toggles at **half** the rate of the one before: a **frequency divider** chain (÷2, ÷4, ÷8, ÷16).
- The outputs read as a binary number counting 0000 → 1111 → 0000 (up counter). It is called "ripple-through" because each stage waits for the one before.
- Read the bits in the right order: stage A is the **least significant** bit.

> [!example] Tracing a counter (Mills Table 3.3.5 method)
> Keep a table with one column per stage showing $Q$ and ($\overline Q = D$). At each **rising** input edge:
> 1. stage A toggles;
> 2. a stage toggles whenever the stage before it produces a rising edge on its clock, i.e. when the previous $\overline Q$ goes 0 → 1, which is when the previous $Q$ goes 1 → 0.
>
> Reading $DCBA$ then gives 0, 1, 2, …, 15, 0. The W15 multiple-choice counter question is solved the same way: list each $D$ just before each clock edge. Do not guess from the pattern.

## 4. Memory (§3.3.6)
| Type | Stores a bit as | Volatile? | Notes |
|---|---|---|---|
| SRAM | a flip-flop | yes | fast, needs no refresh |
| DRAM | charge on a MOSFET gate / capacitor | yes | dense, must be **refreshed** |
| Flash | charge trapped on an insulated (floating) gate | **no** | portable storage |

RAM is **random access** (any order), unlike a shift register (sequential).

## 5. Interactive exam-style question: LED on an AC supply (W15)
A 5 V rms, 50 Hz source drives an LED ($V_F$ = 2.8 V) through 200 Ω.
- Amplitude = $5\sqrt2$ = 7.07 V; period = 20 ms.
- The LED conducts only while $v_{in} > 2.8$ V. Solving $7.07\sin(100\pi t) = 2.8$ gives ON at **1.30 ms** and OFF at **8.70 ms** in each cycle.
- While ON: $i = (7.07\sin100\pi t - 2.8)/200$ A (KVL, Ohm, and KCL for the LED current). Its peak is 21.4 mA.

## Year 2 bridge
- **Clocked sampling**: an ADC's sample-and-hold and output register are sequential logic. The clock sets the sample rate, and hence aliasing ([[Nyquist Sampling and Aliasing]], [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).
- **Counters** time events: encoder pulse counting for wheel speed, and PWM generation for motor drives ([[DC Motor Speed Control]]).
- **Radiation** can flip a stored bit (single-event upset). Spacecraft memories use error-correcting codes and scrubbing ([[Space Environment Hazards]]).
- **Payload data** buffered in memory before downlink sets storage sizing ([[Payload Data Rate]]).

## Links
- Previous: [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]] · Next: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]

## Sources
- Mills notes §3.3; Week 15 interactive session (EL5).
