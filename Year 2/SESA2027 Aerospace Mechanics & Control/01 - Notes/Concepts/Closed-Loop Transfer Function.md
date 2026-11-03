---
title: "Closed-Loop Transfer Function"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["closed loop", "feedback loop", "characteristic polynomial of the closed loop", "sensitivity function", "complementary sensitivity"]
tags: [sesa2027, concept, control]
status: complete
parent_lectures: ["[[SESA2027 B1 - Control System Fundamentals and PID Control]]", "[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
related_concepts: ["[[PID Controller]]", "[[Root Locus]]", "[[Gain and Phase Margins]]", "[[Transfer Function]]"]
sources: ["02 - Sources/Lectures/Lecture 2.02.pdf", "02 - Sources/Lectures/Lecture 2.07.pdf"]
---

# Closed-Loop Transfer Function

With controller $C$, plant $G$ and sensor $H$ in a negative-feedback loop, the output follows the reference through

$$
\frac{X(s)}{R(s)} = \frac{G(s)C(s)}{1+G(s)C(s)H(s)} .
$$

The closed-loop poles are the roots of $1+GCH = 0$, not the plant's own poles, and that is how feedback adds stability or damping. With unity feedback ($H = 1$) and $G = B/A$, a proportional controller gives the closed-loop characteristic equation $A(s)+K_pB(s) = 0$. A double integrator under P control, $K_p/(s^2+K_p)$, is only marginally stable; adding derivative action gives $s^2+K_Ds+K_P$, which is stable ([[SESA2027 B2 - Root Locus Method]]). A second-order closed loop $s^2+bs+c$ is stable if and only if $b>0$ and $c>0$, and uncertainty in the plant's $\zeta$, $\omega_n$ or zero shifts $b$ and $c$, which is why margins are needed.

L2.07 splits the output into the response to the reference, to a disturbance at the plant input and to sensor noise:

$$
X = \underbrace{\frac{GC}{1+GCH}}_{\text{reference}}R+\underbrace{\frac{G}{1+GCH}}_{\text{disturbance}}U_P-\underbrace{\frac{GCH}{1+GCH}}_{\text{noise}}X_N
$$

A high loop gain $|GCH|$ gives good tracking and rejects disturbances, but it also pushes the noise transfer function towards 1, so noise passes straight through. The loop gain should therefore be high at low frequency, where the signals are, and low at high frequency, where the noise is. For a step with unity feedback the steady-state error is $e_{ss} = 1/(1+G(0)C(0))$, which goes to zero once $C$ contains an integrator.

If the plant gain is negative, as for $q/\eta$, the controller needs $K_p<0$ to keep the feedback negative. PS2 Q4 works the general case, $\dfrac{K_pK(s+z)}{s^2+(2\zeta\omega_n+K_pK)s+(\omega_n^2+K_pKz)}$ ([[SESA2027 Practice Problems 2 Solutions]]).

## Related

- The three transfer functions and $S+T=1$: [[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process#3. The three closed-loop transfer functions|B4 §3]]
- [[PID Controller]] · [[Root Locus]] · [[Gain and Phase Margins]] · [[Transfer Function]] · [[Routh-Hurwitz Stability Criterion]]
