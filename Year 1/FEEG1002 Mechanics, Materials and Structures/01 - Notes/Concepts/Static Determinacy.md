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
sources: ["Statics 1 Lectures 4 and 11"]
---

# Static Determinacy

A structure is **statically determinate** when the equilibrium equations alone fix all its reactions and internal forces. It is a **mechanism** when there are too few members or supports to hold it in shape, and **statically indeterminate** when there are more unknowns than independent equilibrium equations.

For a plane pin-jointed frame with $j$ joints, $m$ bars and $r$ reaction components, each joint supplies two equilibrium equations and each bar or reaction is one unknown, so

$$
2j=m+r\ \text{(determinate)},\qquad 2j>m+r\ \text{(mechanism)},\qquad 2j<m+r\ \text{(indeterminate)}
$$

The count is necessary but not sufficient. One part of a frame can be over-braced while another part has no diagonal at all; the totals still balance, but the frame is a mechanism. The geometry has to be inspected as well.

For a beam under vertical loads the same comparison is made with two equilibrium equations, vertical force and moment. A simply supported beam or a cantilever has two unknown reactions and is determinate; a propped cantilever has three and is indeterminate to the first degree; a beam built in at both ends has four and is indeterminate to the second degree.

An indeterminate structure cannot be solved by equilibrium alone because its load sharing depends on the relative stiffness of its parts. The missing equations come from compatibility, the condition that the deformed parts still fit together and meet the supports. That redundancy is useful, since the structure survives the loss of a member, but it also means that misfit, support settlement or temperature change can set up stresses with no external load at all.

![[s1_truss_static_determinacy.png|860]]

## Related

- Topic notes: [[FEEG1002 A2 - Pin-Jointed Trusses#6. Mechanisms, determinate and indeterminate trusses|A2, mechanisms and determinacy]] · [[FEEG1002 A2 - Pin-Jointed Trusses#The counting test|A2, the counting test]] · [[FEEG1002 A6 - Statically Indeterminate Beams#Counting reactions|A6, counting reactions]]
- Concepts: [[Method of Joints and Method of Sections]] · [[Free Body Diagram and Equilibrium]] · [[Superposition for Indeterminate Beams]]
- Year 2: redundants by [[Castigliano Second Theorem]] in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] · a mechanism appears as a singular stiffness matrix, see [[Boundary Conditions and Rigid Body Modes]]
