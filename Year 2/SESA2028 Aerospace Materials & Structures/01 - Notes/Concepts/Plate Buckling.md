---
title: "Plate Buckling"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, plate-buckling]
status: complete
parent: ["[[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]"]
---

# Plate Buckling

**What it is:** local elastic instability of a thin plate (a skin panel, a web, or a flange of a thin-walled section) under in-plane compression or shear, often well **before** the material yields or the whole member buckles as a column.

$$
\sigma_{cr}=k\,\frac{\pi^2E}{12(1-\nu^2)}\left(\frac tb\right)^2
$$

- $b$: the **loaded width** between supports (stringers, ribs, webs), not the length;
- $t$: plate thickness;
- $k$: the buckling coefficient, depending on edge support, aspect ratio and load type ([[Plate Buckling Coefficient]]).

## Typical $k$ (long plates in uniform compression)

| Unloaded edges | $k$ |
|---|---:|
| both simply supported | 4.0 |
| both clamped | about 6.97 |
| one simply supported, one free (outstanding flange) | about 0.43 |
| one clamped, one free | about 1.28 |

## Plate vs column

A column's critical stress scales with $(r_g/L)^2$. A plate's scales with $(t/b)^2$, so **the plate length hardly matters** once it is long compared with $b$ (the plate buckles into several half-waves of length about $b$). The $1/(1-\nu^2)$ factor appears because a plate is restrained against anticlastic curvature (plate bending stiffness $D=Et^3/[12(1-\nu^2)]$).

## Design implications

- Halving $b$ (adding a stringer) raises $\sigma_{cr}$ **4×**, far cheaper than doubling $t$ across the whole skin.
- Free (outstanding) flanges are weak ($k\approx0.43$): stiffen them with lips.
- Unlike a column, a plate supported on its edges has **post-buckling reserve**: the stiff edges keep carrying load (effective-width concept). First-buckling calculations ignore this unless told otherwise.

![Plate buckling mode envelope](../Figures/structures_plate_buckling_mode_envelope.png)

See [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]].
