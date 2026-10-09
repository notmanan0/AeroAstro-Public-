---
title: "SESA2024 14 - Orbit Control, Drag and Payload Data Rate"
module: "SESA2024 Astronautics"
type: topic
stream: "Remote Sensing Case Study"
order: 14
tags:
  - sesa2024
  - remote-sensing
  - orbit-control
  - atmospheric-drag
  - data-rate
aliases: ["Orbit maintenance", "Drag make-up", "Ground-track control", "Data rate"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]", "[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
next_topics: ["[[SESA2024 15 - Space Sustainability, Debris and NewSpace]]"]
key_concepts: ["[[Orbit Control Cycle]]", "[[Payload Data Rate]]", "[[Swath Width and Push-Broom Imaging]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]]"]
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf", "03 - Exams & Past Papers/SESA2024-201516-01-SESA2024W1.pdf", "03 - Exams & Past Papers/SESA2024-201718-01-SESA2024W1.pdf"]
---

# SESA2024 14 - Orbit Control, Drag and Payload Data Rate

> [!abstract] Summary
> Drag lowers a LEO orbit by $\delta a = -2\pi\rho(SC_D/m)a^2$ per orbit and shortens its period by $\delta\tau = 3\pi\delta a/V$. The ground track therefore drifts East relative to its reference grid.
>
> To keep the track within $\pm E_0$ at the equator, the orbit is boosted **above** nominal and allowed to decay through it. The track error is a parabola in orbit number. The cycle lasts $2k$ orbits with $k = \sqrt{2\Delta t_0/|\delta\tau|}$. The height lost per cycle ($2k|\delta a|$) is restored by a small Hohmann transfer.
>
> The payload data rate is pixels × bits × bands ÷ the time to cross one ground pixel.
>
> *These equations come from the workbook and are quoted in the 2015/16 and 2017/18 data sheets. Recent papers expect you to know them.*

## Key Concepts
- [[Orbit Control Cycle]] · [[Payload Data Rate]] · [[Swath Width and Push-Broom Imaging]]

---

## 1. Drag decay per orbit
Drag force $D = \tfrac12\rho V^2SC_D$. Over one circular orbit the energy lost is $D\cdot2\pi a$. Using $\varepsilon = -\mu/2a$, so $d\varepsilon = (\mu/2a^2)\,da$:

$$
\frac{\mu m}{2a^2}\delta a = -\tfrac12\rho V^2SC_D(2\pi a),\qquad V^2 = \frac{\mu}{a}\ \Rightarrow\ \boxed{\delta a = -2\pi\rho\frac{SC_D}{m}a^2\ \text{per orbit}}
$$

(Asked as a derivation in 2019/20 B3(ii), 6 marks.)

**Period change** from $\tau = 2\pi a^{3/2}/\sqrt\mu$:

$$
\delta\tau = \frac{d\tau}{da}\delta a = 3\pi\sqrt{\frac{a}{\mu}}\,\delta a = \frac{3\pi}{V}\delta a
$$

- **The spacecraft speeds up as drag acts**: $V = \sqrt{\mu/a}$ rises as $a$ falls. This is the drag paradox.
- $\rho$ varies **by about 10×** between solar minimum and maximum (see the 2020/21 table and the 2024/25 Figure B3.2). Always design for the **worst case (high solar activity)**.
- **Drag sail for end-of-life disposal** (2019/20 B3(iii)): $\delta a\propto S$, so a 9 m² sail on a 1 m² spacecraft makes it decay **9× faster**. At 7078 km with ρ = 10⁻¹⁴ kg/m³ and 50 kg: 0.14 m/orbit becomes 1.24 m/orbit. Effective for compliance with the 25-year (or FCC 5-year) rule.

## 2. Ground-track control
- **Tolerance** $E_0$ (km) at the equator becomes a longitude tolerance and a time tolerance:

$$
\delta\lambda = \frac{2E_0}{R_E}\cdot\frac{180}{\pi}\ (\text{deg}),\qquad \Delta t_0 = \frac{\delta\lambda}{\omega_E},\quad\omega_E = 0.004178^\circ/\text{s}
$$

- **Strategy**:
  1. Boost to $a_{nom}+\Delta a/2$. The period is now slightly long, so the track drifts West.
  2. Drag shrinks the period, and the drift slows, reverses, and returns East.
  3. Boost again when the error reaches the other limit.
  4. The accumulated timing error grows as $\tfrac12|\delta\tau|j^2$, so the error–orbit plot is a **parabola** spanning $\pm E_0$.
- Half-cycle $k$ and full cycle $2k$:

$$
k = \sqrt{\frac{2\Delta t_0}{|\delta\tau|}},\qquad \Delta a_{decay} = 2k|\delta a|,\qquad T_{cycle} = 2k\tau
$$

![[ast_orbit_control_cycle.png|620]]

**Worked (workbook 11B Q1)**: 619 km, ρ = 5.18 × 10⁻¹⁴, $S$ = 1 m², $m$ = 150 kg, $E_0$ = 0.5 km:
- $\delta a$ = −0.234 m, $\delta\tau$ = −2.92 × 10⁻⁴ s, $\Delta t_0$ = 2.15 s;
- **$k$ = 121**, cycle **242 orbits = 16.3 days**, $\Delta a$ = 56.6 m.

(Exam: "explain, with a diagram, the full orbit control strategy required to maintain a repeating ground track", 2013/14 and 2016/17, 4 marks. Draw the parabola between $\pm E_0$ and the saw-tooth in $a$.)

## 3. ΔV and propellant for orbit maintenance
Each cycle, a Hohmann transfer between $r_{low} = a-\Delta a/2$ and $r_{high} = a+\Delta a/2$:

$$
\Delta V_{cycle} = \Delta V_1+\Delta V_2\approx\frac{V\,\Delta a}{2a}
$$

- Over the life: $N = \text{life}/T_{cycle}$, so $\Delta V_{tot} = N\Delta V_{cycle}$.
- Propellant: $M_e = M_0(1-e^{-\Delta V_{tot}/g_0I_{sp}})$.

| Case | $h$ | $k$ / cycle | $\Delta V_{tot}$ | $M_e$ |
|---|---|---|---|---|
| Workbook civil (150 kg, 1 m², 3 yr) | 619 km | 121 / 16.3 d | 2.05 m/s | 0.17 kg |
| Workbook handwritten (150 kg) | 506 km | 56 / 7.4 d | 10 m/s (+ 20 m/s for inclination) | 2.5 kg |
| Workbook military (1000 kg, 10 m², 3 yr) | 277 km | 4 / 0.5 d | **1765 m/s** | **632 kg** |

**Three elements of a remote-sensing ΔV budget** (2015/16 Q1(vii)):
1. **Orbit acquisition / injection correction**: from the launcher's dispersion.
2. **Drag make-up**: ground-track maintenance.
3. **Inclination / LST maintenance** (Sun perturbations drift $i$, and so the LST) and **end-of-life disposal**.

## 4. Payload data rate (push-broom)
- Ground speed: $V_{gd} = V_{orb}\dfrac{R_E}{a}$ (the sub-satellite point moves more slowly).
- Line (sample) time: $t_s = p/V_{gd}$, the time to advance one pixel.

$$
\boxed{R_b = \frac{N_{pixels}\times\text{bits per pixel}\times N_{bands}}{t_s}}
$$

- **Paired sampling** (2013/14, 2016/17): if CCD elements are read in pairs and each pair is one 16-bit word, the words per line are $N/2$ and the effective ground pixel is two elements.
- **FOV and pixel size from a detector**: $d = N\times p$ and $\beta = 2\tan^{-1}(d/2h)$.

| Mission | $t_s$ | $R_b$ uncompressed |
|---|---|---|
| Workbook civil (19 500 px × 3 bands × 8 bit, 26.9 m) | 3.91 ms | 119.6 Mbps |
| Workbook military (20 000 px × 7 bit, 1 m) | 0.136 ms | 1.03 Gbps |

**Compression** (2013/14, 2014/15, 2017/18): if the downlink limit is exceeded, reduce the data by:
- lossless coding (for example differential PCM, fewer bits per pixel);
- **fewer bits per pixel** (16 → 12 bits);
- summing adjacent pixels or bands (lower resolution);
- imaging only land or cloud-free regions (duty cycle);
- on-board storage with relay satellites (EDRS, TDRSS).

Example: to cut a data volume by 25 % with 8-bit words, send 6-bit words, or drop one band in four.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]] · Next: [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]
- Hohmann: [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]] · Propellant: [[SESA2024 07 - Spacecraft Propulsion]]

## Sources
- Workbook 2025-26 Ch 11B solutions; data sheets of the 2015/16 and 2017/18 papers; 2019/20 B3 (drag sail)
