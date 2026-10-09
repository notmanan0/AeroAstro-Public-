---
title: "FEEG1004 A7 - Thevenin, Superposition and Relays"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 7
tags: [feeg1004, fundamentals, thevenin, norton, superposition, relays, flyback-diode, source-resistance]
aliases: ["Lecture 7a-7c", "Thevenin equivalent", "Thévenin", "Superposition", "Relays"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A6 - Mesh Analysis]]", "[[FEEG1004 A5 - Inductors and Electrical Resonance]]"]
next_topics: ["[[FEEG1004 B1 - Semiconductors and Diodes]]"]
key_concepts: ["[[Thevenin and Norton Equivalent Circuits]]", "[[Superposition Theorem (Circuits)]]", "[[Maximum Power Transfer]]", "[[Electromechanical Relays]]", "[[Flyback Diode]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]", "[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf"]
---

# FEEG1004 A7 - Thevenin, Superposition and Relays

> [!abstract] Summary
> Circuit **transformations** avoid writing the full mesh equations.
> - **Thévenin**: any two-terminal network of resistors and ideal sources is equivalent to one source $V_{TH}$ (the open-circuit voltage) in series with $R_{TH}$ (the resistance seen with all sources zeroed). **Norton** is the current-source dual.
> - **Superposition**: in a *linear* circuit, the response to several sources is the sum of the responses to each alone. Zero a voltage source by shorting it and a current source by opening it.
> - **Relays** are electromagnetic switches: a coil (with $R$ and $L$) moves contacts. Switching an inductive coil off needs a **flyback diode**.

## Key Concepts
- [[Thevenin and Norton Equivalent Circuits]] · [[Superposition Theorem (Circuits)]] · [[Maximum Power Transfer]] · [[Electromechanical Relays]] · [[Flyback Diode]]

---

## 1. Real sources have internal resistance (L7a)
- An ideal 5 V source shorted by a 1 mΩ wire would deliver $V^2/R$ = **25 kW** (answer C). Real sources cannot: their terminal voltage **droops** as current is drawn. Headlights dim while the starter motor cranks.
- **Battery model**: an ideal source $V_b$ in series with an **equivalent series resistance** $R_{ESR}$.
  - KVL gives $V_{out} = V_b - I_{out}R_{ESR}$: a straight V–I line.
  - The **intercept** is the open-circuit voltage; the **slope** is $-R_{ESR}$.

![[ee_a7_battery_model.png|900]]

The left panel is Tutorial 1 Q2: Sam's battery sags to 8 V at 200 A, so $R_{ESR} = (13 - 8)/200$ = 25 mΩ instead of the healthy 10 mΩ.

## 2. Thévenin's theorem
**Method**:
1. Identify the part of the network to replace (as seen from terminals A–B).
2. $R_{TH}$: **zero all sources** (voltage source → short; current source → open) and simplify.
3. $V_{TH}$: the **open-circuit** voltage $V_{AB}$ (no current leaves A or B).
4. Reconnect the load to the equivalent and solve.

![[ee_a7_thevenin_example.png|920]]

> [!example] Lecture 7a: current in a 3 Ω load
> - **$R_{TH}$**: shorting the 12 V source shorts out the 1 Ω. The 4 Ω and 6 Ω are in series (10 Ω), and that is in parallel with 2 Ω: $R_{TH} = 2\parallel10$ = **5/3 Ω**.
> - **$V_{TH}$**: the 1 Ω across the ideal 12 V source does not affect $V_{AB}$ (the source fixes its own terminal voltage). The remaining perimeter loop gives $12 - 2I - 4I - 6 - 6I = 0$, so $I$ = 0.5 A. Then $V_{AB} = 12 - 2I$ = **11 V**.
> - **Load**: $I = 11/(5/3 + 3)$ = **33/14 = 2.36 A**.

> [!example] W6 interactive: current in a 40 Ω resistor
> - $R_{TH} = 10\parallel20$ = 6.67 Ω.
> - Open-circuit loop: $10 - 10I - 20I - 20 = 0$, so $I$ = −0.333 A (the current flows anticlockwise). $V_{TH} = 10 - 10I$ = **13.3 V**.
> - $I_{40} = 13.33/(40 + 6.67)$ = **0.286 A**.

**Uses**:
- as a solving tool;
- as a model of batteries and power supplies ("12.8 V open circuit, 30 mΩ ESR");
- as a model of **amplifier outputs**.

**Norton**: a current source $I_N$ in parallel with $R_N$. Converting: $R_{TH} = R_N$ and $V_{TH} = I_NR_N$.

Lecture example 2 answer: $R_{TH}$ = 10 Ω, $V_{TH}$ = 0.5 V. Tutorial 2 Q3: 8.5 Ω and 0.75 V.

**Maximum power transfer**: power into a load is greatest when $R_L = R_{TH}$, giving $P_{max} = V_{TH}^2/4R_{TH}$. At that point efficiency is only 50 % (right panel above). That trade-off suits signal circuits but not power systems ([[Maximum Power Transfer]]).

## 3. Superposition (L7b)
For a circuit with several sources, any voltage or current is the sum of the contributions of each source acting alone, with the others **zeroed**:
- a voltage source is replaced by a **short circuit**;
- a current source is replaced by an **open circuit**.

It is **only valid for linear circuits**. Other linear systems include elastic structures (beam superposition, [[Superposition for Indeterminate Beams]]) and linear ODEs.

> [!example] W6: find the current in the 20 Ω resistor
> - **Current source zeroed (open)**: $R_p = 10\parallel(10 + 20)$ = 7.5 Ω. Potential divider: $V_a = 20\times7.5/12.5$ = 12 V, so $I_1 = 12/30$ = 0.4 A.
> - **Voltage source zeroed (short)**: $R_{eq} = 5\parallel10 + 10$ = 13.33 Ω. Current divider: $I_2 = 4\times13.33/33.33$ = 1.6 A.
> - **Sum**: $I$ = **2.0 A**.

> [!example] Why not wire amplifier outputs together (L7b)
> - Two sources $V_1$ (1 Ω output) and $V_2$ (5 Ω) are joined and feed an amplifier with 2 kΩ input.
> - Superposition gives $v_{in}\approx\tfrac{5}{6}V_1 + \tfrac{1}{6}V_2$. The mix depends on the **other amplifier's output impedance**, which is uncontrolled.
> - The fix is a **summing amplifier** ([[FEEG1004 B4 - Operational Amplifiers]]), which isolates the inputs through a virtual earth.

## 4. Relays and design with V and I (L7c)
- An electromechanical relay is an electrically operated switch: a small coil current **pulls an armature** to switch a much larger load current.
- **Terminology**: poles (number of switches) and throws (contacts per switch), e.g. SPDT, DPST. NO/NC describe the **de-energised** state.

> [!example] Relay design (L7c)
> - **Rating**: a 230 V, 1 kW spotlight draws $I = P/V$ = 4.3 A rms, so choose a relay with contacts rated above 4.3 A.
> - The Panasonic 4.5 V DC relay is rated 8 A, has a 101 Ω coil and DPST contacts.
> - **Indicator lamp in series with the coil (fails)**:
>   - A 5 V, 60 mA lamp is 83 Ω hot. The coil is inductive, but once the transient has passed it is simply its 101 Ω resistance.
>   - The divider gives the coil $5\times101/184$ = **2.74 V**, below the 4.5 V pull-in. The relay does not operate.
> - **Lamp in parallel with the coil (works)**: both see 5 V.
>   - Fault behaviour differs: with the series lamp, a failed coil also puts out the lamp.
>   - In parallel, the lamp stays on even if the coil fails, so the indicator could lie.

**Equivalent circuit**: a relay coil is $L$ in series with $R$ (plus a contact resistance). It is **inductive**, so opening the drive switch is dangerous:
- Before opening, $i = 5/101$ = 49.6 mA, and this cannot change instantly. $v = L\,di/dt$ rises until the current finds a path, usually a **spark across the switch**, which destroys transistors.
- A **flyback (snubber) diode** across the coil, reverse-biased in normal operation, gives the current a loop to decay through ($\tau = L/R$), clamping the voltage at supply + 0.7 V.

![[ee_a7_flyback.png|760]]

## Year 2 bridge
- A Thévenin source driving a load is the **loading-effect** divider of every sensor chain. Buffering makes $R_{load}\gg R_{TH}$ ([[Loading Effect and Buffering]], [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).
- **Solar arrays** have a strongly non-linear source curve with a maximum-power point; the power-conditioning electronics track it, the non-linear cousin of $R_L = R_{TH}$ ([[Solar Cells and Arrays]], [[SESA2024 08 - Electrical Power Subsystem]]).
- **Battery ESR** sets the voltage sag at eclipse-peak loads ([[Battery Sizing]]).
- **Superposition** is the basis of linear-systems analysis: convolution, transfer functions and frequency response ([[Transfer Function]], [[Frequency Response Function]]).
- **Flyback diodes** protect every transistor driving a solenoid valve, relay or motor, e.g. propulsion latch valves and reaction-wheel drives ([[Transistor as a Switch]], [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]).

## Links
- Previous: [[FEEG1004 A6 - Mesh Analysis]] · Next: [[FEEG1004 B1 - Semiconductors and Diodes]]
- Worked problems: [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]] (Q2) · [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]] (Q2, Q3, Q5)

## Sources
- Recorded lectures 7a (Thévenin), 7b (superposition) and 7c (relays and circuit examples), P. Glynne-Jones; Week 6 interactive session.
