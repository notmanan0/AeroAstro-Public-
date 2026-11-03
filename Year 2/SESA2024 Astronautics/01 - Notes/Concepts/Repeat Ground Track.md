---
title: "Repeat Ground Track"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["Earth-synchronous orbit", "Earth synchronism", "repeat parameters", "n and m", "N and M", "ground track"]
tags: [sesa2024, concept, orbital-mechanics, remote-sensing]
status: lectured
parent_lectures: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Sun-Synchronous Orbit]]", "[[Swath Width and Push-Broom Imaging]]", "[[Orbit Control Cycle]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-12-11.txt", "02 - Sources/Lectures/SESA2024 Lecture 9.txt"]
---

# Repeat Ground Track

An Earth-synchronous orbit has a repeat ground track: after $N$ orbits in $M$ days the sub-satellite track returns exactly to where it started, so every point is revisited with the same viewing geometry every $M$ days.

The condition is $N\Delta\lambda=M\times360^\circ$, where $\Delta\lambda$ is the westward step in longitude between successive equator crossings. For a Sun-synchronous orbit that step is the Earth's rotation, $360^\circ\tau/T_{sid}$, less the eastward turn of the plane, $360^\circ\tau/T_{yr}$, and the condition reduces to

$$
\tau=\frac MN\times86\,400\ \mathrm s,
$$

the solar day appearing because the plane keeps pace with the Sun. Kepler's third law then gives $a$, and the regression condition $i$.

For a push-broom imager, full coverage needs the swath to span the track spacing at the equator, $2\pi R_E/N$, so $N\approx2\pi R_E/d$ and $M\approx N\tau/86\,400$, rounded to integers and iterated until the altitude is in range. $N$ and $M$ must have no common factor: $(98,7)$ is the same orbit as $(14,1)$, with only 14 distinct tracks. Drag slowly shortens the period, so the track drifts and has to be held within tolerance by a control cycle.

![[ast_repeat_groundtrack_solutions.png|560]]

## Related

- [[SESA2024 12 - Sun- and Earth-Synchronous Orbits#4. Both at once|Derivation in the lecture note]] · [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission#2. The iteration|The N, M iteration]]
- [[Sun-Synchronous Orbit]] · [[Swath Width and Push-Broom Imaging]] · [[Orbit Control Cycle]]
