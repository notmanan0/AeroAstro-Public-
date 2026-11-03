---
title: "Goodman Relation"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Goodman equation", "Goodman line", "Mean stress correction"]
tags: [sesa2028, materials, fatigue, mean-stress]
status: lectured
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[S-N Curve and Basquin Law]]", "[[Shot Peening]]"]
---

# Goodman Relation

The Goodman relation $\sigma_a=\sigma_{a0}(1-\sigma_m/\sigma_{ts})$ gives the stress amplitude a material can carry for a chosen life when the cycle has a mean stress $\sigma_m$, by assuming a straight line between the fully reversed fatigue strength $\sigma_{a0}$ and the tensile strength $\sigma_{ts}$.

At the same amplitude a higher mean stress shortens the life, so fatigue data form a family of S-N curves, one per mean stress. Goodman collapses the family into one line on a plot of amplitude against mean stress: at $\sigma_m=0$ the allowable amplitude is $\sigma_{a0}$, and with no amplitude at all the mean stress can rise to $\sigma_{ts}$ before the part fails statically. Points below the line are safe for that life.

![[materials_goodman_mean_stress.png|800]]

The relation explains why residual stresses matter even though they do not change the stress range. A compressive residual stress lowers the effective mean stress and moves the operating point down and to the left, which is how [[Shot Peening]] raises the fatigue limit; a tensile residual stress, such as a weld leaves, does the opposite. As a quick number: with $\sigma_{a0}=300$ MPa and $\sigma_{ts}=600$ MPa, a mean stress of 150 MPa cuts the allowable amplitude to 225 MPa.

## Related

- Topic: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[S-N Curve and Basquin Law]] · [[Shot Peening]] · [[Miner's Rule]]
