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
status: lectured
coverage: "L1.07 (Laplace transform, SPO step response, time-domain specifications)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
next_topics: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
key_concepts: ["[[Laplace Transform]]", "[[Transfer Function]]", "[[Poles and Zeros]]", "[[Step Response Specifications]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 1 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf", "02 - Sources/Lectures/Lecture 1.07 recording.txt"]
---

# SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response

> [!abstract] Summary
> The Laplace transform turns linear ODEs into algebra in $s$, with the initial conditions built in and piecewise inputs such as steps easy to handle. Solving the SPO approximation for a step input introduces the transfer function $G(s) = X(s)/U(s)$, whose poles are the system's eigenvalues and whose zeros are the roots of its numerator. Partial fractions and inverse transforms then give $x(t)$, which is characterised by its rise time, overshoot and settling time.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives $\omega_n$ and $\zeta$ (or a second-order transfer function) and asks for $t_r$, $OS$, $t_s$, $t_p$, the final value of a step response, or a sketch. Laplace and partial fractions are not examined as calculations (L1.07, ll. 8–12, 720–727).
> - **Assumptions:** linear, time-invariant, zero initial conditions; stable (for the final-value theorem); underdamped $0<\zeta<1$ for the overshoot and peak-time formulas; 1 % settling band in this module.
> - **Method:** 1. Read $\omega_n^2$ and $2\zeta\omega_n$ off $s^2+2\zeta\omega_ns+\omega_n^2$. 2. Final value $=\lim_{s\to0}sX(s)$ = static gain × step size. 3. $OS=e^{-\zeta\pi/\sqrt{1-\zeta^2}}\times100\%$. 4. $t_s\approx4.6/(\zeta\omega_n)$, $t_p=\pi/(\omega_n\sqrt{1-\zeta^2})$, $t_r\approx1.8/\omega_n$. 5. Sketch: start at 0 with zero slope, peak at $t_p$, settle by $t_s$.
> - **Common mistakes:** dropping the square root in the overshoot exponent (the PS1 Q3 sheet answer does this); giving overshoot as a fraction instead of a percentage (L1.07, l. 943).
> - **Practise:** [[#Worked example: PS1 Q3 specifications from first principles]] · [[SESA2027 Mock Questions#Q4. Step response of a second-order system|Mock Q4]] · [[SESA2027 Practice Problems 1 Solutions]]

Kick the elevator to a new position and hold it: that is a step. The aircraft's pitch response is the SPO mass–spring–damper being pushed to a new equilibrium. It accelerates towards the new value, overshoots because nothing stops it in time, swings back, and settles. Three numbers describe that shape. Rise time says how fast it gets there and is set mainly by $\omega_n$, the stiffness. Overshoot says how far it misses and is set only by $\zeta$, the damping. Settling time says when it stops wobbling and is set by the decay rate $\zeta\omega_n$, the real part of the poles.

The Laplace transform is the tool that gets us there without solving the ODE by hand. It turns differentiation into multiplication by $s$, so the ODE becomes algebra. The ratio of output to input, the transfer function, is then a property of the aircraft alone. Its denominator is the same characteristic polynomial as in A3, so the poles are the eigenvalues and they fix the shape of every response.

---

## 1. Why Laplace? (L1.07, DAP3)
The route is:
1. ODE in the time domain.
2. Transform to an algebraic equation in the $s$-domain.
3. Solve the algebra.
4. Apply the inverse Laplace transform to get the time-domain solution.

The classical method (homogeneous solution plus particular integral) only works for simple forcing, is labour-intensive, and becomes impractical for piecewise inputs.

$$
\mathcal L\{g(t)\} = G(s) = \int_0^\infty g(t)e^{-st}dt,\qquad s = \sigma+i\omega,\qquad g(t) = 0\text{ for }t<0
$$

> [!note] One-sided transform (L1.07, ll. 48–53)
> The integral starts at $t = 0$: this is the unilateral Laplace transform, and $g(t)$ is taken as zero for $t<0$. If an event before $t = 0$ matters, shift the time origin so that the whole input starts at or after zero.

> [!note] $i$, not $j$
> The slide writes $s = \sigma+j\omega$. The lecturer said "I made a mistake, I didn't update my slide here, I should have used i instead of j" and promised a corrected upload (L1.07, ll. 45–46). The course uses $i$ for $\sqrt{-1}$ everywhere else, so this note does too.

> [!info] Exam scope (L1.07, ll. 6–12)
> "I'm not expecting you to solve Laplace transform problems in the exam, I won't expect you to do that also in the quiz." The aim is to understand why the transform is useful for analysis. You may need to use it in the lab report. A quick self-check if you do transform by hand: "if … you end up with a $t$ in the final transform, you know there's something wrong" (l. 43).

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

In short, differentiation in time is multiplication by $s$, and integration is division by $s$. The lecturer flagged both results as the ones used later to design controllers (L1.07, ll. 76–79): the D term of a PID is a factor $s$ and the I term a factor $1/s$.

Why differentiation becomes multiplication by $s$ (integration by parts, assuming $g(t)e^{-st}\to0$ as $t\to\infty$):

$$
\mathcal L\{\dot g\}=\int_0^\infty\dot g(t)e^{-st}\,dt
$$

$$
=\Big[g(t)e^{-st}\Big]_0^\infty-\int_0^\infty g(t)\,(-s)e^{-st}\,dt
$$

$$
=\big(0-g(0)\big)+s\int_0^\infty g(t)e^{-st}\,dt
$$

$$
=sG(s)-g(0)
$$

Apply it twice for $\ddot g$: $\mathcal L\{\ddot g\}=s\big(sG-g(0)\big)-\dot g(0)=s^2G-sg(0)-\dot g(0)$. With zero initial conditions every $d/dt$ is just a factor $s$.

> [!example] The doublet (the self-study task)
> A doublet of unit amplitude and half-width $t_1$ is $u(t)-2u(t-t_1)+u(t-2t_1)$. By linearity and the time-shift rule:
>
> $$\mathcal L\{\text{doublet}\}=\frac1s-\frac{2e^{-t_1s}}{s}+\frac{e^{-2t_1s}}{s}=\frac{(1-e^{-t_1s})^2}{s}$$
>
> As $s\to0$, $(1-e^{-t_1s})^2\approx(t_1s)^2$, so $s\cdot\mathcal L\{\cdot\}\to0$: the input has no lasting value, which is why the aircraft returns to trim (see the tip below, L1.07, ll. 89–224).

L1.07 uses four standard inputs, each with a purpose (ll. 89–224). A step is an elevator change from 0° to, say, 5° at $t = 0$, and a series of steps models a series of stick inputs. A ramp, the integral of a step, is a continuously increasing elevator input; adding a delayed negative ramp, $t\,u(t)-(t-t_1)\,u(t-t_1)$, stops the increase at $t_1$ and holds the deflection there (ll. 103–108), and a further pair of ramps with the opposite sign brings it back to zero. A doublet, $u(t)-2u(t-t_1)+u(t-2t_1)$, is built from time-shifted steps. It excites the dynamics but returns the aircraft to trim, adding no net energy, which is why flight testing uses it (see also L2.05 in [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning|B3]]). An impulse models a gust. The slide and lecture describe it as built from two step functions; strictly it is the difference of a step and a delayed step, scaled to unit area, in the limit of zero width, $\delta(t) = \lim_{t_0\to0}\,[u(t)-u(t-t_0)]/t_0$.

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
- Roots of $B(s)$ are the zeros. Roots of $A(s)$ are the poles, the system's eigenvalues and natural modes.

### Partial fractions (F-4C: $\omega_n = 1.4115$, $\zeta = 0.2637$)

The form of the expansion depends on the roots of the denominator (L1.07, ll. 525–536):

| Roots | Terms in $X(s)$ | Terms in $x(t)$ |
|---|---|---|
| Real and distinct, $p_1\neq p_2$ | $\dfrac{r_1}{s-p_1}+\dfrac{r_2}{s-p_2}$ | $r_1e^{p_1t}+r_2e^{p_2t}$ |
| Real and repeated, $p$ twice | $\dfrac{r_1}{s-p}+\dfrac{r_2}{(s-p)^2}$ | $r_1e^{pt}+r_2te^{pt}$ |
| Complex pair, $\sigma\pm i\omega$ | $\dfrac{r_2(s-\sigma)+r_3\omega}{(s-\sigma)^2+\omega^2}$ | $e^{\sigma t}(r_2\cos\omega t+r_3\sin\omega t)$ |

The SPO step response has one root of each of the first and third kinds:
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

Where the residues come from (not examined, but this is the step the slide jumps). Work with the normalised case $K=\omega_n^2$, so the final value is 1, and write $\sigma=-\zeta\omega_n$, $\omega_d=\omega_n\sqrt{1-\zeta^2}$. Then $s^2+2\zeta\omega_ns+\omega_n^2=(s+\zeta\omega_n)^2+\omega_d^2$. Try

$$
\frac{\omega_n^2}{s\left(s^2+2\zeta\omega_ns+\omega_n^2\right)}=\frac{r_1}{s}+\frac{Bs+C}{s^2+2\zeta\omega_ns+\omega_n^2}
$$

Multiply through by the denominator:

$$
\omega_n^2=r_1\left(s^2+2\zeta\omega_ns+\omega_n^2\right)+(Bs+C)s
$$

Match coefficients: $s^0$ gives $r_1=1$; $s^2$ gives $r_1+B=0$, so $B=-1$; $s^1$ gives $2\zeta\omega_nr_1+C=0$, so $C=-2\zeta\omega_n$. Hence

$$
X(s)=\frac1s-\frac{s+2\zeta\omega_n}{(s+\zeta\omega_n)^2+\omega_d^2}
$$

Split the numerator as $(s+\zeta\omega_n)+\zeta\omega_n$ to match the two table entries:

$$
X(s)=\frac1s-\frac{s+\zeta\omega_n}{(s+\zeta\omega_n)^2+\omega_d^2}-\frac{\zeta\omega_n}{\omega_d}\cdot\frac{\omega_d}{(s+\zeta\omega_n)^2+\omega_d^2}
$$

Invert term by term:

$$
\boxed{x(t)=1-e^{-\zeta\omega_nt}\left(\cos\omega_dt+\frac{\zeta}{\sqrt{1-\zeta^2}}\sin\omega_dt\right)}
$$

So $r_2=-r_1$ and $r_3=-r_1\,\zeta\omega_n/\omega_d=r_2\,\zeta/\sqrt{1-\zeta^2}$, as listed above. For general $K$ multiply everything by $K/\omega_n^2$.

Final-value theorem, line by line (assumes the system is stable, so the limit exists):

$$
sX(s) = s\cdot\frac{K}{s(s^2+2\zeta\omega_ns+\omega_n^2)}
$$

$$
sX(s) = \frac{K}{s^2+2\zeta\omega_ns+\omega_n^2}
$$

$$
\lim_{t\to\infty}x(t) = \lim_{s\to0}sX(s) = \frac{K}{\omega_n^2}
$$

> [!check] Residues for the F-4C example
> With $\omega_n^2 = 1.9925$ and $r_1 = 2.843\times10^{-5}$, $K = r_1\omega_n^2 = 5.665\times10^{-5}$. With $\zeta = 0.2637$, $\zeta/\sqrt{1-\zeta^2} = 0.2734$, so $r_3 = -2.843\times10^{-5}\times0.2734 = -7.77\times10^{-6}$, matching the slide.

> [!info] What the exam can ask here (L1.07)
> - Finding the residues by partial fractions: "I won't be asking you to do that in the exam" (ll. 712–727). Know where the three terms come from.
> - "What is the time response as time tends to infinity to a step?" "This could be an exam question" (ll. 811–821). The final value is set by the system's static gain (here $K/\omega_n^2$), not by the step size alone (clarified at ll. 883–911). If you do not want to work out $r_1$, answer for the normalised response: it tends to 1 (ll. 914–922).

## 4. Time-domain specifications
Normalise by the final value.

![[amc_second_order_step_family.png|560]]

| Spec | Definition | 2nd-order formula |
|---|---|---|
| Rise time $t_r$ | 10% to 90% of final value (speed) | $t_r\approx\dfrac{1.8}{\omega_n}$ |
| Overshoot $OS$ | Maximum excursion beyond the final value, as % | $OS = e^{-\zeta\pi/\sqrt{1-\zeta^2}}\times100\%$ |
| Peak time | Time of the first peak | $t_p = \dfrac{\pi}{\omega_n\sqrt{1-\zeta^2}}$ |
| Settling time $t_s$ | Time to stay within 1% (or 5%) of the final value | $t_s\approx\dfrac{4.6}{\zeta\omega_n} = \dfrac{4.6}{\vert\sigma\vert}$ (1%), $\dfrac{3}{\zeta\omega_n}$ (5%) |

- Overshoot depends only on $\zeta$, and increases as $\zeta$ decreases.
- Settling time depends on the real part $\sigma = -\zeta\omega_n$.
- $t_r\approx1.8/\omega_n$ is a rough rule, best near $\zeta\approx0.5$. For $\zeta=0.4$ the exact 10–90% rise time is $1.46/\omega_n$.

![[amc_step_envelope_settling.png|860]]

### Deriving the specifications

Start from the normalised step response derived above, with $a=\zeta\omega_n$ and $\omega_d=\omega_n\sqrt{1-\zeta^2}$ (underdamped, $0<\zeta<1$):

$$
x(t)=1-e^{-at}\left(\cos\omega_dt+\frac{a}{\omega_d}\sin\omega_dt\right)
$$

**Peak time.** Differentiate with the product rule:

$$
\dot x=a\,e^{-at}\left(\cos\omega_dt+\frac{a}{\omega_d}\sin\omega_dt\right)-e^{-at}\left(-\omega_d\sin\omega_dt+a\cos\omega_dt\right)
$$

The cosine terms cancel:

$$
\dot x=e^{-at}\sin\omega_dt\left(\frac{a^2}{\omega_d}+\omega_d\right)=\frac{\omega_n^2}{\omega_d}\,e^{-at}\sin\omega_dt
$$

using $a^2+\omega_d^2=\omega_n^2$. The slope is zero when $\sin\omega_dt=0$. The first peak is at $\omega_dt=\pi$:

$$
t_p=\frac{\pi}{\omega_d}=\frac{\pi}{\omega_n\sqrt{1-\zeta^2}}
$$

The same line shows $\dot x(0)=0$: a second-order step response always starts with zero slope.

**Overshoot.** At $t_p$, $\cos\omega_dt_p=-1$ and $\sin\omega_dt_p=0$:

$$
x(t_p)=1-e^{-at_p}(-1)=1+e^{-a\pi/\omega_d}
$$

$$
\frac{a\pi}{\omega_d}=\frac{\zeta\omega_n\pi}{\omega_n\sqrt{1-\zeta^2}}=\frac{\zeta\pi}{\sqrt{1-\zeta^2}}
$$

$$
OS=e^{-\zeta\pi/\sqrt{1-\zeta^2}}\times100\%
$$

$\omega_n$ has cancelled: overshoot depends on $\zeta$ alone.

**Settling time.** The bracket $\cos\omega_dt+(a/\omega_d)\sin\omega_dt$ is a sinusoid of amplitude $\sqrt{1+a^2/\omega_d^2}=\omega_n/\omega_d=1/\sqrt{1-\zeta^2}$. So the response stays inside the envelope

$$
1\pm\frac{e^{-\zeta\omega_nt}}{\sqrt{1-\zeta^2}}
$$

It is certainly within ±1 % once the envelope is:

$$
\frac{e^{-\zeta\omega_nt_s}}{\sqrt{1-\zeta^2}}=0.01\quad\Rightarrow\quad t_s=\frac{\ln\!\left(100/\sqrt{1-\zeta^2}\right)}{\zeta\omega_n}
$$

For light damping $\sqrt{1-\zeta^2}\approx1$ and $\ln100=4.61$, which gives $t_s\approx4.6/(\zeta\omega_n)$. The 5 % band gives $\ln20=3.0$.

**Rise time.** There is no closed form for the 10 % and 90 % crossings. $t_r\approx1.8/\omega_n$ is a straight-line fit to the exact values for $\zeta$ around 0.5 (Franklin, Powell & Emami-Naeini, Ch. 3).

![[amc_pole_location_specs.png|620]]

Each specification is one coordinate of the pole. Overshoot is set by the angle ($\cos^{-1}\zeta$ from the negative real axis), settling time by the real part, peak time by the imaginary part, and rise time roughly by the distance $\omega_n$ from the origin. Root-locus design in [[SESA2027 B2 - Root Locus Method|B2]] is about moving the poles into the region where all four are acceptable.

### Worked example: PS1 Q3 specifications from first principles

$\omega_n=3.65$ rad/s, $\zeta=0.40$:

- $\sqrt{1-\zeta^2}=0.9165$, so $\omega_d=3.345$ rad/s and $\zeta\omega_n=1.46$ s⁻¹.
- $t_p=\pi/3.345=0.939$ s.
- $OS=e^{-0.4\pi/0.9165}=e^{-1.371}=0.254=25.4\%$.
- $t_s\approx4.6/1.46=3.15$ s (the exact envelope value is $\ln(100/0.9165)/1.46=3.21$ s).
- $t_r\approx1.8/3.65=0.493$ s (exact 10–90 %: 0.401 s).

> [!check] Numerical check (Python, the figure above)
> A simulated step gives a peak of 1.254 at 0.939 s and a 10–90 % rise time of 0.401 s. ✓ The rule-of-thumb rise time over-predicts by 23 % at $\zeta=0.4$, so quote it as approximate.

> [!info] Lecturer's conventions and the design trade-off (L1.07, ll. 922–964)
> - Give overshoot as a percentage: "whenever I ask you for the overshoot, remember I want you to express it as a percentage" (l. 943).
> - Settling time uses the 1 % band in this module ($4.6/|\sigma|$); some texts use 5 % (ll. 953–955).
> - Rise time measures speed. This is why the CubeSat project asks for it: a faster system reaches its pointing reference sooner (ll. 924–934).
> - Overshoot measures how far a tracking system "misses" before coming back. A missile or a tracking task wants it very small (ll. 944–950).
> - A client who wants the lowest $t_r$, $OS$ and $t_s$ at once is asking for a trade-off. Part B (control) is about moving these numbers (ll. 956–965).
> - In the lab, report $t_r$, $OS$ and $t_s$ for your aircraft (ll. 972–973).

> [!example] PS1 Q3: $\omega_n = 3.65$ rad/s, $\zeta = 0.40$
> $t_r = 1.8/3.65 = 0.493$ s, $t_s = 4.6/(0.4\times3.65) = 3.151$ s, and
>
> $$OS = e^{-0.4\pi/\sqrt{0.84}} = 25.4\%$$
>
> The sheet quotes 22.4%, which is what you get if you forget the square root: $e^{-0.4\pi/0.84}$. See [[SESA2027 Practice Problems 1 Solutions]].

![[amc_ps1_q3_step_annotated.png|620]]

## Lecturer emphasis and exam hints (transcripts)

> [!info] Summary of the signals in L1.07
> - Laplace transforms and partial fractions are not examined as calculations (ll. 8–12, 720–727).
> - The final value of a step response is a possible exam question (ll. 811–821).
> - The three time-domain specifications, $t_r$, $OS$ (as %) and $t_s$ (1 %), are used throughout Part B and in the lab report (ll. 943, 953, 972).
> - Further reading: Franklin, Powell & Emami-Naeini, Ch. 3 (derivation of the specifications); Cook, Ch. 5 (ll. 974–975).

> [!info] Lecturer intuition
> - Laplace is DAP3 (divide and conquer): ODE → algebra → back to time, instead of one hard step (ll. 23–37).
> - All the coefficients in the SPO step-response equation are positive for a stable aircraft ($m$, $I_{yy}$, $\zeta$, $\omega_n$), which is what makes the complex-root recipe apply (ll. 402–418).
> - Because the system is linear, the step response is the sum of a constant (the step), a decaying cosine and a decaying sine. The slide plot shows each part separately (ll. 762–803).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L1.07, l. 2 | "the Schoepier approximation" | the SPO approximation |
> | L1.07, ll. 18, 38, 47 | "math 2048", "lecture 11 format 2028", "MAT 2048" | MATH2048, Lecture 11 |
> | L1.07, l. 24 | "in a media way" | in a number of ways |
> | L1.07, l. 43 | "every hand has to be in S domain" | everything has to be in the $s$-domain |
> | L1.07, l. 45 | slide uses $j$ | $s = \sigma+i\omega$ (lecturer's correction) |
> | L1.07, l. 48 | "your function time e to the st" | $g(t)e^{-st}$ |
> | L1.07, l. 80 | "hip-side function" | Heaviside function |
> | L1.07, ll. 105–107 | a ramp plus a negative ramp simulates "continuously changing the elevator input and then going back to the value of zero" | $t\,u(t)-(t-t_1)u(t-t_1)$ is a ramp-and-hold: the rate returns to zero, the deflection does not. Returning the deflection to zero needs a second, opposite pair of ramps |
> | L1.07, ll. 82–83 | step "exactly at one" | exactly at $t = 0$ (self-corrected) |
> | L1.07, ll. 122–123 | time-shift slide "is incorrect … it should be unit step" | multiply the shifted function by the shifted unit step $u(t-a)$ |
> | L1.07, l. 196 | "infinitely narrow poles" | infinitely narrow pulse |
> | L1.07, ll. 199–213 | impulse "as the sum of two step functions" | the scaled difference of a step and a delayed step |
> | L1.07, ll. 217–224 | "a ghost" | a gust |
> | L1.07, l. 250 | "mass damping spraying system" | mass–spring–damper |
> | L1.07, ll. 280–282 | "two zeta gamma" | $2\zeta\omega_n$ |
> | L1.07, ll. 342–345 | slide equation missing $I_{yy}$ | the forcing term is $r(t)/(mI_{yy})$ |
> | L1.07, l. 500 | "on lecture 1.87" | the aircraft transfer function is derived in L1.11 (see [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#6. From state space to transfer function\|A2 §6]]) |
> | L1.07, l. 630 | "partial flagship suspension method" | partial-fraction expansion |
> | L1.07, ll. 907–910 | "the magnitude of the stress response" | the step response |
> | L1.07, l. 939 | "fugoid" | phugoid |
> | L1.07, l. 965 | "we withdrew the Laplace transform" | we went through the Laplace transform |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| Laplace transform $\mathcal L$, $s=\sigma+i\omega$ | $s=\sigma+j\omega$ in engineering texts | L1.07 slide 3 | the course uses $i$ (lecturer's correction, l. 45) |
| unit step $u(t)$ | Heaviside function $H(t)$ | L1.07 | do not confuse with the speed perturbation $u$ or the input vector $\mathbf u$ |
| transfer function $G(s)=B(s)/A(s)$ | system function, plant transfer function | L1.07 slide 9 | |
| poles / zeros | roots of the denominator / numerator, natural modes (poles) | L1.07 | poles = eigenvalues of $\mathbf A$ |
| rise time $t_r$ (10–90 %) | — (some texts use 0–100 % for underdamped systems) | L1.07 slide 16 | |
| overshoot $OS$ (%) | percent overshoot, maximum overshoot $M_p$ | L1.07 slide 16 | always as a percentage in this module |
| settling time $t_s$ (1 %) | 2 % or 5 % settling time in other texts | L1.07 slide 16 | the module uses 1 % ($4.6/\zeta\omega_n$) |
| final-value theorem | steady-state value, DC gain × step | L1.07 | valid only for a stable system |
| partial-fraction expansion | residue method, Heaviside cover-up | L1.07 slides 11–13 | |
| doublet | 1-1 input (one step up, one down), "3-2-1-1" is a related test input | L1.07 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] · Next: [[SESA2027 A5 - Frequency Response and Bode Plots]]
- Concepts: [[Laplace Transform]] · [[Transfer Function]] · [[Poles and Zeros]] · [[Step Response Specifications]]
- Maths: MATH2048 Lectures 11–13 (Laplace transforms), partial fractions
- Sensors use the same metrics: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]

## Year 1 foundation
- The SDOF equation $m\ddot x + c\dot x + kx = f$ and its characteristic equation $ms^2 + cs + k = 0$: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lecture 1.07 (Dr S. Araujo-Estrada): slides `Lecture 1.07.pdf`; transcript `Lecture 1.07 recording.txt` (speech-to-text)
- Franklin, Powell & Emami-Naeini, *Feedback Control of Dynamic Systems*, Ch. 3
- Figures: `01 - Notes/Figures/generate_amc_a4_figures.py`

## Self-study tasks

No tasks were set in L1.07. The three specifications are required in the lab report (ll. 972–973), and Franklin et al. Ch. 3 and Cook Ch. 5 were recommended for the derivations (ll. 974–975). Every task below is suggested, not lecturer-set, except that the final value of a step response was named as a possible exam question (ll. 811–821).

### Core

- [ ] Final value of a step response from $\lim_{s\to0}sX(s)$; check $r_1=K/\omega_n^2$ for the F-4C (possible exam question). → [[#3. SPO step response]]
- [ ] For $\omega_n = 3.65$ rad/s and $\zeta = 0.40$, compute $t_r$, $OS$ (%), $t_p$ and $t_s$ (1 %), then sketch the response. → [[#Worked example: PS1 Q3 specifications from first principles]]
- [ ] Say which pole coordinate controls each specification, and which way each moves if $\zeta$ rises at fixed $\omega_n$. → [[#Deriving the specifications]]
- [ ] PS1 Q3. → [[SESA2027 Practice Problems 1 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q4. Step response of a second-order system|Mock Q4]]

### Further practice

- [ ] Write a doublet of amplitude 1 and half-width $t_1$ as shifted steps and find its Laplace transform. → [[#2. Properties and standard transforms (MATH2048 L11–13 recap)]]
- [ ] Derive the normalised step response by partial fractions, then $t_p$, $OS$ and $t_s$ from it. → [[#Deriving the specifications]]
- [ ] Derive $\mathcal L\{\dot g\}=sG-g(0)$ by integration by parts. → [[#2. Properties and standard transforms (MATH2048 L11–13 recap)]]
