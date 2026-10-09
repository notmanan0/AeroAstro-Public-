---
title: "FEEG1004 Electronics Hub"
module: "FEEG1004 Electronics"
type: hub
aliases: ["FEEG1004 Electrical and Electronic Systems", "FEEG1004 Hub", "Electrical and Electronic Systems"]
tags: [feeg1004, hub, electronics, circuits, machines, ac-circuits, transducers]
status: complete
---

# FEEG1004 Electronics Hub

*FEEG1004 Electrical and Electronic Systems*: five strands that take you from a single charge to a complete measurement system.

> [!abstract] Module at a glance
> Every strand uses the same toolkit: **KCL, KVL, Ohm and $P = VI$**, applied with the right V–I law for each component.
> - **Part A, Fundamentals (S1)**: charge, fields, potential and induction → DC circuit laws → capacitors and inductors → mesh analysis, Thévenin and superposition.
> - **Part B, Electronics (S1)**: semiconductors → diodes (rectifiers, regulators, limiters) → transistors as switches and amplifiers → op-amps (golden rules) → combinational and sequential logic.
> - **Part C, Electric machines (S2)**: Faraday and Lorentz in machine form → synchronous generators and three-phase → transformers → DC generators and motors, characteristics and speed control.
> - **Part D, AC circuits (S2)**: phasors turn ODEs into complex algebra → impedance → filters and Bode plots → active, reactive and apparent power, and power-factor correction.
> - **Part E, Transducers (S2)**: measurement vocabulary → temperature, displacement, strain, pressure and flow sensors, with the bridges and op-amps that condition them.
>
> Quick reference: [[FEEG1004 Formula Sheet]]

## Topic map

### Part A: Electrical Fundamentals and DC Circuits
1. [[FEEG1004 A1 - Electrostatics, Potential and Current]]: Coulomb, $\mathbf E = \mathbf F/q$, $E = -dV/dx$, drift velocity, $P = VI$
2. [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]: flux, $\mathcal E = -N\,d\Phi/dt$, Lenz, $F = BIL$, Maxwell overview
3. [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]: hydraulic analogy, series/parallel, potential and current dividers
4. [[FEEG1004 A4 - Capacitors]]: $Q = CV$, $i = C\,dv/dt$, $\tfrac{1}{2}CV^2$, charging
5. [[FEEG1004 A5 - Inductors and Electrical Resonance]]: $v = L\,di/dt$, R–L transients, LC resonance, ignition coil
6. [[FEEG1004 A6 - Mesh Analysis]]: loop currents, $\mathbf{RI} = \mathbf V$, branch-current matrices
7. [[FEEG1004 A7 - Thevenin, Superposition and Relays]]: source resistance, Thévenin/Norton, superposition, relays, flyback diodes

### Part B: Electronics
1. [[FEEG1004 B1 - Semiconductors and Diodes]]: band theory, doping, the p-n junction, the diode V–I curve
2. [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]: half/full-wave, ripple $I/2fC$, Zener, clippers, clamps
3. [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]: $I_C = \beta I_B$, saturation switches, MOSFETs, the common emitter
4. [[FEEG1004 B4 - Operational Amplifiers]]: comparators, golden rules, the seven standard circuits, gain–bandwidth
5. [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]: gates, SOP, De Morgan, K-maps, NAND-only
6. [[FEEG1004 B6 - Sequential Logic - Flip-Flops, Registers and Counters]]: the D flip-flop, shift registers, ripple counters, memory

### Part C: Electric Machines
1. [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]: mmf and reluctance, $\mathcal E = NBLu$, $F = BiL$
2. [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]: rpm = 120f/Np, turbo-generator EMF, star/delta
3. [[FEEG1004 C3 - Transformers and AC Power Transmission]]: turns ratio, $4.44fN\Phi_m$, why AC
4. [[FEEG1004 C4 - DC Generators and the Commutator]]: commutation, $E = K_E\omega$, $K_E = ZN_p\Phi/2\pi a$
5. [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]: $T = K_Ti$, $V = E + iR_a$, efficiency, torque ∝ volume
6. [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]: torque–speed, series/shunt, choppers, H-bridge, brushless

### Part D: AC Circuit Analysis
1. [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]: rms, phasors, Euler, complex arithmetic
2. [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]: $Z = R + jX$, CIVIL, phasor circuits, inductive/capacitive loads
3. [[FEEG1004 D3 - AC Filters and Bode Plots]]: RC/RL filters, −3 dB, dB, 20 dB/decade, filter design
4. [[FEEG1004 D4 - AC Power and Power Factor]]: P, Q, S = VI*, power factor, correction

### Part E: Transducers and Measurement
1. [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]: sensitivity to accuracy, passive/active, RTD, thermistor, thermocouple
2. [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]: loaded pot, op-amp linearised capacitive sensor, LVDT
3. [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]: gauge factor, $V = NEG\varepsilon/4$, bridge layouts, pressure, Venturi, pitot

## Core concept notes

| Fundamentals | Circuits and theorems | Electronics | Digital |
|---|---|---|---|
| [[Coulomb's Law and Electric Field]] | [[Ohm's Law and Resistivity]] | [[Band Theory and Semiconductor Doping]] | [[Boolean Algebra and De Morgan's Theorems]] |
| [[Electric Potential and Voltage]] | [[Kirchhoff's Current and Voltage Laws]] | [[P-N Junction Diode]] | [[Karnaugh Maps]] |
| [[Electric Current and Electrical Power]] | [[Series and Parallel Resistors]] | [[Rectification and Smoothing]] | [[D-Type Flip-Flop]] |
| [[Magnetic Flux and Flux Density]] | [[Potential Divider]] | [[Zener Diode Regulator]] | [[Shift Registers and Binary Counters]] |
| [[Faraday's Law and Lenz's Law]] | [[Current Divider]] | [[Diode Limiters and Clamps]] | |
| [[Lorentz Force]] | [[Mesh Current Method]] | [[Bipolar Junction Transistor]] | |
| [[Hydraulic Analogy for Circuits]] | [[Thevenin and Norton Equivalent Circuits]] | [[MOSFET]] | |
| [[Capacitance]] | [[Superposition Theorem (Circuits)]] | [[Transistor as a Switch]] | |
| [[Inductance]] | [[Maximum Power Transfer]] | [[Op-Amp Golden Rules]] | |
| [[RC and RL Transients]] | [[Flyback Diode]] | [[Standard Op-Amp Configurations]] | |
| | [[Electromechanical Relays]] | [[Op-Amp Comparator]] | |

| Machines | AC circuits | Transducers |
|---|---|---|
| [[Magnetomotive Force and Reluctance]] | [[RMS Value]] | [[Transducer Static Characteristics]] |
| [[Synchronous Speed and Pole Number]] | [[Phasor Representation]] | [[Passive and Active Transducers]] |
| [[Motional EMF in Electric Machines]] | [[Complex Impedance]] | [[RTDs and Thermistors]] |
| [[Three-Phase Star and Delta Connections]] | [[RC Low-Pass and High-Pass Filters]] | [[Thermocouples and Cold-Junction Compensation]] |
| [[Ideal Transformer]] | [[Active, Reactive and Apparent Power]] | [[Potentiometric Displacement Sensor]] |
| [[Transformer EMF Equation]] | [[Power Factor Correction]] | [[Capacitive Displacement Sensor]] |
| [[Commutator]] | | [[Linear Variable Differential Transformer]] |
| [[Back EMF and Torque Constants]] | | [[Gauge Factor]] |
| [[Torque-Speed Characteristics of DC Motors]] | | [[Strain Gauge Bridge Configurations]] |
| [[Electric and Magnetic Loading]] | | |
| [[DC Motor Speed Control]] | | |

**Shared with other modules** (linked rather than duplicated): [[Decibels]] · [[Bode Plot]] · [[Transfer Function]] · [[Resonance]] · [[Measurement Chain]] · [[Loading Effect and Buffering]] · [[Accuracy and Precision]] · [[ADC Quantisation and Resolution]] · [[Wheatstone Bridge and Strain Gauges]] · [[Stagnation Pressure and Pitot Tube]]

## Tutorial sheets: full worked solutions

| Sheet | Topics | Solution note |
|---|---|---|
| 1 | electrostatics, battery ESR, resistor ladder, rotating coil | [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]] |
| 2 | mesh matrices, superposition, Thévenin, L/C transients | [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]] |
| 3 | diode circuits, rectifiers, limiter, smoothing | [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]] |
| 4 | op-amp chain, T-network, Boolean, K-maps | [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]] |
| 5 | Faraday, synchronous generator, transformer | [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] |
| 6 | DC motor constants, losses, torque–size, characteristics | [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] |
| 7 | complex numbers, phasors, impedance, current divider | [[FEEG1004 Tutorial 7 - Phasors and Complex Impedance Solutions]] |
| 8 | loaded filter, RL filters, power-factor correction | [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]] |

> [!info] How the solutions were checked
> - Every numerical answer was reproduced in Python: matrix solves for mesh problems, complex arithmetic for AC, exhaustive truth tables for logic.
> - Sheets 1 and 7 have official answers; all are matched. Sheets 2–6 and 8 print none, so their solutions were derived independently; circuit topologies were read from high-resolution renders.
> - **Slips found in the sources, noted where they occur**:
>   - Tutorial 7 solutions: $10\angle20°$ is printed as 9.58 + j3.49; the correct value is 9.40 + j3.42.
>   - Sharkh machines notes: the DC-motor example prints 6600 rpm (π omitted); the correct value is 2101 rpm. The turbo-generator EMF "2473 V" is a typo for 2463 V.
>   - AC 03 slides: the "47 kΩ" low-pass example calculates with 4.7 kΩ.
>   - Lecture 1b: the drift-velocity example uses the wire diameter as its radius.

## Figures
- 74 figures live in `01 - Notes/Figures`. Every plotted number is computed in the generator scripts, which use one shared style module (`feeg1004_style.py`: schematic primitives, logic gates, CVD-checked colours):
  - `generate_fundamentals_figures.py` (Part A, Tutorials 1–2);
  - `generate_electronics_figures.py` (Part B, Tutorials 3–4);
  - `generate_machines_figures.py` (Part C);
  - `generate_ac_transducer_figures.py` (Parts D and E, Tutorials 7–8).

## Recommended study route
1. Read the topic note for the physical model, then **redraw** each circuit yourself.
2. Attempt the tutorial sheet **before** opening the solution note. Compare your **sign conventions and diode/transistor state assumptions**, not just the numbers.
3. For AC, write every phasor in both polar and Cartesian form. Most lost marks are **sin→cos conversions and quadrant errors**.
4. Use [[FEEG1004 Formula Sheet]] as a one-page equation map.

## All notes

```dataview
TABLE type, stream, status, file.mtime AS "Updated"
FROM "Year 1/FEEG1004 Electronics"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into

- **Builds on**:
  - A-level physics (charge, fields, circuits);
  - complex numbers and calculus (MATH1054; see its [[Useful Trigonometry Identities and stuff|trigonometry identities]] note);
  - [[FEEG1002 Mechanics, Materials and Structures Hub]]: the SDOF oscillator is the mechanical twin of the RLC circuit ($m\leftrightarrow L$, $k\leftrightarrow1/C$, $c\leftrightarrow R$), and stress and strain feed straight into strain gauges.

| Later module | Bridge from FEEG1004 | Continue with |
|---|---|---|
| [[SESA2027 Aerospace Mechanics & Control Hub]] (sensing) | transducers, bridges, op-amp conditioning, loading, filters | [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] · [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]] · [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]] |
| SESA2027 (control) | RC/RLC dynamics → transfer functions; filters → Bode plots; op-amp feedback → closed loop | [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · [[SESA2027 A5 - Frequency Response and Bode Plots]] · [[SESA2027 B1 - Control System Fundamentals and PID Control]] |
| [[SESA2024 Astronautics Hub]] | power sources, batteries, regulators, motors, magnetic torquers, dB | [[SESA2024 08 - Electrical Power Subsystem]] · [[SESA2024 06 - Attitude Control]] · [[SESA2024 09 - Communications]] · [[SESA2024 07 - Spacecraft Propulsion]] |
| [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] | circuit ODEs, phasors, rectified waveforms | [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]] · [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]] |
| [[SESA3047 Advanced Aerospace Mechanics & Control Hub]] | feedback, actuators and sensors in the loop | [[SESA3047 1.1 - Dynamic Systems and Control Architectures]] |
| [[SESA2022 Aerodynamics Hub]], [[SESA1015 Intro to Aero & Astro Hub]] | pressure transducers, pitot-static airspeed, strain-gauge balances | [[SESA2022 Wind Tunnel Lab Summary]] · [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] |

> [!tip] The cleanest progression
> - **RC circuit → first-order system → Bode plot**: the same equation appears in [[FEEG1004 A4 - Capacitors]], [[FEEG1004 D3 - AC Filters and Bode Plots]] and SESA2027 A5.
> - **Op-amp golden rules → negative feedback → control**: the 1920s amplifier idea is the closed-loop transfer function of SESA2027 B1.
> - **Strain gauge → bridge → differential amplifier → ADC**: the full measurement chain that SESA2027 Part C analyses dynamically.
> - **$F = BIL$ and $E = K\omega$**: every reaction wheel, magnetorquer and electromechanical actuator on an aerospace vehicle.
