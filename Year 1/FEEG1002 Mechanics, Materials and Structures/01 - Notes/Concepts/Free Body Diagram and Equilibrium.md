---
title: "Free Body Diagram and Equilibrium"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["FBD", "free body diagram", "equilibrium equations", "static equilibrium"]
tags: [feeg1002, concept, statics, equilibrium]
status: complete
parent_lectures: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]", "[[FEEG1002 A2 - Pin-Jointed Trusses]]", "[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
related_concepts: ["[[Stress, Strain and Young's Modulus]]", "[[Method of Joints and Method of Sections]]", "[[Static Determinacy]]"]
sources: []
---

# Free Body Diagram and Equilibrium

## Definition

> [!note] Definition
> A **free body diagram** isolates a body (or part of one) and replaces everything it touches with the forces and moments those contacts exert. A body in **static equilibrium** has zero resultant force and moment:
>
> $$\sum F_x = 0,\qquad \sum F_y = 0,\qquad \sum M_A = 0\ \ (\text{any point A})$$
>
> In 2D that is three independent equations, so at most three unknowns can be found per rigid body.

## Explanation

- **Internal becomes external.** Moving the boundary of the FBD (e.g. cutting a cable, a truss bar or a beam) exposes the internal force at the cut. This one idea underlies the method of joints, the method of sections and SF/BM diagrams.
- **Support reactions**:
  - pin gives $R_x$, $R_y$;
  - roller gives one force normal to the surface (up **or** down);
  - built-in gives $R_x$, $R_y$, $M$.
- Draw unknowns in an assumed positive direction; a negative result means the opposite direction.
- **Moment point**: choose a point through which as many unknowns as possible pass.
- **Two-force members** (truss bars) carry force only along the line joining their pins. **Three-force members** in equilibrium have concurrent (or parallel) forces.
- A distributed load can be replaced by its resultant at its centroid **for equilibrium of the whole body only**, never when finding internal $Q$ and $M$ inside the loaded region.

## Examples

- Crane tipping (Statics 1 Tutorial 1 Q1): $F_B = 0$ at tip-over. Moments about the front axle give $m_{box} = \tfrac34m_{crane} = 3750$ kg.
- Portal crane: $F_A = \dfrac{c}{b+c}F_G$. The support nearer the load carries more of it.
- Dynamics reuses the FBD with the resultant equal to $m\mathbf a$ ([[FEEG1002 D1 - Linear Motion of Particles]]).

## Related

- Topic notes: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] · [[FEEG1002 A2 - Pin-Jointed Trusses]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]
- Concepts: [[Stress, Strain and Young's Modulus]] · [[Method of Joints and Method of Sections]] · [[Static Determinacy]]
- Year 2: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (the resultant is not zero: $\mathbf F = m\dot{\mathbf v}$) · every SESA2028 structures topic

## Sources

- Statics 1 Lecture 1a–b
