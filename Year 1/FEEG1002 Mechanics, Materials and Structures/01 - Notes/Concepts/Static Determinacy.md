---
title: "Static Determinacy"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["statically determinate", "statically indeterminate", "mechanism", "2j = r + m", "redundancy"]
tags: [feeg1002, concept, statics, trusses, indeterminacy]
status: complete
parent_lectures: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]", "[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
related_concepts: ["[[Method of Joints and Method of Sections]]", "[[Free Body Diagram and Equilibrium]]", "[[Superposition for Indeterminate Beams]]"]
sources: []
---

# Static Determinacy

## Definition

> [!note] Definition
> A structure is **statically determinate** if equilibrium alone fixes all its internal forces and reactions. For a plane pin-jointed frame with $j$ joints, $r$ reaction components and $m$ bars:
> $$2j = r+m\ \ \text{determinate},\qquad r+m<2j\ \ \text{mechanism},\qquad r+m>2j\ \ \text{indeterminate}$$
> For beams: two equilibrium equations for vertical loading, compared with the number of unknown support reactions.

## Explanation

- **Mechanism**: too few members. It moves without straining and cannot carry general loads.
- **Indeterminate**: redundant members or supports. The force distribution depends on the relative stiffnesses, so **compatibility** (deformation) equations are needed. Such structures are more robust (redundancy) but sensitive to misfit, settlement and temperature.
- The counting test is **necessary, not sufficient**. One part of a frame can be over-braced while another part is a mechanism, and the count still balances. Always inspect the geometry.
- Degree of indeterminacy = unknowns − independent equilibrium equations:
  - propped cantilever: 1;
  - fixed–fixed beam: 2.

## Examples

![[s1_truss_static_determinacy.png|760]]

## Related

- Topic notes: [[FEEG1002 A2 - Pin-Jointed Trusses]] · [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Concepts: [[Method of Joints and Method of Sections]] · [[Free Body Diagram and Equilibrium]] · [[Superposition for Indeterminate Beams]]
- Year 2: Redundants solved by [[Castigliano Second Theorem]] ([[SESA2028 S8 - Virtual Work and Castigliano Theorems]]) · [[Boundary Conditions and Rigid Body Modes]] (a mechanism shows up as a singular FE stiffness matrix)

## Sources

- Statics 1 Lectures 4b and 11a
