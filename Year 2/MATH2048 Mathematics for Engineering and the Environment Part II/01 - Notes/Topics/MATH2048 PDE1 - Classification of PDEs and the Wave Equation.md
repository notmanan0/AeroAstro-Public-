---
title: "MATH2048 PDE1 - Classification of PDEs and the Wave Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 10
tags:
  - math2048
  - pdes
  - wave-equation
  - classification
aliases: ["MATH2048 Lecture 14", "Hyperbolic parabolic elliptic"]
date: 2026-10-30
status: lectured
coverage: "Lecture 14 (29 Oct 2024, Ian Hawke): what a linear homogeneous second-order PDE is, the three types and their physical meaning, how many boundary and initial conditions each needs, the b^2 - ac test, the Tricomi equation, and the derivation of the wave equation for a string."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
next_topics: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]"]
key_concepts: ["[[PDE Classification]]", "[[Wave Equation]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 14.txt", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture14_Hyperbolic1.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§5.1–5.3)"]
---

# MATH2048 PDE1 - Classification of PDEs and the Wave Equation

> [!abstract] Summary
> A linear second-order PDE $au_{xx}+2bu_{xy}+cu_{yy}+du_x+eu_y+fu=0$ is hyperbolic, parabolic or elliptic according to whether $b^2-ac$ is positive, zero or negative. The three types behave differently, with waves at finite speed, instant smoothing, or static balance, and so need different initial and boundary conditions for a unique solution. The prototype hyperbolic equation, the wave equation $y_{tt}=c^2y_{xx}$, follows from Newton's second law on a short piece of taut string, with wave speed $c=\sqrt{T/\rho}$.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to classify a PDE, to say what conditions make a problem well posed, or to derive the wave equation.
> - **Assumptions:** two independent variables; linear, so $a,\dots,f$ depend only on the independent variables; for the string, small displacements and purely vertical motion.
> - **Method:** 1. Read $a$, $2b$, $c$ off the second-derivative terms (halve the mixed coefficient). 2. Compute $b^2-ac$. 3. If it depends on position, classify region by region. 4. Count conditions: one per derivative in each variable.
> - **Common mistakes:** using the mixed coefficient itself as $b$, which quadruples it in $b^2$; mixing up the coefficient $c$ in the classification with the wave speed $c$.
> - **Practise:** [[#The Tricomi equation changes type]] · [[#4. Deriving the wave equation for a string]]

A PDE has an unknown depending on at least two independent variables, with derivatives in more than one of them. As with ODEs, whether a solution exists and is well behaved depends on the boundary conditions, and for PDEs that question is harder. With ODEs, initial value problems almost always have a solution and boundary value problems need not. For PDEs, where and how the conditions may be given depends on the coefficients of the equation, and sorting equations by that is called classification.

The three classes match three kinds of physics. Hyperbolic equations carry information from A to B at a finite speed: they describe theories where the small-scale cause and effect is resolved, such as Newton's laws applied to a gas, which is why gas dynamics and so much of aeronautics is hyperbolic. Parabolic equations appear when small-scale behaviour that is too complicated to follow is averaged over, such as the Brownian motion of every air molecule in a room, and describe diffusion. Elliptic equations describe things that are static.

---

## 1. Linear PDEs and the three types

The most general linear, homogeneous, second-order PDE in two independent variables is

$$
a\,\frac{\partial^2u}{\partial x^2}+2b\,\frac{\partial^2u}{\partial x\,\partial y}+c\,\frac{\partial^2u}{\partial y^2}+d\,\frac{\partial u}{\partial x}+e\,\frac{\partial u}{\partial y}+f\,u=0,\qquad u=u(x,y).
$$

It is **linear** because $a,\dots,f$ are given functions of $x$ and $y$ only, never of $u$ or its derivatives, so solutions can be added. It is **homogeneous** because the right-hand side is zero; a non-zero right-hand side would have to be a function of $x$ and $y$ only. This is the PDE version of $y''+p(x)y'+q(x)y=0$.

### Hyperbolic: the wave equation

The prototype is the wave equation, written with time and space as the independent variables:

$$
\frac{\partial^2u}{\partial t^2}=c^2\frac{\partial^2u}{\partial x^2}.
$$

Dimensional analysis says what $c$ is. Each derivative divides the dimensions by those of the variable, so the left side has dimensions $[u]/[t]^2$ and the right side $[c]^2[u]/[x]^2$. Matching them, $c$ has dimensions of length over time: it is a velocity, the speed of propagation. A Gaussian pulse evolved by the wave equation splits into two pulses, one moving right and one moving left, each at speed $c$, leaving nothing in the middle (left panel below).

> [!check] A shape moving at speed c solves the wave equation
> Let $u=f(x-ct)$ for any twice-differentiable $f$, and write $\xi=x-ct$. By the chain rule $u_x=f'(\xi)$, $u_{xx}=f''(\xi)$, $u_t=-cf'(\xi)$ and $u_{tt}=c^2f''(\xi)$, so $u_{tt}=c^2u_{xx}$ exactly. The same works for $g(x+ct)$, moving left, and by linearity for the sum. That is the pulse-splitting in the figure: a Gaussian released from rest becomes two half-height copies moving apart. Any theory that carries information at a finite speed is described by hyperbolic equations: gas dynamics, where the speeds are the flow speed and the speed of sound, acoustics, seismic waves, electromagnetism, general relativity.

### Parabolic: the heat equation

The prototype is the heat equation,

$$
\frac{\partial u}{\partial t}=k\,\frac{\partial^2u}{\partial x^2},
$$

with one time derivative where the wave equation has two. So $k$ is no longer a speed; dimensionally it is a length squared over a time. With $k>0$, the solution smooths out: sharp corners in the initial data are rounded immediately, and after a while the solution is set mainly by the boundary conditions rather than the initial data (right panel). Nothing here travels at a definite speed: for a triangle of initial data surrounded by zeros, the exact solution is already non-zero everywhere at any time $t>0$, however small. This amounts to propagation at infinite speed, an artefact of the averaging that produced the equation.

$k$ is often written $\kappa^2$ to stress that it is positive, but nothing forces that. A negative $k$ sharpens features instead of smoothing them and tends to blow up, which is sometimes the right model, for instance in combustion.

### Elliptic: Laplace's equation

The prototype is Laplace's equation,

$$
\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}=0,
$$

which looks like the wave equation with the sign changed: moving everything to one side, the wave equation reads $u_{tt}-c^2u_{xx}=0$ and Laplace's equation has a plus. Elliptic equations describe static problems, so both variables are spatial. The two-dimensional wave equation shows where this comes from. Starting from

$$
u_{tt}=c^2(u_{xx}+u_{yy}),
$$

a static solution has $u_t=0$, so $u_{tt}=0$ and the left side vanishes. Since $c>0$, dividing by $c^2$ leaves $u_{xx}+u_{yy}=0$. A hyperbolic equation in the static case gives an elliptic one. Elliptic problems behave like the boundary value problems of [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems|ODE3]]: a solution is not guaranteed, but when it exists it is very useful.

![[m2048_pde_wave_vs_heat.png|900]]

## 2. How many conditions each type needs

Without boundary conditions there is no unique solution, because the integration "constants" of a PDE are whole functions. The rule of thumb is one condition for every derivative in each variable.

The wave equation has two time derivatives, so it needs two conditions in time. The standard choice is the initial displacement $u(x,0)$ and the initial velocity $u_t(x,0)$. In principle you could give $u$ at two times instead, but that rarely gives a physically meaningful problem. It also has two space derivatives, so it needs one condition at each end of the domain, on the value (Dirichlet), the normal derivative (Neumann) or a combination. Fewer conditions leave arbitrary functions in the solution; more over-determine it, and there is no solution at all.

The heat equation has one time derivative, so only one condition in time, and the only sensible one is the initial value $u(x,0)$. Giving the initial time derivative instead would not fix the solution, which could still be offset by a constant. In space it needs one condition at each end, as before.

Laplace's equation is a boundary value problem on a closed region, with one condition on each part of the boundary. If every condition is on the normal derivative, the solution is again not unique, so at least part of the boundary must have the value given.

## 3. The classification test

The type depends only on the principal part, the terms with the highest derivatives, so only $a$, $b$ and $c$ matter:

$$
b^2-ac\ \begin{cases}>0 & \text{hyperbolic,}\\=0 & \text{parabolic,}\\<0 & \text{elliptic.}\end{cases}
$$

This is the discriminant of a quadratic. Had the mixed term been written $B\,u_{xy}$ instead of $2b\,u_{xy}$, the test would be the familiar $B^2-4ac$. Read the coefficients from the form you are given: if the mixed term is $B\,u_{xy}$, then $b=B/2$.

For the prototypes, with $t$ playing the part of $y$, the coefficients are constants. The wave equation $u_{tt}-c^2u_{xx}=0$ has $a=-c^2$ (wave speed squared), $b=0$ and coefficient $1$ on $u_{tt}$, so $b^2-ac=c^2>0$. The heat equation $u_t-ku_{xx}=0$ has no $u_{tt}$, so $b^2-ac=0$. Laplace's equation has $a=c=1$ and $b=0$, so $b^2-ac=-1<0$. The letter $c$ means two things here, the classification coefficient and the wave speed, and the context tells you which.

### The Tricomi equation changes type

When $a$, $b$ and $c$ depend on position, so can the type. The Tricomi equation, a model for transonic flow, is written

$$
y\,u_{xx}=u_{yy},
$$

so $a=y$, $b=0$ and $c=-1$, giving

$$
b^2-ac=0-y\cdot(-1)=y .
$$

At $y=1$ it is the wave equation $u_{xx}-u_{yy}=0$, and at $y=-1$ it is Laplace's equation after multiplying by $-1$. It is hyperbolic for $y>0$, elliptic for $y<0$, and none of the three on the line $y=0$. Nothing stops you choosing a domain $-1<y<1$, and then the two halves need different kinds of boundary conditions. The usual approach is to find the surface where the type changes, solve on each side and glue the solutions together, which is hard, so problems of mixed type are best avoided by reformulating the problem. Books often write the Tricomi equation as $yu_{xx}+u_{yy}=0$, which swaps which half is hyperbolic, so always compute $b^2-ac$ from the form in front of you.

### Worked classifications

*(Suggested, not lecturer-set; these are the Core self-study tasks.)* In each of the three constant-coefficient equations below, $a=1$ and the mixed coefficient has to be halved to give $b$.

For $u_{xx}+4u_{xy}+3u_{yy}=0$: $2b=4$, so $b=2$, and $b^2-ac=4-3=1>0$, hyperbolic.

For $u_{xx}+2u_{xy}+u_{yy}=0$: $b=1$ and $b^2-ac=1-1=0$, parabolic. The principal part is a perfect square, $(\partial_x+\partial_y)^2u$, which is the signature of the parabolic case.

For $u_{xx}+u_{xy}+u_{yy}=0$: $b=\tfrac12$ and $b^2-ac=\tfrac14-1=-\tfrac34<0$, elliptic. Using the mixed coefficient $1$ as $b$ would give $1-1=0$ and the wrong answer, parabolic.

A variable mixed coefficient can make the type depend on position just as the Tricomi equation's $a=y$ does. For $u_{xx}+2x\,u_{xy}+u_{yy}=0$, $b=x$ and

$$
b^2-ac=x^2-1,
$$

so the equation is hyperbolic for $|x|>1$, parabolic on the two lines $x=\pm1$ and elliptic in the strip $|x|<1$. And for $x\,u_{xx}+u_{yy}=0$ (a Further-practice task), $a=x$, $b=0$, $c=1$, so $b^2-ac=-x$: hyperbolic for $x<0$ and elliptic for $x>0$. On $-1<x<1$ the left half needs wave-type data (two conditions in the variable that plays the part of time) and the right half needs a value or normal derivative on every part of its boundary.

![[m2048_pde_type_regions.png|820]]

> [!check] Each prototype from the general form
> Writing the wave equation as $u_{tt}-c^2u_{xx}=0$ with $t$ as the first variable: $a=1$, $b=0$, $c_{\text{coef}}=-c^2$, $b^2-ac_{\text{coef}}=c^2>0$. The heat equation $ku_{xx}-u_t=0$ has $a=k$, $b=0$, $c_{\text{coef}}=0$, so $0$. Laplace gives $-1$. The sign of the answer does not depend on which variable is called first, because swapping $x$ and $y$ swaps $a$ and $c$ and leaves $b^2-ac$ unchanged.

## 4. Deriving the wave equation for a string

The wave equation is written in several equivalent forms: $y_{tt}=c^2y_{xx}$, $y_{tt}-c^2y_{xx}=0$ and $\frac1{c^2}y_{tt}=y_{xx}$. The derivation is for a guitar string, but $y$ could equally be the displacement of a water surface from flat.

A string of mass per unit length $\rho$ under tension is displaced by $y(x,t)$ from its rest position $y=0$. The small piece between $x$ and $x+\Delta x$ is pulled at its left end by a tension $T_1$ at angle $\alpha$ below the horizontal, and at its right end by a tension $T_2$ at angle $\beta$ above it. The model assumes the displacement is small and each point of the string moves only up and down, never sideways.

![[m2048_pde_string_element.png|640]]

There is no horizontal motion, so no horizontal acceleration, and the horizontal forces balance:

$$
T_2\cos\beta-T_1\cos\alpha=0\quad\Longrightarrow\quad T_1\cos\alpha=T_2\cos\beta\equiv T .
$$

This common value $T$ is called the tension in the string. For small slopes $\cos\alpha=1-\tfrac12\alpha^2+\dots$ is $1$ to first order, so $T_1\approx T_2\approx T$: the tension is the same all along the string. Vertically, the mass of the piece is $\rho\,\Delta x$ and its acceleration is $y_{tt}$, so Newton's second law gives

$$
\rho\,\Delta x\,\frac{\partial^2y}{\partial t^2}=T_2\sin\beta-T_1\sin\alpha .
$$

Replace each tension using the horizontal balance. $T_1=T/\cos\alpha$, so $T_1\sin\alpha=T\tan\alpha$, and likewise $T_2\sin\beta=T\tan\beta$:

$$
\rho\,\Delta x\,\frac{\partial^2y}{\partial t^2}=T(\tan\beta-\tan\alpha).
$$

The tangent of each angle is the slope of the string at that end, opposite over adjacent in the small triangle of sides $\Delta x$ and $\Delta y$, so as the piece shrinks

$$
\tan\beta\approx\frac{\partial y}{\partial x}\Big|_{x+\Delta x},\qquad\tan\alpha\approx\frac{\partial y}{\partial x}\Big|_{x}.
$$

Substitute and divide by $\Delta x$:

$$
\rho\,\frac{\partial^2y}{\partial t^2}\approx T\,\frac{y_x(x+\Delta x,t)-y_x(x,t)}{\Delta x}.
$$

As $\Delta x\to0$ the difference quotient becomes the derivative of $y_x$, which is $y_{xx}$. Explicitly, Taylor-expand the slope at the right end about $x$:

$$
y_x(x+\Delta x,t)=y_x(x,t)+\Delta x\,y_{xx}(x,t)+\tfrac12\Delta x^2\,y_{xxx}(x,t)+\dots,
$$

so the quotient is $y_{xx}+\tfrac12\Delta x\,y_{xxx}+\dots$, and every correction vanishes in the limit. The same limit turns the approximate signs into equalities, because the error in $\tan\approx$ slope at each end also shrinks with $\Delta x$:

$$
\rho\,\frac{\partial^2y}{\partial t^2}=T\,\frac{\partial^2y}{\partial x^2}.
$$

Divide by $\rho$:

$$
\frac{\partial^2y}{\partial t^2}=c^2\frac{\partial^2y}{\partial x^2},\qquad c=\sqrt{\frac T\rho}.
$$

This makes sense as a wave speed only if $T/\rho>0$. Density is always positive. A negative tension would mean the string is being compressed, and the small-displacement assumptions behind the derivation would break down.

> [!check] Numbers
> A steel guitar string with $T=70\ \mathrm N$ and $\rho=1.0\times10^{-3}\ \mathrm{kg\,m^{-1}}$ has $c=\sqrt{70/0.001}=265\ \mathrm{m\,s^{-1}}$. Dimensionally, $\mathrm N/(\mathrm{kg\,m^{-1}})=\mathrm{kg\,m\,s^{-2}}\cdot\mathrm{m\,kg^{-1}}=\mathrm{m^2\,s^{-2}}$, the square of a speed.

D'Alembert's general solution $y=f(x+ct)+g(x-ct)$ on an infinite string is the pulse-splitting in the figure above written as a formula. It was not covered in the 2024-25 lectures and has not been examined in the last three papers.

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Next: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]
- Concepts: [[PDE Classification]] · [[Wave Equation]] · [[Boundary Value Problems]]
- In aerodynamics, the same change of type separates subsonic (elliptic) from supersonic (hyperbolic) small-disturbance flow.

## Sources

- Lecture 14 (29 Oct 2024) recording, Ian Hawke: `MATH2048 Lecture 14.txt`
- Slides `Lecture14_Hyperbolic1.pdf`; lecture notes §5.1–5.3

## Self-study tasks

Nothing was set in Lecture 14; the slide on diffusion was left as reading (l. 190). Suggested tasks, not lecturer-set:

### Core

- [ ] Classify $u_{xx}+4u_{xy}+3u_{yy}=0$, $u_{xx}+2u_{xy}+u_{yy}=0$ and $u_{xx}+u_{xy}+u_{yy}=0$. Answers: $b=2$, $b^2-ac=1$, hyperbolic; $b=1$, $b^2-ac=0$, parabolic; $b=\frac12$, $b^2-ac=-\frac34$, elliptic (suggested, not lecturer-set). → [[#Worked classifications]]
- [ ] Derive the wave equation for a string from Newton's second law, stating each assumption where it is used (suggested, not lecturer-set). → [[#4. Deriving the wave equation for a string]]

### Further practice

- [ ] Find where $x\,u_{xx}+u_{yy}=0$ is hyperbolic and where it is elliptic, and say what boundary data a problem on $-1<x<1$ would need on each side (suggested, not lecturer-set). → [[#Worked classifications]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lecture 14
> | Where | Transcript says | Correct |
> |---|---|---|
> | l. 27 | "PDA" | PDE (also "ODAs" at l. 214) |
> | l. 136 | in acoustics the wave speed is "linked to the Young's modulus" | for sound in a fluid it is set by the bulk modulus (or $\gamma p$) and density; Young's modulus governs waves in solid rods |
> | l. 275 | "trichome equation" | Tricomi equation |
> | l. 401 | $\tan\alpha\approx y_x\vert_x$ "but with a minus sign because of the way it's flipped" | the minus sign is already in $T_2\sin\beta-T_1\sin\alpha$; $\tan\alpha=+y_x\vert_x$, as on the slide |
