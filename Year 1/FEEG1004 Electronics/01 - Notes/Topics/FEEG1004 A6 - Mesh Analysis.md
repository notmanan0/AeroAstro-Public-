---
title: "FEEG1004 A6 - Mesh Analysis"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 6
tags: [feeg1004, fundamentals, mesh-analysis, kvl, matrices, loop-currents]
aliases: ["Lecture 5c / 6", "Mesh analysis", "Loop currents"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
next_topics: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
key_concepts: ["[[Mesh Current Method]]", "[[Kirchhoff's Current and Voltage Laws]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W05-6 Mesh Analysis - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W05 Inductors Resonance and Mesh Analysis - Interactive.pdf"]
---

# FEEG1004 A6 - Mesh Analysis

> [!abstract] Summary
> A systematic way to write **just enough** KVL equations to find every current in a planar circuit.
> 1. Assign a **loop current** (capital $I$) to each window, all the same sense (clockwise).
> 2. Write KVL around each window. A resistor shared by two loops carries the **difference** of their loop currents.
> 3. Collect the equations as a matrix $\mathbf{RI} = \mathbf V$ and solve.
> 4. Recover **branch currents** (lower-case $i$) as sums and differences of loop currents.
>
> The course uses KVL-based mesh analysis only (nodal analysis with KCL is the alternative).

## Key Concepts
- [[Mesh Current Method]] · [[Kirchhoff's Current and Voltage Laws]]

---

## 1. Why a method is needed
- A network has many possible loops; writing KVL for all of them gives **more equations than unknowns**, many redundant.
- In a planar circuit, **one equation per window** (mesh) is exactly enough.

**Sign convention for a single loop** (the lecturer's choice, used throughout):
- Go round the loop in the current direction, **adding rises** (− to + through a source) and **subtracting** $IR$ drops.
- For a loop with a source $V$ and three resistors: $V - IR_1 - IR_2 - IR_3 = 0$.
- The equivalent "drops positive" form $-V + IR_1 + IR_2 + IR_3 = 0$ also works. Pick one and never mix.
- Mark the + end of each resistor (where the current enters) before writing the equation. Concept question: loop 1 with $V_2$, $I_1$ and $I_2$ gives answer **A**, $-V_2 + I_1R_1 - I_2R_2 = 0$.

## 2. The worked example (L6)
The mesh equations, written starting at the bottom-left corner of each loop:

$$
\begin{aligned}
\text{Loop 1:}&\quad 10 - 2(I_1 - I_3) - 4(I_1 - I_2) = 0\\
\text{Loop 2:}&\quad -4(I_2 - I_1) - 2(I_2 - I_3) - 3I_2 = 0\\
\text{Loop 3:}&\quad -4I_3 - 2(I_3 - I_2) - 2(I_3 - I_1) = 0
\end{aligned}
\qquad\Rightarrow\qquad
\begin{pmatrix}6&-4&-2\\-4&9&-2\\-2&-2&8\end{pmatrix}\begin{pmatrix}I_1\\I_2\\I_3\end{pmatrix} = \begin{pmatrix}10\\0\\0\end{pmatrix}
$$

- Solving gives $I_1$ = 3.21 A, $I_2$ = 1.70 A, $I_3$ = 1.23 A (not asked for in the lecture; checked numerically).
- Branch currents follow, e.g. $i_1 = I_1 - I_3$. They can be written as a second matrix (branch = incidence × loop).

> [!tip] Build the matrix by inspection
> - **Diagonal**: the sum of all resistance around mesh $k$.
> - **Off-diagonal** $(j, k)$: **minus** the resistance shared by meshes $j$ and $k$. The matrix is **symmetric**.
> - **Right-hand side**: the net source rise around the mesh in the loop direction.
> - Check your matrix against this pattern: it catches most sign errors.

> [!warning] Loop currents are not "real"
> - Only branch currents are physical. W5 check: the upward current in a resistor shared by loops 2 and 3 is $-I_2 + I_3$.
> - Exams do not always ask for the branch-current matrix, but Tutorial 2 Q1 does.

## 3. Tutorial 2 Q1: a four-mesh network
![[ee_t2_q1_mesh.png|880]]

$$
\begin{pmatrix}9&0&-4&0\\0&8&-2&0\\-4&-2&7&-1\\0&0&-1&4\end{pmatrix}\mathbf I = \begin{pmatrix}20\\0\\-10\\15\end{pmatrix},\qquad
\begin{pmatrix}i_1\\i_2\\i_3\\i_4\\i_5\\i_6\\i_7\end{pmatrix} = \begin{pmatrix}1&0&0&0\\0&-1&1&0\\1&0&-1&0\\0&0&-1&0\\0&0&1&-1\\0&1&0&0\\0&0&0&1\end{pmatrix}\mathbf I
$$

The full derivation is in [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]].

## Year 2 bridge
- $\mathbf{RI} = \mathbf V$ is a symmetric linear system, the same structure as the FE stiffness equation $\mathbf{Ku} = \mathbf f$ ([[Matrix Displacement Method]], [[Global Stiffness Matrix Assembly]]). Iterative solvers apply to both ([[Jacobi, Gauss-Seidel and SOR Iteration]]).
- In AC, replace $R$ by complex impedances $Z$ and the method is unchanged ([[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]).

## Links
- Previous: [[FEEG1004 A5 - Inductors and Electrical Resonance]] · Next: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Worked problems: [[FEEG1004 Tutorial 2 - DC Circuit Analysis and Kirchhoff's Laws Solutions]] (Q1)

## Sources
- Recorded lecture 6 (mesh analysis), P. Glynne-Jones; Week 5 interactive session.
