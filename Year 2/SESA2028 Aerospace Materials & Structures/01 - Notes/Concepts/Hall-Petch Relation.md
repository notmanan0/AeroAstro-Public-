---
title: "Hall-Petch Relation"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, strengthening, grain-size]
status: complete
parent: ["[[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]"]
related: ["[[Precipitation Hardening]]", "[[Ductile-Brittle Transition]]", "[[Creep Curve and Mechanisms]]"]
---

# Hall-Petch Relation

$$
\sigma_y=\sigma_0+k_y\,d^{-1/2}
$$

- $\sigma_0$: lattice friction stress (plus any other strengthening).
- $k_y$: the Hall-Petch coefficient (the grain-boundary locking strength).
- $d$: mean grain diameter.

## Mechanism

A dislocation cannot pass straight through a grain boundary, because the slip planes change orientation. Dislocations on one slip plane therefore **pile up** against the boundary. Their stress fields add together, and the stress at the head of the pile-up eventually activates slip in the next grain. **Smaller grains** mean (1) more boundaries (barriers) and (2) **shorter pile-ups**, so less stress concentration at each boundary and a higher applied stress needed. Yield strength goes up.

## Why it is special

Grain refinement is the only common mechanism that raises **both strength and toughness** (it also lowers the DBT temperature in steels). Precipitates, solute and work hardening usually cost ductility.

## How grain size is controlled

- **Working + recrystallisation anneal**: stored dislocation energy nucleates new grains, and more strain gives finer grains. Limit the anneal time and temperature to avoid grain growth.
- **Pinning particles**: micro-alloy carbides (Nb, V, Ti) in HSLA steels; Zr in Mg alloys.
- **Faster solidification** (castings).
- **Thermomechanical processing** (controlled rolling).

## Where it stops helping

At high temperature, grain boundaries become **creep paths** (boundary sliding and diffusion), so turbine blades use *coarse*, columnar or single-crystal structures instead ([[Single Crystal Casting]]).
