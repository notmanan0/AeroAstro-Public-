---
title: "D-Type Flip-Flop"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["D flip-flop", "flip-flop", "latch", "edge-triggered", "R-S flip-flop"]
tags: [feeg1004, concept, digital, sequential]
status: complete
parent_lectures: ["[[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]"]
related_concepts: ["[[Shift Registers and Binary Counters]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# D-Type Flip-Flop

A D-type flip-flop is a one-bit memory with a data input $D$ and a clock input $C$. On the active clock edge the output takes the value of the input, $Q\leftarrow D$; between edges $Q$ holds whatever $D$ does, and $\overline Q$ is always its complement.

It is built from the R-S latch, a pair of cross-coupled gates, by adding gating from the clock and an inverter from $D$ to the R input. Because S and R then always take opposite values, the forbidden state $R=S=1$ can never occur. Rising-edge and falling-edge versions both exist, and a triangle on the C input of the symbol marks edge triggering.

Feeding $\overline Q$ back to $D$ makes the flip-flop toggle on every edge, so its output runs at half the clock frequency: a divide-by-2. The D-type is the basic cell of registers, counters and SRAM.

![[ee_b6_flipflop_counter_timing.png|700]]

## Related

- [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]
- [[Shift Registers and Binary Counters]] · [[Boolean Algebra and De Morgan's Theorems]]
- Sources: Mills notes §3.3.1–3.3.3; Week 15 session
