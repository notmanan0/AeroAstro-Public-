---
title: "Keplerian Orbital Elements"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["orbital elements", "classical orbital elements", "ephemerides", "RAAN", "right ascension of the ascending node", "argument of perigee", "inclination", "true anomaly", "First Point of Aries"]
tags: [sesa2024, concept, orbital-mechanics]
status: lectured
parent_lectures: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]"]
related_concepts: ["[[Orbit Equation and Conic Sections]]", "[[Local Solar Time and RAAN]]", "[[Sun-Synchronous Orbit]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_orbital elements and conic sections_2025-26_V2.pdf"]
---

# Keplerian Orbital Elements

The six Keplerian elements are the numbers that fix a two-body orbit and the spacecraft's position on it: semi-major axis $a$, eccentricity $e$, inclination $i$, right ascension of the ascending node $\Omega$, argument of perigee $\omega$ and true anomaly $\theta$.

Two describe the size and shape of the orbit in its own plane ($a$ and $e$), three orient it in space ($i$, $\Omega$, $\omega$) and one locates the spacecraft ($\theta$). In unperturbed motion only $\theta$ changes. The inclination is the angle between the orbit plane and the equator, measured at the ascending node, the point where the spacecraft crosses the equator heading north; $i>90^\circ$ means a retrograde orbit. $\Omega$ is measured in the equatorial plane from the First Point of Aries ♈, the direction of the Sun from the Earth at the March equinox, which lies along the intersection of the equator and the ecliptic. $\omega$ is measured in the orbit plane, in the direction of motion, from the ascending node to periapsis, and $\theta$ from periapsis to the spacecraft.

Some elements are undefined in common cases. An equatorial orbit ($i=0$) has no node, so $\Omega$ is undefined, and a circular orbit ($e=0$) has no periapsis, so $\omega$ is undefined; GEO is both. Real orbits are perturbed, and the Earth's oblateness in particular turns $\Omega$, which Sun-synchronous orbits exploit.

Mission analysis consists of choosing these six values from the payload's needs, with $\Omega$ usually fixed through the local solar time of the node (see [[Local Solar Time and RAAN]]).

## Related

- [[SESA2024 03 - Orbital Elements and Conic Sections#2. The orientation elements: i, Ω and ω|Orientation elements in the lecture note]] · [[SESA2024 03 - Orbital Elements and Conic Sections#When elements are undefined|Undefined cases]]
- [[Orbit Equation and Conic Sections]] · [[Local Solar Time and RAAN]] · [[Sun-Synchronous Orbit]]
