---
title: FEEG1004 B4 - Operational Amplifiers
module: FEEG1004 Electronics
type: topic
stream: 'Part B: Electronics'
order: 4
tags:
- feeg1004
- electronics
- operational-amplifiers
- feedback
- analogue-circuits
aliases:
- EL3 op-amps
- Op-amp circuits
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"
- "[[FEEG1004 A4 - Capacitors]]"
- "[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"
next_topics:
- "[[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]"
- "[[FEEG1004 D3 - AC Filters and Bode Plots]]"
- "[[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]"
key_concepts:
- "[[Op-Amp Golden Rules]]"
- "[[Op-Amp Comparator]]"
- "[[Standard Op-Amp Configurations]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]]"
sources:
- 02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf
- 02 - Sources/S1 Electronics/S1-W09-EL3 Op-Amps - Interactive.pdf
- 02 - Sources/S1 Electronics/S1-W15-EL5 Digital Logic 2 Sequential - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 3a.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 3b.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 3c.txt
- 02 - Sources/Tutorial Sheets/Tutorial Sheet 04 - Electronics B - Operational Amplifiers.pdf
coverage: Lecture 3a (ll. 1–169, op-amp pins, open-loop gain, rail saturation, and comparator circuits), Lecture 3b (ll. 1–205, negative feedback, golden rules, inverting, non-inverting, follower, summing, differential, integrator, and differentiator derivations), Lecture 3c (ll. 1–215, multi-stage worked examples and practical limits: bias currents, offset null, slew rate, and gain-bandwidth product), W15-EL5 interactive recap (integrator derivation)
---

# FEEG1004 B4 - Operational Amplifiers

> [!abstract] Summary
> An operational amplifier is a differential amplifier with a very large open-loop gain ($A_{\text{OL}} \approx 2 \times 10^5$ for the 741). Without feedback its output saturates near a supply rail whenever the inputs differ by more than about $70\ \mu\text{V}$, so it acts as a comparator. With negative feedback from the output to the inverting input, the output settles where $V_- \approx V_+$, and the closed-loop operation (scaling, inversion, buffering, addition, subtraction, integration or differentiation) is set by the external resistors and capacitors alone. Real op-amps add input bias currents, an offset voltage, a finite slew rate and a constant gain–bandwidth product.

> [!summary]- Exam use: quick path
> - **Use it when:** finding the output of a comparator or a negative-feedback op-amp circuit, deriving a circuit transfer function, or checking a design against saturation, bandwidth and slew-rate limits.
> - **Assumptions:** an ideal op-amp; for the golden rules, negative feedback to $V_-$ and an unsaturated output, $-V_{\max} < V_{\text{out}} < +V_{\max}$ with $\pm V_{\max} \approx \pm(V_{CC} - 1\ \text{V})$.
> - **Method:** 1. Look for a feedback path from $V_{\text{out}}$ to $V_-$; with none (or with feedback to $V_+$), treat the circuit as a comparator that saturates at $+V_{\max}$ when $V_+ > V_-$ and at $-V_{\max}$ when $V_+ < V_-$. 2. Find $V_+$, using an unloaded potential divider if resistors feed it ($I_+ = 0$). 3. Set $V_- = V_+$ (golden rule 1). 4. Apply Ohm's law in each branch at $V_-$ and KCL with $I_- = 0$ (golden rule 2) to find $V_{\text{out}}$. 5. In a multi-stage circuit work from input to output, then check that no $|V_{\text{out}}|$ exceeds $V_{\max}$.
> - **Common mistakes:** applying the golden rules to a circuit with no negative feedback (or with feedback to $V_+$); losing a sign in a cascade, where an input that passes through two inverting stages comes out positive.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q1: Circuit transfer function of the three-stage chain|Tutorial 4 Q1]]

Operational amplifiers take their name from the mathematical operations they performed on voltages in analogue computers before digital microprocessors existed: addition, subtraction, scaling, integration and differentiation. An integrated op-amp such as the industry-standard **741** contains twenty or so transistors, but circuit analysis treats it as a five-terminal block made of a differential input stage and a high-gain output stage.

Used open-loop, the gain is so large that the output can only sit at one rail or the other unless the two inputs are within tens of microvolts of each other. That makes the bare op-amp a fast two-state comparator, useful for squaring up sine waves, pulse-width modulation and threshold alarms.

When negative feedback returns part of the output to the inverting input, any difference between the inputs drives the output in the direction that removes the difference, and the loop settles with $V_-$ almost exactly equal to $V_+$. The circuit's gain then depends on resistor ratios rather than on the poorly controlled, temperature-sensitive open-loop gain, which is the reason op-amps replaced single-transistor amplifier stages for most linear work.

## 1. Open-loop operation, saturation and comparators

### Terminals, packaging and open-loop gain

As a circuit element an op-amp has five functional connections, all referenced to a common $0\ \text{V}$ ground line. In the standard 8-pin dual-in-line (DIL) package of the 741, pin 1 is marked by a semicircular notch or dot, and the pins are assigned as follows.

| Terminal | Symbol | 741 pin | Role |
| :--- | :---: | :---: | :--- |
| Non-inverting input | $V_+$ | 3 | a positive voltage here drives the output positively |
| Inverting input | $V_-$ | 2 | a positive voltage here drives the output negatively |
| Output | $V_{\text{out}}$ | 6 | the amplified signal, relative to $0\ \text{V}$ ground |
| Positive supply rail | $+V_{CC}$ | 7 | typically $+15\ \text{V}$ for a dual-supply 741 |
| Negative supply rail | $-V_{CC}$ | 4 | typically $-15\ \text{V}$, with $0\ \text{V}$ as the mid-rail reference |
| Offset null | — | 1 and 5 | trim internal asymmetries (see [[#Input offset voltage and offset null]]) |
| No connection | — | 8 | — |

Schematics routinely omit the supply and offset-null pins to keep the layout uncluttered, showing only $V_+$, $V_-$ and $V_{\text{out}}$.

When no external component connects the output back to either input, the op-amp operates in **open-loop mode**. Its output voltage is proportional to the potential difference between the two inputs:

$$
V_{\text{out}} = A_{\text{OL}}(V_+ - V_-)
$$

where $A_{\text{OL}}$ is the **open-loop voltage gain** (dimensionless, in $\text{V}\,\text{V}^{-1}$). For a 741 at DC and low frequencies, $A_{\text{OL}}$ is of the order of $2 \times 10^5$.

### Supply-rail saturation and the linear input window

The output cannot exceed the supply voltages. Saturation of the transistors inside the output stage restricts $V_{\text{out}}$ to two limits $\pm V_{\max}$ that lie roughly $1\ \text{V}$ (and up to $2\ \text{V}$ under heavy load) inside the rails:

$$
\begin{aligned}
-V_{\max} &\le V_{\text{out}} \le +V_{\max} \\[4pt]
+V_{\max} &\approx +V_{CC} - 1\ \text{V} \\[4pt]
-V_{\max} &\approx -V_{CC} + 1\ \text{V}
\end{aligned}
$$

On a standard $\pm 15\ \text{V}$ dual supply, the output saturates at $+V_{\max} \approx +14\ \text{V}$ and $-V_{\max} \approx -14\ \text{V}$.

![[ee_b4_opamp_open_loop.png|900]]

The range of differential input $\Delta V_{\text{in}} = V_+ - V_-$ over which the op-amp stays in its **linear region** follows from dividing the total output swing between the saturation limits by $A_{\text{OL}} = 2 \times 10^5$:

$$
\begin{aligned}
\Delta V_{\text{in,total}} &= \frac{+V_{\max} - (-V_{\max})}{A_{\text{OL}}} \\[6pt]
&= \frac{14\ \text{V} - (-14\ \text{V})}{2 \times 10^5} \\[6pt]
&= \frac{28\ \text{V}}{2 \times 10^5} \\[6pt]
&= 1.4 \times 10^{-4}\ \text{V} = 140\ \mu\text{V}
\end{aligned}
$$

This $140\ \mu\text{V}$ span is centred on $V_+ = V_-$, so the input difference can be at most half of it before the output clips at a rail:

$$
|V_+ - V_-|_{\text{linear}} \le \frac{140\ \mu\text{V}}{2} = 70\ \mu\text{V}
$$

In panel (b) of the figure, $V_+$ is held at a fixed reference $V_{\text{REF}}$ while the inverting input $V_{\text{in}} = V_-$ varies above and below it. For $V_- < V_{\text{REF}} - 70\ \mu\text{V}$, the difference $V_+ - V_-$ exceeds $+70\ \mu\text{V}$ and the output is clamped at $+V_{\max} \approx +14\ \text{V}$. As $V_-$ rises past $V_{\text{REF}}$, the output falls steeply with slope $-A_{\text{OL}}$ through the narrow $\pm 70\ \mu\text{V}$ linear band, and once $V_- > V_{\text{REF}} + 70\ \mu\text{V}$ it is clamped at $-V_{\max} \approx -14\ \text{V}$.

### Comparator circuits

The $\pm 70\ \mu\text{V}$ transition band is negligible beside ordinary signal amplitudes of several volts, so an open-loop op-amp acts as a non-linear **comparator** that reports which input is at the higher potential:

$$
V_{\text{out}} = \begin{cases} +V_{\max} & \text{if } V_+ > V_- \\ -V_{\max} & \text{if } V_+ < V_- \end{cases}
$$

Three standard circuits use this two-state switching.

A **zero-crossing detector** converts a sine wave into a square wave. The inverting input is grounded ($V_- = V_{\text{REF}} = 0\ \text{V}$) and a sine wave of reasonable amplitude (say about $1\ \text{V}$ peak) is applied to $V_+$. The output switches between $+V_{\max}$ and $-V_{\max}$ every time the sine wave crosses $0\ \text{V}$. Because the input traverses the $\pm 70\ \mu\text{V}$ window in a tiny fraction of a cycle, the output is a sharp square wave of the same frequency and in phase with the input, rising when $V_{\text{in}}$ crosses zero going positive and falling when it crosses zero going negative.

A variable pulse-width (mark–space ratio) generator feeds a triangular carrier into $V_+$ and an adjustable DC voltage $V_{\text{REF}}$ into $V_-$. The output is a rectangular wave whose duty cycle varies continuously with $V_{\text{REF}}$. With a low reference $V_{\text{REF1}}$, $V_+ > V_{\text{REF1}}$ for most of each triangular period and the $+V_{\max}$ pulse is wide. Raising the reference to $V_{\text{REF2}} > V_{\text{REF1}}$ shortens the part of each cycle during which $V_+ > V_{\text{REF2}}$ and narrows the pulse. This is **pulse-width modulation** (PWM).

A high-temperature warning circuit places the comparator across a Wheatstone bridge. A single-supply op-amp powered between $+6\ \text{V}$ and $0\ \text{V}$ (so its output saturates at roughly $+6\ \text{V}$ or $0\ \text{V}$) compares two potential-divider branches across the $+6\ \text{V}$ rail. The reference branch has two equal fixed resistors $R$, which hold the inverting input at half the supply:

$$
V_- = V_{\text{REF}} = 6\ \text{V} \cdot \frac{R}{R + R} = +3\ \text{V}
$$

The sensing branch has a **negative temperature coefficient (NTC) thermistor** $R_{\text{NTC}}(T)$ in the upper position (connected to $+6\ \text{V}$) and a fixed resistor $R$ in the lower position (connected to $0\ \text{V}$), and feeds the non-inverting input:

$$
V_+ = 6\ \text{V} \cdot \frac{R}{R_{\text{NTC}}(T) + R}
$$

At low temperature $R_{\text{NTC}} \gg R$, so more than $3\ \text{V}$ drops across the thermistor, $V_+ < +3\ \text{V} = V_{\text{REF}}$, the output stays at $0\ \text{V}$ and the warning lamp on $V_{\text{out}}$ is off. As the temperature rises $R_{\text{NTC}}$ falls, and as soon as it drops below $R$, $V_+$ rises above $+3\ \text{V}$. Then $V_+ > V_-$, the output switches to positive saturation ($\approx +6\ \text{V}$) and the lamp lights.

## 2. Negative feedback and the golden rules

A linear amplifier, whose output follows the input proportionally across the operating range, needs a **negative feedback** path from $V_{\text{out}}$ back to the inverting input $V_-$.

Negative feedback makes the circuit self-correcting. Suppose $V_+$ is held fixed and $V_-$ momentarily rises slightly above it. Then $V_+ - V_-$ is negative, $V_{\text{out}} = A_{\text{OL}}(V_+ - V_-)$ moves negative, and the feedback network pulls $V_-$ back down towards $V_+$. If instead $V_-$ falls slightly below $V_+$, the output swings positive and pushes $V_-$ back up. Because $A_{\text{OL}} \approx 2 \times 10^5$ is so large, the loop settles where $V_-$ tracks $V_+$ to within a few tens of microvolts, $|V_+ - V_-| = |V_{\text{out}}|/A_{\text{OL}}$.

> [!warning] Feedback must return to the inverting input ($V_-$), never to $V_+$
> A feedback resistor wired to $V_+$ by mistake, or a schematic read with the $+$ and $-$ terminals swapped, gives **positive feedback**: a small positive nudge at $V_+$ drives $V_{\text{out}}$ positive, which pushes $V_+$ higher still, and the output runs regeneratively into $+V_{\max}$ or $-V_{\max}$. The golden rules below apply only when negative feedback is present and the output has not saturated.

For first-pass analysis of negative-feedback circuits, the microvolt difference between the inputs and the nanoampere bias currents into the input transistors are neglected. This gives the two **golden rules** of ideal linear op-amp operation. The first is that the output does whatever is necessary, within its saturation limits, to make the voltage difference between the inputs zero:

$$
V_- = V_+
$$

The second is that no current flows into or out of either input terminal (infinite input impedance):

$$
I_+ = 0 \quad \text{and} \quad I_- = 0
$$

When $V_+$ is wired directly to $0\ \text{V}$, the first rule forces the inverting node $V_-$ to $0\ \text{V}$ even though it has no direct conductive path to ground. A node held at $0\ \text{V}$ by active feedback while drawing no current into the amplifier is a **virtual earth** (or virtual ground).

## 3. Standard closed-loop configurations

Ohm's law, Kirchhoff's laws and the two golden rules give the transfer function $V_{\text{out}}(V_{\text{in}})$ of each standard closed-loop circuit in the figure.

![[ee_b4_opamp_configurations.png|900]]

### Inverting amplifier

In the inverting amplifier (panel (a)), $V_+ = 0\ \text{V}$, the input $V_{\text{in}}$ reaches the inverting node A through $R_1$, and feedback resistor $R_F$ links $V_{\text{out}}$ back to node A.

By golden rule 1, node A is a virtual earth at the same potential as $V_+$:

$$
V_A = V_- = V_+ = 0\ \text{V}
$$

Ohm's law across $R_1$ gives the input current $I_1$ flowing from $V_{\text{in}}$ into node A:

$$
I_1 = \frac{V_{\text{in}} - V_A}{R_1} = \frac{V_{\text{in}}}{R_1}
$$

KVL along the feedback branch, from node A through $R_F$ (carrying $I_F$ towards the output) to $V_{\text{out}}$, gives

$$
V_A - I_F R_F - V_{\text{out}} = 0
$$

By golden rule 2 no current enters the inverting input ($I_- = 0$), so KCL at node A sends all of $I_1$ through $R_F$:

$$
I_F = I_1
$$

Substituting $V_A = 0$ and $I_F = I_1 = V_{\text{in}}/R_1$ into the KVL equation:

$$
\begin{aligned}
0 - I_1 R_F - V_{\text{out}} &= 0 \\[6pt]
V_{\text{out}} &= -I_1 R_F \\[6pt]
V_{\text{out}} &= -\frac{V_{\text{in}}}{R_1} R_F \\[6pt]
V_{\text{out}} &= -\frac{R_F}{R_1} V_{\text{in}}
\end{aligned}
$$

The closed-loop gain is $A_v = V_{\text{out}}/V_{\text{in}} = -R_F/R_1$: the output is inverted ($180^\circ$ out of phase with $V_{\text{in}}$) and scaled by the resistor ratio alone. Because node A sits at virtual earth, the input impedance seen by the source is $R_{\text{in}} = V_{\text{in}}/I_1 = R_1$.

If a fixed non-zero reference $V_{\text{ref}}$ is applied to $V_+$ instead of $0\ \text{V}$, golden rule 1 holds node A at $V_A = V_{\text{ref}}$, so $I_1 = (V_{\text{in}} - V_{\text{ref}})/R_1$ and $V_{\text{out}} = V_A - I_1 R_F = V_{\text{ref}} - \frac{R_F}{R_1}(V_{\text{in}} - V_{\text{ref}})$.

### Non-inverting amplifier

In the non-inverting amplifier (panel (b)), $V_{\text{in}}$ is connected directly to $V_+$. The feedback network is a potential divider from $V_{\text{out}}$ through feedback resistor $R_1$ to node A (at $V_-$), and from node A through $R_2$ to ground.

By golden rule 1, node A sits at $V_+$:

$$
V_A = V_- = V_+ = V_{\text{in}}
$$

Ohm's law across the grounded resistor $R_2$ gives the current $I_2$ from node A to ground:

$$
I_2 = \frac{V_A - 0}{R_2} = \frac{V_{\text{in}}}{R_2}
$$

By golden rule 2 ($I_- = 0$), the current $I_1$ flowing from $V_{\text{out}}$ through $R_1$ into node A equals $I_2$:

$$
I_1 = I_2
$$

KVL from $V_{\text{out}}$ across $R_1$ to node A gives

$$
V_{A} + I_1 R_1 - V_{\text{out}} = 0
$$

Substituting $V_A = V_{\text{in}}$ and $I_1 = I_2 = V_{\text{in}}/R_2$ one step at a time:

$$
\begin{aligned}
V_{\text{out}} &= V_A + I_1 R_1 \\[6pt]
V_{\text{out}} &= V_A + I_2 R_1 \\[6pt]
V_{\text{out}} &= V_{\text{in}} + \frac{V_{\text{in}}}{R_2} R_1 \\[6pt]
V_{\text{out}} &= \left(1 + \frac{R_1}{R_2}\right) V_{\text{in}}
\end{aligned}
$$

The output is in phase with the input and the gain $A_v = 1 + R_1/R_2$ is never less than 1. Because $V_{\text{in}}$ drives the non-inverting terminal directly ($I_+ = 0$), the amplifier presents a very high input impedance to the source.

### Voltage follower (unity-gain buffer)

The **voltage follower**, or buffer (panel (c)), is the limiting case of the non-inverting amplifier with $R_1 = 0$ (a direct wire from $V_{\text{out}}$ to $V_-$) and $R_2 \to \infty$ (open circuit to ground). With $V_{\text{out}}$ wired straight to $V_-$ and golden rule 1 equating $V_-$ to $V_+ = V_{\text{in}}$,

$$
\begin{aligned}
V_- &= V_{\text{out}} \\[4pt]
V_+ &= V_{\text{in}} \\[4pt]
V_{\text{out}} &= V_{\text{in}}
\end{aligned}
$$

A gain of 1 gives no voltage amplification, but the follower solves the loading problem studied in [[FEEG1004 A7 - Thevenin, Superposition and Relays]]. A sensor with a high Thévenin source resistance $R_S$ connected directly to a low load resistance $R_L$ forms a potential divider $R_L/(R_S + R_L)$, and most of the signal is lost across $R_S$. A follower placed between them draws no current from the source, so the full open-circuit sensor voltage reaches $V_+$, and it drives $R_L$ from the op-amp's low-impedance output stage without attenuation.

### Summing amplifier

The **summing amplifier** (panel (d)) extends the inverting amplifier by connecting several inputs $V_1, V_2, V_3$ through resistors $R_1, R_2, R_3$ to the single virtual-earth node A, with feedback resistor $R_F$ from node A to $V_{\text{out}}$.

With $V_+ = 0\ \text{V}$, golden rule 1 fixes node A at virtual earth:

$$
V_A = 0\ \text{V}
$$

Each input therefore sees its full voltage across its own resistor, without interacting with the other inputs. By Ohm's law,

$$
I_1 = \frac{V_1 - V_A}{R_1} = \frac{V_1}{R_1}, \qquad I_2 = \frac{V_2 - V_A}{R_2} = \frac{V_2}{R_2}, \qquad I_3 = \frac{V_3 - V_A}{R_3} = \frac{V_3}{R_3}
$$

KCL at node A with golden rule 2 ($I_- = 0$) makes the feedback current the sum of the input currents:

$$
I_F = I_1 + I_2 + I_3
$$

KVL along the feedback path from node A across $R_F$ to $V_{\text{out}}$ gives

$$
\begin{aligned}
V_A - I_F R_F - V_{\text{out}} &= 0 \\[6pt]
V_{\text{out}} &= -I_F R_F \\[6pt]
V_{\text{out}} &= -(I_1 + I_2 + I_3) R_F \\[6pt]
V_{\text{out}} &= -\left(\frac{R_F}{R_1} V_1 + \frac{R_F}{R_2} V_2 + \frac{R_F}{R_3} V_3\right)
\end{aligned}
$$

For $n$ inputs, each additional branch $i$ adds a term $(R_F/R_i)V_i$ inside the brackets. Making all the resistors equal ($R_1 = R_2 = R_3 = R_F$) gives an unweighted adder,

$$
V_{\text{out}} = -(V_1 + V_2 + V_3)
$$

An audio mixer makes each input resistor a potentiometer, so that each instrument or microphone channel has its own level control, while a variable resistor in series with $R_F$ sets the master volume.

The weighted sum also gives a 4-bit **digital-to-analogue converter** (DAC). A 4-bit binary word $b_3 b_2 b_1 b_0$ (such as $1111_2 = 1\times 2^3 + 1\times 2^2 + 1\times 2^1 + 1\times 2^0 = 8 + 4 + 2 + 1 = 15_{10}$) is represented by four logic voltages $V_3, V_2, V_1, V_0$. Choosing the input resistors so that the gains $R_F/R_i$ are in the binary ratio $8 : 4 : 2 : 1$ (for instance $R_3 = R$, $R_2 = 2R$, $R_1 = 4R$, $R_0 = 8R$) gives an analogue output proportional to the numerical value of the input word.

As a sizing example, $R_F = 10\ \text{k}\Omega$, logic levels of $0\ \text{V}$ and $+5\ \text{V}$ and a required step of $-0.5\ \text{V}$ per least significant bit give, with only $b_0 = 1$, a summing-amplifier result that reduces to

$$
\begin{aligned}
V_{\text{out}} &= -\frac{R_F}{R_0}(5\ \text{V}) = -0.5\ \text{V} \\[6pt]
\frac{R_F}{R_0} &= 0.1 \\[6pt]
R_0 &= \frac{10\ \text{k}\Omega}{0.1} = 100\ \text{k}\Omega
\end{aligned}
$$

The binary weighting then halves each resistor for the next bit up, $R_1 = 50\ \text{k}\Omega$, $R_2 = 25\ \text{k}\Omega$ and $R_3 = 12.5\ \text{k}\Omega$, so the gains $R_F/R_i$ are $0.8$, $0.4$, $0.2$ and $0.1$. The full-scale word $1111_2$ gives

$$
V_{\text{out}} = -(0.8 + 0.4 + 0.2 + 0.1)(5\ \text{V}) = -7.5\ \text{V} = 15 \times (-0.5\ \text{V}),
$$

which stays above $-V_{\max} \approx -14\ \text{V}$ on a $\pm 15\ \text{V}$ supply, so the output does not saturate.

### Differential amplifier

The **differential amplifier** (panel (e)) amplifies the difference between two inputs $V_1$ and $V_2$ and rejects any voltage common to both. In the standard symmetric circuit, $V_1$ drives the inverting node A through $R_1$, with feedback resistor $R_2$ from $V_{\text{out}}$ to node A, while $V_2$ drives the non-inverting node B through an identical $R_1$, with a second $R_2$ from node B to ground.

Golden rule 2 guarantees $I_+ = 0$, so the two resistors at node B form an unloaded potential divider across $V_2$:

$$
V_B = \frac{R_2}{R_1 + R_2} V_2
$$

At the inverting input no current enters $V_-$ ($I_- = 0$), so one current flows from $V_1$ through $R_1$ and $R_2$ to $V_{\text{out}}$. The drop $V_A - V_{\text{out}}$ across $R_2$ is therefore the fraction $R_2/(R_1 + R_2)$ of the total difference $V_1 - V_{\text{out}}$ across the series pair:

$$
\begin{aligned}
V_A - V_{\text{out}} &= (V_1 - V_{\text{out}}) \frac{R_2}{R_1 + R_2} \\[6pt]
V_A &= V_{\text{out}} + (V_1 - V_{\text{out}}) \frac{R_2}{R_1 + R_2}
\end{aligned}
$$

Golden rule 1 sets $V_A = V_B$:

$$
(V_1 - V_{\text{out}}) \frac{R_2}{R_1 + R_2} + V_{\text{out}} = \frac{R_2}{R_1 + R_2} V_2
$$

Multiplying every term by $(R_1 + R_2)/R_2$ and isolating $V_{\text{out}}$:

$$
\begin{aligned}
(V_1 - V_{\text{out}}) + V_{\text{out}} \frac{R_1 + R_2}{R_2} &= V_2 \\[6pt]
V_1 - V_{\text{out}} + V_{\text{out}} \left(\frac{R_1}{R_2} + 1\right) &= V_2 \\[6pt]
V_{\text{out}} \left(\frac{R_1}{R_2} + 1 - 1\right) &= V_2 - V_1 \\[6pt]
V_{\text{out}} \frac{R_1}{R_2} &= V_2 - V_1 \\[6pt]
V_{\text{out}} &= \frac{R_2}{R_1} (V_2 - V_1)
\end{aligned}
$$

With all four resistors equal ($R_1 = R_2$), this is pure subtraction, $V_{\text{out}} = V_2 - V_1$. Differential amplifiers are essential in biomedical instruments such as **electrocardiograms (ECG)** and **electroencephalograms (EEG)**, where microvolt differences between skin electrodes must be extracted from much larger $50\ \text{Hz}$ mains interference picked up equally on both leads.

### Inverting amplifier with a T-network feedback loop

A standard inverting amplifier ($A_v = -R_F/R_1$) has input resistance $R_{\text{in}} = R_1$. An application that needs both a high input resistance (say $R_1 \sim 100\ \text{k}\Omega$) and a large gain (say $|A_v| > 100$) would need a single feedback resistor in the tens of megaohms ($R_F > 10\ \text{M}\Omega$), where resistor tolerance, thermal drift and stray capacitance are poor. Replacing $R_F$ with a three-resistor **T-feedback network** ($R_2, R_3, R_4$, Tutorial Sheet 4 Q5) achieves a large gain with modest resistor values.

In the T-network circuit, $V_{\text{in}}$ feeds the inverting node A through $R_1$, $R_2$ connects node A to a central junction X (at potential $V_X$), $R_3$ connects X to ground, $R_4$ connects X to $V_{\text{out}}$, and $V_+ = 0\ \text{V}$.

By golden rule 1 node A is a virtual earth ($V_A = 0\ \text{V}$), so the input current through $R_1$ is

$$
I_1 = \frac{V_{\text{in}} - V_A}{R_1} = \frac{V_{\text{in}}}{R_1}
$$

By golden rule 2 ($I_- = 0$), all of $I_1$ flows from node A through $R_2$ into node X, which fixes $V_X$:

$$
\begin{aligned}
I_2 &= I_1 = \frac{V_{\text{in}}}{R_1} \\[6pt]
V_A - V_X &= I_2 R_2 \\[6pt]
V_X &= -I_1 R_2 = -\frac{R_2}{R_1} V_{\text{in}}
\end{aligned}
$$

At node X, current $I_2$ arrives from node A, current $I_3 = (0 - V_X)/R_3$ arrives from ground through $R_3$, and current $I_4 = (V_X - V_{\text{out}})/R_4$ leaves towards $V_{\text{out}}$. KCL gives

$$
\begin{aligned}
\frac{V_A - V_X}{R_2} + \frac{0 - V_X}{R_3} + \frac{V_{\text{out}} - V_X}{R_4} &= 0 \\[6pt]
\frac{V_{\text{out}} - V_X}{R_4} &= \frac{V_X}{R_2} + \frac{V_X}{R_3} \\[6pt]
V_{\text{out}} &= V_X + R_4 V_X \left(\frac{1}{R_2} + \frac{1}{R_3}\right) \\[6pt]
V_{\text{out}} &= V_X \left(1 + \frac{R_4}{R_2} + \frac{R_4}{R_3}\right)
\end{aligned}
$$

Substituting $V_X = -(R_2/R_1)V_{\text{in}}$ gives the T-network transfer function:

$$
\frac{V_{\text{out}}}{V_{\text{in}}} = -\frac{R_2}{R_1}\left(1 + \frac{R_4}{R_2} + \frac{R_4}{R_3}\right)
$$

## 4. Integrator and differentiator

Replacing either the feedback resistor or the input resistor of an inverting amplifier with a capacitor $C$ brings in the charge–voltage relation $Q = C V_C$, so that $I_C = \mathrm{d}Q/\mathrm{d}t = C\,\mathrm{d}V_C/\mathrm{d}t$, and the amplifier becomes a continuous-time integrator or differentiator.

![[ee_b4_integrator_differentiator.png|900]]

### Op-amp integrator

In the integrator (panel (a)), $V_{\text{in}}(t)$ is applied through resistor $R$ to the inverting node A, capacitor $C$ sits in the feedback path between node A and $V_{\text{out}}(t)$, and $V_+ = 0\ \text{V}$.

By golden rule 1, node A is a virtual earth:

$$
V_A = 0\ \text{V}
$$

Ohm's law across $R$ gives the input current

$$
I_1(t) = \frac{V_{\text{in}}(t) - V_A}{R} = \frac{V_{\text{in}}(t)}{R}
$$

By golden rule 2 ($I_- = 0$), the capacitor charging current $I_2(t)$, flowing from node A towards $V_{\text{out}}$, equals $I_1(t)$:

$$
I_2(t) = I_1(t) = \frac{V_{\text{in}}(t)}{R}
$$

The charge $Q(t)$ on the left plate of $C$ is the time integral of $I_2(t)$, and it produces a drop $V_C(t) = Q(t)/C$ from node A to $V_{\text{out}}$. KVL from node A across $C$ to $V_{\text{out}}$ gives

$$
\begin{aligned}
V_A - \frac{Q(t)}{C} - V_{\text{out}}(t) &= 0 \\[6pt]
V_{\text{out}}(t) &= -\frac{Q(t)}{C} \\[6pt]
V_{\text{out}}(t) &= -\frac{1}{C} \int I_2(t)\,\mathrm{d}t \\[6pt]
V_{\text{out}}(t) &= -\frac{1}{C} \int \frac{V_{\text{in}}(t)}{R}\,\mathrm{d}t \\[6pt]
V_{\text{out}}(t) &= -\frac{1}{RC} \int V_{\text{in}}(t)\,\mathrm{d}t
\end{aligned}
$$

For a constant input $V_{\text{in}}$ applied at $t = 0$, the integral $\int_0^t V_{\text{in}}\,\mathrm{d}t' = V_{\text{in}} t$ grows linearly, so the output ramps at $\mathrm{d}V_{\text{out}}/\mathrm{d}t = -V_{\text{in}}/(RC)$ until it saturates. Integrators are used as precision **ramp generators** in timing circuits and dual-slope analogue-to-digital converters.

### Op-amp differentiator

Swapping the resistor and capacitor gives the **differentiator** (panel (b)), with $C$ at the input and $R$ in the feedback loop.

Because $V_A = 0\ \text{V}$ by golden rule 1, the voltage across the input capacitor is $V_C(t) = V_{\text{in}}(t) - V_A = V_{\text{in}}(t)$, and the charge on $C$ is

$$
Q(t) = C V_{\text{in}}(t)
$$

Differentiating with respect to time gives the current $I_1(t)$ through $C$ into node A:

$$
I_1(t) = \frac{\mathrm{d}Q(t)}{\mathrm{d}t} = C\,\frac{\mathrm{d}V_{\text{in}}(t)}{\mathrm{d}t}
$$

By golden rule 2 the feedback current $I_2(t)$ through $R$ equals $I_1(t)$, and KVL from node A across $R$ to $V_{\text{out}}(t)$ gives

$$
\begin{aligned}
V_A - I_2(t) R - V_{\text{out}}(t) &= 0 \\[6pt]
V_{\text{out}}(t) &= -I_2(t) R \\[6pt]
V_{\text{out}}(t) &= -I_1(t) R \\[6pt]
V_{\text{out}}(t) &= -RC\,\frac{\mathrm{d}V_{\text{in}}(t)}{\mathrm{d}t}
\end{aligned}
$$

A triangular input has a constant positive slope on its rising half-cycle and a constant negative slope on its falling half-cycle, so the differentiator turns it into a square wave of amplitude $RC\,|\mathrm{d}V_{\text{in}}/\mathrm{d}t|$.

## 5. Practical limitations

The golden rules predict DC and low-frequency behaviour well, but real op-amps have four imperfections that matter in design, together with the finite open-loop gain behind rule 1.

![[ee_b4_gain_bandwidth.png|900]]

### Input bias currents

Golden rule 2 assumes no current enters $V_+$ or $V_-$. In reality the bases of the internal BJT input pair need small DC **input bias currents** to conduct. For the BJT-input 741 the specified bias current is below $500\ \text{nA}$ (typically about $80\ \text{nA}$), whereas FET-input op-amps draw only a few picoamperes. Signal currents in $10\ \text{k}\Omega$ to $100\ \text{k}\Omega$ feedback networks are tens to hundreds of microamperes, so a sub-microampere bias current introduces negligible error.

### Input offset voltage and offset null

Even with both inputs tied together ($V_+ = V_- = 0\ \text{V}$), small manufacturing asymmetries between the two halves of the internal differential amplifier leave the output at a non-zero DC voltage. This is equivalent to a small **input offset voltage** of $1$–$5\ \text{mV}$ between the inputs, multiplied by the closed-loop gain. On the 741 the offset is trimmed to zero with a $10\ \text{k}\Omega$ potentiometer whose outer ends connect to the offset-null pins (1 and 5) and whose wiper connects to $-V_{CC}$ (pin 4); the wiper is adjusted until $V_{\text{out}} = 0\ \text{V}$ for zero differential input.

### Slew rate

The internal compensation capacitor can only be charged by a finite internal current, which limits the maximum rate of change of the output voltage, the **slew rate** (usually quoted in $\text{V}\,\mu\text{s}^{-1}$):

$$
\text{SR} = \left|\frac{\mathrm{d}V_{\text{out}}}{\mathrm{d}t}\right|_{\max}
$$

A classic $\mu\text{A}741$ has a slew rate of only about $0.5\ \text{V}\,\mu\text{s}^{-1}$, while faster general-purpose op-amps reach about $10\ \text{V}\,\mu\text{s}^{-1}$. If a step or a high-frequency square wave demands a jump $\Delta V$ in less than $\Delta t_{\min} = \Delta V / \text{SR}$, the output cannot keep up and becomes a sloped ramp or triangle wave, as in panel (b) of the figure.

### Gain–bandwidth product

To stop high-frequency phase shifts from turning negative feedback into oscillation, a general-purpose op-amp has an internal low-pass compensation capacitor. It makes the open-loop gain $A_{\text{OL}}(f)$ fall inversely with frequency ($-20\ \text{dB}$ per decade, a factor of 10 drop in gain for every factor of 10 rise in frequency) above a low break frequency of roughly $5$–$10\ \text{Hz}$ (panel (a)). In this roll-off region the product of the closed-loop gain $|A_{\text{CL}}|$ and the highest frequency $f_{\max}$ at which that gain can be sustained is constant, and equals the **gain–bandwidth product** (GBP):

$$
\text{GBP} = |A_{\text{CL}}|\,f_{\max} = f_{\text{unity}}
$$

For the 741, $\text{GBP} \approx 1\ \text{MHz}$. At unity gain the bandwidth extends to $f_{\max} = 1\ \text{MHz}$; at $|A_{\text{CL}}| = 5$ it is $1\ \text{MHz}/5 = 200\ \text{kHz}$; and at $|A_{\text{CL}}| = 100$ ($40\ \text{dB}$) it drops to $1\ \text{MHz}/100 = 10\ \text{kHz}$.

### Finite open-loop gain

Golden rule 1 ($V_- = V_+$) is also an approximation, valid when $A_{\text{OL}}$ is much larger than the closed-loop gain. Since $V_+ - V_- = V_{\text{out}}/A_{\text{OL}}$, an op-amp with $A_{\text{OL}} = 2 \times 10^5$ needs a differential input of only $1/(2\times 10^5) = 0.0005\%$ of $V_{\text{out}}$, well below the $1\%$ tolerance of standard resistors.

## Worked examples

### Non-inverting amplifier between two potential dividers

A $4\ \text{V}$ DC source drives an input divider of two equal $20\ \text{k}\Omega$ resistors, whose midpoint $V_1$ connects directly to $V_+$. The op-amp is a non-inverting amplifier with feedback resistor $R_1 = 20\ \text{k}\Omega$ from its output node $V_2$ to $V_-$ and $R_2 = 10\ \text{k}\Omega$ from $V_-$ to ground. The output $V_2$ drives an output divider of two equal $20\ \text{k}\Omega$ resistors whose midpoint is $V_{\text{out}}$ (Mills §2.4 Example 2). The task is to find $V_1$, $V_2$ and $V_{\text{out}}$ for an ideal op-amp, then the error when $A_{\text{OL}} = 2 \times 10^5$.

The circuit splits into three cascaded blocks. Golden rule 2 says no current flows into $V_+$, so the input resistors form an unloaded divider across the $4\ \text{V}$ input:

$$
\begin{aligned}
V_1 &= V_{\text{in}} \frac{20\ \text{k}\Omega}{20\ \text{k}\Omega + 20\ \text{k}\Omega} \\[6pt]
&= 4\ \text{V} \times \frac{1}{2} = 2.0\ \text{V}
\end{aligned}
$$

The non-inverting stage with $V_1 = 2.0\ \text{V}$, $R_1 = 20\ \text{k}\Omega$ and $R_2 = 10\ \text{k}\Omega$ gives the op-amp output

$$
\begin{aligned}
V_2 &= \left(1 + \frac{R_1}{R_2}\right) V_1 \\[6pt]
&= \left(1 + \frac{20\ \text{k}\Omega}{10\ \text{k}\Omega}\right) (2.0\ \text{V}) \\[6pt]
&= (1 + 2)(2.0\ \text{V}) = 6.0\ \text{V}
\end{aligned}
$$

The op-amp output acts as a stiff voltage source holding $V_2$ at $6.0\ \text{V}$ across the output divider, so

$$
\begin{aligned}
V_{\text{out}} &= V_2 \frac{20\ \text{k}\Omega}{20\ \text{k}\Omega + 20\ \text{k}\Omega} \\[6pt]
&= \frac{6.0\ \text{V}}{2} = 3.0\ \text{V}
\end{aligned}
$$

> [!check] Finite open-loop gain ($A_{\text{OL}} = 2 \times 10^5$)
> Without golden rule 1, the inverting input sits at $V_- = \beta V_2$, with feedback fraction $\beta = R_2/(R_1 + R_2) = 10\ \text{k}\Omega / (20\ \text{k}\Omega + 10\ \text{k}\Omega) = 1/3$. Substituting into the exact open-loop relation $V_2 = A_{\text{OL}}(V_+ - V_-) = A_{\text{OL}}(V_1 - \beta V_2)$ gives
> $$V_2 = \frac{A_{\text{OL}}}{1 + A_{\text{OL}}\beta}\,V_1 = \frac{2 \times 10^5}{1 + (2 \times 10^5)(1/3)}\,(2.0\ \text{V}) = 5.999910\ \text{V}$$
> Then $V_- = \frac{1}{3}(5.999910\ \text{V}) = 1.999970\ \text{V}$, the differential input is $V_+ - V_- = 2.0\ \text{V} - 1.999970\ \text{V} = 30.0\ \mu\text{V}$, and $V_{\text{out}} = V_2/2 = 2.999955\ \text{V}$, a relative error of $1.5 \times 10^{-5}$ ($0.0015\%$) against the ideal $3.0\ \text{V}$.

### Cascaded summing amplifiers

In this two-stage circuit (Mills §2.4 Example 3), stage A is a summing amplifier with $V_1$ through $10\ \text{k}\Omega$, $V_3$ through $100\ \text{k}\Omega$ and a $50\ \text{k}\Omega$ feedback resistor, producing an intermediate output $V'$. Stage B is a second summing amplifier fed by $V'$ through $20\ \text{k}\Omega$ and by $V_2$ through $10\ \text{k}\Omega$, with a $20\ \text{k}\Omega$ feedback resistor to $V_{\text{out}}$. The task is the transfer function $V_{\text{out}}(V_1, V_2, V_3)$ and its value for $V_1 = 1.2\ \text{V}$, $V_2 = 2.0\ \text{V}$ and $V_3 = -4.0\ \text{V}$.

Stage A has $R_{F,A} = 50\ \text{k}\Omega$, $R_{1,A} = 10\ \text{k}\Omega$ and $R_{3,A} = 100\ \text{k}\Omega$, so

$$
\begin{aligned}
V' &= -\left(\frac{R_{F,A}}{R_{1,A}} V_1 + \frac{R_{F,A}}{R_{3,A}} V_3\right) \\[6pt]
&= -\left(\frac{50\ \text{k}\Omega}{10\ \text{k}\Omega} V_1 + \frac{50\ \text{k}\Omega}{100\ \text{k}\Omega} V_3\right) \\[6pt]
&= -5 V_1 - 0.5 V_3
\end{aligned}
$$

Stage B has $R_{F,B} = 20\ \text{k}\Omega$, $R'_{B} = 20\ \text{k}\Omega$ for $V'$ and $R_{2,B} = 10\ \text{k}\Omega$ for $V_2$:

$$
\begin{aligned}
V_{\text{out}} &= -\left(\frac{20\ \text{k}\Omega}{20\ \text{k}\Omega} V' + \frac{20\ \text{k}\Omega}{10\ \text{k}\Omega} V_2\right) \\[6pt]
&= -\left(1 \cdot (-5 V_1 - 0.5 V_3) + 2 V_2\right) \\[6pt]
&= 5 V_1 - 2 V_2 + 0.5 V_3
\end{aligned}
$$

$V_1$ and $V_3$ pass through two inverting stages and come out with positive signs, whereas $V_2$ passes through stage B only and comes out inverted. For $V_1 = 1.2\ \text{V}$, $V_2 = 2.0\ \text{V}$ and $V_3 = -4.0\ \text{V}$:

$$
\begin{aligned}
V' &= -5(1.2\ \text{V}) - 0.5(-4.0\ \text{V}) = -6.0\ \text{V} + 2.0\ \text{V} = -4.0\ \text{V} \\[6pt]
V_{\text{out}} &= -\left(\frac{20\ \text{k}\Omega}{20\ \text{k}\Omega}(-4.0\ \text{V}) + \frac{20\ \text{k}\Omega}{10\ \text{k}\Omega}(2.0\ \text{V})\right) = -(-4.0\ \text{V} + 4.0\ \text{V}) = 0.0\ \text{V}
\end{aligned}
$$

> [!check] Direct substitution
> Substituting the same inputs into $V_{\text{out}} = 5 V_1 - 2 V_2 + 0.5 V_3$ gives $5(1.2\ \text{V}) - 2(2.0\ \text{V}) + 0.5(-4.0\ \text{V}) = 6.0\ \text{V} - 4.0\ \text{V} - 2.0\ \text{V} = 0.0\ \text{V}$. At the stage B summing junction (virtual earth), the current arriving from $V'$ is $(-4.0\ \text{V})/(20\ \text{k}\Omega) = -0.20\ \text{mA}$ and the current from $V_2$ is $(+2.0\ \text{V})/(10\ \text{k}\Omega) = +0.20\ \text{mA}$; they cancel, so $I_F = 0\ \text{mA}$ and $V_{\text{out}} = 0\ \text{V}$.

### Three-op-amp summing circuit (Tutorial 4 Q1)

In Tutorial Sheet 4 Q1, $V_1$ drives the non-inverting terminal of an upper op-amp (feedback resistor $100\ \text{k}\Omega$, resistor to ground $25\ \text{k}\Omega$), while $V_2$ drives the inverting terminal of a lower op-amp through $25\ \text{k}\Omega$ with a $100\ \text{k}\Omega$ feedback resistor and a grounded non-inverting terminal. Their outputs $V_A$ and $V_B$ each feed a third, summing op-amp through $50\ \text{k}\Omega$, with a $150\ \text{k}\Omega$ feedback resistor to $V_{\text{out}}$. The task is the transfer function relating $V_{\text{out}}$ to $V_1$ and $V_2$, and the largest $V_2$ before the output saturates at $+14\ \text{V}$ when $V_1 = 0.20\ \text{V}$.

The upper stage is a non-inverting amplifier on $V_1$ with $R_{\text{feedback}} = 100\ \text{k}\Omega$ and $R_{\text{ground}} = 25\ \text{k}\Omega$:

$$
\begin{aligned}
V_A &= \left(1 + \frac{100\ \text{k}\Omega}{25\ \text{k}\Omega}\right) V_1 \\[6pt]
&= (1 + 4) V_1 = 5 V_1
\end{aligned}
$$

The lower stage is an inverting amplifier on $V_2$ with $R_{\text{in}} = 25\ \text{k}\Omega$ and $R_{\text{feedback}} = 100\ \text{k}\Omega$:

$$
\begin{aligned}
V_B &= -\frac{100\ \text{k}\Omega}{25\ \text{k}\Omega} V_2 \\[6pt]
&= -4 V_2
\end{aligned}
$$

Both outputs drive the third op-amp's virtual earth through equal resistors $R_S = 50\ \text{k}\Omega$, with $R_F = 150\ \text{k}\Omega$:

$$
\begin{aligned}
V_{\text{out}} &= -\left(\frac{150\ \text{k}\Omega}{50\ \text{k}\Omega} V_A + \frac{150\ \text{k}\Omega}{50\ \text{k}\Omega} V_B\right) \\[6pt]
&= -3(V_A + V_B) \\[6pt]
&= -3(5 V_1 - 4 V_2) \\[6pt]
&= 12 V_2 - 15 V_1
\end{aligned}
$$

With $V_1 = 0.20\ \text{V}$, setting $V_{\text{out}} = +V_{\max} = +14\ \text{V}$ gives the saturation limit:

$$
\begin{aligned}
12 V_{2,\max} - 15(0.20\ \text{V}) &= 14\ \text{V} \\[6pt]
12 V_{2,\max} &= 14\ \text{V} + 3.0\ \text{V} = 17.0\ \text{V} \\[6pt]
V_{2,\max} &= \frac{17.0\ \text{V}}{12} = 1.42\ \text{V}\quad(3\text{ s.f.})
\end{aligned}
$$

> [!check] Intermediate-stage rail check
> At $V_1 = 0.20\ \text{V}$ and $V_2 = 1.42\ \text{V}$, the intermediate outputs are $V_A = 5(0.20\ \text{V}) = +1.00\ \text{V}$ and $V_B = -4(1.42\ \text{V}) = -5.67\ \text{V}$. Both lie well inside $\pm 14\ \text{V}$, so the third stage is the first op-amp in the chain to reach positive saturation.

### T-network gain, bandwidth and slew-rate limit

An inverting T-network amplifier ([[#Inverting amplifier with a T-network feedback loop]], Tutorial Sheet 4 Q5) uses a 741 ($A_{\text{OL}} = 2 \times 10^5$, $\text{GBP} = 1\ \text{MHz}$, $\text{SR} = 0.5\ \text{V}\,\mu\text{s}^{-1}$) with $R_1 = 10\ \text{k}\Omega$, $R_2 = 10\ \text{k}\Omega$, $R_3 = 1.0\ \text{k}\Omega$ and $R_4 = 100\ \text{k}\Omega$. Part (a) asks for the ideal closed-loop gain and the single feedback resistance $R_{F,\text{eq}}$ a standard inverting amplifier with $R_1 = 10\ \text{k}\Omega$ would need for the same gain. Part (b) asks for the output at $V_{\text{in}} = 50\ \text{mV}$ DC, the maximum operating frequency at this gain, and the minimum time for the output to swing from $-5\ \text{V}$ to $+5\ \text{V}$.

For part (a), substituting the resistor values into the T-network gain formula:

$$
\begin{aligned}
A_{\text{CL}} = \frac{V_{\text{out}}}{V_{\text{in}}} &= -\frac{R_2}{R_1}\left(1 + \frac{R_4}{R_2} + \frac{R_4}{R_3}\right) \\[6pt]
&= -\frac{10\ \text{k}\Omega}{10\ \text{k}\Omega}\left(1 + \frac{100\ \text{k}\Omega}{10\ \text{k}\Omega} + \frac{100\ \text{k}\Omega}{1.0\ \text{k}\Omega}\right) \\[6pt]
&= -1 \times (1 + 10 + 100) = -111
\end{aligned}
$$

A conventional two-resistor inverting amplifier with $R_1 = 10\ \text{k}\Omega$ would need

$$
R_{F,\text{eq}} = |A_{\text{CL}}|\,R_1 = 111 \times 10\ \text{k}\Omega = 1.11\ \text{M}\Omega
$$

whereas the T-network uses no resistor larger than $100\ \text{k}\Omega$.

For part (b), a DC input $V_{\text{in}} = 50\ \text{mV} = 0.050\ \text{V}$ gives the ideal output

$$
V_{\text{out}} = A_{\text{CL}} V_{\text{in}} = -111 \times 0.050\ \text{V} = -5.55\ \text{V}
$$

With $\text{GBP} = 1\ \text{MHz} = 10^6\ \text{Hz}$, the maximum frequency at $|A_{\text{CL}}| = 111$ is

$$
f_{\max} = \frac{\text{GBP}}{|A_{\text{CL}}|} = \frac{1.0 \times 10^6\ \text{Hz}}{111} = 9.01 \times 10^3\ \text{Hz} = 9.01\ \text{kHz}\quad(3\text{ s.f.})
$$

For a step of $\Delta V_{\text{out}} = (+5\ \text{V}) - (-5\ \text{V}) = 10\ \text{V}$, the slew rate $\text{SR} = 0.5\ \text{V}\,\mu\text{s}^{-1}$ sets the minimum transition time

$$
\Delta t_{\min} = \frac{\Delta V_{\text{out}}}{\text{SR}} = \frac{10\ \text{V}}{0.5\ \text{V}\,\mu\text{s}^{-1}} = 20\ \mu\text{s}
$$

> [!check] Finite-gain nodal solve for the T-network
> Solving the exact KCL equations at nodes A and X in Python with $V_{\text{out}} = -A_{\text{OL}} V_A$ ($A_{\text{OL}} = 2 \times 10^5$) and $V_{\text{in}} = 50\ \text{mV}$ gives $V_A = +27.7\ \mu\text{V}$, $V_X = -49.95\ \text{mV}$ and $V_{\text{out}} = -5.544\ \text{V}$, within $0.11\%$ of the ideal $-5.550\ \text{V}$. The numbers also show how the T-network multiplies the gain: node X sits near $-50\ \text{mV}$, so $R_3 = 1\ \text{k}\Omega$ draws $(49.95\ \text{mV})/(1\ \text{k}\Omega) \approx 50\ \mu\text{A}$ from ground, and $R_4 = 100\ \text{k}\Omega$ must carry $I_2 + I_3 \approx 5\ \mu\text{A} + 50\ \mu\text{A} = 55\ \mu\text{A}$, dropping $55\ \mu\text{A} \times 100\ \text{k}\Omega = 5.50\ \text{V}$ between X and $V_{\text{out}}$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Next: [[FEEG1004 B5 - Combinational Logic - Boolean Algebra and Karnaugh Maps]]
- Concepts: [[Op-Amp Comparator]] · [[Op-Amp Golden Rules]] · [[Standard Op-Amp Configurations]] · [[Potential Divider]]
- Worked problems: [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions]]

## Sources

- J. Mills, *Diodes, Transistors, Op-amps and Digital Electronics* (`S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`), Section 2, *Operational Amplifiers*, pp. 39–63: §2.1 introduction, 741 pinout, open-loop gain and saturation window (pp. 39–42); §2.2 comparator applications (sine-to-square converter, variable pulse-width generator, NTC bridge high-temperature warning circuit) (pp. 42–45); §2.3 negative feedback, golden rules, and the inverting, non-inverting, follower, summing, differential, integrator and differentiator derivations (pp. 46–56); §2.4 worked examples 1–3 (pp. 56–60); §2.5 practical considerations: bias currents, offset null, slew rate and frequency response (pp. 60–63).
- `S1-W09-EL3 Op-Amps - Interactive.pdf`: open-loop saturation, positive and negative feedback quizzes, inverting amplifier with non-zero $V_+$, and multi-stage design. `S1-W15-EL5 Digital Logic 2 Sequential - Interactive.pdf`, slides 11–12: capacitor integral relation and op-amp integrator derivation.
- `FEEG1004 Lecture 3a.txt` (ll. 1–169: 741 terminals and DIL package, open-loop gain $2\times 10^5$, $\pm 70\ \mu\text{V}$ linear range, comparators, PWM and the Wheatstone thermistor warning circuit); `FEEG1004 Lecture 3b.txt` (ll. 1–205: negative feedback, golden rules, virtual earth and the seven standard closed-loop configurations); `FEEG1004 Lecture 3c.txt` (ll. 1–215: worked examples and practical op-amp limits).
- `Tutorial Sheet 04 - Electronics B - Operational Amplifiers.pdf`, Q1 and Q5.

## Self-study tasks

### Core

- [ ] Break down the divider–amplifier–divider circuit driven by $4\ \text{V}$ and show that $V_1 = 2\ \text{V}$, $V_2 = 6\ \text{V}$ and $V_{\text{out}} = 3\ \text{V}$ (Mills §2.4 Example 2, pp. 57–58; Lecture 3c, ll. 29–68). → [[#Non-inverting amplifier between two potential dividers]]
- [ ] Obtain the transfer function $V_{\text{out}} = 5 V_1 - 2 V_2 + 0.5 V_3$ for the two-stage summing circuit (Mills §2.4 Example 3, pp. 59–60; Lecture 3c, ll. 69–114). → [[#Cascaded summing amplifiers]]
- [ ] Determine the transfer function relating $V_{\text{out}}$ to $V_1$ and $V_2$ for the three-op-amp circuit (Tutorial Sheet 4 Q1). → [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q1: Circuit transfer function of the three-stage chain|Tutorial 4 Q1]] · [[#Three-op-amp summing circuit (Tutorial 4 Q1)]]
- [ ] Using the golden rules, prove that the T-feedback network has $V_{\text{out}}/V_{\text{in}} = -(R_2/R_1)(1 + R_4/R_2 + R_4/R_3)$ (Tutorial Sheet 4 Q5). → [[FEEG1004 Tutorial 4 - Operational Amplifiers and Logic Solutions#Q5: The T feedback network|Tutorial 4 Q5]] · [[#Inverting amplifier with a T-network feedback loop]]
- [ ] Starting from $Q = CV$ and the golden rules, derive $V_{\text{out}}(t) = -\frac{1}{RC}\int V_{\text{in}}(t)\,\mathrm{d}t$ (W15-EL5 interactive, slides 11–12; Lecture 3b, ll. 152–181). → [[#Op-amp integrator]]

### Further practice

- [ ] A non-inverting op-amp has $V_{\text{in}} = 3\ \text{V}$, feedback resistor $R_1 = 30\ \text{k}\Omega$ and grounded resistor $R_2 = 15\ \text{k}\Omega$. Derive the transfer function from the golden rules and verify that $V_{\text{out}} = 9\ \text{V}$ (Mills §2.4 Example 1, p. 57; Lecture 3c, ll. 9–28). → [[#Non-inverting amplifier]]
- [ ] An inverting op-amp has $R_{\text{in}} = 1\ \text{k}\Omega$, $R_F = 2\ \text{k}\Omega$, $V_{\text{in}} = 4\ \text{V}$ and $V_+ = +2\ \text{V}$. Use golden rule 1 ($V_- = +2\ \text{V}$) and KCL at $V_-$ to show that $I_{\text{in}} = (4 - 2)\ \text{V}/(1\ \text{k}\Omega) = 2\ \text{mA}$ and $V_{\text{out}} = 2\ \text{V} - (2\ \text{mA})(2\ \text{k}\Omega) = -2\ \text{V}$ (W09-EL3 interactive, slide 10). → [[#Inverting amplifier]]
- [ ] Choose the four input resistors $R_3, R_2, R_1, R_0$ of a summing amplifier with $R_F = 10\ \text{k}\Omega$ and logic levels $0\ \text{V}$ and $+5\ \text{V}$ so that each least-significant-bit step gives $-0.5\ \text{V}$ at $V_{\text{out}}$ (DAC idea from Mills §2.3.2.4; the values are suggested, not lecturer-set). → [[#Summing amplifier]]

## Transcript and slide slips

### Meaning of the CC subscript

> [!warning] `V_CC` described as standing for "common collector"
> Where: [[#Terminals, packaging and open-loop gain]]
> In `FEEG1004 Lecture 3a.txt` (ll. 53–55), the subscript in $+V_{CC}$ and $-V_{CC}$ is explained as meaning "common collector". As the printed notes (§2.1, p. 39) state, the repeated letter C comes from "collector": the positive rail powers the collector side of the internal BJT circuitry, just as $V_{EE}$ denotes the emitter supply and $V_{DD}$/$V_{SS}$ the FET drain and source supplies. It does not mean the op-amp is a common-collector amplifier.

### Typical slew rate of the 741

> [!warning] $10\ \text{V}\,\mu\text{s}^{-1}$ quoted after 741 parameters
> Where: [[#Slew rate]]
> Both `FEEG1004 Lecture 3c.txt` (ll. 151–156) and Mills (§2.5(iii), p. 61) move from the 741's bias current and offset-null pins to slew rate and quote $10\ \text{V}\,\mu\text{s}^{-1}$ as "a typical value". That figure is typical of JFET-input or high-speed op-amps (such as the TL081 or LF351); the standard bipolar $\mu\text{A}741$ used throughout the chapter has a datasheet slew rate of only $0.5\ \text{V}\,\mu\text{s}^{-1}$.
