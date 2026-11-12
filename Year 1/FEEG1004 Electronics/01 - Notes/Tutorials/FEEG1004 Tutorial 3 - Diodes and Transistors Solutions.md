---
title: "FEEG1004 Tutorial 3 - Diodes and Transistors Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part B: Electronics"
tags: [feeg1004, tutorial-solutions, diodes, rectifier, limiter, smoothing, conduction-angle]
sheet: "Question sheet 3 - Electronics A"
theory_notes: ["[[FEEG1004 B1 - Semiconductors and Diodes]]", "[[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]"]
key_concepts: ["[[P-N Junction Diode]]", "[[Rectification and Smoothing]]", "[[Diode Limiters and Clamps]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 03 - Electronics A - Diodes & Transistors.pdf"]
---

# FEEG1004 Tutorial 3 - Diodes and Transistors Solutions

> [!abstract] Sheet Info
> Six diode problems: ideal-diode states, half-wave behaviour, a biased soft limiter, a rectifier voltmeter, the conduction angle and smoothing-capacitor design. No answer key is printed, so all values were derived and verified numerically. Every diode question uses the same method: assume each diode's state, solve the circuit, then check that the resulting current or voltage is consistent with that state.

## Theory Links
- [[FEEG1004 B1 - Semiconductors and Diodes]] · [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]] · [[P-N Junction Diode]] · [[Rectification and Smoothing]]

---

## Q1: Four ideal-diode circuits (2.5 kΩ in series, diode across the output)

The ideal diode is a short circuit when forward-biased and an open circuit when reverse-biased. $I$ is defined downwards through the diode.

| Circuit | Supply | Diode orientation (top → bottom) | State | $I$ | $V_{out}$ |
|---|---|---|---|---|---|
| (a) | +5 V | anode at top (points down) | forward: ON | $5/2500$ = +2 mA | 0 V |
| (b) | +5 V | cathode at top (points up) | reverse: OFF | 0 | +5 V |
| (c) | −5 V | anode at top | top at −5 V, reverse: OFF | 0 | −5 V |
| (d) | −5 V | cathode at top | anode (0 V) above cathode (−5 V): ON | −2 mA (2 mA flows upwards) | 0 V |

To check (b), OFF means no current, so there is no drop across the 2.5 kΩ resistor and $V_{out} = 5$ V. The diode then sees 5 V in reverse, which is consistent with the OFF assumption.

## Q2: Half-wave circuit (series diode, output across the resistor)

**(a) Transfer characteristic.** For $v_{in} > 0$ the diode conducts and $v_{out} = v_{in}$, a line of slope 1. For $v_{in} < 0$ it blocks and $v_{out} = 0$.

**(b) Diode voltage.** While the diode conducts, $v_D = 0$. While it blocks, no current flows, so KVL puts the whole input across the diode and $v_D = v_{in}$ during the negative half-cycles. The diode must therefore withstand the full peak inverse voltage.

![[ee_t3_q2_half_wave.png|820]]

## Q3: Soft limiter with biased diodes

In this circuit $v_{in}$ feeds the output node through 10 kΩ, and two branches run from the output node to ground, each made of a diode, a 5 V battery and a 10 kΩ resistor. One diode conducts when $v_{out}$ rises above 5 V; the other, reversed, conducts when $v_{out}$ falls below −5 V. The batteries are taken as oriented for the symmetric design with ±5 V thresholds. (On the printed Figure 4, both 5 V cell symbols have their long plate drawn at the top. If the left branch literally had $+5\ \mathrm V$ rather than $-5\ \mathrm V$, its upward-pointing diode would conduct for $v_{in} < 5\ \mathrm V$ while the right downward-pointing diode would conduct for $v_{in} > 5\ \mathrm V$, giving $v_{out} = (v_{in} + 5)/2$ everywhere.)

For the symmetric design there are three regions. When $|v_{in}| < 5$ V, both diodes are off, no current flows and $v_{out} = v_{in}$. When $v_{in} > 5$ V, the upper branch conducts and KCL at the output gives

$$\frac{v_{in} - v_{out}}{10\,\mathrm k} = \frac{v_{out} - 5}{10\,\mathrm k}\ \Rightarrow\ v_{out} = \frac{v_{in} + 5}{2}.$$

When $v_{in} < -5$ V, symmetry gives $v_{out} = (v_{in} - 5)/2$.

The characteristic therefore has unity slope between ±5 V and half slope beyond. The 10 kΩ resistor inside each branch softens the clipping instead of holding the output flat. This is limiter (d) in the figure.

![[ee_b2_limiters.png|700]]

## Q4: Rectifier AC voltmeter: find R for full scale at 20 V p-p

The meter responds to the average current. The diode passes only the positive half-cycles, with peak current $10/(R + 50)$ A. Averaged over a whole cycle, a half-wave-rectified sine of amplitude $A = 10\ \mathrm V$ has mean $A/\pi$, so

$$
\frac{1}{\pi}\cdot\frac{10}{R + 50} = 1\ \mathrm{mA}\ \Rightarrow\ R + 50 = \frac{10}{\pi\times10^{-3}} = 3183.1\ \Omega\ \Rightarrow\ R = 3133.1\ \Omega \approx 3.13\ \mathrm{k\Omega}.
$$

> [!warning] The printed hint averages over a half-cycle
> The sheet states that the average value of a half-cycle of a sine wave of amplitude $A$ is $2A/\pi$. Because the diode blocks during the negative half-cycle, averaging over the full cycle halves this to $A/\pi$. Substituting $2A/\pi$ directly would give $R + 50 = 20/(\pi \times 10^{-3}) = 6366.2\ \Omega$, so $R = 6316.2\ \Omega \approx 6.32\ \mathrm{k\Omega}$.

## Q5: Conduction angle of a real (0.7 V) half-wave rectifier, 20 V p-p input

The peak input is 10 V, so the diode conducts while $10\sin\theta > 0.7$, that is while $\sin\theta > 0.07$. This runs from $\theta_1 = \arcsin(0.07) = 4.01°$ to $180° - 4.01° = 175.99°$, giving

$$
\text{conduction angle} = 180° - 2(4.01°) = 172.0°\ \text{per cycle}.
$$

![[ee_t3_q5_conduction_angle.png|760]]

## Q6: Full-wave rectifier with smoothing: 10 V average, 0.2 V ripple, 5 mA, 50 Hz

**(a) Capacitor.** The full-wave ripple period is $T/2 = 10$ ms, so

$$C = \frac{I}{2f\,\Delta V} = \frac{0.005}{2(50)(0.2)} = 250\ \mu\mathrm F.$$

**(b) Input amplitude.** The 10 V average sits $\Delta V/2$ below the peak, so $V_{p,out} = 10.1$ V. Two diodes conduct at once in the bridge, so $V_{p,in} = 10.1 + 1.4 = 11.5$ V and the input must be 23 V peak-to-peak.

![[ee_b2_rectifiers.png|700]]

## Sources
- FEEG1004 Question sheet 3 (Electronics A); topologies read from high-resolution renders; answers derived and verified numerically.
