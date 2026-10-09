---
title: "FEEG1004 B4 - Operational Amplifiers"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 4
tags: [feeg1004, electronics, op-amp, comparator, negative-feedback, golden-rules, integrator, gain-bandwidth]
aliases: ["EL3 op-amps", "Op-amps", "Operational amplifier", "Golden rules"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
next_topics: ["[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"]
key_concepts: ["[[Op-Amp Golden Rules]]", "[[Standard Op-Amp Configurations]]", "[[Op-Amp Comparator]]", "[[Loading Effect and Buffering]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W09-EL3 Op-Amps - Interactive.pdf", "02 - Sources/S1 Electronics/S1-W15-EL5 Digital Logic 2 Sequential - Interactive.pdf"]
---

# FEEG1004 B4 - Operational Amplifiers

> [!abstract] Summary
> An op-amp is a very-high-gain differential amplifier.
> - **Open loop**: $V_{out} = A_{OL}(V_+ - V_-)$ with $A_{OL}\sim2\times10^5$. It **saturates** near the rails for any input difference above ~70 µV. That makes it a **comparator**.
> - **With negative feedback** (output → $V_-$), two **golden rules** give every linear circuit's transfer function:
>   1. the output does whatever makes $V_+ = V_-$;
>   2. no current flows into either input.
> - Standard blocks: follower, inverting, non-inverting, summing, differential, integrator, differentiator.

## Key Concepts
- [[Op-Amp Golden Rules]] · [[Standard Op-Amp Configurations]] · [[Op-Amp Comparator]] · [[Loading Effect and Buffering]]

---

## 1. The device (Mills §2.1)
- There are five terminals: $+V_{CC}$, $-V_{CC}$ (typically ±15 V), the inverting input $V_-$, the non-inverting input $V_+$ and the output. The classic 741 also has offset-null pins.
- The output saturates about 1 V inside the rails, at ±14 V for ±15 V supplies.
- The linear input window is $28\ \mathrm V/2\times10^5$ = 140 µV wide, i.e. **±70 µV** about the reference.

## 2. Open loop: the comparator (§2.2, W9)
![[ee_b4_opamp_open_loop.png|900]]

- With no feedback, the output slams to $+V_{sat}$ if $V_+ > V_-$ and $-V_{sat}$ otherwise.
- **Sine → square converter**: $V_-$ = 0 gives a zero-crossing detector with the same frequency and in phase.
- **Variable pulse width**: a triangle wave on $V_+$ against an adjustable $V_{REF}$ on $V_-$. Raising $V_{REF}$ shortens the high time, which is the basis of PWM.
- **Temperature alarm** (Mills §2.2.3): an NTC thermistor divider against an $R$–$R$ reference of +3 V. When the thermistor falls below $R$ (hot), $V_+ > V_{REF}$ and the output goes high, lighting the lamp.

> [!example] W9: NTC thermistor switching a light at 40 °C
> - $V_{REF} = V_{CC}/2$ from equal resistors. The light switches ON as temperature rises: the NTC resistance falls and moves $V_+$ past $V_{REF}$.
> - Switching happens when the two dividers have the same ratio (1/3 here). With $R_{40}$ = 5 kΩ, $R$ = **2.5 kΩ**.

## 3. Negative feedback and the golden rules (§2.3)
- Feed a fraction of the output back to $V_-$. If $V_-$ rises above $V_+$, the output falls and pulls $V_-$ back down.
- The huge, unpredictable $A_{OL}$ is traded for a **precise gain set only by resistor ratios**. This idea dates from the 1920s and appears in mechanical, thermal and biological systems too.
- The golden rules only hold **with negative feedback** (a resistor or wire from the output to $V_-$).

| Rule | Physical basis |
|---|---|
| **GR1**: $V_+ = V_-$ | $A_{OL}$ huge, so $V_+ - V_- = V_{out}/A_{OL}\approx0$ (about 0.001 % of the output for the 741) |
| **GR2**: no input current | input bias currents < 500 nA (741) or pA (FET input) |

## 4. The standard circuits (§2.3.2)
![[ee_b4_opamp_configurations.png|1000]]

**Inverting amplifier derivation** (W9):
- GR1: $V_A = V_+ = 0$, a **virtual earth**.
- Ohm: $I_1 = V_{in}/R_1$.
- GR2: all of $I_1$ flows through $R_F$.
- KVL from A to the output: $0 - I_1R_F = V_{out}$, so

$$
V_{out} = -\frac{R_F}{R_1}V_{in}
$$

**Non-inverting amplifier derivation**:
- GR2 means $R_1$ and $R_2$ form an unloaded divider, so $V_- = V_{out}R_2/(R_1 + R_2)$.
- GR1 sets this equal to $V_{in}$, giving $V_{out} = (1 + R_1/R_2)V_{in}$.

| Configuration | Transfer function | Recognise it by |
|---|---|---|
| Voltage follower | $V_{out} = V_{in}$ | wire from output to $V_-$; input on $V_+$ |
| Inverting | $-R_F/R_1$ | input via $R_1$ to $V_-$; $V_+$ grounded |
| Non-inverting | $1 + R_1/R_2$ | input straight to $V_+$ |
| Summing | $-R_F\sum V_k/R_k$ | inverting with extra inputs |
| Differential | $(R_2/R_1)(V_2 - V_1)$ | one input to each terminal |
| Integrator | $-\dfrac{1}{RC}\int V_{in}\,dt$ | capacitor in the feedback path |
| Differentiator | $-RC\,dV_{in}/dt$ | capacitor at the input |

- **Summing amplifier uses**: a 4-bit DAC with weights 8:4:2:1 (the *Summing* panel), an audio mixer, and the clean way to add two sources, since the virtual earth isolates the inputs ([[FEEG1004 A7 - Thevenin, Superposition and Relays]]).
- **Differential amplifier**: measures small differences (ECG, bridge outputs). It is the strain-gauge amplifier of [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]].
- **Follower**: infinite input impedance and ~zero output impedance. It stops a high-impedance source being divided down by a low-impedance load ([[Loading Effect and Buffering]]).

![[ee_b4_integrator_differentiator.png|760]]

> [!example] Integrator derivation (W15 recap)
> - GR1: $V_- = 0$, so $V_{out} = -V_C$.
> - Ohm: $I_R = V_{in}/R$. GR2: $I_C = I_R$.
> - Capacitor: $V_C = \frac{1}{C}\int I_C\,dt$. Therefore $V_{out} = -\frac{1}{RC}\int V_{in}\,dt$.
> - A constant input gives a **ramp**, used as a ramp generator or timer.

> [!example] Mills worked examples
> - **Ex. 1**, non-inverting with 30 kΩ/15 kΩ: $V_{out} = (1 + 2)\times3$ = **9 V**.
> - **Ex. 2**, divider → non-inverting → divider: 4 V → 2 V → ×(1 + 20/10) = 6 V → **3 V**. Break the circuit into blocks.
> - **Ex. 3**, two cascaded summing amplifiers: $V' = -(5V_1 + 0.5V_3)$, then $V_{out} = -(V' + 2V_2)$ = **5V₁ − 2V₂ + 0.5V₃**. A *circuit* transfer function is built from the *general* ones.

## 5. Practical limits (§2.5)
- **Bias currents** (nA–pA) justify GR2.
- **Input offset voltage**: nulled with a 10 kΩ potentiometer on pins 1 and 5.
- **Slew rate** (~10 V/µs) limits the output rate of change, so square edges become ramps.
- **Gain–bandwidth product**: the open-loop gain falls as $1/f$ above a few Hz, so closed-loop gain × bandwidth ≈ constant (1 MHz for the 741). A gain of 5 is flat to 200 kHz, a gain of 1000 only to 1 kHz. The roll-off is deliberate, to prevent oscillation.

![[ee_b4_gain_bandwidth.png|720]]

## Year 2 bridge
- **Negative feedback is control theory**: $A_{CL} = A/(1 + A\beta)\to1/\beta$ as $A\to\infty$ is the closed-loop transfer function $G/(1 + GH)$ ([[Closed-Loop Transfer Function]], [[SESA2027 B1 - Control System Fundamentals and PID Control]], [[Open-Loop, Feedback and Feedforward Control]]).
- **Analogue PID**: an inverting amplifier (P), an integrator (I) and a differentiator (D), summed ([[PID Controller]]). The differentiator amplifies high-frequency noise, the same warning SESA2027 gives for numerical derivatives ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).
- **Gain–bandwidth** is a first-order pole; the op-amp frequency response is a Bode plot ([[Bode Plot]], [[SESA2027 A5 - Frequency Response and Bode Plots]]).
- **Signal conditioning** scales and offsets sensor voltages into the ADC range with these circuits ([[Measurement Chain]], [[ADC Quantisation and Resolution]]).
- **Active filters** add an op-amp to RC filters for gain and buffering ([[FEEG1004 D3 - AC Filters and Bode Plots]]).

## Links
- Previous: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]] · Next: [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- Worked problems: [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]] (Q1, Q5)

## Sources
- Mills notes §2 (op-amps, worked examples, practical considerations); Week 9 interactive session (EL3); Week 15 recap (integrator).
