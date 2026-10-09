---
title: "Electric and Magnetic Loading"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["torque per unit volume", "T = 2BAV", "electric loading", "magnetic loading", "machine sizing", "gearbox argument"]
tags: [feeg1004, concept, machines, sizing]
status: complete
parent_lectures: ["[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]"]
related_concepts: ["[[Back EMF and Torque Constants]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf"]
---

# Electric and Magnetic Loading

## Definition

> [!note] Definition
> $$T = 2\,B\,A\,V_R,\qquad A = \frac{Zi_c}{\pi D}\ \text{(electric loading)},\qquad B\ \text{(magnetic loading)},\qquad V_R = \frac{\pi D^2L}{4}$$

## Explanation
- $B$ ≈ 0.5–0.8 T (limited by steel saturation) and $A$ ≈ 20–70 kA/m (limited by cooling) are much the same for machines of any size. So **torque ∝ rotor volume**.
- With $P = T\omega$: **volume ∝ P/ω**. High-speed machines are small for their power.
- This is why a motor drives a slow load through a step-down gearbox (up to about 1000:1), and why slow wind or tidal turbines use step-up gearboxes.

## Examples
- 1 kW at 10 rad/s needs 100 N m; at 100 rad/s only 10 N m, about a tenth of the volume.
- Tutorial 6 Q4 derives $T = 2BAV_R$; Q5 asks why gearboxes are used.

## Related
- Topic notes: [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Cross-module: [[Specific Speed]] · [[Dimensional Analysis of Turbomachines]]

## Sources
- Sharkh notes §4.4; Machines 07 slides
