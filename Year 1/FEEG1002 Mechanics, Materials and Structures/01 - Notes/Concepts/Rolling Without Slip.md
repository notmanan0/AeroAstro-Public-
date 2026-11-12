---
title: "Rolling Without Slip"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["no slip condition", "v = omega r", "rolling with slip", "rolling resistance", "pure rolling", "rolling condition", "slippage distance"]
tags: [feeg1002, concept, dynamics, rigid-body, rolling]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Instantaneous Centre of Rotation]]", "[[Coulomb Friction]]", "[[Kinetic Energy of a Rigid Body]]", "[[Planar Rigid-Body Equations of Motion]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 07 - Kinematics of Rigid Bodies.pdf", "02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf", "02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf"]
---

# Rolling Without Slip

A wheel rolls without slip when its contact point has the velocity of the surface it touches, zero on fixed ground, so that the arc of rim that has touched the ground equals the distance moved by the centre.

$$
s_G=r\theta,\qquad v_G=r\omega,\qquad a_G=r\alpha
$$

These link the motion of the centre to the rotation only; other points do not obey them. Because the contact point is momentarily at rest it is the instantaneous centre, so the top of the wheel moves at $2v_G$. The contact point still accelerates, at $r\omega^2$ towards the centre.

In the kinetics the no-slip condition replaces a friction law. A wheel's force and moment equations have four unknowns (friction, normal force, $a_G$ and $\alpha$), and the fourth relation is either $a_G=r\alpha$ or $F=\mu_kN$, depending on whether it slips, which is not known in advance. So assume no slip, solve for the static friction needed, and check $F\le\mu_sN$; if the check fails, re-solve with kinetic friction opposing the sliding at the contact and with $a_G$ and $\alpha$ independent. The friction on a wheel driven by a torque acts forwards, while on one pulled at its centre it acts backwards. The lawn roller pushed at its axle needs 94.3 N of friction to roll but only 81.0 N is available, so it slips with $a_G=5.38$ m/s² and $\alpha=16.9$ rad/s².

In energy terms the friction and normal force on a rolling wheel act at a point with zero velocity and do no work. The kinetic energy is $\tfrac12mv^2(1+k^2/r^2)$, so a body rolling down a height $h$ reaches $v=\sqrt{2gh/(1+k^2/r^2)}$ whatever its mass and size: a frictionless block arrives first, then a solid cylinder, then a hollow one. If the wheel slips, kinetic friction does $-F_k\Delta s_{sl}$ over the slippage distance $\Delta s_{sl}=|x_G-R\theta|$, not over the displacement of the wheel.

A rigid wheel rolling freely on level ground would roll for ever. Real wheels slow down because of **rolling resistance**, from deformation and hysteresis of wheel and ground, modelled as a force opposing the motion equal to a fraction of the weight.

The common errors are writing $F=\mu_sN$ for a wheel assumed not to slip and applying $v=\omega r$ to points other than the centre.

![[d_rolling_race_energy_split.png|760]]

## Related

- [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling without slip|kinematics in D7]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling wheel by relative velocity|rolling wheel by relative velocity]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rolling with and without slip|kinetics in D8]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Lawn roller pushed along the ground|lawn roller]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Driven wheel from the mock exam|driven wheel]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling wheels|work on rolling wheels]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling race down a slope|rolling race]]
- [[Instantaneous Centre of Rotation]] · [[Coulomb Friction]] · [[Kinetic Energy of a Rigid Body]] · [[Planar Rigid-Body Equations of Motion]]
