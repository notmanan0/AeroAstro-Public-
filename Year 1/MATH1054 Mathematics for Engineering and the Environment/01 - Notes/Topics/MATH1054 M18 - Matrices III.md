---
title: "MATH1054 M18 - Matrices III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 4: Vectors and Matrices"
order: 18
tags:
  - math1054
  - matrices
  - rank
  - eigenvalues
aliases: ["MATH1054 Module 18", "Matrices III"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M17 - Matrices II]]"]
next_topics: ["[[MATH1054 M20 - Further Calculus II]]"]
key_concepts: ["[[Rank and Consistency of Linear Systems]]", "[[Eigenvalues and Eigenvectors]]", "[[Characteristic Equation and Eigenvalues]]"]
tutorial_sheets: ["[[MATH1054 M18 Solutions - Matrices III]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 18)", "02 - Sources/Modern Engineering Mathematics.pdf (§5.6–5.7)"]
---

# MATH1054 M18 - Matrices III

> [!abstract] Summary
> **Rank** counts the genuinely independent rows of a matrix. It settles, for *any* system (square or not), whether solutions exist and how many free parameters they have.
>
> **Eigenvalues and eigenvectors** solve $\mathbf A\mathbf X=\lambda\mathbf X$: the directions a matrix only stretches. They are the natural frequencies and mode shapes of vibration, the poles of control systems, and the principal stresses of solid mechanics.

## Key Concepts
- [[Rank and Consistency of Linear Systems]] · [[Eigenvalues and Eigenvectors]] · [[Characteristic Equation and Eigenvalues]] (SESA2027)

---

## 1. Echelon form and rank (James §5.6)
**Row echelon form**: each row's leading non-zero entry lies to the right of the one above, and any zero rows sit at the bottom. The **rank** is the number of non-zero rows after reduction.
- $\operatorname{rank}\mathbf A\le\min(m,n)$.
- For a square matrix, full rank means $|\mathbf A|\neq0$.

### Consistency of $\mathbf{AX}=\mathbf b$ ($n$ unknowns)
| Condition | Solutions |
|---|---|
| $\operatorname{rank}\mathbf A<\operatorname{rank}[\mathbf A\vert\mathbf b]$ | **none**: some row reads $0=c\neq0$ |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=n$ | **unique** |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=r<n$ | **infinitely many**, with $n-r$ free parameters |

This works for over- and under-determined systems too (Ex 90).

## 2. Eigenvalues and eigenvectors (James §5.7)

$$
\mathbf A\mathbf X=\lambda\mathbf X,\ \mathbf X\neq\mathbf0\quad\Longleftrightarrow\quad(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0\ \text{has a non-trivial solution}\quad\Longleftrightarrow\quad|\mathbf A-\lambda\mathbf I|=0
$$

1. Expand the **characteristic equation** $|\mathbf A-\lambda\mathbf I|=0$, a polynomial of degree $n$. Solve it for the $\lambda$.
2. For each $\lambda$, solve $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$. The equations are dependent: drop one and solve for the ratios.

**Checks**:
- $\sum\lambda_i=\operatorname{tr}\mathbf A$ and $\prod\lambda_i=|\mathbf A|$.
- A triangular matrix has its eigenvalues on the diagonal.

| Matrix type | Eigen-behaviour |
|---|---|
| **symmetric** | real eigenvalues, **orthogonal** eigenvectors (Booklet A(iii)) |
| rotation $\begin{smallmatrix}0&-1\\1&0\end{smallmatrix}$ | complex $\pm\mathrm j$, because no real direction is preserved |
| triangular | $\lambda$ = the diagonal entries |

> [!note] Why engineers care
> - **Vibration**: $\mathbf M\ddot{\mathbf x}+\mathbf K\mathbf x=\mathbf0$ gives eigenvalues $\omega^2$ (natural frequencies) and eigenvectors (mode shapes). The $\begin{bmatrix}-2&1\\1&-2\end{bmatrix}$ of Ex 5.40 is two masses coupled by three springs, with in-phase and anti-phase modes. See [[Natural Frequencies and Mode Shapes]].
> - **Stability**: the eigenvalues of a state matrix are the system poles ([[State-Space Representation]]).
> - **Stress**: the eigenvalues of the stress tensor are the principal stresses ([[Principal Stresses]]).

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M18 Solutions - Matrices III]]
- Prev: [[MATH1054 M17 - Matrices II]]
- Later: SESA2027 [[Characteristic Equation and Eigenvalues]], MATH2048 [[ODE Eigenvalue Problems]] (the function-space analogue)

## Sources
- MATH1054 Module Booklet, Module 18; James §5.6–5.7
