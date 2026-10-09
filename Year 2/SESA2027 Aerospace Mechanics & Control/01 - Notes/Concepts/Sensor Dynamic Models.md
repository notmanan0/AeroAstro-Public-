---
title: "Sensor Dynamic Models"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["zeroth-order sensor", "first-order sensor", "second-order sensor", "sensor order", "sensor lag", "time constant"]
tags: [sesa2027, concept, sensors, dynamics]
status: complete
parent_lectures: ["[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Step Response Specifications]]", "[[Damping Ratio and Natural Frequency]]", "[[Bode Plot]]", "[[Transfer Function]]"]
sources: ["02 - Sources/Lectures/Lecture 3.05.pdf", "02 - Sources/Lectures/Lecture 3.06.pdf"]
---

# Sensor Dynamic Models

## Definition

> [!note] Definition
> Most aerospace sensors are approximated (DAP2) by one of three transfer functions from the physical input $u$ to the reported output $y$:
>
> $$\text{0th: } y = Ku,\qquad \text{1st: } \frac{Y}{U} = \frac{K}{\tau s+1},\qquad \text{2nd: } \frac{Y}{U} = \frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}$$
>
> $K$ is the static sensitivity.

## Explanation

| Order | Examples | Design aim | Risk to the control loop |
|---|---|---|---|
| 0th | Strain gauge, potentiometer, LVDT, squat switch | Assume instantaneous | Unsmoothed noise, EMI and temperature sensitivity cause jitter |
| 1st | Thermocouple, pitot-static with long lines, fuel float | $\tau\ll$ airframe time scale | Lag (63.2 % at $t = \tau$) and phase lag $-\tan^{-1}\omega\tau$ reduce margins |
| 2nd | Accelerometer, rate gyro, diaphragm, AoA vane, IMU | High $\omega_n$, $\zeta\approx0.7$ | Low $\zeta$ gives false peaks and resonance; high $\zeta$ gives sluggish, stale data |

- **Identifying** the model: sensor state-space matrices are hard to derive, so the TF is found experimentally with sine sweeps or broadband noise and a spectrum analyser.
- **Frequency behaviour**:
  - **transparent** ($|G|\approx K$) well below the corner or $\omega_n$;
  - **resonant** near $\omega_n$ when $\zeta$ is low;
  - attenuating, with growing phase lag, above it.
- **Bandwidth matching**: the sensor bandwidth must comfortably exceed the aircraft dynamics being controlled, otherwise the sensor's phase lag erodes the loop's phase margin.

## Examples
- PS C Q4: $\omega_n = 12$, $\zeta = 0.35$ gives poles $-4.2\pm11.2i$, $OS = 30.9\%$, $t_s = 1.10$ s.
- PS C Q5: $\zeta = 0.2/0.7/1.2$ comparison ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_sensor_order_step.png|620]]

## Related
- [[Step Response Specifications]] · [[Damping Ratio and Natural Frequency]] · [[Bode Plot]] · [[Transfer Function]]

## Sources
- Lectures 3.05–3.06
