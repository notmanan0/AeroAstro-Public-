---
title: "FE Element Quality Checks"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["aspect ratio", "element distortion", "warping", "shape checking", "mesh check"]
tags: [sesa2029, concept, fea, meshing, validation]
status: complete
parent_lectures: ["[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]", "[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
related_concepts: ["[[CFD Mesh Quality Metrics]]", "[[Solid Elements (Tetrahedra and Hexahedra)]]", "[[h- and p-Refinement]]", "[[FE Model Verification Checks]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf", "02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# FE Element Quality Checks

## Definition

> [!note] Definition
> Geometric tests on individual elements that flag shapes which degrade accuracy or make $[K]$ ill-conditioned. They cover aspect ratio, internal angles, skew, taper, warping, midside-node position and curved edges.

## Explanation

- **Aspect ratio** (longest/shortest side): ≲ 2–4 for good 2D stress accuracy. Solids ≤ 3 (linear) or ≤ 5 (quadratic).
- **Angles** between element sides must not approach 0° or 180°. Avoid near-triangular quads, highly skewed shapes, off-centre midside nodes and curved sides.
- **Warping**: non-planar shell elements, common at trailing edges and twisted surfaces.
- In ANSYS: *Meshing → Check Mesh → Individual Elements → Plot Warning/Error Elements*, or `SHPP,SUMMARY` / `CHECK`. **Errors** must be fixed; **warnings** reduce accuracy.
- **Fixes**:
  - remesh with local sizing;
  - use mapped meshing where possible;
  - switch linear → quadratic, which tolerates about 5 → 7 in aspect ratio;
  - simplify sliver geometry.
- Also check for coincident nodes and elements, free edges (gaps), and consistent shell normals.

## Examples

- Crashes when refining a wing mesh are often distorted trailing-edge elements producing a singular stiffness matrix, not just memory limits.

## Related

- Parent lectures: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]] · [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Related concepts: [[CFD Mesh Quality Metrics]] · [[Solid Elements (Tetrahedra and Hexahedra)]] · [[h- and p-Refinement]] · [[FE Model Verification Checks]]
- APDL commands: [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf
- 02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt
