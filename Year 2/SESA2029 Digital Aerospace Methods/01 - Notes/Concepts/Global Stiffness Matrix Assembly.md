---
title: "Global Stiffness Matrix Assembly"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["assembly", "global stiffness matrix", "direct stiffness assembly", "element expansion"]
tags: [sesa2029, concept, fea, matrix-displacement-method]
status: complete
parent_lectures: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]", "[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
related_concepts: ["[[Matrix Displacement Method]]", "[[Euler-Bernoulli Beam Element]]", "[[Boundary Conditions and Rigid Body Modes]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf", "02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Global Stiffness Matrix Assembly

## Definition

> [!note] Definition
> Forming the global $[K]$ by adding each element stiffness matrix into the rows and columns of its global DOF. This enforces **displacement compatibility** (shared nodes have one displacement) and **force equilibrium** (the element forces at a node sum to the applied nodal force).

## Explanation

- **Size**: $n\times n$, with $n$ = total DOF (nodes × DOF per node). The matrix is square, symmetric and banded (sparse). Before BCs it is singular.
- **Mechanics**:
  - map each element's local DOF to global DOF numbers;
  - "expand" each element matrix with zeros to $n\times n$ (conceptually);
  - add. Only overlapping entries (shared DOF) sum.
- **Keep the DOF ordering consistent**, e.g. $(v_1,\theta_1,v_2,\theta_2)$ for beams. The element matrix is only valid for its own ordering.
- **Inclined bars** need the transformation $[K] = [T]^T[k][T]$, giving entries in $c^2$, $cs$ and $s^2$ ($c = \cos\theta$, $s = \sin\theta$).

## Examples

- Two bars in series: $[K] = \begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}$.
- Two beam elements ($L = 2$ and 1 m, $EI = 10^7$ N m²): the $(v_2,\theta_2)$ block becomes $1.25\times10^6\begin{bmatrix}12+96&-12+48\\-12+48&16+32\end{bmatrix}$ ([[SESA2029 B5 - Euler-Bernoulli Beam Element]]).

## Related

- Parent lectures: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] · [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- Related concepts: [[Matrix Displacement Method]] · [[Euler-Bernoulli Beam Element]] · [[Boundary Conditions and Rigid Body Modes]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf
- 02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt
