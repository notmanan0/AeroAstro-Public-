---
title: "Principle of Angular Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["angular momentum", "moment of momentum", "H = r x mv", "conservation of angular momentum", "central force", "angular impulse"]
tags: [feeg1002, concept, dynamics, angular-momentum]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D5 - Angular Impulse and Momentum]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
related_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Conservative Forces and Potential Energy]]", "[[Orbital Angular Momentum]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 05 - Angular Impulse and Momentum.pdf", "02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf"]
---

# Principle of Angular Impulse and Momentum

The angular momentum of a particle about a fixed point O is the moment of its linear momentum, $\mathbf H_O=\mathbf r\times m\mathbf v$, and the principle of angular impulse and momentum states that the angular impulse of the moments about O over an interval equals the change in $\mathbf H_O$.

$$
(\mathbf H_O)_1+\sum\int_{t_1}^{t_2}\mathbf M_O\,dt=(\mathbf H_O)_2
$$

In plane motion $H_O=mvd=mv'r$, with $d$ the perpendicular distance from O to the line of the velocity and $v'$ the velocity component perpendicular to $\mathbf r$; anticlockwise is positive. Crossing Newton's second law with $\mathbf r$ gives $\sum\mathbf M_O=\mathbf r\times m\dot{\mathbf v}$, and differentiating $\mathbf H_O$ gives the same thing plus $\dot{\mathbf r}\times m\mathbf v$, which is zero only because O is fixed and $\dot{\mathbf r}=\mathbf v$. So $\sum\mathbf M_O=\dot{\mathbf H}_O$, and integrating over time gives the principle.

If the forces have no net moment about O, $H_O$ is conserved. The key case is a **central force**, always directed at a fixed point: a cord to a pivot, a spring pinned at one end, a planet's gravity. Conservation is always about a named point; a satellite's angular momentum is conserved about the Earth's centre and nowhere else. The 120 kg ride car pulled in from 3.6 m to 3.15 m keeps $r_1mv_1=r_2mv_2'$, so $v_2'=1.371$ m/s and, with the 0.15 m/s radial component, $v_2=1.380$ m/s. Conserved angular momentum is not conserved energy: the cable does $\tfrac12m(v_2^2-v_1^2)=27.8$ J of work. Combined with energy conservation, the same idea fixes an orbit: from perigee at $6.976\times10^6$ m and 8333.3 m/s, apogee is at $10.79\times10^6$ m with $v_B=5386$ m/s.

For a rigid body, $H_G=I_G\omega$ and about any point $H_P=\bar{\mathbf r}\times m\mathbf v_G+I_G\omega$; about a fixed axis $H_O=I_O\omega$. A body that changes its own $I$ keeps $I\omega$ constant, as a spinning chair speeds up when the arms come in. The wheel driven from rest by 300 N m for 6 s, with moments taken about the contact point so that friction and the normal force drop out, reaches 11.5 rad/s.

The usual mistakes are to claim conservation without naming the point and to use the full speed instead of $v'$ on a non-circular path.

![[d_elliptical_orbit_example.png|640]]

## Related

- [[FEEG1002 D5 - Angular Impulse and Momentum#1. Moment of a vector|moment of a vector]] · [[FEEG1002 D5 - Angular Impulse and Momentum#2. The moment equation|moment equation]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Conservation of angular momentum|conservation]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Amusement-park ride pulled in on a cable|ride]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Satellite in an elliptical orbit|orbit]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Fun-fair game with an elastic cord|fun-fair game]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#4. Impulse and momentum for rigid bodies|rigid bodies]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Wheel driven by a torque from rest|driven wheel]]
- [[Principle of Linear Impulse and Momentum]] · [[Planar Rigid-Body Equations of Motion]] · [[Conservative Forces and Potential Energy]]
- Year 2: [[Orbital Angular Momentum]] · [[Kepler's Laws]] · [[Vis-Viva Equation]] · momentum exchange in [[Reaction Wheels and Momentum Dumping]] and [[SESA2024 06 - Attitude Control]]
