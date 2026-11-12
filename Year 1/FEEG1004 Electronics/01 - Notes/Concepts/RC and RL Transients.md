---
title: "RC and RL Transients"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["time constant", "tau = RC", "tau = L/R", "DC transients", "first-order circuit"]
tags: [feeg1004, concept, transients, first-order]
status: complete
parent_lectures: ["[[FEEG1004 A4 - Capacitors]]", "[[FEEG1004 A5 - Inductors and Electrical Resonance]]"]
related_concepts: ["[[Capacitance]]", "[[Inductance]]", "[[Transfer Function]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W05-5abc Inductors and Resonance - Recorded.pdf", "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Recorded lectures 4 and 5a", "Mills notes §1.5.3 and §1.6.7"]
---

# RC and RL Transients

After a switching event, any first-order circuit with one capacitor or one inductor relaxes exponentially from its initial value to its final value with a time constant $\tau$, where $R$ is the Thévenin resistance seen by the $C$ or $L$.

$$
x(t) = x_\infty + (x_0 - x_\infty)e^{-t/\tau},\qquad \tau_{RC} = RC,\qquad \tau_{RL} = \frac{L}{R}
$$

A transient can be sketched from three pieces of information (Tutorial 2 Q4):

1. The initial value: $v_C$ or $i_L$ carries over unchanged across the switching instant.
2. The final value: at DC the capacitor is an open circuit and the inductor a short circuit.
3. The initial slope: $dv_C/dt = i/C$ and $di_L/dt = v/L$. A straight line at this slope reaches the final value at $t = \tau$.

After one time constant 63 % of the change has happened, after $3\tau$ 95 %, and after $5\tau$ more than 99 %. The governing equation $\tau\dot x + x = x_\infty$ is a **first-order system** with a single pole at $s = -1/\tau$, which links these circuits to the transfer-function and step-response methods of Year 2.

![[ee_a4_capacitor_charging.png|700]]

In Tutorial 2 Q4, 5 Ω with 1 µF gives $\tau$ = 5 µs, and 5 Ω with 1 µH gives $\tau$ = 0.2 µs. A 101 Ω relay coil with an assumed inductance of 50 mH has $\tau\approx$ 0.5 ms for the flyback decay. A rectifier smoothing capacitor works because $R_LC$ is much longer than the ripple period ([[Rectification and Smoothing]]).

![[ee_t2_q4_transients.png|700]]

## Related

- [[FEEG1004 A4 - Capacitors]] · [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Year 2: [[Transfer Function]] · [[Step Response Specifications]] · [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]
- Sources: Recorded lectures 4 and 5a; Mills notes §1.5.3 and §1.6.7
