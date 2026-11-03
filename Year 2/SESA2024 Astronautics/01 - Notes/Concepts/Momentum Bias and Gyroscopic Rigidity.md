---
title: "Momentum Bias and Gyroscopic Rigidity"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["momentum bias", "gyroscopic rigidity", "gyroscopic precession", "nutation", "spin stability"]
tags: [sesa2024, concept, attitude-control]
status: lectured
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Inertia Matrix]]", "[[Spacecraft Stabilisation Types]]", "[[Reaction Wheels and Momentum Dumping]]"]
sources: ["02 - Sources/Lectures/Chapter 6/Chapter 6 - Attitude Control - prerecorded material.pdf"]
---

# Momentum Bias and Gyroscopic Rigidity

Momentum bias is a large angular momentum $H_0$ stored deliberately about one axis of a spacecraft, by spinning the body or a wheel; gyroscopic rigidity is the resulting resistance of that axis to being turned by a torque.

A torque $\mathbf T$ perpendicular to $\mathbf H_0$ acting for $\Delta t$ adds $\mathbf T\Delta t$ at right angles to it, so the momentum vector turns through $\psi\approx T\Delta t/H_0$ rather than tipping in the direction of the torque: it precesses at $\dot\psi=T/H_0$, the displacement appearing $90^\circ$ later in the direction of rotation. The larger the bias, the smaller the deflection from the same disturbance, which is why a bicycle is easier to balance at speed.

Bias is only worth having about an axis that should stay fixed for the whole mission, usually the orbit normal, because turning it needs a sustained torque and propellant. It also brings a nutation mode, a coning wobble excited by any impulsive torque that would last indefinitely in space, so dampers must be carried; and it changes the torque response, since a biased body precesses at a steady rate under a steady torque instead of coasting after a pulse. Disturbances still build up momentum secularly, so external torquers are needed whatever the bias.

The three biased stabilisation types differ only in how the bias is stored: a spinner uses a large inertia at 10–60 rpm, a dual spinner the same with a despun platform, and a hybrid a small wheel at thousands of rpm.

![[ast_gyroscopic_rigidity.png|560]]

## Related

- [[SESA2024 06 - Attitude Control#3. Gyroscopic precession and momentum bias|Precession and bias in the lecture note]]
- [[Inertia Matrix]] · [[Spacecraft Stabilisation Types]] · [[Reaction Wheels and Momentum Dumping]]
