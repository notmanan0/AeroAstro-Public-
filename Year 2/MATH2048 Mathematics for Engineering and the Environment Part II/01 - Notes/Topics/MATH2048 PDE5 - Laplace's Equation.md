---
title: "MATH2048 PDE5 - Laplace's Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 14
tags:
  - math2048
  - pdes
  - laplace-equation
  - elliptic
aliases: ["MATH2048 Lecture 20", "Harmonic functions", "Maximum principle", "Poisson's equation"]
date: 2026-10-30
status: lectured
coverage: "Lecture 20 (12 Nov 2024, Ian Hawke): Laplace's and Poisson's equations as the static limits of the wave and heat equations, the Laplacian, separation of variables on the unit square with all sides held at zero and with u = x(1 - x) on one side, why all-Neumann problems are not unique, and the maximum principle. The PDE recap lecture (13 Nov 2024) worked past exam questions."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
next_topics: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]"]
key_concepts: ["[[Laplace's Equation]]", "[[Separation of Variables]]", "[[Divergence, Curl and the Laplacian]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 20.txt", "02 - Sources/Lectures/MATH2048 Lecture 2024-11-13.txt", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture20_LaplaceEquation1.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 7)"]
---

# MATH2048 PDE5 - Laplace's Equation

> [!abstract] Summary
> Laplace's equation $\nabla^2u=0$ is what the wave and heat equations become when nothing changes in time, so it describes static states, and every condition is a boundary condition. On a rectangle, separation of variables gives sines in one direction and hyperbolic functions, $\cosh$ and $\sinh$, in the other. With zero on every side the only solution is $u\equiv0$; with $u=x(1-x)$ on the top side, $u=\sum\frac{4(1-(-1)^n)}{(n\pi)^3\sinh n\pi}\sin n\pi x\,\sinh n\pi y$. Both illustrate the maximum principle: without sources, the largest and smallest values of $u$ are on the boundary.

> [!summary]- Exam use: quick path
> - **Use it when:** a steady-state problem on a rectangle has data on its sides, or you are asked where a solution of Laplace's equation can take its maximum.
> - **Assumptions:** Cartesian coordinates on a rectangle; homogeneous conditions on one opposite pair of sides; no source (or expand it as in PDE4).
> - **Method:** 1. Separate $u=X(x)Y(y)$ with $X''/X=-Y''/Y=\lambda$. 2. Solve the eigenvalue problem in the direction whose two sides are homogeneous. 3. Solve the other ODE with that $\lambda_n$: $Y_n=C_n\cosh n\pi y+D_n\sinh n\pi y$. 4. Use the homogeneous side in $y$ to remove one constant. 5. Fit the remaining side with a half-range series.
> - **Common mistakes:** solving the $y$ equation with trig functions when its sign makes it hyperbolic; giving Neumann conditions on every side, which leaves an undetermined constant.
> - **Practise:** [[#One side not held at zero (L20)]]

The wave equation propagates information without damping, because its time behaviour is undamped sines and cosines; the heat equation smooths it out, because its time behaviour is decaying exponentials (ll. 1–11). This lecture covers the third type, elliptic equations, with Laplace's equation as the prototype, and it is the one PDE in the block with no derivation (ll. 12–16).

A simple linear PDE is hyperbolic, parabolic, elliptic or mixed, and the lecturer's advice on mixed problems was to stay away from them (ll. 17–26). They usually mean the problem is trying to describe a transition between two kinds of physics at once, and they can often be avoided by restricting the domain or changing coordinates.

---

## 1. The Laplacian and the static limit (L20)

Elliptic equations have no time dependence, so all the variables are spatial coordinates, $x$, $y$, $z$ (ll. 27–46). They are written with the operator $\nabla^2$, called del squared or nabla squared. In Cartesian coordinates the gradient of a scalar $\phi$ is the vector of its derivatives,

$$
\nabla\phi=\frac{\partial\phi}{\partial x}\,\mathbf i+\frac{\partial\phi}{\partial y}\,\mathbf j+\frac{\partial\phi}{\partial z}\,\mathbf k,
$$

and the Laplacian is the divergence of the gradient,

$$
\nabla^2\phi=\nabla\cdot\nabla\phi=\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}+\frac{\partial^2\phi}{\partial z^2}.
$$

The point of the notation is that physics doesn't depend on the coordinate system (ll. 47–69). $\nabla^2u=0$ holds whatever coordinates you use; the version written with $x$, $y$ and $z$ derivatives holds only in Cartesian coordinates, which is fine in a box and useless on a sphere or around a wing. How to translate between coordinate systems is the subject of the vector calculus block ([[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities|VC2]]).

In the same notation, the wave and heat equations in several dimensions are $u_{tt}=c^2\nabla^2u$ and $u_t=\kappa^2\nabla^2u$. Setting every time derivative to zero leaves (ll. 71–89)

$$
\nabla^2u=0,\qquad\text{in two dimensions}\qquad\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}=0,
$$

which is Laplace's equation: the static limit of both. With a source on the right-hand side, $\nabla^2u=f(x,y)$, it is Poisson's equation (ll. 90–92). In one dimension it is just the ODE $u''=0$, whose solutions are straight lines, the steady states of [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions#Constant boundary values: subtract the steady state|PDE4]].

## 2. Separation of variables on the unit square (L20)

There are two derivatives in each direction, so the rule of thumb from PDE1 asks for two conditions in $x$ and two in $y$ (ll. 100–108). The difference from the time-dependent problems is where they go. There, both conditions in time were given at $t=0$. Here they sit at opposite sides of the domain, $x=0,1$ and $y=0,1$, so every condition is a boundary condition. Only Dirichlet conditions are used in this lecture (ll. 96–99).

### All sides held at zero

Solve $u_{xx}+u_{yy}=0$ on $0<x<1$, $0<y<1$ with $u=0$ on all four sides (ll. 109–233). Substitute $u=X(x)Y(y)$; the primes mean $x$-derivatives on $X$ and $y$-derivatives on $Y$, which the lecturer agreed is bad notation but standard (ll. 117–122):

$$
X''Y+XY''=0 .
$$

Move the second term across and divide by $XY$:

$$
\frac{X''}X=-\frac{Y''}Y=\lambda ,
$$

so

$$
X''-\lambda X=0,\qquad Y''+\lambda Y=0 .
$$

The $X$ equation is the familiar one; the $Y$ equation has the opposite sign (ll. 138–141). Either direction could go first, since all the conditions are boundary conditions, but $x$ is the habit (ll. 142–147). $u(0,y)=X(0)Y(y)=0$ gives $X(0)=0$, and likewise $X(1)=0$. This is the fixed-end eigenvalue problem of PDE2–PDE4, so (ll. 159–169)

$$
\lambda_n=-(n\pi)^2,\qquad X_n=\sin n\pi x .
$$

With $\lambda_n$ known, the $Y$ equation is (ll. 172–184)

$$
Y_n''-(n\pi)^2Y_n=0 .
$$

The auxiliary equation $m^2-(n\pi)^2=0$ has real, distinct roots $m=\pm n\pi$, so $Y_n=Ae^{n\pi y}+Be^{-n\pi y}$. The slides write this instead as (ll. 185–200)

$$
Y_n=\tilde C_n\cosh n\pi y+\tilde D_n\sinh n\pi y .
$$

This is the same family, since $\cosh\theta=\frac12(e^\theta+e^{-\theta})$ and $\sinh\theta=\frac12(e^\theta-e^{-\theta})$, so it only relabels the constants. It is more convenient because $\cosh0=1$ and $\sinh0=0$, which play the part $\cos0=1$ and $\sin0=0$ do for the trig functions when a side is at zero. So the general solution satisfying the PDE and the conditions on $x=0,1$ is (ll. 201–204)

$$
u=\sum_{n=1}^\infty\sin n\pi x\,\big[\tilde C_n\cosh n\pi y+\tilde D_n\sinh n\pi y\big].
$$

On $y=0$ (ll. 205–213), $\sinh0=0$ and $\cosh0=1$:

$$
0=\sum_{n=1}^\infty\tilde C_n\sin n\pi x ,
$$

so every $\tilde C_n=0$ by uniqueness. On $y=1$ (ll. 214–232):

$$
0=\sum_{n=1}^\infty\tilde D_n\sinh n\pi\,\sin n\pi x .
$$

$\sinh n\pi>0$ because $n\pi>0$, so every $\tilde D_n=0$, and $u\equiv0$. A lot of work for a dull answer, but it is the first sign of the maximum principle in §3.

### Neumann conditions on every side

If the derivative is given on every side, the eigenfunctions become cosines, including the constant for $n=0$ (ll. 238–255). Then any constant is a solution, and nothing in the boundary conditions can fix it; trying to impose its value as well over-determines the problem. This is a general feature of elliptic equations, already met in [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation#2. How many conditions each type needs (L14)|PDE1]]: never give Neumann conditions on the whole boundary.

### One side not held at zero (L20)

Now keep $u=0$ on three sides but set $u(x,1)=x(1-x)$ on the top (ll. 256–326). The problem is inhomogeneous, but the pair of conditions on $x=0$ and $x=1$ is still homogeneous, and that pair is all the eigenvalue problem needs (ll. 274–288). The separation and the $x$-problem are unchanged, so the general solution is the same as above. The non-zero side then behaves like the initial data of the time-dependent problems: it is fitted at the end.

On $y=0$, $\tilde C_n=0$ as before (ll. 294–296). On $y=1$ (ll. 297–305):

$$
x(1-x)=\sum_{n=1}^\infty\tilde D_n\sinh n\pi\,\sin n\pi x .
$$

Write $\hat D_n=\tilde D_n\sinh n\pi$, a constant for each $n$. Then this is the sine series of $x(1-x)$, found in [[MATH2048 PDE2 - Separation of Variables for the Wave Equation#Guitar string with fixed ends (L16)|PDE2]]:

$$
\hat D_n=\frac{4\big(1-(-1)^n\big)}{(n\pi)^3}\quad\Longrightarrow\quad\tilde D_n=\frac{4\big(1-(-1)^n\big)}{(n\pi)^3\sinh n\pi}.
$$

So (ll. 316–319)

$$
u(x,y)=\sum_{n=1}^\infty\frac{4\big(1-(-1)^n\big)}{(n\pi)^3\sinh n\pi}\sin n\pi x\,\sinh n\pi y .
$$

Each term grows like $\sinh n\pi y$ from zero at the bottom to its boundary value at the top. Higher modes are concentrated close to the top edge, since $\sinh n\pi y/\sinh n\pi\approx e^{-n\pi(1-y)}$ for large $n$, so the fine detail of the boundary data fades within a distance of order $1/(n\pi)$ of it.

![[m2048_pde_laplace_square.png|560]]

> [!check] Numbers
> Summing 60 terms gives $u(0.5,1)=0.250$, the boundary value $\frac14$, while $u(0.5,0.9)=0.185$ and $u(0.5,0.5)=0.051$. On a $99\times99$ interior grid the largest value is $0.243<\frac14$, as the maximum principle requires.

Sources are handled exactly as in PDE4 (ll. 256–260, 347–350): solve for the eigenfunctions, expand the source in them, and solve the resulting ODEs for the coefficients.

## 3. The maximum principle (L20)

The lecturer called this "possibly the most important mathematical result" for elliptic equations (ll. 327–346). A solution of Laplace's equation, and of many other elliptic equations without sources, takes its largest value on the boundary of the domain, never strictly inside. Applying the same result to $-u$ shows the smallest value is on the boundary too.

Both examples obey it. With zero on every side, the maximum and minimum are both $0$, so $u$ must be zero everywhere, which is the dull answer of §2 obtained without any calculation. More generally, constant boundary values force a constant solution. With $x(1-x)$ on the top, everything inside lies between $0$ and the boundary maximum $\frac14$.

It fails when there is a source, which can put the maximum inside. That makes it a diagnostic: if a quantity you believe obeys Laplace's equation is larger somewhere inside the domain than anywhere on its boundary, there must be a source in there adding to it.

Separation of variables now covers all three types, with non-trivial boundary conditions and sources, but only for linear equations (ll. 352–358). For a nonlinear problem the options are to approximate it by a linear one or to solve it numerically.

## Transcript slips

> [!warning] Lecture 20
> | Where | Transcript says | Correct |
> |---|---|---|
> | ll. 78–82 | the static limit written as $\nabla^2y=0$ | $\nabla^2u=0$; $y$ is now a coordinate, as the lecturer notes |
> | l. 164 | "I think I've managed to flip my conventions" | naming of the constants only; $X_n=\sin n\pi x$ either way |
> | ll. 197, 236 | "banishes" | vanishes |
> | l. 214 | "the boundary condition at X is equal to 1" | the side $y=1$, where $\sinh n\pi$ appears |
> | l. 298 | "the boundary value at x is equal to 1" | $y=1$ |
> | ll. 311–313 | sine coefficients of $x(1-x)$ are "4 on n pi all squared" | $\frac{4(1-(-1)^n)}{(n\pi)^3}$, cubed, as in PDE2 |
> | Recap, l. 22 | the 2022/23 question uses "Dirichlet boundaries" with cosine eigenfunctions | Neumann boundaries give the cosines (corrected at l. 277) |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]] · Next: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]
- Concepts: [[Laplace's Equation]] · [[Separation of Variables]] · [[PDE Classification]] · [[Divergence, Curl and the Laplacian]]
- In aerodynamics, the velocity potential of incompressible irrotational flow obeys Laplace's equation, which is why potential-flow solutions add.

## Sources

- Lecture 20 (12 Nov 2024) recording, Ian Hawke: `MATH2048 Lecture 20.txt`; PDE recap lecture (13 Nov 2024): `MATH2048 Lecture 2024-11-13.txt`
- Slides `Lecture20_LaplaceEquation1.pdf`; lecture notes Ch. 7

## Self-study tasks

Nothing was set in Lecture 20. The recap lecture's advice was to practise the past-paper A2 questions until the mechanical steps take about 20 minutes (recap, ll. 257–261); those are linked from PDE2–PDE4. Suggested tasks, not lecturer-set:

### Core

- [ ] Rework the square with $u(x,1)=x(1-x)$ and check $u(0.5,1)=\frac14$ from the series (suggested, not lecturer-set). → [[#One side not held at zero (L20)]]
- [ ] Solve the same square with $u(x,1)=\sin\pi x$ and zero on the other sides, by inspection. Answer: $u=\frac{\sinh\pi y}{\sinh\pi}\sin\pi x$ (suggested, not lecturer-set). → [[#One side not held at zero (L20)]]

### Further practice

- [ ] Solve the square with $u(1,y)=y(1-y)$ on the right side and zero on the others, by separating with the eigenvalue problem in $y$. Answer: $u=\sum\frac{4(1-(-1)^n)}{(n\pi)^3\sinh n\pi}\sinh n\pi x\,\sin n\pi y$ (suggested, not lecturer-set). → [[#2. Separation of variables on the unit square (L20)]]
