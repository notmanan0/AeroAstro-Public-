---
title: "Eclipse Duration"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["eclipse time", "eclipse period", "worst-case eclipse", "time in sunlight", "eclipse fraction"]
tags: [sesa2024, concept, power, orbital-mechanics]
status: lectured
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]"]
related_concepts: ["[[Battery Sizing]]", "[[Local Solar Time and RAAN]]", "[[Spacecraft Thermal Balance Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf"]
---

# Eclipse Duration

The eclipse duration is the time a spacecraft spends in the Earth's shadow on each orbit; for a circular orbit with the Sun in the orbit plane (the worst case) and a cylindrical shadow of radius $R_E$,

$$
t_e=\tau\,\frac{180^\circ-2\alpha}{360^\circ},\qquad\cos\alpha=\frac{R_E}{R_E+h},\qquad t_s=\tau-t_e.
$$

The orbit enters and leaves the shadow where its radius makes the angle $\alpha$ with the Earth–Sun line, so the shadowed arc subtends $180^\circ-2\alpha$. The eclipse fraction falls with altitude, from about 40 % at 350 km to 4.8 % at GEO, but the period rises, so the duration has a broad minimum of about 35 minutes for LEO altitudes of roughly 700–1500 km and climbs to 69 minutes at GEO.

| Altitude | Period | Worst-case eclipse | Sunlight |
|---|---|---|---|
| 350 km | 91.5 min | 36.3 min | 55.2 min |
| 800 km (lecture example) | 100.9 min (1.68 h) | 35.1 min (0.59 h) | 65.7 min (1.09 h) |
| 900 km | 103.0 min | 35.0 min | 68.0 min |
| GEO | 1436 min | 69.4 min | 1367 min |

The worst case need not occur. If the Sun is an angle $\beta$ out of the orbit plane, the orbit's closest approach to the shadow axis is $a\sin\beta$, and there is no eclipse at all if that exceeds $R_E$ (Workbook Ch10 Q7: $18\,000\sin23.5^\circ=7177$ km). GEO satellites see eclipses only in seasons of about 45 days around the equinoxes, and a dawn–dusk Sun-synchronous orbit has little or none, while a 10:30 orbit has one every orbit. Run backwards, an eclipse of a third of the orbit means $\alpha=30^\circ$ and an altitude of 987 km (2022/23 A3).

The eclipse sets the battery capacity, the array's recharge power and the thermal cold case.

![[ast_eclipse_vs_altitude.png|560]]

## Related

- [[SESA2024 08 - Electrical Power Subsystem#Worst-case eclipse|Derivation in the lecture note]]
- [[Battery Sizing]] · [[Local Solar Time and RAAN]] · [[Spacecraft Thermal Balance Equation]]
