---
title: "Hohmann Transfer"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["Hohmann transfer orbit", "two-burn transfer", "GTO", "impulsive transfer"]
tags: [sesa2024, concept, orbital-mechanics, orbital-transfer]
status: lectured
parent_lectures: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]", "[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
related_concepts: ["[[Vis-Viva Equation]]", "[[Tsiolkovsky Rocket Equation]]", "[[Orbit Control Cycle]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Hohman transfers_V2.pdf"]
---

# Hohmann Transfer

A Hohmann transfer moves a spacecraft between two coplanar circular orbits with two impulsive prograde burns, using a transfer ellipse whose periapsis touches the inner circle and whose apoapsis touches the outer one.

An impulsive burn changes velocity at one point without moving the spacecraft, so the orbits before and after a burn share that point. Two separate circles need at least two burns, and putting both at the apses of the transfer ellipse means the thrust is along the velocity with no gravity loss. With $a_T=(r_1+r_2)/2$,

$$
\Delta V_{Tp}=\sqrt{\frac{\mu}{r_1}}\left(\sqrt{\frac{2r_2}{r_1+r_2}}-1\right),
\qquad
\Delta V_{Ta}=\sqrt{\frac{\mu}{r_2}}\left(1-\sqrt{\frac{2r_1}{r_1+r_2}}\right),
\qquad
t_T=\pi\sqrt{\frac{a_T^3}{\mu}}.
$$

The course's standard example is a 200 km parking orbit to GEO: 2.455 plus 1.477 km/s, 3.93 km/s in total, in 5.26 h. With an apogee engine of $V_{ex}=2.5$ km/s, the circularisation burn alone uses about 45 % of the spacecraft's mass, which is why GEO satellites are roughly half propellant at launch. Normalised by the inner circular speed, the total ΔV peaks at $0.536V_1$ when $r_2/r_1=15.58$.

It is the minimum-ΔV two-impulse transfer between coplanar circles, but it is slow for distant targets (years to the outer planets), needs the target correctly phased (a launch window), and does not cover plane changes or low-thrust electric propulsion, which spirals out instead. In Chapter 11 a small Hohmann transfer restores the altitude a remote-sensing satellite loses to drag.

![[ast_hohmann_leo_geo.png|560]]

## Related

- [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer#2. The Hohmann transfer|Derivation in the lecture note]] · [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer#200 km parking orbit to GEO|Worked example]]
- [[Vis-Viva Equation]] · [[Tsiolkovsky Rocket Equation]] · [[Orbit Control Cycle]]
