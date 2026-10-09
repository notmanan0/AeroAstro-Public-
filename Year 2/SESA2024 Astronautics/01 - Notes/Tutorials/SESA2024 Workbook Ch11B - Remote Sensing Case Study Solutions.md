---
title: "SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Remote Sensing Case Study"
tags:
  - sesa2024
  - tutorial-solutions
  - remote-sensing
  - sun-synchronous
  - orbit-control
sheet: "Problem Sheet Workbook 2025-26, Chapter 11B (pp. 57-87)"
theory_notes: ["[[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]", "[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]", "[[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]"]
key_concepts: ["[[Sun-Synchronous Orbit]]", "[[Repeat Ground Track]]", "[[Swath Width and Push-Broom Imaging]]", "[[Orbit Control Cycle]]", "[[Payload Data Rate]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions

> [!abstract] Sheet Info
> Two open-ended design problems: a civilian multispectral imager and a military surveillance imager. For each, find:
> - $a$, $e$, $i$ and the repeat parameters $(n,m)$;
> - the orbit-control cycle;
> - the lifetime $\Delta V$ and propellant;
> - the uncompressed data rate.
>
> The workbook gives two model solutions: an **Excel iteration** (pp. 61–75) and a **handwritten** version (pp. 79–87). They reach different but valid answers, because the problem is open. **This is the single most examined calculation in SESA2024**: it appears as Section B in 2014–2019 and 2021–2025. All numbers were reproduced in Python ✔.

> [!info] The "Excel sheet"
> The model answer was built as a spreadsheet: one row per trial $(n,m)$, with columns $\tau$, $a$, $h$, swath, resolution, $i$ and coverage. The rows are transcribed below, so you do not need the Excel file. Note that the 2024/25 paper states *"screenshots of Excel formula will not be marked"*. You must show the chain by hand.

## Theory Links
- [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]] · [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]] · [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Concepts: [[Sun-Synchronous Orbit]] · [[Repeat Ground Track]] · [[Swath Width and Push-Broom Imaging]] · [[Orbit Control Cycle]] · [[Payload Data Rate]]

---

## The toolkit (in order)

| Step | Formula | Note |
|---|---|---|
| 1 Swath | $d = N_{px}\,p$ or $d = 2h\tan(\beta/2)$ | $p$ = pixel resolution, $\beta$ = FOV |
| 2 Height from resolution | $h = d/[2\tan(\beta/2)]$ | |
| 3 $n$ | $n = 2\pi R_E/d$ | ≥ 100 % coverage at the equator |
| 4 Period | $\tau = 2\pi\sqrt{a^3/\mu}$ | |
| 5 $m$ | $m = n\tau/86400$ | round to an integer |
| 6 Actual period | $\tau = (m/n)\,86400$ | |
| 7 $a$ and $h$ | $a = [\mu(\tau/2\pi)^2]^{1/3}$, $h = a-R_E$ | |
| 8 Inclination | $\cos i = 0.986/(-2.0647\times10^{14}a^{-3.5})$ | $a$ in km, $0.986^\circ$/day |
| 9 Coverage | $n\,d/(2\pi R_E)$ | must be ≥ 100 % |
| 10 Decay | $\delta a = -2\pi\rho SC_Da^2/m$ per orbit | SI units: $a$ in m |
| 11 Period change | $\delta\tau = 3\pi\,\delta a/V$ per orbit | $V = \sqrt{\mu/a}$ |
| 12 Tolerance | $\delta\lambda = (2E_0/R_E)(180/\pi)$, $\Delta t_0 = \delta\lambda/\omega_E$ | $\omega_E = 0.004178^\circ$/s |
| 13 Half-cycle | $k = \sqrt{2\Delta t_0/\lvert\delta\tau\rvert}$ | cycle is $2k$ orbits |
| 14 Height lost | $\Delta a = 2k\lvert\delta a\rvert$; cycle time $2k\tau$ | |
| 15 Boost | Hohmann between $a\pm\Delta a/2$ | $\Delta V\approx V\Delta a/(2a)$ |
| 16 Propellant | $M_e = M_0(1-e^{-\Delta V_{tot}/V_{ex}})$ | |
| 17 Data rate | $V_{gd} = V\,R_E/a$, $t_s = p/V_{gd}$, $R_b = N_{px}\cdot\text{bits}\cdot\text{bands}/t_s$ | |

![[ast_orbit_control_cycle.png|620]]

---

## Mission 1: civilian multispectral imager
**Data**:
- 19 500 pixels per band, 3 bands, FOV 45.95°, 8-bit;
- resolution 20–30 m (like Landsat or SPOT); 3-year life; revisit as often as possible;
- $S$ = 1 m², $M_0$ = 150 kg, $C_D$ = 2.2.
- Not given in the question (use these): $E_0$ = 0.5 km, $I_{sp}$ = 180 s (the SPOT 6 value).

### Excel solution
**First try (best resolution, 20 m)**:
- $d = 19\,500\times20$ m = 390 km, giving $h = 459.9$ km, $\tau$ = 5627 s, $n$ = 102.75 → 103, $m$ = 6.71 → 7.
- Actual: $\tau$ = 5871.8 s, $h$ = 656.6 km, resolution 28.6 m, $i$ = 98.02°, coverage 143 %.
- Valid, but the repeat period is not the shortest possible.

**Explore to shorten the repeat** (target $h\approx650$–700 km):

| $m$ | $n$ | $\tau$ (s) | $h$ (km) | swath (km) | res (m) | $i$ (°) | coverage | OK? |
|---|---|---|---|---|---|---|---|---|
| 5 | 72 | 6000.0 | 758.6 | 643.3 | 33.0 | 98.43 | 115.6 % | ✘ res |
| 5 | 73 | 5917.8 | 693.3 | 587.9 | 30.1 | 98.16 | 107.1 % | ✘ res |
| 5 | 74 | 5837.8 | 629.5 | 533.7 | 27.4 | 97.91 | 98.6 % | ✘ cov |
| 6 | 90 | 5760.0 | 567.0 | 480.8 | 24.7 | 97.66 | 108.0 % | ✔ |
| **6** | **89** | **5824.7** | **619.0** | **524.8** | **26.9** | **97.86** | **116.6 %** | **✔ chosen** |
| 6 | 88 | 5890.9 | 671.9 | 569.7 | 29.2 | 98.08 | 125.1 % | ✔ |
| 6 | 87 | 5958.6 | 725.8 | 615.4 | 31.6 | 98.30 | 133.6 % | ✘ res |

$m$ = 5 cannot meet both resolution and coverage. The middle value **$(n,m) = (89, 6)$** is the best compromise.

**Final orbit**: $\tau$ = 5824.7 s, $a$ = 6997.0 km, $h$ = 619.0 km, swath 524.8 km, resolution 26.9 m, **$i$ = 97.9°**, $e$ = 0 (constant sensor range).

**Orbit control** ($\rho = 5.18\times10^{-14}$ kg/m³ at 620 km):
- $\delta a = -2\pi(5.18\times10^{-14})(1)(2.2)(6.997\times10^6)^2/150 = -0.234$ m/orbit;
- $V$ = 7.548 km/s, so $\delta\tau = 3\pi\delta a/V = -2.92\times10^{-4}$ s/orbit;
- $\delta\lambda$ = 0.00898°, $\Delta t_0$ = 2.15 s;
- $k = \sqrt{2(2.15)/2.92\times10^{-4}}$ = 121.4 → **121**;
- cycle $2k$ = **242 orbits = 16.3 days**; height lost $2k\lvert\delta a\rvert$ = **56.6 m**;
- boost by Hohmann between $r = a\mp28.3$ m: $\Delta V_1 = \Delta V_2 = 1.525\times10^{-5}$ km/s, so **0.031 m/s per cycle**;
- over 3 years: 67.2 cycles, **$\Delta V_{tot}$ = 2.05 m/s**;
- $V_{ex} = 9.81\times180$ = 1765.8 m/s, so $M_e = 150(1-e^{-2.05/1765.8})$ = **0.17 kg**.

**Data rate**:
- $V_{gd} = V R_E/a$ = 6880 m/s; $t_s$ = 26.9/6880 = 3.91 ms;
- one band: $19\,500\times8/t_s$ = 39.9 Mbps; three bands: **119.6 Mbps** uncompressed.

### Handwritten alternative: "disaster monitoring" (pp. 79–83)
- Takes 30 m resolution: swath = 19 500 × 0.03 = 585 km, giving $h\approx690$ km.
- Uses a **10 % overlap**: $d = 0.9\times585 = 527$ km, so $n = 2\pi R_E/d\approx76$.
- $\tau(690)\approx5914$ s, so $m = 5914(76)/86400\approx5$.
- Trials: (76,4) gives $a$ = 5932 km (inside the Earth!); **(76,5)** gives $h$ = 506 km, $i$ = 97.43°, resolution 22 m; (76,6) gives $h$ = 1396 km.
- Drag at 506 km ($\rho = 2.5\times10^{-13}$): $\delta a$ = −1.09 m/orbit, $\delta\tau$ = −0.00135 s/orbit, $k$ = 56, cycle 7.43 days, $\Delta a$ = 123 m.
- Hohmann $\Delta V$ = 3.41 + 3.41 cm/s = 6.81 cm/s per cycle. Over 147.5 cycles in 3 years that is **10.05 m/s**.
- Adding an inclination correction of 0.05°/yr ($\Delta V = \Delta i\,V$ ≈ 19.9 m/s) gives a worst case of about **30 m/s**, so $M_e$ = **2.5 kg** plus margin.
- Data rate: $t_s$ = 22/7050 = 3.1 ms, giving 50 Mbps per band.

> [!note] Why two answers differ
> The Excel route favours resolution (619 km, 6-day repeat). The handwritten route favours a 5-day repeat and accepts a lower orbit with 4–5× more drag. Both are defensible. The **marks come from the chain of reasoning**, not the specific $(n,m)$.

![[ast_repeat_groundtrack_solutions.png|650]]

---

## Mission 2: military surveillance imager
**Data**:
- about 275 km, panchromatic, 20 000 pixels, about 1 m resolution, FOV 4.165°, 7-bit;
- $S$ = 10 m², $M_0$ = 1000 kg; 3-year life; $\rho = 2.83\times10^{-11}$ at 280 km.

### Excel solution
- $d$ = 20 000 × 1 m = 20 km, so $h$ = 275.0 km, $\tau$ = 5400.5 s.
- $n$ = 2003.7 → 2004; $m$ = 125.26 → 125.
- Actual $h$ = 265.7 km, resolution 0.97 m, coverage 96.6 %. That is incomplete, but is full coverage even needed for surveillance?
- The explored $(m,n)$ grid shows that many combinations give more than 100 % coverage.
- **Chosen (1999, 125)**: $\tau$ = 5402.7 s, $a$ = 6654.8 km, **$h$ = 276.8 km**, swath 20.1 km, resolution 1.0 m, **$i$ = 96.6°**.

**Orbit control**:
- $\delta a$ = −173 m/orbit (very low and heavy drag); $\delta\tau$ = −0.211 s/orbit; $k$ = 4.5 → 4.
- Cycle = **8 orbits ≈ 0.5 days**; $\Delta a$ = 1.39 km.
- Hohmann: 0.806 m/s per cycle. Over 2190 cycles, **$\Delta V_{tot}$ = 1765 m/s**.
- $M_e = 1000(1-e^{-1765/1766})$ = **632 kg**, which is 63 % of the spacecraft.

**Data rate**: $V_{gd}$ = 7417 m/s, $t_s$ = 1.0/7417 = 0.136 ms, $R_b = 20\,000\times7/t_s$ = **1032 Mbps** (about 1 Gbps).

### Handwritten alternative (pp. 84–87)
- $n$ from 10 % overlap: $2\pi R_E/18\approx2226$; $m = n\tau/86400\approx139$.
- $(2226, 139)$: $\tau$ = 5395.1 s, $h$ = 270.6 km, **$i$ = 96.587°**.
- Data rate 1.039 Gbps. A 360 Gbyte (2880 Gbit) store fills in **≈ 46 min**. (The handwritten sheet divides 360 by 1.039 and gets 5.78 min: a bytes/bits slip.)
- **Downlink**:
  - A ground station at a 10° minimum elevation, using the sine rule: $\beta = \sin^{-1}[(R_E/a)\sin100^\circ]$ = 70.75°, $\alpha$ = 180 − 100 − β = 9.25°.
  - Pass = $(2\alpha/360)\tau$ = **277 s ≈ 4.6 min**.
  - At 50 Mbps a pass cannot empty the store, so use a **GEO data-relay satellite** (ESA EDRS or NASA TDRSS: 2100 kg, 1700 W). The link budget is harder.

> [!warning] Workbook slip: bytes vs bits
> The handwritten storage time divides 360 **Gbyte** by 1.039 **Gbit/s** without converting units. Correct: $360\times8/1.039 = 2772$ s ≈ **46 min**, not 5.8 min. The ground-pass time ($\alpha/180^\circ\cdot\tau$ = 277 s) is correct ✔.

---

## Takeaways for the exam
- **Low altitude costs propellant in a nonlinear way.** At 277 km the orbit needs about 1.8 km/s over 3 years; at 619 km it needs about 2 m/s. $\rho$ changes by about 500× between them.
- **Resolution, swath, altitude and coverage are coupled** through $n = 2\pi R_E/d$ and $d = 2h\tan(\beta/2)$. You cannot pick all of them independently.
- **Data rates grow as $1/p^2$** (pixel size in both directions). Sub-metre imagers need compression, on-board storage and relay satellites.

## Sources
- Workbook 2025-26 Chapter 11B questions (p. 57), Excel solutions (p. 61–75) and handwritten solutions (p. 79–87)
- Chapter 11 lectures: first-pass orbit selection, SSO/ESO, calculating orbital elements (worked example $(n,m) = (98,7)$)
