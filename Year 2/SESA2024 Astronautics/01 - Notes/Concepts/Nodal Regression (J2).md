---
title: "Nodal Regression (J2)"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["nodal regression", "J2", "oblateness perturbation", "RAAN drift", "nodal precession"]
tags: [sesa2024, concept, orbital-mechanics, perturbations]
status: lectured
parent_lectures: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
related_concepts: ["[[Sun-Synchronous Orbit]]", "[[Orbital Angular Momentum]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-12-09.txt"]
---

# Nodal Regression (J2)

Nodal regression is the slow rotation of an orbit plane about the Earth's polar axis, which moves the ascending node along the equator, caused by the Earth's equatorial bulge; its strength is described by the coefficient $J_2=1.0826\times10^{-3}$.

The Earth is oblate: its equatorial radius exceeds its polar radius by about 21 km. The bulge adds a small pull towards the equatorial plane whenever a spacecraft is north or south of it, which has a component normal to the orbit and so exerts a torque on it. The orbit's angular momentum responds like a gyroscope: instead of tipping, $\mathbf h$ precesses about the polar axis, and the node moves a little each orbit. For a circular orbit

$$
\dot\Omega=-\frac32J_2\sqrt\mu\,R_E^2\,a^{-7/2}\cos i=-2.0647\times10^{14}\,a^{-7/2}\cos i\ \text{deg/day},
$$

with $a$ in km. The rate falls steeply with altitude ($a^{-7/2}$). It is westward for prograde orbits, zero for exactly polar ones, and eastward for retrograde ones.

The course uses it constructively: choosing $a$ and $i>90^\circ$ so that $\dot\Omega=+0.9856^\circ$/day makes the orbit Sun-synchronous at no propellant cost. Elsewhere it is a nuisance to be allowed for, for example in the drift between planes of a constellation or a fragment cloud.

## Related

- [[SESA2024 12 - Sun- and Earth-Synchronous Orbits#2. Nodal regression from the Earth's oblateness|Nodal regression in the lecture note]]
- [[Sun-Synchronous Orbit]] · [[Orbital Angular Momentum]] · [[Momentum Bias and Gyroscopic Rigidity]]
