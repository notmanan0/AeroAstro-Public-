---
title: FEEG1004 A4 - Capacitors
module: FEEG1004 Electronics
type: topic
stream: 'Part A: Electrical Fundamentals and DC Circuits'
order: 4
tags:
- feeg1004
- fundamentals
- capacitor
- capacitance
- energy-storage
- transients
aliases:
- Lecture 4
- Capacitors
- Q = CV
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A1 - Electrostatics, Potential and Current]]"
- "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"
next_topics:
- "[[FEEG1004 A5 - Inductors and Electrical Resonance]]"
key_concepts:
- "[[Capacitance]]"
- "[[RC and RL Transients]]"
- "[[Hydraulic Analogy for Circuits]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"
sources:
- 02 - Sources/S1 Fundamentals/S1-W04-4 Capacitors - Recorded.pdf
- 02 - Sources/S1 Fundamentals/S1-W04 Circuits and Capacitors - Interactive.pdf
- 02 - Sources/S1 Fundamentals/S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-09-11.txt
coverage: 4 Capacitors, 11 September 2020 (ll. 1-165); W04 interactive pp. 13-17 and W05 interactive p. 7 provide additional circuit exercises without a matching interactive transcript
---


# FEEG1004 A4 - Capacitors

> [!abstract] Summary
> A capacitor stores energy in the electric field between separated charges, with $Q=CV$ for constant capacitance. Its circuit law is $i=C\,dv_C/dt$, so finite current changes voltage continuously. Charging through a resistor gives $v_C=V_s(1-e^{-t/RC})$ from an uncharged initial state, and the stored energy is $E_C=\tfrac12 CV_C^2$.

> [!summary]- Exam use: quick path
> - **Use it when:** finding stored charge or energy, initial/final circuit states, or a capacitor's voltage during charging.
> - **Assumptions:** ideal, constant capacitance; finite current for voltage continuity; constant source and resistance for the RC exponential; initially uncharged unless stated otherwise.
> - **Method:** 1. Define capacitor voltage and current into its positive terminal. 2. Find the initial voltage and DC final circuit. 3. Apply $i=C\,dv_C/dt$ and KVL/KCL. 4. Use the initial condition to fix the integration constant. 5. Check limits and $\tau=RC$.
> - **Common mistakes:** setting capacitor voltage to zero at every switching event; treating a constant-current source as though it sets a final charging voltage.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q4: Capacitor and inductor steady states and transients|Tutorial 2 Q4]]

A capacitor has two conducting plates separated by an insulating gap. Connecting it to a source removes electrons from one plate and supplies electrons to the other. The plates acquire equal and opposite charges, creating an electric field between them. The energy used to separate the charges is stored in that field.

As charge builds, the capacitor's voltage rises and opposes further charging from a fixed-voltage source. A series resistor determines how quickly the charge can move. Once the circuit reaches DC steady state, the ideal capacitor carries no current, but it can retain a non-zero voltage and stored energy.

The hydraulic model is an elastic membrane across a pipe. Flow stretches the membrane and increases the pressure difference needed to stretch it further. Fluid does not cross the membrane, just as conducting charge does not cross an ideal capacitor's dielectric. The two external terminal currents still form part of the same charging circuit.

## 1. Capacitance and plate geometry

**Capacitance** is charge transferred per unit voltage. For an ideal capacitor of constant $C$,

$$
Q=CV_C.
$$

Here $Q$ is the charge on the plate labelled positive for $V_C$; the other plate has charge $-Q$. The capacitor as a whole need not have gained net charge. Rearranging,

$$
C=\frac{Q}{V_C},
$$

so a farad is a coulomb per volt, $1\,\mathrm F=1\,\mathrm{C\,V^{-1}}$. Distinguish the symbol $C$ for capacitance from $\mathrm C$, the unit of charge.

For parallel plates of overlap area $A$ separated by $d$, with a uniform dielectric and negligible edge fields, the plate model gives

$$
C=\frac{\varepsilon A}{d}.
$$

Permittivity $\varepsilon$ describes the material in the gap. Larger area or permittivity increases capacitance; increasing separation reduces it. This geometry relation specifies the device capacitance before using $Q=CV_C$ in the circuit.

Reducing the gap also increases the field for a given voltage. Dielectric breakdown limits the voltage a real capacitor can withstand, so capacitance and voltage rating are separate design quantities. An isolated ideal capacitor retains its charge; real leakage and breakdown limit that idealisation.

## 2. Deriving the current–voltage law

Use the passive sign convention: $i$ enters the plate defined as positive for $v_C$. For constant capacitance, differentiate the charge relation:

$$
\frac{dQ}{dt}=\frac{d(Cv_C)}{dt},
$$

$$
\frac{dQ}{dt}=C\frac{dv_C}{dt}.
$$

Current is the rate of change of this plate charge, giving

$$
i=C\frac{dv_C}{dt}.
$$

Dividing by $C$ and integrating between specified times,

$$
\frac{dv_C}{dt}=\frac{i}{C},
$$

$$
\int_{v_C(0)}^{v_C(t)}dv_C=\frac1C\int_0^t i(t')\,dt',
$$

$$
v_C(t)=v_C(0)+\frac1C\int_0^t i(t')\,dt'.
$$

The initial voltage is part of the solution. Omitting it implicitly assumes an initially uncharged capacitor. For finite current over an interval tending to zero, the integral tends to zero, so capacitor voltage is continuous through switching:

$$
v_C(0^+)=v_C(0^-).
$$

This condition does not require the voltage to be zero. An ideal impulsive current is an exception to the finite-current assumption.

At DC steady state, $dv_C/dt=0$ and therefore $i=0$. Replace the capacitor branch by an open circuit to solve the remaining network, then recover the voltage between its terminals.

## 3. Deriving the stored energy

With current entering the positive terminal, instantaneous absorbed power is

$$
p=v_Ci.
$$

For charging from zero voltage, integrate this power:

$$
E_C=\int_0^t v_Ci\,dt'.
$$

Substitute the capacitor current law:

$$
E_C=\int_0^t Cv_C\frac{dv_C}{dt'}\,dt'.
$$

Change the integration variable to capacitor voltage:

$$
E_C=C\int_0^{V_C}v\,dv.
$$

Integrating,

$$
E_C=C\left[\frac{v^2}{2}\right]_0^{V_C},
$$

$$
E_C=\frac12 CV_C^2.
$$

Using $V_C=Q/C$ gives

$$
E_C=\frac12 C\left(\frac{Q}{C}\right)^2,
$$

$$
E_C=\frac{Q^2}{2C}.
$$

Equivalently $E_C=\tfrac12 QV_C$. The factor of one half arises because the charging voltage rises from zero to its final value. Multiplying final charge by final voltage would overestimate the stored energy.

## 4. Deriving RC charging from the differential equation

A constant source $V_s>0$ is connected to an initially uncharged capacitor through a resistor $R>0$, with current defined from the source through the resistor into the capacitor's positive plate. KVL gives

$$
V_s-Ri-v_C=0.
$$

Substitute $i=C\,dv_C/dt$:

$$
V_s-RC\frac{dv_C}{dt}-v_C=0.
$$

Rearrange to isolate the derivative:

$$
RC\frac{dv_C}{dt}=V_s-v_C.
$$

For the charging interval $v_C<V_s$, separate the variables:

$$
\frac{dv_C}{V_s-v_C}=\frac{dt}{RC}.
$$

Integrate both sides:

$$
\int\frac{dv_C}{V_s-v_C}=\int\frac{dt}{RC},
$$

$$
-\ln\left(\frac{V_s-v_C}{V_s}\right)=\frac{t}{RC}+K.
$$

The logarithm has a dimensionless argument. At $t=0$, $v_C=0$, so the integration constant satisfies

$$
-\ln(1)=K,
$$

$$
K=0.
$$

Multiply the integrated equation by minus one:

$$
\ln\left(\frac{V_s-v_C}{V_s}\right)=-\frac{t}{RC}.
$$

Exponentiate:

$$
\frac{V_s-v_C}{V_s}=e^{-t/(RC)}.
$$

Multiply by $V_s$:

$$
V_s-v_C=V_se^{-t/(RC)}.
$$

Hence

$$
v_C(t)=V_s\left(1-e^{-t/(RC)}\right).
$$

Recover the resistor current from KVL:

$$
i(t)=\frac{V_s-v_C(t)}{R},
$$

$$
i(t)=\frac{V_s}{R}e^{-t/(RC)}.
$$

The **time constant** is $\tau=RC$, measured in seconds. Its dimensions are $\Omega\,\mathrm F=\mathrm s$. At one time constant,

$$
v_C(\tau)=V_s(1-e^{-1})=0.63212V_s.
$$

This is $63.2\%$ of the final voltage. Current has fallen to $e^{-1}=36.8\%$ of its initial value. At $5\tau$, voltage is $99.326\%$ of the final value; reaching the exact final value is an asymptotic limit.

![[ee_a4_capacitor_charging.png|900]]

The plotted RC values illustrate the shape. The initial voltage is zero, initial current is $V_s/R$ and initial voltage gradient is $V_s/(RC)$. At long times, voltage tends to $V_s$ and current tends to zero.

### A different initial voltage

For $v_C(0)=V_0$, use the same differential equation with $u=V_s-v_C$. Then $du=-dv_C$, giving

$$
\frac{du}{u}=-\frac{dt}{RC},
$$

$$
\int_{V_s-V_0}^{u(t)}\frac{du}{u}=-\int_0^t\frac{dt'}{RC},
$$

$$
\ln\left|\frac{u(t)}{V_s-V_0}\right|=-\frac{t}{RC},
$$

$$
u(t)=(V_s-V_0)e^{-t/(RC)},
$$

$$
v_C(t)=V_s+(V_0-V_s)e^{-t/(RC)}.
$$

The equilibrium case $V_0=V_s$ is the constant solution. For discharge through $R$ with $V_s=0$, this result reduces to $v_C=V_0e^{-t/(RC)}$; the capacitor releases energy as resistor heat.

## 5. Constant-current and alternating-current behaviour

For a constant current $I_0$, the integral law becomes

$$
v_C(t)=V_0+\frac1C\int_0^t I_0\,dt',
$$

$$
v_C(t)=V_0+\frac{I_0t}{C}.
$$

The voltage is a straight ramp. Unlike resistor charging from a fixed-voltage source, an ideal non-zero current source gives no finite final voltage. A real current source eventually reaches its voltage limit, or a component exceeds its rating.

Alternating current repeatedly reverses the charging direction. In the series capacitor-and-lamp model, increasing frequency reduces the time available for charge to accumulate before reversal, so the capacitor impedes the current less. For the fixed source amplitude and idealised lamp in the question, the lamp is brighter at higher frequency. Quantitative sinusoidal analysis is developed in [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]].

## Worked examples

### Charging a capacitor with a current source

A constant current $I=1\,\mathrm{mA}$ charges an initially uncharged capacitor $C=5\,\mathrm{\mu F}$ for $t=5\,\mathrm s$. The transferred charge is

$$
Q=It,
$$

$$
Q=(1\times10^{-3}\,\mathrm A)(5\,\mathrm s)=5\times10^{-3}\,\mathrm C.
$$

The final voltage is

$$
V_C=\frac{5\times10^{-3}\,\mathrm C}{5\times10^{-6}\,\mathrm F}=1000\,\mathrm V.
$$

Then

$$
E_C=\frac12(5\times10^{-6}\,\mathrm F)(1000\,\mathrm V)^2=2.50\,\mathrm J.
$$

> [!check] Average charging voltage
> The ramp rises from $0\,\mathrm V$ to $1000\,\mathrm V$, giving average voltage $500\,\mathrm V$. Source work is $(500\,\mathrm V)(0.001\,\mathrm A)(5\,\mathrm s)=2.50\,\mathrm J$, equal to stored energy in the ideal circuit.

### RC response in Tutorial 2

Tutorial Sheet 2 Q4(b) gives $V_s=1\,\mathrm V$, $R=5\,\Omega$ and $C=1\,\mathrm{\mu F}$, initially uncharged. Its time constant is

$$
\tau=(5\,\Omega)(1\times10^{-6}\,\mathrm F)=5.00\,\mathrm{\mu s}.
$$

At one time constant,

$$
v_C(5\,\mathrm{\mu s})=(1\,\mathrm V)(1-e^{-1})=0.63212\,\mathrm V,
$$

$$
i(5\,\mathrm{\mu s})=\frac{1\,\mathrm V}{5\,\Omega}e^{-1}=0.073576\,\mathrm A.
$$

Initially $i(0^+)=(1\,\mathrm V)/(5\,\Omega)=0.200\,\mathrm A$. In DC steady state $v_C=1\,\mathrm V$ and $i=0\,\mathrm A$, so

$$
E_C(\infty)=\frac12(1\times10^{-6}\,\mathrm F)(1\,\mathrm V)^2=0.500\,\mathrm{\mu J}.
$$

> [!check] KVL at one time constant
> The resistor drop is $(5\,\Omega)(0.073576\,\mathrm A)=0.36788\,\mathrm V$. Adding the capacitor's $0.63212\,\mathrm V$ recovers the $1.00000\,\mathrm V$ supply, to rounding.

### Charge after the rest of the circuit settles

The W5 exercise has a $2.5\,\mathrm V$ source with $0.5\,\Omega$ internal resistance, a $2\,\Omega$ load and a branch containing a $2\,\mathrm{\mu F}$ capacitor in series with $10\,\Omega$. In DC steady state the capacitor branch carries no current, so its $10\,\Omega$ resistor has zero drop. The capacitor therefore sees the load-terminal voltage:

$$
V_C=(2.5\,\mathrm V)\frac{2\,\Omega}{0.5\,\Omega+2\,\Omega}=2.00\,\mathrm V.
$$

Its charge is

$$
Q=(2\times10^{-6}\,\mathrm F)(2.00\,\mathrm V)=4.00\,\mathrm{\mu C}.
$$

Opening the capacitor branch for analysis does not mean setting its voltage to zero. The internal source resistance and the conducting load branch still determine the terminal voltage.

### Voltage from two current pulses

The W4 exercise drives a $2\,\Omega$ resistor and $500\,\mathrm{\mu F}$ capacitor in series: $2\,\mathrm A$ for $0$–$1\,\mathrm{ms}$, zero for $1$–$2\,\mathrm{ms}$ and $4\,\mathrm A$ for $2$–$3\,\mathrm{ms}$. With zero initial capacitor voltage, the first gradient is

$$
\frac{dv_C}{dt}=\frac{2\,\mathrm A}{500\times10^{-6}\,\mathrm F}=4000\,\mathrm{V\,s^{-1}}.
$$

Thus $v_C(1\,\mathrm{ms})=(4000\,\mathrm{V\,s^{-1}})(0.001\,\mathrm s)=4.00\,\mathrm V$. During the zero-current interval its voltage stays at $4.00\,\mathrm V$. The final gradient is $(4\,\mathrm A)/(500\,\mathrm{\mu F})=8000\,\mathrm{V\,s^{-1}}$, giving $v_C(3\,\mathrm{ms})=4.00\,\mathrm V+(8000\,\mathrm{V\,s^{-1}})(0.001\,\mathrm s)=12.0\,\mathrm V$.

The resistor voltage follows current directly: $4\,\mathrm V$, $0\,\mathrm V$, then $8\,\mathrm V$. Its voltage can jump while the capacitor voltage remains continuous.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]
- Next: [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Concepts: [[Capacitance]] · [[RC and RL Transients]] · [[Hydraulic Analogy for Circuits]]
- Application: [[Capacitive Displacement Sensor]]

## Sources

- `S1-W04-4 Capacitors - Recorded.pdf`, pp. 3–18; `FEEG1004 Lecture 2020-09-11.txt` (ll. 1–165), including the energy derivation set for independent study at ll. 120–130 and current-source example at ll. 131–158.
- `S1-W04 Circuits and Capacitors - Interactive.pdf`, pp. 13–17; `S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf`, p. 7. No matching interactive transcript is filed for these exercises.
- `Tutorial Sheet 02 - DC Circuit Analysis & Kirchhoff's Laws.pdf`, Q4(b). The sheet asks for endpoint/gradient sketches without solving the differential equation at that stage; the complete RC working above develops the same model.
- The index's `5a Inductors` assignment to A4 is a mismatch: its content concerns A5, so it is used there.
- Every numerical example, exponential fraction and KVL/energy check computed in Python.

## Self-study tasks

### Core

- [ ] Derive the differential and integral current–voltage relations, retaining the initial voltage (capacitor transcript ll. 94–115). → [[#2. Deriving the current–voltage law]].
- [ ] Complete the stored-energy derivation by changing integration variable (capacitor transcript ll. 120–130). → [[#3. Deriving the stored energy]].
- [ ] Solve the $5\,\mathrm{\mu F}$ current-source example (capacitor transcript ll. 131–149). → [[#Charging a capacitor with a current source]].
- [ ] Find capacitor initial/final values, stored energy and sketch its voltage and source current (Tutorial Sheet 2 Q4, capacitor parts). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q4: Capacitor and inductor steady states and transients|Tutorial 2 Q4]]; [[#RC response in Tutorial 2]].

### Further practice

- [ ] Solve the two-pulse voltage exercise (W4 interactive pp. 14–15). → [[#Voltage from two current pulses]].
- [ ] Find the capacitor charge with source internal resistance (W5 interactive p. 7). → [[#Charge after the rest of the circuit settles]].
- [ ] Reproduce the RC integration and verify the $63.2\%$ result (suggested, not lecturer-set). → [[#4. Deriving RC charging from the differential equation]].

## Transcript and slide slips

> [!warning] Integral form needs an initial condition
> Where: [[#2. Deriving the current–voltage law]]
> Recorded p. 13 writes $V=(1/C)\int I\,dt$ without displaying its integration constant. For a definite integral from $0$ to $t$, include $v_C(0)$. The zero-initial-voltage expression applies to an initially uncharged capacitor.
