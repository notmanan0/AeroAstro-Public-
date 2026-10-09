---
title: "Miner's Rule"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, cumulative-damage, total-life]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[S-N Curve and Basquin Law]]", "[[Creep Miner's Rule]]", "[[Total Life vs Damage Tolerance]]"]
---

# Miner's Rule

Miner's (Palmgren-Miner) rule adds up fatigue damage from blocks of different severity. Block $i$ applies $n_i$ cycles at a level whose life is $N_i$, so it uses up the fraction $n_i/N_i$:

$$
\sum_i\frac{n_i}{N_i}=1\quad\text{at failure}.
$$

## Procedure

1. Reduce the service history to blocks. **Rainflow counting** turns an irregular signal (e.g. storm loading on an offshore platform) into counted cycles.
2. Find each $N_i$ from the S-N (stress) or $\varepsilon$-N (strain) curve.
3. Add up the fractions already used. Remaining life at a new level = $(1-\sum)\,N_{new}$.
4. Apply a safety factor.

## Worked example (MT2 Q2 / 2018-19 A2(i))

$$
\frac{550}{150(0.23)^{-1.5}}+\frac{2.53\times10^6}{7.5\times10^9(320)^{-1.2}}=0.404+0.342=0.747,
$$

$$
N_{remaining}=(1-0.747)\times150(0.18)^{-1.5}=0.253\times1964\approx498\ \text{stop-starts}\ (\approx250\ \text{with SF 2}).
$$

## Limitations

- Assumes damage accumulates **linearly** and **sequence does not matter**. High-then-low loading is usually more damaging than low-then-high.
- Ignores load interaction (overload retardation) and mean-stress effects, unless each $N_i$ is Goodman-corrected.
- Real failure sums range from about 0.3 to 3.

The same idea is used for creep, with time fractions ([[Creep Miner's Rule]]).
