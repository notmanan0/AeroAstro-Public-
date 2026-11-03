---
title: "Turbine Entry Temperature and Blade Cooling"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["TET", "combustor outlet temperature", "film cooling", "thermal barrier coating", "blade cooling"]
tags: [sesa2023, concept, cycle-analysis, materials]
status: complete
parent_lectures: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Brayton Cycle]]", "[[Turbojet]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# Turbine Entry Temperature and Blade Cooling

The **turbine entry temperature** $T_{04}$, the combustor outlet temperature, is the peak temperature of the cycle. Raising $T_{04}/T_{02}$ increases both the efficiency and the specific work, but turbine materials limit it, and cooling air is what lets it exceed the metal's own temperature limit.

A higher turbine entry temperature improves the efficiency of the irreversible cycle, raises the specific work considerably, so the core can be smaller and lighter for the same thrust, and raises the optimum pressure ratio. Against that come creep, oxidation and thermal fatigue in the materials, the cooling air and its losses, NOₓ, which rises steeply with temperature, shorter life with more maintenance, and cost. Single-crystal nickel superalloys melt at about 1500 K.

| Condition | $T_{02}$ (K) | $T_{04}$ (K) | $T_{04}/T_{02}$ |
|---|---|---|---|
| Take-off | 288 | 1750 | 6.07 |
| Top of climb | 245 | 1600 | 6.52 (highest rpm) |
| Cruise | 245 | 1500 | 6.11 (dominates life) |

Blades are cooled convectively through internal passages, by film cooling from holes and slots that lay down a protective cool layer, and with low-conductivity ceramic thermal barrier coatings worth about 100 K; ceramic matrix composites may follow once their toughness improves. Cooling has a cost, though. It takes 15–25 % of the compressor air, at 800–900 K, which has been compressed but bypasses the combustor, loses pressure in the passages and mixes irreversibly, so there is an optimum turbine entry temperature for efficiency. GasTurb models the cooling as a bypass flow mixing back in part-way through the turbine. In Table 2, 10 % cooling air costs 2.1 efficiency points (57.8 % to 55.7 %), while in PS7 raising the turbine entry temperature from 1500 K to 1600 K at a 245 K inlet raises $w_{net}$ from 361 to 411 kJ/kg.

With the compressor work and overall pressure ratio fixed (2024-25 Q3(ii)), a higher turbine entry temperature needs a smaller turbine pressure ratio to supply the same work, which leaves a larger nozzle pressure ratio, a higher $V_j$ and more thrust.

## Related

- [[Brayton Cycle]] · [[Turbojet]]
- SESA2028 materials: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|SESA2028 M8 high-temperature materials]] · [[Thermal Barrier Coatings]] · [[Single Crystal Casting]] · [[Gamma Prime Strengthening]]
