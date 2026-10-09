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

## Definition

> [!note] Definition
> From $\omega = (V - iR_{tot})/K$, speed is controlled by:
> - the armature **voltage** $V$ (a PWM chopper gives average $\delta V_S$, where $\delta = t_{on}/T$);
> - added series **resistance** (wasteful);
> - the **field** flux $\Phi$ (field weakening).
>
> Direction is reversed by reversing $V$ with an **H-bridge**.

## Explanation
- **Chopper**: a MOSFET or IGBT switched above ~15 kHz. The armature inductance smooths the current; the **freewheeling diode** carries it during off-time.
- **Series resistance**: at constant torque the current is fixed, so the resistor dissipates $I^2R$. Halving speed can waste about half the input.
- **H-bridge**: T1 + T4 for forward, T2 + T3 for reverse. Never turn on both switches in one leg.
- **Brushless DC / steppers**: electronic commutation, no brush wear; they need a controller.

![[ee_c6_speed_control.png|700]]

## Examples
- 230 V, 20 A, $K$ = 1, $R_a$ = 0.5 Ω: 5.5 Ω halves the speed at constant torque and wastes 2.2 kW.
- Fan on a chopper: 40 % duty gives about 163 rad/s ≈ 1556 rpm.

## Related
- Topic notes: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Concepts: [[Flyback Diode]] · [[Transistor as a Switch]] · [[Op-Amp Comparator]] (PWM)
- Year 2: [[PID Controller]] · [[Reaction Wheels and Momentum Dumping]]

## Sources
- Machines 08 slides; Sharkh notes §4.6
