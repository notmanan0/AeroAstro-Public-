---
title: "Eigenvalues and Eigenvectors"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Eigenvalue", "Eigenvector", "Characteristic polynomial"]
tags: [math1054, concept, eigenvalues]
status: complete
parent_lectures: ["[[MATH1054 M18 - Matrices III]]", "[[MATH1054 M17 - Matrices II]]"]
related_concepts: ["[[Characteristic Equation and Eigenvalues]]", "[[Natural Frequencies and Mode Shapes]]", "[[Principal Stresses]]", "[[Rank and Consistency of Linear Systems]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.7", "MATH1054 Module Booklet, Module 18"]
---

# Eigenvalues and Eigenvectors

## Definition

> [!note] Definition
>
> $$\mathbf{AX}=\lambda\mathbf X,\ \mathbf X\neq\mathbf0\quad\Longleftrightarrow\quad|\mathbf A-\lambda\mathbf I|=0\ \ (\text{the characteristic equation})$$

## Explanation
1. Solve the characteristic polynomial for the $\lambda$.
2. For each $\lambda$, solve $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$. The equations are dependent, so you get the eigenvector up to a scale factor.

**Checks**: $\sum\lambda=\operatorname{tr}\mathbf A$ and $\prod\lambda=|\mathbf A|$.

**Special cases**:
- **Triangular**: the eigenvalues are the diagonal entries.
- **Symmetric**: real eigenvalues and orthogonal eigenvectors.
- **Rotation**: complex eigenvalues.

**Applications**: vibration modes, principal stresses, and the stability poles of state-space systems.

## Examples
- $\begin{bmatrix}-2&1\\1&-2\end{bmatrix}$: $\lambda=-1$ with $(1,1)$, and $\lambda=-3$ with $(1,-1)$. These are the in-phase and anti-phase modes (Ex 5.40, 5.42).
- The symmetric matrix of Booklet Ex A(iii) has $\lambda=-2,-3,-6$, with orthogonal eigenvectors $(1,0,-1)$, $(1,1,1)$, $(1,-2,1)$.

## Related
- Topics: [[MATH1054 M18 - Matrices III]] · [[MATH1054 M17 - Matrices II]]
- Concepts: [[Characteristic Equation and Eigenvalues]] · [[Natural Frequencies and Mode Shapes]] · [[Principal Stresses]] · [[Rank and Consistency of Linear Systems]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §5.7
- MATH1054 Module Booklet, Module 18
