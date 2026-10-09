---
title: "Method of Joints and Method of Sections"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["method of joints", "method of sections", "truss analysis", "zero-force member"]
tags: [feeg1002, concept, statics, trusses]
status: complete
parent_lectures: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Static Determinacy]]", "[[Williot Displacement Diagram]]"]
sources: []
---

# Method of Joints and Method of Sections

## Definition

> [!note] Definition
> Two ways to find the axial bar forces in a statically determinate pin-jointed truss:
> - **Method of joints**: isolate each pin and apply $\sum F_x = \sum F_y = 0$ (two unknowns per joint).
> - **Method of sections**: cut through at most three bars, isolate one part and apply all three equilibrium equations. Pick moment points where two unknown bar lines intersect, so each equation has one unknown.

## Explanation

- **Tension-positive convention**: draw every cut bar force pointing **away** from the joint. A negative result means compression.
- **Joints** suit small trusses or finding every force; start where only two bars meet an unknown.
- **Sections** suit a few bars in a long truss; never cut through a joint.
- **Zero-force members**:
  - at an unloaded joint with two non-collinear bars, both are zero;
  - at an unloaded joint with three bars, two of them collinear, the third is zero.
  They still stabilise the structure and carry load if the loading changes.
- Sanity check: imagine removing the bar. Would its joints separate (tension) or approach (compression)?

## Examples

- L3 three-bar truss: $F_{BC} = -447$ N, $F_{AC} = +400$ N, $F_{AB} = 0$.
- Warren truss (Tutorial 2 Q2): $F_{DE} = -25$ kN, $F_{GF} = +40$ kN (moments about C), $F_{GC} = 0$.

![[s1_truss_method_of_sections.png|760]]

## Related

- Topic notes: [[FEEG1002 A2 - Pin-Jointed Trusses]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Static Determinacy]] · [[Williot Displacement Diagram]]
- Year 2: [[Unit Load Method]] for truss deflection and [[Castigliano Second Theorem]] for redundant bars in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] · stiffness-method trusses in [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]

## Sources

- Statics 1 Lectures 3b and 4a
