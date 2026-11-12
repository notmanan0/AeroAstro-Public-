---
title: "Relative Velocity Equation for Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["v_B = v_A + omega x r_B/A", "relative motion analysis", "relative acceleration", "relative velocity analysis", "general plane motion kinematics"]
tags: [feeg1002, concept, dynamics, rigid-body, kinematics]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
related_concepts: ["[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]", "[[Normal and Tangential Coordinates]]", "[[Kinetic Energy of a Rigid Body]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 07 - Kinematics of Rigid Bodies.pdf"]
---

# Relative Velocity Equation for Rigid Bodies

For two points A and B on the same rigid body in plane motion, the velocity of B is the velocity of A plus a rotation of B about A at the body's angular velocity.

$$
\mathbf v_B=\mathbf v_A+\boldsymbol\omega\times\mathbf r_{B/A},\qquad\boldsymbol\omega=\omega\mathbf k
$$

An observer translating with A, without rotating, sees B at a fixed distance because the body is rigid, so B can only move on a circle round A. Its relative velocity is therefore $\omega r_{B/A}$, perpendicular to AB. In components the cross product is

$$
\omega\mathbf k\times\mathbf r_{B/A}=-\omega r_y\,\mathbf i+\omega r_x\,\mathbf j
$$

i.e. $\mathbf r_{B/A}$ turned 90° counter-clockwise and scaled by $\omega$, with counter-clockwise positive. The vector equation gives two scalar equations, enough for two unknowns such as $\omega$ and the speed of B, or it can be solved as a velocity triangle. A and B should be points whose directions of motion are known from the constraints: pins, sliders, the centre of a rolling wheel. Each body in a linkage has its own $\omega$.

For the 1.5 m bar with end A on the floor moving at 3 m/s and end B on a wall, at 30° to the floor, the $\mathbf i$ component gives $\omega=4$ rad/s and the $\mathbf j$ component $v_B=-5.20$ m/s, so B moves down the wall. For a wheel rolling without slip, taking the contact point as A (zero velocity) gives $v_G=\omega r$ at the centre, $2\omega r$ at the top and $\sqrt2\,\omega r$ at 45° at the 9 o'clock point. Choosing the reference point with zero velocity is exactly the [[Instantaneous Centre of Rotation]] method.

Differentiating once more gives $\mathbf a_B=\mathbf a_A+\boldsymbol\alpha\times\mathbf r_{B/A}-\omega^2\mathbf r_{B/A}$, with a normal part directed from B towards A. This relative-acceleration form is not assessed in the module; accelerations are found by absolute motion analysis, differentiating a geometric relation between a position and an angle.

The figure follows a crank and connecting rod through one revolution; where the crank pin and the piston move parallel, the rod momentarily translates and its $\omega$ is zero.

![[d_t7_q5_crank_slider.png|620]]

## Related

- [[FEEG1002 D7 - Kinematics of Rigid Bodies#4. Relative velocity analysis|D7 §4]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#The relative velocity equation|derivation]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling wheel by relative velocity|rolling wheel]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Sliding bar between wall and floor|sliding bar]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#5. Relative acceleration analysis|relative acceleration]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#3. Absolute motion analysis|absolute motion analysis]] · [[FEEG1002 D2 - Curvilinear Motion#6. Relative motion of two particles|relative motion of particles]]
- [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]] · [[Normal and Tangential Coordinates]] · [[Kinetic Energy of a Rigid Body]]
- Later: rotating frames and the [[Transport Theorem]] · [[Euler Angles and Rotation Matrices]] · [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]
