---
title: "Damping Ratio and Natural Frequency"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["damping ratio", "natural frequency", "zeta", "omega_n", "half-life", "time to double", "second-order system"]
tags: [sesa2027, concept, dynamics]
status: complete
parent_lectures: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2027 B2 - Root Locus Method]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Characteristic Equation and Eigenvalues]]", "[[Step Response Specifications]]", "[[Root Locus]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "02 - Sources/Lectures/Lecture 2.04.pdf"]
---

# Damping Ratio and Natural Frequency

Any second-order mode can be written in terms of a natural frequency $\omega_n$ and a damping ratio $\zeta$:

$$
\lambda^2+2\zeta\omega_n\lambda+\omega_n^2 = 0\quad\Rightarrow\quad\lambda = -\zeta\omega_n\pm i\omega_n\sqrt{1-\zeta^2} = \sigma\pm i\omega .
$$

So for a quadratic $\lambda^2+a\lambda+b$, $\omega_n = \sqrt b$ and $\zeta = a/(2\sqrt b)$; from the roots, $\omega_n = \sqrt{\sigma^2+\omega^2}$ and $\zeta = -\sigma/\omega_n$. The names come from the mass–spring–damper $m\ddot x+c\dot x+kx = 0$, where $\omega_n = \sqrt{k/m}$ and $\zeta = c/(2\sqrt{km})$ ([[FEEG1002 D6 - Single Degree of Freedom Vibration]] covers this, with the log decrement).

| $\zeta$ | Response |
|---|---|
| $<0$ | Unstable (growing oscillation) |
| $0$ | Undamped (sustained oscillation) |
| $0<\zeta<1$ | Underdamped (decaying oscillation) |
| $1$ | Critically damped |
| $>1$ | Overdamped (two real poles, no overshoot) |

The time characteristics follow from the roots: the period is $T = 2\pi/\omega$, the half-life of a stable mode $t_{1/2} = \ln2/|\sigma|$, and the time to double of an unstable one $t_2 = \ln2/\sigma$. In the s-plane, $\omega_n$ is the pole's distance from the origin and $\zeta = \cos\beta$, where $\beta$ is the angle from the negative real axis, so lines of constant damping are rays from the origin.

In L1.05 the SPO has $\omega_n = 1.41$ rad/s and $\zeta = 0.35$, the phugoid $\omega_n = 0.0707$ rad/s and $\zeta = 0.018$. PS1 Q2 gives $\omega_n = 5.429$ rad/s, $\zeta = 0.162$, $T = 1.173$ s and $t_{1/2} = 0.790$ s ([[SESA2027 Practice Problems 1 Solutions]]). The course quotes two design targets: Level 1, Category A handling needs an SPO damping ratio between 0.35 and 1.30, and second-order sensors are usually built with $\zeta\approx0.7$ (PS C Q5 compares $\zeta = 0.2$, 0.7 and 1.2; [[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_s_plane_modes.png|520]]

## Related

- [[Characteristic Equation and Eigenvalues]] · [[Step Response Specifications]] · [[Root Locus]] · [[Short Period Oscillation]]
