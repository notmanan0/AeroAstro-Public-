---
title: "SESA2024 2014-15 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Examination 2014-15 (closed book, 120 min; Section A all, Section B 2 of 3)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201415-01-SESA2024W1.pdf"]
---

# SESA2024 2014-15 Exam Solutions

> [!abstract] Paper
> - Q1: ten short questions.
> - Q2: the launcher ΔV equation, and Ariane 5.
> - Q3: ISS power (eclipse, batteries, array).
> - Q4: pan imager SSO, data rate, launch azimuth.
>
> Numbers verified in Python; not the official scheme.

## Section A (Q1)
**(i) Van Allen belts (3)**:
- Trapped protons (inner belt, about 1000–6000 km) and electrons (outer belt, about 13 000–60 000 km).
- Design impacts:
  - total dose, which degrades solar cells and electronics;
  - single-event upsets and latch-up;
  - surface and internal charging.
- Responses:
  - rad-hard parts, shielding and cover glass;
  - array oversizing (EOL degradation);
  - EDAC memory;
  - orbits that avoid the belts or pass through them quickly.

**(ii) Energy equation (3)**: $\varepsilon = V^2/2-\mu/r$ is the **specific mechanical energy**, kinetic plus potential (zero at infinity). Gravity is conservative, so it is **constant** along the orbit. Speed trades against radius: the satellite is fastest at perigee and slowest at apogee. $\varepsilon = -\mu/2a$ depends only on $a$. $\varepsilon<0$ means bound, $\varepsilon = 0$ escape. See [[Vis-Viva Equation]].

**(iii) Hohmann transfer (2)**: the minimum-energy two-impulse transfer between coplanar circular orbits. It follows an ellipse tangent to both orbits, with perigee on the inner orbit and apogee on the outer. It takes half the transfer period ([[Hohmann Transfer]]).

**(iv) Products of inertia (2)**:
- They are the off-diagonal terms $I_{xy} = \int xy\,dm$, etc. (with a minus sign in $[\mathbf I]$).
- They measure how asymmetric the mass distribution is about the body axes. Non-zero values mean the body axes are **not principal axes**, so spinning about a body axis gives $\mathbf H$ not parallel to $\boldsymbol\omega$, i.e. wobble ([[Inertia Matrix]]).

**(v) Nutation (3)**: a spinner disturbed by a torque impulse has **H** fixed in inertial space, but the spin axis cones around it at the **nutation frequency**. Energy dissipation (flexing, fuel slosh) damps nutation about the maximum-inertia axis and grows it about the minimum axis (Explorer 1). Nutation dampers remove it.

**(vi) Specific impulse (3)**:
- $I_{sp} = I/(M_eg_0) = V_{ex}/g_0$ (in seconds): the impulse per unit weight of propellant.
- Physically, it measures **propellant efficiency**. A higher $I_{sp}$ needs less propellant for a given ΔV, exponentially so via the rocket equation.

**(vii) Digital modulation (4)**:
- The three types are **ASK** (amplitude), **FSK** (frequency) and **PSK** (phase) shift keying.
- **PSK (BPSK/QPSK)** is the common choice: it has the best BER against $E_b/N_0$ and a constant envelope ([[Bit Error Rate and Eb-N0]]).

**(viii) Remote-sensing orbit drivers (4)** ([[SESA2024 11 - Payload and Orbit Selection]]):
- **$a$**: resolution and swath (lower is better) against drag, lifetime and coverage (higher is better). Also the repeat track: $\tau = (m/n)86400$.
- **$i$**: global coverage and the Sun-synchronous condition, about 98°.
- **$e$**: 0, for constant scale and resolution.
- **RAAN**: sets the node LST (e.g. 10:30), i.e. the illumination and cloud conditions.

**(ix) Eclipse fraction (4)**:
- It is governed mainly by **altitude ($a$)** and the **Sun–orbit-plane angle β**, which depends on $i$, RAAN and season. High β or high $a$ gives short or no eclipses.
- It drives:
  - **power**: battery capacity, cycle count (lifetime), and extra array area to recharge;
  - **thermal**: cold soak, so heaters are needed, and thermal cycling fatigue.

**(x) CCD push-broom (2)**: a linear CCD array across-track images one line of the swath. The spacecraft's motion sweeps successive lines along-track. There are no moving parts, and each element has a long dwell time (good SNR). Sketch: the detector line, its footprint line, and the ground-track direction ([[Swath Width and Push-Broom Imaging]]).

## Q2: Launcher
**(i) Derivation (15)**: along the flight path, with flight-path angle γ:

$$M\frac{dV}{dt} = \dot mV_{ex}-D-Mg\sin\gamma,\qquad \dot m = -\frac{dM}{dt}$$

Dividing by $M$:

$$dV = -V_{ex}\frac{dM}{M}-g\sin\gamma\,dt-\frac DM\,dt$$

Integrating from $M_0$ to $M_b$ over time $t$:

$$\Delta V = V_{ex}\ln\frac{M_0}{M_b}-\underbrace{\int_0^t g\sin\gamma\,dt}_{\Delta V_g}-\underbrace{\int_0^t\frac DM\,dt}_{\Delta V_D}$$

**(ii) Ariane 5 (15)**: total $M_0$ = 707 350 kg (all stages + 18 500 kg payload). Each stage's structure is dropped before the next stage fires.

| Stage | $M_0$ (kg) | $M_b$ (kg) | $M_0/M_b$ | ΔV (km/s) |
|---|---|---|---|---|
| 1 | 707 350 | 232 350 | 3.044 | 3.117 |
| 2 | 216 850 | 51 850 | 4.182 | 5.652 |
| 3 | 37 850 | 22 950 | 1.649 | 2.161 |

- **$\Delta V_{ideal}$ = 10.93 km/s**.
- After 1.92 km/s of losses: **ΔV = 9.01 km/s**.
- That is more than the circular speed in LEO (7.78 km/s at 200 km), so **yes, it can reach orbit**, with margin for the higher insertion altitude. Launching eastward also gains 0.46 km/s from Earth's rotation.

## Q3: ISS power
**(i) Solar array (10)** ([[Solar Cells and Arrays]]):
- **Construction**: cover glass (radiation and UV protection, AR coating) → adhesive → cell → interconnects → Kapton/substrate → honeycomb panel.
- **Temperature**: $V_{oc}$ and efficiency fall as $T$ rises (Si about −0.5 %/°C).
- **Sun angle**: power ∝ cos θ (plus extra reflection loss at grazing angles).
- **Radiation**: displacement damage cuts $I_{sc}$ and $V_{oc}$. This is the degradation factor $D_0$, and the reason arrays are sized at EOL.

**(ii) Eclipse and cycles (7)**:
- $a$ = 6728 km, so $\tau$ = 5492 s = 91.5 min.
- $t_e = \dfrac{180^\circ-2\cos^{-1}(R_E/a)}{360^\circ}\tau$ = **36.3 min** (worst case, β = 0).
- Over 15 years: **86 190 cycles**.

**(iii) Batteries (8)**: $C = Pt_e/(\text{DoD}\,V_B)$.

| | DoD | $C$ (A·h) | Energy (kWh) | Mass |
|---|---|---|---|---|
| NiCd | 10 % | 43 250 | 1211 | **40.4 t** |
| NiH₂ | 30 % | 14 420 | 404 | **8.1 t** |

**Choose NiH₂**: five times lighter, because it tolerates a deeper DoD at high cycle counts and has a higher energy density. It is also the ISS heritage choice (later replaced by Li-ion).

**(iv) Array (5)**:
- $t_s$ = 0.920 h, so $R = \text{DoD}\,C/t_s$ = 4700 A (the same for both batteries, since $\text{DoD}\,C = Pt_e/V_B$).
- $P_{EOL} = P+RV_a$ = 200 + 4700(33.5)/1000 = **357.5 kW**.

$$A = \frac{P_{EOL}}{S\cos\theta\,\eta\,\eta_p(1-D_0)} = \frac{357\,500}{1365\cos10^\circ(0.18)(0.9)(0.65)}\approx\mathbf{2525\ m^2}$$

## Q4: Pan imager (swath 90 km, 30-day coverage)
**(i)(a) $h$ and $i$ (12)**:
- $n_{min} = 2\pi R_E/d$ = 445.3, so $n\ge446$ with $\gcd(n, 30) = 1$ (otherwise the track repeats early).
- 446, 447 and 448 fail; **$n$ = 449**.
- $\tau = (30/449)86400$ = 5772.8 s, $a$ = 6955.3 km, **$h$ = 577.3 km**, **$i$ = 97.70°**.

**(i)(b) FOV**: $2\tan^{-1}(45/577.3)$ = **8.91°**.

**(ii) Data rate (12)**:
- 90 km/10 m = 9000 pixels per line.
- $V$ = 7.570 km/s and $V_g = VR_E/a$ = 6.942 km/s, so the line time is 10/6942 = 1.44 ms.
- $R_b$ = 9000 × 8/1.44 ms = **50.0 Mbps**.
- **25 % reduction** to 37.5 Mbps:
  - requantise 8 → 6 bits per pixel, or
  - use **DPCM**: transmit the difference between adjacent pixels in 6 bits, because neighbouring pixels are highly correlated.

**(iii) Launch azimuth (6)**:
- A site can reach inclinations only with $|L|\le i$ (prograde), or $|L|\le180^\circ-i$ (retrograde). It is at the node crossing, or at the orbit's extreme latitude, where a direct launch into the plane is possible. Lower inclinations need a costly plane change.
- $\sin\beta = \cos i/\cos L = \cos97.70^\circ/\cos5^\circ$, so β = −7.73°.
  - **Launch at the ascending node** (heading north): azimuth **352.3°** (7.7° west of north).
  - **Launch at the descending node** (heading south): azimuth $180^\circ-\beta$ = **187.7°** (7.7° west of south).
- Both are westward, i.e. retrograde, so they **lose** the Earth-rotation benefit.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
