---
title: "Absorptance and Emittance"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["absorptance", "emittance", "solar absorptance", "alpha over epsilon", "Kirchhoff's law", "reflectance", "transmittance", "surface finish"]
tags: [sesa2024, concept, thermal-control]
status: lectured
parent_lectures: ["[[SESA2024 10 - Thermal Control]]"]
related_concepts: ["[[Blackbody Radiation]]", "[[Spacecraft Thermal Balance Equation]]", "[[Passive vs Active Thermal Control]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture 2025-11-20.txt", "02 - Sources/Lectures/SESA2024 Lecture 2025-11-25.txt"]
---

# Absorptance and Emittance

Absorptance is the fraction of incident radiation a surface absorbs, and emittance the ratio of what it emits to what a black body at the same temperature would emit; both lie between 0 and 1.

Incident radiation is absorbed, reflected or transmitted, so $\alpha+\rho+\tau=1$, and for opaque spacecraft surfaces $\alpha+\rho\approx1$. Absorptance depends on wavelength, so the useful number is the total absorptance weighted by the source's spectrum; for sunlight this is the solar absorptance $\alpha_S$, which can be integrated over 0.2–3 μm, where 97 % of the Sun's energy lies. Emittance $\varepsilon$ gives the emission of a real surface as $\varepsilon\sigma T^4$.

Kirchhoff's law says absorptance equals emittance at the same wavelength. A spacecraft near 290 K emits in the same infrared band as the Earth, so its absorptance for Earth infrared can be taken as $\varepsilon$; that is why the Earth term in the balance uses $\varepsilon$, and why an unpowered body's eclipse temperature is independent of its finish.

Sunlight dominates a lit spacecraft's heat input, so its temperature is governed by $\alpha_S/\varepsilon$. White paint (about 0.2/0.9) and optical solar reflectors run cold; black paint (about 0.9/0.9) runs near the black-body value; polished aluminium (about 0.15/0.05) runs hot. Ultraviolet and atomic oxygen degrade finishes over a mission, usually raising $\alpha_S$.

![[ast_thermal_alpha_eps.png|560]]

## Related

- [[SESA2024 10 - Thermal Control#1. Absorption, reflection and transmission|Absorptance in the lecture note]] · [[SESA2024 10 - Thermal Control#4. What the equation tells you|Why the ratio matters]]
- [[Blackbody Radiation]] · [[Spacecraft Thermal Balance Equation]] · [[Passive vs Active Thermal Control]]
