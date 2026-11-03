---
title: "Creep Miner's Rule"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Robinson's rule", "Creep life fraction rule", "Creep damage summation"]
tags: [sesa2028, materials, creep, lifing, cumulative-damage]
status: lectured
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Larson-Miller Parameter]]", "[[Miner's Rule]]", "[[Creep Curve and Mechanisms]]"]
---

# Creep Miner's Rule

The creep form of Miner's rule says that time $t_i$ spent at a stress and temperature whose rupture life is $t_{r,i}$ uses the fraction $t_i/t_{r,i}$ of the creep life, and that rupture is expected when $\sum t_i/t_{r,i}=1$.

It is the same damage-summation assumption as in fatigue, applied to time fractions instead of cycle fractions; the lecturer stresses that the rule belongs to neither mechanism but is a general assumption about adding damage. Each condition's rupture life is read or interpolated from stress–rupture data. Because rupture life is exponential in temperature and a power law in stress, interpolation must be done on logarithmic axes, in $\log t_r$, never linearly in $t_r$. Once the fractions used so far are added, the remaining life at a new condition is $(1-\sum)\,t_{r,\text{new}}$, which should then be reduced by a safety factor.

![[materials_creep_miner_budgets.png|800]]

The past papers ask for it almost every year: 2013-14 B3(iv) leaves 155 h at 1000 °C after 22 % of an SRR99 blade's life is used; 2021-22 MQ1(d) leaves 70 h at 475 MPa for CM247LC. When the stress–rupture data are exact power laws, a fitted $t_r=B\sigma^{-n}$ can extrapolate beyond the data, but the answer should say it is extrapolating. The rule ignores the order of loading and interactions between conditions, and real creep damage is not strictly linear.

## Related

- Topic: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]] · [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[Larson-Miller Parameter]] · [[Miner's Rule]] · [[Creep Curve and Mechanisms]]
