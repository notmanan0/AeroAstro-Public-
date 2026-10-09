---
title: "Strain Components and Volumetric Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["normal strain", "engineering shear strain", "tensor shear strain", "gamma_xy", "epsilon_xy", "volumetric strain", "dilatation"]
tags: [feeg1002, concept, statics-2, strain]
status: complete
parent_lectures: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
related_concepts: ["[[Thermal Strain]]", "[[Generalised Hooke's Law]]", "[[Strain Gauge Rosettes]]"]
sources: []
---

# Strain Components and Volumetric Strain

## Definition

> [!note] Definition
> Small-strain components are **displacement gradients**:
> $$\varepsilon_{xx} = \frac{\partial u_x}{\partial x},\qquad \gamma_{xy} = \frac{\partial u_x}{\partial y} + \frac{\partial u_y}{\partial x},\qquad \varepsilon_{xy} = \tfrac12\gamma_{xy}$$
> $$\varepsilon_{vol} = \frac{\Delta V}{V}\approx\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}$$

## Explanation

- Normal strain is stretch. Shear strain is the **reduction of a right angle**: $\gamma_{xy} > 0$ closes the angle between the $+x$ and $+y$ faces.
- Rigid translation and rotation give **zero** strain; strain measures deformation only.
- **Factor of 2**: $\gamma_{xy}$ (engineering) is used with $\tau = G\gamma$. $\varepsilon_{xy} = \gamma_{xy}/2$ (tensor) is used in transformation equations and on Mohr's circle for strain.
- Shear alone produces no volume change.
- Typical magnitudes are 10⁻⁴–10⁻³ (100–1000 με): an aluminium alloy at yield is at 3600 με.

## Examples

![[s2_strain_definitions.png|760]]

## Related

- Topic notes: [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]
- Concepts: [[Thermal Strain]] · [[Generalised Hooke's Law]] · [[Strain Gauge Rosettes]]
- Year 2: Polar forms $\varepsilon_r = du/dr$, $\varepsilon_\theta = u/r$ ([[Polar Strain-Displacement Relations]]) and [[Strain Compatibility]] in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] · strain-rate tensor in fluids ([[Newtonian Fluid and Strain-Rate Tensor]])

## Sources

- Statics 2 Lecture 2a–b
