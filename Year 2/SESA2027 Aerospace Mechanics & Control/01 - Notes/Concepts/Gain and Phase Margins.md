---
title: "Gain and Phase Margins"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["gain margin", "phase margin", "GM", "PM", "stability margins", "crossover frequency"]
tags: [sesa2027, concept, control, robustness]
status: complete
parent_lectures: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]", "[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]", "[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
related_concepts: ["[[Bode Plot]]", "[[PID Controller]]", "[[Closed-Loop Transfer Function]]", "[[Nyquist Sampling and Aliasing]]"]
sources: ["02 - Sources/Lectures/Lecture 2.05.pdf", "02 - Sources/Lectures/Lecture 2.07.pdf", "02 - Sources/Lectures/Lecture 3.07.pdf", "MIL-F-9490D"]
---

# Gain and Phase Margins

The gain and phase margins measure how far a feedback loop is from instability, read off the open-loop frequency response $L(i\omega) = C(i\omega)G(i\omega)$:

$$
GM = -|L(i\omega_{pc})|_{dB}\quad\text{at}\ \angle L = -180^\circ,\qquad PM = 180^\circ+\angle L(i\omega_{gc})\quad\text{at}\ |L| = 1\ (0\ \text{dB}).
$$

The gain margin is the factor by which the loop gain could rise before the closed loop goes unstable; the phase margin is the extra phase lag it could tolerate. Both are measures of robustness to model error, unmodelled dynamics and delay. MIL-F-9490D asks for GM of at least 4.5–6 dB and PM of 30–45°, while civil certification (CS-25.672) uses qualitative rules. For well-behaved second-order loops there is a useful rule of thumb, $\zeta\approx PM/100$ with PM in degrees, so a 55° margin gives $\zeta\approx0.55$. If $|L|$ never reaches 0 dB there is no gain crossover and PM is infinite; if the phase never reaches −180°, GM is infinite. A plain second-order plant has both, as in PS2 Q1.

Delay is the main enemy of phase margin. A delay $T_d$ adds phase $-\omega T_d$ without changing the gain, so

$$
PM_{new} = PM_{old}-\omega_{gc}T_d ,
$$

and sensor lag, filters, ADC conversion, computation and bus latency all subtract from it ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]). A 20 ms total latency at $\omega_{gc} = 10$ rad/s costs 0.2 rad, or 11.5°.

The margins also drive design. Choose $\omega_{gc}$, add the phase lead $\phi_{PD} = PM_{target}-(180^\circ+\angle G(i\omega_{gc}))$, then set $K_p$ so that $|CG| = 1$ at $\omega_{gc}$ ([[PID Controller]]). In PS2 Q7 the plant phase is −155°, a margin of 25°, and a PD controller adding 30° brings it to 55° ([[SESA2027 Practice Problems 2 Solutions]]).

![[amc_gain_phase_margins.png|600]]

## Related

- Why GM and PM measure the distance to instability: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#1. Why frequency-response design (L2.05)|B3 §1]]
- [[Bode Plot]] · [[PID Controller]] · [[Closed-Loop Transfer Function]] · [[Stability vs Manoeuvrability]]
