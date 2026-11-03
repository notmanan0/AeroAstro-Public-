---
title: "Plane Strain Constraint"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Constraint", "Crack-tip constraint"]
tags: [sesa2028, materials, fracture-mechanics, constraint]
status: lectured
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Fracture Toughness and LEFM Validity]]", "[[Plane Stress and Plane Strain]]"]
---

# Plane Strain Constraint

Plane strain constraint is the triaxial tension that builds up near a crack tip in the middle of a thick section, because the surrounding material stops the crack-tip region contracting through the thickness.

Pulled in the opening direction, the material at the tip wants to contract sideways by the Poisson effect. In thin sheet nothing stops it, and nothing carries stress through the thickness either: $\sigma_{33}\approx0$, a plane-stress state. The largest shear stress then acts on planes at 45° to the load, the tip yields easily, and the fracture surface is slanted. In a thick section the material around the tip does not contract with it, so the through-thickness strain is prevented. Setting $\varepsilon_{33}=0$ in Hooke's law gives $\sigma_{33}=\nu(\sigma_{11}+\sigma_{22})$, a tensile reaction stress. With all three principal stresses tensile, the differences between them are smaller, yielding is suppressed and the opening stress stays high. The lecture calls this the most severe stress condition.

That is why the critical stress intensity measured on thin specimens is higher than on thick ones, and why it falls to a plateau as the thickness grows. Only the plateau, the plane-strain value $K_{Ic}$, is a material constant, and it is the lowest value, so it is the one to design with; using it for thin sheet is conservative. The fracture surface of a thick part records the two states side by side: a flat, square centre under plane strain and small shear lips at the free surfaces, where plane stress returns. The same reading identifies the final-fracture zone on a fatigue surface ([[Fatigue Fracture Surface Features]]).

![[materials_thickness_effect_kcrit.png|800]]

The constitutive definitions of plane stress and plane strain are in [[Plane Stress and Plane Strain]].

## Related

- Topic: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]]
- Concepts: [[Fracture Toughness and LEFM Validity]] · [[Fatigue Fracture Surface Features]]
- Elsewhere: [[Plane Stress and Plane Strain]]
