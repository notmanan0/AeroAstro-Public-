---
title: "Rule of Mixtures"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, composites, stiffness, micromechanics]
status: complete
parent: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
related: ["[[Specific Stiffness and Strength]]", "[[Critical Fibre Length]]", "[[MMC vs CMC]]"]
---

# Rule of Mixtures

![[Figures/materials_rule_of_mixtures.png]]

For a unidirectional composite with fibre volume fraction $V_f$ and $V_m=1-V_f$:

## Longitudinal (isostrain, Voigt): the upper bound

Fibres and matrix strain together, and the loads add:

$$
E_L=V_fE_f+V_mE_m,\qquad \sigma_L\approx V_f\sigma_f+V_m\sigma_m,\qquad \rho_c=V_f\rho_f+V_m\rho_m.
$$

The load fraction carried by the fibres is $V_fE_f/E_L$, which is nearly all of it for carbon/epoxy.

## Transverse (isostress, Reuss): the lower bound

Fibres and matrix carry the same stress, and the strains add:

$$
\frac1{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m}.
$$

$E_T$ is dominated by the matrix, so there is little improvement across the fibres.

## Required volume fraction

$$
V_f=\frac{P_{req}-P_m}{P_f-P_m}
$$

Do this separately for stiffness and strength, and **take the larger**. Treat $V_f\gtrsim0.6$-0.7 as impractical to manufacture.

## Worked results

| Case | $E_L$ | $E_T$ |
|---|---:|---:|
| 60 % glass (72.5) / resin (4) | 45.1 GPa | 9.24 GPa |
| 55 % carbon (325) / epoxy (3.1) | 180 GPa | 6.81 GPa |

**Hybrids:** $E=V_{f1}E_{f1}+V_{f2}E_{f2}+V_mE_m$.

## Limits

The rule works well for density, longitudinal stiffness and electrical conductivity. It is **not valid for toughness**, which depends on interfaces, pull-out and delamination. Strength is only approximate: in reality the matrix stress at fibre-failure strain should be used, not $\sigma_m$. Applying the rule to *specific* properties, as in 2023-24 MQ2, is only an approximation, but it is what the question intends. For ceramic matrices, check whether the quoted strengths are compressive.
