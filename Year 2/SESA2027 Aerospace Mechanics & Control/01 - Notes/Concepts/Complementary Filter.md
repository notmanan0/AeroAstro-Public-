---
title: "Complementary Filter"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["complementary filtering", "sensor fusion", "IMU fusion", "gyro-accelerometer fusion", "blending filter"]
tags: [sesa2027, concept, sensors, sensor-fusion]
status: complete
parent_lectures: ["[[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[Digital Filtering]]", "[[Accuracy and Precision]]", "[[Measurement Chain]]"]
sources: ["02 - Sources/Lectures/Lecture 3.03.pdf", "02 - Sources/Lectures/Lecture 3.08.pdf", "Groves, Ch. 4"]
---

# Complementary Filter

A complementary filter fuses a fast estimate that is good in the short term but drifts (the integrated gyro) with a slow estimate that is stable in the long term but noisy (the accelerometer tilt):

$$
\hat\theta[k] = \alpha\,\hat\theta_{gyro}[k]+(1-\alpha)\,\hat\theta_{acc}[k],
$$

usually implemented recursively as $\hat\theta[k] = \alpha(\hat\theta[k-1]+T_sq[k])+(1-\alpha)\theta_{acc}[k]$. In effect the gyro path is high-pass filtered and the accelerometer path low-pass filtered, and the two filters sum to 1.

Each sensor is trusted only in the band where it is good. A MEMS (Coriolis) gyroscope measures angular rate accurately at high frequency, but integrating its bias gives drift that grows without limit. An accelerometer senses gravity through the specific force, so it gives an absolute, drift-free tilt at low frequency, but manoeuvre accelerations and vibration corrupt it. Simple averaging would weight both equally at every frequency and inherit both sets of errors.

$\alpha$ sets the crossover between the two. The equivalent time constant is $\tau\approx\alpha T_s/(1-\alpha)$, so $\alpha = 0.98$ at 100 Hz gives $\tau\approx0.49$ s. Pushing $\alpha$ towards 1 makes the estimate smooth but lets it drift; towards 0 it becomes noisy and picks up manoeuvre errors. PS C Q13 works an example ([[SESA2027 Part C Problem Sheet Solutions]]). The complementary filter is the simplest fusion method; the Kalman filter in Year 3 chooses the blend optimally from the noise statistics.

![[amc_complementary_filter.png|650]]

## Related

- Transfer functions, discrete update and the bounded bias error: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion#Complementary filter|C1]]
- [[Digital Filtering]] · [[Accuracy and Precision]] · [[Measurement Chain]]
