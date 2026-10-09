---
title: "Determinants and Cofactors"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Determinant", "Minor", "Cofactor", "Adjoint", "Adjugate"]
tags: [math1054, concept, matrices]
status: complete
parent_lectures: ["[[MATH1054 M16 - Matrices I]]", "[[MATH1054 M17 - Matrices II]]"]
related_concepts: ["[[Matrix Algebra]]", "[[Matrix Inverse]]", "[[Scalar Triple Product]]", "[[Eigenvalues and Eigenvectors]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.3–5.4", "MATH1054 Module Booklet, Module 16"]
---

# Determinants and Cofactors

## Definition

> [!note] Definition
>
> $$|\mathbf A|=\sum_ja_{ij}A_{ij}\ \ (\text{expanding along any row or column}),\qquad A_{ij}=(-1)^{i+j}M_{ij}$$
>
> Here $M_{ij}$ is the minor: the determinant left after deleting row $i$ and column $j$.

## Explanation
| Operation | Effect on the determinant |
|---|---|
| swap two rows | $\times(-1)$ |
| scale a row by $k$ | $\times k$ |
| $R_i+cR_j$ | unchanged |
| transpose | unchanged |
| triangular matrix | product of the diagonal |
| product | $\lvert\mathbf{AB}\rvert=\lvert\mathbf A\rvert\lvert\mathbf B\rvert$ |

- **Adjoint**: $\operatorname{adj}\mathbf A=[A_{ij}]^{\mathrm T}$, with $\mathbf A\operatorname{adj}\mathbf A=|\mathbf A|\mathbf I$.
- **Strategy**: create zeros with row operations, then expand along the row with the most zeros.
- $|\mathbf A|=0$ iff $\mathbf A$ is singular, i.e. its rows are linearly dependent.

## Examples
- $\begin{vmatrix}1&1&1&1\\1&1+a&1&1\\1&1&1+b&1\\1&1&1&1+c\end{vmatrix}=abc$ (Ex 5.18).
- A $4\times4$ with block symmetry has determinant $100$ (Ex 45(b)).

## Related
- Topics: [[MATH1054 M16 - Matrices I]] · [[MATH1054 M17 - Matrices II]]
- Concepts: [[Matrix Algebra]] · [[Matrix Inverse]] · [[Scalar Triple Product]] · [[Eigenvalues and Eigenvectors]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §5.3–5.4
- MATH1054 Module Booklet, Module 16
