---
title: "Stress Transformation Equations"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["plane stress transformation", "stress on an inclined plane", "strain transformation"]
tags: [feeg1002, concept, statics-2, stress-transformation]
status: complete
parent_lectures: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Mohr's Circle]]", "[[Principal Stresses]]", "[[Stress Tensor and Stress Element]]", "[[Strain Gauge Rosettes]]"]
sources: []
---

# Stress Transformation Equations

## Definition

> [!note] Definition
> For axes $x'y'$ rotated **anticlockwise** by $\theta$ from $xy$ (plane stress):
> $$\sigma_{x'x'} = \frac{\sigma_{xx}+\sigma_{yy}}2 + \frac{\sigma_{xx}-\sigma_{yy}}2\cos2\theta + \sigma_{xy}\sin2\theta$$
> $$\sigma_{x'y'} = -\frac{\sigma_{xx}-\sigma_{yy}}2\sin2\theta + \sigma_{xy}\cos2\theta$$
> Strains transform identically with $\varepsilon_{xy} = \gamma_{xy}/2$ in place of $\sigma_{xy}$.

## Explanation

- Derived from force equilibrium of a wedge. It is geometry plus statics, so no material law enters, and it holds for any material.
- $\sigma_{y'y'}$ follows from $\theta + 90^\circ$. $\sigma_{x'x'} + \sigma_{y'y'}$ is invariant.
- **Uniaxial special case**: $\sigma_n = \sigma\cos^2\theta$ and $\tau = -\sigma\sin\theta\cos\theta$, so the maximum shear is $\sigma/2$ at 45°.
- Applications:
  - welds and glue lines at an angle;
  - resolved shear on slip planes ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]);
  - fibre-direction stress in composites;
  - interpreting rosette gauges.

## Examples

- Helical weld (Statics 2 Tutorial 4): $\sigma_n = 107$ MPa and $\tau = 37.1$ MPa at $\theta = 30^\circ$.

![[s2_inclined_section_uniaxial.png|600]]

## Related

- Topic notes: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
- Concepts: [[Mohr's Circle]] · [[Principal Stresses]] · [[Stress Tensor and Stress Element]] · [[Strain Gauge Rosettes]]
- Year 2: The same algebra for $I_{yy}, I_{zz}, I_{yz}$ in [[Principal Axes of a Section]] ([[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]) · tensor rotation $\mathbf R\boldsymbol\sigma\mathbf R^T$ as in [[Euler Angles and Rotation Matrices]]

## Sources

- Statics 2 Lecture 5a–b; Statics 2 Lecture 7b
