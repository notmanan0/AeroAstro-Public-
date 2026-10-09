---
title: "MATH1054 M17 - Matrices II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 4: Vectors and Matrices"
order: 17
tags:
  - math1054
  - matrices
  - matrix-inverse
  - linear-systems
aliases: ["MATH1054 Module 17", "Matrices II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M16 - Matrices I]]"]
next_topics: ["[[MATH1054 M18 - Matrices III]]"]
key_concepts: ["[[Matrix Inverse]]", "[[Gaussian Elimination]]"]
tutorial_sheets: ["[[MATH1054 M17 Solutions - Matrices II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 17)", "02 - Sources/Modern Engineering Mathematics.pdf (§5.4–5.5)"]
---

# MATH1054 M17 - Matrices II

> [!abstract] Summary
> The inverse $\mathbf A^{-1}$ exists iff $|\mathbf A|\neq0$. This module covers two ways to find it:
> - the **direct/cofactor** method, which is fine for $2\times2$ and $3\times3$;
> - **elimination**, i.e. Gauss–Jordan on $[\mathbf A|\mathbf I]$, which is far cheaper for big matrices.
>
> Then linear systems $\mathbf{AX}=\mathbf b$: when solutions exist, how to find them by Gaussian elimination and back-substitution, and why ill-conditioned systems are dangerous.

## Key Concepts
- [[Matrix Inverse]] · [[Gaussian Elimination]] · [[Determinants and Cofactors]]

---

## 1. The inverse (James §5.4)
$$
\mathbf A^{-1}=\frac{\operatorname{adj}\mathbf A}{|\mathbf A|},\qquad\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac1{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}
$$
- $(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}$ (reversed order).
- $(\mathbf A^{\mathrm T})^{-1}=(\mathbf A^{-1})^{\mathrm T}$.
- **Singular** means $|\mathbf A|=0$. Typical signs are a zero row, two equal rows, or one row a combination of the others.

**Gauss–Jordan elimination**: row-reduce $[\mathbf A\,|\,\mathbf I]\to[\mathbf I\,|\,\mathbf A^{-1}]$ using only row operations. It costs $O(n^3)$, whereas cofactor expansion costs $O(n!)$.

## 2. When does $\mathbf{AX}=\mathbf b$ have solutions? (James §5.5)
| | $\mathbf b\neq\mathbf0$ | $\mathbf b=\mathbf0$ (homogeneous) |
|---|---|---|
| $\lvert\mathbf A\rvert\neq0$ | **unique**: $\mathbf X=\mathbf A^{-1}\mathbf b$ | only $\mathbf X=\mathbf0$ |
| $\lvert\mathbf A\rvert=0$ | **none** (inconsistent) **or infinitely many** (consistent) | **infinitely many** non-trivial |

The key test for non-trivial homogeneous solutions is $|\mathbf A|=0$. It drives Ex 5.27 and Ex 64, and the eigenvalue problem $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ in [[MATH1054 M18 - Matrices III|M18]].

## 3. Gaussian elimination with back-substitution (James §5.5.x, booklet pp.354–356)
1. Write the augmented matrix $[\mathbf A\,|\,\mathbf b]$.
2. **Forward elimination**: for each column, use the pivot to zero every entry below it with $R_i\to R_i-\frac{a_{ik}}{a_{kk}}R_k$. If the pivot is zero, swap rows.
3. **Back-substitution**: solve the last equation, then work upwards.

Only three operations are allowed: swap rows, scale a row, or add a multiple of one row to another. None of them changes the solution set.

> [!warning] Ill-conditioning (Ex 5.36)
> When $|\mathbf A|\approx0$, the rows are nearly parallel. Tiny changes in the data then cause huge changes in $\mathbf X$: $0.5001\to0.4999$ flips $y$ from $+4500$ to $-4500$. In practice, use partial pivoting, and be suspicious of near-singular systems.

**Tridiagonal systems** (Ex 73) need only one elimination per row. That is the basis of the Thomas algorithm, used everywhere in the CFD and finite-difference work of SESA2029 ([[Finite Difference Approximations]]).

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M17 Solutions - Matrices II]]
- Prev: [[MATH1054 M16 - Matrices I]] · Next: [[MATH1054 M18 - Matrices III]]
- Related: [[Jacobi, Gauss-Seidel and SOR Iteration]] (iterative alternatives), [[Global Stiffness Matrix Assembly]]

## Sources
- MATH1054 Module Booklet, Module 17; James §5.4–5.5
