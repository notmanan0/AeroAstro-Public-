---
title: "Plate, Shell and Membrane Elements"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["shell element", "plate element", "membrane element", "SHELL181", "SHELL281"]
tags: [sesa2029, concept, fea, element-types]
status: complete
parent_lectures: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
related_concepts: ["[[Plane Stress and Plane Strain]]", "[[Solid Elements (Tetrahedra and Hexahedra)]]", "[[Euler-Bernoulli Beam Element]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Plate, Shell and Membrane Elements

## Definition

> [!note] Definition
> Surface elements for thin structures:
> - **membranes** carry only in-plane load;
> - **plates** are flat and carry transverse load by bending in two directions and twisting, with DOF $w,\theta_x,\theta_y$;
> - **shells** may be curved and carry membrane + bending + twist together, with up to 6 DOF per node.

## Explanation

- A shell = membrane (plane stress) + plate bending, superposed. It suits fuselages, wing skins, tanks and roofs.
- **Use shells when** $t\lesssim L_{max}/20$. They give in-plane and bending stresses accurately, but **not** through-thickness normal stress. Transverse shear is recovered from equilibrium.
- **SHELL181**: 4 nodes, 6 DOF per node, linear; efficient for large models and mild curvature.
- **SHELL281**: 8 nodes, quadratic; better for curvature and bending accuracy; costlier.
- Results can be read at the TOP, MID or BOT surfaces (`SHELL,TOP`). The element normal defines "top" and the direction of pressure.
- **Plate vs beam**: a plate bends in two directions and twists; a beam bends in one plane per section axis.
- **Solids vs shells for thin walls**: single-layer solids badly mis-predict bending. In one lecture example they gave about double the shell or beam stress.

## Examples

- Wing skin: a SHELL181 surface extruded from an aerofoil section, clamped at the root, with upper and lower pressures ([[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]).

## Related

- Parent lectures: [[SESA2029 B6 - 2D and 3D Elements]]
- Related concepts: [[Plane Stress and Plane Strain]] · [[Solid Elements (Tetrahedra and Hexahedra)]] · [[Euler-Bernoulli Beam Element]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt
