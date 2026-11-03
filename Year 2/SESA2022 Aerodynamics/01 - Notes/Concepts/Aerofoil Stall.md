---
title: "Aerofoil Stall"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["stall", "leading-edge stall", "trailing-edge stall", "thin aerofoil stall", "Clmax"]
tags: [sesa2022, concept, thin-aerofoil-theory, viscous-effects]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Boundary Layer Separation]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-10-28.txt … 2025-11-05.txt (2025-26 transcripts)"]
---

# Aerofoil Stall

**Stall** is the loss of lift beyond $C_{l,max}$, caused by large-scale [[Boundary Layer Separation]] on the suction surface. Thin aerofoil theory, with $C_l = 2\pi(\alpha-\alpha_{L=0})$ linear for ever, can't predict it.

Aerofoils stall in three ways, depending mainly on thickness and leading-edge shape:

| Type | Typical sections | Mechanism | Lift curve |
|---|---|---|---|
| Trailing-edge stall | thick, above ~12 % | turbulent separation starts at the TE and creeps forward as $\alpha$ rises | gentle, rounded peak, benign |
| Leading-edge stall | moderate, ~6–12 % | laminar separation bubble near the LE suddenly bursts | sharp, abrupt drop, with hysteresis |
| Thin-aerofoil stall | thin, below ~6 %, sharp LE | the LE bubble grows steadily along the chord until it reaches the TE | early, gradual rounding |

The leading edge matters because thin aerofoil theory's $A_0(1+\cos\theta)/\sin\theta$ term predicts infinite suction there. A real leading edge has a very high suction peak followed by a steep adverse pressure gradient, which is exactly what the boundary layer struggles with. Camber, leading-edge slats and flaps, vortex generators, boundary-layer suction or blowing and a larger leading-edge radius all delay stall. On hydrofoils the low-pressure peak can trigger cavitation before stall. After stall $C_d$ rises sharply, $C_{m,c/4}$ becomes more nose-down and the flow turns unsteady (buffet).

Past-paper uses: sketches at 6° and 16° for a 10 % section ([[SESA2022 Exam 2021-22 Solutions]] B Q1(v)–(vi)); the consequence of a high leading-edge pressure difference ([[SESA2022 Exam 2022-23 Solutions]] B Q1(v), [[SESA2022 Exam 2024-25 Solutions]] Q3(d)–(e)); $C_{p,max}$ against $\alpha$ from test data ([[SESA2022 Exam 2023-24 Solutions]] B Q3).

## Related

- Stall types in the lecture: [[SESA2022 T4 - Thin Aerofoil Theory#Stall types|T4 §8]]
- [[Boundary Layer Separation]] · [[Aerodynamic Centre and Centre of Pressure]]
