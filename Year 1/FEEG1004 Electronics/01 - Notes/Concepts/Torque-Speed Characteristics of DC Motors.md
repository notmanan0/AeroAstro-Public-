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
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "Sharkh notes §4.5", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf", "Tutorial Sheet 6 Q6"]
---

# Torque-Speed Characteristics of DC Motors

The torque-speed characteristic of a DC motor is the steady-state shaft speed as a function of load torque at a fixed supply voltage. For a permanent-magnet or separately excited motor it is a straight line:

$$
\omega = \frac{V}{K} - \frac{R_a}{K^2}T,\qquad \omega_{NL} = \frac{V}{K},\qquad T_{stall} = \frac{KV}{R_a}
$$

The line droops gently, so the speed stays nearly constant as the load changes. A **shunt** motor on a fixed supply behaves the same way.

In a **series** motor the field flux is proportional to the armature current, $\Phi\propto i$, so $T\propto i^2$ and $\omega\propto1/\sqrt T$. The motor gives a very large starting torque, which suits traction and engine starters, but it runs away if the load is removed. A **compound** motor lies between the shunt and series characteristics.

The operating point is where the motor torque equals the load torque, which is constant for a lift and proportional to $\omega^2$ for a fan.

![[ee_c6_torque_speed_types.png|640]]

## Related

- [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- [[Back EMF and Torque Constants]] · [[DC Motor Speed Control]]
- Sources: Sharkh notes §4.5; Machines 07 slides; Tutorial 6 Q6
