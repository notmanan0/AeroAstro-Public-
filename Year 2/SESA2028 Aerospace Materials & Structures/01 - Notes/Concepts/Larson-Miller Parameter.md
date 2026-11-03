---
title: "Larson-Miller Parameter"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["LMP", "Larson-Miller", "Time-temperature parameter"]
tags: [sesa2028, materials, creep, lifing]
status: lectured
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Creep Curve and Mechanisms]]", "[[Creep Miner's Rule]]"]
---

# Larson-Miller Parameter

The Larson–Miller parameter $\mathrm{LMP}=T(C+\log_{10}t_r)$, with $T$ in kelvin, $t_r$ in hours and $C\approx20$, combines time and temperature so that one curve of stress against LMP describes an alloy's creep rupture at every temperature.

It comes from the Arrhenius form of the rupture time at constant stress, $t_r=A'\exp(Q/RT)$. Taking logarithms gives $\ln t_r=\ln A'+Q/RT$, and rearranging gives $T(\ln t_r-\ln A')=Q/R$, a constant; in base-10 form with the constant renamed $C$ this is the parameter. It assumes secondary creep controls the life and applies at a fixed stress, so the stress dependence is carried by plotting stress against LMP. The time can be the rupture time or the time to a set strain such as 1 %. For titanium, carbon, chromium–molybdenum and stainless steels the values lie roughly between 20 and 28 thousand.

To find a life, read the LMP at the service stress from the master curve and rearrange: $\log_{10}t_r=\mathrm{LMP}/T-C$. For the lecture's S-590 alloy at 140 MPa and 800 °C, an LMP of 24,000 at 1073 K gives $10^{2.367}=233$ h. The same equivalence justifies accelerated tests: a short test at a higher temperature with the same LMP represents a long life at a lower one, which matters because tests longer than $10^5$ h (11 years) are rare.

Because the life is exponential in LMP, small read-off errors matter: ±200 at 973 K changes the life by a factor of 1.6. An answer should state that uncertainty and apply a safety factor, and should use kelvin, since the parameter is meaningless in °C.

## Related

- Topic: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]
- Concepts: [[Creep Curve and Mechanisms]] · [[Creep Miner's Rule]]
