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
sources: ["02 - Sources/S1 Fundamentals/S1-W05-5abc Inductors and Resonance - Recorded.pdf", "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# RC and RL Transients

## Definition

> [!note] Definition
> Any first-order circuit relaxes exponentially from its initial to its final value:
> $$x(t) = x_\infty + (x_0 - x_\infty)e^{-t/\tau},\qquad \tau_{RC} = RC,\qquad \tau_{RL} = \frac{L}{R}$$
> Here $R$ is the Thévenin resistance seen by the $C$ or $L$.

## Explanation
- **Sketching recipe** (Tutorial 2 Q4):
  1. Initial value: $v_C$ or $i_L$ carries over across the switching instant.
  2. Final value: $C$ is open and $L$ is shorted at DC.
  3. Initial slope: $dv_C/dt = i/C$ and $di_L/dt = v/L$. The slope line hits the final value at $t = \tau$.
- 63 % of the change occurs after $\tau$, 95 % after $3\tau$ and over 99 % after $5\tau$.
- The equation $\tau\dot x + x = x_\infty$ is a **first-order system** with pole $s = -1/\tau$.

![[ee_a4_capacitor_charging.png|700]]

## Examples
- 5 Ω with 1 µF: τ = 5 µs. 5 Ω with 1 µH: τ = 0.2 µs (Tutorial 2 Q4).
- Relay coil 101 Ω with an assumed 50 mH: τ ≈ 0.5 ms for flyback decay.
- Rectifier smoothing needs $R_LC\gg$ the ripple period ([[Rectification and Smoothing]]).

![[ee_t2_q4_transients.png|700]]

## Related
- Topic notes: [[FEEG1004 A4 - Capacitors]] · [[FEEG1004 A5 - Inductors and Electrical Resonance]]
- Year 2: [[Transfer Function]] · [[Step Response Specifications]] · [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]

## Sources
- Recorded lectures 4 and 5a; Mills notes §1.5.3 and §1.6.7
