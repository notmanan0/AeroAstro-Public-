---
title: "FEEG1004 C6 - DC Motor Characteristics and Speed Control"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 6
tags: [feeg1004, machines, dc-motor, torque-speed, shunt, series, chopper, pwm, h-bridge, brushless]
aliases: ["Electric Machines 07-08", "Torque-speed characteristic", "DC motor speed control", "Chopper", "H-bridge"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]", "[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
next_topics: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]"]
key_concepts: ["[[Torque-Speed Characteristics of DC Motors]]", "[[DC Motor Speed Control]]", "[[Flyback Diode]]", "[[Electric and Magnetic Loading]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf"]
---

# FEEG1004 C6 - DC Motor Characteristics and Speed Control

> [!abstract] Summary
> - Eliminate the current from $V = K\omega + iR_a$ and $T = Ki$ to get the **torque–speed line** of a PM or separately excited motor:
> $$\omega = \frac{V}{K} - \frac{R_a}{K^2}T$$
>   It has a no-load speed of $V/K$ and a stall torque of $KV/R_a$.
> - Wound-field machines (shunt, series, compound) have other shapes; the series motor gives huge starting torque.
> - **Speed control** means changing $V$ (efficiently, with a PWM **chopper**), adding $R$ (wastefully) or weakening the field.
> - **Direction** control uses an **H-bridge**. **Brushless** motors replace the commutator with electronics.

## Key Concepts
- [[Torque-Speed Characteristics of DC Motors]] · [[DC Motor Speed Control]] · [[Flyback Diode]] · [[Electric and Magnetic Loading]]

---

## 1. Wound-field connections (Sharkh §4.5)
Large machines use **field windings** instead of magnets. The field current sets $\Phi$, and hence $K$.

| Connection | Field fed from | Characteristic |
|---|---|---|
| Separate excitation / PM | independent supply | straight drooping line: nearly constant speed |
| Shunt | parallel with the armature, from the same supply | as separate excitation, for constant $V$ |
| Series | the armature current itself | $\Phi\propto i$, so $T\propto i^2$ and $\omega\propto1/\sqrt T$: huge starting torque, **runaway at no load** |
| Compound | both | in between |

![[ee_c6_torque_speed_types.png|760]]

## 2. The PM / separately excited characteristic
- From $V = K\omega + iR_a$ and $T = Ki$:
  - **no-load speed** $\omega_0 = V/K$;
  - **stall torque** $T_s = KV/R_a$;
  - slope $-R_a/K^2$.
- The nominal operating point sits on the line where the motor torque equals the load torque.

> [!example] Exam 2021 lift: 1:20 gearbox, 0.4 m drum, 200 kg cabin, 300 kg counterweight, 1 m/s
> - **300 kg passengers**:
>   - The net load is $(200 + 300 - 300)g$ = 1962 N, so $P$ = 1962 W.
>   - Drum $\omega = 1/0.2$ = 5 rad/s, so the motor turns at 100 rad/s. $T$ = 19.62 N m.
>   - With 20 A: $K = T/I$ = **0.981 N m/A**. From $102 = 20R_a + 0.981(100)$: **$R_a$ = 0.195 Ω**.
> - **500 kg passengers** at the same speed:
>   - The net load is 400 kg, so $T$ = 39.24 N m and $I$ = 40 A.
>   - $V = 40(0.195) + 98.1$ = **105.9 V**.

## 3. Speed control (Machines 08)
Rearrange: $\omega = (V - iR_{tot})/K$. There are three levers:
- **(A) armature voltage** $V$;
- **(B) series resistance**;
- **(C) field current** (field weakening, changing $\Phi$).

![[ee_c6_speed_control.png|900]]

> [!example] Series resistance to halve the speed (Machines 08)
> - A PM motor on 230 V draws 20 A with $K$ = 1 and $R_a$ = 0.5 Ω, so $\omega$ = 220 rad/s.
> - Half speed (110 rad/s) at **constant load torque** means the current stays 20 A. Then $230 = 20(0.5 + R) + 110$, so **R = 5.5 Ω**.
> - The resistor burns $I^2R$ = 2.2 kW of the 4.6 kW input. This is why resistive control is inefficient.

**DC chopper (PWM)**:
- A transistor (MOSFET/IGBT) switches the supply on and off above ~15 kHz. The motor sees an average voltage $\delta V_S$, where $\delta = t_{on}/(t_{on} + t_{off})$ is the **duty ratio**.
- The armature inductance smooths the current.
- The **freewheeling diode** carries the current when the switch is off (answer b in the slides, and not an optional extra). Without it, $L\,di/dt$ would destroy the switch ([[Flyback Diode]]).

> [!example] Chopper-driven fan: $R_a$ = 0.1 Ω, 12 V battery, 0.6 V switch and diode drops, $P\propto\omega^3$
> - **100 % duty**: 3600 rpm (377 rad/s) at 15 A with $V$ = 11.4 V.
>   - $K = (11.4 - 15\times0.1)/377$ = **0.0263 V s/rad** (notes: 0.026).
>   - $T = K(15)$ = 0.394 N m.
>   - Fan law: $T = k\omega^2$, so $k$ = 2.77 × 10⁻⁶ N m s².
> - **40 % duty**: $V = 0.4\times11.4$ = 4.56 V.
>   - Substituting $I = k\omega^2/K$ into $V = IR_a + K\omega$ gives $\dfrac{R_ak}{K}\omega^2 + K\omega - 4.56 = 0$.
>   - The positive root is **ω ≈ 163 rad/s ≈ 1556 rpm**. The notes, rounding K to 0.026, get 165 rad/s ≈ 1575 rpm.
> - **80 % duty waveforms**: $V$ alternates between 11.4 V (switch on) and −0.6 V (diode freewheeling); the current is continuous with a small triangular ripple.
>
> ![[ee_c6_chopper_fan.png|880]]

**Loads**: constant-torque loads (lifts) need current independent of speed. Fan and pump loads have $T\propto\omega^2$ and $P\propto\omega^3$.

## 4. Direction control and brushless machines
- **H-bridge** (four-quadrant): T1 + T4 on drive one direction; T3 + T2 on reverse the polarity. Never switch both transistors of one leg on together: that is a shoot-through short.
- **Brushless DC and steppers**: commutators arc, wear and need brush replacement. **Semiconductor switches** do the commutation electronically instead, which needs a controller circuit.
- **Induction motors** (AC) are the rugged industrial workhorse. They are mentioned only for context.

## Year 2 bridge
- **Servo actuators** (control-surface actuators, gimbals) are DC or brushless motors in a speed/position loop. The chopper is the "plant input" of the controller ([[SESA2027 B1 - Control System Fundamentals and PID Control]], [[PID Controller]]).
- **Reaction-wheel drives** are brushless, H-bridge / three-phase inverter driven, with speed limits from $V/K_E$ ([[Reaction Wheels and Momentum Dumping]]).
- **PWM** comes from a comparator against a triangle wave ([[Op-Amp Comparator]]) or from a microcontroller timer ([[Shift Registers and Binary Counters]]).

## Links
- Previous: [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]] · Next: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]
- Worked problems: [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] (Q5, Q6)

## Sources
- Sharkh/Niu machines notes §4.4–4.6; Electric Machines 07–08 slides (including the 2021 exam lift question); Hughes Ch. 40–42.
