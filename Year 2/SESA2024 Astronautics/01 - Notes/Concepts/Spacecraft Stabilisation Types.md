---
title: "Spacecraft Stabilisation Types"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["spinner", "dual spin", "hybrid stabilisation", "3-axis stabilised", "spin stabilisation"]
tags: [sesa2024, concept, attitude-control]
status: complete
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Momentum Bias and Gyroscopic Rigidity]]", "[[Inertia Matrix]]", "[[Reaction Wheels and Momentum Dumping]]"]
sources: ["02 - Sources/Lectures/Chapter 6/2025 Lecture 2 - Chapter 6 - Attitude Control - complete.pdf"]
---

# Spacecraft Stabilisation Types

## Definition

> [!note] Definition
> The four active stabilisation categories (2016/17 Q1(iv)):
> 1. **Spinner** (pure spin);
> 2. **Dual-spinner**;
> 3. **Hybrid** (3-axis with a momentum-bias wheel);
> 4. **3-axis stabilised** (zero bias).

## Explanation
| | Mechanism | Momentum | Main consequences | Examples |
|---|---|---|---|---|
| 1 | whole body spins at 10–60 rpm | large $I$, small $\omega$ | **power-limited** (body-mounted cells, only a fraction lit); thermal is simple but uneven; limited mounting for non-scanning payloads; the spin axis must be the **maximum-inertia principal axis**; nutation damping | Intelsat 1, Meteosat SG, Cluster |
| 2 | spun rotor + despun platform (Earth-pointing) | large $I$, small $\omega$ | more configuration freedom; **despin bearing and slip-ring power transfer** (reliability); balance; nutation | Giotto, Intelsat 2–4 and 6, Galileo |
| 3 | 3-axis body + momentum wheel(s) at ~6500 rpm | **small $I$, large $\omega$** | deployable Sun-tracking arrays; the wheel stores one axis of momentum (±10 % of bias); nutation | Navstar GPS 2R, Eurostar 3000 |
| 4 | reaction wheels near 0 rpm, thrusters | ~0 | full slewing freedom; stable platform for optics; continuous active control | Hubble, JWST, SPOT 5, Envisat, Magellan |

- Types 1 and 2 are **power-limited** and have limited mounting space. Types 3 and 4 relieve this with large deployable arrays.
- **Passive vs active**: spin (gyroscopic rigidity), gravity-gradient and magnetic stabilisation are passive. A 3-axis spacecraft is the archetype of active control.

## Examples
- A spinner suits **GEO weather imaging** (Meteosat MSG: 100 rpm, 3.2 m × 2.4 m cylinder). The spin sweeps the imager across the Earth disc; thermal loading is uniform; it is stable. A spinner does not suit **LEO** push-broom imaging, where nadir rotates once per orbit and a stable nadir-pointing platform is needed (2021/22 A2, B2(i)).
- A **GEO observatory** needs 3-axis stabilisation, because it points in arbitrary directions (workbook Ch6 Q12).
- A remote-sensing 3-axis spacecraft has **zero angular momentum** (2023/24 A2: answer C).

## Related
- [[Momentum Bias and Gyroscopic Rigidity]] · [[Inertia Matrix]] · [[Reaction Wheels and Momentum Dumping]]

## Sources
- Chapter 6 lecture slides 21–35
