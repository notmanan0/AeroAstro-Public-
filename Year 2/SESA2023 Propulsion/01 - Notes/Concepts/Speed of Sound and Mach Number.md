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

The speed of sound is the speed of a weak, isentropic pressure wave, and the Mach number is the flow speed measured in units of it:

$$
a^2 = \left(\frac{\partial p}{\partial\rho}\right)_s = \frac{\gamma p}{\rho} = \gamma RT,\qquad M = \frac{V}{a} .
$$

It is derived from a control volume on a weak wave moving at $a$, in the wave's frame. Mass conservation gives $a\,\delta\rho = \rho\,\delta U$ and momentum $\delta p = 2\rho a\,\delta U-a^2\delta\rho$; eliminating $\delta U$ gives $a^2 = \delta p/\delta\rho$. The wave is weak, so it is reversible and adiabatic, hence isentropic, and $p/\rho^\gamma$ = const gives $dp/d\rho = \gamma p/\rho = \gamma RT$.

For an ideal gas the speed of sound depends on temperature alone; air at 288 K has $a = 340$ m/s. The same flight speed is therefore a different Mach number in hot or cold air (M 1.1 at 220 K is M 0.94 at 300 K), and for a moving object the static temperature of the surrounding air is the one to use. Light gases have a high speed of sound (helium 988 m/s, hydrogen 1292 m/s), which is why a light, low-Mach exhaust helps rockets. In a compressible-flow dimensional analysis $a$ enters through $c_pT$, since $a = \sqrt{(\gamma-1)c_pT}$ (W09).

| Mach | Regime |
|---|---|
| $M<0.3$ | effectively incompressible |
| $M<1$ | subsonic: disturbances travel upstream |
| $M>1$ | supersonic: no upstream influence beyond the Mach cone $\mu = \sin^{-1}(1/M)$; shocks form |

Worked values: argon ($\gamma = 1.67$, $R = 208$) at 350 K has $a = 348.7$ m/s, so 700 m/s is M 2.01 (2020-21 Q1); rocket gas ($\gamma = 1.24$, $R = 356.8$) at 3600 K has $a = 1262$ m/s.

## Related

- [[Stagnation Properties]] · [[Normal Shock Waves]] · [[Critical Conditions and Choked Flow]]
