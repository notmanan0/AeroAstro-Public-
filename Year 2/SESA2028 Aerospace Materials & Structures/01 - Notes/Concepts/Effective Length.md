---
title: "Effective Length"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, buckling]
status: complete
parent: ["[[SESA2028 S5 - Euler Buckling and Effective Length]]"]
---

# Effective Length

**What it is:** the length $L_e=KL$ of the equivalent **pin-ended** column that has the same Euler buckling load as the real member. It is the distance between points of inflexion (zero moment) of the buckled shape.

$$
P_E=\frac{\pi^2EI}{(KL)^2}
$$

| End conditions | Buckled shape | $K$ |
|---|---|---:|
| Pinned-pinned | half sine wave | 1.0 |
| Fixed-free (flagpole) | quarter wave | **2.0** |
| Fixed-pinned | | about 0.699 (often 0.7) |
| Fixed-fixed | full wave, inflexions at $L/4$ | 0.5 |
| Fixed-fixed with sway (guided) | | 1.0 |

$P_E\propto1/K^2$, so a fixed-free column carries only **1/16** of the load of a fixed-fixed one of the same length.

![Euler end conditions](../Figures/structures_euler_buckling_end_conditions.png)

## Good practice

- **Sketch the buckled shape** before picking $K$; count the half-waves.
- Real joints are neither perfectly pinned nor perfectly fixed. Design codes use larger $K$ for "fixed" ends (e.g. 0.65 instead of 0.5).
- $K$ can differ in the two planes (e.g. pinned about one axis, fixed about the other). Check **both** planes with the corresponding $I$ ([[Slenderness Ratio]]).

See [[Euler Buckling]] and [[SESA2028 S5 - Euler Buckling and Effective Length]].
