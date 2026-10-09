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

## Definition

> [!note] Definition
> For controller $C$, plant $G$ and sensor $H$ in negative feedback:
> $$\frac{X(s)}{R(s)} = \frac{G(s)C(s)}{1+G(s)C(s)H(s)}$$
> With unity feedback ($H = 1$) and $G = B/A$, the **closed-loop characteristic equation** is $1+GC = 0$. For a proportional controller this becomes $A(s)+K_pB(s) = 0$.

## Explanation
- **Feedback moves the poles**: the closed-loop poles are the roots of $1+GCH = 0$, not the plant's poles. This is how control adds stability or damping.
- **Three inputs, three transfer functions** (L2.07):

$$
X = \underbrace{\frac{GC}{1+GCH}}_{\text{reference}}R+\underbrace{\frac{G}{1+GCH}}_{\text{disturbance}}U_P-\underbrace{\frac{GCH}{1+GCH}}_{\text{noise}}X_N
$$

  - A high loop gain $|GCH|$ gives good tracking and disturbance rejection.
  - **But** the noise term tends to 1, so noise passes straight through. Hence the loop gain should be high at low frequency and low at high frequency.
- **Steady-state error** (step, unity feedback): $e_{ss} = \dfrac{1}{1+G(0)C(0)}$. It becomes zero once $C$ contains an integrator.
- **Stability of a second-order closed loop**: $s^2+bs+c$ is stable iff $b>0$ and $c>0$. Uncertainty in $\zeta$, $\omega_n$ or $z$ shifts $b$ and $c$, which is why margins matter.
- **Sign convention**: if the plant gain is negative (e.g. $q/\eta<0$), use $K_p<0$ to keep **negative** feedback.

## Examples
- Double integrator with P control: $K_p/(s^2+K_p)$ is marginally stable. Adding D gives $s^2+K_Ds+K_P$, which is stable ([[SESA2027 B2 - Root Locus Method]]).
- PS2 Q4: $\dfrac{K_pK(s+z)}{s^2+(2\zeta\omega_n+K_pK)s+(\omega_n^2+K_pKz)}$ ([[SESA2027 Practice Problems 2 Solutions]]).

## Related
- [[PID Controller]] · [[Root Locus]] · [[Gain and Phase Margins]] · [[Transfer Function]] · [[Routh-Hurwitz Stability Criterion]]

## Sources
- Lectures 2.02, 2.07
