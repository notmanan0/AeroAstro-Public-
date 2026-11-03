---
title: "Phugoid Mode"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["phugoid", "long-period mode"]
tags: [sesa2027, concept, flight-dynamics, modes]
status: complete
parent_lectures: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
related_concepts: ["[[Short Period Oscillation]]", "[[Damping Ratio and Natural Frequency]]", "[[Characteristic Equation and Eigenvalues]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 1.06.pdf", "Cook (2013), Ch. 6–7"]
---

# Phugoid Mode

The **phugoid** is the slow, lightly damped longitudinal mode: a long-period exchange of kinetic and potential energy at roughly constant angle of attack, with $mgh+\tfrac12mV^2$ nearly constant. The aircraft climbs and slows, then dives and speeds up, with a period of tens of seconds to minutes.

The states that take part are mainly $u$, $\theta$ and height, while $\alpha$ and $q$ stay small. The only damping comes from the difference in drag across the cycle. Drag is higher in the fast, low part, so a little energy is lost each cycle, but not much, and the mode can even be slightly unstable. Lanchester's approximation, which neglects drag altogether, gives $\omega_{ph}\approx\sqrt2\,g/U_\infty$, so the period $T\approx\pi\sqrt2\,U_\infty/g$ is proportional to speed. Because it is so slow, pilots correct it without noticing, and altitude- or speed-hold autopilots suppress it. On a Bode plot it shows up as a sharp low-frequency resonance; Blakelock's $\theta/\delta_e$, for instance, has $\omega_n = 0.073$ rad/s.

The L1.05 example has $\lambda = -0.00125\pm0.0707i$, giving $T = 88.9$ s, $t_{1/2} = 554$ s and $\zeta = 0.018$. The F-4C phugoid is $\lambda = -0.0065\pm0.0779i$ with $\zeta = 0.083$. In PS1 Q1 it is unstable, $\lambda = 8\times10^{-4}\pm0.040i$, with $T = 157$ s and a time to double of 866 s ([[SESA2027 Practice Problems 1 Solutions]]).

## Related

- F-4C phugoid time history: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid#3. Physical description of the modes|A3 §3]]
- [[Short Period Oscillation]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]] · [[Routh-Hurwitz Stability Criterion]]
