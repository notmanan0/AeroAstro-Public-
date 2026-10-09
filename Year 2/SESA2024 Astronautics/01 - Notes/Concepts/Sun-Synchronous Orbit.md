---
title: "Sun-Synchronous Orbit"
module: "SESA2024 Astronautics"
type: concept
stream: "Remote Sensing Case Study"
aliases: ["SSO", "Sun-synchronism", "Sun-synchronous inclination"]
tags: [sesa2024, concept, remote-sensing, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
related_concepts: ["[[Nodal Regression (J2)]]", "[[Repeat Ground Track]]", "[[Local Solar Time and RAAN]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Sun and Earth synchronous orbits_V1.pdf"]
---

# Sun-Synchronous Orbit

## Definition

> [!note] Definition
> An orbit whose plane keeps a **constant angle to the Earth–Sun line**, $\phi = \alpha_S-\Omega$ = constant. The spacecraft therefore passes each latitude at the **same local solar time** on every pass. It requires
> $$\dot\Omega = \dot\alpha_S = \frac{360^\circ}{365.25\ \text{d}} = +0.986^\circ/\text{day (East)}\quad\Rightarrow\quad\cos i = \frac{0.986}{-2.0647\times10^{14}a^{-3.5}}$$

## Explanation
- **Why**: invariant illumination (Sun angle, shadow length and direction) for change detection by optical and near-IR sensors. It also gives predictable power and thermal conditions (2019/20 B3(i), 2022/23 B3(i)).
- **How**: $J_2$ oblateness precesses the node for free. Propulsive rotation of the plane would cost excessive fuel.
- $\dot\Omega>0$ needs $\cos i<0$, so the orbit is **retrograde**, $i>90^\circ$.
  - 700–900 km: $i$ = 98.2–99.0°.
  - 267 km: 96.6°.
  - 567 km: 97.66°.
- Seasonal variations remain: the Sun's declination changes through the year.
- Other planets use their own $J_2$, $R$ and year (Mars 2021/22, Jupiter 2023/24).

![[ast_sso_inclination.png|520]]

## Examples
- Lecture worked example: (98, 7), $a$ = 7271.93 km, **$i$ = 99.006°**.
- 2024/25 A6: (16, 1) gives $\tau$ = 5400 s, $h$ = **274.6 km**, $i$ = **96.59°**.
- 2023/24 A6: (15, 1) gives $h$ = **567 km**.
- **LST constancy**: arriving at the ascending node at 10:00 LST means arriving at the next ascending node at **10:00 LST** too (2021/22 A7, 2024/25 A7). That is the definition of Sun-synchronism.

## Related
- [[Nodal Regression (J2)]] · [[Repeat Ground Track]] · [[Local Solar Time and RAAN]]

## Sources
- Chapter 11 Sun-synchronous lecture, slides 5–22
