---
title: "FEEG1004 E1 - Measurement Systems and Temperature Sensors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part E: Transducers and Measurement"
order: 1
tags: [feeg1004, transducers, measurement, sensitivity, resolution, accuracy, precision, rtd, thermistor, thermocouple]
aliases: ["Transducers 01", "Measurement systems", "Sensor definitions", "Temperature sensors"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 B4 - Operational Amplifiers]]"]
next_topics: ["[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]"]
key_concepts: ["[[Transducer Static Characteristics]]", "[[Passive and Active Transducers]]", "[[RTDs and Thermistors]]", "[[Thermocouples and Cold-Junction Compensation]]", "[[Measurement Chain]]", "[[Accuracy and Precision]]"]
tutorial_sheets: []
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf"]
---

# FEEG1004 E1 - Measurement Systems and Temperature Sensors

> [!abstract] Summary
> A **transducer** converts a physical quantity into an electrical signal.
> - **Chain**: sensing element → transducer → signal conditioning (mV → V) → ADC → record, analyse or control.
> - **Vocabulary**: sensitivity, linearity, resolution, uncertainty, precision, accuracy, repeatability, drift and error. Resolution is often over-rated: **precision (noise) usually limits you first**.
> - **Passive** transducers (R, C, L) need excitation; **active** ones (thermocouple, piezo) generate their own signal.
> - **Temperature**: RTDs (metal, +0.4 %/°C), NTC thermistors (semiconductor, about −4 %/°C) and thermocouples (Seebeck, µV/°C, needing a reference junction).

## Key Concepts
- [[Transducer Static Characteristics]] · [[Passive and Active Transducers]] · [[RTDs and Thermistors]] · [[Thermocouples and Cold-Junction Compensation]] · [[Measurement Chain]] · [[Accuracy and Precision]]

---

## 1. Instrumentation systems
![[ee_e1_measurement_chain.png|1000]]

- The **primary sensing element** (diaphragm, spring, float, turbine, beam) turns the measurand into a mechanical change. The **transducer** converts that to an electrical change; e.g. a strain gauge gives resistance → voltage.
- **Signal conditioning** amplifies, filters and buffers mV signals up to the ADC's full scale (typically 10 V).
- Typical mechanical measurands: displacement, velocity, acceleration, vibration, force, pressure, strain, flow and temperature.
- Motivation: control systems, **structural health monitoring (SHM/HUMS)** and **digital twins** all start from measurement.

## 2. Static characteristics and error vocabulary
| Term | Meaning |
|---|---|
| **Sensitivity** (responsivity, scale factor) | $\Delta A_{out}/\Delta A_{in}$, e.g. mV/°C, V/mm, V/Pa |
| **Linearity** | how constant the sensitivity stays across the range; quoted as maximum deviation, % of full scale |
| **Uncertainty** | the range within which the true value lies; linked to the standard deviation |
| **Resolution** | the smallest detectable increment; a 16-bit ADC on 10 V gives $10/2^{16}$ = **0.15 mV** |
| **Precision** | the spread from noise, non-linearity, hysteresis etc.; a 10 mV noise floor makes 0.15 mV resolution irrelevant |
| **Accuracy** | closeness of the mean to the true value (bias) |
| **Repeatability** | closeness of repeated readings under the same conditions |
| **Drift** | output change not caused by an input change |
| **Error** | measured value − true value |

![[ee_e1_static_characteristics.png|900]]

![[ee_e1_accuracy_precision.png|1000]]

## 3. Passive vs active transducers
| Type | Needs power? | Principle | Examples |
|---|---|---|---|
| **Passive** | yes, excitation | a change in $R = \rho L/A$, $C = \varepsilon A/d$ or $L = N^2/\mathcal R$ | RTD, thermistor, potentiometer, strain gauge, capacitive sensor, LVDT |
| **Active** | no | a material effect generates the signal (thermoelectric, piezoelectric, electromagnetic) | thermocouple, piezo accelerometer, tachogenerator |
| **Optical** | usually | light (lasers, fibres) | fibre-Bragg strain sensors, encoders |

## 4. Temperature sensors
![[ee_e1_temperature_sensors.png|920]]

- **RTD (metal)**:
  - $R = R_0(1 + \alpha_1T + \alpha_2T^2 + \dots)$ with $R_0$ at 0 °C;
  - platinum (Pt100) gives about +0.39 %/°C;
  - stable, accurate and nearly linear, but low sensitivity.
- **Thermistor (NTC semiconductor)**:
  - resistance **falls** strongly as more carriers are thermally generated, about −4 %/°C;
  - highly non-linear (exponential); typically −90 to +130 °C;
  - big signal but needs linearisation. PTC types trip sharply and are used as resettable fuses.
- **Thermocouple (active)**:
  - a junction of two dissimilar metals has a temperature-dependent contact potential of a few tens of µV/°C;
  - with both ends joined at different temperatures, a current flows: the **Seebeck effect**;
  - it measures a **temperature difference**, so the reference ("cold") junction must be known: a classic ice bath at 0 °C, or **cold-junction compensation**.
  - CJC measures the terminal temperature with an IC (silicon transistor) sensor and adds the equivalent EMF. Purpose-built amplifiers include CJC and gain, giving e.g. 10 mV/°C.
  - Extra junctions with the meter leads cancel if they are at the same temperature.

> [!example] Op-amp comparator thermostat, a passive sensor in a system (links to Part B)
> An NTC in a divider against a reference divider feeds a comparator. The output switches when the ratios match ([[Op-Amp Comparator]], [[FEEG1004 B4 - Operational Amplifiers]]).

## Year 2 bridge
- SESA2027 Part C revisits the same vocabulary, then adds **dynamic** characteristics: sensor order, time constant and bandwidth ([[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]], [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]], [[Accuracy and Precision]], [[Measurement Chain]]).
- **ADC resolution vs noise** and scaling/offsetting into the ADC range are covered in [[ADC Quantisation and Resolution]] and [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]].
- **Thermocouples** are the workhorse of engine test beds, measuring exhaust gas and turbine entry temperatures ([[Turbine Entry Temperature and Blade Cooling]], [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]). Spacecraft thermal control uses thermistors and PRTs ([[SESA2024 10 - Thermal Control]]).

## Links
- Next: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]

## Sources
- Transducers and Measurement Systems lecture 1 of 3 (C. Holmes, 2024); Mills notes §1.6.7 (NTC thermistors).
