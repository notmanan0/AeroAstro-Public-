---
title: "Critical Fibre Length"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, composites, short-fibre, shear-lag]
status: complete
parent: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
related: ["[[Rule of Mixtures]]", "[[Composite Manufacturing Routes]]"]
---

# Critical Fibre Length

![[Figures/materials_short_fibre_stress.png]]

Load enters a discontinuous (or broken) fibre by **interfacial shear** through the matrix (the **shear-lag** model). The fibre's tensile stress is zero at its ends and builds up linearly over the **transfer (ineffective) length**.

A force balance on half a fibre of diameter $d$, with interfacial shear strength $\tau$, gives the length needed to reach the fibre strength $\sigma_f^*$ at mid-length:

$$
l_c=\frac{\sigma_f^*\,d}{2\tau}.
$$

## Regimes

| Fibre length | Behaviour |
|---|---|
| $l<l_c$ | the fibre **cannot be broken**: peak stress below $\sigma_f^*$, so it pulls out; poor reinforcement |
| $l=l_c$ | the fibre just breaks at mid-length; triangular stress profile, so the **average is only 50 %** of the peak |
| $l\gtrsim15\,l_c$ | end effects negligible; behaves like a continuous fibre (rule of mixtures) |

## Practical points

- Short fibres are cheaper and much easier to mould (injection moulding, chopped-strand mat), **but alignment cannot be controlled**, so properties are lower and less predictable.
- A better interface (sizing) raises $\tau$ and shortens $l_c$.
- The same shear-lag load transfer lets a continuous composite survive individual fibre breaks: load is shed onto neighbouring fibres over the ineffective length.
