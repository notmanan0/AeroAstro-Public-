---
title: "Chemical Propulsion Systems"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["monopropellant", "bipropellant", "hydrazine thruster", "hypergolic", "solid rocket motor", "cold gas thruster", "hybrid rocket"]
tags: [sesa2024, concept, propulsion]
status: complete
parent_lectures: ["[[SESA2024 07 - Spacecraft Propulsion]]"]
related_concepts: ["[[Electric Propulsion Sizing]]", "[[Tsiolkovsky Rocket Equation]]", "[[Rocket Performance Parameters]]"]
sources: ["02 - Sources/Lectures/Chapter 7/Chapter 7 - Propulsion - original slides(1)(1).pdf"]
---

# Chemical Propulsion Systems

## Definition

> [!note] Definition
> Chemical systems are **energy-limited**: the exhaust energy comes from the chemical energy stored in the propellants.
> - $I_{sp}\propto\sqrt{T_c/\mathcal M}$: a high combustion temperature and a light exhaust are best.
> - Types: liquid (mono- or bi-propellant), solid, hybrid, and cold gas (not combustion).

## Explanation
| Type | $I_{sp}$ (s) | ✔ | ✘ |
|---|---|---|---|
| Cold gas (N₂, Ar) | ~50 | simple; tiny impulse bits (~20 mN); clean plume | very low $I_{sp}$ and total impulse |
| Monoprop N₂H₄ | 230–240 (290 augmented) | simple; small minimum impulse; restartable | toxic handling; low $I_{sp}$ |
| Solid | ~260 | simple; storable; high thrust | one-shot; not throttleable |
| Biprop MMH/N₂O₄ | ~310 | hypergolic; restartable; throttleable | complex feed; hazardous; worse dry/wet ratio |
| Biprop LOX/LH₂ | ~450 | highest chemical $I_{sp}$ | cryogenic, boil-off |
| Fluorine oxidiser | ~410 | very hot | corrosive; cryogenic |
| Hybrid | – | can shut down and throttle | still in development |

- **Hydrazine thruster**:
  1. a valve opens (needs power);
  2. N₂H₄ is injected onto a **Pt/Ir catalyst on alumina**;
  3. exothermic decomposition gives N₂ + NH₃ + H₂;
  4. the gas expands through a nozzle.
  Thrust 1–10 N.
- **Hypergolic**: ignites on contact, so no igniter is needed. N₂O₄ boils at 294 K, which makes it storable.
- **Solid motors**: the grain geometry sets the thrust history. Used for launchers and GEO apogee motors. Not used for ACS, except gimballed launcher nozzles.
- **Unified bipropellant systems** (for example Eurostar) share tanks between the apogee engine (400 N) and the RCS thrusters (10 N).

## Examples
- Workbook Ch7 Q2, Q4, Q6–Q9.
- 2015/16 Q1(iii): "list three types of chemical propulsion" (3 marks).
- Exam 2021/22 B1: Apollo CM RCS, 410 N, $I_{sp}$ = 336 s. An 8.5 min burn uses $\dot m = T/g_0I_{sp}$ = 0.124 kg/s, so about 63 kg.

## Related
- [[Electric Propulsion Sizing]] · [[Tsiolkovsky Rocket Equation]] · [[Rocket Performance Parameters]] · [[Thrust Equation]]

## Sources
- Chapter 7 lecture slides 16–30
