---
title: "Structured, Unstructured and Hybrid Grids"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["structured grid", "unstructured grid", "hybrid mesh", "C-grid", "O-grid", "H-grid", "block-structured", "overset grid"]
tags: [sesa2029, concept, meshing]
status: complete
parent_lectures: ["[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]"]
related_concepts: ["[[CFD Mesh Quality Metrics]]", "[[First-Cell Height and y-plus]]", "[[Finite Volume Method]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L11)", "02 - Sources/CFD/CFD.txt"]
---

# Structured, Unstructured and Hybrid Grids

## Definition

> [!note] Definition
> - **Structured grids** have $(i,j,k)$-indexed nodes with implicit neighbours (4 in 2D, 6 in 3D).
> - **Unstructured grids** have cells of any shape, with explicit connectivity.
> - **Hybrid grids** combine them: typically prism or hex **inflation layers** at walls surrounded by an unstructured tet fill.

## Explanation

| | Structured | Unstructured |
|---|---|---|
| Geometry | hard for complex shapes; blocks needed | anything, automatically |
| Efficiency | regular matrix, vectorises, fast | scattered memory, slower |
| Accuracy | typically higher | higher truncation error (especially triangles in BLs) |
| Point control | clustering propagates, wasting points in the far field | local refinement and adaptation |

**Structured topologies**:
- **H-grid**: lines follow the streamlines (cascades);
- **O-grid**: wraps the body (inviscid aerofoils; weak wake resolution);
- **C-grid**: wraps the body and continues down the wake (viscous aerofoils).

**Multi-block** grids join structured blocks. Put interpolating interfaces away from important flow. **Overset (chimera)** grids overlap and interpolate, which suits moving parts such as rotors.

**Viscous vs inviscid**: RANS needs thin, stretched wall cells for the target $y_1^+$; Euler grids don't. **Solution-based adaptation** reveals under-resolved regions, e.g. a wing wake.

## Examples

- A wing mesh that is automatically unstructured (tets) gives lift well, but drag poorly until adaptation refines the trailing-vortex wake.

## Related

- Parent lectures: [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Related concepts: [[CFD Mesh Quality Metrics]] · [[First-Cell Height and y-plus]] · [[Finite Volume Method]]
- FEA meshing: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L11)
- 02 - Sources/CFD/CFD.txt
