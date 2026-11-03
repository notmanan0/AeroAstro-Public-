---
title: "Ziegler-Nichols Tuning"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part B: Control Systems"
aliases: ["Ziegler–Nichols", "ZN tuning", "ultimate gain", "ultimate period", "quarter decay", "ultimate sensitivity method"]
tags: [sesa2027, concept, control, pid]
status: complete
parent_lectures: ["[[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]]"]
related_concepts: ["[[PID Controller]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 2.06.pdf", "Ziegler & Nichols (1942)"]
---

# Ziegler-Nichols Tuning

Ziegler–Nichols is an empirical way of tuning a PID controller from one experiment. In the ultimate-sensitivity version you use proportional control only and raise $K_p$ until the loop oscillates steadily; that gain is $K_u$ and the oscillation period $T_u$. The gains then come from a table:

| Controller | $K_p$ | $T_I$ | $T_D$ |
|---|---|---|---|
| P | $0.5K_u$ | – | – |
| PI | $0.45K_u$ | $T_u/1.2$ | – |
| PID | $0.6K_u$ | $0.5T_u$ | $0.125T_u$ |

In PS2 Q8, $K_u = 2.4$ and $T_u = 1.1$ s give $K_p = 1.20$ for P; $K_p = 1.08$ and $T_I = 0.917$ s for PI; and $K_p = 1.44$, $T_I = 0.55$ s and $T_D = 0.1375$ s for PID ([[SESA2027 Practice Problems 2 Solutions]]). The lecture's DC servo, with $K_u = 3.7$ and $T_u = 0.924$ s, gives a PID with $K_p = 2.22$; the slide misprints it as 1.22. The other version, the reaction-curve (quarter-decay) method, applies an open-loop step to an S-shaped overdamped plant, measures the delay $L$, time constant $\tau$ and slope $R = A/\tau$, and uses a second table.

$K_u$ is the gain margin expressed as a gain and $2\pi/T_u$ is the phase-crossover frequency, so Ziegler–Nichols is really a margin-based rule. It is also aggressive. It aims for a quarter-decay ratio, each overshoot a quarter of the one before, which for a dominant second-order pair means $\zeta\approx0.22$ and about 50 % first overshoot ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#Ziegler–Nichols: ultimate sensitivity method|derived in B3]]). The rules were developed for process plants, deliberately driving an aircraft into sustained oscillation is unsafe, and the method ignores actuator limits, noise and handling-quality rules. The course treats it as a starting point, to be refined with frequency-response or root-locus design and robustness checks. Tyreus–Luyben (more robust), Cohen–Coon (for plants with dead time) and lambda tuning are the alternatives mentioned.

## Related

- Quarter-decay ratio and the ZN tables: [[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning#4. PID tuning algorithms (L2.06)|B3 §4]]
- [[PID Controller]] · [[Gain and Phase Margins]]
