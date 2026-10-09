---
title: "MATH1054 M06 Solutions - Differential Equations I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 3: Differential Equations"
tags:
  - math1054
  - tutorial-solutions
  - odes
sheet: "Module 06 work scheme: Examples 10.1–10.13, 10.34–10.36; Exercises 2, 3, 4, 11–14, 55–59; Specimen Test 6"
theory_notes: ["[[MATH1054 M06 - Differential Equations I]]"]
key_concepts: ["[[Classification of Differential Equations]]", "[[Separable First-Order ODEs]]", "[[Auxiliary Equation]]"]
status: complete
sources: ["tmp/md/module_06_differential_equations_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§10.2–10.5, §10.9)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 6)"]
---

# MATH1054 M06 Solutions - Differential Equations I

> [!abstract] Sheet Info
> This note covers the whole Module 06 work scheme plus Specimen Test 6. Every solution was checked with SymPy `dsolve` (with `ics` for the IVPs and BVPs). The notation follows James: $x(t)$ is the dependent variable and $t$ the independent one, unless the question says otherwise. $A$, $B$ and $C$ are arbitrary constants.

## Theory Links
- [[MATH1054 M06 - Differential Equations I]] · [[Classification of Differential Equations]] · [[Separable First-Order ODEs]] · [[Auxiliary Equation]]

---

# Part A: Worked examples

## Examples 10.1–10.4: The classification vocabulary
These four examples define the terms. Here they are applied to each equation.

| Equation | Dependent / independent variable | Order | Linear? | Homogeneous? |
|---|---|---|---|---|
| $f''-4xf'=\cos2x$ | $f$ / $x$ | 2 | yes | no (the $\cos2x$ term is free of $f$) |
| coupled $4\dot x+3\dot y-x+2y=\cos t$, … | $x,y$ / $t$ | 1 | yes | no |
| $(\dot x)^2+4\dot x=0$ | $x$ / $t$ | 1 (the *highest derivative* is first order; its power doesn't matter) | **no**, $\dot x$ is squared | — |
| $\ddot x+x\dot x=4\sin t$ | $x$ / $t$ | 2 | **no**, the product $x\dot x$ | — |
| $4\dot x+\sin x=0$ | $x$ / $t$ | 1 | **no**, $\sin x$ | — |
| $\dot x+4x=0$ | $x$ / $t$ | 1 | yes | yes |
| $4\dot x+(\sin t)x=0$ | $x$ / $t$ | 1 | yes (coefficients *may* depend on $t$) | yes |
| $\ddot x+t\dot x=4\sin t$ | $x$ / $t$ | 2 | yes | no |

> [!note] The rules
> - **Order**: the highest derivative present.
> - **Linear**: $x$ and its derivatives appear only to the first power, never multiplied together, and never inside a function such as $\sin x$ or $e^x$. The coefficients may be any functions of $t$.
> - **Homogeneous** (linear equations only): every term contains $x$ or a derivative of $x$. There is no "forcing" term that is a function of $t$ alone.

## Example 10.5: Classify (10.3), (10.6), (10.7), (10.9)
| Equation | Model | Classification |
|---|---|---|
| (10.3) $m\ddot s-(\mu\alpha-\beta)\dot s^{\,2}=T-\mu mg$ | vehicle with drag | 2nd order, **nonlinear** ($\dot s^2$); $s$ dependent, $t$ independent |
| (10.6) $V\dot T_w+AU_aT_w=AU_aT_{\text{in}}$ | water-heater temperature | 1st order, **linear, nonhomogeneous** (forced by $T_{\text{in}}$); $T_w$ dependent, $t$ independent |
| (10.7) $\frac{\rho d}{A}\dot Q+(\alpha+\beta+\gamma)\frac{\rho}{2A^2}Q^2=\rho gh$ | pipe flow with losses | 1st order, **nonlinear** ($Q^2$); $Q$ dependent, $t$ independent |
| (10.9) $L\ddot i+R\dot i+\frac1Ci=0$ | LRC circuit | 2nd order, **linear, homogeneous**, constant coefficients; $i$ dependent, $t$ independent |

## Example 10.6: $\dot x=-4x$
Try $x=e^{-4t}$. Then $\dot x=-4e^{-4t}=-4x$ ✔. In fact $x=Ae^{-4t}$ works for **any** constant $A$, because the equation is linear and homogeneous. This is the general solution, with one constant for a first-order equation.

## Example 10.7: $\ddot x+\lambda^2x=0$
- $x=\sin\lambda t$ gives $\ddot x=-\lambda^2\sin\lambda t=-\lambda^2x$ ✔.
- $\cos\lambda t$ works in the same way.
- So the general solution is $x=A\sin\lambda t+B\cos\lambda t$: two constants for a second-order equation. This is **simple harmonic motion** with angular frequency $\lambda$.

## Example 10.8: $\ddot x=t-3e^{3t}$
The right-hand side depends only on $t$, so integrate twice:

$$\dot x=\tfrac12t^2-e^{3t}+A,\qquad \boxed{x=\tfrac16t^3-\tfrac13e^{3t}+At+B}$$

## Example 10.9: $\dot x=-4x$, $x(0)=2.5$
The general solution is $x=Ae^{-4t}$. At $t=0$, $A=2.5$, so $\boxed{x=2.5e^{-4t}}$.

## Example 10.10: IVP $\ddot x+\lambda^2x=0$, $x(0)=4$, $\dot x(0)=3$
- Start from $x=A\sin\lambda t+B\cos\lambda t$, so $\dot x=\lambda A\cos\lambda t-\lambda B\sin\lambda t$.
- $x(0)=B=4$.
- $\dot x(0)=\lambda A=3$, so $A=3/\lambda$.

$$\boxed{x=\frac3\lambda\sin\lambda t+4\cos\lambda t}$$

## Example 10.11: BVP with $x(0)=4$, $\dot x(\pi/\lambda)=3$
- $x(0)=B=4$.
- $\dot x(\pi/\lambda)=\lambda A\cos\pi-\lambda B\sin\pi=-\lambda A=3$, so $A=-3/\lambda$.

$$\boxed{x=-\frac3\lambda\sin\lambda t+4\cos\lambda t}$$

The conditions are applied at two different times, which makes this a **boundary-value problem**. Here it has a unique solution. Compare this with the eigenvalue problems in MATH2048 ([[Boundary Value Problems]]).

## Example 10.13: $\dot x=4xt$, $x>0$ (separable)
Separate the variables and integrate:

$$\int\frac{\mathrm dx}{x}=\int4t\,\mathrm dt\ \Rightarrow\ \ln x=2t^2+c$$

$$\boxed{x=Ae^{2t^2}}\quad(A=e^c>0)$$

## Example 10.34: $\ddot x-9\dot x+6x=0$
Try $x=e^{mt}$. The auxiliary equation is $m^2-9m+6=0$, so

$$m=\frac{9\pm\sqrt{81-24}}2=\frac{9\pm\sqrt{57}}2.$$

These are real and distinct:

$$\boxed{x=Ae^{\frac{9+\sqrt{57}}2t}+Be^{\frac{9-\sqrt{57}}2t}}\approx Ae^{8.27t}+Be^{0.725t}$$

## Example 10.35: $2\ddot x-3\dot x+5x=0$
The auxiliary equation is $2m^2-3m+5=0$, so

$$m=\frac{3\pm\sqrt{9-40}}4=\frac34\pm\mathrm j\frac{\sqrt{31}}4.$$

Complex roots $\alpha\pm\mathrm j\beta$ give $x=e^{\alpha t}(A\cos\beta t+B\sin\beta t)$:

$$\boxed{x=e^{3t/4}\Big(A\cos\tfrac{\sqrt{31}}4t+B\sin\tfrac{\sqrt{31}}4t\Big)}$$

Since $\alpha>0$, this is a growing oscillation.

## Example 10.36: IVP $\ddot x+6\dot x+9x=0$, $x(0)=1$, $\dot x(0)=2$
- The auxiliary equation is $(m+3)^2=0$, a repeated root $m=-3$. So $x=(A+Bt)e^{-3t}$.
- Then $\dot x=(B-3A-3Bt)e^{-3t}$.
- $x(0)=A=1$, and $\dot x(0)=B-3=2$, so $B=5$.

$$\boxed{x=(1+5t)e^{-3t}}$$

This is **critical damping**: a single overshoot hump, then decay without oscillation.

---

# Part B: Assigned exercises

## Exercise 2 (p.799): Classification
| | Equation | Order | Type | Dependent / independent |
|---|---|---|---|---|
| (a) | $p''\,p'+(\sin z)p=\ln z$ | 2 | **nonlinear** (the product $p''p'$) | $p$ / $z$ |
| (b) | $s''+(\sin t)s'+(t+\cos t)s=e^t$ | 2 | **linear, nonhomogeneous** (forcing $e^t$) | $s$ / $t$ |
| (f) | $\dot x=f(t)x+g(t)$ | 1 | **linear**: nonhomogeneous if $g\not\equiv0$, homogeneous if $g\equiv0$ | $x$ / $t$ |

## Exercise 3 (p.805): General solutions and counting constants
**(a)** $\dot x=4t^2$. This is first order, so expect **1** constant.

$$x=\tfrac43t^3+A$$

One constant ✔.

**(e)** $\dddot x=\dfrac2{t^3}+\sin5t$. This is third order, so expect **3** constants. Integrate three times:
- $\ddot x=-\dfrac1{t^2}-\tfrac15\cos5t+A$
- $\dot x=\dfrac1t-\tfrac1{25}\sin5t+At+B$
- $x=\ln|t|+\tfrac1{125}\cos5t+\tfrac12At^2+Bt+C$

$$\boxed{x=\ln|t|+\tfrac1{125}\cos5t+A't^2+Bt+C}$$

Three constants ✔ (with $A'=A/2$).

## Exercise 4 (p.805): Constants left after the conditions
**(a)** $\ddot x=4t$ with $x(0)=2$. There are 2 constants, and 1 condition removes one, so expect **1** to remain.
- $x=\tfrac23t^3+At+B$, and $x(0)=B=2$.

$$\boxed{x=\tfrac23t^3+At+2}$$

One arbitrary constant remains ✔.

**(b)** $\ddot x=\sin2t$ with $x(\frac\pi4)=2$ and $x(\frac{3\pi}4)=2$. There are 2 constants and 2 conditions, so expect **0**.
- $x=-\tfrac14\sin2t+At+B$.
- $x(\frac\pi4)$: $-\tfrac14+\frac\pi4A+B=2$.
- $x(\frac{3\pi}4)$: $+\tfrac14+\frac{3\pi}4A+B=2$.
- Subtracting: $\tfrac12+\tfrac\pi2A=0$, so $A=-\tfrac1\pi$. Then $B=2+\tfrac14+\tfrac14=\tfrac52$.

$$\boxed{x=\tfrac52-\frac t\pi-\tfrac14\sin2t}$$

There are no arbitrary constants left ✔.

## Exercise 11(b) (p.811): $\dot x=6xt^2$

$$\int\frac{\mathrm dx}x=\int6t^2\,\mathrm dt\ \Rightarrow\ \ln|x|=2t^3+c\ \Rightarrow\ \boxed{x=Ae^{2t^3}}$$

The solution $x\equiv0$ (lost when dividing by $x$) is recovered by taking $A=0$.

## Exercise 12(b): $t^2\dot x=1/x$, $x(4)=9$
Separate and integrate:

$$\int x\,\mathrm dx=\int t^{-2}\,\mathrm dt\ \Rightarrow\ \tfrac12x^2=-\frac1t+C$$

At $t=4$: $\tfrac{81}2=-\tfrac14+C$, so $C=\tfrac{163}4$. Then

$$x^2=\frac{163}2-\frac2t.$$

Take the positive root because $x(4)=9>0$:

$$\boxed{x=\sqrt{\frac{163}2-\frac2t}}$$

## Exercise 13(a): $\sqrt t\,\dot x=\sqrt x$

$$\int x^{-1/2}\,\mathrm dx=\int t^{-1/2}\,\mathrm dt\ \Rightarrow\ 2\sqrt x=2\sqrt t+2c\ \Rightarrow\ \boxed{x=(\sqrt t+c)^2}$$

Also $x\equiv0$ is a singular solution, lost when dividing by $\sqrt x$.

## Exercise 14: Initial-value problems
**(a)** $\dot x=\dfrac{t^2+1}{x+2}$, $x(0)=-2$:

$$\int(x+2)\,\mathrm dx=\int(t^2+1)\,\mathrm dt\ \Rightarrow\ \tfrac12(x+2)^2=\tfrac13t^3+t+C$$

The condition gives $C=0$, so $(x+2)^2=\tfrac23t^3+2t$ and

$$\boxed{x=-2\pm\sqrt{\tfrac23t^3+2t}}\qquad(t\ge0)$$

> [!warning] Two solutions
> At the initial point $x+2=0$, so $\dot x$ is infinite: the right-hand side is singular. Both signs satisfy the ODE and the condition, so this IVP does **not** have a unique solution. The uniqueness theorem needs the right-hand side to be well behaved at $(t_0,x_0)$.

**(d)** $\dot x=e^{x+t}=e^xe^t$, $x(0)=a$:

$$\int e^{-x}\,\mathrm dx=\int e^t\,\mathrm dt\ \Rightarrow\ -e^{-x}=e^t+C$$

At $t=0$: $-e^{-a}=1+C$, so $C=-1-e^{-a}$. Then $e^{-x}=1+e^{-a}-e^t$, and

$$\boxed{x=-\ln\big(1+e^{-a}-e^t\big)}$$

This is valid only while $e^t<1+e^{-a}$, that is, $t<\ln(1+e^{-a})$. The solution **blows up** ($x\to\infty$) in finite time.

## Exercise 55(a) (p.856): $2\ddot x-5\dot x+3x=0$
The auxiliary equation is $2m^2-5m+3=(2m-3)(m-1)=0$, so $m=1,\tfrac32$:

$$\boxed{x=Ae^t+Be^{3t/2}}$$

## Exercise 56(a): $5\ddot x-3\dot x-2x=0$, $x(0)=-1$, $\dot x(0)=1$
- The auxiliary equation is $5m^2-3m-2=(5m+2)(m-1)=0$, so $m=1,-\tfrac25$ and $x=Ae^t+Be^{-2t/5}$.
- The conditions give $A+B=-1$ and $A-\tfrac25B=1$.
- Subtracting: $\tfrac75B=-2$, so $B=-\tfrac{10}7$ and $A=\tfrac37$.

$$\boxed{x=\tfrac37e^t-\tfrac{10}7e^{-2t/5}}$$

## Exercise 57
**(b)** $\ddot x+6\dot x-4x=0$ gives $m^2+6m-4=0$, so $m=-3\pm\sqrt{13}$:

$$\boxed{x=Ae^{(-3+\sqrt{13})t}+Be^{(-3-\sqrt{13})t}}$$

**(d)** $\ddot x-8\dot x+16x=0$ gives $(m-4)^2=0$, a repeated root:

$$\boxed{x=(A+Bt)e^{4t}}$$

## Exercise 59
**(a)** $2\ddot x-2\dot x+3x=0$, $x(0)=1$, $\dot x(0)=0$.
- The auxiliary equation is $2m^2-2m+3=0$, so $m=\dfrac{2\pm\sqrt{4-24}}4=\tfrac12\pm\mathrm j\tfrac{\sqrt5}2$.
- So $x=e^{t/2}(A\cos\omega t+B\sin\omega t)$ with $\omega=\tfrac{\sqrt5}2$.
- $x(0)=A=1$.
- $\dot x(0)=\tfrac12A+\omega B=0$, so $B=-\dfrac{1}{2\omega}=-\dfrac1{\sqrt5}$.

$$\boxed{x=e^{t/2}\Big(\cos\tfrac{\sqrt5}2t-\tfrac1{\sqrt5}\sin\tfrac{\sqrt5}2t\Big)}$$

**(b)** $\ddot x-4\dot x+4x=0$, $x(1)=0$, $\dot x(1)=2$.
- The root is repeated, $m=2$. Because the data are given at $t=1$, write the solution in powers of $(t-1)$: $x=\big[A+B(t-1)\big]e^{2(t-1)}$.
- $x(1)=A=0$.
- $\dot x=\big[B+2A+2B(t-1)\big]e^{2(t-1)}$, so $\dot x(1)=B=2$.

$$\boxed{x=2(t-1)e^{2(t-1)}}$$

---

# Part C: Specimen Test 6

## Q1: Classification
| | Equation | ODE/PDE | Linear? | Homogeneous? | Order | Dependent / independent |
|---|---|---|---|---|---|---|
| (i) | $\dot x+\frac1tx=1$ | ODE | linear | **inhomogeneous** (the "1") | 1 | $x$ / $t$ |
| (ii) | $y_{xx}-y_{tt}=0$ | **PDE** (the wave equation) | linear | homogeneous | 2 | $y$ / $x,t$ |
| (iii) | $xy''+x^2y'+y=0$ | ODE | linear (variable coefficients are allowed) | homogeneous | 2 | $y$ / $x$ |

## Q2: $\ddot x=t+e^{2t}$
This is second order, so expect **two** arbitrary constants. Integrate twice:
- $\dot x=\tfrac12t^2+\tfrac12e^{2t}+A$

$$\boxed{x=\tfrac16t^3+\tfrac14e^{2t}+At+B}$$

## Q3
**(i)** $xt\,\dot x=1$ is separable:

$$\int x\,\mathrm dx=\int\frac{\mathrm dt}t\ \Rightarrow\ \tfrac12x^2=\ln|t|+C\ \Rightarrow\ \boxed{x^2=2\ln|t|+A}$$

**(ii)** $\dot x=\dfrac{t+1}{x+1}$, $x(0)=1$:

$$\int(x+1)\,\mathrm dx=\int(t+1)\,\mathrm dt\ \Rightarrow\ \tfrac12(x+1)^2=\tfrac12(t+1)^2+C$$

At $t=0$: $2=\tfrac12+C$, so $C=\tfrac32$. Then $(x+1)^2=(t+1)^2+3$. Take the positive root, since $x+1=2>0$ at $t=0$:

$$\boxed{x=\sqrt{t^2+2t+4}-1}$$

## Q4
**(i)** $\ddot x-4\dot x+13x=0$ gives $m^2-4m+13=0$, so $m=2\pm3\mathrm j$:

$$\boxed{x=e^{2t}(A\cos3t+B\sin3t)}$$

**(ii)** $y''-2y'+y=0$ gives $(m-1)^2=0$:

$$\boxed{y=(A+Bx)e^{x}}$$

## Q5: $\ddot x+3\dot x+2x=0$, $x(0)=1$, $\dot x(0)=-1$
- $(m+1)(m+2)=0$, so $x=Ae^{-t}+Be^{-2t}$.
- The conditions give $A+B=1$ and $-A-2B=-1$. Adding: $-B=0$, so $B=0$ and $A=1$.

$$\boxed{x=e^{-t}}$$

The initial slope $-1$ exactly matches the slow mode $e^{-t}$, so the fast mode is never excited.

## Sources
- Transcribed problem statements: `tmp/md/module_06_differential_equations_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §10.2–10.5, §10.9; MATH1054 Module Booklet, Module 6
