---
title: "Matrix Inverse"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Inverse matrix", "Cofactor method", "Gauss-Jordan inverse", "Singular matrix"]
tags: [math1054, concept, matrices]
status: complete
parent_lectures: ["[[MATH1054 M17 - Matrices II]]"]
related_concepts: ["[[Determinants and Cofactors]]", "[[Gaussian Elimination]]", "[[Matrix Algebra]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.4", "MATH1054 Module Booklet, Module 17"]
---

# Matrix Inverse

## Definition

> [!note] Definition
> $\mathbf A^{-1}\mathbf A=\mathbf A\mathbf A^{-1}=\mathbf I$. The inverse exists iff $|\mathbf A|\neq0$, and then
>
> $$\mathbf A^{-1}=\frac{\operatorname{adj}\mathbf A}{|\mathbf A|},\qquad\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac1{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$$

## Explanation
- There are two methods:
  - the **direct (cofactor)** method above;
  - **elimination**: row-reduce $[\mathbf A|\mathbf I]\to[\mathbf I|\mathbf A^{-1}]$, which is much cheaper for large $n$.
- $(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}$.
- $\mathbf{AX}=\mathbf b$ gives $\mathbf X=\mathbf A^{-1}\mathbf b$. This is conceptual; in practice, eliminate directly.

## Examples
- $\begin{bmatrix}-1&2&1\\0&1&-2\\1&4&-1\end{bmatrix}^{-1}=-\frac1{12}\begin{bmatrix}7&6&-5\\-2&0&-2\\-1&6&-1\end{bmatrix}$ (Ex 63, Booklet Ex B).
- $\begin{bmatrix}1&\mathrm j\\-\mathrm j&2\end{bmatrix}^{-1}=\begin{bmatrix}2&-\mathrm j\\\mathrm j&1\end{bmatrix}$ (Ex 51).

## Related
- Topics: [[MATH1054 M17 - Matrices II]]
- Concepts: [[Determinants and Cofactors]] · [[Gaussian Elimination]] · [[Matrix Algebra]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §5.4
- MATH1054 Module Booklet, Module 17
