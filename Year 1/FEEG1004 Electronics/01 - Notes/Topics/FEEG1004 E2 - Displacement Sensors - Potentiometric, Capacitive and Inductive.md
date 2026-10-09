---
title: "FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive"
module: "FEEG1004 Electronics"
type: topic
stream: "Part E: Transducers and Measurement"
order: 2
tags: [feeg1004, transducers, displacement, potentiometer, capacitive-sensor, lvdt, linearisation, loading]
aliases: ["Transducers 02", "Displacement sensors", "Potentiometer sensor", "Capacitive sensor", "LVDT"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]", "[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
next_topics: ["[[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]"]
key_concepts: ["[[Potentiometric Displacement Sensor]]", "[[Capacitive Displacement Sensor]]", "[[Linear Variable Differential Transformer]]", "[[Loading Effect and Buffering]]"]
tutorial_sheets: []
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf"]
---

# FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive

> [!abstract] Summary
> Each passive component formula has a length in it, so each can sense displacement:
> $$R = \frac{\rho L}{A},\qquad C = \frac{\varepsilon_0\varepsilon_rA}{d},\qquad L = \frac{N^2}{\mathcal R} = \frac{N^2\mu_0\mu_rA}{l}$$
> - **Potentiometer**: a divider with $V_{out}/V_{in} = x$, but **loading** makes it non-linear. Fix it with an op-amp buffer.
> - **Capacitive**: $C\propto1/d$ is non-linear. Put the sensor in the **feedback** path of an inverting amplifier and $V_{out}\propto d$.
> - **LVDT**: a movable core couples an AC primary to two opposed secondaries. The output amplitude is ∝ displacement and the phase gives the direction.

## Key Concepts
- [[Potentiometric Displacement Sensor]] · [[Capacitive Displacement Sensor]] · [[Linear Variable Differential Transformer]] · [[Loading Effect and Buffering]]

---

## 1. Resistive: the displacement potentiometer
- A three-terminal resistive track with a sliding or rotating **wiper**. Tracks are wire-wound, carbon film, thick-film printed or conductive polymer.
- **Unloaded**: $V_{out} = V_{in}x$, where $x$ is the fractional position. It is linear.
- **Loaded** by $R_{load}$ (any meter or ADC input), the lower section $xR_p$ appears in parallel with the load:

$$
\frac{V_{out}}{V_{in}} = \frac{x}{1 + \dfrac{R_p}{R_{load}}x(1 - x)}
$$

  - This is linear only if $R_{load}\gg R_p$. The error is worst mid-travel.
- **Solution**: a **voltage follower** on the wiper. It has infinite input impedance (no current, so no loading) and zero output impedance (it drives the load without loss) ([[Loading Effect and Buffering]]).

![[ee_e2_pot_loading.png|920]]

| Advantages | Disadvantages |
|---|---|
| low cost, very simple, light, wide temperature range, servo-grade versions exist | sliding contact gives friction and **wear**, so it is unreliable for critical uses; rotary pots have a dead zone (no full 360°) |

## 2. Capacitive displacement sensors
- **Non-contact**, capable of **nanometre** precision. Used for proximity detection, position sensing and touch screens.
- Vary one of three things: **overlap area $A$** (linear), **gap $d$** (∝ 1/d) or **dielectric** (e.g. a fuel-level gauge with Jet A-1 between the plates).
- Gap sensing is **inherently non-linear**. Fix it in hardware (op-amp) or software (look-up table or calculation).

**Op-amp linearisation**:
- An inverting amplifier with an oscillator input (above 50 kHz), a known capacitor $C_s$ at the input and the sensor $C_u$ in the feedback path:

$$
V_{out} = -\frac{Z_f}{Z_{in}}V_{in} = -\frac{1/j\omega C_u}{1/j\omega C_s}V_{in} = -\frac{C_s}{C_u}V_{in} = -\frac{C_s\,d}{\varepsilon_0\varepsilon_rA}V_{in}\ \propto\ d
$$

- The amplitude is linear in the gap. $C_s$ is chosen for a high gain.

![[ee_e2_capacitive_sensor.png|900]]

**Practicalities**:
- Sensor capacitances are 1–500 pF, so measure through the **reactance** at over 100 kHz to get practical impedances.
- The output is an **amplitude-modulated** carrier; **demodulate** it to recover the displacement.
- Useful displacement bandwidth is about 1 Hz–10 kHz.

## 3. Inductive: the LVDT
- Self-inductance $L = N^2/S$ with reluctance $S = l/(\mu_0\mu_rA)$. Changing $N$, the permeability or the reluctance (gap) changes $L$.
- **Linear variable differential transformer**:
  - one **primary** wound uniformly along the length, excited by AC at several kHz;
  - two identical **secondaries** either side, wired in **series opposition**, so $V_{out} = V_a - V_b$;
  - a movable **NiFe core** (slotted to cut eddy currents) on a non-ferromagnetic rod.
- **Centred core**: equal coupling, so $V_{out}$ = 0 (the null). Off-centre, the amplitude grows ∝ displacement, and the **phase flips by 180°** across the null.
- **Phase-sensitive demodulation** recovers a signed DC output. Simple rectification loses the direction.
- **Advantages**: no friction (non-contact), good accuracy, linearity and sensitivity, and **infinite resolution**.

![[ee_e2_lvdt.png|820]]

## Year 2 bridge
- **Aircraft actuators**: LVDTs and RVDTs give position feedback on control-surface actuators and fuel-metering valves. They are rugged and friction-free.
- **Capacitive MEMS accelerometers and gyros** in IMUs use exactly the gap-change principle ([[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]).
- **Fuel-quantity gauging** in aircraft tanks uses capacitive dielectric-level probes.
- The loading-effect lesson is the SESA2027 buffering note ([[Loading Effect and Buffering]], [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).

## Links
- Previous: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]] · Next: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]

## Sources
- Transducers and Measurement Systems lecture 2 of 3 (C. Holmes, 2024).
