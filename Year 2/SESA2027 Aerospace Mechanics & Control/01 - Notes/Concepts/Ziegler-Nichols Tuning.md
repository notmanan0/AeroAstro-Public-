---
title: "Ziegler-Nichols Tuning"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["Ziegler–Nichols", "ZN tuning", "ultimate gain", "ultimate period", "quarter decay"]
tags: [sesa2027, concept, control, pid]
status: complete
parent_lectures: ["[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
related_concepts: ["[[PID Controller]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 2.06.pdf"]
---

# Ziegler-Nichols Tuning

## Definition

> [!note] Definition
> An empirical PID tuning method. The **ultimate sensitivity** version:
> 1. Use P control only and raise $K_p$ until the loop oscillates steadily. That gain is $K_u$, and the oscillation period is $T_u$.
> 2. Read the gains from the table below.
>
> | Controller | $K_p$ | $T_I$ | $T_D$ |
> |---|---|---|---|
> | P | $0.5K_u$ | – | – |
> | PI | $0.45K_u$ | $T_u/1.2$ | – |
> | PID | $0.6K_u$ | $0.5T_u$ | $0.125T_u$ |

## Explanation
- **Reaction-curve (quarter-decay) version**: apply an open-loop step to an S-shaped, overdamped plant. Measure the delay $L$, the time constant $\tau$ and the slope $R = A/\tau$, then use a second table.
- $K_u$ is the gain margin (as a gain), and $2\pi/T_u$ is the phase crossover frequency, so ZN is really a margin-based rule.
- **Why it is aggressive**:
  - it targets quarter-amplitude decay, which means $\zeta\approx0.2$ and 25 % or more overshoot;
  - the rules were derived for process plants;
  - driving an aircraft to sustained oscillation is unsafe;
  - it takes no account of actuator limits, noise or handling-qualities rules.
- **Use it as a starting point**, then refine with frequency-response or root-locus design and robustness checks. Alternatives include Tyreus–Luyben (more robust), Cohen–Coon (for dead time) and lambda tuning.

## Examples
- PS2 Q8 ($K_u = 2.4$, $T_u = 1.1$ s):
  - P: $K_p = 1.20$.
  - PI: $K_p = 1.08$, $T_I = 0.917$ s.
  - PID: $K_p = 1.44$, $T_I = 0.55$ s, $T_D = 0.1375$ s ([[SESA2027 Practice Problems 2 Solutions]]).
- Lecture DC servo: $K_u = 3.7$ and $T_u = 0.924$ s give a PID with $K_p = 2.22$ (the slide misprints 1.22).

## Related
- [[PID Controller]] · [[Gain and Phase Margins]]

## Sources
- Lecture 2.06; Ziegler & Nichols (1942)
