---
title: "Space Environment Hazards"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Space Hazards", "Space environment effects", "Natural space environment"]
tags: [sesa1015, concept, astronautics, space-environment]
status: complete
parent_lectures: ["[[SESA1015 A02 - Space Environment]]"]
related_concepts: ["[[Atomic Oxygen Erosion]]", "[[Van Allen Radiation Belts]]", "[[Exponential Atmosphere and Scale Height]]", "[[Blackbody Radiation]]", "[[Launch Environment Loads]]"]
sources: ["Astronautics Part 2 (Environment), pp. 3–38"]
---

# Space Environment Hazards

The space environment hazards are the natural conditions in orbit that degrade or damage a spacecraft: hard vacuum, solar electromagnetic radiation, charged particles (solar wind, solar proton events, galactic cosmic rays and the trapped radiation belts), the residual atmosphere with its atomic oxygen, and debris.

Each hazard has a characteristic effect, and the useful habit is to go from the environment to the effect to the design response:

| Environment | Effect | Typical response |
|---|---|---|
| vacuum | outgassing of resins, adhesives, lubricants; contamination of optics and radiators | low-outgassing materials, bake-out |
| microgravity (free fall) | no convection, propellant not settled, deployments hard to test | conductive and radiative thermal design, propellant management, offloaded ground tests |
| solar UV | embrittled polymers, darkened cover glass, changed optical properties | UV-stable materials and coatings |
| ionising particles | semiconductor and solar-cell degradation, single event upsets, charging | shielding, radiation-tolerant parts, error correction, grounding |
| atmosphere (LEO) | drag and orbit decay; AO erosion of Kapton, silver | orbit-raising, low-erosion materials and coatings |
| debris | hypervelocity impact (70 kJ from a 1 cm aluminium sphere at 10 km/s) | shielding, collision avoidance, redundancy |

The hazards depend strongly on the orbit. Atomic oxygen and drag matter only in LEO and fall off exponentially with height ([[Exponential Atmosphere and Scale Height]], [[Atomic Oxygen Erosion]]); radiation dose behind 5 mm of aluminium rises from about 20 rad/yr at 500 km and 28° to about $6\times10^3$ rad/yr at GEO, because GEO sits in the outer electron belt ([[Van Allen Radiation Belts]]). Most also follow the 11-year solar cycle: at solar maximum the thermosphere heats from about 700 K to about 1500 K, the density at a given LEO altitude rises by about an order of magnitude, and solar proton events become more frequent.

Two kinds of requirement come out of this. Some effects accumulate, such as total dose, AO erosion and UV darkening, and are sized on the mission-integrated environment. Others are single events, such as an upset from one cosmic ray or a debris strike, and are handled statistically and by fault tolerance. An average environment is not enough for either: dose and erosion depend on mission length and solar-cycle phase, and one particle is enough for an upset. The friendly side of the environment (no rain, no wind, no weight to carry) is what allows very light deployable structures, once they have survived launch ([[Launch Environment Loads]]).

## Related

- Topic: [[SESA1015 A02 - Space Environment]]
- Concepts: [[Atomic Oxygen Erosion]] · [[Van Allen Radiation Belts]] · [[Exponential Atmosphere and Scale Height]] · [[Blackbody Radiation]] · [[Space Debris Mitigation]] · [[Launch Environment Loads]]
- Later: [[SESA2024 10 - Thermal Control]] · [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]] · [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]
- Sources: Astronautics Part 2, pp. 3–38
