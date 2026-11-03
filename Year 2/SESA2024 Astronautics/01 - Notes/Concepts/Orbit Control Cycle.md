---
title: "Orbit Control Cycle"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["drag make-up", "ground-track maintenance", "orbit maintenance", "drag decay", "station keeping in LEO"]
tags: [sesa2024, concept, orbital-mechanics, drag]
status: lectured
parent_lectures: ["[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
related_concepts: ["[[Repeat Ground Track]]", "[[Hohmann Transfer]]", "[[Space Debris Mitigation]]"]
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# Orbit Control Cycle

The orbit control cycle keeps a low-orbit satellite's repeat ground track within a tolerance $\pm E_0$ at the equator despite drag, by boosting the orbit slightly above nominal and letting drag carry it down through nominal before boosting again.

Drag reduces the semi-major axis by $\delta a=-2\pi\rho(SC_D/m)a^2$ per orbit and the period by $\delta\tau=3\pi\delta a/V$; the spacecraft actually speeds up. With a shortening period the track drifts east. Starting just above nominal, the track first drifts west, slows, reverses and returns, tracing a parabola across the whole tolerance window. The window $2E_0$ corresponds to a timing error $\Delta t_0=(2E_0/R_E)/\omega_E$, and the half-cycle is

$$
k=\sqrt{\frac{2\Delta t_0}{|\delta\tau|}}\ \text{orbits},
$$

so the cycle lasts $2k$ orbits and loses $2k|\delta a|$ of height, restored by a small Hohmann transfer costing about $V\Delta a/2a$.

Density varies tenfold with solar activity, so the design uses the high value. The workbook's 150 kg imager at 619 km boosts every 16 days for a total of 2 m/s over three years; a 1000 kg, 10 m² imager at 277 km needs a boost twice a day and 1765 m/s. The same decay equation explains why drag sails speed up end-of-life disposal.

![[ast_orbit_control_cycle.png|560]]

## Related

- [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate#2. The orbit-control cycle|Derivation in the topic note]]
- [[Repeat Ground Track]] · [[Hohmann Transfer]] · [[Space Debris Mitigation]]
