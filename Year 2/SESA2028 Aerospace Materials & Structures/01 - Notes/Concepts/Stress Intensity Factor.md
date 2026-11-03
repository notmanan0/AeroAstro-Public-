---
title: "Stress Intensity Factor"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["K", "Stress intensity"]
tags: [sesa2028, materials, fracture-mechanics, lefm]
status: lectured
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Fracture Toughness and LEFM Validity]]", "[[Griffith Energy Balance]]", "[[Paris Law]]", "[[Stress Singularities]]"]
---

# Stress Intensity Factor

The stress intensity factor $K=Q\sigma\sqrt{\pi a}$ is the single number that sets the size of the elastic stress field around a sharp crack tip, combining the remote stress $\sigma$, the crack size $a$ and a geometry factor $Q$.

Linear elasticity gives the stresses near any crack tip as $\sigma_{ij}=K f_{ij}(\theta)/\sqrt{2\pi r}$ plus higher-order terms, where $r$ is the distance from the tip and $f_{ij}$ depends only on the angle and the loading mode. Every crack loaded in the same mode therefore has the same shape of field, and $K$ only scales it. That is what makes a single critical value usable for any geometry of the same material: fast fracture happens when $K$ reaches the fracture toughness $K_{Ic}$, whether the crack is in a test piece or a wing skin.

The crack size $a$ is the depth of a surface crack or half the length of an internal one, and it must be in metres so that $K$ comes out in MPa√m. $Q$ (some texts write $Y$) is 1 for a centre crack in a large plate and about 1.12 for an edge crack; this module's exam papers almost always give $Q=1.2$. Rearranging $K=K_{Ic}$ at the peak stress gives the critical crack size $a_c=\frac1\pi(K_{Ic}/Q\sigma_{max})^2$, and in fatigue the range $\Delta K=Q\Delta\sigma\sqrt{\pi a}$, using the tensile part of the cycle, drives crack growth through the [[Paris Law]].

$K$ is not the stress concentration factor $K_t$. $K_t$ is a dimensionless ratio of peak to nominal stress at one point, and it becomes infinite for a sharp crack; $K$ has units and describes the stress distribution over the region ahead of the tip, which is what the material in the plastic zone responds to. It is valid only while that plastic zone is small ([[Fracture Toughness and LEFM Validity]]). Its link to energy is $K_c=\sqrt{EG_c}$ ([[Griffith Energy Balance]]), and the same $1/\sqrt r$ singularity is what defeats mesh refinement in finite-element models ([[Stress Singularities]]).

## Related

- Topic: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]] · [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[Griffith Energy Balance]] · [[Fracture Toughness and LEFM Validity]] · [[Paris Law]]
- Elsewhere: [[Stress Concentration Factor and Factor of Safety]] · [[Stress Singularities]]
