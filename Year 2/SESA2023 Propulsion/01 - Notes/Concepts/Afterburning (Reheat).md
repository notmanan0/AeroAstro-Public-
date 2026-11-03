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

Afterburning, or reheat, burns extra fuel in the jet pipe downstream of the turbine (station 6 to 7) to raise $T_0$ before the nozzle. It increases $V_j$ and thrust at a large cost in sfc.

The thrust rises because $V_j\propto\sqrt{T_{06}}$ at the same nozzle pressure ratio. It is inefficient because the heat goes in at a low pressure ratio, after the turbine expansion, so the effective cycle pressure ratio for that heat is low; plenty of oxygen is left because the main burner runs lean, so a large extra $f$ is possible. A variable-area nozzle is essential. The nozzle is choked, $\dot m = C\,A_8p_{06}/\sqrt{T_{06}}$, so to hold the engine's mass flow and $p_{06}$, and keep the compressor and turbine where they are on their maps, $A_8$ has to scale as $\sqrt{T_{06}}$ times $(1+f_{tot})/(1+f)$.

Reheat is used for take-off, combat, interception and transonic acceleration. 2020-21 Q3(iii) asks for the alternatives for more thrust: a larger engine (more $\dot m$, but heavier), a higher turbine entry temperature (materials and cooling), a higher pressure ratio, water/methanol injection (short term), a variable-cycle or low-bypass turbofan (adding bypass air improves $\eta_P$), or a lift engine or rocket boost. Through the engine (2016-17 Q4(i)), the stagnation temperature jumps in the afterburner, $p_0$ drops slightly from flameholder drag and heat addition, the velocity rises through the nozzle, and the exit static temperature is higher with reheat.

![[prop_e2021_q3_reheat_Ts.png|600]]

2020-21 Q3, at M 1.5 and 31,000 ft:

| | $V_j$ (m/s) | $F/\dot m$ | sfc (g/s/kN) | $\eta_P$ |
|---|---|---|---|---|
| Dry | 1252 | 831 | 30.5 | 0.54 |
| Reheat ($T_{06} = 1800$ K) | 1528 | 1141 | 37.7 | 0.46 |

Thrust rises 37 % and sfc 24 %, and the throat area has to grow 24 %. In 2016-17 Q1, reheat to 2500 K gives $V_j = 1793$ m/s and $F/\dot m = 1305$, against 766 dry.

## Related

- [[Turbojet]] · [[Critical Conditions and Choked Flow]] · [[Ramjet]]
