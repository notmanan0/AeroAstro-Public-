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

A potentiometric displacement sensor is a resistive track of total resistance $R_p$ with a sliding wiper attached to the moving part, so that the track forms a potential divider whose output is set by the fractional wiper position $x$.

$$
\frac{V_{out}}{V_{in}} = x\ \text{(unloaded)},\qquad \frac{V_{out}}{V_{in}} = \frac{x}{1 + (R_p/R_{load})\,x(1 - x)}\ \text{(loaded)}
$$

The output is linear in $x$ only when $R_{load}\gg R_p$. A finite load draws current through the wiper and pulls the output below the straight line; the term $x(1-x)$ is zero at both ends of the track, so the error peaks at mid-travel. A voltage-follower buffer on the wiper restores linearity, because it draws no input current from the divider and can drive any load from its output.

The sensor is cheap, simple and light and works over a wide temperature range. Against that, the sliding contact brings friction and **wear**, which makes it unreliable for critical uses, and a rotary pot has a dead zone where the wiper leaves the track.

![[ee_e2_pot_loading.png|700]]

## Related

- [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- [[Potential Divider]] · [[Loading Effect and Buffering]] · [[Standard Op-Amp Configurations]]
- Sources: Transducers lecture 2
