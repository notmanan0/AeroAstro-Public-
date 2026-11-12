---
title: "Standard Op-Amp Configurations"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["inverting amplifier", "non-inverting amplifier", "voltage follower", "buffer", "summing amplifier", "differential amplifier", "integrator", "differentiator"]
tags: [feeg1004, concept, op-amp]
status: complete
parent_lectures: ["[[FEEG1004 B4 - Operational Amplifiers]]"]
related_concepts: ["[[Op-Amp Golden Rules]]", "[[Loading Effect and Buffering]]", "[[Strain Gauge Bridge Configurations]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W09-EL3 Op-Amps - Interactive.pdf", "Mills notes §2.3.2–2.4"]
---

# Standard Op-Amp Configurations

The standard op-amp configurations are a small set of negative-feedback circuits whose outputs follow from the golden rules alone, and most op-amp circuits are built from them.

| Circuit | $V_{out}$ |
|---|---|
| Follower | $V_{in}$ |
| Inverting | $-\dfrac{R_F}{R_1}V_{in}$ |
| Non-inverting | $\left(1 + \dfrac{R_1}{R_2}\right)V_{in}$ |
| Summing | $-R_F\left(\dfrac{V_1}{R_1} + \dfrac{V_2}{R_2} + \dots\right)$ |
| Differential | $\dfrac{R_2}{R_1}(V_2 - V_1)$ |
| Integrator | $-\dfrac{1}{RC}\int V_{in}\,dt$ |
| Differentiator | $-RC\,\dfrac{dV_{in}}{dt}$ |

In the non-inverting amplifier $R_1$ is the feedback resistor and $R_2$ runs from $V_-$ to ground. In AC, a general impedance pair in the inverting position gives $V_{out} = -(Z_f/Z_{in})V_{in}$, and the integrator and differentiator are the cases where one of the impedances is a capacitor.

A circuit is recognised by where the input goes: an input to $V_-$ makes an inverting stage, an input to $V_+$ a non-inverting stage, and a plain wire from the output to $V_-$ a follower. A larger circuit is broken into blocks, such as divider, amplifier and divider, and the general transfer function of each block is chained into the transfer function of the whole circuit.

Each configuration has its typical use. The follower is a **buffer**, with infinite input impedance and roughly zero output impedance. The differential amplifier amplifies bridge outputs, and the summing amplifier makes DACs and mixers. A capacitive sensor placed in the feedback path of an inverting amplifier gives an output that is linear in the gap ([[Capacitive Displacement Sensor]]).

![[ee_b4_opamp_configurations.png|800]]

Tutorial 4 Q1 gives $V_{out} = -1.6V_1 - 2V_2$, and Mills Ex. 3 gives $V_{out} = 5V_1 - 2V_2 + 0.5V_3$.

## Related

- [[FEEG1004 B4 - Operational Amplifiers]]
- [[Op-Amp Golden Rules]] · [[Loading Effect and Buffering]] · [[Capacitive Displacement Sensor]]
- Year 2: [[PID Controller]]
- Sources: Mills notes §2.3.2–2.4
