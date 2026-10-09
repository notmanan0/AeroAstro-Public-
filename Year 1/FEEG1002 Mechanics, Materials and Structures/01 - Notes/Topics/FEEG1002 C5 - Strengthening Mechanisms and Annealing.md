---
title: "FEEG1002 C5 - Strengthening Mechanisms and Annealing"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 20
tags: [feeg1002, materials, strengthening, hall-petch, work-hardening, annealing]
aliases: ["Materials Lecture 7", "Strengthening and annealing"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]", "[[FEEG1002 C3 - Diffusion]]"]
next_topics: ["[[FEEG1002 C6 - Phase Diagrams]]"]
key_concepts: ["[[Strengthening Mechanisms in Metals]]", "[[Annealing of Cold-Worked Metals]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 07 - Strengthening Mechanisms and Annealing.pdf"]
---

# FEEG1002 C5 - Strengthening Mechanisms and Annealing

> [!abstract] Summary
> Yield begins when dislocations move, so every strengthening method makes that motion harder: add solutes, add/tangle dislocations, add grain boundaries, or add precipitates. Strength normally trades against ductility. Annealing reverses cold work by recovery, recrystallisation and grain growth.

## Key Concepts
- [[Strengthening Mechanisms in Metals]] · [[Annealing of Cold-Worked Metals]]

---

## 1. One unifying idea
> [!important] To raise yield strength, obstruct dislocation motion.

| Mechanism | Obstacle | Main control | Typical trade-off |
|---|---|---|---|
| solid-solution strengthening | solute/dislocation elastic fields | solute size and concentration | conductivity/ductility may fall |
| work hardening | other dislocations (“forest”) | prior plastic strain | ductility falls; residual stress rises |
| grain refinement | grain boundaries and change of slip orientation | grain size | boundary diffusion/corrosion may rise |
| precipitation hardening | coherent/incoherent second-phase particles | size, spacing, coherency | can over-age in hot service |

![[m5_strengthening.png|760]]

## 2. Work hardening
Plastic strain multiplies dislocations. Their elastic fields interact and they tangle, so progressively larger stress is needed for further glide.

- $\sigma_y$, UTS and hardness increase.
- ductility and formability decrease.
- $E$ changes very little because elastic stiffness comes from bond curvature, not dislocation density.
- grains become elongated and the material can become anisotropic.

Cold work is often expressed as percentage area reduction:

$$\%CW=\frac{A_0-A_f}{A_0}\times100\%$$

## 3. Grain-boundary strengthening
Dislocations pile up at a boundary because the next grain has a different orientation. A longer pile-up creates a larger local stress that can start slip in the next grain; therefore smaller grains are stronger:

$$\sigma_y=\sigma_0+k_y d^{-1/2}$$

- $d$: mean grain diameter.
- $\sigma_0$: lattice/dislocation friction including other strengthening contributions.
- $k_y$: material-dependent Hall-Petch slope.

Grain refinement is unusual because it can improve both strength and resistance to brittle fracture. At high temperature, however, many grain boundaries accelerate diffusion and grain-boundary sliding, so creep-resistant alloys often favour coarse grains or single crystals.

## 4. Precipitation strengthening
Second-phase particles block dislocations:
- very small coherent particles may be **cut**;
- larger/harder particles are bypassed by dislocation **bowing** (Orowan loops);
- strengthening depends on particle size, spacing, volume fraction and coherency.

The processing route is developed in [[FEEG1002 C7 - Steels and Precipitation Hardening]].

## 5. Annealing cold-worked metal
Annealing at roughly $0.5T_m$ (absolute scale; alloy-dependent) proceeds by diffusion:

1. **Recovery**: dislocations rearrange/annihilate and residual stresses fall; grain shape changes little.
2. **Recrystallisation**: new nearly dislocation-free equiaxed grains nucleate and sweep out the deformed structure; strength falls and ductility returns.
3. **Grain growth**: large grains consume small ones to reduce total boundary energy.

![[m5_annealing.png|760]]

Recrystallised grain size depends on:
- more prior cold work $\rightarrow$ more nucleation sites $\rightarrow$ finer grains;
- higher temperature/longer time $\rightarrow$ faster diffusion and more growth $\rightarrow$ coarser grains.

> [!example] Growth kinetics from the tutorial
> Fitting $v=Ae^{-Q/RT}$ to the aluminium data gives $Q\approx229$ kJ/mol. Extrapolation to $v=10^{-2}$ m/s gives approximately **523°C**. This is far outside the measured range, so it is an estimate, not a precision result.

> [!warning] Common traps
> - Annealing is not one event: recovery can remove residual stress without replacing the grains.
> - Fine grains are good for room-temperature yield/fracture, but not always for creep.
> - Work hardening raises strength but does not materially raise Young's modulus.

## Links
- Previous: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]] · Next: [[FEEG1002 C6 - Phase Diagrams]]
- Worked problems: [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]]

## Sources
- Materials Lecture 7; audited against [[FEEG1002 Materials L07 Contact Sheet.png]].

