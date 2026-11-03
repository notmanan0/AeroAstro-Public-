---
title: "MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 1: Ordinary Differential Equations"
order: 1
tags:
  - math2048
  - odes
  - constant-coefficients
  - auxiliary-equation
aliases: ["MATH2048 Lecture 1", "Constant coefficient ODEs"]
date: 2026-10-30
status: lectured
coverage: "Lecture 1 (30 Sep 2024, Ian Hawke): module introduction, linear ODEs, the particular-integral substitution, constant-coefficient ODEs and the three root cases. Slides 10–12 (mass–spring–damper) and the slide-14 homework."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: []
next_topics: ["[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
key_concepts: ["[[Auxiliary Equation]]", "[[Damping Ratio and Natural Frequency]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 1.txt", "02 - Sources/Lectures & Problem Sheets/ODEs/Lecture1_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix-solution ODE with repeated roots.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.1.1)"]
---

# MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients

> [!abstract] Summary
> A linear second-order ODE $y''+p(x)y'+q(x)y=r(x)$ can always be reduced to a homogeneous one by subtracting any particular integral, and the homogeneous solution is a sum of two independent solutions with arbitrary constants. With constant coefficients, $ay''+by'+cy=0$, the guess $y=e^{\lambda x}$ turns the ODE into the quadratic auxiliary equation $a\lambda^2+b\lambda+c=0$, and the sign of $b^2-4ac$ picks one of three solution forms: two exponentials, $(c_1+c_2x)e^{\lambda x}$, or $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$.

> [!summary]- Exam use: quick path
> - **Use it when:** an ODE has the form $ay''+by'+cy=0$ (or that left-hand side with a source), on its own or as the spatial or time ODE after separating a PDE.
> - **Assumptions:** linear, constant $a\neq0$, $b$, $c$; homogeneous (deal with any source by subtracting a particular integral first, [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs|ODE2]]); $j=\sqrt{-1}$ (STACK uses $i$).
> - **Method:** 1. Write the auxiliary equation $a\lambda^2+b\lambda+c=0$. 2. Classify by $b^2-4ac$. 3. Write the matching general solution from the table in §2. 4. Differentiate once if a condition involves $y'$. 5. Apply the conditions to find $c_1$, $c_2$.
> - **Common mistakes:** writing $(c_1+c_2x)e^{\lambda x}$ only when the roots are genuinely repeated, and forgetting it then; dropping the $-e^{-x}$ part of the product rule when differentiating $e^{-x}\cos2x$ for an initial condition.
> - **Practise:** [[#An initial value problem with complex roots]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q1: Constant coefficients|PS1 Q1]]

The module is about partial differential equations, the Navier–Stokes, Navier–Cauchy and Maxwell equations being the motivation, but the method it builds towards, separation of variables, works by reducing a PDE to several ordinary differential equations that we already know how to solve (L1, ll. 52–64). So the first week is a fast recap of first-year ODEs, and the lecturer was clear that it is meant to be familiar: "if you don't remember it then please practice that like now instantly" (ll. 428–431).

Linear ODEs are the ones we can actually solve. The unknown $y$ only ever appears on its own or differentiated, multiplied by known functions of $x$, so two solutions of the homogeneous equation can be added to give another. That makes the homogeneous problem the one to master, and a single trick, subtracting any particular solution, reduces every inhomogeneous problem to it.

With constant coefficients the solutions are exponentials, because an exponential is the one function whose derivatives are multiples of itself. The guess $y=e^{\lambda x}$ therefore turns a differential equation into a quadratic, and the three kinds of root of a quadratic give the three kinds of behaviour: pure growth or decay, the borderline repeated case, and oscillation inside an exponential envelope. The lecturer's reason for caring about constant coefficients in a module full of variable-coefficient physics is that any smooth problem looks constant-coefficient in a small enough region, so this case always gives the first look at local behaviour (ll. 335–339).

---

## 1. Linear ODEs, and why homogeneous problems are enough (L1)

The general linear second-order ODE, divided through by the coefficient of $y''$, is

$$
y''+p(x)\,y'+q(x)\,y=r(x).
$$

It is linear because $y$ appears only as $y$, $y'$ or $y''$, each multiplied by a known function of $x$; a term such as $y^2$ or $yy'$ would make it nonlinear and much harder (ll. 238–250). It is **homogeneous** when $r\equiv0$ and inhomogeneous otherwise, with $r$ the source or forcing term.

### Removing the source with any particular integral

Suppose $y_{PI}$ is a **particular integral**: any one function that satisfies the full equation. It doesn't have to satisfy the boundary or initial conditions or be physically sensible, "it can be total nonsense as long as it solves the differential equation" (ll. 264–276). Define

$$
v=y-y_{PI}.
$$

Substitute into the left-hand side:

$$
v''+pv'+qv=(y''-y_{PI}'')+p(y'-y_{PI}')+q(y-y_{PI})
$$

$$
=\big(y''+py'+qy\big)-\big(y_{PI}''+py_{PI}'+qy_{PI}\big)
$$

$$
=r-r
$$

$$
=0.
$$

So $v$ satisfies the homogeneous equation, and solving the inhomogeneous problem comes down to finding one particular integral and then solving a homogeneous problem (ll. 277–290). The lecturer stressed that the same trick works for linear PDEs, which is how it will be used in [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions|PDE4]] (l. 286).

### The general solution and how many conditions fix it

For the homogeneous second-order equation the general solution is

$$
y=c_1y_1(x)+c_2y_2(x),
$$

where $y_1$ and $y_2$ are **linearly independent** solutions (neither is a constant multiple of the other: $c_1y_1+c_2y_2\equiv0$ only when $c_1=c_2=0$). With a source, the general solution is that plus $y_{PI}$, which carries no constant (ll. 291–296). An $n$th-order linear ODE has $n$ independent solutions and so $n$ arbitrary constants (ll. 297–305), and fixing them takes $n$ independent conditions: for second order, two, either the value and derivative at one point or values or derivatives at two points (ll. 312–321). Which of these it is matters a great deal, as [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems|ODE3]] shows.

The lecture notes add, as non-examinable background, that independence can be tested with the Wronskian $W=y_1y_2'-y_1'y_2$, which satisfies $W'+pW=0$ and so is either zero everywhere or nowhere.

## 2. Constant coefficients: the auxiliary equation

For

$$
ay''+by'+cy=0\qquad(a,b,c\ \text{constant},\ a\neq0),
$$

guess an exponential (the "Ansatz", German for an educated guess, ll. 341–343):

$$
y=e^{\lambda x}.
$$

Each derivative brings down a factor $\lambda$:

$$
y'=\lambda e^{\lambda x},\qquad y''=\lambda^2e^{\lambda x}.
$$

Substitute:

$$
a\lambda^2e^{\lambda x}+b\lambda e^{\lambda x}+ce^{\lambda x}=0
$$

$$
\big(a\lambda^2+b\lambda+c\big)e^{\lambda x}=0.
$$

The exponential is never zero, so the bracket must vanish (ll. 351–356). This is the **auxiliary equation**,

$$
a\lambda^2+b\lambda+c=0\quad\Longrightarrow\quad \lambda=\frac{-b\pm\sqrt{b^2-4ac}}{2a}.
$$

An $n$th-order constant-coefficient ODE gives an $n$th-degree polynomial in the same way, "which is obviously highly not fun when you get beyond quadratic" (ll. 357–360).

| Discriminant | Roots | Independent solutions | General solution |
|---|---|---|---|
| $b^2-4ac>0$ | real, distinct $\lambda_1\neq\lambda_2$ | $e^{\lambda_1x},\ e^{\lambda_2x}$ | $c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $b^2-4ac=0$ | real, repeated $\lambda=-\frac{b}{2a}$ | $e^{\lambda x},\ x\,e^{\lambda x}$ | $(c_1+c_2x)e^{\lambda x}$ |
| $b^2-4ac<0$ | complex, $\alpha\pm j\beta$ | $e^{\alpha x}\cos\beta x,\ e^{\alpha x}\sin\beta x$ | $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |

Three special cases come up constantly in the PDE block. $y''+k^2y=0$ has $\lambda=\pm jk$ and $y=c_1\cos kx+c_2\sin kx$. $y''-k^2y=0$ has $\lambda=\pm k$ and $y=c_1e^{kx}+c_2e^{-kx}$, which is the same as $A\cosh kx+B\sinh kx$; the hyperbolic form is usually easier when a condition sits at $x=0$. And if $c=0$ one root is $\lambda=0$, giving a constant solution: $y''-3y'=0$ has $y=c_1+c_2e^{3x}$.

Throughout the module $j$ denotes $\sqrt{-1}$, the engineering convention. The STACK coursework system was "written by mathematicians" and uses $i$, so answers there have to be translated (ll. 400–412).

### Repeated roots and the second solution

With a repeated root the quadratic gives only one exponential, so a second independent solution has to come from somewhere else. The lecturer was explicit that it doesn't follow from the quadratic or the guess, only from the ODE together with the vanishing discriminant, and that you check it once and quote it thereafter (ll. 384–397).

A repeated root means $b^2=4ac$ and $\lambda=-b/(2a)$, so

$$
2a\lambda+b=0.
$$

Try $y=xe^{\lambda x}$:

$$
y'=(1+\lambda x)e^{\lambda x},
$$

$$
y''=\lambda e^{\lambda x}+\lambda(1+\lambda x)e^{\lambda x}=(2\lambda+\lambda^2x)e^{\lambda x}.
$$

Substitute and collect the terms with and without $x$:

$$
ay''+by'+cy=e^{\lambda x}\big[a(2\lambda+\lambda^2x)+b(1+\lambda x)+cx\big]
$$

$$
=e^{\lambda x}\big[x(a\lambda^2+b\lambda+c)+(2a\lambda+b)\big]
$$

$$
=e^{\lambda x}\big[x\cdot0+0\big]=0.
$$

The first bracket vanishes because $\lambda$ is a root, the second because the root is repeated. For distinct roots $2a\lambda+b\neq0$, which is why $xe^{\lambda x}$ is not a solution then. The two solutions are independent, since $c_1e^{\lambda x}+c_2xe^{\lambda x}\equiv0$ means $c_1+c_2x\equiv0$ for all $x$, forcing $c_1=c_2=0$.

The appendix on repeated roots reaches the same answer by reduction of order: put $y=v(x)e^{\lambda x}$ into $y''-2\lambda y'+\lambda^2y=0$, and everything cancels except $v''e^{\lambda x}=0$, so $v=c_1+c_2x$.

### Complex roots: from exponentials to cosine and sine (the L1 homework)

The slide-14 homework asks why complex roots give cosines and sines. Start from the two exponential solutions with arbitrary, possibly complex, constants $A$ and $B$:

$$
y=Ae^{(\alpha+j\beta)x}+Be^{(\alpha-j\beta)x}.
$$

Split each exponent:

$$
y=e^{\alpha x}\big(Ae^{j\beta x}+Be^{-j\beta x}\big).
$$

Use Euler's formula, $e^{\pm j\theta}=\cos\theta\pm j\sin\theta$:

$$
y=e^{\alpha x}\big[A(\cos\beta x+j\sin\beta x)+B(\cos\beta x-j\sin\beta x)\big]
$$

$$
=e^{\alpha x}\big[(A+B)\cos\beta x+j(A-B)\sin\beta x\big].
$$

Rename the constants:

$$
y=e^{\alpha x}\big(c_1\cos\beta x+c_2\sin\beta x\big),\qquad c_1=A+B,\ c_2=j(A-B).
$$

For a real solution $B=\bar A$, and then $c_1=2\,\mathrm{Re}\,A$ and $c_2=-2\,\mathrm{Im}\,A$ are both real. The slide's plot of $y=\tfrac23e^{-x/5}\cos x+\tfrac13e^{-x/5}\sin x$ shows the decaying oscillation; the decay comes entirely from the real part $\alpha$, which comes from the $by'$ term, the friction.

## 3. The mass–spring–damper (slides 10–12)

The slides end with the standard physical example; it was not talked through in the recording, which stops after the three root cases. A mass $m$ on a spring of stiffness $k$ with friction obeys Newton's second law

$$
m\ddot y+2c\dot y+ky=0,
$$

or, dividing by $m$ and writing $\omega_0=\sqrt{k/m}$ for the natural frequency,

$$
\ddot y+\frac{2c}{m}\dot y+\omega_0^2y=0.
$$

This is constant-coefficient with $a=1$, $b=2c/m$ and $c\to\omega_0^2$, so the auxiliary equation $\lambda^2+\frac{2c}{m}\lambda+\omega_0^2=0$ has roots

$$
\lambda_{1,2}=-\frac cm\pm\sqrt{\frac{c^2}{m^2}-\omega_0^2}.
$$

Which case applies depends on the friction. With $c<m\omega_0$ the square root is imaginary, the roots are $-c/m\pm j\omega$ with $\omega=\sqrt{\omega_0^2-c^2/m^2}$, and the motion is a damped oscillation,

$$
y=e^{-ct/m}\big(c_1\cos\omega t+c_2\sin\omega t\big).
$$

With $c=m\omega_0$ the root $-c/m$ is repeated and $y=(c_1+c_2t)e^{-ct/m}$, critical damping: the fastest return to rest without oscillating. With $c>m\omega_0$ both roots are real and negative, and the mass creeps back without oscillating (over-damped).

![[m2048_ode_damping_regimes.png|640]]

Writing $c/m=\zeta\omega_0$ gives the SESA2027 form $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y=0$, so this auxiliary equation is the characteristic equation of [[Damping Ratio and Natural Frequency]] and its roots are the poles $\sigma\pm j\omega_d$.

## 4. Worked examples

### One of each case

| ODE | Auxiliary equation | Roots | General solution |
|---|---|---|---|
| $y''-3y'+2y=0$ | $(\lambda-1)(\lambda-2)=0$ | $1,\ 2$ | $c_1e^x+c_2e^{2x}$ |
| $y''-6y'+9y=0$ | $(\lambda-3)^2=0$ | $3$ (repeated) | $(c_1+c_2x)e^{3x}$ |
| $y''+4y'+13y=0$ | $\lambda=\frac{-4\pm\sqrt{16-52}}{2}$ | $-2\pm3j$ | $e^{-2x}(c_1\cos3x+c_2\sin3x)$ |

All three were checked with SymPy's `dsolve`. The first and third are PS1 Q1(a) and (b).

### An initial value problem with complex roots

*(Suggested, not lecturer-set.)* Solve $y''+2y'+5y=0$ with $y(0)=1$ and $y'(0)=3$.

The auxiliary equation is $\lambda^2+2\lambda+5=0$, so

$$
\lambda=\frac{-2\pm\sqrt{4-20}}{2}=-1\pm2j,
$$

giving $\alpha=-1$, $\beta=2$ and the general solution

$$
y=e^{-x}(c_1\cos2x+c_2\sin2x).
$$

Differentiate with the product rule:

$$
y'=-e^{-x}(c_1\cos2x+c_2\sin2x)+e^{-x}(-2c_1\sin2x+2c_2\cos2x)
$$

$$
=e^{-x}\big[(2c_2-c_1)\cos2x-(c_2+2c_1)\sin2x\big].
$$

Apply the conditions:

$$
y(0)=c_1=1,
$$

$$
y'(0)=2c_2-c_1=3\quad\Longrightarrow\quad c_2=2.
$$

So

$$
y=e^{-x}(\cos2x+2\sin2x).
$$

> [!check] SymPy
> `dsolve` with these initial conditions returns $(2\sin2x+\cos2x)e^{-x}$, and $y(0)=1$, $y'(0)=-1+4=3$.

## Transcript slips

> [!warning] Lecture 1 transcript slips
> | Where | Transcript says | Correct |
> |---|---|---|
> | l. 19 | "Navier-Kauchy equations" | Navier–Cauchy |
> | l. 120 | "CrySig" | Kreyszig (the recommended textbook) |
> | l. 253 | "the R… banishes" | vanishes |
> | l. 383 | the repeated root is "minus b over 2x" | $-b/(2a)$; the lecturer said $-b/2a$ correctly at l. 380 |
> | ll. 342, 388 | "ANZATs" | Ansatz (plural Ansätze) |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Next: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]
- Used in [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] and in every separation-of-variables PDE ([[MATH2048 PDE2 - Separation of Variables for the Wave Equation|PDE2]], [[MATH2048 PDE3 - The Heat Equation|PDE3]], [[MATH2048 PDE5 - Laplace's Equation|PDE5]]).
- Concepts: [[Auxiliary Equation]] · [[Damping Ratio and Natural Frequency]] (SESA2027) · [[Characteristic Equation and Eigenvalues]] (SESA2027)

## Sources

- Lecture 1 recording, 30 Sep 2024 (Ian Hawke): `MATH2048 Lecture 1.txt`
- Slides `Lecture1_ODE.pdf` (Dias / Richardson / Gan); appendices on Lectures 1–2 and on repeated roots (K. Ashari)
- Lecture notes §1.1.1
- Problem Sheet 1 Q1; worked solutions in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]

## Self-study tasks

Lecture 1 set one homework, the slide-14 derivation for complex roots, and otherwise pointed at the problem sheets and the first STACK assignment: "there's a bunch of problems on the weekly problem sheets along that line" (ll. 432–434).

### Core

- [ ] Lecturer-set (slide 14 homework): starting from $Ae^{(\alpha+j\beta)x}+Be^{(\alpha-j\beta)x}$, derive $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ and show $c_1$, $c_2$ are real when $B=\bar A$. → [[#Complex roots: from exponentials to cosine and sine (the L1 homework)]]
- [ ] Show directly that $xe^{\lambda x}$ solves $ay''+by'+cy=0$ when $\lambda$ is a repeated root, and say which step fails for distinct roots (L1, ll. 384–397). → [[#Repeated roots and the second solution]]
- [ ] PS1 Q1(a)–(d). → [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q1: Constant coefficients]]

### Further practice

- [ ] PS2 Q1(a)–(d), initial value problems for each root type. → [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q1: Initial value problems]]
- [ ] Derive the three damping regimes of $m\ddot y+2c\dot y+ky=0$ and sketch each (suggested, not lecturer-set). → [[#3. The mass–spring–damper (slides 10–12)]]
- [ ] Show that $v=y-y_{PI}$ satisfies the homogeneous equation, then explain why it doesn't matter which particular integral you use (suggested, not lecturer-set). → [[#Removing the source with any particular integral]]
