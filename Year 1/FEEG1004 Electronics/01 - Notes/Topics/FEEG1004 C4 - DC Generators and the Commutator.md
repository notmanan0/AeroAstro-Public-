---
title: "FEEG1004 C4 - DC Generators and the Commutator"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 4
tags: [feeg1004, machines, dc-generator, commutator, emf-constant, tachogenerator]
aliases: ["Electric Machines 05", "DC generator", "Commutator", "E = K_E omega"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
next_topics: ["[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]"]
key_concepts: ["[[Commutator]]", "[[Back EMF and Torque Constants]]", "[[Motional EMF in Electric Machines]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 05 - DC Generators - Lecture Slides.pdf"]
---

# FEEG1004 C4 - DC Generators and the Commutator

> [!abstract] Summary
> Replace the slip rings of a rotating-coil AC generator with a **split ring (commutator)**: the output is rectified mechanically and becomes unidirectional.
> - Many coils on many segments smooth the output to nearly constant DC with $E = K_E\omega$.
> - From the conductor count: $K_E = \dfrac{ZN_p\Phi}{2\pi a}$.
> - Delivering current creates an opposing torque (Lenz). The equivalent circuit is $E$ in series with $R_a$ (and $L_a$).

## Key Concepts
- [[Commutator]] · [[Back EMF and Torque Constants]] · [[Motional EMF in Electric Machines]]

---

## 1. From AC to DC
- A rotating coil has $\Phi = \Phi_m\cos\omega t$, so $e = N\omega\Phi_m\sin\omega t$ (AC).
- A **commutator** (a split ring with brushes) reverses the coil's connection every half-turn. The terminal voltage is $|e|$: unidirectional but pulsating.
- **More coils and segments** let the brushes always pick the coil near its peak. The ripple shrinks, e.g. 29 % with 2 coils and 13 % with 3 in the idealised figure.
- Because $E\propto\omega$, a small DC generator makes a **tachogenerator** (speed sensor).

![[ee_c4_commutator_emf.png|820]]

## 2. The EMF constant (Sharkh §4.3.1)
- Take $Z$ armature conductors in $a$ parallel paths, so $Z/a$ are in series.
- Each conductor cuts flux at $u = \omega D/2$: $e_c = BL\omega D/2$.
- Flux per pole: $\Phi = \pi BLD/N_p$ (the rotor surface area divided among the poles).

$$
E = \frac{Z}{a}\cdot\frac{BL\omega D}{2} = \frac{ZN_p\Phi}{2\pi a}\,\omega = K_E\,\omega,\qquad K_E = \frac{ZN_p\Phi}{2\pi a}\ \ [\mathrm{V\,s/rad}]
$$

## 3. Generator loading and the equivalent circuit
- A generator supplying current has coil current that makes its own poles. These are dragged towards like stator poles, giving a **counter-torque** (Lenz). More electrical output means a harder shaft.
- **General equivalent circuit**: EMF $E$ in series with $R_a$ and $L_a$, driving the load.
- With **constant current**, $L_a\,di/dt = 0$ and the terminal voltage is

$$
V = E - iR_a
$$

  The terminal voltage is below the EMF (Tutorial 6 Q2 contrasts this with a motor, where $V > E$).

![[ee_c5_dc_machine_circuits.png|900]]

> [!example] How to measure $K_E$ (Machines 05 question; Tutorial 6 Q1)
> - Spin the machine at a known speed with its terminals **open** (no current, so no $iR_a$ drop) and read $E$: $K_E = E/\omega$.
> - Tutorial 6 Q1: 10 V at 1000 rpm (104.7 rad/s) gives $K_E$ = **0.0955 V s/rad**.

## Year 2 bridge
- **Tachogenerators** and back-EMF sensing give speed feedback in servo loops ([[SESA2027 B1 - Control System Fundamentals and PID Control]], [[Measurement Chain]]).
- The commutator's wear and arcing motivate **brushless** machines with electronic commutation: reaction wheels, drones ([[FEEG1004 C6 - DC Motor Characteristics and Speed Control]], [[Reaction Wheels and Momentum Dumping]]).

## Links
- Previous: [[FEEG1004 C3 - Transformers and AC Power Transmission]] · Next: [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Worked problems: [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] (Q1)

## Sources
- Sharkh/Niu machines notes §4–4.3.1; Electric Machines 05 slides; Hughes Ch. 39.
