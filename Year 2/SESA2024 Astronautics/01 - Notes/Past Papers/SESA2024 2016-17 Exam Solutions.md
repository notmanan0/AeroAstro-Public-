---
title: "SESA2024 2016-17 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Examination 2016-17 (closed book, 120 min; Section A all, Section B 2 of 3)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201617-01-SESA2024W1.pdf"]
---

# SESA2024 2016-17 Exam Solutions

> [!abstract] Paper
> - Q1: eight short questions.
> - Q2: Ariane 5 → parking orbit → apogee raise.
> - Q3: blackbody, thermal balance, a GEO cube with radiators.
> - Q4: SSO repeat orbit, data rate, battery charging.
>
> Numbers verified in Python; not the official scheme.

## Section A (Q1)
**(i) Launch loads (3)**:
- **quasi-static acceleration** (steady thrust, up to about 4–6 g);
- **vibration**: sinusoidal (low-frequency, from POGO and engines) and random (structure-borne);
- **acoustic** noise (lift-off, transonic);
- **shock** at stage and fairing separation.

(Any three.)

**(ii) Environment at 250 km (6)**:
- A relatively dense **neutral atmosphere**: strong drag, so a short lifetime without propulsion.
- **Atomic oxygen** erosion of polymers and coatings.
- Solar UV and full solar flux; Earth IR and albedo.
- **Frequent eclipses** (about 36 % of each orbit), so thermal cycling.
- **Ionospheric plasma** (charging).
- Low trapped radiation (below the belts), except in the **SAA** if inclined.
- Micrometeoroids and debris.
- The geomagnetic field, which is useful for magnetorquers but also a disturbance.
- Gravity gradient.

**(iii) Why external torquers (2)**: environmental disturbance torques (gravity gradient, aerodynamic, solar pressure, magnetic) have **secular components** that keep adding angular momentum. Internal devices only store it, so wheels saturate. An external torque (thrusters or magnetorquers) is needed to **dump momentum** and to control total **H** ([[Reaction Wheels and Momentum Dumping]]).

**(iv) Four active stabilisation categories (4)** ([[Spacecraft Stabilisation Types]]):
1. **spin** stabilised (the whole body spins);
2. **dual spin** (a spinning rotor plus a despun platform);
3. **3-axis with momentum bias** (a momentum wheel);
4. **3-axis zero-bias** (reaction wheels or thrusters).

**(v) Radiation and solar cells (2)**: particle radiation (mainly protons and electrons) causes **displacement damage** in the crystal lattice, which cuts minority-carrier lifetime. $I_{sc}$, $V_{oc}$ and efficiency fall steadily. Cover glass limits it, and arrays are sized for **EOL** ($D_0$).

**(vi) Gain and diameter (1)**: $G = \eta(\pi D/\lambda)^2$, so **$G\propto D^2$**: doubling $D$ adds 6 dB.

**(vii) Remote sensing and SSO (3)**:
- Remote sensing is acquiring information about the Earth's surface or atmosphere from a distance, by measuring reflected or emitted EM radiation (visible, IR, microwave).
- SSO gives a **constant local solar time** at each latitude, so repeatable illumination, which makes images comparable across dates and passes.

**(viii) Orbit control strategy (4)**: see [[SESA2024 2013-14 Exam Solutions|2013/14 Q1(ix)]] and [[Orbit Control Cycle]].
1. Boost above nominal.
2. Drag decay moves the track across the $\pm E_0$ corridor along a parabola over $2k$ orbits.
3. Re-boost by $2k|\delta a|$ with a Hohmann transfer.

## Q2: Ariane 5 and the parking orbit
**(i) Gravity against drag losses (4)**:
- **Gravity loss** $\int g\sin\gamma\,dt$ is minimised by pitching over early (small γ) and burning quickly (high thrust).
- **Drag loss** $\int D/M\,dt$ is minimised by climbing steeply out of the dense atmosphere and flying slower low down.
- So the trajectory is a compromise: vertical rise, then a **gravity turn**. Large launchers (low $D/M$) favour early pitch-over. Losses are typically 1.5–2 km/s.

**(ii) ΔV (11)**: $M_0$ = 735 200 kg (structure + propellant for all stages + 20 100 kg payload).

| Stage | $M_0$ | $M_b$ | ΔV (km/s) |
|---|---|---|---|
| 1 | 735 200 | 245 200 | 3.184 |
| 2 | 223 700 | 53 700 | 5.494 |
| 3 | 39 700 | 24 700 | 2.017 |

**$\Delta V_{ideal}$ = 10.69 km/s**. After losses of 1.3 + 0.4 km/s: **ΔV = 8.99 km/s**.

**(iii) Energy equation (6)**:
- $m\ddot{\mathbf r} = -(\mu m/r^2)\hat{\mathbf r}$. Dot with $\dot{\mathbf r}$:

$$V\dot V = -\frac{\mu}{r^2}\dot r\ \Rightarrow\ \frac{d}{dt}\left(\frac{V^2}{2}-\frac{\mu}{r}\right) = 0$$

- So $V^2/2-\mu/r = \varepsilon$, a constant.

**(iv) Parking orbit (3)**:
- Burnout is at $h$ = 250 km ($r$ = 6628 km) with $V$ = 8.99 km/s, horizontal. This is **faster** than circular speed there (7.755 km/s), so the burnout point is the **perigee** of an ellipse:

$$\frac{8.99^2}{2}-\frac{\mu}{6628} = -\frac{\mu}{2a}\ \Rightarrow\ \mathbf{a = 10\,124\ km},\qquad e = 1-\frac{r_p}{a} = \mathbf{0.345}$$

- The apogee radius is 13 620 km (7242 km altitude).

**(v) Apogee raise to 25 000 km (6)**:
- New $a$ = (6628 + 25 000)/2 = 15 814 km.
- $V_p' = \sqrt{\mu(2/6628-1/15814)}$ = 9.746 km/s.
- **ΔV = 9.746 − 8.990 = 0.756 km/s**.
- Fuel: $M_p = M_0(1-e^{-0.756/2.8})$ = 0.237 $M_0$, so **about 4755 kg** for the 20 100 kg satellite.

> [!note] Alternative reading
> If you take the parking orbit as **circular** at 250 km ($a$ = 6628 km, $e$ = 0), ignoring the (ii) result, then ΔV = 2.00 km/s and the fuel fraction is 51 % (10 245 kg). The question gives $r_p = a(1-e)$ and asks for $e$, which suggests the elliptical reading intended above. State your assumption.

## Q3: Thermal
**(i) Blackbody (3)**: an ideal surface that **absorbs all incident radiation** at every wavelength ($\alpha = \varepsilon = 1$) and emits the maximum possible at its temperature: Planck's spectrum, total $\sigma T^4$, peak at $\lambda_{max} = 2898/T$ µm ([[Blackbody Radiation]]).

**(ii) Balance equation (10)**: see [[SESA2024 2013-14 Exam Solutions|2013/14 Q3(ii)]]: the terms, the assumptions, and $T\propto(\alpha_S/\varepsilon)^{1/4}$.

**(iii) GEO cube, one radiator (11)**:
- 1.5 m cube, face area $A$ = 2.25 m².
- One insulated face ($\alpha = \varepsilon$ = 0.1) always points at the Sun. The radiator ($\varepsilon$ = 0.8) faces the orbit normal, so it never sees the Sun or Earth.
- $\sum\varepsilon A = 5(0.1)(2.25)+0.8(2.25)$ = 2.925 m². $F$ = 0.02288.

| | Inputs (W) | $T$ |
|---|---|---|
| (a) Noon | Sun 308.3 + albedo 2.4 + IR 1.2 + $P$ 1200 | **35.8 °C** |
| (b) Terminator | Sun 308.3 + IR 1.2 + 1200 | **35.7 °C** |
| (c) Midnight (in eclipse at the equinox) | IR 1.2 + 1200 | **18.6 °C** |

At noon the Earth faces the anti-Sun face; at midnight it faces the Sun face. Either way it is insulated, so the Earth terms are tiny. **$P$ dominates**, so the temperature swing is only about 17 °C.

**(iv) Two radiators (6)**:
- $\sum\varepsilon A = 4(0.1)(2.25)+2(0.8)(2.25)$ = 4.5 m².
- Noon **4.3 °C**; midnight (eclipse) **−11.2 °C**.
- **One radiator is better**. Two radiators run the spacecraft too cold: hydrazine freezes at about 2 °C, and batteries prefer 0–20 °C. One radiator keeps it at 19–36 °C, within typical equipment limits (about −10 to 40 °C). Louvres or heaters would trim it.

## Q4: SSO (swath 88 km, 38-day coverage, 8-year life)
**(i) $h$ and $i$ (10)**:
- $n_{min} = 2\pi R_E/88$ = 455.4. The smallest $n\ge456$ coprime with 38 is 457, but that gives $h$ = 1669 km. It is outside the payload's 700–900 km band (the resolution would suffer).
- For 700–900 km, $n/m$ ≈ 14.2–14.5, so $n$ ≈ 535–553 (odd, so coprime with 38 = 2 × 19).

| $(n, 38)$ | $h$ (km) | $i$ | Coverage |
|---|---|---|---|
| 535 | 866.7 | 98.89° | 117 % |
| 541 | 813.1 | 98.66° | 119 % |
| **543** | **795.4** | **98.58°** | **119 %** |
| 549 | 743.0 | 98.36° | 121 % |

A good answer: **(543, 38)**, with $h$ = 795 km and $i$ = 98.58°. Any coprime choice in the band, with its $h$ and $i$ computed, is acceptable.

**(ii) Pixel and data rate (10)**: at $h$ = 900 km (as given).
- 2000 elements paired gives 1000 pixels, so the **pixel is 88 m**.
- $V$ = 7.400 km/s, $V_g$ = 6.485 km/s, line time 88/6485 = 13.57 ms.
- $R_b$ = 1000 × 16 × 40/0.01357 = **47.2 Mbps**.

**(iii) Battery charging (10)**:
- At 900 km: $\tau$ = 103.0 min, $t_e$ = 35.0 min, $t_s$ = 68.0 min.
- $C = P_et_e/(\text{DoD}\,V_B) = 500(0.5836)/(0.2\times25)$ = 58.4 A·h.
- Charge current $R = \text{DoD}\,C/t_s$ = 0.2(58.4)/1.133 = 10.3 A.
- Charging power from the 36 V array: $RV_A$ = **371 W**.
- The array must deliver about 1100 + 371 ≈ **1470 W** in daylight.
- (The ideal minimum, with no voltage mismatch, is $P_et_e/t_s$ = 258 W. The $V_A/V_B$ ratio accounts for the charge regulation.)

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
