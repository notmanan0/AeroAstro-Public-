---
title: "Frequency Response Function"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["FRF", "frequency response", "G(iω)", "steady-state sinusoidal response", "resonance"]
tags: [sesa2027, concept, frequency-response]
status: complete
parent_lectures: ["[[SESA2027 A5 - Frequency Response and Bode Plots]]"]
related_concepts: ["[[Bode Plot]]", "[[Transfer Function]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 1.08.pdf"]
---

# Frequency Response Function

## Definition

> [!note] Definition
> For a stable LTI system driven by $u = A\sin\omega t$, the steady-state output is
>
> $$x_{ss}(t) = A|G(i\omega)|\sin[\omega t+\angle G(i\omega)]$$
>
> $G(i\omega)$, obtained by substituting $s = i\omega$, is the **frequency response function**. Its magnitude is the amplitude ratio (gain) and its argument is the phase shift.

## Explanation
- **Derivation**: partial fractions of $G(s)U(s)$ split into the **system poles** (the transient, which decays if stable) and the **input poles** $\pm i\omega$ (the steady state).
- **Recipe**: substitute $i\omega$, separate the real and imaginary parts, then compute $|G| = |N|/|D|$ and $\angle G = \angle N-\angle D$. Use `atan2` so the phase continues past −90°.
- **Second order**, $\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$:

$$
|G| = \frac{\omega_n^2}{\sqrt{(\omega_n^2-\omega^2)^2+(2\zeta\omega_n\omega)^2}},\qquad \angle G = -\mathrm{atan2}(2\zeta\omega_n\omega,\ \omega_n^2-\omega^2)
$$

  - At $\omega = \omega_n$: $|G| = 1/(2\zeta)$ and the phase is −90°.
  - Resonant peak at $\omega_r = \omega_n\sqrt{1-2\zeta^2}$ with $M_r = 1/(2\zeta\sqrt{1-\zeta^2})$, which exists only if $\zeta<0.707$.
- **Measuring it**: sine sweeps or broadband input fed through a spectrum analyser. Examples are flight tests (XV-15 tiltrotor) and sensor identification ([[Sensor Dynamic Models]]).

## Examples
- PS1 Q4 ($\omega_n = 1.9$, $\zeta = 0.35$, $\omega = 1.7$): $|G| = 1.521$ and $\angle G = -72.34^\circ$. That is amplification near resonance ([[SESA2027 Practice Problems 1 Solutions]]).
- SPO example ($\omega_n = 1.41$): $|G| = 1.896$ at $\omega_n$ and $2.03\times10^{-2}$ at 10 rad/s.

## Related
- [[Bode Plot]] · [[Transfer Function]] · [[Gain and Phase Margins]]

## Year 1 foundation
- Mechanical FRF (receptance) of an SDOF system: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lecture 1.08
