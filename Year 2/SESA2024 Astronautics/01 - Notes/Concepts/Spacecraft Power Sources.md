---
title: "Spacecraft Power Sources"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["RTG", "radioisotope thermoelectric generator", "fuel cell", "solar dynamic", "primary and secondary power"]
tags: [sesa2024, concept, power]
status: lectured
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
related_concepts: ["[[Solar Cells and Arrays]]", "[[Battery Sizing]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf", "Fortescue, Stark and Swinerd, Spacecraft Systems Engineering, Ch. 10"]
---

# Spacecraft Power Sources

A spacecraft's primary power source supplies its electrical energy over the mission, and a secondary source stores energy for when the primary is unavailable; the options are solar arrays, batteries, fuel cells, solar dynamic systems, RTGs and nuclear reactors.

Solar arrays are the primary source for almost every Earth-orbiting spacecraft, with batteries as the secondary source through eclipse. Arrays convert 10–20 % of the 1370 W/m² solar flux, and the flux falls with the square of the distance from the Sun, to about 5.5 W/m² of electrical output at Jupiter and 1.4 W/m² at Saturn for a 10 % cell, so beyond about 5 AU other sources take over.

An RTG converts the heat of decaying plutonium-238 into electricity through thermocouples (the Seebeck effect): about 200 W from a unit roughly 1 m long and 40 kg, for decades, which is why the Voyagers still work. It emits heat continuously from integration to orbit and is tightly regulated. Fuel cells react hydrogen and oxygen for kilowatts over short missions and produce drinking water, which suits crewed flight. Primary (non-rechargeable) batteries suit short, low-power missions such as launchers. Solar dynamic systems heat a working fluid to drive a turbine: efficient but heavy and complex. Nuclear reactors are the only option for very high power over very long missions, but are currently not used.

The selection chart plots power against mission duration, and the Sun distance then decides between arrays and RTGs for long missions.

## Related

- [[SESA2024 08 - Electrical Power Subsystem#1. Power sources|Power sources in the lecture note]]
- [[Solar Cells and Arrays]] · [[Battery Sizing]]
