---
title: "Plane Strain Constraint"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fracture-mechanics, constraint]
status: complete
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Fracture Toughness and LEFM Validity]]", "[[Plane Stress and Plane Strain]]"]
---

# Plane Strain Constraint

Near a crack tip in a **thick** section, the material in the middle cannot contract through the thickness, because the surrounding elastic material stops it. So $\varepsilon_{33}\approx0$ and a tensile $\sigma_{33}$ develops: a **triaxial** stress state.

| | Plane stress (thin, or near free surfaces) | Plane strain (thick section centre) |
|---|---|---|
| Through-thickness | $\sigma_{33}=0$ | $\varepsilon_{33}=0$, $\sigma_{33}=\nu(\sigma_{11}+\sigma_{22})$ |
| Maximum shear | large, on $45^\circ$ planes, so easy yielding | reduced by triaxiality, so yielding is suppressed |
| Plastic zone | large | small (about 1/3 of the plane-stress size) |
| Fracture surface | **slant**: $45^\circ$ shear lips | **flat (square)** |
| Measured toughness | higher, thickness dependent | lowest, constant: $K_{Ic}$ |

## Consequences

- A thick fracture surface has a **flat centre and shear lips at the edges**. This is how you identify the final-fracture zone in fatigue ([[Fatigue Fracture Surface Features]]).
- **Design with $K_{Ic}$** (plane strain) because it is the most severe condition and the only thickness-independent value. It is conservative for thin sheet.
- Thin sheets are "tougher" only because of geometry, not because the material changed.

See [[Plane Stress and Plane Strain]] (SESA2029) for the constitutive definitions.
