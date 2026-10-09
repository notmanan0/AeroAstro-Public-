---
title: "Stress Tensor and Stress Element"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["stress element", "stress tensor", "stress components", "complementary shear stress", "sigma_ij"]
tags: [feeg1002, concept, statics-2, stress]
status: complete
parent_lectures: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
related_concepts: ["[[Stress Transformation Equations]]", "[[Principal Stresses]]", "[[Generalised Hooke's Law]]"]
sources: []
---

# Stress Tensor and Stress Element

## Definition

> [!note] Definition
> The state of stress at a point is fully described by the stresses on three mutually perpendicular faces of a small element: $\sigma_{ij}$ is the stress in direction $j$ on a face with normal $i$. Moment equilibrium makes the tensor **symmetric** ($\sigma_{xy} = \sigma_{yx}$), so 3D has **six** independent components:
> $$\boldsymbol\sigma = \begin{bmatrix}\sigma_{xx} & \sigma_{xy} & \sigma_{xz}\\ \sigma_{xy} & \sigma_{yy} & \sigma_{yz}\\ \sigma_{xz} & \sigma_{yz} & \sigma_{zz}\end{bmatrix}$$

## Explanation

- **Signs**:
  - normal stress: tension positive;
  - shear stress: positive when it points in $+x$ or $+y$ on a face with a positive outward normal.
- **One state, many descriptions**: rotating the element changes the components, not the physical state ([[Stress Transformation Equations]]). Invariants such as $\sigma_{xx}+\sigma_{yy}+\sigma_{zz}$ do not change.
- **Plane stress**: only $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$ are non-zero. This suits thin plates, shells and free surfaces.
- **Equilibrium with gradients**: $\partial\sigma_{xx}/\partial x + \partial\sigma_{xy}/\partial y = 0$, and similarly for $y$. This underlies the beam shear-stress formula.

## Examples

![[s2_stress_element_notation.png|760]]

## Related

- Topic notes: [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]
- Concepts: [[Stress Transformation Equations]] · [[Principal Stresses]] · [[Generalised Hooke's Law]]
- Year 2: Cylindrical-coordinate stresses $\sigma_r, \sigma_\theta, \sigma_z$ in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] · Cauchy stress in [[Navier-Stokes Equations]] (fluid stress is also a symmetric tensor)

## Sources

- Statics 2 Lecture 1b
