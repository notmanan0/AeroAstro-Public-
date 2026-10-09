---
title: "SESA2029 A4 - Time Marching - Explicit and Implicit Methods"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 4
tags:
  - sesa2029
  - cfd
  - numerical-methods
  - time-integration
aliases: ["Unsteady heat equation", "Explicit vs implicit Euler"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]"]
next_topics: ["[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]"]
key_concepts: ["[[Explicit and Implicit Time Integration]]", "[[CFL and Fourier Numbers]]", "[[CFD Boundary Conditions]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L5, pp. 71–76)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A4 - Time Marching - Explicit and Implicit Methods

> [!abstract] Summary
> For the **unsteady** heat equation $T_t = \alpha T_{xx}$ we march in time from an initial state. Two first-order (Euler) choices:
> - **Explicit**: evaluate the right-hand side at the *known* level $n$. The update is one line of code, but it is only stable when the **Fourier number** $F = \alpha\Delta t/h^2\le\tfrac12$.
> - **Implicit**: evaluate it at the *unknown* level $n+1$. Every step then needs a matrix solve, but the scheme is stable for **any** $\Delta t$.
>
> Stability is not accuracy. Big implicit steps stay bounded but are wrong in time, because both schemes are only $O(\Delta t)$. A new boundary condition also appears: the **adiabatic (Neumann)** wall, $\partial T/\partial x = 0$.

## Key Concepts
- [[Explicit and Implicit Time Integration]] · [[CFL and Fourier Numbers]] · [[CFD Boundary Conditions]]

---

## 1. Problem set-up (L5)
- Same wall as in A3: $T(0) = 1200$ K is held fixed and the initial interior temperature is 300 K.
- The inner face $x = 1$ is now **adiabatic** (no heat transfer), so it heats up over time.
- Discretise the Neumann condition with a simple backward difference: $(T_N-T_{N-1})/h = 0\;\Rightarrow\;T_N = T_{N-1}$.

Notation: $T_j^n$, where **superscript $n$ is the time level** and **subscript $j$ is the grid point**.

**Dirichlet vs Neumann**:
- **Dirichlet** fixes a value (e.g. $T_0 = 1200$ K, no-slip $u = 0$).
- **Neumann** fixes a gradient (e.g. an adiabatic wall, zero-gradient outflow, symmetry). See [[CFD Boundary Conditions]].

## 2. Two discretisations (L5)
**Explicit Euler**: forward difference in time, central in space, right-hand side at level $n$.

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t} = \alpha\frac{T_{j-1}^n-2T_j^n+T_{j+1}^n}{h^2}\;\Rightarrow\;\boxed{T_j^{n+1} = T_j^n+F\left(T_{j-1}^n-2T_j^n+T_{j+1}^n\right)},\quad F = \frac{\alpha\Delta t}{h^2}
$$

Only one unknown appears on the left, so each new value can be written down directly. That is what "explicit" means.

**Implicit (backward) Euler**: backward difference in time, with the right-hand side at level $n+1$.

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t} = \alpha\frac{T_{j-1}^{n+1}-2T_j^{n+1}+T_{j+1}^{n+1}}{h^2}\;\Rightarrow\;\boxed{-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1} = T_j^n}
$$

Several unknowns are coupled, giving a tridiagonal system $\mathbf A\mathbf T^{n+1} = \mathbf T^n$ to solve every step. The boundary rows are $T_0 = 1200$ and $T_N-T_{N-1} = 0$.

| | Explicit | Implicit |
|---|---|---|
| Work per step | a few multiply–adds per point | a linear solve (elimination or GMRES) |
| Stability | $F\le\tfrac12$ | unconditional |
| Time accuracy | $O(\Delta t)$ | $O(\Delta t)$ |
| Best for | time-accurate, small $\Delta t$ | reaching a steady state fast; stiff problems |

## 3. Numerical experiments (L5, recomputed)
Take $\alpha = 0.1$, $N = 8$ ($h = 0.125$) and run to $t = 0.72$. The table gives the inner-wall temperature $T_8$:

| Scheme | $\Delta t$ | $F$ | $T_8$ [K] | Error vs converged 330.3 K |
|---|---|---|---|---|
| explicit | 0.06 | 0.384 | 325.06 | −5.2 |
| explicit | 0.03 | 0.192 | 327.82 | −2.5 |
| explicit | 0.015 | 0.096 | 329.09 | −1.2 |
| explicit | 0.0006 | 0.0038 | 330.26 | (reference) |
| implicit | 0.06 | 0.384 | 334.60 | +4.3 |
| implicit | 0.24 | 1.54 | 344.06 | +13.8 |
| implicit | 0.72 (one step) | 4.61 | 357.86 | +27.6 |

- **First order in time.** Halving $\Delta t$ halves the error: 5.2 → 2.5 → 1.2 K.
- **Explicit error and implicit error have opposite signs.** Explicit lags the true heating and implicit over-predicts it. That is why averaging the two (Crank–Nicolson) is second order.
- **Explicit instability.** $\Delta t = 0.07$ ($F = 0.448$) behaves. $\Delta t = 0.08$ ($F = 0.512$) starts to wiggle. $\Delta t = 0.09$ ($F = 0.576$) grows a saw-tooth that explodes. The threshold $F = \tfrac12$ is proved in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]].
- **Implicit is stable even in one giant step** ($F = 4.6$), but that step is 28 K too hot.

![[dam_heat_explicit_stability.png|760]]

![[dam_heat_explicit_vs_implicit.png|620]]

> [!tip] Why the explicit instability looks like a saw-tooth
> The fastest-growing error is the shortest wave the grid can hold: 2 points per wavelength, $kh = \pi$, alternating $+,-,+,-$. For explicit Euler its amplification factor per step is $|1-4F|$. At $F = 0.576$ that is $1.30$, so after 20 steps the error has grown by $1.3^{20}\approx190$.

## 4. Preview: the model equation $df/dt = \lambda f$ (L5)
To study stability in general, numerical analysts use $\dfrac{df}{dt} = \lambda f$ with exact solution $f = f_0e^{\lambda t}$.

Let $\lambda = \sigma+i\omega$ be complex:
- $\sigma$ is the **growth rate** ($>0$ unstable, $<0$ decaying);
- $\omega$ is the **frequency** in rad/s.

$$
f = f_0e^{\sigma t}(\cos\omega t+i\sin\omega t)\qquad\text{(take the real part for a physical signal)}
$$

This is not just a toy. Every aircraft dynamic mode obeys it. The F-4C short-period oscillation has $\lambda\approx-0.5+1.3i$: stable, a damped oscillation of about 2 s ([[Short Period Oscillation]], [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]).

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] · Next: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Higher-order time stepping: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Characteristic roots and modes: [[Characteristic Equation and Eigenvalues]]

## Sources
- CFD Lecture 5, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 71–76; transcript `CFD.txt` (Python demonstrations)
- All table values recomputed (`scripts/make_figures.py`)
