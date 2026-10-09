---
title: "Karnaugh Maps"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["K-map", "Karnaugh map", "Gray code", "logic minimisation"]
tags: [feeg1004, concept, digital]
status: complete
parent_lectures: ["[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"]
related_concepts: ["[[Boolean Algebra and De Morgan's Theorems]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Karnaugh Maps

## Definition

> [!note] Definition
> A truth table redrawn on a grid with **Gray-coded** axes (00, 01, 11, 10), so adjacent cells differ in one variable. Grouping adjacent 1s in blocks of $2^n$ eliminates the variables that change within each block.

## Explanation
- The map wraps around (a torus): edges are adjacent.
- Use the **largest, fewest** groups; overlap is allowed; no diagonals. Each group becomes one product term.
- A term missing a variable covers several cells: $AB$ fills the whole $AB = 11$ column of a 4-variable map.
- Practical for up to 4 (at most 5) variables.

![[ee_b5_karnaugh_maps.png|800]]

## Examples
- Tutorial 4 Q4(a): a wrap-around group of four gives $F = \overline B$.
- Tutorial 4 Q4(b): the whole $C = 0$ half gives $F = \overline C$.
- Mills Ex. 7: $F = AB + C + D$.

## Related
- Topic notes: [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- Concepts: [[Boolean Algebra and De Morgan's Theorems]]

## Sources
- Mills notes §3.2.5–3.2.6
