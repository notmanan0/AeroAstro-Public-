---
title: "Boolean Algebra and De Morgan's Theorems"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["Boolean algebra", "De Morgan", "logic identities", "sum of products", "universal gates", "NAND logic"]
tags: [feeg1004, concept, digital]
status: complete
parent_lectures: ["[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"]
related_concepts: ["[[Karnaugh Maps]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W11-EL4 Digital Logic 1 Combinational - Interactive.pdf"]
---

# Boolean Algebra and De Morgan's Theorems

## Definition

> [!note] Definition
>
> $$\overline{A + B} = \overline A\cdot\overline B,\qquad \overline{A\cdot B} = \overline A + \overline B\qquad(\text{"break the line, change the sign"})$$
>
> Also key: $A + 1 = 1$, $A + A = A$, $A + \overline A = 1$, $A\overline A = 0$, $A + AB = A$, $A + BC = (A + B)(A + C)$ and $A\oplus B = A\overline B + \overline AB$.

## Explanation
- It mostly behaves like ordinary algebra (AND ↔ ×, OR ↔ +). The exceptions are **OR-dominance, idempotence and OR-distributivity**.
- **SOP from a truth table**: OR together one AND-term per row with $F = 1$.
- Every identity can be proved by a truth table, row by row (Tutorial 4 Q2).
- **NAND/NOR are universal**. Double-invert and apply De Morgan to build any function from one gate type.

## Examples
- Mills Ex. 3: $A\overline B\,\overline C + AB\overline C + \overline A\,\overline BC + \overline ABC = A\oplus C$ (independent of B).
- Tutorial 4 Q3: $\overline{\overline{AB} + (B\oplus C)} = ABC$.

![[ee_b5_logic_gates.png|760]]

## Related
- Topic notes: [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- Concepts: [[Karnaugh Maps]] · [[D-Type Flip-Flop]]

## Sources
- Mills notes §3.2.3; Week 11 session
