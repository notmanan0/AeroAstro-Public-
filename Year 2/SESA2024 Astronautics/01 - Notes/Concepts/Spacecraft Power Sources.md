---
title: "Spacecraft Power Sources"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["RTG", "fuel cell", "solar dynamic", "primary power", "secondary power"]
tags: [sesa2024, concept, power]
status: complete
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
related_concepts: ["[[Solar Cells and Arrays]]", "[[Battery Sizing]]", "[[Electric Propulsion Sizing]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf"]
---

# Spacecraft Power Sources

## Definition

> [!note] Definition
> - **Primary power** is the main energy source (solar array, RTG, fuel cell, primary battery).
> - **Secondary power** is energy storage for peaks and eclipse (rechargeable batteries).
> - The requirement is **reliable, continuous** operation, because a power interruption can be catastrophic.

## Explanation
| Source | Principle | Use |
|---|---|---|
| Solar arrays | photovoltaic | Earth orbit to about 5 AU; the default |
| Primary battery | non-rechargeable chemistry | minutes to hours (launchers, probes) |
| Fuel cell | H₂ + O₂ → electricity + **water** | crewed missions of days to weeks (Shuttle, Apollo) |
| Solar dynamic | concentrator heats a fluid, which drives a turbine | more efficient than PV but heavy; rarely used |
| RTG | Pu-238 decay heat → thermocouples (**Seebeck**) | outer planets: Ulysses, Voyager, Galileo, Cassini (~40 kg for ~200 W) |
| Nuclear reactor | fission | very high power |

- **Mission-duration map**: batteries for hours, fuel cells for days to weeks, solar or RTG for years, reactors for high power over years.
- **RTG drawbacks**: heat and radiation affect the launcher and payload; public ("Green lobby") concern about a launch failure dispersing the isotope.

## Examples
- 2018/19 Q3(ii): power sources other than batteries and arrays (4 marks).
- 2015/16 Q1(i): the space environment. RTG choice is driven by distance from the Sun.
- The Pluto EP orbiter's $\beta$ = 5.4 W/kg points to RTGs.

## Related
- [[Solar Cells and Arrays]] · [[Battery Sizing]] · [[Electric Propulsion Sizing]]

## Sources
- Chapter 8 slides 3–8; workbook Ch8 Q1–Q3
