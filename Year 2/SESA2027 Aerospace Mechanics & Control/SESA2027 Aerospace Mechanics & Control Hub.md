---
title: "SESA2027 Aerospace Mechanics & Control Hub"
module: "SESA2027 Aerospace Mechanics & Control"
type: hub
tags: [sesa2027, hub, moc]
status: complete
---

# SESA2027 Aerospace Mechanics & Control Hub

> [!abstract] Module at a glance
> **Model the aircraft** (Part A: EOM → state space → modes → Laplace/Bode), **control it** (Part B: feedback, PID, root locus, margins, robustness), then **measure it** (Part C: sensors → conditioning → ADC → digital filtering).
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
8. [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]: GM/PM, eight-step design, ZN
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
| [[SESA2027 Practice Problems 2 Solutions]] | A2, A5, B1–B3: Bode, elevator derivatives, SS→TF, P control, root locus, PD design, ZN | No printed answers; all values checked in Python |
| [[SESA2027 Part C Problem Sheet Solutions]] | C1–C3: all 13 questions | 3 s.f. as requested |

## Past papers
> [!info] No SESA2027 past papers are in the vault
> `03 - Exams & Past Papers` is empty. Until a paper appears, use the three problem sheets together with the worked lecture examples as exam practice:
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

## All notes
```dataview
TABLE type, status, file.mtime AS "Updated"
FROM "Year 2/SESA2027 Aerospace Mechanics & Control"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into
- **From** [[FEEG1002 Mechanics, Materials and Structures Hub]] (Year 1 Dynamics):
  - $\sum F = ma$ and rigid-body kinetics: [[FEEG1002 D7 - Kinematics of Rigid Bodies]], [[FEEG1002 D8 - Kinetics of Rigid Bodies]];
  - the mass–spring–damper behind every $\omega_n$, $\zeta$ and FRF here: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].
- **From** [[FEEG1004 Electronics Hub]] (Year 1 Electrical and Electronic Systems):
  - RC circuits as first-order systems and RC filters as Bode plots: [[FEEG1004 A4 - Capacitors]], [[FEEG1004 D3 - AC Filters and Bode Plots]];
  - negative feedback and op-amp golden rules, the analogue ancestor of the closed loop: [[FEEG1004 B4 - Operational Amplifiers]];
  - the Part C transducers, bridges and conditioning: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]], [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]], [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]];
  - actuators: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]].
- **From** [[SESA2022 Aerodynamics Hub]]: static stability (T6), which becomes the dynamic derivatives ($M_w$, $M_q$) and lift-curve slopes.
- **From** MATH2048: ODEs, eigenvalues, Laplace transforms.
- **Into** [[SESA3047 Advanced Aerospace Mechanics & Control]]: lateral/directional modes, state feedback (LQR), Kalman filtering.
