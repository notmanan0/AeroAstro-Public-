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
> Six diode problems: ideal-diode states, half-wave behaviour, a biased soft limiter, a rectifier voltmeter, the conduction angle, and smoothing-capacitor design.
> - No answer key is printed. All values were **derived and verified numerically**.
> - The key habit: **assume** each diode's state, solve, then **check** that the current or voltage is consistent.

## Theory Links
- [[FEEG1004 B1 - Semiconductors and Diodes]] · [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]] · [[P-N Junction Diode]] · [[Rectification and Smoothing]]

---

## Q1: Four ideal-diode circuits (2.5 kΩ in series, diode across the output)
The ideal diode is a short when forward-biased and an open circuit when reverse-biased. $I$ is defined **downwards** through the diode.

| Circuit | Supply | Diode orientation (top → bottom) | State | $I$ | $V_{out}$ |
|---|---|---|---|---|---|
| (a) | +5 V | anode at top (points down) | forward: ON | $5/2500$ = **+2 mA** | **0 V** |
| (b) | +5 V | cathode at top (points up) | reverse: OFF | **0** | **+5 V** |
| (c) | −5 V | anode at top | top at −5 V, reverse: OFF | **0** | **−5 V** |
| (d) | −5 V | cathode at top | anode (0 V) above cathode (−5 V): ON | **−2 mA** (2 mA flows upwards) | **0 V** |

Check (b): OFF means no current, so no drop across the 2.5 kΩ and $V_{out}$ = 5 V; the diode then sees 5 V **reverse** ✔ (consistent).

## Q2: Half-wave circuit (series diode, output across the resistor)
- **(a) Transfer characteristic**: for $v_{in} > 0$ the diode conducts and $v_{out} = v_{in}$ (slope 1). For $v_{in} < 0$ it blocks and $v_{out} = 0$.
- **(b) Diode voltage**:
  - While conducting, $v_D = 0$.
  - While blocking, no current flows, so KVL puts the **whole** input across the diode: $v_D = v_{in}$ (negative half-cycles).
  - The diode must therefore withstand the full **peak inverse voltage**.

![[ee_t3_q2_half_wave.png|820]]

## Q3: Soft limiter with biased diodes
**Circuit**:
- $v_{in}$ feeds the output node through 10 kΩ.
- Two branches go from the output node to ground, each a diode + 5 V battery + 10 kΩ.
- One diode conducts for positive $v_{out}$ above 5 V; the other, reversed, for negative $v_{out}$ below −5 V.
- The batteries are oriented for the symmetric design.

**Regions**:
- $|v_{in}| < 5$ V: both diodes are off. No current flows, so $v_{out} = v_{in}$.
- $v_{in} > 5$ V: the upper branch conducts. KCL at the output:
$$\frac{v_{in} - v_{out}}{10\,\mathrm k} = \frac{v_{out} - 5}{10\,\mathrm k}\ \Rightarrow\ v_{out} = \frac{v_{in} + 5}{2}$$
- $v_{in} < -5$ V: by symmetry $v_{out} = (v_{in} - 5)/2$.

**Description**: a **unity-slope** region between ±5 V, with **half-slope** beyond. The 10 kΩ inside each branch softens the clipping instead of holding the output flat. This is limiter (d) in the figure.

![[ee_b2_limiters.png|700]]

## Q4: Rectifier AC voltmeter: find $R$ for full scale at 20 V p-p
- The meter responds to the **average** current. The diode passes only positive half-cycles, of peak $10/(R + 50)$ A.
- Averaged over a whole cycle, a half-wave-rectified sine of amplitude $A$ has mean $A/\pi$. (The hint's $2A/\pi$ is the mean over the conducting half-cycle only; it is halved over the full cycle.)

$$
\frac{1}{\pi}\cdot\frac{10}{R + 50} = 1\ \mathrm{mA}\ \Rightarrow\ R + 50 = \frac{10}{\pi\times10^{-3}} = 3183\ \Omega\ \Rightarrow\ R\approx3.13\ \mathrm{k\Omega}
$$

## Q5: Conduction angle of a real (0.7 V) half-wave rectifier, 20 V p-p input
- The diode conducts while $10\sin\theta > 0.7$, i.e. $\sin\theta > 0.07$: from $\theta_1 = \arcsin(0.07)$ = 4.01° to $180° - 4.01°$ = 175.99°.

$$
\text{conduction angle} = 180° - 2(4.01°) = 172.0°\ \text{per cycle}
$$

![[ee_t3_q5_conduction_angle.png|760]]

## Q6: Full-wave rectifier with smoothing: 10 V average, 0.2 V ripple, 5 mA, 50 Hz
- **(a)** The full-wave ripple period is $T/2$ = 10 ms:
$$C = \frac{I}{2f\,\Delta V} = \frac{0.005}{2(50)(0.2)} = 250\ \mu\mathrm F$$
- **(b)** The average 10 V sits $\Delta V/2$ below the peak, so $V_{p,out}$ = 10.1 V. Two diodes conduct at once: $V_{p,in} = 10.1 + 1.4$ = 11.5 V, so $v_{in}$ = **23 V peak-to-peak**.

![[ee_b2_rectifiers.png|700]]

## Sources
- FEEG1004 Question sheet 3 (Electronics A); topologies read from high-resolution renders; answers derived and verified numerically.
