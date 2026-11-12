---
title: "Stress Tensor and Stress Element"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["stress element", "stress tensor", "stress components", "complementary shear stress", "sigma_ij"]
tags: [feeg1002, concept, statics-2, stress]
status: complete
parent_lectures: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
related_concepts: ["[[Stress Transformation Equations]]", "[[Principal Stresses]]", "[[Generalised Hooke's Law]]", "[[Thin-Walled Pressure Vessels]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 01 - Stress in Multiple Dimensions and Pressure Vessels.pdf"]
---

# Stress Tensor and Stress Element

A stress element is a small square (2D) or cube (3D) of material, with faces normal to chosen axes, on which the stresses at a point are drawn; the set of stress components on it, $\sigma_{xx}$, $\sigma_{yy}$, $\sigma_{zz}$, $\sigma_{xy}$, $\sigma_{xz}$ and $\sigma_{yz}$, is the stress tensor for those axes.

In the FEEG1002 notation the first index gives the direction of the stress and the second the normal of the face it acts on, so $\sigma_{xx}$ is a normal stress on the $x$-face and $\sigma_{yx}$ a shear stress acting in $y$ on the $x$-face. Normal stresses are positive in tension. A shear stress is positive when it points in $+x$ or $+y$ on a face whose outward normal is $+x$ or $+y$, which means reading signs from the right-hand and top faces; on the left and bottom faces a positive shear stress points the other way.

Force equilibrium makes the stresses on opposite faces equal and opposite when the stress is uniform. Moment equilibrium about the centre of the element makes the shear stresses on perpendicular faces equal, $\sigma_{xy}=\sigma_{yx}$ (complementary shear), so in 3D only six components are independent and the tensor is symmetric:

$$
\boldsymbol\sigma=\begin{bmatrix}\sigma_{xx}&\sigma_{xy}&\sigma_{xz}\\ \sigma_{xy}&\sigma_{yy}&\sigma_{yz}\\ \sigma_{xz}&\sigma_{yz}&\sigma_{zz}\end{bmatrix}
$$

When the stress varies with position, equilibrium becomes a balance of gradients, $\partial\sigma_{xx}/\partial x+\partial\sigma_{xy}/\partial y=0$ without body forces, which is the mechanism behind shear stress in beams.

A point has one physical state of stress but a different set of components for every orientation of the element. Rotating the element changes the numbers according to the [[Stress Transformation Equations]], while quantities such as $\sigma_{xx}+\sigma_{yy}$ and the [[Principal Stresses]] do not change. In plane stress, which covers thin plates, thin-walled vessels and free surfaces, only $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$ are non-zero.

![[s2_stress_element_notation.png|800]]

## Related

- [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#2. The stress element|stress element and notation]] · [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#Moment balance and complementary shear|complementary shear]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle|transformation in B4]]
- [[Stress Transformation Equations]] · [[Principal Stresses]] · [[Generalised Hooke's Law]] · [[Thin-Walled Pressure Vessels]]
- Year 2: stresses in cylindrical coordinates in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]
