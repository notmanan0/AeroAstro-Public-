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
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 1.06.pdf"]
---

# Phugoid Mode

## Definition

> [!note] Definition
> The **slow, lightly damped** longitudinal mode. It is a long-period exchange of kinetic and potential energy at roughly **constant angle of attack**:
> $$mgh+\tfrac12mV^2\approx\text{const}$$
> The aircraft climbs and slows, then dives and speeds up, with a period of tens of seconds to minutes.

## Explanation
- The states involved are mainly $u$, $\theta$ and height. $\alpha$ and $q$ stay small.
- **Damping** comes only from the drag difference across the cycle: drag is higher in the fast, low part, so energy is slowly dissipated. The damping is therefore very light, and the mode can be slightly **unstable**.
- **Lanchester's approximation** (drag neglected) gives $\omega_{ph}\approx\sqrt2\,g/U_\infty$, so $T\approx\pi\sqrt2\,U_\infty/g$. The period is proportional to speed.
- Pilots correct it easily because it is so slow. Autopilots (altitude or speed hold) suppress it.
- It appears as a sharp, low-frequency resonance on the Bode plot. For example, Blakelock's $\theta/\delta_e$ has $\omega_n = 0.073$ rad/s.

## Examples
- L1.05 example: $\lambda = -0.00125\pm0.0707i$, $T = 88.9$ s, $t_{1/2} = 554$ s, $\zeta = 0.018$.
- F-4C: $\lambda = -0.0065\pm0.0779i$, $\zeta = 0.083$.
- PS1 Q1 (**unstable**): $\lambda = 8\times10^{-4}\pm0.040i$, $T = 157$ s, $t_2 = 866$ s ([[SESA2027 Practice Problems 1 Solutions]]).

## Related
- [[Short Period Oscillation]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]] · [[Routh-Hurwitz Stability Criterion]]

## Sources
- Lectures 1.05–1.06; Cook (2013), Ch. 6–7
