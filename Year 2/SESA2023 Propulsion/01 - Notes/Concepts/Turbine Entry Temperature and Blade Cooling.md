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

## Definition

> [!note] Definition
> The **turbine entry temperature** $T_{04}$ (the combustor outlet temperature) is the peak cycle temperature. Raising $T_{04}/T_{02}$ increases both efficiency and specific work, but turbine materials limit it. Cooling air lets TET exceed the metal temperature limit.

## Explanation
**Benefits**:
- higher cycle efficiency (for an irreversible cycle);
- much higher specific work, so a smaller and lighter core for the same thrust;
- a higher optimum pressure ratio.

**Costs**:
- materials: creep, oxidation, thermal fatigue;
- cooling air and its losses;
- NOₓ, which rises steeply with temperature;
- shorter life and higher maintenance;
- cost.

**Typical values**:

| Condition | $T_{02}$ (K) | $T_{04}$ (K) | $T_{04}/T_{02}$ |
|---|---|---|---|
| Take-off | 288 | 1750 | 6.07 |
| Top of climb | 245 | 1600 | 6.52 (highest rpm) |
| Cruise | 245 | 1500 | 6.11 (dominates life) |

Single-crystal Ni superalloys melt at about 1500 K.

**Cooling technologies**:
- **Convective**: internal passages.
- **Film**: holes and slots lay a protective cool layer.
- **Thermal barrier coatings** (low-conductivity ceramic): about 100 K of benefit.
- Future ceramic matrix composites (toughness is still an issue).

**Trade-off**: 15–25 % of compressor air (800–900 K) is used. It is compressed but bypasses the combustor, it loses pressure in the passages, and it mixes irreversibly. So there is an optimum TET for efficiency. GasTurb models cooling as a bypass flow mixing back in part-way through the turbine.

**Effect on pressure ratios** (2024-25 Q3(ii)), with a fixed compressor work and OPR:
- a higher TET needs a **smaller turbine pressure ratio** to supply the same work;
- that leaves a **larger nozzle pressure ratio**, so a higher $V_j$ and more thrust.

## Examples
- Table 2: 10 % cooling air costs 2.1 efficiency points (57.8 % → 55.7 %).
- PS7: raising TET from 1500 K to 1600 K at 245 K inlet raises $w_{net}$ from 361 to 411 kJ/kg.

## Related
- [[Brayton Cycle]] · [[Turbojet]]

**Related (SESA2028 materials):** [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|SESA2028 M8 high-temperature materials]] · [[Thermal Barrier Coatings]] · [[Single Crystal Casting]] · [[Gamma Prime Strengthening]]

## Sources
- Weeks 6–7 handout §6.7; Lecture 17
