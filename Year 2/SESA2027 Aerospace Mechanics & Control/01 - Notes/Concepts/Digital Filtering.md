---
title: "Digital Filtering"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["moving average", "recursive filter", "IIR", "FIR", "median filter", "filtered derivative", "discrete integration", "outlier rejection", "low-pass filter", "exponential moving average", "boxcar filter"]
tags: [sesa2027, concept, sensors, signal-processing]
status: complete
parent_lectures: ["[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Complementary Filter]]", "[[Nyquist Sampling and Aliasing]]", "[[PID Controller]]", "[[Accuracy and Precision]]"]
sources: ["02 - Sources/Lectures/Lecture 3.06.pdf", "02 - Sources/Lectures/Lecture 3.08.pdf"]
---

# Digital Filtering

A digital filter is an algorithm $\hat x[k] = F(y[k],y[k-1],\dots)$ that uses past samples to estimate the true signal from a measurement $y[k] = x[k]+b[k]+n[k]$, which is truth plus bias or drift plus noise. The two basic low-pass filters in the course are the FIR moving average and the first-order IIR filter:

$$
y_f[k] = \frac1N\sum_{i=0}^{N-1}y[k-i]\quad(\text{delay}\approx\tfrac{N-1}{2}T_s),\qquad y_f[k] = \alpha y[k]+(1-\alpha)y_f[k-1],\quad \alpha\approx\frac{T_s}{\tau+T_s}.
$$

The lecture calls the cost of filtering a software tax: every filter trades noise reduction for delay or distortion, so choosing $\alpha$ or $N$ is choosing the measurement dynamics. Inside a control loop the filter costs phase margin. In PS C Q11, a five-point average at $T_s = 0.01$ s delays the signal by 0.02 s, and $\tau = 0.09$ s gives $\alpha = 0.1$ ([[SESA2027 Part C Problem Sheet Solutions]]). Each filter also carries a hidden assumption. The moving average assumes the signal is constant over its window, and drift removal assumes slow content is error, so it can remove real slow motion along with the drift.

Spikes and derivatives need different tools. A median filter ignores isolated spikes: for $\{1.01, 1.03, 8.50, 1.02, 1.00\}$ the mean is 2.512 but the median is 1.02. Outliers can also be caught by flagging $|y[k]-y[k-1]|>\Delta_{max}$ and holding, interpolating or flagging the sample. Differentiation amplifies noise, because the noise difference $(n[k]-n[k-1])/T_s$ is scaled by $1/T_s$, so the course uses a filtered derivative $d[k] = \beta d[k-1]+(1-\beta)\Delta y/T_s$. Integration does the opposite and accumulates bias as $kT_sb$: in PS C Q12 a bias of 0.02 unit/s integrated for 60 s gives a 1.2 unit error. The fix is a bias estimate, a baseline, a high-pass filter or a periodic reset from a reference.

Some damage can't be undone in software. No filter recovers clipped peaks, undoes aliasing, creates bandwidth that was never sampled, or removes a bias without some assumption about it. The analogue RC low-pass, $1/(RCs+1)$, plays the same role in hardware and is needed before the ADC as the anti-alias filter.

![[amc_digital_filter_tradeoff.png|680]]

## Related

- Moving-average delay and the recursive filter from the RC filter: [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#8. Digital processing after the ADC (L3.08)|C3 §8]]
- [[Complementary Filter]] · [[Nyquist Sampling and Aliasing]] · [[PID Controller]] · [[Accuracy and Precision]]
