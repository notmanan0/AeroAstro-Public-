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

## Definition

> [!note] Definition
> A **characteristic (map)** plots $p_{02}/p_{01}$ (and $\eta$) against the non-dimensional mass flow $\dot m\sqrt{T_{01}}/p_{01}$, with lines of constant non-dimensional speed $N/\sqrt{T_{01}}$. One map covers every inlet condition.

## Explanation
**Compressor**:
- Each speed line runs from the **surge/stall line** at low flow (high positive incidence), rises to a peak pressure ratio, then drops steeply at high flow until it goes **vertical at choke** (negative incidence, sonic blade passages).
- The lines get steeper and closer together at high speed.
- Efficiency islands sit near the middle.
- The engine **working line** must keep a **surge margin**.
- Per stage: about 2:1 (axial, limited by shocks), about 10:1 (centrifugal). Overall $\pi = \pi_{stage}^n$ if the stages are equal.
- A mismatch between stages snowballs, so machines with pressure ratio above about 10 are hard to start. Hence split spools, variable stator vanes and handling bleed.

**Turbine**:
- Stable boundary layers allow high pressure ratios, so the blade rows **choke**. The non-dimensional flow becomes **constant**, independent of speed and pressure ratio.
- The mass flow is controlled by the inlet $p_0$ and $T_0$.
- There is no surge. A stage takes about 4:1, and up to about 100:1 is possible overall.
- The speed has little effect, because turbine lift depends less on incidence.

**Nozzle**: $\dot m\sqrt{T_0}/p_0$ rises with the pressure ratio until the choke value (0.0404 $A$ for air) at $p/p_0 = 0.528$.

**Sketch for exams** (2021-22 Q4(i)):
- axes: pressure ratio against $\dot m\sqrt{T_{01}}/p_{01}$;
- 4–5 speed lines;
- the surge line joining their left ends;
- vertical choke at the right;
- efficiency islands;
- the working line.

![[prop_compressor_map.png|600]]

## Examples
- Steam-turbine throttling: a choked turbine has $\dot m\sqrt{T_0}/p_0$ constant, and an adiabatic throttle keeps $T_0$, so $\dot m\propto p$ after the throttle. The volume flow $\dot m/\rho_0$ is **constant** ([[SESA2023 Problem Sheet 9 Solutions]] Q9.5).

## Related
- [[Compressor Stall and Surge]] · [[Dimensional Analysis of Turbomachines]] · [[Critical Conditions and Choked Flow]]

## Sources
- Week 9 handout §9.6; Lectures 25–26
