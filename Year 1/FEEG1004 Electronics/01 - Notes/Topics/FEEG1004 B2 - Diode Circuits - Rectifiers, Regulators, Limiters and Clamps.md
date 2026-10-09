---
title: "FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 2
tags: [feeg1004, electronics, diode, rectifier, smoothing, ripple, zener, regulator, limiter, clamp]
aliases: ["Rectifiers", "Smoothing capacitor", "Zener regulator", "Clipper circuits", "Diode clamp"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 B1 - Semiconductors and Diodes]]", "[[FEEG1004 A4 - Capacitors]]"]
next_topics: ["[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
key_concepts: ["[[Rectification and Smoothing]]", "[[Zener Diode Regulator]]", "[[Diode Limiters and Clamps]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf"]
---

# FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps

> [!abstract] Summary
> Four families of diode circuit, all analysed with the ON/OFF switch model:
> - **Rectifiers** convert AC to DC. Half-wave uses one diode; the full-wave bridge uses four and loses 2 × 0.7 V. A **smoothing capacitor** holds the peak, leaving a ripple $\Delta V = I/(2fC)$ for full-wave.
> - **Zener regulators** clamp a load at $V_Z$: $R_S = (V_{in} - V_Z)/(I_L + I_Z)$.
> - **Limiters (clippers)** stop the output passing a threshold (±0.7 V, or $V_x$ + 0.7 V with a battery).
> - **Clamps** shift a waveform by charging a series capacitor to $V_p - 0.7$.

## Key Concepts
- [[Rectification and Smoothing]] · [[Zener Diode Regulator]] · [[Diode Limiters and Clamps]]

---

## 1. Rectification (Mills §1.5.2)
- **Half-wave**: one series diode conducts only while $v_{in} > 0.7$ V. The output is the positive half-cycles minus 0.7 V. It is inefficient and very bumpy.
- **Full-wave bridge**: four diodes steer both half-cycles through the load **in the same direction**.
  - Two diodes conduct at a time, so the peak drops by **1.4 V**.
  - The output has **twice** the input frequency (100 Hz from 50 Hz mains).

![[ee_b2_rectifiers.png|780]]

> [!example] Bridge rectifier (W7)
> - When $v_{in}$ is negative, the other diagonal pair of the bridge conducts.
> - With a 10 V input amplitude, the maximum load voltage is $10 - 2(0.7)$ = **8.6 V**.
> - A capacitor across the load holds the peak, provided it can only discharge through the load. The diodes block any other path.

## 2. Smoothing and ripple (§1.5.3)
- A capacitor across the load charges to the peak, then discharges through $R_L$ until the next peak.
- If $R_LC\gg$ the period, the discharge is nearly linear at the load current $I$:

$$
I = C\frac{\Delta V}{\Delta t},\qquad \Delta t = \frac{T}{2} = \frac{1}{2f}\ \Rightarrow\ C = \frac{I}{2f\,\Delta V},\qquad V_{avg} = V_p - \frac{\Delta V}{2} = V_p - \frac{I}{4fC}
$$

- **Half-wave**: $\Delta t = T$, so $C$ must be **twice** as large for the same ripple.
- Design to the **average** voltage and remember the diode drops. A 5 V ± 0.1 V target means a peak of 5.1 V.

> [!example] Tutorial 3 Q6: 10 V average, 0.2 V ripple, 5 mA, 50 Hz, bridge
> - $C = 0.005/(2\times50\times0.2)$ = **250 µF**.
> - The output peak is $10 + 0.1 = 10.1$ V. Add 1.4 V for two diodes: $v_{in}$ peak = 11.5 V, i.e. **23 V peak-to-peak**.

## 3. Zener regulator (§1.5.4–1.5.5)
- A Zener is designed to **break down** at a precise reverse voltage (1.8–200 V). On the steep part of its curve the voltage is fixed while the current varies.
- It is placed in **parallel with the load**, fed through a series $R_S$ that absorbs the difference $V_{in} - V_Z$:

$$
R_S = \frac{V_{in} - V_Z}{I_L + I_Z}\qquad (I_Z\approx5\ \mathrm{mA\ minimum\ to\ stay\ in\ breakdown})
$$

![[ee_b2_zener_regulator.png|880]]

> [!example] W7: 10 V supply, 50 Ω, 6 V Zener
> - **How it works**: if $V_{out}$ tries to rise above 6 V, the Zener takes more current. The extra drop across $R_S$ pulls $V_{out}$ back to 6 V.
> - **No load**: $I_{R_S} = (10 - 6)/50$ = **80 mA**, all through the Zener.
> - **Power** = $4(0.08) + 6(0.08)$ = **0.8 W**, wasted even at no load.
> - **Maximum load current** = 80 mA. Beyond that the Zener switches off and the output droops as a plain divider.

## 4. Limiters and clamps (§1.5.6)
![[ee_b2_limiters.png|780]]

- **(a) One shunt diode**: passes $v_{in}$ until $v_{in} < -0.7$ V, then holds −0.7 V.
- **(b) Anti-parallel pair**: bounded to ±0.7 V. This protects op-amp inputs.
- **(c) Diode + bias battery $V_x$**: the threshold moves to $V_x + 0.7$.
- **(d) Soft limiter (Tutorial 3 Q3)**: each diode connects a 10 kΩ + 5 V branch beyond ±5 V. The slope halves because the series 10 kΩ and branch 10 kΩ form a divider.
- Transfer characteristics assume **no current is drawn** from the output.

**Clamp (DC restorer)**: a series capacitor plus a shunt diode.
- On the first negative peak the diode conducts and charges $C$ to $V_p - 0.7$.
- The capacitor can never discharge (the diode blocks), so $v_{out} = v_{in} + (V_p - 0.7)$. The waveform is shifted with its shape unchanged.
- A battery in series with the diode sets the clamp level.

![[ee_b2_clamp.png|760]]

## Year 2 bridge
- A full-wave rectified sine $|\sin\omega t|$ has a Fourier series of DC plus even harmonics. The smoothing capacitor is a low-pass filter that removes them ([[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]], [[RC Low-Pass and High-Pass Filters]]).
- **Spacecraft power** uses shunt regulators (Zener-like) to dump excess array power, and blocking diodes to stop batteries discharging back into the array during eclipse ([[SESA2024 08 - Electrical Power Subsystem]]).
- **Limiters** protect ADC inputs from over-range signals ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).

## Links
- Previous: [[FEEG1004 B1 - Semiconductors and Diodes]] · Next: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Worked problems: [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]] (Q2–Q6)

## Sources
- Mills notes §1.5.2–1.5.6; Week 7 interactive session.
