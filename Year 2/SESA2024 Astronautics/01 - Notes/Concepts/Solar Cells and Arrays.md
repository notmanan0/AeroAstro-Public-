---
title: "Solar Cells and Arrays"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["solar cell", "solar array", "I-V curve", "maximum power point", "packing efficiency", "BOL and EOL", "array sizing"]
tags: [sesa2024, concept, power]
status: lectured
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
related_concepts: ["[[Battery Sizing]]", "[[Spacecraft Power Sources]]", "[[Eclipse Duration]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 Chapter 8 - Power - prerecord slides.pdf", "02 - Sources/Lectures/SESA2024 Lecture Chapter 8 - Power - prerecorded material.txt"]
---

# Solar Cells and Arrays

A solar cell is a p–n semiconductor junction in which photons with more energy than the band gap free electrons and drive a current; cells wired in series (for voltage) and parallel (for current) on a panel form a solar array.

Efficiency is limited because each junction is tuned to one band gap: lower-energy photons do nothing and the excess energy of higher-energy ones becomes heat. Production silicon cells reach a little over 10 %, gallium arsenide about 20 %, and multi-junction cells more. A cell's current and voltage depend on its load, between the short-circuit current $I_{sc}$ and the open-circuit voltage $V_{oc}$; the power $IV$ peaks at the maximum power point, which the regulator tracks, and operating away from it is one way to shed surplus power.

Output falls with temperature (0.44 %/°C for silicon, 0.16 %/°C for GaAs), so arrays need a radiating back face and give a power surge leaving eclipse when they are cold. It falls roughly as $\cos\theta$ with the off-Sun angle, and it degrades with radiation over the mission, so arrays are sized for end of life and over-produce at the start. Wiring gaps give a packing efficiency below 1.

The array area for an end-of-life power $P$ (load plus battery recharge) is

$$
A=\frac{P}{S\cos\theta\;\eta\;\eta_p\,(1-D)},
$$

which gives 13.2 m² for the course's 1 kW, 800 km example.

![[ast_solar_cell_iv.png|600]]

## Related

- [[SESA2024 08 - Electrical Power Subsystem#2. Solar cells|Solar cells in the lecture note]] · [[SESA2024 08 - Electrical Power Subsystem#Array|Array sizing]]
- [[Battery Sizing]] · [[Spacecraft Power Sources]] · [[Eclipse Duration]]
