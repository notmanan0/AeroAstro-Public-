---
title: "MATH1054 M16 - Matrices I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 4: Vectors and Matrices"
order: 16
tags:
  - math1054
  - matrices
  - determinants
aliases: ["MATH1054 Module 16", "Matrices I"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M15 - Vectors II]]"]
next_topics: ["[[MATH1054 M17 - Matrices II]]"]
key_concepts: ["[[Matrix Algebra]]", "[[Determinants and Cofactors]]"]
tutorial_sheets: ["[[MATH1054 M16 Solutions - Matrices I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 16)", "02 - Sources/Modern Engineering Mathematics.pdf (§5.2–5.4)"]
---

# MATH1054 M16 - Matrices I

> [!abstract] Summary
> A matrix is a rectangular array that acts as a **linear map**. This module covers:
> - **matrix algebra**, with its two surprises: multiplication is **not commutative**, and $\mathbf{AB}=\mathbf0$ does not force $\mathbf A$ or $\mathbf B$ to be zero;
> - the **determinant**, a single number that says whether the map is invertible, and by what factor it scales area or volume;
> - the **adjoint**, which leads straight to the inverse in [[MATH1054 M17 - Matrices II|M17]].

## Key Concepts
- [[Matrix Algebra]] · [[Determinants and Cofactors]]

---

## 1. Matrix algebra (James §5.2–5.3)
- **Addition** is defined only for the same size, and is done entry by entry.
- **Multiplication**: $(\mathbf{AB})_{ij}=\sum_k a_{ik}b_{kj}$, which is row $i$ dotted with column $j$. An $(m\times n)(n\times p)$ product is $m\times p$, and the **inner sizes must match**.

| Law | Holds? |
|---|---|
| $(\mathbf{AB})\mathbf C=\mathbf A(\mathbf{BC})$ | ✔ |
| $\mathbf A(\mathbf B+\mathbf C)=\mathbf{AB}+\mathbf{AC}$ | ✔ |
| $\mathbf{AB}=\mathbf{BA}$ | ✘ in general |
| $\mathbf{AB}=\mathbf0\Rightarrow\mathbf A=\mathbf0$ or $\mathbf B=\mathbf0$ | ✘ (Ex 5.4(f)) |
| $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$ | ✔ (reversed order) |

**Special matrices**:
- **square**;
- **diagonal**;
- **unit** $\mathbf I$;
- **symmetric** ($\mathbf A^{\mathrm T}=\mathbf A$);
- **triangular**.

$\mathbf A+\mathbf A^{\mathrm T}$ is always symmetric. A **quadratic form** $\mathbf X^{\mathrm T}\mathbf A\mathbf X$ depends only on the symmetric part of $\mathbf A$.

**Rotation** by $\theta$: $\mathbf R=\begin{bmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{bmatrix}$ satisfies $\mathbf R^{\mathrm T}\mathbf R=\mathbf I$, so it preserves lengths and angles ([[Euler Angles and Rotation Matrices]]).

## 2. Determinants (James §5.4)

$$
\begin{vmatrix}a&b\\c&d\end{vmatrix}=ad-bc,\qquad|\mathbf A|=\sum_{j}a_{ij}A_{ij}\ \ (\text{expansion along any row }i\text{ or column})
$$

Here the cofactor is $A_{ij}=(-1)^{i+j}M_{ij}$, and $M_{ij}$ is the minor: the determinant left after deleting row $i$ and column $j$.

**Properties** (these make big determinants tractable):

| Operation | Effect on $\lvert\mathbf A\rvert$ |
|---|---|
| swap two rows (or columns) | changes sign |
| multiply a row by $k$ | multiplies by $k$ |
| add a multiple of one row to another | **no change** |
| transpose | no change |
| two equal (or proportional) rows | $\lvert\mathbf A\rvert=0$ |
| triangular matrix | product of the diagonal |
| product | $\lvert\mathbf{AB}\rvert=\lvert\mathbf A\rvert\lvert\mathbf B\rvert$ |

> [!tip] Strategy
> Use row and column operations to create zeros, then expand along the row or column with the most zeros. For example:
> - $\begin{vmatrix}1&1&1&1\\1&1+a&1&1\\\cdots\end{vmatrix}=abc$ after subtracting row 1 from the others;
> - Ex 45(b) collapses to a single $3\times3$ determinant after $C_1-C_2$ and $C_3-C_4$.

## 3. The adjoint (James §5.4.x)

$$
\operatorname{adj}\mathbf A=[A_{ij}]^{\mathrm T}\quad(\text{the transposed cofactor matrix}),\qquad\mathbf A\,(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\,\mathbf A=|\mathbf A|\,\mathbf I
$$

Hence $\mathbf A^{-1}=\dfrac{\operatorname{adj}\mathbf A}{|\mathbf A|}$ whenever $|\mathbf A|\neq0$. This is continued in [[MATH1054 M17 - Matrices II|M17]].

**Don't forget the transpose**: the entry in row $i$, column $j$ of the adjoint is the cofactor $A_{ji}$.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M16 Solutions - Matrices I]]
- Prev: [[MATH1054 M15 - Vectors II]] (the $3\times3$ determinant as a triple product) · Next: [[MATH1054 M17 - Matrices II]]
- Applied: [[Global Stiffness Matrix Assembly]], [[State-Space Representation]]

## Sources
- MATH1054 Module Booklet, Module 16; James §5.2–5.4
