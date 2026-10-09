---
title: "Hohmann Transfer"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["Hohmann", "two-impulse transfer", "impulsive manoeuvre", "orbit raising", "delta-V"]
tags: [sesa2024, concept, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
related_concepts: ["[[Vis-Viva Equation]]", "[[Tsiolkovsky Rocket Equation]]", "[[Orbit Control Cycle]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Hohman transfers_V2.pdf"]
---

# Hohmann Transfer

## Definition

> [!note] Definition
> The **minimum-ΔV two-impulse transfer between coplanar circular orbits**, via an ellipse tangent to both ($r_p = r_1$, $r_a = r_2$):
>
> $$a_T = \frac{r_1+r_2}{2},\quad\Delta V_1 = \sqrt{\frac{\mu}{r_1}}\left(\sqrt{\frac{2r_2}{r_1+r_2}}-1\right),\quad\Delta V_2 = \sqrt{\frac{\mu}{r_2}}\left(1-\sqrt{\frac{2r_1}{r_1+r_2}}\right),\quad t = \pi\sqrt{\frac{a_T^3}{\mu}}$$

## Explanation
- **Impulsive assumption**: high thrust, short burn, small $\gamma$, so no gravity loss. The burn point is common to both orbits.
- Both burns are **tangential**, along the velocity (raising) or against it (lowering).
- With $x = r_1/r_2$: $\Delta V = V_1\left[\sqrt{2/(x+1)}\,(1-x)+\sqrt x-1\right]$.
- The cost peaks at $r_2/r_1\approx15.6$ (0.536 $V_1$). Beyond about 11.9 a bi-elliptic transfer is cheaper.
- **Small-change limit** (orbit maintenance): $\Delta V_{tot}\approx V\Delta r/2r$.
- **Drawbacks for interplanetary missions**: long transfer times, launch windows, assumes coplanar circles.

![[ast_hohmann_dv_ratio.png|480]]

## Examples
| Transfer | ΔV₁ | ΔV₂ | Total | Time |
|---|---|---|---|---|
| 200 km → GEO | 2.455 | 1.478 | 3.933 km/s | 5.26 h |
| 300 km → GEO | 2.426 | 1.467 | 3.893 km/s | 5.3 h |
| Earth → comet perihelion (3 × 10⁸ km) | 4.55 | – | – | 340 d |
| GEO → GEO + 100 km (2019/20) | – | – | ≈ 3.6 m/s | ≈ 12 h |

## Related
- [[Vis-Viva Equation]] · [[Tsiolkovsky Rocket Equation]] · [[Orbit Control Cycle]]

## Sources
- Chapter 5 Lectures 11–13; workbook Ch5 Q3, Q7, Q8
