---
title: "MATH2048 PDE3 - The Heat Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 12
tags:
  - math2048
  - pdes
  - heat-equation
  - separation-of-variables
aliases: ["MATH2048 Lecture 17", "Diffusion equation", "Random walk derivation"]
date: 2026-10-30
status: lectured
coverage: "Lecture 17 (5 Nov 2024, Ian Hawke): the heat equation derived from a random walk on a grid, why diffusion scales as dx^2/dt, and separation of variables for an insulated rod with u(x, 0) = x(1 - x)."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]"]
next_topics: ["[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
key_concepts: ["[[Heat Equation]]", "[[Separation of Variables]]", "[[ODE Eigenvalue Problems]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 17.txt", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture17_Parabolic1.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 6)"]
---

# MATH2048 PDE3 - The Heat Equation

> [!abstract] Summary
> The heat (or diffusion) equation $y_t=\kappa^2y_{xx}$ is what a random walk becomes on large scales: particles that hop left or right at random, averaged over many hops with $\Delta x^2/\Delta t$ held fixed. Separation of variables works exactly as for the wave equation, with the same spatial eigenvalue problem, but the time equation is first order, so each mode decays as $e^{-(n\pi\kappa)^2t}$ instead of oscillating. With insulated ends, every mode except the constant one dies away and the rod settles to the mean of its initial temperature.

> [!summary]- Exam use: quick path
> - **Use it when:** a heat or diffusion equation on a finite interval has homogeneous boundary conditions (2023/24 A2; PS7 Q1–Q2).
> - **Assumptions:** constant $\kappa^2>0$; homogeneous linear boundary conditions; one initial condition, on $y$ only.
> - **Method:** 1. Separate: $X''-\lambda X=0$ and $\dot T-\lambda\kappa^2T=0$. 2. Solve the eigenvalue problem for $X$ with the boundary conditions, all three cases. 3. Solve $\dot T_n=\lambda_n\kappa^2T_n$ to get $e^{\lambda_n\kappa^2t}$. 4. Superpose. 5. Match $y(x,0)$ with a half-range series, or by inspection if it is already a sum of eigenfunctions.
> - **Common mistakes:** copying the wave equation's $\cos$ and $\sin$ in time, when the heat equation gives a decaying exponential; dropping the $\lambda=0$ constant mode with insulated ends.
> - **Practise:** [[#Separating the insulated rod]] · [[#3. The 2023-24 exam, question A2]]

Parabolic equations ([[MATH2048 PDE1 - Classification of PDEs and the Wave Equation|PDE1]]) are what averaging over small-scale behaviour too complicated to follow gives, and the prototype is diffusion: heat spreading through a rod, or a dye spreading through water. The separation of variables of [[MATH2048 PDE2 - Separation of Variables for the Wave Equation|PDE2]] carries over with a single change.

That change is in the time equation. The heat equation has one time derivative, so it needs only one initial condition, the initial temperature, and its time behaviour is exponential decay. Each spatial mode fades at a rate that grows like $n^2$, so the fine detail in the initial data disappears first and the solution smooths out, as in the right-hand panel of the figure in [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation|PDE1]].

---

## 1. Deriving the heat equation from a random walk

The model is of gas particles in a pipe that can only sit at grid points $x$, $x\pm\Delta x,\dots$ and only move at times $t$, $t+\Delta t,\dots$. Let $y(x,t)$ be the number of particles at $x$ at time $t$. At each time step every particle flips two coins. If they differ it stays put, with probability $\frac12$; two heads move it one step left and two tails one step right, each with probability $\frac14$.

Particles arrive at $x$ at time $t+\Delta t$ in only three ways: half of those already at $x$ stay, a quarter of those at $x-\Delta x$ step right, and a quarter of those at $x+\Delta x$ step left. So, exactly on the grid,

$$
y(x,t+\Delta t)=\tfrac14\,y(x+\Delta x,t)+\tfrac14\,y(x-\Delta x,t)+\tfrac12\,y(x,t).
$$

On scales much larger than $\Delta x$ and $\Delta t$, Taylor-expand both sides. The left side, in time:

$$
y(x,t+\Delta t)=y+\Delta t\,y_t+\tfrac12\Delta t^2\,y_{tt}+\dots
$$

The right side, in space, with everything evaluated at $(x,t)$:

$$
\tfrac14\Big[\big(y+\Delta x\,y_x+\tfrac12\Delta x^2y_{xx}\big)+\big(y-\Delta x\,y_x+\tfrac12\Delta x^2y_{xx}\big)+2y\Big]+\dots
$$

Inside the bracket the four copies of $y$ make $4y$, which the $\frac14$ turns back into $y$; the first derivatives cancel; and the two half second-derivative terms add to $\Delta x^2y_{xx}$. So the right side is

$$
y+\frac{\Delta x^2}{4}\,y_{xx}+\dots
$$

Cancel $y$ from both sides and divide by $\Delta t$:

$$
y_t+\tfrac12\Delta t\,y_{tt}+\dots=\frac{\Delta x^2}{4\,\Delta t}\,y_{xx}+\dots
$$

Let $\Delta x$ and $\Delta t$ go to zero together with $\Delta x^2/\Delta t$ held fixed. The $\Delta t\,y_{tt}$ term and the higher-order terms vanish, and with $\kappa^2=\lim\frac{\Delta x^2}{4\Delta t}>0$,

$$
\frac{\partial y}{\partial t}=\kappa^2\frac{\partial^2y}{\partial x^2}.
$$

> [!check] The spread of the walkers
> Each step moves a particle by $-\Delta x$, $0$ or $+\Delta x$ with probabilities $\frac14,\frac12,\frac14$, so its mean is $0$ and its variance is $\frac12\Delta x^2$. After $N=t/\Delta t$ independent steps the variance is $\frac{N\Delta x^2}{2}=2\cdot\frac{\Delta x^2}{4\Delta t}\,t=2\kappa^2t$, exactly the variance of the spreading Gaussian solution of $y_t=\kappa^2y_{xx}$. A simulation of $2\times10^4$ walkers for 400 steps gives a variance of $198.9$ grid units squared against the predicted $200$.

![[m2048_pde_random_walk.png|820]]

In the limit $\Delta x^2/\Delta t$ stays constant; for the wave equation it was $\Delta x/\Delta t$, a speed. Diffusion over a distance $\ell$ therefore takes a time of order $\ell^2/\kappa^2$, so doubling the distance quadruples the time, and diffusion problems live on long time scales compared with their length scales. There are many other derivations, from conservation of heat for example, and they all lead to the same equation.

## 2. Separation of variables for the heat equation

### Separating the insulated rod

Solve $y_t=\kappa^2y_{xx}$ on $0<x<1$ with insulated ends, $y_x(0,t)=y_x(1,t)=0$, and initial temperature $y(x,0)=x(1-x)$. This is the Neumann problem from [[MATH2048 PDE2 - Separation of Variables for the Wave Equation#Changing to Neumann ends|PDE2]] with two changes: one time derivative instead of two, and so only one initial condition. Insulated means no heat flows through the ends, and the heat flux is proportional to $-y_x$.

**Step 1.** Substitute $y=X(x)T(t)$:

$$
X\dot T=\kappa^2X''T .
$$

Divide by $\kappa^2XT$:

$$
\frac1{\kappa^2}\frac{\dot T}{T}=\frac{X''}{X}=\lambda ,
$$

so

$$
X''-\lambda X=0,\qquad\dot T-\lambda\kappa^2T=0 .
$$

The $X$ equation is identical to the wave case; the $T$ equation is not, because the PDE has changed.

**Steps 2 and 3.** The boundary conditions give $X'(0)T=0$ and $X'(1)T=0$, so $X'(0)=X'(1)=0$, exactly as before, since this depends only on the boundary conditions and the ansatz. The eigenvalue problem is therefore the same as PDE2's Neumann problem, which is one reason to keep the constants on the time side: the spatial problem then looks the same whatever the PDE. The three cases are run again, as in every eigenvalue problem:

- $\lambda=0$: $X=Ax+B$, $X'=A=0$, so $X_0=$ constant is a mode.
- $\lambda=k^2>0$: $X'=k(Ce^{kx}-De^{-kx})$; $X'(0)=0$ gives $C=D$, then $X'(1)=kC(e^k-e^{-k})=0$ forces $C=0$, and only the zero solution remains.
- $\lambda=-k^2<0$: $X'=k(-E\sin kx+F\cos kx)$; $X'(0)=kF=0$ gives $F=0$, and $X'(1)=-kE\sin k=0$ gives $k=n\pi$.

So $\lambda_n=-(n\pi)^2$ with $X_n=\cos n\pi x$ for $n=0,1,2,\dots$, where $n=0$ is the constant mode.

**Step 4.** Now the time equation. For $\lambda=0$, $\dot T_0=0$, so $T_0$ is a constant. For $\lambda_n=-(n\pi)^2$,

$$
\dot T_n+(n\pi\kappa)^2T_n=0 .
$$

This is first order and separable (or use an integrating factor). Divide by $T_n$:

$$
\frac{\dot T_n}{T_n}=-(n\pi\kappa)^2 .
$$

The left side is $\frac{d}{dt}\ln T_n$. Integrate:

$$
\ln T_n=-(n\pi\kappa)^2t+\text{const},
$$

and exponentiate:

$$
T_n=G_n\,e^{-(n\pi\kappa)^2t}.
$$

**Step 5.** Multiply matching modes and add them up, writing the constant mode as $\frac12a_0$ in anticipation of a Fourier series:

$$
y(x,t)=\tfrac12a_0+\sum_{n=1}^\infty a_n\cos n\pi x\;e^{-(n\pi\kappa)^2t}.
$$

Compared with the wave equation, the only differences come from the $T$ equation: $T_0$ is a constant rather than $Gt+H$, and each $T_n$ is a decaying exponential rather than a cosine and a sine.

**Step 6.** At $t=0$ every exponential is 1, so $x(1-x)$ must equal the cosine series $\frac12a_0+\sum a_n\cos n\pi x$. The constant term:

$$
a_0=2\int_0^1x(1-x)\,dx=2\Big[\frac{x^2}2-\frac{x^3}3\Big]_0^1=2\Big(\frac12-\frac13\Big)=\frac13 .
$$

For $a_n$, integrate by parts twice, differentiating the polynomial:

$$
a_n=2\int_0^1x(1-x)\cos n\pi x\,dx=2\left(\Big[x(1-x)\frac{\sin n\pi x}{n\pi}\Big]_0^1-\int_0^1(1-2x)\frac{\sin n\pi x}{n\pi}\,dx\right).
$$

The bracket vanishes because $\sin n\pi=0$. The second integration by parts:

$$
a_n=2\left(\Big[(1-2x)\frac{\cos n\pi x}{(n\pi)^2}\Big]_0^1+\int_0^1\frac{2\cos n\pi x}{(n\pi)^2}\,dx\right).
$$

The last integral gives sines at $0$ and $1$, which vanish. The bracket is $\frac{-(-1)^n}{(n\pi)^2}-\frac{1}{(n\pi)^2}$, so

$$
a_n=-\frac{2\big(1+(-1)^n\big)}{(n\pi)^2}.
$$

The solution is

$$
y(x,t)=\frac16-\sum_{n=1}^\infty\frac{2\big(1+(-1)^n\big)}{(n\pi)^2}\cos n\pi x\;e^{-(n\pi\kappa)^2t}.
$$

Only even $n$ contribute. As $t\to\infty$ every exponential dies and $y\to\frac16$, the average of $x(1-x)$ over the rod. With insulated ends no heat gets in or out, so the total heat $\int_0^1y\,dx$ never changes and the rod ends up uniform at the initial mean. That can be shown straight from the PDE, without the series. Differentiate the total heat and use the PDE inside the integral:

$$
\frac{d}{dt}\int_0^1y\,dx=\int_0^1y_t\,dx=\kappa^2\int_0^1y_{xx}\,dx=\kappa^2\big[y_x\big]_0^1=\kappa^2\big(y_x(1,t)-y_x(0,t)\big)=0 .
$$

So $\int_0^1y\,dx$ keeps its initial value $\int_0^1x(1-x)\,dx=\frac16$, and since the rod is $1$ long, a uniform final state must sit at $\frac16$. Every $\cos n\pi x$ with $n\geq1$ integrates to zero over the rod, which is the series' version of the same fact.

> [!check] Decay rates
> With $\kappa=1$, the first surviving mode, $n=2$, decays as $e^{-4\pi^2t}=e^{-39.5t}$, so its amplitude halves in $\ln2/39.5=0.018$ time units; the $n=4$ mode decays 4 times faster again. That is why the right-hand panel below is already almost flat at $t=0.07$. At $x=\frac12$, $t=0.01$, 400 terms give $y=0.2300$, down from the initial $0.25$. SymPy confirms the coefficients, which are the same integrals as in PDE2's Neumann wave example.

![[m2048_pde_heat_dirichlet_vs_neumann.png|900]]

The left-hand panel (a case not lectured) uses the same initial data with fixed-temperature ends $y(0,t)=y(1,t)=0$: there the sine modes are used, there is no constant mode, and heat leaks out of the ends until the rod is at zero everywhere. Steps 1 and 4 are unchanged; steps 2–3 are PDE2's fixed-end eigenproblem, $X_n=\sin n\pi x$; and step 6 is PDE2's sine series of $x(1-x)$, so

$$
y=\sum_{n=1}^\infty\frac{4\big(1-(-1)^n\big)}{(n\pi)^3}\sin n\pi x\;e^{-(n\pi\kappa)^2t}.
$$

Here the slowest mode is $n=1$, decaying as $e^{-\pi^2\kappa^2t}$, four times slower than the insulated rod's $n=2$.

### A decay term removed by a substitution (PS7 Q2)

PS7 Q2 adds a loss term, $u_t=h^2u_{xx}-ku$ on $0\leq x\leq1$, with $u(0,t)=u(1,t)=0$ and $u(x,0)=x(1-x)$; physically, heat also leaks out through the sides of the rod at a rate proportional to its temperature. Substitute $u=e^{-kt}v$. By the product rule,

$$
u_t=e^{-kt}v_t-ke^{-kt}v,\qquad u_{xx}=e^{-kt}v_{xx}.
$$

Substitute into the PDE:

$$
e^{-kt}v_t-ke^{-kt}v=h^2e^{-kt}v_{xx}-ke^{-kt}v .
$$

The $-ke^{-kt}v$ terms cancel, and dividing by $e^{-kt}\neq0$ leaves $v_t=h^2v_{xx}$, the plain heat equation. The data carry over unchanged: $v=e^{kt}u$ vanishes wherever $u$ does, so $v(0,t)=v(1,t)=0$, and at $t=0$, $e^{0}=1$, so $v(x,0)=x(1-x)$. That is the fixed-end problem just solved with $\kappa=h$, so

$$
u=e^{-kt}\sum_{n=1}^\infty\frac{4\big(1-(-1)^n\big)}{(n\pi)^3}\sin n\pi x\;e^{-(n\pi h)^2t}.
$$

Every mode now decays at the rate $(n\pi h)^2+k$: the loss through the sides adds the same amount to every decay rate.

> [!check] Against a direct numerical solution
> With $h=1$, $k=2$, at $x=\frac12$, $t=0.05$ the series gives $u=e^{-0.1}\times0.15740=0.14242$; an explicit finite-difference solution of $u_t=u_{xx}-2u$ on 400 cells gives $0.14242$.

## 3. The 2023-24 exam, question A2

Solve $u_t=\frac14u_{xx}$ on $0\leq x\leq\pi$ with $u_x(0,t)=u_x(\pi,t)=0$ and $u(x,0)=\cos^3x$.

Separating, $4\frac{\dot T}{T}=\frac{X''}{X}=\lambda$, so $X''-\lambda X=0$ and $\dot T-\frac14\lambda T=0$. The eigenvalue problem is the insulated one on $[0,\pi]$, so $\lambda_n=-n^2$ and $X_n=\cos nx$ for $n=0,1,2,\dots$; the case $n=0$ is the constant mode. Then $\dot T_n=-\frac{n^2}4T_n$ gives $T_n=e^{-n^2t/4}$, and

$$
u=\sum_{n=0}^\infty A_n\cos nx\;e^{-n^2t/4}.
$$

At $t=0$ this must equal $\cos^3x$. Rather than integrate, write $\cos^3x$ as a sum of eigenfunctions using the hint's identities:

$$
\cos^3x=\cos x\cdot\tfrac12(1+\cos2x)=\tfrac12\cos x+\tfrac12\cos x\cos2x .
$$

$$
\cos x\cos2x=\tfrac12(\cos3x+\cos x),
$$

so

$$
\cos^3x=\tfrac34\cos x+\tfrac14\cos3x .
$$

By uniqueness, $A_1=\frac34$, $A_3=\frac14$ and every other $A_n=0$:

$$
u=\tfrac34\cos x\;e^{-t/4}+\tfrac14\cos3x\;e^{-9t/4}.
$$

The mean of $\cos^3x$ over $[0,\pi]$ is zero, so here the rod tends to zero temperature. A quick check: at $t=0$, $x=0$ the solution is $\frac34+\frac14=1=\cos^30$, and $u_x=-\frac34\sin x\,e^{-t/4}-\frac34\sin3x\,e^{-9t/4}$ vanishes at $x=0$ and $x=\pi$.

### By inspection (PS7 Q1)

PS7 Q1 is the same insulated problem with $u(x,0)=7+5\cos2x$. The initial data is already a sum of eigenfunctions, $7$ being the $n=0$ mode and $5\cos2x$ the $n=2$ mode, so uniqueness gives $A_0=7$, $A_2=5$ and nothing else. With $T_2=e^{-4t/4}=e^{-t}$,

$$
u=7+5\cos2x\;e^{-t},
$$

and the rod relaxes to its mean temperature $7$.

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]] · Next: [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]
- Concepts: [[Heat Equation]] · [[Separation of Variables]] · [[ODE Eigenvalue Problems]] · [[Half-Range Expansions]]
- Practice: [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] · [[MATH2048 Past Paper Solutions]]

## Sources

- Lecture 17 (5 Nov 2024) recording, Ian Hawke: `MATH2048 Lecture 17.txt`
- Slides `Lecture17_Parabolic1.pdf`; lecture notes Ch. 6
- Problem Sheet 7; 2023/24 exam question A2 and its published solutions

## Self-study tasks

Nothing was explicitly set in Lecture 17. The problem-sheet and past-paper questions on it:

### Core

- [ ] PS7 Q1: $u_t=\frac14u_{xx}$ on $[0,\pi]$, insulated ends, $u(x,0)=7+5\cos2x$. Answer: $u=7+5\cos2x\,e^{-t}$, by inspection. → [[#By inspection (PS7 Q1)]]
- [ ] 2023/24 A2: insulated rod with $u(x,0)=\cos^3x$, all four parts. → [[#3. The 2023-24 exam, question A2]]
- [ ] Rederive the heat equation from the random walk without notes, and say why $\Delta x^2/\Delta t$ is held fixed (suggested, not lecturer-set). → [[#1. Deriving the heat equation from a random walk]]

### Further practice

- [ ] PS7 Q2: the heat equation with a decay term, $u_t=h^2u_{xx}-ku$. → [[#A decay term removed by a substitution (PS7 Q2)]]
- [ ] Solve the insulated-rod example again with fixed ends $y(0,t)=y(1,t)=0$ and compare with the left panel of the figure. Answer: $y=\sum\frac{4(1-(-1)^n)}{(n\pi)^3}\sin n\pi x\,e^{-(n\pi\kappa)^2t}$ (suggested, not lecturer-set). → [[#Separating the insulated rod]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lecture 17
> | Where | Transcript says | Correct |
> |---|---|---|
> | l. 52 | "If they both turn up the same, then sorry, if they turn up differently" | corrected immediately: different faces mean the particle stays |
> | l. 74 | "tailor series" | Taylor series |
> | l. 186 | "t dot minus kappa squared t is equal to 0" | $\dot T-\lambda\kappa^2T=0$; the lecturer restores the $\lambda$ at ll. 274–277 |
> | l. 221 | constants named "the wrong way around" | naming only; $X=Ax+B$ with $X_0=B$ |
