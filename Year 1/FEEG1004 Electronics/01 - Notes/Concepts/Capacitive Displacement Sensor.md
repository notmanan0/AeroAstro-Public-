---
title: "Capacitive Displacement Sensor"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["capacitive sensor", "proximity sensor", "capacitance probe", "fuel level gauge"]
tags: [feeg1004, concept, transducers, displacement, capacitance]
status: complete
parent_lectures: ["[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]"]
related_concepts: ["[[Capacitance]]", "[[Standard Op-Amp Configurations]]", "[[Complex Impedance]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf"]
---

# Capacitive Displacement Sensor

## Definition

> [!note] Definition
> $C = \varepsilon_0\varepsilon_rA/d$ is varied through the overlap area, the gap or the dielectric. With the sensor $C_u$ in the **feedback** path of an inverting amplifier and a reference $C_s$ at the input:
>
> $$V_{out} = -\frac{C_s}{C_u}V_{in} = -\frac{C_s\,d}{\varepsilon_0\varepsilon_rA}V_{in}\ \propto\ d$$

## Explanation
- Non-contact, nanometre precision; used for proximity sensing and touch screens.
- Gap sensing is ∝ 1/d. The op-amp trick inverts it; software look-up tables are the alternative.
- Sensor values of 1–500 pF are measured through the reactance at over 100 kHz. The output is an AM carrier that must be demodulated.
- The displacement bandwidth is about 1 Hz–10 kHz.

![[ee_e2_capacitive_sensor.png|700]]

## Related
- Topic notes: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Capacitance]] · [[Complex Impedance]] · [[Standard Op-Amp Configurations]]

## Sources
- Transducers lecture 2
