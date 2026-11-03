---
title: "Creep Curve and Mechanisms"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Creep", "Secondary creep", "Power-law creep", "Diffusion creep", "Grain-boundary sliding", "Stress relaxation", "Superplasticity"]
tags: [sesa2028, materials, creep, high-temperature]
status: lectured
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Larson-Miller Parameter]]", "[[Creep Miner's Rule]]", "[[Gamma Prime Strengthening]]", "[[Single Crystal Casting]]"]
---

# Creep Curve and Mechanisms

Creep is time-dependent permanent deformation under a constant load, significant above about 40 % of the absolute melting temperature, and its steady-state rate follows $\dot\varepsilon_{ss}=A\sigma^n\exp(-Q/RT)$ with $Q$ close to the activation energy for self-diffusion.

At constant stress a creep curve shows an instantaneous elastic strain, a primary stage whose rate falls as work hardening outpaces recovery, a secondary stage at constant rate where hardening and recovery balance, and a tertiary stage that accelerates to rupture as damage builds up. Secondary creep usually dominates the life and sets design limits, such as a blade's growth towards its casing. The rupture time is the inverse, $t_r\propto\sigma^{-n}\exp(Q/RT)$, so modest changes in stress or temperature change the life greatly. At fixed strain instead of fixed load the same process relaxes the stress, $\sigma=\sigma_0e^{-t/\tau}$, which is how bolts lose preload.

![[materials_creep_mechanisms.png|850]]

Which mechanism operates depends on stress and homologous temperature, as a deformation-mechanism map shows. At higher stresses, dislocations glide and climb: vacancies diffusing to an edge dislocation's half-plane let it climb over precipitates. At high temperature and low stress, atoms diffuse through the grains to the faces under tension and the grains lengthen (Nabarro–Herring creep). In between, much faster diffusion along grain boundaries lets them slide under shear; sliding opens cavities at triple points that link up into intergranular rupture. Precipitates coarsen or dissolve and the microstructure recovers and recrystallises at the same time.

Resisting creep means attacking each mechanism: a high melting point, a microstructure that stays stable, solutes that slow diffusion, precipitates and dispersoids that pin dislocations, and few grain boundaries or boundaries aligned with the load, the logic behind directionally solidified and single-crystal blades. The same grain-boundary sliding, in nanometre-grained metals at slow strain rates, gives superplastic elongations of several hundred per cent, used to blow-form complex shapes.

![[materials_creep_curve.png|700]]

## Related

- Topic: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]
- Concepts: [[Larson-Miller Parameter]] · [[Creep Miner's Rule]] · [[Gamma Prime Strengthening]] · [[Single Crystal Casting]] · [[Hall-Petch Relation]]
