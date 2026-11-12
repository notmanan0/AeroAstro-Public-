---
title: "FEEG1004 C4 - DC Generators and the Commutator"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 4
tags: [feeg1004, machines, dc-generator, commutator, emf-constant, tachogenerator]
aliases: ["Electric Machines 05", "DC generator", "Commutator", "E = K_E omega"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-02-14 (ll. 1–188, 358–417)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites:
  - "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"
  - "[[FEEG1004 C3 - Transformers and AC Power Transmission]]"
next_topics: ["[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]"]
key_concepts: ["[[Commutator]]", "[[Back EMF and Torque Constants]]", "[[Motional EMF in Electric Machines]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]]"]
sources:
  - "02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"
  - "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 05 - DC Generators - Lecture Slides.pdf"
  - "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 06 - DC Motors Torque - Lecture Slides.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-02-14.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf"
---

# FEEG1004 C4 - DC Generators and the Commutator

> [!abstract] Summary
> A brushed DC generator is a rotating-coil AC generator whose two slip rings are replaced by a split-ring commutator, which swaps each coil's connection to the brushes every half-turn and so mechanically rectifies the induced voltage. A single coil gives a pulsating $|E_m\sin(\omega t)|$, while many coils on a multi-segment commutator give a nearly constant EMF $E = K_E\omega$ with $K_E = \dfrac{Z}{a}\,B L \dfrac{D}{2} = \dfrac{Z N_p \Phi}{2\pi a}\ \text{V}\,\text{s}\,\text{rad}^{-1}$, for $Z$ conductors in $a$ parallel paths and flux per pole $\Phi = \dfrac{\pi B L D}{N_p}$. Load current produces a counter-torque $T_{\text{em}} = K_T i$ on the prime mover, and the armature behaves as $E$ in series with $R_a$ and $L_a$, so $V = E - i R_a - L_a\dfrac{\mathrm{d}i}{\mathrm{d}t}$, which reduces to $V = K_E \omega - i R_a$ in steady state.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks how a commutator turns the coil voltage into DC, for the EMF constant of a DC machine from its geometry or from a test, or for the terminal voltage of a loaded DC generator.
> - **Assumptions:** steady speed with $\omega$ in $\text{rad}\,\text{s}^{-1}$; an average radial air-gap flux density $B$ under the poles; brushes on the neutral axis; $\mathrm{d}i/\mathrm{d}t = 0$ for the steady-state circuit.
> - **Method:** 1. Convert speed with $\omega = 2\pi\,\text{rpm}/60$. 2. Find $K_E$ from $\dfrac{Z}{a}BL\dfrac{D}{2}$, from $\dfrac{Z N_p \Phi}{2\pi a}$, or from an open-circuit test $K_E = V_{\text{oc}}/\omega$. 3. Compute $E = K_E\omega$. 4. Apply $V = E - iR_a$ for the loaded generator. 5. Check that $Ei = T_{\text{em}}\omega = P_{\text{out}} + P_{\text{cu}}$.
> - **Common mistakes:** putting speed in rpm into $E = K_E\omega$; using the motor equation $V = E + iR_a$ for a generator, which gives a terminal voltage above the EMF.
> - **Practise:** [[#Open-circuit test for the EMF constant]] · [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q1: Back-EMF constant from an open-circuit test|Tutorial 6 Q1]]

A brushed DC generator and a brushed DC motor are the same machine. If mechanical shaft power spins the rotor and electrical power is delivered to a load, it operates as a DC generator; if a DC supply drives current into the terminals to produce shaft torque, it operates as a DC motor ([[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]).

The coils on the rotor always have an alternating EMF induced in them, because each coil side passes under a North pole and then a South pole on every revolution. What makes the output DC is the way the coils are connected to the outside world. The commutator reconnects each coil every half-turn so that the brush polarity never changes, and spreading many coils around the rotor fills in the dips between peaks.

The rectified EMF is proportional to speed through a single constant $K_E$, set by the geometry, the winding and the magnetic field. The same constant reappears as the torque constant when the machine runs as a motor, so the commutator's rectification and the armature circuit equations underpin both DC generation and DC motor analysis.

## 1. Construction and the commutator

### Parts of a brushed DC machine

A radial-gap permanent-magnet DC machine has four main sub-assemblies. The **stator yoke** is an outer cylindrical steel shell (can) that gives mechanical protection and a low-reluctance magnetic return path. Inside it, two curved arc **permanent magnets** are held on opposite sides by a spring clip and set up a stationary radial field from the North pole to the South pole across the rotor bore. Large industrial machines use DC-excited **field windings** wound around salient pole cores instead of magnets.

The **rotor core** is a central steel shaft carrying a cylindrical stack of insulated silicon-steel laminations with axial slots punched around the outer perimeter. As in an AC stator, laminating the iron guides the flux across the air gap with low reluctance while blocking the axial eddy currents that would otherwise be induced as the iron spins through the stationary stator field.

Insulated copper coils wound into these slots form the **armature**, the name given in a DC machine to the rotating coil assembly in which the main EMF is induced.

Mounted coaxially on the shaft next to the laminations is the **commutator**, a cylinder of wedge-shaped copper bars (**commutator segments**) insulated from one another and from the shaft by mica or moulded plastic. The terminals of each armature coil are soldered to a pair of segments. Two stationary spring-loaded **carbon brushes**, held in an insulated nylon end-cap, press radially inwards on opposite sides of the spinning commutator and connect the rotating armature circuit to the two external DC terminals.

### From slip rings to a split-ring commutator

In a rotating-coil AC generator ([[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]), a single $N$-turn coil spinning at constant angular velocity $\omega$ in a stationary two-pole field links a sinusoidally varying flux $\Phi(t) = \Phi_m \sin(\omega t)$. By Faraday's law, the EMF induced in the rotating coil alternates:

$$e_{\text{coil}}(t) = -\frac{\mathrm{d}(N\Phi)}{\mathrm{d}t} = -N \omega \Phi_m \cos(\omega t)$$

If the coil ends are connected to two continuous coaxial **slip rings**, each brush stays connected to the same coil end throughout the $360^\circ$ rotation, so the terminal voltage alternates between $+E_m$ and $-E_m$ every half-turn.

A two-segment commutator replaces the two slip rings with a single ring split into two insulated half-cylinders. The brushes are positioned so that the insulating gaps between the half-rings pass under the brushes as the coil passes through the zero-EMF neutral plane, at $\theta = \omega t = \pi/2, 3\pi/2, \dots$

During the first half-revolution ($-\pi/2 < \omega t < \pi/2$), coil side $1$ sweeps past the North pole, with its EMF directed out of the page say, while it touches the positive brush. Coil side $2$ sweeps past the South pole, with its EMF into the page, while it touches the negative brush. At $\omega t = \pi/2$ the coil sides cross the neutral zone between the poles, where $B = 0$ and $e_{\text{coil}} = 0$. At that instant the two segments pass the brushes and swap connections: coil side $2$ enters the North-pole zone and meets the positive brush, while coil side $1$ enters the South-pole zone and meets the negative brush.

The positive brush is therefore always connected to whichever coil side is under the North pole, and the negative brush to whichever is under the South pole, so the polarity at the brushes never reverses. The commutator acts as a synchronous mechanical full-wave rectifier, giving a unidirectional but pulsating terminal voltage:

$$e_{\text{term}}(t) = \bigl|E_m \cos(\omega t)\bigr| \quad (\text{or } \bigl|E_m \sin(\omega t)\bigr|)$$

Brushes, armature coils and laminations can all exist in a rotating-coil AC machine. The commutator is the component that makes a machine a DC machine rather than an AC one.

### Smoothing the output with several coils

A single coil on a two-segment split ring gives a $100\%$ pulsating voltage that falls to zero twice per revolution. Practical armatures obtain a steady, low-ripple voltage by winding several coils at equal angles around the rotor slots and connecting them to a multi-segment commutator.

![[ee_c4_commutator_emf.png|820]]

Suppose $n$ identical coils (or coil groups) are displaced by $\pi/n$ radians around the rotor and connected to $2n$ commutator segments, so that the brushes always contact the coil currently passing through the middle of the pole faces, near its peak EMF $E_{\text{peak}}$. Each coil stays connected over an angular window of width $\Delta\theta = \pi/n$ centred on its peak, $\theta \in [-\pi/(2n), +\pi/(2n)]$. At the hand-over instant $\theta = \pm \dfrac{\pi}{2n}$, where the brushes pass to the next coil, the instantaneous EMF falls only to

$$E_{\text{min}} = E_{\text{peak}}\cos\!\left(\frac{\pi}{2n}\right)$$

The fractional peak-to-valley ripple is therefore

$$\text{Ripple} = \frac{E_{\text{peak}} - E_{\text{min}}}{E_{\text{peak}}} = 1 - \cos\!\left(\frac{\pi}{2n}\right)$$

For $n = 2$ coils ($90^\circ$ apart) the ripple falls from $100\%$ to $1 - \cos 45^\circ = 29.3\%$, and for $n = 3$ coils ($60^\circ$ apart) it falls to $1 - \cos 30^\circ = 13.4\%$. A practical industrial armature has $12$ to $36+$ commutator segments, with the coils also connected in series-parallel rings by **lap** or **wave** windings so that all coils in a path add continuously. The ripple is then below $1\%$, and the EMF is effectively constant and proportional to shaft speed:

$$E = K_E \omega$$

Because $E$ is proportional to $\omega$, a small permanent-magnet DC generator coupled to a rotating shaft makes a linear analogue speed sensor, the **tachogenerator**.

## 2. Armature EMF equation

The EMF constant $K_E$ can be written in terms of the machine's dimensions, winding layout and field. Consider a cylindrical rotor of diameter $D$ (radius $R = D/2$) and active axial length $L$, spinning at mechanical angular velocity $\omega\ \text{rad}\,\text{s}^{-1}$ inside an $N_p$-pole stator whose radial air-gap flux density has average magnitude $B$ under the poles.

Let $Z$ be the total number of **active conductors**, the axial conductors in the rotor slots. Each turn of a coil has two axial sides cutting flux, one under a North pole and one returning under a South pole, so an armature with $N_{\text{tot}}$ turns has $Z = 2 N_{\text{tot}}$ active conductors. Depending on how the coil ends are connected to the commutator segments, the $Z$ conductors are divided between the brushes into $a$ identical **parallel paths**: a wave winding has $a = 2$, and a lap winding has $a = N_p$. Each path then contains $\dfrac{Z}{a}$ conductors in series.

Parallel paths keep the winding cool. Each conductor has finite copper resistance and a thin polymer enamel insulation inside tightly packed slots. Splitting the winding into $a$ paths divides the current per conductor to $i_c = i/a$ for a total armature current $i$, cutting the ohmic heating per conductor ($i_c^2 R_c \propto 1/a^2$) so that the slot temperature does not burn through the insulation. The cost is that fewer conductors ($Z/a$) sit in series per path, which reduces the terminal voltage $E$ by the same factor $a$.

Each active conductor of length $L$ sits at radius $R = D/2$ and cuts the radial field at peripheral velocity

$$u = \omega R = \omega\,\frac{D}{2}$$

The motional EMF $e_c = B L u$ from [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] then gives the EMF in one conductor:

$$e_c = B L u = B L \omega\,\frac{D}{2}$$

The $\dfrac{Z}{a}$ conductors in one path are in series and commutated so that their EMFs add in the same direction. The total EMF across the brushes is their sum:

$$\begin{aligned}
E &= \sum_{k=1}^{Z/a} e_c \\[4pt]
&= \frac{Z}{a}\,e_c \\[4pt]
&= \frac{Z}{a}\,B L \frac{D}{2}\,\omega \\[4pt]
&= K_E\,\omega
\end{aligned}$$

This defines the **EMF constant** in terms of the average air-gap flux density and the rotor dimensions:

$$K_E = \frac{Z}{a}\,B L \frac{D}{2} \quad \bigl[\text{V}\,\text{s}\,\text{rad}^{-1}\bigr]$$

An alternative form uses the flux per pole. The cylindrical surface area of the rotor is $A_{\text{rotor}} = \pi D L$, and dividing it equally among the $N_p$ poles gives an air-gap area per pole of $A_{\text{pole}} = \dfrac{\pi D L}{N_p}$. With average radial flux density $B$, the **flux per pole** $\Phi$ (in webers) is

$$\Phi = B A_{\text{pole}} = \frac{\pi B L D}{N_p} \iff B L D = \frac{N_p \Phi}{\pi}$$

Substituting $B L D = \dfrac{N_p \Phi}{\pi}$ into $K_E$:

$$\begin{aligned}
K_E &= \frac{Z}{a}\,\frac{B L D}{2} \\[4pt]
&= \frac{Z}{a}\,\frac{1}{2}\left(\frac{N_p \Phi}{\pi}\right) \\[4pt]
&= \frac{Z N_p \Phi}{2\pi a}
\end{aligned}$$

Collecting both forms, the armature EMF of a brushed DC machine is

$$E = K_E\,\omega, \qquad K_E = \frac{Z}{a}\,B L \frac{D}{2} = \frac{Z N_p \Phi}{2\pi a} \quad \bigl[\text{V}\,\text{s}\,\text{rad}^{-1}\bigr]$$

$K_E$ depends only on the fixed geometry ($Z, a, N_p, D, L$) and the magnetic excitation ($B$ or $\Phi$). In a **permanent-magnet (PM)** machine the magnets fix $\Phi$, so $K_E$ is a constant; in a **wound-field** machine, $K_E$ can be varied by adjusting the DC field current $i_f$ to change $\Phi$.

## 3. Generator loading and the equivalent circuit

### Counter-torque under load

On open circuit ($i = 0$) no current flows in the armature conductors, so there is no electromagnetic Lorentz force on the rotor. The prime mover then only has to overcome small bearing friction, brush friction and aerodynamic windage losses.

Connecting a load resistor $R_{\text{load}}$ across the terminals lets the induced EMF $E$ drive an armature current $i$ out of the positive brush. By the right-hand grip rule, this current sets up a **rotor magnetic field** with its own North and South poles, perpendicular to the stator field axis. As the prime mover turns the rotor (clockwise, say), the rotor's South pole is forced towards the stator's South pole while being pulled back by the stator's North pole, and similarly for the rotor's North pole. Equivalently, by Fleming's left-hand rule ($F_c = B i_c L$), every conductor carrying $i_c = i/a$ feels a Lorentz force directed opposite to its velocity $u$.

The result is an electromagnetic **counter-torque** $T_{\text{em}} = K_T i$ opposing the prime mover. As the load current rises, the shaft becomes harder to turn, and the prime mover must supply mechanical power $P_{\text{em}} = T_{\text{em}} \omega = E i$, as Lenz's law and conservation of energy require.

### Dynamic and steady-state equivalent circuit

The armature winding is a long coil of copper wire in iron slots, so it has a series **armature resistance** $R_a$ and a series **armature inductance** $L_a$. $R_a$ covers the copper resistance of the parallel winding paths plus the contact resistance of the carbon brushes on the commutator.

![[ee_c5_dc_machine_circuits.png|900]]

Inside the generator, the motional EMF acts as an ideal source $E = K_E \omega$ in series with $R_a$ and $L_a$, driving $i(t)$ out of the positive terminal into the load at terminal voltage $V(t)$. KVL around the loop in the direction of $i(t)$ gives

$$\begin{aligned}
E - i R_a - L_a\frac{\mathrm{d}i}{\mathrm{d}t} - V &= 0 \\[4pt]
V &= E - i R_a - L_a\frac{\mathrm{d}i}{\mathrm{d}t}
\end{aligned}$$

Once the speed and the load resistance have settled so that $i$ is constant ($\mathrm{d}i/\mathrm{d}t = 0$), the voltage across the inductance vanishes:

$$v_{L_a} = L_a\frac{\mathrm{d}i}{\mathrm{d}t} = 0$$

$L_a$ can then be replaced by a short circuit, and the steady-state terminal voltage is

$$V = E - i R_a = K_E \omega - i R_a$$

> [!warning] Generator and motor signs differ
> In a generator, current flows out of the machine and $R_a$ drops $iR_a$, so a loaded generator always has $V < E$. In a DC motor ([[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]) an external supply drives current into the machine, so $V = E + i R_a > E$. Using the motor sign for a generator gives a terminal voltage above the EMF.

### Open-circuit measurement of the EMF constant

With the terminals open-circuited ($i = 0$), both internal drops vanish ($i R_a = 0$ and $L_a\,\mathrm{d}i/\mathrm{d}t = 0$), so a high-impedance voltmeter across the brushes reads the internal EMF directly:

$$V_{\text{oc}} = E = K_E \omega \iff K_E = \frac{V_{\text{oc}}}{\omega}$$

Driving the shaft at a known speed $\omega = \dfrac{2\pi\,\text{rpm}}{60}$ on open circuit and measuring $V_{\text{oc}}$ is the standard experimental method for finding $K_E$, and hence $K_T = K_E$, of an unknown DC machine.

## Worked examples

### Open-circuit test for the EMF constant

The back-EMF constant $K_E$ of a permanent-magnet DC machine is estimated by driving its shaft as a generator at a known speed with the terminals open-circuited (Tutorial Sheet 6 Q1; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q1: Back-EMF constant from an open-circuit test|Tutorial 6 Q1]]). At $1000\ \text{rpm}$ the open-circuit voltage is $V_{\text{oc}} = 10.0\ \text{V}$. Find (a) $K_E$ in $\text{V}\,\text{s}\,\text{rad}^{-1}$, and (b), for the machine used as a tachogenerator with a high-impedance voltmeter drawing negligible current, the voltage at $2500\ \text{rpm}$ and the speed in $\text{rpm}$ that gives a reading of $6.4\ \text{V}$.

(a) On open circuit $i = 0\ \text{A}$, so there is no drop across the armature resistance ($i R_a = 0$) and the terminal voltage equals the induced EMF, $E = V_{\text{oc}} = 10.0\ \text{V}$. The speed of $1000\ \text{rev}\,\text{min}^{-1}$ in SI units is

$$\begin{aligned}
\omega &= \frac{2\pi\,\text{rpm}}{60} \\[4pt]
&= \frac{2\pi \times 1000}{60} \\[4pt]
&= \frac{100\pi}{3}\ \text{rad}\,\text{s}^{-1} = 104.72\ \text{rad}\,\text{s}^{-1}
\end{aligned}$$

Dividing the EMF by this speed gives the EMF constant:

$$\begin{aligned}
K_E &= \frac{E}{\omega} \\[4pt]
&= \frac{10.0\ \text{V}}{104.72\ \text{rad}\,\text{s}^{-1}} \\[4pt]
&= 0.09549\ \text{V}\,\text{s}\,\text{rad}^{-1} \approx 0.0955\ \text{V}\,\text{s}\,\text{rad}^{-1}
\end{aligned}$$

(b) $E = K_E \omega$ is linear in speed. At $2500\ \text{rpm}$, $\omega_2 = \dfrac{2\pi \times 2500}{60} = 261.80\ \text{rad}\,\text{s}^{-1}$, so

$$V_{\text{oc},2} = K_E \omega_2 = (0.095493\ \text{V}\,\text{s}\,\text{rad}^{-1})(261.80\ \text{rad}\,\text{s}^{-1}) = 25.0\ \text{V}$$

A reading of $V_{\text{oc},3} = 6.4\ \text{V}$ corresponds to

$$\omega_3 = \frac{V_{\text{oc},3}}{K_E} = \frac{6.4\ \text{V}}{0.095493\ \text{V}\,\text{s}\,\text{rad}^{-1}} = 67.02\ \text{rad}\,\text{s}^{-1} \implies \text{rpm}_3 = \frac{60\,\omega_3}{2\pi} = 640\ \text{rpm}$$

> [!check] Cross-check in volts per krpm
> Datasheets often quote tachogenerator sensitivity in volts per $1000\ \text{rpm}$, here $k_v = \dfrac{10.0\ \text{V}}{1000\ \text{rpm}} = 10.0\ \text{V}/\text{krpm}$. At $2.5\ \text{krpm}$ this gives $10.0 \times 2.5 = 25.0\ \text{V}$, and $6.4\ \text{V}$ corresponds to $\dfrac{6.4}{10.0} = 0.640\ \text{krpm} = 640\ \text{rpm}$, agreeing with the calculation in $\text{rad}\,\text{s}^{-1}$.

### EMF constant, loaded terminal voltage and parallel paths

A $4$-pole ($N_p = 4$) permanent-magnet DC machine has rotor diameter $D = 0.20\ \text{m}$, active axial length $L = 0.20\ \text{m}$ and average radial air-gap flux density $B = 0.50\ \text{T}$. Its armature has $Z = 200$ active conductors in $a = 2$ parallel paths, with total armature resistance $R_a = 0.50\ \Omega$ between the brushes. A prime mover drives it as a generator at a constant $1500\ \text{rpm}$. Find (a) the flux per pole $\Phi$, and check that $K_E = \dfrac{Z}{a} B L \dfrac{D}{2}$ and $K_E = \dfrac{Z N_p \Phi}{2\pi a}$ agree; (b) the open-circuit EMF $E$, and the terminal voltage $V$, load resistance $R_{\text{load}}$, output power $P_{\text{out}}$ and counter-torque $T_{\text{em}}$ for a steady load current $i = 20\ \text{A}$; (c) how $K_E$, $E$, the rated terminal current $i$ and the rated electromagnetic power $P_{\text{em}}$ change if the same $Z = 200$ conductors are reconnected during manufacture into $a = 4$ parallel paths (a $4$-pole lap winding), with the maximum current per conductor held at $i_c = 10\ \text{A}$.

(a) With $D = 0.20\ \text{m}$, $L = 0.20\ \text{m}$, $B = 0.50\ \text{T}$ and $N_p = 4$ poles, the flux per pole is

$$\begin{aligned}
\Phi &= \frac{\pi B L D}{N_p} \\[4pt]
&= \frac{\pi \times (0.50\ \text{T}) \times (0.20\ \text{m}) \times (0.20\ \text{m})}{4} \\[4pt]
&= 0.005\pi\ \text{Wb} = 15.71\ \text{mWb}
\end{aligned}$$

With $Z = 200$ and $a = 2$, the dimensional formula and the flux-per-pole formula give

$$\begin{aligned}
K_E &= \frac{Z}{a}\,B L \frac{D}{2} = \frac{200}{2} \times (0.50\ \text{T}) \times (0.20\ \text{m}) \times \left(\frac{0.20\ \text{m}}{2}\right) = 1.000\ \text{V}\,\text{s}\,\text{rad}^{-1} \\[6pt]
K_E &= \frac{Z N_p \Phi}{2\pi a} = \frac{200 \times 4 \times (0.005\pi\ \text{Wb})}{2\pi \times 2} = \frac{4.000\pi}{4\pi} = 1.000\ \text{V}\,\text{s}\,\text{rad}^{-1}
\end{aligned}$$

Both give $K_E = 1.00\ \text{V}\,\text{s}\,\text{rad}^{-1}$.

(b) At $1500\ \text{rpm}$ the angular velocity is

$$\omega = \frac{2\pi \times 1500}{60} = 50\pi\ \text{rad}\,\text{s}^{-1} = 157.08\ \text{rad}\,\text{s}^{-1}$$

and the internal EMF is

$$\begin{aligned}
E &= K_E \omega \\[4pt]
&= (1.000\ \text{V}\,\text{s}\,\text{rad}^{-1})(157.08\ \text{rad}\,\text{s}^{-1}) \\[4pt]
&= 157.08\ \text{V} \approx 157.1\ \text{V}
\end{aligned}$$

Delivering $i = 20\ \text{A}$ through $R_a = 0.50\ \Omega$, the steady-state terminal voltage and load resistance are

$$\begin{aligned}
V &= E - i R_a = 157.08\ \text{V} - (20\ \text{A})(0.50\ \Omega) = 157.08\ \text{V} - 10.00\ \text{V} = 147.08\ \text{V} \approx 147.1\ \text{V} \\[4pt]
R_{\text{load}} &= \frac{V}{i} = \frac{147.08\ \text{V}}{20\ \text{A}} = 7.354\ \Omega
\end{aligned}$$

With $K_T = K_E = 1.000\ \text{N}\,\text{m}\,\text{A}^{-1}$, the power delivered to the load, the armature copper loss and the counter-torque are

$$\begin{aligned}
P_{\text{out}} &= V i = (147.08\ \text{V})(20\ \text{A}) = 2941.6\ \text{W} \\[4pt]
P_{\text{cu}} &= i^2 R_a = (20\ \text{A})^2 (0.50\ \Omega) = 200.0\ \text{W} \\[4pt]
T_{\text{em}} &= K_T i = (1.000\ \text{N}\,\text{m}\,\text{A}^{-1})(20\ \text{A}) = 20.0\ \text{N}\,\text{m}
\end{aligned}$$

(c) With $a = 2$ paths and $i = 20\ \text{A}$, each conductor carries $i_c = i/a = 20/2 = 10\ \text{A}$. Reconnected into $a = 4$ paths, each path holds $Z/a = 50$ conductors in series instead of $100$. $K_E$ halves to $K_E' = \dfrac{200}{4}(0.50)(0.20)(0.10) = 0.500\ \text{V}\,\text{s}\,\text{rad}^{-1}$, so the EMF at $1500\ \text{rpm}$ halves to $E' = 78.54\ \text{V}$. For the same thermal limit of $i_c = 10\ \text{A}$ per conductor, the permissible terminal current doubles to $i' = a i_c = 4 \times 10\ \text{A} = 40\ \text{A}$. Since $4$ paths of half the length are now in parallel, $R_a'$ falls by a factor of $4$ to $0.125\ \Omega$.

The electromagnetic power $P_{\text{em}} = E' i' = (78.54\ \text{V})(40\ \text{A}) = 3141.6\ \text{W}$ and the copper loss $P_{\text{cu}} = (40\ \text{A})^2 (0.125\ \Omega) = 200.0\ \text{W}$ are unchanged. Increasing $a$ trades lower voltage for higher current at constant machine power.

> [!check] Electromechanical power balance
> For the $a = 2$ generator at $\omega = 157.08\ \text{rad}\,\text{s}^{-1}$ and $i = 20\ \text{A}$, the mechanical power absorbed by the counter-torque is
> $$P_{\text{em}} = T_{\text{em}}\,\omega = (20.0\ \text{N}\,\text{m})(157.0796\ \text{rad}\,\text{s}^{-1}) = 3141.6\ \text{W}$$
> The total electrical power generated is
> $$E i = (157.0796\ \text{V})(20\ \text{A}) = 3141.6\ \text{W} = P_{\text{out}} + P_{\text{cu}} = 2941.6\ \text{W} + 200.0\ \text{W}$$
> The mechanical power put in against the counter-torque equals the power delivered to the load plus the Joule heat in $R_a$.

### Ripple with several commutator coils

An idealised commutator generator has peak coil EMF $E_{\text{peak}} = 100\ \text{V}$ and $n$ identical armature coils displaced by $180^\circ/n$, with the brushes always selecting the coil with the largest instantaneous voltage. Find the hand-over angle from the peak, $\theta_{\text{sw}} = 90^\circ/n$, the minimum terminal voltage $E_{\text{min}}$ and the percentage ripple for $n = 1$, $2$, $3$ and $6$.

Using $E_{\text{min}} = E_{\text{peak}}\cos\!\left(\dfrac{\pi}{2n}\right)$ for $n \ge 1$ and $\text{Ripple} = \dfrac{E_{\text{peak}} - E_{\text{min}}}{E_{\text{peak}}} \times 100\%$, one coil on $2$ commutator segments gives

$$\theta_{\text{sw}} = 90^\circ, \qquad E_{\text{min}} = 100\cos 90^\circ = 0.0\ \text{V}, \qquad \text{Ripple} = 100.0\%$$

Two coils at $90^\circ$ on $4$ segments give

$$\theta_{\text{sw}} = 45^\circ, \qquad E_{\text{min}} = 100\cos 45^\circ = 70.71\ \text{V}, \qquad \text{Ripple} = 29.29\% \approx 29\%$$

Three coils at $60^\circ$ on $6$ segments give

$$\theta_{\text{sw}} = 30^\circ, \qquad E_{\text{min}} = 100\cos 30^\circ = 86.60\ \text{V}, \qquad \text{Ripple} = 13.40\% \approx 13\%$$

Six coils at $30^\circ$ on $12$ segments give

$$\theta_{\text{sw}} = 15^\circ, \qquad E_{\text{min}} = 100\cos 15^\circ = 96.59\ \text{V}, \qquad \text{Ripple} = 3.41\%$$

> [!check] Small-angle scaling for large n
> With $\cos x \approx 1 - \tfrac{1}{2}x^2$ for $x = \dfrac{\pi}{2n} \ll 1$, the fractional ripple scales as
> $$\text{Ripple} \approx \frac{1}{2}\left(\frac{\pi}{2n}\right)^2 = \frac{\pi^2}{8 n^2} \approx \frac{1.234}{n^2}$$
> Doubling the number of coils from $n = 3$ to $n = 6$ cuts the ripple by a factor of $4$, from $13.40\%$ to $3.41\%$, against $1.234/36 = 3.43\%$ from the approximation.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Prerequisites: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- Next: [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Concepts: [[Commutator]] · [[Back EMF and Torque Constants]] · [[Motional EMF in Electric Machines]]
- Worked problems: [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] (Q1, Q2)
- In servo positioning systems such as radar pedestals and aircraft flight-control test rigs, a small PM DC tachogenerator on the motor shaft outputs $V_{\text{tacho}} = K_E \omega$, giving rate damping in a closed-loop controller ([[SESA2027 B1 - Control System Fundamentals and PID Control]], [[Measurement Chain]]).
- Brushes on a commutator bring sliding friction, sparking that causes electromagnetic interference and erodes the segments (fast in vacuum, where the protective oxide and moisture films on carbon brushes evaporate) and a finite maintenance life. Spacecraft reaction wheels and UAV motors therefore put the magnets on the rotor and commutate stationary stator coils electronically with MOSFET H-bridges or inverters ([[FEEG1004 C6 - DC Motor Characteristics and Speed Control]], [[Reaction Wheels and Momentum Dumping]]).

## Sources

- `02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf` (§4 DC Machine, with Fig. 4.1 two-segment commutator, Fig. 4.2 multi-coil commutator and Fig. 4.3 generator under load; §4.2 Construction, Fig. 4.9 teardown; §4.3.1 EMF and $K_E$; Figs. 4.4–4.5 equivalent circuits; pp. 20–25)
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 05 - DC Generators - Lecture Slides.pdf` (slides 1–9; slide 6 EMF derivation; slide 8 open-circuit measurement of $K_E$, the Tutorial Sheet 6 Q1 example)
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 06 - DC Motors Torque - Lecture Slides.pdf` (slide 2: DC generator revision)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-14.txt` (ll. 1–188: DC machine anatomy teardown, commutator vs slip rings, $E = K_E \omega$, and DC generator equivalent circuit; ll. 358–417: physical reason for $a$ parallel paths)
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf` (Q1, Q2)
- E. Hughes, *Electrical and Electronic Technology*, Ch. 39 (Direct-Current Machines)

## Self-study tasks

### Core

- [ ] Explain which component (brushes, commutator, armature coils or laminations) turns a rotating-coil AC generator into a DC generator, and why the other three can all be present in an AC machine (`Electric Machines 06` slide 2 poll; Lecture 2025-02-14, ll. 119–158). → [[#From slip rings to a split-ring commutator]]
- [ ] Starting from $e_c = B L u$ for one conductor, derive $E = \dfrac{Z}{a} B L \dfrac{D}{2} \omega = \dfrac{Z N_p \Phi}{2\pi a} \omega$ for $Z$ conductors in $a$ parallel paths (`Electric Machines 05` slide 6; Sharkh §4.3.1). → [[#2. Armature EMF equation]]
- [ ] Explain why the terminals must be open-circuited when measuring $K_E$, and find $K_E$ in $\text{V}\,\text{s}\,\text{rad}^{-1}$ for a motor giving $10\ \text{V}$ on open circuit at $1000\ \text{rpm}$ (`Electric Machines 05` slide 8; Tutorial Sheet 6 Q1). → [[#Open-circuit test for the EMF constant]]; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q1: Back-EMF constant from an open-circuit test|Tutorial 6 Q1]]
- [ ] Compare the steady-state KVL equation of a loaded DC generator ($V = E - i R_a$) with that of a DC motor at the same speed ($V = E + i R_a$), and explain why the generator terminal voltage is lower (Tutorial Sheet 6 Q2). → [[#Dynamic and steady-state equivalent circuit]]; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q2: Running light as a motor at 1000 rpm: 10.2 V, 1 A|Tutorial 6 Q2]]

### Further practice

- [ ] For the $1500\ \text{rpm}$ generator ($E = 157.08\ \text{V}$, $R_a = 0.50\ \Omega$, $i = 20\ \text{A}$, $V = 147.08\ \text{V}$), take friction, windage and iron losses as $P_{\text{rot}} = 150\ \text{W}$; find the shaft input $P_{\text{in,mech}} = P_{\text{em}} + P_{\text{rot}} = 3291.6\ \text{W}$ and the efficiency $\eta = P_{\text{out}} / P_{\text{in,mech}} = 89.4\%$ (suggested, not lecturer-set). → [[#EMF constant, loaded terminal voltage and parallel paths]]

## Transcript and slide slips

> [!warning] Missing $BL$ factor in the printed $K_E$ box (`S2-W18-21 Electric Machines 05 - DC Generators - Lecture Slides.pdf`, slides 6 and 8)
> Where: [[#2. Armature EMF equation]]
> On slides 6 and 8 of `S2-W18-21 Electric Machines 05`, the text-extracted formula for the EMF constant $K_E$ next to $E = \dfrac{Z}{a} B L \omega \dfrac{D}{2}$ omits or clips the $B L$ factor in the separate $K_E =$ box. As shown on `S2-W18-21 Electric Machines 06` slide 2 and in Sharkh Notes Eq. (4.5), the complete expression is $K_E = \dfrac{Z}{a}\,B L \dfrac{D}{2} = \dfrac{Z N_p \Phi}{2\pi a}$.

> [!warning] Typo "conencted" in the Fig. 4.5 caption (`S2 Electric Machines Notes - Sharkh.pdf`, p. 22)
> Where: [[#Dynamic and steady-state equivalent circuit]]
> On page 22 of the printed notes, the caption to Figure 4.5 reads "Steady state constant current equivalent circuit of a DC generator conencted to a load" ("conencted" for "connected").
