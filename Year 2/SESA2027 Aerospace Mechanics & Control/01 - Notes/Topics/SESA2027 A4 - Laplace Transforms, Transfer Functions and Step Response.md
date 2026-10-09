---
title: "SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part A: Dynamic Systems"
order: 4
tags:
  - sesa2027
  - laplace-transform
  - transfer-function
  - step-response
aliases: ["Step Response", "Time-Domain Specifications"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
next_topics: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
key_concepts: ["[[Laplace Transform]]", "[[Transfer Function]]", "[[Poles and Zeros]]", "[[Step Response Specifications]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 1 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf"]
---

# SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response

> [!abstract] Summary
> The Laplace transform turns linear ODEs into algebraic equations in $s$. Initial conditions come in automatically, and piecewise inputs such as steps are easy to handle. Solving the SPO approximation driven by a step input introduces the **transfer function** $G(s) = X(s)/U(s)$. Its denominator roots are the **poles**, which are the system's eigenvalues, and its numerator roots are the **zeros**. Partial fractions and inverse transforms give $x(t)$, which we characterise by **rise time**, **overshoot** and **settling time**.

## Key Concepts
- [[Laplace Transform]] · [[Transfer Function]] · [[Poles and Zeros]] · [[Step Response Specifications]]

---

## 1. Why Laplace? (L1.07, DAP3)
The route is:
1. ODE in the time domain.
2. Transform to an algebraic equation in the $s$-domain.
3. Solve the algebra.
4. Apply the inverse Laplace transform to get the time-domain solution.

The classical method (homogeneous solution plus particular integral) only works for simple forcing, is labour-intensive, and becomes impractical for piecewise inputs.

$$
\mathcal L\{g(t)\} = G(s) = \int_0^\infty g(t)e^{-st}dt,\qquad s = \sigma+j\omega,\qquad g(t) = 0\text{ for }t<0
$$

## 2. Properties and standard transforms (MATH2048 L11–13 recap)

| Property / function | Result |
|---|---|
| Linearity | $\mathcal L\{\alpha g_1+\beta g_2\} = \alpha G_1+\beta G_2$ |
| Derivative | $\mathcal L\{\dot g\} = sG(s)-g(0)$ |
| 2nd derivative | $\mathcal L\{\ddot g\} = s^2G-sg(0)-\dot g(0)$ |
| $n$th derivative | $s^nG-s^{n-1}g(0)-\dots-g^{(n-1)}(0)$ |
| Integral | $\mathcal L\{\int_0^tg\,d\tau\} = G(s)/s$ |
| Unit step $u(t)$ | $1/s$ |
| Unit ramp $t$ | $1/s^2$ |
| Time shift | $\mathcal L\{g(t-a)u(t-a)\} = e^{-as}G(s)$ |
| Impulse $\delta(t)$ | $1$ |
| $\sin\omega t$ | $\omega/(s^2+\omega^2)$ |
| $e^{\sigma t}\cos\omega t$ | $(s-\sigma)/[(s-\sigma)^2+\omega^2]$ |
| $e^{\sigma t}\sin\omega t$ | $\omega/[(s-\sigma)^2+\omega^2]$ |

In short, differentiation in time is multiplication by $s$, and integration is division by $s$.

## 3. SPO step response
The SPO as a forced mass–spring–damper: $m\ddot x+c\dot x+kx = r(t)$. In terms of $\omega_n$ and $\zeta$:

$$
\ddot x+2\zeta\omega_n\dot x+\omega_n^2x = \frac{1}{mI_{yy}}r(t),\qquad r(t) = u(t)\ (\text{unit step})
$$

Transform with zero initial conditions, $x(0) = \dot x(0) = 0$:

$$
(s^2+2\zeta\omega_ns+\omega_n^2)X(s) = \frac{1}{mI_{yy}}\frac1s\quad\Rightarrow\quad X(s) = \underbrace{\left[\frac{1}{s^2+2\zeta\omega_ns+\omega_n^2}\right]}_{G(s)}\underbrace{\frac{1}{mI_{yy}s}}_{U(s)}
$$

### Transfer function
- $G(s) = X(s)/U(s) = B(s)/A(s)$ describes the input–output behaviour, independent of the input.
- Roots of $B(s)$ are the **zeros**. Roots of $A(s)$ are the **poles**, the system's eigenvalues and natural modes.

### Partial fractions (F-4C: $\omega_n = 1.4115$, $\zeta = 0.2637$)
The denominator is $s(s^2+0.744s+1.992)$, with roots $s_1 = 0$ and $s_{2,3} = -0.372\pm1.362i$. Write

$$
X(s) = \frac{K}{s(s^2+0.744s+1.992)} = \frac{r_1}{s}+\frac{r_2(s-\sigma)}{(s-\sigma)^2+\omega^2}+\frac{r_3\omega}{(s-\sigma)^2+\omega^2}
$$

$$
x(t) = r_1+r_2e^{\sigma t}\cos\omega t+r_3e^{\sigma t}\sin\omega t
$$

with the slide values $r_1 = 2.843\times10^{-5}$, $r_2 = -2.843\times10^{-5}$, $r_3 = -7.766\times10^{-6}$ ($\sigma=-0.372$, $\omega=1.362$), where $K$ collects the input scaling.

- $r_2 = -r_1$, so that $x(0) = 0$.
- $r_3 = r_2\,\zeta/\sqrt{1-\zeta^2}$.
- The final value is $r_1 = K/\omega_n^2 = \lim_{s\to0}sX(s)$ (the final-value theorem).

## 4. Time-domain specifications
Normalise by the final value.

![[amc_second_order_step_family.png|560]]

| Spec | Definition | 2nd-order formula |
|---|---|---|
| **Rise time** $t_r$ | 10% to 90% of final value (speed) | $t_r\approx\dfrac{1.8}{\omega_n}$ |
| **Overshoot** $OS$ | Maximum excursion beyond the final value, as % | $OS = e^{-\zeta\pi/\sqrt{1-\zeta^2}}\times100\%$ |
| **Peak time** | Time of the first peak | $t_p = \dfrac{\pi}{\omega_n\sqrt{1-\zeta^2}}$ |
| **Settling time** $t_s$ | Time to stay within 1% (or 5%) of the final value | $t_s\approx\dfrac{4.6}{\zeta\omega_n} = \dfrac{4.6}{\vert\sigma\vert}$ (1%), $\dfrac{3}{\zeta\omega_n}$ (5%) |

- Overshoot depends **only on $\zeta$**, and increases as $\zeta$ decreases.
- Settling time depends on the **real part** $\sigma = -\zeta\omega_n$.
- $t_r\approx1.8/\omega_n$ is a rough rule, best near $\zeta\approx0.5$. For $\zeta=0.4$ the exact 10–90% rise time is $1.46/\omega_n$.

> [!example] PS1 Q3: $\omega_n = 3.65$ rad/s, $\zeta = 0.40$
> $t_r = 1.8/3.65 = 0.493$ s, $t_s = 4.6/(0.4\times3.65) = 3.151$ s, and
>
> $$OS = e^{-0.4\pi/\sqrt{0.84}} = 25.4\%$$
>
> The sheet quotes 22.4%, which is what you get if you **forget the square root**: $e^{-0.4\pi/0.84}$. See [[SESA2027 Practice Problems 1 Solutions]].

![[amc_ps1_q3_step_annotated.png|620]]

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] · Next: [[SESA2027 A5 - Frequency Response and Bode Plots]]
- Maths: MATH2048 Lectures 11–13 (Laplace transforms), partial fractions
- Sensors use the same metrics: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]

## Year 1 foundation
- The SDOF equation $m\ddot x + c\dot x + kx = f$ and its characteristic equation $ms^2 + cs + k = 0$: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lecture 1.07; Franklin, Powell & Emami-Naeini, *Feedback Control of Dynamic Systems*, Ch. 3
