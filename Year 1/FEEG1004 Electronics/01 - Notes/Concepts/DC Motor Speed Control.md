---
title: "DC Motor Speed Control"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["chopper", "PWM", "duty cycle", "H-bridge", "series resistance control", "field weakening", "brushless DC"]
tags: [feeg1004, concept, machines, dc-motor, power-electronics]
status: complete
parent_lectures: ["[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
related_concepts: ["[[Torque-Speed Characteristics of DC Motors]]", "[[Flyback Diode]]", "[[Transistor as a Switch]]"]
sources: ["02 - Sources/S2 Machines/S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# DC Motor Speed Control

The speed of a DC motor follows from its steady equivalent circuit as $\omega=(V-iR_{tot})/K$, so it can be set by the armature voltage $V$, by the total armature-circuit resistance $R_{tot}$, or by the field flux $\Phi$ through $K$. The direction is reversed by reversing $V$ with an **H-bridge**.

Voltage control is the efficient method. A **chopper** switches a MOSFET or IGBT at above about $15\ \mathrm{kHz}$, so the motor sees an average voltage $\delta V_S$, where the duty cycle is $\delta=t_{on}/T$. The armature inductance smooths the current, and a freewheeling diode carries it during the off-time.

Adding series resistance also lowers the speed, but wastefully. At constant torque the current is fixed, so the extra resistor dissipates $I^2R$; halving the speed can waste about half the input power. Reducing the field flux (**field weakening**) raises the speed above its base value.

In an H-bridge, switches T1 and T4 conduct for forward rotation and T2 and T3 for reverse. Both switches in one leg must never be on together, since that shorts the supply. Brushless DC motors and steppers use electronic commutation, so there is no brush wear, but they need a controller.

![[ee_c6_speed_control.png|700]]

For a $230\ \mathrm V$, $20\ \mathrm A$ motor with $K=1$ and $R_a=0.5\ \Omega$, adding $5.5\ \Omega$ halves the speed at constant torque and wastes $2.2\ \mathrm{kW}$. A fan on a chopper at $40\ \%$ duty runs at about $163\ \mathrm{rad/s}\approx1556\ \mathrm{rpm}$.

## Related

- [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- [[Flyback Diode]] · [[Transistor as a Switch]] · [[Op-Amp Comparator]] (PWM)
- Year 2: [[PID Controller]] · [[Reaction Wheels and Momentum Dumping]]
- Sources: Machines 08 slides; Sharkh notes §4.6
