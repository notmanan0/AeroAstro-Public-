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
> The unsteady heat equation is marched forward in time. Evaluating the spatial derivative at the old time level gives an explicit scheme, one line of code per point, which becomes unstable once the Fourier number $F=\alpha\Delta t/h^2$ exceeds one half. Evaluating it at the new level gives an implicit scheme, which needs a linear solve every step but stays stable for any time step. Both are first order in time: halving the step halves the error, and the two err in opposite directions, because one uses the slope at the start of the step and the other the slope at the end.

> [!summary]- Exam use: quick path
> - **Use it when:** you must discretise an unsteady diffusion equation, take a step by hand, say whether a scheme is explicit or implicit, or check a time step against the stability limit.
> - **Assumptions:** forward or backward difference in time, central in space; uniform grid; constant $\alpha$.
> - **Method:** 1. Write $T_j^n$ with superscript time level and subscript grid point. 2. Explicit: $T_j^{n+1}=T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)$. 3. Implicit: $-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1}=T_j^n$, a tridiagonal solve. 4. Boundaries: Dirichlet fixes a value; Neumann (adiabatic) sets $T_N=T_{N-1}$. 5. Explicit needs $F\le\tfrac12$.
> - **Common mistakes:** calling the implicit scheme accurate because it is stable (large steps give large errors); forgetting that the explicit limit $\Delta t\le h^2/2\alpha$ tightens fourfold when the grid spacing halves.
> - **Practise:** [[#One explicit and one implicit step by hand]] · [[SESA2029 CFD Worked Examples#Q5: Explicit and implicit steps for the unsteady heat equation|CFD worked examples Q5]]

The capsule wall of [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|A3]] evolves in time. The outer face is held at 1200 K, the inside starts at 300 K, and the inner face is insulated, so it can warm up but no heat leaves through it. How long the inside stays tolerable depends on the temperature history, which needs an accurate solution in time, not just the final steady state.

Information spreads through the grid as in the steady problem, but now in real time. An explicit scheme lets each point respond only to its neighbours' values a moment ago, so heat can move only one grid point per step. If the step is too long, the scheme tries to move more heat than the physics allows and overshoots, and the overshoot grows. An implicit scheme couples all the points at the new time, so information crosses the whole grid in one step. That is why it never blows up, and also why, with a large step, it can still be badly wrong: stability and accuracy are separate questions.

## 1. Set-up and boundary conditions

The heat equation

$$
\frac{\partial T}{\partial t}=\alpha\frac{\partial^2T}{\partial x^2}
$$

is solved on $0\le x\le1$ with $T(0)=1200$ K and an initial temperature of 300 K inside. $T$ is a function of time and space. The notation is $T_j^n$: subscript $j$ for the grid point at $x_j=jh$, superscript $n$ for the time level $t_n=n\Delta t$, not a power.

The inner face is adiabatic, with no heat transfer, so by Fourier's law the temperature gradient there is zero. That is a Neumann boundary condition, fixing a derivative, as opposed to the Dirichlet condition at $x=0$, which fixes a value. A backward difference discretises it:

$$
\left.\frac{\partial T}{\partial x}\right|_{x=1}=0
\quad\Longrightarrow\quad
\frac{T_N-T_{N-1}}{h}=0
\quad\Longrightarrow\quad
T_N=T_{N-1}.
$$

In Python that is the line setting the last element equal to the one before it. Fluent's adiabatic walls, symmetry planes and zero-gradient outflows are all Neumann conditions ([[CFD Boundary Conditions]]). This backward difference is only first order, which dominates the spatial error in [[#4. What the experiments show]].

## 2. The explicit scheme

Use a forward difference in time and the second-order central difference in space, with the right-hand side evaluated at the known level $n$:

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t}=\alpha\frac{T_{j-1}^n-2T_j^n+T_{j+1}^n}{h^2}.
$$

Multiply by $\Delta t$:

$$
T_j^{n+1}-T_j^n=\frac{\alpha\Delta t}{h^2}\left(T_{j-1}^n-2T_j^n+T_{j+1}^n\right).
$$

Collect the constants into the Fourier number $F=\alpha\Delta t/h^2$ and move $T_j^n$ across:

$$
\boxed{T_j^{n+1}=T_j^n+F\left(T_{j-1}^n-2T_j^n+T_{j+1}^n\right)}
$$

The left-hand side contains a single term at level $n+1$ and everything on the right is known, so each new value can be written down directly. That is what explicit means, and the whole solver is about six lines of Python.

![[dam_explicit_implicit_stencils.png|900]]

The Fourier number is dimensionless: $\alpha$ is in m²/s, $\Delta t$ in s and $h^2$ in m². It compares the time step with the time heat takes to diffuse across one cell, $h^2/\alpha$.

## 3. The implicit scheme

The implicit scheme writes the equation at the new level $n+1$, so that the time derivative looks back from $n+1$ to $n$ (a backward difference), and evaluates the right-hand side at $n+1$ too:

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t}=\alpha\frac{T_{j-1}^{n+1}-2T_j^{n+1}+T_{j+1}^{n+1}}{h^2}.
$$

Multiply by $\Delta t$ and use $F$:

$$
T_j^{n+1}-T_j^n=F\left(T_{j-1}^{n+1}-2T_j^{n+1}+T_{j+1}^{n+1}\right).
$$

Move the unknowns to the left and the known value to the right:

$$
T_j^{n+1}-FT_{j-1}^{n+1}+2FT_j^{n+1}-FT_{j+1}^{n+1}=T_j^n.
$$

Collect the $T_j^{n+1}$ terms:

$$
\boxed{-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1}=T_j^n}
$$

Three unknowns appear in every equation, so the new values must be found together. With the Dirichlet row $T_0^{n+1}=1200$ and the Neumann row $T_N^{n+1}-T_{N-1}^{n+1}=0$, the system for $N=8$ is

$$
\begin{bmatrix}
1&&&&&&&&\\
-F&1+2F&-F&&&&&&\\
&-F&1+2F&-F&&&&&\\
&&\ddots&\ddots&\ddots&&&&\\
&&&&&-F&1+2F&-F&\\
&&&&&&&-1&1
\end{bmatrix}
\begin{Bmatrix}T_0^{n+1}\\T_1^{n+1}\\T_2^{n+1}\\\vdots\\T_7^{n+1}\\T_8^{n+1}\end{Bmatrix}
=\begin{Bmatrix}1200\\T_1^n\\T_2^n\\\vdots\\T_7^n\\0\end{Bmatrix},
$$

a tridiagonal system $\mathbf A\mathbf T^{n+1}=\mathbf b^n$ solved every step by Gaussian elimination (the library call `linalg.solve`) or GMRES. $\mathbf A$ is the same every step when $\Delta t$ is fixed; only the right-hand side changes.

| | Explicit | Implicit |
|---|---|---|
| Work per step | a few operations per point | a linear solve |
| Stability | $F\le\tfrac12$ | any $\Delta t$ |
| Time accuracy | first order | first order |
| Suited to | time-accurate problems with small steps | reaching a steady state quickly, stiff problems |

### Why both are first order, with opposite errors

Expand $T_j^{n+1}$ about $t_n$ by Taylor series, as in [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|A2]] but in time:

$$
T_j^{n+1}=T_j^n+\Delta t\,\frac{\partial T}{\partial t}\bigg|^n+\frac{\Delta t^2}{2}\frac{\partial^2T}{\partial t^2}\bigg|^n+\dots
$$

Rearrange:

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t}=\frac{\partial T}{\partial t}\bigg|^n+\frac{\Delta t}{2}\frac{\partial^2T}{\partial t^2}\bigg|^n+\dots
$$

The forward difference overestimates the derivative at $t_n$ by $\tfrac{\Delta t}{2}T_{tt}$, an error proportional to $\Delta t$: first order. Expanding $T_j^n$ about $t_{n+1}$ instead,

$$
T_j^n=T_j^{n+1}-\Delta t\,\frac{\partial T}{\partial t}\bigg|^{n+1}+\frac{\Delta t^2}{2}\frac{\partial^2T}{\partial t^2}\bigg|^{n+1}-\dots
$$

so

$$
\frac{T_j^{n+1}-T_j^n}{\Delta t}=\frac{\partial T}{\partial t}\bigg|^{n+1}-\frac{\Delta t}{2}\frac{\partial^2T}{\partial t^2}\bigg|^{n+1}+\dots
$$

The backward difference is also first order, with the leading error of opposite sign. Physically, the explicit scheme advances each step with the heating rate at the start of the step and the implicit scheme with the rate at the end. At the capsule's inner wall the heating is accelerating, $T_{tt}>0$, so the start-of-step rate is too low and the explicit result lags, while the end-of-step rate is too high and the implicit result leads. The space discretisation is the second-order central difference in both schemes.

## 4. What the experiments show

The runs below use $\alpha=0.1$ and $N=8$ ($h=0.125$) up to $t=0.72$.

Accuracy. With $\Delta t=0.06$ (12 steps, $F=0.384$) the explicit scheme gives an inner-wall temperature of 325.1 K, against 330.3 K when the time step is made very small. Halving the step gives 327.8 K, and halving again 329.1 K: errors of 5.2, 2.4 and 1.2 K, halving each time, the signature of a first-order method. The implicit scheme gives 334.6, 332.6 and 331.5 K at the same three steps, errors of $+4.3$, $+2.3$ and $+1.2$ K, the same size and opposite sign.

![[dam_heat_explicit_vs_implicit.png|900]]

Stability. Increasing $\Delta t$ in the explicit code, $F=0.448$ ($\Delta t=0.07$) is stable but not accurate, $F=0.512$ ($\Delta t=0.08$) starts to wiggle, and $F=0.64$ and $0.768$ ($\Delta t=0.10$ and $0.12$) blow up. Somewhere around 0.5 is the limit; [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]] proves it. The implicit code stays stable at $F=0.768$, at $F=1.536$ and even in a single step of 0.72 ($F=4.6$), but that one step gives 357.9 K, nearly 28 K too hot.

![[dam_heat_explicit_stability.png|900]]

The explicit instability appears as a saw-tooth because the fastest-growing error is the shortest wave the grid can carry, alternating in sign from point to point. For that wave $T_{j\pm1}=-T_j$, so the update becomes $T_j^{n+1}=T_j^n+F(-4T_j^n)=(1-4F)T_j^n$, and the saw-tooth is multiplied by $|1-4F|$ every step. That factor exceeds 1 once $F>\tfrac12$; at $F=0.576$ it is 1.30.

> [!check] The 330.3 K reference is converged in time, not in space
> Refining the time step alone cannot remove the spatial error. The exact solution of the PDE with these boundary conditions, a Fourier series in $\sin\big((2k+1)\pi x/2\big)$, gives 315.1 K at the inner wall at $t=0.72$. Repeating the calculation with tiny time steps on finer grids gives 330.2, 320.6, 317.4, 316.2 and 315.6 K for $N=8$ to 128, errors that roughly halve with $h$. The first-order backward difference in the Neumann condition, which makes the heat flux between $x_{N-1}$ and $x_N$ zero and so effectively puts the insulated wall half a cell early, at $x=1-h/2$, dominates the error: a thinner wall heats through faster. On $N=8$ the 5 K time error of the 12-step run is smaller than the 15 K space error.

## 5. The model equation for stability

[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]] analyses stability once for many equations by using a model ordinary differential equation:

$$
\frac{\mathrm df}{\mathrm dt}=\lambda f.
$$

Try $f=f_0e^{\lambda t}$: differentiating gives $\mathrm df/\mathrm dt=\lambda f_0e^{\lambda t}=\lambda f$, so it is the exact solution for any constant $\lambda$, real or complex. Let $\lambda=\sigma+i\omega$. Split the exponential:

$$
f=f_0e^{\sigma t}e^{i\omega t}.
$$

Use Euler's formula $e^{i\omega t}=\cos\omega t+i\sin\omega t$:

$$
f=f_0e^{\sigma t}\left(\cos\omega t+i\sin\omega t\right).
$$

For real $f_0$ the real part is $f_0e^{\sigma t}\cos\omega t$. So $\sigma$ is a growth rate, unstable if positive and decaying if negative, and $\omega$ is a circular frequency in rad/s. The equation also describes real dynamics: the F-4C's short-period pitch oscillation, the response to a sudden pitch-up, follows it with $\lambda\approx-0.5+1.3i$, a decaying and therefore stable oscillation ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]). Writing the right-hand side as $R=\lambda f$ lets the same analysis apply to any scheme of the form $\mathrm df/\mathrm dt=R$.

## Worked examples

### One explicit and one implicit step by hand

*(Flagged for the exam.)* For $\alpha=0.1$, $h=0.125$ and $\Delta t=0.06$,

$$
F=\frac{0.1\times0.06}{0.125^2}=\frac{0.006}{0.015625}=0.384.
$$

Start from $T^0=(1200,300,300,\dots,300)$.

Explicit step. At $j=1$:

$$
T_1^1=300+0.384\,(1200-2\times300+300)=300+0.384\times900=645.6\ \mathrm K.
$$

At $j=2$, $T_2^1=300+0.384(300-600+300)=300$, and likewise every other interior point stays at 300 K, so $T_8^1=T_7^1=300$ K. Heat has moved exactly one grid point.

Implicit step. Each interior row reads $-0.384T_{j-1}^1+1.768T_j^1-0.384T_{j+1}^1=300$, with $T_0^1=1200$ and $T_8^1=T_7^1$. Solving the $9\times9$ system gives

$$
T^1=(1200,\ 505.7,\ 347.0,\ 310.7,\ 302.5,\ 300.6,\ 300.1,\ 300.04,\ 300.04)\ \mathrm K.
$$

Every point has warmed, however slightly, in a single step.

> [!check] Substituting back
> Row 1: $-0.384\times1200+1.768\times505.685-0.384\times347.007=-460.80+894.05-133.25=300.00$, the old value $T_1^0$. The implicit step gives less heating at $j=1$ (505.7 K against 645.6 K) because it spreads the same heat input over the whole wall at once.

### The heating of the capsule's inner wall

$\alpha=0.1$, $N=8$, run to $t=0.72$; inner-wall temperature $T_8$:

| Scheme | $\Delta t$ | $F$ | $T_8$ (K) | Error against 330.3 K |
|---|---|---|---|---|
| explicit | 0.06 | 0.384 | 325.06 | −5.2 |
| explicit | 0.03 | 0.192 | 327.82 | −2.4 |
| explicit | 0.015 | 0.096 | 329.09 | −1.2 |
| explicit | 0.0006 | 0.004 | 330.26 | reference |
| implicit | 0.06 | 0.384 | 334.60 | +4.3 |
| implicit | 0.03 | 0.192 | 332.55 | +2.3 |
| implicit | 0.015 | 0.096 | 331.45 | +1.2 |
| implicit | 0.12 | 0.768 | 338.22 | +8.0 |
| implicit | 0.24 | 1.536 | 344.06 | +13.8 |
| implicit | 0.72 (one step) | 4.608 | 357.86 | +27.6 |

Halving $\Delta t$ halves both columns of error. With $\Delta t=0.12$ the explicit scheme has $F=0.768$ and its largest temperature passes $7\times10^4$ K within 12 steps; the implicit scheme at the same step is merely 8 K out.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- Next: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Concepts: [[Explicit and Implicit Time Integration]] · [[CFL and Fourier Numbers]] · [[CFD Boundary Conditions]]
- Higher-order time stepping: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Eigenvalues and dynamic modes: [[Characteristic Equation and Eigenvalues]]

## Sources

- `All_lectures_as_delivered.pdf`, L5 (slides 7–12; slides 2–6 repeat the Gauss–Seidel and SOR material of A3), with transcript `SESA2029 Lecture 2025-10-16.txt`, ll. 241–620 (Prof N. Sandham; Python demonstrations on Blackboard)
- Hand steps, the table, the stability runs, the PDE series solution and the grid study recomputed in Python. Figures: `01 - Notes/Figures/generate_dam_a4_figures.py`

## Self-study tasks

### Core

- [ ] Discretise the unsteady heat equation explicitly and implicitly (flagged for the exam, 2025-10-16, l. 269). → [[#2. The explicit scheme]] · [[#3. The implicit scheme]]
- [ ] One explicit and one implicit step by hand (example sheet). → [[#One explicit and one implicit step by hand]] · [[SESA2029 CFD Worked Examples#Q5: Explicit and implicit steps for the unsteady heat equation|Worked examples Q5]]
- [ ] Run the explicit and implicit codes and find the stability limit and the order of accuracy yourself (2025-10-16, ll. 601–623; the example sheet suggests tests). → [[#The heating of the capsule's inner wall]]

### Further practice

- [ ] Show from Taylor series that forward and backward Euler are first order with opposite errors, and explain the sign from the shape of the heating curve (suggested, not lecturer-set). → [[#Why both are first order, with opposite errors]]
- [ ] Explain the difference between Dirichlet and Neumann conditions, with a CFD example of each. → [[#1. Set-up and boundary conditions]]
- [ ] Show that $f=f_0e^{\lambda t}$ solves $\mathrm df/\mathrm dt=\lambda f$ and interpret complex $\lambda$ (asked of the class, 2025-10-16, ll. 511–600). → [[#5. The model equation for stability]]

## Transcript and slide slips

> [!warning] Slide slip: implicit discretisation (L5 slide 8)
> Where: [[#3. The implicit scheme]].
>
> The first line of the implicit scheme prints the right-hand side as $\alpha(T_{j-1}^{n+1}-2T_j^{n+1}+T_{j-1}^{n+1})/h^2$, with $j-1$ twice. The last term is $T_{j+1}^{n+1}$, as in the rearranged line below it and on slide 10.

> [!warning] Transcript slips (2025-10-16)
> Where: [[#4. What the experiments show]].
>
> | Line | Transcript says | Correct |
> |---|---|---|
> | l. 425 | "go back to 0.016 and 12" | $\Delta t=0.06$ and 12 steps, the default case |
> | l. 436 | "0.08. That was a Fourier number of 0.64" | $\Delta t=0.10$ gives $F=0.64$; $\Delta t=0.08$ gives $F=0.512$, as said next |
> | l. 478 | the one-step implicit answer is "now up to 350" | 357.9 K, against 330.3 K |
