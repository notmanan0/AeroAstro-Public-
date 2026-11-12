---
title: FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers
module: FEEG1004 Electronics
type: topic
stream: 'Part A: Electrical Fundamentals and DC Circuits'
order: 3
tags:
- feeg1004
- fundamentals
- dc-circuits
- ohms-law
- kirchhoff
- potential-divider
- resistors
aliases:
- Lecture 3a-3b
- Circuit laws
- KCL and KVL
- Potential divider
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A1 - Electrostatics, Potential and Current]]"
next_topics:
- "[[FEEG1004 A4 - Capacitors]]"
key_concepts:
- "[[Ohm's Law and Resistivity]]"
- "[[Kirchhoff's Current and Voltage Laws]]"
- "[[Series and Parallel Resistors]]"
- "[[Potential Divider]]"
- "[[Current Divider]]"
- "[[Hydraulic Analogy for Circuits]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]"
sources:
- 02 - Sources/S1 Fundamentals/S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf
- 02 - Sources/S1 Fundamentals/S1-W04 Circuits and Capacitors - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-09-04 - 3a Circuits KCL, resistors FEEG1004.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-09-04 - 3b KVL, potential dividers FEEG1004.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 5.txt
coverage: 3a Circuits KCL, resistors (ll. 1-418); 3b KVL, potential dividers (ll. 1-187); Lecture 5 (ll. 18-116, 273-300, 378-440)
---


# FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers

> [!abstract] Summary
> Circuit analysis uses conservation of charge and energy together with each component's voltage–current law. For ideal resistors, $V=IR$ leads to series and parallel equivalents and to potential and current dividers. Divider formulas depend on the actual connections: drawing current from a divider output changes its effective resistance and output voltage.

> [!summary]- Exam use: quick path
> - **Use it when:** finding DC currents, node voltages, resistor values or dissipated power.
> - **Assumptions:** ideal wires and sources unless internal resistance is shown; fixed, positive resistances; negligible output current for an unloaded potential divider.
> - **Method:** 1. Mark nodes, polarities and reference currents. 2. Combine genuine series/parallel groups. 3. Apply KCL, KVL and $V=IR$. 4. Recover internal currents and voltages. 5. Check units and power balance.
> - **Common mistakes:** putting the branch's own resistance on top of the current-divider ratio; using the unloaded voltage-divider formula after connecting a load.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q4: Deriving series and parallel resistance|Tutorial 1 Q4]]

In a circuit model, each component is described by the current through its terminals and the voltage across them. This avoids solving the electric and magnetic fields throughout space. The approximation is useful when neglected coupling between components is small; at higher frequencies, additional capacitance and inductance may be needed in the model.

Charge flows around the connected paths without being used up by resistors. A resistor transfers electrical energy to heat, so current continues through it while electric potential falls in the direction of conventional current. At a junction the current can divide, but the total arriving current must equal the total leaving current.

The hydraulic analogy maps voltage difference to pressure difference and current to volume flow rate. A narrow resistive passage needs a pressure difference to sustain flow, just as a resistor needs a voltage difference. For laminar hydraulic flow the equations have the same form; current corresponds to volume flow rate, rather than fluid speed.

## 1. Nodes, sources and signs

A **node** is a set of points joined by ideal wires, all at the same potential. Ground is the selected zero-voltage reference; the symbol need not indicate a physical connection to Earth. Moving a component in the drawing does not change the circuit if its terminal connections remain the same.

An ideal voltage source fixes its terminal voltage while its current is determined by the rest of the circuit. An ideal current source fixes its current while its voltage is determined by the circuit. A short circuit fixes zero voltage; an open circuit fixes zero current. These ideal models do not specify practical current or voltage limits.

Use the **passive sign convention**: define current as entering the terminal labelled positive for the component voltage. Then $P=VI$ is power absorbed by that component. Positive $P$ means energy enters it; negative $P$ means it supplies energy. For a positive resistor with this convention,

$$
V=IR.
$$

The voltage arrow points towards the terminal defined as positive. In a KVL traversal, crossing a component from negative to positive is a rise; crossing positive to negative is a drop. A resistor traversed in its reference-current direction contributes $-IR$ to a sum of rises.

Choose a current direction before solving. A negative result means the physical current is opposite to that arrow; it does not invalidate the equations.

An ideal voltmeter draws no current and is connected across two nodes. An ideal ammeter has zero voltage drop and is inserted in series with the branch whose current is required.

## 2. Resistance and power

For a uniform conductor of length $L$, cross-sectional area $A$ and resistivity $\rho$,

$$
R=\frac{\rho L}{A}.
$$

Resistivity has units $\Omega\,\mathrm m$. Conductivity is its reciprocal, $\sigma=1/\rho$, measured in $\mathrm{S\,m^{-1}}$, giving $R=L/(\sigma A)$. Increasing length increases resistance; increasing area reduces it.

An ideal resistor has fixed $R$. A real metal's resistance generally increases as it heats. The stated copper coefficient is approximately $0.4\%$ per kelvin over a limited temperature range. A glowing filament cools after switching off, so its resistance falls; a constant-resistance bulb model leaves out that thermal change.

Starting from absorbed power,

$$
P=VI,
$$

and substituting $V=IR$,

$$
P=(IR)I,
$$

so

$$
P=I^2R.
$$

Alternatively substitute $I=V/R$:

$$
P=V\left(\frac{V}{R}\right),
$$

which gives

$$
P=\frac{V^2}{R}.
$$

Both expressions are non-negative for a positive resistor. They are resistor formulas, while $P=VI$ also applies to other two-terminal elements with consistent signs.

## 3. Kirchhoff's laws

Kirchhoff's current law follows from charge conservation at an ideal circuit node. If $I_1,I_2,I_3$ enter and $I_4,I_5$ leave,

$$
I_1+I_2+I_3=I_4+I_5.
$$

Putting everything on one side,

$$
I_1+I_2+I_3-I_4-I_5=0.
$$

Thus the algebraic sum of currents is zero when entering and leaving currents have opposite signs. Adding unsigned magnitudes of entering currents and setting that sum to zero would be incorrect.

Kirchhoff's voltage law sums the signed voltage changes around a closed path. For a source feeding a resistor, traverse clockwise from the negative source terminal:

$$
V_s-V_R=0.
$$

Substitute the resistor law:

$$
V_s-IR=0.
$$

Rearranging and dividing by $R$ gives

$$
\begin{aligned}
IR&=V_s,\\
I&=\frac{V_s}{R}.
\end{aligned}
$$

KVL here applies to the lumped circuit model. An externally changing magnetic flux linking a loop must be represented by its induced EMF, rather than omitted from the voltage equation.

## 4. Deriving series and parallel resistance

### Resistors in series

Series resistors share intermediate nodes with no current drawn elsewhere, so KCL gives the same current through each. KVL gives the total voltage across three resistors:

$$
V=V_1+V_2+V_3.
$$

Apply Ohm's law to each:

$$
V=IR_1+IR_2+IR_3.
$$

Factor out the common current:

$$
V=I(R_1+R_2+R_3).
$$

The equivalent resistor must have the same terminal behaviour, $V=IR_s$, hence

$$
R_s=R_1+R_2+R_3.
$$

### Resistors in parallel

Parallel resistors bridge the same two nodes, so their voltages are equal. KCL gives

$$
I=I_1+I_2+I_3.
$$

Using the common voltage,

$$
I=\frac{V}{R_1}+\frac{V}{R_2}+\frac{V}{R_3}.
$$

Replace total current by $V/R_p$:

$$
\frac{V}{R_p}=V\left(\frac1{R_1}+\frac1{R_2}+\frac1{R_3}\right).
$$

Comparing the voltage–current coefficients gives

$$
\frac1{R_p}=\frac1{R_1}+\frac1{R_2}+\frac1{R_3}.
$$

For two resistors, combine the fractions:

$$
\frac1{R_p}=\frac{R_1+R_2}{R_1R_2}.
$$

Taking reciprocals,

$$
R_p=\frac{R_1R_2}{R_1+R_2}.
$$

For positive finite resistances, this is smaller than either branch resistance. A zero-resistance wire in parallel with a resistor makes the terminal voltage zero and bypasses it. This explains why a shorted bulb receives no power in the ideal model.

## 5. Deriving both divider formulas

![[ee_a3_divider_circuits.png|900]]

### Potential divider

Use the labels shown in the figure: $R_2$ is above the tap and $R_1$ is below it. Measure $V_{out}$ across $R_1$, positive at the tap. Assume negligible current is drawn from the tap, so both resistors carry the same downward current $I$.

KVL gives

$$
V_{in}-IR_2-IR_1=0.
$$

Collecting the resistor drops,

$$
V_{in}=I(R_1+R_2).
$$

Divide by the total resistance:

$$
I=\frac{V_{in}}{R_1+R_2}.
$$

Ohm's law across the lower resistor gives

$$
V_{out}=IR_1.
$$

Substitute the current:

$$
V_{out}=\frac{V_{in}}{R_1+R_2}R_1.
$$

Therefore

$$
V_{out}=V_{in}\frac{R_1}{R_1+R_2}.
$$

The numerator is the resistor across which voltage is measured. If the labels are swapped and the output is taken across $R_2$, the numerator becomes $R_2$. The physical rule is unchanged.

For a sensor resistance $R_s$ below a fixed resistance $R_a$, the same derivation gives $V_{out}=V_{in}R_s/(R_s+R_a)$. This is not proportional to $R_s$ because the denominator also changes. An ideal buffer draws no input current, preserving the unloaded divider voltage while supplying current at its output.

### Loaded potential divider

A load $R_L$ connected from the tap to ground is in parallel with the lower resistor. Write

$$
R_b=\frac{R_1R_L}{R_1+R_L}.
$$

The upper resistor and this equivalent lower resistance are in series, so

$$
V_{out}=V_{in}\frac{R_b}{R_2+R_b}.
$$

The unloaded result is recovered as $R_L$ becomes large compared with $R_1$. A finite load reduces $R_b$ and therefore reduces $V_{out}$ for a positive supply and positive resistances.

### Current divider

Let total current $I$ enter parallel resistors $R_1,R_2$, with branch currents $I_1,I_2$ in the same direction. Their common voltage is $V$. Start with KCL and substitute Ohm's law:

$$
\begin{aligned}
I&=I_1+I_2,\\
I&=\frac{V}{R_1}+\frac{V}{R_2},\\
I&=V\frac{R_1+R_2}{R_1R_2}.
\end{aligned}
$$

Solve for the common voltage:

$$
V=I\frac{R_1R_2}{R_1+R_2}.
$$

The current in the first branch is

$$
I_1=\frac{V}{R_1}.
$$

Substituting and then cancelling $R_1$,

$$
\begin{aligned}
I_1&=\frac{I R_1R_2}{R_1(R_1+R_2)},\\
I_1&=I\frac{R_2}{R_1+R_2}.
\end{aligned}
$$

Interchanging the branch labels gives $I_2=IR_1/(R_1+R_2)$. The opposite resistance appears on top because the branch's own resistance cancelled. The lower-resistance branch takes the larger current.

## Worked examples

### Limiting an LED current

The specified LED operating point is $20\,\mathrm{mA}$ at $2\,\mathrm V$, supplied from $12\,\mathrm V$. The LED is modelled by that operating-point voltage, rather than as an ohmic resistor. KVL gives

$$
\begin{aligned}
V_R&=V_s-V_{LED},\\
V_R&=12\,\mathrm V-2\,\mathrm V=10\,\mathrm V.
\end{aligned}
$$

The series resistor carries the LED current:

$$
\begin{aligned}
R&=\frac{V_R}{I},\\
R&=\frac{10\,\mathrm V}{20\times10^{-3}\,\mathrm A}=500\,\Omega.
\end{aligned}
$$

Its power is $P_R=(10\,\mathrm V)(0.020\,\mathrm A)=0.200\,\mathrm W$. The LED receives $P_{LED}=(2\,\mathrm V)(0.020\,\mathrm A)=0.040\,\mathrm W$. A nominal $0.25\,\mathrm W$ resistor is above the calculated dissipation, though a practical design also needs operating margin.

> [!check] Power balance
> Source output is $(12\,\mathrm V)(0.020\,\mathrm A)=0.240\,\mathrm W$, equal to $0.200+0.040=0.240\,\mathrm W$ absorbed. Only $0.040/0.240=16.7\%$ reaches the LED electrically; this is not its optical efficiency.

### Loading the bulb divider

A $10\,\mathrm V$ ideal source feeds two $2\,\Omega$ bulbs, modelled as fixed resistors. Bulb A is the upper series resistor and bulb B is the lower resistor. Initially,

$$
V_B=(10\,\mathrm V)\frac{2\,\Omega}{2\,\Omega+2\,\Omega}=5.00\,\mathrm V.
$$

With a third $2\,\Omega$ bulb connected in parallel with B, the lower equivalent becomes

$$
R_b=\frac{(2\,\Omega)(2\,\Omega)}{2\,\Omega+2\,\Omega}=1.00\,\Omega.
$$

The new output voltage is

$$
V_B=(10\,\mathrm V)\frac{1\,\Omega}{2\,\Omega+1\,\Omega}=3.333\,\mathrm V.
$$

The total source current is

$$
I_A=\frac{10\,\mathrm V}{3\,\Omega}=3.333\,\mathrm A.
$$

Each lower branch takes $I_B=(3.333\,\mathrm V)/(2\,\Omega)=1.667\,\mathrm A$. Before loading, both bulbs carried $(10\,\mathrm V)/(4\,\Omega)=2.50\,\mathrm A$. A brightens while B dims in the fixed-resistance model. The unloaded divider formula would incorrectly retain $5\,\mathrm V$ because the tap now supplies substantial load current.

> [!check] Current split
> The two lower currents add to $1.667+1.667=3.333\,\mathrm A$, matching the upper current before rounding. Equal lower resistances divide current equally, while the loaded output remains below its original $5.00\,\mathrm V$.

### Reducing and recovering a resistor network

The network has a $120\,\mathrm V$ source and $500\,\Omega$ series resistor feeding P–S. Between P and R, a $5\,\mathrm{k\Omega}+10\,\mathrm{k\Omega}$ path is parallel with $10\,\mathrm{k\Omega}$. R–S is $15\,\mathrm{k\Omega}$; a separate $20\,\mathrm{k\Omega}$ bridges P–S.

Reduce from the innermost series pair:

$$
\begin{aligned}
R_{PQR}&=5\,\mathrm{k\Omega}+10\,\mathrm{k\Omega}=15\,\mathrm{k\Omega},\\
R_{PR}&=\frac{(15\,\mathrm{k\Omega})(10\,\mathrm{k\Omega})}{15\,\mathrm{k\Omega}+10\,\mathrm{k\Omega}}=6\,\mathrm{k\Omega},\\
R_{PRS}&=6\,\mathrm{k\Omega}+15\,\mathrm{k\Omega}=21\,\mathrm{k\Omega},\\
R_{PS}&=\frac{(20\,\mathrm{k\Omega})(21\,\mathrm{k\Omega})}{20\,\mathrm{k\Omega}+21\,\mathrm{k\Omega}}=10.24390\,\mathrm{k\Omega}.
\end{aligned}
$$

The input divider now gives

$$
V_{PS}=(120\,\mathrm V)\frac{10.24390\,\mathrm{k\Omega}}{0.500\,\mathrm{k\Omega}+10.24390\,\mathrm{k\Omega}}=114.415\,\mathrm V.
$$

Undo the reduction of the $21\,\mathrm{k\Omega}$ branch to recover its current:

$$
I_{RS}=\frac{114.415\,\mathrm V}{21\,\mathrm{k\Omega}}=5.44835\,\mathrm{mA}.
$$

Then

$$
V_{RS}=(5.44835\,\mathrm{mA})(15\,\mathrm{k\Omega})=81.7253\,\mathrm V.
$$

Keeping the unreduced nodes labelled makes it possible to recover quantities hidden by an equivalent resistor. Early rounding explains the small difference from the displayed $5.43\,\mathrm{mA}$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]
- Next: [[FEEG1004 A4 - Capacitors]]
- Concepts: [[Ohm's Law and Resistivity]] · [[Kirchhoff's Current and Voltage Laws]] · [[Series and Parallel Resistors]] · [[Potential Divider]] · [[Current Divider]] · [[Hydraulic Analogy for Circuits]]
- Loading: [[Loading Effect and Buffering]]

## Sources

- `S1-W04-3ab Circuits KCL KVL Resistors - Recorded.pdf`, pp. 3–30; `FEEG1004 Lecture 2020-09-04 - 3a Circuits KCL, resistors FEEG1004.txt` (ll. 1–418); `FEEG1004 Lecture 2020-09-04 - 3b KVL, potential dividers FEEG1004.txt` (ll. 1–187).
- `S1-W04 Circuits and Capacitors - Interactive.pdf`, pp. 2–3, 6–12. Capacitor material is developed in A4.
- `FEEG1004 Lecture 5.txt` (ll. 18–116: loaded bulb circuit; ll. 273–300: both dividers; ll. 378–440: source and bulb checks). Its Thévenin and superposition content belongs in A7, despite the index's automatic A3 assignment.
- `Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors.pdf`, Q2–Q4. All numerical examples and checks computed in Python with unrounded intermediate values.

## Self-study tasks

### Core

- [ ] Derive the three-resistor series and parallel equivalents, naming the laws used (Tutorial Sheet 1 Q4; 3a transcript ll. 189–190). → [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q4: Deriving series and parallel resistance|Tutorial 1 Q4]]; [[#4. Deriving series and parallel resistance]].
- [ ] Solve the resistor ladder from its voltmeter reading (Tutorial Sheet 1 Q3). → [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q3: Resistor ladder with a 5 V voltmeter reading|Tutorial 1 Q3]].
- [ ] Find the battery resistance, wire diameter and charging current (Tutorial Sheet 1 Q2). → [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q2: Sam's car battery (13 V, nominally 10 mΩ ESR)|Tutorial 1 Q2]].
- [ ] Reduce the P–S network and recover the R–S quantities (3b transcript ll. 135–186). → [[#Reducing and recovering a resistor network]].
- [ ] Explain why adding the third bulb makes A brighter and B dimmer (Lecture 5 transcript ll. 69–102). → [[#Loading the bulb divider]].

### Further practice

- [ ] Re-derive both divider formulas without memorising the numerators (suggested, not lecturer-set). → [[#5. Deriving both divider formulas]].
- [ ] Explain why a shorted resistor dissipates no power in the ideal-wire model (3a transcript ll. 404–417). → [[#4. Deriving series and parallel resistance]].

## Transcript and slide slips

### Material units

> [!warning] Resistivity and conductivity units
> Where: [[#2. Resistance and power]]
> The 3a transcript ll. 120–122 calls conductivity siemens, and ll. 372–380 calls resistivity ohms per metre. Recorded p. 9 gives the correct units: conductivity is $\mathrm{S\,m^{-1}}$ and resistivity is $\Omega\,\mathrm m$. These are material properties, distinct from conductance and resistance of a whole component.

### Conductivity ordering

> [!warning] Silver has the lower resistivity in the table
> Where: [[#2. Resistance and power]]
> The 3a transcript ll. 372–375 calls copper more conductive than silver and gold. Recorded p. 19 lists resistivities at $20\,^{\circ}\mathrm C$ of $1.72\times10^{-8}\,\Omega\,\mathrm m$ for copper, $1.62\times10^{-8}\,\Omega\,\mathrm m$ for silver and $2.44\times10^{-8}\,\Omega\,\mathrm m$ for gold. Since conductivity is reciprocal resistivity, the table puts silver above copper, then gold.
