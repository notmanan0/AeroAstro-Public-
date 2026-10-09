---
title: "Speed of Sound and Mach Number"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["speed of sound", "Mach number", "acoustic speed"]
tags: [sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
related_concepts: ["[[Stagnation Properties]]", "[[Normal Shock Waves]]", "[[Critical Conditions and Choked Flow]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf"]
---
# Speed of Sound and Mach Number

## Definition

> [!note] Definition
> $$a^2 = \left(\frac{\partial p}{\partial\rho}\right)_s = \frac{\gamma p}{\rho} = \gamma RT,\qquad M = \frac{V}{a}$$

## Explanation
**Derivation**: put a control volume on a weak wave moving at $a$, in the wave frame.
- Mass: $a\,\delta\rho = \rho\,\delta U$.
- Momentum: $\delta p = 2\rho a\,\delta U-a^2\delta\rho$.
- Eliminating $\delta U$ gives $a^2 = \delta p/\delta\rho$.
- The wave is weak, so it is reversible and adiabatic (isentropic): $p/\rho^\gamma$ = const, so $dp/d\rho = \gamma p/\rho = \gamma RT$.

**Consequences**:
- For an ideal gas, $a$ depends on **$T$ only**. Air at 288 K has $a = 340$ m/s.
- The same flight speed is a *different* Mach number in hot or cold air (M 1.1 at 220 K is M 0.94 at 300 K).
- Light gases have high $a$ (He 988 m/s, H₂ 1292 m/s), which is why low-$M$ exhaust helps rockets.
- For a moving object, use the **static** temperature of the surrounding air.
- **Regimes**:

  | Mach | Regime |
  |---|---|
  | $M<0.3$ | effectively incompressible |
  | $M<1$ | subsonic: disturbances travel upstream |
  | $M>1$ | supersonic: no upstream influence beyond the Mach cone $\mu = \sin^{-1}(1/M)$; shocks form |

- In a compressible-flow dimensional analysis, $a$ enters through $c_pT$, since $a = \sqrt{(\gamma-1)c_pT}$ (W09).

## Examples
- Argon (γ = 1.67, R = 208) at 350 K: $a = 348.7$ m/s, so 700 m/s is M 2.01 (2020-21 Q1).
- Rocket gas (γ = 1.24, R = 356.8) at 3600 K: $a = 1262$ m/s.

## Related
- [[Stagnation Properties]] · [[Normal Shock Waves]] · [[Critical Conditions and Choked Flow]]

## Sources
- Week 3 notes §3.3; Lecture 7
