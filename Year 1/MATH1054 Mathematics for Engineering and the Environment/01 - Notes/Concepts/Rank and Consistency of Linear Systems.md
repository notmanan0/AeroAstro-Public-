---
title: "Rank and Consistency of Linear Systems"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Rank", "Echelon form", "Consistency", "Free parameters"]
tags: [math1054, concept, linear-systems]
status: complete
parent_lectures: ["[[MATH1054 M18 - Matrices III]]"]
related_concepts: ["[[Gaussian Elimination]]", "[[Eigenvalues and Eigenvectors]]", "[[Determinants and Cofactors]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.6", "MATH1054 Module Booklet, Module 18"]
---

# Rank and Consistency of Linear Systems

## Definition

> [!note] Definition
> The **rank** is the number of non-zero rows in echelon form, i.e. the number of linearly independent rows. For $\mathbf{AX}=\mathbf b$ with $n$ unknowns:
> - $\operatorname{rank}\mathbf A<\operatorname{rank}[\mathbf A|\mathbf b]$: **no solution**.
> - The ranks are equal and $=n$: a **unique** solution.
> - The ranks are equal and $=r<n$: **infinitely many**, with $n-r$ free parameters.

## Explanation
- Inconsistency shows up as a row reading $0=c\neq0$.
- It works for non-square systems too, whether over- or under-determined.
- A homogeneous system always has the trivial solution. It has non-trivial ones iff $\operatorname{rank}<n$, i.e. $|\mathbf A|=0$ for a square matrix.

## Examples
- Ex 88(a): rank 2, so $(x,y,z)=(\alpha-2,5-2\alpha,\alpha)$.
- Ex 88(b) and Ex 90(b): inconsistent.
- Ex 5.38(b): rank 2 with 5 unknowns, so 3 free parameters.

## Related
- Topics: [[MATH1054 M18 - Matrices III]]
- Concepts: [[Gaussian Elimination]] · [[Eigenvalues and Eigenvectors]] · [[Determinants and Cofactors]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §5.6
- MATH1054 Module Booklet, Module 18
