---
title: "Keplerian Orbital Elements"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["orbital elements", "classical orbital elements", "RAAN", "argument of perigee", "inclination", "true anomaly"]
tags: [sesa2024, concept, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
related_concepts: ["[[Orbit Equation and Conic Sections]]", "[[Local Solar Time and RAAN]]", "[[Sun-Synchronous Orbit]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_orbital elements and conic sections_2025-26_V2.pdf"]
---

# Keplerian Orbital Elements

## Definition

> [!note] Definition
> Six numbers fix an orbit and the body's position on it:
> - $a$ (size) and $e$ (shape), both in plane;
> - $i$ (plane tilt from the equator, 0–180°), $\Omega$ (RAAN, measured from ♈ to the ascending node) and $\omega$ (argument of perigee, from the node to perigee), which give the orientation;
> - $\theta$ (true anomaly, from perigee), the position.

## Explanation
- **♈, the First Point of Aries**: the Sun direction at the spring equinox, lying in the equatorial plane. It is the inertial datum for $\Omega$.
- **Ascending node**: where the orbit crosses the equator going South → North. $i$ is measured there.
- **Prograde** $i<90^\circ$; **retrograde** $i>90^\circ$ (Sun-synchronous orbits).
- **Undefined**: $\Omega$ when $i = 0$; $\omega$ when $e = 0$.
- In the two-body problem **only $\theta$ changes**. Perturbations ($J_2$, drag, the Sun and Moon) slowly change $\Omega$, $\omega$, $a$ and $e$.
- In mission design **the payload selects the elements**: $i$ for coverage, $e$ for constant range, $a$ for resolution against lifetime, $\Omega$ for the LST.

![[ast_orbital_elements_3d.png|520]]

## Examples
- ISS: 6780 km, $e$ = 0.0005, $i$ = 51°.
- QZSS: 42 164 km, $e$ = 0.075, $i$ = 43°, $\omega$ = 270° (apogee dwell over Japan).
- Molniya (heavens-above activity): high $e$, $i\approx63.4^\circ$, $\omega$ = 270°.
- Exams: estimate $a$, $e$, $i$, $\Omega$ (and $\omega$, $\theta$) from a schematic at the spring equinox (2023/24 A3, 2024/25 A3).

## Related
- [[Orbit Equation and Conic Sections]] · [[Local Solar Time and RAAN]] · [[Sun-Synchronous Orbit]]

## Sources
- Chapter 5 Lectures 3–4
