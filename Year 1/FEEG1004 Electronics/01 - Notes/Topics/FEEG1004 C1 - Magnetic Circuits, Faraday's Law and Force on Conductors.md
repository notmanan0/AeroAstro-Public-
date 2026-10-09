---
title: "FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 1
tags: [feeg1004, machines, magnetic-circuit, mmf, reluctance, faraday, lorentz, motional-emf]
aliases: ["Electric Machines 01", "Magnetic field quantities", "E = NBLu", "Machines introduction"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]"]
next_topics: ["[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
key_concepts: ["[[Magnetomotive Force and Reluctance]]", "[[Motional EMF in Electric Machines]]", "[[Faraday's Law and Lenz's Law]]", "[[Lorentz Force]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 01 - Intro and Faraday - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf"]
---

# FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors

> [!abstract] Summary
> Electric machines (generators and motors) run on two laws from [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]], rewritten in machine-friendly forms:
> - **Generator effect**: a conductor of length $L$ cutting flux at speed $u$ has EMF $\mathcal E = NBLu$ (Fleming's **right** hand).
> - **Motor effect**: a current-carrying conductor in a field feels $F = BiL$ (Fleming's **left** hand).
>
> Fields are produced and steered by **magnetic circuits**: mmf $\mathcal F = Ni$ drives flux through a reluctance, $\mathcal F = \mathcal R\Phi$. This is the magnetic twin of Ohm's law.

## Key Concepts
- [[Magnetomotive Force and Reluctance]] · [[Motional EMF in Electric Machines]] · [[Faraday's Law and Lenz's Law]] · [[Lorentz Force]]

---

## 1. Magnetic field quantities (Sharkh §2)
| Quantity | Symbol and definition | Unit |
|---|---|---|
| Flux | $\Phi$ | Wb (= V s) |
| Flux linkage | $\lambda = N\Phi$ | Wb-turn |
| Flux density | $B = \Phi/A$ (uniform) | T |
| Magnetomotive force | $\mathcal F = Ni$ | A-turns |
| Field intensity | $H$, with $\oint H\,dl = Ni$; $\sum H_kl_k = Ni$ on a piecewise path | A/m |
| Reluctance | $\mathcal F = \mathcal R\Phi$ | A/Wb |

- The field direction comes from the **right-hand rule**: fingers curl with the current, thumb points to N, where the flux emerges.
- More turns or more current give more mmf, and hence more flux.
- A steel core has low reluctance, so the flux follows it (transformer cores, machine stators).

> [!example] Toroid (Machines 02 slides): $I$ = 4 A, $N$ = 100, $\mathcal R = 1.68\times10^6$ A/Wb, $A$ = 500 mm², $l$ = 0.4 m
> - mmf $\mathcal F = NI$ = **400 A-turns**.
> - $\Phi = \mathcal F/\mathcal R$ = **0.238 mWb**, so $B = \Phi/A$ = **0.476 T**.
> - $H = \mathcal F/l$ = **1000 A/m**.
> - The flux circulates around the ring in the direction given by the grip rule.

## 2. Faraday's law in machine form
- The general law $\mathcal E = -N\,d\Phi/dt$ is hard to apply when coils move. Consider instead a coil side of length $L$ moving at $u$ across a uniform field $B$.
- The linked flux is $\Phi = BLx$, and $u = -dx/dt$:

$$
\mathcal E = -N\frac{d(BLx)}{dt} = NBLu
$$

- Only conductors that **cut flux** contribute. The end connections to the voltmeter do not.
- The direction follows Fleming's **right-hand** rule, with Lenz's law behind it.

![[ee_c1_motor_generator_effect.png|900]]

## 3. The force on a conductor

$$
F = BiL
$$

- The direction follows Fleming's **left-hand** rule.
- **Field-line picture**: the applied field and the wire's circular field add on one side and cancel on the other. The "stretched rubber bands" of flux push the wire towards the weak side (Sharkh Fig. 2.5).

**Interaction principle**:
- In every machine, generator and motor action happen **simultaneously**.
- A generator delivering current feels a braking force; a spinning motor generates a back-EMF.
- That is energy conversion, and Lenz's law guarantees it.

## 4. What the machines part covers
| Topic note | Machine |
|---|---|
| [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] | rotating-magnet AC generator, poles, speed, three-phase |
| [[FEEG1004 C3 - Transformers and AC Power Transmission]] | transformer, why AC |
| [[FEEG1004 C4 - DC Generators and the Commutator]] | commutator, $E = K_E\omega$ |
| [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]] | $T = K_Ti$, equivalent circuit, efficiency |
| [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]] | torque–speed, field connections, choppers, H-bridge |

## Year 2 bridge
- **Magnetorquers** and **reaction wheels** in attitude control are exactly the motor effect ([[Attitude Sensors and Torquers]], [[Reaction Wheels and Momentum Dumping]], [[SESA2024 06 - Attitude Control]]).
- **Electric propulsion** (Hall thrusters) uses a radial magnetic field to trap electrons: the Lorentz force again ([[Electric (Ion) Propulsion]]).
- **Inductive transducers** vary the reluctance of a magnetic circuit to sense displacement: $L = N^2/\mathcal R$ ([[Linear Variable Differential Transformer]]).

## Links
- Background: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · Next: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- Worked problems: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q1, Q3)

## Sources
- Sharkh/Niu, *An Introduction to Electric Machines*, §1–2; Electric Machines 01–02 slides (X. Niu); Hughes, *Electrical and Electronic Technology*, Ch. 6–8.
