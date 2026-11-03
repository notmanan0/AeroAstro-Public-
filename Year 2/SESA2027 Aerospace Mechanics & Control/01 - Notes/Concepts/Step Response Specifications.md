---
title: "Step Response Specifications"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["rise time", "overshoot", "settling time", "peak time", "time-domain specifications", "time constant", "percent overshoot"]
tags: [sesa2027, concept, time-response]
status: complete
parent_lectures: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Sensor Dynamic Models]]", "[[PID Controller]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf", "02 - Sources/Lectures/Lecture 3.05.pdf", "Franklin, Powell & Emami-Naeini, Ch. 3"]
---

# Step Response Specifications

The step response specifications are time-domain measures of how a system responds to a normalised step. For the standard second-order system they follow from $\omega_n$ and $\zeta$:

$$
t_r\approx\frac{1.8}{\omega_n},\qquad OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}\ \%,\qquad t_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^2}},\qquad t_s\approx\frac{4.6}{\zeta\omega_n}\ (1\%)\ \text{or}\ \frac{3}{\zeta\omega_n}\ (5\%).
$$

| Spec | Meaning | Depends on |
|---|---|---|
| Rise time $t_r$ (10–90 %) | Speed | Mainly $\omega_n$ |
| Overshoot $OS$ | Peak excursion beyond the final value | Only $\zeta$ |
| Peak time $t_p$ | Time of the first peak | $\omega_d = \omega_n\sqrt{1-\zeta^2}$ |
| Settling time $t_s$ | Time to stay within ±1 % (or ±5 %) | Real part $\zeta\omega_n = \vert\sigma\vert$ |
| Time constant $\tau$ (first order) | 63.2 % of the final value | $\tau$ |
| Steady-state error $e_{ss}$ | $1-$ final value (unity-feedback loops) | DC loop gain; zero with integral action |

The settling-time constants come from the envelope $e^{-\zeta\omega_nt}$: $4.6 = -\ln0.01$ and $3.0\approx-\ln0.05$. The rise-time rule is rough and works best near $\zeta\approx0.5$; for $\zeta = 0.4$ the exact 10–90 % value is closer to $1.46/\omega_n$. A few overshoot values are worth knowing: $\zeta = 0.7$ gives about 4.6 % (the usual sensor choice), $\zeta = 0.4$ gives 25.4 % and $\zeta = 0.2$ gives 52.7 %.

The course uses the same measures for aircraft modes, closed loops and sensors. For a sensor, overshoot is a false peak in the reported signal and a long rise time is lag. PS1 Q3 ($\omega_n = 3.65$ rad/s, $\zeta = 0.4$) gives $t_r = 0.493$ s, $t_s = 3.151$ s and $OS = 25.4\%$; the sheet's answer of 22.4 % drops the square root ([[SESA2027 Practice Problems 1 Solutions]]). PS C Q4 ($\omega_n = 12$ rad/s, $\zeta = 0.35$) gives $t_r = 0.150$ s, $OS = 30.9\%$ and $t_s = 1.10$ s ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_second_order_step_family.png|560]]

## Related

- Peak time, overshoot and settling time derived: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response#Deriving the specifications|A4]]
- [[Damping Ratio and Natural Frequency]] · [[Sensor Dynamic Models]] · [[PID Controller]]
