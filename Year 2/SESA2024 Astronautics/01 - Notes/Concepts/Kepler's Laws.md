---
title: "Kepler's Laws"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["Kepler's laws of planetary motion", "Kepler 1", "Kepler 2", "Kepler 3", "orbital period"]
tags: [sesa2024, concept, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]"]
related_concepts: ["[[Orbit Equation and Conic Sections]]", "[[Orbital Angular Momentum]]", "[[Vis-Viva Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf"]
---

# Kepler's Laws

## Definition

> [!note] Definition
> 1. **Ellipse law (1609)**: each orbit is an ellipse with the central body at one **focus**.
> 2. **Area law (1609)**: the radius vector sweeps **equal areas in equal times**, so $\dot A = h/2$ is constant.
> 3. **Harmonic law (1619)**: $\tau^2\propto a^3$. Precisely:
>
> $$\tau = 2\pi\sqrt{\frac{a^3}{\mu}},\qquad\mu = GM$$

## Explanation
- They are empirical (from Tycho Brahe's data). Newton (1687) showed they follow from an **inverse-square** central force.
- Law 1 comes from the radial equation of motion, $u''+u = \mu/h^2$.
- Law 2 comes from conservation of angular momentum (a central force exerts no torque).
- Law 3 comes from area ÷ area rate: $\tau = \pi ab/(h/2)$ with $h^2 = \mu a(1-e^2)$.
- **$\tau$ depends only on $a$**. Orbits with the same $a$ have the same period whatever $e$ is.
- Consequence of law 2: fastest at periapsis, slowest at apoapsis ($r_pV_p = r_aV_a$).
- Constants: $\mu_E$ = 398 600 km³/s²; $\mu_{Sun}$ = 1.327 × 10¹¹ km³/s².

## Examples
- GEO: $\tau$ = 86 164 s gives $a$ = 42 164 km.
- ISS at 6780 km: 15.55 orbits/day.
- 700 / 800 / 900 km: $\tau$ = 5926 / 6052 / 6179 s.
- Ratio form (2024/25 B1): 6 asteroid orbits per 5 Earth orbits gives $a = (5/6)^{2/3}$ AU = 0.886 AU.
- A smaller orbit is faster in angular terms: RemoveDebris pulls ahead of the ISS.

## Related
- [[Orbit Equation and Conic Sections]] · [[Orbital Angular Momentum]] · [[Vis-Viva Equation]]

## Sources
- Chapter 5 Lectures 1–3
