---
title: "Generalised Hooke's Law"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["3D Hooke's law", "plane stress Hooke's law", "bulk modulus", "isotropic linear elasticity", "constitutive law"]
tags: [feeg1002, concept, statics-2, hookes-law, elasticity]
status: complete
parent_lectures: ["[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Stress, Strain and Young's Modulus]]", "[[Plane Stress and Plane Strain]]", "[[Thin-Walled Pressure Vessels]]", "[[Strain Gauge Rosettes]]"]
sources: []
---

# Generalised Hooke's Law

## Definition

> [!note] Definition
> For a homogeneous, isotropic, linear elastic solid:
> $$\varepsilon_{xx} = \tfrac1E[\sigma_{xx} - \nu(\sigma_{yy}+\sigma_{zz})]\ \ (\text{and cyclic}),\qquad \varepsilon_{xy} = \frac{1+\nu}{E}\sigma_{xy} = \frac{\sigma_{xy}}{2G}$$
> Plane-stress inverse:
> $$\sigma_{xx} = \frac{E}{1-\nu^2}(\varepsilon_{xx}+\nu\varepsilon_{yy}),\quad \sigma_{yy} = \frac{E}{1-\nu^2}(\varepsilon_{yy}+\nu\varepsilon_{xx}),\quad \sigma_{xy} = \frac{E}{1+\nu}\varepsilon_{xy}$$

## Explanation

- Only $E$ and $\nu$ are independent: $G = \dfrac{E}{2(1+\nu)}$ and $K = \dfrac{E}{3(1-2\nu)}$.
- **Volume**: $\varepsilon_{vol} = \dfrac{1-2\nu}{E}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})$. As $\nu\to0.5$ the material is incompressible (rubber).
- **Plane stress**: $\sigma_{zz} = 0$, $\varepsilon_{zz} = -\frac\nu E(\sigma_{xx}+\sigma_{yy})\neq0$.
- **Plane strain**: $\varepsilon_{zz} = 0$, $\sigma_{zz} = \nu(\sigma_{xx}+\sigma_{yy})\neq0$.
- **Isotropy decouples** normal and shear behaviour. Anisotropic materials (wood, fibre composites) do not have this property.
- With temperature, add $\alpha\Delta T$ to each normal strain.

## Examples

- Submarine hull (Statics 2 Tutorial 3): $\varepsilon_{xx} = -313$ and $\varepsilon_{yy} = -1963$ με. Poisson coupling cuts $|\varepsilon_{xx}|$ by a factor of 4.
- Rosette to stress (Tutorial 8 Q1): $\sigma_{xx} = 200$, $\sigma_{yy} = 115$, $\sigma_{xy} = -18.4$ MPa.

![[s2_elastic_constants.png|600]]

## Related

- Topic notes: [[FEEG1002 B3 - Generalised Hooke's Law]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
- Concepts: [[Stress, Strain and Young's Modulus]] · [[Plane Stress and Plane Strain]] · [[Thin-Walled Pressure Vessels]] · [[Strain Gauge Rosettes]]
- Year 2: Material $\mathbf D$ matrix of FE elements ([[SESA2029 B6 - 2D and 3D Elements]]) · Lamé problems in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] · anisotropic laminae in [[SESA2028 M4 - Polymer Matrix Composites]]

## Sources

- Statics 2 Lecture 4a–b
