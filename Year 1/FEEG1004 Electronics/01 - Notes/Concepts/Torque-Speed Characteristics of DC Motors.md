---
title: "Torque-Speed Characteristics of DC Motors"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["torque-speed curve", "no-load speed", "stall torque", "shunt motor", "series motor", "compound motor"]
tags: [feeg1004, concept, machines, dc-motor]
status: complete
parent_lectures: ["[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
related_concepts: ["[[Back EMF and Torque Constants]]", "[[DC Motor Speed Control]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf"]
---

# Torque-Speed Characteristics of DC Motors

## Definition

> [!note] Definition
> PM or separately excited motor:
>
> $$\omega = \frac{V}{K} - \frac{R_a}{K^2}T,\qquad \omega_{NL} = \frac{V}{K},\qquad T_{stall} = \frac{KV}{R_a}$$

## Explanation
- A straight, gently drooping line: nearly constant speed. The **shunt** motor behaves the same on a fixed supply.
- **Series** motor: $\Phi\propto i$, so $T\propto i^2$ and $\omega\propto1/\sqrt T$. It gives huge starting torque (traction, engine starters) but **runs away** if unloaded.
- **Compound**: in between.
- The operating point is where the motor torque equals the load torque (constant for lifts, $\propto\omega^2$ for fans).

![[ee_c6_torque_speed_types.png|640]]

## Related
- Topic notes: [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Concepts: [[Back EMF and Torque Constants]] · [[DC Motor Speed Control]]

## Sources
- Sharkh notes §4.5; Machines 07 slides; Tutorial 6 Q6
