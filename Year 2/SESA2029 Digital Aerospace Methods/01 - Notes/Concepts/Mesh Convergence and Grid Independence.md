---
title: "Mesh Convergence and Grid Independence"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Parts A & B: CFD and FEA"
aliases: ["grid independence", "mesh independence", "mesh convergence study", "grid study", "grid refinement study"]
tags: [sesa2029, concept, meshing, validation]
status: complete
parent_lectures: ["[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]", "[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]"]
related_concepts: ["[[Truncation Error and Order of Accuracy]]", "[[Stress Singularities]]", "[[Residual vs Solution Error]]", "[[h- and p-Refinement]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)", "02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf", "02 - Sources/CFD/CFD.txt"]
---

# Mesh Convergence and Grid Independence

## Definition

> [!note] Definition
> Showing that a quantity of interest no longer changes significantly as the mesh is refined. The remaining discretisation error is then acceptably small. A result that changes with the mesh is not a result.

## Explanation

- **Procedure**:
  1. Use at least **three meshes with large increments**, e.g. a 2× cell-size ratio or several times the cell count (80k → 300k → 1M), not 300k/400k/500k.
  2. Plot each output against $N$, $N^{1/3}$ or $h$, on log axes where helpful.
  3. Look for the curve flattening.
- **Report the quantity, not just the mesh**: lift and pitching moment converge early, drag (especially induced drag) slowly. In FE, displacements converge fast and peak stresses slowly.
- With a known order $p$, successive differences should shrink by $2^p$ per halving of $h$. The asymptote can be extrapolated (Richardson).
- **Singularities never converge**: judge convergence at a point away from them ([[Stress Singularities]]).
- **Refinement strategies**: global h, local h (graded, gradual), p (element order), adaptive.
- Iteration convergence (residuals) must be achieved on **each** mesh first.

## Examples

![[dam_mesh_convergence_singularity.png|520]]

- L-plate: the stress away from the corner converges to 0.831 of the coarse value, while the corner peak keeps rising.
- Hole in a plate: $K_t$ converges because a round hole is not singular.
- Transonic wing: about 10 million cells were needed to settle $C_D$ to 3 decimal places.

## Related

- Parent lectures: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]] · [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- Related concepts: [[Truncation Error and Order of Accuracy]] · [[Stress Singularities]] · [[Residual vs Solution Error]] · [[h- and p-Refinement]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)
- 02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf
- 02 - Sources/CFD/CFD.txt
