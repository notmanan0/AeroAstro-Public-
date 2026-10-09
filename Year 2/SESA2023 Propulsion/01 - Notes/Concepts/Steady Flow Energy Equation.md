---
title: "Steady Flow Energy Equation"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["SFEE", "first law for control volumes", "stagnation enthalpy"]
tags: [sesa2023, concept, thermodynamics]
status: complete
parent_lectures: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Stagnation Properties]]", "[[Isentropic Efficiency]]", "[[Euler Work Equation]]", "[[Adiabatic Flame Temperature]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Steady Flow Energy Equation

## Definition

> [!note] Definition
>
> $$\dot Q-\dot W_x = \sum_{out}\dot m\left(h+\tfrac12V^2+gz\right)-\sum_{in}\dot m\left(h+\tfrac12V^2+gz\right)\;\Rightarrow\; q-w_x = h_{0,out}-h_{0,in}$$
>
> Here $\dot Q>0$ means heat added and $\dot W_x>0$ means shaft work done **by** the fluid.

## Explanation
- It is the First Law for a steady control volume. The $p/\rho$ flow work is absorbed into $h = u+p/\rho$, and the work term is **shaft work only**.
- Neglect $gz$ in propulsion. Neglect KE where the velocity is low (compressor and burner entry and exit). **Never** neglect the KE at intake entry at speed, or at nozzle exit.
- **Component forms** (per kg):

  | Component | Result |
  |---|---|
  | Diffuser | $h_{02} = h_{01}$, so $T_{02} = T_{01}$ |
  | Compressor | $w_c = h_{03}-h_{02}$ |
  | Burner | $q = h_{04}-h_{03}$, or the combustion form with LCV |
  | Turbine | $w_t = h_{04}-h_{05}$ |
  | Nozzle | $\tfrac12V_j^2 = h_{05}-h_{9}$ |
  | Spool balance | $\sum\dot W_x = 0$, so $\dot m_ac_{p,a}\Delta T_c = (1+f)\dot m_ac_{p,p}\Delta T_t$ |

- **Working in stagnation quantities** avoids needing velocities inside the engine (the lecturer's tip).
- **Adiabatic combustion**: $h_{out} = h_{in}$, but $T$ rises because chemical energy becomes sensible. See [[Adiabatic Flame Temperature]].
- With heat loss (2022-23 Q3): $\dot Q = -2\text{ MJ}\times\dot m_f$ goes in on the left-hand side.

## Examples
- Intake at 200 m/s, 250 K: $T_{02} = 270$ K.
- Turbojet PS2 Q2.3:
  - $T_{02} = 286.3$ K and $T_{03} = 673.9$ K;
  - $T_{04} = T_{03}+q/c_p = 1171.4$ K;
  - $T_{05} = T_{04}-(T_{03}-T_{02}) = 783.9$ K.

## Related
- [[Stagnation Properties]] · [[Isentropic Efficiency]] · [[Euler Work Equation]] · [[Adiabatic Flame Temperature]]

## Sources
- Week 2 notes §2.4; Lecture 6; Data Book p. 9
