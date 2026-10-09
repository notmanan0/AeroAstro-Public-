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
sources: ["02 - Sources/Lectures/Lecture 2.05.pdf", "02 - Sources/Lectures/Lecture 2.07.pdf", "02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# Gain and Phase Margins

## Definition

> [!note] Definition
> Computed from the **open-loop** frequency response $L(i\omega) = C(i\omega)G(i\omega)$:
>
> $$GM = -|L(i\omega_{pc})|_{dB}\quad\text{at}\ \angle L = -180^\circ,\qquad PM = 180^\circ+\angle L(i\omega_{gc})\quad\text{at}\ |L| = 1\ (0\ \text{dB})$$
>
> - The GM is the factor by which the gain could increase before the closed loop goes unstable.
> - The PM is the extra phase lag the loop could tolerate before it goes unstable.

## Explanation
- Both margins measure **robustness** to model error, unmodelled dynamics and delay.
- **Typical requirements**: MIL-F-9490D asks for GM ≥ 4.5–6 dB and PM ≥ 30–45°. Civil certification uses qualitative rules (CS-25.672).
- **PM and damping**: for well-behaved second-order loops, $\zeta\approx PM/100$ (PM in degrees), so PM = 55° gives $\zeta\approx0.55$.
- **Delay eats phase margin**: a delay $T_d$ adds phase $-\omega T_d$ with no gain change, so

$$
PM_{new} = PM_{old}-\omega_{gc}T_d
$$

  Sensor lag, filters, ADC conversion, computation and bus latency all subtract from PM ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).
- If $|L|$ never reaches 0 dB, $\omega_{gc}$ does not exist and PM = ∞. If the phase never reaches −180°, GM = ∞. This is the case for a plain second-order plant.
- **Design use**: choose $\omega_{gc}$, add phase lead $\phi_{PD} = PM_{target}-(180^\circ+\angle G(i\omega_{gc}))$, then set $K_p$ so that $|CG| = 1$ ([[PID Controller]]).

## Examples
- PS2 Q7: $\angle G = -155^\circ$ gives a plant PM of 25°. A PD adds 30°, giving PM = 55° ([[SESA2027 Practice Problems 2 Solutions]]).
- PS2 Q1: GM = PM = ∞.
- A 20 ms total latency at $\omega_{gc} = 10$ rad/s costs $0.2$ rad, i.e. 11.5° of PM.

![[amc_gain_phase_margins.png|600]]

## Related
- [[Bode Plot]] · [[PID Controller]] · [[Closed-Loop Transfer Function]] · [[Stability vs Manoeuvrability]]

## Sources
- Lectures 2.05, 2.07, 3.07; MIL-F-9490D
