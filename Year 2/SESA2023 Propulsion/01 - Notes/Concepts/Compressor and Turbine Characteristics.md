---
title: "Compressor and Turbine Characteristics"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["compressor map", "turbine map", "characteristic", "working line", "choke", "speed lines"]
tags: [sesa2023, concept, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Compressor Stall and Surge]]", "[[Dimensional Analysis of Turbomachines]]", "[[Critical Conditions and Choked Flow]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---

# Compressor and Turbine Characteristics

A compressor or turbine **characteristic**, or map, plots the pressure ratio $p_{02}/p_{01}$ (and the efficiency) against the non-dimensional mass flow $\dot m\sqrt{T_{01}}/p_{01}$, with lines of constant non-dimensional speed $N/\sqrt{T_{01}}$. Because the groups are non-dimensional, one map covers every inlet condition.

On a compressor map each speed line runs from the surge or stall line at low flow, where the incidence is high and positive, rises to a peak pressure ratio, then drops steeply at high flow until it goes vertical at choke, where the incidence is negative and the blade passages are sonic. The lines get steeper and closer together at high speed, and the efficiency islands sit near the middle. The engine's working line has to keep a surge margin from the surge line. An axial stage gives about 2:1 (limited by shocks) and a centrifugal stage about 10:1, and with equal stages the overall ratio is $\pi = \pi_{stage}^n$. A mismatch between stages snowballs through the machine, so compressors above about 10:1 are hard to start; hence split spools, variable stator vanes and handling bleed.

Turbines behave quite differently. Their boundary layers are stable, so high pressure ratios are possible and the blade rows choke, after which the non-dimensional flow is constant, independent of speed and pressure ratio, and the mass flow is set by the inlet $p_0$ and $T_0$. There is no surge; a stage takes about 4:1 and up to about 100:1 is possible overall. Speed has little effect, because turbine blade lift depends less on incidence. A nozzle is the simplest case: $\dot m\sqrt{T_0}/p_0$ rises with the pressure ratio until it reaches the choked value, $0.0404A$ for air, at $p/p_0 = 0.528$.

An exam sketch of a compressor map (2021-22 Q4(i)) needs the axes (pressure ratio against $\dot m\sqrt{T_{01}}/p_{01}$), four or five speed lines, the surge line joining their left-hand ends, vertical choke on the right, the efficiency islands and the working line.

![[prop_compressor_map.png|600]]

In the steam-turbine throttling problem ([[SESA2023 Problem Sheet 9 Solutions]] Q9.5), a choked turbine has $\dot m\sqrt{T_0}/p_0$ constant and an adiabatic throttle keeps $T_0$, so $\dot m\propto p$ after the throttle and the volume flow $\dot m/\rho_0$ stays constant.

## Related

- [[Compressor Stall and Surge]] · [[Dimensional Analysis of Turbomachines]] · [[Critical Conditions and Choked Flow]]
