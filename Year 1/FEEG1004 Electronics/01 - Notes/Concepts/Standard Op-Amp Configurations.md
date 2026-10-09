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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W09-EL3 Op-Amps - Interactive.pdf"]
---

# Standard Op-Amp Configurations

## Definition

> [!note] Definition
> | Circuit | $V_{out}$ |
> |---|---|
> | Follower | $V_{in}$ |
> | Inverting | $-\dfrac{R_F}{R_1}V_{in}$ |
> | Non-inverting | $\left(1 + \dfrac{R_1}{R_2}\right)V_{in}$ |
> | Summing | $-R_F\left(\dfrac{V_1}{R_1} + \dfrac{V_2}{R_2} + \dots\right)$ |
> | Differential | $\dfrac{R_2}{R_1}(V_2 - V_1)$ |
> | Integrator | $-\dfrac{1}{RC}\int V_{in}\,dt$ |
> | Differentiator | $-RC\,\dfrac{dV_{in}}{dt}$ |
>
> In AC, a general impedance pair gives $V_{out} = -(Z_f/Z_{in})V_{in}$.

## Explanation
- **Recognise by the input**: input to $V_-$ means inverting; input to $V_+$ means non-inverting; a wire from the output to $V_-$ means follower.
- **Break big circuits into blocks** (divider → amplifier → divider) and chain the *general* transfer functions into a *circuit* transfer function.
- The follower is a **buffer**: infinite $Z_{in}$ and ~0 $Z_{out}$.
- The differential amplifier amplifies bridge outputs.
- The summing amplifier makes DACs and mixers.

![[ee_b4_opamp_configurations.png|800]]

## Examples
- Tutorial 4 Q1: $V_{out} = -1.6V_1 - 2V_2$.
- Mills Ex. 3: $V_{out} = 5V_1 - 2V_2 + 0.5V_3$.
- A capacitive sensor in the feedback path of an inverting amplifier gives an output linear in the gap ([[Capacitive Displacement Sensor]]).

## Related
- Topic notes: [[FEEG1004 B4 - Operational Amplifiers]]
- Concepts: [[Op-Amp Golden Rules]] · [[Loading Effect and Buffering]] · [[Capacitive Displacement Sensor]]
- Year 2: [[PID Controller]]

## Sources
- Mills notes §2.3.2–2.4
