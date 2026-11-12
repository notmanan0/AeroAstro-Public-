---
title: "FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 5
tags: [feeg1004, machines, dc-motor, torque-constant, back-emf, efficiency, equivalent-circuit]
aliases: ["Electric Machines 06", "DC motor", "T = K_T i", "Back EMF", "KT = KE"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-02-14 (ll. 189–673); FEEG1004 Lecture 2025-02-20 (ll. 56–65, 120–145)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C4 - DC Generators and the Commutator]]"]
next_topics: ["[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
key_concepts: ["[[Back EMF and Torque Constants]]", "[[Lorentz Force]]", "[[Electric and Magnetic Loading]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]]"]
sources:
  - "02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"
  - "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 06 - DC Motors Torque - Lecture Slides.pdf"
  - "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-02-14.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2025-02-20.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf"
---

# FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency

> [!abstract] Summary
> A DC supply $V$ driving current $i$ into a brushed DC machine makes it a motor, in which one constant appears twice: each conductor carrying $i_c = i/a$ across the field gives a total torque $T = K_T i$, and the spinning rotor induces an opposing back EMF $E' = K_E \omega$, with $K_T = K_E = \dfrac{Z}{a}\,B L \dfrac{D}{2} = \dfrac{Z N_p \Phi}{2\pi a}$ in SI units ($\text{N}\,\text{m}\,\text{A}^{-1} \equiv \text{V}\,\text{s}\,\text{rad}^{-1}$). In steady state $V = E' + i R_a = K_E \omega + i R_a$, so the input $P_{\text{in}} = V i$ splits into copper loss $P_{\text{cu}} = i^2 R_a$ and electromagnetic power $P_{\text{em}} = E' i = T \omega$, and subtracting the rotational losses $P_{\text{rot}}$ (friction, windage and core loss) leaves $P_{\text{out}} = P_{\text{em}} - P_{\text{rot}}$ and $\eta = P_{\text{out}} / P_{\text{in}}$. In terms of magnetic loading $B$, electric loading $A = \dfrac{Z i_c}{\pi D}$ and rotor volume $V_R = \dfrac{\pi D^2 L}{4}$, the torque is $T = 2 B A V_R$, so motor size scales with the torque $T = P/\omega$ rather than with power, and a fast compact motor driving a slow load through a step-down gearbox is much smaller and lighter than a direct drive.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a DC motor's geometry, supply, current or test data and asks for torque, speed, back EMF, power flow, efficiency or rotor size.
> - **Assumptions:** steady state ($\mathrm{d}i/\mathrm{d}t = 0$); constant flux (PM or fixed field current); brushes at the maximum-torque position; $\omega$ in $\text{rad}\,\text{s}^{-1}$ so that $K_T = K_E$.
> - **Method:** 1. Find $K_T = K_E$ from geometry or from a test ($K_E = E/\omega$). 2. Get $T_{\text{em}} = K_T i$. 3. Get $E' = V - iR_a$, then $\omega = E'/K_E$. 4. Compute $P_{\text{in}} = Vi$, $P_{\text{cu}} = i^2R_a$, $P_{\text{em}} = E'i$, $P_{\text{out}} = P_{\text{em}} - P_{\text{rot}}$. 5. Find $\eta = P_{\text{out}}/P_{\text{in}}$ and check that the losses and output add up to $P_{\text{in}}$.
> - **Common mistakes:** using rpm in $E' = K_E\omega$, which makes $E'$ or $T$ wrong by a factor of $9.55$; forgetting $P_{\text{rot}}$, so that the electromagnetic torque is reported as the shaft torque.
> - **Practise:** [[#Torque, speed and efficiency of a 230 V motor]] · [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q2: Running light as a motor at 1000 rpm: 10.2 V, 1 A|Tutorial 6 Q2]]

Any brushed DC machine can run either as a generator or as a motor. When an external DC supply forces current into the armature, the Lorentz force on the rotor conductors gives a driving torque that accelerates the shaft.

The rotation that follows induces a Faraday back EMF that opposes the supply voltage. The difference between the supply and the back EMF, across the small armature resistance, sets how much current the motor draws, so the speed settles where the current gives just enough torque for the load.

Both effects come from the same conductors in the same field, which is why the torque constant and the back-EMF constant of [[FEEG1004 C4 - DC Generators and the Commutator]] are equal.

## 1. Torque production and commutation

Replacing the load resistor of the DC generator of [[FEEG1004 C4 - DC Generators and the Commutator]] with a DC voltage source $V$ (a battery or DC power supply) across the brushes drives current $i$ into the armature.

Consider a cross-section of a two-pole DC motor with the stator North pole on the left and the South pole on the right, so that the field $\mathbf{B}$ points horizontally from left to right across the rotor bore. By Fleming's left-hand rule ($F_c = B i_c L$), a conductor under the left-hand North pole carrying current into the page ($\otimes$) feels a downward Lorentz force, while a conductor under the right-hand South pole carrying current out of the page ($\odot$) feels an upward force. The downward forces on the left half and the upward forces on the right half form a couple that drives the rotor anticlockwise.

As a conductor on the left half rotates past the bottom neutral plane into the right half under the South pole, its commutator segment slides past the stationary brush and the current in that conductor reverses, from $\otimes$ to $\odot$. The commutator therefore ensures that every conductor under the North pole carries current into the page ($\otimes$) and every conductor under the South pole carries current out of the page ($\odot$), whatever the rotor angle. The electromagnetic torque is unidirectional and continuous.

### Maximum-torque and zero-torque brush positions

The current pattern set up by the brushes creates a **rotor magnetic field** whose axis lies along the brush axis. When the brushes are placed so that the current reverses at the top and bottom neutral planes between the stator poles, all conductors under the North pole carry $\otimes$ and all under the South pole carry $\odot$. By the right-hand grip rule, the rotor's magnetic axis is then vertical, at $90^\circ$ to the horizontal stator field. Every conductor's tangential force acts in the same rotational sense, giving the maximum torque per ampere.

If the brushes were instead rotated by $90^\circ$, so that all conductors in the upper half of the rotor carried $\otimes$ and all in the lower half carried $\odot$, the rotor's magnetic axis would be horizontal and aligned with the stator field. The downward forces on the upper-left conductors would turn the rotor one way and the equal downward forces on the upper-right conductors would turn it the other, so their torques cancel; the same happens with the upward forces on the lower half. The net torque is zero. Practical DC motors fix the brushes at the $90^\circ$ maximum-torque position.

## 2. Torque constant, back EMF and why they are equal

### Electromagnetic torque

Consider an armature with $Z$ active axial conductors in $a$ parallel paths, on a rotor of diameter $D$ (radius $r = D/2$) and active length $L$, in an average radial air-gap flux density $B$. The supply feeds total current $i$ into the positive brush, and it divides equally among the $a$ paths, so each conductor carries

$$i_c = \frac{i}{a}$$

Each conductor of length $L$ lies perpendicular to the radial field and feels a tangential Lorentz force

$$F_c = B i_c L$$

Acting at radius $r = \dfrac{D}{2}$, this force gives a torque about the shaft axis of force times lever arm:

$$T_c = F_c r = B i_c L\,\frac{D}{2}$$

With the brushes at the maximum-torque position, all $Z$ conductors produce torque in the same direction. Summing over them and substituting $i_c = i/a$ gives the total electromagnetic torque $T$ (or $T_{\text{em}}$):

$$\begin{aligned}
T &= \sum_{k=1}^{Z} T_c \\[4pt]
&= Z B i_c L\,\frac{D}{2} \\[4pt]
&= Z B \left(\frac{i}{a}\right) L\,\frac{D}{2} \\[4pt]
&= \left(\frac{Z}{a}\,B L \frac{D}{2}\right) i \\[4pt]
&= K_T\,i
\end{aligned}$$

where the **torque constant** (in $\text{N}\,\text{m}\,\text{A}^{-1}$) is

$$K_T = \frac{Z}{a}\,B L \frac{D}{2}$$

Using the flux per pole $\Phi = \dfrac{\pi B L D}{N_p}$, so that $B L D = \dfrac{N_p \Phi}{\pi}$ (derived in [[FEEG1004 C4 - DC Generators and the Commutator#2. Armature EMF equation|C4 §2]]), the torque constant can also be written

$$\begin{aligned}
K_T &= \frac{Z}{a}\,\frac{B L D}{2} \\[4pt]
&= \frac{Z}{a}\,\frac{1}{2}\left(\frac{N_p \Phi}{\pi}\right) \\[4pt]
&= \frac{Z N_p \Phi}{2\pi a}
\end{aligned}$$

### Back EMF

Once the torque spins the rotor at $\omega\ \text{rad}\,\text{s}^{-1}$, the $Z$ conductors cut the radial field at peripheral velocity $u = \omega r = \omega D/2$. Faraday's law still applies when the machine runs as a motor, so each conductor has a motional EMF

$$e_c' = B L u = B L \omega\,\frac{D}{2}$$

By Fleming's right-hand rule (or Lenz's law), a conductor moving in the direction of the motor force $\mathbf{F}$ inside the field $\mathbf{B}$ has an EMF $e_c'$ directed against the externally driven current $i_c$. Summing the $\dfrac{Z}{a}$ series conductors along each path gives the total opposing voltage across the armature, the **back EMF** $E'$ (also written $E$):

$$\begin{aligned}
E' &= \sum_{k=1}^{Z/a} e_c' \\[4pt]
&= \frac{Z}{a}\,e_c' \\[4pt]
&= \left(\frac{Z}{a}\,B L \frac{D}{2}\right)\omega \\[4pt]
&= K_E\,\omega
\end{aligned}$$

where the **back-EMF constant** (sometimes written $K_E'$) is

$$K_E = \frac{Z}{a}\,B L \frac{D}{2} = \frac{Z N_p \Phi}{2\pi a} \quad \bigl[\text{V}\,\text{s}\,\text{rad}^{-1}\bigr]$$

### Why the two constants are equal

Comparing the expressions derived from $F_c = B i_c L$ and $e_c' = B L u$ shows directly that both constants are the same combination of machine parameters:

$$K_T = \frac{Z}{a}\,B L \frac{D}{2} = \frac{Z N_p \Phi}{2\pi a} = K_E$$

Conservation of energy gives the same result without the geometry. When current $i$ is forced into the motor against $E' = K_E \omega$, the electrical power converted to mechanical form, with the copper loss in $R_a$ counted separately, is $P_{\text{em,elec}} = E' i$. On the mechanical side of the air gap, the torque $T = K_T i$ turning the rotor at $\omega$ does work at the rate $P_{\text{em,mech}} = T \omega$. In steady state the magnetic field neither creates nor destroys energy, so the two powers are equal:

$$\begin{aligned}
E' i &= T \omega \\[4pt]
(K_E \omega)\,i &= (K_T i)\,\omega \\[4pt]
K_E &= K_T
\end{aligned}$$

The SI units agree: $1\ \text{V}\,\text{s}\,\text{rad}^{-1} = 1\ (\text{J}\,\text{C}^{-1})\,\text{s} = 1\ \text{J}\,\text{A}^{-1} = 1\ \text{N}\,\text{m}\,\text{A}^{-1}$.

> [!warning] The equality needs consistent SI units
> $K_T = K_E$ holds only with $\omega$ in radians per second, $T$ in $\text{N}\,\text{m}$, $E'$ in $\text{V}$ and $i$ in $\text{A}$. If speed is substituted in $\text{rpm}$ instead of $\text{rad}\,\text{s}^{-1}$, the conversion factor $\dfrac{2\pi}{60} = \dfrac{\pi}{30} \approx 0.10472\ \text{rad}\,\text{s}^{-1}/\text{rpm}$ is lost and $E'$ or $T$ is wrong by a factor of $9.55$.

## 3. Equivalent circuit, power flow and efficiency

### Dynamic and steady-state equivalent circuit

As in the DC generator of [[FEEG1004 C4 - DC Generators and the Commutator]], the motor's armature has series resistance $R_a$ and series inductance $L_a$ along with the speed-dependent back EMF $E' = K_E \omega$. The difference is the direction of $i$. In a motor, the supply voltage $V$ is larger than $E'$ and drives current into the positive terminal against the back EMF, much as a charger drives current into a rechargeable battery of voltage $E'$.

![[ee_c5_dc_machine_circuits.png|900]]

KVL around the loop in the direction of the input current $i(t)$ gives

$$V = E' + i R_a + L_a\frac{\mathrm{d}i}{\mathrm{d}t} = K_E \omega + i R_a + L_a\frac{\mathrm{d}i}{\mathrm{d}t}$$

At steady speed and constant torque, $i$ is constant ($\mathrm{d}i/\mathrm{d}t = 0$), the inductor drop $L_a\,\mathrm{d}i/\mathrm{d}t$ is zero, and the circuit reduces to $R_a$ in series with $E' = K_E \omega$:

$$V = E' + i R_a = K_E \omega + i R_a \iff i = \frac{V - K_E \omega}{R_a}$$

The back EMF regulates the armature current automatically. At no load the mechanical load torque is zero, so the rotor accelerates until $E' = K_E \omega$ almost equals $V$. Only a small no-load current $i_0 = (V - E')/R_a$ then flows, enough to produce the small torque $K_T i_0$ that overcomes internal friction and windage. When a mechanical load is applied, it slows the rotor slightly and reduces $E'$. Because $R_a$ is small, the increase in $V - E'$ raises the current $i = (V - E')/R_a$ and the torque $T = K_T i$ until $T$ matches the new load torque.

> [!warning] Stall current
> At starting or stall the rotor is stationary ($\omega = 0$), so there is no back EMF ($E' = 0$). The full supply voltage $V$ appears across the small armature resistance and draws a large **stall (starting) current** $i_{\text{stall}} = V / R_a$, which can overheat the winding or trip the supply unless current-limiting control or soft-starting is used ([[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]).

### Power flow and efficiency

Multiplying the steady-state equation $V = E' + i R_a$ through by $i$ traces the power from the electrical terminals to the shaft:

$$\underbrace{V i}_{P_{\text{in}}} = \underbrace{i^2 R_a}_{P_{\text{cu}}} + \underbrace{E' i}_{P_{\text{em}} = T_{\text{em}}\omega}$$

The DC source supplies the **electrical input power**

$$P_{\text{in}} = V i$$

Part of it is dissipated as Joule heat in the armature resistance, the **armature copper loss**

$$P_{\text{cu}} = i^2 R_a$$

The rest is the **electromagnetic (air-gap) power** converted from electrical to mechanical form on the rotor:

$$P_{\text{em}} = P_{\text{in}} - P_{\text{cu}} = E' i = (K_E \omega) i = (K_T i) \omega = T_{\text{em}}\,\omega$$

As the rotor spins, part of $P_{\text{em}}$ is lost inside the machine to bearing and brush friction, aerodynamic windage (air drag on the rotor), and iron core losses (eddy-current and hysteresis heating in the rotating laminations). Calling the sum of these **rotational losses** at speed $\omega$ $P_{\text{rot}}$, the useful mechanical shaft output power and the net shaft torque delivered to the load are

$$P_{\text{out}} = P_{\text{em}} - P_{\text{rot}} = E' i - P_{\text{rot}} = V i - i^2 R_a - P_{\text{rot}}, \qquad T_{\text{shaft}} = \frac{P_{\text{out}}}{\omega} = T_{\text{em}} - \frac{P_{\text{rot}}}{\omega}$$

The **efficiency** is the ratio of shaft output power to electrical input power:

$$\eta = \frac{P_{\text{out}}}{P_{\text{in}}} = \frac{E' i - P_{\text{rot}}}{V i} = \frac{V i - i^2 R_a - P_{\text{rot}}}{V i} \quad (\text{or } \times 100\%)$$

![[ee_c5_dc_motor_performance.png|760]]

## 4. Torque, rotor volume and step-down gearboxes

The torque a motor must produce sets its physical size, as the conductor torque equation $T = Z B i_c L \dfrac{D}{2}$ shows once two machine-design quantities are introduced. The **electric loading** $A$ ($\text{A}\,\text{m}^{-1}$) is the total axial ampere-conductors $Z i_c$ around the rotor divided by the circumference $\pi D$:

$$A = \frac{Z i_c}{\pi D} \iff Z i_c = \pi D A$$

The **rotor volume** $V_R$ ($\text{m}^3$) is the volume of the active rotor cylinder of diameter $D$ and length $L$:

$$V_R = \frac{\pi D^2 L}{4}$$

Substituting $Z i_c = \pi D A$ into the torque and factoring out $V_R$:

$$\begin{aligned}
T &= Z B i_c L\,\frac{D}{2} \\[4pt]
&= B \,(Z i_c)\,\frac{D L}{2} \\[4pt]
&= B \,(\pi D A)\,\frac{D L}{2} \\[4pt]
&= 2 B \left(\frac{Z i_c}{\pi D}\right) \left(\frac{\pi D^2 L}{4}\right) \\[4pt]
&= 2 B A V_R
\end{aligned}$$

Both loadings are tightly constrained by materials across machines with similar cooling. The **magnetic loading** $B$, $0.5\text{--}0.8\ \text{T}$ average air-gap flux density and at most $1.5\ \text{T}$ in the steel teeth, is limited by the magnetic saturation of silicon steel. The electric loading $A$, $20\text{--}70\ \text{kA}\,\text{m}^{-1}$ depending on whether the machine is naturally air-cooled, fan-cooled or liquid-cooled, is limited by the heat flux the winding insulation can dissipate without burning out.

Since $B$ and $A$ are roughly the same whatever the machine size, $T = 2 B A V_R$ gives two scaling laws. First, rotor volume and mass are proportional to torque ($V_R \propto T$), not to power: a $100\ \text{N}\,\text{m}$ motor needs roughly ten times the rotor volume and mass of a $10\ \text{N}\,\text{m}$ motor with the same cooling, even if both have the same power rating. Second, substituting $T = \dfrac{P}{\omega}$ into $V_R = \dfrac{T}{2 B A}$ gives

$$V_R = \frac{P}{2 B A \omega} \propto \frac{P}{\omega}$$

For a given output power, the rotor volume is inversely proportional to speed. Driving a slow, high-torque load such as a lift drum, robot joint or conveyor directly at its low speed $\omega_{\text{load}}$ would need a large, heavy and expensive motor. A small, fast motor running at $\omega_m = n \omega_{\text{load}}$ needs only $T_m = T_{\text{load}}/n$, and so $1/n$ of the rotor volume. It is coupled to the load through an $n:1$ **step-down gearbox** (ratios up to $1000:1$), which divides the speed by $n$ and multiplies the torque by $n$.

## Worked examples

### Torque, speed and efficiency of a 230 V motor

A permanent-magnet DC motor draws a steady armature current $i = 20\ \text{A}$ from a $V = 230\ \text{V}$ supply. It has rotor diameter $D = 0.2\ \text{m}$, active length $L = 0.2\ \text{m}$ and average radial air-gap flux density $B = 0.5\ \text{T}$. The armature has $Z = 200\ \text{conductors}$ in $a = 2\ \text{parallel paths}$ and resistance $R_a = 0.5\ \Omega$, and the friction, windage and iron rotational losses total $P_{\text{rot}} = 200\ \text{W}$. Find (a) $K_T$, $K_E$ and the electromagnetic torque $T_{\text{em}}$; (b) the back EMF $E'$ and the speed in $\text{rad}\,\text{s}^{-1}$ and $\text{rpm}$; (c) $P_{\text{em}}$, the shaft output power $P_{\text{out}}$, the net shaft torque $T_{\text{shaft}}$, the input power $P_{\text{in}}$ and the efficiency $\eta$.

(a) With $Z = 200$, $a = 2$, $B = 0.5\ \text{T}$, $L = 0.2\ \text{m}$ and $D = 0.2\ \text{m}$, the constants in SI units are

$$\begin{aligned}
K_T = K_E &= \frac{Z}{a}\,B L \frac{D}{2} \\[4pt]
&= \frac{200}{2} \times (0.5\ \text{T}) \times (0.2\ \text{m}) \times \left(\frac{0.2\ \text{m}}{2}\right) \\[4pt]
&= 100 \times 0.5 \times 0.2 \times 0.1 \\[4pt]
&= 1.00\ \text{N}\,\text{m}\,\text{A}^{-1} \quad (= 1.00\ \text{V}\,\text{s}\,\text{rad}^{-1})
\end{aligned}$$

The electromagnetic torque is then

$$\begin{aligned}
T_{\text{em}} &= K_T i \\[4pt]
&= (1.00\ \text{N}\,\text{m}\,\text{A}^{-1})(20\ \text{A}) \\[4pt]
&= 20.0\ \text{N}\,\text{m}
\end{aligned}$$

Equivalently, each conductor in the $a = 2$ paths carries $i_c = i/a = 20\ \text{A}/2 = 10\ \text{A}$, so $T_{\text{em}} = Z B i_c L (D/2) = 200(0.5)(10)(0.2)(0.1) = 20.0\ \text{N}\,\text{m}$.

(b) From the steady-state circuit $V = E' + i R_a$ with $V = 230\ \text{V}$, $i = 20\ \text{A}$ and $R_a = 0.5\ \Omega$:

$$\begin{aligned}
E' &= V - i R_a \\[4pt]
&= 230\ \text{V} - (20\ \text{A})(0.5\ \Omega) \\[4pt]
&= 230\ \text{V} - 10\ \text{V} \\[4pt]
&= 220\ \text{V}
\end{aligned}$$

With $E' = K_E \omega$ and $K_E = 1.00\ \text{V}\,\text{s}\,\text{rad}^{-1}$, the speed is

$$\begin{aligned}
\omega &= \frac{E'}{K_E} = \frac{220\ \text{V}}{1.00\ \text{V}\,\text{s}\,\text{rad}^{-1}} = 220\ \text{rad}\,\text{s}^{-1} \\[6pt]
\text{rpm} &= \frac{60\,\omega}{2\pi} = \frac{60 \times 220}{2\pi} = 2100.85\ \text{rpm} \approx 2101\ \text{rpm}
\end{aligned}$$

(c) The electromagnetic power converted on the rotor is

$$P_{\text{em}} = T_{\text{em}}\,\omega = (20.0\ \text{N}\,\text{m})(220\ \text{rad}\,\text{s}^{-1}) = 4400\ \text{W}$$

Subtracting $P_{\text{rot}} = 200\ \text{W}$ of friction, windage and core loss gives the shaft output power and net shaft torque:

$$\begin{aligned}
P_{\text{out}} &= P_{\text{em}} - P_{\text{rot}} = 4400\ \text{W} - 200\ \text{W} = 4200\ \text{W} \\[4pt]
T_{\text{shaft}} &= \frac{P_{\text{out}}}{\omega} = \frac{4200\ \text{W}}{220\ \text{rad}\,\text{s}^{-1}} = 19.09\ \text{N}\,\text{m}
\end{aligned}$$

The $230\ \text{V}$ supply provides

$$P_{\text{in}} = V i = (230\ \text{V})(20\ \text{A}) = 4600\ \text{W}$$

so the efficiency is

$$\begin{aligned}
\eta &= \frac{P_{\text{out}}}{P_{\text{in}}} \times 100\% \\[4pt]
&= \frac{4200\ \text{W}}{4600\ \text{W}} \times 100\% \\[4pt]
&= 91.30\% \approx 91\%
\end{aligned}$$

> [!check] Power balance
> Of the $P_{\text{in}} = V i = 4600\ \text{W}$ entering the terminals, the armature copper loss is $P_{\text{cu}} = i^2 R_a = (20\ \text{A})^2 (0.5\ \Omega) = 200\ \text{W}$ ($4.35\%$ of $P_{\text{in}}$). The air-gap power is $E' i = (220\ \text{V})(20\ \text{A}) = 4400\ \text{W}$, equal to $T_{\text{em}}\,\omega = (20.0\ \text{N}\,\text{m})(220\ \text{rad}\,\text{s}^{-1})$. The rotational loss $P_{\text{rot}} = 200\ \text{W}$ is another $4.35\%$, and the shaft output $P_{\text{out}} = T_{\text{shaft}}\,\omega = 4200\ \text{W}$ is $91.30\%$. Together
> $$P_{\text{cu}} + P_{\text{rot}} + P_{\text{out}} = 200\ \text{W} + 200\ \text{W} + 4200\ \text{W} = 4600\ \text{W} = P_{\text{in}}$$

### No-load and pump-load tests

In the open-circuit test of [[FEEG1004 C4 - DC Generators and the Commutator#Open-circuit test for the EMF constant|C4]] (Tutorial Sheet 6 Q1) the machine gave $E = 10.0\ \text{V}$ at $1000\ \text{rpm}$ ($\omega = 104.72\ \text{rad}\,\text{s}^{-1}$), so $K_E = K_T = 0.09549\ \text{V}\,\text{s}\,\text{rad}^{-1}$ (Tutorial Sheet 6 Q2–Q3; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q2: Running light as a motor at 1000 rpm: 10.2 V, 1 A|Tutorial 6 Q2]]). (a) With nothing on its shaft, the machine is run as a motor from a variable DC supply adjusted until the shaft turns at $1000\ \text{rpm}$, and the terminals read $V_0 = 10.2\ \text{V}$ and $i_0 = 1.0\ \text{A}$ (Q2). Explain why the voltage is higher than the $10.0\ \text{V}$ of Q1 at the same speed, and find $R_a$ and the no-load rotational loss $P_{\text{rot}}$ at $1000\ \text{rpm}$. (b) The motor then drives a small water pump at $1000\ \text{rpm}$ and draws $i = 5.0\ \text{A}$ (Q3). Find the supply voltage $V$, the output power $P_{\text{out}}$, the net shaft torque $T_{\text{shaft}}$ and the efficiency $\eta$.

(a) The speed is still $1000\ \text{rpm}$ ($\omega = 104.72\ \text{rad}\,\text{s}^{-1}$) and the magnet flux is constant, so the back EMF $E' = K_E \omega$ is still $10.0\ \text{V}$. Running as a motor, though, the supply must drive $i_0 = 1.0\ \text{A}$ into the armature against $E'$ and through $R_a$, so $V_0 = E' + i_0 R_a > E'$. In Q1 the machine was on open circuit with $i = 0$, so $V_{\text{oc}} = E = 10.0\ \text{V}$. The extra $0.2\ \text{V}$ at the terminals is the resistive drop $i_0 R_a$:

$$\begin{aligned}
R_a &= \frac{V_0 - E'}{i_0} \\[4pt]
&= \frac{10.2\ \text{V} - 10.0\ \text{V}}{1.0\ \text{A}} \\[4pt]
&= 0.20\ \Omega
\end{aligned}$$

At no load $P_{\text{out}} = 0\ \text{W}$, so all of the input $P_{\text{in},0} = V_0 i_0 = (10.2\ \text{V})(1.0\ \text{A}) = 10.2\ \text{W}$ goes into internal losses. The copper loss at no load is

$$P_{\text{cu},0} = i_0^2 R_a = (1.0\ \text{A})^2 (0.20\ \Omega) = 0.20\ \text{W}$$

and the electromagnetic power that overcomes friction, windage and iron loss at $1000\ \text{rpm}$ is

$$P_{\text{rot}} = E' i_0 = (10.0\ \text{V})(1.0\ \text{A}) = 10.0\ \text{W}$$

(b) The speed is still $1000\ \text{rpm}$, so the back EMF remains $E' = 10.0\ \text{V}$ and the speed-dependent rotational loss remains $P_{\text{rot}} = 10.0\ \text{W}$. KVL at $i = 5.0\ \text{A}$ gives

$$\begin{aligned}
V &= E' + i R_a \\[4pt]
&= 10.0\ \text{V} + (5.0\ \text{A})(0.20\ \Omega) \\[4pt]
&= 10.0\ \text{V} + 1.0\ \text{V} \\[4pt]
&= 11.0\ \text{V}
\end{aligned}$$

The power flow and efficiency follow:

$$\begin{aligned}
P_{\text{in}} &= V i = (11.0\ \text{V})(5.0\ \text{A}) = 55.0\ \text{W} \\[4pt]
P_{\text{cu}} &= i^2 R_a = (5.0\ \text{A})^2 (0.20\ \Omega) = 5.0\ \text{W} \\[4pt]
P_{\text{em}} &= E' i = (10.0\ \text{V})(5.0\ \text{A}) = 50.0\ \text{W} \\[4pt]
P_{\text{out}} &= P_{\text{em}} - P_{\text{rot}} = 50.0\ \text{W} - 10.0\ \text{W} = 40.0\ \text{W} \\[4pt]
\eta &= \frac{P_{\text{out}}}{P_{\text{in}}} \times 100\% = \frac{40.0\ \text{W}}{55.0\ \text{W}} \times 100\% = 72.73\% \approx 72.7\%
\end{aligned}$$

The electromagnetic and shaft torques are

$$T_{\text{em}} = K_T i = (0.09549\ \text{N}\,\text{m}\,\text{A}^{-1})(5.0\ \text{A}) = 0.4775\ \text{N}\,\text{m}, \qquad T_{\text{shaft}} = \frac{P_{\text{out}}}{\omega} = \frac{40.0\ \text{W}}{104.72\ \text{rad}\,\text{s}^{-1}} = 0.3820\ \text{N}\,\text{m}$$

> [!check] Power balance in both tests
> In the no-load test ($i_0 = 1.0\ \text{A}$),
> $$P_{\text{in},0} = 10.2\ \text{W} = P_{\text{cu},0} + P_{\text{rot}} + P_{\text{out},0} = 0.2\ \text{W} + 10.0\ \text{W} + 0.0\ \text{W} = 10.2\ \text{W}$$
> In the pump test ($i = 5.0\ \text{A}$),
> $$P_{\text{in}} = 55.0\ \text{W} = P_{\text{cu}} + P_{\text{rot}} + P_{\text{out}} = 5.0\ \text{W} + 10.0\ \text{W} + 40.0\ \text{W} = 55.0\ \text{W}$$
> On the mechanical side, $(T_{\text{em}} - T_{\text{shaft}})\omega = (0.47746 - 0.38197)\ \text{N}\,\text{m} \times 104.72\ \text{rad}\,\text{s}^{-1} = 10.0\ \text{W} = P_{\text{rot}}$.

### Rotor volume with and without a step-down gearbox

This example illustrates Tutorial Sheet 6 Q4–Q5 ([[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q4: Show T = 1/2 B Z i_c D L = 2 B A V_R|Tutorial 6 Q4]]). A winch needs a continuous shaft power $P_{\text{out}} = 1000\ \text{W}$ at a low speed $\omega_{\text{load}} = 10\ \text{rad}\,\text{s}^{-1}$ ($95.5\ \text{rpm}$). Two motors are compared, both designed with magnetic loading $B = 0.60\ \text{T}$ and electric loading $A = 25\ \text{kA}\,\text{m}^{-1}$, and both running at $V = 100\ \text{V}$, $i = 10.5\ \text{A}$ ($R_a = 0.4535\ \Omega$, so $P_{\text{cu}} = 50\ \text{W}$, with negligible rotational losses). Option A is a direct-drive motor coupled to the winch shaft at $\omega_A = 10\ \text{rad}\,\text{s}^{-1}$. Option B runs at $\omega_B = 100\ \text{rad}\,\text{s}^{-1}$ ($954.9\ \text{rpm}$) and drives the winch through an ideal $10:1$ step-down gearbox. Find the motor torque $T$ and rotor volume $V_R$ for each.

From $P_{\text{em}} = P_{\text{out}} = T \omega = 1000\ \text{W}$, the direct-drive motor needs

$$T_A = \frac{P_{\text{out}}}{\omega_A} = \frac{1000\ \text{W}}{10\ \text{rad}\,\text{s}^{-1}} = 100.0\ \text{N}\,\text{m}$$

and the geared motor needs

$$T_B = \frac{P_{\text{out}}}{\omega_B} = \frac{1000\ \text{W}}{100\ \text{rad}\,\text{s}^{-1}} = 10.0\ \text{N}\,\text{m}$$

The rotor volume follows from $T = 2 B A V_R \implies V_R = \dfrac{T}{2 B A}$, with $2 B A = 2 \times (0.60\ \text{T}) \times (25 \times 10^3\ \text{A}\,\text{m}^{-1}) = 3.0 \times 10^4\ \text{N}\,\text{m}^{-2}$. For the direct drive,

$$V_{R,A} = \frac{100.0\ \text{N}\,\text{m}}{3.0 \times 10^4\ \text{N}\,\text{m}^{-2}} = 3.333 \times 10^{-3}\ \text{m}^3 = 3333\ \text{cm}^3$$

and for the geared motor,

$$V_{R,B} = \frac{10.0\ \text{N}\,\text{m}}{3.0 \times 10^4\ \text{N}\,\text{m}^{-2}} = 3.333 \times 10^{-4}\ \text{m}^3 = 333.3\ \text{cm}^3$$

Running the motor $10\times$ faster through a $10:1$ step-down gearbox reduces the active rotor volume, and with it the copper and iron mass, by a factor of $10$.

> [!check] Power balance across motor and gearbox
> In both options the supply provides $P_{\text{in}} = V i = (100\ \text{V})(10.5\ \text{A}) = 1050\ \text{W}$, of which $P_{\text{cu}} = i^2 R_a = (10.5\ \text{A})^2 (0.4535\ \Omega) = 50.0\ \text{W}$ is armature heat, leaving $E' = V - i R_a = 95.24\ \text{V}$ and $P_{\text{em}} = E' i = 1000\ \text{W}$. For option A, $K_{T,A} = \dfrac{100\ \text{N}\,\text{m}}{10.5\ \text{A}} = 9.524\ \text{N}\,\text{m}\,\text{A}^{-1} = \dfrac{95.24\ \text{V}}{10\ \text{rad}\,\text{s}^{-1}} = K_{E,A}$, and $P_{\text{out}} = T_A \omega_A = (100\ \text{N}\,\text{m})(10\ \text{rad}\,\text{s}^{-1}) = 1000\ \text{W}$. For option B, $K_{T,B} = \dfrac{10\ \text{N}\,\text{m}}{10.5\ \text{A}} = 0.9524\ \text{N}\,\text{m}\,\text{A}^{-1} = \dfrac{95.24\ \text{V}}{100\ \text{rad}\,\text{s}^{-1}} = K_{E,B}$, the motor shaft power is $T_B \omega_B = (10\ \text{N}\,\text{m})(100\ \text{rad}\,\text{s}^{-1}) = 1000\ \text{W}$, and after the $10:1$ gearbox ($T_{\text{load}} = 10 T_B = 100\ \text{N}\,\text{m}$, $\omega_{\text{load}} = \omega_B / 10 = 10\ \text{rad}\,\text{s}^{-1}$) the output is $T_{\text{load}} \omega_{\text{load}} = 1000\ \text{W} = P_{\text{in}} - P_{\text{cu}}$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Prerequisites: [[FEEG1004 C4 - DC Generators and the Commutator]]
- Next: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Concepts: [[Back EMF and Torque Constants]] · [[Lorentz Force]] · [[Electric and Magnetic Loading]]
- Worked problems: [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] (Q1–Q5)
- Combining $V(t) = L_a\dfrac{\mathrm{d}i}{\mathrm{d}t} + R_a i(t) + K_E \omega(t)$ with Newton's second law for rotor inertia $J$ and viscous damping $b$, $J\dfrac{\mathrm{d}\omega}{\mathrm{d}t} + b\omega(t) = K_T i(t)$, gives the second-order transfer function $G(s) = \dfrac{\Omega(s)}{V(s)} = \dfrac{K_T}{(L_a s + R_a)(J s + b) + K_T K_E}$ ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]], [[Transfer Function]]).
- A spacecraft reaction wheel uses a brushless DC motor ($T = K_T i$) to accelerate a flywheel and apply an equal and opposite attitude torque. As $\omega$ approaches the no-load limit $V_{\text{bus}}/K_E$, $E' = K_E \omega$ approaches $V_{\text{bus}}$ and the current and torque fall away; this **wheel saturation** is cleared by momentum dumping with thrusters or magnetorquers ([[Reaction Wheels and Momentum Dumping]], [[SESA2024 06 - Attitude Control]]).
- Drone and RC brushless motors quote a speed constant $K_V$ in $\text{rpm}\,\text{V}^{-1}$, the reciprocal of $K_E$ converted to rpm: $K_V\ [\text{rpm}\,\text{V}^{-1}] = \dfrac{60}{2\pi\,K_E\ [\text{V}\,\text{s}\,\text{rad}^{-1}]} = \dfrac{9.549}{K_E}$.

## Sources

- `02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf` (§4.1 DC Motor, Fig. 4.6; §4.3.2 Torque and $K_T$; §4.4 Relationship Between Torque and Size; worked $230\ \text{V}$ motor example p. 26; pp. 22–27)
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 06 - DC Motors Torque - Lecture Slides.pdf` (slides 3–9; slide 4 maximum- and zero-torque brush positions; slide 9 the $230\ \text{V}$, $20\ \text{A}$ motor example)
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf` (slides 1–4; slide 4 $T = 2BAV_R$, loadings and gearbox argument)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-14.txt` (ll. 189–673: DC motor torque, commutator action, $T = K_T i$, back EMF $E' = K_E \omega$, $K_T = K_E$, equivalent circuit, and $230\ \text{V}$, $20\ \text{A}$ motor worked example)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-20.txt` (ll. 56–65, 120–145: gearbox demonstration and motor equivalent-circuit review)
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf` (Q1–Q5)
- E. Hughes, *Electrical and Electronic Technology*, Chs. 39–40, 42

## Self-study tasks

### Core

- [ ] Work through every part of the $230\ \text{V}$, $20\ \text{A}$ motor example ($D = L = 0.2\ \text{m}$, $B = 0.5\ \text{T}$, $Z = 200$, $a = 2$, $R_a = 0.5\ \Omega$, $P_{\text{rot}} = 200\ \text{W}$) (`Electric Machines 06` slide 9; Sharkh p. 26; Lecture 2025-02-14, ll. 530–671). → [[#Torque, speed and efficiency of a 230 V motor]]
- [ ] Using $K_E = 0.0955\ \text{V}\,\text{s}\,\text{rad}^{-1}$ from Q1, find $R_a$ and the no-load losses from the $10.2\ \text{V}$, $1\ \text{A}$ test at $1000\ \text{rpm}$, then the terminal voltage and efficiency driving a pump at $1000\ \text{rpm}$ and $5\ \text{A}$ (Tutorial Sheet 6 Q2–Q3). → [[#No-load and pump-load tests]]; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q2: Running light as a motor at 1000 rpm: 10.2 V, 1 A|Tutorial 6 Q2–Q3]]
- [ ] Derive $T = 2 B \left(\dfrac{Z i_c}{\pi D}\right)\left(\dfrac{\pi D^2 L}{4}\right) = 2 B A V_R$ from $F_c = B i_c L$, and explain why a step-down gearbox is used between a motor and a slow load (Tutorial Sheet 6 Q4–Q5; `Electric Machines 07` slide 4). → [[#4. Torque, rotor volume and step-down gearboxes]]; [[#Rotor volume with and without a step-down gearbox]]; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q4: Show T = 1/2 B Z i_c D L = 2 B A V_R|Tutorial 6 Q4–Q5]]

### Further practice

- [ ] For the $230\ \text{V}$ motor ($R_a = 0.5\ \Omega$, $P_{\text{rot}} = 200\ \text{W}$), verify that at $i = 20\ \text{A}$ the variable copper loss $i^2 R_a = 200\ \text{W}$ equals the fixed rotational loss, which puts the operating point at the peak of the efficiency curve in `ee_c5_dc_motor_performance.png` ($\eta = 91.3\%$); then check $\eta$ at a heavy overload of $i = 60\ \text{A}$ ($T = 60\ \text{N}\,\text{m}$, $\omega = 200\ \text{rad}\,\text{s}^{-1}$, $P_{\text{cu}} = 1800\ \text{W}$, $\eta = 85.5\%$) (suggested, not lecturer-set). → [[#Power flow and efficiency]]; [[#Torque, speed and efficiency of a 230 V motor]]

## Transcript and slide slips

> [!warning] Stray factor $\pi r^2$ in Eq. (4.15) (`S2 Electric Machines Notes - Sharkh.pdf`, p. 26)
> Where: [[#Electromagnetic torque]]
> On page 26 of the printed notes, Equation (4.15) for the torque constant is printed as "$K_T = \dfrac{z}{a} B L \dfrac{D}{2} = \pi r^2 \dfrac{Z N_p}{2 a \pi}\varphi$". The factor of $\pi r^2$ in front of $\dfrac{Z N_p}{2 a \pi}\varphi$ is a typographical insertion; substituting $B L D = \dfrac{N_p \Phi}{\pi}$ into $\dfrac{Z}{a} B L \dfrac{D}{2}$ gives $K_T = \dfrac{Z N_p \Phi}{2\pi a}$ (as correctly printed on `S2-W18-21 Electric Machines 07` slide 3).

> [!warning] Missing division by $\pi$ in the "6600 rpm" result (`S2 Electric Machines Notes - Sharkh.pdf`, p. 26)
> Where: [[#Torque, speed and efficiency of a 230 V motor]]
> In the worked motor example on page 26 of the printed notes, converting $\omega = 220\ \text{rad}\,\text{s}^{-1}$ to revolutions per minute is written as "$\text{rpm} = \dfrac{60\omega}{2\pi} = \dfrac{60 \times 220}{2\pi} = 6600\ \text{rpm}$". Because $\dfrac{60 \times 220}{2} = 6600$, the division by $\pi$ was omitted when evaluating the fraction; the true speed is $\dfrac{6600}{\pi} = 2100.85\ \text{rpm} \approx 2101\ \text{rpm}$.

> [!warning] Unit slip "20~70 kA/mm" for electric loading (`S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf`, slide 4)
> Where: [[#4. Torque, rotor volume and step-down gearboxes]]
> On slide 4 of `S2-W18-21 Electric Machines 07`, the typical range of electric loading $A = \dfrac{Z i_c}{\pi D}$ is printed as "$20\sim 70\ \text{kA/mm}$". The correct unit is $20\text{--}70\ \text{kA}\,\text{m}^{-1}$ (kiloamperes per metre of rotor periphery, equivalent to $20\text{--}70\ \text{A}\,\text{mm}^{-1}$).
