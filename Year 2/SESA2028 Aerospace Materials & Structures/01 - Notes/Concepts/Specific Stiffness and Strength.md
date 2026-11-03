---
title: "Specific Stiffness and Strength"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Specific properties", "Specific modulus", "Material index", "Performance index"]
tags: [sesa2028, materials, lightweighting, materials-selection, performance-index]
status: lectured
parent: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
related: ["[[Rule of Mixtures]]", "[[Euler Buckling]]", "[[Titanium Alloy Classes]]"]
---

# Specific Stiffness and Strength

Specific stiffness $E/\rho$ and specific strength $\sigma/\rho$ are a material's stiffness and strength per unit density, the properties that matter when a structure has to be light because it moves.

For anything that is transported or rotates, mass costs fuel, payload or inertia, so the useful question is how much stiffness or strength a kilogram of material provides. Which ratio to maximise depends on the loading, found by writing the mass of the part for a fixed load and length. A tie sized for strength has mass $FL\rho/\sigma$, so it should maximise $\sigma/\rho$; sized for stiffness its mass is $FL^2\rho/(E\delta)$, so it should maximise $E/\rho$. A slender strut fails by Euler buckling, and since $I=A^2/4\pi$ for a solid round section, its mass goes as $\rho/E^{1/2}$, so it should maximise $E^{1/2}/\rho$; the square root rewards low density more than stiffness, which is why light materials win struts and panels even more clearly than ties ([[Euler Buckling]]).

![[materials_specific_property_map.png|700]]

The numbers explain the drive towards composites. Steel, aluminium and titanium alloys all have $E/\rho$ of about 25–27 GPa·cm³/g, so among metals lightweighting is decided by strength, toughness and temperature capability rather than stiffness. Unidirectional CFRP reaches about 130 along its fibres, and wins as a strut too (8.7 against 3.0 for aluminium in the MT3 table). Steel stays competitive in mass-produced cars because high-strength grades allow very thin sections at low cost. The weakness of the composite figures is that they hold only along the fibres and in tension; compressive strength, limited by fibre microbuckling and delamination, is much lower.

## Related

- Topic: [[SESA2028 M4 - Polymer Matrix Composites|M4]] · [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]]
- Concepts: [[Rule of Mixtures]] · [[Euler Buckling]] · [[Titanium Alloy Classes]]
