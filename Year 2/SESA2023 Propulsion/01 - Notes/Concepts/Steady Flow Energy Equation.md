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

The steady flow energy equation is the first law for a steady control volume:

$$
\dot Q-\dot W_x = \sum_{out}\dot m\left(h+\tfrac12V^2+gz\right)-\sum_{in}\dot m\left(h+\tfrac12V^2+gz\right)\;\Rightarrow\; q-w_x = h_{0,out}-h_{0,in},
$$

with $\dot Q>0$ for heat added and $\dot W_x>0$ for shaft work done by the fluid.

The $p/\rho$ flow work is absorbed into $h = u+p/\rho$, so the work term is shaft work only. In propulsion $gz$ is neglected, and so is the kinetic energy where the velocity is low, at compressor and burner entry and exit, but never the kinetic energy at the intake entry at speed or at the nozzle exit. The lecturer's tip is to work in stagnation quantities, which avoids needing the velocities inside the engine. Applied to each component, per kg:

| Component | Result |
|---|---|
| Diffuser | $h_{02} = h_{01}$, so $T_{02} = T_{01}$ |
| Compressor | $w_c = h_{03}-h_{02}$ |
| Burner | $q = h_{04}-h_{03}$, or the combustion form with LCV |
| Turbine | $w_t = h_{04}-h_{05}$ |
| Nozzle | $\tfrac12V_j^2 = h_{05}-h_{9}$ |
| Spool balance | $\sum\dot W_x = 0$, so $\dot m_ac_{p,a}\Delta T_c = (1+f)\dot m_ac_{p,p}\Delta T_t$ |

Adiabatic combustion keeps $h_{out} = h_{in}$, but the temperature rises because chemical energy becomes sensible energy ([[Adiabatic Flame Temperature]]); a heat loss, as in 2022-23 Q3, puts $\dot Q = -2\text{ MJ}\times\dot m_f$ on the left-hand side. An intake at 200 m/s and 250 K gives $T_{02} = 270$ K. In the PS2 Q2.3 turbojet, $T_{02} = 286.3$ K and $T_{03} = 673.9$ K, then $T_{04} = T_{03}+q/c_p = 1171.4$ K, and the spool balance gives $T_{05} = T_{04}-(T_{03}-T_{02}) = 783.9$ K.

## Related

- [[Stagnation Properties]] · [[Isentropic Efficiency]] · [[Euler Work Equation]] · [[Adiabatic Flame Temperature]]
