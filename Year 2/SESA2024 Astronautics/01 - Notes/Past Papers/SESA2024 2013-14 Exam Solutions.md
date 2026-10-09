---
title: "SESA2024 2013-14 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Examination 2013-14 (closed book, 120 min; Section A all, Section B 2 of 3)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201314-01-SESA2024W1.pdf"]
---

# SESA2024 2013-14 Exam Solutions

> [!abstract] Paper
> - Q1: nine short questions.
> - Q2: orbit types, the energy constant, and a debris intercept by Hohmann transfer.
> - Q3: thermal balance for a GEO spinner.
> - Q4: hyperspectral remote-sensing orbit and data rate.
>
> Numbers verified in Python; not the official scheme.

## Section A (Q1)
**(i) Design phases (4)**: the ECSS life cycle ([[Systems Engineering Design Phases]]):
- **0/A**: mission analysis and feasibility;
- **B**: preliminary definition;
- **C**: detailed definition;
- **D**: qualification and production;
- **E**: utilisation (operations);
- **F**: disposal.

Reviews (MDR, PRR, SRR, PDR, CDR, QR, AR, FRR) are the gates between phases.

**(ii) High-radiation orbits (3)**:
- **MEO** (navigation constellations, about 20 000 km) sits in the outer Van Allen belt (trapped electrons).
- **GTO/HEO** orbits pass through **both belts** twice per orbit.
- High-inclination LEO crosses the **South Atlantic Anomaly** and the polar horns.

The belts are charged particles trapped by the geomagnetic field. Dose causes cell degradation, single-event upsets and electronics damage.

**(iii) Launcher stages (3)**: typically **2–3 stages**.
- Staging discards dead structural mass, so each later stage starts with a better mass ratio.
- The gain diminishes with each extra stage. Meanwhile every stage adds engines, separation systems, interstage mass, cost and failure points (reliability).
- Beyond about 3 stages the added complexity outweighs the ΔV gain.

**(iv) Internal vs external torquers (4)** ([[Attitude Sensors and Torquers]]):
- **Internal** torquers (reaction/momentum wheels, CMGs) **exchange angular momentum** with the spacecraft body. They cannot change the total **H**.
- **External** torquers (thrusters, magnetorquers, solar sails, gravity gradient) apply torque **from outside**. They change the total **H**, so they are needed for momentum dumping and against secular disturbances.

**(v) Temperature and solar cells (3)**: efficiency **falls as temperature rises**. Open-circuit voltage drops by about 2 mV/°C per Si cell, and efficiency by about 0.5 %/°C, while the current rises only slightly. Cells are most efficient when cold, e.g. at **eclipse exit** ([[Solar Cells and Arrays]]).

**(vi) Power–gain trade-off (3)**: EIRP = $P_TG_T$, so the same link can be closed with more RF power (mass, power subsystem, heat) or a larger, higher-gain antenna. A larger antenna costs mass and stowage, may need deployment, and has a narrower beam ($\theta_{3dB} = 72\lambda/D$), which demands tighter pointing (ACS). See [[EIRP and G-T]].

**(vii) Civil remote sensing (3)**:
- **Payload requirements**:
  - global coverage, so near-polar;
  - constant illumination, so Sun-synchronous;
  - constant scale and resolution, so circular.
- **Orbit**:
  - $a\approx7078$–$7278$ km ($h$ = 700–900 km);
  - $e\approx0$;
  - $i\approx98^\circ$ (retrograde SSO).

**(viii) SSO (3)**: $J_2$ makes the orbit plane precess. Choosing $i$ (about 98° in LEO) so that $\dot\Omega$ = +0.9856°/day (360°/year, eastward) keeps the plane fixed relative to the Sun. Each latitude is then overflown at the **same local solar time** ([[Sun-Synchronous Orbit]]).

**(ix) Orbit control strategy (4)** ([[Orbit Control Cycle]]):
1. Boost the orbit slightly **above** the nominal height, so the period is too long and the track drifts one way to the tolerance edge $+E_0$.
2. Drag lowers $a$ and shortens $\tau$, so the drift slows, reverses at nominal and heads to $-E_0$ after $2k$ orbits.
3. Re-boost (Hohmann) by $\Delta a = 2k|\delta a|$ and repeat.

Sketch: along-track drift against time, a parabola between $\pm E_0$ with the boost at each $-E_0$.

## Q2
**(i) Four orbits (8)** ([[Keplerian Orbital Elements]]):
| Orbit | Parameters | Missions |
|---|---|---|
| LEO | 200–2000 km, any $i$ | ISS, crewed, EO, constellations |
| SSO | 600–900 km, $i\approx98^\circ$ | Earth observation, weather |
| MEO | about 20 000 km, $i\approx55^\circ$ | navigation (GPS, Galileo) |
| GEO | 35 786 km, $i = 0$, $e = 0$ | communications, weather (fixed over one longitude) |
| HEO (Molniya) | 500 × 40 000 km, $i = 63.4^\circ$ | high-latitude comms (12 h) |

**(ii) Energy constant (8)**: see [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] and [[SESA2024 Workbook Ch5 - Mission Analysis Solutions|workbook Ch5 Q2]].
- $\varepsilon = V_p^2/2-\mu/r_p = V_a^2/2-\mu/r_a$ with $V_a = V_pr_p/r_a$.
- Eliminating $V_p$: $\varepsilon = -\mu/(r_a+r_p) = -\mu/2a$.
- So $V^2/2-\mu/r = -\mu/2a$, which gives $V^2 = \mu(2/r-1/a)$.

**(iii) Debris intercept (14)**:
- (a) $r_p = 8500(0.9)$ = **7650 km**, and $V_p = \sqrt{\mu(2/7650-1/8500)}$ = **7.571 km/s**.
- (b) Parking orbit $r_1$ = 6678 km, $V_1$ = 7.726 km/s. Transfer $a_T = (6678+7650)/2$ = 7164 km, $V_{Tp} = \sqrt{\mu(2/6678-1/7164)}$ = 7.984 km/s, so **ΔV = 0.258 km/s**.
- (c) Half a transfer period: $t = \pi\sqrt{a_T^3/\mu}$ = 3017 s = **50.3 min** before the encounter.
- (d) At the transfer apoapsis, $V_{Ta} = \sqrt{\mu(2/7650-1/7164)}$ = 6.969 km/s. Both velocities are tangential and in the same direction, so the relative speed is 7.571 − 6.969 = **0.60 km/s** (the debris is faster and overtakes).

## Q3: Thermal
**(i) Why thermal control (4)**:
- Equipment works, and survives, only within temperature limits:
  - batteries 0–20 °C;
  - hydrazine above 2 °C (it freezes);
  - electronics about −10 to 40 °C;
  - optics need stability.
- The environment swings between direct Sun (1350 W/m²) and a 3 K sky in eclipse.
- Gradients cause thermal distortion (pointing, optics).

**(ii) Balance equation (10)** ([[Spacecraft Thermal Balance Equation]]):
- Terms, left to right:
  - solar input;
  - albedo input (reduced by $\cos\phi$ away from the subsolar point, and by $F = (R_E/R)^2$);
  - Earth IR input;
  - internal dissipation;
  - output = emitted IR over the whole surface.
- Assumptions: isothermal, steady state, no conduction or storage, and $\alpha_{IR} = \varepsilon$ (Kirchhoff).
- When the Sun dominates, $T\approx[q_S\alpha_SA^{proj}/(\sigma\varepsilon A_{surf})]^{1/4}\propto(\alpha_S/\varepsilon)^{1/4}$, so a finish choice sets $T$ passively ([[Absorptance and Emittance]]).

**(iii) GEO spinner (16)**: $D$ = 2 m, $L$ = 1.8 m.
- $A^{proj} = DL$ = 3.6 m² (toward both the Sun and the Earth; the axis is normal to the orbit plane).
- $F = (1/6.611)^2$ = 0.02288.
- $\sum\varepsilon A = 0.75\pi(2)(1.8)+0.05(2)\pi(1)^2$ = 8.797 m².

| | Inputs (W) | $T$ |
|---|---|---|
| (a) Noon | Sun 3645 + albedo 28.4 + IR 14.8 + $P$ 300 | **25.9 °C** |
| (b) Terminator | Sun 3645 + IR 14.8 + 300 | **25.4 °C** |
| (c) Eclipse | IR 14.8 + 300 | **−114.6 °C** |

**The eclipse is the concern** (up to about 69 min, near the equinoxes). Remedies:
- heaters powered from the battery, sized into the power budget;
- MLI on the ends and louvres to cut radiation when cold;
- the spacecraft's thermal mass, because the real drop is transient and much smaller than the equilibrium value.

## Q4: Hyperspectral SSO (FOV 64°, 8-year life)
**(i) $(n, m)$ (7)**:
- Basic payload requirement: $h$ = 700–900 km, so $\tau\approx$ 5926–6179 s, i.e. 14.0–14.6 orbits/day.
- Swath $d = 2h\tan32^\circ\approx1.25h$ (about 1000 km at 800 km), so $n\ge2\pi R_E/d\approx40$.

| $(n,m)$ | $h$ (km) | $i$ | Swath (km) | Coverage |
|---|---|---|---|---|
| (29,2) | 725.8 | 98.29° | 907 | 66 % ✗ |
| **(43,3)** | **780.7** | **98.52°** | **975.7** | **105 % ✔** |
| (44,3) | 671.9 | 98.07° | 840 | 92 % ✗ (and below 700 km) |

The shortest repeat with complete, overlapping coverage is **(43, 3)**: every point is revisited every 3 days.

**(ii) Orbit (6)**:
- $\tau = (3/43)86400$ = 6027.9 s, $a$ = 7158.7 km, **$h$ = 780.7 km**.
- $\cos i = 0.9856/(-2.0647\times10^{14}a^{-3.5})$, so **$i$ = 98.52°**.
- **LST about 10:30 descending node**:
  - the Sun is high enough for good illumination, with shadows helping relief;
  - it is before the afternoon convective cloud builds up;
  - it matches the heritage of other missions (Landsat/SPOT), which makes their data comparable.

**(iii) Swath, pixel, data rate (17)**:
- Swath $d = 2(780.7)\tan32^\circ$ = **975.7 km**.
- Pixels are pairs: 6000/2 = 3000 per line, so the pixel is 975.7/3000 = **325 m**.
- $V = \sqrt{\mu/a}$ = 7.462 km/s. Ground speed $V_g = VR_E/a$ = 6.648 km/s.
- Line time $t = p/V_g$ = 48.9 ms.
- $R_b$ = 3000 × 16 × 60/0.0489 = **58.9 Mbps**.
- **Compression to ≤ 50 Mbps** (1.18:1):
  - requantise to 13-bit words (47.8 Mbps), or
  - lossless DPCM or entropy coding (≥ 1.2:1 is routine for imagery), or
  - drop or bin redundant bands.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
