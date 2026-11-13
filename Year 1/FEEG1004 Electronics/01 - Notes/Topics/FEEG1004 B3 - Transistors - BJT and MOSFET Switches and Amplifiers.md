---
title: "FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 3
tags: [feeg1004, electronics, transistor, bjt, mosfet, jfet, switch, amplifier, common-emitter]
aliases: ["EL2 transistors", "BJT", "MOSFET", "Transistor switch", "Common-emitter amplifier"]
date: 2026-09-27
status: lectured
coverage: "JKA 2a Bipolar junction transistors ll. 1–280; JKA 2b Field effect transistors ll. 1–275; JKA 2c Transistors as switches ll. 1–187; L7 (20 Nov 2024) ll. 1–543."
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 B1 - Semiconductors and Diodes]]", "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
next_topics: ["[[FEEG1004 B4 - Operational Amplifiers]]"]
key_concepts: ["[[Bipolar Junction Transistor]]", "[[MOSFET]]", "[[Transistor as a Switch]]", "[[Flyback Diode]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]"]
sources:
  - "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"
  - "02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2a.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2b.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2c.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 7.txt"
---

# FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers

> [!abstract] Summary
> A transistor uses a small input signal to control a much larger current in an external circuit, either as a proportional amplifier in its linear active region or as a solid-state switch toggling between cut-off and saturation. In an npn bipolar junction transistor (BJT), forward-biasing the base–emitter junction ($V_{BE}\approx 0.7\ \mathrm V$) injects a base current $I_B$ that sets a collector current $I_C=\beta I_B$ ($\beta\approx 100$–$200$) in the active region, until the external load limits $I_C$ and the collector–emitter voltage falls to $V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V$. In a field-effect transistor (JFET or MOSFET), the gate–source voltage $V_{GS}$ sets up an electric field that controls the conductivity of a semiconductor channel while drawing virtually no DC gate current; driven well above its threshold $V_{GS(\mathrm{th})}$, a MOSFET acts as a low-resistance switch $R_{DS(\mathrm{on})}$.

> [!summary]- Exam use: quick path
> - **Use it when:** sizing base and collector resistors for a BJT switch, verifying whether a BJT is in cut-off, active mode or saturation, analysing a biased common-emitter or common-source amplifier, or calculating current and power dissipation in a MOSFET switch.
> - **Assumptions:** npn BJT with $V_{BE}=0.7\ \mathrm V$ when conducting, constant DC current gain $\beta$ in the active region, and $V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V$ (or $0\ \mathrm V$ ideal switch) in saturation; enhancement-mode n-channel MOSFET with zero DC gate current ($I_G=0$), OFF for $V_{GS}<V_{GS(\mathrm{th})}$, and ohmic ON resistance $R_{DS(\mathrm{on})}$ when driven well above threshold.
> - **Method:** 1. For a BJT, find the base current from the input loop using $I_B=(V_{\mathrm{in}}-0.7\ \mathrm V)/R_B$ (or $I_B=0$ if $V_{\mathrm{in}}<0.7\ \mathrm V$). 2. Find the maximum collector current that the external collector loop can supply at saturation: $I_{C(\mathrm{sat})}=(V_{CC}-V_{\mathrm{load}}-V_{CE(\mathrm{sat})})/R_C$. 3. Compare $\beta I_B$ against $I_{C(\mathrm{sat})}$: if $\beta I_B<I_{C(\mathrm{sat})}$, the BJT is in the active mode with $I_C=\beta I_B$ and $V_{CE}=V_{CC}-V_{\mathrm{load}}-I_CR_C$; if $\beta I_B\ge I_{C(\mathrm{sat})}$, the BJT is saturated with $V_{CE}=V_{CE(\mathrm{sat})}$ and $I_C=I_{C(\mathrm{sat})}$. 4. For a MOSFET switch, find $V_{GS}$ with $I_G=0$ (unloaded divider), check $V_{GS}>V_{GS(\mathrm{th})}$, and use $P=I_D^2R_{DS(\mathrm{on})}$ for ON-state switch heating.
> - **Common mistakes:** applying $I_C=\beta I_B$ after the transistor has already saturated (where $I_C$ is fixed by the collector supply and load resistance, so $I_C<\beta I_B$); choosing $R_B$ at the exact active-to-saturation boundary without an overdrive margin, leaving the switch vulnerable to $\beta$ variations.
> - **Practise:** [[#Worked examples]] · [[#BJT switch design with base overdrive and saturation check]]

Microcontrollers, logic gates and sensors work at low currents. A digital output pin on an Arduino can source at most $20\ \mathrm{mA}$ continuously, and its on-board $5\ \mathrm V$ and $3.3\ \mathrm V$ regulators are limited to about $500\ \mathrm{mA}$ and $50\text{–}100\ \mathrm{mA}$. Connecting a DC motor, a high-power LED array or a relay coil that draws hundreds of milliamperes or several amperes directly to a digital pin would destroy the output stage, while a series resistor large enough to keep the current below $20\ \mathrm{mA}$ would starve the motor of the current it needs to turn. A transistor solves this interfacing problem: the low-current control pin switches or modulates a much larger current drawn from a separate power rail.

Three-terminal semiconductor transistors use one of two physical mechanisms. A **bipolar junction transistor (BJT)** is **current-controlled**: a small base current $I_B$ injected across a forward-biased base–emitter junction sweeps a much larger collector current $I_C$ across a thin base region. A **field-effect transistor (FET)**, most commonly a **metal-oxide-semiconductor FET (MOSFET)**, is **voltage-controlled**: a voltage $V_{GS}$ applied to an insulated metal gate creates an electric field that forms or pinches a conducting channel between source and drain without drawing DC input current.

## 1. The bipolar junction transistor (BJT) and the load line

A bipolar junction transistor consists of three adjacent doped regions in a single silicon crystal, forming two p-n junctions back to back. An **npn** device has a thin p-type **base** between an n-type **emitter** and an n-type **collector**; a **pnp** device has an n-type base between a p-type emitter and a p-type collector. On the circuit symbol the arrow is always on the emitter leg and points in the direction of conventional current: out of the emitter for an npn transistor (the mnemonic is "not pointing in") and into it for a pnp transistor.

The **npn** transistor is the standard choice for low-side switching and amplification with a positive supply rail. If a voltage $V_{CE}$ is connected between collector (positive) and emitter (negative) with the base left unconnected ($I_B=0$), the base–collector junction is reverse-biased, so no current flows from collector to emitter apart from a tiny thermal leakage current. To turn the transistor on, a control supply forward-biases the base–emitter junction ($V_{BE}\approx 0.7\ \mathrm V$ for silicon) while the collector is held above the base so that the base–collector junction stays reverse-biased.

The doping makes this work. The emitter is heavily doped with n-type donors, so forward-biasing the base–emitter junction injects a dense stream of conduction electrons into the base. The base is lightly doped with p-type acceptors and made very narrow (typically around $1\ \mu\mathrm m$), and the collector is also lightly doped, so the reverse-biased base–collector depletion region widens into the base and makes the neutral base layer even thinner. With so thin a base containing so few holes, only about $1\%$ of the injected electrons recombine there and leave through the base lead as the small base current $I_B$. The remaining $\approx 99\%$ diffuse across the base into the collector's depletion field and are swept into the positive collector terminal as the large collector current $I_C$.

By KCL applied to the transistor as a whole, the emitter current is the sum of the base and collector currents:

$$
I_E=I_B+I_C.
$$

In the **linear active mode**, the collector current is proportional to the base current:

$$
\boxed{I_C=\beta I_B},
$$

where $\beta$ (often written $h_{FE}$ on datasheets) is the DC **current gain**, typically $100$ to $200$ for a general-purpose small-signal or medium-power BJT. Substituting $I_C=\beta I_B$ into the KCL relation gives $I_E=(\beta+1)I_B\approx I_C$. Two BJTs joined so that the emitter of the first drives the base of the second form a **Darlington pair**, packaged as a single high-gain transistor whose overall current gain is the product of the individual gains, $\beta_{\mathrm{pair}}=\beta_1\beta_2$.

### Three operating modes and the collector load line

Suppose an npn transistor with grounded emitter drives a load connected to a positive supply rail $V_{CC}$: a resistor $R_L$ and an LED of forward drop $V_F$, or a collector resistor alone with $V_F=0$. KVL around the collector–emitter loop imposes a linear constraint between the collector current $I_C$ and the collector–emitter voltage $V_{CE}$:

$$
\begin{aligned}
V_{CC}-V_F-I_CR_L-V_{CE}&=0,\\
\boxed{V_{CE}=(V_{CC}-V_F)-I_CR_L}.
\end{aligned}
$$

![[ee_b3_bjt_characteristics.png|900]]

The output characteristic plots $I_C$ against $V_{CE}$ for several fixed values of $I_B$. Each curve rises steeply from the origin for $V_{CE}\lesssim 0.2\ \mathrm V$ and then flattens into an almost horizontal line at $I_C=\beta I_B$. The external circuit equation $V_{CE}=(V_{CC}-V_F)-I_CR_L$ plots as a straight, downward-sloping **load line**. In the figure (orange line, $V_{CC}=12\ \mathrm V$, $V_F=2.4\ \mathrm V$, $R_L=31.3\ \Omega$, so $V_{CE}=9.6\ \mathrm V-(31.3\ \Omega)I_C$) it runs from the horizontal-axis intercept at $I_C=0$, $V_{CE}=V_{CC}-V_F=9.6\ \mathrm V$ to the vertical-axis intercept at $V_{CE}=0$, $I_C=(V_{CC}-V_F)/R_L=306\ \mathrm{mA}$.

Both the transistor characteristic and KVL must hold at once, so the operating point is the intersection of the load line with the curve for the actual base current. As $I_B$ increases, the operating point moves along the load line from right to left through three modes.

In **cut-off** (switch OFF, bottom-right end of the load line), the base voltage is below the turn-on threshold ($V_{BE}<0.7\ \mathrm V$), so no base current flows ($I_B=0$). Both junctions block and $I_C=0$, nothing is dropped across the load ($I_CR_L=0$), and the whole available supply voltage appears across the open switch, $V_{CE}=V_{CC}-V_F$.

In the **active (linear) mode** (middle of the load line, used for amplifiers), moderate base currents put the intersection on the flat part of the characteristic, where $V_{CE}>V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V$. The transistor acts as a current-controlled current source with $V_{BE}=0.7\ \mathrm V$ and $I_C=\beta I_B$. As $I_B$ increases, $I_C$ rises in proportion, the drop $I_CR_L$ across the load grows and $V_{CE}$ moves leftwards down the load line.

In **saturation** (switch ON, top-left end of the load line), $I_B$ is large enough that $\beta I_B$ reaches the top-left knee of the load line and $V_{CE}$ falls to the saturation floor $V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V$, often approximated as $0\ \mathrm V$ for an ideal switch. The transistor is then turned on as hard as it can go, and the external load resistance $R_L$ and the supply $V_{CC}$ limit the collector current to

$$
\boxed{I_{C(\mathrm{sat})}=\frac{V_{CC}-V_F-V_{CE(\mathrm{sat})}}{R_L}}.
$$

Increasing $I_B$ further cannot raise $I_C$ beyond $I_{C(\mathrm{sat})}$, so in saturation the active relation no longer holds and

$$
I_C=I_{C(\mathrm{sat})}<\beta I_B,\qquad V_{CE}=V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V.
$$

## 2. Designing a BJT saturated switch with base overdrive

In an npn low-side switch (`ee_b3_transistor_switches.png`(a)), the load and its current-limiting resistor $R_L$ sit in the collector branch between $+V_{CC}$ and the collector, the emitter is connected directly to the $0\ \mathrm V$ rail, and the digital control voltage $V_{\mathrm{in}}$ drives the base through a base resistor $R_B$.

![[ee_b3_transistor_switches.png|900]]

With the transistor saturated ($V_{CE}=V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V$) at the required load current $I_C=I_{C(\mathrm{sat})}$, KVL around the collector loop gives the load series resistor:

$$
\begin{aligned}
V_{CC}-V_F-I_{C(\mathrm{sat})}R_L-V_{CE(\mathrm{sat})}&=0,\\
I_{C(\mathrm{sat})}R_L&=V_{CC}-V_F-V_{CE(\mathrm{sat})},\\
\boxed{R_L=\frac{V_{CC}-V_F-V_{CE(\mathrm{sat})}}{I_{C(\mathrm{sat})}}}.
\end{aligned}
$$

The minimum base current needed just to reach the edge of saturation is

$$
I_{B,\min}=\frac{I_{C(\mathrm{sat})}}{\beta}.
$$

The forward-biased base–emitter junction drops $V_{BE}=0.7\ \mathrm V$ with the emitter at $0\ \mathrm V$, so KVL around the base input loop gives

$$
\begin{aligned}
V_{\mathrm{in}}-I_BR_B-V_{BE}&=0,\\
I_BR_B&=V_{\mathrm{in}}-0.7\ \mathrm V,\\
I_B&=\frac{V_{\mathrm{in}}-0.7\ \mathrm V}{R_B}.
\end{aligned}
$$

Setting $I_B=I_{B,\min}$ gives the **maximum allowable base resistance**, at the boundary between active mode and saturation:

$$
\boxed{R_{B,\max}=\frac{V_{\mathrm{in}}-0.7\ \mathrm V}{I_{B,\min}}=\frac{\beta(V_{\mathrm{in}}-0.7\ \mathrm V)}{I_{C(\mathrm{sat})}}}.
$$

Choosing $R_B>R_{B,\max}$ gives too little base current ($I_B<I_{B,\min}$) and leaves the transistor in the active region with $I_C=\beta I_B<I_{C(\mathrm{sat})}$. The load then receives too little current, and the transistor drops several volts across $V_{CE}$, wasting power and overheating. Because $\beta$ varies widely between units and with temperature, practical designs choose $R_B$ smaller than $R_{B,\max}$ by an **overdrive factor** $k_{\mathrm{od}}\ge 2$, for example halving $R_B$ so that $I_B=k_{\mathrm{od}}I_{B,\min}$. The base current must still stay well within the microcontroller pin's $20\ \mathrm{mA}$ limit and the transistor's maximum base current rating. In saturation the extra base current does not increase $I_C$, which remains capped at $I_{C(\mathrm{sat})}$ by $R_L$, but it guarantees $\beta I_B>I_{C(\mathrm{sat})}$, so the switch stays firmly bottomed out at $V_{CE(\mathrm{sat})}\approx 0.2\ \mathrm V$.

When the switched collector load is inductive, such as a motor winding or a relay coil (as in the NTC thermistor thermostat of Mills Figure 1.6.7.2, p. 36), a reverse-biased **flyback (protective) diode** must be wired in parallel with the coil, cathode to $+V_{CC}$ and anode to the collector. When the transistor turns off and interrupts the coil current $i$, the collapsing magnetic flux induces a back EMF $v_L=L\,di/dt$ that drives the collector above $+V_{CC}$. Without the diode this spike can reach hundreds of volts and punch through the collector–base junction. With the diode present, the collector rises only to $V_{CC}+0.7\ \mathrm V$ ($12.7\ \mathrm V$ on a $12\ \mathrm V$ supply) before the diode becomes forward-biased, clamps it there and circulates the decaying coil current safely around the coil–diode loop (as derived in [[FEEG1004 A7 - Thevenin, Superposition and Relays]]).

## 3. The BJT common-emitter amplifier

To use the BJT as a linear voltage amplifier rather than a switch, it is operated in the middle of its active region, where $I_C=\beta I_B$. In the basic **common-emitter configuration**, named because the grounded emitter is shared by the input base loop and the output collector loop, a collector resistor $R_C$ connects the collector to the DC supply rail $V_C$ (or $V_{CC}$).

KVL from the supply rail through $R_C$ to the collector output node $V_{\mathrm{out}}$ gives

$$
\begin{aligned}
V_{\mathrm{out}}&=V_{CC}-V_{R_C},\\
V_{\mathrm{out}}&=V_{CC}-I_CR_C.
\end{aligned}
$$

Substituting the active-region law $I_C=\beta I_B$ gives the collector voltage in terms of the base current:

$$
\boxed{V_{\mathrm{out}}=V_{CC}-\beta R_CI_B}.
$$

The base current is multiplied by the large factor $\beta R_C$ with a minus sign, so a small increase in $I_B$ produces a large decrease in $V_{\mathrm{out}}$, and a small decrease produces a large increase. The common-emitter amplifier is therefore an **inverting amplifier**, introducing a $180^\circ$ phase shift between a sinusoidal input and its amplified output.

### DC quiescent biasing and AC coupling capacitors

An unbiased transistor cannot amplify an AC signal directly, because the base–emitter diode needs at least $+0.7\ \mathrm V$ to conduct and blocks completely whenever the input falls below that, clipping the negative half-cycles. A practical common-emitter AC amplifier (Mills Figure 1.6.2.2, p. 26) adds a **bias resistor** $R_B$ from the supply rail $V_{CC}$ to the base, together with **input and output coupling capacitors** $C_1$ and $C_2$.

With no AC input ($i_b=0$, $i_c=0$, $v_c=0$), the circuit sits at its quiescent DC operating point. At DC steady state the capacitors are open circuits ($i=C\,dv/dt=0$), and $V_{CC}$ drives a steady **quiescent base current** $I_B$ through $R_B$ into the forward-biased base–emitter junction ($V_{BE}=0.7\ \mathrm V$):

$$
\begin{aligned}
V_{CC}-I_BR_B-0.7\ \mathrm V&=0,\\
I_B&=\frac{V_{CC}-0.7\ \mathrm V}{R_B}.
\end{aligned}
$$

This sets a steady **quiescent collector current** $I_C=\beta I_B$ and a **quiescent collector voltage**

$$
V_C'=V_{CC}-I_CR_C=V_{CC}-\beta I_BR_C.
$$

For the collector voltage to swing equally upwards (towards cut-off at $V_{CC}$) and downwards (towards saturation near $0\ \mathrm V$) without clipping either peak, $R_B$ and $R_C$ are chosen so that the quiescent collector drop is half the supply voltage:

$$
I_CR_C\approx\frac{1}{2}V_{CC}\implies V_C'\approx\frac{1}{2}V_{CC}.
$$

When an AC signal $v_{\mathrm{in}}(t)$ is applied, the input coupling capacitor $C_1$ passes the time-varying signal ($i=C\,dv/dt$) into the base while stopping the $0.7\ \mathrm V$ DC base voltage from leaking back into the signal source. On a positive half-cycle of $v_{\mathrm{in}}$ the base current rises to $I_B+i_b$ and the collector current to $I_C+i_c$, with $i_c=\beta i_b$, so the instantaneous collector voltage is

$$
\begin{aligned}
v_C^{\mathrm{total}}(t)&=V_{CC}-(I_C+i_c)R_C,\\
v_C^{\mathrm{total}}(t)&=(V_{CC}-I_CR_C)-i_cR_C,\\
v_C^{\mathrm{total}}(t)&=V_C'+v_c(t),\qquad v_c(t)=-i_cR_C=-\beta R_Ci_b.
\end{aligned}
$$

The output coupling capacitor $C_2$ blocks the steady quiescent offset $V_C'$ and passes the amplified, inverted AC variation $v_{\mathrm{out}}(t)=v_c(t)=-i_cR_C$ to the external load. Together with the load resistance it forms a high-pass filter that passes signal frequencies and rejects DC.

![[ee_b3_common_emitter_waveforms.png|900]]

## 4. Field-effect transistors (JFET and MOSFET)

A **field-effect transistor (FET)** has three terminals, the **drain ($D$)**, **gate ($G$)** and **source ($S$)**, which correspond functionally to the collector, base and emitter of a BJT. Instead of injecting a base current across a forward-biased junction, a FET applies a control voltage $V_{GS}$ between gate and source to set up an electric field that controls the drain–source current $I_D$. The gate is either a reverse-biased p-n junction (**JFET**) or a metal electrode separated from the silicon by a thin insulating layer of silicon dioxide glass, $\mathrm{SiO_2}$ (**MOSFET**). Either way the DC gate current is nearly zero ($I_G\approx 0$) and the input resistance is extremely high ($\mathrm{M\Omega}$ to $\mathrm{T\Omega}$). FETs are also less sensitive to temperature than BJTs and pack much more densely on integrated circuits, although an individual FET typically gives lower small-signal voltage gain than a BJT.

### JFET and MOSFET operating mechanisms

Three n-channel FET structures are used; their p-channel counterparts work in the same way with reversed dopants, voltages and current directions.

The **n-channel junction FET (JFET)** is an n-type bar between source and drain, with p-type gate regions diffused into both sides. At $V_{GS}=0$ the channel conducts like a resistor of resistance $R=\rho L/A$. A negative gate–source voltage ($V_{GS}<0$) reverse-biases the gate–channel junctions, widening their depletion regions into the channel and reducing its conducting cross-section $A$, which raises the resistance and reduces $I_D$. The channel potential rises from $0\ \mathrm V$ at the source to $+V_{DS}$ at the drain, so the reverse bias is greatest near the drain and the depletion regions taper until they meet at the **pinch-off** point. Beyond pinch-off, $I_D$ saturates at a nearly constant value set by $V_{GS}$.

The **n-channel enhancement-mode MOSFET** is the standard power and digital switch. Two n-type regions (source and drain) are diffused into a p-type substrate and separated by a p-type region under an aluminium gate, which is insulated by a thin $\mathrm{SiO_2}$ layer. At $V_{GS}=0$ the source–substrate and drain–substrate junctions form two back-to-back diodes, so no channel exists and the transistor is OFF. A positive gate–source voltage above the **threshold voltage** $V_{GS(\mathrm{th})}\approx 1\text{–}2\ \mathrm V$ repels holes and attracts minority-carrier electrons from the substrate to the oxide interface. These form an n-type **inversion layer** that connects source to drain and lets $I_D$ flow. Raising $V_{GS}$ further draws more electrons into the inversion layer and increases $I_D$.

In the **n-channel depletion-mode MOSFET**, a continuous n-type channel is diffused under the insulated gate during manufacture, so the device conducts at $V_{GS}=0$. A negative $V_{GS}$ repels electrons from the channel, depleting it and reducing $I_D$, whereas a positive $V_{GS}$ attracts extra electrons and enhances conduction.

### MOSFET common-source amplifier and MOSFET switches

In an n-channel enhancement-mode **common-source amplifier** (Mills Figure 1.6.6, p. 33), resistors $R_1$ (from $+V_{\mathrm{supply}}$ to the gate) and $R_2$ (from the gate to $0\ \mathrm V$) form a potential divider that holds the gate at a quiescent bias $V_G$ above the threshold $V_{GS(\mathrm{th})}$. The insulated gate draws no DC current ($I_G=0$), so the unloaded divider equation applies exactly:

$$
\boxed{V_{GS}=V_G=V_{\mathrm{supply}}\frac{R_2}{R_1+R_2}}.
$$

As in the BJT common-emitter stage, an input capacitor $C_1$ couples the AC input onto the gate, modulating $I_D$ through the drain resistor $R_3$, and an output capacitor $C_2$ couples the inverted AC drain voltage ($v_{\mathrm{out}}=-i_dR_3$) to the load.

An enhancement-mode MOSFET used as a **power switch** (`ee_b3_transistor_switches.png`(b)) and driven with $V_{GS}$ well above $V_{GS(\mathrm{th})}$ has an inversion channel that behaves as a small ohmic **on-state resistance** $R_{DS(\mathrm{on})}$ between drain and source. A steady drain (load) current $I_D$ then produces a drain–source voltage drop and a switch dissipation given by Ohm's law and Joule heating:

$$
\begin{aligned}
V_{DS(\mathrm{on})}&=I_DR_{DS(\mathrm{on})},\\
\boxed{P_{\mathrm{MOSFET}}=I_D^2R_{DS(\mathrm{on})}}.
\end{aligned}
$$

Solving for $I_D$ gives the maximum steady current the MOSFET can carry without exceeding a specified thermal dissipation limit $P_{\max}$, which is carried to ambient air through a heatsink:

$$
\begin{aligned}
I_D^2&=\frac{P_{\max}}{R_{DS(\mathrm{on})}},\\
\boxed{I_{D,\max}=\sqrt{\frac{P_{\max}}{R_{DS(\mathrm{on})}}}}.
\end{aligned}
$$

## Worked examples

### BJT switch design with base overdrive and saturation check

A $V_{\mathrm{in}}=5.0\ \mathrm V$ control signal switches an npn BJT ($\beta=100$, $V_{BE}=0.70\ \mathrm V$, $V_{CE(\mathrm{sat})}=0.20\ \mathrm V$) that drives a high-power LED ($V_F=2.40\ \mathrm V$ at a target forward current $I_F=300\ \mathrm{mA}=0.300\ \mathrm A$) from a $V_{CC}=12.0\ \mathrm V$ collector supply (`ee_b3_transistor_switches.png`(a)).

With the base switch open, $I_B=0\ \mathrm{mA}$, the BJT is in cut-off, the collector current is $I_C=\boxed{0\ \mathrm{mA}}$ and the LED is off.

To size the collector current-limiting resistor $R_L$, take the BJT fully ON in saturation ($V_{CE}=V_{CE(\mathrm{sat})}=0.20\ \mathrm V$) with $I_C=I_F=0.300\ \mathrm A$. KVL around the collector–emitter stack gives the voltage across $R_L$:

$$
\begin{aligned}
V_{R_L}&=V_{CC}-V_F-V_{CE(\mathrm{sat})},\\
V_{R_L}&=12.0\ \mathrm V-2.40\ \mathrm V-0.20\ \mathrm V=9.40\ \mathrm V.
\end{aligned}
$$

Dividing by the required $0.300\ \mathrm A$ gives $R_L$:

$$
R_L=\frac{V_{R_L}}{I_C}=\frac{9.40\ \mathrm V}{0.300\ \mathrm A}=31.33\ \Omega\approx\boxed{31.3\ \Omega}.
$$

To reach $I_{C(\mathrm{sat})}=0.300\ \mathrm A$ at $\beta=100$, the minimum base current, at the active-to-saturation boundary, is

$$
I_{B,\min}=\frac{I_{C(\mathrm{sat})}}{\beta}=\frac{0.300\ \mathrm A}{100}=3.00\times 10^{-3}\ \mathrm A=\boxed{3.00\ \mathrm{mA}}.
$$

With $V_{BE}=0.70\ \mathrm V$ across the base–emitter diode, the voltage across $R_B$ is $V_{R_B}=5.00\ \mathrm V-0.70\ \mathrm V=4.30\ \mathrm V$, so the boundary resistor that gives exactly $3.00\ \mathrm{mA}$ is

$$
R_{B,\max}=\frac{5.00\ \mathrm V-0.70\ \mathrm V}{3.00\times 10^{-3}\ \mathrm A}=\frac{4.30\ \mathrm V}{0.00300\ \mathrm A}=1433\ \Omega\approx\boxed{1.43\ \mathrm{k\Omega}}.
$$

To keep the switch saturated even if $\beta$ drops below $100$, apply an overdrive factor by choosing a standard resistor near half of $R_{B,\max}$, say $R_B=680\ \Omega$. The base current is then

$$
I_B=\frac{5.00\ \mathrm V-0.70\ \mathrm V}{680\ \Omega}=\frac{4.30\ \mathrm V}{680\ \Omega}=6.32\times 10^{-3}\ \mathrm A=6.32\ \mathrm{mA},
$$

which is still well below an Arduino pin's $20\ \mathrm{mA}$ continuous limit. To verify saturation, compare the collector current that active mode would support,

$$
\beta I_B=100(6.32\ \mathrm{mA})=632\ \mathrm{mA},
$$

with $I_{C(\mathrm{sat})}$. Since $632\ \mathrm{mA}>300\ \mathrm{mA}$ (an overdrive factor of $k_{\mathrm{od}}=632/300=2.11$), the collector circuit cannot supply $\beta I_B$, and the BJT is deep in saturation with $V_{CE}=0.20\ \mathrm V$ and $I_C=300\ \mathrm{mA}$ fixed by $R_L$.

> [!check] Comparison of transistor heating in saturation vs under-driven active mode
> In the saturated design ($I_C=300\ \mathrm{mA}$, $V_{CE}=0.20\ \mathrm V$, $I_B=6.32\ \mathrm{mA}$), the total power dissipated in the BJT is $P_Q=V_{CE}I_C+V_{BE}I_B=(0.20\ \mathrm V)(0.300\ \mathrm A)+(0.70\ \mathrm V)(0.00632\ \mathrm A)=60.0\ \mathrm{mW}+4.4\ \mathrm{mW}=64.4\ \mathrm{mW}$. With $R_B$ too large at $4.30\ \mathrm{k\Omega}$, the base current falls to $I_B=4.30\ \mathrm V/4300\ \Omega=1.00\ \mathrm{mA}<I_{B,\min}$, leaving the BJT in the active region with $I_C=\beta I_B=100\ \mathrm{mA}$ (a dim LED) and $V_{CE}=12.0\ \mathrm V-2.40\ \mathrm V-(0.100\ \mathrm A)(31.33\ \Omega)=6.47\ \mathrm V$. The collector heating then rises tenfold to $P_Q=V_{CE}I_C=(6.47\ \mathrm V)(0.100\ \mathrm A)=647\ \mathrm{mW}$.

### Common-emitter amplifier quiescent bias and inverted AC output

The biased npn common-emitter amplifier of `ee_b3_common_emitter_waveforms.png` has supply rail $V_{CC}=12.0\ \mathrm V$, collector resistor $R_C=2.00\ \mathrm{k\Omega}=2000\ \Omega$, current gain $\beta=100$ and $V_{BE}=0.70\ \mathrm V$.

For a mid-rail quiescent point, the collector voltage is centred at half the supply ($V_C'=V_{CC}/2=6.00\ \mathrm V$) so that the output can swing symmetrically by up to $\pm 6.00\ \mathrm V$. The quiescent drop across $R_C$ must then be $6.00\ \mathrm V$, which fixes the quiescent collector and base currents:

$$
\begin{aligned}
I_C&=\frac{V_{CC}-V_C'}{R_C}=\frac{12.0\ \mathrm V-6.00\ \mathrm V}{2000\ \Omega}=3.00\times 10^{-3}\ \mathrm A=3.00\ \mathrm{mA},\\
I_B&=\frac{I_C}{\beta}=\frac{3.00\times 10^{-3}\ \mathrm A}{100}=3.00\times 10^{-5}\ \mathrm A=30.0\ \mu\mathrm A.
\end{aligned}
$$

KVL from the $12.0\ \mathrm V$ rail through $R_B$ to the $0.70\ \mathrm V$ base gives the bias resistance:

$$
R_B=\frac{V_{CC}-V_{BE}}{I_B}=\frac{12.0\ \mathrm V-0.70\ \mathrm V}{30.0\times 10^{-6}\ \mathrm A}=\frac{11.3\ \mathrm V}{30.0\times 10^{-6}\ \mathrm A}=\boxed{376.7\ \mathrm{k\Omega}}.
$$

A sinusoidal base current variation $i_b(t)=(10.0\ \mu\mathrm A)\sin(\omega t)$ is superimposed through $C_1$ on $I_B=30.0\ \mu\mathrm A$. The total base current oscillates between $20.0\ \mu\mathrm A$ and $40.0\ \mu\mathrm A$ and stays positive, so the base–emitter junction never cuts off. In the active region the collector current varies by

$$
i_c(t)=\beta i_b(t)=100(10.0\ \mu\mathrm A)\sin(\omega t)=(1.00\ \mathrm{mA})\sin(\omega t)
$$

about $I_C=3.00\ \mathrm{mA}$ (between $2.00\ \mathrm{mA}$ and $4.00\ \mathrm{mA}$), and the total collector voltage is

$$
\begin{aligned}
v_C^{\mathrm{total}}(t)&=V_{CC}-\big(I_C+i_c(t)\big)R_C,\\
v_C^{\mathrm{total}}(t)&=12.0\ \mathrm V-\big(3.00\ \mathrm{mA}+(1.00\ \mathrm{mA})\sin(\omega t)\big)(2.00\ \mathrm{k\Omega}),\\
v_C^{\mathrm{total}}(t)&=6.00\ \mathrm V-(2.00\ \mathrm V)\sin(\omega t).
\end{aligned}
$$

After $C_2$ removes the $6.00\ \mathrm V$ DC offset, the AC output is $\boxed{v_{\mathrm{out}}(t)=-(2.00\ \mathrm V)\sin(\omega t)}$, swinging by $\pm 2.00\ \mathrm V$ and $180^\circ$ out of phase with the input.

> [!check] Active-region margin check at both signal peaks
> At the positive input peak ($I_B+i_b=40.0\ \mu\mathrm A$, $I_C+i_c=4.00\ \mathrm{mA}$), the collector voltage reaches its minimum, $v_{C,\min}^{\mathrm{total}}=12.0\ \mathrm V-(4.00\ \mathrm{mA})(2.00\ \mathrm{k\Omega})=4.00\ \mathrm V$, well above the saturation floor $V_{CE(\mathrm{sat})}=0.20\ \mathrm V$. At the negative input peak ($I_B+i_b=20.0\ \mu\mathrm A$, $I_C+i_c=2.00\ \mathrm{mA}$), it reaches $v_{C,\max}^{\mathrm{total}}=8.00\ \mathrm V<12.0\ \mathrm V$, so operation stays linear and undistorted throughout the cycle.

### MOSFET motor switch current limit and gate-divider biasing

An n-channel enhancement-mode power MOSFET switching a DC motor has a datasheet on-resistance $R_{DS(\mathrm{on})}=0.040\ \Omega$, specified at $V_{GS}=10\ \mathrm V$. If the continuous power dissipated in the MOSFET is limited to $P_{\max}=100\ \mathrm W$ (removed through a heatsink), rearranging $P_{\max}=I_{D,\max}^2R_{DS(\mathrm{on})}$ gives the maximum steady motor current:

$$
\begin{aligned}
I_{D,\max}^2&=\frac{P_{\max}}{R_{DS(\mathrm{on})}},\\
I_{D,\max}&=\sqrt{\frac{100\ \mathrm W}{0.040\ \Omega}}=\sqrt{2500\ \mathrm{A^2}}=\boxed{50.0\ \mathrm A}.
\end{aligned}
$$

At $I_D=50.0\ \mathrm A$, the drain–source drop across the conducting MOSFET is

$$
V_{DS(\mathrm{on})}=I_{D,\max}R_{DS(\mathrm{on})}=(50.0\ \mathrm A)(0.040\ \Omega)=2.00\ \mathrm V,
$$

and $P=V_{DS(\mathrm{on})}I_{D,\max}=(2.00\ \mathrm V)(50.0\ \mathrm A)=100\ \mathrm W$. Although the device's absolute maximum power rating is listed as $200\ \mathrm W$, the continuous current cannot be raised above $50.0\ \mathrm A$, because the internal bond wires and package pins have a $50\ \mathrm A$ current limit.

The gate-bias examples of Mills §§1.6.6–1.6.7 rely on $I_G=0$. In Mills Figure 1.6.6 (p. 33), a $V_{\mathrm{supply}}=15.0\ \mathrm V$ rail biases a MOSFET gate through $R_1=910\ \mathrm{k\Omega}$ and $R_2=330\ \mathrm{k\Omega}$, so the quiescent gate–source voltage is

$$
V_{GS}=(15.0\ \mathrm V)\frac{330\ \mathrm{k\Omega}}{910\ \mathrm{k\Omega}+330\ \mathrm{k\Omega}}=\frac{4950}{1240}\ \mathrm V=\boxed{3.99\ \mathrm V},
$$

comfortably above the $1\text{–}2\ \mathrm V$ threshold needed to form the inversion layer. In the dark-activated lamp switch (Mills Figure 1.6.7.1, p. 35), a $V_S=6.0\ \mathrm V$ supply feeds a series resistor $R=1.8\ \mathrm{k\Omega}=1800\ \Omega$ above a reverse-biased photodiode connected to $0\ \mathrm V$. Their midpoint drives the MOSFET gate ($I_G=0$, $V_{GS(\mathrm{th})}\approx 2.0\ \mathrm V$). By KVL, a photocurrent $I_P$ through $R$ sets the gate voltage to

$$
V_{GS}=V_S-I_PR=6.0\ \mathrm V-I_P(1800\ \Omega).
$$

In bright room light, a photocurrent $I_P=3.0\ \mathrm{mA}$ drops $(3.0\ \mathrm{mA})(1.8\ \mathrm{k\Omega})=5.4\ \mathrm V$ across $R$ and holds $V_{GS}=6.0\ \mathrm V-5.4\ \mathrm V=0.60\ \mathrm V<2.0\ \mathrm V$, so the MOSFET is OFF and the $6.0\ \mathrm V$, $0.10\ \mathrm A$ lamp is dark. In darkness $I_P$ falls to the reverse leakage level ($\approx 1.0\ \mu\mathrm A$), the drop across $R$ is only $(1.0\ \mu\mathrm A)(1800\ \Omega)=1.8\ \mathrm{mV}$, and $V_{GS}$ rises to $5.998\ \mathrm V>V_{GS(\mathrm{th})}$. The MOSFET turns fully on and lights the $100\ \mathrm{mA}$ lamp while the sensor branch draws only $1.0\ \mu\mathrm A$.

> [!check] Threshold crossover photocurrent check
> Setting $V_{GS}=V_{GS(\mathrm{th})}=2.0\ \mathrm V$ in $V_{GS}=6.0\ \mathrm V-I_P(1800\ \Omega)$ gives the switching photocurrent $I_{P,\mathrm{crit}}=(6.0\ \mathrm V-2.0\ \mathrm V)/(1800\ \Omega)=2.22\ \mathrm{mA}$. Because $I_G=0$, the sensor branch never supplies control current to the transistor, whereas a BJT switching a $100\ \mathrm{mA}$ lamp at $\beta=100$ would need at least $1.0\ \mathrm{mA}$ of base current through $R=1.8\ \mathrm{k\Omega}$, which would load the divider and drop $1.8\ \mathrm V$ across $R$ even in total darkness.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Next: [[FEEG1004 B4 - Operational Amplifiers]]
- Concepts: [[Bipolar Junction Transistor]] · [[MOSFET]] · [[Transistor as a Switch]] · [[Flyback Diode]]
- Worked problems: [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]

## Sources

- `S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`, pp. 23–38 (§1.6.1: npn BJT structure and operation; §1.6.2: BJT common-emitter amplifier, biasing and coupling capacitors; §1.6.3–1.6.5: FET overview, JFET pinch-off, enhancement and depletion MOSFETs; §1.6.6: MOSFET common-source amplifier and Darlington pair; §1.6.7: photodiode MOSFET switch and NTC thermistor BJT relay thermostat with flyback diode).
- 2a Bipolar junction transistors, `FEEG1004 Lecture 2a.txt` (ll. 42–123: npn/pnp doping, thin lightly doped base, symbol arrow rule and $I_C=\beta I_B$; ll. 124–280: common-emitter inverter, $V_C'\approx V_{CC}/2$ quiescent biasing and $C_1,C_2$ AC coupling waveforms).
- 2b Field effect transistors, `FEEG1004 Lecture 2b.txt` (ll. 19–58: BJT vs FET comparison; ll. 59–139: n-channel JFET depletion wedge and pinch-off; ll. 140–224: enhancement and depletion MOSFETs, $\mathrm{SiO_2}$ insulated gate and inversion layer; ll. 225–275: MOSFET common-source amplifier with $910\ \mathrm{k\Omega}$ / $330\ \mathrm{k\Omega}$ gate divider).
- 2c Transistors as switches, `FEEG1004 Lecture 2c.txt` (ll. 10–69: photodiode–MOSFET light-activated lamp switch; ll. 70–165: NTC thermistor–BJT relay thermostat and $12.7\ \mathrm V$ flyback diode clamping).
- L7, `FEEG1004 Lecture 7.txt` (ll. 28–88: Arduino pin current limits and motor switch options A–E; ll. 89–213: BJT cut-off, active and saturation modes; ll. 214–370: $300\ \mathrm{mA}$, $2.4\ \mathrm V$ LED switch design for $I_B$, $R_B$ and $R_L$; ll. 371–419: active-mode common-emitter amplifier; ll. 420–543: MOSFET motor switch, flyback protection and $0.04\ \Omega$, $100\ \mathrm W\to 50\ \mathrm A$ calculation), matching `S1-W08-EL2 Transistors - Recorded.pdf`, pp. 3–16.
- All numerical values were recomputed in Python. Figures `ee_b3_bjt_characteristics.png`, `ee_b3_transistor_switches.png` and `ee_b3_common_emitter_waveforms.png` are generated by `generate_electronics_figures.py`.

## Self-study tasks

### Core

- [ ] Explain why an Arduino digital I/O pin ($20\ \mathrm{mA}$ limit) cannot drive a DC motor directly, and identify which of circuits A–E turn the motor without damaging the Arduino (L7, ll. 28–88; W8 pp. 3–4). → [[#1. The bipolar junction transistor (BJT) and the load line]]
- [ ] For the $12\ \mathrm V$ BJT switch driving a $300\ \mathrm{mA}$, $2.4\ \mathrm V$ LED ($\beta=100$, $V_{CE(\mathrm{sat})}=0.2\ \mathrm V$) from a $5\ \mathrm V$ control signal, find $I_C$ when the switch is open, the minimum base current $I_{B,\min}$, the boundary resistor $R_{B,\max}$, the effect of making $R_B$ larger or smaller, and the collector resistor $R_L$ (L7, ll. 214–343; W8 pp. 8–9). → [[#BJT switch design with base overdrive and saturation check]]
- [ ] Write the active-region expressions for $I_C$ and $V_{\mathrm{out}}$ in a common-emitter amplifier with supply $12\ \mathrm V$ and collector resistor $R_C$, and explain why the output is $180^\circ$ out of phase with the input (L7, ll. 371–398; W8 p. 11). → [[#3. The BJT common-emitter amplifier]]
- [ ] Draw a MOSFET low-side switch circuit controlled by a $5\ \mathrm V$ Arduino pin to drive an inductive motor with flyback spike protection, and calculate the maximum steady motor current for $R_{DS(\mathrm{on})}=0.04\ \Omega$ and $P_{\max}=100\ \mathrm W$ (L7, ll. 435–540; W8 pp. 14–16). → [[#MOSFET motor switch current limit and gate-divider biasing]]

### Further practice

- [ ] Explain the roles of the bias resistor $R_B$, the mid-rail quiescent point $V_C'\approx V_{CC}/2$, and the coupling capacitors $C_1$ and $C_2$ in a practical AC common-emitter amplifier (2a, ll. 165–279; L7, ll. 399–419; W8 p. 12). → [[#DC quiescent biasing and AC coupling capacitors]] · [[#Common-emitter amplifier quiescent bias and inverted AC output]]
- [ ] Calculate the quiescent gate voltage of the $15\ \mathrm V$, $910\ \mathrm{k\Omega}$ / $330\ \mathrm{k\Omega}$ MOSFET common-source amplifier and explain why the unloaded divider equation is exact at DC (2b, ll. 225–274; Mills §1.6.6). → [[#MOSFET motor switch current limit and gate-divider biasing]]
- [ ] Explain how the photodiode–MOSFET lamp switch and the NTC thermistor–BJT relay thermostat operate, including why the flyback diode across the $12\ \mathrm V$ relay coil clamps the collector at $12.7\ \mathrm V$ at switch-off (2c, ll. 10–165; Mills §1.6.7). → [[#2. Designing a BJT saturated switch with base overdrive]] · [[#MOSFET motor switch current limit and gate-divider biasing]]

## Transcript and slide slips

### Base current stated as 30 mA instead of 3 mA in L7

> [!warning] The 1433 ohm base resistor corresponds to 3 mA, not 30 mA
> Where: [[#BJT switch design with base overdrive and saturation check]]
> In `FEEG1004 Lecture 7.txt`, ll. 298–300, while calculating $R_B=(5\ \mathrm V-0.7\ \mathrm V)/I_B=1433\ \Omega$, the speaker says "to give us 30 milliamps and it comes out at 1,433". The required base current found on the preceding slide (l. 258 and W8 slide p. 8) is $I_B=300\ \mathrm{mA}/100=3\ \mathrm{mA}$, for which $4.3\ \mathrm V/0.003\ \mathrm A=1433\ \Omega$ ($30\ \mathrm{mA}$ would give $143\ \Omega$ and exceed the $20\ \mathrm{mA}$ digital pin limit).

### Verbal slips in L7 on MOSFET terminals and datasheet power rating

> [!warning] MOSFETs have insulated gates (not bases), and the datasheet power rating on slide 15 is 200 W (not 300 W)
> Where: [[#4. Field-effect transistors (JFET and MOSFET)]]
> In `FEEG1004 Lecture 7.txt`, l. 427 states that MOSFETs "draw very very little current like microamps into their bases"; the control terminal of a MOSFET is the gate (insulated by $\mathrm{SiO_2}$ so its DC gate current is nanoamperes or less, practically zero). Later at l. 507, the speaker reads the datasheet maximum power dissipation on W8 slide p. 15 as "300 watts", before correcting it to "rated at 200 watts" at l. 533 (matching $P_D=200\ \mathrm W$ on slides pp. 15–16).
