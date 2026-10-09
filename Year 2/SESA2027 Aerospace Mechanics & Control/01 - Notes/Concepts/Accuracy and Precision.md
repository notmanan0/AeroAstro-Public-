---
title: "Accuracy and Precision"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["accuracy", "precision", "bias", "noise", "drift", "repeatability", "SNR", "signal-to-noise ratio"]
tags: [sesa2027, concept, sensors]
status: complete
parent_lectures: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Measurement Chain]]", "[[Digital Filtering]]", "[[Complementary Filter]]"]
sources: ["02 - Sources/Lectures/Lecture 3.01.pdf", "02 - Sources/Lectures/Lecture 3.04.pdf"]
---

# Accuracy and Precision

## Definition

> [!note] Definition
> - **Accuracy**: how close the **mean** measurement is to the true value. It is lost through **systematic** error (bias or offset), measured by $\mu\neq0$.
> - **Precision** (repeatability): how tightly repeated measurements of the same state cluster. It is lost through **random** error (noise), measured by $\sigma$.
>
> $$\mu = \frac1N\sum x_i,\qquad \sigma^2 = \frac{1}{N-1}\sum(x_i-\mu)^2$$

## Explanation

| | Poor accuracy (bias) | Poor precision (noise) |
|---|---|---|
| Example | IMU reads +2° pitch when level | GPS wanders ±5 m while stationary |
| Control effect | **Steady-state deviation** that feedback cannot see | **Actuator jitter**, wear, excited structural modes |
| Fix | Calibration, a reference sensor, fusion | Filtering (at the cost of lag), averaging, better SNR |

- **Drift**: a slow change in bias (temperature, ageing). Integration turns bias into a growing error, $kT_sb$.
- **Noise description**:
  - usually zero-mean Gaussian (95 % of readings within ±2σ);
  - in frequency, band-limited white noise plus EMI lines.
- **SNR**: signal power over noise power. Below the **noise floor** a signal cannot be detected.
- The two are independent: a sensor can be accurate but imprecise (noisy but unbiased), or precise but inaccurate (repeatable but offset).

## Examples
- A 0.8 °/s gyro bias in a rate damper leaves the aircraft pitching at −0.8 °/s, and an integrated attitude drifts 48° per minute ([[SESA2027 Part C Problem Sheet Solutions]] Q1).

## Related
- [[Measurement Chain]] · [[Digital Filtering]] · [[Complementary Filter]]

## Sources
- Lectures 3.01, 3.04
