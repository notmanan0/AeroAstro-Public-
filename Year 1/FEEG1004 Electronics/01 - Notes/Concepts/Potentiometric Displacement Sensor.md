---
title: "Potentiometric Displacement Sensor"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["displacement potentiometer", "wiper", "pot sensor", "loaded potentiometer"]
tags: [feeg1004, concept, transducers, displacement]
status: complete
parent_lectures: ["[[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]"]
related_concepts: ["[[Potential Divider]]", "[[Loading Effect and Buffering]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 02 - Displacement Sensors - Lecture Slides.pdf"]
---

# Potentiometric Displacement Sensor

## Definition

> [!note] Definition
> A resistive track with a sliding wiper forms a potential divider:
> $$\frac{V_{out}}{V_{in}} = x\ \text{(unloaded)},\qquad \frac{V_{out}}{V_{in}} = \frac{x}{1 + (R_p/R_{load})\,x(1 - x)}\ \text{(loaded)}$$

## Explanation
- It is linear only when $R_{load}\gg R_p$. The error peaks mid-travel.
- A **voltage-follower buffer** on the wiper restores linearity: no input current, and it drives any load.
- Pros: cheap, simple, light, wide temperature range. Cons: friction and **wear** (unreliable for critical uses); a dead zone on rotary pots.

![[ee_e2_pot_loading.png|700]]

## Related
- Topic notes: [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Potential Divider]] · [[Loading Effect and Buffering]] · [[Standard Op-Amp Configurations]]

## Sources
- Transducers lecture 2
