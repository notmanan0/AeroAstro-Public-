---
title: "Kutta-Joukowski Theorem"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["Kutta–Joukowski", "L' = rho V Gamma", "lift from circulation"]
tags: [sesa2022, concept, potential-flow, lift]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Flow Past a Cylinder]]", "[[Kutta Condition]]", "[[Vortex Sheet]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# Kutta-Joukowski Theorem

## Definition

> [!note] Definition
> The lift per unit span on **any** 2D closed body in a steady, inviscid, incompressible stream is
> $$L' = \rho_\infty V_\infty\Gamma$$
> where $\Gamma = -\oint\mathbf V\cdot d\mathbf s$ is the circulation round the body (clockwise positive in this course). The drag is zero.

## Explanation
- It holds for any shape. The body's geometry only matters through the circulation it supports. For an aerofoil, $\Gamma$ is fixed by the [[Kutta Condition]].
- **Proof for the cylinder**: integrate $-p\sin\theta$ over the surface. Only the cross term $4k\sin\theta$ in $(2\sin\theta+k)^2$ survives, giving $\rho V_\infty\Gamma$ ([[SESA2022 Exam 2016-17 Solutions]] Q1(ii)).
- **In thin-aerofoil theory**: $\Gamma = \int_0^c\gamma(\xi)\,d\xi$, so $c_l = 2\Gamma/(V_\infty c) = \pi(2A_0+A_1)$.
- **In lifting-line theory**: $L'(y) = \rho V_\infty\Gamma(y)$ holds at each section, and $L = \rho V_\infty\int\Gamma\,dy$.
- **Physical picture**: circulation speeds the flow over the top and slows it underneath, and Bernoulli then gives the pressure difference. The **Magnus effect** (spinning ball) is the same result with viscous generation of $\Gamma$.

## Examples
- [[SESA2022 Exam 2016-17 Solutions]] Q1 and [[SESA2022 Exam 2015-16 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]], [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Flow Past a Cylinder]], [[Kutta Condition]], [[Kelvin's Circulation Theorem]], [[Vortex Sheet]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`
