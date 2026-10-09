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
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M06 - Differential Equations I]]", "[[MATH1054 M12 - Differential Equations II]]"]
next_topics: ["[[MATH1054 M14 - Vectors I]]"]
key_concepts: ["[[Linear Differential Operators and Superposition]]", "[[Auxiliary Equation]]", "[[Method of Undetermined Coefficients]]", "[[Damping Ratio and Natural Frequency]]", "[[Resonance]]"]
tutorial_sheets: ["[[MATH1054 M13 Solutions - Differential Equations III]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 13)", "02 - Sources/Modern Engineering Mathematics.pdf (§10.8–10.10)"]
---

# MATH1054 M13 - Differential Equations III

> [!abstract] Summary
> Linear ODEs obey **superposition**: $\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2]$. Everything in this module follows from that one fact:
> - the general solution of $\mathrm L[x]=f$ is **CF + PI**;
> - the CF comes from the auxiliary equation, of any order;
> - the PI comes from an educated guess matching $f$, adjusted when the guess clashes with the CF.
>
> The engineering reading, via $\zeta$ and $\omega$, classifies every damped second-order system.

## Key Concepts
- [[Linear Differential Operators and Superposition]] · [[Auxiliary Equation]] · [[Method of Undetermined Coefficients]] · [[Damping Ratio and Natural Frequency]] · [[Resonance]]

---

## 1. Operators and linearity (James §10.8)
$\mathrm L=a_n(t)\mathrm D^n+\dots+a_1(t)\mathrm D+a_0(t)$ is linear. So:
- if $x_1,\dots,x_n$ solve $\mathrm L[x]=0$, then so does $\sum c_ix_i$;
- if $x_p$ solves $\mathrm L[x]=f$, then **every** solution is $x=x_c+x_p$;
- if $\mathrm L[x_1]=f_1$ and $\mathrm L[x_2]=f_2$, then $\mathrm L[x_1+x_2]=f_1+f_2$. This lets you split the forcing into pieces (Ex 10.43).

## 2. The complementary function, of any order (James §10.9)
Try $e^{mt}$ to get $P(m)=0$. Each root contributes:

| Root of $P$ | Contribution |
|---|---|
| real $m$, simple | $e^{mt}$ |
| real $m$, multiplicity $k$ | $(A_0+A_1t+\dots+A_{k-1}t^{k-1})e^{mt}$ |
| pair $\alpha\pm\mathrm j\beta$ | $e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ |

For example, $m^4-\lambda^4=(m^2-\lambda^2)(m^2+\lambda^2)$ gives $e^{\pm\lambda t}$, $\cos\lambda t$ and $\sin\lambda t$.

## 3. The particular integral (undetermined coefficients)
| $f(t)$ | Trial $x_p$ |
|---|---|
| polynomial of degree $n$ | general polynomial of degree $n$ (include every lower power) |
| $e^{kt}$ | $Ce^{kt}$, with $C=1/P(k)$ |
| $\cos\omega t$ or $\sin\omega t$ | $a\cos\omega t+b\sin\omega t$ (**both** terms) |
| sum of the above | sum of the trials (superposition) |

**Clash rule**: if the trial already appears in the CF, multiply it by $t^s$, where $s$ is the multiplicity of the root. For exponentials there are shortcuts:

$$
x_p=\frac{e^{kt}}{P(k)},\qquad x_p=\frac{te^{kt}}{P'(k)}\ \ (\text{simple root}),\qquad x_p=\frac{t^2e^{kt}}{P''(k)}\ \ (\text{double root})
$$

See [[Method of Undetermined Coefficients]] (MATH2048) for the general version.

## 4. Damped second-order systems (James §10.10)

$$
\ddot x+2\zeta\omega\,\dot x+\omega^2x=0,\qquad m=-\zeta\omega\pm\omega\sqrt{\zeta^2-1}
$$

| $\zeta$ | Behaviour | Solution form |
|---|---|---|
| $\zeta=0$ | undamped SHM | $A\cos\omega t+B\sin\omega t$ |
| $0<\zeta<1$ | **under-damped**: decaying oscillation, frequency $\omega\sqrt{1-\zeta^2}$ | $e^{-\zeta\omega t}(A\cos\omega_dt+B\sin\omega_dt)$ |
| $\zeta=1$ | **critical**: fastest return without overshoot | $(A+Bt)e^{-\omega t}$ |
| $\zeta>1$ | **over-damped**: sluggish, with no oscillation | two decaying exponentials |

**Reading off $\zeta$ and $\omega$**: first divide by the coefficient of $\ddot x$. Then $\omega^2$ is the coefficient of $x$, and $2\zeta\omega$ is the coefficient of $\dot x$.

Some rules of thumb (James):
- $\zeta\approx0.3$ gives about 3 visible overshoots, and $\zeta\approx0.7$ gives about 1.
- The **decay time** is $1/(\zeta\omega)$.

With forcing, the **CF is the transient** (it decays when $\zeta>0$), and the **PI is the steady state**.

![[m1054_step_response_21a.png|600]]

> [!warning] Resonance
> Forcing at the natural frequency of an undamped system ($\ddot x+16x=2\sin4t$) clashes with the CF. The PI $-\frac14t\cos4t$ then grows without bound ([[Resonance]]).

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M13 Solutions - Differential Equations III]]
- Prev: [[MATH1054 M12 - Differential Equations II]]
- Next level: MATH2048 [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]; SESA2027 [[Damping Ratio and Natural Frequency]], [[Step Response Specifications]]

## Sources
- MATH1054 Module Booklet, Module 13; James §10.8–10.10
