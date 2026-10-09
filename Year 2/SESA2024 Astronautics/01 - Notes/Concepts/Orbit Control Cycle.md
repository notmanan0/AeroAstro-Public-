---
title: "Orbit Control Cycle"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["orbit maintenance", "drag decay", "ground track control", "orbit boost", "atmospheric drag", "station keeping LEO"]
tags: [sesa2024, concept, remote-sensing, orbit-control]
status: complete
parent_lectures: ["[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
related_concepts: ["[[Repeat Ground Track]]", "[[Hohmann Transfer]]", "[[Space Debris Mitigation]]"]
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# Orbit Control Cycle

## Definition

> [!note] Definition
> $$\delta a = -2\pi\rho\frac{SC_D}{m}a^2,\quad\delta\tau = \frac{3\pi}{V}\delta a\quad(\text{per orbit})$$
> $$\delta\lambda = \frac{2E_0}{R_E}\frac{180}{\pi},\quad\Delta t_0 = \frac{\delta\lambda}{\omega_E},\quad k = \sqrt{\frac{2\Delta t_0}{|\delta\tau|}},\quad\Delta a = 2k|\delta a|,\quad T_{cycle} = 2k\tau$$

## Explanation
- Drag lowers $a$ and shortens $\tau$ each orbit. The ground track drifts relative to its reference.
- **Strategy**: boost to just above nominal. The track first drifts one way, stops, then drifts back; the error traces a parabola from $-E_0$ to $+E_0$ and back over $2k$ orbits. Then boost again.
- Each boost is a small Hohmann transfer between $a\pm\Delta a/2$: $\Delta V\approx V\Delta a/2a$.
- Lifetime $\Delta V = (\text{life}/T_{cycle})\Delta V_{cycle}$; propellant $M_e = M_0(1-e^{-\Delta V/V_{ex}})$.
- **Worst case** means high solar activity: $\rho$ is about 5–10× higher at solar maximum.
- **Alternative (period-tolerance) form** (2024/25 B3): if $|\tau-\tau_{nom}|\le\Delta\tau_{max}$, the cycle is about $2\Delta\tau_{max}/|\delta\tau|$ orbits, and the allowed $\Delta a = \tfrac23(a/\tau)\Delta\tau_{max}$ each side.

![[ast_orbit_control_cycle.png|540]]

## Examples
| Case | $\delta a$/orbit | $k$ | Cycle | $\Delta V$ (life) |
|---|---|---|---|---|
| Workbook civil, 619 km | −0.234 m | 121 | 16.3 d | 2.05 m/s |
| Workbook military, 277 km | −173 m | 4 | 0.5 d | 1765 m/s |
| 2015/16 Q4, (502,33) at 502 km ($E_0$ = 1.5 km, ρ = 5.83 × 10⁻¹³, 150 kg, 1 m²) | −2.54 m | 63 (63.98, rounded down) | 126 orbits = 8.3 d ($\Delta a$ = 320 m) | – |

- Draw the full orbit-control strategy for a repeating ground track (2013/14, 2016/17; 4 marks).

## Related
- [[Repeat Ground Track]] · [[Hohmann Transfer]] · [[Space Debris Mitigation]]

## Sources
- Workbook Ch11B solutions; 2015/16 and 2017/18 data sheets
