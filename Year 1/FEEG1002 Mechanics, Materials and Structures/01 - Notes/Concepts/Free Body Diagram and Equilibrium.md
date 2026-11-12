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
sources: ["Statics 1 Lectures 1-2"]
---

# Free Body Diagram and Equilibrium

A **free body diagram** isolates a body, or part of one, and replaces everything it touches with the forces and moments those contacts exert on it. A body in **static equilibrium** has no acceleration, so the resultant force and the resultant moment about any point are both zero:

$$
\sum F_x=0,\qquad\sum F_y=0,\qquad\sum M_A=0
$$

In two dimensions that is three independent equations per body, so at most three unknowns can be found from one free body diagram.

Each support contributes the reactions that stop the movements it prevents. A pin stops translation in both directions and gives two force components; a roller stops movement normal to its surface only and gives one force, which can be up or down; a built-in support stops translation and rotation and gives two forces and a moment. Unknowns are drawn in an assumed direction, and a negative answer means the actual direction is opposite.

Moments can be taken about any point, and the choice decides how much algebra follows. Taking moments about a point on the line of action of an unknown removes it from the equation, so the best point is where two unknown forces cross. A seesaw or a crane is solved this way in one line.

Moving the boundary of the free body diagram is the idea behind all of Statics 1. Cutting through a cable, a truss bar or a beam turns the internal force at the cut into an external force on the isolated part, which equilibrium can then find. That is the method of joints and the method of sections for trusses and the shear force and bending moment for beams. A distributed load can be replaced by its resultant at its centroid when finding reactions, but not when finding the internal forces inside the loaded length, since a cut there takes only part of the load.

![[s1_seesaw_moment_point.png|760]]

## Related

- Topic notes: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Free body diagrams|A1, free body diagrams]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#2. Equilibrium|A1, equilibrium]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Load off centre: the lever rule|A1, lever rule]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#2. Internal forces|A3, internal forces]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]]
- Concepts: [[Method of Joints and Method of Sections]] · [[Static Determinacy]] · [[Stress, Strain and Young's Modulus]]
- Dynamics, where the resultant equals $m\mathbf a$ instead of zero: [[FEEG1002 D1 - Linear Motion of Particles]]
