---
title: "Specific Stiffness and Strength"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, lightweighting, materials-selection, performance-index]
status: complete
parent: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
related: ["[[Rule of Mixtures]]", "[[Euler Buckling]]", "[[Titanium Alloy Classes]]"]
---

# Specific Stiffness and Strength

![[Figures/materials_specific_property_map.png]]

Specific properties divide by density, because for a moving structure mass is the real cost:

$$
\frac E\rho\ (\text{specific stiffness}),\qquad \frac{\sigma_{UTS}}\rho\ (\text{specific strength}).
$$

## Choose the index that matches the loading

Minimising mass for a given stiffness or strength and a fixed length gives the Ashby **performance indices**:

| Component and constraint | Stiffness-limited | Strength-limited |
|---|---|---|
| Tie (tension) | $E/\rho$ | $\sigma/\rho$ |
| Beam in bending; **strut in buckling** | $E^{1/2}/\rho$ | $\sigma^{2/3}/\rho$ |
| Panel or plate in bending or buckling | $E^{1/3}/\rho$ | $\sigma^{1/2}/\rho$ |

The strut index follows from Euler, $P_{cr}\propto EI\propto E\,A^2$: for a fixed load the area scales as $E^{-1/2}$, so mass $\propto\rho/E^{1/2}$ ([[Euler Buckling]]).

## Observations the lecturer wants

- Steel, Al and Ti have almost the **same $E/\rho$** (about 25-27 GPa·cm³/g). Among metals, lightweighting comes from strength, not stiffness, **unless** you alloy with Li or reinforce (MMC), or use Be.
- CFRP dominates both indices **along the fibres**, but compressive strength, transverse properties, damage tolerance and temperature limits all need checking.
- Higher-index members allow smaller sections, so less mass **and** less space (2018-19 and 2020-21 rod questions).

## Table QB2 (MT3 Q5 / 2014-15 B2)

| | $\sigma/\rho$ | $E/\rho$ | $E^{1/2}/\rho$ |
|---|---:|---:|---:|
| CFRP | 882 | 129 | 8.72 |
| GFRP | 450 | 20.5 | 3.05 |
| Steel | 128 | 26.5 | 1.84 |
| Al alloy | 196 | 25.4 | 3.01 |
| Ti alloy | 244 | 26.7 | 2.43 |
