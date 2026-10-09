---
title: "Creep Curve and Mechanisms"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, creep, high-temperature]
status: complete
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Larson-Miller Parameter]]", "[[Creep Miner's Rule]]", "[[Gamma Prime Strengthening]]", "[[Single Crystal Casting]]"]
---

# Creep Curve and Mechanisms

![[Figures/materials_creep_curve.png]]

**Creep** is time-dependent, permanent deformation under constant load. It becomes significant above about $0.4T_m$ (homologous temperature).

## The curve (constant stress)

1. Instantaneous elastic strain.
2. **Primary**: decelerating. Work hardening dominates recovery.
3. **Secondary / steady state**: constant $\dot\varepsilon$. **Work-hardening rate = recovery rate.** Most of the life, and the design basis.
4. **Tertiary**: accelerating, as cavities, necking and microstructural degradation lead to rupture.

$$
\dot\varepsilon_{ss}=A\sigma^n e^{-Q/RT},\qquad t_r=A'\sigma^{-n}e^{+Q/RT},
$$

where $Q$ is roughly the activation energy for self-diffusion.

## Mechanisms (deformation-mechanism map: $\tau/\mu$ against $T/T_m$)

| Mechanism | Dominates at | How it works |
|---|---|---|
| Dislocation glide (plasticity) | high stress | ordinary yielding |
| **Dislocation (power-law) creep** | high $T$, moderate-high stress | vacancies let edge dislocations **climb** over obstacles, then glide; recovery balances hardening. BCC and HCP slip is thermally activated |
| **Grain-boundary diffusion / sliding** | intermediate $T$ and stress | fast diffusion along disordered boundaries lets grains slide under shear; **much larger strains** than bulk diffusion |
| **Bulk (lattice) diffusion creep** | high $T$, low stress | atoms diffuse to grain faces under tension (vacancies the other way), so grains elongate |

Boundary sliding nucleates **cavities** at triple points and boundaries. They coalesce into **intergranular creep rupture**. Microstructural degradation adds to it: precipitates coarsen or dissolve, recrystallisation, and $\gamma'$ rafting in Ni alloys.

## Designing against creep (link each measure to a mechanism)

| Measure | Mechanism suppressed |
|---|---|
| High $T_m$ base (Ni, refractory metals, ceramics) | everything (lower $T/T_m$) |
| Solutes that slow diffusion (W, Mo, Re) | climb, diffusion creep |
| Stable, coherent precipitates ($\gamma'$) and dispersoids | dislocation creep (pinning, less recovery) |
| Large grains, DS columnar grains aligned with the stress, **single crystals** | boundary sliding, cavitation |
| Boundary carbides (C, B, Zr, Hf) | boundary sliding (in polycrystals) |

**Stress relaxation** is the same mechanism under constant strain: $\sigma=\sigma_0e^{-t/\tau}$.

**Superplasticity** is useful creep: very fine grains plus slow strain rates give boundary sliding and 300-600 % elongation, used for SPF-DB hollow Ti fan blades.
