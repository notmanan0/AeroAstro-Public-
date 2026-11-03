---
title: "Frequency Response Function"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["FRF", "frequency response", "G(iω)", "steady-state sinusoidal response", "resonance", "sinusoidal transfer function"]
tags: [sesa2027, concept, frequency-response]
status: complete
parent_lectures: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
related_concepts: ["[[Bode Plot]]", "[[Transfer Function]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 1.08.pdf"]
---

# Frequency Response Function

When a stable LTI system is driven by $u = A\sin\omega t$, its steady-state output is a sinusoid at the same frequency, scaled and shifted:

$$
x_{ss}(t) = A|G(i\omega)|\sin[\omega t+\angle G(i\omega)] .
$$

$G(i\omega)$, the transfer function with $s = i\omega$, is the **frequency response function**: its magnitude is the gain and its argument the phase shift.

The result comes from partial fractions of $G(s)U(s)$. The terms from the system's poles are the transient, which dies away if the system is stable, and the terms from the input's poles at $\pm i\omega$ are what remains. To evaluate $G(i\omega)$ by hand, substitute $i\omega$, separate real and imaginary parts, and take $|G| = |N|/|D|$ and $\angle G = \angle N-\angle D$, using `atan2` so the phase carries on past −90°. For the standard second-order system $\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$,

$$
|G| = \frac{\omega_n^2}{\sqrt{(\omega_n^2-\omega^2)^2+(2\zeta\omega_n\omega)^2}},\qquad \angle G = -\mathrm{atan2}(2\zeta\omega_n\omega,\ \omega_n^2-\omega^2).
$$

At $\omega = \omega_n$ the gain is $1/(2\zeta)$ and the phase −90°. If $\zeta<0.707$ there is a resonant peak $M_r = 1/(2\zeta\sqrt{1-\zeta^2})$ at $\omega_r = \omega_n\sqrt{1-2\zeta^2}$. In PS1 Q4 ($\omega_n = 1.9$, $\zeta = 0.35$, $\omega = 1.7$) the input is amplified near resonance, $|G| = 1.521$ with $\angle G = -72.34^\circ$ ([[SESA2027 Practice Problems 1 Solutions]]). For the lecture's SPO ($\omega_n = 1.41$), $|G| = 1.896$ at $\omega_n$ but only $2.03\times10^{-2}$ at 10 rad/s.

In practice an FRF is measured with sine sweeps or broadband input fed through a spectrum analyser, as in the XV-15 tiltrotor flight tests and in sensor identification ([[Sensor Dynamic Models]]). The mechanical version, the receptance of a single-degree-of-freedom system, is in [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Related

- Steady state from complex partial fractions: [[SESA2027 A5 - Frequency Response and Bode Plots#2. Response to a sinusoidal input|A5 §2]]
- [[Bode Plot]] · [[Transfer Function]] · [[Gain and Phase Margins]]
