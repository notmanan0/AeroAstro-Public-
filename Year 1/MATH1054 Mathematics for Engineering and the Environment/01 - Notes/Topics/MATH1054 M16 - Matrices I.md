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
status: lectured
coverage: "Module Booklet Module 16 work scheme; James §5.1–5.3 (pp. 297–339): definitions and special matrices, addition, scalar multiples, the transpose, matrix products and their laws, (AB)^T, quadratic forms, rotation matrices, determinants, minors and cofactors, properties of determinants, |AB| = |A||B|, the adjoint and A adj A = |A| I"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M15 - Vectors II]]"]
next_topics: ["[[MATH1054 M17 - Matrices II]]"]
key_concepts: ["[[Matrix Algebra]]", "[[Determinants and Cofactors]]"]
tutorial_sheets: ["[[MATH1054 M16 Solutions - Matrices I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 16)", "02 - Sources/Modern Engineering Mathematics.pdf (§5.2–5.4)"]
---

# MATH1054 M16 - Matrices I

> [!abstract] Summary
> A matrix is a rectangular array of numbers that represents a linear map, and the matrix product $(\mathbf{AB})_{ij}=\sum_k a_{ik}b_{kj}$ is the composition of two such maps. Matrix algebra keeps the associative and distributive laws but loses commutativity and cancellation, and transposing a product reverses its order, $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$. The determinant of a square matrix is a single number, computed by cofactor expansion along any row or column, that measures how the map scales area or volume and is zero exactly when the map collapses space. The adjoint, the transposed matrix of cofactors, satisfies $\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\,\mathbf I$, which is the route to the inverse in M17.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks which sums or products exist, asks for a product, transpose, minor, cofactor or determinant, or asks for $\operatorname{adj}\mathbf A$.
> - **Assumptions:** sums need equal orders; $\mathbf{AB}$ needs (columns of $\mathbf A$) = (rows of $\mathbf B$); determinants, cofactors and adjoints exist only for square matrices.
> - **Method:** 1. Write the order of every matrix and check that each operation is defined. 2. Multiply row of the first by column of the second. 3. For a determinant, create zeros with row or column operations (adding multiples changes nothing). 4. Expand along the row or column with most zeros, using signs $(-1)^{i+j}$. 5. For $\operatorname{adj}\mathbf A$, find all nine cofactors, then transpose, and check $\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\mathbf I$.
> - **Common mistakes:** dropping the sign $(-1)^{i+j}$ when turning a minor into a cofactor; forgetting the transpose in the adjoint (or the order reversal in $(\mathbf{AB})^{\mathrm T}$).
> - **Practise:** [[#The adjoint of a 3 by 3 matrix (Example 5.21)]] · [[MATH1054 M16 Solutions - Matrices I#Part C: Specimen Test 16|Specimen Test 16]]

A matrix stores the coefficients of a set of linear equations, or of a linear change of coordinates, in one object. The equations $x+2y=3$, $x+y=4$, $2x+y+z=5$ become $\mathbf{AX}=\mathbf b$ with $\mathbf A$ the $3\times3$ array of coefficients, and a rotation of axes becomes $\mathbf X'=\mathbf R\mathbf X$. Engineering problems produce such systems in very large numbers: a finite-element model of a wing, a truss, an electrical network solved by mesh currents and the state-space model of an aircraft all reduce to matrix equations, and computers handle them as matrices.

The product is defined so that multiplying matrices does the same thing as performing one linear map after another. Everything unusual about matrix algebra follows from that. Doing two maps in the opposite order usually gives a different result, so $\mathbf{AB}\neq\mathbf{BA}$, and one map can flatten everything another produces, so $\mathbf{AB}=\mathbf0$ is possible with neither factor zero.

The determinant answers the question of whether a square system $\mathbf{AX}=\mathbf b$ has a unique solution. For a $2\times2$ system it appears as the denominator when the equations are solved, and for a $3\times3$ system it is the scalar triple product of the rows from [[MATH1054 M15 - Vectors II|M15]]. Geometrically it is the factor by which the map multiplies areas (in two dimensions) or volumes (in three), with a sign recording whether orientation is reversed. The cofactors that build the determinant also build the adjoint, and dividing the adjoint by the determinant gives the inverse matrix, which [[MATH1054 M17 - Matrices II|M17]] develops alongside Cramer's rule and Gaussian elimination. Eigenvalues in [[MATH1054 M18 - Matrices III|M18]] are the values of $\lambda$ that make $|\mathbf A-\lambda\mathbf I|=0$.

---

## 1. Matrices, orders and special matrices

A **matrix of order $m\times n$** is a rectangular array of numbers with $m$ rows and $n$ columns,

$$
\mathbf A=\begin{bmatrix}a_{11}&a_{12}&\cdots&a_{1n}\\a_{21}&a_{22}&\cdots&a_{2n}\\\vdots&\vdots&&\vdots\\a_{m1}&a_{m2}&\cdots&a_{mn}\end{bmatrix}=[a_{ij}],
$$

where $a_{ij}$ is the element in row $i$ and column $j$. The order is always written rows first. Square brackets (James) and curved brackets (the booklet) mean the same thing, and either is accepted in answers.

A matrix with one column is a **column vector** ($m\times1$) and one with one row is a **row vector** ($1\times n$). In matrix work "vector" means a column vector unless stated otherwise, so the position vector $(x,y,z)$ of [[MATH1054 M14 - Vectors I|M14]] becomes $\mathbf X=[x\ y\ z]^{\mathrm T}$.

A **square matrix of order $n$** has $m=n$. Its elements $a_{11},a_{22},\dots,a_{nn}$ form the **leading diagonal** (also called the principal or main diagonal), and their sum is the **trace**,

$$
\operatorname{tr}\mathbf A=\sum_{i=1}^{n}a_{ii}.
$$

The special square matrices are these.

- A **diagonal matrix** has every element off the leading diagonal equal to zero (diagonal elements may also be zero).
- The **unit matrix** $\mathbf I_n$ (also called the identity matrix) is the diagonal matrix with every diagonal element 1. Its elements are the Kronecker delta, $\delta_{ij}=1$ if $i=j$ and $0$ if $i\neq j$. A unit matrix must be square.
- An **upper triangular** matrix has $a_{ij}=0$ for $i>j$ (zeros below the diagonal); a **lower triangular** matrix has $a_{ij}=0$ for $i<j$.
- A **symmetric** matrix satisfies $\mathbf A^{\mathrm T}=\mathbf A$, that is $a_{ij}=a_{ji}$, so its elements are mirrored about the leading diagonal. A symmetric matrix must be square, because $\mathbf A^{\mathrm T}$ is $n\times m$ and can only equal $\mathbf A$ if $m=n$ (Specimen Test 16, Q2).
- A **skew-symmetric** (antisymmetric) matrix satisfies $\mathbf A^{\mathrm T}=-\mathbf A$. On the diagonal this gives $a_{ii}=-a_{ii}$, so every diagonal element is zero.

The **zero matrix** $\mathbf0$ of any order has every element zero, and is not required to be square. The **transpose** $\mathbf A^{\mathrm T}$ of an $m\times n$ matrix is the $n\times m$ matrix with rows and columns interchanged:

$$
(\mathbf A^{\mathrm T})_{ij}=a_{ji}.
$$

A column vector transposes to a row vector and vice versa. For example $\mathbf B=\begin{bmatrix}1&2&3\\2&3&4\\3&4&5\end{bmatrix}$ is symmetric with $\operatorname{tr}\mathbf B=1+3+5=9$, and $\begin{bmatrix}2&0&0\\0&3&0\\0&0&4\end{bmatrix}$ is diagonal with trace 9.

## 2. Equality, addition, scalar multiples and the transpose

Two matrices are **equal** if they have the same order and every pair of corresponding elements is equal, $a_{ij}=b_{ij}$ for all $i,j$. Addition and subtraction are defined only for matrices of the same order, element by element:

$$
(\mathbf A\pm\mathbf B)_{ij}=a_{ij}\pm b_{ij}.
$$

Multiplying by a scalar $\lambda$ multiplies every element, $(\lambda\mathbf A)_{ij}=\lambda a_{ij}$. Subtraction is then addition of a scalar multiple, $\mathbf C-\mathbf A=\mathbf C+(-1)\mathbf A$. Because every one of these operations is ordinary arithmetic on each element, the usual laws carry over:

$$
\mathbf A+\mathbf B=\mathbf B+\mathbf A,\qquad(\mathbf A+\mathbf B)+\mathbf C=\mathbf A+(\mathbf B+\mathbf C),\qquad\lambda(\mathbf A+\mathbf B)=\lambda\mathbf A+\lambda\mathbf B.
$$

Transposing twice returns the original matrix, and the transpose of a sum is the sum of the transposes:

$$
(\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf A,\qquad(\mathbf A+\mathbf B)^{\mathrm T}=\mathbf A^{\mathrm T}+\mathbf B^{\mathrm T}.
$$

For a square matrix these two facts show that $\mathbf A+\mathbf A^{\mathrm T}$ is always symmetric:

$$
\begin{aligned}
(\mathbf A+\mathbf A^{\mathrm T})^{\mathrm T}&=\mathbf A^{\mathrm T}+(\mathbf A^{\mathrm T})^{\mathrm T}\\
&=\mathbf A^{\mathrm T}+\mathbf A\\
&=\mathbf A+\mathbf A^{\mathrm T}.
\end{aligned}
$$

The same steps give $(\mathbf A-\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf A^{\mathrm T}-\mathbf A=-(\mathbf A-\mathbf A^{\mathrm T})$, so $\mathbf A-\mathbf A^{\mathrm T}$ is skew-symmetric. Adding the two halves splits any square matrix into a symmetric part and a skew-symmetric part:

$$
\mathbf A=\tfrac12(\mathbf A+\mathbf A^{\mathrm T})+\tfrac12(\mathbf A-\mathbf A^{\mathrm T}).
$$

### Sums, multiples and transposes (Example 5.1)

Take

$$
\mathbf A=\begin{bmatrix}1&2&1\\1&1&2\\1&1&1\end{bmatrix},\qquad\mathbf B=\begin{bmatrix}2&1\\1&0\\1&1\end{bmatrix},\qquad\mathbf C=\begin{bmatrix}0&1&1\\0&0&1\\1&0&0\end{bmatrix},
$$

so $\mathbf A$ and $\mathbf C$ are $3\times3$ and $\mathbf B$ is $3\times2$.

| | Expression | Result |
|---|---|---|
| (a) | $\mathbf A+\mathbf B$ | not defined ($3\times3$ and $3\times2$) |
| (b) | $\mathbf A+\mathbf C$ | $\begin{bmatrix}1&3&2\\1&1&3\\2&1&1\end{bmatrix}$ |
| (c) | $\mathbf C-\mathbf A$ | $\begin{bmatrix}-1&-1&0\\-1&-1&-1\\0&-1&-1\end{bmatrix}$ |
| (d) | $3\mathbf A$ | $\begin{bmatrix}3&6&3\\3&3&6\\3&3&3\end{bmatrix}$ |
| (e) | $4\mathbf B$ | $\begin{bmatrix}8&4\\4&0\\4&4\end{bmatrix}$ |
| (f) | $\mathbf C+\mathbf B$ | not defined |
| (g) | $3\mathbf A+2\mathbf C$ | $\begin{bmatrix}3&8&5\\3&3&8\\5&3&3\end{bmatrix}$ |
| (h) | $\mathbf A^{\mathrm T}+\mathbf A$ | $\begin{bmatrix}2&3&2\\3&2&3\\2&3&2\end{bmatrix}$, symmetric |
| (i) | $\mathbf A+\mathbf C^{\mathrm T}+\mathbf B^{\mathrm T}$ | not defined ($\mathbf B^{\mathrm T}$ is $2\times3$) |

Part (h) illustrates the symmetric-part result. The skew-symmetric part of the same matrix is $\tfrac12(\mathbf A-\mathbf A^{\mathrm T})$ with $\mathbf A-\mathbf A^{\mathrm T}=\begin{bmatrix}0&1&0\\-1&0&1\\0&-1&0\end{bmatrix}$, which has the zero diagonal every skew-symmetric matrix has.

## 3. Matrix multiplication

### The product as composition of two linear maps

Two linear changes of variables in the plane, $\mathbf y=\mathbf B\mathbf x$ and $\mathbf z=\mathbf A\mathbf y$, give:

$$
\begin{aligned}
y_1&=b_{11}x_1+b_{12}x_2, & z_1&=a_{11}y_1+a_{12}y_2,\\
y_2&=b_{21}x_1+b_{22}x_2, & z_2&=a_{21}y_1+a_{22}y_2.
\end{aligned}
$$

Substitute the first pair into $z_1$:

$$
\begin{aligned}
z_1&=a_{11}(b_{11}x_1+b_{12}x_2)+a_{12}(b_{21}x_1+b_{22}x_2)\\
&=(a_{11}b_{11}+a_{12}b_{21})x_1+(a_{11}b_{12}+a_{12}b_{22})x_2 .
\end{aligned}
$$

The same substitution into $z_2$ gives

$$
z_2=(a_{21}b_{11}+a_{22}b_{21})x_1+(a_{21}b_{12}+a_{22}b_{22})x_2 .
$$

The composite map $\mathbf z=\mathbf C\mathbf x$ therefore has coefficient matrix

$$
\mathbf C=\begin{bmatrix}a_{11}b_{11}+a_{12}b_{21}&a_{11}b_{12}+a_{12}b_{22}\\a_{21}b_{11}+a_{22}b_{21}&a_{21}b_{12}+a_{22}b_{22}\end{bmatrix},
$$

and this is defined to be the product $\mathbf{AB}$. Each element is a row of $\mathbf A$ multiplied term by term into a column of $\mathbf B$ and added up. In general, if $\mathbf A$ is $m\times p$ and $\mathbf B$ is $p\times n$, then $\mathbf C=\mathbf{AB}$ is the $m\times n$ matrix with

$$
c_{ij}=\sum_{k=1}^{p}a_{ik}b_{kj}=a_{i1}b_{1j}+a_{i2}b_{2j}+\dots+a_{ip}b_{pj}.
$$

This is the scalar product of row $i$ of $\mathbf A$ with column $j$ of $\mathbf B$, so the row and the column must have the same length. The product exists only when the inner sizes match, and the result has the outer sizes:

$$
(m\times p)(p\times n)=(m\times n).
$$

For example, $z_1=y_1+3y_2$, $z_2=2y_1-y_2$ with $y_1=-x_1+2x_2$, $y_2=2x_1-x_2$ gives, by substitution, $z_1=5x_1-x_2$ and $z_2=-4x_1+5x_2$. The matrix product gives the same coefficients:

$$
\begin{bmatrix}1&3\\2&-1\end{bmatrix}\begin{bmatrix}-1&2\\2&-1\end{bmatrix}=\begin{bmatrix}(1)(-1)+(3)(2)&(1)(2)+(3)(-1)\\(2)(-1)+(-1)(2)&(2)(2)+(-1)(-1)\end{bmatrix}=\begin{bmatrix}5&-1\\-4&5\end{bmatrix}.
$$

A matrix times a column vector is the special case $n=1$, and it is how a set of linear equations is written. The system $x+2y=3$, $x+y=4$, $2x+y+z=5$ is

$$
\begin{bmatrix}1&2&0\\1&1&0\\2&1&1\end{bmatrix}\begin{bmatrix}x\\y\\z\end{bmatrix}=\begin{bmatrix}3\\4\\5\end{bmatrix},\qquad\text{that is}\qquad\mathbf{AX}=\mathbf b .
$$

A $1\times1$ matrix is treated as a number, so the brackets are dropped. With this convention $\mathbf X^{\mathrm T}\mathbf X=x^2+y^2+z^2$ is the squared length of $\mathbf X$, and $\mathbf X^{\mathrm T}\mathbf X'=xx'+yy'+zz'$ is the scalar product of [[Scalar (Dot) Product|M14]] written as a matrix product.

### Products and a zero product (Example 5.4)

Take

$$
\mathbf A=\begin{bmatrix}1&1&0\\2&0&1\end{bmatrix},\quad\mathbf B=\begin{bmatrix}2&0\\0&1\\1&3\end{bmatrix},\quad\mathbf b=\begin{bmatrix}-1\\2\end{bmatrix},\quad\mathbf c=\begin{bmatrix}1\\1\\-1\end{bmatrix},\quad\mathbf C=\begin{bmatrix}1&2\\-1&-2\\-2&-4\end{bmatrix}.
$$

(a) $\mathbf{AB}$ is $(2\times3)(3\times2)=2\times2$:

$$
\mathbf{AB}=\begin{bmatrix}(1)(2)+(1)(0)+(0)(1)&(1)(0)+(1)(1)+(0)(3)\\(2)(2)+(0)(0)+(1)(1)&(2)(0)+(0)(1)+(1)(3)\end{bmatrix}=\begin{bmatrix}2&1\\5&3\end{bmatrix}.
$$

(b) $\mathbf{BA}$ is $(3\times2)(2\times3)=3\times3$:

$$
\mathbf{BA}=\begin{bmatrix}2+0&2+0&0+0\\0+2&0+0&0+1\\1+6&1+0&0+3\end{bmatrix}=\begin{bmatrix}2&2&0\\2&0&1\\7&1&3\end{bmatrix}.
$$

So $\mathbf{AB}\neq\mathbf{BA}$; they are not even the same size.

(c) $\mathbf B\mathbf b=\begin{bmatrix}2(-1)+0(2)\\0(-1)+1(2)\\1(-1)+3(2)\end{bmatrix}=\begin{bmatrix}-2\\2\\5\end{bmatrix}$.

(d) $\mathbf A^{\mathrm T}\mathbf b=\begin{bmatrix}1&2\\1&0\\0&1\end{bmatrix}\begin{bmatrix}-1\\2\end{bmatrix}=\begin{bmatrix}-1+4\\-1+0\\0+2\end{bmatrix}=\begin{bmatrix}3\\-1\\2\end{bmatrix}$.

(e) $\mathbf c^{\mathrm T}(\mathbf A^{\mathrm T}\mathbf b)=(1)(3)+(1)(-1)+(-1)(2)=0$, the $1\times1$ zero matrix.

(f) $\mathbf{AC}=\begin{bmatrix}1-1+0&2-2+0\\2+0-2&4+0-4\end{bmatrix}=\begin{bmatrix}0&0\\0&0\end{bmatrix}$, although neither $\mathbf A$ nor $\mathbf C$ is zero.

Not every product exists: $\mathbf A$ is $2\times3$ and $\mathbf b$ is $2\times1$, so neither $\mathbf A\mathbf b$ nor $\mathbf b\mathbf A$ can be formed.

### Exercise 13, which products exist

With $\mathbf A=\begin{bmatrix}1&2&1\\3&0&2\end{bmatrix}$, $\mathbf B=\begin{bmatrix}4&1&3\\0&2&1\end{bmatrix}$ (both $2\times3$) and $\mathbf C=\begin{bmatrix}1&2\\3&1\\2&3\end{bmatrix}$ ($3\times2$), check the inner sizes:

| Product | Sizes | Exists? | Value |
|---|---|---|---|
| $\mathbf{AB}$ | $(2\times3)(2\times3)$ | no | |
| $\mathbf{AC}$ | $(2\times3)(3\times2)$ | yes | $\begin{bmatrix}1+6+2&2+2+3\\3+0+4&6+0+6\end{bmatrix}=\begin{bmatrix}9&7\\7&12\end{bmatrix}$ |
| $\mathbf{BC}$ | $(2\times3)(3\times2)$ | yes | $\begin{bmatrix}4+3+6&8+1+9\\0+6+2&0+2+3\end{bmatrix}=\begin{bmatrix}13&18\\8&5\end{bmatrix}$ |
| $\mathbf{AB}^{\mathrm T}$ | $(2\times3)(3\times2)$ | yes | $\begin{bmatrix}4+2+3&0+4+1\\12+0+6&0+0+2\end{bmatrix}=\begin{bmatrix}9&5\\18&2\end{bmatrix}$ |
| $\mathbf{AC}^{\mathrm T}$ | $(2\times3)(2\times3)$ | no | |
| $\mathbf{BC}^{\mathrm T}$ | $(2\times3)(2\times3)$ | no | |

### Exercise 12, products and special matrices

With $\mathbf A=\begin{bmatrix}1&1&1\\1&1&1\end{bmatrix}$, $\mathbf B=\begin{bmatrix}1&1&0\\1&1&0\\0&0&-1\end{bmatrix}$ and $\mathbf C=\begin{bmatrix}0&2\\1&1\\-1&-1\end{bmatrix}$:

$$
\mathbf{AB}=\begin{bmatrix}2&2&-1\\2&2&-1\end{bmatrix},\quad\mathbf{AC}=\begin{bmatrix}0&2\\0&2\end{bmatrix},\quad\mathbf{BC}=\begin{bmatrix}1&3\\1&3\\1&1\end{bmatrix},\quad\mathbf{CA}=\begin{bmatrix}2&2&2\\2&2&2\\-2&-2&-2\end{bmatrix},\quad\mathbf{BA}^{\mathrm T}=\begin{bmatrix}2&2\\2&2\\-1&-1\end{bmatrix}.
$$

Every row of $\mathbf A$ is $(1,1,1)$, so each row of $\mathbf{AB}$ is the list of column sums of $\mathbf B$, and each row of $\mathbf{CA}$ repeats the row sum of $\mathbf C$. Only $\mathbf{AC}$ and $\mathbf{CA}$ are square, and neither is diagonal, unit or symmetric: $(\mathbf{AC})_{12}=2\neq(\mathbf{AC})_{21}=0$ and $(\mathbf{CA})_{13}=2\neq(\mathbf{CA})_{31}=-2$.

### Specimen Test 16, Q1

The orders are $\mathbf A=\begin{pmatrix}1&2&-1\\3&1&4\end{pmatrix}$: $2\times3$; $\mathbf B=\begin{pmatrix}-2&1\\3&2\end{pmatrix}$: $2\times2$; $\mathbf C=\begin{pmatrix}0&-2\\-1&1\end{pmatrix}$: $2\times2$; $\mathbf D=\begin{pmatrix}3&1\\2&-1\\0&1\end{pmatrix}$: $3\times2$.

| | Expression | Exists? | Result |
|---|---|---|---|
| (i) | $2\mathbf C-\mathbf B$ | yes, $2\times2$ | $\begin{pmatrix}0&-4\\-2&2\end{pmatrix}-\begin{pmatrix}-2&1\\3&2\end{pmatrix}=\begin{pmatrix}2&-5\\-5&0\end{pmatrix}$ |
| (ii) | $\mathbf A^{\mathrm T}-\mathbf D^{\mathrm T}$ | no | $3\times2$ minus $2\times3$ |
| (iii) | $\mathbf{AD}$ | yes, $2\times2$ | $\begin{pmatrix}3+4+0&1-2-1\\9+2+0&3-1+4\end{pmatrix}=\begin{pmatrix}7&-2\\11&6\end{pmatrix}$ |
| (iv) | $\mathbf{AB}^{\mathrm T}$ | no | $(2\times3)(2\times2)$, inner sizes differ |
| (v) | $\mathbf{DC}$ | yes, $3\times2$ | $\begin{pmatrix}0-1&-6+1\\0+1&-4-1\\0-1&0+1\end{pmatrix}=\begin{pmatrix}-1&-5\\1&-5\\-1&1\end{pmatrix}$ |

## 4. Laws of matrix multiplication and the transpose of a product

### Order matters

Matrices do not commute in general. Even for two square matrices of the same size,

$$
\begin{bmatrix}1&0\\0&0\end{bmatrix}\begin{bmatrix}1&2\\1&0\end{bmatrix}=\begin{bmatrix}1&2\\0&0\end{bmatrix},\qquad\begin{bmatrix}1&2\\1&0\end{bmatrix}\begin{bmatrix}1&0\\0&0\end{bmatrix}=\begin{bmatrix}1&0\\1&0\end{bmatrix}.
$$

If $\mathbf A$ is $m\times p$ and $\mathbf B$ is $p\times n$, then $\mathbf{BA}$ exists only when $n=m$; for instance $[1\ 1\ 1]$ times a $3\times2$ matrix exists but the reverse does not. The order is therefore named: $\mathbf{AB}$ is $\mathbf B$ **pre-multiplied** by $\mathbf A$, and $\mathbf{BA}$ is $\mathbf B$ **post-multiplied** by $\mathbf A$. Whatever is done to one side of a matrix equation must be done on the same side of the other.

### Associative law

Let $\mathbf A$ be $m\times p$, $\mathbf B$ be $p\times q$ and $\mathbf C$ be $q\times n$. Write out element $(i,j)$ of $(\mathbf{AB})\mathbf C$:

$$
\begin{aligned}
[(\mathbf{AB})\mathbf C]_{ij}&=\sum_{l=1}^{q}(\mathbf{AB})_{il}\,c_{lj}\\
&=\sum_{l=1}^{q}\Big(\sum_{k=1}^{p}a_{ik}b_{kl}\Big)c_{lj}\\
&=\sum_{k=1}^{p}\sum_{l=1}^{q}a_{ik}b_{kl}c_{lj}\\
&=\sum_{k=1}^{p}a_{ik}\Big(\sum_{l=1}^{q}b_{kl}c_{lj}\Big)\\
&=\sum_{k=1}^{p}a_{ik}(\mathbf{BC})_{kj}\\
&=[\mathbf A(\mathbf{BC})]_{ij}.
\end{aligned}
$$

The only move in the middle is swapping the order of two finite sums. So $(\mathbf{AB})\mathbf C=\mathbf A(\mathbf{BC})$ and the brackets can be dropped. This is the algebra behind composition: applying $\mathbf C$, then $\mathbf B$, then $\mathbf A$ is the same however the steps are grouped.

### Distributive laws, scalars and the unit matrix

Element $(i,j)$ of $(\mathbf A+\mathbf B)\mathbf C$ splits in one line:

$$
\begin{aligned}
[(\mathbf A+\mathbf B)\mathbf C]_{ij}&=\sum_k(a_{ik}+b_{ik})c_{kj}\\
&=\sum_ka_{ik}c_{kj}+\sum_kb_{ik}c_{kj}\\
&=(\mathbf{AC})_{ij}+(\mathbf{BC})_{ij},
\end{aligned}
$$

so $(\mathbf A+\mathbf B)\mathbf C=\mathbf{AC}+\mathbf{BC}$, and likewise $\mathbf A(\mathbf B+\mathbf C)=\mathbf{AB}+\mathbf{AC}$. Brackets multiply out as usual provided the left-right order of every product is kept. A scalar can be moved anywhere, $(\lambda\mathbf A)\mathbf B=\mathbf A(\lambda\mathbf B)=\lambda\mathbf{AB}$, because $\sum_k(\lambda a_{ik})b_{kj}=\sum_ka_{ik}(\lambda b_{kj})=\lambda\sum_ka_{ik}b_{kj}$.

For an $m\times n$ matrix $\mathbf A$, the unit matrices of orders $m$ and $n$ leave it unchanged:

$$
(\mathbf I_m\mathbf A)_{ij}=\sum_{k=1}^{m}\delta_{ik}a_{kj}=a_{ij},
$$

because only the $k=i$ term survives. Similarly $\mathbf A\mathbf I_n=\mathbf A$. So $\mathbf I_m\mathbf A=\mathbf A\mathbf I_n=\mathbf A$.

### The transpose of a product

Let $\mathbf A$ be $m\times p$ and $\mathbf B$ be $p\times n$. Then $(\mathbf{AB})^{\mathrm T}$ is $n\times m$, and its element $(i,j)$ is

$$
\begin{aligned}
[(\mathbf{AB})^{\mathrm T}]_{ij}&=(\mathbf{AB})_{ji}\\
&=\sum_{k=1}^{p}a_{jk}b_{ki}\\
&=\sum_{k=1}^{p}b_{ki}a_{jk}\\
&=\sum_{k=1}^{p}(\mathbf B^{\mathrm T})_{ik}(\mathbf A^{\mathrm T})_{kj}\\
&=(\mathbf B^{\mathrm T}\mathbf A^{\mathrm T})_{ij}.
\end{aligned}
$$

The third line only reorders two numbers, which is allowed because they are scalars; the fourth reads $b_{ki}$ as element $(i,k)$ of $\mathbf B^{\mathrm T}$ and $a_{jk}$ as element $(k,j)$ of $\mathbf A^{\mathrm T}$. Hence

$$
(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}.
$$

The orders confirm the reversal: $\mathbf B^{\mathrm T}$ is $n\times p$ and $\mathbf A^{\mathrm T}$ is $p\times m$, so $\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$ is $n\times m$, while $\mathbf A^{\mathrm T}\mathbf B^{\mathrm T}$ need not even exist. Applying the rule twice gives $(\mathbf{ABC})^{\mathrm T}=\mathbf C^{\mathrm T}\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$. Combined with $(\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf A$ it handles Specimen Test 16, Q3:

$$
(\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf A,\qquad(\mathbf A^{\mathrm T}\mathbf B)^{\mathrm T}=\mathbf B^{\mathrm T}(\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A .
$$

In Q4, $(\mathbf P+\mathbf Q)\mathbf R=\mathbf{PR}+\mathbf{QR}$ always holds (distributive law), and $\mathbf{PQ}=\mathbf{QP}$ does not hold in general.

> [!warning] No commuting and no cancelling
> Two habits from ordinary algebra fail. First, $(\mathbf A+\mathbf B)^2=\mathbf A^2+\mathbf{AB}+\mathbf{BA}+\mathbf B^2$, which equals $\mathbf A^2+2\mathbf{AB}+\mathbf B^2$ only if $\mathbf A$ and $\mathbf B$ commute. Second, $\mathbf{AC}=\mathbf0$ in Example 5.4(f) with $\mathbf A\neq\mathbf0$ and $\mathbf C\neq\mathbf0$, so $\mathbf{AB}=\mathbf{AD}$ does not imply $\mathbf B=\mathbf D$ (add $\mathbf C$ to $\mathbf B$ and the product is unchanged). Cancelling a matrix factor is only allowed when that matrix has an inverse, which needs $|\mathbf A|\neq0$.

### The transpose of a product and a solution by pre-multiplication (Example 5.6)

Take

$$
\mathbf A=\begin{bmatrix}1&2&2\\0&1&1\\1&0&1\end{bmatrix},\qquad\mathbf B=\begin{bmatrix}1&-2&0\\1&-1&-1\\-1&2&1\end{bmatrix},\qquad\mathbf c=\begin{bmatrix}1\\0\\1\end{bmatrix}.
$$

(a) Row 1 of $\mathbf A$ into the columns of $\mathbf B$ gives $(1+2-2,\ -2-2+4,\ 0-2+2)=(1,0,0)$, and the other rows give $(0,1,0)$ and $(0,0,1)$, so

$$
\mathbf{AB}=\mathbf I_3,\qquad(\mathbf{AB})^{\mathrm T}=\mathbf I_3^{\mathrm T}=\mathbf I_3,\qquad\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}=\mathbf I_3,
$$

which agrees with $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$.

(b) The system $x-2y=1$, $x-y-z=0$, $-x+2y+z=1$ is $\mathbf{BX}=\mathbf c$. Pre-multiply both sides by $\mathbf A$:

$$
\begin{aligned}
\mathbf A(\mathbf{BX})&=\mathbf{Ac}\\
(\mathbf{AB})\mathbf X&=\mathbf{Ac}\\
\mathbf I\mathbf X&=\mathbf{Ac}\\
\mathbf X&=\begin{bmatrix}1&2&2\\0&1&1\\1&0&1\end{bmatrix}\begin{bmatrix}1\\0\\1\end{bmatrix}=\begin{bmatrix}1+0+2\\0+0+1\\1+0+1\end{bmatrix}=\begin{bmatrix}3\\1\\2\end{bmatrix}.
\end{aligned}
$$

So $x=3$, $y=1$, $z=2$. Substituting back: $3-2=1$, $3-1-2=0$, $-3+2+2=1$. The matrix $\mathbf A$ that removes $\mathbf B$ in this way is the inverse $\mathbf B^{-1}$ (here $\mathbf{BA}=\mathbf I$ as well); the systematic method is in [[MATH1054 M17 - Matrices II|M17]].

### The associative and distributive laws checked (Example 5.7)

With

$$
\mathbf A=\begin{bmatrix}1&-1&1\\-2&0&3\\0&1&-2\end{bmatrix},\qquad\mathbf B=\begin{bmatrix}0&0&1\\0&2&3\\1&2&3\end{bmatrix},\qquad\mathbf C=\begin{bmatrix}2&3\\-1&2\\-3&1\end{bmatrix},
$$

the intermediate products are

$$
\mathbf{AB}=\begin{bmatrix}1&0&1\\3&6&7\\-2&-2&-3\end{bmatrix},\qquad\mathbf{BC}=\begin{bmatrix}-3&1\\-11&7\\-9&10\end{bmatrix},\qquad\mathbf{AC}=\begin{bmatrix}0&2\\-13&-3\\5&0\end{bmatrix},
$$

and then

$$
(\mathbf{AB})\mathbf C=\begin{bmatrix}-1&4\\-21&28\\7&-13\end{bmatrix}=\mathbf A(\mathbf{BC}),
$$

$$
(\mathbf A+\mathbf B)\mathbf C=\begin{bmatrix}1&-1&2\\-2&2&6\\1&3&1\end{bmatrix}\begin{bmatrix}2&3\\-1&2\\-3&1\end{bmatrix}=\begin{bmatrix}-3&3\\-24&4\\-4&10\end{bmatrix}=\mathbf{AC}+\mathbf{BC}.
$$

## 5. Quadratic forms and the symmetric part

For a square matrix $\mathbf A$ and $\mathbf X=[x_1\ \dots\ x_n]^{\mathrm T}$, the $1\times1$ product $\mathbf X^{\mathrm T}\mathbf A\mathbf X$ is a **quadratic form**. Writing out the two sums,

$$
\mathbf X^{\mathrm T}\mathbf A\mathbf X=\sum_{i=1}^{n}\sum_{j=1}^{n}a_{ij}x_ix_j,
$$

so the coefficient of $x_i^2$ is $a_{ii}$ and, for $i\neq j$, the coefficient of the cross term $x_ix_j$ is $a_{ij}+a_{ji}$. Only the sum of each mirrored pair matters. The same conclusion follows in matrix form. A $1\times1$ matrix equals its own transpose, so

$$
\begin{aligned}
\mathbf X^{\mathrm T}\mathbf A\mathbf X&=(\mathbf X^{\mathrm T}\mathbf A\mathbf X)^{\mathrm T}\\
&=\mathbf X^{\mathrm T}\mathbf A^{\mathrm T}(\mathbf X^{\mathrm T})^{\mathrm T}\\
&=\mathbf X^{\mathrm T}\mathbf A^{\mathrm T}\mathbf X .
\end{aligned}
$$

Averaging the first and last expressions,

$$
\begin{aligned}
\mathbf X^{\mathrm T}\mathbf A\mathbf X&=\tfrac12\big(\mathbf X^{\mathrm T}\mathbf A\mathbf X+\mathbf X^{\mathrm T}\mathbf A^{\mathrm T}\mathbf X\big)\\
&=\mathbf X^{\mathrm T}\Big[\tfrac12(\mathbf A+\mathbf A^{\mathrm T})\Big]\mathbf X .
\end{aligned}
$$

A quadratic form depends only on the symmetric part of its matrix, so quadratic forms are always written with a symmetric matrix. Stress, inertia and stiffness matrices are symmetric for this reason, and their quadratic forms are energies.

### A quadratic form (Example 5.5)

With $\mathbf A=\begin{bmatrix}1&2&0\\1&1&0\\2&1&1\end{bmatrix}$ and $\mathbf X=[x\ y\ z]^{\mathrm T}$:

(a) $\mathbf X^{\mathrm T}\mathbf X=x^2+y^2+z^2$.

(b) $\mathbf{AX}=\begin{bmatrix}x+2y\\x+y\\2x+y+z\end{bmatrix}$.

(c) The quadratic form is

$$
\begin{aligned}
\mathbf X^{\mathrm T}(\mathbf{AX})&=x(x+2y)+y(x+y)+z(2x+y+z)\\
&=x^2+2xy+xy+y^2+2xz+yz+z^2\\
&=x^2+y^2+z^2+3xy+2xz+yz .
\end{aligned}
$$

The cross-term coefficients are $a_{12}+a_{21}=2+1=3$, $a_{13}+a_{31}=0+2=2$ and $a_{23}+a_{32}=0+1=1$, as the general formula says.

(d) The symmetric part is $\tfrac12(\mathbf A^{\mathrm T}+\mathbf A)=\begin{bmatrix}1&\frac32&1\\\frac32&1&\frac12\\1&\frac12&1\end{bmatrix}$, and

$$
\tfrac12\mathbf X^{\mathrm T}(\mathbf A^{\mathrm T}+\mathbf A)\mathbf X=\begin{bmatrix}x&y&z\end{bmatrix}\begin{bmatrix}x+\frac32y+z\\\frac32x+y+\frac12z\\x+\frac12y+z\end{bmatrix}=x^2+y^2+z^2+3xy+2xz+yz,
$$

the same as (c).

## 6. Rotation matrices (James §5.2 and Example 5.8)

Rotate the axes $Oxy$ anticlockwise through $\theta$ about $O$ to give new axes $Ox'y'$. A point $P$ at distance $r$ from $O$ and at angle $\phi$ to the $x$-axis has

$$
x=r\cos\phi,\qquad y=r\sin\phi .
$$

Its angle to the new $x'$-axis is $\phi-\theta$, so its new coordinates are

$$
\begin{aligned}
x'&=r\cos(\phi-\theta)\\
&=r\cos\phi\cos\theta+r\sin\phi\sin\theta\\
&=x\cos\theta+y\sin\theta,
\end{aligned}
$$

$$
\begin{aligned}
y'&=r\sin(\phi-\theta)\\
&=r\sin\phi\cos\theta-r\cos\phi\sin\theta\\
&=-x\sin\theta+y\cos\theta .
\end{aligned}
$$

In matrix form,

$$
\begin{bmatrix}x'\\y'\end{bmatrix}=\mathbf R\begin{bmatrix}x\\y\end{bmatrix},\qquad\mathbf R=\begin{bmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{bmatrix}.
$$

Read the other way, with the axes held fixed, the same matrix moves every point through $\theta$ clockwise about $O$.

Multiplying $\mathbf R$ by its transpose:

$$
\begin{aligned}
\mathbf R^{\mathrm T}\mathbf R&=\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}\begin{bmatrix}\cos\theta&\sin\theta\\-\sin\theta&\cos\theta\end{bmatrix}\\
&=\begin{bmatrix}\cos^2\theta+\sin^2\theta&\cos\theta\sin\theta-\sin\theta\cos\theta\\\sin\theta\cos\theta-\cos\theta\sin\theta&\sin^2\theta+\cos^2\theta\end{bmatrix}\\
&=\mathbf I .
\end{aligned}
$$

So the transpose undoes the rotation, and lengths are preserved:

$$
\begin{aligned}
|\mathbf X'|^2&=\mathbf X'^{\mathrm T}\mathbf X'\\
&=(\mathbf{RX})^{\mathrm T}(\mathbf{RX})\\
&=\mathbf X^{\mathrm T}\mathbf R^{\mathrm T}\mathbf R\mathbf X\\
&=\mathbf X^{\mathrm T}\mathbf X\\
&=|\mathbf X|^2 .
\end{aligned}
$$

The same steps with two different vectors give $(\mathbf{RX})^{\mathrm T}(\mathbf{RY})=\mathbf X^{\mathrm T}\mathbf Y$, so scalar products, and hence angles, are preserved too. Rotations also compose by matrix multiplication. Element $(1,1)$ of $\mathbf R(\alpha)\mathbf R(\beta)$ is $\cos\alpha\cos\beta-\sin\alpha\sin\beta=\cos(\alpha+\beta)$, element $(1,2)$ is $\cos\alpha\sin\beta+\sin\alpha\cos\beta=\sin(\alpha+\beta)$, element $(2,1)$ is $-\sin\alpha\cos\beta-\cos\alpha\sin\beta=-\sin(\alpha+\beta)$, and element $(2,2)$ is $-\sin\alpha\sin\beta+\cos\alpha\cos\beta=\cos(\alpha+\beta)$, so

$$
\mathbf R(\alpha)\mathbf R(\beta)=\mathbf R(\alpha+\beta).
$$

Rotations about one axis in the plane therefore commute, unlike matrices in general. The three-dimensional version, built from three such rotations about different axes, is the aircraft attitude matrix of [[Euler Angles and Rotation Matrices]], and the order of those rotations does matter.

> [!tip] Two readings of one matrix
> $\mathbf X'=\mathbf R\mathbf X$ can describe one point seen from rotated axes (the derivation above) or a point moved while the axes stay put (Example 5.8). Rotating the axes anticlockwise by $\theta$ looks, from the new axes, exactly like rotating the plane clockwise by $\theta$. Check the direction by mapping $(1,0)$: here it goes to $(\cos\theta,-\sin\theta)$, below the $x$-axis for $0<\theta<\pi$.

### A rotation maps the square onto a square (Example 5.8)

With $\theta=60^\circ$, $\cos\theta=\tfrac12$ and $\sin\theta=\tfrac{\sqrt3}{2}$, so

$$
x'=\tfrac12x+\tfrac{\sqrt3}{2}y,\qquad y'=-\tfrac{\sqrt3}{2}x+\tfrac12y .
$$

The corners of the square map to

| Corner | Exact image | Image (3 d.p.) |
|---|---|---|
| A $(1,1)$ | $\big(\tfrac12+\tfrac{\sqrt3}{2},\ \tfrac12-\tfrac{\sqrt3}{2}\big)$ | $(1.366,\,-0.366)$ |
| B $(1,2)$ | $\big(\tfrac12+\sqrt3,\ 1-\tfrac{\sqrt3}{2}\big)$ | $(2.232,\,0.134)$ |
| C $(2,2)$ | $\big(1+\sqrt3,\ 1-\sqrt3\big)$ | $(2.732,\,-0.732)$ |
| D $(2,1)$ | $\big(1+\tfrac{\sqrt3}{2},\ \tfrac12-\sqrt3\big)$ | $(1.866,\,-1.232)$ |

The image edges from A' are $\overrightarrow{A'B'}=(0.866,\,0.500)$ and $\overrightarrow{A'D'}=(0.500,\,-0.866)$. Both have length $\sqrt{0.75+0.25}=1$ and their scalar product is $0.433-0.433=0$, so the image is again a unit square, turned $60^\circ$ clockwise about the origin.

![[m1054_m16_rotation_square.png|620]]

## 7. The determinant of a 2 by 2 and a 3 by 3 matrix

### The 2 by 2 determinant from two equations

Solve the general pair

$$
\begin{aligned}
a_{11}x+a_{12}y&=b_1 \qquad(1)\\
a_{21}x+a_{22}y&=b_2 \qquad(2)
\end{aligned}
$$

by elimination. Multiply (1) by $a_{22}$ and (2) by $a_{12}$:

$$
\begin{aligned}
a_{11}a_{22}x+a_{12}a_{22}y&=a_{22}b_1\\
a_{12}a_{21}x+a_{12}a_{22}y&=a_{12}b_2
\end{aligned}
$$

Subtract to remove $y$:

$$
(a_{11}a_{22}-a_{12}a_{21})\,x=a_{22}b_1-a_{12}b_2 .
$$

Multiplying (2) by $a_{11}$ and (1) by $a_{21}$ and subtracting removes $x$ in the same way:

$$
(a_{11}a_{22}-a_{12}a_{21})\,y=a_{11}b_2-a_{21}b_1 .
$$

Both unknowns are found by dividing by the same number, so the system has a unique solution exactly when that number is non-zero. It is the **determinant** of the coefficient matrix:

$$
|\mathbf A|=\det\mathbf A=\begin{vmatrix}a_{11}&a_{12}\\a_{21}&a_{22}\end{vmatrix}=a_{11}a_{22}-a_{12}a_{21}.
$$

The determinant is defined only for a square matrix. A $1\times1$ matrix $[a]$ has $|\mathbf A|=a$, which can be negative; the bars here do not mean the modulus. Exercise 35(a): $\begin{vmatrix}1&7\\4&9\end{vmatrix}=(1)(9)-(7)(4)=9-28=-19$.

### The determinant as an area scale factor

Write $\mathbf A=\begin{bmatrix}a&b\\c&d\end{bmatrix}$. The unit vectors $\mathbf i=(1,0)$ and $\mathbf j=(0,1)$ map to the columns, $\mathbf A\mathbf i=(a,c)$ and $\mathbf A\mathbf j=(b,d)$, so the unit square maps to the parallelogram on those two edges. Treat the edges as three-dimensional vectors with zero $z$-component and use the cross product from [[Vector (Cross) Product|M15]]:

$$
\begin{aligned}
(a\mathbf i+c\mathbf j)\times(b\mathbf i+d\mathbf j)&=ad\,(\mathbf i\times\mathbf j)+cb\,(\mathbf j\times\mathbf i)\\
&=ad\,\mathbf k-cb\,\mathbf k\\
&=(ad-bc)\,\mathbf k .
\end{aligned}
$$

The parallelogram's area is the magnitude, $|ad-bc|$. Every small square in the plane is scaled in the same way, so the map multiplies every area by $|\det\mathbf A|$. The sign carries orientation: if $\det\mathbf A>0$ the turn from $\mathbf A\mathbf i$ to $\mathbf A\mathbf j$ is anticlockwise like the turn from $\mathbf i$ to $\mathbf j$, and if $\det\mathbf A<0$ the plane has been reflected. When $\det\mathbf A=0$ the two columns are parallel and the square collapses onto a line, which is the geometric reason the equations above then have no unique solution. The rotation matrix of Section 6 has $\det\mathbf R=\cos^2\theta+\sin^2\theta=1$, so it preserves area as well as length.

![[m1054_m16_det_area.png|900]]

### The 3 by 3 determinant from three equations

For a $3\times3$ matrix with rows $\mathbf r_1$, $\mathbf r_2$, $\mathbf r_3$, the homogeneous system $\mathbf{AX}=\mathbf0$ says $\mathbf r_1\cdot\mathbf X=\mathbf r_2\cdot\mathbf X=\mathbf r_3\cdot\mathbf X=0$. Suppose $\mathbf r_2$ and $\mathbf r_3$ are not parallel. A vector perpendicular to both is a multiple of their cross product,

$$
\mathbf X=t\,(\mathbf r_2\times\mathbf r_3),
$$

and the first equation then requires

$$
t\,\mathbf r_1\cdot(\mathbf r_2\times\mathbf r_3)=0 .
$$

A non-zero solution ($t\neq0$) exists exactly when $\mathbf r_1\cdot(\mathbf r_2\times\mathbf r_3)=0$; otherwise only $\mathbf X=\mathbf0$ works and the system $\mathbf{AX}=\mathbf b$ has a unique solution for every $\mathbf b$. So the scalar triple product of the rows plays the role $ad-bc$ played for two equations. Expand it with the component form of the cross product:

$$
\mathbf r_2\times\mathbf r_3=\big(a_{22}a_{33}-a_{23}a_{32},\ \ a_{23}a_{31}-a_{21}a_{33},\ \ a_{21}a_{32}-a_{22}a_{31}\big),
$$

$$
\begin{aligned}
\mathbf r_1\cdot(\mathbf r_2\times\mathbf r_3)&=a_{11}(a_{22}a_{33}-a_{23}a_{32})+a_{12}(a_{23}a_{31}-a_{21}a_{33})+a_{13}(a_{21}a_{32}-a_{22}a_{31})\\
&=a_{11}(a_{22}a_{33}-a_{23}a_{32})-a_{12}(a_{21}a_{33}-a_{23}a_{31})+a_{13}(a_{21}a_{32}-a_{22}a_{31})\\
&=a_{11}\begin{vmatrix}a_{22}&a_{23}\\a_{32}&a_{33}\end{vmatrix}-a_{12}\begin{vmatrix}a_{21}&a_{23}\\a_{31}&a_{33}\end{vmatrix}+a_{13}\begin{vmatrix}a_{21}&a_{22}\\a_{31}&a_{32}\end{vmatrix}.
\end{aligned}
$$

This defines the $3\times3$ determinant (James equation 5.8), called the **expansion along the first row**:

$$
|\mathbf A|=\begin{vmatrix}a_{11}&a_{12}&a_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{vmatrix}=a_{11}\begin{vmatrix}a_{22}&a_{23}\\a_{32}&a_{33}\end{vmatrix}-a_{12}\begin{vmatrix}a_{21}&a_{23}\\a_{31}&a_{33}\end{vmatrix}+a_{13}\begin{vmatrix}a_{21}&a_{22}\\a_{31}&a_{32}\end{vmatrix}.
$$

Each $2\times2$ determinant is what remains of $\mathbf A$ after deleting the row and column through the element in front of it. Multiplied out, it has six terms:

$$
|\mathbf A|=a_{11}a_{22}a_{33}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33}+a_{12}a_{23}a_{31}+a_{13}a_{21}a_{32}-a_{13}a_{22}a_{31}.
$$

Since $|\mathbf A|=\mathbf r_1\cdot(\mathbf r_2\times\mathbf r_3)$, it is the signed volume of the parallelepiped on the three rows ([[Scalar Triple Product]]), and the same argument as for areas makes $|\det\mathbf A|$ the factor by which the map scales volumes. The cross product itself is evaluated as a determinant with $\mathbf i,\mathbf j,\mathbf k$ in the first row, which is this first-row expansion with vectors in place of numbers.

### Expansion along the first row (Example 5.14)

$$
\begin{aligned}
\begin{vmatrix}1&2&4\\-1&0&3\\3&1&-2\end{vmatrix}&=1\begin{vmatrix}0&3\\1&-2\end{vmatrix}-2\begin{vmatrix}-1&3\\3&-2\end{vmatrix}+4\begin{vmatrix}-1&0\\3&1\end{vmatrix}\\
&=1\big[(0)(-2)-(3)(1)\big]-2\big[(-1)(-2)-(3)(3)\big]+4\big[(-1)(1)-(0)(3)\big]\\
&=1(-3)-2(-7)+4(-1)\\
&=-3+14-4\\
&=7 .
\end{aligned}
$$

### Exercise 35(b)

$$
\begin{aligned}
\begin{vmatrix}1&4&3\\2&-4&1\\3&2&-6\end{vmatrix}&=1\big[(-4)(-6)-(1)(2)\big]-4\big[(2)(-6)-(1)(3)\big]+3\big[(2)(2)-(-4)(3)\big]\\
&=1(22)-4(-15)+3(16)\\
&=22+60+48\\
&=130 .
\end{aligned}
$$

## 8. Minors, cofactors and expansion along any row or column

Deleting row $i$ and column $j$ of an $n\times n$ matrix leaves an $(n-1)\times(n-1)$ determinant called the **minor** $M_{ij}$ of the element $a_{ij}$. The minor with its place sign attached is the **cofactor**

$$
A_{ij}=(-1)^{i+j}M_{ij}.
$$

The sign $(-1)^{i+j}$ is $+$ when $i+j$ is even, which gives a chessboard pattern starting with $+$ in the top-left corner:

$$
\begin{bmatrix}+&-&+&\cdots\\-&+&-&\cdots\\+&-&+&\cdots\\\vdots&\vdots&\vdots&\ddots\end{bmatrix}
$$

In this notation the first-row expansion of Section 7 is $|\mathbf A|=a_{11}A_{11}+a_{12}A_{12}+a_{13}A_{13}$. The general rule (James equation 5.9) is that **any** row or column may be used:

$$
|\mathbf A|=\sum_{j=1}^{n}a_{ij}A_{ij}\quad\text{(along row }i\text{)},\qquad|\mathbf A|=\sum_{i=1}^{n}a_{ij}A_{ij}\quad\text{(along column }j\text{)}.
$$

For $n\times n$ matrices this is the recursive definition of the determinant together with a theorem that every row and column give the same value; the general proof is long. For $3\times3$ it can be checked directly against the six-term formula. Along column 1:

$$
\begin{aligned}
a_{11}A_{11}+a_{21}A_{21}+a_{31}A_{31}&=a_{11}(a_{22}a_{33}-a_{23}a_{32})-a_{21}(a_{12}a_{33}-a_{13}a_{32})+a_{31}(a_{12}a_{23}-a_{13}a_{22})\\
&=a_{11}a_{22}a_{33}-a_{11}a_{23}a_{32}-a_{12}a_{21}a_{33}+a_{13}a_{21}a_{32}+a_{12}a_{23}a_{31}-a_{13}a_{22}a_{31},
\end{aligned}
$$

which is the same six terms in a different order. Along row 2:

$$
\begin{aligned}
a_{21}A_{21}+a_{22}A_{22}+a_{23}A_{23}&=-a_{21}(a_{12}a_{33}-a_{13}a_{32})+a_{22}(a_{11}a_{33}-a_{13}a_{31})-a_{23}(a_{11}a_{32}-a_{12}a_{31})\\
&=-a_{12}a_{21}a_{33}+a_{13}a_{21}a_{32}+a_{11}a_{22}a_{33}-a_{13}a_{22}a_{31}-a_{11}a_{23}a_{32}+a_{12}a_{23}a_{31},
\end{aligned}
$$

again the same six terms. The remaining rows and columns check in the same way. A $3\times3$ matrix can therefore be expanded in six ways, and the row or column with the most zeros needs the least work.

### Minors and cofactors of the first row (Example 5.15)

For $|\mathbf A|=\begin{vmatrix}3&4&5\\6&-4&2\\2&-1&1\end{vmatrix}$:

$$
\begin{aligned}
M_{11}&=\begin{vmatrix}-4&2\\-1&1\end{vmatrix}=(-4)(1)-(2)(-1)=-2, & A_{11}&=(-1)^{2}M_{11}=-2,\\
M_{12}&=\begin{vmatrix}6&2\\2&1\end{vmatrix}=6-4=2, & A_{12}&=(-1)^{3}M_{12}=-2,\\
M_{13}&=\begin{vmatrix}6&-4\\2&-1\end{vmatrix}=-6+8=2, & A_{13}&=(-1)^{4}M_{13}=2.
\end{aligned}
$$

$$
|\mathbf A|=3(-2)+4(-2)+5(2)=-6-8+10=-4 .
$$

### Exercise 34, all minors and cofactors

For $\begin{vmatrix}1&2&3\\1&0&1\\1&1&1\end{vmatrix}$ the nine minors and cofactors are

$$
[M_{ij}]=\begin{bmatrix}-1&0&1\\-1&-2&-1\\2&-2&-2\end{bmatrix},\qquad[A_{ij}]=\begin{bmatrix}-1&0&1\\1&-2&1\\2&2&-2\end{bmatrix},
$$

where the cofactors flip the sign of the minors in the $-$ places $(1,2),(2,1),(2,3),(3,2)$. Expanding along row 1 gives $1(-1)+2(0)+3(1)=2$; along column 2 it gives $2(0)+0(-2)+1(2)=2$, the same value.

### Exercise A, Exercise 35(c) expanded along the third row

For $\begin{bmatrix}2&-1&3\\4&2&9\\1&3&-4\end{bmatrix}$, row 3 is $(1,3,-4)$ with place signs $(+,-,+)$:

$$
\begin{aligned}
A_{31}&=+\begin{vmatrix}-1&3\\2&9\end{vmatrix}=-9-6=-15,\\
A_{32}&=-\begin{vmatrix}2&3\\4&9\end{vmatrix}=-(18-12)=-6,\\
A_{33}&=+\begin{vmatrix}2&-1\\4&2\end{vmatrix}=4+4=8,
\end{aligned}
$$

$$
|\mathbf A|=1(-15)+3(-6)+(-4)(8)=-15-18-32=-65 .
$$

### Specimen Test 16, Q5 and Q6

For $\begin{vmatrix}5&2&-7\\6&11&4\\3&8&1\end{vmatrix}$, the minor of the element in row 1, column 3 is $M_{13}=\begin{vmatrix}6&11\\3&8\end{vmatrix}=48-33=15$, and the cofactor of the element in row 2, column 2 is $A_{22}=+\begin{vmatrix}5&-7\\3&1\end{vmatrix}=5+21=26$. Expanding along column 3 needs $A_{13}=+15$, $A_{23}=-\begin{vmatrix}5&2\\3&8\end{vmatrix}=-34$ and $A_{33}=+\begin{vmatrix}5&2\\6&11\end{vmatrix}=43$:

$$
|\cdot|=(-7)(15)+(4)(-34)+(1)(43)=-105-136+43=-198 .
$$

## 9. Properties of determinants and row operations

Each property below follows from expanding along a suitable row, which Section 8 allows. Every statement about rows holds for columns too, by property (f).

Property (b): multiplying one row by $\lambda$ multiplies the determinant by $\lambda$. Expand along that row $i$. Its cofactors $A_{ij}$ do not involve row $i$, so they are unchanged:

$$
\sum_j(\lambda a_{ij})A_{ij}=\lambda\sum_ja_{ij}A_{ij}=\lambda|\mathbf A| .
$$

Property (c): interchanging two rows changes the sign. For $2\times2$, $\begin{vmatrix}c&d\\a&b\end{vmatrix}=cb-da=-(ad-bc)$. For $3\times3$, let $\mathbf B$ be $\mathbf A$ with rows 1 and 2 swapped and expand $|\mathbf B|$ along its row 2, which holds $a_{11},a_{12},a_{13}$. Deleting row 2 of $\mathbf B$ leaves rows 2 and 3 of $\mathbf A$ in their original order, so the minors are $M_{11},M_{12},M_{13}$ of $\mathbf A$, but the place signs in row 2 are $(-,+,-)$:

$$
\begin{aligned}
|\mathbf B|&=-a_{11}M_{11}+a_{12}M_{12}-a_{13}M_{13}\\
&=-\big(a_{11}M_{11}-a_{12}M_{12}+a_{13}M_{13}\big)\\
&=-|\mathbf A| .
\end{aligned}
$$

The same argument works for any two adjacent rows, and swapping rows 1 and 3 takes three adjacent swaps, so it also changes the sign.

Property (a): two equal rows give zero. Swapping the two equal rows leaves the matrix unchanged but, by (c), changes the sign: $D=-D$, so $D=0$. With (b), two proportional rows also give zero, because the factor can be taken out to leave two equal rows.

Property (d), the addition rule: if one row is a sum, the determinant splits. Expanding along row 1,

$$
\begin{aligned}
\begin{vmatrix}a_{11}+b_{11}&a_{12}+b_{12}&a_{13}+b_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{vmatrix}&=(a_{11}+b_{11})A_{11}+(a_{12}+b_{12})A_{12}+(a_{13}+b_{13})A_{13}\\
&=(a_{11}A_{11}+a_{12}A_{12}+a_{13}A_{13})+(b_{11}A_{11}+b_{12}A_{12}+b_{13}A_{13})\\
&=\begin{vmatrix}a_{11}&a_{12}&a_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{vmatrix}+\begin{vmatrix}b_{11}&b_{12}&b_{13}\\a_{21}&a_{22}&a_{23}\\a_{31}&a_{32}&a_{33}\end{vmatrix}.
\end{aligned}
$$

Property (e): adding a multiple of one row to another changes nothing. Replace row 1 by $\mathbf r_1+\lambda\mathbf r_2$. By (d), then (b), then (a):

$$
\begin{aligned}
\begin{vmatrix}\mathbf r_1+\lambda\mathbf r_2\\\mathbf r_2\\\mathbf r_3\end{vmatrix}&=\begin{vmatrix}\mathbf r_1\\\mathbf r_2\\\mathbf r_3\end{vmatrix}+\begin{vmatrix}\lambda\mathbf r_2\\\mathbf r_2\\\mathbf r_3\end{vmatrix}\\
&=|\mathbf A|+\lambda\begin{vmatrix}\mathbf r_2\\\mathbf r_2\\\mathbf r_3\end{vmatrix}\\
&=|\mathbf A|+\lambda\cdot0\\
&=|\mathbf A| .
\end{aligned}
$$

This is the operation that makes determinants practical: it creates zeros at no cost.

Property (f): transposing changes nothing, $|\mathbf A^{\mathrm T}|=|\mathbf A|$. Expanding $\mathbf A^{\mathrm T}$ along its first row is expanding $\mathbf A$ along its first column, which gives the same six terms (Section 8).

For a triangular matrix the determinant is the product of the diagonal. For an upper triangular $\mathbf U$, expand along column 1, where only $u_{11}$ is non-zero; the minor is again upper triangular, so repeat:

$$
|\mathbf U|=u_{11}\begin{vmatrix}u_{22}&\cdots&u_{2n}\\&\ddots&\vdots\\0&&u_{nn}\end{vmatrix}=u_{11}u_{22}\begin{vmatrix}u_{33}&\cdots\\&\ddots\end{vmatrix}=\dots=u_{11}u_{22}\cdots u_{nn}.
$$

By (f) the same holds for a lower triangular matrix, and a diagonal matrix is both, so $|\mathbf I|=1$.

Property (g), the product rule $|\mathbf{AB}|=|\mathbf A||\mathbf B|$. For $2\times2$ matrices, multiply out both sides. The right-hand side is

$$
\begin{aligned}
|\mathbf A||\mathbf B|&=(a_{11}a_{22}-a_{12}a_{21})(b_{11}b_{22}-b_{12}b_{21})\\
&=a_{11}a_{22}b_{11}b_{22}-a_{11}a_{22}b_{12}b_{21}-a_{12}a_{21}b_{11}b_{22}+a_{12}a_{21}b_{12}b_{21}.
\end{aligned}
$$

The left-hand side is

$$
\begin{aligned}
|\mathbf{AB}|&=\begin{vmatrix}a_{11}b_{11}+a_{12}b_{21}&a_{11}b_{12}+a_{12}b_{22}\\a_{21}b_{11}+a_{22}b_{21}&a_{21}b_{12}+a_{22}b_{22}\end{vmatrix}\\
&=(a_{11}b_{11}+a_{12}b_{21})(a_{21}b_{12}+a_{22}b_{22})-(a_{11}b_{12}+a_{12}b_{22})(a_{21}b_{11}+a_{22}b_{21})\\
&=\big(a_{11}a_{21}b_{11}b_{12}+a_{11}a_{22}b_{11}b_{22}+a_{12}a_{21}b_{12}b_{21}+a_{12}a_{22}b_{21}b_{22}\big)\\
&\quad-\big(a_{11}a_{21}b_{11}b_{12}+a_{11}a_{22}b_{12}b_{21}+a_{12}a_{21}b_{11}b_{22}+a_{12}a_{22}b_{21}b_{22}\big)\\
&=a_{11}a_{22}b_{11}b_{22}+a_{12}a_{21}b_{12}b_{21}-a_{11}a_{22}b_{12}b_{21}-a_{12}a_{21}b_{11}b_{22},
\end{aligned}
$$

where the terms in $a_{11}a_{21}b_{11}b_{12}$ and $a_{12}a_{22}b_{21}b_{22}$ cancel. The four surviving terms match. For larger matrices the result is hard to prove by algebra, but the geometry explains it: $\mathbf{AB}$ applies $\mathbf B$ and then $\mathbf A$, which scales volumes by $|\mathbf B|$ and then by $|\mathbf A|$.

The row operations used in practice are summarised here.

| Operation | Effect on the determinant |
|---|---|
| swap two rows (or columns) | changes sign |
| multiply one row (or column) by $k$ | multiplies by $k$ |
| add a multiple of one row (or column) to another | no change |
| transpose | no change |
| two equal or proportional rows (or columns) | determinant is 0 |
| triangular matrix | product of the diagonal |
| product $\mathbf{AB}$ | $\lvert\mathbf{AB}\rvert=\lvert\mathbf A\rvert\lvert\mathbf B\rvert$ |

> [!warning] Scaling a whole matrix, and adding matrices
> Property (b) scales one row. Multiplying the whole $n\times n$ matrix by $\lambda$ scales all $n$ rows, so $|\lambda\mathbf A|=\lambda^n|\mathbf A|$, not $\lambda|\mathbf A|$; for the $3\times3$ matrix of Example 5.21, $|2\mathbf A|=8\times4=32$. There is also no sum rule: in general $|\mathbf A+\mathbf B|\neq|\mathbf A|+|\mathbf B|$, since (d) splits only one row at a time.

A square matrix is **singular** if $|\mathbf A|=0$ and **non-singular** if $|\mathbf A|\neq0$. A determinant is zero exactly when the rows are linearly dependent, that is when one row is a combination of the others, which by (e) can then be reduced to a row of zeros.

Expanding an $n\times n$ determinant directly by cofactors produces $n!$ products, each needing $n-1$ multiplications: for $n=10$ that is $10!\times9=32\,659\,200$ multiplications. Large determinants are therefore reduced with row operations first, and computers use elimination rather than cofactors. The method by hand is:

1. Use (e) to create zeros in one row or column, keeping a whole-number pivot if possible.
2. Record any swaps (sign change) and any factors taken out of a row (multiply back at the end).
3. Expand along the row or column that is now mostly zeros.
4. Repeat on the smaller determinant, or stop once it is triangular.

### Properties checked on 3 by 3 determinants (Example 5.16)

| | Determinant | Relation to (a) | Value |
|---|---|---|---|
| (a) | $\begin{vmatrix}1&0&1\\0&1&2\\1&1&0\end{vmatrix}$ | expand along row 1: $1(0-2)-0+1(0-1)$ | $-3$ |
| (b) | $\begin{vmatrix}1&0&1\\1&1&0\\0&1&2\end{vmatrix}$ | rows 2 and 3 of (a) swapped | $+3$ |
| (c) | $\begin{vmatrix}1&1&0\\0&1&1\\1&0&2\end{vmatrix}$ | transpose of (b) | $+3$ |
| (d) | $\begin{vmatrix}1&0&1\\0&2&4\\3&3&0\end{vmatrix}$ | row 2 of (a) $\times2$, row 3 $\times3$ | $2\times3\times(-3)=-18$ |

Each value can be confirmed by direct expansion; for instance (b) along column 1 is $1(2-0)-1(0-1)+0=3$.

### The product rule with a singular matrix (Example 5.17)

Take $\mathbf A=\begin{bmatrix}1&2&3\\2&3&4\\4&5&6\end{bmatrix}$ and $\mathbf B=\begin{bmatrix}1&0&1\\1&1&1\\1&2&3\end{bmatrix}$.

(a) Expanding along row 1, $|\mathbf A|=1(18-20)-2(12-16)+3(10-12)=-2+8-6=0$. Row operations show why: $R_3\to R_3-R_2$ gives $(2,2,2)$ and then $R_2\to R_2-R_1$ gives $(1,1,1)$, so two rows are proportional. The rows of $\mathbf A$ are linearly dependent, $\mathrm R_3-\mathrm R_2=2(\mathrm R_2-\mathrm R_1)$.

(b) Subtract column 1 from column 3, then use the triangular rule:

$$
|\mathbf B|=\begin{vmatrix}1&0&0\\1&1&0\\1&2&2\end{vmatrix}=1\times1\times2=2 .
$$

(c) $\mathbf{AB}=\begin{bmatrix}6&8&12\\9&11&17\\15&17&27\end{bmatrix}$, and

$$
\begin{aligned}
|\mathbf{AB}|&=6\big[(11)(27)-(17)(17)\big]-8\big[(9)(27)-(17)(15)\big]+12\big[(9)(17)-(11)(15)\big]\\
&=6(8)-8(-12)+12(-12)\\
&=48+96-144\\
&=0,
\end{aligned}
$$

which agrees with $|\mathbf A||\mathbf B|=0\times2$.

### A 4 by 4 determinant by row operations (Example 5.18)

Subtract row 1 from each of rows 2, 3 and 4, which by (e) leaves the value unchanged, then use the triangular rule:

$$
D=\begin{vmatrix}1&1&1&1\\1&1+a&1&1\\1&1&1+b&1\\1&1&1&1+c\end{vmatrix}=\begin{vmatrix}1&1&1&1\\0&a&0&0\\0&0&b&0\\0&0&0&c\end{vmatrix}=1\cdot a\cdot b\cdot c=abc .
$$

### Exercise 45(b), a 4 by 4 determinant with repeated structure

The matrix $\begin{bmatrix}5&4&1&1\\4&5&1&1\\1&1&4&2\\1&1&2&4\end{bmatrix}$ has its first two columns nearly equal and its last two columns nearly equal. Apply $C_1\to C_1-C_2$ and $C_3\to C_3-C_4$:

$$
\begin{vmatrix}1&4&0&1\\-1&5&0&1\\0&1&2&2\\0&1&-2&4\end{vmatrix}.
$$

Then apply $R_2\to R_2+R_1$ and $R_4\to R_4+R_3$, and expand along column 1, which now holds a single 1:

$$
\begin{aligned}
\begin{vmatrix}1&4&0&1\\0&9&0&2\\0&1&2&2\\0&2&0&6\end{vmatrix}&=1\cdot\begin{vmatrix}9&0&2\\1&2&2\\2&0&6\end{vmatrix}\\
&=9(12-0)-0+2(0-4)\\
&=108-8\\
&=100 .
\end{aligned}
$$

> [!check] Exercise 45(b) by eigenvalues
> The determinant of a matrix is the product of its eigenvalues ([[MATH1054 M18 - Matrices III|M18]]). Here $(1,-1,0,0)$ and $(0,0,1,-1)$ are eigenvectors with eigenvalues 1 and 2, and on vectors of the form $(a,a,b,b)$ the matrix acts as $\begin{bmatrix}9&2\\2&6\end{bmatrix}$, whose eigenvalues are 5 and 10. The product is $1\times2\times5\times10=100$.

## 10. The adjoint matrix and the adjoint theorem

The **adjoint** (also called the adjugate) of a square matrix is the transpose of its matrix of cofactors:

$$
\operatorname{adj}\mathbf A=[A_{ij}]^{\mathrm T}=\begin{bmatrix}A_{11}&A_{21}&A_{31}\\A_{12}&A_{22}&A_{32}\\A_{13}&A_{23}&A_{33}\end{bmatrix},\qquad(\operatorname{adj}\mathbf A)_{kj}=A_{jk}.
$$

For a $2\times2$ matrix the cofactors are $A_{11}=d$, $A_{12}=-c$, $A_{21}=-b$, $A_{22}=a$, so transposing gives

$$
\operatorname{adj}\begin{bmatrix}a&b\\c&d\end{bmatrix}=\begin{bmatrix}d&-b\\-c&a\end{bmatrix}:
$$

swap the diagonal elements and change the sign of the other two.

### Alien cofactors give zero

Multiplying a row of $\mathbf A$ by the cofactors of a **different** row ("alien" cofactors) always gives zero. Take rows $i\neq j$ and form $\sum_ka_{ik}A_{jk}$. Let $\mathbf B$ be $\mathbf A$ with row $j$ replaced by a copy of row $i$. The cofactors of row $j$ do not involve row $j$, so $\mathbf B$ and $\mathbf A$ have the same row-$j$ cofactors, $B_{jk}=A_{jk}$. Expand $|\mathbf B|$ along row $j$:

$$
\begin{aligned}
|\mathbf B|&=\sum_kb_{jk}B_{jk}\\
&=\sum_ka_{ik}A_{jk}.
\end{aligned}
$$

But $\mathbf B$ has two equal rows (rows $i$ and $j$), so $|\mathbf B|=0$ by property (a). Together with the expansion along row $i$ itself,

$$
\sum_{k=1}^{n}a_{ik}A_{jk}=\begin{cases}|\mathbf A|,&i=j,\\0,&i\neq j.\end{cases}
$$

The column version, $\sum_ka_{ki}A_{kj}=|\mathbf A|$ if $i=j$ and $0$ otherwise, follows in the same way by replacing a column. For $\mathbf A=\begin{bmatrix}1&2&3\\6&5&4\\7&8&1\end{bmatrix}$ (James Example 5.19) the cofactor matrix is $\begin{bmatrix}-27&22&13\\22&-20&6\\-7&14&-7\end{bmatrix}$. Row 1 against its own cofactors gives $1(-27)+2(22)+3(13)=56=|\mathbf A|$, while row 2 against the row-1 cofactors gives $6(-27)+5(22)+4(13)=-162+110+52=0$.

### The adjoint theorem

Element $(i,j)$ of $\mathbf A(\operatorname{adj}\mathbf A)$ is row $i$ of $\mathbf A$ times column $j$ of $\operatorname{adj}\mathbf A$, and column $j$ of the adjoint holds the cofactors of row $j$ of $\mathbf A$:

$$
\begin{aligned}
[\mathbf A(\operatorname{adj}\mathbf A)]_{ij}&=\sum_ka_{ik}(\operatorname{adj}\mathbf A)_{kj}\\
&=\sum_ka_{ik}A_{jk}\\
&=|\mathbf A|\,\delta_{ij}.
\end{aligned}
$$

The diagonal elements are expansions along a row and equal $|\mathbf A|$; the off-diagonal elements use alien cofactors and are zero. Hence

$$
\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\,\mathbf I,
$$

and the column version gives $(\operatorname{adj}\mathbf A)\mathbf A=|\mathbf A|\,\mathbf I$ as well. The transpose in the definition is what puts the cofactors of row $j$ into column $j$, where row-by-column multiplication meets them. Taking determinants of both sides of the theorem for an $n\times n$ matrix gives $|\mathbf A|\,|\operatorname{adj}\mathbf A|=|\mathbf A|^n$, so $|\operatorname{adj}\mathbf A|=|\mathbf A|^{n-1}$ when $|\mathbf A|\neq0$ (Cauchy's theorem).

> [!warning] Transpose the cofactor matrix
> The element in row $i$, column $j$ of $\operatorname{adj}\mathbf A$ is the cofactor $A_{ji}$, not $A_{ij}$. For a symmetric matrix the two agree, which hides the mistake; for any other matrix the check $\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\mathbf I$ fails unless the transpose is taken.

### The adjoint of a 3 by 3 matrix (Example 5.21)

For $\mathbf A=\begin{bmatrix}1&1&2\\2&0&1\\3&1&1\end{bmatrix}$ the cofactors are

$$
\begin{aligned}
A_{11}&=+(0-1)=-1, & A_{12}&=-(2-3)=1, & A_{13}&=+(2-0)=2,\\
A_{21}&=-(1-2)=1, & A_{22}&=+(1-6)=-5, & A_{23}&=-(1-3)=2,\\
A_{31}&=+(1-0)=1, & A_{32}&=-(1-4)=3, & A_{33}&=+(0-2)=-2.
\end{aligned}
$$

Transposing the cofactor matrix,

$$
[A_{ij}]=\begin{bmatrix}-1&1&2\\1&-5&2\\1&3&-2\end{bmatrix},\qquad\operatorname{adj}\mathbf A=\begin{bmatrix}-1&1&1\\1&-5&3\\2&2&-2\end{bmatrix}.
$$

Expanding along row 1, $|\mathbf A|=1(-1)+1(1)+2(2)=4$. Row 1 of $\mathbf A$ times the columns of $\operatorname{adj}\mathbf A$ gives $(-1+1+4,\ 1-5+4,\ 1+3-4)=(4,0,0)$, and the other rows give $(0,4,0)$ and $(0,0,4)$:

$$
\mathbf A(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\mathbf A=\begin{bmatrix}4&0&0\\0&4&0\\0&0&4\end{bmatrix}=4\mathbf I=|\mathbf A|\,\mathbf I .
$$

Cauchy's theorem checks too: $|\operatorname{adj}\mathbf A|=16=4^2$.

### Exercise 39

For $\mathbf A=\begin{bmatrix}2&1&1\\3&2&2\\1&1&2\end{bmatrix}$ the cofactor matrix and adjoint are

$$
[A_{ij}]=\begin{bmatrix}2&-4&1\\-1&3&-1\\0&-1&1\end{bmatrix},\qquad\operatorname{adj}\mathbf A=\begin{bmatrix}2&-1&0\\-4&3&-1\\1&-1&1\end{bmatrix},
$$

and $|\mathbf A|=2(2)+1(-4)+1(1)=1$. So $\mathbf A(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\mathbf A=\mathbf I$: with determinant 1, the adjoint is itself the inverse.

### Specimen Test 16, Q7

For $\mathbf A=\begin{pmatrix}1&2&1\\3&0&-1\\-2&1&1\end{pmatrix}$,

$$
[A_{ij}]=\begin{pmatrix}1&-1&3\\-1&3&-5\\-2&4&-6\end{pmatrix},\qquad\operatorname{adj}\mathbf A=\begin{pmatrix}1&-1&-2\\-1&3&4\\3&-5&-6\end{pmatrix},
$$

with $|\mathbf A|=1(1)+2(-1)+1(3)=2$ and $\mathbf A(\operatorname{adj}\mathbf A)=2\mathbf I$.

### Towards the inverse

If $|\mathbf A|\neq0$, divide the adjoint theorem by $|\mathbf A|$:

$$
\mathbf A\left(\frac{\operatorname{adj}\mathbf A}{|\mathbf A|}\right)=\left(\frac{\operatorname{adj}\mathbf A}{|\mathbf A|}\right)\mathbf A=\mathbf I .
$$

The matrix $\operatorname{adj}\mathbf A/|\mathbf A|$ therefore undoes $\mathbf A$ from either side, as $\mathbf A$ undid $\mathbf B$ in Example 5.6. It is the inverse $\mathbf A^{-1}$, which exists only for a non-singular matrix; its properties, Cramer's rule and Gaussian elimination are in [[MATH1054 M17 - Matrices II|M17]] and [[Matrix Inverse]].

## Terminology and alternative names

| Term here | Also called | Note |
|---|---|---|
| unit matrix $\mathbf I$ | identity matrix | James uses both |
| adjoint $\operatorname{adj}\mathbf A$ | adjugate | in other texts "adjoint" can mean the conjugate transpose, a different matrix |
| leading diagonal | principal or main diagonal | |
| $\lvert\mathbf A\rvert$ | $\det\mathbf A$ | not the modulus, even for a $1\times1$ matrix |
| skew-symmetric | antisymmetric | |
| $\begin{bmatrix}\ \end{bmatrix}$ (James) | $\begin{pmatrix}\ \end{pmatrix}$ (booklet) | either accepted in answers |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M16 Solutions - Matrices I]]
- Previous: [[MATH1054 M15 - Vectors II]] (the cross product as a determinant and the scalar triple product as a $3\times3$ determinant) · Next: [[MATH1054 M17 - Matrices II]] (the inverse, Cramer's rule, Gaussian elimination) · Then: [[MATH1054 M18 - Matrices III]] (rank, eigenvalues from $\lvert\mathbf A-\lambda\mathbf I\rvert=0$)
- Concepts: [[Matrix Algebra]] · [[Determinants and Cofactors]] · [[Matrix Inverse]] · [[Scalar Triple Product]] · [[Vector (Cross) Product]] · [[Gaussian Elimination]] · [[Eigenvalues and Eigenvectors]]
- Year 1 uses: [[Stress Tensor and Stress Element]] (a symmetric $3\times3$ matrix) and [[Stress Transformation Equations]] (rotation of axes) in FEEG1002; [[Mesh Current Method]] in FEEG1004 (a matrix equation for the mesh currents)
- Year 2 uses: [[Jacobian and Volume Elements]] (the determinant as a volume scale factor, MATH2048) · [[Euler Angles and Rotation Matrices]] · [[State-Space Representation]] · [[Characteristic Equation and Eigenvalues]] (SESA2027) · [[Global Stiffness Matrix Assembly]] (SESA2029)

## Sources

- MATH1054 Module Booklet, Module 16 (pp. 1–4 of the module: work scheme sections 1–9 and Specimen Test 16)
- James, *Modern Engineering Mathematics* (6th ed.), §5.1 (pp. 297–298), §5.2 (pp. 298–326: definitions §5.2.1, basic operations §5.2.2, multiplication §5.2.4, properties of multiplication §5.2.6, Examples 5.1, 5.4–5.8), §5.3 (pp. 327–339: determinants, minors and cofactors, properties (a)–(g), the adjoint (5.12)–(5.13), Examples 5.14–5.21, Exercises 34–45)
- Worked solutions: [[MATH1054 M16 Solutions - Matrices I]]

## Self-study tasks

### Core

- [ ] Exercises 12 and 13(a),(b) (Module 16 work scheme, section 5): which products exist, evaluate them, and identify special matrices. → [[MATH1054 M16 Solutions - Matrices I#Exercise 12: Products, and which are special|Exercise 12]] · [[MATH1054 M16 Solutions - Matrices I#Exercise 13: Which products exist?|Exercise 13]]
- [ ] Exercises 35(a),(b) (Module 16 work scheme, section 6): $2\times2$ and $3\times3$ determinants by first-row expansion. → [[MATH1054 M16 Solutions - Matrices I#Exercise 35(a),(b): Determinants|solution]]
- [ ] Exercise 34 and Exercise A (Module 16 work scheme, section 7): all nine minors and cofactors, and Exercise 35(c) expanded along the third row. → [[MATH1054 M16 Solutions - Matrices I#Part B: Assigned exercises|Exercise 34]] · [[MATH1054 M16 Solutions - Matrices I#Booklet Exercise A: Exercise 35(c) expanded along the third row|Exercise A]]
- [ ] Exercise 39 (Module 16 work scheme, section 9): $\operatorname{adj}\mathbf A$ and the check $\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\mathbf I$. → [[MATH1054 M16 Solutions - Matrices I#Part B: Assigned exercises|Exercise 39]]
- [ ] Specimen Test 16, Q1–Q7, timed. → [[MATH1054 M16 Solutions - Matrices I#Part C: Specimen Test 16|solutions]]

### Further practice

- [ ] Exercise 45(b) (Module 16 work scheme, section 9): a $4\times4$ determinant by column then row operations. → [[MATH1054 M16 Solutions - Matrices I#Part B: Assigned exercises|Exercise 45(b)]] · [[#Exercise 45(b), a 4 by 4 determinant with repeated structure]]
- [ ] Examples 5.16, 5.17 and 5.18 (Module 16 work scheme, section 8) without looking: properties of determinants, $|\mathbf{AB}|=|\mathbf A||\mathbf B|$ and a $4\times4$ by row operations. → [[MATH1054 M16 Solutions - Matrices I#Example 5.16: Properties of determinants|Example 5.16]] · [[MATH1054 M16 Solutions - Matrices I#Part A: Worked examples|Examples 5.17, 5.18]]
- [ ] Examples 5.6 and 5.8 (Module 16 work scheme, section 5): the solution by pre-multiplication, and the rotated square. → [[MATH1054 M16 Solutions - Matrices I#Example 5.6: Transpose of a product, and a solution by pre-multiplication|Example 5.6]] · [[MATH1054 M16 Solutions - Matrices I#Example 5.8: A rotation maps the square onto a square|Example 5.8]]
- [ ] Suggested, not set in the work scheme: for James Example 5.19's matrix, verify all six alien-cofactor sums are zero and that $\mathbf A(\operatorname{adj}\mathbf A)=56\,\mathbf I$. → [[#Alien cofactors give zero]]

## Transcript and slide slips

> [!warning] James Example 5.14, MATLAB check
> Where: [[#Expansion along the first row (Example 5.14)]]
> The printed determinant has third row $(3,1,-2)$ and value 7, and the hand working uses that row. The MATLAB line on James p. 332 enters the third row as `3 2 -2`; that matrix has determinant $1(0-6)-2(2-9)+4(-2-0)=0$, so the command as printed does not return 7. Enter `A = [1 2 4; -1 0 3; 3 1 -2]`.
