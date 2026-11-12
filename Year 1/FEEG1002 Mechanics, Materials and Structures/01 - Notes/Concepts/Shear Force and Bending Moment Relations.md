---
title: "Shear Force and Bending Moment Relations"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["dQ/dx = -w", "dM/dx = Q", "SF and BM relations", "load-shear-moment relations"]
tags: [feeg1002, concept, statics, beams, sfd, bmd]
status: complete
parent_lectures: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]", "[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Engineer's Bending Theory]]", "[[Macaulay's Method]]"]
sources: ["Statics 1 Lectures 5-6"]
---

# Shear Force and Bending Moment Relations

For a beam carrying a downward distributed load $w(x)$, with the shear force $Q$ positive downwards on the right-hand face of the left part and the bending moment $M$ positive when sagging, the load, shear force and bending moment are linked by

$$
\frac{dQ}{dx}=-w,\qquad\frac{dM}{dx}=Q
$$

Both come from the equilibrium of a short element of length $dx$. Vertical equilibrium of the element gives the change in shear force, $dQ=-w\,dx$. Moments about one face give $dM=Q\,dx$, after dropping the $\tfrac12w\,dx^2$ term of the load, which is of second order in $dx$.

The relations turn the diagrams into a sketching exercise. Where there is no load, $Q$ is constant and $M$ linear; under a uniform load $Q$ is linear and $M$ parabolic. A point force makes $Q$ jump by the force, and an applied couple makes $M$ jump by the couple, with a clockwise couple making it jump up. $M$ has a turning point wherever $Q$ passes through zero, and the change in $M$ between two points is the area under the shear force diagram between them. $M$ is zero at pinned, roller and free ends unless a couple is applied there.

A turning point of $M$ is a local extremum only. The largest $|M|$ can also be at a support, under a point load or at a jump caused by a couple, so every candidate has to be checked.

The chain continues into deflection through $EI\,d^2v/dx^2=-M$. Going from $w$ to $v$ is four integrations, each with a constant fixed by a boundary condition, which is how a beam can be solved entirely by integration when the load is a continuous function.

![[s1_beam_element_wqm.png|760]]

## Related

- Topic notes: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#5. Relations between distributed load, shear force and bending moment|A3, the relations]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Procedure for sketching|A3, procedure for sketching]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#When the mathematical maximum is not the largest moment|A3, the largest moment]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Solving by integration|A5, solving by integration]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Engineer's Bending Theory]] · [[Macaulay's Method]]
- Year 2: the same chain in [[SESA2028 S2 - Beam Deflection and Bending Design]] · $Q$ drives [[Shear Flow]] · $M$ drives the unit-load integrals of [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
