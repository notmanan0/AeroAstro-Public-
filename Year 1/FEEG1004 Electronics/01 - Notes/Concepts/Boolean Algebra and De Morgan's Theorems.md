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

Boolean algebra is the algebra of two-valued logic variables, with AND written as a product and OR as a sum. De Morgan's theorems convert between the two operations under a complement:

$$
\overline{A+B}=\overline A\cdot\overline B,\qquad \overline{A\cdot B}=\overline A+\overline B.
$$

The mnemonic is "break the line, change the sign": splitting the complement bar over the variables swaps AND and OR.

Most manipulations follow ordinary algebra, with AND behaving like multiplication and OR like addition. The exceptions come from OR-dominance, idempotence and the distributivity of OR over AND:

$$
A+1=1,\qquad A+A=A,\qquad A+\overline A=1,\qquad A\overline A=0,\qquad A+AB=A,\qquad A+BC=(A+B)(A+C).
$$

Exclusive-OR is $A\oplus B=A\overline B+\overline AB$. Every identity can be proved row by row with a truth table, which is the method of Tutorial 4 Q2.

A sum-of-products expression is read straight from a truth table: OR together one AND-term for each row with $F=1$. NAND and NOR are universal gates. Double-inverting an expression and applying De Morgan turns any function into one built from a single gate type.

In Mills Ex. 3, $A\overline B\,\overline C+AB\overline C+\overline A\,\overline BC+\overline ABC=A\oplus C$, which does not depend on $B$. In Tutorial 4 Q3, $\overline{\overline{AB}+(B\oplus C)}=ABC$.

![[ee_b5_logic_gates.png|760]]

## Related

- [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- [[Karnaugh Maps]] · [[D-Type Flip-Flop]]
- Sources: Mills notes §3.2.3; Week 11 session
