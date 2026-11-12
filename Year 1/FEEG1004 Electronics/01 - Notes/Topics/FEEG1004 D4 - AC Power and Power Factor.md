---
title: "FEEG1004 D4 - AC Power and Power Factor"
module: "FEEG1004 Electronics"
type: topic
stream: "Part D: AC Circuit Analysis"
order: 4
tags: [feeg1004, ac-circuits, power, active-power, reactive-power, complex-power, power-factor, pfc]
aliases: ["AC Analysis 04", "AC power", "Power factor", "Complex power", "Power triangle", "Power factor correction"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-03-18 (ll. 159–376); complex power and power-factor correction written-ahead from AC Analysis 04 slides and Niu notes"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]", "[[FEEG1004 D3 - AC Filters and Bode Plots]]"]
next_topics: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"]
key_concepts: ["[[Active, Reactive and Apparent Power]]", "[[Power Factor Correction]]", "[[RMS Value]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]]"]
sources:
  - "02 - Sources/S2 AC Analysis/S2-W25 AC Analysis 04 - AC Power - Lecture Slides.pdf"
  - "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-03-18.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf"
---

# FEEG1004 D4 - AC Power and Power Factor

> [!abstract] Summary
> In steady-state AC at angular frequency $\omega$, the instantaneous power $p(t)=v(t)i(t)$ pulses at $2\omega$ and splits into an irreversible part, whose average is the active power $P=VI\cos\phi=I^2R$ in watts, and a reversible exchange with magnetic and electric fields, whose amplitude is the reactive power $Q=VI\sin\phi=I^2X$ in VAR. Both are carried by the complex power $\mathbf S=\mathbf V\mathbf I^*=P+jQ$, whose magnitude $S=VI=\sqrt{P^2+Q^2}$ in VA sets the rating of generators, transformers and cables; inductors absorb reactive power ($Q_L=+I^2X_L>0$) and capacitors generate it ($Q_C=-I^2X_C<0$). The power factor $\text{PF}=\cos\phi=P/S$ is lagging for inductive loads and leading for capacitive ones. A parallel capacitor bank supplies an inductive load's reactive power locally ($Q_C=-\omega CV^2$), raising $\cos\phi$ towards unity and cutting the supply current and $I^2R_{\text{line}}$ losses without changing $P$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the active, reactive, apparent or complex power of an AC load, its power factor, or the shunt capacitor that corrects it.
> - **Assumptions:** sinusoidal steady state at one frequency; RMS phasors; $\phi=\theta_v-\theta_i$ keeps its sign; the correction capacitor is lossless and sits in parallel with the load.
> - **Method:** 1. Find the current phasor $\mathbf I=\mathbf V/Z$. 2. Form $\mathbf S=\mathbf V\mathbf I^*=P+jQ$, or use $P=I^2R$ and $Q=I^2X$. 3. Take $\text{PF}=P/S$, lagging if $Q>0$ and leading if $Q<0$. 4. For correction, hold $P$ fixed and set $Q_{\text{new}}=P\tan\phi_2$. 5. Size $C=P(\tan\phi_1-\tan\phi_2)/(2\pi fV^2)$ and check by summing $P$ and $Q$ element by element.
> - **Common mistakes:** multiplying $\mathbf V\mathbf I$ instead of $\mathbf V\mathbf I^*$, which flips the sign of $Q$; using $P=V^2/R$ with the total terminal voltage of a series impedance.
> - **Practise:** [[#Correcting an 80 kVA industrial load]] · [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions#Q3: Furnace (R_1 = 1 Ω, L_1 = 5 mH) fed through a cable (0.01 Ω, 50 µH), with 1 mF across the load, 400 V at 50 Hz|Tutorial 8 Q3]]

When a DC voltage $V$ drives a steady current $I$ through a load, the power is the constant product $P=VI$. Under sinusoidal excitation both $v(t)$ and $i(t)$ reverse polarity every half-cycle, and when the load contains inductance or capacitance the current is shifted from the voltage by $\phi=\theta_v-\theta_i$. For part of each cycle $v$ and $i$ have the same sign, $p(t)=v(t)i(t)>0$, and energy flows from the generator into the load. For the rest of the cycle they have opposite signs, $p(t)<0$, and energy stored in the load's magnetic or electric field flows back to the generator.

Power engineering separates the net one-way flow from this two-way exchange. Reactive power does no net work over a cycle, but the current that carries it still passes through generator windings, transformers and cables, where it causes real $I^2R_{\text{line}}$ heating and voltage drops.

## 1. Instantaneous, active and reactive power in pure R, L and C

The **instantaneous power** absorbed by a two-terminal element with terminal voltage $v(t)$ and entering current $i(t)$ is

$$
p(t) = v(t)\,i(t) \quad [\text{W}].
$$

The **active power** $P$ (also called real or average power) is its time average over one period $T=2\pi/\omega$:

$$
P = \frac{1}{T}\int_0^T p(t)\,\mathrm{d}t = \frac{1}{T}\int_0^T v(t)\,i(t)\,\mathrm{d}t \quad [\text{W}].
$$

For each ideal element below, the reference voltage across it is $v(t)=V_p\cos(\omega t)=\sqrt2\,V\cos(\omega t)$, where $V=V_p/\sqrt2$ is the RMS voltage and $I=I_p/\sqrt2$ the RMS current.

### Resistor: power pulsing at twice the supply frequency

In a pure resistor, Ohm's law $i(t)=v(t)/R$ keeps the current in phase with the voltage ($\theta_v=\theta_i=0$, so $\phi=0^\circ$):

$$
v(t) = \sqrt{2}\,V\cos(\omega t), \qquad i(t) = \sqrt{2}\,I\cos(\omega t).
$$

Multiplying them and using $\cos^2(\omega t)=\dfrac{1+\cos(2\omega t)}{2}$ gives

$$
\begin{aligned}
p_R(t) &= \big(\sqrt{2}\,V\cos(\omega t)\big)\big(\sqrt{2}\,I\cos(\omega t)\big) \\
&= 2VI\cos^2(\omega t) \\
&= 2VI\left(\frac{1 + \cos(2\omega t)}{2}\right) \\
&= VI\big(1 + \cos(2\omega t)\big) = P\big(1 + \cos(2\omega t)\big).
\end{aligned}
$$

Since $-1\le\cos(2\omega t)\le+1$, the power satisfies $0\le p_R(t)\le 2VI$ at all times, so $p_R(t)$ is never negative. Power flows only from the source into the resistor, pulsing between $0$ and $2VI$ at $2\omega$, twice per AC cycle, because both half-cycles dissipate heat $i^2R\ge0$. Over a full period the $\cos(2\omega t)$ term averages to zero, leaving

$$
P = VI = I^2 R = \frac{V^2}{R} \quad [\text{W}].
$$

No energy returns to the source, so the reactive power of a pure resistor is zero, $Q_R=0\ \text{VAR}$.

### Inductor: zero average power and absorbed reactive power

In a pure inductor with reactance $X_L=\omega L$ the current lags the voltage by $90^\circ$ ($\pi/2\ \text{rad}$, so $\phi=\theta_v-\theta_i=+90^\circ$). With $\cos(\omega t-\pi/2)=\sin(\omega t)$,

$$
v(t) = \sqrt{2}\,V\cos(\omega t), \qquad i(t) = \sqrt{2}\,I\cos\!\left(\omega t - \frac{\pi}{2}\right) = \sqrt{2}\,I\sin(\omega t).
$$

Multiplying and using $2\sin(\omega t)\cos(\omega t)=\sin(2\omega t)$ gives

$$
\begin{aligned}
p_L(t) &= \big(\sqrt{2}\,V\cos(\omega t)\big)\big(\sqrt{2}\,I\sin(\omega t)\big) \\
&= 2VI\sin(\omega t)\cos(\omega t) \\
&= VI\sin(2\omega t).
\end{aligned}
$$

Unlike the resistor's, this is a pure sinusoid at $2\omega$ with no DC offset. In the first quarter-cycle ($0<\omega t<\pi/2$) the current rises from $0$ to $I_p$, $v$ and $i$ are both positive, $p_L>0$, and the inductor takes energy from the supply to build its magnetic field $\tfrac12Li^2$. In the second quarter-cycle ($\pi/2<\omega t<\pi$) the current falls back to $0$ while $v$ is negative, $p_L<0$, and the collapsing field returns the same energy to the supply. The positive and negative lobes of $\sin(2\omega t)$ have equal area, so the average power is zero:

$$
P_L = \frac{1}{T}\int_0^T VI\sin(2\omega t)\,\mathrm{d}t = 0\ \text{W}.
$$

The amplitude of this double-frequency wave measures the back-and-forth exchange and is defined as the **reactive power** of the inductor:

$$
Q_L = +VI = +I^2 X_L = +\frac{V^2}{X_L} = +I^2(\omega L) = +\frac{V^2}{\omega L} \quad [\text{VAR}],
$$

so that $p_L(t)=Q_L\sin(2\omega t)$. To keep it distinct from active power in watts and apparent power in volt-amperes, $Q$ is given the unit **volt-ampere reactive** (VAR). By the power-systems convention an inductor has $Q_L>0$ and is said to absorb (consume) reactive power.

### Capacitor: zero average power and generated reactive power

In a pure capacitor with reactance $X_C=\dfrac{1}{\omega C}$ the current leads the voltage by $90^\circ$ ($\phi=\theta_v-\theta_i=-90^\circ$). With $\cos(\omega t+\pi/2)=-\sin(\omega t)$,

$$
v(t) = \sqrt{2}\,V\cos(\omega t), \qquad i(t) = \sqrt{2}\,I\cos\!\left(\omega t + \frac{\pi}{2}\right) = -\sqrt{2}\,I\sin(\omega t).
$$

Multiplying and using $2\sin(\omega t)\cos(\omega t)=\sin(2\omega t)$ again,

$$
\begin{aligned}
p_C(t) &= \big(\sqrt{2}\,V\cos(\omega t)\big)\big(-\sqrt{2}\,I\sin(\omega t)\big) \\
&= -2VI\sin(\omega t)\cos(\omega t) \\
&= -VI\sin(2\omega t).
\end{aligned}
$$

This oscillates symmetrically between $+VI$ and $-VI$ at $2\omega$, so the capacitor also takes zero average power:

$$
P_C = \frac{1}{T}\int_0^T (-VI\sin 2\omega t)\,\mathrm{d}t = 0\ \text{W}.
$$

The minus sign puts $p_C(t)$ $180^\circ$ out of phase with $p_L(t)=+VI\sin(2\omega t)$. Whenever an inductor across $v(t)$ is absorbing energy ($p_L>0$), a capacitor across the same voltage is discharging its electric field $\tfrac12Cv^2$ and releasing energy ($p_C<0$), and the other way round. Writing $p_C(t)=Q_C\sin(2\omega t)$ in the same form as the inductor assigns a negative reactive power to the capacitor:

$$
Q_C = -VI = -I^2 X_C = -\frac{V^2}{X_C} = -I^2\!\left(\frac{1}{\omega C}\right) = -\omega C V^2 \quad [\text{VAR}].
$$

With $Q_C<0$, a capacitor is said to generate (supply) reactive power, or equivalently to absorb negative reactive power.

| Ideal element | Phase shift $\phi = \theta_v - \theta_i$ | Instantaneous power $p(t)$ | Active power $P\ [\text{W}]$ | Reactive power $Q\ [\text{VAR}]$ | Physical role |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Resistor $R$ | $0^\circ$ | $VI(1 + \cos 2\omega t) \ge 0$ | $VI = I^2 R = \dfrac{V^2}{R}$ | $0$ | Absorbs active power irreversibly |
| Inductor $L$ | $+90^\circ$ ($I$ lags $V$) | $+VI\sin(2\omega t) = Q_L\sin(2\omega t)$ | $0$ | $+VI = +I^2 X_L = +\dfrac{V^2}{X_L} > 0$ | Absorbs reactive power ($Q > 0$) |
| Capacitor $C$ | $-90^\circ$ ($I$ leads $V$) | $-VI\sin(2\omega t) = Q_C\sin(2\omega t)$ | $0$ | $-VI = -I^2 X_C = -\dfrac{V^2}{X_C} < 0$ | Generates reactive power ($Q < 0$) |

![[ee_d4_instantaneous_power.png|900]]

## 2. Mixed loads, complex power and the power triangle

### Splitting the power of a load with any phase shift

A general linear load with impedance $Z=R+jX=|Z|\angle\phi$ has voltage and current with arbitrary phase angles $\theta_v$ and $\theta_i$:

$$
v(t) = \sqrt{2}\,V\cos(\omega t + \theta_v), \qquad i(t) = \sqrt{2}\,I\cos(\omega t + \theta_i),
$$

where the impedance angle is the voltage-minus-current phase difference $\phi=\theta_v-\theta_i$. Let $\alpha=\omega t+\theta_v$, so that $\omega t+\theta_i=\alpha-\phi$. Expanding $\cos(\alpha-\phi)=\cos\alpha\cos\phi+\sin\alpha\sin\phi$ gives

$$
\begin{aligned}
p(t) &= \big(\sqrt{2}\,V\cos\alpha\big)\big(\sqrt{2}\,I\cos(\alpha - \phi)\big) \\
&= 2VI\cos\alpha\,(\cos\alpha\cos\phi + \sin\alpha\sin\phi) \\
&= 2VI\cos\phi\cos^2\alpha + 2VI\sin\phi\sin\alpha\cos\alpha.
\end{aligned}
$$

The identities $2\cos^2\alpha=1+\cos(2\alpha)$ and $2\sin\alpha\cos\alpha=\sin(2\alpha)$ separate $p(t)$ into a non-negative resistive part and a zero-average reactive part:

$$
\begin{aligned}
p(t) &= \underbrace{VI\cos\phi}_{P}\,\big(1 + \cos 2(\omega t + \theta_v)\big) + \underbrace{VI\sin\phi}_{Q}\,\sin 2(\omega t + \theta_v) \\
&= P\big(1 + \cos 2(\omega t + \theta_v)\big) + Q\sin 2(\omega t + \theta_v).
\end{aligned}
$$

Averaging over a period removes both $\cos 2(\omega t+\theta_v)$ and $\sin 2(\omega t+\theta_v)$, which leaves the general **active power** and **reactive power**:

$$
P = VI\cos\phi = VI\cos(\theta_v - \theta_i) \quad [\text{W}], \qquad Q = VI\sin\phi = VI\sin(\theta_v - \theta_i) \quad [\text{VAR}].
$$

The impedance triangle of $Z=R+jX=|Z|\angle\phi$ ([[FEEG1004 D2 - Impedance and Phasor Circuit Analysis#4. Impedance triangles and inductive and capacitive loads|D2 §4]]) gives $V=I|Z|$, $\cos\phi=R/|Z|$ and $\sin\phi=X/|Z|$. Substituting these shows that active power is dissipated only in the equivalent resistance $R$ and reactive power is exchanged only with the net reactance $X=X_L-X_C$:

$$
\begin{aligned}
P &= (I|Z|)\,I\left(\frac{R}{|Z|}\right) = I^2 R \quad [\text{W}], \\
Q &= (I|Z|)\,I\left(\frac{X}{|Z|}\right) = I^2 X = I^2(X_L - X_C) \quad [\text{VAR}].
\end{aligned}
$$

> [!warning] $P\ne V^2/R$ with the terminal voltage of a series impedance
> In a series impedance $Z=R+jX$ the current $I$ is common to $R$ and $X$, so $P=I^2R$ and $Q=I^2X$ always hold. The terminal voltage $V=I\sqrt{R^2+X^2}$ is shared between $R$ and $jX$, so in terms of $V$ the correct forms are $P=\dfrac{V_R^2}{R}=\dfrac{V^2R}{R^2+X^2}$ and $Q=\dfrac{V_X^2}{X}=\dfrac{V^2X}{R^2+X^2}$. The expressions $P=V^2/R$ and $Q=V^2/X$ apply only when $R$ and $jX$ are in parallel directly across the full terminal voltage $V$.

### Complex power and the power triangle

In the phasor domain the RMS phasors are $\mathbf V=V\angle\theta_v=Ve^{j\theta_v}$ and $\mathbf I=I\angle\theta_i=Ie^{j\theta_i}$. The plain product $\mathbf V\mathbf I$ would have phase $\theta_v+\theta_i$, which depends on the arbitrary choice of time origin rather than on the physical phase difference $\theta_v-\theta_i$. Multiplying instead by the complex conjugate $\mathbf I^*=I\angle(-\theta_i)=Ie^{-j\theta_i}$ defines the **complex power**:

$$
\begin{aligned}
\mathbf{S} &= \mathbf{V}\mathbf{I}^* \\
&= \big(Ve^{j\theta_v}\big)\big(Ie^{-j\theta_i}\big) \\
&= VI\,e^{j(\theta_v - \theta_i)} = VI\,e^{j\phi} \\
&= VI\cos\phi + jVI\sin\phi \\
&= P + jQ.
\end{aligned}
$$

Substituting $\mathbf V=Z\mathbf I$ and using $\mathbf I\mathbf I^*=|\mathbf I|^2=I^2$ links the power triangle to the impedance triangle:

$$
\mathbf{S} = (Z\mathbf{I})\mathbf{I}^* = Z(\mathbf{I}\mathbf{I}^*) = I^2 Z = I^2(R + jX) = I^2 R + jI^2 X = P + jQ.
$$

Since $\mathbf S=I^2Z$ is the impedance scaled by the positive real factor $I^2$, the **power triangle** in the complex plane is similar to the impedance triangle. Its horizontal leg is the active power $P=\Re(\mathbf S)=VI\cos\phi=I^2R$ in watts, its vertical leg the reactive power $Q=\Im(\mathbf S)=VI\sin\phi=I^2X$ in VAR, and its angle to the positive real axis $\angle\mathbf S=\phi=\theta_v-\theta_i=\theta_Z=\arctan(Q/P)$. The hypotenuse is the **apparent power**

$$
S = |\mathbf{S}| = |\mathbf{V}||\mathbf{I}^*| = VI = \sqrt{P^2 + Q^2} = I^2|Z| \quad [\text{VA}].
$$

Tellegen's theorem (KCL and KVL in phasor form) implies that active and reactive power are conserved separately in any AC network. For any combination of series and parallel branches fed by a supply, the complex power delivered by the supply equals the sum of the branch complex powers:

$$
\mathbf{S}_{\text{supply}} = \sum_{k} \mathbf{S}_k \implies P_{\text{supply}} = \sum_{k} P_k \quad \text{and} \quad Q_{\text{supply}} = \sum_{k} Q_k.
$$

Apparent powers do not add algebraically, $|\mathbf S_{\text{supply}}|\ne\sum|\mathbf S_k|$, unless every branch has the same phase angle $\phi_k$.

## 3. Power factor, line losses and voltage regulation

### Lagging and leading power factor

The **power factor** of a load is the dimensionless ratio of active to apparent power:

$$
\text{PF} = \frac{P}{S} = \frac{VI\cos\phi}{VI} = \cos\phi = \frac{R}{|Z|}.
$$

For any passive load ($R\ge0$), $-90^\circ\le\phi\le+90^\circ$, so $0\le\text{PF}\le1$. A purely resistive load ($\phi=0^\circ$, $Q=0$) has $\text{PF}=\cos0^\circ=1$, called **unity power factor**, and every volt-ampere does real work ($P=S$). A purely reactive load ($\phi=\pm90^\circ$, $R=0$) has $\text{PF}=\cos(\pm90^\circ)=0$: a large current circulates but no net work is done ($P=0$, $S=|Q|$).

Cosine is even, $\cos(-\phi)=\cos(+\phi)$, so a value such as $\text{PF}=0.8$ does not say whether $\phi=+36.87^\circ$ or $\phi=-36.87^\circ$. The words lagging and leading resolve this, and they always describe the current relative to the voltage. A **lagging** power factor ($\phi=\theta_v-\theta_i>0$) means the current lags the voltage ($\theta_i<\theta_v$); the load is inductive ($X>0$) and absorbs reactive power ($Q=+S\sin|\phi|>0$). Induction motors, transformers, arc furnaces and solenoids all have lagging power factors. A **leading** power factor ($\phi<0$) means the current leads the voltage ($\theta_i>\theta_v$); the load is capacitive ($X<0$) and generates reactive power ($Q=-S\sin|\phi|<0$).

### Line losses and voltage regulation

Utilities penalise industrial customers whose power factor falls below about $0.85$–$0.90$ because of what a low power factor does to the network. Suppose a factory needs a fixed active power $P$ (say $50\ \text{kW}$ of shaft power) at a fixed RMS load voltage $V_L$. Rearranging $P=V_LI\cos\phi$ gives the RMS line current the cable must carry:

$$
I = \frac{P}{V_L\cos\phi} = \frac{P}{V_L \cdot \text{PF}}.
$$

If the cable has resistance $R_{\text{line}}$, the power lost as heat in it is

$$
P_{\text{loss}} = I^2 R_{\text{line}} = \frac{P^2 R_{\text{line}}}{V_L^2\cos^2\phi} = \frac{P_{\text{loss}}(\text{PF}=1)}{\text{PF}^2}.
$$

Reducing the power factor from $1.0$ to $0.5$ therefore doubles the line current and quadruples the line heating loss while delivering the same useful power $P$. Generators and transformers must also be sized for the larger apparent power $S=V_LI=P/\text{PF}$.

A poor power factor also degrades **voltage regulation**. When a source $\mathbf V_s$ feeds a load at $\mathbf V_L=V_L\angle0^\circ$ through a line of impedance $Z_{\text{line}}=R_{\text{line}}+jX_{\text{line}}$, the source phasor must be

$$
\mathbf{V}_s = \mathbf{V}_L + \mathbf{I}\,Z_{\text{line}} = V_L + (I\cos\phi - jI\sin\phi)(R_{\text{line}} + jX_{\text{line}}).
$$

The fractional change in voltage magnitude between no-load ($|\mathbf V_s|$) and full-load ($|\mathbf V_L|$) is the voltage regulation:

$$
\text{Voltage regulation} = \frac{|\mathbf{V}_s| - |\mathbf{V}_L|}{|\mathbf{V}_s|}.
$$

Overhead and underground lines are mainly inductive ($X_{\text{line}}>R_{\text{line}}$). A lagging current ($\phi>0$) produces an inductive drop $I\sin\phi\,X_{\text{line}}$ in phase with $\mathbf V_L$, so $|\mathbf V_s|$ must be much larger than $|\mathbf V_L|$: a large positive regulation, or a severe sag in load voltage if $|\mathbf V_s|$ is fixed. A strongly leading current ($\phi<0$) gives a negative reactance drop that lifts $|\mathbf V_L|$ above $|\mathbf V_s|$, a negative regulation known on high-voltage grids as the Ferranti rise. Operating near unity power factor ($\text{PF}\approx0.90$–$1.0$ lagging) keeps line losses low and load voltages stable.

![[ee_d4_pf_effects.png|900]]

## 4. Power factor correction with a shunt capacitor

Almost all heavy industrial loads (induction motors, welding transformers, induction furnaces) are inductive, with $Q_{\text{old}}>0$ and a lagging power factor. Connecting a **capacitor bank** $C$ in parallel across the load terminals raises the power factor seen by the supply. Instead of the motor's reactive magnetising current travelling back and forth along miles of utility cable from the power station, the capacitor exchanges reactive energy with the motor's magnetic field locally, at the factory substation.

Let the inductive load at RMS voltage $V$ and frequency $f$ ($\omega=2\pi f$) absorb active power $P$ and reactive power $Q_{\text{old}}=P\tan\phi_1>0$, with initial lagging angle $\phi_1=\arccos(\text{PF}_1)$. Adding a lossless capacitor across the same terminals leaves the voltage across the load unchanged, so the load's own $P$ and $Q_{\text{old}}$ are unchanged, and the capacitor absorbs no active power ($P_C=0$). The total active power is therefore $P_{\text{new}}=P+0=P$. The capacitor generates negative reactive power

$$
Q_C = -\frac{V^2}{X_C} = -\omega C V^2 = -2\pi f C V^2 < 0,
$$

and by conservation of reactive power the net reactive power the mains must supply falls to

$$
Q_{\text{new}} = Q_{\text{old}} + Q_C = Q_{\text{old}} - \omega C V^2.
$$

To raise the power factor from $\text{PF}_1=\cos\phi_1$ lagging to a target $\text{PF}_2=\cos\phi_2$ lagging ($0\le\phi_2<\phi_1$), the target net reactive power is $Q_{\text{new}}=P\tan\phi_2$. Solving for $C$:

$$
\begin{aligned}
\omega C V^2 &= Q_{\text{old}} - Q_{\text{new}} \\
&= P\tan\phi_1 - P\tan\phi_2, \\
C &= \frac{Q_{\text{old}} - Q_{\text{new}}}{\omega V^2} = \frac{P(\tan\phi_1 - \tan\phi_2)}{2\pi f V^2}.
\end{aligned}
$$

For complete correction to unity power factor ($\text{PF}_2=1.0$, $\phi_2=0^\circ$, $\tan\phi_2=0$, $Q_{\text{new}}=0$) the capacitor supplies all of the load's reactive power, $|Q_C|=Q_{\text{old}}$:

$$
C_{\text{unity}} = \frac{Q_{\text{old}}}{\omega V^2} = \frac{P\tan\phi_1}{2\pi f V^2}.
$$

![[ee_d4_power_triangle_pfc.png|700]]

## Worked examples

### Power in single elements and an inductive load

(a) An RMS current $I=10\ \text{A}$ flows through a $4\ \Omega$ resistor, a $5\ \Omega$ inductive reactance and a $3\ \Omega$ capacitive reactance in turn; find $P$ and $Q$ for each. (b) A source $\mathbf V=50\angle0^\circ\ \text{V}$ (RMS) drives a series load $Z=6+j11.31\ \Omega$; find the current phasor $\mathbf I$, $P$, $Q$, the complex power $\mathbf S$, the apparent power $|\mathbf S|$ and the power factor.

(a) For the resistor, $P=I^2R=(10\ \text{A})^2(4\ \Omega)=400\ \text{W}$ and $Q=0\ \text{VAR}$. For the inductive reactance, $P=0\ \text{W}$ and $Q_L=+I^2X_L=+(10\ \text{A})^2(5\ \Omega)=+500\ \text{VAR}$, i.e. $500\ \text{VAR}$ absorbed. For the capacitive reactance, $P=0\ \text{W}$ and $Q_C=-I^2X_C=-(10\ \text{A})^2(3\ \Omega)=-300\ \text{VAR}$, i.e. $300\ \text{VAR}$ generated. If all three were in series carrying $10\ \text{A}$, conservation of $P$ and $Q$ would give $P_{\text{total}}=400\ \text{W}$ and $Q_{\text{total}}=+500-300=+200\ \text{VAR}$.

(b) In polar form,

$$
\begin{aligned}
|Z| &= \sqrt{R^2 + X^2} = \sqrt{6^2 + 11.31^2} = \sqrt{36 + 127.916} = \sqrt{163.916} = 12.803\ \Omega, \\
\theta_Z &= \arctan\!\left(\frac{11.31}{6}\right) = \arctan(1.8850) = 62.05^\circ = 1.083\ \text{rad}.
\end{aligned}
$$

Generalised Ohm's law gives the current phasor:

$$
\begin{aligned}
\mathbf{I} &= \frac{\mathbf{V}}{Z} = \frac{50\angle 0^\circ\ \text{V}}{12.803\angle 62.05^\circ\ \Omega} \\
&= 3.905\angle(-62.05^\circ)\ \text{A}.
\end{aligned}
$$

With $I=3.9053\ \text{A}$, $R=6\ \Omega$ and $X=+11.31\ \Omega$,

$$
\begin{aligned}
P &= I^2 R = (3.9053\ \text{A})^2(6\ \Omega) = 91.51\ \text{W} \approx 91.5\ \text{W}, \\
Q &= I^2 X = (3.9053\ \text{A})^2(11.31\ \Omega) = +172.50\ \text{VAR}.
\end{aligned}
$$

Directly from $\mathbf S=\mathbf V\mathbf I^*$, with $\mathbf I^*=3.9053\angle(+62.05^\circ)\ \text{A}$,

$$
\begin{aligned}
\mathbf{S} &= \mathbf{V}\mathbf{I}^* = (50\angle 0^\circ\ \text{V})(3.9053\angle 62.05^\circ\ \text{A}) \\
&= 195.27\angle 62.05^\circ\ \text{VA} \\
&= 195.27\cos(62.05^\circ) + j\,195.27\sin(62.05^\circ) \\
&= 91.51\ \text{W} + j172.50\ \text{VAR}.
\end{aligned}
$$

The apparent power is $S=|\mathbf S|=VI=195.3\ \text{VA}$ and the power factor is

$$
\text{PF} = \cos\phi = \frac{P}{S} = \frac{91.51\ \text{W}}{195.27\ \text{VA}} = 0.469 \text{ lagging}.
$$

> [!check] Conjugate sign check
> $\mathbf I$ has a negative angle ($-62.05^\circ$, lagging $\mathbf V$). The conjugate flips it to $+62.05^\circ$, so $\mathbf S=\mathbf V\mathbf I^*=+91.51+j172.50\ \text{VA}$ gives the inductive load ($X=+11.31\ \Omega>0$) a positive $Q=+172.5\ \text{VAR}$. Without the conjugate, $\mathbf V\mathbf I$ would give $-j172.5\ \text{VAR}$ and wrongly suggest a capacitive load.

### Line loss and voltage regulation against load power factor

A load takes a constant $P_L=50\ \text{W}$ at RMS terminal voltage $\mathbf V_L=10\angle0^\circ\ \text{V}$ through a line of impedance $Z_{\text{line}}=0.2+j1.0\ \Omega$. Compare the line current $I$, the line loss $P_{\text{loss}}$, the source voltage $|\mathbf V_s|$ and the voltage regulation at load power factors of $0.6$ lagging, $0.8$ lagging, $1.0$, $0.8$ leading and $0.6$ leading.

For any power factor the line current is $I=\dfrac{P_L}{V_L\cos\phi}=\dfrac{50\ \text{W}}{(10\ \text{V})\cos\phi}=\dfrac{5.0}{\cos\phi}\ \text{A}$, and the loss in $R_{\text{line}}=0.2\ \Omega$ is $P_{\text{loss}}=I^2R_{\text{line}}=0.2I^2$:

$$
\begin{aligned}
\text{PF} = 1.0\ (\phi = 0^\circ):&\quad I = \frac{5.0}{1.0} = 5.00\ \text{A},\quad P_{\text{loss}} = (5.00)^2(0.2) = 5.00\ \text{W}, \\
\text{PF} = 0.8\ (\phi = \pm 36.87^\circ):&\quad I = \frac{5.0}{0.8} = 6.25\ \text{A},\quad P_{\text{loss}} = (6.25)^2(0.2) = 7.81\ \text{W}, \\
\text{PF} = 0.6\ (\phi = \pm 53.13^\circ):&\quad I = \frac{5.0}{0.6} = 8.333\ \text{A},\quad P_{\text{loss}} = (8.333)^2(0.2) = 13.89\ \text{W}.
\end{aligned}
$$

At $0.6$ the loss is $2.78$ times the unity-PF loss. With $\mathbf V_L$ as reference the current phasor is $\mathbf I=I\angle(-\phi)=I\cos\phi-jI\sin\phi=5.00-j(5.00\tan\phi)\ \text{A}$, with $\phi>0$ lagging and $\phi<0$ leading, and KVL gives $\mathbf V_s=\mathbf V_L+\mathbf I Z_{\text{line}}$.

At $0.6$ lagging, $\tan\phi=+4/3$ and $\mathbf I=5.00-j6.667\ \text{A}$:

$$
\begin{aligned}
\mathbf{V}_s &= 10 + (5.00 - j6.667)(0.2 + j1.0) \\
&= 10 + (1.00 + 6.667) + j(5.00 - 1.333) \\
&= 17.67 + j3.67\ \text{V} = 18.04\angle 11.7^\circ\ \text{V},
\end{aligned}
$$

so the regulation is $\dfrac{18.04-10.0}{18.04}=+44.6\%$.

At unity power factor, $\tan\phi=0$ and $\mathbf I=5.00+j0\ \text{A}$:

$$
\mathbf{V}_s = 10 + 5.00(0.2 + j1.0) = 11.00 + j5.00\ \text{V} = 12.08\angle 24.4^\circ\ \text{V},
$$

so the regulation is $\dfrac{12.08-10.0}{12.08}=+17.2\%$.

At $0.6$ leading, $\tan\phi=-4/3$ and $\mathbf I=5.00+j6.667\ \text{A}$:

$$
\begin{aligned}
\mathbf{V}_s &= 10 + (5.00 + j6.667)(0.2 + j1.0) \\
&= 10 + (1.00 - 6.667) + j(5.00 + 1.333) \\
&= 4.33 + j6.33\ \text{V} = 7.67\angle 55.6^\circ\ \text{V},
\end{aligned}
$$

so the regulation is $\dfrac{7.67-10.0}{7.67}=-30.3\%$: the load voltage exceeds the source voltage.

| Load power factor | Phase $\phi$ | Current $I\ [\text{A}]$ | Line loss $P_{\text{loss}}\ [\text{W}]$ | Source voltage $\|\mathbf{V}_s\|\ [\text{V}]$ | Voltage regulation |
| :--- | :--- | :--- | :--- | :--- | :--- |
| $0.6\text{ lagging}$ | $+53.13^\circ$ | $8.33$ | $13.89$ | $18.04$ | $+44.6\%$ |
| $0.8\text{ lagging}$ | $+36.87^\circ$ | $6.25$ | $7.81$ | $15.35$ | $+34.9\%$ |
| $1.0\text{ (unity)}$ | $0^\circ$ | $5.00$ | $5.00$ | $12.08$ | $+17.2\%$ |
| $0.8\text{ leading}$ | $-36.87^\circ$ | $6.25$ | $7.81$ | $9.25$ | $-8.1\%$ |
| $0.6\text{ leading}$ | $-53.13^\circ$ | $8.33$ | $13.89$ | $7.67$ | $-30.3\%$ |

> [!check] Complex power balance across the line
> At $0.6$ lagging the load absorbs $P_L=50.00\ \text{W}$ and $Q_L=P_L\tan(53.13^\circ)=+66.67\ \text{VAR}$, and the line absorbs $P_{\text{line}}=I^2R_{\text{line}}=(8.333)^2(0.2)=13.89\ \text{W}$ and $Q_{\text{line}}=I^2X_{\text{line}}=(8.333)^2(1.0)=+69.44\ \text{VAR}$. The sums are $P_s=50.00+13.89=63.89\ \text{W}$ and $Q_s=66.67+69.44=+136.11\ \text{VAR}$, and $\mathbf S_s=\mathbf V_s\mathbf I^*=(17.667+j3.667)(5.00+j6.667)=63.89+j136.11\ \text{VA}$ agrees to the precision shown.

### Correcting an 80 kVA industrial load

A plant on a $400\ \text{V}$ (RMS), $50\ \text{Hz}$ supply draws $S_0=80\ \text{kVA}$ at $\text{PF}_0=0.50$ lagging. (a) Find its active power $P$ and initial reactive power $Q_0$. (b) A $C=1.0\ \text{mF}$ capacitor bank is connected across the $400\ \text{V}$ terminals; find $Q_C$, the new net reactive power $Q_{\text{new}}$, the new apparent power $S_{\text{new}}$ and the corrected power factor. (c) Find the total capacitance $C_{\text{unity}}$ that would bring the plant to unity power factor.

(a) From $\text{PF}_0=\cos\phi_0=0.50$ lagging, $\phi_0=\arccos(0.50)=+60^\circ$ and $\sin60^\circ=\sqrt3/2\approx0.8660$:

$$
\begin{aligned}
P &= S_0\cos\phi_0 = (80\ \text{kVA})(0.50) = 40.0\ \text{kW}, \\
Q_0 &= S_0\sin\phi_0 = (80\ \text{kVA})\sin(60^\circ) = 80 \times 0.8660 = +69.28\ \text{kVAR}.
\end{aligned}
$$

(b) At $f=50\ \text{Hz}$ ($\omega=2\pi\times50=100\pi\approx314.16\ \text{rad s}^{-1}$) and $V=400\ \text{V}$ the capacitor generates

$$
\begin{aligned}
Q_C &= -\omega C V^2 = -2\pi f C V^2 \\
&= -2\pi(50\ \text{Hz})(1.0 \times 10^{-3}\ \text{F})(400\ \text{V})^2 \\
&= -50\,265.5\ \text{VAR} \approx -50.27\ \text{kVAR}.
\end{aligned}
$$

$P=40.0\ \text{kW}$ is unchanged, so the supply now provides

$$
\begin{aligned}
Q_{\text{new}} &= Q_0 + Q_C = 69.28\ \text{kVAR} - 50.27\ \text{kVAR} = +19.02\ \text{kVAR}, \\
S_{\text{new}} &= \sqrt{P^2 + Q_{\text{new}}^2} = \sqrt{(40.0\ \text{kW})^2 + (19.02\ \text{kVAR})^2} \\
&= \sqrt{1600 + 361.6} = 44.29\ \text{kVA},
\end{aligned}
$$

and the corrected power factor is

$$
\text{PF}_{\text{new}} = \frac{P}{S_{\text{new}}} = \frac{40.0\ \text{kW}}{44.29\ \text{kVA}} = 0.903\text{ lagging} \approx 0.90\text{ lagging}.
$$

Rounding $|Q_0|$ to $69\ \text{kVAR}$ and $|Q_C|$ to $50\ \text{kVAR}$ gives $Q_{\text{new}}\approx19\ \text{kVAR}$, $S_{\text{new}}=\sqrt{40^2+19^2}\approx44\ \text{kVA}$ and $\text{PF}_{\text{new}}=40/44.3\approx0.90$ lagging.

(c) Unity power factor needs $Q_{\text{new}}=0$:

$$
C_{\text{unity}} = \frac{Q_0}{2\pi f V^2} = \frac{69\,282\ \text{VAR}}{2\pi(50\ \text{Hz})(400\ \text{V})^2} = 1.378 \times 10^{-3}\ \text{F} = 1.38\ \text{mF}.
$$

> [!check] Line current before and after correction
> Before the capacitor the supply current is $I_{\text{old}}=S_0/V=80\,000\ \text{VA}/400\ \text{V}=200.0\ \text{A}$, or as a phasor with $\mathbf V=400\angle0^\circ\ \text{V}$, $\mathbf I_{\text{load}}=200\angle(-60^\circ)=100.0-j173.21\ \text{A}$. The capacitor draws a leading quadrature current $\mathbf I_C=j\omega C\mathbf V=+j(314.16)(10^{-3})(400)=+j125.66\ \text{A}$. By KCL the new supply current is $\mathbf I_{\text{new}}=\mathbf I_{\text{load}}+\mathbf I_C=100.0-j47.54\ \text{A}$, of magnitude $\sqrt{100.0^2+47.54^2}=110.73\ \text{A}=S_{\text{new}}/V=44\,290\ \text{VA}/400\ \text{V}$. The capacitor cuts the supply current by $44.6\%$ and the cable $I^2R_{\text{line}}$ losses by $1-(110.73/200)^2=69.3\%$.

### Furnace fed through a cable with a shunt capacitor

An industrial furnace, modelled as $R_1=1\ \Omega$ in series with $L_1=5\ \text{mH}$, is fed from a $V_s=400\ \text{V}$ (RMS), $50\ \text{Hz}$ supply through a cable of $R_2=0.01\ \Omega$ and $L_2=50\ \mu\text{H}$. A $C=1\ \text{mF}$ correction capacitor sits across the furnace terminals (Tutorial Sheet 8 Q3; [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions#Q3: Furnace (R_1 = 1 Ω, L_1 = 5 mH) fed through a cable (0.01 Ω, 50 µH), with 1 mF across the load, 400 V at 50 Hz|Tutorial 8 Q3]]). Find (a) the branch impedances and the parallel impedance $Z_p$ of furnace and capacitor, (b) the cable current $\mathbf I_2$ and the furnace voltage $\mathbf V$, and (c) the active power, reactive power and power factor of the furnace alone and of the whole system seen by the supply.

(a) At $f=50\ \text{Hz}$, $\omega=2\pi\times50=314.159\ \text{rad s}^{-1}$, so

$$
\begin{aligned}
Z_{\text{load}} &= R_1 + j\omega L_1 = 1.00 + j(314.159)(5 \times 10^{-3}) = 1.000 + j1.5708\ \Omega = 1.862\angle 57.52^\circ\ \Omega, \\
Z_C &= \frac{1}{j\omega C} = -\frac{j}{(314.159)(10^{-3})} = -j3.1831\ \Omega = 3.183\angle(-90^\circ)\ \Omega, \\
Z_{\text{cab}} &= R_2 + j\omega L_2 = 0.0100 + j(314.159)(50 \times 10^{-6}) = 0.0100 + j0.01571\ \Omega.
\end{aligned}
$$

The furnace and capacitor in parallel give $Z_p=Z_{\text{load}}\parallel Z_C$:

$$
\begin{aligned}
Z_p &= \frac{Z_{\text{load}} Z_C}{Z_{\text{load}} + Z_C} = \frac{(1.000 + j1.5708)(-j3.1831)}{1.000 + j1.5708 - j3.1831} \\
&= \frac{5.000 - j3.1831}{1.000 - j1.6123} \\
&= 2.8149 + j1.3553\ \Omega = 3.124\angle 25.71^\circ\ \Omega.
\end{aligned}
$$

(b) With $\mathbf V_s=400\angle0^\circ\ \text{V}$ as reference, the total impedance is $Z_{\text{total}}=Z_{\text{cab}}+Z_p=2.8249+j1.3710\ \Omega=3.140\angle25.89^\circ\ \Omega$, so

$$
\begin{aligned}
\mathbf{I}_2 &= \frac{\mathbf{V}_s}{Z_{\text{cab}} + Z_p} = \frac{400\angle 0^\circ\ \text{V}}{3.140\angle 25.89^\circ\ \Omega} = 127.39\angle(-25.89^\circ)\ \text{A} \approx 127.4\angle(-25.9^\circ)\ \text{A}, \\
\mathbf{V} &= \mathbf{I}_2 Z_p = (127.39\angle{-25.89^\circ}\ \text{A})(3.1241\angle 25.71^\circ\ \Omega) = 397.98\angle(-0.18^\circ)\ \text{V} \approx 398.0\angle(-0.18^\circ)\ \text{V}.
\end{aligned}
$$

The cable drops only about $2.0\ \text{V}$ in magnitude and shifts the phase by $-0.18^\circ$.

(c) The furnace branch current is $\mathbf I_1=\dfrac{\mathbf V}{Z_{\text{load}}}=\dfrac{397.98\angle(-0.18^\circ)\ \text{V}}{1.8621\angle57.52^\circ\ \Omega}=213.73\angle(-57.70^\circ)\ \text{A}$, so for the furnace alone

$$
\begin{aligned}
P_{\text{load}} &= I_1^2 R_1 = (213.73\ \text{A})^2(1.00\ \Omega) = 45.68\ \text{kW}, \\
Q_{\text{load}} &= I_1^2 X_{L1} = (213.73\ \text{A})^2(1.5708\ \Omega) = +71.75\ \text{kVAR}, \\
\text{PF}_{\text{load}} &= \cos(57.52^\circ) = 0.537\text{ lagging} \approx 0.54\text{ lagging}.
\end{aligned}
$$

At the supply terminals,

$$
\begin{aligned}
\mathbf{S}_s &= \mathbf{V}_s\mathbf{I}_2^* = (400\angle 0^\circ\ \text{V})(127.39\angle{+25.89^\circ}\ \text{A}) = 50.96\angle 25.89^\circ\ \text{kVA} \\
&= 45.84\ \text{kW} + j22.25\ \text{kVAR}, \\
\text{PF}_{\text{supply}} &= \cos(25.89^\circ) = 0.900\text{ lagging}.
\end{aligned}
$$

![[ee_t8_q3_power_factor.png|900]]

> [!check] Element-by-element P and Q
> The furnace takes $P_{\text{load}}=45.680\ \text{kW}$ and $Q_{\text{load}}=+71.754\ \text{kVAR}$. The capacitor at $V=397.98\ \text{V}$ takes $P_C=0\ \text{kW}$ and $Q_C=-\omega CV^2=-(314.159)(10^{-3})(397.98)^2=-49.759\ \text{kVAR}$. The cable at $I_2=127.39\ \text{A}$ takes $P_{\text{cab}}=I_2^2R_2=(127.39)^2(0.01)=0.162\ \text{kW}$ and $Q_{\text{cab}}=I_2^2X_{L2}=(127.39)^2(0.01571)=+0.255\ \text{kVAR}$. The sums $\sum P=45.680+0+0.162=45.842\ \text{kW}=P_s$ and $\sum Q=+71.754-49.759+0.255=+22.250\ \text{kVAR}=Q_s$ match the supply. Without the $1\ \text{mF}$ capacitor the cable current would rise from $127.4\ \text{A}$ to $212.7\ \text{A}$ and the cable loss by a factor $(212.7/127.4)^2=2.79$, from $162\ \text{W}$ to $452\ \text{W}$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 D3 - AC Filters and Bode Plots]]
- Next: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- Concepts: [[Active, Reactive and Apparent Power]] · [[Power Factor Correction]] · [[RMS Value]]
- Tutorial: [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions]] (Q3)
- Aircraft AC distribution: airliners distribute $115\ \text{V}_{\text{rms}}$, $400\ \text{Hz}$ three-phase power to inductive actuator motors, fans and transformer-rectifier units, and alternators and busbars are rated in kVA ($|\mathbf S|$) rather than kW ($P$), because winding temperature is set by $I^2R$ heating and core saturation by $V$. See [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] and [[FEEG1004 C3 - Transformers and AC Power Transmission]].
- Spacecraft power: spacecraft buses run on DC ($Q=0$), but the same component-by-component power balance, $\sum P_{\text{loads}}+P_{\text{harness}}=P_{\text{array}}$, underpins solar-array and battery sizing in [[SESA2024 08 - Electrical Power Subsystem]] and [[Battery Sizing]].
- Three-phase power: single-phase power $p(t)=P(1+\cos2\omega t)+Q\sin2\omega t$ pulses at $2\omega$ (causing $100\ \text{Hz}$ torque vibration in single-phase motors), whereas the three phase powers of a balanced system sum to the constant $p_{3\phi}(t)=3VI\cos\phi=P_{3\phi}$. See [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems#Proof of constant instantaneous power and the three-phase power formula]] and [[Three-Phase Star and Delta Connections]].

## Sources

- `02 - Sources/S2 AC Analysis/S2-W25 AC Analysis 04 - AC Power - Lecture Slides.pdf`: active and reactive power definitions, the $10\ \text{A}$ element recap (slides 2–3), mixed-load power equations, complex power $\mathbf S=\mathbf V\mathbf I^*=P+jQ$, apparent power, power factor, and the $50\angle0^\circ\ \text{V}$ into $6+j11.31\ \Omega$ example (slides 5 and 8).
- `02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf` (Section 4, Power in AC Circuits, pp. 20–27): derivations of $p(t)$ for pure $R$, $L$, $C$ and general loads, complex power, power-factor effects on line loss and voltage regulation (Figs. 36–37), and the $80\ \text{kVA}$, $400\ \text{V}$, $1\ \text{mF}$ correction example (Figs. 38–40, pp. 26–27).
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-03-18.txt` (ll. 159–376): instantaneous power in resistors, inductors and capacitors, active against reactive power, VAR units, conservation of $P$ and $Q$, and the mixed-load calculations.
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf`, Q3: industrial furnace with cable impedance and $1\ \text{mF}$ correction capacitor.
- All worked-example values and the element-by-element checks recomputed in Python.

## Self-study tasks

### Core

- [ ] Find $P$ and $Q$ for a $4\ \Omega$ resistor, a $5\ \Omega$ inductive reactance and a $3\ \Omega$ capacitive reactance each carrying $10\ \text{A}$ RMS (Lecture 2025-03-18, ll. 295–318; AC Analysis 04 slides 2–3). → [[#Power in single elements and an inductive load]]
- [ ] Find $\mathbf I$, $P$, $Q$, $\mathbf S$ and the power factor for $Z=6+j11.31\ \Omega$ across $50\angle0^\circ\ \text{V}$ (Lecture 2025-03-18, ll. 342–376; AC Analysis 04 slides 5 and 8). → [[#Power in single elements and an inductive load]]
- [ ] Correct an $80\ \text{kVA}$, $0.5$ lagging load with $1\ \text{mF}$ across $400\ \text{V}$, $50\ \text{Hz}$: find $P$, $Q_0$, $Q_C$, $Q_{\text{new}}$, $S_{\text{new}}$ and the new power factor (Niu notes, pp. 26–27). → [[#Correcting an 80 kVA industrial load]]
- [ ] For the furnace ($1\ \Omega$, $5\ \text{mH}$) fed through a cable ($0.01\ \Omega$, $50\ \mu\text{H}$) with $1\ \text{mF}$ across it on $400\ \text{V}$, $50\ \text{Hz}$, find the furnace voltage, the furnace power and power factor, the cable current, and the supply power and power factor (Tutorial Sheet 8 Q3). → [[#Furnace fed through a cable with a shunt capacitor]]; [[FEEG1004 Tutorial 8 - Filters, Transfer Functions and Power Factor Solutions#Q3: Furnace (R_1 = 1 Ω, L_1 = 5 mH) fed through a cable (0.01 Ω, 50 µH), with 1 mF across the load, 400 V at 50 Hz|Tutorial 8 Q3]]

### Further practice

- [ ] Size the shunt capacitor that brings the $80\ \text{kVA}$, $0.50$ lagging plant on $400\ \text{V}$, $50\ \text{Hz}$ to $0.95$ lagging (suggested, not lecturer-set). Answer: $\phi_2=\arccos(0.95)=18.19^\circ$, $Q_{\text{new}}=40\tan(18.19^\circ)=13.15\ \text{kVAR}$, $|Q_C|=69.28-13.15=56.13\ \text{kVAR}$, so $C=\dfrac{56\,135}{100\pi\times400^2}=1.12\ \text{mF}$. → [[#4. Power factor correction with a shunt capacitor]]

## Transcript and slide slips

> [!warning] Double negative in the capacitive reactive power formula (Niu notes, p. 22, Eq. 21)
> Where: [[#Capacitor: zero average power and generated reactive power]], [[#Splitting the power of a load with any phase shift]]
> On p. 22 of `S2 AC Analysis Lecture Notes 2021 - Niu.pdf`, Figure 33 defines the phase angle of a capacitive load as negative ($\phi<0$, so $\sin\phi<0$), and Equation (21) then writes "$Q_C=-I^2X_C=-VI\sin\phi$". A minus sign in front of $VI\sin\phi$ when $\phi$ is already negative double-negates the expression and would make $Q_C$ positive. With $\phi=\theta_v-\theta_i$ carrying its sign ($\phi=-90^\circ$ for a pure capacitor), the general formula is $Q=+VI\sin\phi$, which evaluates to $VI\sin(-90^\circ)=-VI<0$; in terms of the magnitude $|\phi|$, $Q_C=-VI\sin|\phi|=-I^2X_C$.

> [!warning] Misprinted sin 60° and a VA/kVA unit slip in the correction example (Niu notes, pp. 26–27)
> Where: [[#Correcting an 80 kVA industrial load]]
> On p. 26 the initial reactive power is printed as "$Q=|S|\sin\phi=80\times0.886=69\ \text{kVAR}$", misprinting $\sin(60^\circ)=0.8660$ as $0.886$, although the product $80\times0.8660=69.28\approx69\ \text{kVAR}$ uses $0.866$. On p. 27 the new apparent power is printed as "$|S|=(\sqrt{40^2+19^2}=44\ \text{VA}$", with an unmatched opening parenthesis and the unit VA instead of kVA ($44\ \text{kVA}$).
