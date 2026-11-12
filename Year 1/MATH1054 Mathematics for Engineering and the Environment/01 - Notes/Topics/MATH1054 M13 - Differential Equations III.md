---
title: "MATH1054 M13 - Differential Equations III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 3: Differential Equations"
order: 13
tags:
  - math1054
  - odes
  - constant-coefficients
  - damping
aliases: ["MATH1054 Module 13", "Differential Equations III"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 13 work scheme and Specimen Test 13; James §10.8 (linear operators, linearity principle, linear independence, CF + PI), §10.9.1 (characteristic equation of any order), §10.9.3 (undetermined coefficients, superposition of forcing, the clash case), §10.10.1–10.10.4 (free and forced oscillations, damping parameter, natural frequency, resonance, LCR circuit)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M06 - Differential Equations I]]", "[[MATH1054 M12 - Differential Equations II]]"]
next_topics: ["[[MATH1054 M14 - Vectors I]]"]
key_concepts: ["[[Linear Differential Operators and Superposition]]", "[[Auxiliary Equation]]", "[[Method of Undetermined Coefficients]]", "[[Damping Ratio and Natural Frequency]]", "[[Resonance]]"]
tutorial_sheets: ["[[MATH1054 M13 Solutions - Differential Equations III]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 13)", "02 - Sources/Modern Engineering Mathematics.pdf (§10.8–10.10)"]
---

# MATH1054 M13 - Differential Equations III

> [!abstract] Summary
> A linear differential operator $\mathrm L$ satisfies $\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2]$, and from that one property the general solution of $\mathrm L[x]=f$ is the complementary function (the general solution of $\mathrm L[x]=0$) plus any one particular integral. With constant coefficients the trial $e^{mt}$ turns the ODE into the polynomial equation $P(m)=0$ of any order, and the particular integral comes from a trial function shaped like the forcing, multiplied by $t^s$ when the forcing already sits in the complementary function. Written as $\ddot x+2\zeta\omega\dot x+\omega^2x=F\cos\Omega t$, a damped second-order system is classified by its damping parameter $\zeta$ and natural frequency $\omega$: the complementary function is the decaying transient and the particular integral is the steady state of amplitude $F/\sqrt{(\omega^2-\Omega^2)^2+4\zeta^2\omega^2\Omega^2}$.

> [!summary]- Exam use: quick path
> - **Use it when:** a linear ODE of any order with constant coefficients has polynomial, exponential, sine or cosine forcing (or a sum of these), or a damped oscillator has to be classified by $\omega$ and $\zeta$.
> - **Assumptions:** real constant coefficients; the forcing is one of the standard types; conditions are applied to the full solution, never to the complementary function alone.
> - **Method:** 1. Solve $P(m)=0$ and write the CF. 2. Pick the trial PI from the forcing, both $\cos$ and $\sin$ for trig forcing, and multiply by $t^s$ if the trial is in the CF ($s$ = multiplicity of the root). 3. Substitute and match coefficients. 4. Write $x=\text{CF}+\text{PI}$. 5. Apply the initial or boundary conditions to that $x$.
> - **Common mistakes:** a trial of $a\cos\omega t$ alone for $\cos\omega t$ forcing when a $\dot x$ term is present; applying the initial conditions to the CF before the PI has been added.
> - **Practise:** [[#Specimen Test 13, Q2]] · [[MATH1054 M13 Solutions - Differential Equations III#Exercise 63|Exercise 63]]

A linear ODE is one in which the unknown $x$ and its derivatives appear only to the first power, multiplied by functions of $t$ alone ([[MATH1054 M06 - Differential Equations I|Module 6]]). Stated through an operator, linearity has a structural consequence: solutions of the homogeneous equation can be added and scaled, so the general solution of an $n$th-order equation is a combination of $n$ independent pieces, and the forced equation needs only one solution of its own on top of that. Every method for linear ODEs here, and the Laplace-transform and eigenfunction methods in Year 2, rests on that split.

With constant coefficients both parts can be found systematically. Differentiating $e^{mt}$ only multiplies it by $m$, so the homogeneous ODE reduces to a polynomial in $m$. The forcing types that engineering problems produce (polynomials, exponentials, sines and cosines) reproduce themselves under differentiation, so a trial of the same shape with unknown coefficients always closes. The one complication is a clash, when the forcing is itself a solution of the homogeneous equation: the trial then needs an extra factor of $t$, and in an undamped oscillator that factor is resonance.

Physically, a mass on a spring with a dashpot, a pendulum with air resistance, a cantilevered lamp post in the wind and an LCR circuit all reduce to $\ddot x+2\zeta\omega\dot x+\omega^2x=f(t)$. The natural frequency $\omega$ sets the time scale, the damping parameter $\zeta$ decides whether the free response oscillates, and the forced response splits into a transient that dies away and a steady oscillation at the forcing frequency. The same two numbers reappear as the damping ratio and natural frequency of aircraft modes and control loops in SESA2027.

---

## 1. Operators and linear operators (James §10.8.1)

An **operator** maps a function to another function. Write $\mathrm D=\dfrac{\mathrm d}{\mathrm dt}$, so $\mathrm D^2=\dfrac{\mathrm d^2}{\mathrm dt^2}$ and so on. A **linear differential operator** of order $n$ is

$$
\mathrm L=a_n(t)\mathrm D^n+a_{n-1}(t)\mathrm D^{n-1}+\dots+a_1(t)\mathrm D+a_0(t),
$$

so that $\mathrm L[x]=a_n x^{(n)}+\dots+a_1\dot x+a_0x$, and the ODE $a_n x^{(n)}+\dots+a_0x=f(t)$ is written $\mathrm L[x]=f$. The equation is **homogeneous** when $f=0$ and **inhomogeneous** (or nonhomogeneous) otherwise.

### Examples of operators (Examples 10.23–10.26)

The operator $\phi[f]=f^2$ squares its argument. For $f=3t^2-2t+4$,

$$
\begin{aligned}
\phi[3t^2-2t+4]&=(3t^2-2t+4)^2\\
&=9t^4-12t^3+(4+24)t^2-16t+16\\
&=9t^4-12t^3+28t^2-16t+16 .
\end{aligned}
$$

The operator $\phi[f]=tf^2-4f+t^2$ gives $\phi[g^2]=tg^4-4g^2+t^2$ and $\phi[e^t]=te^{2t}-4e^t+t^2$. The operator $\phi=\mathrm D$ gives $\phi[4t^3-\tan t]=12t^2-\sec^2t$. With $\mathrm L=\mathrm D^2-(\sin t)\mathrm D+e^t$, the ODE $f''-(\sin t)f'+e^tf=t^4$ is $\mathrm L[f]=t^4$.

An operator is **linear** when, for all functions $x_1,x_2$ and constants $a,b$,

$$
\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2].
$$

Squaring fails this test: $\phi[2f]=4f^2$ but $2\phi[f]=2f^2$.

### Why every operator of this form is linear

Differentiation is linear, from the sum and constant-multiple rules:

$$
\mathrm D[ax_1+bx_2]=a\dot x_1+b\dot x_2=a\mathrm D[x_1]+b\mathrm D[x_2].
$$

Applying this $k$ times gives $\mathrm D^k[ax_1+bx_2]=a\mathrm D^kx_1+b\mathrm D^kx_2$. Multiplying by a function $a_k(t)$ and summing over $k$:

$$
\begin{aligned}
\mathrm L[ax_1+bx_2]&=\sum_{k=0}^{n}a_k(t)\,\mathrm D^k[ax_1+bx_2]\\
&=\sum_{k=0}^{n}a_k(t)\big(a\,\mathrm D^kx_1+b\,\mathrm D^kx_2\big)\\
&=a\sum_{k=0}^{n}a_k(t)\mathrm D^kx_1+b\sum_{k=0}^{n}a_k(t)\mathrm D^kx_2\\
&=a\mathrm L[x_1]+b\mathrm L[x_2].
\end{aligned}
$$

The coefficients may depend on $t$; they must not depend on $x$. This is the formal definition of a linear ODE: one whose operator is linear in this sense.

### Linearity of a differential operator (Example 10.27)

The equation $\ddot x+4t\dot x-(\sin t)x=\cos t$ has $\mathrm L=\mathrm D^2+4t\,\mathrm D-\sin t$. Directly,

$$
\begin{aligned}
\mathrm L[ax_1+bx_2]&=(ax_1+bx_2)''+4t(ax_1+bx_2)'-\sin t\,(ax_1+bx_2)\\
&=a\big(\ddot x_1+4t\dot x_1-\sin t\,x_1\big)+b\big(\ddot x_2+4t\dot x_2-\sin t\,x_2\big)\\
&=a\mathrm L[x_1]+b\mathrm L[x_2],
\end{aligned}
$$

so the equation is linear even though its coefficients vary with $t$. Exercise 46(a) asks for the operator of $\dot x+t^2x=0$, which is $\mathrm L=\mathrm D+t^2$. Exercise 49(c), $\ddot x+(\sin t)\dot x=(t+\cos t)x$, needs every $x$ term moved to the left first, giving $\mathrm L=\mathrm D^2+(\sin t)\mathrm D-(t+\cos t)$. Specimen Test 13 Q1, $\ddot x+3\dot x+4x=0$, has $\mathrm L=\mathrm D^2+3\mathrm D+4$.

## 2. Superposition and the structure of the general solution (James §10.8.2)

### The linearity principle

If $\mathrm L[x_1]=0$ and $\mathrm L[x_2]=0$, then

$$
\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2]=a\cdot0+b\cdot0=0,
$$

so every combination $ax_1+bx_2$ is also a solution. In Example 10.28, $\sin\lambda t$ and $\cos\lambda t$ both satisfy $\ddot x+\lambda^2x=0$, so $x=A\sin\lambda t+B\cos\lambda t$ does too, with the two constants a second-order equation needs. In Example 10.29, $\sin\lambda t$, $\cos\lambda t$, $\sinh\lambda t$ and $\cosh\lambda t$ all satisfy $x^{(4)}-\lambda^4x=0$, so

$$
x=A\sin\lambda t+B\cos\lambda t+C\sinh\lambda t+D\cosh\lambda t .
$$

### Linear independence (Examples 10.30 and 10.31)

Counting constants is not enough. The functions $e^t$, $e^{-t}$ and $\cosh t$ all satisfy $\dddot x-2\ddot x-\dot x+2x=0$ (Example 10.30), but

$$
\begin{aligned}
Ae^t+Be^{-t}+C\cosh t&=Ae^t+Be^{-t}+\tfrac12C(e^t+e^{-t})\\
&=\big(A+\tfrac12C\big)e^t+\big(B+\tfrac12C\big)e^{-t}\\
&=De^t+Ee^{-t},
\end{aligned}
$$

which has only two genuine constants. The third solution, $e^{2t}$, is missing.

Functions $f_1,\dots,f_p$ are **linearly dependent** if constants $k_1,\dots,k_p$, not all zero, exist with $k_1f_1+\dots+k_pf_p=0$ for every $t$, and **linearly independent** if not. Dependent functions are not genuinely different, since one is a combination of the others: $1$, $t$ and $2+3t$ are dependent because $2+3t=2(1)+3(t)$.

Example 10.31 tests four sets.

(a) $\{1+t,\ t,\ 1\}$ is dependent, because $(1+t)-t-1=0$ has coefficients $1,-1,-1$.

(b) $\{1+t,\ 1+t+t^2,\ 1+t^2\}$: set $a_1(1+t)+a_2(1+t+t^2)+a_3(1+t^2)=0$ and match the coefficients of $1$, $t$ and $t^2$:

$$
\begin{aligned}
a_1+a_2+a_3&=0,\\
a_1+a_2&=0,\\
a_2+a_3&=0 .
\end{aligned}
$$

The coefficient matrix has determinant

$$
\begin{vmatrix}1&1&1\\1&1&0\\0&1&1\end{vmatrix}=1(1-0)-1(1-0)+1(1-0)=1\neq0,
$$

so the only solution is $a_1=a_2=a_3=0$ and the set is independent.

(c) $\{\sin t,\ \cos t\}$: $a_1\cos t+a_2\sin t=0$ must hold for every $t$. At $t=0$ it gives $a_1=0$, and at $t=\pi/2$ it gives $a_2=0$, so the pair is independent.

(d) $\{e^t,\ e^{2t},\ e^{3t}\}$: evaluating $a_1e^t+a_2e^{2t}+a_3e^{3t}=0$ at $t=0,1,2$ gives a homogeneous system whose determinant is

$$
\begin{vmatrix}1&1&1\\e&e^2&e^3\\e^2&e^4&e^6\end{vmatrix}=e^8-2e^7+2e^5-e^4=e^4\big(e^4-2e^3+2e-1\big)\approx1029.9\neq0,
$$

so $a_1=a_2=a_3=0$ and the set is independent.

The general result for the homogeneous equation follows. If $x_1,\dots,x_p$ are linearly independent solutions of the $p$th-order equation $\mathrm L[x]=0$, the general solution is

$$
x=A_1x_1+A_2x_2+\dots+A_px_p .
$$

Repeated use of the linearity principle shows that this is a solution, it has $p$ arbitrary constants, and independence means none of them can be absorbed into the others. (A full proof that nothing else solves the equation needs the existence and uniqueness theorem for initial-value problems, which is beyond this module.)

### Why CF plus PI is the general solution

For the inhomogeneous equation $\mathrm L[x]=f$, let $x_p$ be any one solution, the **particular integral** (PI), and let $x_c=A_1x_1+\dots+A_px_p$ be the general solution of $\mathrm L[x]=0$, the **complementary function** (CF). Two facts together make $x_c+x_p$ the general solution.

First, $x_c+x_p$ is a solution for every choice of the constants:

$$
\begin{aligned}
\mathrm L[x_c+x_p]&=\mathrm L[x_c]+\mathrm L[x_p]\\
&=0+f\\
&=f .
\end{aligned}
$$

Second, every solution has this form. If $\mathrm L[x]=f$ for some $x$, then

$$
\begin{aligned}
\mathrm L[x-x_p]&=\mathrm L[x]-\mathrm L[x_p]\\
&=f-f\\
&=0,
\end{aligned}
$$

so $x-x_p$ solves the homogeneous equation and is therefore $A_1x_1+\dots+A_px_p$ for some constants. Hence $x=x_c+x_p$. Any particular integral will do: two different PIs differ by a solution of $\mathrm L[x]=0$, which the CF's constants absorb.

Example 10.32 shows the structure. For $\ddot x+\lambda^2x=4t^3$ the CF is $A\cos\lambda t+B\sin\lambda t$. A cubic forcing needs a full cubic trial $x_p=at^3+bt^2+ct+d$, with $\ddot x_p=6at+2b$:

$$
\begin{aligned}
6at+2b+\lambda^2(at^3+bt^2+ct+d)&=4t^3\\
\lambda^2a\,t^3+\lambda^2b\,t^2+(6a+\lambda^2c)\,t+(2b+\lambda^2d)&=4t^3 .
\end{aligned}
$$

Matching powers: $t^3$ gives $a=4/\lambda^2$; $t^2$ gives $b=0$; $t$ gives $c=-6a/\lambda^2=-24/\lambda^4$; the constant gives $d=0$. So

$$
x=A\cos\lambda t+B\sin\lambda t+\frac{4t^3}{\lambda^2}-\frac{24t}{\lambda^4}.
$$

### Splitting the forcing

If $\mathrm L[x_1]=f_1$ and $\mathrm L[x_2]=f_2$, then

$$
\mathrm L[x_1+x_2]=\mathrm L[x_1]+\mathrm L[x_2]=f_1+f_2 ,
$$

so a forcing that is a sum of terms of different types is handled one term at a time and the particular integrals are added ([[#Sums of forcing terms (Example 10.43, Exercise 63(h))]]).

## 3. The complementary function of any order (James §10.9.1)

From here on the coefficients are real constants: $\mathrm L=a_n\mathrm D^n+\dots+a_1\mathrm D+a_0$.

### The characteristic equation from the trial e to the mt

Differentiating an exponential multiplies it by $m$:

$$
\mathrm D[e^{mt}]=me^{mt},\qquad\mathrm D^2[e^{mt}]=m^2e^{mt},\qquad\dots,\qquad\mathrm D^k[e^{mt}]=m^ke^{mt}.
$$

Substituting $x=e^{mt}$ into $\mathrm L[x]$:

$$
\begin{aligned}
\mathrm L[e^{mt}]&=a_nm^ne^{mt}+\dots+a_1me^{mt}+a_0e^{mt}\\
&=\big(a_nm^n+\dots+a_1m+a_0\big)e^{mt}\\
&=P(m)\,e^{mt}.
\end{aligned}
$$

Since $e^{mt}\neq0$, the trial solves $\mathrm L[x]=0$ exactly when

$$
P(m)=a_nm^n+\dots+a_1m+a_0=0,
$$

the **auxiliary equation**, also called the characteristic equation. It is the ODE with $\mathrm D^k$ replaced by $m^k$, and it has $n$ roots counted with multiplicity. Distinct real roots $m_1,\dots,m_n$ give $n$ independent exponentials and $x=A_1e^{m_1t}+\dots+A_ne^{m_nt}$.

### Repeated roots

A double root gives only one exponential, so a second solution is needed. For a second-order equation with $P(m)=m^2+a_1m+a_0=(m-r)^2$, comparing coefficients gives $a_1=-2r$ and $a_0=r^2$, so $P(r)=0$ and $P'(r)=2r+a_1=0$. Try $x=v(t)e^{rt}$:

$$
\begin{aligned}
\dot x&=(\dot v+rv)e^{rt},\\
\ddot x&=(\ddot v+2r\dot v+r^2v)e^{rt}.
\end{aligned}
$$

Substituting into $\ddot x+a_1\dot x+a_0x$:

$$
\begin{aligned}
\ddot x+a_1\dot x+a_0x&=\big[\ddot v+2r\dot v+r^2v+a_1(\dot v+rv)+a_0v\big]e^{rt}\\
&=\big[\ddot v+(2r+a_1)\dot v+(r^2+a_1r+a_0)v\big]e^{rt}\\
&=\big[\ddot v+P'(r)\dot v+P(r)v\big]e^{rt}\\
&=\ddot v\,e^{rt}.
\end{aligned}
$$

So $x=ve^{rt}$ is a solution exactly when $\ddot v=0$, that is $v=A+Bt$, and the CF is $x=(A+Bt)e^{rt}$.

For any order the same result comes from differentiating with respect to $m$. Because $\mathrm L$ acts on $t$ and has constant coefficients, $\partial/\partial m$ passes through it:

$$
\begin{aligned}
\mathrm L[te^{mt}]&=\mathrm L\Big[\frac{\partial}{\partial m}e^{mt}\Big]\\
&=\frac{\partial}{\partial m}\mathrm L[e^{mt}]\\
&=\frac{\partial}{\partial m}\big[P(m)e^{mt}\big]\\
&=\big[P'(m)+tP(m)\big]e^{mt}.
\end{aligned}
$$

Differentiating $j$ times and using Leibniz's rule,

$$
\mathrm L[t^je^{mt}]=\frac{\partial^j}{\partial m^j}\big[P(m)e^{mt}\big]=\sum_{i=0}^{j}\binom{j}{i}P^{(i)}(m)\,t^{j-i}e^{mt}.
$$

A root $r$ of multiplicity $k$ means $P(m)=(m-r)^kQ(m)$, so $P(r)=P'(r)=\dots=P^{(k-1)}(r)=0$. For $j\le k-1$ every term of the sum vanishes at $m=r$, so $e^{rt},te^{rt},\dots,t^{k-1}e^{rt}$ are $k$ independent solutions and the root contributes $(A_0+A_1t+\dots+A_{k-1}t^{k-1})e^{rt}$. The same identity gives the clash rule in [[#5. The clash case: forcing that is already in the CF]].

### Complex roots and Euler's formula

Real coefficients make complex roots come in conjugate pairs $\alpha\pm\mathrm j\beta$, because $\overline{P(m)}=P(\bar m)$. By [[Euler's Formula]], $e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta$, so

$$
e^{(\alpha\pm\mathrm j\beta)t}=e^{\alpha t}e^{\pm\mathrm j\beta t}=e^{\alpha t}(\cos\beta t\pm\mathrm j\sin\beta t).
$$

Combining the pair with constants $C_1,C_2$:

$$
\begin{aligned}
C_1e^{(\alpha+\mathrm j\beta)t}+C_2e^{(\alpha-\mathrm j\beta)t}&=e^{\alpha t}\big[C_1(\cos\beta t+\mathrm j\sin\beta t)+C_2(\cos\beta t-\mathrm j\sin\beta t)\big]\\
&=e^{\alpha t}\big[(C_1+C_2)\cos\beta t+\mathrm j(C_1-C_2)\sin\beta t\big]\\
&=e^{\alpha t}\big(A\cos\beta t+B\sin\beta t\big),
\end{aligned}
$$

with $A=C_1+C_2$ and $B=\mathrm j(C_1-C_2)$. Choosing $C_2=\bar C_1$ makes $A$ and $B$ real, which is what a physical solution needs. Writing $A=R\cos\varphi$ and $B=R\sin\varphi$ gives the amplitude–phase form

$$
e^{\alpha t}(A\cos\beta t+B\sin\beta t)=Re^{\alpha t}\cos(\beta t-\varphi),\qquad R=\sqrt{A^2+B^2},\quad\tan\varphi=\frac BA ,
$$

an oscillation of angular frequency $\beta$ inside the envelope $\pm Re^{\alpha t}$, decaying when $\alpha<0$ and growing when $\alpha>0$.

### Summary table and examples (Examples 10.29, 10.30, 10.34–10.36)

| Root of $P(m)$ | Contribution to the CF |
|---|---|
| real $m$, simple | $Ae^{mt}$ |
| real $m$, multiplicity $k$ | $(A_0+A_1t+\dots+A_{k-1}t^{k-1})e^{mt}$ |
| pair $\alpha\pm\mathrm j\beta$ | $e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ |
| pair $\alpha\pm\mathrm j\beta$, multiplicity $k$ | $e^{\alpha t}\big[(A_0+\dots+A_{k-1}t^{k-1})\cos\beta t+(B_0+\dots+B_{k-1}t^{k-1})\sin\beta t\big]$ |

Example 10.29, $x^{(4)}-\lambda^4x=0$, factorises as a difference of two squares:

$$
\begin{aligned}
m^4-\lambda^4&=(m^2-\lambda^2)(m^2+\lambda^2)=0\\
m&=\pm\lambda,\ \pm\mathrm j\lambda,
\end{aligned}
$$

so

$$
x=Ae^{\lambda t}+Be^{-\lambda t}+C\cos\lambda t+D\sin\lambda t ,
$$

or equivalently $A'\cosh\lambda t+B'\sinh\lambda t+C\cos\lambda t+D\sin\lambda t$, which matches Section 2. This is the equation for the transverse vibration of a beam.

Example 10.30, $\dddot x-2\ddot x-\dot x+2x=0$, factorises by grouping:

$$
\begin{aligned}
m^3-2m^2-m+2&=m^2(m-2)-(m-2)\\
&=(m-2)(m^2-1)\\
&=(m-2)(m-1)(m+1),
\end{aligned}
$$

so $x=Ae^{2t}+Be^{t}+Ce^{-t}$, which supplies the missing $e^{2t}$.

Examples 10.34–10.36 repeat the three second-order cases from Module 06:

| Example | Equation | Roots | Solution |
|---|---|---|---|
| 10.34 | $\ddot x-9\dot x+6x=0$ | $\frac{9\pm\sqrt{57}}{2}\approx8.275,\ 0.725$ | $Ae^{\frac{9+\sqrt{57}}2t}+Be^{\frac{9-\sqrt{57}}2t}$ |
| 10.35 | $2\ddot x-3\dot x+5x=0$ | $\frac34\pm\mathrm j\frac{\sqrt{31}}4$ | $e^{3t/4}\big(A\cos\frac{\sqrt{31}}4t+B\sin\frac{\sqrt{31}}4t\big)$ |
| 10.36 | $\ddot x+6\dot x+9x=0$, $x(0)=1$, $\dot x(0)=2$ | $-3$ (double) | $(1+5t)e^{-3t}$ |

## 4. Particular integrals by undetermined coefficients (James §10.9.3)

### Why the trial functions work

Differentiating a polynomial of degree $n$ gives polynomials of lower degree; differentiating $e^{kt}$ gives multiples of $e^{kt}$; differentiating $\cos\omega t$ or $\sin\omega t$ gives multiples of $\sin\omega t$ and $\cos\omega t$. So with constant coefficients, $\mathrm L$ maps each family into itself, and a trial from the same family as $f$ with unknown coefficients turns $\mathrm L[x_p]=f$ into linear equations for those coefficients. This is the **method of undetermined coefficients**. Work out the CF first, because the trial depends on it ([[#5. The clash case: forcing that is already in the CF]]).

| Forcing $f(t)$ | Trial $x_p$ | Unknowns |
|---|---|---|
| polynomial of degree $n$, e.g. $6t^3+4t^2-2t+5$ | full polynomial of degree $n$, e.g. $at^3+bt^2+ct+d$ | every coefficient |
| $e^{kt}$, e.g. $e^{-3t}$ | $Ce^{kt}$ | $C$ ($=1/P(k)$) |
| $\cos\omega t$ or $\sin\omega t$, e.g. $\sin5t$ | $a\cos\omega t+b\sin\omega t$ | $a,b$ |
| a sum of the above | the sum of the trials | all of them |
| any of the above, already in the CF | the trial times $t^s$ ($s$ = multiplicity of the root) | as before |

Examples 10.40–10.43 all have the operator $\mathrm L=\mathrm D^2+5\mathrm D-9$, with

$$
m^2+5m-9=0\quad\Rightarrow\quad m_{1,2}=\frac{-5\pm\sqrt{61}}{2}\approx1.405,\ -6.405,
$$

so the CF is $x_c=Ae^{m_1t}+Be^{m_2t}$, and none of the forcing terms below appears in it.

### Polynomial forcing (Example 10.40, Exercise 62(b))

For $\ddot x+5\dot x-9x=t^2$, try $x_p=at^2+bt+c$, with $\dot x_p=2at+b$ and $\ddot x_p=2a$:

$$
\begin{aligned}
2a+5(2at+b)-9(at^2+bt+c)&=t^2\\
-9a\,t^2+(10a-9b)\,t+(2a+5b-9c)&=t^2 .
\end{aligned}
$$

Matching $t^2$: $-9a=1$, so $a=-\tfrac19$. Matching $t$: $10a-9b=0$, so $b=\tfrac{10a}{9}=-\tfrac{10}{81}$. Matching the constant: $9c=2a+5b=-\tfrac{18}{81}-\tfrac{50}{81}=-\tfrac{68}{81}$, so $c=-\tfrac{68}{729}$. Hence

$$
x=Ae^{m_1t}+Be^{m_2t}-\tfrac19t^2-\tfrac{10}{81}t-\tfrac{68}{729}.
$$

The trial must contain every lower power, even though $f=t^2$ has no $t$ or constant term, because $\dot x_p$ and $\ddot x_p$ generate them.

Exercise 62(b), $\ddot x-2\dot x-5x=t^2-2t$, has $m^2-2m-5=0$, so $m=1\pm\sqrt6$. With $x_p=at^2+bt+c$:

$$
\begin{aligned}
2a-2(2at+b)-5(at^2+bt+c)&=t^2-2t\\
-5a\,t^2+(-4a-5b)\,t+(2a-2b-5c)&=t^2-2t .
\end{aligned}
$$

So $a=-\tfrac15$; then $-4a-5b=-2$ gives $5b=\tfrac45+2=\tfrac{14}5$ and $b=\tfrac{14}{25}$; then $5c=2a-2b=-\tfrac{10}{25}-\tfrac{28}{25}$ gives $c=-\tfrac{38}{125}$:

$$
x=Ae^{(1+\sqrt6)t}+Be^{(1-\sqrt6)t}-\tfrac15t^2+\tfrac{14}{25}t-\tfrac{38}{125}.
$$

> [!warning] No $x$ term in the equation
> If $a_0=0$, so that $P(0)=0$, a constant forcing clashes with the CF constant and the polynomial trial must be raised by one degree. For $\ddot x+3\dot x=6$ a constant trial gives $0=6$; the trial $x_p=at$ gives $3a=6$, so $x_p=2t$. This is the clash rule of Section 5 with $k=0$.

### Exponential forcing (Example 10.42, Exercise 63(b))

For $f=e^{kt}$, try $x_p=Ce^{kt}$. From Section 3, $\mathrm L[Ce^{kt}]=CP(k)e^{kt}$, so

$$
CP(k)e^{kt}=e^{kt}\quad\Rightarrow\quad C=\frac1{P(k)}\qquad(P(k)\neq0).
$$

Example 10.42, $\ddot x+5\dot x-9x=e^{4t}$: $P(4)=16+20-9=27$, so $x_p=\tfrac1{27}e^{4t}$.

Exercise 63(b), $9\ddot x-12\dot x+4x=e^{-3t}$: the auxiliary equation is $9m^2-12m+4=(3m-2)^2=0$, a double root $m=\tfrac23$, so $x_c=(A+Bt)e^{2t/3}$. Then $P(-3)=81+36+4=121$, and

$$
x=(A+Bt)e^{2t/3}+\tfrac1{121}e^{-3t}.
$$

### Sine and cosine forcing (Example 10.41, Exercise 63(a))

For $\ddot x+5\dot x-9x=\cos2t$, a trial $a\cos2t$ alone fails, because $5\dot x$ produces a $\sin2t$ term that nothing can cancel. Try $x_p=a\cos2t+b\sin2t$, for which $\ddot x_p=-4x_p$ and $\dot x_p=-2a\sin2t+2b\cos2t$:

$$
\begin{aligned}
\ddot x_p+5\dot x_p-9x_p&=-13x_p+5\dot x_p\\
&=-13a\cos2t-13b\sin2t-10a\sin2t+10b\cos2t\\
&=(-13a+10b)\cos2t+(-10a-13b)\sin2t .
\end{aligned}
$$

Matching with $\cos2t$: $-13a+10b=1$ and $-10a-13b=0$. The second gives $b=-\tfrac{10}{13}a$; substituting, $-13a-\tfrac{100}{13}a=1$, so $-\tfrac{269}{13}a=1$, $a=-\tfrac{13}{269}$ and $b=\tfrac{10}{269}$:

$$
x_p=\tfrac1{269}(10\sin2t-13\cos2t).
$$

> [!tip] The complex-exponential shortcut
> Since $\cos\Omega t=\operatorname{Re}e^{\mathrm j\Omega t}$ and the coefficients are real, $x_p=\operatorname{Re}\big[e^{\mathrm j\Omega t}/P(\mathrm j\Omega)\big]$. For Example 10.41, $P(2\mathrm j)=-4+10\mathrm j-9=-13+10\mathrm j$, so $1/P(2\mathrm j)=(-13-10\mathrm j)/269$, and $\operatorname{Re}\big[(-13-10\mathrm j)(\cos2t+\mathrm j\sin2t)\big]/269=(-13\cos2t+10\sin2t)/269$, the same answer.

Exercise 63(a), $\ddot x-3\dot x+4x=\cos4t-2\sin4t$, has $m^2-3m+4=0$, so $m=\tfrac32\pm\mathrm j\tfrac{\sqrt7}2$ and $x_c=e^{3t/2}\big(A\cos\tfrac{\sqrt7}2t+B\sin\tfrac{\sqrt7}2t\big)$. With $x_p=a\cos4t+b\sin4t$ and $\ddot x_p=-16x_p$:

$$
\begin{aligned}
\ddot x_p-3\dot x_p+4x_p&=-12x_p-3\dot x_p\\
&=-12a\cos4t-12b\sin4t+12a\sin4t-12b\cos4t\\
&=(-12a-12b)\cos4t+(12a-12b)\sin4t .
\end{aligned}
$$

Matching: $-12a-12b=1$ and $12a-12b=-2$. Adding gives $-24b=-1$, so $b=\tfrac1{24}$; subtracting gives $-24a=3$, so $a=-\tfrac18$:

$$
x=e^{3t/2}\Big(A\cos\tfrac{\sqrt7}2t+B\sin\tfrac{\sqrt7}2t\Big)-\tfrac18\cos4t+\tfrac1{24}\sin4t .
$$

### Sums of forcing terms (Example 10.43, Exercise 63(h))

For $\ddot x+5\dot x-9x=e^{-2t}+2-t$, split the forcing. The exponential piece has $P(-2)=4-10-9=-15$, so its PI is $-\tfrac1{15}e^{-2t}$. The linear piece takes $x_p=at+b$:

$$
\begin{aligned}
5a-9(at+b)&=2-t\\
-9a\,t+(5a-9b)&=2-t,
\end{aligned}
$$

so $a=\tfrac19$, then $9b=5a-2=\tfrac59-2=-\tfrac{13}9$ and $b=-\tfrac{13}{81}$. Adding the two:

$$
x=Ae^{m_1t}+Be^{m_2t}-\tfrac1{15}e^{-2t}+\tfrac19t-\tfrac{13}{81}.
$$

In the same way, $f=t+\sin t$ takes the trial $At+B+C\sin t+D\cos t$.

Exercise 63(h), $3\ddot x+3\dot x-x=t^2+e^{-2t}$, has $3m^2+3m-1=0$, so $m=\dfrac{-3\pm\sqrt{21}}6$. For the $t^2$ piece, $x_p=at^2+bt+c$:

$$
\begin{aligned}
6a+3(2at+b)-(at^2+bt+c)&=t^2\\
-a\,t^2+(6a-b)\,t+(6a+3b-c)&=t^2,
\end{aligned}
$$

so $a=-1$, $b=6a=-6$ and $c=6a+3b=-24$. For the exponential, $P(-2)=12-6-1=5$, giving $\tfrac15e^{-2t}$. Hence

$$
x=Ae^{\frac{-3+\sqrt{21}}6t}+Be^{\frac{-3-\sqrt{21}}6t}-t^2-6t-24+\tfrac15e^{-2t}.
$$

## 5. The clash case: forcing that is already in the CF

### Simple root: multiply by t (Example 10.44)

For $\ddot x+\dot x-2x=e^{-2t}$, the auxiliary equation is $m^2+m-2=(m+2)(m-1)=0$, so $x_c=Ae^t+Be^{-2t}$. The usual trial $Ce^{-2t}$ is in the CF, so $\mathrm L[Ce^{-2t}]=CP(-2)e^{-2t}=0$ and no $C$ can produce $e^{-2t}$: substituting gives $4C-2C-2C=0\neq1$.

The fix comes from the identity in Section 3. If $P(k)=0$ but $P'(k)\neq0$ (a simple root),

$$
\begin{aligned}
\mathrm L[te^{kt}]&=\big[P'(k)+tP(k)\big]e^{kt}\\
&=P'(k)e^{kt},
\end{aligned}
$$

so the trial $x_p=Cte^{kt}$ works with

$$
C=\frac1{P'(k)} .
$$

Here $P'(m)=2m+1$ and $P'(-2)=-3$, so $C=-\tfrac13$. Checking by direct substitution, with $x_p=Cte^{-2t}$:

$$
\begin{aligned}
\dot x_p&=C(1-2t)e^{-2t},\\
\ddot x_p&=C(4t-4)e^{-2t},\\
\ddot x_p+\dot x_p-2x_p&=C\big[(4t-4)+(1-2t)-2t\big]e^{-2t}=-3Ce^{-2t},
\end{aligned}
$$

so $-3C=1$ and $C=-\tfrac13$. The general solution is

$$
x=Ae^t+Be^{-2t}-\tfrac13te^{-2t}.
$$

Specimen Test 13 Q2(ii)(b) is the same situation: $\ddot x+5\dot x+6x=e^{-2t}$ with $P(m)=(m+2)(m+3)$, $P'(m)=2m+5$ and $P'(-2)=1$, so $x_p=te^{-2t}$.

### Repeated root: multiply by t to the multiplicity (Example 10.45)

If $k$ is a root of multiplicity $s$, then $P(k)=\dots=P^{(s-1)}(k)=0$ and the Leibniz sum of Section 3 leaves one term:

$$
\mathrm L[t^se^{kt}]=P^{(s)}(k)e^{kt},\qquad x_p=\frac{t^se^{kt}}{P^{(s)}(k)} .
$$

For a double root this reads $\mathrm L[t^2e^{kt}]=\big[P''(k)+2tP'(k)+t^2P(k)\big]e^{kt}=P''(k)e^{kt}$.

Example 10.45 is $x^{(4)}-2\dddot x+5\ddot x-8\dot x+4x=e^t$, with $P(m)=m^4-2m^3+5m^2-8m+4$. Testing $m=1$:

$$
\begin{aligned}
P(1)&=1-2+5-8+4=0,\\
P'(1)&=4-6+10-8=0,\\
P''(1)&=12-12+10=10,
\end{aligned}
$$

so $m=1$ is a double root. Dividing by $(m-1)^2=m^2-2m+1$ leaves $m^2+4$, and expanding back, $(m^2-2m+1)(m^2+4)=m^4-2m^3+5m^2-8m+4$. So

$$
P(m)=(m-1)^2(m^2+4),\qquad x_c=(A+Bt)e^t+C\cos2t+D\sin2t .
$$

The trial $Ke^t$ gives $0$, and $Kte^t$ also gives $0$ because $te^t$ is in the CF too; the trial must be $Kt^2e^t$, with $K=1/P''(1)=\tfrac1{10}$. Directly, the derivatives of $t^2e^t$ are $(t^2+2t)e^t$, $(t^2+4t+2)e^t$, $(t^2+6t+6)e^t$ and $(t^2+8t+12)e^t$, and in $\mathrm L[t^2e^t]$ the $t^2$ coefficients sum to $1-2+5-8+4=0$, the $t$ coefficients to $8-12+20-16=0$ and the constants to $12-12+10=10$. Hence

$$
x=(A+Bt)e^t+C\cos2t+D\sin2t+\tfrac1{10}t^2e^t .
$$

### Undamped resonance (Exercise 63(j))

For $\ddot x+16x=1+2\sin4t$ the CF is $A\cos4t+B\sin4t$, natural frequency $4$. The constant piece gives $x_p=\tfrac1{16}$. The $2\sin4t$ piece is forcing at the natural frequency, so $a\cos4t+b\sin4t$ is in the CF and the trial is $x_p=tu$ with $u=a\cos4t+b\sin4t$ and $\ddot u=-16u$:

$$
\begin{aligned}
\ddot x_p&=2\dot u+t\ddot u=2\dot u-16tu,\\
\ddot x_p+16x_p&=2\dot u\\
&=2(-4a\sin4t+4b\cos4t)\\
&=8b\cos4t-8a\sin4t .
\end{aligned}
$$

Matching with $2\sin4t$: $b=0$ and $-8a=2$, so $a=-\tfrac14$. Hence

$$
x=A\cos4t+B\sin4t+\tfrac1{16}-\tfrac14t\cos4t .
$$

The same answer comes from the exponential rule with the imaginary root $k=4\mathrm j$: $2\sin4t=\operatorname{Im}(2e^{4\mathrm jt})$ and $P'(4\mathrm j)=8\mathrm j$, so $x_p=\operatorname{Im}\big[2te^{4\mathrm jt}/(8\mathrm j)\big]=\operatorname{Im}\big[-\tfrac{\mathrm j}4t(\cos4t+\mathrm j\sin4t)\big]=-\tfrac14t\cos4t$.

The amplitude of $-\tfrac14t\cos4t$ grows linearly without bound. This is [[Resonance]]: an undamped system forced at its natural frequency. Any damping removes the clash, because the roots move off the imaginary axis, and the amplitude then stays finite ([[#Amplitude, phase and the resonance peak]]).

## 6. Initial and boundary conditions

The constants are fixed by conditions applied to the general solution $x=x_c+x_p$, never to $x_c$ alone, because $x_p$ also contributes to $x(0)$ and $\dot x(0)$. An $n$th-order equation needs $n$ conditions.

### An initial-value problem (Exercise 21(a))

Solve $\ddot x+2\dot x+5x=1$ with $x(0)=\dot x(0)=0$. The auxiliary equation $m^2+2m+5=0$ gives $m=-1\pm2\mathrm j$, and a constant forcing gives $x_p=\tfrac15$. So

$$
x=\tfrac15+e^{-t}(A\cos2t+B\sin2t),
$$

and differentiating,

$$
\dot x=e^{-t}\big[(-A+2B)\cos2t+(-B-2A)\sin2t\big].
$$

The condition $x(0)=0$ gives $\tfrac15+A=0$, so $A=-\tfrac15$. The condition $\dot x(0)=0$ gives $-A+2B=0$, so $B=\tfrac12A=-\tfrac1{10}$. Hence

$$
x=\tfrac15-e^{-t}\Big(\tfrac15\cos2t+\tfrac1{10}\sin2t\Big).
$$

This is an under-damped step response. Substituting the constants into $\dot x$ gives $\dot x=\tfrac12e^{-t}\sin2t$, which first vanishes at $t=\pi/2$, where $x=\tfrac15\big(1+e^{-\pi/2}\big)=0.2416$: an overshoot of $e^{-\pi/2}=20.8\%$ above the steady state $\tfrac15$.

![[m1054_step_response_21a.png|600]]

### Specimen Test 13, Q2

The equation is $\ddot x+5\dot x+6x=f(t)$.

(i) $m^2+5m+6=(m+2)(m+3)=0$ gives $m=-2,-3$, so $x_c=Ae^{-3t}+Be^{-2t}$.

(ii)(a) For $f=\cos t$, try $a\cos t+b\sin t$; with $\ddot x_p=-x_p$,

$$
\begin{aligned}
\ddot x_p+5\dot x_p+6x_p&=5x_p+5\dot x_p\\
&=5a\cos t+5b\sin t-5a\sin t+5b\cos t\\
&=5(a+b)\cos t+5(b-a)\sin t,
\end{aligned}
$$

so $a+b=\tfrac15$ and $b-a=0$, giving $a=b=\tfrac1{10}$ and $x_p=\tfrac1{10}(\cos t+\sin t)$.

(ii)(b) For $f=e^{-2t}$, a simple root of $P$, $x_p=te^{-2t}/P'(-2)=te^{-2t}$ (see [[#Simple root: multiply by t (Example 10.44)]]).

(ii)(c) For $f=1-6t$, try $at+b$: $5a+6(at+b)=1-6t$, so $6a=-6$, $a=-1$, and $5a+6b=1$ gives $b=1$. So $x_p=1-t$.

(iii) With $f=e^{-2t}$,

$$
\begin{aligned}
x&=Ae^{-3t}+Be^{-2t}+te^{-2t},\\
\dot x&=-3Ae^{-3t}-2Be^{-2t}+(1-2t)e^{-2t}.
\end{aligned}
$$

The conditions $x(0)=\tfrac14$ and $\dot x(0)=0$ give

$$
\begin{aligned}
A+B&=\tfrac14,\\
-3A-2B+1&=0 .
\end{aligned}
$$

Substituting $B=\tfrac14-A$ into the second: $-3A-\tfrac12+2A+1=0$, so $A=\tfrac12$ and $B=-\tfrac14$:

$$
x=\tfrac12e^{-3t}-\tfrac14e^{-2t}+te^{-2t}.
$$

### A boundary-value problem (Example 10.33)

A **boundary-value problem** (BVP) fixes $x$ at two different values of $t$ instead of $x$ and $\dot x$ at one. Solve $\ddot x-k^2x=\sin2t$ ($k>0$) with $x(0)=0$ and $x(\pi/4)=0$. The CF is $A\cosh kt+B\sinh kt$ (equivalently $Ae^{kt}+Be^{-kt}$). Trying $x_p=C\sin2t$:

$$
\begin{aligned}
-4C\sin2t-k^2C\sin2t&=\sin2t\\
C&=-\frac1{k^2+4}.
\end{aligned}
$$

The condition $x(0)=0$ gives $A=0$. The condition $x(\pi/4)=0$, with $\sin\frac\pi2=1$, gives

$$
\begin{aligned}
B\sinh\frac{k\pi}4-\frac1{k^2+4}&=0\\
B&=\frac1{(k^2+4)\sinh(k\pi/4)} .
\end{aligned}
$$

So

$$
x=\frac1{k^2+4}\left[\frac{\sinh kt}{\sinh(k\pi/4)}-\sin2t\right].
$$

The solution is unique because $\sinh(k\pi/4)\neq0$ for $k>0$. A BVP need not have a unique solution. For $\ddot x+x=0$ with $x(0)=0$ and $x(\pi)=0$, the solution $A\cos t+B\sin t$ needs $A=0$, and then $B\sin\pi=0$ holds for every $B$, so there are infinitely many solutions; with $x(\pi)=1$ instead there are none. That behaviour is the starting point of the eigenvalue problems in [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]].

## 7. Free oscillations of damped systems (James §10.10.1–10.10.2)

### Standard form, natural frequency and damping parameter

A body of mass $M$ displaced by $x$ from equilibrium, with a restoring force $\lambda x$ and a resistance $\mu\dot x$ proportional to speed, obeys

$$
\begin{aligned}
M\ddot x&=-\mu\dot x-\lambda x\\
\ddot x+p\dot x+qx&=0,\qquad p=\frac{\mu}{M}>0,\quad q=\frac{\lambda}{M}>0 .
\end{aligned}
$$

A cantilever, a pendulum (small angles), a floating buoy and a suspension all give this form. The **standard form** writes $p=2\zeta\omega$ and $q=\omega^2$:

$$
\ddot x+2\zeta\omega\dot x+\omega^2x=0,\qquad\omega=\sqrt q,\quad\zeta=\frac{p}{2\sqrt q},
$$

where $\omega>0$ is the **natural frequency** (the angular frequency of the motion with no damping) and $\zeta>0$ is the **damping parameter** (the damping ratio in SESA2027 and FEEG1002). To read them off any equation, first divide by the coefficient of $\ddot x$; then $\omega^2$ is the coefficient of $x$ and $2\zeta\omega$ the coefficient of $\dot x$.

### The three damping regimes

The auxiliary equation is $m^2+2\zeta\omega m+\omega^2=0$, so

$$
\begin{aligned}
m&=\frac{-2\zeta\omega\pm\sqrt{4\zeta^2\omega^2-4\omega^2}}{2}\\
&=-\zeta\omega\pm\omega\sqrt{\zeta^2-1}.
\end{aligned}
$$

The sign of $\zeta^2-1$ decides the form of the solution.

When $\zeta>1$ the system is **over-damped**: there are two distinct real roots, both negative because $\sqrt{\zeta^2-1}<\zeta$, so

$$
x=Ae^{-(\zeta-\sqrt{\zeta^2-1})\omega t}+Be^{-(\zeta+\sqrt{\zeta^2-1})\omega t},
$$

a sum of two decaying exponentials with no oscillation.

When $\zeta=1$ the system is **critically damped**: the root $m=-\omega$ is double, so

$$
x=(A+Bt)e^{-\omega t}.
$$

When $0<\zeta<1$ the system is **under-damped**: $\sqrt{\zeta^2-1}=\mathrm j\sqrt{1-\zeta^2}$, so $m=-\zeta\omega\pm\mathrm j\omega_d$ with the **damped frequency** $\omega_d=\omega\sqrt{1-\zeta^2}$, and

$$
x=e^{-\zeta\omega t}\big(A\cos\omega_dt+B\sin\omega_dt\big),
$$

an oscillation at $\omega_d<\omega$ inside the decaying envelope $e^{-\zeta\omega t}$.

With $\zeta=0$ the roots are $\pm\mathrm j\omega$ and $x=A\cos\omega t+B\sin\omega t$, undamped simple harmonic motion. For every $\zeta>0$, $x\to0$ as $t\to\infty$, and changing $\omega$ only rescales the time axis.

![[m1054_damping_regimes.png|900]]

### Why critical damping decays fastest

After the faster term has died, the response decays at the rate $\sigma$ set by the root nearest zero. For $0<\zeta\le1$ both roots have real part $-\zeta\omega$, so $\sigma=\zeta\omega$, which rises with $\zeta$ to $\omega$ at $\zeta=1$. For $\zeta>1$ the slower root gives

$$
\begin{aligned}
\sigma&=\omega\big(\zeta-\sqrt{\zeta^2-1}\big)\\
&=\omega\frac{\big(\zeta-\sqrt{\zeta^2-1}\big)\big(\zeta+\sqrt{\zeta^2-1}\big)}{\zeta+\sqrt{\zeta^2-1}}\\
&=\frac{\omega}{\zeta+\sqrt{\zeta^2-1}},
\end{aligned}
$$

which is less than $\omega$ and falls towards zero as $\zeta$ grows. So $\sigma$ is largest, equal to $\omega$, at $\zeta=1$: critical damping returns to equilibrium fastest without oscillating, and heavier damping makes the return slower, not faster.

### Overshoots and decay time

The response is contained in the envelope $e^{-\zeta\omega t}$. Since $e^{-3}=0.0498$ and $e^{-4.5}=0.0111$, the amplitude falls to about 5% after $\zeta\omega t=3$ and to about 1% after $\zeta\omega t=4.5$. The **decay time** is therefore

$$
T=\frac1{\zeta\omega},
$$

and the response falls to 5% in $3T$ and 1% in $4.5T$.

The number of overshoots that can be seen follows from the step response. For $\ddot x+2\zeta\omega\dot x+\omega^2x=\omega^2$ from rest, the solution is $x=1-e^{-\zeta\omega t}\big(\cos\omega_dt+\tfrac{\zeta\omega}{\omega_d}\sin\omega_dt\big)$, and differentiating,

$$
\begin{aligned}
\dot x&=\zeta\omega e^{-\zeta\omega t}\Big(\cos\omega_dt+\tfrac{\zeta\omega}{\omega_d}\sin\omega_dt\Big)-e^{-\zeta\omega t}\big(-\omega_d\sin\omega_dt+\zeta\omega\cos\omega_dt\big)\\
&=e^{-\zeta\omega t}\Big(\frac{\zeta^2\omega^2}{\omega_d}+\omega_d\Big)\sin\omega_dt\\
&=\frac{\omega^2}{\omega_d}e^{-\zeta\omega t}\sin\omega_dt .
\end{aligned}
$$

The extremes are at $\omega_dt_n=n\pi$, where $\cos n\pi=(-1)^n$ and $\sin n\pi=0$, so

$$
x(t_n)-1=(-1)^{n+1}e^{-\zeta\omega t_n}=(-1)^{n+1}\exp\Big(-\frac{n\pi\zeta}{\sqrt{1-\zeta^2}}\Big).
$$

| $\zeta$ | 1st | 2nd | 3rd | 4th | Discernible overshoots |
|---|---|---|---|---|---|
| 0.3 | 37.2% | 13.9% | 5.2% | 1.9% | 3 (the 4th and later are below 2%) |
| 0.5 | 16.3% | 2.7% | 0.43% | 0.07% | 2 (the 3rd and later are below 0.5%) |
| 0.7 | 4.6% | 0.21% | | | 1 |

For Exercise 21(a), $\zeta=1/\sqrt5$ gives $\zeta/\sqrt{1-\zeta^2}=\tfrac12$ and a first overshoot of $e^{-\pi/2}=20.8\%$, as found in Section 6.

### Reading off the natural frequency and damping parameter (Exercises 66(b), 68(d), Specimen Test 13 Q3)

Exercise 66(b), $\ddot x+4\dot x+7x=0$: $\omega^2=7$, so $\omega=\sqrt7\approx2.646$; $2\zeta\omega=4$, so $\zeta=2/\sqrt7\approx0.756$. Since $\zeta<1$ the system is under-damped.

Exercise 68(d), $\frac1\eta\ddot x+40\dot x+25\eta x=0$ with $\eta>0$: multiplying by $\eta$ gives the standard form

$$
\ddot x+40\eta\dot x+25\eta^2x=0,
$$

so $\omega^2=25\eta^2$, $\omega=5\eta$, and $2\zeta\omega=40\eta$ gives $\zeta=\dfrac{40\eta}{10\eta}=4$. The system is over-damped for every $\eta>0$.

Specimen Test 13 Q3, $\ddot x+6\alpha\dot x+16x=0$ with $\alpha>0$: $\omega^2=16$, so $\omega=4$, and $2\zeta\omega=6\alpha$, so $\zeta=\tfrac{6\alpha}{8}=\tfrac{3\alpha}4$. The system is under-damped when $\tfrac{3\alpha}4<1$, that is $0<\alpha<\tfrac43$, and critically damped when $\alpha=\tfrac43$. For part (iii), the complementary function, which decays for $\zeta>0$, is the transient, and the particular integral is the steady state. This equation is unforced, so it has no PI: the whole solution is transient and the steady state is $x=0$.

### The damped pendulum (Example 10.46)

A pendulum of mass $M=4\ \mathrm{kg}$ and length $l=2\ \mathrm m$, with air resistance $R=kl\dot\theta$ where $k=5\ \mathrm{N\,s\,m^{-1}}$, is released from $20^\circ$. Resolving perpendicular to the arm, $Ml\ddot\theta=-kl\dot\theta-Mg\sin\theta$, and for small angles ($\sin\theta\approx\theta$, $\theta$ in radians)

$$
\ddot\theta+\frac kM\dot\theta+\frac gl\theta=0 .
$$

Comparing with the standard form:

$$
\begin{aligned}
\omega&=\sqrt{g/l}=\sqrt{9.81/2}=2.215\ \mathrm{rad\,s^{-1}},\\
2\zeta\omega&=k/M=1.25\quad\Rightarrow\quad\zeta=\frac{1.25}{2(2.215)}=0.282 .
\end{aligned}
$$

With $\zeta\approx0.3$, three overshoots are visible, about one and a half cycles. The decay time is $T=1/(\zeta\omega)=2M/k=1.6\ \mathrm s$. Falling below $1^\circ$ from $20^\circ$ means falling to 5% of the initial amplitude, which takes $3T=4.8\ \mathrm s$.

## 8. Forced oscillations: transient and steady state (James §10.10.3–10.10.4)

### The steady-state solution

A cantilevered lamp post of tip mass $M$, stiffness $\lambda$ and damping $\mu$, driven by an oscillating side-force $W_0\cos\Omega t$ from vortex shedding, obeys $M\ddot x+\mu\dot x+\lambda x=W_0\cos\Omega t$. Dividing by $M$:

$$
\ddot x+2\zeta\omega\dot x+\omega^2x=F\cos\Omega t,\qquad F=W_0/M .
$$

Try $x_p=a\cos\Omega t+b\sin\Omega t$, with $\dot x_p=-a\Omega\sin\Omega t+b\Omega\cos\Omega t$ and $\ddot x_p=-\Omega^2x_p$:

$$
\begin{aligned}
\ddot x_p+2\zeta\omega\dot x_p+\omega^2x_p&=(\omega^2-\Omega^2)(a\cos\Omega t+b\sin\Omega t)+2\zeta\omega\Omega(-a\sin\Omega t+b\cos\Omega t)\\
&=\big[(\omega^2-\Omega^2)a+2\zeta\omega\Omega\,b\big]\cos\Omega t+\big[(\omega^2-\Omega^2)b-2\zeta\omega\Omega\,a\big]\sin\Omega t .
\end{aligned}
$$

Write $c=\omega^2-\Omega^2$ and $s=2\zeta\omega\Omega$. Matching with $F\cos\Omega t$:

$$
\begin{aligned}
ca+sb&=F,\\
-sa+cb&=0 .
\end{aligned}
$$

The determinant is $\Delta=c^2+s^2$, and Cramer's rule ([[MATH1054 M17 - Matrices II]]) gives

$$
a=\frac{Fc}{\Delta}=\frac{F(\omega^2-\Omega^2)}{(\omega^2-\Omega^2)^2+4\zeta^2\omega^2\Omega^2},\qquad b=\frac{Fs}{\Delta}=\frac{2\zeta\omega\Omega F}{(\omega^2-\Omega^2)^2+4\zeta^2\omega^2\Omega^2}.
$$

To put this in amplitude–phase form, set $a=R\cos\delta$ and $b=R\sin\delta$, so that $a\cos\Omega t+b\sin\Omega t=R\cos(\Omega t-\delta)$. Then

$$
\begin{aligned}
R&=\sqrt{a^2+b^2}=\frac{F\sqrt{c^2+s^2}}{\Delta}=\frac{F}{\sqrt{\Delta}},\\
\tan\delta&=\frac ba=\frac{2\zeta\omega\Omega}{\omega^2-\Omega^2},
\end{aligned}
$$

with $0\le\delta\le\pi$ because $b\ge0$. So the steady state is

$$
x_p=F\,A(\Omega)\cos(\Omega t-\delta),\qquad A(\Omega)=\frac{1}{\sqrt{(\omega^2-\Omega^2)^2+4\zeta^2\omega^2\Omega^2}} .
$$

The full solution is CF + PI. For $\zeta>0$ the CF decays, so it is the **transient**; the PI persists for as long as the forcing does, so it is the **steady state**. The steady state has the forcing frequency $\Omega$, not $\omega$ or $\omega_d$; its amplitude is the forcing amplitude times $A(\Omega)$; and it lags the forcing by $\delta$.

### Amplitude, phase and the resonance peak

At $\Omega=0$, $A(0)=1/\omega^2$, the static deflection per unit force. Dividing, with $r=\Omega/\omega$,

$$
\frac{A(\Omega)}{A(0)}=\frac{1}{\sqrt{(1-r^2)^2+4\zeta^2r^2}} .
$$

The peak is where $D(u)=(\omega^2-u)^2+4\zeta^2\omega^2u$, with $u=\Omega^2$, is smallest:

$$
\begin{aligned}
\frac{\mathrm dD}{\mathrm du}&=-2(\omega^2-u)+4\zeta^2\omega^2=0\\
u&=\omega^2(1-2\zeta^2).
\end{aligned}
$$

A peak at positive $\Omega$ therefore needs $\zeta<1/\sqrt2$, and it lies at $\Omega_r=\omega\sqrt{1-2\zeta^2}$, slightly below $\omega$. At that point

$$
\begin{aligned}
D&=(2\zeta^2\omega^2)^2+4\zeta^2\omega^2\cdot\omega^2(1-2\zeta^2)\\
&=4\zeta^4\omega^4+4\zeta^2\omega^4-8\zeta^4\omega^4\\
&=4\zeta^2\omega^4(1-\zeta^2),
\end{aligned}
$$

so

$$
\frac{A_{\max}}{A(0)}=\frac{1}{2\zeta\sqrt{1-\zeta^2}} ,
$$

which is $5.03$ for $\zeta=0.1$ and grows without bound as $\zeta\to0$. For $\zeta\ge1/\sqrt2$ the amplitude falls steadily from $A(0)$. At $\Omega=\omega$ the phase lag is $90^\circ$ for every $\zeta$. This large response near the natural frequency is **resonance**, and in the limit $\zeta=0$, $\Omega=\omega$ it becomes the unbounded clash of [[#Undamped resonance (Exercise 63(j))]].

![[m1054_forced_amplitude_phase.png|800]]

A lamp post's natural frequency is fixed by its structure, while the vortex-shedding frequency rises with wind speed, so its amplitude grows as the wind speed brings $\Omega$ up to $\omega$ and falls again beyond it. Stiffer concrete or cast-iron posts have a higher $\omega$ that ordinary winds do not reach.

### A worked forced response

Solve $\ddot x+2\dot x+5x=10\cos t$ from rest, $x(0)=\dot x(0)=0$. This is the system of Exercise 21(a), with $\omega=\sqrt5$, $2\zeta\omega=2$ so $\zeta=1/\sqrt5\approx0.447$, and forcing $F=10$, $\Omega=1$. The CF is $e^{-t}(A\cos2t+B\sin2t)$. Trying $x_p=a\cos t+b\sin t$ with $\ddot x_p=-x_p$:

$$
\begin{aligned}
\ddot x_p+2\dot x_p+5x_p&=4x_p+2\dot x_p\\
&=4a\cos t+4b\sin t-2a\sin t+2b\cos t\\
&=(4a+2b)\cos t+(4b-2a)\sin t .
\end{aligned}
$$

Matching: $4b-2a=0$ gives $a=2b$, and $4a+2b=10$ then gives $10b=10$, so $b=1$ and $a=2$:

$$
x_p=2\cos t+\sin t=\sqrt5\cos(t-\delta),\qquad\delta=\arctan\tfrac12=0.4636\ \mathrm{rad}=26.57^\circ .
$$

> [!check] Against the general formula
> With $c=\omega^2-\Omega^2=4$ and $s=2\zeta\omega\Omega=2$, $\Delta=16+4=20$, so $a=10(4)/20=2$, $b=10(2)/20=1$, amplitude $F/\sqrt\Delta=10/\sqrt{20}=\sqrt5=2.236$ and $\tan\delta=2/4$. The amplification is $A(1)/A(0)=(1/\sqrt{20})/(1/5)=\sqrt5/2=1.118$, below the peak $1/(2\zeta\sqrt{1-\zeta^2})=5/4$ at $\Omega_r=\sqrt{5(1-2/5)}=\sqrt3\approx1.732$.

The conditions apply to the full solution $x=e^{-t}(A\cos2t+B\sin2t)+2\cos t+\sin t$, with

$$
\dot x=e^{-t}\big[(-A+2B)\cos2t+(-B-2A)\sin2t\big]-2\sin t+\cos t .
$$

The condition $x(0)=0$ gives $A+2=0$, so $A=-2$. The condition $\dot x(0)=0$ gives $-A+2B+1=0$, so $2+2B+1=0$ and $B=-\tfrac32$. Hence

$$
x=\underbrace{-e^{-t}\big(2\cos2t+\tfrac32\sin2t\big)}_{\text{transient}}+\underbrace{2\cos t+\sin t}_{\text{steady state}} .
$$

By $t=3T=3$ (with $T=1/(\zeta\omega)=1$) the transient envelope has fallen to 5%, and the motion is the steady oscillation at the forcing frequency.

![[m1054_transient_steady_state.png|900]]

### The LCR circuit

For a series inductor $L$, resistor $R$ and capacitor $C$ driven by $V_i$, with output $V_o$ across the capacitor, the same current $i=C\dot V_o$ flows through all three, and Kirchhoff's voltage law gives

$$
\begin{aligned}
L\frac{\mathrm di}{\mathrm dt}+Ri+V_o&=V_i\\
LC\ddot V_o+RC\dot V_o+V_o&=V_i\\
\ddot V_o+\frac RL\dot V_o+\frac1{LC}V_o&=\frac1{LC}V_i .
\end{aligned}
$$

Comparing with the standard form, $\omega^2=1/(LC)$ and $2\zeta\omega=R/L$, so

$$
\omega=\frac1{\sqrt{LC}},\qquad\zeta=\frac R{2L}\sqrt{LC}=\frac R2\sqrt{\frac CL},
$$

and a sinusoidal input $V_i=V\cos\Omega t$ is the forced problem above with $F=V/(LC)$. Every result above carries over: the resistor sets the damping and the circuit resonates near $\Omega=1/\sqrt{LC}$.

## Terminology and alternative names

| Here (booklet and James) | Also called | Where |
|---|---|---|
| auxiliary equation | characteristic equation | James §10.9; MATH2048 and SESA2027 |
| damping parameter $\zeta$ | damping ratio | SESA2027, FEEG1002 |
| natural frequency $\omega$ | undamped natural frequency $\omega_n$ | SESA2027, FEEG1002 |
| inhomogeneous equation | nonhomogeneous equation | James |
| particular integral, complementary function | particular solution, homogeneous solution | MATH2048 |
| $\mathrm j=\sqrt{-1}$ | $i$ | mathematics texts |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M13 Solutions - Differential Equations III]]
- Previous: [[MATH1054 M12 - Differential Equations II]] · Next: [[MATH1054 M14 - Vectors I]]
- Earlier: [[MATH1054 M06 - Differential Equations I]] first solves the homogeneous second-order equation and classifies ODEs ([[Classification of Differential Equations]]); the complex-root form uses [[Euler's Formula]] and [[Complex Numbers - Cartesian, Polar and Exponential Forms]] from [[MATH1054 M05 - Complex Numbers I]]; the independence tests use [[Determinants and Cofactors]].
- Concept: [[Linear Differential Operators and Superposition]]
- Year 2 mathematics: [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] (Wronskian, mass–spring–damper), [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]] (undetermined coefficients, clashes, resonance), [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]], and [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]], which solves the same initial-value problems by transform; concepts [[Auxiliary Equation]], [[Method of Undetermined Coefficients]], [[Resonance]], [[Boundary Value Problems]].
- Vibration and control: [[FEEG1002 D6 - Single Degree of Freedom Vibration]] and [[Logarithmic Decrement]]; [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] (aircraft modes as damped second-order systems), [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]], [[SESA2027 A5 - Frequency Response and Bode Plots]], [[Damping Ratio and Natural Frequency]], [[Step Response Specifications]], [[Frequency Response Function]]; [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]].

## Sources

- MATH1054 Module Booklet, Module 13 (PDF pp. 48–51): work scheme items 1–8 (James) and the Stroud alternative (Programme 25, frames 23–49); Specimen Test 13 on the module's final page. The work scheme's "p. 881" for Examples 10.44–10.45 is p. 861 of James.
- James, *Modern Engineering Mathematics* (6th ed.): §10.8.1–10.8.2 (pp. 839–849, Examples 10.23–10.33, Exercises 46, 49); §10.9.1 (Examples 10.34–10.36); §10.9.3 (pp. 857–862, Examples 10.40–10.45, Figure 10.19, Exercises 62–63); §10.10.1–10.10.4 (pp. 864–876, equations 10.48–10.56, Example 10.46, Exercises 66, 68); Review Exercise 21(a) (p. 893).

## Self-study tasks

### Core

- [ ] Exercises 62(b), 63(a),(b) (Module 13 work scheme, item 3): particular integrals for polynomial, trigonometric and exponential forcing. → [[#4. Particular integrals by undetermined coefficients (James §10.9.3)]] · [[MATH1054 M13 Solutions - Differential Equations III#Exercise 63|solution]] (62(b) under [[MATH1054 M13 Solutions - Differential Equations III#Part B: Assigned exercises|Part B]])
- [ ] Exercise 63(h) (Module 13 work scheme, item 4): a sum of forcing terms. → [[#Sums of forcing terms (Example 10.43, Exercise 63(h))]] · [[MATH1054 M13 Solutions - Differential Equations III#Exercise 63|solution]]
- [ ] Exercise 63(j) (Module 13 work scheme, item 5): forcing at the natural frequency. → [[#Undamped resonance (Exercise 63(j))]] · [[MATH1054 M13 Solutions - Differential Equations III#Exercise 63|solution]]
- [ ] Exercise 21(a) (Module 13 work scheme, item 6): an initial-value problem applied to CF + PI. → [[#An initial-value problem (Exercise 21(a))]] · [[MATH1054 M13 Solutions - Differential Equations III#Part B: Assigned exercises|solution]]
- [ ] Specimen Test 13, Q1–Q3, timed. → [[MATH1054 M13 Solutions - Differential Equations III#Part C: Specimen Test 13|solution]]

### Further practice

- [ ] Exercises 46(a), 49(c) (Module 13 work scheme, item 2): write down the operator. → [[MATH1054 M13 Solutions - Differential Equations III#Part B: Assigned exercises|solution]]
- [ ] Exercises 66(b), 68(d) (Module 13 work scheme, item 8): natural frequency and damping parameter. → [[#Reading off the natural frequency and damping parameter (Exercises 66(b), 68(d), Specimen Test 13 Q3)]] · [[MATH1054 M13 Solutions - Differential Equations III#Part B: Assigned exercises|solution]]
- [ ] Examples 10.40–10.45 (Module 13 work scheme, items 3–5), reworked without the text, including both clash cases. → [[MATH1054 M13 Solutions - Differential Equations III#Part A: Worked examples|solution]]
- [ ] Example 10.31 (Module 13 work scheme, item 2): test four sets of functions for linear independence. → [[#Linear independence (Examples 10.30 and 10.31)]]
- [ ] Example 10.46 (James §10.10.2, Module 13 work scheme, item 7): the damped pendulum's natural frequency, damping parameter, overshoots and decay time. → [[#The damped pendulum (Example 10.46)]]
