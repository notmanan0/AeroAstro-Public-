---
title: "Explicit and Implicit Time Integration"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["explicit Euler", "implicit Euler", "forward Euler", "backward Euler", "time marching"]
tags: [sesa2029, concept, numerical-methods, time-integration]
status: complete
parent_lectures: ["[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]", "[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]"]
related_concepts: ["[[Von Neumann Stability Analysis]]", "[[CFL and Fourier Numbers]]", "[[Runge-Kutta Methods]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L5–L6)", "02 - Sources/CFD/CFD.txt"]
---

# Explicit and Implicit Time Integration

## Definition

> [!note] Definition
> Two ways to advance $df/dt = R(f)$:
> - An **explicit** scheme evaluates $R$ at the **known** level $n$, e.g. $f^{n+1} = f^n+\Delta tR(f^n)$. Each update is written down directly.
> - An **implicit** scheme evaluates $R$ at the **unknown** level $n+1$, e.g. $f^{n+1}-\Delta tR(f^{n+1}) = f^n$. Each step needs a (matrix) solve.

## Explanation

| | Explicit Euler | Implicit Euler |
|---|---|---|
| Heat equation update | $T_j^{n+1} = T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)$ | $-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1} = T_j^n$ |
| Cost per step | cheap | tridiagonal or sparse solve |
| Stability ($f' = \lambda f$) | inside the circle $\lvert1+\lambda\Delta t\rvert\le1$ | outside the circle $\lvert1-\lambda\Delta t\rvert\ge1$: all of the left half-plane |
| Heat equation limit | $F = \alpha\Delta t/h^2\le\tfrac12$ | none |
| Accuracy | $O(\Delta t)$ | $O(\Delta t)$ |

- Implicit methods are the workhorse for reaching **steady states** quickly and for **stiff** problems.
- Explicit methods suit **time-accurate** simulation where small steps are needed anyway.
- Large implicit steps are stable but **inaccurate**: they can even damp physically growing modes.
- Higher-order options: BDF2 (implicit, used in dual time-stepping) and RK2/RK4 (explicit).

## Examples

- Inner-wall temperature after $t = 0.72$ (converged value 330.3 K): explicit at $\Delta t = 0.06$ gives 325.1 K and implicit gives 334.6 K. A single implicit step of 0.72 is stable but reads 357.9 K.

![[dam_heat_explicit_vs_implicit.png|520]]

## Related

- Parent lectures: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]] · [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Related concepts: [[Von Neumann Stability Analysis]] · [[CFL and Fourier Numbers]] · [[Runge-Kutta Methods]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L5–L6)
- 02 - Sources/CFD/CFD.txt
