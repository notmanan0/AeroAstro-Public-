---
title: "Ideal Transformer"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["transformer", "turns ratio", "step-up", "step-down", "V1/V2 = N1/N2"]
tags: [feeg1004, concept, machines, transformer]
status: complete
parent_lectures: ["[[FEEG1004 C3 - Transformers and AC Power Transmission]]"]
related_concepts: ["[[Transformer EMF Equation]]", "[[Faraday's Law and Lenz's Law]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Ideal Transformer

## Definition

> [!note] Definition
> $$\frac{V_1}{V_2} = \frac{N_1}{N_2},\qquad V_1I_1 = V_2I_2\ \Rightarrow\ \frac{I_2}{I_1} = \frac{N_1}{N_2},\qquad \eta = \frac{P_2}{P_1}\ (\to99\ \%\ \text{large units})$$

## Explanation
- The same core flux links both windings. Faraday on each gives the voltage ratio.
- Stepping voltage up steps current down, which reduces transmission $I^2R$ losses.
- The core is **laminated** to stop eddy-current losses.
- It only works on AC: constant flux induces nothing.
- A load $R_L$ on the secondary looks like $(N_1/N_2)^2R_L$ from the primary (standard result, not derived in the lectures).

## Examples
- 400:1000 turns at 500 V gives 1250 V.
- Tutorial 5 Q5: 70:350 turns, 230 V gives 1150 V; a 10 kW load draws 43.5 A on the primary.

## Related
- Topic notes: [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- Concepts: [[Transformer EMF Equation]] · [[Linear Variable Differential Transformer]]

## Sources
- Sharkh notes §3.5; Machines 04 slides
