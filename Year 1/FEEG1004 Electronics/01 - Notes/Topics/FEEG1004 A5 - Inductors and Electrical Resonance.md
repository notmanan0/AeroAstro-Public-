---
title: FEEG1004 A5 - Inductors and Electrical Resonance
module: FEEG1004 Electronics
type: topic
stream: 'Part A: Electrical Fundamentals and DC Circuits'
order: 5
tags:
- feeg1004
- fundamentals
- inductor
- inductance
- resonance
- lc-circuit
- ignition
aliases:
- Lecture 5a-5b
- Inductors
- Electrical resonance
- V = L di/dt
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]"
- "[[FEEG1004 A4 - Capacitors]]"
next_topics:
- "[[FEEG1004 A6 - Mesh Analysis]]"
key_concepts:
- "[[Inductance]]"
- "[[RC and RL Transients]]"
- "[[Resonance]]"
- "[[Hydraulic Analogy for Circuits]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"
sources:
- 02 - Sources/S1 Fundamentals/S1-W05-5abc Inductors and Resonance - Recorded.pdf
- 02 - Sources/S1 Fundamentals/S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-10-13 - 5a Inductors.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 2020-10-13 - 5b Electrical resonance.txt
coverage: 5a Inductors (ll. 1-116); 5b Electrical resonance (ll. 1-169); W05 interactive pp. 8-11 provide additional checks
---


# FEEG1004 A5 - Inductors and Electrical Resonance

> [!abstract] Summary
> An inductor stores energy in its magnetic field, with $v_L=L\,di/dt$ and $E_L=\tfrac12 Li^2$ for constant inductance. Finite voltage changes current continuously, and a series RL circuit approaches its DC current with time constant $\tau=L/R$. Connecting an inductor and capacitor allows energy to pass between magnetic and electric stores; an ideal LC circuit has natural angular frequency $\omega_0=1/\sqrt{LC}$.

> [!summary]- Exam use: quick path
> - **Use it when:** finding initial current gradients, RL switching curves, stored magnetic energy or LC oscillation frequency.
> - **Assumptions:** ideal, constant inductance; finite voltage for current continuity; positive series resistance for an RL final value; lossless components for the ideal LC frequency and energy equality.
> - **Method:** 1. Define current and passive voltage polarities. 2. Preserve the initial inductor current. 3. Apply KVL and $v_L=L\,di/dt$. 4. Integrate using the initial condition, or form the LC charge equation. 5. Check limits, energy and frequency units.
> - **Common mistakes:** setting the inductor voltage to zero immediately after switch-on; using $1/\sqrt{LC}$ as a frequency in hertz without dividing by $2\pi$.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q4: Capacitor and inductor steady states and transients|Tutorial 2 Q4]]

Current in a coil produces a magnetic field around its turns. Increasing that field requires energy, while reducing it releases energy. The coil therefore needs a voltage across it while its current changes. In the ideal model, maintaining an already established constant current requires no inductor voltage.

The hydraulic analogy is a heavy waterwheel in a pipe. A pressure difference accelerates the wheel and the flow; removing that pressure does not instantly stop the wheel. Inductance corresponds to this inertia. Resistance dissipates energy and determines the final current when a constant source feeds an RL circuit.

A capacitor provides a second energy store. Its electric field can drive current through an inductor, building a magnetic field. Current can then continue after the capacitor is discharged, charging it with reversed polarity. Repetition produces an oscillation, with resistance and other losses reducing its amplitude in a real circuit.

## 1. Inductance and the voltage–current law

For a linear coil, flux linkage is proportional to current:

$$
N\Phi=Li.
$$

**Inductance** $L$ is this proportionality constant, measured in henries, $\mathrm H=\mathrm{Wb\,A^{-1}}=\mathrm{V\,s\,A^{-1}}$. $L$ is treated as constant here; a real magnetic core can make the relation nonlinear.

Differentiate the linkage relation:

$$
\frac{d(N\Phi)}{dt}=L\frac{di}{dt}.
$$

Faraday's law gives a back EMF $\mathcal E=-d(N\Phi)/dt$ around the winding. Define the terminal voltage $v_L$ using the passive sign convention, with current entering its positive terminal. That applied terminal drop opposes the back EMF:

$$
\begin{aligned}
v_L&=-\mathcal E,\\
v_L&=\frac{d(N\Phi)}{dt},\\
v_L&=L\frac{di}{dt}.
\end{aligned}
$$

The minus sign in Faraday's law has not disappeared physically: the back EMF resists the change in current. The passive terminal voltage and the circulating induced EMF have opposite reference signs.

Rearrange and integrate:

$$
\begin{aligned}
\frac{di}{dt}&=\frac{v_L}{L},\\
\int_{i(0)}^{i(t)}di&=\frac1L\int_0^t v_L(t')\,dt',\\
i(t)&=i(0)+\frac1L\int_0^t v_L(t')\,dt'.
\end{aligned}
$$

Finite voltage over a vanishingly short interval cannot produce a finite current jump. Therefore

$$
i(0^+)=i(0^-).
$$

The preserved current can be non-zero. At DC steady state, $di/dt=0$, so an ideal inductor has zero terminal voltage and behaves as a short circuit. A real winding still has resistance.

For example, $4\,\mathrm V$ across $5\,\mathrm{mH}$ gives

$$
\frac{di}{dt}=\frac{4\,\mathrm V}{5\times10^{-3}\,\mathrm H}=800\,\mathrm{A\,s^{-1}}.
$$

## 2. Deriving magnetic energy storage

Absorbed power is $p=v_Li$. Starting with zero current and substituting the inductor law,

$$
\begin{aligned}
E_L&=\int_0^t v_Li\,dt',\\
E_L&=\int_0^t Li\frac{di}{dt'}\,dt'.
\end{aligned}
$$

Change the integration variable to current:

$$
E_L=L\int_0^I i\,di.
$$

Integrate and evaluate the limits:

$$
\begin{aligned}
E_L&=L\left[\frac{i^2}{2}\right]_0^I,\\
E_L&=\frac12 LI^2.
\end{aligned}
$$

Energy is non-negative for positive $L$, irrespective of current direction. With current positive and decreasing, $v_L$ is negative under the passive convention, so $p=v_Li<0$: the inductor returns stored energy to the circuit.

## 3. Deriving the RL switch-on transient

A constant supply $V_s>0$ drives a resistor $R>0$ and ideal inductor $L$ in series, with $i(0)=0$. KVL around the loop, traversed in the current direction, gives

$$
V_s-Ri-v_L=0.
$$

Substitute the inductor voltage:

$$
V_s-Ri-L\frac{di}{dt}=0.
$$

Rearrange:

$$
L\frac{di}{dt}=V_s-Ri.
$$

Separate the variables while $i<V_s/R$:

$$
\frac{di}{V_s-Ri}=\frac{dt}{L}.
$$

Integrate both sides:

$$
\begin{aligned}
\int\frac{di}{V_s-Ri}&=\int\frac{dt}{L},\\
-\frac1R\ln\left(\frac{V_s-Ri}{V_s}\right)&=\frac{t}{L}+K.
\end{aligned}
$$

At $t=0$, $i=0$, giving

$$
\begin{aligned}
-\frac1R\ln(1)&=K,\\
K&=0.
\end{aligned}
$$

Multiply by $-R$:

$$
\ln\left(\frac{V_s-Ri}{V_s}\right)=-\frac{Rt}{L}.
$$

Exponentiate:

$$
\frac{V_s-Ri}{V_s}=e^{-Rt/L}.
$$

Multiply by $V_s$ and rearrange one term at a time:

$$
\begin{aligned}
V_s-Ri&=V_se^{-Rt/L},\\
Ri&=V_s\left(1-e^{-Rt/L}\right),\\
i(t)&=\frac{V_s}{R}\left(1-e^{-Rt/L}\right).
\end{aligned}
$$

The **time constant** is $\tau=L/R$, with units $\mathrm H/\Omega=\mathrm s$. At $t=\tau$,

$$
i(\tau)=\frac{V_s}{R}(1-e^{-1})=0.63212\frac{V_s}{R}.
$$

Current has reached $63.2\%$ of its final value. Recover the inductor voltage using KVL:

$$
\begin{aligned}
v_L&=V_s-Ri,\\
v_L&=V_s-V_s\left(1-e^{-t/\tau}\right),\\
v_L&=V_se^{-t/\tau}.
\end{aligned}
$$

At switch-on, current is zero, resistor drop is zero and the whole source voltage appears across the inductor. At long times, current approaches $V_s/R$ and inductor voltage approaches zero. Its gradient also tends to zero, since differentiating the exponential gives $dv_L/dt=-(V_s/\tau)e^{-t/\tau}$.

![[ee_a5_rl_transient.png|900]]

The figure uses the $6\,\mathrm V$, $100\,\Omega$, $2\,\mathrm{mH}$ example. This circuit has a DC final value because resistance limits current. An ideal inductor directly across a non-zero constant voltage would instead have a continuously changing current.

## 4. Deriving the LC natural frequency

Consider a closed, lossless loop containing an ideal capacitor and inductor. Let $q$ be charge on the capacitor plate into which the loop current enters, so $i=dq/dt$. Define both component drops using that current direction. With no source, KVL gives

$$
v_L+v_C=0.
$$

Insert the component laws:

$$
L\frac{di}{dt}+\frac{q}{C}=0.
$$

Replace current by the charge derivative:

$$
L\frac{d^2q}{dt^2}+\frac{q}{C}=0.
$$

Divide by inductance:

$$
\frac{d^2q}{dt^2}+\frac1{LC}q=0.
$$

For a sinusoidal charge $q=Q_m\cos(\omega_0t+\phi)$ the derivatives are

$$
\begin{aligned}
\frac{dq}{dt}&=-Q_m\omega_0\sin(\omega_0t+\phi),\\
\frac{d^2q}{dt^2}&=-\omega_0^2q.
\end{aligned}
$$

Substitute into the differential equation:

$$
\left(-\omega_0^2+\frac1{LC}\right)q=0.
$$

For a non-zero oscillation, the coefficient must vanish:

$$
\begin{aligned}
\omega_0^2&=\frac1{LC},\\
\omega_0&=\frac1{\sqrt{LC}}.
\end{aligned}
$$

This is angular frequency in $\mathrm{rad\,s^{-1}}$. One cycle is $2\pi$ radians, so the frequency in hertz is

$$
\begin{aligned}
f_0&=\frac{\omega_0}{2\pi},\\
f_0&=\frac1{2\pi\sqrt{LC}}.
\end{aligned}
$$

At a maximum of capacitor voltage, current is zero and all the ideal loop's energy is electric. When capacitor voltage passes through zero, the energy is magnetic and current magnitude is greatest. Equating the two maxima gives

$$
\frac12 CV_{pk}^2=\frac12 LI_{pk}^2.
$$

A driven circuit can show a large response near its natural frequency. The lossless LC result does not specify the peak response of a damped, loaded circuit; resistance and the measured quantity matter.

## 5. Ignition switching and energy transfer

In the ignition circuit, the condenser is a capacitor across the contact switch, called the points. With the points closed it is shorted, so its voltage is zero. The primary winding acts as an inductor and the ballast resistor limits its eventual current.

When the points open, the established primary current continues into the capacitor. Capacitor voltage rises rapidly because $dv_C/dt=i/C$. Magnetic energy transfers to electric energy; the capacitor subsequently drives current in the reverse direction. Resistance dissipates energy and the spark takes energy through the secondary winding, so the oscillations decay.

The battery remains connected in the displayed circuit. After opening, a settled zero-current state leaves no drop across the ballast resistor or ideal primary inductance, so the capacitor tends towards the $12\,\mathrm V$ supply voltage. The point-voltage trace therefore settles at $12\,\mathrm V$ while the points remain open, rather than at zero.

![[ee_a5_ignition_resonance.png|900]]

This figure is an approximate damped LC illustration, with $250\,\mathrm{nF}$ from the circuit diagram and inductance inferred from the lossless energy estimate below. It omits the battery offset and secondary spark loading; its calculated period is not a specified ignition-coil measurement. The complete circuit's final capacitor voltage is $12\,\mathrm V$.

The primary pulse is about $300\,\mathrm V$, while the secondary pulse is about $20\,\mathrm{kV}$ because the secondary has many more turns. Modern switching electronics provide more control of spark timing and energy.

## Worked examples

### The six-volt RL circuit

For $V_s=6\,\mathrm V$, $R=100\,\Omega$ and $L=2\,\mathrm{mH}$, initially unenergised,

$$
\tau=\frac{2\times10^{-3}\,\mathrm H}{100\,\Omega}=20.0\,\mathrm{\mu s}.
$$

The initial current gradient is

$$
\left.\frac{di}{dt}\right|_{0^+}=\frac{6\,\mathrm V}{2\times10^{-3}\,\mathrm H}=3000\,\mathrm{A\,s^{-1}}.
$$

The final current is

$$
I_\infty=\frac{6\,\mathrm V}{100\,\Omega}=0.0600\,\mathrm A.
$$

At one time constant,

$$
\begin{aligned}
i(20\,\mathrm{\mu s})&=(0.0600\,\mathrm A)(1-e^{-1})=0.037927\,\mathrm A,\\
v_L(20\,\mathrm{\mu s})&=(6\,\mathrm V)e^{-1}=2.20728\,\mathrm V.
\end{aligned}
$$

The final stored energy is $E_L=\tfrac12(2\times10^{-3}\,\mathrm H)(0.0600\,\mathrm A)^2=3.60\,\mathrm{\mu J}$.

> [!check] KVL and the time constant
> At $\tau$, resistor voltage is $(100\,\Omega)(0.037927\,\mathrm A)=3.79272\,\mathrm V$. Adding $2.20728\,\mathrm V$ across the inductor gives $6.00000\,\mathrm V$, and the current is $63.212\%$ of its final value.

### Tutorial 2 output across the resistor

Tutorial Sheet 2 Q4(c) has $1\,\mathrm V$, $L=1\,\mathrm{\mu H}$ and $R=5\,\Omega$. The output is across the resistor, rather than the inductor. Starting from zero current,

$$
\begin{aligned}
\tau&=\frac{1\times10^{-6}\,\mathrm H}{5\,\Omega}=0.200\,\mathrm{\mu s},\\
I_\infty&=\frac{1\,\mathrm V}{5\,\Omega}=0.200\,\mathrm A.
\end{aligned}
$$

At $t=\tau$,

$$
\begin{aligned}
i&=(0.200\,\mathrm A)(1-e^{-1})=0.126424\,\mathrm A,\\
V_{out}&=(5\,\Omega)(0.126424\,\mathrm A)=0.63212\,\mathrm V.
\end{aligned}
$$

Initially $V_{out}=0\,\mathrm V$; its final value is $1\,\mathrm V$. Stored magnetic energy at the final current is

$$
E_L=\frac12(1\times10^{-6}\,\mathrm H)(0.200\,\mathrm A)^2=20.0\,\mathrm{nJ}.
$$

### An energy estimate using the ignition values

The ignition diagram gives a $12\,\mathrm V$ battery, $3\,\Omega$ ballast resistance and $250\,\mathrm{nF}$ capacitor. Its approximate pulse values are $4\,\mathrm A$ and $300\,\mathrm V$. With ideal winding resistance neglected, the closed-points current is

$$
I_0=\frac{12\,\mathrm V}{3\,\Omega}=4.00\,\mathrm A.
$$

The capacitor's initial voltage gradient after opening is

$$
\left.\frac{dv_C}{dt}\right|_{0^+}=\frac{4\,\mathrm A}{250\times10^{-9}\,\mathrm F}=1.60\times10^7\,\mathrm{V\,s^{-1}}.
$$

To estimate an inductance from the pulse, neglect resistor loss, battery work and secondary energy transfer during the first exchange. Equating ideal energy maxima and rearranging gives

$$
\begin{aligned}
L&=C\left(\frac{V_{pk}}{I_0}\right)^2,\\
L\approx(250\times10^{-9}\,\mathrm F)\left(\frac{300\,\mathrm V}{4\,\mathrm A}\right)^2&=1.40625\,\mathrm{mH}.
\end{aligned}
$$

This is an inferred estimate, not a supplied coil specification. In that ideal model,

$$
\begin{aligned}
\omega_0\approx\frac1{\sqrt{(1.40625\times10^{-3}\,\mathrm H)(250\times10^{-9}\,\mathrm F)}}&=5.3333\times10^4\,\mathrm{rad\,s^{-1}},\\
f_0\approx\frac{5.3333\times10^4\,\mathrm{rad\,s^{-1}}}{2\pi}&=8.4883\,\mathrm{kHz}.
\end{aligned}
$$

> [!check] Ideal energy exchange
> $\tfrac12(250\,\mathrm{nF})(300\,\mathrm V)^2=11.25\,\mathrm{mJ}$, matching $\tfrac12(1.40625\,\mathrm{mH})(4\,\mathrm A)^2$. Actual ignition energy is shared with losses, the battery and the secondary, so this equality is an estimate for the isolated LC model.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A4 - Capacitors]]
- Next: [[FEEG1004 A6 - Mesh Analysis]]
- Concepts: [[Inductance]] · [[RC and RL Transients]] · [[Resonance]] · [[Hydraulic Analogy for Circuits]]
- Switch-off protection: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]

## Sources

- `S1-W05-5abc Inductors and Resonance - Recorded.pdf`, pp. 3–24; `FEEG1004 Lecture 2020-10-13 - 5a Inductors.txt` (ll. 1–116), and `FEEG1004 Lecture 2020-10-13 - 5b Electrical resonance.txt` (ll. 1–169).
- `S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf`, pp. 8–11. The index assigns `5a Inductors` near A4, but its full content belongs here.
- `Tutorial Sheet 02 - DC Circuit Analysis & Kirchhoff's Laws.pdf`, Q4(c). Its original task asks for qualitative sketches; the full RL and LC derivations above follow from the stated ideal component models.
- Every numerical result and check computed in Python. The ignition figure uses the slide's $250\,\mathrm{nF}$; its inferred inductance and frequency are explicitly approximate.

## Self-study tasks

### Core

- [ ] Sketch the six-volt circuit's initial gradient and final values (5a transcript ll. 62–112). → [[#The six-volt RL circuit]].
- [ ] Explain why the final gradient of inductor voltage is zero (5a transcript ll. 113–114). → [[#3. Deriving the RL switch-on transient]].
- [ ] Find initial/final output, source current and stored energy for the RL circuit (Tutorial Sheet 2 Q4, inductor parts). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q4: Capacitor and inductor steady states and transients|Tutorial 2 Q4]]; [[#Tutorial 2 output across the resistor]].
- [ ] Calculate the initial switch-gap voltage after opening an energised inductor circuit (Tutorial Sheet 2 Q5). → [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions#Q5: Opening the switch on a 5 mH inductor fed from 12 V with 0.2 Ω internal resistance|Tutorial 2 Q5]].
- [ ] Explain why the open-points voltage settles at $12\,\mathrm V$ rather than zero (5b transcript ll. 151–161). → [[#5. Ignition switching and energy transfer]].

### Further practice

- [ ] Reproduce the RL integration and its $63.2\%$ check (suggested, not lecturer-set). → [[#3. Deriving the RL switch-on transient]].
- [ ] Derive the LC angular frequency, then convert it to hertz (suggested, not lecturer-set). → [[#4. Deriving the LC natural frequency]].

## Transcript and slide slips

> [!warning] Initial slope and steady-state qualifications
> Where: [[#The six-volt RL circuit]] and [[#3. Deriving the RL switch-on transient]]
> The 5a transcript l. 87 gives $300\,\mathrm{A\,s^{-1}}$ for $6\,\mathrm V$ across $2\,\mathrm{mH}$. The correct result is $3000\,\mathrm{A\,s^{-1}}$, as recorded p. 9 shows. Lines 93–94 also say AC has no steady state and DC always has one: the relevant state here is a constant DC final value in the resistive RL circuit. AC circuits can have a periodic steady state, and an ideal inductor driven by constant non-zero voltage has no finite final current.
