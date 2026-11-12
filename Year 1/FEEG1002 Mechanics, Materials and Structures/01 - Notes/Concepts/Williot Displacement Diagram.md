---
title: "Williot Displacement Diagram"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["displacement diagram", "truss deformation", "compatibility of truss joints"]
tags: [feeg1002, concept, statics, trusses, deflection]
status: complete
parent_lectures: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
related_concepts: ["[[Method of Joints and Method of Sections]]", "[[Stress, Strain and Young's Modulus]]"]
sources: ["Statics 1 Lecture 4"]
---

# Williot Displacement Diagram

A displacement diagram finds how far a joint of a pin-jointed truss moves, given the changes in length of the bars that meet there. Each bar's change in length is laid off along the bar, a line perpendicular to the bar is drawn through its end, and the joint's displacement is where those perpendiculars cross.

The construction starts from the bar forces. Each bar is a spring, so it changes length by $\Delta L=FL/EA$, lengthening in tension and shortening in compression. The joint has to stay connected to every bar meeting it, so its displacement is limited by compatibility: each bar may change length and also rotate about its other end. A rotation moves the bar's free end along an arc, but the displacements are tiny next to the bar lengths (micrometres on metres), so the arc can be replaced by its tangent, the line perpendicular to the bar. With two bars meeting at a joint whose other ends are fixed, the two perpendiculars cross at one point, which is the joint's new position.

The algebraic form of the same statement is that the displacement $\mathbf u$ of the joint, resolved along each bar's unit vector $\mathbf e_i$, equals that bar's change in length, $\mathbf u\cdot\mathbf e_i=\Delta L_i$. Two bars give two linear equations for the two components of $\mathbf u$, which is also what the stiffness method automates for large trusses.

When two bars meet at a small angle $\theta$ the joint is held firmly along them but loosely across them, and the movement across them is amplified by roughly $1/\sin\theta$. That is why a joint can move several times further than any bar changes length.

![[s1_williot_displacement.png|860]]

## Related

- Topic notes: [[FEEG1002 A2 - Pin-Jointed Trusses#7. Truss deformation|A2, truss deformation]] · [[FEEG1002 A2 - Pin-Jointed Trusses#The displacement diagram|A2, the displacement diagram]] · [[FEEG1002 A2 - Pin-Jointed Trusses#Vector form of the same result|A2, vector form]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Extra Q3 - Displacement of a three-bar truss|Tutorial 2 Extra Q3]]
- Concepts: [[Method of Joints and Method of Sections]] · [[Stress, Strain and Young's Modulus]]
- Year 2: the [[Unit Load Method]] gives the same displacements without drawing, in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
