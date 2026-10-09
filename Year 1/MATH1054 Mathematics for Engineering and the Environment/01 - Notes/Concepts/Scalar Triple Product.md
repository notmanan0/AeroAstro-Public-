---
title: "Scalar Triple Product"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Triple product", "Box product", "Coplanarity test"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Vector (Cross) Product]]", "[[Determinants and Cofactors]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.3.3", "MATH1054 Module Booklet, Module 15"]
---

# Scalar Triple Product

## Definition

> [!note] Definition
> $$[\mathbf a,\mathbf b,\mathbf c]=\mathbf a\cdot(\mathbf b\times\mathbf c)=\begin{vmatrix}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{vmatrix}$$

## Explanation
- Its absolute value is the **volume of the parallelepiped** on the three vectors.
- It is zero iff the vectors are **coplanar** (linearly dependent).
- It is invariant under cyclic shifts; swapping two vectors flips its sign.
- It also appears in the skew-line distance formula $d=\frac{|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|}{|\mathbf d_1\times\mathbf d_2|}$.

## Examples
- $(2,-1,1)$, $(1,2,-3)$ and $(3,\lambda,5)$ are coplanar iff $\lambda=-4$ (Ex 4.31).
- The parallelepiped in Ex 57 has volume $15$.

## Related
- Topics: [[MATH1054 M15 - Vectors II]]
- Concepts: [[Vector (Cross) Product]] · [[Determinants and Cofactors]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §4.3.3
- MATH1054 Module Booklet, Module 15
