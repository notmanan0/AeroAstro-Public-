---
title: FEEG1004 A7 - Thevenin, Superposition and Relays
module: FEEG1004 Electronics
type: topic
stream: 'Part A: Electrical Fundamentals and DC Circuits'
order: 7
tags:
- feeg1004
- fundamentals
- thevenin
- norton
- superposition
- relays
- flyback-diode
- source-resistance
aliases:
- Lecture 7a-7c
- Thevenin equivalent
- Thévenin
- Superposition
- Relays
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"
- "[[FEEG1004 A6 - Mesh Analysis]]"
- "[[FEEG1004 A5 - Inductors and Electrical Resonance]]"
next_topics:
- "[[FEEG1004 B1 - Semiconductors and Diodes]]"
key_concepts:
- "[[Thevenin and Norton Equivalent Circuits]]"
- "[[Superposition Theorem (Circuits)]]"
- "[[Electromechanical Relays]]"
- "[[Flyback Diode]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]"
- "[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"
sources:
- 02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf
- 02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-10-13 - 7a Thevenin.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-10-13 - 7b Superposition.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-10-13 - 7c Relays and circuit examples.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 5.txt
coverage: 7a Thevenin (ll. 17-225); 7b Superposition (ll. 1-108); 7c Relays and circuit examples (ll. 1-123); Lecture 5 (ll. 117-377)
---


# FEEG1004 A7 - Thevenin, Superposition and Relays

> [!abstract] Summary
> A linear two-terminal source network can be represented by a Thévenin voltage and series resistance, giving $V_{out}=V_{TH}-I_{out}R_{TH}$. Superposition finds a voltage or current by adding the contributions from independent sources acting separately. Relay circuits apply these ideas to coil voltage and switching; a flyback diode provides a path for the coil's stored magnetic energy to dissipate after switch-off.

> [!summary]- Exam use: quick path
> - **Use it when:** replacing a source network, calculating a response from several sources, or checking a relay drive and its switch-off path.
> - **Assumptions:** linear resistors and independent ideal sources for Thévenin/superposition; specified coil resistance at DC steady state; finite inductor voltage for current continuity.
> - **Method:** 1. Select the load terminals and reference directions. 2. Find open-circuit voltage with sources active. 3. Find resistance with independent sources zeroed, or solve each source contribution. 4. Reconnect the load or add signed contributions. 5. Check against the original circuit and identify the coil's decay path.
> - **Common mistakes:** leaving sources zeroed while calculating $V_{TH}$; adding powers rather than signed voltages or currents in superposition.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q3: Thévenin equivalent at A–B|Tutorial 2 Q3]]

A load connected to a source network responds to the voltage between its two terminals and the current supplied through them. The details inside the network can often be replaced by a simpler model with the same terminal behaviour. For a linear resistive network, Thévenin's equivalent uses one voltage source and one series resistor.

Superposition takes a different approach to the same linear circuit laws. It separates the response into contributions from individual sources, keeping the resistors in place throughout. The partial voltages or currents can reinforce or oppose one another, so their reference directions must stay fixed.

A relay adds a mechanical switch operated by a coil. Its steady coil voltage depends on the resistive circuit, while its switching transient depends on stored magnetic energy. Opening the drive circuit removes the supply path but does not immediately remove the coil current or its energy.

## 1. Source resistance and terminal behaviour

Model a real source as an ideal voltage $V_b$ in series with equivalent series resistance $R_{ESR}$. Define $I_{out}$ as current delivered from the positive terminal, and $V_{out}$ positive at that terminal. KVL gives

$$
\begin{aligned}
V_b-I_{out}R_{ESR}-V_{out}&=0,\\
V_{out}&=V_b-I_{out}R_{ESR}.
\end{aligned}
$$

The voltage–current graph has intercept $V_b$ and slope $-R_{ESR}$. Greater load current produces a larger internal voltage drop. This is an approximate battery model, rather than a statement that battery resistance is fixed under all operating conditions.

For the tutorial battery, $13\,\mathrm V$ open circuit becomes $8\,\mathrm V$ at $200\,\mathrm A$:

$$
\begin{aligned}
R_{ESR}&=\frac{V_b-V_{out}}{I_{out}},\\
R_{ESR}&=\frac{13\,\mathrm V-8\,\mathrm V}{200\,\mathrm A}=0.0250\,\Omega=25.0\,\mathrm{m\Omega}.
\end{aligned}
$$

An ideal $5\,\mathrm V$ source across $1\,\mathrm{m\Omega}$ would deliver $P=V^2/R=(5\,\mathrm V)^2/(1\,\mathrm{m\Omega})=25.0\,\mathrm{kW}$. That result follows from the ideal model and shows the need to include source resistance or other limits when representing a real supply.

## 2. Finding a Thévenin equivalent

The **Thévenin equivalent** represents the selected linear two-terminal network by $V_{TH}$ in series with $R_{TH}$. Remove the load before finding these two parameters. Open circuit means no external load current, not necessarily zero current inside the network.

Find $V_{TH}$ as the open-circuit terminal voltage with the original sources active. Find $R_{TH}$ looking into the same terminals after setting independent sources to zero. A zero-voltage source is a short circuit; a zero-current source is an open circuit. Any separate source resistance remains in place.

For a reconnected resistor $R_L$, KVL gives

$$
\begin{aligned}
V_{TH}-I_LR_{TH}-I_LR_L&=0,\\
V_{TH}&=I_L(R_{TH}+R_L),\\
I_L&=\frac{V_{TH}}{R_{TH}+R_L}.
\end{aligned}
$$

The terminal voltage is $V_L=I_LR_L$. The equivalent reproduces these external quantities; it does not reproduce every internal branch current or internal power loss.

For positive finite $R_{TH}$, shorting the output sets its voltage to zero. Rearrange the terminal equation:

$$
\begin{aligned}
0&=V_{TH}-I_{short}R_{TH},\\
I_{short}R_{TH}&=V_{TH},\\
I_{short}&=\frac{V_{TH}}{R_{TH}}.
\end{aligned}
$$

This is the current-axis intercept of the straight-line characteristic.

### Open terminals can still have a voltage

Consider a network with a $1\,\mathrm V$ source, two $12\,\Omega$ resistors in its upper loop and a $4\,\Omega$ resistor leading to terminal B. With no load connected, no current flows through the $4\,\Omega$ resistor, so it has zero voltage drop. The upper-loop current is

$$
I=\frac{1\,\mathrm V}{12\,\Omega+12\,\Omega}=\frac1{24}\,\mathrm A.
$$

The open-circuit terminal voltage is the drop across one $12\,\Omega$ resistor:

$$
V_{TH}=\left(\frac1{24}\,\mathrm A\right)(12\,\Omega)=0.500\,\mathrm V.
$$

Zeroing the source puts the two $12\,\Omega$ resistors in parallel, in series with $4\,\Omega$:

$$
R_{TH}=4\,\Omega+\frac{(12\,\Omega)(12\,\Omega)}{12\,\Omega+12\,\Omega}=10.0\,\Omega.
$$

Norton's alternative is a current source $I_N$ in parallel with $R_N$. In open circuit all its current flows through $R_N$, giving $V_{TH}=I_NR_N$. Zeroing that current source leaves $R_N$, so $R_{TH}=R_N$. Only this equivalence with the Thévenin form is needed here.

## 3. Superposition and amplifier outputs

For a linear resistor network, KVL, KCL and the component laws form linear equations. If two sources give vectors of source terms $\mathbf b_1$ and $\mathbf b_2$, their separate responses satisfy

$$
\mathbf A\mathbf x_1=\mathbf b_1,\qquad \mathbf A\mathbf x_2=\mathbf b_2.
$$

Adding the equations gives

$$
\begin{aligned}
\mathbf A\mathbf x_1+\mathbf A\mathbf x_2&=\mathbf b_1+\mathbf b_2,\\
\mathbf A(\mathbf x_1+\mathbf x_2)&=\mathbf b_1+\mathbf b_2.
\end{aligned}
$$

Thus the total response is the sum of the separate responses for a uniquely solvable network. Set the other independent voltage sources to shorts and current sources to opens when calculating each contribution. Keep resistor values and response directions unchanged.

Power is quadratic in current or voltage, so this addition does not apply directly to power. For example, $R(i_1+i_2)^2$ includes a cross term absent from $Ri_1^2+Ri_2^2$. Add the currents first, then calculate power.

### Why directly joining amplifier outputs gives a weighted mix

Two amplifier outputs, $R_1=5\,\Omega$ with $V_1$ and $R_2=1\,\Omega$ with $V_2$, are joined to an input of resistance $R_{in}=2\,\mathrm{k\Omega}$. With $V_2$ suppressed, the lower divider resistance is

$$
R_{p1}=\frac{(1\,\Omega)(2000\,\Omega)}{1\,\Omega+2000\,\Omega}=0.999500\,\Omega.
$$

The first source contribution is

$$
\begin{aligned}
v_{in,1}&=V_1\frac{R_{p1}}{5\,\Omega+R_{p1}},\\
v_{in,1}&=0.166597V_1\approx\frac16V_1.
\end{aligned}
$$

Suppressing $V_1$ instead gives

$$
\begin{aligned}
R_{p2}&=\frac{(5\,\Omega)(2000\,\Omega)}{5\,\Omega+2000\,\Omega}=4.987531\,\Omega,\\
v_{in,2}&=V_2\frac{R_{p2}}{1\,\Omega+R_{p2}},\\
v_{in,2}&=0.832986V_2\approx\frac56V_2.
\end{aligned}
$$

Adding the two contributions,

$$
v_{in}\approx\frac16V_1+\frac56V_2.
$$

The mix depends on the output resistances and input loading. Joining outputs can also drive current from one amplifier into the other. A summing amplifier provides a controlled way to combine signals, developed in [[FEEG1004 B4 - Operational Amplifiers]].

## 4. Relay contacts and coil operation

An **electromechanical relay** uses an electromagnet to move contacts, with a spring restoring the de-energised position. Normally open and normally closed describe that de-energised state. The common terminal belongs to a changeover contact, which connects it to one of two alternatives.

Poles count the separate switch circuits moved together. Throws count the alternative contact positions per pole. SPDT means one pole with two throws; DPST means two separate on/off contact sets, rather than one changeover switch.

The coil model is inductance in series with winding resistance. At DC steady state its ideal inductive voltage is zero, leaving the winding resistance to set current. The contacts have their own resistance and ratings, separate from the coil voltage rating.

For a resistive $1\,\mathrm{kW}$, $230\,\mathrm V$ AC spotlight, use RMS values and unity power factor:

$$
\begin{aligned}
I_{rms}&=\frac{P}{V_{rms}},\\
I_{rms}&=\frac{1000\,\mathrm W}{230\,\mathrm V}=4.3478\,\mathrm A.
\end{aligned}
$$

The relay chosen has an $8\,\mathrm A$ contact rating, $4.5\,\mathrm V$ nominal DC coil and $101\,\Omega$ coil resistance. These are catalogue values, not a complete assessment of contact inrush or coil operating limits.

## 5. Flyback current and the destination of stored energy

With a $5\,\mathrm V$ supply across the $101\,\Omega$ coil in DC steady state,

$$
I_0=\frac{5\,\mathrm V}{101\,\Omega}=49.505\,\mathrm{mA}.
$$

Opening the drive switch does not instantly remove this current. Without a suitable path, the voltage rises until another path conducts, such as an arc through the separating contacts. That arc heats and erodes the contacts, while excessive voltage can damage a semiconductor switch.

A **flyback diode** is connected across the coil with its cathode towards the positive supply connection. It is reverse-biased during normal energisation. After opening the switch, coil current keeps its original direction and returns through the diode, forming a local loop disconnected from the supply's positive terminal.

![[ee_a7_flyback.png|900]]

Let $R$ be winding resistance and $V_D$ the forward diode drop during decay. KVL around the local loop gives

$$
\begin{aligned}
v_L+Ri+V_D&=0,\\
L\frac{di}{dt}&=-Ri-V_D.
\end{aligned}
$$

Multiply by current:

$$
Li\frac{di}{dt}=-Ri^2-V_Di.
$$

Since $E_L=\tfrac12 Li^2$ for constant $L$,

$$
\frac{dE_L}{dt}=-Ri^2-V_Di.
$$

Stored magnetic energy decreases as winding heat and diode heat are produced. For an ideal zero-drop diode, the winding resistance dissipates the stored energy. The diode provides a controlled current path; it does not make the energy disappear at switch opening.

In the shown supply-side switch arrangement, the coil's upper terminal goes slightly below the lower terminal while the diode conducts. The open switch sees approximately supply voltage plus $V_D$. No numerical inductance or forward-drop model is specified for this example, so a numerical decay time or clamp voltage is not inferred.

## Worked examples

### Thévenin load check in both circuits

The circuit has $12\,\mathrm V$ and $6\,\mathrm V$ sources, resistors $1\,\Omega$, $2\,\Omega$, $4\,\Omega$ and $6\,\Omega$, and a $3\,\Omega$ load across A–B.

![[ee_a7_thevenin_example.png|900]]

Remove the load. To find $R_{TH}$, short both ideal voltage sources. The $1\,\Omega$ resistor is then bypassed. The $4\,\Omega$ and $6\,\Omega$ resistors are in series, and that path is parallel with $2\,\Omega$:

$$
\begin{aligned}
R_s&=4\,\Omega+6\,\Omega=10\,\Omega,\\
R_{TH}&=\frac{(2\,\Omega)(10\,\Omega)}{2\,\Omega+10\,\Omega}=\frac53\,\Omega.
\end{aligned}
$$

Restore both sources for $V_{TH}$. The $1\,\Omega$ resistor draws current but does not alter the voltage fixed by the ideal $12\,\mathrm V$ source. In the remaining perimeter loop, take clockwise current $I$:

$$
\begin{aligned}
12\,\mathrm V-(2\,\Omega)I-(4\,\Omega)I-6\,\mathrm V-(6\,\Omega)I&=0,\\
6\,\mathrm V-(12\,\Omega)I&=0,\\
I&=\frac{6\,\mathrm V}{12\,\Omega}=0.500\,\mathrm A.
\end{aligned}
$$

The open-circuit output is

$$
V_{TH}=12\,\mathrm V-(2\,\Omega)(0.500\,\mathrm A)=11.0\,\mathrm V.
$$

Reconnect the load to the equivalent:

$$
I_L=\frac{11\,\mathrm V}{(5/3)\,\Omega+3\,\Omega}=\frac{33}{14}\,\mathrm A=2.357143\,\mathrm A.
$$

To check the original loaded circuit independently, define clockwise mesh currents $J_1$ in the left load loop and $J_2$ in the right loop. The resistor across the ideal source still does not affect the load-loop voltages. With coefficients in ohms and source terms in volts,

$$
\begin{aligned}
12-2J_1-3(J_1-J_2)&=0,\\
-6-4J_2-6J_2-3(J_2-J_1)&=0,
\end{aligned}
$$

$$
\begin{pmatrix}5&-3\\-3&13\end{pmatrix}
\begin{pmatrix}J_1\\J_2\end{pmatrix}=\begin{pmatrix}12\\-6\end{pmatrix}.
$$

Python solves the original equations and the equivalent separately:

```python
import numpy as np
J1, J2 = np.linalg.solve([[5., -3.], [-3., 13.]], [12., -6.])
i_original = J1 - J2
i_equivalent = 11. / (5./3. + 3.)
assert np.isclose(i_original, i_equivalent)
# J1 = 2.46428571 A; J2 = 0.10714286 A
# Both load currents = 2.35714286 A
```

> [!check] Same load behaviour
> Both circuits give $I_L=2.357143\,\mathrm A$ and $V_L=(3\,\Omega)I_L=7.071429\,\mathrm V$. The check compares the original loaded network with its loaded equivalent, rather than reusing the equivalent twice.

### Forty-ohm load fed by two sources

This circuit has a $10\,\mathrm V$ source through $10\,\Omega$ and a $20\,\mathrm V$ source through $20\,\Omega$, feeding a shared $40\,\Omega$ load. Remove the load and zero both sources for the resistance:

$$
R_{TH}=\frac{(10\,\Omega)(20\,\Omega)}{10\,\Omega+20\,\Omega}=\frac{20}{3}\,\Omega.
$$

Restore the sources and take clockwise current around the open-load perimeter. With resistance coefficients in ohms and source terms in volts,

$$
\begin{aligned}
10-10I-20I-20&=0,\\
30I&=-10,\\
I&=-\frac13\,\mathrm A.
\end{aligned}
$$

The current actually flows anticlockwise. The left-hand path gives the open-circuit voltage:

$$
V_{TH}=10\,\mathrm V-(10\,\Omega)\left(-\frac13\,\mathrm A\right)=\frac{40}{3}\,\mathrm V.
$$

Reconnect the load:

$$
I_L=\frac{(40/3)\,\mathrm V}{40\,\Omega+(20/3)\,\Omega}=\frac27\,\mathrm A=0.285714\,\mathrm A.
$$

This matches the independent mesh solution of the original circuit in [[FEEG1004 A6 - Mesh Analysis#Two meshes solved by hand and in Python|A6's two-mesh example]].

### Superposition with opposing contributions

This circuit has $12\,\mathrm V$ and $9\,\mathrm V$ sources; find the left-to-right current through $3\,\Omega$. With the $9\,\mathrm V$ source shorted, the right-hand path is $2\,\Omega+2\,\Omega$, in parallel with $4\,\Omega$. Reduce towards the left input node:

$$
\begin{aligned}
R_{right}&=4\,\Omega\parallel4\,\Omega=2\,\Omega,\\
R_{branch}&=3\,\Omega+2\,\Omega=5\,\Omega,\\
R_{lower}&=2\,\Omega\parallel5\,\Omega=\frac{10}{7}\,\Omega,\\
V_{left}&=(12\,\mathrm V)\frac{(10/7)\,\Omega}{2\,\Omega+(10/7)\,\Omega}=5.00\,\mathrm V,\\
I_{12}&=\frac{5\,\mathrm V}{5\,\Omega}=1.00\,\mathrm A.
\end{aligned}
$$

With the $12\,\mathrm V$ source shorted, the left node sees $2\,\Omega\parallel2\,\Omega=1\,\Omega$. From the right node, the target path is $3\,\Omega+1\,\Omega=4\,\Omega$, parallel with the vertical $4\,\Omega$, giving $2\,\Omega$. The $9\,\mathrm V$ source feeds that combination through $4\,\Omega$:

$$
\begin{aligned}
V_{right}&=(9\,\mathrm V)\frac{2\,\Omega}{4\,\Omega+2\,\Omega}=3.00\,\mathrm V,\\
I_9&=-\frac{3\,\mathrm V}{4\,\Omega}=-0.750\,\mathrm A.
\end{aligned}
$$

The minus sign keeps the original left-to-right reference. Therefore

$$
I=I_{12}+I_9=1.00\,\mathrm A-0.750\,\mathrm A=0.250\,\mathrm A.
$$

### Superposition with a current source

This circuit has a $20\,\mathrm V$ source through $5\,\Omega$ to node A, a $10\,\Omega$ shunt at A, a $10\,\Omega$ link to node B, and a $20\,\Omega$ load at B. A $4\,\mathrm A$ current source injects current into B. Find downward load current.

With the current source opened, the lower network seen from A is

$$
\begin{aligned}
R_p&=10\,\Omega\parallel(10\,\Omega+20\,\Omega)=7.50\,\Omega,\\
V_{A,1}&=(20\,\mathrm V)\frac{7.5\,\Omega}{5\,\Omega+7.5\,\Omega}=12.0\,\mathrm V,\\
I_1&=\frac{12\,\mathrm V}{10\,\Omega+20\,\Omega}=0.400\,\mathrm A.
\end{aligned}
$$

For the second contribution the voltage source is shorted. The alternative path from B to ground is

$$
R_{alt}=10\,\Omega+(5\,\Omega\parallel10\,\Omega)=\frac{40}{3}\,\Omega.
$$

The current divider has the opposite path resistance in the numerator:

$$
\begin{aligned}
I_2&=(4\,\mathrm A)\frac{(40/3)\,\Omega}{(40/3)\,\Omega+20\,\Omega}=1.60\,\mathrm A,\\
I&=I_1+I_2=0.400\,\mathrm A+1.60\,\mathrm A=2.00\,\mathrm A.
\end{aligned}
$$

> [!check] Original-network KCL
> The full solution gives $V_B=(20\,\Omega)(2\,\mathrm A)=40\,\mathrm V$ and $V_A=20\,\mathrm V$. Current from B to A is $(40-20)\,\mathrm V/(10\,\Omega)=2\,\mathrm A$. The injected $4\,\mathrm A$ therefore splits into $2\,\mathrm A$ through the load and $2\,\mathrm A$ towards A.

### Indicator lamp in series with the relay coil

The lamp is specified at $5\,\mathrm V$, $60\,\mathrm{mA}$. Approximate its resistance by its hot operating value:

$$
R_{lamp}=\frac{5\,\mathrm V}{0.060\,\mathrm A}=83.333\,\Omega.
$$

At DC steady state, the coil's inductive voltage is zero. With a $5\,\mathrm V$ supply, the series circuit gives

$$
\begin{aligned}
I&=\frac{5\,\mathrm V}{101\,\Omega+83.333\,\Omega}=27.1248\,\mathrm{mA},\\
V_{coil}&=(101\,\Omega)(0.0271248\,\mathrm A)=2.73960\,\mathrm V.
\end{aligned}
$$

This is well below the stated nominal coil voltage, and too low to operate the relay. The hot-lamp approximation does not predict the exact lower-temperature resistance or the relay's actual pull-in threshold.

Putting the lamp in parallel with the coil gives both branches $5\,\mathrm V$, as assumed in the alternative design. If the coil fails open, a series indicator goes out, whereas a parallel indicator can remain lit even though the relay has released. If the indicator fails open, the series arrangement also interrupts the coil; the parallel arrangement can continue operating the relay. The preferred behaviour depends on what the indicator is intended to confirm.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A6 - Mesh Analysis]]
- Next: [[FEEG1004 B1 - Semiconductors and Diodes]]
- Concepts: [[Thevenin and Norton Equivalent Circuits]] · [[Superposition Theorem (Circuits)]] · [[Electromechanical Relays]] · [[Flyback Diode]]

## Sources

- `S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf`, pp. 3–31, 34–53; `FEEG1004 Lecture 2020-10-13 - 7a Thevenin.txt` (ll. 17–225); `FEEG1004 Lecture 2020-10-13 - 7b Superposition.txt` (ll. 1–108); `FEEG1004 Lecture 2020-10-13 - 7c Relays and circuit examples.txt` (ll. 1–123).
- `S1-W06 Thevenin and Superposition - Interactive.pdf`, pp. 7–21; `FEEG1004 Lecture 5.txt` (ll. 117–377). Its current-divider explanation is developed in A3. The index's automatic A3 assignment for `7b Superposition` does not match its actual A7 content.
- `Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors.pdf`, Q2; `Tutorial Sheet 02 - DC Circuit Analysis & Kirchhoff's Laws.pdf`, Q2, Q3 and Q5.
- All numerical results checked in Python, including the original/equivalent loaded circuits, both superposition exercises, exact amplifier weights and relay calculations. The flyback figure follows the source schematic without inventing an inductance or air-gap resistance.

## Self-study tasks

### Core

- [ ] Find the battery's ESR and charging behaviour (Tutorial Sheet 1 Q2). → [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q2: Sam's car battery (13 V, nominally 10 mΩ ESR)|Tutorial 1 Q2]].
- [ ] Calculate and plot current as a function of the current source (Tutorial Sheet 2 Q2). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q2: Superposition for ia (50 Ω) with a current source Is and a 12 V source behind 200 Ω|Tutorial 2 Q2]].
- [ ] Find the A–B Thévenin equivalent (Tutorial Sheet 2 Q3). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q3: Thévenin equivalent at A–B|Tutorial 2 Q3]].
- [ ] Find the initial switch-gap voltage and discuss the real spark path (Tutorial Sheet 2 Q5). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q5: Opening the switch on a 5 mH inductor fed from 12 V with 0.2 Ω internal resistance|Tutorial 2 Q5]].
- [ ] Find the open-terminal equivalent with the $4\,\Omega$ branch (7a transcript ll. 188–225). → [[#Open terminals can still have a voltage]].
- [ ] Find the equivalent and load current in the $40\,\Omega$ circuit (Lecture 5 transcript ll. 186–271). → [[#Forty-ohm load fed by two sources]].
- [ ] Solve the current-source superposition example (Lecture 5 transcript ll. 322–377). → [[#Superposition with a current source]].
- [ ] Explain why the series indicator arrangement fails (7c transcript ll. 43–75), and compare open-circuit failures (ll. 76–88). → [[#Indicator lamp in series with the relay coil]].

### Further practice

- [ ] Derive the straight-line terminal characteristic and its intercepts (7a transcript ll. 57–85). → [[#1. Source resistance and terminal behaviour]]; $V_{out}=0$ gives $I_{short}=V_{TH}/R_{TH}$ for positive finite $R_{TH}$.
- [ ] Complete the recorded $12\,\mathrm V$/$9\,\mathrm V$ superposition exercise (recorded p. 36; 7b transcript ll. 15–34). → [[#Superposition with opposing contributions]].
- [ ] Explain where the coil energy goes after the switch opens (7c transcript ll. 92–123). → [[#5. Flyback current and the destination of stored energy]].

## Transcript and slide slips

### Source slope

> [!warning] The voltage–current slope is negative
> Where: [[#1. Source resistance and terminal behaviour]]
> Recorded p. 7 and 7a transcript l. 42 call the graph's gradient $R_{ESR}$. With delivered current positive along the horizontal axis, $V_{out}=V_b-I_{out}R_{ESR}$ has gradient $-R_{ESR}$. Resistance is the magnitude of that downward slope.

### Relay contact description

> [!warning] DPST is not a changeover contact
> Where: [[#4. Relay contacts and coil operation]]
> The 7c transcript ll. 40–42 describes the listed DPST relay as one switch with normally open and normally closed contacts. DPST means two single-throw switch circuits. The generic SPDT changeover drawing and the listed DPST device must be distinguished.

### Relay voltage arithmetic

> [!warning] A doubled supply does not divide equally
> Where: [[#Indicator lamp in series with the relay coil]]
> The 7c transcript ll. 56–57 suggests $10\,\mathrm V$ gives $5\,\mathrm V$ across both series components. With its own fixed hot-lamp model, the voltages are $10(101)/(101+83.333)=5.4792\,\mathrm V$ across the coil and $4.5208\,\mathrm V$ across the lamp. Actual operation needs the lamp characteristic and coil limits. Recorded p. 52 also prints $5/101=49.6\,\mathrm{mA}$; the calculation is $49.505\,\mathrm{mA}$, or $49.5\,\mathrm{mA}$ to three significant figures.
