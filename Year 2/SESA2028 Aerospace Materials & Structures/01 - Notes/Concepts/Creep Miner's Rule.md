---
title: "Creep Miner's Rule"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, creep, lifing, cumulative-damage]
status: complete
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Larson-Miller Parameter]]", "[[Miner's Rule]]", "[[Creep Curve and Mechanisms]]"]
---

# Creep Miner's Rule

![[Figures/materials_creep_miner_budgets.png]]

Assume each (stress, temperature) condition uses up life in proportion to the time spent there:

$$
\sum_i\frac{t_i}{t_{r,i}}=1\quad\text{at rupture}.
$$

## Procedure

1. **Find $t_r$ at each condition.** Rupture life is exponential in $T$ and a power law in $\sigma$, so **interpolate linearly in $\log t_r$** (against $T$, or against $\log\sigma$). The lecturer uses a log-log plot. Never interpolate $t_r$ itself linearly.
2. Fraction used $=\sum t_i/t_{r,i}$.
3. Remaining time at the new condition $=(1-\sum)\,t_{r,new}$.
4. Apply a safety factor and state the assumptions.

## Lecture example: SRR99 at 400 MPa

Data: 700 °C 100,000 h; 800 °C 10,000 h; 900 °C 1,050 h; 1000 °C 200 h; 1100 °C 15 h.

$$
\frac{500}{3163}+\frac{2100}{31623}=0.158+0.066=0.224
$$

$$
t_{remaining}=(1-0.224)\times200\approx155\ \text{h at }1000\ ^\circ\text{C}.
$$

## Stress-varying data and power-law fits

When the data are at a fixed temperature and varying stress, fit $t_r=B\sigma^{-n}$ on log-log axes (2017-18 asks for this "by graphical means"). The exam data sets turn out to be exact power laws ($n=6$ or $n=4$), so extrapolating to stresses outside the data (650 MPa, 825 MPa) is possible. Say that it is an extrapolation.

## Assumptions and limitations

- Damage is linear and **order-independent** (a hot-then-cool sequence may not equal cool-then-hot).
- It ignores microstructural history (precipitate coarsening, rafting), oxidation and environment, and creep-fatigue interaction.
- The interpolation method affects the answer (e.g. 3,240 h vs the lecturer's 3,163 h).
