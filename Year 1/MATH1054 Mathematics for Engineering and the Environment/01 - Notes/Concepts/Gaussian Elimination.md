---
title: "Gaussian Elimination"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Elimination", "Back substitution", "Row reduction", "Ill-conditioning"]
tags: [math1054, concept, linear-systems]
status: complete
parent_lectures: ["[[MATH1054 M17 - Matrices II]]", "[[MATH1054 M18 - Matrices III]]"]
related_concepts: ["[[Matrix Inverse]]", "[[Rank and Consistency of Linear Systems]]", "[[Jacobi, Gauss-Seidel and SOR Iteration]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.5", "MATH1054 Module Booklet, Module 17"]
---

# Gaussian Elimination

Gaussian elimination solves $\mathbf{AX}=\mathbf b$ by applying row operations to the augmented matrix $[\mathbf A\,|\,\mathbf b]$ until the coefficient part is upper triangular, then finding the unknowns from the bottom row upwards by back-substitution.

Three elementary row operations are allowed: multiply a row by a non-zero constant, interchange two rows, and add a multiple of one row to another. None changes the solution set. Every new equation is a combination of old ones, so a solution of the old system solves the new one; and each operation is undone by another of the same kind (divide by the constant, swap back, subtract the multiple), so a solution of the new system solves the old one.

The forward sweep uses the diagonal entry of each column, the **pivot**, to clear the entries below it with $R_i\to R_i-(a_{ik}/a_{kk})R_k$. The last equation then holds one unknown, and back-substitution gives

$$
x_n=\frac{c_n}{u_{nn}},\qquad x_i=\frac{1}{u_{ii}}\Big(c_i-\sum_{j=i+1}^{n}u_{ij}x_j\Big)\quad(i=n-1,\dots,1),
$$

where $u_{ij}$ and $c_i$ are the entries of the triangular system. The forward sweep costs about $n^3/3$ multiplications, far less than Cramer's rule or the cofactor inverse, whose determinants grow factorially. A tridiagonal matrix needs only one operation per row (the Thomas algorithm), so its cost grows like $n$.

A zero pivot needs a row swap, and a small pivot magnifies rounding error, so **partial pivoting** swaps the largest available entry of the column into the pivot position before each column is cleared. If $|\mathbf A|=0$ the sweep ends in a row of zeros on the left: $0=0$ means a consistent system with a free parameter, and $0=c\neq0$ means no solution.

For example, Example 5.31:

$$
\left[\begin{array}{ccc|c}1&2&3&10\\-1&1&1&0\\0&1&-1&1\end{array}\right]\xrightarrow{R_2+R_1}\left[\begin{array}{ccc|c}1&2&3&10\\0&3&4&10\\0&1&-1&1\end{array}\right]\xrightarrow{R_3-\frac13R_2}\left[\begin{array}{ccc|c}1&2&3&10\\0&3&4&10\\0&0&-\frac73&-\frac73\end{array}\right],
$$

so $z=1$, then $3y=10-4=6$ gives $y=2$, then $x=10-4-3=3$. The $4\times4$ system of Example 5.34 gives $(x,y,z,t)=(1,1,1,-1)$ and the tridiagonal system of Exercise 73 gives $(1,2,2,3)$ the same way.

The trap is **ill-conditioning**. When the rows are nearly proportional, $|\mathbf A|$ is small relative to the entries and elimination subtracts nearly equal numbers. In Example 5.36, changing one coefficient of $\begin{bmatrix}2&1\\1&0.5001\end{bmatrix}$ from $0.5001$ to $0.4999$, with right-hand side $(0.3,0.6)$, flips the solution from $y=4500$, $x=-2249.85$ to $y=-4500$, $x=2250.15$. The algebra is correct both times; the answer is hypersensitive to the data, so such systems need pivoting and suspicion.

## Related

- Topics: [[MATH1054 M17 - Matrices II]] · [[MATH1054 M18 - Matrices III]] · [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- Concepts: [[Matrix Inverse]] · [[Rank and Consistency of Linear Systems]] · [[Jacobi, Gauss-Seidel and SOR Iteration]] · [[Finite Difference Approximations]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §5.5 (pp. 354–356, 363–368); MATH1054 Module Booklet, Module 17.
