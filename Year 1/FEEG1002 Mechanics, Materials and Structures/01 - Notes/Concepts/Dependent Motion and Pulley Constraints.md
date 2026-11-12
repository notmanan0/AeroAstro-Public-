---
title: "Dependent Motion and Pulley Constraints"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["pulley kinematics", "cord length constraint", "mechanical advantage", "dependent motion", "constrained motion", "block and tackle"]
tags: [feeg1002, concept, dynamics, kinematics, pulleys]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
related_concepts: ["[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]", "[[Work-Energy Principle]]", "[[Power and Efficiency]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf"]
---

# Dependent Motion and Pulley Constraints

Blocks joined by inextensible cords over pulleys have dependent motion: the constant length of each cord ties their positions together, and differentiating that length gives the links between their velocities and accelerations.

Each block's position is measured from a fixed datum, positive in its direction of motion, and each cord's length is written as the sum of its variable segments plus constant ones (arcs over pulleys, fixed lengths), which can be dropped. With several cords there is one equation per cord, and the intermediate coordinates are eliminated before differentiating once for velocities and twice for accelerations, keeping the signs. For block A pulling a cord that runs down to a movable pulley on block B and back up,

$$
2s_B+h+s_A=l_T\quad\Rightarrow\quad 2v_B+v_A=0,\quad 2a_B=-a_A
$$

Measuring $s_B$ the other way gives $2v_B=v_A$; this is the same physical statement in a different coordinate, so the sign of any result must be read against the datum chosen.

For the kinetics, pulleys are massless and frictionless and the cords massless, so the tension is the same all along one cord. A body hanging on $n$ strands of a cord feels $nT$. This is the **mechanical advantage**: the force on the load is multiplied by $n$, while the load moves $n$ times more slowly than the free end of the cord. The anchors carry the sum of all their strand tensions and must be checked too; with one movable pulley the load sees $2F$ and the anchors $3F$. In the two-cord system of D1, eliminating the intermediate pulley gives $s_A+4s_B=l_1+2l_2$, so $v_A=-4v_B$, the load hangs on $4T$ and the ceiling carries $5T$.

Cord tensions inside a system do no net work, so energy methods skip them: in the motor-driven hoist of D3 the power fed into the cable at the motor, $Tv_P$, equals the power delivered at the block, $2Tv_A$.

![[d_pulley_constraints.png|760]]

## Related

- [[FEEG1002 D1 - Linear Motion of Particles#6. Dependent motion and pulleys|D1 §6]] · [[FEEG1002 D1 - Linear Motion of Particles#Pulley kinetics and mechanical advantage|pulley kinetics]] · [[FEEG1002 D1 - Linear Motion of Particles#Pulley system with a movable pulley|movable-pulley example]] · [[FEEG1002 D2 - Curvilinear Motion#Mine car hoisted by its own motor|mine car]] · [[FEEG1002 D3 - Work, Energy and Power#Motor hoisting a block through a pulley|motor hoist]]
- [[Kinematic Relations for Rectilinear Motion]] · [[Newton's Laws of Motion]] · [[Work-Energy Principle]] · [[Power and Efficiency]]
