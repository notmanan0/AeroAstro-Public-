---
title: "S-N Curve and Basquin Law"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, total-life]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Goodman Relation]]", "[[Miner's Rule]]", "[[Total Life vs Damage Tolerance]]"]
---

# S-N Curve and Basquin Law

![[Figures/materials_sn_curves.png]]

An S-N curve plots stress amplitude $\sigma_a$ against cycles to failure $N_f$ (log scale) for smooth specimens.

## Two regimes (boundary about $10^5$ cycles)

**High-cycle fatigue (HCF)**: low, nominally elastic stress, and life dominated by **initiation**. Described by **Basquin's law**:

$$
\frac{\Delta\sigma}{2}=\sigma_f'\,(2N_f)^b,
$$

where $\sigma_f'$ is the fatigue strength coefficient and $b$ the fatigue strength exponent (about $-0.05$ to $-0.12$).

**Low-cycle fatigue (LCF)**: high stress with cyclic plasticity, and early initiation, so growth dominates. Written in **strain**, because a small change in stress gives a large change in plastic strain. Described by **Coffin-Manson**:

$$
\frac{\Delta\varepsilon_p}{2}=\varepsilon_f'\,(2N_f)^c,
$$

where $\varepsilon_f'$ is the fatigue ductility coefficient and $c$ (about $-0.5$ to $-0.7$) the fatigue ductility exponent.

Exam versions often give simplified forms, e.g. $N_f=150\,\Delta\varepsilon^{-1.5}$ (LCF) and $N_f=7.5\times10^9\,\Delta\sigma^{-1.2}$ (HCF) in MT2 Q2.

## Fatigue limit vs endurance limit

- **Steels** (BCC, interstitials pin dislocations) show a true **fatigue limit**: below it, effectively infinite life.
- **Al alloys** do not, so an **endurance limit** is quoted at $10^7$-$10^8$ cycles.

## Sensitivity

S-N data depend strongly on **surface finish** (electropolished ≫ machined), mean stress ([[Goodman Relation]]), environment, size and residual stress. Designing from S-N curves is effectively designing against **initiation** ([[Total Life vs Damage Tolerance]]).

Typical applications: HCF for fuselage and wing vibration and blade flutter; LCF for disc and blade start-stop cycles.
