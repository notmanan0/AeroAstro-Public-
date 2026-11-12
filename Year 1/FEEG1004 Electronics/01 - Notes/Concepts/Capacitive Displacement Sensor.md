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

A capacitive displacement sensor measures position through the change in $C=\varepsilon_0\varepsilon_rA/d$ as the overlap area, the gap or the dielectric varies. It is non-contact, reaches nanometre precision, and is used for proximity sensing and touch screens.

When the gap is the measured variable, the capacitance varies as $1/d$. Placing the sensor capacitance $C_u$ in the feedback path of an inverting amplifier, with a reference capacitor $C_s$ at the input, inverts this dependence and makes the output linear in the gap:

$$
V_{out}=-\frac{C_s}{C_u}V_{in}=-\frac{C_s\,d}{\varepsilon_0\varepsilon_rA}V_{in}\ \propto\ d.
$$

The alternative is to linearise in software with a look-up table.

Sensor capacitances are only $1$–$500\ \mathrm{pF}$, so they are measured through their reactance with an excitation above $100\ \mathrm{kHz}$. The output is then an amplitude-modulated carrier that must be demodulated, and the usable displacement bandwidth is about $1\ \mathrm{Hz}$ to $10\ \mathrm{kHz}$.

![[ee_e2_capacitive_sensor.png|700]]

## Related

- [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- [[Capacitance]] · [[Complex Impedance]] · [[Standard Op-Amp Configurations]]
- Sources: Transducers lecture 2
