---
title: "Critical Fibre Length"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Shear-lag model", "Load transfer length", "Short-fibre composites"]
tags: [sesa2028, materials, composites, short-fibre, shear-lag]
status: lectured
parent: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
related: ["[[Rule of Mixtures]]", "[[Composite Manufacturing Routes]]"]
---

# Critical Fibre Length

The critical fibre length $l_c=\sigma_f^*d/2\tau$ is the shortest fibre that can be loaded to its breaking stress $\sigma_f^*$ at its midpoint by shear transfer from the matrix, for a fibre of diameter $d$ and interface shear strength $\tau$.

At the end of a fibre there is nothing to carry stress, so the fibre stress there is zero. Load is fed in from the surrounding matrix by shear along the fibre surface, the shear-lag picture, so the fibre stress builds up linearly from each end at the rate $4\tau/d$, set by balancing the shear force on the surface against the tensile force in the fibre. A fibre reaches $\sigma_f^*$ at its middle only if half its length is at least $l_c/2$.

![[materials_critical_fibre_length.png|800]]

At exactly $l_c$ the stress profile is a triangle and the average stress is only half the peak. A shorter fibre can never be broken: it pulls out of the matrix instead. A longer fibre carries $\sigma_f^*$ over its middle, with an average of $\sigma_f^*(1-l_c/2l)$, and once it is about fifteen times $l_c$ the end losses are only a few per cent and the [[Rule of Mixtures]] can be used. For a 7 μm carbon fibre of strength 3.5 GPa with an interface carrying 50 MPa, $l_c$ is about 0.25 mm. The practical catch is alignment: chopped fibres are cheap and flow easily into moulds, but they cannot be aligned as well as continuous ones, so short-fibre composites fall short of the rule-of-mixtures prediction even when the fibres are long enough.

## Related

- Topic: [[SESA2028 M4 - Polymer Matrix Composites|M4]]
- Concepts: [[Rule of Mixtures]] · [[Composite Manufacturing Routes]]
