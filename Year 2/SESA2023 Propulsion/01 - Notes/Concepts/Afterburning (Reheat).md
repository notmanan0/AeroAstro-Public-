---
title: "Afterburning (Reheat)"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
aliases: ["reheat", "afterburner", "variable area nozzle", "thrust augmentation"]
tags: [sesa2023, concept, cycle-analysis]
status: complete
parent_lectures: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Turbojet]]", "[[Critical Conditions and Choked Flow]]", "[[Ramjet]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Afterburning (Reheat)

## Definition

> [!note] Definition
> Extra fuel is burned in the jet pipe downstream of the turbine (station 6→7) to raise $T_{0}$ before the nozzle. This increases $V_j$ and thrust at a large sfc penalty.

## Explanation
- **Why the thrust rises**: $V_j\propto\sqrt{T_{06}}$ at the same nozzle pressure ratio.
- **Why it is inefficient**: the heat is added at a **low pressure ratio**, after the turbine expansion, so the "effective" cycle pressure ratio for that heat is low. Plenty of oxygen remains because the main burner runs lean, so a large extra $f$ is possible.
- **Variable-area nozzle is essential**. The nozzle is choked, so $\dot m = C\,A_8p_{06}/\sqrt{T_{06}}$. To hold the engine's mass flow and $p_{06}$ (so the turbine and compressor don't move on their maps), $A_8$ must scale as $\sqrt{T_{06}}$, times $(1+f_{tot})/(1+f)$.
- **Uses**: take-off, combat, intercept, transonic acceleration, supercruise alternatives.
- **Alternatives** to more thrust (2020-21 Q3(iii)):
  - a larger engine (more $\dot m$), which is heavier;
  - higher TET (materials and cooling);
  - a higher pressure ratio;
  - water/methanol injection (short-term);
  - a variable-cycle or low-bypass turbofan (adding bypass air improves $\eta_P$);
  - an extra lift engine or rocket boost.
- **Profiles** (2016-17 Q4(i)): the stagnation temperature jumps in the afterburner. $p_0$ drops slightly (flameholder drag and heat addition). The velocity rises through the nozzle. Static $T$ at exit is higher with reheat.

![[prop_e2021_q3_reheat_Ts.png|600]]

## Examples
2020-21 Q3 (M 1.5 at 31,000 ft):

| | $V_j$ (m/s) | $F/\dot m$ | sfc (g/s/kN) | $\eta_P$ |
|---|---|---|---|---|
| Dry | 1252 | 831 | 30.5 | 0.54 |
| Reheat ($T_{06} = 1800$ K) | 1528 | 1141 | 37.7 | 0.46 |

The thrust rises 37 %, sfc rises 24 %, and the **throat area must grow 24 %**.

2016-17 Q1: reheat to 2500 K gives $V_j = 1793$ m/s and $F/\dot m = 1305$ against 766 dry.

## Related
- [[Turbojet]] · [[Critical Conditions and Choked Flow]] · [[Ramjet]]

## Sources
- Weeks 6–7 handout §6.9; Lecture 16
