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
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf"]
---

# Aerofoil Stall

## Definition

> [!note] Definition
> **Stall** is the loss of lift beyond $C_{l,max}$, caused by large-scale [[Boundary Layer Separation]] on the suction surface. TAT ($C_l = 2\pi(\alpha-\alpha_{L=0})$, linear for ever) cannot predict it.

## Explanation

| Type | Typical sections | Mechanism | Lift curve |
|---|---|---|---|
| **Trailing-edge stall** | thick, above ~12 % | turbulent separation starts at the TE and creeps forward as $\alpha$ rises | gentle, rounded peak, benign |
| **Leading-edge stall** | moderate, ~6–12 % | laminar separation bubble near the LE suddenly **bursts** | sharp, abrupt drop, with hysteresis |
| **Thin-aerofoil stall** | thin, below ~6 %, sharp LE | the LE bubble grows steadily along the chord until it reaches the TE | early, gradual rounding |

- **Why the LE matters**: TAT's $A_0\frac{1+\cos\theta}{\sin\theta}$ term predicts infinite suction at the LE. A real LE has a very high suction peak followed by a steep adverse gradient.
- **Delaying stall**: camber, LE slats and flaps, vortex generators, boundary-layer suction, blowing, and a larger LE radius.
- **Hydrofoils**: the low-pressure peak can also trigger **cavitation** before stall.
- **After stall**: $C_d$ rises sharply, $C_{m,c/4}$ becomes more nose-down, and the flow is unsteady (buffet).

## Examples
- Sketches at 6° and 16°, 10 % thickness: [[SESA2022 Exam 2021-22 Solutions]] B Q1(v)–(vi).
- Consequence of a high LE pressure difference: [[SESA2022 Exam 2022-23 Solutions]] B Q1(v) and [[SESA2022 Exam 2024-25 Solutions]] Q3(d)–(e).
- $C_{p,max}$ against $\alpha$ from test data: [[SESA2022 Exam 2023-24 Solutions]] B Q3.

## Related
- Parent lectures: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Boundary Layer Separation]], [[Aerodynamic Centre and Centre of Pressure]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf`
