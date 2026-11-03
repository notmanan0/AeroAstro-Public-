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

**Accuracy** is how close the mean measurement is to the true value; it is lost through systematic error (a bias or offset, $\mu\neq0$). **Precision**, or repeatability, is how tightly repeated measurements of the same state cluster; it is lost through random error (noise, measured by $\sigma$).

$$
\mu = \frac1N\sum x_i,\qquad \sigma^2 = \frac{1}{N-1}\sum(x_i-\mu)^2
$$

The two are independent. A sensor can be accurate but imprecise (noisy but unbiased) or precise but inaccurate (repeatable but offset), and they hurt a control loop in different ways:

| | Poor accuracy (bias) | Poor precision (noise) |
|---|---|---|
| Example | IMU reads +2° pitch when level | GPS wanders ±5 m while stationary |
| Control effect | A steady-state deviation that feedback cannot see | Actuator jitter, wear, excited structural modes |
| Fix | Calibration, a reference sensor, fusion | Filtering (at the cost of lag), averaging, better SNR |

Drift is a slow change in bias with temperature or ageing. It matters most when a signal is integrated, because integration turns a constant bias $b$ into an error $kT_sb$ that grows without limit. A 0.8 °/s gyro bias in a rate damper, for instance, leaves the aircraft pitching at −0.8 °/s, and an attitude obtained by integrating that gyro drifts 48° per minute ([[SESA2027 Part C Problem Sheet Solutions]] Q1).

Noise is usually modelled as zero-mean Gaussian, so about 95 % of readings fall within ±2σ. In the frequency domain it looks like band-limited white noise plus lines from electromagnetic interference. The signal-to-noise ratio (SNR) is signal power over noise power, and a signal below the noise floor cannot be detected at all.

## Related

- [[Measurement Chain]] · [[Digital Filtering]] · [[Complementary Filter]]
