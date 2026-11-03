---
title: "Orbital Angular Momentum"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["orbital moment of momentum", "moment of momentum", "specific angular momentum", "h = r x V", "rpVp = raVa"]
tags: [sesa2024, concept, orbital-mechanics]
status: lectured
parent_lectures: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
related_concepts: ["[[Kepler's Laws]]", "[[Vis-Viva Equation]]", "[[Nodal Regression (J2)]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf"]
---

# Orbital Angular Momentum

The orbital moment of momentum $h$ is the angular momentum of an orbiting body per unit mass, $\mathbf h=\mathbf r\times\mathbf V$, with magnitude $h=r^2\dot\theta=rV\sin\alpha$, where $\alpha$ is the angle between the radius and the velocity.

It is constant on any two-body orbit because gravity is a central force: it acts along $\mathbf r$, so it exerts no torque about the central body. In the derivation this appears as the transverse equation of motion $2\dot r\dot\theta+r\ddot\theta=0$, which is $\frac1r\frac{d}{dt}(r^2\dot\theta)=0$.

Three results follow. The direction of $\mathbf h$ is fixed, so the orbit plane is fixed in inertial space; only a perturbation such as the Earth's $J_2$ bulge can turn it (see [[Nodal Regression (J2)]]). The area rate $\dot A=h/2$ is constant, which is Kepler's second law. And at periapsis and apoapsis, where the velocity is perpendicular to the radius, $r_pV_p=r_aV_a$, so the speed ratio between the apses is the inverse of the radius ratio.

Comparing the orbit equation with the polar ellipse gives its size in terms of the orbit's shape:

$$
h=\sqrt{\mu a(1-e^2)}=\sqrt{\mu p},
$$

with $p$ the semi-latus rectum. For a circular orbit this reduces to $h=\sqrt{\mu r}=rV_{\text{circ}}$.

## Related

- [[SESA2024 02 - Kepler's Laws and the Orbit Equation#Transverse equation: angular momentum is conserved|Derivation in the lecture note]]
- [[Kepler's Laws]] · [[Vis-Viva Equation]] · [[Orbit Equation and Conic Sections]]
