---
title: "SESA3047 Chapter 6 Practice Problems - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: tutorial
subtype: handout-practice-problems
lecturer_set: true
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
tags: [sesa3047, tutorial-solutions, flight-dynamics, eigenvectors, modes, spo, phugoid, lateral-dynamics]
sheet: "Chapter 6 §6.10 Practice problems (Dr Sean Symon)"
theory_notes: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA3047 6.2 - Phugoid Approximation]]", "[[SESA3047 6.3 - Lateral Modes and their Approximations]]"]
parent: ["[[SESA3047 Advanced Aerospace Mechanics & Control Hub]]"]
status: complete
coverage: "All five §6.10 problems: 1–3 (longitudinal) here, 4–5 (lateral) in 6.3 §12; not discussed in the lectures; no answer key issued"
date: 2026-11-19
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# SESA3047 Chapter 6 Practice Problems - Solutions

> [!info] About this sheet
> The five problems are §6.10 of the Chapter 6 handout (p. 14). No answer key has been issued, so these are my worked solutions, with every number checked numerically (`generate_amc_ch6_practice_figures.py --check` for problems 1–3, `generate_amc_ch6b_figures.py --check` for 4–5). Problems 1 and 2 use the numerical longitudinal matrix of Eq. 6.4 ($U_\infty=212$ m/s), problem 3 the F-4C of Table 6.1. Problems 4 and 5 are lateral and are solved in [[SESA3047 6.3 - Lateral Modes and their Approximations#12. Practice problems 4 and 5 (6.10)|6.3 §12]].

The tool behind all three longitudinal problems is the modal solution of [[SESA3047 5.4 - Time-Domain Solution and Stability|5.4]] and [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#5. Starting the system on an eigenvector (6.19–6.21)|6.1 §5]]: any initial state splits into eigenvector components,

$$
\mathbf x_0=\sum_k c_k\mathbf v_k,\qquad\mathbf c=\mathbf V^{-1}\mathbf x_0,\qquad\mathbf x(t)=\sum_kc_ke^{\lambda_kt}\mathbf v_k ,
$$

and each mode is excited in proportion to its share of $\mathbf x_0$. For Eq. 6.4 the eigenvalues are $-0.4988\pm1.3237j$ (SPO) and $-0.00125\pm0.0709j$ (phugoid).

## Problem 1. How much of each mode a pitch disturbance excites

> An aircraft is disturbed from trim with an initial pitch angle of $2^\circ$, while $u=w=q=0$. Use the longitudinal matrix in Eq. 6.4 to determine how much of each longitudinal mode is excited, find accompanying values of $u,w,q$ that eliminate the phugoid, and explain why the same initial pitch angle can produce different motion.

### Splitting the initial condition

The initial state is $\mathbf x_0=[0,\ 0,\ 0,\ 0.03491]^T$ ($2^\circ=0.03491$ rad). Solving $\mathbf V\mathbf c=\mathbf x_0$ and adding each conjugate pair gives two real vectors, one per mode, which sum to $\mathbf x_0$:

| Component of $\mathbf x_0$ | $u$ (m/s) | $w$ (m/s) | $q$ (rad/s) | $\theta$ (rad) |
|---|---|---|---|---|
| SPO pair | $0.0015$ | $-0.0161$ | $-0.00009$ | $-0.00004$ |
| phugoid pair | $-0.0015$ | $0.0161$ | $0.00009$ | $0.03495$ |
| sum | 0 | 0 | 0 | 0.03491 |

Almost all of the $2^\circ$ is phugoid: its share of $\theta$ is $2.002^\circ$, the SPO's $-0.002^\circ$. The SPO is excited only weakly, and only to cancel the small $w$ and $q$ that the phugoid component carries, so that the sum has $w=q=0$ as specified.

The physics explains why. With $w=0$ the angle of attack has not changed ($\alpha\approx w/U_\infty=0$), so pitching the nose up by $2^\circ$ has tilted the flight path by $\gamma=\theta-\alpha=2^\circ$: the aircraft is climbing at trim speed. A change of flight path at constant angle of attack is the phugoid's kind of motion, an exchange of speed and height ([[SESA3047 6.2 - Phugoid Approximation#1. The phugoid as an exchange of energy (Fig. 6.3)|6.2 §1]]). The SPO is a change of angle of attack, and there is almost none here.

![[amc_ch6p_problem1_responses.png|900]]

### A start with no phugoid

To excite the SPO alone, $\mathbf x_0$ must lie in the real plane spanned by the SPO eigenvector pair, $\mathbf x_0=a\,\mathrm{Re}\,\mathbf v_1+b\,\mathrm{Im}\,\mathbf v_1$, so that $c_3=c_4=0$. Fixing $\theta=2^\circ$ is one condition on the two unknowns $a$, $b$, so there is a one-parameter family of such starts. Adding $q=0$ picks one:

$$
u=-0.170\ \text{m/s},\qquad w=8.518\ \text{m/s},\qquad q=0,\qquad\theta=2^\circ .
$$

Now $\alpha\approx w/U_\infty=8.518/212=0.0402$ rad $=2.30^\circ$, so the nose and the angle of attack rise together and the flight path barely moves ($\gamma=\theta-\alpha=-0.30^\circ$). The motion is the SPO alone: a well-damped pitch oscillation that is over in about 10 s (right panel), with no slow speed–height exchange afterwards. The ratio of $w$ to $\theta$ is set by the SPO eigenvector, in which $\theta$ lags $w$ by about $21^\circ$, so the two rise and fall nearly together.

### Why the same pitch angle gives different motion

$\theta$ is one of four states. The motion is decided by the whole state vector, and the two starts differ in $w$, that is, in whether the nose rose relative to the flight path (an angle-of-attack disturbance, SPO) or the flight path rose with the nose (a flight-path disturbance, phugoid). The two starts project onto the eigenvectors differently, so they excite the modes in different proportions.

## Problem 2. Changing the phase of an SPO start

> Let $\mathbf v$ be an SPO eigenvector of the matrix in Eq. 6.4. Construct $\mathbf x_0(\psi)=\mathrm{Re}\big(e^{j\psi}\mathbf v\big)$, plot the responses for $\psi=0,\pi/4,\pi/2$, and determine which properties of the motion change and which remain unchanged.

### The responses

With $\mathbf v$ normalised to unit length and its $w$ entry real, the three starts are

| $\psi$ | $u$ (m/s) | $w$ (m/s) | $q$ (rad/s) | $\theta$ (rad) |
|---|---|---|---|---|
| $0$ | $-0.0198$ | $0.9964$ | $-0.00001$ | $0.00408$ |
| $\pi/4$ | $0.0445$ | $0.7045$ | $-0.00437$ | $0.00397$ |
| $\pi/2$ | $0.0827$ | $0$ | $-0.00617$ | $0.00153$ |

Because $\mathrm{Re}(e^{j\psi}\mathbf v)$ is a combination of $\mathrm{Re}\,\mathbf v$ and $\mathrm{Im}\,\mathbf v$, every start lies in the SPO plane and excites the SPO alone. Its response is

$$
\mathbf x(t)=\mathrm{Re}\big(e^{j\psi}\mathbf v\,e^{\lambda t}\big),\qquad\lambda=\sigma+j\omega=-0.4988+1.3237j .
$$

![[amc_ch6p_problem2_phase.png|900]]

### What changes and what does not

Write $e^{j\psi}$ in terms of $e^{\lambda t}$. Since $\lambda\,\psi/\omega=\sigma\psi/\omega+j\psi$,

$$
e^{j\psi}=e^{\lambda\psi/\omega}\,e^{-\sigma\psi/\omega}.
$$

Substitute into the response:

$$
\mathbf x_\psi(t)=e^{-\sigma\psi/\omega}\,\mathrm{Re}\big(\mathbf v\,e^{\lambda(t+\psi/\omega)}\big)=e^{-\sigma\psi/\omega}\,\mathbf x_0(t+\psi/\omega).
$$

So changing $\psi$ is the same motion seen from a different starting point in its cycle, $\psi/\omega$ seconds later, and rescaled by $e^{-\sigma\psi/\omega}$ to keep the start the same size as the eigenvector. For $\psi=\pi/2$ the shift is $1.187$ s and the factor $1.807$.

Unchanged, therefore: the frequency $\omega=1.324$ rad/s and period 4.75 s, the decay rate $\sigma$ and half-life 1.39 s, so $\omega_n=1.415$ rad/s and $\zeta=0.353$; and the mode shape, meaning the ratios of the state amplitudes and the phase differences between states (for example $\theta$ always lags $q$ by $90^\circ+\arcsin\zeta=110.6^\circ$). Changed: the initial values of each state, which state is at its peak when the motion starts ($w$ for $\psi=0$; $w=0$ and $q$ at its largest magnitude for $\psi=\pi/2$), and therefore the overall amplitude and timing of the curves on the plot. A complex eigenvector's overall phase is a free choice, and this is what that freedom looks like in the time domain.

## Problem 3. Speed derivatives and the separation of the modes

> Starting with the F-4C model, multiply both dimensional speed derivatives $\mathring X_u$ and $\mathring Z_u$ by a parameter $k$, leaving all other quantities fixed. Track the full-system eigenvalues as $k$ increases from 0 to 5, then compare the SPO eigenvalues with those predicted by the reduced short-period model.

### The eigenvalue tracks

![[amc_ch6p_problem3_eigenvalues.png|900]]

| $k$ | SPO (full model) | Phugoid (full model) | Phugoid $\omega_n$, $\zeta$ | Eq. 6.38 $\omega_n$ |
|---|---|---|---|---|
| 0 | $-0.3685\pm1.3569j$ | $-0.00335\pm0.0494j$ | 0.0495, 0.068 | 0.0505 |
| 1 | $-0.3690\pm1.3558j$ | $-0.00645\pm0.0779j$ | 0.0781, 0.083 | 0.0797 |
| 5 | $-0.3709\pm1.3514j$ | $-0.0189\pm0.1430j$ | 0.1443, 0.131 | 0.1467 |

The SPO pair barely moves: over the whole range its eigenvalue changes by less than 0.5 %. The reduced short-period model of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]] does not contain $\mathring X_u$ or $\mathring Z_u$ at all, so it predicts the same $-0.3723\pm1.3616j$ for every $k$, and it stays within 0.73 % of the full model throughout.

The phugoid moves a long way. From $k=1$ to $k=5$ its natural frequency nearly doubles, from 0.078 to 0.144 rad/s, and its damping ratio rises by more than half, from 0.083 to 0.131. Eq. 6.38 explains both: the stiffness is

$$
\omega_n^2=\frac{g}{mU_\infty}\left(\frac{\mathring M_u\mathring Z_w}{\mathring M_w}-k\mathring Z_u\right)=\frac{g}{mU_\infty}\left(817.5+1214.0\,k\right)\ \text{(kg/s in the bracket)},
$$

which grows with $k$, and the damping term $-k\mathring X_u/m$ grows with $k$ too. Even at $k=0$ the phugoid still oscillates, because the speed-stability term $\mathring M_u\mathring Z_w/\mathring M_w$ supplies stiffness without $\mathring Z_u$ ([[SESA3047 6.2 - Phugoid Approximation#Lanchester as a special case of Eq. 6.38|6.2 §4]]). The improved approximation tracks the full-model phugoid frequency to within about 2 % over the whole range.

### What it shows

The speed derivatives belong to the phugoid, the slow mode in which speed changes. The SPO happens so fast that the speed hardly changes during it, so $\mathring X_u$ and $\mathring Z_u$ have almost no lever on it. That is the separation of time scales ([[Separation of Time Scales]]) that justifies dropping $u$ from the SPO approximation, seen directly in the eigenvalues.

## Problems 4 and 5 (lateral)

- Problem 4, the $N_v$ sweep for the Navion: [[SESA3047 6.3 - Lateral Modes and their Approximations#Practice problem 4: stronger directional stability|6.3 §12]]. Stronger directional stability raises the Dutch-roll frequency but lowers its damping ratio, and makes the spiral unstable above 123 % of the original $N_v$.
- Problem 5, modes from a flight test: [[SESA3047 6.3 - Lateral Modes and their Approximations#Practice problem 5: modes from a flight test|6.3 §12]]. Eigenvalues $-7.68$ (roll subsidence), $-0.0578\pm2.618j$ (Dutch roll, $\omega_n=2.62$ rad/s, $\zeta=0.022$) and $+0.0087$ s⁻¹ (unstable spiral); the system is unstable, but slowly.

## Links

- Theory: [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]] · [[SESA3047 6.2 - Phugoid Approximation]] · [[SESA3047 6.3 - Lateral Modes and their Approximations]]
- Concepts: [[Eigenvectors as Mode Shapes]] · [[Matrix Exponential and Modal Solution]] · [[Separation of Time Scales]] · [[Short Period Oscillation]] · [[Phugoid Mode]]
- Hub: [[SESA3047 Advanced Aerospace Mechanics & Control Hub]] · Previous sheet: [[SESA3047 Chapter 5 Practice Problems - Solutions]]

## Sources

- Lecture Notes - Chapter 6.pdf, Dr Sean Symon, p. 14 (§6.10); Eq. 6.4 (p. 2) and Table 6.1 (p. 6).
- Computation and plots: generate_amc_ch6_practice_figures.py (`--check` verifies the modal split of problem 1, the phugoid-free start, the time-shift identity of problem 2 and the eigenvalue tracks of problem 3 against Eq. 6.38).
