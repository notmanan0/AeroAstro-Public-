---
title: "SESA2024 Past Paper Trend Analysis"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, exam-technique]
status: complete
sources: ["03 - Exams & Past Papers"]
---

# SESA2024 Past Paper Trend Analysis

> [!abstract] Twelve papers, 2013/14 – 2024/25
> **Format** (every year except 2020/21):
> - **Section A** (25 marks, all compulsory): 7–10 short questions.
> - **Section B** (3 × 30 marks, **answer 2**): multi-part case studies. Section B is 70 % of the paper.
>
> Since 2021/22 the exam has been **online open-book** (2–3 h expected, 8 h window), with real-mission storylines: Apollo 9, Meteosat, Artemis/OMOTENASHI, Starlink, Starship IFT-2, a Jupiter orbiter, asteroid deflection, GPS, a CO₂ monitor.
>
> **Every recent paper has one orbital-mechanics B question, one comms/power/thermal B question, and one remote-sensing/SSO B question.**

> [!warning] File naming
> `SESA2024-202425-01-SESA2024.pdf` is actually the **2022/23** paper (its header reads "Semester 1 Final Assessment 2022/23"). The real 2024/25 paper is `SESA2024-202425-01-SESA2024W1.pdf`. The notes below use the correct years.

## Section B topics by year
| Year | B1 | B2 | B3 |
|---|---|---|---|
| 2013/14 | orbits + debris intercept (Hohmann) | thermal: GEO spinner | **RS: SSO + repeat + data rate** |
| 2014/15 | launcher staging (Ariane 5) | power: ISS battery and array | **RS: SSO + repeat + FOV + data rate + launch azimuth** |
| 2015/16 | Kepler + Hohmann to GEO | comms: Phobos link budget | **RS: SSO + orbit control** |
| 2016/17 | staging + energy + apogee raise | thermal: GEO cube radiator | **RS: SSO + data rate + power** |
| 2017/18 | Hohmann to Saturn | comms: dish trade + Voyager downlink | **RS: SSO + data rate + drag** |
| 2018/19 | orbits (Kepler 2, GTO kick) | power: 900 km Li-ion vs NiCd | **RS: SSO + data rate + compression** |
| 2019/20 | GEO derivation + manoeuvre corridor | power/thermal: SSO array | **RS: SSO + drag sail + data rate** |
| 2020/21 | *single reference mission, 9 questions (RS design, all subsystems)* | | |
| 2021/22 | Apollo 9 de-orbit (orbits + ground track) | Meteosat thermal and power | **Mars SSO + repeat + orbit control** |
| 2022/23 | Artemis/OMOTENASHI (rocket eq. + orbits) | thermal array + comms EIRP | **Starlink SSO + ground track + drag** |
| 2023/24 | Starship IFT-2 (orbits + rocket eq.) | comms EIRP + dish + GEO battery | **Jupiter SSO + repeat + Hohmann + thermal** |
| 2024/25 | asteroid deflection (heliocentric orbits) | GPS comms (EIRP, power–gain) | **CO₂ SSO + repeat + drag + Hohmann + thermal** |

## Topic frequency (all 12 papers, A and B)
| Topic | Appearances | Typical marks | Notes |
|---|---|---|---|
| **Sun-synchronous inclination** $\cos i = 0.986/(-2.0647\times10^{14}a^{-3.5})$ | **12/12** | 2–10 | always |
| **Repeat ground track** $\tau = (m/n)86400$, swath and $n$ | 11/12 | 4–12 | Mars and Jupiter variants |
| **Vis-viva / energy equation** | 11/12 | 3–12 | given on the formula sheet |
| Hohmann transfer or small-ΔV boost | 10/12 | 4–12 | orbit maintenance since 2021 |
| **Link budget / EIRP** | 9/12 | 11–15 | "explain the physical significance of EIRP" recurs |
| **Thermal balance** (noon / terminator / eclipse) | 9/12 | 9–16 | material selection since 2023 |
| Rocket equation / $I_{sp}$ | 9/12 | 2–11 | |
| Battery / array sizing | 7/12 | 7–15 | |
| Orbit control cycle (drag, $k$) | 7/12 | 5–8 | |
| Payload data rate (push-broom) | 7/12 | 7–17 | |
| Stabilisation types / momentum bias / $[\mathbf I]$ | 10/12 (Section A) | 2–5 | |
| LST of nodes | 6/12 (Section A) | 2 | free marks |
| Ground-track sketch | 4/12 | 5–7 | label nodes, max latitude, eclipse |
| Debris / fragment clouds | 3/12 | 5 | 2021/22 A6, 2022/23 A6 |
| Systems engineering (phases, TLR/DR) | 4/12 | 2–4 | |
| EP optimisation curve | 2/12 | 4–6 | 2022/23 A1, 2024/25 A2 |

## What to prioritise
1. **The remote-sensing chain** (Q B3 every year): swath → $n$ → $\tau$ → $m$ → recompute $\tau$ → $a$, $h$ → $i$ → LST/RAAN → drag $\delta a$, $\delta\tau$ → cycle → Hohmann ΔV → propellant → data rate. See [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]].
2. **Vis-viva with real storylines**: $a$ and $e$ from one state, $\theta$ from the orbit equation, ΔV between two orbits at a common point (as a *vector* if the flight-path angles differ), and Kepler 3 for timing.
3. **The link budget in dB**, plus the global-coverage dish ($\theta_{3dB} = 2\sin^{-1}(R_E/r)$) and transponder power.
4. **The thermal balance** for 3–4 orbit positions, and material selection against a temperature window.
5. **Section A free marks**:
   - LST ascending/descending is ±12 h and constant pass to pass;
   - the eclipse equilibrium is independent of $\varepsilon$;
   - $[\mathbf I]$ with products of inertia means 3-axis;
   - spinner vs 3-axis reasoning;
   - Gabbard/fragment reasoning (forward kick means longer period).

## Solutions in this vault
- [[SESA2024 2024-25 Exam Solutions]]
- [[SESA2024 2023-24 Exam Solutions]]
- [[SESA2024 2022-23 Exam Solutions]]
- [[SESA2024 2021-22 Exam Solutions]]
- [[SESA2024 2020-21 Exam Solutions]] (24-h reference mission; parts needing the Blackboard data set are solved by method)
- [[SESA2024 2019-20 Exam Solutions]]
- [[SESA2024 2018-19 Exam Solutions]]
- [[SESA2024 2017-18 Exam Solutions]]
- [[SESA2024 2016-17 Exam Solutions]]
- [[SESA2024 2015-16 Exam Solutions]]
- [[SESA2024 2014-15 Exam Solutions]]
- [[SESA2024 2013-14 Exam Solutions]]
- Quick-check index: [[SESA2024 Legacy Papers 2013-2021 Key Answers]]

> [!tip] Traps caught while solving the older papers
> - **Check for eclipse before any "far side" thermal case**: $a\sin\beta<R_E$ means shadow (2019/20 B2, 2016/17 Q3, 2020/21 Q8).
> - **A super-circular burnout speed means an elliptical parking orbit** (2016/17 Q2(iv)).
> - **$(n, m)$ must be coprime**: 501 fails with 33, and 446–448 fail with 30.
> - **Round $k$ down** so the drift stays inside $\pm E_0$.

## Exam technique (from the rubrics)
- Handwritten, **show working**: "marks will only be awarded when appropriate working is given". Screenshots of Excel or code are **not marked** (2024/25).
- **Reference external sources** (open book).
- Spend about 35 min on A and about 85 min on B. Answer **exactly two** B questions, and strike through any extra.
