---
title: "SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part A: Dynamic Systems"
order: 3
tags:
  - sesa2027
  - dynamic-stability
  - short-period
  - phugoid
aliases: ["Longitudinal Modes", "SPO Approximation"]
date: 2026-09-23
status: lectured
coverage: "L1.05 (general solution, stability, modes), L1.06 (F-4C, SPO approximation)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
next_topics: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]"]
key_concepts: ["[[Characteristic Equation and Eigenvalues]]", "[[Damping Ratio and Natural Frequency]]", "[[Short Period Oscillation]]", "[[Phugoid Mode]]", "[[Routh-Hurwitz Stability Criterion]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 1 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 1.06.pdf", "02 - Sources/Lectures/Lecture 1.05 recording.txt", "02 - Sources/Lectures/Lecture 1.06 recording.txt"]
---

# SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid

> [!abstract] Summary
> The free, stick-fixed model $\dot{\mathbf x}=\mathbf A\mathbf x$ has solutions $\mathbf x_0e^{\lambda t}$, where the $\lambda$ are the roots of the longitudinal stability quartic $\det(\lambda\mathbf I-\mathbf A)=0$. The quartic factors into two quadratics: the fast, well-damped short-period oscillation in $w$ and $q$ at almost constant speed, and the slow, lightly damped phugoid, which trades kinetic and potential energy at almost constant $\alpha$. The two-equation SPO approximation gives $\omega_n$ and $\zeta$ in closed form and matches the full 4×4 model closely.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a factorised (or factorisable) quartic, a matrix to find eigenvalues of, or the dimensional derivatives, and asks for roots, stability, $\omega_n$, $\zeta$, $T$, $t_{1/2}$ or $t_2$, or which mode is which.
> - **Assumptions:** stick fixed, unforced ($\dot{\mathbf x}=\mathbf A\mathbf x$), linear about trim; for the SPO approximation also $u=0$, $\gamma_0=0$, $\mathring Z_{\dot w}\ll m$, $\mathring Z_q\ll mU_\infty$.
> - **Method:** 1. Roots of each quadratic $\lambda^2+a\lambda+b$: $\lambda=\sigma\pm i\omega$. 2. Stable if $\sigma<0$ (equivalently $\zeta>0$). 3. $\omega_n=\sqrt b=\sqrt{\sigma^2+\omega^2}$, $\zeta=a/(2\sqrt b)=-\sigma/\omega_n$. 4. $T=2\pi/\omega$; $t_{1/2}=\ln2/\lvert\sigma\rvert$ if stable, else $t_2=\ln2/\sigma$. 5. Larger $\omega_n$ = SPO, smaller = phugoid.
> - **Common mistakes:** dividing by the damped frequency $\omega$ instead of $\omega_n$ when finding $\zeta$ (the slide 14 slip); quoting a half-life for an unstable mode.
> - **Practise:** [[#Worked example: an unstable oscillatory mode]] · [[SESA2027 Mock Questions#Q3. Modes from a factorised quartic|Mock Q3]] · [[SESA2027 Practice Problems 1 Solutions]]

Disturb a trimmed aircraft and let go of the stick. Two things happen on two very different time-scales. First, within a few seconds, the nose bobs: the angle of attack overshoots, the static stability ($M_w$) pulls it back, and the tailplane's pitch damping ($M_q$) kills the bobbing within a cycle or two. The speed has no time to change. This is the short-period oscillation, and it is what you feel in turbulence.

Then, over a minute or more, the whole flight path undulates. The aircraft climbs and slows, then dives and speeds up, trading kinetic and potential energy at almost constant angle of attack. Only the small extra drag in the fast part removes energy, so this phugoid is very lightly damped and pilots correct it without noticing.

Mathematically, each mode is one complex-conjugate pair of eigenvalues of $\mathbf A$. The real part sets how fast the mode decays, the imaginary part how fast it oscillates. Because the two time-scales are so far apart, the fast mode can be studied on its own with two equations: the SPO approximation.

---

## 1. General solution (L1.05)
The course calls $\mathbf A$ the characteristic matrix: it ties the states to the aircraft's physical parameters (mass, inertia, derivatives, trim climb angle), and its eigenvalues are the modes (L1.05, ll. 44–52).

Try $\mathbf x = \mathbf x_0e^{\lambda t}$, which gives $(\mathbf A-\lambda\mathbf I)\mathbf x_0 = 0$. A non-trivial solution needs

$$
\det(\mathbf A-\lambda\mathbf I) = 0\quad\Rightarrow\quad A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0
$$

Each root is $\lambda = \sigma\pm i\omega$:
- $\sigma$ is the growth or decay rate: $\sigma<0$ is stable, $\sigma>0$ is unstable.
- $\omega$ is the damped angular frequency (rad/s).

The [[Routh-Hurwitz Stability Criterion]] says the aircraft is stable if all the coefficients are positive and the Routh discriminant $R = D(BC-AD)-B^2E$ is positive too. In practice aircraft are stable if $E>0$ and $R>0$.

> [!info] What the lecturer said you must be able to do (L1.05)
> - "If we have a negative real part … we have a stable solution. So this is very important for you to remember … It could be an exam question" (ll. 89–96).
> - "Please state what the Routh–Hurwitz stability criterion is": all coefficients positive and the discriminant positive (ll. 190–194). You do not need to memorise the formula for $R$: "if you tell me the Routh discriminant is greater than zero, I would take that as a positive answer" (ll. 196–203).
> - Given a quartic already factorised into two quadratics, find the roots, say whether each mode is stable, and give $t_{1/2}$ and $T$ (ll. 237–256).
> - Sketch the roots in the complex plane; placement matters, not precision (ll. 266–271).

To expand a 4×4 determinant quickly, go along the row or column with the most zeros (L1.05, ll. 127–144). In the example the bottom row $[0,0,1,0]$ has three zeros, so only one cofactor survives. The slides expand along the first column, which works but takes longer.

### Worked numerical example (L1.05 slides 6–10)

$$
\mathbf A = \begin{bmatrix}0&0.16&0&-9.81\\-0.125&-0.5&212&0\\0&-0.0082&-0.5&0\\0&0&1&0\end{bmatrix}
$$

Expand $\det(\lambda\mathbf I-\mathbf A)$ along the first column:

$$
\lambda[(\lambda+0.5)(\lambda+0.5)\lambda+212\times0.0082\lambda]+0.16\times0.125(\lambda+0.5)\lambda-9.81\times0.125\times0.0082\times(-1)=0
$$

$$
\lambda^4+\lambda^3+2.01\lambda^2+0.01\lambda+0.01=0\;\approx\;(\lambda^2+\lambda+2)(\lambda^2+0.0025\lambda+0.005)=0
$$

The quicker expansion, along the bottom row (the lecturer's tip below). Write

$$
\lambda\mathbf I-\mathbf A=\begin{bmatrix}\lambda&-0.16&0&9.81\\0.125&\lambda+0.5&-212&0\\0&0.0082&\lambda+0.5&0\\0&0&-1&\lambda\end{bmatrix}
$$

The bottom row $[0,0,-1,\lambda]$ leaves two cofactors. The $(4,4)$ cofactor is the top-left $3\times3$ determinant, expanded along its first column:

$$
C_{44}=\lambda\left[(\lambda+0.5)^2+212\times0.0082\right]-0.125\left[-0.16(\lambda+0.5)\right]
$$

$$
C_{44}=\lambda\left[(\lambda+0.5)^2+1.7384\right]+0.02(\lambda+0.5)
$$

The $(4,3)$ minor deletes row 4 and column 3. Its only non-zero product uses the $9.81$ in the last column:

$$
M_{43}=9.81\times\begin{vmatrix}0.125&\lambda+0.5\\0&0.0082\end{vmatrix}=9.81\times0.125\times0.0082=0.01006
$$

with cofactor $C_{43}=(-1)^{4+3}M_{43}=-0.01006$. Then

$$
\det(\lambda\mathbf I-\mathbf A)=(-1)\,C_{43}+\lambda\,C_{44}
$$

$$
=0.01006+\lambda^2\left[\lambda^2+\lambda+1.9884\right]+0.02\lambda^2+0.01\lambda
$$

$$
=\lambda^4+\lambda^3+2.0084\lambda^2+0.01\lambda+0.01006
$$

> [!check] Factorisation check
> $(\lambda^2+\lambda+2)(\lambda^2+0.0025\lambda+0.005)=\lambda^4+1.0025\lambda^3+2.0075\lambda^2+0.0100\lambda+0.0100$. Every coefficient agrees with the quartic to within 0.3 %, so the two quadratics are a good approximation. Whenever the roots are far apart, a quartic splits like this: the big coefficients belong to the fast mode, the tiny ones to the slow mode.

| | Mode 1: $\lambda^2+\lambda+2$ | Mode 2: $\lambda^2+0.0025\lambda+0.005$ |
|---|---|---|
| Roots | $-0.5\pm1.32i$ | $-0.00125\pm0.0707i$ |
| Half-life $t_{1/2}=\ln2/\vert\sigma\vert$ | 1.39 s | 554 s |
| Period $T = 2\pi/\omega$ | 4.76 s | 88.9 s |
| $\omega_n = \sqrt{\sigma^2+\omega^2}$ | 1.41 rad/s | 0.0707 rad/s |
| $\zeta = -\sigma/\omega_n$ | 0.35 | 0.018 |
| Identity | SPO (strongly damped) | Phugoid (very lightly damped) |

The slide lists $\zeta = 0.378$ and $0.035$, but the numbers in the table give 0.35 and 0.018. Use the definitions above.

> [!warning] The slide's mode-1 natural frequency is also off
> Slide 14 prints $\omega_n = 1.22$ rad/s with $\zeta = 0.378$ for mode 1, and the lecture read these out (L1.05, l. 357). For $\lambda^2+\lambda+2$ the correct values are $\omega_n = \sqrt2 = 1.414$ rad/s and $\zeta = 1/(2\sqrt2) = 0.354$. The slide's 0.378 equals $|\sigma|/\omega = 0.5/1.32$, i.e. it divides by the damped frequency instead of $\omega_n$. The lecturer made the same slip aloud in L1.06 (l. 241) and corrected himself: "No, sorry. The real part and the natural frequency" (ll. 242–243).
>
> The lecture also said the phugoid damping is "one order of magnitude smaller" and its frequency "two orders of magnitude smaller" (L1.05, ll. 369–372). With the correct values both ratios are about 20 ($0.354/0.018$ and $1.414/0.0707$). The conclusion stands: the phugoid is far slower and far more lightly damped.

The table answers the questions the lecturer asked in L1.05. Mode 1's period is longer than its half-life (4.76 s against 1.39 s), so the oscillation has mostly died away before one cycle is complete: it is well damped (ll. 257–263). Mode 2 is closer to instability, because its roots sit almost on the imaginary axis (ll. 379–386). And the modes can be identified from the eigenvalues alone: the pair with the larger magnitude is the SPO and the smaller one is the phugoid (ll. 439–441; L1.06, ll. 228–236).

Python cross-check: `np.linalg.eig(A)` gives $-0.4988\pm1.3237i$ (SPO) and $-0.0012\pm0.0709i$ (phugoid).

![[amc_s_plane_modes.png|560]]

## 2. Damping factor and natural frequency
By analogy with a mass–spring–damper, $m\ddot x+c\dot x+kx=0$, so $\lambda^2+\frac cm\lambda+\frac km=0$:

$$
\omega_n = \sqrt{k/m},\qquad \zeta = \frac{c/m}{2\omega_n},\qquad \lambda^2+2\zeta\omega_n\lambda+\omega_n^2 = 0
$$

For a quadratic $\lambda^2+a\lambda+b$: $\omega_n=\sqrt b$ and $\zeta = a/(2\sqrt b)$. From the eigenvalues:

$$
\boxed{\omega_n = \sqrt{\sigma^2+\omega^2},\qquad \zeta = -\frac{\sigma}{\omega_n},\qquad \omega = \omega_n\sqrt{1-\zeta^2}}
$$

**Time characteristics**:
- **Period**: $T = 2\pi/\omega$.
- Half-life (if $\sigma<0$): $t_{1/2} = \ln 2/|\sigma|$.
- Time to double (if $\sigma>0$): $t_2 = \ln2/\sigma$.

See [[Damping Ratio and Natural Frequency]].

### From the roots to the natural frequency and damping ratio
This step was set as a task: "I will let for you to expand this solution, so to get from this to this in your own time" (L1.05, l. 351). Assume $0<\zeta<1$ (an oscillatory mode). Solve $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2 = 0$ with the quadratic formula:

$$
\lambda = \frac{-2\zeta\omega_n\pm\sqrt{4\zeta^2\omega_n^2-4\omega_n^2}}{2}
$$

$$
\lambda = -\zeta\omega_n\pm\omega_n\sqrt{\zeta^2-1}
$$

$$
\lambda = -\zeta\omega_n\pm i\,\omega_n\sqrt{1-\zeta^2}\qquad(\zeta<1)
$$

Compare with $\lambda = \sigma\pm i\omega$:

$$
\sigma = -\zeta\omega_n,\qquad \omega = \omega_n\sqrt{1-\zeta^2}
$$

Square and add:

$$
\sigma^2+\omega^2 = \zeta^2\omega_n^2+\omega_n^2(1-\zeta^2)
$$

$$
\sigma^2+\omega^2 = \omega_n^2
$$

$$
\omega_n = \sqrt{\sigma^2+\omega^2}
$$

Then from $\sigma = -\zeta\omega_n$:

$$
\zeta = -\frac{\sigma}{\omega_n}
$$

So $\omega_n$ is the distance of the root from the origin, and $\zeta$ is the cosine of the angle between the root and the negative real axis.

Since $\omega_n>0$, $\zeta>0$ exactly when $\sigma<0$, so the sign of the damping ratio is the stability test. The lecturer: "the only way you can get a damping factor that is positive is if your real part is negative … That's an important question that I could ask … in the quiz or in the exam" (L1.05, ll. 344–350).

> [!info] Unstable roots: half-life does not exist (L1.06, ll. 269–299)
> If $\sigma>0$ the amplitude doubles instead of halving. "If I ask you, what is the half-life? You say, the half-life doesn't exist because the system is unstable" (ll. 285–289). If the question asks for the half-life *or the time to double*, give $t_2 = \ln2/\sigma$. The period $T = 2\pi/\omega$ is computed the same way whether or not the mode is stable.

### Worked example: an unstable oscillatory mode

*(Suggested, not lecturer-set; the self-study task below.)* A mode has roots $\lambda=+0.05\pm1.2i$.

- Stability: $\sigma=+0.05>0$, so the mode is unstable.
- Natural frequency: $\omega_n=\sqrt{0.05^2+1.2^2}=1.201$ rad/s.
- Damping ratio: $\zeta=-0.05/1.201=-0.042$. Negative, as it must be when $\sigma>0$.
- Period: $T=2\pi/1.2=5.24$ s.
- Time to double: $t_2=\ln2/0.05=13.9$ s. A half-life does not exist.
- The quadratic is $\lambda^2-0.1\lambda+1.4425$: a negative middle coefficient, so Routh–Hurwitz (all coefficients positive) fails too.

> [!check] Numerical check
> `np.roots([1, -0.1, 1.4425])` returns $0.05\pm1.2i$. ✓ The amplitude doubles about every $13.9/5.24=2.65$ cycles: slow enough for a pilot to catch, which is why a slightly unstable phugoid is tolerated.

## 3. Physical description of the modes

**Types of dynamic motion**:
- (a) no overshoot (heavily damped);
- (b) oscillation dies away (damped);
- (c) oscillation grows (unstable).

### Short-period pitching oscillation ([[Short Period Oscillation]])
- A disturbance in $\alpha$ is corrected by the restoring pitching moment, but the aircraft overshoots, which gives a rapid pitch oscillation (period of a few seconds).
- It is heavily damped: the tail sees an extra angle of attack due to pitch rate, $\Delta\alpha_T\approx ql/U$.
- The airspeed stays almost constant because the motion is too fast for inertia to change $u$.

![[amc_f4c_spo_time_history.png|720]]

*F-4C full 4×4 model (L1.06 matrices), free response to $w_0=5$ m/s. The oscillation in $\alpha$, $\theta$ and $q$ has almost gone after one period. The slow drift in $u$ and $\theta$ that remains is the phugoid starting, which the SPO approximation deliberately ignores.*

### Phugoid ([[Phugoid Mode]])
- A long-period exchange of kinetic and potential energy with $\alpha$ roughly constant:

$$
E = mgh+\tfrac12mV^2 \approx \text{const}
$$

  The aircraft is at high $h$ and low $V$, then low $h$ and high $V$.
- It is lightly damped: drag is higher in the fast (low) part, which dissipates energy and slowly damps the motion. It can even be slightly unstable, which a pilot corrects easily.

![[amc_phugoid_flight_path.png|820]]

![[amc_f4c_phugoid_time_history.png|720]]

*F-4C full model, free response to $u_0=10$ m/s. Speed and pitch attitude swing with a period of about 81 s while $\alpha$ hardly moves, so $\theta\approx\gamma$: the nose follows the flight path. The brief wiggle in $\alpha$ in the first few seconds is the short-period mode, excited because the initial condition is not a pure phugoid shape.*

Which mode a disturbance excites depends on its frequency, as with resonance in a mass–spring–damper (L1.05, ll. 413–431). A short, sharp disturbance such as turbulence or a gust excites the SPO: "every single time you feel turbulence in an aircraft, that's exciting the short period". A slow change, such as a gradual change in wind, excites the phugoid, which is usually too slow to notice (88.9 s in the example). Both are demonstrated in the summer Cranfield flight lab.

> [!warning] Phugoid speed never reaches zero
> The lecture describes the phugoid as reaching "a maximum point where your velocity is zero" (L1.05, ll. 486–487). That is a slip. At the top of each cycle the speed is a minimum, not zero, and the angle of attack stays roughly constant throughout (l. 489). The lift changes because the speed changes, not because $\alpha$ changes (ll. 491–492).

There are two modes longitudinally but three laterally because complex roots of a real polynomial come in conjugate pairs (L1.06, ll. 6–20). The longitudinal quartic gives two complex pairs, so two oscillatory modes. The lateral quartic gives one complex pair (Dutch roll) and two separate real roots (spiral and roll subsidence), so three modes. Lateral dynamics come in [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]].

## 4. Example: McDonnell Douglas F-4C Phantom II (L1.06)
Data: $m = 17642$ kg, $I_{yy} = 165669$ kg m², $U_\infty = 178$ m/s. The dimensional state equation has

$$
\mathbf M = \begin{bmatrix}17642&0&0&0\\0&17660&0&0\\0&132&165669&0\\0&0&0&1\end{bmatrix},\qquad \mathbf A' = \begin{bmatrix}-127&81&0&-173068\\-1214&-5215&3130394&0\\277&-1770&-50798&0\\0&0&1&0\end{bmatrix}
$$

$\mathbf A = \mathbf M^{-1}\mathbf A'$ has eigenvalues:
- $\lambda_1 = -0.3690\pm1.3558i$: SPO, $\omega_n = 1.4052$ rad/s, $\zeta = 0.2626$.
- $\lambda_2 = -0.0065\pm0.0779i$: phugoid, $\omega_n = 0.0781$ rad/s, $\zeta = 0.0825$.

The eigenvector (mode shape) of the SPO is dominated by $w$ and $\theta$. The $u$ component is negligible ($0.0165+0.0308i$ versus $0.9993$ for $w$).

> [!info] F-4C: what the exam will and will not ask (L1.06)
> - **Not examined**: assembling $\mathbf M$ and $\mathbf A'$ from the data tables. "Are you going to expect us to calculate these matrix in an exam? No … I'm going to give you some values, and then I'm going to ask you to do some simplifications" (ll. 128–130).
> - **Possible exam/quiz question**: convert a dimensionless derivative to dimensional form with the table in [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#Dimensional vs dimensionless derivatives|A2]], and state its units (ll. 108–117). For example $\mathring M_w = M_w\cdot\tfrac12\rho U_\infty S\bar c$ has units $\text{kg m}^{-3}\cdot\text{m s}^{-1}\cdot\text{m}^2\cdot\text{m} = \text{kg m s}^{-1} = \text{N s}$.
> - **Possible exam question**: get $\alpha$ from an eigenvector. Index 1 of the state vector is $w$ (Python counts from 0), so $\alpha_0\approx w_0/U_\infty$. Index 3 is $\theta_0$ directly (ll. 174–192). The flight-path angle follows from $\gamma = \theta-\alpha$ (l. 168).
> - **Sketching the SPO response**: an oscillation in $q$, $\theta$ and $\alpha$ that decays in a few seconds (ll. 158–169). Use radians in the calculation and convert to degrees only for display (ll. 194–202).

## 5. The SPO approximation (L1.06)
Because the SPO is fast:
1. $u = \dot u = 0$ (no speed change), so the $X$ equation is not needed.
2. Set $\gamma_0 = 0$, so there are no $\theta$ terms in the $Z$ or $M$ equations and the $\dot\theta$ equation is not needed.
3. Neglect $\mathring Z_{\dot w}\ll m$ and $\mathring Z_q\ll mU_\infty$.

$$
\begin{bmatrix}m&0\\-\mathring M_{\dot w}&I_{yy}\end{bmatrix}\begin{bmatrix}\dot w\\\dot q\end{bmatrix} = \begin{bmatrix}\mathring Z_w&mU_\infty\\\mathring M_w&\mathring M_q\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix}
$$

With $w=w_0e^{\lambda t}$ and $q = q_0e^{\lambda t}$, every $\dot{}$ becomes a factor $\lambda$. Move everything to one side:

$$
\begin{bmatrix}m\lambda-\mathring Z_w&-mU_\infty\\-\mathring M_{\dot w}\lambda-\mathring M_w&I_{yy}\lambda-\mathring M_q\end{bmatrix}\begin{bmatrix}w_0\\q_0\end{bmatrix}=\mathbf 0
$$

A non-zero $(w_0,q_0)$ needs the determinant to vanish:

$$
(m\lambda-\mathring Z_w)(I_{yy}\lambda-\mathring M_q)-(-mU_\infty)(-\mathring M_{\dot w}\lambda-\mathring M_w) = 0
$$

$$
(m\lambda-\mathring Z_w)(I_{yy}\lambda-\mathring M_q)-mU_\infty(\mathring M_{\dot w}\lambda+\mathring M_w) = 0
$$

Multiply out the first product:

$$
mI_{yy}\lambda^2-m\mathring M_q\lambda-\mathring Z_wI_{yy}\lambda+\mathring Z_w\mathring M_q-mU_\infty\mathring M_{\dot w}\lambda-mU_\infty\mathring M_w=0
$$

Collect powers of $\lambda$:

$$
mI_{yy}\lambda^2-\left[m(\mathring M_q+U_\infty\mathring M_{\dot w})+\mathring Z_wI_{yy}\right]\lambda+\left(\mathring M_q\mathring Z_w-mU_\infty\mathring M_w\right)=0
$$

Divide by $mI_{yy}$:

$$
\lambda^2-\left[\frac{\mathring M_q+U_\infty\mathring M_{\dot w}}{I_{yy}}+\frac{\mathring Z_w}{m}\right]\lambda+\frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}}=0
$$

Compare with $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2$: the constant term is $\omega_n^2$ and the middle coefficient is $2\zeta\omega_n$:

$$
\boxed{\omega_n^2 = \frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad \zeta = -\frac{m(\mathring M_q+U_\infty\mathring M_{\dot w})+\mathring Z_wI_{yy}}{2\omega_nmI_{yy}}}
$$

> [!example] F-4C check
> The approximation gives $\omega_n = 1.4115$ rad/s and $\zeta = 0.2637$. The full 4×4 model gives $1.4052$ and $0.2626$. The error is under 0.5%, so DAP2 applies: from here on we use the simpler model.
>
> The numbers ($m=17\,642$ kg, $I_{yy}=165\,669$ kg m², $U_\infty=178$ m/s, $\mathring Z_w=-5215.44$, $\mathring M_w=-1770.07$, $\mathring M_q=-50\,798$, $\mathring M_{\dot w}=-132.47$):
>
> $$\omega_n^2=\frac{(-50\,798)(-5215.44)-17\,642\times178\times(-1770.07)}{17\,642\times165\,669}=\frac{2.649\times10^8+5.558\times10^9}{2.923\times10^9}=1.9925$$
>
> $$2\zeta\omega_n=\frac{50\,798+178\times132.47}{165\,669}+\frac{5215.44}{17\,642}=0.4490+0.2956=0.7446$$
>
> so $\omega_n=1.4115$ rad/s and $\zeta=0.7446/(2\times1.4115)=0.2638$ (the slide's 0.2637 is a rounding difference). The two terms of $2\zeta\omega_n$, $-0.2956$ and $-0.4490$, are the diagonal entries of the PS2 Q3 matrix: that sheet uses the F-4C SPO, see the warning in [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#Worked example: SPO state space to transfer function (PS2 Q3)|A2]].

**Interpretation**:
- Two equations and seven parameters are enough for design.
- The model relates directly to regulations: FAR/CS-25.181 requires a heavily damped short period, and MIL-F-8785C gives flying-qualities limits on $\zeta_{sp}$ and $\omega_{sp}$.
- Sensitivity (L1.06 slide 17 and ll. 417–430): mass mainly changes $\zeta$; pitch inertia mainly changes $\omega_n$. Increasing either lowers both, but by very different amounts (see the check below). So if you want to move $\omega_n$ or $\zeta$, "you know where to look" (l. 430).
- The SPO is equivalent to a mass–spring–damper: $m\ddot x+c\dot x+kx = r(t)$. Forced responses are solved with Laplace transforms. See [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]].

> [!check] F-4C sensitivity to $\pm10\%$ mass and inertia (SPO approximation, computed)
> Baseline: $\omega_n = 1.4115$ rad/s, $\zeta = 0.2637$.
>
> | Change | $\omega_n$ | $\zeta$ |
> |---|---|---|
> | $m\times1.1$ | 1.4086 (−0.2 %) | 0.2548 (−3.4 %) |
> | $m\times0.9$ | 1.4151 (+0.3 %) | 0.2747 (+4.1 %) |
> | $I_{yy}\times1.1$ | 1.3459 (−4.7 %) | 0.2615 (−0.9 %) |
> | $I_{yy}\times0.9$ | 1.4879 (+5.4 %) | 0.2670 (+1.2 %) |
>
> Why: in $\omega_n^2 = \mathring M_q\mathring Z_w/(mI_{yy})-U_\infty\mathring M_w/I_{yy}$ the second term is about 95 % of the total and does not contain $m$, so $\omega_n\propto1/\sqrt{I_{yy}}$ almost exactly. In $2\zeta\omega_n = -(\mathring M_q+U_\infty\mathring M_{\dot w})/I_{yy}-\mathring Z_w/m$ the mass term is about 40 % of the total, so $m$ moves $\zeta$.

How much SPO damping is wanted depends on the aircraft (L1.06, ll. 44–66). Airliners are heavily damped for comfort, which the lab's Boeing 747 data should confirm. Fighters from the 1920s to the 1950s were stable but lightly damped so they could change attitude quickly, since heavy damping feels sluggish. From the 1980s computers stabilise the aircraft, so fighters are designed marginally stable or unstable; the tailless B-2 is unstable, with redundant flight computers voting on the control action. The regulations follow the same logic: CS-25/FAR-25 require a heavily damped SPO but allow a lightly damped phugoid, and MIL-F-8785C sets flying-quality limits on $\zeta_{sp}$ (ll. 408–416).

> [!example] PS1 Q2: SPO approximation
> With $m=17642$, $I_{yy}=165669$, $U_\infty=356$, $\mathring M_{\dot w}=-132.47$, $\mathring Z_w=-12809.54$, $\mathring M_w=-13465.56$, $\mathring M_q=-123272.02$:
>
> $\omega_n = 5.429$ rad/s, $\zeta = 0.162$, $\lambda = -0.877\pm5.358i$, $T = 1.173$ s, $t_{1/2} = 0.790$ s.
>
> Full working in [[SESA2027 Practice Problems 1 Solutions]].

![[amc_ps1_q1_spo_pitch.png|560]]

## Lecturer emphasis and exam hints (transcripts)

> [!info] Exam and quiz signals (all quoted in context above)
> - Stability from the sign of the real part (L1.05, l. 96); state Routh–Hurwitz in words (ll. 190–203).
> - Factorised quartic → roots, stability, $t_{1/2}$, $T$, complex-plane sketch (L1.05, ll. 237–271).
> - $\zeta>0\Leftrightarrow\sigma<0$ (L1.05, l. 350).
> - Quiz format: given a matrix, compute eigenvalues and say which pair is the SPO and which the phugoid (L1.05, ll. 434–441). The larger-magnitude pair is the SPO, the smaller the phugoid.
> - Size of hand calculations: "for the problems that we're going to be looking at, we're going to be dealing with 2 by 2s" (L1.05, ll. 167–168).
> - A Python Jupyter notebook for the eigenvalue calculations was promised for self-study (L1.05, l. 442).
> - Dimensional conversion and units of a derivative (L1.06, ll. 108–117); $\alpha$ from an eigenvector (ll. 187–190); half-life vs time to double (ll. 285–291).
> - Given all parameters, "please give me the short period approximation": use the two closed-form results, not the full matrix (L1.06, ll. 368–371).
> - The mass/inertia sensitivity has been given as an example, so "in the exam, I might ask something a bit more complicated" (L1.06, l. 431).
> - The quiz is open book: "you'll have a chance to look at your lecture notes, at the books" (L1.06, l. 118).
> - Lab report: compare your simulated aircraft with CS-25/FAR-25 and MIL-F-8785C (L1.06, ll. 414–416).

> [!info] Lecturer intuition
> - "Simplify, simplify, simplify" is DAP3 at work: the quartic factors into two quadratics, so each mode can be studied on its own (L1.05, ll. 216–230).
> - "Hey, I'm a designer, I haven't built anything, please verify": linear-model stability predictions are approximations and must be checked (L1.05, ll. 387–396).
> - With the SPO approximation, two equations and seven parameters reproduce the 4×4 result to within 0.5 % (L1.06, ll. 343–381).
> - The constant-mass and flat-Earth assumptions still hold to better than 1 % over the simulation times used (L1.06, ll. 383–395).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L1.05, l. 25 | "model analysis" | modal analysis |
> | L1.05, ll. 33, 189 | "agent values", "root Horwitz" | eigenvalues, Routh–Hurwitz |
> | L1.05, l. 59 | "e to the power of gamma t" | $e^{\lambda t}$ |
> | L1.05, ll. 164–166 | "a 4 by 4 polynomial", "a 2 by 2" | a 4th-order (quartic) polynomial; 2nd order |
> | L1.05, l. 182 | "r equals d multiplied by c minus d a minus b to e" | $R = D(BC-AD)-B^2E$ |
> | L1.05, l. 265 | "MAT2028" | MATH2048 |
> | L1.05, l. 282 | "in a physical system, you always have complex roots" | complex roots of a physical (real) system always come in conjugate pairs; real roots are also possible |
> | L1.05, l. 357 | "1.22 radians per second … 0.378" (read from the slide) | $\omega_n = 1.414$ rad/s, $\zeta = 0.354$ |
> | L1.05, l. 359 | "this factor is actually on the damp" | underdamped |
> | L1.05, ll. 401, 409 | "fugoid", "Hugo" | phugoid |
> | L1.05, l. 422 | "a high or low frequency perturbation" | a low-frequency perturbation excites the phugoid |
> | L1.05, ll. 486–487 | "a maximum point where your velocity is zero" | a point of minimum speed |
> | L1.05, ll. 509–510 | the phugoid in the example is "marginal stable. Some people would call it also unstable" | its real part is negative, so it is stable but very lightly damped. "Marginally stable" strictly means $\sigma = 0$; only $\sigma>0$ is unstable. Some aircraft do have slightly unstable phugoids, but this one does not |
> | L1.05, l. 513 | "u and k-ta" | $u$ and $\theta$ |
> | L1.06, l. 8 | "the dodge roll, … the divergence in roll" | Dutch roll, … roll subsidence |
> | L1.06, l. 10 | "two pairs of routes" | roots (throughout) |
> | L1.06, l. 74 | "the Earth 4C" | the F-4C |
> | L1.06, l. 76 | "Heathley, 1972" | Heffley (NASA report), as cited in Cook |
> | L1.06, ll. 149–150 | "the real part … describes most of the amplitude or the frequency … a large part means a high value of frequency" | the magnitude $\vert\lambda\vert = \omega_n$ sets the frequency; the real part sets the decay rate. For these modes both are larger for the SPO, so the identification still works |
> | L1.06, l. 151 | "the fugitive" | the phugoid |
> | L1.06, l. 183 | "the tangent of w divided by the free strain velocity" | $\alpha = \tan^{-1}(w/U_\infty)\approx w/U_\infty$ |
> | L1.06, l. 197 | "q and theta are going to be in radians per second" | $q$ in rad/s, $\theta$ in rad |
> | L1.06, l. 241 | $\zeta$ is "the ratio between the real part and the imaginary part" | $\zeta = -\sigma/\omega_n$ (self-corrected, l. 243) |
> | L1.06, l. 252 | "an on the dam fugoid" | an underdamped phugoid |
> | L1.06, ll. 332 | "set W dot and set Q" | $\mathring Z_{\dot w}$ and $\mathring Z_q$ |
> | L1.06, ll. 401–403 | "linear time-environment systems" | linear time-invariant (LTI) |
> | L1.06, ll. 409, 413 | "ESA-CS-25", "MIL-F-87", "MIL-F-87-85C" | EASA CS-25, MIL-F-8785C |
> | L1.06, l. 444 | "the Schroppier oscillation" | the short-period oscillation |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| longitudinal stability quartic | characteristic equation, $\det(\lambda\mathbf I-\mathbf A)=0$ | L1.05 slides 4–6 | |
| short-period oscillation (SPO) | short-period mode, short-period pitching oscillation, $\alpha$-mode | L1.05, L1.06 | subscripts $sp$ or $s$ ($\omega_{sp}$, $\zeta_s$) |
| phugoid | long-period mode, $p$ subscript ($\omega_p$, $\zeta_p$) | L1.05, L1.06 | from Lanchester's "phugoid", a misreading of the Greek for "flight" |
| damping factor / damping ratio $\zeta$ | damping coefficient (loosely) | L1.05 slide 12 | the course says "damping factor"; strictly $\zeta\omega_n$ is the damping factor and $\zeta$ the ratio |
| natural frequency $\omega_n$ | undamped natural frequency | L1.05 | |
| damped frequency $\omega$ (imaginary part) | $\omega_d$, damped natural frequency | L1.05 | |
| half-life $t_{1/2}$, time to double $t_2$ | time to half amplitude, time to double amplitude | L1.05, L1.06 | |
| Routh discriminant $R$ | Routh–Hurwitz test function | L1.05 slide 5 | |
| mode shape | eigenvector | L1.06 | read relative magnitudes, not absolute values |
| SPO approximation | short-period approximation, two-degree-of-freedom (α–q) approximation | L1.06 slides 14–17 | |
| flying qualities limits | handling-qualities requirements (MIL-F-8785C, CS-25/FAR-25) | L1.06 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]] · Next: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]
- Concepts: [[Characteristic Equation and Eigenvalues]] · [[Damping Ratio and Natural Frequency]] · [[Routh-Hurwitz Stability Criterion]] · [[Short Period Oscillation]] · [[Phugoid Mode]]
- Maths: eigenvalue problems and second-order ODEs (MATH2048 Lecture 1)
- Year 3: lateral modes (roll, spiral, Dutch roll) in [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]

## Year 1 foundation
- The damped mass–spring–damper, $\omega_n$, $\zeta$ and the log decrement: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lectures 1.05–1.06 (Dr S. Araujo-Estrada): slides `Lecture 1.05.pdf`, `Lecture 1.06.pdf`
- Transcripts (speech-to-text): `Lecture 1.05 recording.txt`, `Lecture 1.06 recording.txt`
- Cook (2013) Ch. 6–7; Barnard & Philpott, *Aircraft Flight*
- Figures: `01 - Notes/Figures/generate_amc_a3_figures.py` (F-4C time histories use the L1.06 $\mathbf M$ and $\mathbf A'$)

## Self-study tasks

Three tasks were set in L1.05–L1.06 (marked lecturer-set below, with transcript lines). The rest are suggested. The quiz is open book (L1.06, l. 118).

### Core

- [ ] Lecturer-set (L1.05, l. 351): starting from $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2 = 0$, show $\omega_n = \sqrt{\sigma^2+\omega^2}$ and $\zeta = -\sigma/\omega_n$. → [[#From the roots to the natural frequency and damping ratio]]
- [ ] Lecturer-set (L1.06, ll. 115–117): do the dimensional analysis of the dimensional derivatives, e.g. show $\mathring M_w$ is in N s. → [[#4. Example: McDonnell Douglas F-4C Phantom II (L1.06)]] and [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#Dimensional vs dimensionless derivatives|A2 table]]
- [ ] Lecturer-set (L1.06, ll. 372–374): from the F-4C data, reproduce $\omega_n\approx1.4$ rad/s and $\zeta\approx0.26$ with the SPO approximation. → [[#5. The SPO approximation (L1.06)]]
- [ ] Redo the L1.05 mode table and confirm $\omega_n = 1.414$, $\zeta = 0.354$ for mode 1 (suggested). → [[#Worked numerical example (L1.05 slides 6–10)]]
- [ ] PS1 Q1–Q2. → [[SESA2027 Practice Problems 1 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q3. Modes from a factorised quartic|Mock Q3]]

### Further practice

- [ ] For roots $+0.05\pm1.2i$, give $T$ and $t_2$, and say why $t_{1/2}$ does not exist (suggested). → [[#Worked example: an unstable oscillatory mode]]
- [ ] Expand the L1.05 determinant along the bottom row and check the quartic (suggested). → [[#Worked numerical example (L1.05 slides 6–10)]]
- [ ] Derive the SPO characteristic equation from the 2×2 matrix form, then the closed-form $\omega_n$ and $\zeta$ (suggested). → [[#5. The SPO approximation (L1.06)]]
- [ ] Explain from the figures why $u$ is negligible in the SPO and $\alpha$ is nearly constant in the phugoid (suggested). → [[#3. Physical description of the modes]]
