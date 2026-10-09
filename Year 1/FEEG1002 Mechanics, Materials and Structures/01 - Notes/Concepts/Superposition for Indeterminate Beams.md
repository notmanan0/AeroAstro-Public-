---
title: "Superposition for Indeterminate Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["compatibility method", "force method", "redundant reaction", "propped cantilever"]
tags: [feeg1002, concept, statics, beams, statically-indeterminate, compatibility]
status: complete
parent_lectures: ["[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
related_concepts: ["[[Static Determinacy]]", "[[Standard Beam Deflections]]", "[[Macaulay's Method]]"]
sources: []
---

# Superposition for Indeterminate Beams

## Definition

> [!note] Definition
> Remove a redundant support and replace it by an unknown force $F$. By linearity, the deflection at that point is the sum of the deflection due to the applied loads and that due to $F$. **Compatibility** (zero deflection, or zero slope, at the real support) fixes $F$:
> $$v_{loads}(x_s) + v_F(x_s) = 0$$

## Explanation

- This is valid only for linear elastic, small-deflection behaviour.
- With $n$ redundants you get $n$ compatibility equations.
- The alternative is **double integration**: carry the unknown reactions through Macaulay's method and use the extra kinematic boundary conditions.
- Both routes need the deflection. **Load sharing in an indeterminate structure depends on stiffness.**

## Examples

Propped cantilever with UDL:
$$\frac{wL^4}{8EI} = \frac{FL^3}{3EI}\;\Rightarrow\;R_B = \tfrac38wL,\quad R_A = \tfrac58wL,\quad M_A = \tfrac18wL^2$$

![[s1_superposition_propped_cantilever.png|640]]

## Related

- Topic notes: [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Concepts: [[Static Determinacy]] · [[Standard Beam Deflections]] · [[Macaulay's Method]]
- Year 2: Energy form: $\partial U/\partial R = 0$ ([[Castigliano Second Theorem]]) in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] · [[Maxwell-Betti Reciprocity]]

## Sources

- Statics 1 Lecture 11c
