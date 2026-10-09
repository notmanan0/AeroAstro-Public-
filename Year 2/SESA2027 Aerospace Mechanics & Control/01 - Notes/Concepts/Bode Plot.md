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
sources: ["02 - Sources/Lectures/Lecture 1.09.pdf", "02 - Sources/Lectures/Lecture 3.06.pdf"]
---

# Bode Plot

## Definition

> [!note] Definition
> A pair of plots against $\log_{10}\omega$: **magnitude** in dB, $|G|_{dB} = 20\log_{10}|G(i\omega)|$, and **phase** $\angle G(i\omega)$ in degrees. Logs turn products into sums, so a Bode plot is the **sum of the plots of each factor**.

## Explanation

| Factor | Magnitude | Phase |
|---|---|---|
| Gain $k$ | Flat at $20\log\vert k\vert$ | 0° (−180° if $k<0$) |
| $s$ / $1/s$ | ±20 dB/dec through 0 dB at 1 rad/s | ±90° |
| Real zero / pole at $\vert a\vert$ | Flat, then ±20 dB/dec after $\vert a\vert$ (−3 dB error at the corner) | 0 → ±90° over $0.1\vert a\vert$ to $10\vert a\vert$ (±45° at the corner) |
| Complex zeros / poles at $\omega_n$ | Flat, then ±40 dB/dec; a peak or notch if $\zeta<0.707$ | 0 → ±180°, sharper for low $\zeta$ |

**Specifications**:
- **cut-off (corner)**: −3 dB below the low-frequency gain (×0.707);
- **bandwidth**: the range where the gain stays within −3 dB of its low-frequency value;
- **peaking / resonant frequency**: any rise above the low-frequency gain, at $\omega_r$;
- **gain crossover** $\omega_{gc}$: 0 dB;
- **phase crossover** $\omega_{pc}$: −180°.

**Uses in the module**:
- loop shaping and margins ([[Gain and Phase Margins]]);
- reading aircraft modes (phugoid and SPO peaks);
- sensor and filter design: where a sensor is "transparent", where it resonates, and how much phase lag it adds.

## Examples
- PS2 Q1 ($5/(s^2+4s+25)$): −13.98 dB DC, a small peak (−11.3 dB) at 4.12 rad/s, −40 dB/dec; no crossovers ([[SESA2027 Practice Problems 2 Solutions]]).
- PS C Q6 RC filter ($\tau = 0.04$ s): corner at 25 rad/s, −20 dB/dec, −45° at the corner ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_bode_second_order_family.png|560]]

## Related
- [[Frequency Response Function]] · [[Gain and Phase Margins]] · [[Poles and Zeros]]

## Sources
- Lectures 1.09, 2.05, 3.06
