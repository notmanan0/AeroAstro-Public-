---
title: "Matrix Algebra"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Matrix multiplication", "Transpose", "Symmetric matrix"]
tags: [math1054, concept, matrices]
status: complete
parent_lectures: ["[[MATH1054 M16 - Matrices I]]"]
related_concepts: ["[[Determinants and Cofactors]]", "[[Matrix Inverse]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.2–5.3", "MATH1054 Module Booklet, Module 16"]
---

# Matrix Algebra

## Definition

> [!note] Definition
> $$(\mathbf{AB})_{ij}=\sum_ka_{ik}b_{kj}\qquad\big((m\times n)(n\times p)=m\times p\big)$$
> The product is defined only when the inner sizes match. Addition requires equal sizes.

## Explanation
- **Associative and distributive**, but **not commutative**: in general $\mathbf{AB}\neq\mathbf{BA}$.
- $\mathbf{AB}=\mathbf0$ is possible with $\mathbf A,\mathbf B\neq\mathbf0$. So there is no cancellation.
- $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$. $\mathbf A+\mathbf A^{\mathrm T}$ is symmetric.
- **Quadratic forms** $\mathbf X^{\mathrm T}\mathbf{AX}$ depend only on the symmetric part $\frac12(\mathbf A+\mathbf A^{\mathrm T})$.
- **Rotation matrices** satisfy $\mathbf R^{\mathrm T}\mathbf R=\mathbf I$, so they preserve lengths ([[Euler Angles and Rotation Matrices]]).

## Examples
- A $2\times3$ times a $3\times2$ gives $\mathbf{AC}=\mathbf0$ (Ex 5.4(f)).
- $\mathbf{AB}=\mathbf I$ gives $\mathbf B=\mathbf A^{-1}$, so $\mathbf{BX}=\mathbf c$ solves as $\mathbf X=\mathbf{Ac}$ (Ex 5.6).

## Related
- Topics: [[MATH1054 M16 - Matrices I]]
- Concepts: [[Determinants and Cofactors]] · [[Matrix Inverse]] · [[Euler Angles and Rotation Matrices]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §5.2–5.3
- MATH1054 Module Booklet, Module 16
