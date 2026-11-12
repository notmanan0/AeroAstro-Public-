---
title: "Matrix Algebra"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Matrix multiplication", "Transpose", "Symmetric matrix"]
tags: [math1054, concept, matrices]
status: complete
parent_lectures: ["[[MATH1054 M16 - Matrices I]]"]
related_concepts: ["[[Determinants and Cofactors]]", "[[Matrix Inverse]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.2–5.3", "MATH1054 Module Booklet, Module 16"]
---

# Matrix Algebra

Matrix algebra is the set of rules for adding, scaling, multiplying and transposing rectangular arrays of numbers. Its central operation is the product $(\mathbf{AB})_{ij}=\sum_ka_{ik}b_{kj}$, defined for an $m\times p$ matrix times a $p\times n$ matrix and giving an $m\times n$ result.

Addition and multiplication by a scalar work element by element, so they need matrices of the same order and obey all the laws of ordinary arithmetic. The product is different because it is defined to represent composition. If $\mathbf y=\mathbf B\mathbf x$ and $\mathbf z=\mathbf A\mathbf y$ are two linear changes of variables, substituting one into the other gives $\mathbf z=\mathbf C\mathbf x$ with $c_{ij}=\sum_ka_{ik}b_{kj}$, and that is the product $\mathbf{AB}$: row $i$ of $\mathbf A$ multiplied term by term into column $j$ of $\mathbf B$ and summed. The row and column must have the same length, which is the inner-size rule $(m\times p)(p\times n)=m\times n$.

Because the product is a composition, it is associative, $(\mathbf{AB})\mathbf C=\mathbf A(\mathbf{BC})$, and distributive over addition, but not commutative: doing two maps in the other order usually gives a different map, and $\mathbf{BA}$ may not even exist. It also has no cancellation, since one map can send everything another produces to zero. The transpose of a product reverses the order. From the index form,

$$
\begin{aligned}
[(\mathbf{AB})^{\mathrm T}]_{ij}&=(\mathbf{AB})_{ji}\\
&=\sum_ka_{jk}b_{ki}\\
&=\sum_k(\mathbf B^{\mathrm T})_{ik}(\mathbf A^{\mathrm T})_{kj}\\
&=(\mathbf B^{\mathrm T}\mathbf A^{\mathrm T})_{ij},
\end{aligned}
$$

so $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$. Two consequences follow. For a square matrix, $(\mathbf A+\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf A^{\mathrm T}+\mathbf A$, so $\mathbf A+\mathbf A^{\mathrm T}$ is symmetric and $\mathbf A-\mathbf A^{\mathrm T}$ is skew-symmetric, and every square matrix is the sum $\tfrac12(\mathbf A+\mathbf A^{\mathrm T})+\tfrac12(\mathbf A-\mathbf A^{\mathrm T})$. And a quadratic form $\mathbf X^{\mathrm T}\mathbf A\mathbf X$, being $1\times1$, equals its own transpose $\mathbf X^{\mathrm T}\mathbf A^{\mathrm T}\mathbf X$, so it depends only on the symmetric part $\tfrac12(\mathbf A+\mathbf A^{\mathrm T})$.

A rotation matrix $\mathbf R=\begin{bmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{bmatrix}$ satisfies $\mathbf R^{\mathrm T}\mathbf R=\mathbf I$ because $\cos^2\theta+\sin^2\theta=1$, so $|\mathbf{RX}|^2=\mathbf X^{\mathrm T}\mathbf R^{\mathrm T}\mathbf R\mathbf X=|\mathbf X|^2$ and lengths are preserved. The three-dimensional version is the attitude matrix of [[Euler Angles and Rotation Matrices]].

For example, with $\mathbf A=\begin{bmatrix}1&1&0\\2&0&1\end{bmatrix}$ and $\mathbf B=\begin{bmatrix}2&0\\0&1\\1&3\end{bmatrix}$ (James Example 5.4),

$$
\mathbf{AB}=\begin{bmatrix}2+0+0&0+1+0\\4+0+1&0+0+3\end{bmatrix}=\begin{bmatrix}2&1\\5&3\end{bmatrix},\qquad\mathbf{BA}=\begin{bmatrix}2&2&0\\2&0&1\\7&1&3\end{bmatrix},
$$

a $2\times2$ and a $3\times3$ matrix from the same two factors. With $\mathbf C=\begin{bmatrix}1&2\\-1&-2\\-2&-4\end{bmatrix}$ the product $\mathbf{AC}$ is the $2\times2$ zero matrix, although neither factor is zero. And because $\mathbf{AB}=\mathbf I$ for the matrices of James Example 5.6, pre-multiplying $\mathbf{BX}=\mathbf c$ by $\mathbf A$ solves it as $\mathbf X=\mathbf{Ac}$.

The common trap is treating matrices like numbers: writing $(\mathbf A+\mathbf B)^2=\mathbf A^2+2\mathbf{AB}+\mathbf B^2$ (the middle term is $\mathbf{AB}+\mathbf{BA}$), cancelling a matrix from $\mathbf{AB}=\mathbf{AC}$, or writing $(\mathbf{AB})^{\mathrm T}=\mathbf A^{\mathrm T}\mathbf B^{\mathrm T}$. A quick order check catches the last one: if $\mathbf A$ is $2\times3$ and $\mathbf B$ is $3\times4$, then $\mathbf A^{\mathrm T}\mathbf B^{\mathrm T}$ is $(3\times2)(4\times3)$ and does not exist.

## Related

- Topics: [[MATH1054 M16 - Matrices I]] (derivations and all work-scheme examples) · [[MATH1054 M17 - Matrices II]] · [[MATH1054 M18 - Matrices III]]
- Concepts: [[Determinants and Cofactors]] · [[Matrix Inverse]] · [[Gaussian Elimination]] · [[Scalar (Dot) Product]] · [[Euler Angles and Rotation Matrices]] · [[State-Space Representation]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §5.2 (definitions, operations, multiplication and its properties, Examples 5.1, 5.4–5.8); MATH1054 Module Booklet, Module 16
