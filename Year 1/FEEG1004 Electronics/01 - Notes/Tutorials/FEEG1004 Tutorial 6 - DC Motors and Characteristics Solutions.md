---
title: "FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions"
module: "FEEG1004 Electronics"
type: tutorial
stream: "Part C: Electric Machines"
tags: [feeg1004, tutorial-solutions, dc-motor, back-emf, efficiency, torque, gearbox]
sheet: "Problems on Electric Machines 2"
theory_notes: ["[[FEEG1004 C4 - DC Generators and the Commutator]]", "[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]", "[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
key_concepts: ["[[Back EMF and Torque Constants]]", "[[Electric and Magnetic Loading]]", "[[Torque-Speed Characteristics of DC Motors]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf"]
---

# FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions

> [!abstract] Sheet Info
> One small PM DC motor is characterised in stages: $K_E$ from an open-circuit test, $R_a$ and the rotational losses from a no-load test, then the efficiency on load. The sheet ends with the torque–size relation, the case for a gearbox and the shunt and series characteristics. No answers are printed; the numerical results here were checked by computation.

## Theory Links
- [[FEEG1004 C4 - DC Generators and the Commutator]] · [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]] · [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]] · [[Back EMF and Torque Constants]]

## Q1: Back-EMF constant from an open-circuit test
On open circuit no current flows, so there is no $iR_a$ drop and the terminal voltage equals the EMF. At 1000 rpm, $\omega = 1000\times2\pi/60$ = 104.7 rad/s, so

$$K_E = \frac{E}{\omega} = \frac{10}{104.7} = 0.0955\ \mathrm{V\,s/rad}\ (= K_T = 0.0955\ \mathrm{N\,m/A})$$

## Q2: Running light as a motor at 1000 rpm: 10.2 V, 1 A
As a motor, the supply must provide the back EMF plus the armature drop, $V = E + iR_a$, whereas a generator gives $V = E - iR_a$. The speed is unchanged, so $E$ is still 10 V (it depends only on ω), and the extra 0.2 V is the $iR_a$ drop. The armature resistance is therefore $R_a = 0.2/1$ = **0.2 Ω**.

The input power is $P_{in} = 10.2\times1$ = 10.2 W, of which $i^2R_a$ = 0.2 W is copper loss. The remaining electromagnetic power $Ei$ = 10 W produces no useful output, so all of it goes into friction, windage and core losses at 1000 rpm.

## Q3: Driving a pump at 1000 rpm with 5 A
The speed is the same, so $E$ = 10 V and $V = E + iR_a = 10 + 5(0.2)$ = **11 V**.

The input power is $P_{in} = 11\times5$ = 55 W. Copper loss takes $5^2\times0.2$ = 5 W, leaving $P_{em} = Ei$ = 50 W, and subtracting the 10 W rotational loss (unchanged at the same speed) leaves $P_{out}$ = 40 W. The efficiency is $\eta = 40/55$ = **72.73 %**.

The net shaft torque is $P_{out}/\omega = (50 - 10)/104.72 = 0.3820\ \mathrm{N\,m}$ ($\approx 0.38\ \mathrm{N\,m}$), while the electromagnetic torque is $K_Ti = 0.09549\times 5 = 0.4775\ \mathrm{N\,m}$ ($\approx 0.48\ \mathrm{N\,m}$).

## Q4: Show T = 1/2 B Z i_c D L = 2 B A V_R
Each of the $Z$ conductors carries $i_c$ in a field $B$ over length $L$, so it feels $F_c = Bi_cL$. At radius $D/2$ this gives a torque $T_c = Bi_cLD/2$, and the commutator keeps all the conductors under the poles acting in the same sense, so their torques add:

$$
T = \frac{1}{2}BZi_cDL
$$

With the **electric loading** $A = Zi_c/(\pi D)$ (current per metre of rotor circumference) and the **rotor volume** $V_R = \pi D^2L/4$, the same torque factorises into the form printed on the sheet:

$$
T = 2B\left(\frac{Zi_c}{\pi D}\right)\left(\frac{\pi D^2L}{4}\right) = 2BAV_R\ ✔
$$

## Q5: Why use a step-down gearbox with a slow load?
$B$ is limited by steel saturation and $A$ by cooling, so both are roughly the same across machines and torque is proportional to rotor volume. A slow load needs high torque at low speed, and driving it directly would need a large, heavy and expensive motor.

Since $P = T\omega$, a motor running $n$ times faster needs only $1/n$ of the torque, and hence about $1/n$ of the volume. The gearbox then multiplies the torque by $n$, less the gear losses. For example, 1 kW at 10 rad/s needs 100 N m from a direct drive, or 10 N m from a motor at 100 rad/s through 10:1 gearing.

## Q6: Torque–speed characteristics, shunt vs series
In a shunt motor the field winding is across the supply, so $\Phi$ is constant and

$$\omega = \frac{V}{K} - \frac{R_a}{K^2}T,$$

a straight line with a slight droop. The speed is nearly constant, with a finite no-load speed $V/K$, which suits fans, pumps and machine tools.

In a series motor the field carries the armature current, so $\Phi\propto i$ and $T\propto i^2$. Neglecting resistance, $E\propto\Phi\omega\propto i\omega$ is fixed by the supply, which gives $\omega\propto1/\sqrt T$. The starting torque is very high, but the speed rises steeply as the load falls and the motor runs away at no load. It suits traction and engine starters, loads that are never removed.

![[ee_c6_torque_speed_types.png|760]]

## Sources
- FEEG1004 Problems on Electric Machines 2; derived and verified numerically.
