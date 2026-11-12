---
title: "RTDs and Thermistors"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["RTD", "resistance temperature detector", "Pt100", "thermistor", "NTC", "PTC"]
tags: [feeg1004, concept, transducers, temperature]
status: complete
parent_lectures: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"]
related_concepts: ["[[Thermocouples and Cold-Junction Compensation]]", "[[Op-Amp Comparator]]", "[[Band Theory and Semiconductor Doping]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf", "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §1.6.7, §2.2.3"]
---

# RTDs and Thermistors

RTDs and thermistors are temperature sensors whose resistance changes with temperature: a **resistance temperature detector** (RTD) is a metal element whose resistance rises gently and almost linearly, and an **NTC thermistor** is a semiconductor element whose resistance falls steeply, at about −4 %/°C and roughly exponentially.

$$
R = R_0(1 + \alpha_1T + \alpha_2T^2 + \dots)\ \text{(RTD)},\qquad \alpha_1\approx3.9\times10^{-3}\ /°\mathrm{C}\ \text{(platinum)}
$$

Here $R_0$ is the resistance at 0 °C. An RTD is accurate, stable and nearly linear, but its signal is small. A thermistor gives a large signal but is non-linear and covers roughly −90 to +130 °C, up to 300 °C for some types. Its negative coefficient comes from thermally generated carriers: more carriers at higher temperature mean lower resistance. A **PTC** thermistor instead switches sharply to a high resistance at a set temperature and is used for over-current protection.

Both sensors are passive, so they are read in a potential divider or a bridge. The excitation current heats the element, and this self-heating is a source of error.

![[ee_e1_temperature_sensors.png|700]]

A comparator thermostat that trips at 40 °C with a sensor of $R_{40}$ = 5 kΩ needs $R$ = 2.5 kΩ. A simple heater controller uses an NTC divider to drive a BJT, which switches a relay.

## Related

- [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]] · [[FEEG1004 B4 - Operational Amplifiers]]
- [[Thermocouples and Cold-Junction Compensation]] · [[Potential Divider]]
- Sources: Transducers lecture 1; Mills notes §1.6.7, §2.2.3
