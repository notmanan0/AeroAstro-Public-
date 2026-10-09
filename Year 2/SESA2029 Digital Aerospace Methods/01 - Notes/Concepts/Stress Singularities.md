---
title: "Stress Singularities"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["singularity", "stress singularity", "re-entrant corner", "stress riser", "point load singularity"]
tags: [sesa2029, concept, fea, meshing]
status: complete
parent_lectures: ["[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]", "[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
related_concepts: ["[[Mesh Convergence and Grid Independence]]", "[[Stress Concentration Factor and Factor of Safety]]", "[[Boundary Conditions and Rigid Body Modes]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf", "02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Stress Singularities

## Definition

> [!note] Definition
> Points where linear elasticity predicts **infinite** stress: sharp re-entrant corners, crack tips, point loads ($F/A$ with $A\to0$), point constraints and over-constraints. At a singularity the FE peak stress **grows without limit** as the mesh is refined, instead of converging.

## Explanation

- **Diagnosis**: in a convergence study the peak keeps rising, often while its location jumps to the sharpest node.
- **Corner exponent**: near a 270° re-entrant corner, $\sigma\propto r^{-0.456}$ (Williams). So refining $h$ by 2× raises the nodal peak about 1.37×.
- **Remedies**:
  - model the real **fillet radius**;
  - spread loads and constraints over an **area or line**;
  - evaluate stresses (and convergence) **away** from the singular point;
  - model contact rather than fixing nodes rigidly;
  - use fracture mechanics (stress intensity factors) for genuine cracks.
- Singular stresses are **not** design values. A round hole, by contrast, has a finite, convergent $K_t$.
- On wings, a sharp clamped root and a knife-edge trailing edge are the usual culprits.

## Examples

![[dam_mesh_convergence_singularity.png|520]]

- L-plate: the corner peak rose ×4.94 from $n = 4$ to 128, while the remote stress converged ([[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]).

## Related

- Parent lectures: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]] · [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Related concepts: [[Mesh Convergence and Grid Independence]] · [[Stress Concentration Factor and Factor of Safety]] · [[Boundary Conditions and Rigid Body Modes]]

**Related (SESA2028 materials):** [[Stress Intensity Factor]] (the $K/\sqrt{2\pi r}$ crack-tip field) · [[Fracture Toughness and LEFM Validity]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf
- 02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt
