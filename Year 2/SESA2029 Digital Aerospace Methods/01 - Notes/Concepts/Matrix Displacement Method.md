---
title: "Matrix Displacement Method"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["MDM", "direct stiffness method", "stiffness method", "F = Kd"]
tags: [sesa2029, concept, fea, matrix-displacement-method]
status: complete
parent_lectures: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]"]
related_concepts: ["[[Global Stiffness Matrix Assembly]]", "[[Boundary Conditions and Rigid Body Modes]]", "[[Principle of Minimum Total Potential Energy]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Matrix Displacement Method

## Definition

> [!note] Definition
> The structural form of the finite element method. The structure is modelled as an assembly of elements whose force–displacement relations $\{F\}^e = [K]^e\{d\}^e$ are simple algebraic equations. These are assembled into the global equilibrium system
>
> $$\{F\} = [K]\{d\}$$
>
> which is solved for the nodal displacements once the boundary conditions are applied.

## Explanation

- **Building blocks** of every element: **equilibrium** ($\sigma = F/A$), **compatibility** ($\varepsilon = u/L$) and the **constitutive** law ($\sigma = E\varepsilon$). For a bar these give $F = (EA/L)u = ku$.
- **2-node bar**: $\begin{Bmatrix}F_i\\F_j\end{Bmatrix} = k\begin{bmatrix}1&-1\\-1&1\end{bmatrix}\begin{Bmatrix}u_i\\u_j\end{Bmatrix}$.
- **Recipe**:
  1. form the element matrices;
  2. assemble;
  3. apply BCs;
  4. solve for $\{d\}$;
  5. back-substitute for the reactions;
  6. compute element forces and stresses.
- Problem size = nodes × DOF per node, and the cost grows quickly with it.
- The same matrices come out of energy methods ([[Principle of Minimum Total Potential Energy]]). Energy methods generalise to beams, plates, shells and solids through $[K] = \int[B]^T[D][B]\,dV$.
- Also called the **direct stiffness method** (Turner, Clough, Martin & Topp, 1956). It was expressed in matrix algebra so it could be programmed.

## Examples

- Two bars with areas $2A$ and $A$, clamped at both ends, with load $P$ at the junction: $u_2 = PL/(3AE)$ ([[SESA2029 FEA Worked Examples]]).
- Springs in series fixed at node 1: $u_2 = F/k_1$ and $u_3 = F/k_1+F/k_2$.

## Related

- Parent lectures: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]
- Related concepts: [[Global Stiffness Matrix Assembly]] · [[Boundary Conditions and Rigid Body Modes]] · [[Principle of Minimum Total Potential Energy]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf
- 02 - Sources/FEM Lectures/FEA.txt
