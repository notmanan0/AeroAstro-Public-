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

## Definition

> [!note] Definition
> Any second-order mode can be written as
> $$\lambda^2+2\zeta\omega_n\lambda+\omega_n^2 = 0\quad\Rightarrow\quad\lambda = -\zeta\omega_n\pm i\omega_n\sqrt{1-\zeta^2} = \sigma\pm i\omega$$
> For a quadratic $\lambda^2+a\lambda+b$: $\omega_n = \sqrt b$ and $\zeta = a/(2\sqrt b)$. From the roots: $\omega_n = \sqrt{\sigma^2+\omega^2}$ and $\zeta = -\sigma/\omega_n$.

## Explanation
- This is the mass–spring–damper analogy: $m\ddot x+c\dot x+kx = 0$ gives $\omega_n = \sqrt{k/m}$ and $\zeta = c/(2\sqrt{km})$.

| $\zeta$ | Response |
|---|---|
| $<0$ | Unstable (growing oscillation) |
| $0$ | Undamped (sustained oscillation) |
| $0<\zeta<1$ | Underdamped (decaying oscillation) |
| $1$ | Critically damped |
| $>1$ | Overdamped (two real poles, no overshoot) |

- **Time characteristics**:
  - period $T = 2\pi/\omega$;
  - half-life $t_{1/2} = \ln2/|\sigma|$;
  - time to double $t_2 = \ln2/\sigma$ (if $\sigma>0$).
- **In the s-plane**:
  - $\omega_n$ is the distance of the pole from the origin;
  - $\zeta = \cos\beta$, where $\beta$ is the angle from the negative real axis;
  - lines of constant $\zeta$ are rays from the origin.
- **Design targets**:
  - SPO: Level 1 Category A needs $0.35\le\zeta\le1.30$.
  - Second-order sensors: $\zeta\approx0.7$.

## Examples
- L1.05: SPO $\omega_n = 1.41$ rad/s, $\zeta = 0.35$; phugoid $\omega_n = 0.0707$ rad/s, $\zeta = 0.018$.
- PS1 Q2: $\omega_n = 5.429$ rad/s, $\zeta = 0.162$, $T = 1.173$ s, $t_{1/2} = 0.790$ s ([[SESA2027 Practice Problems 1 Solutions]]).
- PS C Q5: sensors with $\zeta = 0.2, 0.7, 1.2$ ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_s_plane_modes.png|520]]

## Related
- [[Characteristic Equation and Eigenvalues]] · [[Step Response Specifications]] · [[Root Locus]] · [[Short Period Oscillation]]

## Year 1 foundation
- Mass–spring–damper origin of $\omega_n$ and $\zeta$, with the log decrement: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources
- Lectures 1.05, 2.04, 3.05
