---
title: "SESA2024 2021-22 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Final Assessment 2021/22 (online open-book)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-202122-01-SESA2024.pdf"]
---

# SESA2024 2021-22 Exam Solutions

> [!abstract] Paper
> - B1: Apollo 9 contingency de-orbit (rocket equation, vis-viva, true anomaly, ground track).
> - B2: Meteosat MSG thermal and power.
> - B3: Mars relay orbiter (Sun- and Mars-synchronous orbit, footprint, orbit control).
>
> Verified in Python; not the official scheme.

## Section A
**A1 (3)**: old technology has flight heritage and qualification data. That minimises **cost, schedule and technical risk (uncertainty)** and simplifies approval. New technology needs development and qualification, and it adds margin demands.

**A2 (5)**: in GEO the Earth is a small disc in a fixed direction. A spinner with its axis normal to the orbit (parallel to Earth's axis) scans the Earth once per revolution (Meteosat spin-scan imaging). It is gyroscopically stable, simple, and evenly heated. In LEO the Earth fills half the sky and nadir rotates once per orbit, so an inertially fixed spin axis cannot keep a push-broom imager on the ground. A 3-axis nadir-pointing platform is needed.

**A3 (4)**: $C/N_0 = EIRP+G_R/T_R-L_{FS}-L_A+228.6$. The deep-space $L_{FS}\propto\rho^2$ is enormous and the spacecraft EIRP is limited, so the ground must maximise $G_R$ (a large dish, $\propto D^2$) and minimise $T_R$ (cryogenic LNAs). Both raise $C/N_0$ and hence the data rate.

**A4 (4)**:
- **Chemical**: a two-burn Hohmann ellipse, a half-orbit coast of about 5 h.
- **EP**: a continuous low-thrust **spiral** of many slowly widening revolutions (weeks to months), roughly circular throughout.

**A5 (2)**: at L1 the Sun face sees about 1370 W/m² all the time. Use a **low $\alpha_S/\varepsilon$** finish (OSR/SSM or white paint) to reject heat.

**A6 (5)**: all fragments start at one point with different ΔV, so they have different $a$ and **different periods** (Kepler 3). The differential period makes them shear along-track: forward-kicked fragments fall behind and rear-kicked ones move ahead. Within a few orbits they form a ring. Varying $e$ spreads them radially too.

**A7 (2)**: an SSO crosses the node at a **fixed LST**, so one day later it is again **10:00 am**. (The $m$ = 5 repeat governs *where*, not *when*.)

## B1: Apollo 9
**(i) (2)** The perigee was lowered with apogee unchanged, so the burn happened at **apogee** (retrograde). Place the cross at the apogee point, 180° from the new perigee in the Northern hemisphere.

**(ii) (6)** $\dot m = T/(g_0I_{sp}) = 410/(9.81\times336)$ = 0.124 kg/s. Over 510 s, **$M_p$ = 63.4 kg**.

$$\Delta V = 336(9.81)\ln\frac{5560}{5496.6} = \mathbf{37.8\ m/s}$$

**(iii) (10)** Orbit 176 × 240 km, $a$ = 6586 km, $V_a$ = 7.7419 km/s.
- After the burn: $V = 7.7419-0.0378$ km/s, so $a'$ = 6523.0 km and $r_p' = 2a'-r_a$.
- **New perigee altitude ≈ 50 km**. This is inside the atmosphere, so re-entry is assured.

**(iv) (5)** New $e$ = 0.01456. At 122 km ($r$ = 6500 km):

$$\cos\theta = \frac1e\left[\frac{a(1-e^2)}{r}-1\right]\Rightarrow\theta = 283.2^\circ$$

It is inbound (descending from apogee at 180°), so the answer is 283°, not 77°.

*Check with Kepler's equation*: an impulsive burn at apogee reaches $\theta$ = 283° after about 25 min. The question's 36 min includes the finite 8.5 min burn and differs from the impulsive idealisation. The marks come from $\theta$ via the orbit equation.

**(v) (7)** Ground-track sketch:
- latitudes ±$i$ with $i\approx33.6^\circ$ (Apollo 9's inclination was about 33.6°; the entry point at 33°N, 90°W sits near the northern limit);
- nodes about 180° apart, drifting West by about 22° per orbit ($360\tau/\tau_E$ with $\tau$ = 88.5 min);
- the de-orbit burn at apogee about 103° of true anomaly before the 122 km entry interface (roughly over the Pacific).

## B2: Meteosat MSG (GEO, spinner, 3.2 m × 2.4 m)
**(i) (3)** Spin stabilisation gives:
- gyroscopic stiffness (a passive, stable, simple ACS);
- a **spin-scan** of the imager across the Earth every revolution (100 rpm);
- body-mounted cells and uniform thermal loading, because every side faces the Sun in turn.

**(ii) (12)** The cylinder is isothermal. The side has $\alpha_S$ = 0.91 and $\varepsilon$ = 0.79; the ends have $\varepsilon$ = 0.15; $P$ = 600 W; the Sun is in the orbit plane (equinox). $A^{proj} = DH$ = 7.68 m² for both Sun and Earth. $F = (1/6.611)^2$. Emission area: $\sum\varepsilon A = 0.79\pi DH+0.15(2\pi D^2/4)$.

| Position | Inputs | $T$ |
|---|---|---|
| Noon | Sun + albedo + IR + $P$ | **≈ 30 °C** |
| Terminator | Sun + IR + $P$ | **≈ 29 °C** |
| Eclipse | IR + $P$ | **≈ −122 °C** |

**Comment**: sunlit temperatures are benign, but in eclipse (up to 69 min) the body plunges. The batteries, propellant and instruments need **heaters and insulation**, and the power subsystem must size batteries for the eclipse heaters too. Real spacecraft have large thermal inertia, so the transient drop is much smaller than this equilibrium value.

**(iii) (15)**
- (a) Worst-case eclipse is 1.157 h at 300 W, so 347 W·h from 1200 W·h: **DoD ≈ 29 %**.
- (b) Body-mounted cells produce power only within ±45° of the Sun, i.e. a quarter of the circumference ($\pi DH/4$ = 6.03 m² acting at normal incidence):

$$P_{EOL} = 1365(6.03)(0.16)(0.9)(1-0.2)\approx\mathbf{950\ W}$$

- (c) Use the lecture relation $P_{EOL} = P_{load}+RV_A$, with $R = \text{DoD}\cdot C/t_s$, $C$ = 1200 W·h/28 V = 42.9 A·h and $t_s$ = 22.78 h, giving $R$ = 0.54 A.
  - Solving for $V_A$ with the full 950 W gives an unphysical kilovolt value. This shows the array has large margin over the 300 W load plus charging (0.54 A × ~33 V ≈ 18 W).
  - State the method, note the margin, and quote a practical $V_A\approx1.2V_B\approx33$ V.

> [!note] I could not reconstruct an unambiguous intended answer for B2(iii)(c). Show the relation and your reasoning.

## B3: Mars relay orbiter
**(i) (8)** The Earth derivation with Mars values:
- rotation shift $360\tau/\tau_M$;
- regression shift $360\tau/\tau_Y$;
- $n\tau(1/\tau_M-1/\tau_Y) = m$.

$$\tau = \frac{m}{n}\cdot\frac{\tau_M}{1-\tau_M/\tau_Y} = \frac{m}{n}\,88\,774.6\ \text{s}\approx\frac{m}{n}\tau_{sol}$$

> [!warning] The paper states 88 509.62 s
> $88\,509.62 = \tau_M(1-\tau_M/\tau_Y)$, the first-order expansion with the opposite sign. The two differ by 0.3 %. The exact form gives one sol, just as Earth gives 86 400 s. Show your derivation, note the difference, and **use the paper's value** for the later parts as instructed.

**(ii) (12)** Altitudes 270–310 km give $\tau$ = 6723–6833 s, i.e. $n/m$ = 12.95–13.17 orbits per sol.
- The rover is on the equator and talks only at local noon, so choose a **noon ascending node**: each orbit crosses the equator at noon exactly once.
- Antenna beam 120°, i.e. a nadir half-angle of 60°. At $h\approx300$ km the ground footprint half-angle is $\sin^{-1}[(a/R_M)\sin60^\circ]-60^\circ$ = 10.6°, about **±620 km**.
- With $(n,m) = (13,1)$ the ground track repeats **every sol**. Phasing the orbit so the noon pass is over the rover gives an uplink **every sol** (≤ 3 ✔).
- Other coprime combinations with $m\le3$ fall outside 270–310 km: (26,2) and (39,3) are not coprime.

**$(n,m) = (13, 1)$.**

**(iii) (3)** $\tau$ = 88 509.62/13 = 6808.4 s, $a$ = 3691.1 km, **$h$ = 301.1 km**.
- SSO rate: $\dot\Omega = 360^\circ/\tau_Y$ = 6.065 × 10⁻⁶ °/s.
- $\cos i = \dot\Omega/[-1.7617\times10^{-4}(R_M/a)^{3.5}]$, so **$i$ = 92.66°**.

**(iv) (7)** $\rho$ = 1.916 × 10⁻¹¹, $S$ = 8 m², $C_D$ = 2.2, $M$ = 1600 kg, $V$ = 3.406 km/s.
- $\delta a$ = −18.0 m/orbit; $\delta\tau$ = −0.0499 s/orbit.
- $\delta\lambda = 2E_0/R_M$ = 5.90 × 10⁻³ rad; $\Delta t_0 = \delta\lambda/\omega_M$ = 83.2 s.
- $k = \sqrt{2\Delta t_0/|\delta\tau|}$ = 57.7, so **57**. Cycle 2k = 114 orbits ≈ **8.7 sols**.
- **Height lost ≈ 2.06 km per cycle.**

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Astronautics Hub]]
