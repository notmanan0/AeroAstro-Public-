---
title: "Digital Filtering"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["moving average", "recursive filter", "IIR", "FIR", "median filter", "filtered derivative", "discrete integration", "outlier rejection", "low-pass filter"]
tags: [sesa2027, concept, sensors, signal-processing]
status: complete
parent_lectures: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Complementary Filter]]", "[[Nyquist Sampling and Aliasing]]", "[[PID Controller]]", "[[Accuracy and Precision]]"]
sources: ["02 - Sources/Lectures/Lecture 3.06.pdf", "02 - Sources/Lectures/Lecture 3.08.pdf"]
---

# Digital Filtering

## Definition

> [!note] Definition
> An algorithm $\hat x[k] = F(y[k],y[k-1],\dots)$ that uses past samples to estimate the true signal from the measurement model $y[k] = x[k]+b[k]+n[k]$ (truth plus bias/drift plus noise). The core low-pass filters are:
> $$\text{FIR moving average: } y_f[k] = \frac1N\sum_{i=0}^{N-1}y[k-i]\ (\text{delay}\approx\tfrac{N-1}{2}T_s),\qquad \text{IIR: } y_f[k] = \alpha y[k]+(1-\alpha)y_f[k-1],\ \alpha\approx\frac{T_s}{\tau+T_s}$$

## Explanation
- **The software tax**: every filter trades noise reduction for **delay or distortion**. Choosing $\alpha$ or $N$ is choosing the measurement dynamics. The digital filter is part of the loop and costs phase margin.
- **Hidden assumptions**:
  - the moving average assumes the signal is constant over the window;
  - drift removal assumes slow content is error, so it can remove real slow motion.
- **Median filter**: robust to isolated spikes. For $\{1.01, 1.03, 8.50, 1.02, 1.00\}$ the mean is 2.512 and the median 1.02.
- **Derivatives amplify noise**: the noise difference $(n[k]-n[k-1])/T_s$ is scaled by $1/T_s$. Use a filtered derivative, $d[k] = \beta d[k-1]+(1-\beta)\Delta y/T_s$.
- **Integrals accumulate bias**: $I = \dots+kT_sb$, which grows without bound. Correct with a bias estimate, a baseline, a high-pass filter, or a reset from a reference.
- **Outlier rejection**: flag $|y[k]-y[k-1]|>\Delta_{max}$, then hold, interpolate or flag the sample.
- **Cannot**: recover clipped peaks, undo aliasing, create bandwidth that was never captured, or remove bias without assumptions.
- **Analogue counterpart**: the RC low-pass $1/(RCs+1)$ plays the same role in hardware, and is required as the anti-alias filter.

## Examples
- PS C Q11: $N = 5$ at $T_s = 0.01$ s gives a 0.02 s delay; $\tau = 0.09$ s gives $\alpha = 0.1$.
- PS C Q12: a bias of 0.02 unit/s integrated for 60 s gives a 1.2 unit error ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_digital_filter_tradeoff.png|680]]

## Related
- [[Complementary Filter]] · [[Nyquist Sampling and Aliasing]] · [[PID Controller]] · [[Accuracy and Precision]]

## Sources
- Lectures 3.06, 3.08
