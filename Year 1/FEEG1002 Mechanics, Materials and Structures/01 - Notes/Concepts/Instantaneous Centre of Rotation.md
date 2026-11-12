---
title: "Instantaneous Centre of Rotation"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["IC", "instantaneous centre of zero velocity", "ICR", "instant centre", "instantaneous center of rotation"]
tags: [feeg1002, concept, dynamics, rigid-body, kinematics]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Relative Velocity Equation for Rigid Bodies]]", "[[Rolling Without Slip]]", "[[Kinetic Energy of a Rigid Body]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 07 - Kinematics of Rigid Bodies.pdf", "02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf"]
---

# Instantaneous Centre of Rotation

The instantaneous centre of rotation (IC), also called the instantaneous centre of zero velocity, is the point of a body in plane motion, or of its extension, whose velocity is zero at the instant considered; at that instant the body moves as if it were in pure rotation about it.

$$
\mathbf v_P=\boldsymbol\omega\times\mathbf r_{P/IC},\qquad v_P=\omega r_{P/IC}
$$

This is the relative velocity equation $\mathbf v_P=\mathbf v_A+\boldsymbol\omega\times\mathbf r_{P/A}$ with the reference point A chosen at the IC, where $\mathbf v_A=\mathbf 0$. Every point therefore moves perpendicular to its line from the IC, at a speed proportional to its distance from it.

To locate the IC, take two points whose velocity directions are known from the constraints and are not parallel. Each velocity is perpendicular to the line joining its point to the IC, so the IC is where the perpendiculars through the two points meet. For the 1.5 m bar sliding with A on the floor and B on a wall at 30°, the vertical through A and the horizontal through B meet at the corner of the rectangle with the bar as diagonal, giving $r_{A/IC}=0.75$ m and $r_{B/IC}=1.299$ m; with $v_A=3$ m/s, $\omega=4$ rad/s and $v_B=5.20$ m/s, as the relative velocity equation also gives. For a wheel rolling without slip the IC is the contact point, so the top of the wheel moves at $2\omega r$. If the two velocities are parallel and equal, the perpendiculars never meet and the body is momentarily translating with $\omega=0$.

In energy problems the IC gives the kinetic energy in one term, $KE=\tfrac12I_{IC}\omega^2$ with $I_{IC}=I_G+mr_{G/IC}^2$, valid only at the instant considered. For a rod with its ends in a vertical and a horizontal slot, G is the midpoint of the hypotenuse of the triangle formed with the IC, so $r_{G/IC}=L/2$ at every angle.

The IC moves as the body moves and generally has a non-zero acceleration (the contact point of a rolling wheel accelerates at $r\omega^2$ towards the centre), so it gives velocities only and must not be treated as a fixed pivot when finding accelerations.

![[d_sliding_rod_ic.png|560]]

## Related

- [[FEEG1002 D7 - Kinematics of Rigid Bodies#Instantaneous centre of rotation|IC in D7]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling wheel by relative velocity|rolling wheel]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Sliding bar between wall and floor|sliding bar]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#General plane motion and the IC|kinetic energy about the IC]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rod sliding in two slots|rod in two slots]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rod and spring released from rest|rod and spring]]
- [[Relative Velocity Equation for Rigid Bodies]] · [[Rolling Without Slip]] · [[Kinetic Energy of a Rigid Body]]
