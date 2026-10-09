---
title: "Mesh Current Method"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["mesh analysis", "loop currents", "mesh matrix"]
tags: [feeg1004, concept, dc-circuits, matrices]
status: complete
parent_lectures: ["[[FEEG1004 A6 - Mesh Analysis]]"]
related_concepts: ["[[Kirchhoff's Current and Voltage Laws]]", "[[Superposition Theorem (Circuits)]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W05-6 Mesh Analysis - Recorded.pdf"]
---

# Mesh Current Method

## Definition

> [!note] Definition
> Assign a clockwise loop current to each window of a planar circuit, write KVL per window, and solve
>
> $$\mathbf R\,\mathbf I = \mathbf V,\qquad R_{kk} = \sum R\ \text{round mesh }k,\quad R_{jk} = -\!\!\sum R\ \text{shared by }j,k$$
>
> Branch currents are then differences of loop currents.

## Explanation
- One equation per window is exactly enough; extra loops would be redundant.
- A resistor shared by meshes $j$ and $k$ carries $I_j - I_k$ in the direction of loop $j$.
- The RHS is the net source rise around each mesh, taken in the loop direction.
- The matrix is **symmetric** for passive resistor networks.
- It works unchanged in AC with complex impedances.

## Examples
- Lecture 6: $\left(\begin{smallmatrix}6&-4&-2\\-4&9&-2\\-2&-2&8\end{smallmatrix}\right)\mathbf I = (10, 0, 0)^T$ gives $\mathbf I$ = (3.21, 1.70, 1.23) A.
- Tutorial 2 Q1: a four-mesh network with 7 branch currents.

![[ee_t2_q1_mesh.png|640]]

## Related
- Topic notes: [[FEEG1004 A6 - Mesh Analysis]]
- Cross-module: [[Global Stiffness Matrix Assembly]] · [[Matrix Displacement Method]]

## Sources
- Recorded lecture 6; Tutorial Sheet 2
