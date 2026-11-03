---
title: "Spacecraft Stabilisation Types"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["spinner", "dual spinner", "hybrid stabilisation", "three-axis stabilisation", "3-axis", "zero bias", "spin stabilisation"]
tags: [sesa2024, concept, attitude-control]
status: lectured
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Momentum Bias and Gyroscopic Rigidity]]", "[[Inertia Matrix]]", "[[Reaction Wheels and Momentum Dumping]]"]
sources: ["02 - Sources/Lectures/Chapter 6/2025 WEEK 3 Lecture 1 - Chapter 6 - Attitude Control - complete.pdf"]
---

# Spacecraft Stabilisation Types

The course divides active attitude stabilisation into four types according to whether, and how, momentum bias is used: the spinner, the dual spinner, the hybrid and the three-axis-stabilised spacecraft.

A spinner (type 1) spins its whole body at 10–60 rpm. It is simple and stiff, but its cells must be body-mounted, so it is power-limited; its antenna must be omnidirectional or despun; and its inertia matrix must have zero products of inertia, the largest moment about the spin axis and equal transverse moments. Meteosat Second Generation turns the spin into a whiskbroom scan of the Earth.

A dual spinner (type 2) keeps most of the body spinning but despins a platform for a directional antenna or payload. The rotating joint that carries power and signals across the bearing is the reliability concern. Giotto, which survived a dust impact at Halley's Comet thanks to its spin, is the course example.

A hybrid (type 3) is a three-axis body with a momentum wheel spinning at thousands of rpm, which gives bias from a small inertia at high speed. Large deployable arrays become possible, at the cost of a wheel that does nothing else and nutation to damp. GPS satellites and the Eurostar 3000 platform use it.

A three-axis-stabilised spacecraft (type 4) has no significant bias, so it can slew to any direction, at the price of continuous active control with reaction wheels and thrusters. Telescopes (Hubble, JWST) and Earth observers such as SPOT 5 and Envisat use it.

The choice is driven by the payload's pointing: a fixed direction and a simple payload favour spin; pointing anywhere on the sky demands three-axis control. It then shapes every other subsystem.

## Related

- [[SESA2024 06 - Attitude Control#4. The four stabilisation types|The four types in the lecture note]]
- [[Momentum Bias and Gyroscopic Rigidity]] · [[Inertia Matrix]] · [[Reaction Wheels and Momentum Dumping]]
