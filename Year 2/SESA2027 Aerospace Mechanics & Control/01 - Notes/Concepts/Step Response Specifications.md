---
title: "Step Response Specifications"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["rise time", "overshoot", "settling time", "peak time", "time-domain specifications", "time constant"]
tags: [sesa2027, concept, time-response]
status: complete
parent_lectures: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Sensor Dynamic Models]]", "[[PID Controller]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf", "02 - Sources/Lectures/Lecture 3.05.pdf"]
---

# Step Response Specifications

## Definition

> [!note] Definition
> These are time-domain measures of a (normalised) step response. For a standard second-order system:
> $$t_r\approx\frac{1.8}{\omega_n},\qquad OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}\ \%,\qquad t_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^2}},\qquad t_s\approx\frac{4.6}{\zeta\omega_n}\ (1\%)\ \text{or}\ \frac{3}{\zeta\omega_n}\ (5\%)$$

## Explanation

| Spec | Meaning | Depends on |
|---|---|---|
| Rise time $t_r$ (10–90 %) | Speed | Mainly $\omega_n$ |
| Overshoot $OS$ | Peak excursion beyond the final value | **Only $\zeta$** |
| Peak time $t_p$ | Time of the first peak | $\omega_d = \omega_n\sqrt{1-\zeta^2}$ |
| Settling time $t_s$ | Time to stay within ±1 % (or ±5 %) | Real part $\zeta\omega_n = \vert\sigma\vert$ |
| Time constant $\tau$ (first order) | 63.2 % of the final value | $\tau$ |
| Steady-state error $e_{ss}$ | $1-$ final value (unity-feedback loops) | DC loop gain; zero with integral action |

- $4.6 = -\ln0.01$ and $3.0\approx-\ln0.05$.
- $t_r\approx1.8/\omega_n$ is a rough rule, best near $\zeta\approx0.5$. For $\zeta = 0.4$ the exact 10–90 % value is about $1.46/\omega_n$.
- Useful $\zeta$ values:
  - $\zeta = 0.7$ gives $OS\approx4.6\%$ (the sensor optimum);
  - $\zeta = 0.4$ gives 25.4 %;
  - $\zeta = 0.2$ gives 52.7 %.
- The same metrics judge aircraft, closed loops and **sensors**. For a sensor, overshoot means a **false peak** and a long rise time means **lag**.

## Examples
- PS1 Q3 ($\omega_n = 3.65$, $\zeta = 0.4$): $t_r = 0.493$ s, $t_s = 3.151$ s, $OS = 25.4\%$. The sheet's 22.4 % drops the square root ([[SESA2027 Practice Problems 1 Solutions]]).
- PS C Q4 ($\omega_n = 12$, $\zeta = 0.35$): $t_r = 0.150$ s, $OS = 30.9\%$, $t_s = 1.10$ s ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_second_order_step_family.png|560]]

## Related
- [[Damping Ratio and Natural Frequency]] · [[Sensor Dynamic Models]] · [[PID Controller]]

## Sources
- Lectures 1.07, 3.05; Franklin, Powell & Emami-Naeini, Ch. 3
