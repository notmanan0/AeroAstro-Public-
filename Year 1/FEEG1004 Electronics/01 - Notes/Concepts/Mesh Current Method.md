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
sources: ["02 - Sources/S1 Fundamentals/S1-W05-6 Mesh Analysis - Recorded.pdf", "Recorded lecture 6", "Tutorial Sheet 2"]
---

# Mesh Current Method

The mesh current method assigns a clockwise loop current to each window of a planar circuit, writes KVL round each window and solves the resulting matrix equation. Branch currents are then differences of loop currents.

$$
\mathbf R\,\mathbf I = \mathbf V,\qquad R_{kk} = \sum R\ \text{round mesh }k,\quad R_{jk} = -\!\!\sum R\ \text{shared by }j,k
$$

A planar circuit has as many independent loops as it has windows, so one KVL equation per window gives a complete set and any further loop equation would only repeat information already in them. A resistor shared by meshes $j$ and $k$ carries $I_j - I_k$ in the direction of loop $j$, which is where the negative off-diagonal terms come from. The right-hand side of row $k$ is the net source rise round mesh $k$, taken in the loop direction. For a network of passive resistors the matrix is **symmetric**, and the method carries over unchanged to AC circuits with complex impedances in place of resistances.

For the three-mesh circuit of Lecture 6,

$$
\begin{pmatrix}6&-4&-2\\-4&9&-2\\-2&-2&8\end{pmatrix}\mathbf I = \begin{pmatrix}10\\0\\0\end{pmatrix}
$$

gives $\mathbf I$ = (3.21, 1.70, 1.23) A. Tutorial 2 Q1 is a four-mesh network with seven branch currents, each found as a single loop current or a difference of two.

![[ee_t2_q1_mesh.png|640]]

## Related

- [[FEEG1004 A6 - Mesh Analysis]]
- [[Kirchhoff's Current and Voltage Laws]] · [[Superposition Theorem (Circuits)]]
- Cross-module: the same symmetric matrix assembly appears in [[Global Stiffness Matrix Assembly]] and the [[Matrix Displacement Method]]
- Sources: Recorded lecture 6; Tutorial Sheet 2
