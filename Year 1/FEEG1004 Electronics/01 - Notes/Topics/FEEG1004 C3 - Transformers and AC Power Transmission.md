---
title: "FEEG1004 C3 - Transformers and AC Power Transmission"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 3
tags:
- feeg1004
- machines
- transformer
- turns-ratio
- emf-equation
- transmission
- ac-vs-dc
aliases:
- Electric Machines 04
- Transformer
- 4.44 f N Phi
- AC vs DC
date: 2026-09-27
status: written-ahead
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"
next_topics:
- "[[FEEG1004 C4 - DC Generators and the Commutator]]"
key_concepts:
- "[[Ideal Transformer]]"
- "[[Transformer EMF Equation]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"
sources:
- 02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf
- 02 - Sources/S2 Machines/S2-W18-21 Electric Machines 04 - Transformers and AC Power - Lecture Slides.pdf
- 02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf
coverage: "No matching lecture transcript in 02 - Sources/Lectures/; written ahead from S2 Electric Machines 04 slides and Sharkh §§3.4–3.5"
---

# FEEG1004 C3 - Transformers and AC Power Transmission

> [!abstract] Summary
> A transformer passes AC power from a primary winding of $N_1$ turns to a secondary of $N_2$ turns through the alternating flux in a shared laminated core. In the ideal (lossless, leakage-free) case Faraday's law and power conservation give $V_2/V_1 = N_2/N_1 = I_1/I_2$, and a secondary load $Z_L$ appears at the primary as $Z_L' = (N_1/N_2)^2 Z_L$. A sinusoidal core flux of peak $\Phi_m$ induces $E_{\text{rms}} = 4.44\,f N \Phi_m$, so the supply voltage and frequency fix the peak flux density, which must stay below about $1.5\ \text{T}$. Power is transmitted at high voltage because the line loss $I^2 R_{\text{line}} = (P/V)^2 R_{\text{line}}$ falls as $1/V^2$.

> [!summary]- Exam use: quick path
> - **Use it when:** stepping AC voltages and currents up or down; referring a load impedance through a transformer; finding peak core flux or flux density from the supply voltage; comparing transmission losses at different voltages.
> - **Assumptions:** ideal transformer (zero winding resistance, zero leakage flux, no core loss, negligible magnetising current); sinusoidal flux; RMS values throughout; unity power factor for the line-loss calculation.
> - **Method:** 1. Find the turns ratio $N_2/N_1$. 2. Get $V_2 = V_1 N_2/N_1$. 3. Get $\Phi_m = V_1/(4.44\,f N_1)$ and $B_m = \Phi_m/A$; check $B_m \lesssim 1.5\ \text{T}$. 4. From the load, find $I_2$, then $I_1 = I_2 N_2/N_1$ (or $I_1 = P/V_1$). 5. Refer impedances with $(N_1/N_2)^2$.
> - **Common mistakes:** inverting the current ratio (current steps down when voltage steps up); leaving the core area in $\text{cm}^2$ when computing $B_m$.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q5: Single-phase transformer, 70:350 turns, 100 cm² core, 230 V at 50 Hz|Tutorial 5 Q5]]

Many electronic loads, batteries and solar panels work on direct current, yet electrical energy is generated, transmitted across countries and distributed to factories and homes almost entirely as alternating current. The device that makes long-distance AC networks practical is the static power transformer, which steps voltage up for transmission and back down for safe use at efficiencies approaching $99\%$.

A transformer works only because the flux in its core keeps changing. The primary current sets up an alternating flux, and that flux, confined to the iron, links every turn of both windings, so each turn sees the same induced EMF. The secondary voltage is therefore set by the turns ratio. Power in equals power out, so current is scaled by the inverse ratio, and the secondary load reflects back to the supply scaled by the square of the ratio.

The induced EMF also limits the design. For a sinusoidal flux the primary voltage is proportional to frequency, turns and peak flux, so for a given supply the flux is fixed, and the core must be large enough to carry it without saturating. Lowering the frequency raises the flux, and on DC a transformer fails outright.

## 1. AC versus DC and high-voltage transmission

### DC and AC sources

Electrical sources fall into two classes, according to whether their polarity and current direction stay fixed or reverse periodically. **Direct current (DC)** sources keep a fixed direction and, in steady state, a constant magnitude: electrochemical batteries, fuel cells, solar photovoltaic (PV) panels, thermocouples and commutator DC generators ([[FEEG1004 C4 - DC Generators and the Commutator]]). **Alternating current (AC)** sources reverse periodically, almost always as a sinusoid $v(t) = V_m \sin(2\pi f t)$: synchronous generators ([[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]), induction generators and piezoelectric transducers.

Where DC sources such as solar PV farms or battery storage feed an AC grid, or an AC supply charges a DC battery in a laptop, electric vehicle or aircraft DC bus, solid-state power-electronic **converters** connect the two: rectifiers for $\text{AC} \to \text{DC}$ (as in [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]) and switched-mode inverters for $\text{DC} \to \text{AC}$.

### Why power systems use AC

Power grids run on AC for three reasons (Sharkh §3.4). First, AC is the natural output of rotating machines: as shown in [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]], a field sweeping past stationary stator coils induces a sinusoidal voltage without sliding commutators or brushes.

Second, AC is easier to interrupt. In a $50\ \text{Hz}$ circuit the current passes through zero twice every cycle, every $10\ \text{ms}$. When a high-voltage circuit breaker opens under load or fault, the arc drawn between the separating contacts goes out at the next current zero. A DC current never crosses zero by itself, so it sustains a continuous plasma arc unless arc-chutes or semiconductor breakers force the current down, and high-voltage DC is far harder to switch.

Third, AC voltage can be transformed efficiently, and raising the voltage cuts transmission losses as $1/V^2$. Transmitting power $P = VI$ at unity power factor along a line or cable of total series resistance $R_{\text{line}}$ needs the line current

$$I = \frac{P}{V},$$

so the ohmic heating in the conductors is

$$\begin{aligned}
P_{\text{loss}} &= I^2 R_{\text{line}} \\[4pt]
&= \left(\frac{P}{V}\right)^2 R_{\text{line}} \\[4pt]
&= \frac{P^2 R_{\text{line}}}{V^2}.
\end{aligned}$$

For fixed $P$ and $R_{\text{line}}$ the loss is inversely proportional to the square of the transmission voltage. Stepping the voltage up by a factor $k$ reduces the current by $k$, which allows much thinner, lighter and cheaper aluminium or copper conductors, and cuts the $I^2 R_{\text{line}}$ loss by $k^2$.

In the UK, power is generated at $11\text{--}25\ \text{kV}$ and stepped up by generator transformers to $400\ \text{kV}$ (and $275\ \text{kV}$) for bulk transmission across the National Grid pylon network. Regional and local substations then step it down ($132\ \text{kV} \to 33\ \text{kV} \to 11\ \text{kV}$) before final distribution at $400\ \text{V}$ three-phase to industrial premises and $230\ \text{V}$ single-phase to homes.

![[ee_c3_transformer_transmission.png|900]]

## 2. Transformer construction and ideal turns-ratio relations

### Structure of a single-phase transformer

A single-phase **transformer** is a static electromagnetic device with no moving parts (Sharkh §3.5, Fig. 3.9). Its closed ferromagnetic core is built from thin insulated **silicon-steel laminations**, which suppress eddy-current losses while giving a high-permeability, low-reluctance path $\mathcal{R}_c = l/(\mu_0 \mu_r A)$ ([[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]). In a core-type transformer the two vertical sides carrying the coils are the **limbs** (or legs), and the horizontal top and bottom sections closing the magnetic loop are the **yokes**. A **primary winding** of $N_1$ turns connects to the AC source $v_1(t)$, and a **secondary winding** of $N_2$ turns connects to the load, with terminal voltage $v_2(t)$.

An alternating voltage $v_1(t)$ on the primary drives an alternating magnetising current, which sets up a time-varying flux $\Phi(t)$ round the core. The steel's relative permeability is $\mu_r \sim 10^3\text{--}10^4$, so virtually all of $\Phi(t)$ stays in the limbs and yokes and links every turn of both windings. The primary and secondary circuits are **electrically isolated**, with no conducting path between them; energy passes from one to the other entirely through the time-varying field in the core.

### Ideal voltage, current and power relations

An **ideal transformer** rests on three assumptions:

1. Zero winding resistance ($R_1 = R_2 = 0$), so each terminal voltage equals the winding's induced EMF.
2. Zero leakage flux (perfect coupling), so the same core flux $\Phi(t)$ links all $N_1$ primary turns and all $N_2$ secondary turns.
3. Zero core loss and infinite core permeability: no hysteresis or eddy-current heating in the laminations, and negligible magnetising current, so the efficiency is $\eta = 100\%$.

Faraday's law applied to the two windings linking the common flux gives

$$v_1(t) = -N_1\frac{\mathrm{d}\Phi}{\mathrm{d}t}, \qquad v_2(t) = -N_2\frac{\mathrm{d}\Phi}{\mathrm{d}t}.$$

Dividing the second equation by the first eliminates $\mathrm{d}\Phi/\mathrm{d}t$:

$$\begin{aligned}
\frac{v_2(t)}{v_1(t)} &= \frac{-N_2\,\dfrac{\mathrm{d}\Phi}{\mathrm{d}t}}{-N_1\,\dfrac{\mathrm{d}\Phi}{\mathrm{d}t}} \\[6pt]
\frac{v_2(t)}{v_1(t)} &= \frac{N_2}{N_1}.
\end{aligned}$$

In RMS values $V_1$ and $V_2$ this is the **voltage turns-ratio equation**:

$$\frac{V_2}{V_1} = \frac{N_2}{N_1}.$$

With $N_2 > N_1$ the secondary voltage is higher and the transformer is a **step-up transformer**; with $N_2 < N_1$ it is a **step-down transformer**. With $N_2 = N_1$ it is a $1:1$ **isolation transformer**, used for galvanic safety isolation or to block DC offsets between circuits.

The instantaneous power entering the primary and leaving the secondary are

$$p_1(t) = v_1(t)\,i_1(t), \qquad p_2(t) = v_2(t)\,i_2(t),$$

and the **efficiency** of a practical transformer is the ratio of output to input power,

$$\eta = \frac{P_2}{P_1} \times 100\%.$$

A transformer has no moving parts, and so no friction or windage loss. Its only losses are copper heating in the windings ($I_1^2 R_1 + I_2^2 R_2$) and hysteresis plus eddy-current loss in the laminations, and large grid transformers reach $\eta \approx 99\%$ at full load.

In an **ideal lossless transformer** ($\eta = 100\%$) input and output power are equal at every instant:

$$\begin{aligned}
p_1(t) &= p_2(t) \\[4pt]
v_1(t)\,i_1(t) &= v_2(t)\,i_2(t).
\end{aligned}$$

Rearranging for the current ratio and substituting $v_1(t)/v_2(t) = N_1/N_2$ gives, in instantaneous and RMS form,

$$\frac{i_2(t)}{i_1(t)} = \frac{v_1(t)}{v_2(t)} = \frac{N_1}{N_2} \iff \frac{I_2}{I_1} = \frac{V_1}{V_2} = \frac{N_1}{N_2}.$$

Equivalently $N_1 i_1(t) = N_2 i_2(t)$: the secondary load MMF $N_2 i_2$ is balanced exactly by the primary MMF $N_1 i_1$, so drawing load current leaves the net core flux unchanged. Stepping voltage up by $N_2/N_1$ steps current down by $N_1/N_2$.

### Referred impedance

An impedance $Z_L$ (or a resistive load $R_L$) connected across the secondary of an ideal transformer with turns ratio $N_1 : N_2$ has, on the secondary side,

$$Z_L = \frac{V_2}{I_2}.$$

The source on the primary sees the transformer and load draw current $I_1$ at voltage $V_1$, an effective **referred impedance** $Z_L' = V_1/I_1$. Substituting $V_1 = (N_1/N_2) V_2$ and $I_1 = (N_2/N_1) I_2$,

$$\begin{aligned}
Z_L' &= \frac{V_1}{I_1} \\[4pt]
&= \frac{\left(\dfrac{N_1}{N_2}\right) V_2}{\left(\dfrac{N_2}{N_1}\right) I_2} \\[6pt]
&= \left(\frac{N_1}{N_2}\right)^2 \frac{V_2}{I_2} \\[6pt]
&= \left(\frac{N_1}{N_2}\right)^2 Z_L.
\end{aligned}$$

Moving an impedance from the secondary side to the primary side multiplies it by the square of the turns ratio, $(N_1/N_2)^2$.

## 3. The transformer EMF equation

The **transformer EMF equation** sets how many turns $N_1$ and what core area $A$ a transformer needs to support a given RMS supply voltage $V_1$ at frequency $f$ without saturating.

Let the core flux vary sinusoidally at frequency $f$ (angular frequency $\omega = 2\pi f$) with peak $\Phi_m$:

$$\Phi(t) = \Phi_m \sin(2\pi f t).$$

By Faraday's law the EMF induced in a winding of $N$ turns linking this flux is

$$\begin{aligned}
e(t) &= -N\frac{\mathrm{d}\Phi}{\mathrm{d}t} \\[4pt]
&= -N\frac{\mathrm{d}}{\mathrm{d}t}\bigl(\Phi_m \sin(2\pi f t)\bigr) \\[4pt]
&= -2\pi f N \Phi_m \cos(2\pi f t).
\end{aligned}$$

Its peak magnitude is the amplitude multiplying $\cos(2\pi f t)$:

$$E_p = 2\pi f N \Phi_m.$$

For a sinusoid the RMS value is the peak divided by $\sqrt{2}$. Dividing $E_p$ by $\sqrt{2}$, with $2\pi/\sqrt{2} = \sqrt{2}\,\pi = 4.44288\dots \approx 4.44$, gives the **transformer EMF equation**:

$$\begin{aligned}
E_{\text{rms}} &= \frac{E_p}{\sqrt{2}} \\[4pt]
&= \frac{2\pi}{\sqrt{2}}\,f N \Phi_m \\[4pt]
&= 4.44\,f N \Phi_m.
\end{aligned}$$

Applied to the primary ($N = N_1$, with winding resistance neglected so $V_1 = E_{1,\text{rms}}$) and to the secondary ($N = N_2$, $V_2 = E_{2,\text{rms}}$),

$$V_1 = 4.44\,f N_1 \Phi_m, \qquad V_2 = 4.44\,f N_2 \Phi_m.$$

For a core of net cross-sectional area $A$, $\Phi_m = B_m A$, where $B_m$ is the **peak flux density** in the steel, so

$$V_1 = 4.44\,f N_1 B_m A \iff B_m = \frac{V_1}{4.44\,f N_1 A}.$$

For a given transformer ($N_1$ and $A$ fixed), the peak flux $\Phi_m = V_1/(4.44\,f N_1)$ and the peak flux density $B_m$ are set entirely by the primary RMS voltage and the supply frequency. They do not rise when the secondary draws load current. Driving silicon steel into saturation makes $\mu_r$ collapse, the magnetising current spike and the core overheat, so designers keep $B_m \lesssim 1.5\ \text{T}$.

> [!warning] DC and under-frequency supplies
> As $f \to 0$, $\Phi_m = V_1/(4.44\,f N_1) \to \infty$. On DC, $\mathrm{d}\Phi/\mathrm{d}t \to 0$, so no back-EMF is induced, the core saturates at once, and the primary current is limited only by the small DC winding resistance $R_1$, which burns out the winding. A milder version catches transformers moved between grids: one designed for $60\ \text{Hz}$ with $B_m = 1.4\ \text{T}$, connected to a $50\ \text{Hz}$ supply at the same voltage, has $B_m$ raised by $60/50 = 1.20$ to $1.68\ \text{T}$, which saturates the core.

The same relation explains why aircraft transformers are small. For a given $V_1$, $N_1$ and allowable $B_m$, the core area scales inversely with frequency, $A = V_1/(4.44\,f N_1 B_m) \propto 1/f$. Raising the bus frequency from $50\ \text{Hz}$ (land grid) to $400\ \text{Hz}$ (aircraft) shrinks the required core cross-section and mass by a factor of $8$.

Transport aircraft generate three-phase AC at $115\ \text{V}$, $400\ \text{Hz}$, and Transformer-Rectifier Units (TRUs) step it down through compact $400\ \text{Hz}$ transformers followed by diode rectifiers to supply the $28\ \text{V}$ DC avionics bus ([[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]). Spacecraft solar arrays and batteries run DC buses ($28\ \text{V}$ or $100\ \text{V}$); to step a bus voltage up or down with galvanic isolation, a switched-mode DC–DC converter chops the DC into high-frequency AC ($50\text{--}500\ \text{kHz}$), passes it through a miniature ferrite-core transformer, where the $V = 4.44\,f N B_m A$ scaling makes the core tiny, and rectifies the secondary back to DC ([[SESA2024 08 - Electrical Power Subsystem]]). The LVDT position sensor used on aircraft control surfaces is a single-primary, dual-secondary transformer whose movable core changes the differential flux linkage of the two secondaries ([[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]], [[Linear Variable Differential Transformer]]). And the small magnetising current a real primary draws to set up $\Phi_m$ lags the supply voltage by $90^\circ$, adding lagging reactive power $Q$ to the grid ([[FEEG1004 D4 - AC Power and Power Factor]]).

## Worked examples

### Step-up transformer flux density and voltage

A single-phase transformer has $N_1 = 400$ primary turns and $N_2 = 1000$ secondary turns, and the net cross-sectional area of its laminated core is $A = 60\ \text{cm}^2$. The primary is connected to a $50\ \text{Hz}$ supply of RMS voltage $V_1 = 500\ \text{V}$. The task is the secondary voltage $V_2$, the peak flux $\Phi_m$ and peak flux density $B_m$ (and whether the core saturates), the time-domain $v_1(t)$ and $\Phi(t)$, and the effect on $B_m$ of applying the same $500\ \text{V}$ at $25\ \text{Hz}$.

From the turns ratio,

$$\begin{aligned}
V_2 &= V_1\,\frac{N_2}{N_1} \\[4pt]
&= 500\ \text{V} \times \frac{1000}{400} \\[4pt]
&= 1250\ \text{V}\ (\text{RMS}).
\end{aligned}$$

The EMF equation $V_1 = 4.44\,f N_1 \Phi_m$ gives the peak flux:

$$\begin{aligned}
\Phi_m &= \frac{V_1}{4.44\,f N_1} \\[4pt]
&= \frac{500\ \text{V}}{4.44 \times 50\ \text{Hz} \times 400} \\[4pt]
&= \frac{500}{88\,800}\ \text{Wb} \\[4pt]
&= 5.631 \times 10^{-3}\ \text{Wb} = 5.63\ \text{mWb}.
\end{aligned}$$

The unrounded constant $2\pi/\sqrt{2} = 4.4429$ gives $\Phi_m = 5.627\ \text{mWb}$, which rounds to the same $5.63\ \text{mWb}$.

In SI units the core area is $A = 60\ \text{cm}^2 = 60 \times 10^{-4}\ \text{m}^2 = 6.0 \times 10^{-3}\ \text{m}^2$, so the peak flux density is

$$\begin{aligned}
B_m &= \frac{\Phi_m}{A} \\[4pt]
&= \frac{5.631 \times 10^{-3}\ \text{Wb}}{6.0 \times 10^{-3}\ \text{m}^2} \\[4pt]
&= 0.938\ \text{T},
\end{aligned}$$

comfortably below the $\sim 1.5\ \text{T}$ saturation level of silicon steel, so the core operates in its linear region.

The primary voltage is $v_1(t) = 500\sqrt{2}\sin(2\pi \times 50\,t)\ \text{V} = 707.1\sin(100\pi t)\ \text{V}$. Integrating $v_1(t) = N_1\,\mathrm{d}\Phi/\mathrm{d}t$ (passive sign convention for the primary coil) gives

$$\Phi(t) = \frac{1}{N_1}\int v_1(t)\,\mathrm{d}t = -\frac{500\sqrt{2}}{400 \times 100\pi}\cos(100\pi t)\ \text{Wb} = -5.627\cos(100\pi t)\ \text{mWb},$$

so the core flux lags the applied voltage by $90^\circ$ ($\pi/2\ \text{rad}$). Halving the frequency to $25\ \text{Hz}$ at the same $500\ \text{V}$ would double $B_m$ to $2 \times 0.938\ \text{T} = 1.876\ \text{T} > 1.5\ \text{T}$, driving the core deep into saturation.

> [!check] Secondary voltage from the EMF equation
> With $N_2 = 1000$ and $\Phi_m = 5.6306 \times 10^{-3}\ \text{Wb}$, $V_2 = 4.44 \times (50\ \text{Hz}) \times 1000 \times (5.6306 \times 10^{-3}\ \text{Wb}) = 1250.0\ \text{V}$, matching $V_1 N_2/N_1 = 1250\ \text{V}$.

### Core-type transformer feeding a 10 kW load

This is [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q5: Single-phase transformer, 70:350 turns, 100 cm² core, 230 V at 50 Hz|Tutorial Sheet 5 Q5]]. A single-phase core-type transformer has $N_1 = 70$ and $N_2 = 350$ turns and a square core of net area $A = 100\ \text{cm}^2$. The primary is on a $50\ \text{Hz}$, $230\ \text{V}$ RMS supply; losses and leakage are neglected. The task is the peak core flux density $B_m$, the secondary voltage $V_2$, and, for a $10\ \text{kW}$ resistive load on the secondary, the currents $I_2$ and $I_1$, the load resistance $R_L$ and its referred value $R_L'$.

The peak core flux is

$$\begin{aligned}
\Phi_m &= \frac{V_1}{4.44\,f N_1} \\[4pt]
&= \frac{230\ \text{V}}{4.44 \times 50\ \text{Hz} \times 70} \\[4pt]
&= \frac{230}{15\,540}\ \text{Wb} \\[4pt]
&= 0.01480\ \text{Wb} = 14.8\ \text{mWb}.
\end{aligned}$$

With $A = 100\ \text{cm}^2 = 100 \times 10^{-4}\ \text{m}^2 = 0.010\ \text{m}^2$, the peak flux density is

$$\begin{aligned}
B_m &= \frac{\Phi_m}{A} \\[4pt]
&= \frac{0.01480\ \text{Wb}}{0.010\ \text{m}^2} \\[4pt]
&= 1.48\ \text{T}.
\end{aligned}$$

This sits right at the practical ceiling ($\approx 1.5\ \text{T}$) for silicon-steel laminations, which gets the most power out of a given core size without saturating it.

The turns ratio is $N_2/N_1 = 350/70 = 5$, a $1:5$ step-up, so

$$\begin{aligned}
V_2 &= V_1\,\frac{N_2}{N_1} \\[4pt]
&= 230\ \text{V} \times \frac{350}{70} \\[4pt]
&= 1150\ \text{V}\ (\text{RMS}).
\end{aligned}$$

A $10\ \text{kW}$ purely resistive load ($\cos\phi = 1$) across $1150\ \text{V}$ draws

$$\begin{aligned}
I_2 &= \frac{P_2}{V_2} \\[4pt]
&= \frac{10\,000\ \text{W}}{1150\ \text{V}} \\[4pt]
&= 8.696\ \text{A} \approx 8.70\ \text{A}.
\end{aligned}$$

With losses neglected, $P_1 = P_2 = 10\,000\ \text{W}$, and the primary current is

$$\begin{aligned}
I_1 &= \frac{P_1}{V_1} \\[4pt]
&= \frac{10\,000\ \text{W}}{230\ \text{V}} \\[4pt]
&= 43.48\ \text{A} \approx 43.5\ \text{A}.
\end{aligned}$$

The load resistance and its value referred to the primary are

$$\begin{aligned}
R_L &= \frac{V_2}{I_2} = \frac{V_2^2}{P_2} = \frac{(1150\ \text{V})^2}{10\,000\ \text{W}} = 132.25\ \Omega, \\[6pt]
R_L' &= \left(\frac{N_1}{N_2}\right)^2 R_L = \left(\frac{70}{350}\right)^2 (132.25\ \Omega) = \frac{132.25\ \Omega}{25} = 5.29\ \Omega.
\end{aligned}$$

> [!check] Ampere-turn balance and referred resistance
> $I_1/I_2 = 43.478\ \text{A}/8.6957\ \text{A} = 5.000 = N_2/N_1$, so the load ampere-turns balance: $N_1 I_1 = 70 \times 43.478\ \text{A} = 3043.5\ \text{A-turns} = 350 \times 8.6957\ \text{A} = N_2 I_2$. And $R_L' = 5.29\ \Omega$ connected straight across $230\ \text{V}$ draws $I_1 = 230/5.29 = 43.48\ \text{A}$ and absorbs $V_1^2/R_L' = 230^2/5.29 = 10\,000\ \text{W}$.

### Line losses at 11 kV to 400 kV

A power station sends $P = 100\ \text{MW}$ at unity power factor over a long overhead line of total series resistance $R_{\text{line}} = 1.0\ \Omega$. Compare the line current $I = P/V$, the loss $P_{\text{loss}} = I^2 R_{\text{line}}$, the fraction of power lost and the resistive voltage drop $\Delta V = I R_{\text{line}}$ at four UK voltage levels: the $11\ \text{kV}$ generator terminal voltage (no step-up transformer), $33\ \text{kV}$ sub-transmission, $132\ \text{kV}$ regional grid and the $400\ \text{kV}$ supergrid. Throughout, $P = 1.0 \times 10^8\ \text{W}$ and $R_{\text{line}} = 1.0\ \Omega$.

At $V = 11\ \text{kV} = 1.1 \times 10^4\ \text{V}$,

$$\begin{aligned}
I_{11} &= \frac{1.0 \times 10^8\ \text{W}}{1.1 \times 10^4\ \text{V}} = 9090.9\ \text{A} \\[4pt]
P_{\text{loss},11} &= (9090.9\ \text{A})^2 (1.0\ \Omega) = 8.264 \times 10^7\ \text{W} = 82.64\ \text{MW}\quad (82.64\%\ \text{of } 100\ \text{MW}) \\[4pt]
\Delta V_{11} &= (9090.9\ \text{A})(1.0\ \Omega) = 9090.9\ \text{V} = 9.09\ \text{kV}\quad (82.64\%\ \text{of } 11\ \text{kV}).
\end{aligned}$$

Sending $100\ \text{MW}$ directly at $11\ \text{kV}$ is unworkable: over four-fifths of the power and voltage would be lost as heat in the line, and $9.1\ \text{kA}$ would need massive copper busbars.

At $V = 33\ \text{kV} = 3.3 \times 10^4\ \text{V}$, three times the voltage gives nine times less loss:

$$\begin{aligned}
I_{33} &= \frac{1.0 \times 10^8\ \text{W}}{3.3 \times 10^4\ \text{V}} = 3030.3\ \text{A} \\[4pt]
P_{\text{loss},33} &= (3030.3\ \text{A})^2 (1.0\ \Omega) = 9.183 \times 10^6\ \text{W} = 9.18\ \text{MW}\quad (9.18\%\ \text{loss}).
\end{aligned}$$

At $V = 132\ \text{kV} = 1.32 \times 10^5\ \text{V}$, twelve times the voltage gives $144$ times less loss:

$$\begin{aligned}
I_{132} &= \frac{1.0 \times 10^8\ \text{W}}{1.32 \times 10^5\ \text{V}} = 757.6\ \text{A} \\[4pt]
P_{\text{loss},132} &= (757.6\ \text{A})^2 (1.0\ \Omega) = 5.739 \times 10^5\ \text{W} = 573.9\ \text{kW}\quad (0.574\%\ \text{loss}).
\end{aligned}$$

At $V = 400\ \text{kV} = 4.0 \times 10^5\ \text{V}$, the voltage is $400/11 = 36.36$ times higher and the loss $1322.3$ times lower:

$$\begin{aligned}
I_{400} &= \frac{1.0 \times 10^8\ \text{W}}{4.0 \times 10^5\ \text{V}} = 250.0\ \text{A} \\[4pt]
P_{\text{loss},400} &= (250.0\ \text{A})^2 (1.0\ \Omega) = 6.250 \times 10^4\ \text{W} = 62.5\ \text{kW}\quad (0.0625\%\ \text{loss}) \\[4pt]
\Delta V_{400} &= (250.0\ \text{A})(1.0\ \Omega) = 250.0\ \text{V}\quad (0.0625\%\ \text{of } 400\ \text{kV}).
\end{aligned}$$

| Transmission voltage $V$ | Line current $I = P/V$ | Line loss $I^2 R_{\text{line}}$ | Fraction of $100\ \text{MW}$ lost | Line efficiency $\eta_{\text{line}}$ |
|---|---|---|---|---|
| $11\ \text{kV}$ | $9090.9\ \text{A}$ | $82.64\ \text{MW}$ | $82.64\%$ | $17.36\%$ |
| $33\ \text{kV}$ | $3030.3\ \text{A}$ | $9.18\ \text{MW}$ | $9.18\%$ | $90.82\%$ |
| $132\ \text{kV}$ | $757.6\ \text{A}$ | $573.9\ \text{kW}$ | $0.574\%$ | $99.43\%$ |
| $400\ \text{kV}$ | $250.0\ \text{A}$ | $62.5\ \text{kW}$ | $0.0625\%$ | $99.94\%$ |

> [!check] The $1/V^2$ scaling
> $P_{\text{loss},11}/P_{\text{loss},400} = 82\,644.6\ \text{kW}/62.5\ \text{kW} = 1322.31 = (400\ \text{kV}/11\ \text{kV})^2$. Stepping up from $11\ \text{kV}$ to $400\ \text{kV}$ cuts the loss from $82.6\ \text{MW}$ to $62.5\ \text{kW}$, saving $82.58\ \text{MW}$ of heat on a single $1.0\ \Omega$ line.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- Next: [[FEEG1004 C4 - DC Generators and the Commutator]]
- Concepts: [[Ideal Transformer]] · [[Transformer EMF Equation]]
- Worked problems: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q5)

## Sources

- `02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf` (§3.4 AC vs DC and §3.5 The Transformer, pp. 16–19).
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 04 - Transformers and AC Power - Lecture Slides.pdf` (slides 1–12).
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf` (Q5).
- E. Hughes, *Electrical and Electronic Technology*, Chs. 32 (Transformers) and 37 (Electrical Energy Systems).

## Self-study tasks

### Core

- [ ] A transformer with $N_1 = 400$, $N_2 = 1000$ and $A = 60\ \text{cm}^2$ is on a $50\ \text{Hz}$, $500\ \text{V}$ RMS primary supply: find $V_2$ and $B_m$ (`S2-W18-21 Electric Machines 04` slide 7; Sharkh pp. 18–19). → [[#Step-up transformer flux density and voltage]]
- [ ] For the $70:350$-turn transformer with a $100\ \text{cm}^2$ core on $50\ \text{Hz}$, $230\ \text{V}$, feeding a $10\ \text{kW}$ resistive load, find $B_m$, $V_2$ and $I_1$ (Tutorial Sheet 5 Q5). → [[#Core-type transformer feeding a 10 kW load]]; [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q5: Single-phase transformer, 70:350 turns, 100 cm² core, 230 V at 50 Hz|Tutorial 5 Q5]]

### Further practice

- [ ] Redesign the $230\ \text{V}$, $70:350$-turn transformer for a $400\ \text{Hz}$ aircraft bus, keeping $V_1 = 230\ \text{V}$, $N_1 = 70$ and $B_m = 1.48\ \text{T}$, and show with $V_1 = 4.44\,f N_1 B_m A$ that the core area drops from $100\ \text{cm}^2$ to $12.5\ \text{cm}^2$ (suggested, not lecturer-set). → [[#3. The transformer EMF equation]]; [[#Core-type transformer feeding a 10 kW load]]

## Transcript and slide slips

### Equation (3.10) printed as p1 = p1, and (3.9) skipped

> [!warning] Printed notes typo (Sharkh p. 18)
> Where: [[#Ideal voltage, current and power relations]]
> On p. 18 the equation number (3.9) is skipped between (3.8) and (3.10), and (3.10) is printed as "$p_1 = p_1 \implies v_1 i_1 = v_2 i_2$". The first equality should be $p_1 = p_2$ (input power equals output power in an ideal lossless transformer), as printed correctly on `S2-W18-21 Electric Machines 04` slide 6.

### Missing square root on slide 7 of Electric Machines 04

> [!warning] Slide rendering slip (`S2-W18-21 Electric Machines 04`, slide 7)
> Where: [[#Step-up transformer flux density and voltage]]
> The primary voltage is printed as "$v_1 = 500\ 2\sin(2\pi \times 50 \times t)$", with the square-root sign missing over the $2$. $V_1 = 500\ \text{V}$ is an RMS value, so the peak is $500\sqrt{2}\ \text{V} \approx 707.1\ \text{V}$ and $v_1(t) = 500\sqrt{2}\sin(2\pi \times 50\,t)$.
