---
title: "MATH1054 M06 - Differential Equations I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 3: Differential Equations"
order: 6
tags:
  - math1054
  - odes
  - separable
  - constant-coefficients
aliases: ["MATH1054 Module 6", "Differential Equations I"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 6 work scheme (items 1–16) and Specimen Test 6; James §10.1–10.4 (classification, general and particular solutions, initial and boundary conditions), §10.5.1 and §10.5.3 (direction fields, separable equations), §10.9.1 (second-order linear homogeneous constant-coefficient equations)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M05 - Complex Numbers I]]"]
next_topics: ["[[MATH1054 M12 - Differential Equations II]]", "[[MATH1054 M13 - Differential Equations III]]"]
key_concepts: ["[[Classification of Differential Equations]]", "[[Separable First-Order ODEs]]", "[[Auxiliary Equation]]"]
tutorial_sheets: ["[[MATH1054 M06 Solutions - Differential Equations I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 6)", "02 - Sources/Modern Engineering Mathematics.pdf (§10.2–10.5, §10.9)"]
---

# MATH1054 M06 - Differential Equations I

> [!abstract] Summary
> A differential equation relates an unknown function to its derivatives, and its classification (ordinary or partial, order, linear or nonlinear, homogeneous or inhomogeneous) decides which solution method can work. An $n$th-order ODE has a general solution with $n$ arbitrary constants, and each independent initial or boundary condition fixes one. Two methods solve the first equations exactly: separation of variables for $\dot x=f(t)g(x)$, giving $\int\mathrm dx/g(x)=\int f(t)\,\mathrm dt+C$, and the trial solution $x=e^{mt}$ for $a\ddot x+b\dot x+cx=0$, which reduces the ODE to the auxiliary equation $am^2+bm+c=0$ and gives exponential, repeated-root or oscillatory solutions according to the sign of $b^2-4ac$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks you to classify an ODE, count its arbitrary constants, integrate $x^{(n)}=f(t)$ directly, solve a first-order equation whose right-hand side factorises as $f(t)g(x)$, or solve $a\ddot x+b\dot x+cx=0$ with or without conditions.
> - **Assumptions:** $x(t)$ is the dependent variable and $t$ the independent one unless stated (the Data Book uses $y(x)$); $a\neq0$; for separation, $g(x)\neq0$ on the interval used, with the roots of $g$ checked separately.
> - **Method:** 1. Classify the equation: order, linear or not, homogeneous or not. 2. If the right-hand side depends on $t$ only, integrate $n$ times; if it is $f(t)g(x)$, separate and integrate with one constant. 3. If it is $a\ddot x+b\dot x+cx=0$, solve $am^2+bm+c=0$ and write the solution for distinct, repeated or complex roots. 4. Apply the conditions last and check that the number of constants left equals the order minus the number of conditions. 5. Substitute back, and pick any $\pm$ sign from the initial data.
> - **Common mistakes:** losing the solution $x\equiv0$ (or any root of $g$) when dividing by $g(x)$; writing $Ae^{kt}+Be^{kt}$ for a repeated root instead of $(A+Bt)e^{kt}$.
> - **Practise:** [[#Repeated roots with initial conditions]] · [[MATH1054 M06 Solutions - Differential Equations I#Exercise 14: Initial-value problems|Exercise 14 (separable IVPs)]]

A differential equation states how a quantity changes rather than what it is. Newton's second law for an aircraft on its take-off run, the heat balance of a hot-water tank, the flow in a hydro-electric conduit and the current in an LCR circuit all arrive in this form, as a relation between an unknown function of time and its rates of change. Solving the equation means finding every function that satisfies that relation, and the answer is a family of functions rather than a number: the equation fixes the shape of the motion, and the starting conditions pick out one member of the family.

Before any solving, the equation has to be classified, because the methods are specific to types. A linear equation keeps the unknown and its derivatives to the first power, and that one property gives superposition: sums of solutions of a homogeneous linear equation are solutions. That is why the general solution of such an equation can be built from a few simple pieces, and why nonlinear equations can do things linear ones cannot, such as having two solutions through the same starting point or escaping to infinity at a finite time.

Two exact methods cover the first equations. Separation of variables handles first-order equations of the form $\dot x=f(t)g(x)$ by integrating the $x$ terms and the $t$ terms on opposite sides. The exponential trial $x=e^{mt}$ handles second-order linear equations with constant coefficients, the mass–spring–damper and LCR-circuit equation, and turns calculus into the quadratic $am^2+bm+c=0$; the complex-root case uses Euler's formula from [[MATH1054 M05 - Complex Numbers I|M05]]. Further first-order methods (homogeneous-type, exact, integrating factor) are in [[MATH1054 M12 - Differential Equations II|M12]], and forcing terms and particular integrals in [[MATH1054 M13 - Differential Equations III|M13]]; the same auxiliary equation is used in MATH2048 and the stability and control modules.

---

## 1. Variables, ordinary and partial equations, and order (James §10.3.1–10.3.2)

The variables that are differentiated are the **dependent variables**; the variables they are differentiated with respect to are the **independent variables**. An **ordinary differential equation** (ODE) has a single independent variable, so all its derivatives are ordinary derivatives. A **partial differential equation** (PDE) has two or more independent variables and contains partial derivatives. In

$$
\frac{\mathrm d^2f}{\mathrm dx^2}-4x\frac{\mathrm df}{\mathrm dx}=\cos2x
$$

the dependent variable is $f$ and the independent variable is $x$. A set of **coupled** ODEs has one independent variable and several dependent ones, as in

$$
4\frac{\mathrm dx}{\mathrm dt}+3\frac{\mathrm dy}{\mathrm dt}-x+2y=\cos t,\qquad 6\frac{\mathrm dx}{\mathrm dt}-2\frac{\mathrm dy}{\mathrm dt}-2x+y=2\sin t,
$$

where $t$ is independent and $x$ and $y$ are both dependent. The wave equation $\partial^2y/\partial x^2-\partial^2y/\partial t^2=0$ (Specimen Test 6, Q1(ii)) is a PDE: $y$ depends on both $x$ and $t$. All the equations solved here are ODEs.

The **order** of a differential equation is the order of the highest derivative in it. A power on a derivative does not change the order, so

$$
\left(\frac{\mathrm dx}{\mathrm dt}\right)^2+4\frac{\mathrm dx}{\mathrm dt}=0
$$

is first order: the highest derivative is $\mathrm dx/\mathrm dt$, even though it is squared. The order matters because it predicts the number of arbitrary constants in the general solution (Section 3) and therefore the number of conditions needed to fix a single solution (Section 4).

## 2. Linear and nonlinear, homogeneous and inhomogeneous (James §10.3.3–10.3.4)

### Linear equations and the linear operator

An $n$th-order ODE is **linear** if it can be written as

$$
a_n(t)\frac{\mathrm d^nx}{\mathrm dt^n}+a_{n-1}(t)\frac{\mathrm d^{n-1}x}{\mathrm dt^{n-1}}+\dots+a_1(t)\frac{\mathrm dx}{\mathrm dt}+a_0(t)\,x=f(t).
$$

The dependent variable and its derivatives appear only to the first power, are never multiplied together, and never sit inside another function such as $\sin x$ or $e^x$. The coefficients $a_k(t)$ and the right-hand side $f(t)$ may be any functions of the independent variable: $\ddot x+t\dot x=4\sin t$ and $xy''+x^2y'+y=0$ are both linear. An equation that is not linear is **nonlinear**. Three typical nonlinear terms are a power of a derivative, $(\dot x)^2$; a product of the dependent variable or its derivatives, $x\dot x$ or $\ddot x\,\dot x$; and a nonlinear function of the dependent variable, $\sin x$.

Write the left-hand side as an operator acting on $x$,

$$
L[x]=a_n(t)x^{(n)}+\dots+a_1(t)\dot x+a_0(t)x .
$$

Take two functions $x_1$, $x_2$ and constants $\alpha$, $\beta$. Differentiation is linear, so each derivative of the combination splits:

$$
\frac{\mathrm d^k}{\mathrm dt^k}(\alpha x_1+\beta x_2)=\alpha x_1^{(k)}+\beta x_2^{(k)} .
$$

Multiply by $a_k(t)$ and add over $k=0,\dots,n$:

$$
\begin{aligned}
L[\alpha x_1+\beta x_2]&=\sum_{k=0}^n a_k(t)\big(\alpha x_1^{(k)}+\beta x_2^{(k)}\big)\\
&=\alpha\sum_{k=0}^n a_k(t)x_1^{(k)}+\beta\sum_{k=0}^n a_k(t)x_2^{(k)}\\
&=\alpha L[x_1]+\beta L[x_2].
\end{aligned}
$$

This is the property that defines linearity. Its consequence, the **principle of superposition**, is that if $L[x_1]=0$ and $L[x_2]=0$ then $L[\alpha x_1+\beta x_2]=0$ for every $\alpha$ and $\beta$, which is why general solutions such as $A\sin\lambda t+B\cos\lambda t$ can be built from separate pieces. A nonlinear term breaks it. With $N[x]=x\dot x$,

$$
\begin{aligned}
N[x_1+x_2]&=(x_1+x_2)(\dot x_1+\dot x_2)\\
&=x_1\dot x_1+x_2\dot x_2+x_1\dot x_2+x_2\dot x_1\\
&=N[x_1]+N[x_2]+(x_1\dot x_2+x_2\dot x_1),
\end{aligned}
$$

and the cross terms stop the sum of two solutions from being a solution. The operator view is developed further in [[Linear Differential Operators and Superposition]] and [[MATH1054 M13 - Differential Equations III|M13]].

### Homogeneous and inhomogeneous equations

Classifying a linear equation as homogeneous or not needs a standard arrangement: every term containing the dependent variable on the left, and every term involving only the independent variable or a constant on the right. A linear equation is **homogeneous** if the right-hand side is then zero, so that every term contains the dependent variable or one of its derivatives. It is **inhomogeneous** if at least one term contains neither the dependent variable nor any of its derivatives; that term, $f(t)$ above, is the **forcing** or input. So $\dot x+4x=0$ and $4\dot x+(\sin t)x=0$ are homogeneous, and $\ddot x+t\dot x=4\sin t$ and $f''-4xf'=\cos2x$ are inhomogeneous. The homogeneous/inhomogeneous label is only applied to linear equations.

> [!warning] Two meanings of "homogeneous"
> A first-order equation $\dot x=F(x/t)$, solved by $x=vt$ in [[MATH1054 M12 - Differential Equations II|M12]] ([[Homogeneous First-Order ODEs]]), is also called homogeneous. That is a different property: $\dot x=(x^2+t^2)/(xt)$ is homogeneous in the $F(x/t)$ sense but is nonlinear, so it is neither homogeneous nor inhomogeneous in the sense of this section.

### Classifying the work-scheme equations

The engineering models of James §10.2 classify as follows (Example 10.5). Each has $t$ as the independent variable.

| Equation | Model | Dependent variable | Classification |
|---|---|---|---|
| (10.3) $m\ddot s-(\mu\alpha-\beta)\dot s^{\,2}=T-\mu mg$ | aircraft take-off run with lift and drag $\propto v^2$ | $s$ | second order, nonlinear ($\dot s^{\,2}$) |
| (10.6) $V\dot T_\mathrm w+AU\alpha T_\mathrm w=AU\alpha T_\mathrm{in}$ | hot-water tank | $T_\mathrm w$ | first order, linear, inhomogeneous |
| (10.7) $\dfrac{\rho d}{A}\dot Q+\Big(\dfrac1\alpha+\beta+\gamma\Big)Q=\rho gh$ | hydro-electric conduit | $Q$ | first order, linear, inhomogeneous |
| (10.9) $L\ddot i+R\dot i+\dfrac1Ci=0$ | LCR circuit | $i$ | second order, linear, homogeneous, constant coefficients |

Equation (10.7) is linear because the model takes every pressure drop proportional to the flow rate ($\Delta p_1=Q/\alpha$, $\Delta p_2=\beta Q$, $\Delta p_3=\gamma Q$), so $Q$ appears only to the first power; the inhomogeneous term is $\rho gh$.

The set exercises and the specimen test add the following.

| Source | Equation | Order | Classification | Dependent / independent |
|---|---|---|---|---|
| Ex 2(a) | $p''p'+(\sin z)p=\ln z$ | 2 | nonlinear (product $p''p'$) | $p$ / $z$ |
| Ex 2(b) | $s''+(\sin t)s'+(t+\cos t)s=e^t$ | 2 | linear, inhomogeneous (forcing $e^t$) | $s$ / $t$ |
| Ex 2(f) | $\dot x=f(t)x+g(t)$ | 1 | linear; inhomogeneous unless $g\equiv0$ | $x$ / $t$ |
| Spec Q1(i) | $\dot x+\frac1tx=1$ | 1 | ODE, linear, inhomogeneous (the 1) | $x$ / $t$ |
| Spec Q1(ii) | $y_{xx}-y_{tt}=0$ | 2 | PDE, linear, homogeneous (wave equation) | $y$ / $x,t$ |
| Spec Q1(iii) | $xy''+x^2y'+y=0$ | 2 | ODE, linear (variable coefficients allowed), homogeneous | $y$ / $x$ |

Ex 2(f) is the general first-order linear equation, which [[MATH1054 M12 - Differential Equations II|M12]] solves with an [[Integrating Factor Method|integrating factor]].

## 3. Solutions, arbitrary constants and direct integration (James §10.4.1–10.4.2)

A **solution** of a differential equation is a function that satisfies it identically on some interval. Some equations can be solved by inspection, by recognising a derivative. For $\dot x=-4x$ (Example 10.6), try $x=e^{-4t}$:

$$
\dot x=-4e^{-4t}=-4x .
$$

For $\ddot x+\lambda^2x=0$ (Example 10.7), try $x=\sin\lambda t$:

$$
\ddot x=-\lambda^2\sin\lambda t=-\lambda^2x,
$$

and $\cos\lambda t$ works in the same way. Neither solution is the whole answer. Both equations are linear and homogeneous, so by superposition $x=Ae^{-4t}$ solves the first for every constant $A$, and $x=A\sin\lambda t+B\cos\lambda t$ solves the second for every $A$ and $B$. This is simple harmonic motion with angular frequency $\lambda$.

The most general function satisfying the equation is its **general solution**; it contains arbitrary constants. Giving the constants numerical values produces a **particular solution**. The general solution of an $n$th-order equation normally contains $n$ arbitrary constants. The clearest case is an equation whose right-hand side depends on the independent variable only,

$$
\frac{\mathrm d^nx}{\mathrm dt^n}=f(t).
$$

It is solved by **direct integration**: each integration lowers the order by one and introduces one constant, so $n$ integrations give $n$ constants, and the general solution is a particular antiderivative plus an arbitrary polynomial of degree $n-1$.

### Direct integration examples

Example 10.8, $\ddot x=t-3e^{3t}$, is second order, so expect two constants. Integrate once:

$$
\dot x=\tfrac12t^2-e^{3t}+A .
$$

Integrate again:

$$
x=\tfrac16t^3-\tfrac13e^{3t}+At+B .
$$

Exercise 3(a), $\dot x=4t^2$, is first order, so expect one constant:

$$
x=\tfrac43t^3+A .
$$

Exercise 3(e), $\dddot x=2/t^3+\sin5t$, is third order, so expect three constants. For $t\neq0$, integrate three times:

$$
\begin{aligned}
\ddot x&=-\frac1{t^2}-\tfrac15\cos5t+A,\\
\dot x&=\frac1t-\tfrac1{25}\sin5t+At+B,\\
x&=\ln|t|+\tfrac1{125}\cos5t+\tfrac12At^2+Bt+C .
\end{aligned}
$$

Renaming $\tfrac12A$ as $A'$ gives $x=\ln|t|+\tfrac1{125}\cos5t+A't^2+Bt+C$, with three constants as expected. The solution holds on $t>0$ or on $t<0$, not across $t=0$ where the right-hand side is undefined.

Specimen Test 6, Q2, $\ddot x=t+e^{2t}$, is second order, so expect two constants:

$$
\begin{aligned}
\dot x&=\tfrac12t^2+\tfrac12e^{2t}+A,\\
x&=\tfrac16t^3+\tfrac14e^{2t}+At+B .
\end{aligned}
$$

## 4. Initial and boundary conditions (James §10.4.3–10.4.4)

Extra conditions on the solution fix the arbitrary constants. If all the conditions are given at the same value of the independent variable, as with $x(0)$ and $\dot x(0)$, they are **initial conditions** and the problem is an **initial-value problem** (IVP). If they are given at two or more different values, the problem is a **boundary-value problem** (BVP), usually a two-point BVP. In engineering usage "initial conditions" normally means conditions at the start of a process in time, and "boundary conditions" is normally used when the independent variable is a distance; the labels here follow the number of points instead. A first-order equation has one constant and needs one condition, so it can always be treated as an IVP. For higher-order equations the distinction matters, because IVPs are generally easier to solve than BVPs.

Each independent condition removes one constant, so

$$
\text{constants remaining}=\text{order}-\text{number of independent conditions}.
$$

### Fixing the constants

Example 10.9, $\dot x=-4x$ with $x(0)=2.5$: the general solution is $x=Ae^{-4t}$, and at $t=0$

$$
Ae^{0}=A=2.5,
$$

so $x=2.5e^{-4t}$.

Example 10.10 is the IVP $\ddot x+\lambda^2x=0$, $x(0)=4$, $\dot x(0)=3$, with $\lambda\neq0$. From $x=A\sin\lambda t+B\cos\lambda t$,

$$
\dot x=\lambda A\cos\lambda t-\lambda B\sin\lambda t .
$$

The conditions give

$$
\begin{aligned}
x(0)&=B=4,\\
\dot x(0)&=\lambda A=3\quad\Rightarrow\quad A=\frac3\lambda,
\end{aligned}
$$

so $x=\dfrac3\lambda\sin\lambda t+4\cos\lambda t$.

Example 10.11 keeps the equation but moves the second condition: $x(0)=4$, $\dot x(\pi/\lambda)=3$. This is a BVP. Using $\cos\pi=-1$ and $\sin\pi=0$,

$$
\begin{aligned}
x(0)&=B=4,\\
\dot x(\pi/\lambda)&=\lambda A\cos\pi-\lambda B\sin\pi=-\lambda A=3\quad\Rightarrow\quad A=-\frac3\lambda,
\end{aligned}
$$

so $x=-\dfrac3\lambda\sin\lambda t+4\cos\lambda t$.

Exercise 4(a), $\ddot x=4t$ with $x(0)=2$: two constants and one condition, so one constant should remain. Integrating twice gives $x=\tfrac23t^3+At+B$, and $x(0)=B=2$, so

$$
x=\tfrac23t^3+At+2,
$$

with $A$ still arbitrary.

Exercise 4(b), $\ddot x=\sin2t$ with $x(\pi/4)=2$ and $x(3\pi/4)=2$: two constants and two conditions, so none should remain. Integrating twice gives $x=-\tfrac14\sin2t+At+B$. Using $\sin\frac\pi2=1$ and $\sin\frac{3\pi}2=-1$,

$$
\begin{aligned}
x(\tfrac\pi4)&:\quad -\tfrac14+\tfrac\pi4A+B=2,\\
x(\tfrac{3\pi}4)&:\quad \tfrac14+\tfrac{3\pi}4A+B=2 .
\end{aligned}
$$

Subtract the first from the second:

$$
\tfrac12+\tfrac\pi2A=0\quad\Rightarrow\quad A=-\frac1\pi .
$$

Back-substitute into the first:

$$
B=2+\tfrac14-\tfrac\pi4\Big(-\frac1\pi\Big)=2+\tfrac14+\tfrac14=\tfrac52 .
$$

$$
x=\tfrac52-\frac t\pi-\tfrac14\sin2t .
$$

> [!check] Substituting back in Exercise 4(b)
> $\ddot x=-\tfrac14(-4\sin2t)=\sin2t$. At $t=\pi/4$: $\tfrac52-\tfrac14-\tfrac14=2$. At $t=3\pi/4$: $\tfrac52-\tfrac34+\tfrac14=2$. No arbitrary constant is left, as predicted.

The counting rule says how many constants the conditions can remove, not that a solution always exists. A BVP can have no solution or infinitely many. Take $\ddot x+\lambda^2x=0$ with $x(0)=0$: then $B=0$ and $x=A\sin\lambda t$. Adding $x(\pi/\lambda)=0$ gives $A\sin\pi=0$, which holds for every $A$, so there are infinitely many solutions. Adding $x(\pi/\lambda)=1$ instead gives $0=1$, so there is none.

> [!warning] Boundary-value problems are not always uniquely solvable
> Two conditions on a second-order equation fix both constants only if the resulting pair of linear equations for $A$ and $B$ has a non-zero determinant. When the conditions sit at zeros of the solutions, as above, the determinant vanishes; this is the eigenvalue problem of [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems|MATH2048 ODE3]] ([[Boundary Value Problems]]).

An **analytical solution** is a formula for the dependent variable in terms of the independent variable; it can be evaluated anywhere, and it shows how the solution depends on parameters such as $\lambda$ and on the arbitrary constants. A **numerical solution** is a table of values at discrete points, computed for one set of parameter values and one set of conditions. Analytical solutions are preferable when they exist, but many equations have none, and then numerical methods (James §10.6) are the only route.

## 5. Direction fields and solution families (James §10.5.1)

Most first-order equations can be written as

$$
\frac{\mathrm dx}{\mathrm dt}=f(t,x).
$$

At any point $(t,x)$ where $f$ is defined, the equation gives the gradient of the solution curve through that point. Drawing a short line segment with that gradient at each point of a grid produces the **direction field**. A solution curve has the field's gradient at every point on it, so the field segments are tangent to the solution curves, and the general solution, with its one arbitrary constant, is a one-parameter **family** of curves that fills the plane.

For $\dot x=-\tfrac12x$ (James Example 10.12) the general solution is $x=Ce^{-t/2}$. The condition $x(0)=2$ gives $C=2$. The condition $x(3)=-1$ gives

$$
Ce^{-3/2}=-1\quad\Rightarrow\quad C=-e^{3/2}\approx-4.482 .
$$

The figure shows the field and the family for the separable equation $\dot x=4xt$ of Section 6. The segments are flat along $t=0$ and along $x=0$, where $4xt=0$, and the solution curves $x=Ae^{2t^2}$ follow them; the curve $A=0$ is the constant solution $x\equiv0$.

![[m1054_m06_separable_family.png|900]]

## 6. Separable first-order equations (James §10.5.3)

### Why separating the variables works

A first-order equation is **separable** if it can be rearranged into the form

$$
g(x)\frac{\mathrm dx}{\mathrm dt}=h(t),
$$

with all the dependent-variable terms multiplying the derivative on the left and all the independent-variable terms on the right. The common starting form $\dot x=f(t)g(x)$ becomes $\dfrac1{g(x)}\dot x=f(t)$ wherever $g(x)\neq0$.

Let $G$ be an antiderivative of $g$, so that

$$
\frac{\mathrm dG}{\mathrm dx}=g(x).
$$

Along a solution $x(t)$, the chain rule gives

$$
\frac{\mathrm d}{\mathrm dt}G\big(x(t)\big)=\frac{\mathrm dG}{\mathrm dx}\frac{\mathrm dx}{\mathrm dt}=g(x)\frac{\mathrm dx}{\mathrm dt}.
$$

By the equation, the right-hand side is $h(t)$:

$$
\frac{\mathrm d}{\mathrm dt}G\big(x(t)\big)=h(t).
$$

Integrate with respect to $t$:

$$
G\big(x(t)\big)=\int h(t)\,\mathrm dt+C,
$$

that is,

$$
\int g(x)\,\mathrm dx=\int h(t)\,\mathrm dt+C .
$$

So the usual shorthand of "multiplying by $\mathrm dt$" and integrating each side in its own variable is justified by the chain rule. Only one constant is needed: a constant on each side could be combined into one.

### Method

1. Rearrange into $g(x)\,\dot x=h(t)$. Note every value of $x$ divided out (every root of $g$ in the form $\dot x=f(t)g(x)$).
2. Integrate both sides, adding a single constant.
3. Apply the initial condition to find the constant.
4. Solve for $x$ if possible, taking any $\pm$ sign from the initial data, and state the interval on which the solution is valid.
5. Check whether the constant solutions from step 1 are already in the family, and add them if not.

### Separable equations without conditions

Example 10.13 is $\dot x=4xt$. Divide by $x$ (assuming $x\neq0$) and integrate:

$$
\begin{aligned}
\int\frac{\mathrm dx}{x}&=\int4t\,\mathrm dt,\\
\ln|x|&=2t^2+c,\\
|x|&=e^{c}e^{2t^2},\\
x&=Ae^{2t^2},\qquad A=\pm e^{c}.
\end{aligned}
$$

The sign of $A$ covers $x>0$ and $x<0$, and $A=0$ restores the solution $x\equiv0$ removed by the division, so $x=Ae^{2t^2}$ with any real $A$ is the full general solution (the family in the figure above).

Exercise 11(b) is $\dot x=6xt^2$ in the same way:

$$
\begin{aligned}
\int\frac{\mathrm dx}{x}&=\int6t^2\,\mathrm dt,\\
\ln|x|&=2t^3+c,\\
x&=Ae^{2t^3},
\end{aligned}
$$

and again $A=0$ gives the lost solution $x\equiv0$.

Exercise 13(a) is $\sqrt t\,\dot x=\sqrt x$, with $t>0$ and $x\geq0$. For $x>0$,

$$
\begin{aligned}
\int x^{-1/2}\,\mathrm dx&=\int t^{-1/2}\,\mathrm dt,\\
2\sqrt x&=2\sqrt t+2c,\\
\sqrt x&=\sqrt t+c,\\
x&=\big(\sqrt t+c\big)^2 .
\end{aligned}
$$

The third line needs $\sqrt t+c\geq0$, because a square root is never negative. For $c\geq0$ that holds for all $t>0$; for $c<0$ the formula solves the equation only for $t\geq c^2$. With $c=-1$ at $t=\tfrac14$, the left-hand side $\sqrt t\,\dot x=\sqrt t+c=-\tfrac12$ while $\sqrt x=\tfrac12$, so the squared form fails there. The constant function $x\equiv0$ is a further solution, lost on dividing by $\sqrt x$, and it is not a member of the family for any $c$; for $c<0$ the zero solution can be joined to $(\sqrt t+c)^2$ at $t=c^2$.

Specimen Test 6, Q3(i) is $xt\,\dot x=1$:

$$
\begin{aligned}
\int x\,\mathrm dx&=\int\frac{\mathrm dt}{t},\\
\tfrac12x^2&=\ln|t|+C,\\
x^2&=2\ln|t|+A,\qquad A=2C,
\end{aligned}
$$

so $x=\pm\sqrt{2\ln|t|+A}$, valid for $t\neq0$ where $2\ln|t|+A>0$.

### Separable initial-value problems

Exercise 12(b) is $t^2\dot x=1/x$ with $x(4)=9$. Separate:

$$
\begin{aligned}
\int x\,\mathrm dx&=\int t^{-2}\,\mathrm dt,\\
\tfrac12x^2&=-\frac1t+C .
\end{aligned}
$$

At $t=4$, $x=9$:

$$
\tfrac{81}2=-\tfrac14+C\quad\Rightarrow\quad C=\tfrac{163}4 .
$$

Then

$$
x^2=\frac{163}2-\frac2t,
$$

and the positive root is required because $x(4)=9>0$:

$$
x=\sqrt{\frac{163}2-\frac2t}.
$$

The square root is real for $t\geq4/163\approx0.0245$, and the solution satisfies the equation for $t>4/163$, the interval containing $t=4$.

Specimen Test 6, Q3(ii) is $\dot x=\dfrac{t+1}{x+1}$ with $x(0)=1$:

$$
\begin{aligned}
\int(x+1)\,\mathrm dx&=\int(t+1)\,\mathrm dt,\\
\tfrac12(x+1)^2&=\tfrac12(t+1)^2+C .
\end{aligned}
$$

At $t=0$, $x+1=2$:

$$
2=\tfrac12+C\quad\Rightarrow\quad C=\tfrac32 .
$$

Then

$$
\begin{aligned}
(x+1)^2&=(t+1)^2+3\\
&=t^2+2t+4 .
\end{aligned}
$$

Take the positive root, since $x+1=2>0$ at $t=0$:

$$
x=\sqrt{t^2+2t+4}-1 .
$$

Because $(t+1)^2+3\geq3>0$, this solution exists for every $t$. Integrating the left-hand side as $\tfrac12x^2+x$ instead gives the same answer after completing the square; writing it as $\tfrac12(x+1)^2$ from the start avoids the quadratic.

### When the initial-value problem has two solutions

Exercise 14(a) is $\dot x=\dfrac{t^2+1}{x+2}$ with $x(0)=-2$:

$$
\begin{aligned}
\int(x+2)\,\mathrm dx&=\int(t^2+1)\,\mathrm dt,\\
\tfrac12(x+2)^2&=\tfrac13t^3+t+C .
\end{aligned}
$$

At $t=0$, $x+2=0$, so $C=0$, and

$$
(x+2)^2=\tfrac23t^3+2t,
$$

$$
x=-2\pm\sqrt{\tfrac23t^3+2t},\qquad t\geq0 .
$$

Both signs satisfy the equation and the condition, so this IVP has two solutions. The cause is the starting point. The usual uniqueness theorem guarantees exactly one solution through $(t_0,x_0)$ when $f(t,x)$ and $\partial f/\partial x$ are continuous near that point, and here $f=(t^2+1)/(x+2)$ is not even defined at $x_0=-2$: the slope is infinite along the whole line $x=-2$. The two branches leave the starting point vertically, one upwards and one downwards, and neither exists for $t<0$ because $\tfrac23t^3+2t<0$ there.

![[m1054_m06_nonunique_ivp.png|900]]

### Blow-up in finite time

Exercise 14(d) is $\dot x=e^{x+t}$ with $x(0)=a$. Write $e^{x+t}=e^xe^t$ and separate:

$$
\begin{aligned}
\int e^{-x}\,\mathrm dx&=\int e^t\,\mathrm dt,\\
-e^{-x}&=e^t+C .
\end{aligned}
$$

At $t=0$:

$$
-e^{-a}=1+C\quad\Rightarrow\quad C=-1-e^{-a}.
$$

Then

$$
\begin{aligned}
e^{-x}&=1+e^{-a}-e^t,\\
x&=-\ln\big(1+e^{-a}-e^t\big).
\end{aligned}
$$

The logarithm needs $1+e^{-a}-e^t>0$, that is $t<t^*=\ln(1+e^{-a})$, and as $t\to t^*$ the argument tends to $0^+$ and $x\to+\infty$. The solution **blows up** at a finite time. For $a=0$, $t^*=\ln2\approx0.693$; a larger starting value blows up sooner ($a=2$ gives $t^*\approx0.127$).

> [!tip] Blow-up is a nonlinear effect
> The growth rate $e^x$ increases with $x$, so the faster $x$ grows the harder it is pushed. A linear equation whose coefficients are continuous on an interval, with a leading coefficient that does not vanish there, has solutions that exist on the whole of that interval, so it can only become infinite where a coefficient does (as the solution $x=\tfrac12t+C/t$ of $\dot x+\frac1tx=1$ does at $t=0$).

![[m1054_m06_blowup.png|900]]

## 7. Second-order linear homogeneous equations with constant coefficients (James §10.9.1)

The general equation of this type is

$$
a\frac{\mathrm d^2x}{\mathrm dt^2}+b\frac{\mathrm dx}{\mathrm dt}+cx=0,\qquad a\neq0,
$$

with $a$, $b$, $c$ real constants. It is the free motion of a mass–spring–damper and the current in a source-free LCR circuit, equation (10.9).

### The first-order case suggests the trial solution

The first-order equation $a\dot x+bx=0$ is separable:

$$
\begin{aligned}
\int\frac{\mathrm dx}{x}&=-\frac ba\int\mathrm dt,\\
\ln|x|&=-\frac bat+c_1,\\
x&=Ae^{mt},\qquad m=-\frac ba .
\end{aligned}
$$

The exponent satisfies $am+b=0$. An exponential is the natural trial for the second-order equation too, because differentiating $e^{mt}$ only multiplies it by $m$.

### The auxiliary equation

Substitute $x=e^{mt}$, so that $\dot x=me^{mt}$ and $\ddot x=m^2e^{mt}$:

$$
\begin{aligned}
am^2e^{mt}+bme^{mt}+ce^{mt}&=0,\\
(am^2+bm+c)\,e^{mt}&=0 .
\end{aligned}
$$

Since $e^{mt}\neq0$ for every $t$, $x=e^{mt}$ is a solution exactly when

$$
am^2+bm+c=0 .
$$

This quadratic is the **auxiliary equation** (also the characteristic equation; see [[Auxiliary Equation]]). Its roots are

$$
m=\frac{-b\pm\sqrt{b^2-4ac}}{2a},
$$

and the sign of the discriminant $b^2-4ac$ gives three cases.

### Distinct real roots

If $b^2-4ac>0$ there are two real roots $m_1\neq m_2$, and $e^{m_1t}$ and $e^{m_2t}$ are both solutions. Their ratio $e^{(m_1-m_2)t}$ is not constant, so they are linearly independent, and by superposition

$$
x=Ae^{m_1t}+Be^{m_2t}
$$

is a solution with two arbitrary constants, which is the general solution of a second-order equation.

### Complex roots

If $b^2-4ac<0$ the roots are a complex-conjugate pair $m=\alpha\pm\mathrm j\beta$ with

$$
\alpha=-\frac b{2a},\qquad\beta=\frac{\sqrt{4ac-b^2}}{2a}.
$$

The distinct-root formula still holds with complex constants $A$ and $B$. Factor out the real exponential and apply [[Euler's Formula]], $e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta$:

$$
\begin{aligned}
x&=Ae^{(\alpha+\mathrm j\beta)t}+Be^{(\alpha-\mathrm j\beta)t}\\
&=e^{\alpha t}\big(Ae^{\mathrm j\beta t}+Be^{-\mathrm j\beta t}\big)\\
&=e^{\alpha t}\big[A(\cos\beta t+\mathrm j\sin\beta t)+B(\cos\beta t-\mathrm j\sin\beta t)\big]\\
&=e^{\alpha t}\big[(A+B)\cos\beta t+\mathrm j(A-B)\sin\beta t\big].
\end{aligned}
$$

Rename $C=A+B$ and $D=\mathrm j(A-B)$:

$$
x=e^{\alpha t}\big(C\cos\beta t+D\sin\beta t\big).
$$

For a real solution $C$ and $D$ must be real, which happens when $B$ is the complex conjugate of $A$. The solution oscillates at angular frequency $\beta$ inside the envelope $e^{\alpha t}$: it decays if $\alpha<0$, grows if $\alpha>0$, and is pure simple harmonic motion if $\alpha=0$. For $\ddot x+\lambda^2x=0$ the auxiliary equation $m^2+\lambda^2=0$ gives $m=\pm\mathrm j\lambda$, so $\alpha=0$, $\beta=\lambda$, and $x=C\cos\lambda t+D\sin\lambda t$, the result found by inspection in Section 3.

### Repeated roots

If $b^2-4ac=0$ there is one root $k=-b/(2a)$, and the distinct-root formula collapses to $Ae^{kt}+Be^{kt}=(A+B)e^{kt}$, which has only one independent constant. A second solution is needed. Write $P(m)=am^2+bm+c$; a double root means

$$
P(k)=0\quad\text{and}\quad P'(k)=2ak+b=0 .
$$

Try $x=te^{kt}$. Its derivatives are

$$
\begin{aligned}
\dot x&=(1+kt)e^{kt},\\
\ddot x&=(2k+k^2t)e^{kt}.
\end{aligned}
$$

Substitute and collect the terms in $t$ and the constant terms:

$$
\begin{aligned}
a\ddot x+b\dot x+cx&=\big[a(2k+k^2t)+b(1+kt)+ct\big]e^{kt}\\
&=\big[t\,(ak^2+bk+c)+(2ak+b)\big]e^{kt}\\
&=\big[t\,P(k)+P'(k)\big]e^{kt}\\
&=0 .
\end{aligned}
$$

Both brackets vanish only at a double root, which is why $te^{kt}$ is a solution here and not in the distinct-root case. The ratio $te^{kt}/e^{kt}=t$ is not constant, so the two solutions are independent and

$$
x=(A+Bt)e^{kt}.
$$

The same argument extends to higher order: a $p$th-order constant-coefficient equation has a degree-$p$ auxiliary polynomial, and a root $k$ of multiplicity $n$ contributes $e^{kt},te^{kt},\dots,t^{n-1}e^{kt}$.

### Summary and physical behaviour

| $b^2-4ac$ | Roots of $am^2+bm+c=0$ | General solution | Behaviour |
|---|---|---|---|
| $>0$ | $m_1\neq m_2$, real | $x=Ae^{m_1t}+Be^{m_2t}$ | non-oscillatory; over-damped when both roots are negative |
| $=0$ | $m=k$, repeated | $x=(A+Bt)e^{kt}$ | non-oscillatory; critically damped when $k<0$ |
| $<0$ | $\alpha\pm\mathrm j\beta$ | $x=e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ | oscillatory; decays if $\alpha<0$, grows if $\alpha>0$ |

These results are not on the exam formula sheet, so the table has to be remembered. For a damped oscillator written as $\ddot x+2\zeta\omega\dot x+\omega^2x=0$, the discriminant is $4\omega^2(\zeta^2-1)$, so $\zeta>1$ gives distinct real roots (over-damped), $\zeta=1$ a repeated root (critical damping) and $\zeta<1$ complex roots (under-damped); see [[Damping Ratio and Natural Frequency]].

![[m2048_ode_damping_regimes.png|600]]

### Distinct real roots: Example 10.34 and Exercises 55(a), 57(b)

Example 10.34, $\ddot x-9\dot x+6x=0$, has auxiliary equation $m^2-9m+6=0$:

$$
m=\frac{9\pm\sqrt{81-24}}2=\frac{9\pm\sqrt{57}}2 ,
$$

so $m_1\approx8.27$ and $m_2\approx0.725$, and

$$
x=Ae^{\frac{9+\sqrt{57}}2t}+Be^{\frac{9-\sqrt{57}}2t}\approx Ae^{8.27t}+Be^{0.725t}.
$$

Exercise 55(a), $2\ddot x-5\dot x+3x=0$, factorises:

$$
2m^2-5m+3=(2m-3)(m-1)=0\quad\Rightarrow\quad m=1,\ \tfrac32,
$$

$$
x=Ae^{t}+Be^{3t/2}.
$$

Exercise 57(b), $\ddot x+6\dot x-4x=0$, has $m^2+6m-4=0$:

$$
m=\frac{-6\pm\sqrt{36+16}}2=-3\pm\sqrt{13},
$$

$$
x=Ae^{(-3+\sqrt{13})t}+Be^{(-3-\sqrt{13})t},
$$

with exponents $\approx0.606$ and $\approx-6.61$.

### Complex roots: Example 10.35 and Specimen Test Q4(i)

Example 10.35, $2\ddot x-3\dot x+5x=0$, has $2m^2-3m+5=0$:

$$
m=\frac{3\pm\sqrt{9-40}}4=\frac34\pm\mathrm j\frac{\sqrt{31}}4\approx0.75\pm1.39\mathrm j,
$$

$$
x=e^{3t/4}\Big(A\cos\tfrac{\sqrt{31}}4t+B\sin\tfrac{\sqrt{31}}4t\Big).
$$

Since $\alpha=\tfrac34>0$, this is a growing oscillation.

Specimen Test 6, Q4(i), $\ddot x-4\dot x+13x=0$, has $m^2-4m+13=0$:

$$
m=\frac{4\pm\sqrt{16-52}}2=\frac{4\pm6\mathrm j}2=2\pm3\mathrm j,
$$

$$
x=e^{2t}(A\cos3t+B\sin3t).
$$

### Repeated roots: Exercise 57(d) and Specimen Test Q4(ii)

Exercise 57(d), $\ddot x-8\dot x+16x=0$, gives $(m-4)^2=0$, a repeated root $m=4$:

$$
x=(A+Bt)e^{4t}.
$$

Specimen Test 6, Q4(ii), $y''-2y'+y=0$, uses $y$ as the dependent and $x$ as the independent variable, the Data Book convention. The method is unchanged with $y=e^{mx}$: $(m-1)^2=0$, so

$$
y=(A+Bx)e^{x}.
$$

### Repeated roots with initial conditions

Example 10.36 is $\ddot x+6\dot x+9x=0$ with $x(0)=1$, $\dot x(0)=2$. The auxiliary equation is $(m+3)^2=0$, so $m=-3$ twice and $x=(A+Bt)e^{-3t}$. By the product rule,

$$
\begin{aligned}
\dot x&=Be^{-3t}-3(A+Bt)e^{-3t}\\
&=(B-3A-3Bt)e^{-3t}.
\end{aligned}
$$

The conditions give

$$
\begin{aligned}
x(0)&=A=1,\\
\dot x(0)&=B-3A=2\quad\Rightarrow\quad B=5,
\end{aligned}
$$

so

$$
x=(1+5t)e^{-3t}.
$$

This is critical damping. With $A=1$, $B=5$ the derivative is $\dot x=(2-15t)e^{-3t}$, which is zero at $t=2/15$, so the solution rises once to a peak of $\tfrac53e^{-0.4}\approx1.117$ and then decays without oscillating.

Exercise 59(b) is $\ddot x-4\dot x+4x=0$ with $x(1)=0$, $\dot x(1)=2$. The root is $m=2$, repeated. With the data at $t=1$, write the solution in powers of $(t-1)$, which is the same family because $e^{2t}=e^2e^{2(t-1)}$ and the constants absorb the factor $e^2$:

$$
x=\big[A+B(t-1)\big]e^{2(t-1)} .
$$

Differentiate:

$$
\dot x=\big[B+2A+2B(t-1)\big]e^{2(t-1)} .
$$

At $t=1$ every $(t-1)$ term vanishes and $e^0=1$:

$$
\begin{aligned}
x(1)&=A=0,\\
\dot x(1)&=2A+B=2\quad\Rightarrow\quad B=2,
\end{aligned}
$$

so

$$
x=2(t-1)e^{2(t-1)} .
$$

> [!tip] Conditions at a time other than zero
> Shifting the variable to $t-t_0$ puts the conditions at the origin of the new variable, so the constants come out with no exponential factors. Working with $(A+Bt)e^{2t}$ instead gives the same answer in the form $x=(2e^{-2}t-2e^{-2})e^{2t}$ after more algebra.

### Initial-value problems with distinct and complex roots

Exercise 56(a) is $5\ddot x-3\dot x-2x=0$ with $x(0)=-1$, $\dot x(0)=1$. The auxiliary equation is

$$
5m^2-3m-2=(5m+2)(m-1)=0\quad\Rightarrow\quad m=1,\ -\tfrac25,
$$

so $x=Ae^{t}+Be^{-2t/5}$ and $\dot x=Ae^t-\tfrac25Be^{-2t/5}$. The conditions give

$$
\begin{aligned}
A+B&=-1,\\
A-\tfrac25B&=1 .
\end{aligned}
$$

Subtract the second from the first:

$$
\tfrac75B=-2\quad\Rightarrow\quad B=-\tfrac{10}7,\qquad A=-1-B=\tfrac37,
$$

$$
x=\tfrac37e^{t}-\tfrac{10}7e^{-2t/5}.
$$

Exercise 59(a) is $2\ddot x-2\dot x+3x=0$ with $x(0)=1$, $\dot x(0)=0$. The auxiliary equation $2m^2-2m+3=0$ gives

$$
m=\frac{2\pm\sqrt{4-24}}4=\tfrac12\pm\mathrm j\tfrac{\sqrt5}2,
$$

so with $\omega=\sqrt5/2\approx1.118$,

$$
x=e^{t/2}(A\cos\omega t+B\sin\omega t).
$$

By the product rule,

$$
\dot x=e^{t/2}\Big[\big(\tfrac12A+\omega B\big)\cos\omega t+\big(\tfrac12B-\omega A\big)\sin\omega t\Big].
$$

The conditions give

$$
\begin{aligned}
x(0)&=A=1,\\
\dot x(0)&=\tfrac12A+\omega B=0\quad\Rightarrow\quad B=-\frac1{2\omega}=-\frac1{\sqrt5},
\end{aligned}
$$

so

$$
x=e^{t/2}\Big(\cos\tfrac{\sqrt5}2t-\tfrac1{\sqrt5}\sin\tfrac{\sqrt5}2t\Big),
$$

an oscillation growing inside the envelope $\pm\sqrt{1+\tfrac15}\,e^{t/2}=\pm\sqrt{6/5}\,e^{t/2}$.

Specimen Test 6, Q5 is $\ddot x+3\dot x+2x=0$ with $x(0)=1$, $\dot x(0)=-1$. The auxiliary equation $(m+1)(m+2)=0$ gives $x=Ae^{-t}+Be^{-2t}$, and the conditions give

$$
\begin{aligned}
A+B&=1,\\
-A-2B&=-1 .
\end{aligned}
$$

Adding the two equations gives $-B=0$, so $B=0$ and $A=1$:

$$
x=e^{-t}.
$$

> [!check] Why one mode is missing in Specimen Test Q5
> The slow mode $e^{-t}$ has initial value 1 and initial slope $-1$, exactly the data, so the fast mode $e^{-2t}$ is not needed. Substituting back: $\ddot x+3\dot x+2x=(1-3+2)e^{-t}=0$.

Specimen Test Q5, Example 10.36 and Exercise 59(a) give one solution from each root case: monotonic decay, a single hump then decay, and a growing oscillation.

![[m1054_m06_root_cases.png|900]]

## 8. Choosing a method

1. Classify the equation: ODE or PDE, order, linear or nonlinear, homogeneous or inhomogeneous. This decides which methods are allowed.
2. If the right-hand side depends only on the independent variable, $x^{(n)}=f(t)$, integrate directly $n$ times.
3. If it is first order and $\dot x=f(t)g(x)$, separate the variables, and check the roots of $g$.
4. If it is linear, homogeneous and has constant coefficients, solve the auxiliary equation and use the table in Section 7.
5. Apply the conditions last, check that the number of constants left equals the order minus the number of independent conditions, and substitute the answer back into the equation.

## Terminology and alternative names

| Term used here | Also called | Where |
|---|---|---|
| inhomogeneous | nonhomogeneous | James §10.3.4 uses nonhomogeneous; inhomogeneous is the more common word |
| auxiliary equation | characteristic equation | James §10.9.1 uses characteristic equation first and auxiliary equation as the alternative |
| initial-value problem | conditions at the start of a process | James: all conditions at one value of the independent variable; engineering usage: conditions at the start of a time-dependent process |
| boundary-value problem | two-point boundary-value problem | engineering usage reserves boundary conditions for a distance variable |
| $x(t)$, $\dot x$ | $y(x)$, $y'$ | James uses $x$ and $t$; the Data Book and formula sheet use $y$ and $x$ |
| $\mathrm j=\sqrt{-1}$ | $i$ | engineering texts use j |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M06 Solutions - Differential Equations I]]
- Previous: [[MATH1054 M05 - Complex Numbers I]] (Euler's formula for the complex-root case) · Prerequisite: [[MATH1054 M04 - Integration I]]
- Next: [[MATH1054 M07 - Functions]] · ODE sequence: [[MATH1054 M12 - Differential Equations II]] (homogeneous-type, exact, integrating factor) → [[MATH1054 M13 - Differential Equations III]] (linear operators, complementary function and particular integral, damping)
- Concepts: [[Classification of Differential Equations]] · [[Separable First-Order ODEs]] · [[Auxiliary Equation]] · [[Euler's Formula]] · [[Linear Differential Operators and Superposition]] · [[Homogeneous First-Order ODEs]] · [[Integrating Factor Method]]
- Later: [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] · [[Boundary Value Problems]] · [[PDE Classification]] · [[Wave Equation]] · [[Separation of Variables]] (the PDE method, a different technique)
- Elsewhere: SESA2027 [[Damping Ratio and Natural Frequency]] and [[Characteristic Equation and Eigenvalues]] · FEEG1002 [[Kinematic Relations for Rectilinear Motion]] (separating $a=v\,\mathrm dv/\mathrm ds$)

## Sources

- MATH1054 Module Booklet, Module 6 (PDF pp. 13–15): work scheme based on James, items 1–16; work scheme based on Stroud (Programme 24 frames 1–21, Programme 25 frames 1–16); Specimen Test 6.
- MATH1054 Solutions booklet (`1054solns_(6th_Edition).pdf`), Module 6 solutions to the exercises and Specimen Test 6 (PDF pp. 14–18).
- James, *Modern Engineering Mathematics* (6th ed.): §10.1–10.2 (pp. 790–795), §10.3 classification (pp. 795–799), §10.4 solving differential equations (pp. 799–806), §10.5.1 and §10.5.3 direction fields and separable equations (pp. 806–812), §10.9.1 linear homogeneous constant-coefficient equations (pp. 851–856).

## Self-study tasks

### Core

- [ ] Exercises 2(a), (b), (f), p.799 (Module 06 work scheme, item 7), and Specimen Test 6 Q1. → [[MATH1054 M06 Solutions - Differential Equations I#Exercise 2 (p.799): Classification]] · [[MATH1054 M06 Solutions - Differential Equations I#Q1: Classification]]
- [ ] Exercises 3(a), (e) and 4(a), (b), p.805 (Module 06 work scheme, item 11). → [[MATH1054 M06 Solutions - Differential Equations I#Exercise 3 (p.805): General solutions and counting constants]] · [[MATH1054 M06 Solutions - Differential Equations I#Exercise 4 (p.805): Constants left after the conditions]]
- [ ] Exercises 11(b), 12(b), 13(a), 14(a), (d), pp.811–812 (Module 06 work scheme, item 13). → [[MATH1054 M06 Solutions - Differential Equations I#Part B: Assigned exercises]] · [[MATH1054 M06 Solutions - Differential Equations I#Exercise 14: Initial-value problems]]
- [ ] Exercises 55(a), 56(a), 57(b), (d), 59(a), (b), p.856 (Module 06 work scheme, item 15). → [[MATH1054 M06 Solutions - Differential Equations I#Exercise 57]] · [[MATH1054 M06 Solutions - Differential Equations I#Exercise 59]]
- [ ] Specimen Test 6, Q1–Q5, timed. → [[MATH1054 M06 Solutions - Differential Equations I#Part C: Specimen Test 6]]

### Further practice

- [ ] Examples 10.1–10.5, classification (Module 06 work scheme, items 3–7). → [[MATH1054 M06 Solutions - Differential Equations I#Examples 10.1–10.4: The classification vocabulary]] · [[MATH1054 M06 Solutions - Differential Equations I#Example 10.5: Classify (10.3), (10.6), (10.7), (10.9)]]
- [ ] Examples 10.6–10.11 and 10.13, general solutions, conditions and separation (Module 06 work scheme, items 9, 10 and 13). → [[MATH1054 M06 Solutions - Differential Equations I#Part A: Worked examples]]
- [ ] Examples 10.34–10.36, the auxiliary equation (Module 06 work scheme, item 15). → [[MATH1054 M06 Solutions - Differential Equations I#Part A: Worked examples]] · [[#Repeated roots with initial conditions]]
- [ ] Stroud, Programme 24 frames 1–21 (omitting Example 5 in frame 17) and Programme 25 frames 1–16 (Module 06 work scheme B); the worked answers are in the following frames. → [[#6. Separable first-order equations (James §10.5.3)]] · [[#7. Second-order linear homogeneous equations with constant coefficients (James §10.9.1)]]

## Transcript and slide slips

> [!warning] Textbook slip (James p.798, §10.3.4)
> Where: [[#Homogeneous and inhomogeneous equations]].
>
> The last sentence of the top paragraph defines a nonhomogeneous equation as having "at least one term that does not contain the independent variable or any of its derivatives"; it should read "dependent variable". The Module 6 work scheme (item 7) flags the same correction. A forcing term is one that is free of the dependent variable.
