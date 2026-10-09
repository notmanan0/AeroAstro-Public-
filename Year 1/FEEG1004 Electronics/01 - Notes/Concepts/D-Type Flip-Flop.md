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

## Definition

> [!note] Definition
> A one-bit memory with data input $D$ and clock $C$. On the active clock **edge**, $Q\leftarrow D$. Between edges, $Q$ holds regardless of $D$. $\overline Q$ is always the complement.

## Explanation
- It derives from the R-S latch (cross-coupled gates) plus clock gating plus an inverter from $D$ to R, which removes the forbidden R = S = 1 state.
- Rising- or falling-edge versions exist. The triangle on the C input marks edge triggering.
- Feeding $\overline Q$ back to $D$ makes it **toggle** every edge: a divide-by-2.
- It is the basic cell of registers, counters and SRAM.

![[ee_b6_flipflop_counter_timing.png|700]]

## Related
- Topic notes: [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]
- Concepts: [[Shift Registers and Binary Counters]] · [[Boolean Algebra and De Morgan's Theorems]]

## Sources
- Mills notes §3.3.1–3.3.3; Week 15 session
