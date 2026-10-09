---
title: "Eclipse Duration"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["eclipse period", "worst-case eclipse", "time in shadow", "eclipse fraction"]
tags: [sesa2024, concept, power, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Battery Sizing]]", "[[Local Solar Time and RAAN]]", "[[Spacecraft Thermal Balance Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf"]
---

# Eclipse Duration

## Definition

> [!note] Definition
> For a circular orbit of radius $a$, the **worst-case** eclipse (Earth–Sun vector in the orbit plane, cylindrical shadow) is
>
> $$t_e = \frac{180^\circ-2\rho}{360^\circ}\,\tau,\qquad \cos\rho = \frac{R_E}{a}\ \ (\text{the lecture's }\alpha),\qquad t_s = \tau-t_e$$

## Explanation
- The shadow is a cylinder of radius $R_E$ behind the Earth. The orbit arc inside it subtends $\theta = 180^\circ-2\rho$ at the Earth's centre.
- Eclipse **fraction** falls with altitude (about 40 % in LEO, 4.8 % at GEO). Eclipse **duration** is at a minimum of about 35 min near 1000–1500 km, then rises to about 69 min at GEO.
- **Is there an eclipse?** If the Sun is $\beta$ out of the orbit plane, the closest approach of the orbit to the shadow axis is $R_0 = a\sin\beta$. **No eclipse if $R_0>R_E$.** (Workbook Ch10 Q7 at solstice: $R_0 = 18\,000\sin23.5^\circ = 7177$ km > $R_E$.)
- **Reverse problem** (2022/23 A3): if the eclipse is 1/3 of the orbit, then $180-2\rho = 120^\circ$, so $\rho = 30^\circ$, $a = R_E/\cos30^\circ$ = 7365 km, and $h$ = **987 km**.
- A GEO satellite sees eclipses only in about 45-day seasons around the equinoxes, but sizing uses the worst case.
- In SSOs the LST sets the eclipse: dawn–dusk has little or none; noon–midnight and 10:30 have eclipses on every orbit.

![[ast_eclipse_vs_altitude.png|620]]

## Examples
| Orbit | $\tau$ | $t_e$ | $t_s$ |
|---|---|---|---|
| 350 km (ISS, 2014/15) | 91.5 min | 36.3 min | 55.2 min |
| 694 km (2023/24 A4) | 98.6 min | **35.3 min** | – |
| 800 km (lecture) | 1.68 h | 0.59 h | 1.09 h |
| 900 km (2018/19) | 103.0 min | 35.0 min | 1.13 h |
| GEO | 23.93 h | **1.157 h** | 22.78 h |

## Related
- [[Battery Sizing]] · [[Local Solar Time and RAAN]] · [[Spacecraft Thermal Balance Equation]]

## Sources
- Chapter 8 equations 8.2–8.3; workbook Ch8 Q10
