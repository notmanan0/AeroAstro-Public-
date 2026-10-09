---
title: "SESA2024 2024-25 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Final Assessment 2024/25 (online open-book)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-202425-01-SESA2024W1.pdf"]
---

# SESA2024 2024-25 Exam Solutions

> [!abstract] Paper
> - Section A: 8 short questions (25 marks).
> - Section B: B1 asteroid deflection (heliocentric orbits); B2 GPS link budget and power; B3 CO₂-monitoring SSO (repeat track, drag, Hohmann, thermal).
>
> These are my worked solutions, **not an official mark scheme**. All numbers were verified in Python. Constants: $R_E$ = 6378 km, $\mu$ = 398 600 km³/s², $g_0$ = 9.81 m/s².

## Section A
**A1 (2)**: before the TLRs you need (1) the **mission objectives** (customer) and (2) the **payload definition** (specialist working group). See [[Systems Engineering Design Phases]].

**A2 (6)**:
- $V_{ex} = g_0I_{sp} = 9.81\times1200$ = 11 772 m/s.
- An *optimised* EP system operates at the **peak** of the $M_p/M_0$ = 0.1 curve in Figure A2: $V_{ex}/V_c\approx0.65$ and $\Delta V/V_c\approx0.65$.
- So $V_c = 11\,772/0.65$ = 18 110 m/s, and **ΔV ≈ 0.65 × 18 110 ≈ 11.8 km/s**. (The exact peak, $x^* = 0.633$ with 0.651, also gives 11.8 km/s.)

See [[Electric Propulsion Sizing]].

**A3 (4)**: read from Figure A3 (noon on the spring equinox, so the Sun direction is ♈).
- The orbit is a near-circle just outside the Earth: $r\approx1.1R_E$, so **$a\approx7000$ km** and **$e\approx0$**.
- The satellite sits where the orbit crosses the equator on the Sun line, i.e. at a node on the ♈ direction. So **$\Omega\approx0^\circ$ if that node is ascending, or 180° if descending**. Use the drawn direction of travel.
- **$i$** is the angle between the orbit and the equator at that crossing.

> [!warning] I could not read the direction arrow or the tilt reliably from the scanned figure. Apply the method above to your copy. 10 % margin allowed.

**A4 (2)**: large **products of inertia** mean the body axes are not principal axes and the body is not balanced for spin, so it is **C, 3-axis stabilised**. (A spinner needs a diagonal $[\mathbf I]$ with a maximum-inertia spin axis. Principal moments here: 556, 1698, 2996 kg m².)

**A5 (3)**:

$$P_{EOL} = S A\eta\eta_p(1-D)\cos\theta = 1360(0.03)(0.2)(0.8)(0.95)\cos\theta = 6.20\cos\theta\ \text{W}$$

Need ≥ 4 W: $\cos\theta\ge0.645$, so **$\theta_{max} = 49.8^\circ$**.

**A6 (4)**: $\tau = (1/16)86400$ = 5400 s, so $a = [\mu(\tau/2\pi)^2]^{1/3}$ = 6652.6 km, **$h$ = 274.6 km**, and $i = \cos^{-1}[0.986/(-2.0647\times10^{14}a^{-3.5})]$ = **96.59°**.

**A7 (2)**: Sun-synchronous means the node is crossed at the same LST every orbit, so **10:00 am**.

**A8 (2)**: in eclipse with $P = 0$, only Earth IR is absorbed (with $\alpha_{IR} = \varepsilon$, by Kirchhoff):

$$q_E\varepsilon A_E^{proj}F = \varepsilon\sigma T^4A_{surf}\ \Rightarrow\ T = \left(\frac{q_EA_E^{proj}F}{\sigma A_{surf}}\right)^{1/4}$$

$\varepsilon$ cancels.

## B1: Asteroid deflection
Data: AU = 1.49598 × 10⁸ km, $\mu_S$ = 1.3271 × 10¹¹ km³/s². Earth perihelion 0.9833 AU and aphelion 1.0168 AU, so $a_E$ = 1.00005 AU.

**(i) (7)** Kepler 3 as a ratio: 6 asteroid orbits = 5 Earth orbits, so $\tau_A = \tfrac56\tau_E$ = 304.4 d, and

$$a_A = a_E(5/6)^{2/3} = 0.8856\ \text{AU}$$

The spacecraft (perihelion 0.9833 AU) meets the asteroid **at the asteroid's aphelion**, and the 2029 impact is at Earth's perihelion. So:
- **$r_a$ = 0.9833 AU** (1.471 × 10⁸ km);
- **$r_p = 2a_A-r_a$ = 0.7879 AU** (1.179 × 10⁸ km);
- $e$ = 0.110.

**(ii) (5)** Coplanar, both tangential at the same radius (0.9833 AU):
- $V_E = \sqrt{\mu_S(2/r-1/a_E)}$ = 30.287 km/s;
- $V_A = \sqrt{\mu_S(2/r-1/a_A)}$ = 28.331 km/s.

**Impact speed ≈ 1.96 km/s**. The Earth catches the asteroid from behind.

**(iii) (3)** A retrograde heliocentric orbit would require cancelling Earth's orbital velocity (about 30 km/s) and then adding about 30 km/s in the opposite direction: a launch ΔV of about 60 km/s, far beyond any launcher. (Gravity assists could help, but not enough in 2.5 years.)

**(iv) (3)**:
- (a) At the spacecraft's perihelion, $V_{sc}$ = 32.25 km/s is greater than $V_A$ = 28.33 km/s, and both are tangential. The spacecraft's velocity relative to the asteroid points **along the asteroid's direction of motion (prograde)**, about 3.9 km/s.
- (b) The Earth is faster, so the asteroid's velocity relative to the Earth points **backwards (retrograde) along Earth's track**, 1.96 km/s.

**(v) (12)** Perfectly inelastic collision ($m_A$ = 10⁹ kg, $m_{sc}$ = 10⁴ kg):

$$V' = \frac{m_AV_A+m_{sc}V_{sc}}{m_A+m_{sc}}\ \Rightarrow\ \Delta V_A = \frac{10^4(3.917)}{10^9}\ \text{km/s} = 3.92\times10^{-2}\ \text{m/s}$$

- The kick is prograde at aphelion, so $a$ rises: $1/a' = 2/r_a-V'^2/\mu_S$.
- New period vs old: **$\Delta\tau\approx+87$ s > 75 s, so the deflection succeeds** (marginally).
- Check with the linearised form $\Delta\tau/\tau = 3\Delta a/2a$ and $\Delta a = 2a^2V\Delta V/\mu$: consistent.

## B2: GPS navigation link
**(i) (14)**
- 12 h orbit: $a = [\mu(43200/2\pi)^2]^{1/3}$ = 26 610 km, so $\rho = h$ = 20 232 km.
- $\lambda = c/f$ = 0.1905 m.
- $C/N_0 = E_b/N_0+10\log R_b$ = 10 + 52.55 = **62.55 dB-Hz**.
- $L_{FS} = 20\log(4\pi\rho/\lambda)$ = **182.51 dB**.

$$EIRP = C/N_0-G/T+L_{FS}+L_A+10\log k = 62.55+21.7+182.51+0-228.60 = \mathbf{38.2\ dBW}\ (6.6\ \text{kW})$$

**Significance**: EIRP is the power an isotropic antenna at the satellite would need to radiate to produce the same flux at the user. It sums the transmitter's contribution to the link.

**(ii) (5)** The power–gain trade-off:
- EIRP = $P_TG_T$ with $G_T = \eta(\pi D/\lambda)^2$ and $\theta_{3dB} = 72\lambda/D$.
- A bigger dish gives more gain and less $P_T$ (less array, battery and thermal load), but more mass and volume, deployment risk, tighter pointing, and a narrower beam that may not cover the service area.
- A smaller dish is the reverse.

**(iii) (11)** Global coverage from $a$: $\sin\alpha = R_E/a$, so $\alpha$ = 13.87° and $\theta_{3dB} = 2\alpha$ = 27.74°.
- $D = 72(0.1905)/27.74$ = **0.49 m**.
- $G_T = 0.65(\pi\cdot0.49/0.1905)^2$ = **16.4 dB**.
- $P_T = 10^{(38.2-16.4)/10}$ = 151 W, so $P_{elec} = 151/0.5$ ≈ **303 W, i.e. ≈ 310 W** ✔. (The paper's 310 comes from rounding.)

## B3: CO₂ monitor in SSO (1:30 pm ascending node, 2-day revisit)
**(i) (4)** $\tau(700)$ = 5926 s. With $m$ = 2: $n = 2(86400)/5926$ = 29.16, so **$n$ = 29** (coprime with 2).
- $\tau = (2/29)86400$ = 5958.6 s, $a$ = 7103.8 km, so **$h$ = 725.8 km**. This is inside 700 ± 35 ✔.

**(ii) (2)** **$i$ = 98.30°**.

**(iii) (5)** Figure B3.2 at about 726 km, solar maximum (red): $\rho\approx1\times10^{-13}$ kg/m³.

$$\delta a = -2\pi\rho\frac{SC_D}{m}a^2 = -2\pi(10^{-13})\frac{2(2.2)}{31}(7.1038\times10^6)^2 = -4.50\ \text{m/orbit}$$

$$\delta\tau = \frac{3\pi\delta a}{V} = \frac{3\pi(-4.50)}{7491} = -5.66\times10^{-3}\ \text{s/orbit}$$

- Boost to $\tau_{nom}$ + 2.15 s, then let drag take it to $\tau_{nom}$ − 2.15 s: a total change of 4.3 s.
- **Cycle** = 4.3/5.66 × 10⁻³ ≈ **760 orbits ≈ 52 days**.
- **Altitude change over the cycle** = 760 × 4.50 m ≈ **3.4 km** (±1.71 km about nominal, from $\Delta a = \tfrac23(a/\tau)\Delta\tau$).

(With $\rho$ = 1.2 × 10⁻¹³: 633 orbits, 44 days. State your reading of the figure.)

**(iv) (8)** Hohmann between $r = a\mp1.709$ km:
- $\Delta V_1 = V_{Tp}-V_{low}$ and $\Delta V_2 = V_{high}-V_{Ta}$, each ≈ 0.90 m/s;
- **total ≈ 1.80 m/s per cycle**, consistent with $\approx V\Delta r/2a$.

**(v) (11)** Material selection. Cylinder $D$ = 1 m, $L$ = 2 m, axis to nadir, isothermal. $A_{surf} = \pi DL+2\pi D^2/4$ = 7.85 m². $F = (R_E/a)^2$ = 0.806.
- **Eclipse** (82 W heater; Earth IR on the nadir end, 0.785 m²):

$$T^4 = \frac{240\varepsilon(0.785)(0.806)+82}{\varepsilon\sigma(7.85)}$$

  Only **low-ε** finishes (ε = 0.03) reach ≥ 10 °C: **10.6 °C** for SiO-Al and for MLI. Black and white paint give −120 °C ✘.
- **Sunlit, noon** (Sun on the zenith end, 0.785 m²; albedo and IR on the nadir end):

| Finish | $T$ |
|---|---|
| SiO-Al ($\alpha_S$ = 0.9) | 277 °C ✘ |
| **MLI ($\alpha_S$ = 0.09)** | **38.6 °C ≈ 38 °C ✔** |

- **Choose MLI.** It is the only finish that satisfies both limits (to rounding).

> [!note] Caveat
> Away from noon the Sun strikes the cylinder side (2 m² projected), which gives MLI about 96 °C at the terminator. The question's single "sunlit" case evidently intends the noon attitude. A full design would need radiators or louvres.

See [[Spacecraft Thermal Balance Equation]].

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Astronautics Hub]]
