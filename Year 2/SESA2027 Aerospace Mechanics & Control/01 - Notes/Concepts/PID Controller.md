---
title: "PID Controller"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["PID", "PD", "PI", "proportional integral derivative", "integrator wind-up", "derivative filter", "three-term controller"]
tags: [sesa2027, concept, control, pid]
status: complete
parent_lectures: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]", "[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
related_concepts: ["[[Closed-Loop Transfer Function]]", "[[Ziegler-Nichols Tuning]]", "[[Gain and Phase Margins]]", "[[Root Locus]]", "[[Digital Filtering]]"]
sources: ["02 - Sources/Lectures/Lecture 2.03.pdf", "02 - Sources/Lectures/Lecture 2.05.pdf"]
---

# PID Controller

A PID controller acts on the present error (P), the accumulated error (I) and the predicted error (D):

$$
u(t) = K_Pe+K_I\int_0^te\,d\tau+K_D\dot e\quad\Longleftrightarrow\quad C(s) = K_P+\frac{K_I}{s}+K_Ds = K_p\left(1+\frac{1}{T_Is}+T_Ds\right),
$$

where $T_I = K_p/K_I$ is the integral (reset) time and $T_D = K_D/K_p$ the derivative (rate) time.

| Action | Benefit | Cost |
|---|---|---|
| P | Faster response, smaller error | Steady-state error remains; high gain gives oscillation |
| I | Zero steady-state error | −90° phase lag, overshoot, wind-up under saturation |
| D | Damping, phase lead ($\tan^{-1}\omega T_D$), less overshoot | Amplifies noise (gain $\propto\omega$) |

$T_I$ and $T_D$ are always positive; the sign of $K_p$ is chosen to match the plant gain. Pure derivative action is never used as written. It is filtered, $K_D\,s/(1+s/N)$, or applied to the measurement instead of the error, or replaced by a rate gyro that measures $q$ directly. The course's advice, following DAP2, is to start with P and add terms only when they're needed, giving the P, PD, PI and PID variants.

The gains can be tuned several ways: by frequency-response design (choose $\omega_{gc}$, set $T_D$ for the phase lead needed, take $T_I = 3/\omega_{gc}$, then set $K_p$ so that $|CG| = 1$), by root locus, by [[Ziegler-Nichols Tuning]], or by rules such as Tyreus–Luyben, Cohen–Coon and lambda tuning. The lecture's SPO design gives $K_p = 1.345$, $K_i = 1.345$ and $K_d = 0.46$ at $\omega_{gc} = 3$ rad/s, but these are for the inverted plant. On the real SPO plant, whose gain is negative, they are implemented with a negative sign, while $T_I = 1.0$ s and $T_D = 0.342$ s stay positive; follow the corrected L2.05 slides rather than the lecture as delivered ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#What was said in L2.05 vs the corrected slides]]). PS2 Q7 designs a PD controller with $T_D = 0.192$ s and $K_p = 3.46$ for a 55° phase margin ([[SESA2027 Practice Problems 2 Solutions]]).

![[amc_pid_actions_comparison.png|600]]

## Related

- Steady-state error under P and PI: [[SESA2027 B1 - Control System Fundamentals and PID Control#4. PID control (L2.03)|B1 §4]]
- [[Closed-Loop Transfer Function]] · [[Ziegler-Nichols Tuning]] · [[Gain and Phase Margins]] · [[Root Locus]] · [[Digital Filtering]]
