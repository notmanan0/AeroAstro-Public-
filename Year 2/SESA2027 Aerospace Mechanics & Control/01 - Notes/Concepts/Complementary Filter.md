---
title: "Complementary Filter"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["complementary filtering", "sensor fusion", "IMU fusion", "gyro-accelerometer fusion"]
tags: [sesa2027, concept, sensors, sensor-fusion]
status: complete
parent_lectures: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[Digital Filtering]]", "[[Accuracy and Precision]]", "[[Measurement Chain]]"]
sources: ["02 - Sources/Lectures/Lecture 3.03.pdf", "02 - Sources/Lectures/Lecture 3.08.pdf"]
---

# Complementary Filter

## Definition

> [!note] Definition
> A fusion rule that combines a **fast** estimate (good short-term, drifts) with a **slow** estimate (stable long-term, noisy):
> $$\hat\theta[k] = \alpha\,\hat\theta_{gyro}[k]+(1-\alpha)\,\hat\theta_{acc}[k],\qquad \text{usually implemented as}\quad \hat\theta[k] = \alpha(\hat\theta[k-1]+T_sq[k])+(1-\alpha)\theta_{acc}[k]$$
> The gyro path is effectively **high-pass** filtered and the accelerometer path **low-pass** filtered. The two filters sum to 1.

## Explanation
- **Gyroscope** (Coriolis MEMS): accurate angular rate at high frequency, but integrating its bias gives unbounded **drift**.
- **Accelerometer**: senses gravity (specific force), so it gives an absolute, drift-free tilt at low frequency. It is corrupted by manoeuvre acceleration and vibration.
- **$\alpha$ sets the crossover**: the equivalent time constant is $\tau\approx\dfrac{\alpha T_s}{1-\alpha}$.
  - For example, $\alpha = 0.98$ at 100 Hz gives $\tau\approx0.49$ s.
  - $\alpha\to1$ makes the estimate smooth but drifting.
  - $\alpha\to0$ makes it noisy, with manoeuvre errors.
- **Not averaging**: an average weights both sources equally at all frequencies, so it inherits both errors. The complementary filter assigns each sensor to the band where it is trustworthy.
- It is the simplest fusion method. Kalman filters (Year 3) choose the blend optimally from the noise statistics.

## Examples
- PS C Q13 ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_complementary_filter.png|650]]

## Related
- [[Digital Filtering]] · [[Accuracy and Precision]] · [[Measurement Chain]]

## Sources
- Lectures 3.03, 3.08; Groves, Ch. 4
