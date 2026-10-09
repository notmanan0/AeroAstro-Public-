---
title: "SESA2024 2015-16 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Examination 2015-16 (closed book, 120 min; Section A all, Section B 2 of 3)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201516-01-SESA2024W1.pdf"]
---

# SESA2024 2015-16 Exam Solutions

> [!abstract] Paper
> - Q1: seven short questions.
> - Q2: Kepler's laws, orbit selection, a Hohmann derivation, 220 km → GEO.
> - Q3: link-budget derivation and a Phobos orbiter downlink.
> - Q4: SSO repeat orbit and the orbit-control cycle.
>
> Numbers verified in Python; not the official scheme.

## Section A (Q1)
**(i) Space environment (6)**:
- **Vacuum**: outgassing, cold welding, no convection.
- **Solar EM radiation**: about 1370 W/m² at 1 AU; UV degrades materials.
- **Thermal extremes**: Sun against a 3 K sky, eclipses.
- **Particle radiation**: solar wind, solar particle events, galactic cosmic rays, trapped belts. Effects are dose, SEUs and charging.
- **Neutral atmosphere** (LEO): drag, and atomic oxygen erosion.
- **Plasma**: spacecraft charging.
- **Micrometeoroids and debris**.
- **Magnetic and gravity fields**: disturbance torques.
- **Microgravity**.

**(ii) ACS purpose (3)** ([[SESA2024 06 - Attitude Control]]):
- **stabilise** the spacecraft against disturbance torques;
- **point** payloads, antennas, arrays and thrusters to the required accuracy;
- **slew or re-orient** between targets and for manoeuvres.

It requires determining the attitude (sensors) and controlling it (torquers).

**(iii) Chemical propulsion (3)**: **cold gas**, **liquid** (mono- and bipropellant), **solid**, and hybrid ([[Chemical Propulsion Systems]]).

**(iv) Battery cycle life (1)**: **depth of discharge**. A deeper DoD gives far fewer cycles ([[Battery Sizing]]).

**(v) Thermal balance (5)**:
- **Inputs**: direct solar, Earth albedo (reflected solar), Earth IR, internal dissipation $P$.
- **Output**: IR emitted to space, $\varepsilon\sigma T^4A_{surf}$ ([[Spacecraft Thermal Balance Equation]]).

**(vi) Sun-synchronous (4)**:
- **Condition**: nodal regression $\dot\Omega$ = +0.9856°/day, matching the Sun's apparent motion. From $J_2$, this needs $i\approx98^\circ$ in LEO.
- **Advantages**:
  - the same **LST** at every pass, so consistent illumination and shadows, and images comparable over time;
  - predictable power and thermal conditions.
- **European preference**: about a **10:30 descending node**. The Sun is high enough but it is before the afternoon cloud build-up, and it gives continuity with SPOT/ERS/Envisat data.

**(vii) ΔV budget (3)**:
1. **orbit acquisition**: correcting launcher injection errors and raising to the operational orbit;
2. **orbit maintenance**: drag make-up to hold the repeat ground track, plus inclination and LST trim;
3. **end-of-life disposal**: lowering for re-entry within 25 years (now 5).

## Q2
**(i) Kepler (6)** ([[Kepler's Laws]]):
1. Orbits are **ellipses** with the central body at one focus.
2. The radius vector sweeps **equal areas in equal times**, i.e. $h = r^2\dot\theta$ is constant.
3. $\tau^2\propto a^3$, i.e. $\tau = 2\pi\sqrt{a^3/\mu}$.

**(ii) Orbit selection (4)**:
- The payload's needs come first: coverage, resolution, revisit, illumination, communications visibility.
- They are traded against launch cost and ΔV, radiation, eclipse, drag and lifetime.
- **Example**: a global imager needs a near-polar Sun-synchronous LEO, while a TV broadcaster needs GEO (a fixed dish and one satellite per region).

**(iii) Hohmann derivation (10)**:
- Circular speed $V_1 = \sqrt{\mu/r_1}$.
- Transfer ellipse $a_T = (r_1+r_2)/2$. The energy equation at perigee gives

$$V_{Tp}^2 = \mu\left(\frac2{r_1}-\frac2{r_1+r_2}\right) = \frac{\mu}{r_1}\frac{2r_2}{r_1+r_2}$$

$$\Delta V_1 = V_{Tp}-V_1 = \sqrt{\frac{\mu}{r_1}}\left(\sqrt{\frac{2r_2}{r_1+r_2}}-1\right)$$

- Similarly at apogee, $V_{Ta}^2 = \dfrac{\mu}{r_2}\dfrac{2r_1}{r_1+r_2}$, so

$$\Delta V_2 = \sqrt{\frac{\mu}{r_2}}\left(1-\sqrt{\frac{2r_1}{r_1+r_2}}\right)$$

**(iii, second) 220 km → GEO (6)**: $r_1$ = 6598 km and $r_2 = 6.611R_E$ = 42 165 km.
- **ΔV₁ = 2.449 km/s**.
- **ΔV₂ = 1.475 km/s**.
- **Total 3.924 km/s**.
- $t = \pi\sqrt{a_T^3/\mu}$ = **5.26 h**.

**(iv) Fuel fraction (4)**: $M_p/M_0 = 1-e^{-3924/(325\times9.81)}$ = **0.708**.

## Q3: Communications
**(i) Link budget (12)** ([[Link Budget Equation]]):
- The flux at range ρ from an antenna of gain $G_T$ is $P_TG_T/4\pi\rho^2$.
- A receiving dish with effective area $A_e = G_R\lambda^2/4\pi$ collects

$$C = \frac{P_TG_TG_R}{L_A}\left(\frac{\lambda}{4\pi\rho}\right)^2$$

- The noise density is $N_0 = kT_R$. Dividing and taking 10 log:

$$\frac{C}{N_0} = 10\log P_TG_T+10\log\frac{G_R}{T_R}-20\log\frac{4\pi\rho}{\lambda}-L_A-10\log k$$

- **EIRP = $P_TG_T$**: the power an isotropic radiator would need to produce the same flux in the boresight direction. It is everything the spacecraft contributes. See [[EIRP and G-T]].

**(ii) Phobos downlink (11)**:
- 2 h × 280 kbps downloaded over 4 h gives **$R_b$ = 140 kbps**. $\lambda$ = 0.04 m.
- $C/N_0 = E_b/N_0+10\log R_b$ = 10 + 51.46 = 61.46 dB-Hz.
- $G_R = 10\log[0.5(\pi\cdot70/0.04)^2]$ = 71.79 dB, so $G_R/T_R$ = 71.79 − 6.02 = 65.77 dB/K.
- Free-space loss $20\log(4\pi\times4\times10^{11}/0.04)$ = 281.98 dB.

$$EIRP = 61.46-65.77+281.98+5+(-228.60) = \mathbf{54.07\ dBW}\ \checkmark$$

**(iii) (3)** $EIRP = P_T\eta(\pi D/\lambda)^2$, so

$$P_TD^2 = \frac{10^{5.4}\lambda^2}{\eta\pi^2}\approx\mathbf{81\ W\,m^2}$$

(82.8 using 54.07 dBW exactly.) For example, a 3 m dish needs 9 W, and a 2 m dish 20 W.

**(iv) Power–gain trade-off (4)**:
- More transmitter power costs array area, battery, mass and heat.
- A bigger dish costs mass, stowage and deployment risk, and its narrow beam (about 1° for 3 m at 7.5 GHz) needs precise pointing of the whole spacecraft.
- Here the spacecraft must slew between the imager and Earth anyway, so the ACS pointing accuracy becomes the limit.

## Q4: SSO repeat orbit and control (8000 × 10 m, 33 days)
**(i)(a) (3)**:
- Swath = 8000 × 10 m = **80 km**.
- $n_{min} = 2\pi R_E/d$ = 500.9, so 501. But $501 = 3\times167$ shares a factor with 33, so the track would repeat after 11 days. Hence **$n$ = 502**.

**(i)(b) (7)**:
- $\tau = (33/502)86400$ = 5679.7 s, $a$ = 6880.3 km, **$h$ = 502.3 km**.
- With the data's $J_2$ form, $\dot\Omega = -\tfrac32J_2R_E^2\sqrt\mu\,a^{-7/2}\cos i$ = 1.991 × 10⁻⁷ rad/s, which gives **$i$ = 97.41°** (identical to the empirical form).

**(ii)(a) Drag (10)**: $\rho$ = 5.8337 × 10⁻¹³, $S$ = 1 m², $C_D$ = 2.2, $m$ = 150 kg, $V$ = 7.611 km/s.

$$\delta a = -2\pi\rho\frac{SC_D}{m}a^2 = \mathbf{-2.54\ m/orbit},\qquad \delta\tau = \frac{3\pi}{V}\delta a = \mathbf{-3.15\ ms/orbit}$$

**(ii)(b) Control cycle (10)** ([[Orbit Control Cycle]]):
- $\delta\lambda = 2E_0/R_E$ = 4.70 × 10⁻⁴ rad = 0.02695°, so $\Delta t_0 = \delta\lambda/\omega_E$ = 6.45 s.
- $k = \sqrt{2\Delta t_0/|\delta\tau|}$ = 63.98, so **$k$ = 63** (round down to stay inside the tolerance; 64 is borderline).
- Manoeuvres every $2k$ = 126 orbits = **8.3 days**.
- Height lost per cycle $2k|\delta a|$ ≈ 320 m, restored by a small Hohmann boost.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
