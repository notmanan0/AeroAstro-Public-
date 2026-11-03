---
title: "Sensor Dynamic Models"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["zeroth-order sensor", "first-order sensor", "second-order sensor", "sensor order", "sensor lag", "time constant", "seismic instrument", "first-order lag"]
tags: [sesa2027, concept, sensors, dynamics]
status: complete
parent_lectures: ["[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Step Response Specifications]]", "[[Damping Ratio and Natural Frequency]]", "[[Bode Plot]]", "[[Transfer Function]]"]
sources: ["02 - Sources/Lectures/Lecture 3.05.pdf", "02 - Sources/Lectures/Lecture 3.06.pdf"]
---

# Sensor Dynamic Models

Following DAP2, most aerospace sensors are approximated by one of three transfer functions from the physical input $u$ to the reported output $y$, with static sensitivity $K$:

$$
\text{0th: } y = Ku,\qquad \text{1st: } \frac{Y}{U} = \frac{K}{\tau s+1},\qquad \text{2nd: } \frac{Y}{U} = \frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2} .
$$

| Order | Examples | Design aim | Risk to the control loop |
|---|---|---|---|
| 0th | Strain gauge, potentiometer, LVDT, squat switch | Assume instantaneous | Unsmoothed noise, EMI and temperature sensitivity cause jitter |
| 1st | Thermocouple, pitot-static with long lines, fuel float | $\tau\ll$ airframe time scale | Lag (63.2 % at $t = \tau$) and phase lag $-\tan^{-1}\omega\tau$ reduce margins |
| 2nd | Accelerometer, rate gyro, diaphragm, AoA vane, IMU | High $\omega_n$, $\zeta\approx0.7$ | Low $\zeta$ gives false peaks and resonance; high $\zeta$ gives sluggish, stale data |

Deriving a sensor's state-space matrices from its physics is hard, so in practice the transfer function is identified experimentally, with sine sweeps or broadband noise and a spectrum analyser. The resulting frequency response has three regions. Well below the corner or $\omega_n$ the sensor is transparent, $|G|\approx K$; near $\omega_n$ a lightly damped sensor resonates; above it the output is attenuated and lags more and more. The sensor's bandwidth therefore has to sit comfortably above the aircraft dynamics being controlled, or its phase lag eats into the loop's phase margin.

PS C Q4 has a second-order sensor with $\omega_n = 12$ rad/s and $\zeta = 0.35$: poles at $-4.2\pm11.2i$, 30.9 % overshoot and a settling time of 1.10 s. Q5 compares $\zeta = 0.2$, 0.7 and 1.2 ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_sensor_order_step.png|620]]

## Related

- First-order step response and the accelerometer model: [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design#Three model orders (DAP2, Occam's razor)|C2]]
- [[Step Response Specifications]] · [[Damping Ratio and Natural Frequency]] · [[Bode Plot]] · [[Transfer Function]]
