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
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
next_topics: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]"]
key_concepts: ["[[Characteristic Equation and Eigenvalues]]", "[[Damping Ratio and Natural Frequency]]", "[[Short Period Oscillation]]", "[[Phugoid Mode]]", "[[Routh-Hurwitz Stability Criterion]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 1 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 1.06.pdf"]
---

# SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid

> [!abstract] Summary
> The stick-fixed, unforced model $\dot{\mathbf x}=\mathbf A\mathbf x$ has solutions $\mathbf x = \mathbf x_0e^{\lambda t}$. Here the $\lambda$ are the eigenvalues, the roots of the **longitudinal stability quartic** $\det(\lambda\mathbf I-\mathbf A)=0$. The quartic factors into two quadratics $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2$:
> - the fast, well-damped **short-period oscillation (SPO)**, in $w$ and $q$ at almost constant speed;
> - the slow, lightly damped **phugoid**, an exchange of kinetic and potential energy at almost constant $\alpha$.
>
> The two-equation **SPO approximation** gives $\omega_n$ and $\zeta$ in closed form, and it matches the full 4×4 model closely.

## Key Concepts
- [[Characteristic Equation and Eigenvalues]] · [[Damping Ratio and Natural Frequency]] · [[Routh-Hurwitz Stability Criterion]]
- [[Short Period Oscillation]] · [[Phugoid Mode]]

---

## 1. General solution (L1.05)
Try $\mathbf x = \mathbf x_0e^{\lambda t}$, which gives $(\mathbf A-\lambda\mathbf I)\mathbf x_0 = 0$. A non-trivial solution needs

$$
\det(\mathbf A-\lambda\mathbf I) = 0\quad\Rightarrow\quad A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0
$$

Each root is $\lambda = \sigma\pm i\omega$:
- $\sigma$ is the growth or decay rate: $\sigma<0$ is **stable**, $\sigma>0$ is **unstable**.
- $\omega$ is the damped angular frequency (rad/s).

**[[Routh-Hurwitz Stability Criterion]]**: the aircraft is stable if all coefficients are positive **and** the Routh discriminant $R = D(BC-AD)-B^2E > 0$. In practice aircraft are stable if $E>0$ and $R>0$.

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

| | Mode 1: $\lambda^2+\lambda+2$ | Mode 2: $\lambda^2+0.0025\lambda+0.005$ |
|---|---|---|
| Roots | $-0.5\pm1.32i$ | $-0.00125\pm0.0707i$ |
| Half-life $t_{1/2}=\ln2/\vert\sigma\vert$ | 1.39 s | 554 s |
| Period $T = 2\pi/\omega$ | 4.76 s | 88.9 s |
| $\omega_n = \sqrt{\sigma^2+\omega^2}$ | 1.41 rad/s | 0.0707 rad/s |
| $\zeta = -\sigma/\omega_n$ | 0.35 | 0.018 |
| Identity | **SPO** (strongly damped) | **Phugoid** (very lightly damped) |

The slide lists $\zeta = 0.378$ and $0.035$, but the numbers in the table give 0.35 and 0.018. Use the definitions above.

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
- **Half-life** (if $\sigma<0$): $t_{1/2} = \ln 2/|\sigma|$.
- **Time to double** (if $\sigma>0$): $t_2 = \ln2/\sigma$.

See [[Damping Ratio and Natural Frequency]].

## 3. Physical description of the modes

**Types of dynamic motion**:
- (a) no overshoot (heavily damped);
- (b) oscillation dies away (damped);
- (c) oscillation grows (unstable).

### Short-period pitching oscillation ([[Short Period Oscillation]])
- A disturbance in $\alpha$ is corrected by the restoring pitching moment, but the aircraft **overshoots**, which gives a rapid pitch oscillation (period of a few seconds).
- It is **heavily damped**: the tail sees an extra angle of attack due to pitch rate, $\Delta\alpha_T\approx ql/U$.
- The **airspeed stays almost constant** because the motion is too fast for inertia to change $u$.

### Phugoid ([[Phugoid Mode]])
- A long-period exchange of kinetic and potential energy with $\alpha$ roughly constant:

$$
E = mgh+\tfrac12mV^2 \approx \text{const}
$$

  The aircraft is at high $h$ and low $V$, then low $h$ and high $V$.
- It is **lightly damped**: drag is higher in the fast (low) part, which dissipates energy and slowly damps the motion. It can even be slightly unstable, which a pilot corrects easily.

## 4. Example: McDonnell Douglas F-4C Phantom II (L1.06)
Data: $m = 17642$ kg, $I_{yy} = 165669$ kg m², $U_\infty = 178$ m/s. The dimensional state equation has

$$
\mathbf M = \begin{bmatrix}17642&0&0&0\\0&17660&0&0\\0&132&165669&0\\0&0&0&1\end{bmatrix},\qquad \mathbf A' = \begin{bmatrix}-127&81&0&-173068\\-1214&-5215&3130394&0\\277&-1770&-50798&0\\0&0&1&0\end{bmatrix}
$$

$\mathbf A = \mathbf M^{-1}\mathbf A'$ has eigenvalues:
- $\lambda_1 = -0.3690\pm1.3558i$: SPO, $\omega_n = 1.4052$ rad/s, $\zeta = 0.2626$.
- $\lambda_2 = -0.0065\pm0.0779i$: phugoid, $\omega_n = 0.0781$ rad/s, $\zeta = 0.0825$.

The eigenvector (**mode shape**) of the SPO is dominated by $w$ and $\theta$. The $u$ component is negligible ($0.0165+0.0308i$ versus $0.9993$ for $w$).

## 5. The SPO approximation (L1.06)
Because the SPO is fast:
1. $u = \dot u = 0$ (no speed change), so the $X$ equation is not needed.
2. Set $\gamma_0 = 0$, so there are no $\theta$ terms in the $Z$ or $M$ equations and the $\dot\theta$ equation is not needed.
3. Neglect $\mathring Z_{\dot w}\ll m$ and $\mathring Z_q\ll mU_\infty$.

$$
\begin{bmatrix}m&0\\-\mathring M_{\dot w}&I_{yy}\end{bmatrix}\begin{bmatrix}\dot w\\\dot q\end{bmatrix} = \begin{bmatrix}\mathring Z_w&mU_\infty\\\mathring M_w&\mathring M_q\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix}
$$

With $w=w_0e^{\lambda t}$ and $q = q_0e^{\lambda t}$:

$$
(m\lambda-\mathring Z_w)(I_{yy}\lambda-\mathring M_q)-mU_\infty(\mathring M_{\dot w}\lambda+\mathring M_w) = 0
$$

Divide by $mI_{yy}$ and compare with $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2$:

$$
\boxed{\omega_n^2 = \frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad \zeta = -\frac{m(\mathring M_q+U_\infty\mathring M_{\dot w})+\mathring Z_wI_{yy}}{2\omega_nmI_{yy}}}
$$

> [!example] F-4C check
> The approximation gives $\omega_n = 1.4115$ rad/s and $\zeta = 0.2637$. The full 4×4 model gives $1.4052$ and $0.2626$. The error is under 0.5%, so **DAP2** applies: from here on we use the simpler model.

**Interpretation**:
- Two equations and seven parameters are enough for design.
- The model relates directly to regulations: **FAR/CS-25.181** requires a heavily damped short period, and MIL-F-8785C gives flying-qualities limits on $\zeta_{sp}$ and $\omega_{sp}$.
- Sensitivity: increasing $m$ or $I_{yy}$ lowers $\omega_n$ and $\zeta$ slightly (L1.06 slide 17).
- The SPO is equivalent to a mass–spring–damper: $m\ddot x+c\dot x+kx = r(t)$. Forced responses are solved with Laplace transforms. See [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]].

> [!example] PS1 Q2: SPO approximation
> With $m=17642$, $I_{yy}=165669$, $U_\infty=356$, $\mathring M_{\dot w}=-132.47$, $\mathring Z_w=-12809.54$, $\mathring M_w=-13465.56$, $\mathring M_q=-123272.02$:
>
> $\omega_n = 5.429$ rad/s, $\zeta = 0.162$, $\lambda = -0.877\pm5.358i$, $T = 1.173$ s, $t_{1/2} = 0.790$ s.
>
> Full working in [[SESA2027 Practice Problems 1 Solutions]].

![[amc_ps1_q1_spo_pitch.png|560]]

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]] · Next: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]
- Maths: eigenvalue problems and second-order ODEs (MATH2048 Lecture 1)
- Year 3: lateral modes (roll, spiral, Dutch roll) in [[SESA3047 Advanced Aerospace Mechanics & Control]]

## Year 1 foundation
- The damped mass–spring–damper, $\omega_n$, $\zeta$ and the log decrement: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lectures 1.05–1.06; Cook (2013) Ch. 6–7; Barnard & Philpott, *Aircraft Flight*
