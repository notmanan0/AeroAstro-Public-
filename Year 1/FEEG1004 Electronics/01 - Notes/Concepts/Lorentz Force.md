---
title: "Lorentz Force"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["Lorentz force", "F = BIL", "F = q(E + v x B)", "Fleming's left-hand rule", "motor effect"]
tags: [feeg1004, concept, magnetism, force]
status: complete
parent_lectures: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
related_concepts: ["[[Back EMF and Torque Constants]]", "[[Faraday's Law and Lenz's Law]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W03-2ab Magnetism and Induction - Recorded.pdf"]
---

# Lorentz Force

## Definition

> [!note] Definition
>
> $$\mathbf F = q(\mathbf E + \mathbf v\times\mathbf B),\qquad F = BIL\ \ \text{(straight wire, }\mathbf B\perp\mathbf L)$$

## Explanation
- The magnetic force is perpendicular to both velocity and field, so it bends paths but does no work on a free charge.
- **Direction**: Fleming's **left-hand rule** (Field, Current, Motion) for positive charge or conventional current. Reverse it for negative charges.
- The wire result follows from $q\mathbf v = I\mathbf L$.
- Parallel currents attract and antiparallel currents repel.
- In a motor, $F = BIL$ on each armature conductor times radius $D/2$ gives the torque ([[Back EMF and Torque Constants]]).

## Examples
- Tutorial 5 Q3: 1 kA over 10 m in $10^{-4}$ T gives 1 N, vertical.
- Particle tracks in a field out of the page reveal the sign of the charge by the curvature direction.

![[ee_c1_motor_generator_effect.png|640]]

## Related
- Topic notes: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Concepts: [[Motional EMF in Electric Machines]] · [[Electric and Magnetic Loading]]
- Cross-module: magnetorquers, [[Attitude Sensors and Torquers]]

## Sources
- Recorded lecture 2b; Sharkh machines notes §2.2
