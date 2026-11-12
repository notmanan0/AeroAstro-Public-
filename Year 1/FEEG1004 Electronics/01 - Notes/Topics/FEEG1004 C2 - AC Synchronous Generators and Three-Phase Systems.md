---
title: "FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 2
tags:
- feeg1004
- machines
- synchronous-generator
- alternator
- three-phase
- star
- delta
- poles
aliases:
- Electric Machines 02-03
- Synchronous generator
- Turbo-alternator
- Three-phase
- rpm = 120f/Np
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"
next_topics:
- "[[FEEG1004 C3 - Transformers and AC Power Transmission]]"
key_concepts:
- "[[Synchronous Speed and Pole Number]]"
- "[[Motional EMF in Electric Machines]]"
- "[[Three-Phase Star and Delta Connections]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"
sources:
- 02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf
- 02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf
- 02 - Sources/S2 Machines/S2-W18-21 Electric Machines 03 - Turbo Generators EMF - Lecture Slides.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2025-01-27.txt
- 02 - Sources/Lectures/FEEG1004 Lecture 2025-02-04.txt
- 02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf
coverage: "FEEG1004 Lecture 2025-01-27 (ll. 44–98); FEEG1004 Lecture 2025-02-04 (ll. 1–332)"
---

# FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems

> [!abstract] Summary
> A three-phase synchronous generator (alternator) spins a DC-excited rotor inside a stator carrying three windings displaced by $120^\circ$. A rotor with $N_p$ poles turning at $\text{rpm}$ revolutions per minute generates frequency $f = N_p\,\text{rpm}/120$, and applying $E = NBLu$ to both coil sides gives a peak phase EMF $E_{\text{peak}} = N B_{\text{peak}} L_{\text{rotor}} \omega D$. The three phase EMFs sum to zero at every instant, which allows star connection ($V_L = \sqrt{3}\,V_{\text{ph}}$, $I_L = I_{\text{ph}}$) or delta connection ($V_L = V_{\text{ph}}$, $I_L = \sqrt{3}\,I_{\text{ph}}$), both delivering $P = \sqrt{3}\,V_L I_L \cos\phi$. Into a balanced load the neutral current is zero and the total instantaneous power is constant.

> [!summary]- Exam use: quick path
> - **Use it when:** relating grid frequency, pole count and shaft speed; finding the phase EMF of a generator from rotor size, speed and air-gap flux density; converting between phase and line quantities in star or delta; finding three-phase power and neutral current.
> - **Assumptions:** $N_p$ is the total number of poles (not pole pairs); fully pitched coils whose two sides lie under opposite poles; sinusoidally distributed air-gap flux, so $E_{\text{rms}} = E_{\text{peak}}/\sqrt{2}$; balanced load for zero neutral current.
> - **Method:** 1. Find $f = N_p\,\text{rpm}/120$. 2. Convert speed with $\omega = 2\pi\,\text{rpm}/60$ and find $u = \omega D/2$. 3. Get $E_{\text{peak}} = N B_{\text{peak}}(2L_{\text{rotor}})u$ per coil, then multiply by the number of series coils. 4. Divide by $\sqrt{2}$ for $E_{\text{rms}}$ and apply the star or delta relations. 5. Find $I_{\text{ph}}$, then $P = 3V_{\text{ph}}I_{\text{ph}}\cos\phi$.
> - **Common mistakes:** using pole pairs in $\text{rpm} = 120f/N_p$ (or the formula $60f/p$ with total poles); taking only one coil side, so $L = L_{\text{rotor}}$ instead of $2L_{\text{rotor}}$.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q4: Tidal turbine with a 24-pole, 3-phase PM generator at 150 rpm|Tutorial 5 Q4]]

Power stations, from $3000\ \text{rpm}$ steam-turbine turbo-alternators to slow-turning multipole hydroelectric plants such as Three Gorges ($26 \times 700\ \text{MW} = 18.2\ \text{GW}$), generate three-phase alternating voltage by sweeping a rotating magnetic field past stationary stator conductors. The electrical frequency is locked to the shaft rotation, so every generator connected to a national grid must turn in exact synchronism with the grid frequency.

Each North–South pole pair that sweeps past a stator coil produces one electrical cycle. A fast steam turbine therefore needs only two poles to make $50\ \text{Hz}$, while a slow water turbine needs dozens. The size of the induced EMF follows from the motional law of [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors|C1]]: the stator conductors cut the rotor's air-gap field at the rotor's peripheral speed.

Three windings spaced a third of a revolution apart produce three equal sinusoids $120^\circ$ apart. Their sum is zero at every instant, so the windings can share a return conductor that carries no current, or be closed into a ring without any circulating current, and the power delivered to a balanced load has no ripple.

## 1. Power generation chains and synchronous alternators

In a conventional thermal power station a **heat source** (natural gas, coal, nuclear fission, biomass or concentrated solar thermal) supplies a **heat engine** (a steam turbine, gas turbine, or a diesel engine for standby power). The engine drives the shaft of an **AC synchronous generator**, also called an **alternator**, whose output voltage a power transformer steps up (typically to $400\ \text{kV}$ in the UK national grid) for low-loss transmission over long distances.

Renewable prime movers such as wind turbines, wave energy converters and tidal stream turbines take kinetic energy directly from a fluid flow without a thermal cycle. Wind and marine rotors turn slowly (typically $10\text{--}150\ \text{rpm}$) and at a speed that varies with the wind or tide. They either drive a high-speed generator through a step-up **gearbox** or couple directly to a large-diameter multipole generator, followed by **power-conditioning electronics** (rectifier–inverter stages) that convert the variable-frequency AC into fixed $50\ \text{Hz}$ grid-synchronised power.

The same machines appear in aerospace. Civil and military aircraft distribute three-phase AC at $115\ \text{V}$ phase ($200\ \text{V}$ line-to-line) and $f = 400\ \text{Hz}$ rather than $50\ \text{Hz}$. Raising $f$ by a factor of $8$ lets generators and transformers run at $8$ times the speed or with $1/8$ of the core cross-section ([[FEEG1004 C3 - Transformers and AC Power Transmission]], [[Electric and Magnetic Loading]]), which cuts onboard mass considerably. Jet-engine spool speed varies between ground idle and take-off, so aircraft alternators regulate frequency with either a hydromechanical Constant Speed Drive (CSD) or Integrated Drive Generator (IDG), or with variable-frequency power electronics. The shaft power for large turbo-alternators comes from Brayton and Rankine cycle turbomachinery ([[Brayton Cycle]], [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]). Spacecraft reaction-wheel motors and drone propulsion motors are three-phase permanent-magnet synchronous machines run in reverse, as motors driven by an electronic three-phase inverter ([[FEEG1004 C6 - DC Motor Characteristics and Speed Control]], [[Reaction Wheels and Momentum Dumping]]).

## 2. Generator construction

### Rotating magnet versus rotating coil

Faraday's law $e = -\mathrm{d}(N\Phi)/\mathrm{d}t$ depends only on the relative motion between field and armature coil, so an AC generator can be built either way round.

In the first arrangement a coil rotates inside a stationary magnet. A permanent magnet or DC field winding on the stator sets up a fixed field across the bore, and the armature coil turns with the shaft. Spinning at angular velocity $\omega$, the coil's linked flux varies as $\Phi(t) = \Phi_m \sin(\omega t)$, inducing $e(t) = -N\omega\Phi_m\cos(\omega t)$. To take this current off the rotor, the two coil ends connect to two continuous coaxial copper or brass **slip rings** on the shaft, against which stationary spring-loaded **carbon brushes** press. Brushes wear by friction, arc under high current and add a contact voltage drop, and a compact spinning rotor is hard to insulate and cool at high power. Rotating-coil alternators are therefore restricted to small, low-power machines such as bicycle dynamos and laboratory generators.

All large synchronous generators use the second arrangement, a magnet rotating inside a stationary armature. The high-power, high-voltage AC **armature windings** sit on the stationary **stator**, and the **field magnet** sits on the **rotor**. The field is either permanent magnets or a DC field winding fed with a modest excitation current through small slip rings or a brushless exciter on the same shaft. Putting the main windings on the stator has four advantages. Currents of thousands of amperes at $11\text{--}25\ \text{kV}$ are taken straight from fixed terminals, without sliding brushes and slip rings. High-voltage insulation is much easier to accommodate, and to protect from centrifugal stress, in stationary slots than on a spinning rotor. The outer stator has a much larger circumference and volume, which leaves room for forced cooling (air, hydrogen gas, de-ionised water or oil) to take heat directly from the armature conductors. And the rotor is lighter and stiffer, so it can run faster.

![[ee_c2_synchronous_generator.png|1000]]

### Cylindrical and salient-pole rotors

The rotor's mechanical design depends on the speed of the prime mover. High-speed steam- and gas-turbine **turbo-generators**, with $2$ poles ($3000\ \text{rpm}$ at $50\ \text{Hz}$) or $4$ poles ($1500\ \text{rpm}$), use a **non-salient-pole (cylindrical) rotor**. It is machined from a single solid steel forging with axial slots milled into its surface; insulated copper field bars are wedged flush into the slots and fed with DC to form smooth North and South poles. A long, slender cylinder (typically $D \approx 0.7\ \text{m}$ in diameter and $L_{\text{rotor}} \approx 7\ \text{m}$ long) keeps peripheral speed and centrifugal stress within safe limits, and its smooth surface keeps aerodynamic windage drag low at $3000\ \text{rpm}$.

Slow multipole hydroelectric generators, which may have $20$ to $80$ poles turning at $75\text{--}300\ \text{rpm}$, use a **salient-pole rotor**. Distinct laminated steel pole shoes, the salient poles, project radially from a large-diameter rotor spider or hub (up to $30\ \text{m}$ across in giant hydro units). Each carries a concentrated DC field coil, with polarity alternating $\text{N–S–N–S}$ round the circumference.

### Stator laminations and Roebel bars

The stator core is swept continuously by the rotating field. A solid steel stator would act as a closed single-turn secondary and carry large circulating **eddy currents**, causing severe $I^2 R$ core heating and loss of efficiency. To suppress them while keeping a low-reluctance magnetic path, the core is stacked from thousands of thin silicon-steel punchings (**laminations**), each coated on both faces with insulating varnish or oxide, so that the axial eddy-current paths are broken into thin insulated layers.

In large turbo-alternators the stator conductors face two further AC effects inside the slots. When a conductor carries alternating current, its own time-varying field crowds the current towards the outer surface (the **skin effect**), leaving the centre of a thick solid bar carrying almost nothing. Large stator bars therefore use **hollow rectangular copper sub-conductors**, and the central bore carries cooling gas, de-ionised water or oil right through the conductor where the heat is generated.

The second effect comes from slot leakage. A high-current stator bar is a bundle of parallel copper strands, insulated from one another along the slot and joined at both ends. The field varies across the depth of the slot, so two untwisted strands at different depths would link slightly different fluxes, and the voltage difference between them would drive parasitic currents round the bundle. To prevent this, the insulated strands are continuously twisted and transposed by $180^\circ$ or $360^\circ$ along the slot, forming **Roebel bars**. Over the full slot length, the EMF induced in a strand while it sits at the top of the slot cancels the equal and opposite EMF induced once it is transposed to the bottom, so the net circulating current is zero. Twisted-pair instrumentation and communication cables reject external magnetic pickup for the same reason.

## 3. Synchronous speed, pole number and electrical frequency

In a **2-pole** generator ($N_p = 2$, one North–South pole pair) whose rotor turns at constant mechanical angular velocity $\omega\ \text{rad}\,\text{s}^{-1}$, so the rotor angle is $\theta(t) = \omega t$, the flux linking a stationary $N$-turn stator coil varies sinusoidally as the rotor magnet sweeps past it:

$$\Phi(t) = \Phi_m \sin\theta = \Phi_m \sin(\omega t),$$

where $\Phi_m$ is the maximum linked flux, reached when the rotor's magnetic axis is perpendicular to the coil plane. Faraday's law gives the induced EMF:

$$\begin{aligned}
e(t) &= -\frac{\mathrm{d}(N\Phi)}{\mathrm{d}t} \\[4pt]
&= -N\Phi_m \frac{\mathrm{d}}{\mathrm{d}t}\bigl(\sin(\omega t)\bigr) \\[4pt]
&= -N \omega \Phi_m \cos(\omega t) \\[4pt]
&= -E_m \cos(\omega t).
\end{aligned}$$

Shifting the time origin by a quarter-cycle (equivalently, measuring $\theta$ from the axis where $\Phi(\theta) = \Phi_m \cos\theta$) puts the EMF in standard sine form:

$$e(t) = E_m \sin(\omega t) = E_m \sin(2\pi f t), \qquad E_m = N \omega \Phi_m.$$

$\Phi(t)$ and $e(t)$ are $90^\circ$ ($\pi/2\ \text{rad}$) out of phase. The EMF is zero at the instant of maximum flux, where $\mathrm{d}\Phi/\mathrm{d}t = 0$, and peaks at $E_m$ as the flux passes through zero, when the pole faces sweep straight across the coil sides and cut flux fastest.

A rotor with $N_p$ poles ($N_p$ even: $2, 4, 6, \dots$), arranged alternately $\text{N–S–N–S}$, has $N_p/2$ **pole pairs**. Each pole pair passing a stator coil drives the voltage through one full electrical cycle ($2\pi$ electrical radians), so one mechanical revolution ($2\pi$ mechanical radians) produces $N_p/2$ electrical cycles. With the rotor at mechanical angular speed $\omega\ \text{rad}\,\text{s}^{-1}$, the electrical angular frequency $\omega_e = 2\pi f$ and the frequency $f$ in $\text{Hz}$ are

$$\begin{aligned}
\omega_e &= 2\pi f = \frac{N_p}{2}\,\omega, \\[4pt]
f &= \frac{N_p}{2}\,\frac{\omega}{2\pi}.
\end{aligned}$$

A speed of $\text{rpm}$ revolutions per minute is $\text{rpm}/60$ revolutions per second, so the mechanical angular velocity is

$$\omega = \frac{2\pi\,\text{rpm}}{60} \iff \text{rpm} = \frac{60\,\omega}{2\pi}.$$

Substituting this into $f = \dfrac{N_p}{2}\dfrac{\omega}{2\pi}$ gives the **synchronous speed equation**:

$$\begin{aligned}
f &= \frac{N_p}{2} \cdot \frac{1}{2\pi} \left(\frac{2\pi\,\text{rpm}}{60}\right) \\[4pt]
f &= \frac{N_p\,\text{rpm}}{120} \iff \text{rpm} = \frac{120 f}{N_p}.
\end{aligned}$$

> [!warning] Pole count versus pole pairs
> Here $N_p$ (written $p$ on the slides) is the total number of poles ($N_p = 2, 4, 6, \dots$), giving $\text{rpm} = 120 f/N_p$. Some textbooks define $p_{\text{pairs}} = N_p/2$, the number of pole pairs, and write $\text{rpm} = 60 f/p_{\text{pairs}}$. "A $4$-pole machine" ($N_p = 4$, $p_{\text{pairs}} = 2$, $1500\ \text{rpm}$ at $50\ \text{Hz}$) and "a machine with $2$ pole pairs" are the same machine, so check which a problem means.

![[ee_c2_poles_speed.png|760]]

## 4. Motional EMF of a cylindrical turbo-generator

In a large cylindrical generator the total flux $\Phi_m$ enclosed by a distributed stator coil is hard to measure, whereas the peak radial air-gap flux density $B_{\text{peak}}$ at the rotor surface is easy to measure. The peak phase EMF therefore comes from the motional form of Faraday's law, $E = N B L u$, from [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]. Two quantities are needed: the cutting velocity and the active length.

The radial gap between rotor and stator slots is only a few millimetres, small compared with the rotor diameter $D$, so the stator conductors sit at radius $R \approx D/2$. In a frame attached to the rotor, the stator conductors move round at the same angular speed $\omega$ in the opposite sense (clockwise if the rotor spins anticlockwise). Each stator conductor therefore cuts the radial field lines perpendicularly at the rotor's peripheral speed,

$$u = \omega R = \frac{\omega D}{2}.$$

A **fully pitched** stator coil of $N$ turns spans $180^\circ$ electrical, so its two axial sides lie under opposite poles at the same time. Each side has active length $L_{\text{rotor}}$, the axial length of the rotor core; the two circumferential end-windings lie outside the radial air-gap field and cut no flux. By Fleming's right-hand rule, when the North pole sweeps past the top coil side it induces an EMF out of the page, $e' = N B_{\text{peak}} L_{\text{rotor}} u$, and the South pole passing the bottom side induces an EMF of the same size into the page. Round the closed coil these two EMFs point the same way, so they add in series like two batteries connected nose to tail, and the active length per turn is

$$L = 2 L_{\text{rotor}}.$$

Substituting $L = 2 L_{\text{rotor}}$ and $u = \omega D/2$,

$$\begin{aligned}
E_{\text{peak}} &= 2 e' \\[4pt]
&= N B_{\text{peak}} (2 L_{\text{rotor}}) u \\[4pt]
&= N B_{\text{peak}} (2 L_{\text{rotor}}) \left(\frac{\omega D}{2}\right) \\[4pt]
&= N B_{\text{peak}} L_{\text{rotor}} \omega D.
\end{aligned}$$

If the radial flux density is distributed sinusoidally round the gap, the EMF is sinusoidal, $e(t) = E_{\text{peak}} \sin(2\pi f t)$, and the **root-mean-square (RMS)** phase EMF is

$$E_{\text{rms}} = \frac{E_{\text{peak}}}{\sqrt{2}} = \frac{N B_{\text{peak}} L_{\text{rotor}} \omega D}{\sqrt{2}}.$$

## 5. Three-phase windings, star and delta connections, and power

### Three-phase waveforms and their zero sum

A single-phase generator uses only a small part of the stator circumference, and its instantaneous power pulsates, dropping to zero twice every electrical cycle. Three identical windings $A$, $B$ and $C$ (start terminals $A_1, B_1, C_1$, finish terminals $A_2, B_2, C_2$) placed in slots $120^\circ$ electrical ($2\pi/3\ \text{rad}$) apart are swept by the rotor field in turn: coil $B$ one-third of a cycle after coil $A$, and coil $C$ two-thirds of a cycle after. The result is a **balanced three-phase set** of equal peak amplitude $E_m = E_{\text{peak}}$ and mutual displacement $120^\circ$:

$$\begin{aligned}
e_A(t) &= E_m \sin(\omega_e t) \\[4pt]
e_B(t) &= E_m \sin\!\left(\omega_e t - \frac{2\pi}{3}\right) \\[4pt]
e_C(t) &= E_m \sin\!\left(\omega_e t - \frac{4\pi}{3}\right) = E_m \sin\!\left(\omega_e t + \frac{2\pi}{3}\right),
\end{aligned}$$

where $\omega_e = 2\pi f$. Let $\theta = \omega_e t$ and expand $\sin(\theta - 2\pi/3)$ and $\sin(\theta + 2\pi/3)$ with $\sin(\theta \pm \alpha) = \sin\theta\cos\alpha \pm \cos\theta\sin\alpha$, using $\cos(2\pi/3) = -\tfrac{1}{2}$ and $\sin(2\pi/3) = \tfrac{\sqrt{3}}{2}$:

$$\begin{aligned}
e_A(t) + e_B(t) + e_C(t) &= E_m \left[\sin\theta + \sin\!\left(\theta - \frac{2\pi}{3}\right) + \sin\!\left(\theta + \frac{2\pi}{3}\right)\right] \\[4pt]
&= E_m \left[\sin\theta + \left(-\frac{1}{2}\sin\theta - \frac{\sqrt{3}}{2}\cos\theta\right) + \left(-\frac{1}{2}\sin\theta + \frac{\sqrt{3}}{2}\cos\theta\right)\right] \\[4pt]
&= E_m \bigl[(1 - \tfrac{1}{2} - \tfrac{1}{2})\sin\theta + (-\tfrac{\sqrt{3}}{2} + \tfrac{\sqrt{3}}{2})\cos\theta\bigr] \\[4pt]
&= 0.
\end{aligned}$$

The three phase EMFs therefore sum to zero at every instant:

$$e_A(t) + e_B(t) + e_C(t) = 0.$$

### Star and delta connections

Instead of running six wires (two per phase) from generator to load, the three windings are interconnected inside the machine in one of two ways.

In a **star ($\text{Y}$) connection** the three finish ends $A_2, B_2, C_2$ are joined at a common **neutral point** $N$, and three line conductors ($A, B, C$) plus an optional fourth **neutral wire** are brought out to the load. Each winding is in series with its own line, so the **line current** equals the **phase current**:

$$I_L = I_{\text{ph}}.$$

KCL at the neutral node gives the neutral return current as $i_N(t) = i_A(t) + i_B(t) + i_C(t)$. If the load is **balanced**, with the same impedance in each phase (for example $R_a = R_b = R_c = R$), the three currents have equal amplitudes and are $120^\circ$ apart:

$$i_A(t) = \frac{e_A(t)}{R}, \qquad i_B(t) = \frac{e_B(t)}{R}, \qquad i_C(t) = \frac{e_C(t)}{R}.$$

The same identity as for the voltages makes the neutral current zero at every instant:

$$i_N(t) = i_A(t) + i_B(t) + i_C(t) = \frac{e_A(t) + e_B(t) + e_C(t)}{R} = 0.$$

A balanced three-phase system therefore needs no neutral wire, and carries three times the power of a single-phase two-wire line on only three conductors.

The **line-to-line voltage** between two lines is $v_{AB}(t) = e_A(t) - e_B(t)$:

$$\begin{aligned}
v_{AB}(t) &= E_m\sin\theta - E_m\sin\!\left(\theta - \frac{2\pi}{3}\right) \\[4pt]
&= E_m\left[\sin\theta - \left(-\frac{1}{2}\sin\theta - \frac{\sqrt{3}}{2}\cos\theta\right)\right] \\[4pt]
&= E_m\left(\frac{3}{2}\sin\theta + \frac{\sqrt{3}}{2}\cos\theta\right) \\[4pt]
&= \sqrt{3}\,E_m\left(\frac{\sqrt{3}}{2}\sin\theta + \frac{1}{2}\cos\theta\right) \\[4pt]
&= \sqrt{3}\,E_m\sin\!\left(\theta + \frac{\pi}{6}\right).
\end{aligned}$$

Dividing peak values by $\sqrt{2}$ relates the RMS **line voltage** $V_L$ to the RMS **phase voltage** $V_{\text{ph}} = E_{\text{rms}}$:

$$V_L = \sqrt{3}\,V_{\text{ph}}.$$

UK domestic distribution, for example, has $V_{\text{ph}} = 230\ \text{V}$ RMS line-to-neutral and $V_L = \sqrt{3} \times 230\ \text{V} = 400\ \text{V}$ RMS line-to-line.

In a **delta ($\Delta$) connection** the three windings form a closed triangle ($A_2$ to $B_1$, $B_2$ to $C_1$, $C_2$ to $A_1$), and the three lines are taken from the corners. Three voltage sources in a closed loop would normally drive a destructive short-circuit current, but round the delta the net driving voltage is $e_A(t) + e_B(t) + e_C(t) = 0$ at every instant, so no current circulates round the ring on open circuit. Each winding sits directly across two lines, and each line current is the difference of two phase currents $120^\circ$ apart:

$$V_L = V_{\text{ph}}, \qquad I_L = \sqrt{3}\,I_{\text{ph}}.$$

### Proof of constant instantaneous power and the three-phase power formula

Let the generator feed a balanced resistive load $R_a = R_b = R_c = R$, with phase voltage $e_k(t)$ and phase current $i_k(t) = e_k(t)/R$ in each phase $k \in \{A, B, C\}$. The total instantaneous power is

$$\begin{aligned}
p(t) &= e_A(t)\,i_A(t) + e_B(t)\,i_B(t) + e_C(t)\,i_C(t) \\[4pt]
&= \frac{e_A^2(t) + e_B^2(t) + e_C^2(t)}{R} \\[4pt]
&= \frac{E_m^2}{R}\left[\sin^2\theta + \sin^2\!\left(\theta - \frac{2\pi}{3}\right) + \sin^2\!\left(\theta - \frac{4\pi}{3}\right)\right].
\end{aligned}$$

Apply $\sin^2\alpha = \tfrac{1}{2}\bigl(1 - \cos(2\alpha)\bigr)$ to each term, then use $\cos(2\theta - 8\pi/3) = \cos(2\theta - 2\pi/3)$:

$$\begin{aligned}
p(t) &= \frac{E_m^2}{2R}\left[\bigl(1 - \cos(2\theta)\bigr) + \left(1 - \cos\!\left(2\theta - \frac{4\pi}{3}\right)\right) + \left(1 - \cos\!\left(2\theta - \frac{8\pi}{3}\right)\right)\right] \\[4pt]
&= \frac{E_m^2}{2R}\left[3 - \left(\cos(2\theta) + \cos\!\left(2\theta - \frac{4\pi}{3}\right) + \cos\!\left(2\theta - \frac{2\pi}{3}\right)\right)\right].
\end{aligned}$$

The three cosines $\cos(2\theta)$, $\cos(2\theta - 2\pi/3)$ and $\cos(2\theta - 4\pi/3)$ form another balanced set spaced by $120^\circ$, so their sum is zero for every $\theta$:

$$\cos(2\theta) + \cos\!\left(2\theta - \frac{2\pi}{3}\right) + \cos\!\left(2\theta - \frac{4\pi}{3}\right) = 0.$$

All the $2\omega_e$ ripple terms cancel, and the instantaneous power is constant:

$$p(t) = \frac{3 E_m^2}{2 R} = 3\,\frac{(E_m/\sqrt{2})^2}{R} = \frac{3 E_{\text{rms}}^2}{R} = 3 V_{\text{ph}} I_{\text{ph}}.$$

More generally, if each phase of a balanced load has impedance angle $\phi$ (power factor $\cos\phi$, covered in [[FEEG1004 D4 - AC Power and Power Factor]]), each phase absorbs average real power $P_{\text{ph}} = V_{\text{ph}} I_{\text{ph}} \cos\phi$, and the total is $P = 3 V_{\text{ph}} I_{\text{ph}} \cos\phi$. Writing the phase quantities in terms of line voltage $V_L$ and line current $I_L$ gives the same formula for both connections. In star, $V_{\text{ph}} = V_L/\sqrt{3}$ and $I_{\text{ph}} = I_L$, so

$$P = 3 \left(\frac{V_L}{\sqrt{3}}\right) I_L \cos\phi = \sqrt{3}\,V_L I_L \cos\phi.$$

In delta, $V_{\text{ph}} = V_L$ and $I_{\text{ph}} = I_L/\sqrt{3}$, so

$$P = 3 V_L \left(\frac{I_L}{\sqrt{3}}\right) \cos\phi = \sqrt{3}\,V_L I_L \cos\phi.$$

![[ee_c2_three_phase_power.png|800]]

## Worked examples

### Synchronous speeds of steam and hydro generators

A high-speed steam-turbine generator has $N_p = 2$ poles and a low-head hydroelectric generator has $N_p = 80$ poles; both supply the $50\ \text{Hz}$ UK grid (`S2-W18-21 Electric Machines 02` slide 14; `Electric Machines 03` slide 2). The task is each rotor speed in $\text{rpm}$ and $\text{rad}\,\text{s}^{-1}$, and the speeds on a $60\ \text{Hz}$ grid as in North America.

With $\text{rpm} = 120 f/N_p$ and $\omega = 2\pi\,\text{rpm}/60$, the $2$-pole steam-turbine generator at $50\ \text{Hz}$ runs at

$$\begin{aligned}
\text{rpm}_{\text{steam}} &= \frac{120 \times 50\ \text{Hz}}{2} = 3000\ \text{rpm}, \\[4pt]
\omega_{\text{steam}} &= \frac{2\pi \times 3000}{60} = 100\pi\ \text{rad}\,\text{s}^{-1} = 314.2\ \text{rad}\,\text{s}^{-1}.
\end{aligned}$$

Two poles (one pole pair) is the minimum possible, so $3000\ \text{rpm}$ is the highest synchronous shaft speed for any generator connected directly to a $50\ \text{Hz}$ grid. The $80$-pole hydro generator runs at

$$\begin{aligned}
\text{rpm}_{\text{hydro}} &= \frac{120 \times 50\ \text{Hz}}{80} = 75\ \text{rpm}, \\[4pt]
\omega_{\text{hydro}} &= \frac{2\pi \times 75}{60} = 2.5\pi\ \text{rad}\,\text{s}^{-1} = 7.854\ \text{rad}\,\text{s}^{-1}.
\end{aligned}$$

At $f = 60\ \text{Hz}$,

$$\text{rpm}_{\text{steam},60} = \frac{120 \times 60}{2} = 3600\ \text{rpm}, \qquad \text{rpm}_{\text{hydro},60} = \frac{120 \times 60}{80} = 90\ \text{rpm}.$$

> [!check] Counting cycles
> At $75\ \text{rpm}$ the hydro rotor makes $75/60 = 1.25$ revolutions per second. Its $80$ poles form $40$ pole pairs, so $40 \times 1.25 = 50$ pole pairs pass each stator coil every second, giving exactly $f = 50\ \text{Hz}$.

### Phase EMF of a 2-pole turbo-alternator

The cylindrical rotor of a $2$-pole turbo-generator has diameter $D = 0.7\ \text{m}$ and active axial length $L_{\text{rotor}} = 7.0\ \text{m}$; the peak radial air-gap flux density is $B_{\text{peak}} = 0.8\ \text{T}$ (`S2-W18-21 Electric Machines 03` slides 3–4; Sharkh p. 14). It runs at $3000\ \text{rpm}$ with $N = 2$ turns per phase coil. The task is to show that the voltage is at $50\ \text{Hz}$, find $E_{\text{peak}}$ and $E_{\text{rms}}$, and state $e_A(t)$ and the star-connected line voltage $V_L$.

With $N_p = 2$ and $3000\ \text{rpm}$,

$$\begin{aligned}
f &= \frac{N_p\,\text{rpm}}{120} \\[4pt]
&= \frac{2 \times 3000}{120} \\[4pt]
&= 50\ \text{Hz}.
\end{aligned}$$

Convert the speed to $\omega$ and find the peripheral cutting velocity at $R = D/2 = 0.35\ \text{m}$:

$$\begin{aligned}
\omega &= \frac{2\pi\,\text{rpm}}{60} = \frac{2\pi \times 3000}{60} = 100\pi\ \text{rad}\,\text{s}^{-1} = 314.16\ \text{rad}\,\text{s}^{-1}, \\[4pt]
u &= \omega\,\frac{D}{2} = (314.16\ \text{rad}\,\text{s}^{-1})\left(\frac{0.7\ \text{m}}{2}\right) = 109.96\ \text{m}\,\text{s}^{-1}.
\end{aligned}$$

Each turn has two active sides of $7.0\ \text{m}$ cutting flux in series ($L = 2 L_{\text{rotor}} = 14.0\ \text{m}$), so

$$\begin{aligned}
E_{\text{peak}} &= N B_{\text{peak}} (2 L_{\text{rotor}}) \left(\frac{\omega D}{2}\right) \\[4pt]
&= 2 \times (0.8\ \text{T}) \times (2 \times 7.0\ \text{m}) \times (314.16\ \text{rad}\,\text{s}^{-1}) \times \left(\frac{0.7\ \text{m}}{2}\right) \\[4pt]
&= 2463.0\ \text{V} \approx 2463\ \text{V}.
\end{aligned}$$

With a sinusoidal air-gap field, the phase voltage and its RMS value are

$$\begin{aligned}
e_A(t) &= 2463\sin(2\pi \times 50\,t)\ \text{V} = 2463\sin(100\pi t)\ \text{V}, \\[4pt]
E_{\text{rms}} &= \frac{E_{\text{peak}}}{\sqrt{2}} = \frac{2463.0\ \text{V}}{\sqrt{2}} = 1741.6\ \text{V} \approx 1742\ \text{V}.
\end{aligned}$$

With the phases in star, the RMS line-to-line voltage is

$$V_L = \sqrt{3}\,E_{\text{rms}} = \sqrt{3} \times 1741.6\ \text{V} = 3016.6\ \text{V} \approx 3.02\ \text{kV}.$$

> [!check] Cross-check through the flux per pole
> For a sinusoidal gap field $B(\alpha) = B_{\text{peak}}\sin\alpha$ round a $2$-pole cylinder of radius $D/2$ and length $L_{\text{rotor}}$, integrating over one pole pitch ($\alpha \in [0, \pi]$) gives the flux per pole:
> $$\Phi_m = \int_0^\pi B_{\text{peak}}\sin\alpha\,\left(\frac{D}{2}\,\mathrm{d}\alpha\right) L_{\text{rotor}} = B_{\text{peak}} D L_{\text{rotor}} = (0.8\ \text{T})(0.7\ \text{m})(7.0\ \text{m}) = 3.920\ \text{Wb}.$$
> Then $E_{\text{peak}} = N \omega \Phi_m = 2 \times (314.16\ \text{rad}\,\text{s}^{-1}) \times (3.920\ \text{Wb}) = 2463.0\ \text{V}$. The motional formula $N B_{\text{peak}} L_{\text{rotor}} \omega D$ and the flux-linkage formula $N\omega\Phi_m$ are algebraically identical.

### 24-pole tidal-turbine generator

This is [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q4: Tidal turbine with a 24-pole, 3-phase PM generator at 150 rpm|Tutorial Sheet 5 Q4]]. A tidal turbine drives a $24$-pole, three-phase permanent-magnet synchronous generator directly at $150\ \text{rpm}$. Each phase has $24$ fully pitched coils in series, with $10$ turns per coil. The rotor has $D = 0.4\ \text{m}$ and $L_{\text{rotor}} = 0.4\ \text{m}$, and the peak air-gap flux density is $B_{\text{peak}} = 0.7\ \text{T}$. The stator is star-connected with $4$ wires (three lines and neutral) brought out to a balanced star-connected resistive load of $R = 5.0\ \Omega$ per phase; winding resistance and inductance are neglected. The task is the frequency, the RMS phase EMF, and the phase current, total power, power factor and neutral current.

With $N_p = 24$ and $150\ \text{rpm}$,

$$\begin{aligned}
f &= \frac{N_p\,\text{rpm}}{120} \\[4pt]
&= \frac{24 \times 150}{120} \\[4pt]
&= 30\ \text{Hz}.
\end{aligned}$$

The mechanical angular speed and peripheral velocity ($D/2 = 0.2\ \text{m}$) are

$$\begin{aligned}
\omega &= \frac{2\pi\,\text{rpm}}{60} = \frac{2\pi \times 150}{60} = 5\pi\ \text{rad}\,\text{s}^{-1} = 15.708\ \text{rad}\,\text{s}^{-1}, \\[4pt]
u &= \omega\,\frac{D}{2} = (5\pi\ \text{rad}\,\text{s}^{-1})(0.2\ \text{m}) = \pi\ \text{m}\,\text{s}^{-1} = 3.1416\ \text{m}\,\text{s}^{-1}.
\end{aligned}$$

Each coil has $N_{\text{coil}} = 10$ turns and is fully pitched, so both sides of length $L_{\text{rotor}} = 0.4\ \text{m}$ lie under opposite poles at once ($L = 2 L_{\text{rotor}} = 0.8\ \text{m}$ per turn). The peak EMF of one coil is

$$\begin{aligned}
E_{\text{coil,peak}} &= N_{\text{coil}} B_{\text{peak}} (2 L_{\text{rotor}}) u \\[4pt]
&= 10 \times (0.7\ \text{T}) \times (2 \times 0.4\ \text{m}) \times (3.1416\ \text{m}\,\text{s}^{-1}) \\[4pt]
&= 17.593\ \text{V}.
\end{aligned}$$

The $24$ coils of a phase are in series and sit in phase with one another under the poles ($N_{\text{phase}} = 24 \times 10 = 240$ turns in series), so their EMFs add directly:

$$\begin{aligned}
E_{\text{peak}} &= 24 \times E_{\text{coil,peak}} \\[4pt]
&= 24 \times 17.593\ \text{V} \\[4pt]
&= 422.23\ \text{V}.
\end{aligned}$$

With a sinusoidal air-gap field, the RMS phase EMF is

$$\begin{aligned}
E_{\text{rms}} &= \frac{E_{\text{peak}}}{\sqrt{2}} \\[4pt]
&= \frac{422.23\ \text{V}}{\sqrt{2}} \\[4pt]
&= 298.56\ \text{V} \approx 299\ \text{V}.
\end{aligned}$$

Each star-connected phase ($V_{\text{ph}} = E_{\text{rms}} = 298.56\ \text{V}$) feeds a $5.0\ \Omega$ load resistor, so the RMS phase and line current is

$$\begin{aligned}
I_{\text{ph}} = I_L &= \frac{E_{\text{rms}}}{R} \\[4pt]
&= \frac{298.56\ \text{V}}{5.0\ \Omega} \\[4pt]
&= 59.71\ \text{A}.
\end{aligned}$$

The total real power is

$$\begin{aligned}
P &= 3\,\frac{E_{\text{rms}}^2}{R} = 3 I_{\text{ph}}^2 R \\[4pt]
&= 3 \times \frac{(298.56\ \text{V})^2}{5.0\ \Omega} \\[4pt]
&= 53\,483\ \text{W} \approx 53.5\ \text{kW}.
\end{aligned}$$

The load is purely resistive ($Z_{\text{ph}} = 5.0 + j0\ \Omega$, $\phi = 0^\circ$), so voltage and current are in phase and the power factor is $\cos 0^\circ = 1$. Source and load are both balanced, so the three phase currents have equal magnitude ($59.71\ \text{A}$ RMS) and are $120^\circ$ apart; by KCL at the star point their instantaneous and phasor sum is zero, and $I_N = 0\ \text{A}$.

> [!check] Phasor check in Python
> With $\mathbf{E}_A = 298.56\angle 0^\circ\ \text{V}$, $\mathbf{E}_B = 298.56\angle(-120^\circ)\ \text{V}$ and $\mathbf{E}_C = 298.56\angle(-240^\circ)\ \text{V}$, dividing by $R = 5.0\ \Omega$ (`cmath.rect`) gives
> $$\mathbf{I}_A = 59.712 + j0.000\ \text{A}, \qquad \mathbf{I}_B = -29.856 - j51.712\ \text{A}, \qquad \mathbf{I}_C = -29.856 + j51.712\ \text{A}.$$
> Their sum is
> $$\mathbf{I}_N = (59.712 - 29.856 - 29.856) + j(0 - 51.712 + 51.712) = 0 + j0\ \text{A} \quad (|\mathbf{I}_N| = 2.3 \times 10^{-14}\ \text{A}).$$
> The line voltage and power are
> $$V_L = |\mathbf{E}_A - \mathbf{E}_B| = |298.56 - (-149.28 - j258.56)| = |447.84 + j258.56| = 517.12\ \text{V} = \sqrt{3}\,E_{\text{rms}},$$
> $$S = \mathbf{E}_A \mathbf{I}_A^* + \mathbf{E}_B \mathbf{I}_B^* + \mathbf{E}_C \mathbf{I}_C^* = 53\,483.5 + j0\ \text{VA}, \qquad \sqrt{3}\,V_L I_L \cos 0^\circ = \sqrt{3}(517.12\ \text{V})(59.712\ \text{A})(1) = 53\,483.5\ \text{W}.$$
> Every relation agrees to floating-point precision.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]
- Next: [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- Concepts: [[Synchronous Speed and Pole Number]] · [[Motional EMF in Electric Machines]] · [[Three-Phase Star and Delta Connections]]
- Worked problems: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q2, Q4)

## Sources

- `02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf` (§3.1–3.3 Synchronous Generators, pp. 10–16).
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf` (slides 4–14).
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 03 - Turbo Generators EMF - Lecture Slides.pdf` (slides 1–16).
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-01-27.txt` (ll. 44–98: Three Gorges hydroelectric generator overview).
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-04.txt` (ll. 1–332: synchronous speed, three-phase generator, $3000\ \text{rpm}$ turbo-generator example, cylindrical and salient-pole rotors, stator laminations, Roebel hollow transposed bars, and the moving-coil slip-ring generator).
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf` (Q2, Q4).
- E. Hughes, *Electrical and Electronic Technology*, Chs. 9, 31, 34.

## Self-study tasks

### Core

- [ ] Using the angle-addition and double-angle identities, prove that $i_N = i_A + i_B + i_C = 0$ and $p(t) = 3 E_m^2/(2R) = 3 E_{\text{rms}}^2/R$ for a balanced three-phase resistive load (`S2-W18-21 Electric Machines 02` slide 13, set as homework; Lecture 2025-02-04, ll. 86–91). → [[#Three-phase waveforms and their zero sum]]; [[#Proof of constant instantaneous power and the three-phase power formula]]
- [ ] Find the rotor speeds of a $2$-pole steam-turbine generator and an $80$-pole hydro generator on the $50\ \text{Hz}$ grid (`Electric Machines 02` slide 14; `Electric Machines 03` slide 2). → [[#Synchronous speeds of steam and hydro generators]]
- [ ] For the $2$-pole turbo-generator at $3000\ \text{rpm}$ ($D = 0.7\ \text{m}$, $L_{\text{rotor}} = 7.0\ \text{m}$, $B_{\text{peak}} = 0.8\ \text{T}$, $N = 2$), show that $f = 50\ \text{Hz}$ and find $E_{\text{peak}}$ and $E_{\text{rms}}$ (`Electric Machines 03` slides 3–4; Lecture 2025-02-04, ll. 97–227). → [[#Phase EMF of a 2-pole turbo-alternator]]
- [ ] Sketch the cross-section of a $2$-pole three-phase synchronous generator, plot the three phase voltages and the single-phase flux and EMF against rotor angle, and show the star and delta connections (Tutorial Sheet 5 Q2). → [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q2: Two-pole, three-phase synchronous generator|Tutorial 5 Q2]]; [[#2. Generator construction]]; [[#5. Three-phase windings, star and delta connections, and power]]
- [ ] Work all three parts of the $24$-pole, $150\ \text{rpm}$ tidal generator feeding a balanced $5\ \Omega$ star load (Tutorial Sheet 5 Q4). → [[#24-pole tidal-turbine generator]]; [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q4: Tidal turbine with a 24-pole, 3-phase PM generator at 150 rpm|Tutorial 5 Q4]]

### Further practice

- [ ] Reconnect the three $5.0\ \Omega$ resistors of the tidal example in delta across the same star-connected generator ($V_L = 517.12\ \text{V}$ RMS). Show that each resistor now sees $V_L$, draws $I_{\text{ph},\Delta} = 103.42\ \text{A}$ (line current $\sqrt{3}\,I_{\text{ph},\Delta} = 179.14\ \text{A}$), and that the total power triples to $P_\Delta = 3 \times 53.48\ \text{kW} = 160.45\ \text{kW}$ (suggested, not lecturer-set). → [[#24-pole tidal-turbine generator]]; [[#Star and delta connections]]

## Transcript and slide slips

### Missing division by 60 in the angular-speed note

> [!warning] Printed notes typo (Sharkh p. 14)
> Where: [[#3. Synchronous speed, pole number and electrical frequency]] and [[#Phase EMF of a 2-pole turbo-alternator]]
> In the turbo-generator example on p. 14, the explanatory sentence reads "Note that $\omega = 2\pi \times \text{rpm}$ in radians per second", omitting the division by $60\ \text{s}\,\text{min}^{-1}$. The correct conversion is $\omega = 2\pi \times \text{rpm}/60$, which the substitution on the next line ($\tfrac{3000}{60} \times 2\pi$) applies correctly.

### 2473 printed for 2463 V in the RMS calculation

> [!warning] Printed notes typo (Sharkh p. 14)
> Where: [[#Phase EMF of a 2-pole turbo-alternator]]
> Immediately after computing $E = 2463\ \text{V}$, the notes write $E_{\text{rms}} = 2473/\sqrt{2} = 1742\ \text{V}$. Since $2463/\sqrt{2} = 1741.6\ \text{V} \approx 1742\ \text{V}$, whereas $2473/\sqrt{2} = 1748.7\ \text{V}$, the numerator "2473" is a typo for $2463$. `S2-W18-21 Electric Machines 03` slide 4 prints the correct $2463/\sqrt{2} = 1742\ \text{V}$.

### Transcription artefacts in the 2025-02-04 recording

> [!warning] Speech-to-text artefacts (Lecture 2025-02-04, ll. 103, 166, 211, 246–281)
> Where: [[#2. Generator construction]] and [[#Phase EMF of a 2-pole turbo-alternator]]
> The automated transcription renders the turbo-generator dimensions "$0.7\ \text{m}$" and "$7\ \text{m}$" as "0.0.0, and the exact length is a centimeter" (l. 103), and "5 meter" or "0 from the ceiling divided by 2" (ll. 166, 211; for $0.7/2\ \text{m}$). It gives "salient-pole rotor" as "ceiling-pore rotor" or "cylinder pore rotor" (ll. 252, 255), "non-salient-pole rotor" as "non-cylindrical rotor" or "non-sinine pole router" (ll. 246, 258), and "eddy current" as "any current" (ll. 267, 281). Take numerical values and terminology from `S2-W18-21 Electric Machines 03` slides 3–13.
