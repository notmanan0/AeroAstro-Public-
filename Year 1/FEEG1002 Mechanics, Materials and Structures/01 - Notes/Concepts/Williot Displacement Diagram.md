---
title: "Williot Displacement Diagram"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["displacement diagram", "truss deformation", "compatibility of truss joints"]
tags: [feeg1002, concept, statics, trusses, deflection]
status: complete
parent_lectures: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
related_concepts: ["[[Method of Joints and Method of Sections]]", "[[Stress, Strain and Young's Modulus]]"]
sources: []
---

# Williot Displacement Diagram

## Definition

> [!note] Definition
> A graphical compatibility construction for small truss deflections:
> 1. Compute each bar's length change $\Delta L_i = F_iL_i/(EA)_i$.
> 2. Lay off $\Delta L_i$ along each bar from its fixed end.
> 3. Draw a line **perpendicular** to each bar through the end of its $\Delta L$ (the small-angle approximation of the rotation arc).
> 4. The intersection gives the joint's displacement.
>
> Algebraically: $\mathbf u\cdot\mathbf e_i = \Delta L_i$ for each bar $i$ meeting the joint.

## Explanation

- **Compatibility**: pins keep the bars connected. Each bar may stretch and rotate but not separate.
- The arcs become perpendiculars because displacements are microns on bars of metres, so rotation angles are tiny.
- **Geometric amplification**: if two bars meet at a small angle $\theta$, displacement perpendicular to them scales like $1/\sin\theta$. In the L3 truss ($\theta = 26.6^\circ$), $\Delta Y_C = 2.74$ mm from bar changes under 1 mm.
- The algebraic form $\mathbf u\cdot\mathbf e_i = \Delta L_i$ is exactly what the FE stiffness method automates.

## Examples

- L3/L4 truss: $\mathbf u_C = (0.571, 2.740)$ mm.
- Tutorial 2 Q3: $\Delta x_C = \delta = 13\ \mu$m and $\Delta y_C = (1+\sqrt2)\delta = 32\ \mu$m.

![[s1_williot_displacement.png|760]]

## Related

- Topic notes: [[FEEG1002 A2 - Pin-Jointed Trusses]]
- Concepts: [[Method of Joints and Method of Sections]] · [[Stress, Strain and Young's Modulus]]
- Year 2: The [[Unit Load Method]] ($\delta = \sum FfL/AE$) gives the same answers without drawing ([[SESA2028 S8 - Virtual Work and Castigliano Theorems]])

## Sources

- Statics 1 Lecture 4c; Statics 1 Tutorial 2 Q3
