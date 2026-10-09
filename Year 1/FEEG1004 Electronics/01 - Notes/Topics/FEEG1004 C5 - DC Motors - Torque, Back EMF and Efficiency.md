---
title: "FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 5
tags: [feeg1004, machines, dc-motor, torque-constant, back-emf, efficiency, equivalent-circuit]
aliases: ["Electric Machines 06", "DC motor", "T = K_T i", "Back EMF", "KT = KE"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C4 - DC Generators and the Commutator]]"]
next_topics: ["[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
key_concepts: ["[[Back EMF and Torque Constants]]", "[[Lorentz Force]]", "[[Electric and Magnetic Loading]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 06 - DC Motors Torque - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf"]
---

# FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency

> [!abstract] Summary
> Feed current into a DC machine and it becomes a motor. The same physics gives the same constant twice:
> $$T = K_Ti,\qquad E = K_E\omega,\qquad K_T = K_E = \frac{ZN_p\Phi}{2\pi a}\ \text{(SI units)}$$
> - Steady equivalent circuit: $V = E + iR_a = K_E\omega + iR_a$.
> - Power flow: electrical input $Vi$ → armature copper loss $i^2R_a$ → electromagnetic power $Ei = T\omega$ → minus friction, windage and core losses → shaft output.

## Key Concepts
- [[Back EMF and Torque Constants]] · [[Lorentz Force]] · [[Electric and Magnetic Loading]]

---

## 1. How a DC motor makes torque
- Current in the armature under the stator poles gives a force $F = BiL$ on each conductor.
- The **commutator** reverses each conductor's current as it passes from one pole to the next. The current under a given pole is always in the same direction, so the torque is **unidirectional**.
- **Maximum torque** occurs with the rotor and stator fields at right angles; **zero torque** when they are aligned. The commutator holds the fields near 90° all the time.

## 2. Torque constant (Sharkh §4.3.2)
Each conductor carries $i_c = i/a$ and feels $F_c = Bi_cL$ at radius $D/2$:

$$
T = Z\,B\frac{i}{a}L\frac{D}{2} = \frac{ZN_p\Phi}{2\pi a}\,i = K_T\,i
$$

This uses the same flux-per-pole substitution as the EMF. Hence $K_T = K_E$ in SI units (N m/A ≡ V s/rad). This is a direct consequence of energy conservation: $Ei = T\omega$.

## 3. Back EMF and the equivalent circuit
- The spinning armature also generates an EMF, called the **back EMF** because it opposes the supply: $E = K_E\omega$.
- **General**: $V = E + iR_a + L_a\,di/dt$. **Constant current**: $V = K_E\omega + iR_a$.
- **No load**: $i$ is small, so $\omega\approx V/K_E$. **Stall** ($\omega = 0$): $E = 0$ and the current is limited only by $R_a$, so $i = V/R_a$, which is huge. Big motors need soft-starting.

![[ee_c5_dc_machine_circuits.png|900]]

## 4. Power flow and efficiency
$$
P_{in} = Vi,\qquad P_{cu} = i^2R_a,\qquad P_{em} = Ei = T\omega,\qquad P_{out} = P_{em} - P_{rot},\qquad \eta = \frac{P_{out}}{P_{in}}
$$

> [!example] Sharkh / Machines 06 example: 230 V, 20 A, $D = L$ = 0.2 m, $B$ = 0.5 T, $Z$ = 200, $a$ = 2, $R_a$ = 0.5 Ω, 200 W rotational loss
> - $i_c = 20/2$ = 10 A. $T = Zi_cBL\,D/2 = 200(10)(0.5)(0.2)(0.1)$ = **20 N m**, so $K_T$ = 1 N m/A.
> - $E = 230 - 20(0.5)$ = **220 V**. With $K_E$ = 1 V s/rad, $\omega$ = 220 rad/s = **2101 rpm**.
> - $P_{em} = EI = T\omega$ = 4400 W, $P_{out}$ = 4200 W, $P_{in}$ = 4600 W, so **η = 91 %**.
> - The Sharkh notes print "6600 rpm". Converting correctly, $220\times60/2\pi$ = 2101 rpm; the printed value appears to be a unit slip.

![[ee_c5_dc_motor_performance.png|760]]

## 5. Torque and machine size (Machines 07)
Rewrite the torque in terms of loadings:

$$
T = 2\,B\,A\,V_R,\qquad A = \frac{Zi_c}{\pi D}\ \text{(electric loading, A/m)},\qquad V_R = \frac{\pi D^2L}{4}
$$

- $B$ (magnetic loading, 0.5–0.8 T, at most 1.5 T) and $A$ (20–70 kA/m, set by cooling) are similar for all machines. So **torque ∝ rotor volume**.
- Because $P = T\omega$, **volume ∝ P/ω**: fast machines are small. That is why motors drive slow loads through step-down **gearboxes** (up to 1000:1).
- Machines 07 question: 1000 W at 10 rad/s needs 100 N m, but at 100 rad/s only 10 N m, a machine ten times smaller.

## Year 2 bridge
- **Actuator dynamics**: with $L_a$ and rotor inertia $J$, a DC motor is a second-order plant ($V\to\omega$). Its transfer function is a classic control example ([[Transfer Function]], [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]).
- **Reaction wheels**: wheel torque $= K_Ti$; wheel speed saturates at $V/K_E$. This sets the momentum capacity and the need for **momentum dumping** ([[Reaction Wheels and Momentum Dumping]], [[SESA2024 06 - Attitude Control]]).
- **Electric aircraft and drones**: motor $K_V$ (rpm/V) is $1/K_E$; propeller power ∝ $\omega^3$ ([[Actuator Disk Theory]]).
- The torque ∝ volume and gearbox argument is the machine counterpart of turbomachinery sizing ([[Specific Speed]]).

## Links
- Previous: [[FEEG1004 C4 - DC Generators and the Commutator]] · Next: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Worked problems: [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] (Q2–Q5)

## Sources
- Sharkh/Niu machines notes §4.1–4.4; Electric Machines 06–07 slides; Hughes Ch. 39–40.
