---
title: "SESA2029 A4 - Time Marching - Explicit and Implicit Methods"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 4
tags: [sesa2029, cfd, heat-equation, time-marching, explicit, implicit]
aliases: ["Explicit and implicit methods", "Unsteady heat equation", "CFD Lecture 5"]
date: 2026-10-30
status: lectured
coverage: "Week 3 (2025-10-16, ll. 241–620)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]"]
next_topics: ["[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]"]
key_concepts: ["[[Explicit and Implicit Time Integration]]", "[[CFL and Fourier Numbers]]", "[[CFD Boundary Conditions]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L5)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-16.txt"]
---

# SESA2029 A4 - Time Marching - Explicit and Implicit Methods

> [!abstract] Summary
> The unsteady heat equation is marched forward in time. Evaluating the spatial derivative at the old time level gives an explicit scheme, one line of code per point, which becomes unstable once the Fourier number $F=\alpha\Delta t/h^2$ exceeds one half. Evaluating it at the new level gives an implicit scheme, which needs a linear solve every step but stays stable for any time step. Both are first order in time: halving the step halves the error, and the two err in opposite directions.

> [!summary]- Exam use: quick path
> - **Use it when:** you must discretise an unsteady diffusion equation, say whether a scheme is explicit or implicit, or check a time step against the stability limit.
> - **Assumptions:** forward or backward difference in time, central in space; uniform grid; constant $\alpha$.
> - **Method:** 1. Write $T_j^n$ with superscript time level and subscript grid point. 2. Explicit: $T_j^{n+1}=T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)$. 3. Implicit: $-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1}=T_j^n$, a tridiagonal solve. 4. Boundaries: Dirichlet fixes a value; Neumann (adiabatic) sets $T_N=T_{N-1}$. 5. Explicit needs $F\le\tfrac12$.
> - **Common mistakes:** calling the implicit scheme accurate because it is stable (large steps give large errors); forgetting that the explicit limit tightens with $h^2$ when the grid is refined.
> - **Practise:** [[#The heating of the capsule's inner wall]] · [[SESA2029 CFD Worked Examples#Q5: Explicit and implicit steps for the unsteady heat equation|CFD worked examples Q5]]

The capsule wall of [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|A3]] now evolves in time (2025-10-16, ll. 241–270). The outer face is held at 1200 K, the inside starts at 300 K, and the inner face is insulated, so it can warm up but no heat leaves through it. The question is how long the inside stays tolerable, which needs an accurate solution in time, not just the final steady state.

Information spreads through the grid as in the steady problem, but now in real time. An explicit scheme lets each point respond only to its neighbours' values a moment ago, so heat can only move one grid point per step; if the step is too long, the scheme tries to move more heat than the physics allows and overshoots, and the overshoot grows. An implicit scheme couples all the points at the new time, so information crosses the whole grid in one step, which is why it never blows up, and why with a large step it can still be badly wrong.

## 1. Set-up and boundary conditions

The heat equation $\partial T/\partial t=\alpha\,\partial^2T/\partial x^2$ is solved on $0\le x\le1$ with $T(0)=1200$ K and an initial temperature of 300 K inside (ll. 241–270). The notation is $T_j^n$: subscript $j$ for the grid point, superscript $n$ for the time level, not a power.

The inner face is adiabatic, with no heat transfer, so the temperature gradient there is zero. That is a Neumann boundary condition, fixing a derivative, as opposed to the Dirichlet condition at $x=0$, which fixes a value. A backward difference discretises it simply (ll. 371–395):

$$
\frac{T_N-T_{N-1}}{h}=0\quad\Longrightarrow\quad T_N=T_{N-1}.
$$

In Python that is the line setting the last element equal to the one before it. Fluent's adiabatic walls, symmetry planes and zero-gradient outflows are all Neumann conditions ([[CFD Boundary Conditions]]).

## 2. The explicit scheme

Use a forward difference in time and the second-order central difference in space, with everything on the right at the known level $n$ (ll. 271–300):

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t}=\alpha\frac{T_{j-1}^n-2T_j^n+T_{j+1}^n}{h^2}.
$$

Multiply by $\Delta t$ and collect the constants into the Fourier number $F=\alpha\Delta t/h^2$:

$$
\boxed{T_j^{n+1}=T_j^n+F\left(T_{j-1}^n-2T_j^n+T_{j+1}^n\right)}
$$

Everything on the right is known, so each new value can be written down directly: that is what explicit means, and the whole solver is about six lines of Python (ll. 301–375). The time difference is first order, so halving $\Delta t$ halves the time error; the space difference is second order.

## 3. The implicit scheme

Now write the equation at the new level $n+1$ and look back in time for the derivative, a backward difference (ll. 301–335):

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t}=\alpha\frac{T_{j-1}^{n+1}-2T_j^{n+1}+T_{j+1}^{n+1}}{h^2}.
$$

Multiply by $\Delta t$ and move the unknowns to the left:

$$
\boxed{-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1}=T_j^n}
$$

Three unknowns appear in every equation, so the new values must be found together from a tridiagonal system $\mathbf A\mathbf T^{n+1}=\mathbf T^n$ every step, by Gaussian elimination (the library call `linalg.solve`) or GMRES. That is implicit. A student asked why the backward difference uses $n+1$ rather than $n-1$: the equation is written at level $n+1$ and the time derivative looks back from there to $n$ (ll. 331–345).

| | Explicit | Implicit |
|---|---|---|
| Work per step | a few operations per point | a linear solve |
| Stability | $F\le\tfrac12$ | any $\Delta t$ |
| Time accuracy | first order | first order |
| Suited to | time-accurate problems with small steps | reaching a steady state quickly, stiff problems |

## 4. What the experiments show

Prof Sandham's Python runs use $\alpha=0.1$ and $N=8$ ($h=0.125$) up to $t=0.72$ (ll. 395–480).

Accuracy. With $\Delta t=0.06$ (12 steps) the inner wall reaches 325.1 K against a converged 330.3 K. Halving the step gives 327.8 K, and halving again 329.1 K: errors of 5.2, 2.5 and 1.2 K, halving each time, the signature of a first-order method.

Stability. Increasing $\Delta t$ in the explicit code, $F=0.45$ (0.07) is stable, $F=0.51$ (0.08) starts to wiggle, and $F=0.64$ and $0.77$ blow up: "somewhere around 0.5" is the limit, proved in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]] (ll. 421–450). The implicit code stays stable at $F=0.77$, at $F=1.5$ and even in a single step of 0.72 ($F=4.6$), but that one step gives about 358 K, nearly 28 K too hot (ll. 451–480).

The explicit and implicit errors have opposite signs: explicit lags the true heating, implicit overshoots it. Averaging the two levels (Crank–Nicolson) cancels the leading error and gives a second-order scheme.

![[dam_heat_explicit_stability.png|760]]

The explicit instability appears as a saw-tooth because the fastest-growing error is the shortest wave the grid can carry, alternating sign at every point; for that wave the explicit amplification factor per step is $|1-4F|$, which exceeds 1 once $F>\tfrac12$ ([[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]]).

## 5. The model equation for stability

To analyse stability once for all equations, the next lecture uses a model ordinary differential equation, previewed here (ll. 481–600):

$$
\frac{df}{dt}=\lambda f,\qquad f=f_0e^{\lambda t}.
$$

With complex $\lambda=\sigma+i\omega$,

$$
f=f_0e^{\sigma t}\left(\cos\omega t+i\sin\omega t\right),
$$

so $\sigma$ is a growth rate (unstable if positive, decaying if negative) and $\omega$ a frequency. The equation is not just a toy: the F-4C's short-period pitch oscillation has $\lambda\approx-0.5+1.3i$, a stable, oscillatory response, as SESA2027 and the third-year flight mechanics module show ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]).

## Worked examples

### The heating of the capsule's inner wall

$\alpha=0.1$, $N=8$, run to $t=0.72$; inner-wall temperature $T_8$, recomputed in Python:

| Scheme | $\Delta t$ | $F$ | $T_8$ (K) | Error against 330.3 K |
|---|---|---|---|---|
| explicit | 0.06 | 0.384 | 325.06 | −5.2 |
| explicit | 0.03 | 0.192 | 327.82 | −2.5 |
| explicit | 0.015 | 0.096 | 329.09 | −1.2 |
| explicit | 0.0006 | 0.004 | 330.26 | reference |
| implicit | 0.06 | 0.384 | 334.60 | +4.3 |
| implicit | 0.12 | 0.768 | 338.22 | +7.9 |
| implicit | 0.72 (one step) | 4.608 | 357.86 | +27.6 |

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- Next: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Concepts: [[Explicit and Implicit Time Integration]] · [[CFL and Fourier Numbers]] · [[CFD Boundary Conditions]]
- Higher-order time stepping: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Eigenvalues and dynamic modes: [[Characteristic Equation and Eigenvalues]]

## Sources

- `All_lectures_as_delivered.pdf`, L5, with transcript `SESA2029 Lecture 2025-10-16.txt`, ll. 241–620 (Prof N. Sandham; Python demonstrations on Blackboard)
- Table recomputed in Python

## Self-study tasks

### Core

- [ ] Discretise the unsteady heat equation explicitly and implicitly ("this might be the kind of thing we want you to do in an exam", 2025-10-16, ll. 261–300). → [[#2. The explicit scheme]] · [[#3. The implicit scheme]]
- [ ] One explicit and one implicit step by hand (example sheet). → [[SESA2029 CFD Worked Examples#Q5: Explicit and implicit steps for the unsteady heat equation|Worked examples Q5]]
- [ ] Run the explicit and implicit codes and find the stability limit and the order of accuracy yourself ("just play with these codes", ll. 601–620; the example sheet suggests tests). → [[#The heating of the capsule's inner wall]]

### Further practice

- [ ] Explain the difference between Dirichlet and Neumann conditions, with a CFD example of each. → [[#1. Set-up and boundary conditions]]
- [ ] Show that $f=f_0e^{\lambda t}$ solves $df/dt=\lambda f$ and interpret complex $\lambda$ (asked of the class, ll. 511–600). → [[#5. The model equation for stability]]
