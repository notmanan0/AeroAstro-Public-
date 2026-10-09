---
title: "Boundary Conditions and Rigid Body Modes"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["rigid body motion", "zero pivot", "over-constraint", "symmetry boundary conditions", "supports"]
tags: [sesa2029, concept, fea, boundary-conditions]
status: complete
parent_lectures: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]", "[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]"]
related_concepts: ["[[Matrix Displacement Method]]", "[[FE Model Verification Checks]]", "[[Stress Singularities]]", "[[CFD Boundary Conditions]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf", "02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Boundary Conditions and Rigid Body Modes

## Definition

> [!note] Definition
> The FE boundary conditions are the **applied loads** (in $\{F\}$) and the **prescribed displacements** (supports, in $\{d\}$). They must suppress every **rigid-body mode**: 6 in 3D (3 translations + 3 rotations), 3 in 2D. They must also avoid **over-constraint**, which creates spurious stresses.

## Explanation

- **Under-constrained**: $[K]$ is singular. The body can move without straining, and the solver stops with a **zero-pivot** error or produces nonsense.
- **Over-constrained**: e.g. fixing both $u_x$ and $u_y$ along the base of a squashed block prevents Poisson expansion, giving false stress peaks at the corners. Fix one direction along an edge and the other at a single point, or use symmetry.
- **Homogeneous constraints** ($d_i = 0$): strike out the corresponding row and column before solving, then recover the reactions from the full equations.
- **Symmetry BCs**: on a symmetry plane the normal displacement (and, for beams and shells, the rotations about in-plane axes) is zero. This halves the model and removes rigid-body modes without over-constraining. Cyclic symmetry lets one sector represent a whole fan or rotor.
- **Loads**: apply them directly (nodal forces, element pressures) or on geometry. Point loads create singularities, so distribute them over an area.
- Getting the BCs right is the most critical, and the most examined, part of FE modelling. BCs are the first thing to revisit when a model disagrees with a test.

## Examples

- Beam: a clamp fixes $v = \theta = 0$; a simple support fixes $v = 0$ and leaves $\theta$ free.
- Plate with a hole: fix $u_x = 0$ on the left edge, plus $u_y = 0$ at one node, and apply tension to the right edge ([[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]).

## Related

- Parent lectures: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] · [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]
- Related concepts: [[Matrix Displacement Method]] · [[FE Model Verification Checks]] · [[Stress Singularities]] · [[CFD Boundary Conditions]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf
- 02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf
- 02 - Sources/FEM Lectures/FEA.txt
