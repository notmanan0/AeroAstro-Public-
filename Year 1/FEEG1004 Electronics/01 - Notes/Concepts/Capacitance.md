---
title: "Capacitance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["capacitor", "Q = CV", "i = C dv/dt", "parallel plate capacitor", "energy in a capacitor"]
tags: [feeg1004, concept, capacitor]
status: complete
parent_lectures: ["[[FEEG1004 A4 - Capacitors]]"]
related_concepts: ["[[RC and RL Transients]]", "[[Complex Impedance]]", "[[Capacitive Displacement Sensor]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W04-4 Capacitors - Recorded.pdf"]
---

# Capacitance

## Definition

> [!note] Definition
> $$Q = CV,\qquad i = C\frac{dv}{dt},\qquad C = \frac{\varepsilon_0\varepsilon_rA}{d},\qquad E = \tfrac{1}{2}CV^2$$

## Explanation
- A capacitor stores energy in the **electric field** between its plates.
- $v_C$ is **continuous**: it cannot jump without infinite current.
- DC steady state: $i = 0$, so it acts as an **open circuit**. At switch-on from zero charge it acts as a **short**.
- In AC its impedance is $Z_C = 1/j\omega C = -jX_C$, and the current **leads** the voltage by 90° ([[Complex Impedance]]).
- In parallel capacitances add; in series they combine like parallel resistors.

## Examples
- 5 µF charged by 1 mA for 5 s: 1000 V and 2.5 J.
- A steady-state divider leaves 2 V on a 2 µF capacitor, so $Q$ = 4 µC.
- Smoothing capacitor $C = I/(2f\Delta V)$ = 250 µF (Tutorial 3 Q6).

## Related
- Topic notes: [[FEEG1004 A4 - Capacitors]]
- Concepts: [[RC and RL Transients]] · [[Rectification and Smoothing]] · [[Capacitive Displacement Sensor]] · [[Power Factor Correction]]

## Sources
- Recorded lecture 4
