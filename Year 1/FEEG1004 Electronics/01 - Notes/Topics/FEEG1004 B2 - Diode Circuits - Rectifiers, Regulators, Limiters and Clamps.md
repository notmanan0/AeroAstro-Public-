---
title: "FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 2
tags: [feeg1004, electronics, diode, rectifier, smoothing, ripple, zener, regulator, limiter, clamp]
aliases: ["Rectifiers", "Smoothing capacitor", "Zener regulator", "Clipper circuits", "Diode clamp"]
date: 2026-09-27
status: lectured
coverage: "JKA 1b Diodes as rectifiers ll. 1–181; JKA 1c Zener diodes and voltage limiters ll. 1–104; L6 (13 Nov 2024) ll. 126–548; diode clamps written-ahead from Mills §1.5.6."
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 B1 - Semiconductors and Diodes]]", "[[FEEG1004 A4 - Capacitors]]"]
next_topics: ["[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
key_concepts: ["[[Rectification and Smoothing]]", "[[Zener Diode Regulator]]", "[[Diode Limiters and Clamps]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]"]
sources:
  - "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"
  - "02 - Sources/S1 Electronics/S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 1b.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 1c.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 6.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 03 - Electronics A - Diodes & Transistors.pdf"
---

# FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps

> [!abstract] Summary
> Diodes steer, regulate, clip and shift waveforms by switching between conducting and blocking states. Half-wave and full-wave bridge rectifiers turn alternating current into unidirectional pulses, losing $0.7\ \mathrm V$ or $2\times 0.7\ \mathrm V=1.4\ \mathrm V$ across the conducting silicon diodes, and a parallel smoothing capacitor limits the droop between peaks to $\Delta V=I_{\mathrm{DC}}/(fC)$ for half-wave or $\Delta V=I_{\mathrm{DC}}/(2fC)$ for full-wave rectification. A reverse-biased Zener diode across the load holds the output at $V_Z$ provided the series resistor $R_S=(V_{\mathrm{in}}-V_Z)/(I_L+I_Z)$ supplies enough current to keep it in breakdown. Shunt diode limiters clip excursions beyond a threshold, and series-capacitor clamps shift the DC level of an AC waveform without changing its peak-to-peak swing.

> [!summary]- Exam use: quick path
> - **Use it when:** designing or analysing half-wave and full-wave bridge rectifiers, sizing a smoothing capacitor for a specified ripple voltage, designing a Zener shunt regulator over a load-current range, or finding the transfer characteristic and output waveform of a limiter or clamp circuit.
> - **Assumptions:** constant-drop silicon diode model ($V_{\mathrm{on}}=0.7\ \mathrm V$) unless the problem states the zero-drop ideal model ($V_{\mathrm{on}}=0\ \mathrm V$); small ripple ($\Delta V\ll V_p$, equivalently $R_LC\gg\Delta t$) for the linear capacitor-discharge approximation; constant reverse voltage $V_Z$ across a Zener diode while reverse breakdown current satisfies $I_Z\ge I_{Z,\min}$; zero external current drawn from the output node ($I_{\mathrm{out}}=0$) when plotting unloaded limiter and clamp transfer characteristics.
> - **Method:** 1. Count how many diodes conduct in series during each half-cycle ($1$ for half-wave, $2$ for a four-diode bridge) and subtract their forward drops from the input peak to find $V_{p,\mathrm{out}}$. 2. Set the discharge interval to $\Delta t=1/f$ (half-wave) or $\Delta t=1/(2f)$ (full-wave), relate ripple to average load current by $\Delta V=I_{\mathrm{DC}}\Delta t/C$, and centre the average output at $V_{\mathrm{avg}}=V_{p,\mathrm{out}}-\Delta V/2$. 3. For a Zener regulator, apply KCL ($I_S=I_Z+I_L$) and Ohm's law across $R_S$ to check that $I_Z$ stays above $I_{Z,\min}$ at maximum load and within the Zener power rating at zero load. 4. For a limiter or clamp, test input voltage ranges to find which shunt branch turns on first and apply KVL or voltage division in each region.
> - **Common mistakes:** subtracting only one $0.7\ \mathrm V$ diode drop instead of $2\times 0.7\ \mathrm V=1.4\ \mathrm V$ in a four-diode bridge rectifier, or using $f$ instead of $2f$ for full-wave ripple; equating the target average DC output voltage $V_{\mathrm{avg}}$ to the rectified peak $V_{p,\mathrm{out}}$ instead of adding $\Delta V/2$.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q6: Full-wave rectifier with smoothing: 10 V average, 0.2 V ripple, 5 mA, 50 Hz|Tutorial 3 Q6]]

Electronic instruments and microcontrollers need a steady DC supply rail, whereas mains distribution delivers a sinusoidal AC voltage. After a step-down transformer lowers the mains amplitude to a safe level, diode circuits do the rest of the conversion. A rectifier turns the bidirectional AC into unidirectional pulses. A reservoir capacitor stores charge at each peak and supplies the load between peaks, leaving only a small sawtooth ripple, and a Zener regulator absorbs the remaining supply variation to hold the output at a fixed DC voltage.

The same one-way switching shapes signals in measurement and protection circuits. A diode placed in shunt across an output line makes a voltage limiter (clipper). While the diode stays reverse-biased it draws no current and the output follows the input, but once the input swings past the diode's turn-on threshold the diode conducts and holds the output at a fixed ceiling or floor, with the series resistor absorbing the excess voltage. Replacing the series resistor with a capacitor makes a clamp (DC restorer). The capacitor charges on the first peak that forward-biases the shunt diode and afterwards cannot discharge, because the diode blocks reverse current, so the whole AC waveform is shifted up or down by a constant DC offset.

## 1. Half-wave and full-wave bridge rectification

A **rectifier** converts an alternating input voltage $v_{\mathrm{in}}(t)=V_{p,\mathrm{in}}\sin(2\pi ft)$ of period $T=1/f$ into a unidirectional load voltage $v_L(t)$ across a resistive load $R_L$.

### Half-wave rectifier

The simplest rectifier places a single diode in series with the AC source and the load resistor $R_L$. The $0.7\ \mathrm V$ constant-drop silicon model is used. During the positive half-cycle, once $v_{\mathrm{in}}(t)>0.7\ \mathrm V$, the diode is forward-biased and conducts, and KVL around the single loop makes the load voltage follow the input minus one diode drop:

$$
\begin{aligned}
v_{\mathrm{in}}(t)-V_{\mathrm{on}}-v_L(t)&=0,\\
v_L(t)&=v_{\mathrm{in}}(t)-0.7\ \mathrm V\qquad (v_{\mathrm{in}}(t)>0.7\ \mathrm V).
\end{aligned}
$$

The peak output voltage across the load is therefore

$$
V_{p,\mathrm{out}}=V_{p,\mathrm{in}}-0.7\ \mathrm V.
$$

Whenever $v_{\mathrm{in}}(t)\le 0.7\ \mathrm V$, which includes the whole negative half-cycle, the diode blocks. The circuit current is then $i(t)=0$ and Ohm's law gives

$$
v_L(t)=i(t)R_L=0\ \mathrm V.
$$

With the diode blocking and $v_L(t)=0\ \mathrm V$, KVL places the entire input voltage across the diode terminals:

$$
v_D(t)=v_{\mathrm{in}}(t)-v_L(t)=v_{\mathrm{in}}(t).
$$

At the negative peak, the reverse voltage across the diode reaches $V_{p,\mathrm{in}}$ (its **peak inverse voltage**), so the diode must have a reverse breakdown rating $V_{\mathrm{BD}}>V_{p,\mathrm{in}}$. The negative half-cycles are discarded completely, so the output pulses repeat at the input frequency $f$ (period $T=1/f$) and the output sits at $0\ \mathrm V$ for half of each cycle.

### Full-wave bridge rectifier

A **full-wave bridge rectifier** arranges four diodes in a diamond between the two AC source terminals and the two load terminals, so that both half-cycles drive current through $R_L$ in the same direction.

On the positive half-cycle ($v_{\mathrm{in}}>1.4\ \mathrm V$, top AC terminal positive), conventional current leaves the top AC terminal, passes forward through the upper-right diode to the top (positive) terminal of $R_L$, flows down through $R_L$ and returns to the bottom AC terminal through the lower-left diode. The other two diodes are reverse-biased and block. On the negative half-cycle ($v_{\mathrm{in}}<-1.4\ \mathrm V$, bottom AC terminal positive), current leaves the bottom AC terminal, passes forward through the lower-right diode to the same top terminal of $R_L$, flows down through $R_L$ in the same direction as before, and returns to the top AC terminal through the upper-left diode.

In either half-cycle the load current passes through two conducting diodes in series, so KVL around the conducting path subtracts two forward drops ($2V_{\mathrm{on}}$) from the input magnitude:

$$
\begin{aligned}
|v_{\mathrm{in}}(t)|-2V_{\mathrm{on}}-v_L(t)&=0,\\
v_L(t)&=|v_{\mathrm{in}}(t)|-2(0.7\ \mathrm V)=|v_{\mathrm{in}}(t)|-1.4\ \mathrm V\qquad (|v_{\mathrm{in}}(t)|>1.4\ \mathrm V).
\end{aligned}
$$

The peak load voltage of a silicon bridge rectifier is therefore

$$
\boxed{V_{p,\mathrm{out}}=V_{p,\mathrm{in}}-1.4\ \mathrm V}.
$$

Every negative half-cycle is inverted into an identical positive pulse across $R_L$, so two output pulses occur in each input period $T=1/f$. The ripple period of a full-wave rectifier is halved to

$$
\Delta t=\frac{T}{2}=\frac{1}{2f},
$$

and the fundamental ripple frequency is doubled to $f_{\mathrm{ripple}}=2f$ ($100\ \mathrm{Hz}$ for a $50\ \mathrm{Hz}$ mains input).

## 2. Smoothing capacitor and ripple derivation

Even after full-wave rectification, $v_L(t)$ drops to zero twice per AC cycle. A **smoothing capacitor** $C$ connected in parallel with $R_L$ turns these pulses into a nearly steady DC supply.

On each rising peak of the rectified waveform the conducting bridge diodes have very low forward resistance, so the capacitor charges rapidly to the peak output voltage $V_p=V_{p,\mathrm{out}}$. As the rectified source voltage falls past its peak, the charge stored on $C$ holds $v_L(t)$ up, and the bridge diodes become reverse-biased and block any discharge back into the AC source. The capacitor can therefore discharge only through $R_L$, with time constant $\tau=R_LC$, until the next rectified half-cycle rises above the drooping capacitor voltage and recharges $C$ to $V_p$. The resulting periodic peak-to-trough variation $\Delta V$ is the **ripple voltage**.

![[ee_b2_rectifiers.png|900]]

### Ripple and average output voltage

Assume the ripple is small compared with the peak voltage, $\Delta V\ll V_p$, which holds when $R_LC\gg\Delta t$. Under this small-ripple approximation:

1. The load current $i_{\mathrm{DC}}$ drawn by $R_L$ stays nearly constant during the discharge interval.
2. The charging interval near each peak is brief compared with the interval between peaks, so the discharge time $\Delta t$ is approximately the full period between successive rectified peaks.

Start from the charge–voltage relation of a capacitor:

$$
Q=CV.
$$

Differentiate with respect to time $t$ at constant capacitance $C$:

$$
\frac{dQ}{dt}=C\frac{dV}{dt}.
$$

The rate of charge loss from the capacitor during discharge equals the nearly constant DC load current $i_{\mathrm{DC}}$:

$$
i_{\mathrm{DC}}=C\frac{dV}{dt}.
$$

Under the linear-discharge (triangular-ripple) approximation, replace $dV/dt$ by the ratio of the peak-to-peak droop $\Delta V$ to the discharge time $\Delta t$:

$$
i_{\mathrm{DC}}=C\frac{\Delta V}{\Delta t}.
$$

For a full-wave rectifier, peaks arrive every half-period of the supply, so $\Delta t=T/2$. With $T=1/f$, substitute $\Delta t=1/(2f)$:

$$
\begin{aligned}
i_{\mathrm{DC}}&=C\frac{\Delta V}{T/2},\\
i_{\mathrm{DC}}&=\frac{2C\,\Delta V}{T},\\
i_{\mathrm{DC}}&=2fC\,\Delta V.
\end{aligned}
$$

Solving for the capacitance needed to meet a specified ripple, or for the ripple produced by a given capacitor, gives the full-wave smoothing relations:

$$
\boxed{C=\frac{i_{\mathrm{DC}}}{2f\,\Delta V}},\qquad \boxed{\Delta V=\frac{i_{\mathrm{DC}}}{2fC}}\qquad (\text{full-wave, }\Delta t=\tfrac{1}{2f}).
$$

For a half-wave rectifier, peaks arrive only once per period, so the discharge interval is twice as long, $\Delta t=T=1/f$. Substituting $\Delta t=1/f$ into $i_{\mathrm{DC}}=C\,\Delta V/\Delta t$ gives

$$
\begin{aligned}
i_{\mathrm{DC}}&=fC\,\Delta V,\\
\boxed{C=\frac{i_{\mathrm{DC}}}{f\,\Delta V}},\qquad \boxed{\Delta V=\frac{i_{\mathrm{DC}}}{fC}}\qquad (\text{half-wave, }\Delta t=\tfrac{1}{f}).
\end{aligned}
$$

A half-wave rectifier therefore needs twice the smoothing capacitance of a full-wave rectifier to achieve the same ripple at the same load current.

The triangular ripple oscillates symmetrically between its maximum $V_p$ and its minimum $V_p-\Delta V$, so the **average DC output voltage** $V_{\mathrm{average}}$ sits halfway down the swing, $\Delta V/2$ below the rectified peak:

$$
V_{\mathrm{average}}=V_p-\frac{\Delta V}{2}.
$$

Substituting the full-wave ripple $\Delta V=i_{\mathrm{DC}}/(2fC)$ gives

$$
\begin{aligned}
V_{\mathrm{average}}&=V_p-\frac{1}{2}\left(\frac{i_{\mathrm{DC}}}{2fC}\right),\\
\boxed{V_{\mathrm{average}}=V_p-\frac{i_{\mathrm{DC}}}{4fC}}\qquad (\text{full-wave}).
\end{aligned}
$$

When a power-supply specification states a target DC voltage $V_{\mathrm{average}}$ with ripple $\Delta V$, the output varies over $V_{\mathrm{average}}\pm\Delta V/2$. The rectified peak at the capacitor must then be $V_p=V_{\mathrm{average}}+\Delta V/2$, and the AC source peak before a four-diode bridge must be $V_{p,\mathrm{in}}=V_p+1.4\ \mathrm V$.

## 3. Zener diode voltage regulator

A **Zener diode** is a heavily doped p-n junction made to enter reverse breakdown at a tightly controlled reverse voltage $V_Z$ (commercially $1.8\ \mathrm V$ to $200\ \mathrm V$). Its reverse characteristic in breakdown is nearly vertical, so the voltage across a reverse-conducting Zener stays close to $V_Z$ while its reverse current $I_Z$ varies over a wide range.

To regulate the voltage across a variable load $R_L$, the Zener is connected in reverse bias (cathode to the positive rail, anode to $0\ \mathrm V$) in parallel with $R_L$, and the pair is fed from the unregulated DC supply $V_{\mathrm{in}}$ through a series current-limiting resistor $R_S$.

![[ee_b2_zener_regulator.png|900]]

### Series resistor and load limits

Provided $V_{\mathrm{in}}>V_Z$ and the Zener stays in breakdown, the parallel connection holds the voltage across both the diode and the load at

$$
V_{\mathrm{out}}=V_Z.
$$

Staying in breakdown means $I_Z\ge I_{Z,\min}$, where $I_{Z,\min}\approx 5\ \mathrm{mA}$ is a typical minimum knee current for regulation, or $I_{Z,\min}=0$ in the ideal vertical-breakdown approximation. KVL around the input loop containing $V_{\mathrm{in}}$, $R_S$ and the regulated node gives

$$
\begin{aligned}
V_{\mathrm{in}}-V_{R_S}-V_Z&=0,\\
V_{R_S}&=V_{\mathrm{in}}-V_Z.
\end{aligned}
$$

By Ohm's law, the total current $I_S$ through $R_S$ is fixed by $V_{\mathrm{in}}$ and $V_Z$:

$$
I_S=\frac{V_{\mathrm{in}}-V_Z}{R_S}.
$$

KCL at the output node splits this current between the reverse Zener current $I_Z$ and the load current $I_{\mathrm{load}}=V_Z/R_L$:

$$
\begin{aligned}
I_S&=I_Z+I_{\mathrm{load}},\\
\frac{V_{\mathrm{in}}-V_Z}{R_S}&=I_Z+I_{\mathrm{load}}.
\end{aligned}
$$

Solving for the series resistance that supplies a specified load current while maintaining a required Zener current gives

$$
\boxed{R_S=\frac{V_{\mathrm{in}}-V_Z}{I_{\mathrm{load}}+I_Z}}.
$$

Once $R_S$ is fixed, rearranging the KCL equation for $I_Z$ shows how the shunt regulator compensates for load changes:

$$
\boxed{I_Z=\frac{V_{\mathrm{in}}-V_Z}{R_S}-I_{\mathrm{load}}}.
$$

Two limiting cases bound every Zener regulator design. At minimum load ($I_{\mathrm{load}}=0$, open-circuit output), the whole resistor current flows through the Zener:

$$
I_{Z,\max}=I_S=\frac{V_{\mathrm{in}}-V_Z}{R_S}.
$$

This no-load condition gives the **maximum Zener power dissipation**, $P_{Z,\max}=V_ZI_{Z,\max}$, which must not exceed the manufacturer's rating. Even with no load connected, the regulator continuously consumes $P_{\mathrm{total}}=V_{\mathrm{in}}I_S=V_{R_S}I_S+V_ZI_S$.

As the load draws more current, less flows through the Zener while $I_S$ stays constant. Regulation fails when $I_Z$ falls below $I_{Z,\min}$ (or reaches $0\ \mathrm{mA}$ in the ideal model), which sets the maximum load current:

$$
I_{\mathrm{load},\max}=\frac{V_{\mathrm{in}}-V_Z}{R_S}-I_{Z,\min}.
$$

If the load tries to draw more than $I_{\mathrm{load},\max}$, the drop $I_{\mathrm{load}}R_S$ across the series resistor exceeds $V_{\mathrm{in}}-V_Z$ and pulls $V_{\mathrm{out}}$ below $V_Z$. The Zener then drops out of breakdown ($I_Z=0$), and the output falls with load current as an unregulated potential divider, $V_{\mathrm{out}}=V_{\mathrm{in}}-I_{\mathrm{load}}R_S=V_{\mathrm{in}}R_L/(R_S+R_L)$.

## 4. Diode limiter (clipper) circuits

A **limiter** (or **clipper**) protects sensitive downstream inputs, such as operational amplifiers or analogue-to-digital converters, by clipping any part of the input waveform $v_{\mathrm{in}}$ that crosses a set threshold. Each limiter feeds the output node $v_{\mathrm{out}}$ through a series resistor $R$ and connects one or more diode branches in shunt between $v_{\mathrm{out}}$ and the $0\ \mathrm V$ rail. The transfer characteristic ($v_{\mathrm{out}}$ against $v_{\mathrm{in}}$) is plotted with no external current drawn from the output terminal ($I_{\mathrm{out}}=0$).

![[ee_b2_limiters.png|900]]

With $I_{\mathrm{out}}=0$, KVL and Ohm's law across $R$ give

$$
v_{\mathrm{out}}=v_{\mathrm{in}}-I_RR,
$$

where $I_R$ is the current flowing down into the shunt diode branch or branches. The four standard configurations below use the $0.7\ \mathrm V$ constant-drop model.

In panel (a), a single shunt diode has its anode at $0\ \mathrm V$ and its cathode at $v_{\mathrm{out}}$, so its forward voltage is $V_D=0-v_{\mathrm{out}}=-v_{\mathrm{out}}$. Whenever $v_{\mathrm{in}}>-0.7\ \mathrm V$ the diode is reverse-biased or below turn-on ($V_D<0.7\ \mathrm V$). Then $I_R=0$, nothing is dropped across $R$, and the output copies the input with unity slope ($v_{\mathrm{out}}=v_{\mathrm{in}}$). Once $v_{\mathrm{in}}\le -0.7\ \mathrm V$, the diode turns ON and holds its cathode $0.7\ \mathrm V$ below its grounded anode, so $v_{\mathrm{out}}=-0.7\ \mathrm V$ while $R$ absorbs the excess negative voltage with current $I_D=(-0.7\ \mathrm V-v_{\mathrm{in}})/R$. This circuit clips negative excursions.

Panel (b) adds a second shunt diode in the opposite direction (anode at $v_{\mathrm{out}}$, cathode at $0\ \mathrm V$), forming an anti-parallel pair. The new diode clips positive excursions above $+0.7\ \mathrm V$ in the same way that the first clips negative excursions below $-0.7\ \mathrm V$. For $-0.7\ \mathrm V\le v_{\mathrm{in}}\le +0.7\ \mathrm V$ both diodes are OFF ($I_R=0$) and $v_{\mathrm{out}}=v_{\mathrm{in}}$. Outside that window one diode conducts with current $(|v_{\mathrm{in}}|-0.7\ \mathrm V)/R$, bounding the output to

$$
-0.7\ \mathrm V\le v_{\mathrm{out}}\le +0.7\ \mathrm V.
$$

Panel (c) is a biased limiter: a downward-pointing diode in series with a DC bias battery $V_x$ (positive terminal upwards, low internal resistance). The battery raises the cathode potential to $V_x$, so for forward current to flow downwards the anode at $v_{\mathrm{out}}$ must exceed $V_x$ by $0.7\ \mathrm V$. The diode therefore stays OFF and $v_{\mathrm{out}}=v_{\mathrm{in}}$ for all $v_{\mathrm{in}}<V_x+0.7\ \mathrm V$. Once $v_{\mathrm{in}}\ge V_x+0.7\ \mathrm V$, the branch conducts with $I_R=(v_{\mathrm{in}}-(V_x+0.7\ \mathrm V))/R$ and holds the output at

$$
v_{\mathrm{out}}=V_x+0.7\ \mathrm V.
$$

Panel (d) is the soft limiter of Tutorial Sheet 3 Q3. A resistor inside the shunt diode branch softens the clipping slope instead of holding $v_{\mathrm{out}}$ flat, because once the diode turns ON the series resistor and the branch resistor form a potential divider. Its transfer characteristic is derived line by line in [[#Biased soft limiter and Zener–diode clipper characteristics]].

## 5. Diode clamp (DC restorer) circuits

A limiter chops off the peaks of a waveform, whereas a **clamp** (or **DC restorer**) shifts the whole waveform up or down by a constant DC voltage while keeping its shape and peak-to-peak amplitude $V_{\mathrm{p\text{-}p}}=2V_p$. The circuit replaces the limiter's series resistor with a series capacitor $C$, followed by a shunt diode between the output node $v_{\mathrm{out}}$ and the $0\ \mathrm V$ rail.

![[ee_b2_clamp.png|900]]

Consider an AC input $v_{\mathrm{in}}(t)=V_p\sin(\omega t)$ driving a positive clamp whose shunt diode points upwards (anode at $0\ \mathrm V$, cathode at $v_{\mathrm{out}}$), with an unloaded output ($I_{\mathrm{out}}=0$) and a $0.7\ \mathrm V$ silicon forward drop.

The capacitor charges on the negative peak. When $v_{\mathrm{in}}(t)$ swings below $-0.7\ \mathrm V$, the diode becomes forward-biased and conducts, holding the output node at $v_{\mathrm{out}}=-0.7\ \mathrm V$ (cathode $0.7\ \mathrm V$ below the $0\ \mathrm V$ anode). Define the capacitor voltage $V_C$ as positive on the right-hand (output) plate relative to the left-hand (input) plate. At the negative peak $v_{\mathrm{in}}=-V_p$, KVL from the input terminal through $C$ to the output terminal gives

$$
\begin{aligned}
v_{\mathrm{in}}+V_C&=v_{\mathrm{out}},\\
-V_p+V_C&=-0.7\ \mathrm V,\\
\boxed{V_C=V_p-0.7\ \mathrm V}.
\end{aligned}
$$

The charge is then held for the rest of the cycle. Once $v_{\mathrm{in}}(t)$ rises above its negative peak, $v_{\mathrm{out}}=v_{\mathrm{in}}(t)+V_C$ rises above $-0.7\ \mathrm V$, which reverse-biases the diode. The diode blocks reverse current and no external load is connected ($I_{\mathrm{out}}=0$), so the capacitor has no discharge path and keeps the constant voltage $V_C=V_p-0.7\ \mathrm V$ indefinitely. KVL then gives the steady-state output at every instant $t$:

$$
\boxed{v_{\mathrm{out}}(t)=v_{\mathrm{in}}(t)+(V_p-0.7\ \mathrm V)}.
$$

The minimum of $v_{\mathrm{out}}(t)$ is clamped at $-V_p+(V_p-0.7\ \mathrm V)=-0.7\ \mathrm V$, and its maximum reaches $+V_p+(V_p-0.7\ \mathrm V)=2V_p-0.7\ \mathrm V=V_{\mathrm{p\text{-}p}}-0.7\ \mathrm V$. Reversing the diode charges the capacitor with the opposite polarity on the positive peak and shifts the waveform downwards, to $v_{\mathrm{out}}(t)=v_{\mathrm{in}}(t)-(V_p-0.7\ \mathrm V)$. A series bias battery $V_x$ in the diode branch shifts the clamped trough (or peak) by $V_x$, giving a maximum output of $(V_{\mathrm{p\text{-}p}}-0.7\ \mathrm V)+V_x$.

## Worked examples

### Smoothed full-wave bridge rectifier design and half-wave comparison

Tutorial Sheet 3 Q6 asks for a full-wave bridge rectifier with smoothing capacitor that supplies an average load current $i_{\mathrm{DC}}=5.0\ \mathrm{mA}=5.0\times 10^{-3}\ \mathrm A$ at an average output voltage $V_{\mathrm{average}}=10.0\ \mathrm V$ with peak-to-peak ripple $\Delta V=0.20\ \mathrm V$, from a $f=50\ \mathrm{Hz}$ sinusoidal supply, using silicon diodes with $V_{\mathrm{on}}=0.7\ \mathrm V$.

For part (a), the smoothing capacitance, the full-wave ripple frequency is $2f=100\ \mathrm{Hz}$ ($\Delta t=1/(2f)=10.0\ \mathrm{ms}$). Substitute into the full-wave formula:

$$
\begin{aligned}
C&=\frac{i_{\mathrm{DC}}}{2f\,\Delta V},\\
C&=\frac{5.0\times 10^{-3}\ \mathrm A}{2(50\ \mathrm{s^{-1}})(0.20\ \mathrm V)},\\
C&=\frac{5.0\times 10^{-3}}{20.0}\ \mathrm F=2.50\times 10^{-4}\ \mathrm F=\boxed{250\ \mu\mathrm F}.
\end{aligned}
$$

Part (b) asks for the peak-to-peak AC input. The average output sits $\Delta V/2$ below the rectified peak $V_{p,\mathrm{out}}$, which is therefore found first:

$$
\begin{aligned}
V_{\mathrm{average}}&=V_{p,\mathrm{out}}-\frac{\Delta V}{2},\\
V_{p,\mathrm{out}}&=V_{\mathrm{average}}+\frac{\Delta V}{2},\\
V_{p,\mathrm{out}}&=10.0\ \mathrm V+\frac{0.20\ \mathrm V}{2}=10.10\ \mathrm V.
\end{aligned}
$$

The smoothed output therefore oscillates between $V_{\max}=10.10\ \mathrm V$ and $V_{\min}=10.10\ \mathrm V-0.20\ \mathrm V=9.90\ \mathrm V$. On each charging peak two bridge diodes conduct in series and drop $2V_{\mathrm{on}}=2(0.7\ \mathrm V)=1.40\ \mathrm V$. Adding this drop gives the required peak AC input:

$$
\begin{aligned}
V_{p,\mathrm{in}}&=V_{p,\mathrm{out}}+2V_{\mathrm{on}},\\
V_{p,\mathrm{in}}&=10.10\ \mathrm V+1.40\ \mathrm V=11.50\ \mathrm V.
\end{aligned}
$$

Doubling the peak amplitude gives the peak-to-peak input:

$$
V_{\mathrm{p\text{-}p,in}}=2V_{p,\mathrm{in}}=2(11.50\ \mathrm V)=\boxed{23.0\ \mathrm V}.
$$

A single-diode half-wave rectifier meeting the same specification ($10.0\ \mathrm V$, $\Delta V=0.20\ \mathrm V$, $5.0\ \mathrm{mA}$ at $50\ \mathrm{Hz}$) would have a discharge interval of $\Delta t=1/f=20.0\ \mathrm{ms}$ and so need twice the capacitance, $C_{\mathrm{HW}}=i_{\mathrm{DC}}/(f\Delta V)=500\ \mu\mathrm F$. It would lose only one diode drop ($0.7\ \mathrm V$), giving $V_{p,\mathrm{in,HW}}=10.10\ \mathrm V+0.70\ \mathrm V=10.80\ \mathrm V$ ($21.6\ \mathrm V$ peak-to-peak).

> [!check] Exact exponential RC discharge check
> The effective load resistance is $R_L=V_{\mathrm{average}}/i_{\mathrm{DC}}=(10.0\ \mathrm V)/(5.0\times 10^{-3}\ \mathrm A)=2000\ \Omega=2.00\ \mathrm{k\Omega}$, giving a discharge time constant $\tau=R_LC=(2000\ \Omega)(250\times 10^{-6}\ \mathrm F)=0.500\ \mathrm s=500\ \mathrm{ms}$. This is $50$ times the $10.0\ \mathrm{ms}$ half-period, and an exact exponential decay over $\Delta t=10.0\ \mathrm{ms}$ drops by $\Delta V_{\mathrm{exp}}=V_{p,\mathrm{out}}(1-e^{-\Delta t/\tau})=(10.10\ \mathrm V)(1-e^{-0.010/0.500})=0.2000\ \mathrm V$, so the linear-discharge approximation is accurate to four significant figures.

### Zener shunt regulator analysis and load-range check

An unregulated supply $V_{\mathrm{in}}=10.0\ \mathrm V$ feeds a series resistor $R_S=50.0\ \Omega$ and a reverse-biased Zener diode of breakdown voltage $V_Z=6.0\ \mathrm V$ connected across the output load terminals (Week 7 interactive, p. 7).

While the Zener is in breakdown ($V_{\mathrm{out}}=V_Z=6.0\ \mathrm V$), KVL fixes the voltage across the series resistor:

$$
V_{R_S}=V_{\mathrm{in}}-V_Z=10.0\ \mathrm V-6.0\ \mathrm V=4.0\ \mathrm V.
$$

The current through the series resistor is therefore constant across the whole regulated range:

$$
I_S=\frac{V_{R_S}}{R_S}=\frac{4.0\ \mathrm V}{50.0\ \Omega}=0.0800\ \mathrm A=\boxed{80.0\ \mathrm{mA}}.
$$

At zero load current ($I_{\mathrm{load}}=0\ \mathrm{mA}$), KCL sends the entire $80.0\ \mathrm{mA}$ through the Zener ($I_{Z,\max}=80.0\ \mathrm{mA}$). The power dissipated in the series resistor and in the Zener is

$$
\begin{aligned}
P_{R_S}&=V_{R_S}I_S=(4.0\ \mathrm V)(0.0800\ \mathrm A)=0.320\ \mathrm W,\\
P_{Z,\max}&=V_ZI_{Z,\max}=(6.0\ \mathrm V)(0.0800\ \mathrm A)=0.480\ \mathrm W,\\
P_{\mathrm{total}}&=P_{R_S}+P_{Z,\max}=0.320\ \mathrm W+0.480\ \mathrm W=\boxed{0.800\ \mathrm W}.
\end{aligned}
$$

At the other extreme, under the ideal vertical-breakdown model ($I_{Z,\min}=0\ \mathrm{mA}$), regulation holds until the load absorbs all $80.0\ \mathrm{mA}$ of resistor current. That gives $I_{\mathrm{load},\max}=\boxed{80.0\ \mathrm{mA}}$, corresponding to a minimum load resistance $R_{L,\min}=6.0\ \mathrm V/0.0800\ \mathrm A=75.0\ \Omega$. If a practical minimum breakdown current of $I_{Z,\min}=5.0\ \mathrm{mA}$ is needed to keep the Zener below its knee, the maximum regulated load current is

$$
I_{\mathrm{load},\max}=I_S-I_{Z,\min}=80.0\ \mathrm{mA}-5.0\ \mathrm{mA}=75.0\ \mathrm{mA}\qquad (R_L\ge 80.0\ \Omega).
$$

> [!check] Supply power balance and overload droop check
> At no load, the $10.0\ \mathrm V$ source delivers $P_{\mathrm{source}}=V_{\mathrm{in}}I_S=(10.0\ \mathrm V)(0.0800\ \mathrm A)=0.800\ \mathrm W$, matching $P_{R_S}+P_{Z,\max}=0.320\ \mathrm W+0.480\ \mathrm W=0.800\ \mathrm W$. If the load current rises beyond $80.0\ \mathrm{mA}$ to $I_{\mathrm{load}}=100\ \mathrm{mA}$, the drop across $R_S$ becomes $(0.100\ \mathrm A)(50.0\ \Omega)=5.0\ \mathrm V$, pulling the output down to $V_{\mathrm{out}}=10.0\ \mathrm V-5.0\ \mathrm V=5.0\ \mathrm V<V_Z$, so the Zener is completely OFF ($I_Z=0\ \mathrm{mA}$).

### Biased soft limiter and Zener–diode clipper characteristics

The soft limiter of Tutorial Sheet 3 Q3 uses the zero-drop ideal diode model ($V_{\mathrm{on}}=0\ \mathrm V$) and an unloaded output ($I_{\mathrm{out}}=0$). The input $v_{\mathrm{in}}$ feeds the output node $v_{\mathrm{out}}$ through a series resistor $R_1=10\ \mathrm{k\Omega}$. Two shunt branches connect $v_{\mathrm{out}}$ to $0\ \mathrm V$. Branch 1 has a downward-pointing ideal diode in series with a $+5.0\ \mathrm V$ battery and $R_2=10\ \mathrm{k\Omega}$; Branch 2 has an upward-pointing ideal diode in series with a $-5.0\ \mathrm V$ battery and $R_3=10\ \mathrm{k\Omega}$.

In the middle region ($-5.0\ \mathrm V\le v_{\mathrm{in}}\le +5.0\ \mathrm V$), both diodes are reverse-biased (OFF), so no current flows through $R_1$ and

$$
v_{\mathrm{out}}=v_{\mathrm{in}}\qquad (\text{slope }1).
$$

In the upper region ($v_{\mathrm{in}}>+5.0\ \mathrm V$), the downward diode in Branch 1 turns ON ($V_D=0\ \mathrm V$) while Branch 2 stays OFF. KCL at the unloaded output node equates the current entering through $R_1$ to the current leaving through $R_2$:

$$
\begin{aligned}
\frac{v_{\mathrm{in}}-v_{\mathrm{out}}}{10\ \mathrm{k\Omega}}&=\frac{v_{\mathrm{out}}-5.0\ \mathrm V}{10\ \mathrm{k\Omega}},\\
v_{\mathrm{in}}-v_{\mathrm{out}}&=v_{\mathrm{out}}-5.0\ \mathrm V,\\
2v_{\mathrm{out}}&=v_{\mathrm{in}}+5.0\ \mathrm V,\\
\boxed{v_{\mathrm{out}}=\frac{v_{\mathrm{in}}+5.0\ \mathrm V}{2}=\frac{1}{2}v_{\mathrm{in}}+2.5\ \mathrm V}\qquad (v_{\mathrm{in}}>5.0\ \mathrm V).
\end{aligned}
$$

In the lower region ($v_{\mathrm{in}}<-5.0\ \mathrm V$), Branch 2 turns ON and Branch 1 is OFF, and by symmetry KCL gives

$$
\boxed{v_{\mathrm{out}}=\frac{v_{\mathrm{in}}-5.0\ \mathrm V}{2}=\frac{1}{2}v_{\mathrm{in}}-2.5\ \mathrm V}\qquad (v_{\mathrm{in}}<-5.0\ \mathrm V).
$$

The Zener–diode hard clipper (Week 7 interactive, p. 9) uses the $0.7\ \mathrm V$ constant-drop model instead. A $1\ \mathrm{k\Omega}$ series resistor feeds two parallel shunt branches across $v_{\mathrm{out}}$: an upward-pointing Zener diode ($V_Z=10.0\ \mathrm V$, forward drop $0.7\ \mathrm V$) and a downward-pointing conventional diode $D$ in series with a $+5.0\ \mathrm V$ battery. On positive input swings, $D$ turns ON as soon as $v_{\mathrm{out}}$ reaches $5.0\ \mathrm V+0.7\ \mathrm V=+5.7\ \mathrm V$ and holds $v_{\mathrm{out}}=+5.7\ \mathrm V$. Since $v_{\mathrm{out}}$ never reaches $+10.0\ \mathrm V$, the Zener never enters reverse breakdown. On negative swings, $D$ is reverse-biased, but the upward-pointing Zener becomes forward-biased once $v_{\mathrm{in}}\le -0.7\ \mathrm V$ and holds the output at $v_{\mathrm{out}}=-0.7\ \mathrm V$. For $-0.7\ \mathrm V<v_{\mathrm{in}}<+5.7\ \mathrm V$, both branches are OFF and $v_{\mathrm{out}}=v_{\mathrm{in}}$.

> [!check] Breakpoint continuity check
> In the soft limiter, the upper formula at $v_{\mathrm{in}}=+5.0\ \mathrm V$ gives $v_{\mathrm{out}}=(5.0+5.0)/2=+5.0\ \mathrm V$, and at $v_{\mathrm{in}}=+10.0\ \mathrm V$ gives $v_{\mathrm{out}}=+7.5\ \mathrm V$, matching panel (d) of `ee_b2_limiters.png`. In the Zener–diode clipper at $v_{\mathrm{in}}=+12.0\ \mathrm V$, the conventional branch carries $(12.0\ \mathrm V-5.7\ \mathrm V)/1\ \mathrm{k\Omega}=6.3\ \mathrm{mA}$ and holds $v_{\mathrm{out}}=5.7\ \mathrm V<10.0\ \mathrm V$, so the Zener stays non-conducting in reverse bias.

### Half-wave rectifier AC voltmeter calibration

Tutorial Sheet 3 Q4 models an AC voltmeter as an ideal diode ($V_{\mathrm{on}}=0\ \mathrm V$) in series with a calibration resistor $R$ and a moving-coil meter of resistance $R_m=50.0\ \Omega$. The meter reads full scale when the average current over a full cycle is $I_{\mathrm{avg}}=1.00\ \mathrm{mA}=1.00\times 10^{-3}\ \mathrm A$. The task is to find the $R$ that gives full-scale deflection for a sinusoidal input of $20.0\ \mathrm V$ peak-to-peak ($V_p=10.0\ \mathrm V$).

During the positive half-cycle ($0\le\theta\le\pi$, with $\theta=\omega t$), the ideal diode conducts with $V_D=0\ \mathrm V$, so the current through the series resistance $R+R_m$ is

$$
i(\theta)=\frac{V_p\sin\theta}{R+R_m}=I_p\sin\theta,\qquad I_p=\frac{V_p}{R+R_m}.
$$

During the negative half-cycle ($\pi<\theta\le 2\pi$) the diode blocks and $i(\theta)=0$. Integrating over one complete period $2\pi$ gives the full-cycle average current:

$$
\begin{aligned}
I_{\mathrm{avg}}&=\frac{1}{2\pi}\int_0^{2\pi}i(\theta)\,d\theta,\\
I_{\mathrm{avg}}&=\frac{1}{2\pi}\int_0^{\pi}I_p\sin\theta\,d\theta+0,\\
I_{\mathrm{avg}}&=\frac{I_p}{2\pi}\Big[-\cos\theta\Big]_0^{\pi},\\
I_{\mathrm{avg}}&=\frac{I_p}{2\pi}\big(-\cos\pi-(-\cos 0)\big),\\
I_{\mathrm{avg}}&=\frac{I_p}{2\pi}(1+1)=\frac{I_p}{\pi}.
\end{aligned}
$$

Substitute $I_p=V_p/(R+R_m)$ and solve for $R$:

$$
\begin{aligned}
I_{\mathrm{avg}}&=\frac{V_p}{\pi(R+R_m)},\\
R+R_m&=\frac{V_p}{\pi I_{\mathrm{avg}}},\\
R&=\frac{V_p}{\pi I_{\mathrm{avg}}}-R_m.
\end{aligned}
$$

With $V_p=10.0\ \mathrm V$, $I_{\mathrm{avg}}=1.00\times 10^{-3}\ \mathrm A$ and $R_m=50.0\ \Omega$:

$$
\begin{aligned}
R&=\frac{10.0\ \mathrm V}{\pi(1.00\times 10^{-3}\ \mathrm A)}-50.0\ \Omega,\\
R&=3183.1\ \Omega-50.0\ \Omega=\boxed{3133\ \Omega\approx 3.13\ \mathrm{k\Omega}}.
\end{aligned}
$$

> [!check] Re-substitution of peak and half-cycle currents
> With $R+R_m=3183.1\ \Omega$, the peak current during the conducting half-cycle is $I_p=10.0\ \mathrm V/3183.1\ \Omega=3.1416\ \mathrm{mA}=\pi\ \mathrm{mA}$. Its average over the conducting half-cycle alone ($0$ to $\pi$) is $2I_p/\pi=2.00\ \mathrm{mA}$, and averaging that with $0\ \mathrm{mA}$ over the blocking half-cycle ($\pi$ to $2\pi$) gives $(2.00\ \mathrm{mA}+0\ \mathrm{mA})/2=1.00\ \mathrm{mA}$, the full-scale meter current.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 B1 - Semiconductors and Diodes]]
- Next: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Concepts: [[Rectification and Smoothing]] · [[Zener Diode Regulator]] · [[Diode Limiters and Clamps]]
- Worked problems: [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]

## Sources

- `S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`, pp. 14–23 (§1.5.2: half-wave and full-wave bridge rectification; §1.5.3: smoothing capacitor and ripple derivation; §1.5.4–1.5.5: Zener diodes and voltage regulation; §1.5.6: diode limiter and clamp circuits).
- 1b Diodes as rectifiers, `FEEG1004 Lecture 1b.txt` (ll. 1–50: half-wave rectifier; ll. 51–108: four-diode full-wave bridge rectifier and $1.4\ \mathrm V$ drop; ll. 109–181: smoothing capacitor, triangular ripple approximation, $\Delta V=I/(2fC)$ and $V_{\mathrm{avg}}=V_p-I/(4fC)$).
- 1c Zener diodes and voltage limiters, `FEEG1004 Lecture 1c.txt` (ll. 1–45: Zener doping, reverse breakdown and shunt voltage regulator; ll. 46–104: negative shunt limiter, anti-parallel limiter and battery-biased limiter). The `1c` recording stops after limiters; diode clamps in Section 5 are written-ahead from Mills §1.5.6 (pp. 21–23).
- L6, `FEEG1004 Lecture 6.txt` (ll. 126–186: bridge rectifier conducting pairs and $10\ \mathrm V\to 8.6\ \mathrm V$ peak; ll. 187–290: $10\ \mathrm V$, $50\ \Omega$, $6\ \mathrm V$ Zener regulator current, power balance and $80\ \mathrm{mA}$ maximum load; ll. 291–474: shunt limiters and Zener–diode clipper; ll. 475–548: diode–capacitor peak-hold problem), matching `S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf`, pp. 6–11.
- `Tutorial Sheet 03 - Electronics A - Diodes & Transistors.pdf`, Q2, Q3, Q4 and Q6.
- All numerical values were recomputed in Python. Figures `ee_b2_rectifiers.png`, `ee_b2_zener_regulator.png`, `ee_b2_limiters.png` and `ee_b2_clamp.png` are generated by `generate_electronics_figures.py`.

## Self-study tasks

### Core

- [ ] Sketch the transfer characteristic $v_{\mathrm{out}}$ vs $v_{\mathrm{in}}$ and the diode voltage waveform $v_D(t)$ for an ideal half-wave rectifier (Tutorial Sheet 3 Q2(a–b)). → [[#1. Half-wave and full-wave bridge rectification]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q2: Half-wave circuit (series diode, output across the resistor)|Tutorial 3 Q2]]
- [ ] Identify which bridge diodes conduct on the negative half-cycle and calculate the peak load voltage for a $10\ \mathrm V$ amplitude input (L6, ll. 156–186; interactive p. 6). → [[#1. Half-wave and full-wave bridge rectification]]
- [ ] Derive the transfer characteristic of the biased soft limiter with $10\ \mathrm{k\Omega}$ branches and $\pm 5\ \mathrm V$ batteries (Tutorial Sheet 3 Q3). → [[#Biased soft limiter and Zener–diode clipper characteristics]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q3: Soft limiter with biased diodes|Tutorial 3 Q3]]
- [ ] Calculate the calibration resistor $R$ for the half-wave rectifier AC voltmeter at $20\ \mathrm V$ peak-to-peak (Tutorial Sheet 3 Q4). → [[#Half-wave rectifier AC voltmeter calibration]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q4: Rectifier AC voltmeter: find R for full scale at 20 V p-p|Tutorial 3 Q4]]
- [ ] Calculate the smoothing capacitor and peak-to-peak AC input voltage for the $10\ \mathrm V$, $0.2\ \mathrm V$ ripple, $5\ \mathrm{mA}$, $50\ \mathrm{Hz}$ full-wave bridge supply (Tutorial Sheet 3 Q6(a–b)). → [[#Smoothed full-wave bridge rectifier design and half-wave comparison]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q6: Full-wave rectifier with smoothing: 10 V average, 0.2 V ripple, 5 mA, 50 Hz|Tutorial 3 Q6]]

### Further practice

- [ ] Find the no-load resistor current, total power consumption, and maximum load current of the $10\ \mathrm V$, $50\ \Omega$, $6\ \mathrm V$ Zener regulator (L6, ll. 189–290; interactive p. 7). → [[#Zener shunt regulator analysis and load-range check]]
- [ ] Determine the input–output transfer characteristic of the $10\ \mathrm V$ Zener and $+5\ \mathrm V$ biased-diode limiter circuit (L6, ll. 329–438; interactive p. 9). → [[#Biased soft limiter and Zener–diode clipper characteristics]]
- [ ] Complete the algebraic steps from $V_{\mathrm{average}}=V_p-\Delta V/2$ and $\Delta V=i_{\mathrm{DC}}/(2fC)$ to $V_{\mathrm{average}}=V_p-i_{\mathrm{DC}}/(4fC)$ left as an exercise in the recording (1b, ll. 169–173). → [[#Ripple and average output voltage]]
- [ ] Design the diode limiter circuit that clips both positive and negative excursions at $\pm 0.7\ \mathrm V$ (L6, ll. 439–474; interactive p. 10). → [[#4. Diode limiter (clipper) circuits]]
- [ ] Explain why the series capacitor in a diode clamp or peak detector cannot discharge once charged, and find the held capacitor voltage after a $1.0\ \mathrm V$ input peak under a $0.7\ \mathrm V$ diode drop (L6, ll. 475–544; interactive p. 11). → [[#5. Diode clamp (DC restorer) circuits]]

## Transcript and slide slips

### Full-wave rectified frequency stated as 25 Hz instead of 100 Hz

> [!warning] Halving a 20 ms period doubles the frequency to 100 Hz, not 25 Hz
> Where: [[#Full-wave bridge rectifier]]
> In the 1b transcript, ll. 102–106, when explaining full-wave rectification of a $50\ \mathrm{Hz}$ input ($T=1/50\ \mathrm{s}=20\ \mathrm{ms}$), the speaker states that the rectified period is $10\ \mathrm{ms}$ and then says "So this signal here is 25 Hz signal double the input because we full wave rectified it". A period of $T/2=10\ \mathrm{ms}$ corresponds to $f_{\mathrm{ripple}}=1/(0.010\ \mathrm s)=2f=100\ \mathrm{Hz}$, not $25\ \mathrm{Hz}$.

### Diode model and initial capacitor voltage on the Week 7 peak-hold slide

> [!warning] Slide text specifies an ideal diode with 0.3 V initial charge, whereas the live solution uses a 0.7 V drop from zero initial charge
> Where: [[#5. Diode clamp (DC restorer) circuits]]
> Interactive slide p. 11 prints: "If the diode is ideal diode, and the initial voltage across the capacitor is $0.3\ \mathrm V$, then output voltage $V_o(t)$ at $t = 5\ \mathrm{ms}$ is ___" for an input $V_{\mathrm{in}}(t)$ whose highest peak is $1.0\ \mathrm V$ at $t=3\ \mathrm{ms}$. Under the standard zero-drop ideal diode model ($V_{\mathrm{on}}=0\ \mathrm V$), the capacitor charges up to the full $1.0\ \mathrm V$ peak at $t=3\ \mathrm{ms}$ and holds $V_o(5\ \mathrm{ms})=1.0\ \mathrm V$ (option D). In `FEEG1004 Lecture 6.txt`, ll. 498–544, the speaker instead treats "ideal diode" as the $0.7\ \mathrm V$ constant-drop model (matching slide p. 4's label "ideal diode with $0.7\ \mathrm V$ forward voltage") and starts the capacitor from $0\ \mathrm V$ at $t=0$, so the $1.0\ \mathrm V$ peak charges the capacitor to $1.0\ \mathrm V-0.7\ \mathrm V=0.3\ \mathrm V$ (option A). Under either interpretation, the capacitor holds its maximum forward-charged voltage $V_{\max}=\max(V_{C,0},\,V_{\mathrm{in,peak}}-V_{\mathrm{on}})$ because the reverse-biased diode prevents discharge.
