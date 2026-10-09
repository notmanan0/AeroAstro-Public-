---
title: "Dependent Motion and Pulley Constraints"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["pulley kinematics", "cord length constraint", "mechanical advantage", "dependent motion"]
tags: [feeg1002, concept, dynamics, kinematics, pulleys]
status: complete
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
related_concepts: ["[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]", "[[Work-Energy Principle]]"]
sources: []
---

# Dependent Motion and Pulley Constraints

## Definition

> [!note] Definition
> Blocks joined by an inextensible cord obey **total cord length = constant**. Measure each coordinate from a fixed datum along its own direction of motion. Differentiating gives linked velocities and accelerations: for example $2s_B + s_A = l$ gives $2v_B = -v_A$ and $2a_B = -a_A$.

## Explanation

- **Recipe**:
  1. Define datums.
  2. Write one length equation per cord, omitting constant segments.
  3. Eliminate the intermediate coordinates.
  4. Differentiate, keeping signs.
- **Kinetics**: massless, frictionless pulleys carry **one tension per cord**. A pulley supported by $n$ strands feels $nT$.
- **Mechanical advantage** $n$ multiplies the force but divides the acceleration and speed by $n$. Anchor loads increase, so check them.
- **Energy** is often the quickest route: cord tensions are internal and do no net work (Tutorial 3 Q4).

## Examples

- **Two cords** (Lecture 1): $s_A + 2s_C = l_1$ and $2s_B - s_C = l_2$ give $v_A = -4v_B$ and a $4T$ lift.
- **Tutorial 1 Q11**: $a_A = 2a_D$ and $T = 1240$ N.

![[d_pulley_constraints.png|760]]

## Related

- Topic notes: [[FEEG1002 D1 - Linear Motion of Particles]]
- Concepts: [[Kinematic Relations for Rectilinear Motion]] · [[Newton's Laws of Motion]] · [[Work-Energy Principle]]
- Year 2: Constraint equations and degrees of freedom are the same idea as the boundary conditions and DOF counting in FE ([[Boundary Conditions and Rigid Body Modes]])

## Sources

- Dynamics Lecture 1.4
