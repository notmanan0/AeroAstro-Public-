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
sources: ["02 - Sources/Lectures/Lecture 2.08.pdf", "Cook (2007), Ch. 10", "Etkin (2000)"]
---

# Stability vs Manoeuvrability

Stability is an aircraft's tendency to return to trim after a disturbance; manoeuvrability is its ability to change flight path quickly on command. Statically, stability needs $C_{m_\alpha}<0$ and, dynamically, decaying modes. Manoeuvrability needs a large $|\partial q/\partial\eta|$, high bandwidth and a high $\omega_n$. Pushing one generally costs the other.

| Highly stable | Highly manoeuvrable |
|---|---|
| Large static margin, large negative $C_{m_\alpha}$ | Small or negative margin (relaxed stability) |
| High $\zeta$, lower $\omega_n$ | Lower $\zeta$, higher $\omega_n$ |
| Sluggish, smooth, low workload | Quick, agile, high control power needed |
| Transports (B777, A350), gliders | Fighters (F-16, Typhoon: unstable, fly-by-wire) |

The trade shows up on the SPO poles: more stability moves them left (better damped but slower), more manoeuvrability moves them outwards and to the right (faster but less damped). The link to the static margin is $M_w = -H_sC_{L^*_\alpha}$ ([[Neutral Point and Static Margin]]). A large $H_s$ gives a stiff, stable aircraft that needs a large trim load and responds sluggishly.

How much is enough is set by handling-quality criteria: the Cooper–Harper rating (1–10) and Levels 1–3, the SPO damping limits (Level 1: Category A 0.35–1.30, B 0.30–2.00, C 0.50–1.30) and the $\omega_n$ against $\zeta$ thumbprint. PS1 Q2 falls outside them: at 356 m/s, $\zeta = 0.16<0.35$, so the aircraft needs a stability augmentation system ([[SESA2027 Practice Problems 1 Solutions]]). Modern aircraft resolve the trade with synthetic stability. The airframe is made agile or even unstable, and the flight control system supplies the damping and stability through pitch-rate feedback, filters and gain scheduling.

## Related

- [[Neutral Point and Static Margin]] · [[Short Period Oscillation]] · [[Gain and Phase Margins]] · [[Manoeuvre Point and Manoeuvre Margin]]
