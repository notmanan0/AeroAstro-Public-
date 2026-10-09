---
title: "SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 13
tags:
  - sesa2024
  - remote-sensing
  - sun-synchronous
  - repeat-ground-track
  - local-solar-time
aliases: ["n m iteration", "Repeat parameters", "RAAN from LST", "Chapter 11 calculating orbital elements"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]"]
next_topics: ["[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
key_concepts: ["[[Repeat Ground Track]]", "[[Swath Width and Push-Broom Imaging]]", "[[Local Solar Time and RAAN]]", "[[Sun-Synchronous Orbit]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_V1.pdf", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_Part 2_V1.pdf", "02 - Sources/Lectures/Chapter 11/SESA2024 Astronautics - Chapter 11_Calculating Orbital Elements_worked example_V1.pdf"]
---

# SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission

> [!abstract] Summary
> *We don't choose the elements; the payload does.*
> - The instrument FOV and the altitude set the swath $d$. Global coverage needs orbits that touch at the equator, giving $n = 2\pi R_E/d$.
> - The first-pass altitude range sets $\tau$, so $m = n\tau/86400$.
> - Round $n$ and $m$ to integers, recompute $\tau = (m/n)86400$, and **iterate** (adjust $n$ by ±1) until $\tau$ lies in the allowed band.
> - Then $a = [\mu(\tau/2\pi)^2]^{1/3}$ and $i$ follows from the Sun-synchronous condition.
> - $e\approx0$; $\omega$ is undefined; **$\Omega$ comes from the chosen local solar time of the node and the launch date.** The LST in turn sets the eclipse duration, and so the power and thermal design.

## Key Concepts
- [[Repeat Ground Track]] · [[Swath Width and Push-Broom Imaging]] · [[Local Solar Time and RAAN]] · [[Sun-Synchronous Orbit]]

---

## 1. Global coverage fixes $n$
- Swath from the FOV $\beta$: $d = 2h\tan(\beta/2)$.
- For **complete coverage**, adjacent swaths must at least touch at the equator (the worst case, where the tracks are furthest apart). The separation between tracks equals the swath:

$$
d = \frac{2\pi R_E}{n}\ \Rightarrow\ n = \text{int}\left(\frac{2\pi R_E}{d}\right)
$$

- $n$ depends only on $d$, i.e. on the **instrument FOV and the altitude**.
- Too low an orbit leaves gaps; too high an orbit loses resolution.
- **Overlap**: some solutions deliberately use $d_{eff} = 0.9d$ (a 10 % overlap margin).

## 2. First-pass periods (700–900 km)

| $h$ (km) | $\tau$ (s) |
|---|---|
| 700 | 5926 |
| 800 | 6052 |
| 900 | 6179 |

So we want $\tau\approx6050\pm120$ s.

## 3. The iteration (flow chart)
1. (If the altitude range is not 700–900 km, compute its $\tau$ band first.)
2. Pick any altitude $h$ in the range.
3. Swath: $d = 2h\tan(\beta/2)$.
4. $n = \text{int}(2\pi R_E/d)$.
5. $\tau = 2\pi\sqrt{(R_E+h)^3/\mu}$.
6. $m = \text{int}(n\tau/86400)$.
7. Recompute $\tau = (m/n)86400$.
8. Is $\tau$ in range? If not, change $n$ (or $m$) by 1 and return to step 7.
9. Stop. Keep $n$ and $m$.

- **Change $n$ in preference to $m$**: changing $n$ by 1 alters $\tau$ by about $\tau/n$ (about 1 %), whereas $m$ changes it by about $\tau/m$ (15–50 %).
- **Increasing $n$ shortens $\tau$** (and lowers the altitude). Decreasing $n$ raises it.

**Then**:

$$
a = \left[\mu\Big(\frac{\tau}{2\pi}\Big)^2\right]^{1/3},\qquad h = a-R_E,\qquad i = \cos^{-1}\left(\frac{0.986^\circ}{-2.0647\times10^{14}a^{-3.5}}\right)
$$

Only **discrete** $(a,i)$ pairs satisfy both conditions:

![[ast_repeat_groundtrack_solutions.png|650]]

## 4. Lecture worked example
> *Civilian remote sensing, about 10-year life, visible imager with FOV 28.96°, mapping global infrastructure at high resolution. Find $(n,m)$, $a$ and $i$. Suggest a descending-node LST and find $\Omega$ for a spring-equinox launch.*

- **Step 1**: high resolution but low drag over 10 years, so use 700–900 km and **$\tau\approx6050\pm120$ s**. Choose $h$ = 800 km.
- **Step 2**: $d = 2(800)\tan(14.48^\circ) = 413.19$ km.
- **Step 3**: $\tau(800)$ = 6052 s.
- **Step 4**: $n = \text{int}(2\pi\cdot6378/413.19) = \text{int}(96.99)$. Take **97** (96 would do; the iteration will fix it).
- **Step 5**: $m = \text{int}(97\times6052/86400) = \text{int}(6.79)$. Take **7**, the nearest. (This choice matters more.)
- **Step 6**: $\tau = (7/97)86400$ = **6235 s**.
- **Step 7**: 6235 > 6170, **out of range**.
- **Step 8**: $\tau$ is too high, so **increase $n$** to 98: $\tau = (7/98)86400$ = **6171 s**, which is ✔ in range.

**Result**:

$$
a = \left[398600\Big(\frac{6171}{2\pi}\Big)^2\right]^{1/3} = \mathbf{7271.93\ km},\qquad h = \mathbf{893.93\ km}
$$

$$
i = \cos^{-1}\left(\frac{0.986}{-2.0647\times10^{14}(7271.93)^{-3.5}}\right) = \mathbf{99.006^\circ}
$$

**(n, m) = (98, 7).** (99, 7) also works: $h$ = 844.9 km, $i$ = 98.80°. There are always **exact** $a$ and $i$ for each valid $(n,m)$.

## 5. The remaining elements
- **$e\approx0$**, from the first pass (constant range).
- **$\omega$**: undefined or arbitrary for a circular orbit. ("Frozen" orbits with specific $e$ and $\omega$ exist but are not covered.)
- **$\Omega$**: from Sun-synchronism, $\phi = \alpha_S-\Omega$ is constant. The constant sets where the Sun is when the spacecraft crosses the equator. **$\Omega$ is then fixed by the desired LST, the launch date and the launch time.** See [[Local Solar Time and RAAN]].

![[ast_lst_orbit_planes.png|520]]

| Orbit | $\phi = \alpha_S-\Omega$ | $\Omega$ at launch | Eclipse |
|---|---|---|---|
| **Noon–midnight** (LST 12:00 / 00:00) | 0° (or 180°) | $\Omega = \alpha_S$ | longest (maximum, every orbit) |
| **Dawn–dusk** (LST 06:00 / 18:00) | 90° (or 270°) | $\Omega = \alpha_S-90^\circ$ | little or none (seasonal only) |
| **10:30 am node** | 22.5° (or 337.5°) | $\Omega = \alpha_S-22.5^\circ$ | intermediate |

- **Converting**: 1 hour of LST = 15°.
- The ascending and descending nodes are **12 h apart in LST**. For example, a 06:00 descending node is an 18:00 ascending node (2023/24 A7).
- In an SSO, **the node LST is the same every orbit and every day**. The spacecraft arrives at its ascending node at 10:00 LST every time (2021/22 A7, 2024/25 A7). That is the whole point.
- Most **European** remote-sensing missions use a **descending node near 10:30 am** ("N-hemisphere am"). They pass over Europe at about 10:30–11:00, before afternoon convective cloud builds up (2015/16 Q1(vi)).

> [!example] Lecture example, part 2
> A 10:30 LST node with launch at the spring equinox, where $\alpha_S = 0^\circ$:
> - **10:30 ascending node**: $\Omega = 0^\circ-22.5^\circ = \mathbf{337.5^\circ}$.
> - **10:30 descending node**: the ascending node is at 22:30, 12 h later, so $\Omega = 337.5^\circ-180^\circ = \mathbf{157.5^\circ}$.
>
> Also, 2022/23 A7: at the spring equinox the spacecraft reaches its descending node with the Sun on the far side of the Earth, which is **midnight LST (00:00)**.

## 6. Impacts of the LST choice
The LST sets the **eclipse duration**:
- **power**: battery capacity, array size, array articulation;
- **thermal**: heater and radiator sizing.

At 800 km (lecture): dawn–dusk has almost no eclipse except in the solstice season; noon–midnight and 10:30 have eclipses of up to about 35 min on every orbit. This is an example of how the choice of orbit feeds into the subsystem design.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]] · Next: [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Full design problems: [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]

## Sources
- Chapter 11 "Calculating orbital elements" parts 1–2 and the worked example (C. Ryan, after H. Lewis)
