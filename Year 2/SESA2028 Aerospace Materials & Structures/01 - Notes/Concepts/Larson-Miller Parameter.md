---
title: "Larson-Miller Parameter"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, creep, lifing]
status: complete
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Creep Curve and Mechanisms]]", "[[Creep Miner's Rule]]"]
---

# Larson-Miller Parameter

![[Figures/materials_lmp_rupture_time_map.png]]

## Derivation

At fixed stress, $t_r=A'\exp(Q/RT)$. Take logs:

$$
\ln t_r=\ln A'+\frac Q{RT}\;\Rightarrow\;T(\ln t_r-\ln A')=\frac QR=\text{constant at that stress}.
$$

In base 10:

$$
\mathrm{LMP}=T\,(C+\log_{10}t_r),
$$

where $T$ is in **K**, $t_r$ in **h**, and $C\approx20$ (empirical). $t$ can also be the time to a set strain.

A single master curve of $\log\sigma$ against LMP collapses rupture data from all temperatures. That lets short, hot tests be converted to long, cooler service lives.

## Method

1. Read the LMP at the service stress from the curve (note the axis units, e.g. ×10³).
2. $\log_{10}t_r=\mathrm{LMP}/T-C$, with $T$ **in kelvin**.
3. Apply a **safety factor** (the lecturer deducts a mark without one) and comment on read-off sensitivity.

## Worked examples

- Lecture, S-590 iron, 140 MPa at 800 °C: LMP = 24.0×10³, so $\log t_r=24000/1073-20=2.367$, giving $t_r=233$ h.
- 2014-15 B1(iv), 500 MPa at 700 °C: $\log\sigma=2.699$ gives LMP 26.4×10³, so $\log t_r=7.13$, giving $1.35\times10^7$ h.
- 2015-16 B3(iv), Alloy 738, 300 MPa at 785 °C: LMP 25.0×10³, so $\log t_r=3.629$, giving **4,261 h** (then SF 2: about 2,100 h).
- 2020-21 G92 uses $C=35.28$. Always use the constant the question gives.

## Sensitivity

An error $\delta$ in the LMP read-off changes $\log t_r$ by $\delta/T$. At 700 °C, ±200 changes $t_r$ by a factor of about 1.6. Extrapolating the master curve beyond the test data is risky (mechanisms may change).
