---
title: "SESA2027 Aerospace Mechanics & Control Hub"
module: "SESA2027 Aerospace Mechanics & Control"
type: hub
tags: [sesa2027, hub, moc]
status: complete
---

# SESA2027 Aerospace Mechanics & Control Hub

> [!abstract] Module at a glance
> Model the aircraft (Part A: EOM → state space → modes → Laplace/Bode), control it (Part B: feedback, PID, root locus, margins, robustness), then measure it (Part C: sensors → conditioning → ADC → digital filtering).
>
> One thread runs through all three parts: *every element is a dynamic system with poles, a step response and a Bode plot*. That includes the aircraft, the controller, the sensor, the filter and the delay.
>
> Quick reference: [[SESA2027 Formula Sheet]]

## Topic map

### Part A: Dynamic Systems (Dr S. Araujo-Estrada, L1.01–1.11)
1. [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]: DAP1–3, 6-DoF body-axis EOM, Euler angles, small-perturbation decoupling
2. [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]: $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u$, derivative estimates, elevator $\mathbf B$, $G = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B$
3. [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]: stability quartic, Routh, $\omega_n$, $\zeta$, SPO approximation, F-4C
4. [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]: poles and zeros, partial fractions, $t_r$, OS, $t_s$
5. [[SESA2027 A5 - Frequency Response and Bode Plots]]: $G(i\omega)$, Bode construction, resonance

### Part B: Control Systems (L2.01–2.09)
6. [[SESA2027 B1 - Control System Fundamentals and PID Control]]: objectives, closed loop, P/I/D actions
7. [[SESA2027 B2 - Root Locus Method]]: six construction rules, SPO pitch-rate example
8. [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]: GM/PM, eight-step design, ZN. ⚠ L2.05 was delivered from an uncorrected deck (sign inversion, "65° phase margin", +45.7° lead); the slides were re-issued the next day. Follow the corrected slides: see [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#What was said in L2.05 vs the corrected slides|the comparison]]
9. [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]: sign rules, three closed-loop TFs, handling qualities

### Part C: Sensing Systems (Prof A. Cammarano, L3.01–3.08)
10. [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]: measurement chain, resistive/capacitive/inductive/thermoelectric/piezo, IMU fusion
11. [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]: accuracy vs precision, noise, 0th/1st/2nd-order sensors, $\zeta\approx0.7$, RC filter
12. [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]: range mapping, ADC, loading, Nyquist/aliasing, latency, digital filters

## Concept notes

| Part A: modelling | Part A: response | Part B: control | Part C: sensing |
|---|---|---|---|
| [[Design and Analysis Principles]] | [[Laplace Transform]] | [[Closed-Loop Transfer Function]] | [[Measurement Chain]] |
| [[Euler Angles and Rotation Matrices]] | [[Transfer Function]] | [[PID Controller]] | [[Accuracy and Precision]] |
| [[Small Perturbation Linearisation]] | [[Poles and Zeros]] | [[Root Locus]] | [[Wheatstone Bridge and Strain Gauges]] |
| [[State-Space Representation]] | [[Step Response Specifications]] | [[Gain and Phase Margins]] | [[Complementary Filter]] |
| [[Aerodynamic Stability Derivatives]] | [[Frequency Response Function]] | [[Ziegler-Nichols Tuning]] | [[Sensor Dynamic Models]] |
| [[Characteristic Equation and Eigenvalues]] | [[Bode Plot]] | [[Stability vs Manoeuvrability]] | [[ADC Quantisation and Resolution]] |
| [[Damping Ratio and Natural Frequency]] | | | [[Loading Effect and Buffering]] |
| [[Routh-Hurwitz Stability Criterion]] | | | [[Nyquist Sampling and Aliasing]] |
| [[Short Period Oscillation]] | | | [[Digital Filtering]] |
| [[Phugoid Mode]] | | | |

Shared with SESA2022: [[Neutral Point and Static Margin]] (pitch stiffness $M_w = -H_sC_{L^*_\alpha}$).

## Problem sheets (full worked solutions)

| Sheet | Covers | Notes |
|---|---|---|
| [[SESA2027 Practice Problems 1 Solutions]] | A3–A5: modes, SPO approximation, step specifications, FRF | ⚠ The sheet's Q3 overshoot (22.4 %) drops a square root; the correct value is 25.4 % |
| [[SESA2027 Practice Problems 2 Solutions]] | A2, A5, B1–B3: Bode, elevator derivatives, SS→TF, P control, root locus, PD design, ZN | No printed answers; all values checked in Python. ⚠ Q3's $(2,1)$ entry $-1.045\times10^{-1}$ is ten times the F-4C value the rest of the matrix comes from; see [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#Worked example: SPO state space to transfer function (PS2 Q3)\|A2]] |
| [[SESA2027 Part C Problem Sheet Solutions]] | C1–C3: all 13 questions | 3 s.f. as requested |
| [[SESA2027 Mock Questions]] | A1–C3: one 10-mark question per topic note | Self-written, not lecturer-set; timed at about 1.8 min per mark |

## Past papers
> [!info] No SESA2027 past papers are in the vault
> `03 - Exams & Past Papers` is empty. Until a paper appears, use the three problem sheets, the self-written [[SESA2027 Mock Questions]] and the worked lecture examples as exam practice:
> - F-4C modes;
> - SPO pitch-rate root locus;
> - the frequency-response PID design ($K_p = 1.345$, $T_D = 0.342$ s);
> - the ZN DC servo.
>
> The Part C sheet says it also covers the Part C computer lab.

> [!tip] Likely exam question types (from the sheets and lecture emphasis)
> 1. Factor a quartic, identify the SPO and phugoid, and compute $T$, $t_{1/2}$ or $t_2$, $\omega_n$, $\zeta$.
> 2. SPO approximation from dimensional derivatives, giving $\omega_n$, $\zeta$ and the eigenvalues.
> 3. $t_r$, OS and $t_s$ from $\omega_n$ and $\zeta$ (watch the square root in OS), plus a sketch.
> 4. $|G(i\omega)|$ and $\angle G(i\omega)$ at given frequencies, and a Bode sketch with asymptotes.
> 5. $\mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B$ for a 2×2 system, then standard form.
> 6. Root-locus sketch plus the stable-$K$ range.
> 7. PD/PID design for a PM target; ZN table.
> 8. Sensor calculations: bridge strain, second-order sensor specifications, RC cut-off and dB, range mapping and clipping, ADC $Q$, loading, alias frequency, filter delay and $\alpha$, bias integration.

> [!info] What the lecturers said about the exam and quiz (from the transcripts)
> **Stated as possible questions**:
> - stability from the sign of the real part; state Routh–Hurwitz in words (the formula for $R$ is not needed) ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|A3]]);
> - factorised quartic → roots, $t_{1/2}$ or $t_2$, $T$, complex-plane sketch; $\zeta>0\Leftrightarrow\sigma<0$; identify SPO vs phugoid from eigenvalues (A3);
> - convert a dimensionless derivative and give its units; $\alpha\approx w/U_\infty$ from an eigenvector (A3);
> - name the negligible derivatives $\mathring X_q$, $\mathring X_{\dot w}$, $\mathring M_u$ ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives|A2]]);
> - final value of a step response ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response|A4]]);
> - pole–zero map: stable? physical? ([[SESA2027 A5 - Frequency Response and Bode Plots|A5]]); read the frequency for a given attenuation off a Bode plot (A5);
> - cons of model-based and rule-based control ([[SESA2027 B1 - Control System Fundamentals and PID Control|B1]]);
> - effect of P on the $1/s^2$ root locus; PD locus for another $K_P/K_D$ ratio; full-marks root-locus sketch checklist ([[SESA2027 B2 - Root Locus Method|B2]]);
> - GM and PM read off a Bode plot (±5 % tolerance); infinite phase crossover; compare tuning methods with ZN ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning|B3]]).
>
> **Stated as not examined**: the DAPs as such; deriving the EOM and the linearised moment equations; solving Laplace transforms and partial fractions by hand; the MIMO transfer-function derivation and the $q/\eta$, $\theta/\eta$ derivations; assembling $\mathbf M$ and $\mathbf A'$ from data tables; nonlinear sensor behaviour.
>
> **Exam/quiz format**: the ZPK form will be given for root-locus questions; dB conversion formulas will be on the question sheet; the quiz is open book; quiz plants are simplified.

> [!info] Labs, projects and reports (admin from the transcripts)
> - **Lab 1**: compare your SPO approximation with the full model and experimental data; report $t_r$, $OS$ (%) and $t_s$ (1 %); compare with CS-25/FAR-25 and MIL-F-8785C. Parameter sets (JetStar, Boeing 747, F-4C) are interpolated from historical data over Mach and altitude.
> - **Lab 2 (control)**: closed-loop SPO transfer functions; negative $K_p$ is fine; robustness to about ±5 % parameter changes and a gust; cite MIL-F-9490D for margins and Cook Ch. 10 for handling qualities.
> - **Lab 3**: measurement-noise simulation; the Part C lab uses the sensor dynamics from C2.
> - **Part C lab report**: six pages with guiding questions; a summary and critical assessment of the Jupyter notebooks and what you observed (L3.02–3.03, ll. 607–619).
> - **Self-study notebooks**: a Python Jupyter notebook for the A3 eigenvalue calculations (L1.05, l. 442) and Python scripts for the C2 time-domain metrics (L3.05, ll. 605–606) were promised.
> - **CubeSat/gimbal projects**: rise time and tracking objectives; P alone cannot stabilise a double integrator; sample at about 10× the signal frequency when logging data.
> - **Summer**: the Cranfield flight lab demonstrates the SPO and phugoid.

## Sources
- Slides (authoritative), `02 - Sources/Lectures/`: `Lecture 1.01.pdf`–`Lecture 1.11.pdf`, `Lecture 2.01.pdf`–`Lecture 2.08.pdf`, `lecture_2.09.pdf`, `Lecture 3.01.pdf`–`Lecture 3.08.pdf`. `Lecture 2.05.pdf` is the corrected version re-issued on 6 March 2026, the day after the lecture.
- Transcripts (speech-to-text, 2025/26 delivery), same folder: `Lecture 1.01 recording.txt`–`Lecture 1.11 recording.txt`, `Lecture 2.01 recording.txt`–`Lecture 2.09 recording.txt`, `Lecture 3.02-3.03 recording.txt`, `Lecture 3.04 recording.txt`, `Lecture 3.05-3.06 recording.txt`.
  - No recordings of L3.01, L3.07 or L3.08. The `3.05-3.06` recording stops at the break, so it covers L3.05 only.
  - Each topic note has a Transcript slips table and a Lecturer emphasis and exam hints section built from these.
- **Problem sheets**: `02 - Sources/Problem Sheets/`.
- **Figures**: one generator script per topic note in `01 - Notes/Figures/` (`generate_amc_a1_figures.py` … `generate_amc_c3_figures.py`), using the shared style `Year 3/_shared/year3_style.py`. The older `amc_ps*`, `amc_psc_*` and Part A–C overview PNGs predate these scripts.

> [!info] Note standard (upgraded 28 Oct 2026)
> Every topic note follows the Year 3 layout: abstract, collapsed Exam use: quick path, opening prose giving the physical picture, full derivations of the results the slides state or skip, worked examples checked in Python, a Terminology and alternative names table, and a Core / Further-practice Self-study tasks list that marks what was lecturer-set. All topic notes are at status `lectured`; promote them yourself once revised. Corrections found during the upgrade: the PS2 Q3 $(2,1)$ entry (A2), the curvature-drop rule on L1.02 slide 3 (A1), and the ZN "25 % overshoot" claim (B3; quarter decay implies about 50 %).

## All notes
```dataview
TABLE type, status, file.mtime AS "Updated"
FROM "Year 2/SESA2027 Aerospace Mechanics & Control"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into
- From [[FEEG1002 Mechanics, Materials and Structures Hub]] (Year 1 Dynamics):
  - $\sum F = ma$ and rigid-body kinetics: [[FEEG1002 D7 - Kinematics of Rigid Bodies]], [[FEEG1002 D8 - Kinetics of Rigid Bodies]];
  - the mass–spring–damper behind every $\omega_n$, $\zeta$ and FRF here: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].
- From [[FEEG1004 Electronics Hub]] (Year 1 Electrical and Electronic Systems):
  - RC circuits as first-order systems and RC filters as Bode plots: [[FEEG1004 A4 - Capacitors]], [[FEEG1004 D3 - AC Filters and Bode Plots]];
  - negative feedback and op-amp golden rules, the analogue ancestor of the closed loop: [[FEEG1004 B4 - Operational Amplifiers]];
  - the Part C transducers, bridges and conditioning: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]], [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]], [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]];
  - actuators: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]].
- From [[SESA2022 Aerodynamics Hub]]: static stability (T6), which becomes the dynamic derivatives ($M_w$, $M_q$) and lift-curve slopes.
- From MATH2048: ODEs, eigenvalues, Laplace transforms.
- Into [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]: lateral/directional modes, state feedback (LQR), Kalman filtering.
