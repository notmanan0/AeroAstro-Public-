---
title: "Thevenin and Norton Equivalent Circuits"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["Thevenin", "Thévenin equivalent", "Norton equivalent", "open-circuit voltage", "source resistance", "ESR"]
tags: [feeg1004, concept, dc-circuits, network-theorems]
status: complete
parent_lectures: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Superposition Theorem (Circuits)]]", "[[Maximum Power Transfer]]", "[[Loading Effect and Buffering]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf"]
---

# Thevenin and Norton Equivalent Circuits

## Definition

> [!note] Definition
> Any two-terminal linear network is equivalent, at its terminals, to:
> - **Thévenin**: $V_{TH}$ (the open-circuit voltage) in series with $R_{TH}$;
> - **Norton**: $I_N = V_{TH}/R_{TH}$ (the short-circuit current) in parallel with $R_N = R_{TH}$.
>
> $R_{TH}$ is the resistance seen at the terminals with all independent sources **zeroed** (V source → short, I source → open).

## Explanation
- The terminal V–I line is $V = V_{TH} - IR_{TH}$: intercept = open-circuit voltage, slope = −source resistance.
- Batteries (ESR), power supplies and **amplifier outputs** are specified this way.
- Method: identify the network → $R_{TH}$ → $V_{TH}$ → attach the load.
- In AC, $R_{TH}$ becomes $Z_{TH}$.

## Examples
- Lecture 7a: 11 V and 5/3 Ω, so a 3 Ω load takes 2.36 A.
- W6: 13.3 V and 6.67 Ω, so a 40 Ω load takes 0.286 A.
- Tutorial 2 Q3: 0.75 V and 8.5 Ω.
- Tutorial 8 Q1: the loaded RC filter is a Thévenin source $KV_{in}$, $R_1\parallel R_L$ driving $C$.

![[ee_a7_thevenin_example.png|700]]

## Related
- Topic notes: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Concepts: [[Maximum Power Transfer]] · [[Superposition Theorem (Circuits)]] · [[Loading Effect and Buffering]]

## Sources
- Recorded lecture 7a; Week 6 interactive session
