---
title: "Goodman Relation"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, mean-stress]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[S-N Curve and Basquin Law]]", "[[Shot Peening]]"]
---

# Goodman Relation

![[Figures/materials_goodman_diagram.png]]

A tensile mean stress reduces the stress amplitude a component can tolerate for a given life. **Goodman** assumes a straight line between two anchor points:

- $\sigma_m=0$: allowable amplitude = fully reversed fatigue strength $\sigma_{a0}$;
- $\sigma_a=0$: failure at the tensile strength $\sigma_{TS}$.

$$
\sigma_a=\sigma_{a0}\left(1-\frac{\sigma_m}{\sigma_{TS}}\right).
$$

A design point $(\sigma_m,\sigma_a)$ **below the line** is safe for the chosen life.

## Where it matters

- **Residual stress** adds to the mean stress. Shot-peening compression lowers $\sigma_m$ and moves the point down and left, a big HCF gain even though $\Delta\sigma$ is unchanged ([[Shot Peening]]).
- **Weld tensile residual stress** raises $\sigma_m$, so welds have lower fatigue strength.
- Compressive mean stress is generally beneficial, but the Goodman line is not extended into compression.

Variants: Gerber (parabolic, less conservative) and Soderberg (uses $\sigma_y$, more conservative). SESA2028 uses Goodman.
