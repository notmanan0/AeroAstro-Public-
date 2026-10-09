---
title: "SESA2024 2017-18 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Examination 2017-18 (closed book, 120 min; Section A all, Section B 2 of 3)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201718-01-SESA2024W1.pdf"]
---

# SESA2024 2017-18 Exam Solutions

> [!abstract] Paper
> - Q1: eight short questions.
> - Q2: Hohmann derivation and an Earth → Saturn transfer.
> - Q3: noise sources, dish gains, the Voyager downlink.
> - Q4: SSO repeat orbit, FOV, data rate, drag.
>
> Numbers verified in Python; not the official scheme.

## Section A (Q1)
**(i) Particle radiation against altitude in the equatorial plane (4)**:
- Below about 1000 km it is low, because the atmosphere absorbs particles.
- The **inner Van Allen belt** (peaking around 3000–5000 km) is dominated by energetic **protons**.
- A slot region follows, at about 2–3 $R_E$.
- The **outer belt** (peaking around 15 000–25 000 km) is dominated by **electrons**.
- At GEO (the outer edge of the outer belt) the flux is lower, but there are energetic electrons, charging during substorms, and solar particle events.

**(ii) Rocket equation (3)**: $\Delta V = V_{ex}\ln(M_0/M_b)$.
- ΔV depends only on the exhaust speed and the **mass ratio**, not on the burn rate or thrust.
- The mass ratio grows **exponentially** with $\Delta V/V_{ex}$. So a high $I_{sp}$ is crucial, and a single stage struggles to reach orbit (hence staging).

**(iii) Internal torquers (4)**: reaction wheels, momentum wheels and CMGs. They change attitude by **exchanging momentum** with the body, with total **H** conserved. Uses:
- fine pointing and slewing of 3-axis spacecraft (reaction wheels);
- momentum bias for gyroscopic stiffness (a momentum wheel);
- agile large slews (CMGs).

They need an external torquer to desaturate ([[Attitude Sensors and Torquers]]).

**(iv) Pure spinner consequences (3)** ([[Spacecraft Stabilisation Types]]):
- **power**: body-mounted cells, only about 1/π of which are illuminated, so a larger, heavier surface is needed;
- **payload and comms**: the payload spins, so instruments see the target only part of the time (scanning) and antennas need despinning or omnidirectional patterns;
- **mass properties**: the spin axis must be the maximum-inertia axis (energy dissipation), which constrains the shape.

Also: uniform thermal loading, and no stored-momentum hardware.

**(v) Primary vs secondary propulsion (2)**:
- **Primary**: large ΔV orbit changes (apogee raising, orbit insertion, interplanetary).
- **Secondary**: small-impulse tasks, such as attitude control, momentum dumping, station-keeping and fine orbit trim.

**(vi) Albedo (2)**: the fraction of incident sunlight the Earth reflects, about **0.3–0.34** on average. It varies with cloud cover, snow and ice (high), ocean (low), latitude and season. The input to a satellite falls with the solar angle away from the subsolar point ($\cos\phi$) and is zero on the night side.

**(vii) Push-broom (3)**: see [[Swath Width and Push-Broom Imaging]]. A linear CCD across-track, with the spacecraft's motion sweeping along-track.
- **Key advantage**: **no moving scan mirror**, with a long dwell time per pixel (the whole line time), so a better SNR and geometric fidelity than a whisk-broom.

**(viii) SSO (4)**: the orbit plane precesses eastward at 0.9856°/day, matching the Sun's apparent motion, so the nodes keep a constant LST.
- It is achieved by using **$J_2$** (Earth's oblateness), which drives $\dot\Omega\propto-a^{-7/2}\cos i$.
- A retrograde inclination (about 98° in LEO) gives the right positive rate ([[Nodal Regression (J2)]]).

## Q2: Hohmann and Saturn
**(i) (6)**: the minimum-energy two-impulse transfer between coplanar circular orbits.
- **ΔV₁** is tangential at $r_1$, entering an ellipse with $r_p = r_1$ and $r_a = r_2$.
- The coast lasts half an orbit, $\pi\sqrt{a_T^3/\mu}$.
- **ΔV₂** is tangential at $r_2$, circularising.

Sketch: two concentric circles, the ellipse between them, and burn arrows at the apses ([[Hohmann Transfer]]).

**(ii) (8)**:
- $V_{Tp}^2 = \mu(2/r_1-2/(r_1+r_2)) = V_1^2\cdot\dfrac{2r_2}{r_1+r_2} = V_1^2\dfrac{2}{1+x}$, with $x = r_1/r_2$.
- So $\Delta V_1 = V_1\left(\sqrt{\dfrac{2}{1+x}}-1\right)$.

**(iii) Earth → Saturn (9)**: $\mu_S$ = 1.3 × 10¹¹, $r_1$ = 1.5 × 10⁸ km, $x$ = 1/9.5.
- $V_1 = \sqrt{\mu_S/r_1}$ = 29.44 km/s.
- **ΔV₁ = 10.16 km/s**.
- **ΔV₂** $= V_1\sqrt x\,(1-\sqrt{2x/(1+x)})$ = **5.38 km/s**.
- Total 15.55 km/s.
- $a_T$ = 7.875 × 10⁸ km, so $t = \pi\sqrt{a_T^3/\mu_S}$ = 2229 days = **6.1 years**.

**(iv) Mass ratio (3)**: $M_b/M_0 = e^{-5383/(310\times9.81)}$ = **0.170**, i.e. 83 % of the arrival mass is propellant.

**(v) Hohmann for interplanetary missions (4)**:
- **Advantages**: minimum ΔV for two impulses; simple and predictable.
- **Disadvantages**:
  - long flight times (6 years to Saturn), with radiation, reliability and cost over the long cruise;
  - launch windows only at the right planetary phasing (synodic period);
  - it ignores escape from and capture into the planets' gravity wells (patched conics are needed);
  - gravity assists (Voyager, Cassini) can greatly reduce ΔV and time.

## Q3: Communications
**(i) Noise sources (5)** ([[Link Budget Equation]]):
- **thermal noise** in the receiver electronics (LNA, feed losses), $N = kTB$;
- **sky/antenna noise**: cosmic background, the Sun, the Moon and galactic noise in the beam;
- **atmospheric** absorption and re-emission (rain, oxygen, water vapour);
- the warm **Earth** in the beam (for an uplink receiver on the satellite);
- **interference** from other transmitters;
- intermodulation and quantisation noise.

**(ii) Dish gains at 8.5 GHz (13)**: λ = 0.0353 m, η = 0.5.

| $D$ | $G$ (dB) | $\theta_{3dB}$ |
|---|---|---|
| 2 m | **42.0** | 1.27° |
| 3 m | **45.5** | 0.85° |
| 4 m | **48.0** | 0.64° |

**Trade-off**: every extra 1 dB of $G_T$ adds 1 dB directly to $C/N_0$ (and so to the data rate), or allows 1 dB less $P_T$.
- Going 2 → 4 m gives +6 dB, i.e. **4× the data rate or ¼ of the transmitter power**.
- But the 4 m dish needs a **deployment mechanism** (risk, mass), and its narrower beam demands tighter pointing.
- The 3 m dish is a sensible compromise if it fits the fairing without deployment.

**(iii) Voyager at Saturn (12)**:
- ρ = 9.5 AU = 1.425 × 10¹² m.
- $L_{FS} = 20\log(4\pi\rho/\lambda)$ = 294.11 dB.
- $G_R$ = 72.88 dB, so $G_R/T_R$ = 72.88 − 13.98 = 58.90 dB/K.

$$\frac{C}{N_0} = 61.2+58.90-294.11-3+228.60 = 51.60\ \text{dB-Hz}$$

- $10\log R_b = 51.60-10$, so $R_b$ = 14.4 kbps.
- Time = 5 × 10⁸/14 441 = 34 624 s = **9.6 h**.

## Q4: SSO (8000 × 10 m, 31-day coverage)
**(i) (3)** Swath = 8000 × 10 m = **80 km**.

**(ii) (3)** $n_{min} = 2\pi R_E/d$ = 500.9, so **$n$ = 501**. It is coprime with 31 (31 is prime) ✔.

**(iii) (8)**:
- $\tau = (31/501)86400$ = 5346.1 s, $a$ = 6608.2 km, **$h$ = 230.2 km**.
- **$i$ = 96.43°**.
- This is very low. A narrow swath plus a 31-day coverage requirement forces about 16.2 orbits per day. Any larger coprime $n$ would be lower still, so drag dominates the design.

**(iv) FOV (3)** $2\tan^{-1}(40/230.2)$ = **19.7°**.

**(v) Data rate (7)**:
- $V$ = 7.767 km/s, $V_g = VR_E/a$ = 7.496 km/s, line time 10/7496 = 1.334 ms.
- $R_b$ = 8000 × 8/1.334 ms = **48.0 Mbps**.

**(vi) Drag (6)**: ρ = 4.31 × 10⁻¹¹, $S$ = 0.5 m², $C_D$ = 1.8, $m$ = 150 kg.

$$\delta a = -2\pi\rho\frac{SC_D}{m}a^2 = \mathbf{-71.0\ m/orbit},\qquad\delta\tau = \frac{3\pi}{V}\delta a = \mathbf{-0.086\ s/orbit}$$

That is about 1.1 km of height lost per day, so frequent orbit boosts are needed ([[Orbit Control Cycle]]).

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
