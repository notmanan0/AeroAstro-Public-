---
title: "SESA2024 11 - Payload and Orbit Selection"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 11
tags:
  - sesa2024
  - remote-sensing
  - orbit-selection
  - payload
aliases: ["Orbit selection first pass", "Chapter 4 Payload", "Chapter 11 first pass"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 03 - Orbital Elements and Conic Sections]]", "[[SESA2024 01 - Systems Engineering and Spacecraft Design]]"]
next_topics: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
key_concepts: ["[[Swath Width and Push-Broom Imaging]]", "[[Keplerian Orbital Elements]]", "[[Sun-Synchronous Orbit]]", "[[Repeat Ground Track]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Orbit Selection First Pass_V1.pdf", "02 - Sources/Lectures/Chapter 4/2025 WEEK 9 - Lecture 1 - Chapter 4 - Payload - v1.pdf"]
---

# SESA2024 11 - Payload and Orbit Selection

> [!abstract] Summary
> **The payload selects the orbit.** For a typical Earth-viewing imager (about 10 m resolution, a life of years), a "first pass" gives:
> - **near-polar** $i$, for global coverage;
> - **near-circular** $e\approx0$, for constant sensor range;
> - **700–900 km**, trading resolution against drag.
>
> The payload's *operational* needs then add two conditions: a sunlit target with the same illumination on every pass (**Sun-synchronism**), and a repeating viewing geometry (**Earth-synchronism**). Achieving both precisely is the subject of the next two notes.

## Key Concepts
- [[Swath Width and Push-Broom Imaging]] · [[Keplerian Orbital Elements]] · [[Sun-Synchronous Orbit]] · [[Repeat Ground Track]]

---

## 1. Orbit selection is driven by the mission
- The design concept is a synthesis of payload + orbit + launch vehicle + services.
- **Mission analysis is iterative and system-level**: mission objectives → payload → mission analysis → mission specification → design requirements (propulsion, power, comms, ACS, thermal) → and back round.

Examples:

| Objective | Orbit |
|---|---|
| Global environmental monitoring at high resolution | **LEO near-polar** |
| Global comms via large fixed ground stations | **GEO** |
| Global comms to small mobile terminals | **LEO polar** constellation |
| High-resolution astronomy | LEO, HEO or GEO |

**Remote-sensing applications**: environmental monitoring, climate (GHGs, ozone), weather, agriculture and forestry, resource mapping, cartography and urban planning, disaster assessment, oceanography (fishing, shipping, slicks).

## 2. Push-broom imaging
See [[Swath Width and Push-Broom Imaging]].
- A linear CCD array sits across-track, and the spacecraft's motion sweeps it along-track, like a push broom. Each line is read out once per ground pixel.
- **Advantage over whisk-broom scanning**: no moving scan mirror, and a long dwell time per pixel, which gives better signal-to-noise and geometry (2017/18 Q1(vii)).
- **The orbit determines how much of the ground is sampled, and how quickly.**

$$
d = 2h\tan\frac{\beta}{2}\ \ (\text{swath from FOV } \beta),\qquad d = N_{pixels}\times p\ \ (\text{swath from pixel count and size } p)
$$

## 3. "First pass" selection: a typical imager (about 10 m, years)
| Element | Options | Choice | Why |
|---|---|---|---|
| Inclination | ~0°, ~50°, **~90°** | **near-polar** | global coverage |
| Eccentricity | **~0**, 0.1, 0.4 | **near-circular** | constant sensor range, so constant resolution and scale |
| Altitude | 200 km (resolution) … 1200 km (life) | **700–900 km** ($a$ = 7078–7278 km) | trade-off between resolution (low) and propellant for drag make-up over a life of years (high) |

This matches the exam answers to "first-pass values of $i$, $e$ and $a$ for a remote-sensing mission" (2013/14, 2018/19, 2019/20; 3–4 marks).

### Spy-satellite variant (lecture activity)
Resolution about 0.1 m needs a very low altitude over the target, but it must survive drag for years. The answer is a **highly eccentric orbit** with a **very low perigee** (over the target latitude) and a high apogee. The spacecraft passes quickly through the dense atmosphere, then coasts.

## 4. Payload operational requirements
**Illumination**: most instruments measure reflected sunlight (visible and near-IR), so:
- the target must be **in sunlight**;
- a **moderate Sun angle** is best. A high Sun (noon) gives short shadows and **sun glint** off water for nadir sensors. A low Sun gives long shadows. Moderate means mid-morning.
- **Change detection** (day 1, 10, 20) needs **invariant illumination, shadow direction and shadow length** on successive passes. This requires **Sun-synchronism**.

**View angle**: arrive over the target with the **same viewing geometry at regular intervals**. This requires **Earth-synchronism** (a repeat ground track).

> Summary for about 10 m imaging:
> - near-polar, near-circular, 700–900 km;
> - target sunlit at a moderate Sun angle;
> - invariant illumination, and invariant repeating viewing geometry;
>
> → **Sun- and Earth-synchronous orbit**.

## 5. Payload impact on the spacecraft (Ch 4)
See [[SESA2024 01 - Systems Engineering and Spacecraft Design#6. Payload impact on the spacecraft (Ch 4)|Topic 01 §6]]:
- pointing → ACS;
- resolution and coverage → orbit;
- data rate → OBDH and comms;
- power → EPS;
- thermal tolerances → TCS.

Examples in the lecture: a radar intelligence satellite and an ELINT satellite (large antennas, high power, and orbit chosen for coverage).

## 6. Three basic orbit requirements plus one attitude requirement (2018/19 Q1(vii))
- **Orbit**: near-polar $i$ (Sun-synchronous, about 98°); circular; altitude about 700–900 km, plus a repeat ground track.
- **Attitude**: nadir (Earth) pointing with 3-axis stabilisation and the required accuracy and stability.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 10 - Thermal Control]] · Next: [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]
- Commercial trade-offs (spatial / spectral / temporal resolution): [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]

## Sources
- Chapter 11 "Orbit selection, a first pass" (C. Ryan, after H. Lewis); Chapter 4 Payload (H. Sykulska-Lawrence)
