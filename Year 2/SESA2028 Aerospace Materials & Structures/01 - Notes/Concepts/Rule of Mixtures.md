---
title: "Rule of Mixtures"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Isostrain", "Isostress", "Voigt bound", "Reuss bound", "Inverse rule of mixtures"]
tags: [sesa2028, materials, composites, stiffness, micromechanics]
status: lectured
parent: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
related: ["[[Specific Stiffness and Strength]]", "[[Critical Fibre Length]]", "[[MMC vs CMC]]"]
---

# Rule of Mixtures

The rule of mixtures estimates a unidirectional composite's stiffness from its constituents: along the fibres $E_L=V_fE_f+V_mE_m$, and across them $1/E_T=V_f/E_f+V_m/E_m$.

Along the fibres the fibre and matrix are bonded and stretch together, an isostrain condition. The forces add, so the composite stress is the volume-weighted average of the constituent stresses, and with $\sigma=E\varepsilon$ the same weighting gives the modulus. Because the fibres must carry stress in proportion to their much higher modulus, they take nearly all the load: the ratio of fibre to matrix load is $V_fE_f/(V_mE_m)$, about 27 for 60 % glass in a 4 GPa resin. Across the fibres the load passes through fibre and matrix in series, an isostress condition, so the strains add instead, and the result is dominated by the soft matrix. The longitudinal value is an upper bound and the transverse value a lower bound on the stiffness of any arrangement of the same constituents.

![[materials_isostrain_isostress.png|750]]

The same rules give density and electrical resistivity, and approximate strength along the fibres, $\sigma_L\approx V_f\sigma_f+V_m\sigma_m$. They do not give toughness, which depends on interfaces, pull-out and delamination. For a design requirement $P$, rearranging gives the fibre fraction needed, $V_f=(P-P_m)/(P_f-P_m)$; take the larger of the fractions for stiffness and strength, and remember that more than about 0.65 is hard to make. A hybrid adds a term for each fibre. The same arithmetic applies to metal and ceramic matrices ([[MMC vs CMC]]), and the lecturer calls the rule an exam top tip.

![[materials_rule_of_mixtures.png|700]]

## Related

- Topic: [[SESA2028 M4 - Polymer Matrix Composites|M4]] · [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]]
- Concepts: [[Specific Stiffness and Strength]] · [[Critical Fibre Length]] · [[MMC vs CMC]]
