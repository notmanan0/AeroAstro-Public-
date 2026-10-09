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

## Definition

> [!note] Definition
> A standard model of the atmosphere: $T$, $p$ and $\rho$ as functions of altitude. Sea level is $p = 101.325$ kPa, $T = 288.15$ K, $\rho = 1.225$ kg/m³ and $a = 340$ m/s.
> - Up to 11 km the temperature falls at $-6.5$ K/km.
> - From 11 to 20 km it is constant at 216.65 K.
> - Above 20 km it rises at +1 K/km.

## Explanation
- Tables give ratios $\delta = p/p_{sl}$, $\theta = T/T_{sl}$ and $\sigma = \rho/\rho_{sl}$ (Data Book Tables 24–25; Mattingly App. A, which also gives cold, hot and tropical days).
- Troposphere: $p = p_{sl}(T/T_{sl})^{g_0/(RL)}$ with $g_0/(RL) = 5.256$. Isothermal layer: $p = p_{11}\exp[-g_0(h-h_{11})/(RT)]$.
- Speed of sound $a = a_{sl}\sqrt\theta$. Viscosity comes from Sutherland's law.
- **Engine relevance**:
  - thrust falls with altitude because $\dot m\propto\rho$;
  - $T_{02}$ falls, so $T_{04}/T_{02}$ rises, which helps efficiency;
  - hot days cut take-off power (PS7 Q7.3b: +20 K at the inlet gives −10 % specific work).
- Use the **static** ambient values, then convert to stagnation with the flight Mach number.

![[prop_isa.png|600]]

## Examples

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

## Sources
- Week 1 notes §1.5; Data Book Tables 24–25; Mattingly App. A
