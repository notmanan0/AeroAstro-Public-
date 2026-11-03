---
title: "Bode Plot"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["Bode diagram", "decibels", "corner frequency", "bandwidth", "cut-off frequency"]
tags: [sesa2027, concept, frequency-response]
status: complete
parent_lectures: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]", "[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Frequency Response Function]]", "[[Gain and Phase Margins]]", "[[Poles and Zeros]]"]
sources: ["02 - Sources/Lectures/Lecture 1.09.pdf", "02 - Sources/Lectures/Lecture 2.05.pdf", "02 - Sources/Lectures/Lecture 3.06.pdf"]
---

# Bode Plot

A Bode plot is a pair of graphs against $\log_{10}\omega$: the magnitude in decibels, $|G|_{dB} = 20\log_{10}|G(i\omega)|$, and the phase $\angle G(i\omega)$ in degrees. Because logarithms turn products into sums, the plot of a transfer function is the sum of the plots of its factors.

That additivity is what makes Bode plots quick to sketch by hand. Each factor contributes a standard shape:

| Factor | Magnitude | Phase |
|---|---|---|
| Gain $k$ | Flat at $20\log\vert k\vert$ | 0° (−180° if $k<0$) |
| $s$ / $1/s$ | ±20 dB/dec through 0 dB at 1 rad/s | ±90° |
| Real zero / pole at $\vert a\vert$ | Flat, then ±20 dB/dec after $\vert a\vert$ (−3 dB error at the corner) | 0 → ±90° over $0.1\vert a\vert$ to $10\vert a\vert$ (±45° at the corner) |
| Complex zeros / poles at $\omega_n$ | Flat, then ±40 dB/dec; a peak or notch if $\zeta<0.707$ | 0 → ±180°, sharper for low $\zeta$ |

The course reads several specifications off the plot. The cut-off or corner frequency is where the gain has fallen 3 dB (a factor 0.707) below its low-frequency value, and the bandwidth is the range over which it stays within that 3 dB. Any rise above the low-frequency gain is peaking, at the resonant frequency $\omega_r$. For stability margins the two key points are the gain crossover $\omega_{gc}$, where the magnitude passes 0 dB, and the phase crossover $\omega_{pc}$, where the phase passes −180°.

The module uses Bode plots in all three parts: for loop shaping and margins ([[Gain and Phase Margins]]), for reading the phugoid and SPO peaks of an aircraft response, and for sensor and filter design, where the question is over what band a sensor is transparent, where it resonates and how much phase lag it adds. Two examples from the problem sheets: $5/(s^2+4s+25)$ in PS2 Q1 sits at −13.98 dB at DC, has a small peak (−11.3 dB) at 4.12 rad/s, rolls off at −40 dB/dec and has no crossovers ([[SESA2027 Practice Problems 2 Solutions]]); the RC filter with $\tau = 0.04$ s in PS C Q6 has its corner at 25 rad/s, rolls off at −20 dB/dec and is at −45° at the corner ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_bode_second_order_family.png|560]]

## Related

- Where the asymptotes come from: [[SESA2027 A5 - Frequency Response and Bode Plots#4. Building a Bode plot from factors|A5 §4]]
- [[Frequency Response Function]] · [[Gain and Phase Margins]] · [[Poles and Zeros]]
