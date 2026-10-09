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
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf", "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# RTDs and Thermistors

## Definition

> [!note] Definition
> - **RTD** (metal): $R = R_0(1 + \alpha_1T + \alpha_2T^2 + \dots)$, with $R_0$ at 0 °C. Pt: $\alpha_1\approx3.9\times10^{-3}$ /°C.
> - **NTC thermistor** (semiconductor): resistance **falls** steeply with temperature (≈ −4 %/°C), roughly exponentially.

## Explanation
- RTDs are accurate, stable and nearly linear, with a small signal.
- Thermistors give a large signal but are non-linear, over roughly −90 to +130 °C (up to 300 °C for some types). The negative coefficient comes from thermally generated carriers.
- **PTC** thermistors switch sharply at a set temperature and are used for over-current protection.
- Both are **passive**: read them in a divider or bridge. Self-heating from the excitation current is an error source.

![[ee_e1_temperature_sensors.png|700]]

## Examples
- Comparator thermostat: $R$ = 2.5 kΩ to trip at 40 °C for $R_{40}$ = 5 kΩ.
- Mills heater: NTC divider → BJT → relay.

## Related
- Topic notes: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]] · [[FEEG1004 B4 - Operational Amplifiers]]
- Concepts: [[Thermocouples and Cold-Junction Compensation]] · [[Potential Divider]]

## Sources
- Transducers lecture 1; Mills notes §1.6.7, §2.2.3
