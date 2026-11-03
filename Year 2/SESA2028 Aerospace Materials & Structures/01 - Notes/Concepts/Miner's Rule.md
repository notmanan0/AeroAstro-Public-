---
title: "Miner's Rule"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Palmgren-Miner rule", "Miner's law of cumulative damage", "Linear damage rule"]
tags: [sesa2028, materials, fatigue, cumulative-damage, total-life]
status: lectured
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[S-N Curve and Basquin Law]]", "[[Creep Miner's Rule]]", "[[Total Life vs Damage Tolerance]]"]
---

# Miner's Rule

Miner's rule says that $n_i$ cycles at a stress level whose fatigue life is $N_i$ use up the fraction $n_i/N_i$ of the life, and that failure is expected when the fractions add up to one, $\sum n_i/N_i=1$.

It exists because laboratory S-N curves are measured at one amplitude and one mean stress, while a real structure sees a mixed schedule; the lecturer's example is an offshore platform loaded by the weather. The service history is first broken into blocks of cycles at each amplitude and mean stress by rainflow counting. Each block's life $N_i$ comes from the fitted S-N law (stress for high-cycle fatigue, strain for low-cycle), and the fractions are added. If the sum so far is $D$, the remaining life at a new level with life $N$ is $(1-D)N$, which should then be reduced by a safety factor.

In the MT2 blade example, 550 start-stops at $\Delta\varepsilon=0.23$ (life 1360) and $2.53\times10^6$ vibration cycles at 320 MPa (life $7.39\times10^6$) have used $0.404+0.342=0.747$ of the life, leaving $0.253\times1964\approx498$ start-stops at $\Delta\varepsilon=0.18$, or about 250 with a safety factor of 2 ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing#Combined low- and high-cycle fatigue on a blade|M2]]).

The rule assumes damage builds up linearly and that the order of the blocks does not matter. Neither is quite true: a high-then-low sequence is usually more damaging than low-then-high, and overloads can slow later growth. Mean stress is included only if each $N_i$ is read from the right curve or corrected with the [[Goodman Relation]]. The same bookkeeping, with time fractions instead of cycle fractions, is used for creep ([[Creep Miner's Rule]]).

## Related

- Topic: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]] · [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]
- Concepts: [[S-N Curve and Basquin Law]] · [[Goodman Relation]] · [[Total Life vs Damage Tolerance]] · [[Creep Miner's Rule]]
