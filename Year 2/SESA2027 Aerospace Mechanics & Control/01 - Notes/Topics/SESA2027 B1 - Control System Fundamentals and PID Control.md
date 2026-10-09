---
title: "SESA2027 B1 - Control System Fundamentals and PID Control"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part B: Control Systems"
order: 6
tags:
  - sesa2027
  - control-systems
  - pid
aliases: ["PID Control", "Control Fundamentals"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
next_topics: ["[[SESA2027 B2 - Root Locus Method]]"]
key_concepts: ["[[Closed-Loop Transfer Function]]", "[[PID Controller]]", "[[Transfer Function]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 2.01.pdf", "02 - Sources/Lectures/Lecture 2.02.pdf", "02 - Sources/Lectures/Lecture 2.03.pdf"]
---

# SESA2027 B1 - Control System Fundamentals and PID Control

> [!abstract] Summary
> A **control system** compares a reference $r$ with a measured output $y$. The error $e = r-y$ drives a controller $C(s)$, which commands the plant $G(s)$. With unity feedback the closed loop is $\dfrac{X}{R} = \dfrac{GC}{1+GC}$, and its **closed-loop characteristic polynomial** decides stability. The **PID** controller
> $$C(s) = K_P+\frac{K_I}{s}+K_Ds$$
> combines present error (P), accumulated error (I) and predicted error (D). Each term changes the closed-loop poles differently.

## Key Concepts
- [[Closed-Loop Transfer Function]] · [[PID Controller]]

---

## 1. Why control? (L2.01)
Examples in the lecture:
- A kestrel hovering: feedback in nature.
- Watt's steam-engine governor.
- Chemical process plants.
- Multirotor attitude and position control.
- A wind-tunnel model whose controller fails.

**Definition**: "A control system is an arrangement of components in which a **controller** generates a **control action** by comparing a **reference input** with the system's **feedback signal**, i.e. the **control error**. The controller uses the control error to adjust the system so that its output achieves the specified performance or remains within desired bounds."

| Element | Meaning |
|---|---|
| Controller $C(s)$ | Processes the error and decides the action |
| Control action $u(t)$ | Command sent to the plant |
| Control error $e(t) = r(t)-y(t)$ | Difference between reference and measurement |
| Reference $r(t)$ | Desired or commanded output |
| Feedback $y(t)$ | Measured output (or estimated state) |

**General block diagram**:
- $R\to\Sigma\to E\to C(s)\to U_C\to\Sigma(+U_P\text{, process noise})\to U\to G(s)\to X$
- Feedback path: $X\to\Sigma(+X_N\text{, measurement noise})\to X_M\to H(s)\ (\text{sensor})\to Y\to$ back to the first $\Sigma$ with a minus sign

### Control objectives
1. **Stability** (BIBO): every bounded input gives a bounded output.
2. **Regulation**: hold a variable at a constant set point despite disturbances.
3. **Tracking**: follow a time-varying reference.
4. **Disturbance rejection**: minimise the effect of external disturbances on the output.
5. **Performance management**: meet the rise-time, overshoot and settling specifications while limiting control effort.

## 2. Control classifications (L2.02)

| Type | Pros | Cons |
|---|---|---|
| Open-loop | Simple, cheap, no sensors | No error correction, sensitive to disturbances |
| Closed-loop | Error correction, robust, better stability | Needs sensing, costs more, needs careful tuning |
| Model-based | Predictable, has stability guarantees | Needs an accurate model |
| Model-free | No model needed, robust to modelling errors | Weaker guarantees, tuning-dependent |
| Linear | Simple analysis, well-established tools | Only valid near equilibrium |
| Nonlinear | Covers the full envelope | Complex, relies on model accuracy |
| Rule-based | Transparent logic | Limited adaptability |
| Learning-based (SL/RL) | Adapts to complex environments | Needs data, hard to interpret or validate |

**DAP2**: this module uses **linear, model-based, rule-based, closed-loop** control.

### SPO approximation with elevator input
Add $[\mathring Z_\eta,\ \mathring M_\eta]^T\eta$ to the SPO equations, giving $\dot{\mathbf x}_{SPO} = \mathbf A_{SPO}\mathbf x_{SPO}+\mathbf B_{SPO}\eta$ with $\mathbf x = [w,q]^T$. With $\mathbf C = [0,\ 1]$ (measure $q$):

$$
\left[\frac{q(s)}{\eta(s)}\right]_{SPO} = \frac{m_\eta s+(-m_\eta z_w+m_wz_\eta)}{s^2-(m_q+z_w)s+(z_wm_q-z_qm_w)},\qquad \left[\frac{\theta(s)}{\eta(s)}\right]_{SPO} = \frac1s\left[\frac{q(s)}{\eta(s)}\right]_{SPO}
$$

The lower-case letters are Cook's "concise" derivatives, i.e. the entries of $\mathbf A = \mathbf M^{-1}\mathbf A'$. The lecture example used throughout Part B is

$$
G(s) = \frac{q}{\eta} = \frac{-1.39(s+0.306)}{s^2+0.805s+1.325}
$$

## 3. Closed-loop transfer function
With unity feedback ($H=1$) and no noise:

$$
X = GU,\quad U = CE,\quad E = R-X\quad\Rightarrow\quad\boxed{\frac{X(s)}{R(s)} = \frac{G(s)C(s)}{1+G(s)C(s)}}
$$

Writing $G = B/A$, the **closed-loop characteristic equation** is $A(s)+C(s)B(s) = 0$ (for a proportional $C$). See [[Closed-Loop Transfer Function]].

## 4. PID control (L2.03)

**History**:
- Float valves; Watt's fly-ball governor (1788).
- Airy (1840) and Maxwell (1868): first stability analyses.
- Routh (1877) and Lyapunov (1892): stability criteria.
- Feedback amplifiers: Nyquist (1932) and Bode (1945).
- PID formalised by Callender et al. (1936).
- Root locus: Evans (1948).

$$
u(t) = K_Pe(t)+K_I\int_0^te(\tau)d\tau+K_D\frac{de}{dt}\quad\xrightarrow{\ \mathcal L\ }\quad C(s) = K_P+\frac{K_I}{s}+K_Ds
$$

Each action is studied alone (DAP3), with $G = B/A$:

| Action | Closed loop $X/R$ | Characteristic polynomial | Effect |
|---|---|---|---|
| **P** | $\dfrac{K_PB}{A+K_PB}$ | $A+K_PB=0$ | Faster, reduces error. Higher gain gives oscillation. **Steady-state error remains** |
| **I** | $\dfrac{K_IB}{As+K_IB}$ | $As+K_IB=0$ | **Removes steady-state error**. Slower, can overshoot, **integrator wind-up**. Adds a pole at the origin (extra −90° phase) |
| **D** | $\dfrac{K_DBs}{A+K_DBs}$ | $A+K_DBs=0$ | Adds damping, predicts the error trend, reduces overshoot. **Amplifies noise**, needs filtering |

![[amc_pid_actions_comparison.png|620]]

Common variants are **P, PD, PI and PID**. Start simple and add terms as needed (DAP2). The gains must be chosen to **guarantee stability**.

> [!example] Satellite 1-DoF attitude via a reaction wheel (L2.03 demo)
> Plant: $G(s) = \Psi/U = \dfrac{1}{I_{zz}s^2}$ (double integrator).
>
> The reaction-wheel torque is $\omega_z = -\dfrac{I_{zz-wh}}{I_{zz}}\omega_{z-wh}$, with controller $\omega_{z-wh}(s) = k_ds+k_p$ (PD). The closed loop is
>
> $$T(s) = \frac{-(I_{zz-wh}k_ds+I_{zz-wh}k_p)}{I_{zz}s^2-I_{zz-wh}k_ds-I_{zz-wh}k_p}$$
>
> A P controller alone only gives marginal stability (poles on the imaginary axis). The D term is essential. See [[SESA2027 B2 - Root Locus Method]].

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A5 - Frequency Response and Bode Plots]] · Next: [[SESA2027 B2 - Root Locus Method]]
- Year 3: state-space and optimal control in [[SESA3047 Advanced Aerospace Mechanics & Control]]

## Sources
- Lectures 2.01–2.03; Franklin, Powell & Emami-Naeini (2014) Ch. 1, 4; Brian Douglas, *Map of Control Theory*
