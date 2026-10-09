---
title: "SESA2024 Astronautics Hub"
module: "SESA2024 Astronautics"
type: hub
tags: [sesa2024, hub, moc]
status: complete
---

# SESA2024 Astronautics Hub

> [!abstract] Module at a glance
> **Design a spacecraft from its payload outward.**
> 1. Systems engineering turns the mission objectives into design requirements (Ch 1, 4).
> 2. Mission analysis finds the orbit and the ΔV (Ch 5): Kepler, vis-viva, Hohmann.
> 3. Each subsystem is sized to serve the payload: attitude (Ch 6), propulsion (Ch 7), power (Ch 8), comms (Ch 9), thermal (Ch 10).
> 4. The Ch 11 **remote-sensing case study** ties it all together: the payload selects a Sun- and Earth-synchronous orbit, and that orbit's eclipse, drag and data rate size everything else.
>
> One thread runs through the module: **the payload selects the orbit, and the orbit sizes the spacecraft.**
>
> Quick reference: [[SESA2024 Formula Sheet]] · Exam guide: [[SESA2024 Past Paper Trend Analysis]]

## Topic map

### Systems (Dr C. Ryan, Dr H. Sykulska-Lawrence)
1. [[SESA2024 01 - Systems Engineering and Spacecraft Design]]: subsystems; objectives → payload → TLRs → DRs; ECSS phases 0–F; trade-offs; payload impact (Ch 4)

### Mission analysis: Chapter 5 (Dr C. Ryan, after Prof H. Lewis)
2. [[SESA2024 02 - Kepler's Laws and the Orbit Equation]]: polar ellipse, $a_r$ and $a_\theta$, $h = r^2\dot\theta$, $u''+u = \mu/h^2$, $\tau = 2\pi\sqrt{a^3/\mu}$
3. [[SESA2024 03 - Orbital Elements and Conic Sections]]: $a, e, i, \Omega, \omega, \theta$; orbit categories; conics
4. [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]: $\varepsilon = -\mu/2a$; the 200 × 40 000 km example
5. [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]: impulsive burns; RemoveDebris; LEO → GEO 3.933 km/s

### Spacecraft subsystems: Chapters 6–10 (Dr H. Sykulska-Lawrence)
6. [[SESA2024 06 - Attitude Control]]: $\mathbf H = [\mathbf I]\boldsymbol\omega$; momentum bias; 4 stabilisation types; torquers, sensors, dumping
7. [[SESA2024 07 - Spacecraft Propulsion]]: thrust, $I_{sp}$, rocket equation; chemical systems; EP optimisation (Pluto)
8. [[SESA2024 08 - Electrical Power Subsystem]]: sources; solar cells; batteries; eclipse → $C$ → array area
9. [[SESA2024 09 - Communications]]: dB, bands, PSK; $G$ and $\theta_{3dB}$; link budget; EIRP and $G/T$; BER
10. [[SESA2024 10 - Thermal Control]]: blackbody, $\alpha$ and $\varepsilon$; thermal balance; $\alpha_S/\varepsilon$; passive vs active

### Remote-sensing case study: Chapter 11 (Dr C. Ryan)
11. [[SESA2024 11 - Payload and Orbit Selection]]: first pass (near-polar, circular, 700–900 km); push-broom; illumination and view needs
12. [[SESA2024 12 - Sun- and Earth-Synchronous Orbits]]: $J_2$ regression, $i\approx98^\circ$; $\tau = (m/n)86400$
13. [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]]: the $n, m$ iteration, (98,7) example; LST → RAAN → eclipse
14. [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]: δa, δτ, $k$, Hohmann make-up; data rate and compression

### Sustainability and NewSpace (Dr N. Vaidya)
15. [[SESA2024 15 - Space Sustainability, Debris and NewSpace]]: SDGs, debris, IADC/UN/FCC rules, disposal, ADR, SBSP, NewSpace trade-offs

## Concept notes
| Orbits | Subsystems (6–7) | Subsystems (8–10) | Remote sensing |
|---|---|---|---|
| [[Kepler's Laws]] | [[Inertia Matrix]] | [[Spacecraft Power Sources]] | [[Sun-Synchronous Orbit]] |
| [[Orbit Equation and Conic Sections]] | [[Momentum Bias and Gyroscopic Rigidity]] | [[Solar Cells and Arrays]] | [[Nodal Regression (J2)]] |
| [[Orbital Angular Momentum]] | [[Spacecraft Stabilisation Types]] | [[Battery Sizing]] | [[Repeat Ground Track]] |
| [[Vis-Viva Equation]] | [[Reaction Wheels and Momentum Dumping]] | [[Eclipse Duration]] | [[Local Solar Time and RAAN]] |
| [[Hohmann Transfer]] | [[Attitude Sensors and Torquers]] | [[Decibels]] | [[Swath Width and Push-Broom Imaging]] |
| [[Keplerian Orbital Elements]] | [[Chemical Propulsion Systems]] | [[Antenna Gain and Beamwidth]] | [[Orbit Control Cycle]] |
| [[Systems Engineering Design Phases]] | [[Electric Propulsion Sizing]] | [[Link Budget Equation]] | [[Payload Data Rate]] |
| [[Spacecraft Subsystems]] | [[Tsiolkovsky Rocket Equation]] (SESA2023) | [[EIRP and G-T]] | [[Space Debris Mitigation]] |
| | [[Rocket Performance Parameters]] (SESA2023) | [[Bit Error Rate and Eb-N0]] | |
| | [[Thrust Equation]] (SESA2023) | [[Spacecraft Thermal Balance Equation]] | |
| | | [[Absorptance and Emittance]] · [[Blackbody Radiation]] · [[Passive vs Active Thermal Control]] | |

## Workbook solutions (Problem Sheet Workbook 2025-26)
| Chapter | Note | Highlights |
|---|---|---|
| 5 Mission analysis | [[SESA2024 Workbook Ch5 - Mission Analysis Solutions]] | $\varepsilon = -\mu/2a$ proof; missile vs satellite; 300 km → GEO 600 kg; comet intercept 4.55 km/s, 340 d |
| 6 Attitude control | [[SESA2024 Workbook Ch6 - Attitude Control Solutions]] | 12 Q&As; GEO telescope ACS design |
| 7 Propulsion | [[SESA2024 Workbook Ch7 - Propulsion Solutions]] | EP power at 50 mN; **Pluto EP orbiter** |
| 8 Power | [[SESA2024 Workbook Ch8 - Power Solutions]] | GEO 8 kW: 841 A·h, 771 kg, 84 m² |
| 9 Communications | [[SESA2024 Workbook Ch9 - Communications Solutions]] | band table; GEO global beam 0.83 m; **Pluto link** 3483 bps |
| 10 Thermal | [[SESA2024 Workbook Ch10 - Thermal Control Solutions]] | array at 18 000 km: 49 / 46 / 44 °C (= exam 2022/23 B2) |
| 11B Case study | [[SESA2024 Workbook Ch11B - Remote Sensing Case Study Solutions]] | the Excel iteration transcribed: civil (89,6) and military (1999,125); ⚠ bytes/bits slip in the handwritten version |

> [!note] There are no workbook questions for Chapters 1 and 4 (the lectures carry them). The contents page lists an "11A worksheet": that is the civilian/military mission pair on p. 57, solved in the 11B note. The Blackboard **Excel visualisation tools** (orbit, ΔV, Hohmann, ground track) are not in the vault. The workbook's Excel-based 11B solutions are transcribed in full in the 11B note.

## Past papers
| Year | Solutions | Section B themes |
|---|---|---|
| 2024/25 | [[SESA2024 2024-25 Exam Solutions]] | asteroid deflection · GPS link · CO₂ SSO + thermal |
| 2023/24 | [[SESA2024 2023-24 Exam Solutions]] | Starship IFT-2 · C-band + GEO battery · Jupiter SSO |
| 2022/23 | [[SESA2024 2022-23 Exam Solutions]] | OMOTENASHI · array thermal + L-band · Starlink |
| 2021/22 | [[SESA2024 2021-22 Exam Solutions]] | Apollo 9 · Meteosat · Mars relay SSO |
| 2020/21 | [[SESA2024 2020-21 Exam Solutions]] | 24-h single reference mission: SSO (143,10) → drag, ACS, power, comms, thermal |
| 2019/20 | [[SESA2024 2019-20 Exam Solutions]] | GEO radius + corridor · SSO array thermal/power · drag sail + hyperspectral |
| 2018/19 | [[SESA2024 2018-19 Exam Solutions]] | Kepler 2 + GTO kick · 900 km power · SSO FOV 28° |
| 2017/18 | [[SESA2024 2017-18 Exam Solutions]] | Hohmann to Saturn · dish trade + Voyager · SSO 31-day + drag |
| 2016/17 | [[SESA2024 2016-17 Exam Solutions]] | Ariane 5 → apogee raise · GEO cube radiators · SSO 38-day + charging |
| 2015/16 | [[SESA2024 2015-16 Exam Solutions]] | Kepler + GEO Hohmann · Phobos link · SSO 33-day + control cycle |
| 2014/15 | [[SESA2024 2014-15 Exam Solutions]] | launcher ΔV + Ariane 5 · ISS power · SSO 30-day + launch azimuth |
| 2013/14 | [[SESA2024 2013-14 Exam Solutions]] | orbits + debris intercept · GEO spinner thermal · hyperspectral SSO |
| All legacy | [[SESA2024 Legacy Papers 2013-2021 Key Answers]] | quick-check index of headline numbers |

> [!tip] Most likely exam content (from 12 papers)
> 1. **SSO inclination + $(n,m)$ + $h$** (every year) → orbit-control cycle → Hohmann ΔV → propellant → data rate.
> 2. **Vis-viva storyline**: $a, e$ from $(r, V)$; $\theta$ from $r$; ΔV between orbits; Kepler-3 timing; rocket-equation masses.
> 3. **Link budget**: EIRP; global-coverage dish; transponder power; power–gain trade-off.
> 4. **Thermal balance**: noon / terminator / eclipse; choose a finish for a temperature window.
> 5. **Battery and array sizing** from the worst-case eclipse.
> 6. Section A staples: LST at the nodes; eclipse $T$ independent of $\varepsilon$; $[\mathbf I]$ → 3-axis; spinner vs 3-axis; fragment motion; systems-engineering steps; EP curve.

## Figures
All generated in Python (300 dpi) and stored in `01 - Notes/Figures/`:
- orbits and transfers: `ast_conic_sections`, `ast_orbital_elements_3d`, `ast_visviva_speed`, `ast_hohmann_leo_geo`, `ast_hohmann_dv_ratio`;
- propulsion and ACS: `ast_rocket_equation`, `ast_ep_optimisation`, `ast_momentum_dumping`;
- power, comms and thermal: `ast_eclipse_vs_altitude`, `ast_antenna_gain_beamwidth`, `ast_ber_psk`, `ast_link_budget_pluto`, `ast_thermal_alpha_eps`, `ast_array_temperature_profile`;
- remote sensing: `ast_sso_inclination`, `ast_repeat_groundtrack_solutions`, `ast_sso_ground_track`, `ast_orbit_control_cycle`, `ast_lst_orbit_planes`;
- past papers: `ast_2021_ground_track` (2020/21 Q2(iv)).

## All notes
```dataview
TABLE type, status, file.mtime AS "Updated"
FROM "Year 2/SESA2024 Astronautics"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into
- **From** SESA1015 (Intro to Aero and Astro): basic orbits and the rocket equation.
- **From** [[FEEG1002 Mechanics, Materials and Structures Hub]] (Year 1 Dynamics):
  - central-force angular momentum and the perigee/apogee energy problem: [[FEEG1002 D5 - Angular Impulse and Momentum]];
  - $-GMm/r$ potential energy: [[FEEG1002 D3 - Work, Energy and Power]];
  - mass moment of inertia: [[FEEG1002 D8 - Kinetics of Rigid Bodies]].
- **From** [[FEEG1004 Electronics Hub]] (Year 1 Electrical and Electronic Systems):
  - p-n junctions (solar cells), regulators and rectifiers for the power subsystem: [[FEEG1004 B1 - Semiconductors and Diodes]], [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]];
  - $F = BIL$ and $T = K_Ti$ behind magnetorquers and reaction wheels: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]], [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]];
  - decibels in link budgets: [[FEEG1004 D3 - AC Filters and Bode Plots]].
- **From** [[SESA1016 Thermofluids Hub]]: [[SESA1016 T12 - Conservation of Momentum]] and [[SESA1016 T13 - Conservation of Energy and Propulsion]] provide the control-volume basis for thrust and nozzle energy conversion.
- **Shared with** [[SESA2023 Propulsion Hub]]: [[Tsiolkovsky Rocket Equation]], [[Rocket Staging]], [[Thrust Equation]], nozzle expansion.
- **Shared with** [[SESA2027 Aerospace Mechanics & Control Hub]]: closed-loop control (ACS loop); [[Euler Angles and Rotation Matrices]].
- **From** MATH2048: ODEs ($u''+u = \mu/h^2$), vectors, eigenvalues (principal axes).
- **Into** Year 3: advanced spacecraft design and GDP, astrodynamics and perturbations.

## Sources
- `02 - Sources/Lectures`: Chapters 1, 4–11 and two guest lectures (2025-26); Problem Sheet Workbook 2025-26 V1.1
- `03 - Exams & Past Papers`: 12 papers, 2013/14–2024/25
- Fortescue, Stark & Swinerd, *Spacecraft Systems Engineering* (4th ed.), Wiley. The course textbook.
