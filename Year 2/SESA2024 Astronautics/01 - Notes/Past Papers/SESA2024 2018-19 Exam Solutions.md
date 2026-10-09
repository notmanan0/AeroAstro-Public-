---
title: "SESA2024 2018-19 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Examination 2018-19 (closed book, 120 min; Section A all, Section B 2 of 3)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201819-01-SESA2024W1.pdf"]
---

# SESA2024 2018-19 Exam Solutions

> [!abstract] Paper
> - Q1: eight short questions.
> - Q2: Kepler 2, operational orbits, a space telescope, the GTO apogee burn.
> - Q3: power subsystem at 900 km.
> - Q4: SSO imager (FOV 28°) and data rate.
>
> Numbers verified in Python; not the official scheme.

## Section A (Q1)
**(i) Solar cycle (4)**: an 11-year cycle of sunspots and activity.
- At **solar maximum**:
  - more EUV heats and expands the **upper atmosphere**, so density at a given altitude rises by up to 10×, with **higher drag** and faster decay (see the density tables in 2020/21 and 2024/25);
  - more **solar particle events** (proton storms);
  - more geomagnetic storms (charging, belt enhancement).
- **Galactic cosmic rays** are *lower* at solar max, because the stronger heliospheric field shields them.

**(ii) Launch vehicles (2)**: the losses. $\Delta V = V_{ex}\ln(M_0/M_b)-\Delta V_g-\Delta V_D$ (gravity and drag). Staging is also needed.

**(iii) Momentum bias (3)**: a spacecraft carrying a constant stored angular momentum $\mathbf H_0$ (a momentum wheel, typically aligned with the orbit normal). Disturbances then only **precess** **H** by $d\psi = T\,dt/H_0$, giving **gyroscopic stiffness** about the two transverse axes. Pitch is controlled by varying the wheel speed ([[Momentum Bias and Gyroscopic Rigidity]]).

**(iv) Total impulse (3)**: $I = \int_0^{t_b}T\,dt$, the **area under the thrust–time curve**. Sketch: thrust on the vertical axis against time, with the shaded area. $I = M_eV_{ex}$, and the ΔV follows from the rocket equation.

**(v) EIRP (3)**: $EIRP = P_TG_T$ (dBW), the transmit power times antenna gain. It is the power an isotropic antenna would need to radiate to give the same flux in the beam direction. It is the spacecraft's whole contribution to the link budget ([[EIRP and G-T]]).

**(vi) Passive thermal control (3)**: choose **surface finishes** ($\alpha_S/\varepsilon$: paints, OSRs, anodising), **MLI** blankets to insulate, **radiator** size and placement, **conductive paths** (doublers, heat pipes), and spacecraft **orientation and geometry**. There is no power or moving parts ([[Passive vs Active Thermal Control]]).

**(vii) EO payload requirements (4)**:
- **Orbit**:
  - **near-polar** for global coverage;
  - **Sun-synchronous** for constant illumination;
  - **circular** for constant resolution and scale;
  - LEO 700–900 km, balancing resolution, drag and swath.
- **Attitude**: **Earth (nadir) pointing**, 3-axis stabilised, with stable pointing during imaging.

**(viii) Thrown satellite (3)**: **D**.
- Throwing it forwards adds energy, so it has a larger $a$ and a **longer period**.
- Half an orbit later it is **above** (at its higher apogee) and **behind** the ISS.
- Over successive orbits it drifts ever further behind.

## Q2
**(i) Kepler 2 (5)**: in time $dt$ the radius sweeps a thin triangle of area $dA = \tfrac12r(r\,d\theta)$. So

$$\frac{dA}{dt} = \tfrac12r^2\dot\theta = \frac h2 = \text{constant}$$

Equal areas are swept in equal times ([[Orbital Angular Momentum]]).

**(ii) Four operational orbits (8)**: LEO, SSO, MEO, GEO and Molniya/HEO. See the table in [[SESA2024 2013-14 Exam Solutions|2013/14 Q2(i)]].

**(iii) Space telescope (5)**:
- **Payload requirements**: pointing accuracy and stability (arcsec over long exposures); a low background (thermal, stray light, Earth IR) with long uninterrupted views; possibly cryogenic temperatures.
- **System requirements**: fine ACS (reaction wheels plus star trackers), thermal stability, high data downlink, power, servicing or lifetime.
- **Suitable orbit**:
  - **Sun–Earth L2** or a high Earth orbit (JWST, Gaia): stable thermal conditions, no eclipses, Earth and Sun both behind.
  - Alternatively a LEO at about 550 km (Hubble) if servicing is required.

**(iv) Apogee ΔV (4)**:
- A circular GEO needs $V = \sqrt{\mu/r_a}$.
- ΔV = circular speed − $V_{Ta}$ = $\sqrt{\mu/r_a}-\sqrt{\dfrac{\mu}{r_a}\dfrac{2r_p}{r_p+r_a}} = \sqrt{\dfrac{\mu}{r_a}}\left(1-\sqrt{\dfrac{2r_p}{r_p+r_a}}\right)$.

**(v) Propellant (8)**:
- $r_p$ = 6628 km and $r_a$ = 42 164 km give **ΔV = 1.472 km/s**. ($V_{GEO}$ = 3.075 km/s and $V_{Ta}$ = 1.603 km/s.)
- $V_{ex}$ = 320 × 9.81 = 3139 m/s.
- $M_p = 6000(1-e^{-1472/3139})$ = **2246 kg**.

## Q3: Power at 900 km, 350 W, 5 years
**(i) (4)**: the power subsystem must **generate, store, condition and distribute** electrical power for the whole mission (BOL to EOL).
- **Primary**: the source, e.g. solar arrays, RTG, fuel cell.
- **Secondary**: storage (rechargeable batteries) that supplies eclipse and peak loads and is recharged by the primary.

**(ii) Other sources (4)** ([[Spacecraft Power Sources]]):
- **RTGs** (Pu-238: outer planets, long missions);
- **fuel cells** (H₂/O₂: Apollo, Shuttle; days to weeks);
- **primary batteries** (short missions, probes);
- **nuclear fission reactors** (high power, e.g. SNAP-10A, Soviet RORSATs);
- solar thermal (dynamic).

**(iii) Eclipse (7)**:
- $a$ = 7278 km, $\tau$ = 103.0 min.
- Worst case (β = 0): $t_e = [180^\circ-2\cos^{-1}(6378/7278)]/360^\circ\cdot\tau$ = **35.0 min**.
- **25 540 cycles** in 5 years.

**(iv) Batteries (10)**: $E = Pt_e$ = 350 × 0.5836 h = 204 W·h. With DoD 20 %, **1021 W·h stored**.

| | Cells (≈28 V) | $V_B$ | $C$ | Mass |
|---|---|---|---|---|
| Li-ion (4.1 V) | 7 | 28.7 V | **35.6 A·h** | **7.9 kg** |
| NiCd (1.25 V) | 22 | 27.5 V | **37.1 A·h** | **34.0 kg** |

**Choose Li-ion**: about 4× lighter (130 against 30 W·h/kg), with no memory effect and high efficiency. The 20 % DoD comfortably supports 25 500 cycles.

**(v) Array (5)**:
- $t_s$ = 68.0 min.
- Li-ion: $R = 0.2(35.6)/1.133$ = 6.28 A, so $P_{EOL}$ = 350 + 6.28(33.5) = **560 W**.

$$A = \frac{560}{1360\cos15^\circ(0.23)(0.9)(1-0.4)} = \mathbf{3.44\ m^2}$$

(With NiCd, 570 W and 3.49 m².)

## Q4: SSO imager (FOV 28°, 7-year life)
**(i) $(n, m)$ (7)**:
- Swath $d = 2h\tan14^\circ$ = 0.499$h$. Complete equatorial coverage needs $nd\ge2\pi R_E$.
- For 700–900 km, search for the smallest $m$:

| $(n, m)$ | $h$ (km) | Swath | Coverage |
|---|---|---|---|
| (85, 6) | 836.8 | 417 | 89 % ✗ |
| **(99, 7)** | **844.9** | **421.3** | **104 % ✔** |
| (100, 7) | 796.6 | 397 | 99 % ✗ |
| (113, 8) | 851.0 | 424 | 120 % ✔ |

**(99, 7)** is the shortest repeat that closes the gaps at the equator. (For $m\le6$ the per-day swath budget is too small at any allowed height.)

**(ii) (6)**:
- $\tau = (7/99)86400$ = 6109.1 s, $a$ = 7222.9 km.
- **$h$ = 844.9 km**, **$i$ = 98.79°**.
- **LST**: a **10:30 am descending node** (or a mirror 13:30 ascending). The Sun elevation is moderate (good illumination with shadow relief for the visible and NIR bands), it avoids afternoon cloud, and it is consistent with other EO data.

**(iii) Swath, pixel, data rate (17)**:
- Swath = **421.3 km**.
- Pixel = 421.3 km/13 000 = **32.4 m**.
- $V$ = 7.429 km/s, $V_g$ = 6.560 km/s, line time 32.4/6560 = 4.94 ms.
- $R_b$ = 13 000 × 16 × 6/4.94 ms = **252.6 Mbps**.
- **Compression to ≤ 220 Mbps** (1.15:1):
  - requantise to **13-bit** words (205 Mbps; 14 bits would give 221 Mbps, just over the limit), or
  - lossless DPCM/Rice coding (routinely 1.5–2:1), or
  - bin one band.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
