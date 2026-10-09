---
title: "Stability vs Manoeuvrability"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["stability versus manoeuvrability", "relaxed static stability", "handling qualities", "Cooper-Harper", "thumbprint"]
tags: [sesa2027, sesa2022, concept, handling-qualities]
status: complete
parent_lectures: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Short Period Oscillation]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 2.08.pdf"]
---

# Stability vs Manoeuvrability

## Definition

> [!note] Definition
> A fundamental design trade-off:
> - **Stability** is the tendency to return to trim after a disturbance. Statically it needs $C_{m_\alpha}<0$; dynamically, decaying modes.
> - **Manoeuvrability** is the ability to change the flight path quickly on command: a large $|\partial q/\partial\eta|$, high bandwidth and a high $\omega_n$.
>
> Increasing one generally reduces the other.

## Explanation

| Highly stable | Highly manoeuvrable |
|---|---|
| Large static margin, large negative $C_{m_\alpha}$ | Small or negative margin (**relaxed stability**) |
| High $\zeta$, lower $\omega_n$ | Lower $\zeta$, higher $\omega_n$ |
| Sluggish, smooth, low workload | Quick, agile, high control power needed |
| Transports (B777, A350), gliders | Fighters (F-16, Typhoon: unstable, fly-by-wire) |

- **On the SPO poles**:
  - stability moves them left (better damped, slower);
  - manoeuvrability moves them outward and right (faster, less damped).
- **Static margin link**: $M_w = -H_sC_{L^*_\alpha}$ ([[Neutral Point and Static Margin]]). A large $H_s$ gives a stiff, stable aircraft that needs a large trim load and responds sluggishly.
- **Handling qualities**:
  - Cooper–Harper rating (1–10) and Levels 1–3;
  - SPO damping limits (Level 1: Category A 0.35–1.30, B 0.30–2.00, C 0.50–1.30);
  - the $\omega_n$ vs $\zeta$ "thumbprint".
- **Resolution in modern aircraft**: **synthetic stability**. The airframe is made agile (or even unstable), and the flight control system supplies damping and stability through pitch-rate feedback, filters and gain scheduling.

## Examples
- PS1 Q2: at 356 m/s, $\zeta = 0.16<0.35$, so a stability augmentation system is needed ([[SESA2027 Practice Problems 1 Solutions]]).

## Related
- [[Neutral Point and Static Margin]] · [[Short Period Oscillation]] · [[Gain and Phase Margins]] · [[Manoeuvre Point and Manoeuvre Margin]]

## Sources
- Lecture 2.08; Cook (2007), Ch. 10; Etkin (2000)
