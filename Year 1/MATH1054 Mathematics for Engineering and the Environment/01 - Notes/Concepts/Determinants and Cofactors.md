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

The determinant $|\mathbf A|$ of a square matrix is the single number $a_{11}a_{22}-a_{12}a_{21}$ for a $2\times2$ matrix and, for larger matrices, the sum $\sum_ja_{ij}A_{ij}$ along any row (or column) of each element times its cofactor $A_{ij}=(-1)^{i+j}M_{ij}$, where the minor $M_{ij}$ is the determinant left after deleting row $i$ and column $j$.

The $2\times2$ formula comes from solving $a_{11}x+a_{12}y=b_1$, $a_{21}x+a_{22}y=b_2$ by elimination, which gives $(a_{11}a_{22}-a_{12}a_{21})x=a_{22}b_1-a_{12}b_2$, so a unique solution needs $a_{11}a_{22}-a_{12}a_{21}\neq0$. For three equations the same role is played by the scalar triple product of the rows, $\mathbf r_1\cdot(\mathbf r_2\times\mathbf r_3)$, and writing it out in components gives the first-row expansion

$$
|\mathbf A|=a_{11}\begin{vmatrix}a_{22}&a_{23}\\a_{32}&a_{33}\end{vmatrix}-a_{12}\begin{vmatrix}a_{21}&a_{23}\\a_{31}&a_{33}\end{vmatrix}+a_{13}\begin{vmatrix}a_{21}&a_{22}\\a_{31}&a_{32}\end{vmatrix}.
$$

Geometrically $|\det\mathbf A|$ is the factor by which the map $\mathbf X\mapsto\mathbf{AX}$ scales areas (two dimensions) or volumes (three), and a negative sign means orientation is reversed. That is why $|\mathbf A|=0$ means the rows are linearly dependent and the map flattens space, and why $|\mathbf{AB}|=|\mathbf A||\mathbf B|$: the two scale factors multiply.

Expanding along any row or column gives the same value, so the row or column with most zeros is the cheapest. Zeros are created with row operations, whose effects all follow from expanding along the row being changed: scaling a row by $k$ scales the determinant by $k$; swapping two rows changes its sign; two equal rows therefore give zero; and adding a multiple of one row to another changes nothing, because the determinant splits into the original plus a multiple of one with two equal rows. Transposing changes nothing, and a triangular matrix has determinant equal to the product of its diagonal.

The cofactors also give the adjoint, $\operatorname{adj}\mathbf A=[A_{ij}]^{\mathrm T}$. Multiplying a row by its own cofactors gives $|\mathbf A|$, while multiplying a row by the cofactors of a different row gives the determinant of a matrix with two equal rows, which is zero. Since column $j$ of the adjoint holds the cofactors of row $j$, these two facts are exactly

$$
\mathbf A(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\mathbf A=|\mathbf A|\,\mathbf I,
$$

so $\mathbf A^{-1}=\operatorname{adj}\mathbf A/|\mathbf A|$ whenever $|\mathbf A|\neq0$ ([[Matrix Inverse]]).

For example, with $\mathbf A=\begin{bmatrix}1&1&2\\2&0&1\\3&1&1\end{bmatrix}$ (James Example 5.21) the cofactors of row 1 are $A_{11}=0-1=-1$, $A_{12}=-(2-3)=1$ and $A_{13}=2-0=2$, so $|\mathbf A|=1(-1)+1(1)+2(2)=4$. All nine cofactors, transposed, give $\operatorname{adj}\mathbf A=\begin{bmatrix}-1&1&1\\1&-5&3\\2&2&-2\end{bmatrix}$, and row 1 of $\mathbf A$ times the columns of the adjoint is $(-1+1+4,\ 1-5+4,\ 1+3-4)=(4,0,0)$, the first row of $4\mathbf I$. Row operations shorten larger determinants: subtracting row 1 from the others turns $\begin{vmatrix}1&1&1&1\\1&1+a&1&1\\1&1&1+b&1\\1&1&1&1+c\end{vmatrix}$ into a triangular determinant equal to $abc$ (Example 5.18), and column then row operations reduce Exercise 45(b) to a single $3\times3$ determinant worth $100$.

The common traps are the sign and the transpose. A cofactor is the minor times $(-1)^{i+j}$, so $A_{12}=-M_{12}$; and the entry in row $i$, column $j$ of $\operatorname{adj}\mathbf A$ is $A_{ji}$, not $A_{ij}$. A third trap is scaling: multiplying a whole $n\times n$ matrix by $\lambda$ multiplies every row, so $|\lambda\mathbf A|=\lambda^n|\mathbf A|$.

## Related

- Topics: [[MATH1054 M16 - Matrices I]] (derivations of every property and all work-scheme examples) · [[MATH1054 M17 - Matrices II]] (inverse and Cramer's rule) · [[MATH1054 M18 - Matrices III]] (eigenvalues from $\lvert\mathbf A-\lambda\mathbf I\rvert=0$) · [[MATH1054 M15 - Vectors II]] (triple product)
- Concepts: [[Matrix Algebra]] · [[Matrix Inverse]] · [[Scalar Triple Product]] · [[Vector (Cross) Product]] · [[Eigenvalues and Eigenvectors]] · [[Jacobian and Volume Elements]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §5.3 (determinants, properties (a)–(g), the adjoint, Examples 5.14–5.21) and §5.4 (the inverse); MATH1054 Module Booklet, Module 16
