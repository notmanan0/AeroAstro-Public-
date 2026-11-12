---
title: "Matrix Inverse"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Inverse matrix", "Cofactor method", "Gauss-Jordan inverse", "Singular matrix"]
tags: [math1054, concept, matrices]
status: complete
parent_lectures: ["[[MATH1054 M17 - Matrices II]]"]
related_concepts: ["[[Determinants and Cofactors]]", "[[Gaussian Elimination]]", "[[Matrix Algebra]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.4", "MATH1054 Module Booklet, Module 17"]
---

# Matrix Inverse

The inverse of a square matrix $\mathbf A$ is the matrix $\mathbf A^{-1}$ with $\mathbf A\mathbf A^{-1}=\mathbf A^{-1}\mathbf A=\mathbf I$. It exists exactly when $|\mathbf A|\neq0$ (a **non-singular** matrix), and is then unique.

The cofactor formula follows from the adjoint identity $\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\,\mathbf I$, where $\operatorname{adj}\mathbf A$ is the transpose of the matrix of cofactors. Dividing by the scalar $|\mathbf A|$ gives

$$
\mathbf A^{-1}=\frac{\operatorname{adj}\mathbf A}{|\mathbf A|},\qquad\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}.
$$

The condition $|\mathbf A|\neq0$ is also necessary: taking determinants of $\mathbf A\mathbf A^{-1}=\mathbf I$ gives $|\mathbf A|\,|\mathbf A^{-1}|=1$, which is impossible if $|\mathbf A|=0$, and shows $|\mathbf A^{-1}|=1/|\mathbf A|$. Uniqueness comes from associativity: if $\mathbf B$ and $\mathbf C$ are both inverses, $\mathbf B=(\mathbf{CA})\mathbf B=\mathbf C(\mathbf{AB})=\mathbf C$.

The inverse of a product reverses the order, $(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}$, because $(\mathbf B^{-1}\mathbf A^{-1})(\mathbf{AB})=\mathbf B^{-1}(\mathbf A^{-1}\mathbf A)\mathbf B=\mathbf I$. Transposing $\mathbf A\mathbf A^{-1}=\mathbf I$ gives $(\mathbf A^{\mathrm T})^{-1}=(\mathbf A^{-1})^{\mathrm T}$.

There are two practical methods. The **direct (cofactor) method** above is quickest by hand for $2\times2$ and $3\times3$ matrices. The **elimination method** row-reduces $[\mathbf A\,|\,\mathbf I]$ to $[\mathbf I\,|\,\mathbf A^{-1}]$ (Gauss–Jordan elimination); it works because each row operation is a pre-multiplication by an elementary matrix, and the product of those that turns $\mathbf A$ into $\mathbf I$ is $\mathbf A^{-1}$. Elimination costs of order $n^3$ operations against the factorial growth of cofactor expansion, so it is the only option for large matrices. With an inverse, $\mathbf{AX}=\mathbf b$ has the unique solution $\mathbf X=\mathbf A^{-1}\mathbf b$; in computation the system is solved by elimination directly, without forming $\mathbf A^{-1}$.

For example, $\mathbf A=\begin{bmatrix}-1&2&1\\0&1&-2\\1&4&-1\end{bmatrix}$ has $|\mathbf A|=-1(7)-2(2)+1(-1)=-12$ and

$$
\mathbf A^{-1}=-\frac1{12}\begin{bmatrix}7&6&-5\\-2&0&-2\\-1&6&-1\end{bmatrix},
$$

the same matrix by cofactors (Exercise 63) and by elimination (Booklet Exercise B). Complex entries work the same way: $\begin{bmatrix}1&\mathrm j\\-\mathrm j&2\end{bmatrix}$ has determinant $2+\mathrm j^2=1$ and inverse $\begin{bmatrix}2&-\mathrm j\\\mathrm j&1\end{bmatrix}$ (Exercise 52(c)).

The common trap is forgetting the transpose: the inverse uses $\operatorname{adj}\mathbf A=[A_{ij}]^{\mathrm T}$, not the cofactor matrix itself. Multiplying one row of $\mathbf A$ by one column of the answer, which should give 1 on the diagonal and 0 off it, catches this at once. The second trap is writing $(\mathbf{AB})^{-1}=\mathbf A^{-1}\mathbf B^{-1}$.

## Related

- Topics: [[MATH1054 M17 - Matrices II]] · [[MATH1054 M16 - Matrices I]] · [[MATH1054 M18 - Matrices III]]
- Concepts: [[Determinants and Cofactors]] · [[Gaussian Elimination]] · [[Matrix Algebra]] · [[Rank and Consistency of Linear Systems]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §5.4; MATH1054 Module Booklet, Module 17 (section 7 for the elimination method).
