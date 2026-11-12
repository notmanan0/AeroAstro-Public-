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
sources: ["Statics 1 Lecture 11"]
---

# Superposition for Indeterminate Beams

The superposition method solves a statically indeterminate beam by removing one support, treating its reaction as an unknown applied load, and choosing that load so that the beam's deflection at the support is what the support demands, usually zero.

It works because a linear elastic beam with small deflections obeys a linear equation, so the deflection under several loads is the sum of the deflections under each. For a propped cantilever of length $L$ under a uniform load $w$, built in at the left and propped at the right, the beam without the prop is a cantilever, whose tip deflects down by $wL^4/8EI$. The prop force $R_2$ alone, acting upwards on the same cantilever, lifts the tip by $R_2L^3/3EI$. The real tip does not move, so

$$
\frac{wL^4}{8EI}-\frac{R_2L^3}{3EI}=0\quad\Rightarrow\quad R_2=\frac38wL
$$

and equilibrium then gives $R_1=\tfrac58wL$ and the wall moment $M_1=\tfrac18wL^2$.

This compatibility condition is the equation that equilibrium could not supply. With $n$ redundant reactions there are $n$ such conditions, which may be on slope as well as deflection. The same reactions follow from double integration, carrying the unknown reactions through Macaulay's method and using the extra boundary conditions; superposition is quicker when the pieces are standard cases. Either way, $EI$ cancels from the reactions of a uniform beam, but the load sharing still depends on stiffness: in a beam with parts of different $EI$, the stiffer parts attract more of the load.

![[s1_superposition_propped_cantilever.png|760]]

## Related

- Topic notes: [[FEEG1002 A6 - Statically Indeterminate Beams#3. The superposition method|A6, the superposition method]] · [[FEEG1002 A6 - Statically Indeterminate Beams#Compatibility and the reactions|A6, compatibility and the reactions]] · [[FEEG1002 A6 - Statically Indeterminate Beams#4. Which method|A6, which method]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Q3 - Propped cantilever with a half-length UDL|Tutorial 5 Q3]]
- Concepts: [[Static Determinacy]] · [[Standard Beam Deflections]] · [[Macaulay's Method]]
- Year 2: the energy form, [[Castigliano Second Theorem]], in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] · [[Maxwell-Betti Reciprocity]]
