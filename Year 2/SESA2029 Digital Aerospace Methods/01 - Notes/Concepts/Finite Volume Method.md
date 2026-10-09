---
title: "Finite Volume Method"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["FVM", "finite volumes", "control volume discretisation", "cell-centred scheme"]
tags: [sesa2029, concept, finite-volume]
status: complete
parent_lectures: ["[[SESA2029 A9 - Finite Volume Method]]"]
related_concepts: ["[[Conservation Form of the Governing Equations]]", "[[Convective Interpolation Schemes]]", "[[CFD Boundary Conditions]]", "[[Structured, Unstructured and Hybrid Grids]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L10)", "02 - Sources/CFD/CFD.txt"]
---

# Finite Volume Method

## Definition

> [!note] Definition
> A discretisation of the **integral** conservation laws over non-overlapping control volumes (cells). Each cell's balance is written as
>
> $$\frac{d}{dt}(\bar\phi_P\Delta V)+\sum_{\text{faces}}F_f\,A_f = Q_P\Delta V$$
>
> The face fluxes $F_f$ are shared by neighbouring cells, so conservation holds exactly over the whole domain.

## Explanation

- **Unknowns** are stored at the cell centres (nodes $P$), with neighbours labelled by compass points: N, S, E, W, and lower-case faces n, s, e, w.
- **Surface integrals**: the midpoint rule $\int_{S_e}f\,dS\approx f_eA_e$ is **second order**, because the linear Taylor term integrates to zero over a symmetric face and the error is $\propto\Delta y^3/24$. Higher order needs extra face points.
- **Volume integrals**: $\int_Vq\,dV\approx q_P\Delta V$, second order.
- **Face values** are unknown and must be **interpolated** from the nodes: UDS, CDS, second-order upwind, QUICK ([[Convective Interpolation Schemes]]).
- It works on **any** cell shape (tets, hexes, prisms, polyhedra). This is why commercial CFD codes are finite-volume solvers.
- The result is a sparse algebraic system, solved iteratively.

## Examples

- On a 2D Cartesian cell, the mass balance for incompressible flow is $(u_e-u_w)\Delta y+(v_n-v_s)\Delta x = 0$, the discrete divergence-free condition.

## Related

- Parent lectures: [[SESA2029 A9 - Finite Volume Method]]
- Related concepts: [[Conservation Form of the Governing Equations]] · [[Convective Interpolation Schemes]] · [[CFD Boundary Conditions]] · [[Structured, Unstructured and Hybrid Grids]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L10)
- 02 - Sources/CFD/CFD.txt
