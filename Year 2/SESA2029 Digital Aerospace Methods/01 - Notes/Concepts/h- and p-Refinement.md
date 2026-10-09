---
title: "h- and p-Refinement"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["h-method", "p-method", "element order", "linear vs quadratic elements"]
tags: [sesa2029, concept, fea, meshing]
status: complete
parent_lectures: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]", "[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]"]
related_concepts: ["[[Shape Functions]]", "[[Mesh Convergence and Grid Independence]]", "[[FE Element Quality Checks]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf", "02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# h- and p-Refinement

## Definition

> [!note] Definition
> Two ways to add DOF and improve an FE solution:
> - **h-refinement** shrinks the characteristic element size $h$;
> - **p-refinement** raises the polynomial order $p$ of the shape functions.

## Explanation

- **h**: the mainstream approach (ANSYS, ABAQUS). It can be global or local (graded around stress raisers, with gradual size transitions).
- **p**: used by some CAD-embedded FE tools, with orders up to 8–9. In ANSYS it is effectively the choice between linear and quadratic elements (BEAM188/189, PLANE182/183, SHELL181/281, 4- and 10-node tets).
- Quadratic elements represent linearly varying strain, capture curvature and bending better, and **tolerate distortion** better (aspect-ratio limit about 5 rather than 3). They cost more per element.
- Cost rises roughly with (DOF)². Match the refinement to the quantity sought: loads < displacements < stresses.

## Examples

- At equal mesh density, PLANE182 reached 96–98% of the target stress and PLANE183 reached 100% ([[SESA2029 B6 - 2D and 3D Elements]]).

## Related

- Parent lectures: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]] · [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- Related concepts: [[Shape Functions]] · [[Mesh Convergence and Grid Independence]] · [[FE Element Quality Checks]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf
- 02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt
