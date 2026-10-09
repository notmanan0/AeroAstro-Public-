---
title: "SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 12
tags:
  - sesa2029
  - fea
  - matrix-displacement-method
aliases: ["Matrix displacement method", "Direct stiffness method", "MDM"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: []
next_topics: ["[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]"]
key_concepts: ["[[Matrix Displacement Method]]", "[[Global Stiffness Matrix Assembly]]", "[[Boundary Conditions and Rigid Body Modes]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method

> [!abstract] Summary
> The **finite element method (FEM)** approximates the solution of PDEs by splitting a structure into simple **elements** joined at **nodes**. The **matrix displacement method** (MDM), also called the **direct stiffness method**, is the original structural form.
>
> 1. Write each element's equilibrium as $\{F\}^e = [K]^e\{d\}^e$. A bar has $k = EA/L$.
> 2. **Assemble** the element matrices into the global $\{F\} = [K]\{d\}$ by enforcing displacement **compatibility** and force **equilibrium** at shared nodes.
> 3. Apply **boundary conditions**. Without enough supports, $[K]$ is singular: rigid-body motion, "zero pivot".
> 4. Solve for the nodal displacements.
> 5. Back-substitute for reactions, then element forces and stresses.
>
> The same five steps apply to every element type in Part B.

## Key Concepts
- [[Matrix Displacement Method]] · [[Global Stiffness Matrix Assembly]] · [[Boundary Conditions and Rigid Body Modes]]

---

## 1. What FEM is (L1–L3)
- FEM is a computer-based numerical method for approximate solution of engineering problems defined by PDEs.
- It was proposed by **Courant (1943)** for vibration problems and developed by engineers at **Boeing**. Turner, Clough, Martin and Topp (1956) built it from the direct stiffness method.
- Expressing it in **matrix algebra** made it programmable, hence the name "matrix displacement method".
- Aerospace drove it. Certification demands extensive analysis, and real structures mix materials: glass fibre leading edges, carbon panels and aluminium spars on an A350 wing. That rules out closed-form solutions and favours FE, where each element can have its own geometry and properties.

**Problem size**: number of nodes × degrees of freedom (DOF) per node. Solver cost grows with it (roughly with DOF² for sparse direct solves), so estimate the size before you mesh.

**Terminology**:
- **key points** are geometry;
- **nodes** exist once the mesh is created;
- **elements** join nodes.

## 2. The 1-DOF bar (L3)
A bar with area $A$, length $L$ and modulus $E$, fixed at one end and pulled by $F$. Three relations define its behaviour:

$$
\underbrace{\sigma = F/A}_{\text{equilibrium}},\qquad\underbrace{\varepsilon = u/L}_{\text{compatibility}},\qquad\underbrace{\sigma = E\varepsilon}_{\text{constitutive}}\;\;\Rightarrow\;\;F = \frac{EA}{L}u = ku
$$

Once $u$ is known, everything else follows by back-substitution: $\varepsilon$, then $\sigma$, then reactions. These same three ingredients (equilibrium, compatibility, constitutive law) build every element.

## 3. The 2-DOF bar element (L3)
Nodes $i$ and $j$ can both move axially ($u_i$, $u_j$).

- Load–deformation: $F = k(u_j-u_i)$.
- Nodal equilibrium: $F_i = -F$ and $F_j = F$.

$$
\begin{Bmatrix}F_i\\F_j\end{Bmatrix} = \begin{bmatrix}k&-k\\-k&k\end{bmatrix}\begin{Bmatrix}u_i\\u_j\end{Bmatrix},\qquad k = \frac{EA}{L}\qquad\Longleftrightarrow\qquad\{F\}^e = [K]^e\{d\}^e
$$

$\{F\}$ and $\{d\}$ are 1D arrays and $[K]$ is a 2D array. Its size is the number of element DOF: $2\times2$ for a bar, $4\times4$ for a 2-node beam (see [[Euler-Bernoulli Beam Element]]).

## 4. Assembly (L3)
Two bars, element 1 (nodes 1–2, stiffness $k_1$) and element 2 (nodes 2–3, $k_2$), share node 2. That gives 3 global DOF, $\{d\} = \{u_1\ u_2\ u_3\}^T$, so the global $[K]$ is **3×3**.

- **Compatibility**: element 1's node $j$ and element 2's node $i$ are the same node, so they have the same displacement $u_2$.
- **Expand** each element matrix to 3×3 by padding with zero rows and columns.
- **Equilibrium** at each node: $F_2 = F_j^{(1)}+F_i^{(2)}$. So the expanded matrices **add**:

$$
\begin{Bmatrix}F_1\\F_2\\F_3\end{Bmatrix} = \begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_1\\u_2\\u_3\end{Bmatrix}
$$

**Practical rule**: add each element's entries into the global rows and columns of its DOF. Overlapping DOF sum; the full expansion is rarely written out. The global matrix is **square, symmetric and banded**. Keep the DOF ordering consistent, e.g. $(v_1,\theta_1,v_2,\theta_2)$ for beams, or rows and columns get swapped. See [[Global Stiffness Matrix Assembly]].

> [!note] Inclined bars (2D trusses)
> A bar at angle $\theta$ with 2 DOF per node ($u,v$) has element stiffness $\dfrac{EA}{L}\begin{bmatrix}c^2&cs&-c^2&-cs\\cs&s^2&-cs&-s^2\\-c^2&-cs&c^2&cs\\-cs&-s^2&cs&s^2\end{bmatrix}$ with $c = \cos\theta$ and $s = \sin\theta$. This comes from resolving the force equilibrium into components; it is the "take the angle into account" case mentioned in lecture. Assembly is identical.

## 5. Boundary conditions and solution (L3)
The boundary conditions are the **applied forces** in $\{F\}$ and the **displacement constraints** (supports) in $\{d\}$. The unspecified displacements are the unknowns.

**The model cannot be solved until enough displacement BCs are set.** Otherwise $[K]$ is singular: the structure can move as a rigid body, and the solver stops with a **"zero pivot" error**. See [[Boundary Conditions and Rigid Body Modes]].

**Example.** Bar 1 is fixed at its free end ($u_1 = 0$) and bar 2 is loaded by $F$ at its free end ($F_3 = F$):

$$
\begin{Bmatrix}R_1\\0\\F\end{Bmatrix} = \begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\begin{Bmatrix}0\\u_2\\u_3\end{Bmatrix}
$$

For a homogeneous constraint ($u_1 = 0$), **strike out that row and column**:

$$
\begin{Bmatrix}0\\F\end{Bmatrix} = \begin{bmatrix}k_1+k_2&-k_2\\-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_2\\u_3\end{Bmatrix}\;\Rightarrow\;u_2 = \frac F{k_1},\quad u_3 = \frac F{k_1}+\frac F{k_2}
$$

This is springs in series, as expected.

**Back-substitution**:
- Reaction from row 1 of the full system: $R_1 = -k_1u_2 = -F$.
- Member forces from each element equation: e.g. $F^{(2)} = k_2(u_3-u_2) = F$, and stress $\sigma = F^{(e)}/A_e$.

## 6. The MDM recipe (L3)
1. Form the element matrices.
2. Assemble the global matrix.
3. Apply the boundary conditions.
4. Solve for the displacement DOF.
5. Back-substitute for nodal and reaction forces.
6. Apply element equilibrium to get element forces and stresses.

It is general, and it can be programmed "without much thinking" once you have the element matrices. That is exactly what FE software does.

> [!example] Exam-style problem (example sheet type)
> A two-bar structure has bar 1 with area $2A$ and bar 2 with area $A$, both of length $L$ and modulus $E$. Both ends are clamped and load $P$ acts at the junction.
>
> $k_1 = 2AE/L$ and $k_2 = AE/L$. After striking rows and columns 1 and 3: $P = (k_1+k_2)u_2 = \dfrac{3AE}{L}u_2$, so $\boxed{u_2 = \dfrac{PL}{3AE}}$.
>
> Full working in [[SESA2029 FEA Worked Examples]].

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Next: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]
- Energy route to the same matrices: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]
- Scripted in APDL: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]
- Linear-system solution (direct vs iterative): [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]

## Sources
- FEA Lecture 3, `02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf`; transcript `FEA.txt`
- Logan, *A First Course in the Finite Element Method*, Ch. 2–3
