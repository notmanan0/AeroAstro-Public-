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

The **rank** of a matrix is the number of non-zero rows in its echelon form, which equals the number of linearly independent rows. A linear system $\mathbf A\mathbf X=\mathbf b$ is **consistent** (has at least one solution) exactly when $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]$.

Row reduction with the elementary row operations (interchange, scale by a non-zero constant, add a multiple of another row) never changes the solution set, because each operation can be undone. Reduce the augmented matrix $[\mathbf A|\mathbf b]$ to echelon form, where each row's leading entry lies to the right of the one above and zero rows sit at the bottom. If $\operatorname{rank}\mathbf A=r$, there are $r$ staircase rows and below them rows that are zero in the $\mathbf A$ part. Such a row reads $0=v$. If any $v\neq0$, no $\mathbf X$ satisfies it, and that row is non-zero in $[\mathbf A|\mathbf b]$, so $\operatorname{rank}[\mathbf A|\mathbf b]=r+1$. If every $v=0$, the ranks are equal, and back substitution gives the $r$ leading unknowns in terms of the other $n-r$, which are free. For $n$ unknowns:

| Ranks | Solutions |
|---|---|
| $\operatorname{rank}\mathbf A<\operatorname{rank}[\mathbf A\vert\mathbf b]$ | none |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=n$ | exactly one |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=r<n$ | infinitely many, with $n-r$ free parameters |

The argument uses only the echelon form, so it holds for non-square systems, whether underspecified (more unknowns than equations) or overspecified (more equations than unknowns). Since each non-zero row needs its own row and its own leading column, $\operatorname{rank}\mathbf A\le\min(m,n)$ for an $m\times n$ matrix; a square matrix has full rank exactly when $|\mathbf A|\neq0$. An equivalent definition of rank is the order of the largest square submatrix with non-zero determinant.

A homogeneous system $\mathbf A\mathbf X=\mathbf0$ is always consistent, since it has the trivial solution $\mathbf X=\mathbf0$. It has non-trivial solutions if and only if $\operatorname{rank}\mathbf A<n$, which for a square matrix means $|\mathbf A|=0$. This is the condition behind the characteristic equation of [[Eigenvalues and Eigenvectors]], and behind the rank test for linear dependence: vectors placed as the columns of $\mathbf A$ are dependent exactly when $\operatorname{rank}\mathbf A$ is less than the number of vectors.

For example, Exercise 88(a), $x+2y+3z=8$, $3x+2y+z=4$, $x+y+z=3$, reduces by $R_2-3R_1$, $R_3-R_1$ and then $R_3-\tfrac14R_2$ to

$$
\left[\begin{array}{ccc|c}1&2&3&8\\0&-4&-8&-20\\0&0&0&0\end{array}\right].
$$

Both ranks are 2 with $n=3$, so there is one free parameter: $z=\alpha$, $y=5-2\alpha$, $x=8-2y-3z=\alpha-2$, giving $(x,y,z)=(\alpha-2,\,5-2\alpha,\,\alpha)$. By contrast, Exercise 88(b) reduces to a last row $(0\ 0\ 0\ 0\,|\,-1)$, and Exercise 90(b), three equations in two unknowns, to $(0\ 0\,|\,-\tfrac{21}4)$: both are inconsistent, with $\operatorname{rank}\mathbf A=2$ and $\operatorname{rank}[\mathbf A|\mathbf b]=3$. James Example 5.38(b) has five unknowns and rank 2 for both matrices, so its solution has three free parameters.

The common trap is to miscount a row of the form $(0\ \cdots\ 0\,|\,c)$ with $c\neq0$. It is a zero row of $\mathbf A$ and a non-zero row of $[\mathbf A|\mathbf b]$; counting it the same way for both hides the inconsistency. A second slip is to compare the rank with the number of equations rather than the number of unknowns $n$ when counting free parameters.

## Related

- Topics: [[MATH1054 M18 - Matrices III]] · [[MATH1054 M17 - Matrices II]]
- Concepts: [[Gaussian Elimination]] · [[Eigenvalues and Eigenvectors]] · [[Determinants and Cofactors]] · [[Matrix Inverse]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §5.6; MATH1054 Module Booklet, Module 18.
