---
title: "MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 13
tags:
  - math2048
  - pdes
  - heat-equation
  - eigenfunction-expansion
aliases: ["MATH2048 Lecture 18", "MATH2048 Lecture 19", "Eigenfunction expansion", "Source terms", "Steady-state subtraction"]
date: 2026-10-30
status: lectured
coverage: "Lecture 18 (6 Nov 2024): why separation fails with a source, the eigenfunction-expansion method, integrating factors, and y_t = y_xx + x(1 - x) with fixed ends. Lecture 19 (11 Nov 2024): constant boundary values removed by the steady state, time-dependent boundary values turned into a source, and a rod whose end is heated periodically. Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE3 - The Heat Equation]]", "[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
next_topics: ["[[MATH2048 PDE5 - Laplace's Equation]]"]
key_concepts: ["[[Eigenfunction Expansion Method]]", "[[Heat Equation]]", "[[Separation of Variables]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 18.txt", "02 - Sources/Lectures/MATH2048 Lecture 19.txt", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture18_Parabolic2.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture19_Parabolic3.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Appendix-PDE_additional slides.pdf"]
---

# MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions

> [!abstract] Summary
> With a source term, $y_t=\kappa^2y_{xx}+F(x,t)$, the separation ansatz fails, but the eigenfunctions of the homogeneous problem still fit the boundary conditions. Expanding both the solution and the source in those eigenfunctions, $y=\sum T_n(t)X_n(x)$ and $F=\sum F_n(t)X_n(x)$, turns the PDE into one first-order ODE per mode, $\dot T_n+(n\pi\kappa)^2T_n=F_n$. Non-zero boundary values are removed first by subtracting a function $y_p$ that satisfies them; what is left has homogeneous boundary conditions and, in general, a new source $-\partial_ty_p$.

> [!summary]- Exam use: quick path
> - **Use it when:** a heat or wave equation has a source $F(x,t)$, or boundary values that are not zero (2024/25 A2; PS7 Q3–Q4).
> - **Assumptions:** linear PDE; the source cannot depend on $y$; boundary values of the same type at each end as the eigenfunctions you use.
> - **Method:** 1. If the boundary values are non-zero, subtract $y_p$, linear in $x$, that matches them; put $-\partial_ty_p$ into the source and $y(x,0)-y_p(x,0)$ into the initial data. 2. Solve the homogeneous eigenvalue problem for $X_n$. 3. Expand the source: $F_n=\frac2L\int_0^LF\,X_n\,dx$, or by inspection. 4. Solve each $T_n$ ODE (integrating factor, or undetermined coefficients). 5. Fit the initial data; add $y_p$ back.
> - **Common mistakes:** trying to separate $y=XT$ when the PDE has a source; forgetting to subtract $y_p(x,0)$ from the initial data.
> - **Practise:** [[#A heated rod with fixed ends (L18)]] · [[#A rod with a periodically heated end (L19)]] · [[#3. The 2024-25 exam, question A2]]

So far the rod has been left alone: an initial temperature, ends held at zero (or insulated), and no heating. Lecture 18 adds heating inside the rod, such as a heater placed in the middle, and Lecture 19 heats it through the ends instead (L18, ll. 15–32). Both are called inhomogeneous problems, which the lecturer conceded is "just the annoying feature" (L19, l. 13). The heat equation is used because one time derivative keeps the algebra short, but everything carries over to the wave equation.

The two lectures fit together. A source inside the domain is handled by expanding in eigenfunctions, which needs homogeneous boundary conditions. Non-zero boundary conditions are then handled by subtracting something that absorbs them, which leaves homogeneous boundary conditions and, usually, a source. So any combination comes down to the Lecture 18 method.

---

## 1. Source terms: expanding in eigenfunctions (L18)

### Why separation fails

Try $y=X(x)T(t)$ in $y_t=\kappa^2y_{xx}+F(x,t)$ and divide by $XT$ (ll. 35–51):

$$
\frac{\dot T}{T}=\kappa^2\frac{X''}{X}+\frac{F(x,t)}{X(x)T(t)}.
$$

The last term depends on both $x$ and $t$ in general, so the two sides are no longer functions of different variables and nothing forces them to be constant. The ansatz in this naive form does not work.

### The eigenfunction expansion

Look instead at what the homogeneous solution was, before $T_n$ was solved for (ll. 51–74). With fixed ends it was $y=\sum T_n(t)\sin n\pi x$. Each $\sin n\pi x$ vanishes at $x=0$ and $x=1$, so any such sum satisfies the boundary conditions automatically. Changing the PDE changes how the $T_n$ behave, not the boundary conditions, so the solution should still be a sum of the same sines. With insulated ends it would be cosines. So guess

$$
y(x,t)=\sum_{n=1}^\infty T_n(t)\sin n\pi x,\qquad F(x,t)=\sum_{n=1}^\infty F_n(t)\sin n\pi x .
$$

$F$ is known, so at each fixed $t$ the second sum is just its Fourier sine series, with

$$
F_n(t)=2\int_0^1F(x,t)\sin n\pi x\,dx .
$$

Substitute into the PDE (ll. 86–126). The time derivative acts on the $T_n$, and two $x$-derivatives of $\sin n\pi x$ give $-(n\pi)^2\sin n\pi x$:

$$
\sum_{n=1}^\infty\dot T_n\sin n\pi x=-\sum_{n=1}^\infty(n\pi\kappa)^2T_n\sin n\pi x+\sum_{n=1}^\infty F_n\sin n\pi x .
$$

Every sum is in the same sines, so collect them on one side:

$$
\sum_{n=1}^\infty\Big[\dot T_n+(n\pi\kappa)^2T_n-F_n\Big]\sin n\pi x=0 .
$$

At each $t$ this is a sine series for the zero function, and by uniqueness, or orthogonality, every coefficient is zero (ll. 128–140):

$$
\dot T_n+(n\pi\kappa)^2T_n=F_n(t).
$$

The PDE has become one ODE per mode, with the known $F_n$ as forcing.

### Solving for each mode with an integrating factor

Each equation is first order, linear, constant-coefficient and inhomogeneous, so use an integrating factor (ll. 164–207). Multiply by $e^{(n\pi\kappa)^2t}$. By the product rule,

$$
\frac{d}{dt}\Big[e^{(n\pi\kappa)^2t}T_n\Big]=e^{(n\pi\kappa)^2t}\Big[\dot T_n+(n\pi\kappa)^2T_n\Big]=e^{(n\pi\kappa)^2t}F_n(t).
$$

Integrate in time:

$$
e^{(n\pi\kappa)^2t}T_n=C_n+\int^te^{(n\pi\kappa)^2s}F_n(s)\,ds,
$$

so

$$
T_n=e^{-(n\pi\kappa)^2t}\Big[C_n+\int^te^{(n\pi\kappa)^2s}F_n(s)\,ds\Big].
$$

The $C_n$ term is the familiar decaying mode; the integral is the response to the source, and it need not decay (ll. 205–207). The constants $C_n$ come from the initial data, which at $t=0$ is again a sine series.

### A heated rod with fixed ends (L18)

Solve $y_t=y_{xx}+x(1-x)$ with $y(0,t)=y(1,t)=0$ and $y(x,0)=x(1-x)$, so $\kappa=1$ and a steady heat source peaked in the middle (ll. 225–340). The source is the function whose sine series was found in [[MATH2048 PDE2 - Separation of Variables for the Wave Equation#Guitar string with fixed ends (L16)|PDE2]], chosen "because we're too lazy to compute another set Fourier series" (l. 290):

$$
F_n=\frac{4\big(1-(-1)^n\big)}{(n\pi)^3},
$$

constant in time. With $F_n$ constant the integral is easy (ll. 248–278):

$$
T_n=e^{-(n\pi)^2t}\Big[C_n+\frac{F_n}{(n\pi)^2}e^{(n\pi)^2t}\Big]=C_ne^{-(n\pi)^2t}+\frac{F_n}{(n\pi)^2}.
$$

The initial data $x(1-x)$ has the same sine coefficients, $F_n$ (ll. 286–297). The two functions are the same here by choice; in general the initial-data coefficients and the source coefficients are unrelated. At $t=0$:

$$
F_n=C_n+\frac{F_n}{(n\pi)^2}\quad\Longrightarrow\quad C_n=F_n\Big(1-\frac1{(n\pi)^2}\Big).
$$

Only odd $n$ survive, where $F_n=\frac8{(n\pi)^3}$, so

$$
y(x,t)=\sum_{n\text{ odd}}\left[\frac{8}{(n\pi)^3}\Big(1-\frac1{(n\pi)^2}\Big)e^{-(n\pi)^2t}+\frac{8}{(n\pi)^5}\right]\sin n\pi x .
$$

Two kinds of term appear (ll. 314–340). The ones multiplied by $e^{-(n\pi)^2t}$ are transients: the $\frac8{(n\pi)^3}$ part is exactly the unforced decay of PDE3, and the $-\frac8{(n\pi)^5}$ correction is there because the initial data doesn't match the final state. The term without an exponential, $\sum\frac8{(n\pi)^5}\sin n\pi x$, is what remains as $t\to\infty$: the steady state, in which heat leaking out through the ends balances the heat put in, more of it in the middle.

> [!check] The steady state directly
> Setting $y_t=0$ gives $y''=-x(1-x)$ with $y(0)=y(1)=0$. Integrating twice gives $y_s=\frac{x^4}{12}-\frac{x^3}6+\frac x{12}$, and SymPy finds its sine coefficients are $\frac{4(1-(-1)^n)}{(n\pi)^5}$, exactly the non-decaying part of the series. The series also matches a finite-difference solution at $x=0.4$, $t=0.3$: $0.036217$ against $0.036217$.

![[m2048_pde_inhomogeneous_heat.png|760]]

The same steps work for the wave equation, except that each $T_n$ equation is second order, so it needs undetermined coefficients or variation of parameters instead of an integrating factor, and there are two constants per mode (ll. 341–350). The answer has the same structure: a part that balances the source, plus modes excited around it, which for waves need not decay.

## 2. Inhomogeneous boundary conditions (L19)

Now drop the source and make the boundary values non-zero: $y_t=\kappa^2y_{xx}$ with $y(0,t)=f_0(t)$ and $y(1,t)=f_1(t)$ (ll. 15–43). Separation fails at once. $y(0,t)=X(0)T(t)=f_0(t)$ says nothing about $X(0)$ by itself, so there is no eigenvalue problem to solve.

The fix borrows the particular integral from ODEs (ll. 44–48): find any function that deals with the awkward part, then work with the deviation from it.

### Constant boundary values: subtract the steady state

With constant end temperatures $y(0,t)=T_0$ and $y(1,t)=T_1$, the rod should settle to a steady state that joins the two (ll. 49–84). It satisfies the PDE with $y_t=0$, so $y''=0$ and $y=Ax+B$. The boundary values give $B=T_0$ and $A+B=T_1$, so

$$
y_p=(T_1-T_0)\,x+T_0 .
$$

Write $y=v+y_p$ (ll. 88–123). Since $y_p$ is steady, $\partial_ty_p=0$, and since it is linear, $\partial_x^2y_p=0$, so

$$
v_t=y_t=\kappa^2y_{xx}=\kappa^2(v_{xx}+\partial_x^2y_p)=\kappa^2v_{xx}.
$$

At the ends $v=y-y_p=T_0-T_0=0$ and $T_1-T_1=0$. So $v$ solves the heat equation with homogeneous Dirichlet conditions, which is PDE3, with initial data $v(x,0)=y(x,0)-y_p(x)$. As $t\to\infty$, $v\to0$ and $y\to y_p$. For Neumann ends the same idea works with $y_p$ chosen to match the given slopes instead (ll. 124–129).

### Time-dependent boundary values: a source appears

If $f_0$ and $f_1$ change with time there is no steady state, but any function that matches the boundary values will still remove them (ll. 141–165). The simplest interpolates linearly:

$$
y_p(x,t)=f_0(t)+\big[f_1(t)-f_0(t)\big]x .
$$

At $x=0$ it gives $f_0$ and at $x=1$ it gives $f_1$, so $v=y-y_p$ again vanishes at both ends. The change shows up in the PDE instead (ll. 166–182). $y_p$ is still linear in $x$, so $\partial_x^2y_p=0$, but now $\partial_ty_p\neq0$:

$$
v_t=y_t-\partial_ty_p=\kappa^2v_{xx}+F(x,t),\qquad F=-\partial_ty_p=-\dot f_0-(\dot f_1-\dot f_0)\,x .
$$

This is the Lecture 18 problem, a source with homogeneous boundary conditions. The lecturer stressed that $v$ obeying homogeneous boundary conditions always holds when the steps are done right; $v$ obeying the original PDE unchanged does not (ll. 115–116, 129).

The initial data can be handled in either order (ll. 183–195): solve for $v$, add $y_p$, then fit $y(x,0)$; or fit $v(x,0)=y(x,0)-y_p(x,0)$ first. The general default is the first, but the example uses the second.

### A rod with a periodically heated end (L19)

Solve $y_t=y_{xx}$ with $y(0,t)=\frac12(1-\cos t)$, $y(1,t)=0$ and $y(x,0)=0$ (ll. 196–227). The right end is held at zero while the left end's temperature rises and falls with period $2\pi$. Take

$$
y_p=\tfrac12(1-x)(1-\cos t),
$$

which is $\frac12(1-\cos t)$ at $x=0$ and $0$ at $x=1$. At $t=0$, $y_p=0$, so $v(x,0)=0$ too. The source is

$$
F=-\partial_ty_p=-\tfrac12(1-x)\sin t .
$$

Its sine coefficients (ll. 242–266), pulling $\sin t$ out of the $x$ integral:

$$
F_n=2\int_0^1\Big(-\tfrac12\Big)(1-x)\sin t\,\sin n\pi x\,dx=\sin t\int_0^1(x-1)\sin n\pi x\,dx .
$$

Integrate by parts:

$$
\int_0^1(x-1)\sin n\pi x\,dx=\Big[-(x-1)\frac{\cos n\pi x}{n\pi}\Big]_0^1+\int_0^1\frac{\cos n\pi x}{n\pi}\,dx .
$$

The last integral gives sines at $0$ and $1$, which vanish. The bracket is $0$ at $x=1$ and $-\frac1{n\pi}$ after subtracting its value at $x=0$, so

$$
F_n=-\frac{\sin t}{n\pi}.
$$

Each mode obeys (ll. 267–278)

$$
\dot T_n+(n\pi)^2T_n=-\frac{\sin t}{n\pi}.
$$

This time the lecturer used undetermined coefficients, which works for a first-order constant-coefficient ODE as well as a second-order one (ll. 286–334). The complementary function is $C_ne^{-(n\pi)^2t}$. The forcing is a sine, so try $T_p=A\sin t+B\cos t$:

$$
\dot T_p+(n\pi)^2T_p=\big(A+(n\pi)^2B\big)\cos t+\big((n\pi)^2A-B\big)\sin t .
$$

Match the cosines to zero and the sines to $-\frac1{n\pi}$:

$$
A=-(n\pi)^2B,\qquad(n\pi)^2A-B=-\big(1+(n\pi)^4\big)B=-\frac1{n\pi}.
$$

So

$$
B=\frac1{n\pi\big(1+(n\pi)^4\big)},\qquad A=-\frac{(n\pi)^2}{n\pi\big(1+(n\pi)^4\big)},
$$

and

$$
T_n=C_ne^{-(n\pi)^2t}+\frac{\cos t-(n\pi)^2\sin t}{n\pi\big(1+(n\pi)^4\big)}.
$$

With $v(x,0)=0$, each $T_n(0)=0$, so $C_n=-\frac1{n\pi(1+(n\pi)^4)}$ (ll. 343–353). Putting it together (ll. 354–366):

$$
y=\tfrac12(1-x)(1-\cos t)+\sum_{n=1}^\infty\frac{\cos t-(n\pi)^2\sin t-e^{-(n\pi)^2t}}{n\pi\big(1+(n\pi)^4\big)}\sin n\pi x .
$$

Unlike every previous example, this never settles (ll. 368–372). The exponentials die, but the boundary keeps forcing the rod for ever, so what remains is a periodic temperature that varies in both space and time.

![[m2048_pde_boundary_forcing.png|900]]

> [!check] Numbers
> SymPy confirms $F_n=-\frac1{n\pi}$ and that $T_n$ satisfies its ODE. At $x=0.4$, $t=0.3$ the series gives $0.0068618$ and a finite-difference solution $0.0068617$. The correction $v$ is tiny, because the forcing period $2\pi$ is long compared with the slowest decay time $1/\pi^2\approx0.1$: the rod has time to follow the straight line $y_p$ almost exactly, which is why the snapshots sit on their dashed lines.

## 3. The 2024-25 exam, question A2

Solve $u_{tt}=u_{xx}+\cos x$ on $0\leq x\leq\pi$ with insulated ends $u_x(0,t)=u_x(\pi,t)=0$, $u(x,0)=\cos x+\cos3x$ and $u_t(x,0)=0$.

The homogeneous problem with these ends has $X_0=$ constant and $X_n=\cos nx$, as in [[MATH2048 PDE3 - The Heat Equation#3. The 2023-24 exam, question A2|PDE3]]. The source $\cos x$ is already one eigenfunction, so $F_1=1$ and every other $F_n=0$, with no integrals. Expanding $u=T_0+\sum T_n\cos nx$, substituting and using orthogonality:

$$
\ddot T_0=0,\qquad\ddot T_1+T_1=1,\qquad\ddot T_n+n^2T_n=0\ \ (n\geq2).
$$

So $T_0=A_0+B_0t$, $T_1=A_1\cos t+B_1\sin t+1$ (the $+1$ is the particular integral) and $T_n=A_n\cos nt+B_n\sin nt$. Zero initial velocity makes every $B_n$ zero, including $B_0$. At $t=0$,

$$
\cos x+\cos3x=A_0+(A_1+1)\cos x+\sum_{n\geq2}A_n\cos nx,
$$

so $A_0=0$, $A_1=0$, $A_3=1$ and the rest vanish:

$$
u=\cos x+\cos3x\cos3t .
$$

The $\cos x$ part is the static balance between the source and the curvature, $u_{xx}+\cos x=0$, and the $\cos3x$ part oscillates freely. The published solutions write the separated time equation as $\dot T-\lambda T=0$ and the velocity as $\frac{\partial u}{\partial x}$; both should be time derivatives, $\ddot T$ and $\frac{\partial u}{\partial t}$.

## Transcript slips

> [!warning] Lectures 18–19
> | Where | Transcript says | Correct |
> |---|---|---|
> | L18, ll. 25, 57 | "Richelieu boundary conditions" | Dirichlet |
> | L18, l. 88 | the PDE first written wrongly, then "time derivative equals kappa squared plus f" | $y_t=\kappa^2y_{xx}+F$ |
> | L18, l. 224 | "thurier series" | Fourier series |
> | L19, l. 1 | "pausing terms" | forcing terms |
> | L19, ll. 94–95 | $v=y_p-y$, "got that the wrong way around" | $v=y-y_p$ |
> | L19, l. 171 | $\partial_ty_p$ read out with the terms jumbled | $\partial_ty_p=\dot f_0+(\dot f_1-\dot f_0)x$ |
> | L19, ll. 304–320 | two attempts at $\dot T_p+(n\pi)^2T_p$ abandoned ("that's gibberish") | $(A+(n\pi)^2B)\cos t+((n\pi)^2A-B)\sin t$ |
> | L19, l. 321 | right-hand side "sine of t on n pi" | $-\frac{\sin t}{n\pi}$; the sign is restored at l. 327 |
> | L19, l. 339 | "a decaying exponential, e to the n pi squared t" | $e^{-(n\pi)^2t}$ |
> | L19, l. 371 | "dominated by the transient behavior, sorry" | dominated by the periodic forced response |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE3 - The Heat Equation]] · Next: [[MATH2048 PDE5 - Laplace's Equation]]
- Concepts: [[Eigenfunction Expansion Method]] · [[Heat Equation]] · [[Separation of Variables]] · [[Method of Undetermined Coefficients]]
- Practice: [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] · [[MATH2048 Past Paper Solutions]]

## Sources

- Lecture 18 (6 Nov 2024) and Lecture 19 (11 Nov 2024) recordings, Ian Hawke: `MATH2048 Lecture 18.txt`, `MATH2048 Lecture 19.txt`
- Slides `Lecture18_Parabolic2.pdf`, `Lecture19_Parabolic3.pdf`; the additional PDE slides
- PDE recap lecture (13 Nov 2024): `MATH2048 Lecture 2024-11-13.txt`, working the 2022/23 and 2023/24 A2 questions
- Problem Sheet 7; 2024/25 exam question A2 and its published solutions

## Self-study tasks

Nothing was explicitly set in either lecture; Lecture 18 pointed to the slides' write-up of the integrating-factor step (ll. 214–219).

### Core

- [ ] Rework the L18 heated rod and check that the non-decaying part is the steady state $\frac{x^4}{12}-\frac{x^3}6+\frac x{12}$ (suggested, not lecturer-set). → [[#A heated rod with fixed ends (L18)]]
- [ ] 2024/25 A2: the forced wave equation with insulated ends. → [[#3. The 2024-25 exam, question A2]]
- [ ] PS7 Q3: a source $f\sin^2\pi x$ switched on for $0<t<\tau$ in an insulated rod. Answer: final uniform temperature $\frac\tau2$, with the $\cos2\pi x$ mode decaying after switch-off. → [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]

### Further practice

- [ ] PS7 Q4: mixed conditions $u(0,t)=0$, $u_x(1,t)=C$, $u(x,0)=0$. Answer: $u=C\big\{x+\frac2{\pi^2}\sum\frac{(-1)^n}{(n-\frac12)^2}\sin(n-\tfrac12)\pi x\,e^{-(n-\frac12)^2\pi^2\kappa^2t}\big\}$. → [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]
- [ ] The 2022/23 exam A2, worked in the PDE recap lecture (13 Nov 2024, ll. 263–397): $y_t=y_{xx}+e^{-t}(1-x)$ on $[0,1]$ with insulated ends and $y(x,0)=0$. Answer: $y=\frac12(1-e^{-t})+\sum_{n\geq1}\frac{\hat f_n}{(n\pi)^2-1}\big(e^{-t}-e^{-(n\pi)^2t}\big)\cos n\pi x$ with $\hat f_n=\frac{2(1-(-1)^n)}{(n\pi)^2}$, the cosine coefficients of $1-x$. → [[#Solving for each mode with an integrating factor]]
- [ ] PS7 Q2: $u_t=h^2u_{xx}-ku$; substituting $u=e^{-kt}v$ removes the decay term. → [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]
- [ ] Redo the L19 example with $T_n$ found by an integrating factor instead of undetermined coefficients (suggested, not lecturer-set). → [[#A rod with a periodically heated end (L19)]]
