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

An **eigenvector** of a square matrix $\mathbf A$ is a non-zero vector $\mathbf X$ that $\mathbf A$ maps onto a multiple of itself, $\mathbf A\mathbf X=\lambda\mathbf X$, and the scalar $\lambda$ is the matching **eigenvalue**. The eigenvalues are the roots of the characteristic equation $|\mathbf A-\lambda\mathbf I|=0$.

The characteristic equation comes from rewriting $\mathbf A\mathbf X=\lambda\mathbf X$ as a homogeneous system:

$$
\begin{aligned}
\mathbf A\mathbf X&=\lambda\mathbf I\mathbf X,\\
(\mathbf A-\lambda\mathbf I)\mathbf X&=\mathbf0 .
\end{aligned}
$$

A square homogeneous system has a solution other than $\mathbf X=\mathbf0$ exactly when its matrix is singular ([[Rank and Consistency of Linear Systems]]), so the eigenvalues are the values of $\lambda$ with $|\mathbf A-\lambda\mathbf I|=0$. Expanding the determinant gives a polynomial of degree $n$, the characteristic polynomial, so an $n\times n$ matrix has $n$ eigenvalues counted with multiplicity, real or complex. James writes it as $|\lambda\mathbf I-\mathbf A|=(-1)^n|\mathbf A-\lambda\mathbf I|$, which has the same roots.

The method has two stages. First solve the characteristic equation for the eigenvalues. Then, for each eigenvalue, solve $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$; the equations are dependent, so with distinct eigenvalues one of them can be dropped and the rest give the ratios of the components. Any non-zero multiple of an eigenvector is also an eigenvector, so the answer carries an arbitrary constant. Two checks catch most slips: writing $|\mathbf A-\lambda\mathbf I|=(\lambda_1-\lambda)\cdots(\lambda_n-\lambda)$ and setting $\lambda=0$ gives $\prod\lambda_i=|\mathbf A|$, and comparing the coefficients of $\lambda^{n-1}$ gives $\sum\lambda_i=\operatorname{tr}\mathbf A$, the sum of the diagonal entries.

Three kinds of matrix behave predictably. A triangular matrix has its diagonal entries as eigenvalues, because $\mathbf A-\lambda\mathbf I$ is still triangular and its determinant is the product of the diagonal. A real symmetric matrix has real eigenvalues, and eigenvectors of different eigenvalues are orthogonal: from $\mathbf e_2^{\mathrm T}\mathbf A\mathbf e_1=\lambda_1\mathbf e_2^{\mathrm T}\mathbf e_1$ and, using $\mathbf A^{\mathrm T}=\mathbf A$, $\mathbf e_2^{\mathrm T}\mathbf A\mathbf e_1=(\mathbf A\mathbf e_2)^{\mathrm T}\mathbf e_1=\lambda_2\mathbf e_2^{\mathrm T}\mathbf e_1$, so $(\lambda_1-\lambda_2)\mathbf e_2^{\mathrm T}\mathbf e_1=0$. A rotation such as $\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ turns every real vector, so it has no real eigenvector and its eigenvalues are complex, $\lambda^2+1=0$ giving $\lambda=\pm\mathrm j$.

For example, $\mathbf A=\begin{bmatrix}-2&1\\1&-2\end{bmatrix}$ (James Examples 5.40 and 5.42) has

$$
|\mathbf A-\lambda\mathbf I|=(-2-\lambda)^2-1=\lambda^2+4\lambda+3=(\lambda+1)(\lambda+3),
$$

so $\lambda=-1$ and $\lambda=-3$, with sum $-4=\operatorname{tr}\mathbf A$ and product $3=|\mathbf A|$. For $\lambda=-1$, $\mathbf A+\mathbf I$ has first row $(-1,1)$, so $y=x$ and $\mathbf X=\alpha(1,1)^{\mathrm T}$; for $\lambda=-3$, $\mathbf A+3\mathbf I$ has first row $(1,1)$, so $\mathbf X=\beta(1,-1)^{\mathrm T}$. The matrix is symmetric and the two eigenvectors are perpendicular. It is also the stiffness pattern of two equal masses joined to each other and to two walls by three equal springs: with $\ddot{\mathbf x}=(k/m)\mathbf A\mathbf x$ and $\mathbf x=\mathbf X\cos\omega t$, $\lambda=-m\omega^2/k$, so $\lambda=-1$ is the in-phase mode at $\omega=\sqrt{k/m}$ and $\lambda=-3$ the anti-phase mode at $\omega=\sqrt{3k/m}$. A $3\times3$ symmetric case is Booklet Exercise A(iii), $\begin{pmatrix}-3&1&-1\\1&-5&1\\-1&1&-3\end{pmatrix}$, with $\lambda=-2,-3,-6$ and mutually orthogonal eigenvectors $(1,0,-1)$, $(1,1,1)$ and $(1,-2,1)$.

The common trap is to treat $\mathbf X=\mathbf0$ as an answer, or to drop the arbitrary constant. The zero vector solves $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ for every $\lambda$ and is excluded by definition; if elimination forces every component to zero, the $\lambda$ used is not a root of the characteristic equation.

Eigenvalues are the natural frequencies (through $\omega^2$) of a vibrating system and the eigenvectors its mode shapes; they are the poles of a state-space model, whose signs of real part decide stability; and for a stress tensor they are the principal stresses, with the eigenvectors as principal directions.

## Related

- Topics: [[MATH1054 M18 - Matrices III]] · [[MATH1054 M17 - Matrices II]]
- Concepts: [[Characteristic Equation and Eigenvalues]] · [[Natural Frequencies and Mode Shapes]] · [[Principal Stresses]] · [[Rank and Consistency of Linear Systems]]
- Later: [[ODE Eigenvalue Problems]] (MATH2048) · [[State-Space Representation]] (SESA2027) · [[Eigenvalue Decomposition]] and [[Matrix Exponential and Modal Solution]] (SESA3047)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §5.7.1–5.7.2 and §5.7.7; MATH1054 Module Booklet, Module 18.
