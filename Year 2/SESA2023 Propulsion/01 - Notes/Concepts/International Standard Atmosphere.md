---
title: "International Standard Atmosphere"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["ISA", "standard atmosphere", "altitude tables"]
tags: [sesa2023, concept, atmosphere]
status: complete
parent_lectures: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]"]
related_concepts: ["[[Stagnation Properties]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf"]
---

# International Standard Atmosphere

The International Standard Atmosphere is a standard model of temperature, pressure and density against altitude. At sea level $p = 101.325$ kPa, $T = 288.15$ K, $\rho = 1.225$ kg/m³ and $a = 340$ m/s. The temperature falls at 6.5 K/km up to 11 km, is constant at 216.65 K from 11 to 20 km, and rises at 1 K/km above 20 km.

Tables give the ratios $\delta = p/p_{sl}$, $\theta = T/T_{sl}$ and $\sigma = \rho/\rho_{sl}$ (Data Book Tables 24–25; Mattingly App. A also gives cold, hot and tropical days). In the troposphere $p = p_{sl}(T/T_{sl})^{g_0/(RL)}$ with $g_0/(RL) = 5.256$, and in the isothermal layer $p = p_{11}\exp[-g_0(h-h_{11})/(RT)]$. The speed of sound is $a = a_{sl}\sqrt\theta$, and viscosity comes from Sutherland's law. Use the static ambient values, then convert to stagnation conditions with the flight Mach number.

For engines, thrust falls with altitude because $\dot m\propto\rho$, while the falling $T_{02}$ raises $T_{04}/T_{02}$, which helps efficiency. Hot days cut take-off power: in PS7 Q7.3b, 20 K more at the inlet costs 10 % of the specific work.

![[prop_isa.png|600]]

| Altitude | $T$ (K) | $p$ (kPa) |
|---|---|---|
| 2 km | 275.15 | 79.50 |
| 6 km | 249.19 | 47.22 |
| 10 km | 223.26 | 26.50 |
| 31,000 ft | 226.73 | 28.7 |
| 35,000 ft | 218.81 | 23.8 |
| 44,000 ft | 216.65 | 15.5 |
| 15 km | 216.66 | 12.11 |
| 20 km | 216.66 | 5.53 |
| 51,000 ft | 216.65 | 11.1 |

## Related

- [[Stagnation Properties]] · [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]
