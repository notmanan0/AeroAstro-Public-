---
title: "PID Controller"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["PID", "PD", "PI", "proportional integral derivative", "integrator wind-up", "derivative filter"]
tags: [sesa2027, concept, control, pid]
status: complete
parent_lectures: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]", "[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
related_concepts: ["[[Closed-Loop Transfer Function]]", "[[Ziegler-Nichols Tuning]]", "[[Gain and Phase Margins]]", "[[Root Locus]]", "[[Digital Filtering]]"]
sources: ["02 - Sources/Lectures/Lecture 2.03.pdf", "02 - Sources/Lectures/Lecture 2.05.pdf"]
---

# PID Controller

## Definition

> [!note] Definition
> $$u(t) = K_Pe+K_I\int_0^te\,d\tau+K_D\dot e\quad\Longleftrightarrow\quad C(s) = K_P+\frac{K_I}{s}+K_Ds = K_p\left(1+\frac{1}{T_Is}+T_Ds\right)$$
> Here $T_I = K_p/K_I$ is the integral (reset) time and $T_D = K_D/K_p$ is the derivative (rate) time. P acts on the present error, I on the accumulated error and D on the predicted error.

## Explanation

| Action | Benefit | Cost |
|---|---|---|
| P | Faster response, smaller error | Steady-state error remains; high gain gives oscillation |
| I | **Zero steady-state error** | −90° phase lag, overshoot, **wind-up** under saturation |
| D | Damping, phase lead ($\tan^{-1}\omega T_D$), less overshoot | **Amplifies noise** (gain $\propto\omega$) |

- **Sign rules**: always choose $T_I>0$ and $T_D>0$. Pick the sign of $K_p$ to match the plant gain.
- **Practical D**: filter it, $K_D\dfrac{s}{1+s/N}$, or differentiate the measurement rather than the error. A rate gyro can measure $q$ directly instead.
- **Tuning**:
  - frequency-response design (choose $\omega_{gc}$, $T_D$ for phase lead, $T_I = 3/\omega_{gc}$, and $K_p$ for $|CG| = 1$);
  - root locus;
  - [[Ziegler-Nichols Tuning]];
  - Tyreus–Luyben, Cohen–Coon, lambda.
- **Variants**: P, PD, PI, PID. Start simple and add terms only when needed (DAP2).

## Examples
- Lecture SPO design: $K_p = 1.345$, $K_i = 1.345$, $K_d = 0.46$ at $\omega_{gc} = 3$ rad/s ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]).
- PS2 Q7: PD with $T_D = 0.192$ s and $K_p = 3.46$ for PM = 55° ([[SESA2027 Practice Problems 2 Solutions]]).

![[amc_pid_actions_comparison.png|600]]

## Related
- [[Closed-Loop Transfer Function]] · [[Ziegler-Nichols Tuning]] · [[Gain and Phase Margins]] · [[Root Locus]] · [[Digital Filtering]]

## Sources
- Lectures 2.03, 2.05–2.07
