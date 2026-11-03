---
title: "Kepler's Laws"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["Kepler's laws of planetary motion", "Kepler 1", "Kepler 2", "Kepler 3", "orbital period", "mean motion"]
tags: [sesa2024, concept, orbital-mechanics]
status: lectured
parent_lectures: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]"]
related_concepts: ["[[Orbit Equation and Conic Sections]]", "[[Orbital Angular Momentum]]", "[[Vis-Viva Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf", "Fortescue, Stark and Swinerd, Spacecraft Systems Engineering, Ch. 4"]
---

# Kepler's Laws

Kepler's three laws say that an orbit is an ellipse with the central body at one focus, that the radius line sweeps out equal areas in equal times, and that the square of the period is proportional to the cube of the semi-major axis.

Kepler fitted them to Tycho Brahe's naked-eye planetary data between 1609 and 1619 without any physical explanation. Newton later derived all three from $F=ma$ and inverse-square gravity, and they hold for any two-body orbit, a satellite around the Earth as much as a planet around the Sun.

Each law corresponds to one result of the derivation. The first is the orbit equation $r=(h^2/\mu)/(1+e\cos\theta)$, which matches the polar ellipse $r=a(1-e^2)/(1+e\cos\theta)$ when $a(1-e^2)=h^2/\mu$. The second is conservation of angular momentum: the area rate is $\dot A=\tfrac12r^2\dot\theta=h/2$, a constant, so a body moves fastest near periapsis. The third comes from dividing the ellipse area $\pi ab$ by $h/2$:

$$
\tau=2\pi\sqrt{\frac{a^3}{\mu}},\qquad n=\frac{2\pi}{\tau}=\sqrt{\frac{\mu}{a^3}}.
$$

The period depends only on $a$ and $\mu$, not on $e$. That makes the third law the most used result in the module: the GEO radius from the sidereal day (42 164 km), orbits per day for a LEO satellite (about 15 to 16), a planet's year, and the transfer time of a Hohmann ellipse. Used as a ratio between two bodies orbiting the same centre, $a_2/a_1=(\tau_2/\tau_1)^{2/3}$, it needs no $\mu$ at all.

## Related

- [[SESA2024 02 - Kepler's Laws and the Orbit Equation#6. Kepler's third law and the period|Derivation of the third law]] · [[SESA2024 02 - Kepler's Laws and the Orbit Equation#Worked examples|Worked examples]]
- [[Orbit Equation and Conic Sections]] · [[Orbital Angular Momentum]] · [[Vis-Viva Equation]]
