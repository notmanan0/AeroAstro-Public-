---
title: "Truncation Error and Order of Accuracy"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["order of accuracy", "truncation error", "leading error term", "convergence rate"]
tags: [sesa2029, concept, numerical-methods]
status: complete
parent_lectures: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]", "[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]", "[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
related_concepts: ["[[Finite Difference Approximations]]", "[[Taylor Table Method]]", "[[Mesh Convergence and Grid Independence]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L3, L7, L12)", "02 - Sources/CFD/CFD.txt"]
---

# Truncation Error and Order of Accuracy

## Definition

> [!note] Definition
> The **truncation error** is the part of the Taylor series a discrete scheme drops. If its leading term scales as $h^p$ (or $\Delta t^p$), the scheme is **$p$-th order accurate**: halving the step reduces the error by $2^p$.

## Explanation

- Read the order from the leading error term. For example $f'_j = \dfrac{f_{j+1}-f_{j-1}}{2h}-\dfrac{h^2}{6}f'''_j$ is second order. Always divide through by $h$ before reading the power.
- Its derivative tells you what is differentiated **exactly**: an error $\propto f'''$ means quadratics are exact.
- On log–log axes of error against $N$ (or $h$), a $p$-th order method plots as a line of slope $-p$ (or $+p$ against $h$). In a grid study this is how you check that a code achieves its design order.
- **Runge–Kutta**: an order-$n$ RK scheme reproduces the Taylor series of $e^{\lambda\Delta t}$ up to $(\lambda\Delta t)^n/n!$ exactly.
- **Guidance**: the AIAA expects at least second order in space and time. First-order upwind may be used to get a solution started, but it spoils grid convergence.
- Truncation error is part of the **discretisation error**. Round-off (finite precision) is separate: double precision is about $10^{-16}$.

## Examples

- The 3-point backward scheme $f'_j = \dfrac{f_{j-2}-4f_{j-1}+3f_j}{2h}+\dfrac{h^2}{3}f'''_j$ is second order.
- Explicit Euler on the heat equation: errors of 5.2, 2.5 and 1.2 K as $\Delta t$ halves, so first order in time ([[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]).
- Euler, RK2 and RK4 on $f' = \lambda f$ give slopes 1, 2 and 4:

![[dam_time_order_convergence.png|520]]

## Related

- Parent lectures: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] · [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]] · [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Related concepts: [[Finite Difference Approximations]] · [[Taylor Table Method]] · [[Mesh Convergence and Grid Independence]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L3, L7, L12)
- 02 - Sources/CFD/CFD.txt
