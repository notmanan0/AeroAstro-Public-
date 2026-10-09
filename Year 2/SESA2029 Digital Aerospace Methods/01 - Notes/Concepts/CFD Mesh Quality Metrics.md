---
title: "CFD Mesh Quality Metrics"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["skewness", "aspect ratio", "orthogonality", "orthogonal quality", "mesh metrics"]
tags: [sesa2029, concept, meshing, validation]
status: complete
parent_lectures: ["[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
related_concepts: ["[[Structured, Unstructured and Hybrid Grids]]", "[[Mesh Convergence and Grid Independence]]", "[[FE Element Quality Checks]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)", "02 - Sources/CFD/CFD.txt"]
---

# CFD Mesh Quality Metrics

## Definition

> [!note] Definition
> Geometric measures of cell shape that control the accuracy and stability of a CFD solution:
> - **skewness**: departure from the ideal equilateral cell (0 is best);
> - **aspect ratio**: stretching, longest/shortest dimension;
> - **non-orthogonality**: the angle between the line joining two cell centres and the normal of their shared face (0° is best), or its 0–1 "orthogonal quality".

## Explanation

| Metric | Recommended |
|---|---|
| Skewness | max < 0.9; quad/hex angles ≈ 90°, tri ≈ 60°, tets with equal angles; avoid included angles < 40° or > 140° |
| Aspect ratio | ≲ 5 in the bulk flow (average < 5); ≲ 10 in BL cells; ≤ 20–100 in important regions; near walls ≤ 20 (unsteady) or ≤ 200 (steady); max ≈ 300 |
| Non-orthogonality | < 70°; > 85° usually diverges; orthogonal quality > 0.2 |

- High aspect ratio is **good** inside boundary layers, where gradients are one-directional, and **bad** in the free stream or wake.
- Meshing tools report the min, max, average and a histogram. Outliers usually sit at sharp leading or trailing edges. Use the average for an overall picture, but inspect the outliers.
- Poor quality slows convergence, reduces accuracy or causes divergence. It is the first thing to check when a run fails.

## Examples

- A tetra mesh with skewness 0.95 at the trailing edge diverged. Adding an inflation layer and a finer edge sizing brought it below 0.85, and the run converged.

## Related

- Parent lectures: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Related concepts: [[Structured, Unstructured and Hybrid Grids]] · [[Mesh Convergence and Grid Independence]] · [[FE Element Quality Checks]]
- FE element checks: [[FE Element Quality Checks]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)
- 02 - Sources/CFD/CFD.txt
