---
title: "Nodal Regression (J2)"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["nodal regression", "J2", "Earth oblateness", "RAAN drift", "precession of the node"]
tags: [sesa2024, concept, orbital-mechanics, perturbations]
status: complete
parent_lectures: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
related_concepts: ["[[Sun-Synchronous Orbit]]", "[[Orbital Angular Momentum]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Sun and Earth synchronous orbits_V1.pdf"]
---

# Nodal Regression (J2)

## Definition

> [!note] Definition
> The Earth's equatorial bulge (about 21 km) torques an inclined orbit, so its angular momentum vector **precesses** and the node drifts:
>
> $$\dot\Omega = -2.0647\times10^{14}\,a^{-3.5}\cos i\quad(^\circ/\text{day},\ a\text{ in km, positive East})$$
>
> Equivalently: $\dot\Omega = -\tfrac32J_2\left(\dfrac{R_E}{a}\right)^2\sqrt{\dfrac{\mu}{a^3}}\cos i$, with $J_2 = 1.0826\times10^{-3}$.

## Explanation
- The gravity of the bulge does not point to the Earth's centre. Its tangential components give a torque on the orbit.
- That torque precesses $\mathbf h$ like a gyroscope (compare the bicycle-wheel demo in Ch 6), so the node **regresses** along the equator.

| $i$ | Node motion |
|---|---|
| < 90° | West |
| = 90° | none |
| > 90° | East |

- The effect scales as $a^{-3.5}$, so it is strongest in low orbits.
- The numerical constant matches the $J_2$ formula to 0.003 %.
- It is an **inertial-frame** rate.

## Examples
- 800 km, $i = 0$: $\dot\Omega = -6.59^\circ$/day. At $i = 98.6^\circ$: +0.986°/day (Sun-synchronous).
- 2015/16 Q4 gave the full $J_2$ form, with $\dot\Omega_{SunSyn}$ = 1.991 × 10⁻⁷ rad/s.
- Mars (2021/22 B3): $\dot\Omega = -1.7617\times10^{-4}(R_M/a)^{3.5}\cos i$ °/s, set equal to 360°/(Mars year in s).

## Related
- [[Sun-Synchronous Orbit]] · [[Orbital Angular Momentum]] · [[Momentum Bias and Gyroscopic Rigidity]]

## Sources
- Chapter 11 Sun-synchronous lecture, slides 11–19
