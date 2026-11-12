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

A Karnaugh map is a truth table redrawn on a grid whose axes are labelled in **Gray code** (00, 01, 11, 10), so that neighbouring cells differ in exactly one variable. Grouping adjacent 1s in blocks of $2^n$ cells eliminates the variables that change within each block, giving a minimised logic expression.

![[ee_b5_karnaugh_maps.png|800]]

Because of the Gray-code ordering, the map wraps around like a torus: the left and right edges are adjacent, and so are the top and bottom. Groups must be rectangular blocks of 1, 2, 4, 8 or 16 cells, never diagonal, and they may overlap. The aim is the fewest groups, each as large as possible, because each group becomes one product term and a larger group keeps fewer variables. A term missing a variable covers several cells; on a 4-variable map, $AB$ fills the whole $AB = 11$ column.

In Tutorial 4 Q4(a) a group of four that wraps around the edges gives $F = \overline B$, and in Q4(b) the whole $C = 0$ half of the map gives $F = \overline C$. Mills Ex. 7 reduces to $F = AB + C + D$.

The method is practical for up to four variables, and at most five.

## Related

- [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- [[Boolean Algebra and De Morgan's Theorems]]
- Sources: Mills notes §3.2.5–3.2.6
