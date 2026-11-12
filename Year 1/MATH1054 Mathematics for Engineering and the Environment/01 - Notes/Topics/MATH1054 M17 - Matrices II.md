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
status: lectured
coverage: "Module Booklet Module 17 work scheme: the inverse by cofactors and by elimination (booklet section 7), sets of linear equations and their four cases, Cramer's rule, Gaussian elimination with back-substitution, ill-conditioning; James §5.4 (pp. 339–341), §5.5.1 (pp. 345–350), §5.5.2 (pp. 354–356, Examples 5.31, 5.33–5.34, ill-conditioning pp. 366–368)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M16 - Matrices I]]"]
next_topics: ["[[MATH1054 M18 - Matrices III]]"]
key_concepts: ["[[Matrix Inverse]]", "[[Gaussian Elimination]]"]
tutorial_sheets: ["[[MATH1054 M17 Solutions - Matrices II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 17)", "02 - Sources/Modern Engineering Mathematics.pdf (§5.4–5.5)"]
---

# MATH1054 M17 - Matrices II

> [!abstract] Summary
> A square matrix $\mathbf A$ has an inverse $\mathbf A^{-1}$, with $\mathbf A\mathbf A^{-1}=\mathbf A^{-1}\mathbf A=\mathbf I$, exactly when $|\mathbf A|\neq0$, and then $\mathbf A^{-1}=\operatorname{adj}\mathbf A/|\mathbf A|$; the inverse of a product reverses the order, $(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}$. The system $\mathbf{AX}=\mathbf b$ has a unique solution when $|\mathbf A|\neq0$, and when $|\mathbf A|=0$ it has either none or infinitely many; the homogeneous system $\mathbf{AX}=\mathbf0$ has a non-trivial solution if and only if $|\mathbf A|=0$. In practice systems are solved by Gaussian elimination and back-substitution, and inverses by row-reducing $[\mathbf A\,|\,\mathbf I]$ to $[\mathbf I\,|\,\mathbf A^{-1}]$, because both cost far less than determinants.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for an inverse, to solve $n$ linear equations in $n$ unknowns, to classify a system (unique, none, infinitely many), or to find the parameter that gives a homogeneous system a non-trivial solution.
> - **Assumptions:** $\mathbf A$ is square ($n\times n$); the inverse formula needs $|\mathbf A|\neq0$; row operations act on the whole augmented row, right-hand side included.
> - **Method:** 1. Compute $|\mathbf A|$ first; it decides the case. 2. For a $2\times2$ inverse swap the diagonal, negate the off-diagonal, divide by $|\mathbf A|$; for $3\times3$ use cofactors, transpose, divide. 3. To solve, reduce $[\mathbf A\,|\,\mathbf b]$ to upper-triangular form and back-substitute from the last row. 4. A row $0=0$ means a free parameter; a row $0=c\neq0$ means no solution. 5. Substitute the answer into the original equations.
> - **Common mistakes:** forgetting to transpose the cofactor matrix (adj is the transpose); writing $(\mathbf{AB})^{-1}=\mathbf A^{-1}\mathbf B^{-1}$ instead of $\mathbf B^{-1}\mathbf A^{-1}$.
> - **Practise:** [[#Inverse by elimination, a 3 by 3 example]] · [[MATH1054 M17 Solutions - Matrices II#Exercise 63: Invert, then solve the system|Exercise 63]]

The determinant and the adjoint of [[MATH1054 M16 - Matrices I|M16]] exist mainly to solve one problem: $n$ linear equations in $n$ unknowns, written $\mathbf{AX}=\mathbf b$. The inverse matrix plays the role of division. If $\mathbf A^{-1}$ exists, multiplying both sides by it gives $\mathbf X=\mathbf A^{-1}\mathbf b$ at once, and the determinant decides whether it exists.

Engineering systems of equations are usually large: a truss with a hundred joints, a finite-difference grid with thousands of points, a finite-element stiffness model with millions of unknowns. For those, the cofactor formula is hopeless, because a determinant expanded by cofactors costs of order $n!$ operations. Elimination, which subtracts multiples of one equation from another until the system is triangular, costs of order $n^3$ and is what every computer package does underneath. The cofactor formula still matters, as the theory that says when a solution exists and as the fastest route by hand for a $2\times2$ or $3\times3$.

The homogeneous case $\mathbf{AX}=\mathbf0$ leads to eigenvalues. Asking for which $\lambda$ the system $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ has a non-trivial solution is the eigenvalue problem of [[MATH1054 M18 - Matrices III|M18]], and the condition $|\mathbf A-\lambda\mathbf I|=0$ is the non-trivial-solution test of section 3.

---

## 1. The inverse matrix (James §5.4)

### Definition and uniqueness

For a square matrix $\mathbf A$, a matrix $\mathbf B$ with

$$
\mathbf{BA}=\mathbf{AB}=\mathbf I
$$

is called the **inverse** of $\mathbf A$, written $\mathbf A^{-1}$. A matrix with an inverse is **non-singular** (invertible); one without is **singular**.

If an inverse exists it is unique. Suppose $\mathbf B$ and $\mathbf C$ are both inverses of $\mathbf A$. Then $\mathbf{AB}=\mathbf I$ and $\mathbf{CA}=\mathbf I$, and associativity of matrix multiplication gives

$$
\begin{aligned}
\mathbf B&=\mathbf{IB}\\
&=(\mathbf{CA})\mathbf B\\
&=\mathbf C(\mathbf{AB})\\
&=\mathbf{CI}\\
&=\mathbf C .
\end{aligned}
$$

For square matrices, $\mathbf{AB}=\mathbf I$ holds if and only if $\mathbf{BA}=\mathbf I$, so checking one product is enough.

### The cofactor (direct) formula

The adjoint ([[MATH1054 M16 - Matrices I|M16]]), the transpose of the matrix of cofactors $A_{ij}$, satisfies

$$
\mathbf A(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\mathbf A=|\mathbf A|\,\mathbf I ,
$$

because row $i$ of $\mathbf A$ times column $j$ of $\operatorname{adj}\mathbf A$ is the expansion of $|\mathbf A|$ along row $i$ when $i=j$, and an expansion with alien cofactors (zero) when $i\neq j$ (see [[Determinants and Cofactors]]). If $|\mathbf A|\neq0$, divide by the scalar $|\mathbf A|$:

$$
\begin{aligned}
\mathbf A\left(\frac{\operatorname{adj}\mathbf A}{|\mathbf A|}\right)&=\frac{|\mathbf A|\,\mathbf I}{|\mathbf A|}\\
&=\mathbf I ,
\end{aligned}
$$

and the same holds with the factors the other way round. By uniqueness,

$$
\boxed{\mathbf A^{-1}=\frac{1}{|\mathbf A|}\operatorname{adj}\mathbf A=\frac{1}{|\mathbf A|}\big[A_{ij}\big]^{\mathrm T}\qquad(|\mathbf A|\neq0).}
$$

This is the **direct** or **cofactor method**.

Conversely, if $\mathbf A^{-1}$ exists then $|\mathbf A|\neq0$. Take determinants of $\mathbf A\mathbf A^{-1}=\mathbf I$ and use $|\mathbf{AB}|=|\mathbf A||\mathbf B|$ from M16:

$$
\begin{aligned}
|\mathbf A\mathbf A^{-1}|&=|\mathbf I|\\
|\mathbf A|\,|\mathbf A^{-1}|&=1 .
\end{aligned}
$$

A product equal to 1 cannot have a zero factor, so $|\mathbf A|\neq0$, and as a by-product $|\mathbf A^{-1}|=1/|\mathbf A|$. Together the two directions give: $\mathbf A^{-1}$ exists if and only if $|\mathbf A|\neq0$. Typical signs of a singular matrix are a zero row or column, two equal or proportional rows, or one row a combination of the others.

### The 2 by 2 inverse

For $\mathbf A=\begin{bmatrix}a&b\\c&d\end{bmatrix}$ each minor is a single element, so the cofactors are $A_{11}=d$, $A_{12}=-c$, $A_{21}=-b$, $A_{22}=a$. Then

$$
\begin{aligned}
\operatorname{adj}\mathbf A&=\begin{bmatrix}d&-c\\-b&a\end{bmatrix}^{\mathrm T}\\
&=\begin{bmatrix}d&-b\\-c&a\end{bmatrix},
\end{aligned}
$$

and with $|\mathbf A|=ad-bc$,

$$
\boxed{\begin{bmatrix}a&b\\c&d\end{bmatrix}^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}\qquad(ad-bc\neq0):}
$$

swap the diagonal, negate the off-diagonal, divide by the determinant.

### Worked examples: cofactor inverses

**Example 5.22(a).** $\mathbf A=\begin{bmatrix}1&2\\2&3\end{bmatrix}$ has $|\mathbf A|=3-4=-1$, so

$$
\begin{aligned}
\mathbf A^{-1}&=\frac{1}{-1}\begin{bmatrix}3&-2\\-2&1\end{bmatrix}\\
&=\begin{bmatrix}-3&2\\2&-1\end{bmatrix}.
\end{aligned}
$$

**Booklet Exercise A** (and Exercise 51(a)). $\mathbf A=\begin{pmatrix}1&2\\2&1\end{pmatrix}$: the minors are $M_{11}=1$, $M_{12}=2$, $M_{21}=2$, $M_{22}=1$, so the cofactors are $A_{11}=1$, $A_{12}=-2$, $A_{21}=-2$, $A_{22}=1$, and $|\mathbf A|=1-4=-3$. The cofactor matrix is symmetric, so transposing leaves it unchanged:

$$
\begin{aligned}
\mathbf A^{-1}&=\frac{1}{-3}\begin{pmatrix}1&-2\\-2&1\end{pmatrix}\\
&=\begin{pmatrix}-\frac13&\frac23\\[2pt]\frac23&-\frac13\end{pmatrix}.
\end{aligned}
$$

**Specimen Test 17, Q1.** $\begin{pmatrix}1&3\\2&4\end{pmatrix}$ has determinant $4-6=-2$, so its inverse is $-\frac12\begin{pmatrix}4&-3\\-2&1\end{pmatrix}=\begin{pmatrix}-2&\frac32\\1&-\frac12\end{pmatrix}$.

**Example 5.22(b).** $\mathbf B=\begin{bmatrix}5&2&4\\3&-1&2\\1&4&-3\end{bmatrix}$. Expanding along the first row,

$$
\begin{aligned}
|\mathbf B|&=5\begin{vmatrix}-1&2\\4&-3\end{vmatrix}-2\begin{vmatrix}3&2\\1&-3\end{vmatrix}+4\begin{vmatrix}3&-1\\1&4\end{vmatrix}\\
&=5(3-8)-2(-9-2)+4(12+1)\\
&=-25+22+52\\
&=49 .
\end{aligned}
$$

The nine cofactors, row by row, form

$$
\big[B_{ij}\big]=\begin{bmatrix}-5&11&13\\22&-19&-18\\8&2&-11\end{bmatrix},
$$

so

$$
\begin{aligned}
\operatorname{adj}\mathbf B&=\begin{bmatrix}-5&22&8\\11&-19&2\\13&-18&-11\end{bmatrix},\\
\mathbf B^{-1}&=\frac{1}{49}\begin{bmatrix}-5&22&8\\11&-19&2\\13&-18&-11\end{bmatrix}.
\end{aligned}
$$

> [!check] Checking an inverse
> Row 1 of $\mathbf B$ times column 1 of $\operatorname{adj}\mathbf B$ is $5(-5)+2(11)+4(13)=49=|\mathbf B|$, and row 1 times column 2 is $5(22)+2(-19)+4(-18)=0$. One diagonal and one off-diagonal entry of $\mathbf B\operatorname{adj}\mathbf B$ catch almost every slip, including a forgotten transpose.

**Exercise 51** asks which of four matrices are singular. $\begin{bmatrix}1&2&3\\2&2&1\\5&6&5\end{bmatrix}$ has determinant $1(10-6)-2(10-5)+3(12-10)=0$, and indeed row 3 is row 1 plus twice row 2. $\begin{bmatrix}1&0&1\\0&1&0\\1&0&1\end{bmatrix}$ has two equal rows, so its determinant is 0. The upper-triangular $4\times4$ matrix

$$
\begin{bmatrix}1&0&0&1\\0&1&0&1\\0&0&1&1\\0&0&0&1\end{bmatrix}\quad\text{has determinant }1\text{ and inverse}\quad\begin{bmatrix}1&0&0&-1\\0&1&0&-1\\0&0&1&-1\\0&0&0&1\end{bmatrix},
$$

which undoes "add the last coordinate to each of the others". Complex entries change nothing in the method: for $\begin{bmatrix}1&\mathrm j\\-\mathrm j&2\end{bmatrix}$ the determinant is $2-(\mathrm j)(-\mathrm j)=2+\mathrm j^2=1$, so the inverse is $\begin{bmatrix}2&-\mathrm j\\\mathrm j&1\end{bmatrix}$; and $\begin{bmatrix}1&2&3\\0&1&2\\2&3&1\end{bmatrix}$ has determinant $-3$ and inverse $-\frac13\begin{bmatrix}-5&7&1\\4&-5&-2\\-2&1&1\end{bmatrix}$ (Exercise 52(c) and (d)).

## 2. Inverses of products and transposes (James §5.4)

The inverse of a product reverses the order:

$$
(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}\qquad(\mathbf A,\mathbf B\text{ invertible}).
$$

To prove it, multiply the candidate by $\mathbf{AB}$ and use associativity:

$$
\begin{aligned}
(\mathbf B^{-1}\mathbf A^{-1})(\mathbf{AB})&=\mathbf B^{-1}(\mathbf A^{-1}\mathbf A)\mathbf B\\
&=\mathbf B^{-1}\mathbf I\mathbf B\\
&=\mathbf B^{-1}\mathbf B\\
&=\mathbf I ,
\end{aligned}
$$

and by uniqueness the candidate is the inverse. Since matrices do not commute in general, $\mathbf A^{-1}\mathbf B^{-1}$ is usually a different matrix. The same argument extends to longer products, $(\mathbf{ABC})^{-1}=\mathbf C^{-1}\mathbf B^{-1}\mathbf A^{-1}$.

The transpose and the inverse commute. Transposing $\mathbf A\mathbf A^{-1}=\mathbf I$ with $(\mathbf{PQ})^{\mathrm T}=\mathbf Q^{\mathrm T}\mathbf P^{\mathrm T}$ gives

$$
\begin{aligned}
(\mathbf A\mathbf A^{-1})^{\mathrm T}&=\mathbf I^{\mathrm T}\\
(\mathbf A^{-1})^{\mathrm T}\mathbf A^{\mathrm T}&=\mathbf I ,
\end{aligned}
$$

so $(\mathbf A^{\mathrm T})^{-1}=(\mathbf A^{-1})^{\mathrm T}$. Finally $(\mathbf A^{-1})^{-1}=\mathbf A$, because $\mathbf A\mathbf A^{-1}=\mathbf I$ says that $\mathbf A$ is an inverse of $\mathbf A^{-1}$.

**Example 5.23.** Take $\mathbf A=\begin{bmatrix}1&2\\2&1\end{bmatrix}$ and $\mathbf B=\begin{bmatrix}0&1\\1&1\end{bmatrix}$. Then

$$
\mathbf{AB}=\begin{bmatrix}2&3\\1&3\end{bmatrix},\qquad|\mathbf{AB}|=6-3=3,
$$

$$
\begin{aligned}
(\mathbf{AB})^{-1}&=\frac13\begin{bmatrix}3&-3\\-1&2\end{bmatrix}\\
&=\begin{bmatrix}1&-1\\-\frac13&\frac23\end{bmatrix}.
\end{aligned}
$$

Separately, $\mathbf A^{-1}=-\frac13\begin{bmatrix}1&-2\\-2&1\end{bmatrix}$ and $\mathbf B^{-1}=\frac{1}{-1}\begin{bmatrix}1&-1\\-1&0\end{bmatrix}=\begin{bmatrix}-1&1\\1&0\end{bmatrix}$, and

$$
\mathbf B^{-1}\mathbf A^{-1}=\begin{bmatrix}1&-1\\-\frac13&\frac23\end{bmatrix}=(\mathbf{AB})^{-1},\qquad\mathbf A^{-1}\mathbf B^{-1}=\begin{bmatrix}1&-\frac13\\-1&\frac23\end{bmatrix}\neq(\mathbf{AB})^{-1}.
$$

> [!tip] Why the order reverses
> $\mathbf{AB}$ acting on a vector applies $\mathbf B$ first and $\mathbf A$ second. Undoing it must undo the last operation first, so $\mathbf A^{-1}$ acts first and $\mathbf B^{-1}$ second, which in matrix order is $\mathbf B^{-1}\mathbf A^{-1}$: socks then shoes on, shoes then socks off.

## 3. Sets of linear equations and when they have solutions (James §5.5.1)

$n$ linear equations in $n$ unknowns,

$$
\begin{aligned}
a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n&=b_1\\
a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n&=b_2\\
&\;\;\vdots\\
a_{n1}x_1+a_{n2}x_2+\dots+a_{nn}x_n&=b_n ,
\end{aligned}
$$

are written $\mathbf{AX}=\mathbf b$, with $\mathbf A$ the $n\times n$ matrix of coefficients and $\mathbf X$ the column of unknowns. The system is **homogeneous** if $\mathbf b=\mathbf0$ and **inhomogeneous** (or non-homogeneous) if $\mathbf b\neq\mathbf0$. Four cases arise, depending on $\mathbf b$ and $|\mathbf A|$.

Case (a), $\mathbf b\neq\mathbf0$ and $|\mathbf A|\neq0$. The inverse exists, so pre-multiply by it:

$$
\begin{aligned}
\mathbf{AX}&=\mathbf b\\
\mathbf A^{-1}\mathbf{AX}&=\mathbf A^{-1}\mathbf b\\
\mathbf X&=\mathbf A^{-1}\mathbf b .
\end{aligned}
$$

Every solution must equal $\mathbf A^{-1}\mathbf b$, and $\mathbf A^{-1}\mathbf b$ does satisfy the equations, so the solution exists and is **unique**.

Case (b), $\mathbf b=\mathbf0$ and $|\mathbf A|\neq0$. The same steps give $\mathbf X=\mathbf A^{-1}\mathbf0=\mathbf0$: only the **trivial solution**.

Case (c), $\mathbf b\neq\mathbf0$ and $|\mathbf A|=0$. No inverse exists, and there are two possibilities: the equations contradict each other and there is **no solution** (the system is **inconsistent**), or they are **consistent** and there are **infinitely many** solutions. Which one occurs depends on $\mathbf b$, and elimination (section 5) or the rank test of [[MATH1054 M18 - Matrices III|M18]] settles it.

Case (d), $\mathbf b=\mathbf0$ and $|\mathbf A|=0$. A homogeneous system is always consistent, since $\mathbf X=\mathbf0$ works, and with $|\mathbf A|=0$ there are infinitely many **non-trivial** solutions.

| | $\mathbf b\neq\mathbf0$ | $\mathbf b=\mathbf0$ (homogeneous) |
|---|---|---|
| $\lvert\mathbf A\rvert\neq0$ | unique solution $\mathbf X=\mathbf A^{-1}\mathbf b$ | only $\mathbf X=\mathbf0$ |
| $\lvert\mathbf A\rvert=0$ | none (inconsistent) or infinitely many (consistent) | infinitely many non-trivial |

Cases (b) and (d) together give the result used most often:

$$
\boxed{\mathbf{AX}=\mathbf0\text{ has a non-trivial solution if and only if }|\mathbf A|=0.}
$$

Case (b) proves the "only if" half. For the "if" half, reduce $\mathbf A$ to upper-triangular form $\mathbf U$ by row operations (section 5). Each operation multiplies the determinant by a non-zero number (a swap by $-1$, a scaling by $k\neq0$, adding a multiple of a row by 1, all from M16), so $|\mathbf U|=0$ too. The determinant of a triangular matrix is the product of its diagonal entries, so some diagonal entry of $\mathbf U$ is zero. Then at most $n-1$ of the unknowns are fixed by pivots, at least one unknown is free, and setting it to any non-zero value and back-substituting gives a non-trivial solution.

In two unknowns each equation is a line in the $(x,y)$ plane and the cases are visible: two crossing lines (unique), two coincident lines (infinitely many), two parallel distinct lines (none). A zero determinant means the two lines have the same slope.

![[m1054_m17_system_cases.png|900]]

### Worked example: classifying five systems

**Example 5.25** writes five systems in matrix form and classifies them.

| System | $\lvert\mathbf A\rvert$ | $\mathbf b$ | Case and outcome |
|---|---|---|---|
| (a) $2x+y=5$, $x-2y=-5$ | $-4-1=-5$ | $(5,-5)$ | (a): unique, $x=1$, $y=3$ |
| (b) $2x+y=0$, $x-2y=0$ | $-5$ | $\mathbf0$ | (b): only $x=y=0$ |
| (c) $-3x+6y=15$, $x-2y=-5$ | $6-6=0$ | $(15,-5)$ | (c): equation 1 is $-3\times$ equation 2, consistent; infinitely many, $x=2t-5$, $y=t$ |
| (d) $-3x+6y=10$, $x-2y=-5$ | $0$ | $(10,-5)$ | (c): the left side of equation 1 is $-3\times$ equation 2, the right side $10\neq15$; inconsistent, no solution |
| (e) $-3x+6y=0$, $x-2y=0$ | $0$ | $\mathbf0$ | (d): infinitely many non-trivial, $x=2s$, $y=s$ |

### Worked example: solving by the inverse

**Example 5.26.** Solve $x+y+z=6$, $x+2y+3z=14$, $x+4y+9z=36$. Subtract column 1 from columns 2 and 3 (which leaves the determinant unchanged) and expand along row 1:

$$
\begin{aligned}
|\mathbf A|&=\begin{vmatrix}1&1&1\\1&2&3\\1&4&9\end{vmatrix}\\
&=\begin{vmatrix}1&0&0\\1&1&2\\1&3&8\end{vmatrix}\\
&=1(8-6)\\
&=2\neq0 ,
\end{aligned}
$$

so the solution is unique. The cofactors give

$$
\mathbf A^{-1}=\frac12\begin{bmatrix}6&-5&1\\-6&8&-2\\2&-3&1\end{bmatrix},
$$

and

$$
\begin{aligned}
\mathbf X&=\frac12\begin{bmatrix}6&-5&1\\-6&8&-2\\2&-3&1\end{bmatrix}\begin{bmatrix}6\\14\\36\end{bmatrix}\\
&=\frac12\begin{bmatrix}36-70+36\\-36+112-72\\12-42+36\end{bmatrix}\\
&=\frac12\begin{bmatrix}2\\4\\6\end{bmatrix}\\
&=\begin{bmatrix}1\\2\\3\end{bmatrix}.
\end{aligned}
$$

**Exercise 63.** Invert $\mathbf A=\begin{bmatrix}-1&2&1\\0&1&-2\\1&4&-1\end{bmatrix}$ and solve $\mathbf{AX}=(2,-3,4)^{\mathrm T}$. Along row 1,

$$
\begin{aligned}
|\mathbf A|&=-1(-1+8)-2(0+2)+1(0-1)\\
&=-7-4-1\\
&=-12 .
\end{aligned}
$$

The cofactor matrix and its transpose are

$$
\big[A_{ij}\big]=\begin{bmatrix}7&-2&-1\\6&0&6\\-5&-2&-1\end{bmatrix},\qquad\operatorname{adj}\mathbf A=\begin{bmatrix}7&6&-5\\-2&0&-2\\-1&6&-1\end{bmatrix},
$$

so

$$
\mathbf A^{-1}=-\frac{1}{12}\begin{bmatrix}7&6&-5\\-2&0&-2\\-1&6&-1\end{bmatrix}=\begin{bmatrix}-\frac7{12}&-\frac12&\frac5{12}\\[2pt]\frac16&0&\frac16\\[2pt]\frac1{12}&-\frac12&\frac1{12}\end{bmatrix}.
$$

Then

$$
\begin{aligned}
\mathbf X&=\mathbf A^{-1}\begin{bmatrix}2\\-3\\4\end{bmatrix}\\
&=\begin{bmatrix}-\frac76+\frac32+\frac53\\[2pt]\frac13+0+\frac23\\[2pt]\frac16+\frac32+\frac13\end{bmatrix}\\
&=\begin{bmatrix}2\\1\\2\end{bmatrix}.
\end{aligned}
$$

Substituting back: $-2+2+2=2$, $1-4=-3$ and $2+4-2=4$.

### Worked examples: homogeneous systems with a parameter

**Example 5.27.** Find $k$ so that $x+5y+3z=0$, $5x+y-kz=0$, $x+2y+kz=0$ has a non-trivial solution. Expanding along row 1,

$$
\begin{aligned}
|\mathbf A|&=\begin{vmatrix}1&5&3\\5&1&-k\\1&2&k\end{vmatrix}\\
&=1\big(k-(-2k)\big)-5\big(5k-(-k)\big)+3(10-1)\\
&=3k-30k+27\\
&=27-27k .
\end{aligned}
$$

This vanishes only for $k=1$; for any other $k$ the only solution is $x=y=z=0$. With $k=1$, eliminating $x$ from the first two equations ($5\times$ first minus second) gives $24y+16z=0$, so $y=-\frac23z$, and then $x=-5y-3z=\frac13z$. Taking $z=3\lambda$,

$$
(x,y,z)=\lambda(1,-2,3).
$$

Check in equation 3 with $k=1$: $1-4+3=0$.

**Exercise 64.** Find the two values of $\alpha$ for which

$$
\alpha x-3y+(1+\alpha)z=0,\qquad 2x+y-\alpha z=0,\qquad(\alpha+2)x-2y+\alpha z=0
$$

has a non-trivial solution. Along row 1,

$$
\begin{aligned}
|\mathbf A|&=\alpha\big(\alpha-2\alpha\big)+3\big(2\alpha+\alpha(\alpha+2)\big)+(1+\alpha)\big(-4-(\alpha+2)\big)\\
&=-\alpha^2+3\alpha^2+12\alpha-(\alpha+1)(\alpha+6)\\
&=2\alpha^2+12\alpha-\alpha^2-7\alpha-6\\
&=\alpha^2+5\alpha-6\\
&=(\alpha-1)(\alpha+6).
\end{aligned}
$$

So $\alpha=1$ or $\alpha=-6$. For $\alpha=1$ the equations are $x-3y+2z=0$, $2x+y-z=0$, $3x-2y+z=0$; the first two give $x:y:z=1:5:7$, so $(x,y,z)=\lambda(1,5,7)$, and the third checks: $3-10+7=0$. For $\alpha=-6$ they are $-6x-3y-5z=0$, $2x+y+6z=0$, $-4x-2y-6z=0$; twice the second plus the third gives $6z=0$, so $z=0$ and $y=-2x$, giving $(x,y,z)=\mu(1,-2,0)$, and the first checks: $-6+6=0$.

**Specimen Test 17, Q3.** For $\alpha x+y-z=0$, $2x+3y+3z=0$, $4x+5y+z=0$,

$$
\begin{aligned}
\begin{vmatrix}\alpha&1&-1\\2&3&3\\4&5&1\end{vmatrix}&=\alpha(3-15)-1(2-12)-1(10-12)\\
&=-12\alpha+10+2\\
&=12-12\alpha ,
\end{aligned}
$$

which is zero for $\alpha=1$.

**Example 5.28.** For $\mathbf A=\begin{bmatrix}3&1\\-2&0\end{bmatrix}$, find $\lambda$ so that $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ has a non-trivial solution. The condition is

$$
\begin{aligned}
|\mathbf A-\lambda\mathbf I|&=\begin{vmatrix}3-\lambda&1\\-2&-\lambda\end{vmatrix}\\
&=-\lambda(3-\lambda)+2\\
&=\lambda^2-3\lambda+2\\
&=(\lambda-1)(\lambda-2)=0 .
\end{aligned}
$$

For $\lambda=1$ both rows reduce to $2x+y=0$, so $\mathbf X=\alpha(1,-2)^{\mathrm T}$. For $\lambda=2$ both reduce to $x+y=0$, so $\mathbf X=\beta(1,-1)^{\mathrm T}$. These $\lambda$ and $\mathbf X$ are the eigenvalues and eigenvectors of [[Eigenvalues and Eigenvectors|M18]].

## 4. Cramer's rule (James §5.5.1)

The adjoint also gives each unknown separately. For three equations $\mathbf{AX}=\mathbf b$, multiply equation 1 by the cofactor $A_{11}$, equation 2 by $A_{21}$, equation 3 by $A_{31}$, and add:

$$
\begin{aligned}
&(a_{11}A_{11}+a_{21}A_{21}+a_{31}A_{31})x_1+(a_{12}A_{11}+a_{22}A_{21}+a_{32}A_{31})x_2\\
&\quad+(a_{13}A_{11}+a_{23}A_{21}+a_{33}A_{31})x_3=b_1A_{11}+b_2A_{21}+b_3A_{31}.
\end{aligned}
$$

The coefficient of $x_1$ is the expansion of $|\mathbf A|$ down column 1. The coefficients of $x_2$ and $x_3$ pair column 2 or 3 with the cofactors of column 1, which is the expansion of a determinant with two equal columns, so both are zero. The right-hand side is the expansion down column 1 of $\mathbf A$ with column 1 replaced by $\mathbf b$. Hence

$$
|\mathbf A|\,x_1=\begin{vmatrix}b_1&a_{12}&a_{13}\\b_2&a_{22}&a_{23}\\b_3&a_{32}&a_{33}\end{vmatrix},
$$

and the same argument with the cofactors of column 2 or 3 gives the other unknowns. **Cramer's rule** is

$$
\boxed{x_i=\frac{|\mathbf A_i|}{|\mathbf A|}\qquad(|\mathbf A|\neq0),}
$$

where $\mathbf A_i$ is $\mathbf A$ with column $i$ replaced by $\mathbf b$. It is $\mathbf X=\mathbf A^{-1}\mathbf b=\operatorname{adj}\mathbf A\,\mathbf b/|\mathbf A|$ written out one component at a time.

Applied to Example 5.26, with $|\mathbf A|=2$,

$$
x=\frac12\begin{vmatrix}6&1&1\\14&2&3\\36&4&9\end{vmatrix}=\frac12\big(6(18-12)-1(126-108)+1(56-72)\big)=\frac12(36-18-16)=1,
$$

and the other two determinants are 4 and 6, giving $y=2$ and $z=3$. For Exercise 63 the three determinants are $-24$, $-12$, $-24$ over $|\mathbf A|=-12$, giving $(2,1,2)$ again.

> [!warning] Cramer's rule is a formula, not a method
> Each unknown needs its own $n\times n$ determinant, so the work grows like that of $n+1$ determinants. Ten equations solved this way need of order $4\times10^8$ multiplications, while elimination needs a few hundred. The rule is also numerically unstable. Use it for a $2\times2$, for a single unknown of a small system, or for theory (it shows the solution depends continuously on the data while $|\mathbf A|\neq0$); solve real systems by elimination.

## 5. Gaussian elimination and back-substitution (James §5.5.2)

### Row operations and why they are safe

Elimination transforms the system with three **elementary row operations**, applied to whole rows of the augmented matrix $[\mathbf A\,|\,\mathbf b]$ (both $\mathbf A$ and $\mathbf b$, never $\mathbf X$):

1. multiply a row by a non-zero constant, $R_i\to kR_i$;
2. interchange two rows, $R_i\leftrightarrow R_j$;
3. add a multiple of one row to another, $R_i\to R_i+mR_j$.

None of them changes the solution set. Any $\mathbf X$ that satisfies the old equations satisfies the new ones, because each new equation is a combination of old ones. Each operation is also reversed by an operation of the same kind ($R_i\to\frac1kR_i$, the same swap, $R_i\to R_i-mR_j$), so any $\mathbf X$ satisfying the new equations satisfies the old ones too. The two systems therefore have exactly the same solutions. The condition $k\neq0$ matters: multiplying an equation by zero throws it away and is not reversible.

### The algorithm

Gaussian elimination brings $[\mathbf A\,|\,\mathbf b]$ to **upper-triangular** form, zeros everywhere below the diagonal:

1. Use the first-column entry $a_{11}$ (the **pivot**) to clear every entry below it with $R_i\to R_i-\dfrac{a_{i1}}{a_{11}}R_1$. If the pivot is zero, swap in a lower row with a non-zero entry in that column.
2. Repeat on the second column with the new $a_{22}$ as pivot, clearing rows $3,\dots,n$, and so on until the last column.
3. **Back-substitute.** The last equation contains only $x_n$; solve it, substitute into the equation above, and work upwards.

For an upper-triangular system with entries $u_{ij}$ and right-hand side $c_i$, back-substitution is

$$
\begin{aligned}
x_n&=\frac{c_n}{u_{nn}},\\
x_{n-1}&=\frac{c_{n-1}-u_{n-1,n}x_n}{u_{n-1,n-1}},\\
x_i&=\frac{1}{u_{ii}}\Big(c_i-\sum_{j=i+1}^{n}u_{ij}x_j\Big)\qquad(i=n-1,\dots,1).
\end{aligned}
$$

Clearing column $k$ takes about $(n-k)^2$ multiplications, so the whole forward sweep takes about $\sum_k(n-k)^2\approx n^3/3$, and back-substitution only about $n^2/2$.

### Worked examples: elimination

**Example 5.31.** Solve $x+2y+3z=10$, $-x+y+z=0$, $y-z=1$.

$$
\left[\begin{array}{ccc|c}1&2&3&10\\-1&1&1&0\\0&1&-1&1\end{array}\right]\xrightarrow{R_2+R_1}\left[\begin{array}{ccc|c}1&2&3&10\\0&3&4&10\\0&1&-1&1\end{array}\right]\xrightarrow{R_3-\frac13R_2}\left[\begin{array}{ccc|c}1&2&3&10\\0&3&4&10\\0&0&-\frac73&-\frac73\end{array}\right]
$$

Back-substitution:

$$
\begin{aligned}
-\tfrac73z&=-\tfrac73\;\Rightarrow\;z=1,\\
3y&=10-4z=6\;\Rightarrow\;y=2,\\
x&=10-2y-3z=10-4-3=3 .
\end{aligned}
$$

So $(x,y,z)=(3,2,1)$. Dividing row 2 by 3 first gives the reduced equations $x+2y+3z=10$, $y+\frac43z=\frac{10}3$, $z=1$, the same answer.

**Example 5.33.** Solve $2x+3y+4z=1$, $x+2y+3z=1$, $x+4y+5z=2$.

$$
\left[\begin{array}{ccc|c}2&3&4&1\\1&2&3&1\\1&4&5&2\end{array}\right]\xrightarrow[R_3-\frac12R_1]{R_2-\frac12R_1}\left[\begin{array}{ccc|c}2&3&4&1\\0&\frac12&1&\frac12\\0&\frac52&3&\frac32\end{array}\right]\xrightarrow{R_3-5R_2}\left[\begin{array}{ccc|c}2&3&4&1\\0&\frac12&1&\frac12\\0&0&-2&-1\end{array}\right]
$$

Back-substitution:

$$
\begin{aligned}
-2z&=-1\;\Rightarrow\;z=\tfrac12,\\
\tfrac12y&=\tfrac12-z=0\;\Rightarrow\;y=0,\\
2x&=1-3y-4z=1-2\;\Rightarrow\;x=-\tfrac12 .
\end{aligned}
$$

So $(x,y,z)=\big(-\frac12,0,\frac12\big)$. Dividing each pivot row by its pivot before clearing gives the same solution with the triangular matrix normalised to 1s on the diagonal.

**Example 5.34**, a $4\times4$ system:

$$
\left[\begin{array}{cccc|c}1&2&3&1&5\\2&1&1&1&3\\1&2&1&0&4\\0&1&1&2&0\end{array}\right].
$$

Column 1: $R_2-2R_1$ gives $(0,-3,-5,-1\,|\,-7)$ and $R_3-R_1$ gives $(0,0,-2,-1\,|\,-1)$; row 4 already starts with 0. Column 2: $R_4+\frac13R_2$ gives $(0,0,-\frac23,\frac53\,|\,-\frac73)$; row 3 already has 0 there. Column 3: $R_4-\frac13R_3$ gives $(0,0,0,2\,|\,-2)$. Back-substitution:

$$
\begin{aligned}
2t&=-2\;\Rightarrow\;t=-1,\\
-2z-t&=-1\;\Rightarrow\;-2z+1=-1\;\Rightarrow\;z=1,\\
-3y-5z-t&=-7\;\Rightarrow\;-3y-5+1=-7\;\Rightarrow\;y=1,\\
x&=5-2y-3z-t=5-2-3+1=1 .
\end{aligned}
$$

So $(x,y,z,t)=(1,1,1,-1)$.

**Exercise 73**, by the standard method (the work scheme omits the tridiagonal algorithm):

$$
\left[\begin{array}{cccc|c}4&-1&0&0&2\\-1&4&-1&0&5\\0&-1&4&-1&3\\0&0&-1&4&10\end{array}\right].
$$

Each column has only one entry below the diagonal, so each step is a single row operation:

$$
\begin{aligned}
R_2+\tfrac14R_1&:\;(0,\tfrac{15}4,-1,0\,|\,\tfrac{11}2),\\
R_3+\tfrac4{15}R_2&:\;(0,0,\tfrac{56}{15},-1\,|\,\tfrac{67}{15}),\\
R_4+\tfrac{15}{56}R_3&:\;(0,0,0,\tfrac{209}{56}\,|\,\tfrac{627}{56}).
\end{aligned}
$$

Back-substitution gives $t=\frac{627}{209}=3$, then $\frac{56}{15}z=\frac{67}{15}+3=\frac{112}{15}$ so $z=2$, then $\frac{15}4y=\frac{11}2+2=\frac{15}2$ so $y=2$, then $4x=2+2$ so $x=1$: $(x,y,z,t)=(1,2,2,3)$.

A tridiagonal matrix, non-zero only on the diagonal and its two neighbours, needs one elimination per row and keeps its shape, so the work grows like $n$ rather than $n^3$. That specialisation is the Thomas algorithm, and tridiagonal systems are what the central-difference heat equation produces in [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|SESA2029 A3]] and every implicit time step in [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods|SESA2029 A4]].

### Singular systems under elimination

When $|\mathbf A|=0$, elimination produces a row of zeros in the coefficient part. The right-hand entry of that row decides the case: $0=0$ means the system is consistent with a free unknown, and $0=c$ with $c\neq0$ means it is inconsistent.

**Specimen Test 17, Q4.** Solve $x+2y+z=10$, $2x+y+z=6$, $10x-y+3z=2$.

$$
\left[\begin{array}{ccc|c}1&2&1&10\\2&1&1&6\\10&-1&3&2\end{array}\right]\xrightarrow[R_3-10R_1]{R_2-2R_1}\left[\begin{array}{ccc|c}1&2&1&10\\0&-3&-1&-14\\0&-21&-7&-98\end{array}\right]\xrightarrow{R_3-7R_2}\left[\begin{array}{ccc|c}1&2&1&10\\0&-3&-1&-14\\0&0&0&0\end{array}\right]
$$

The last row reads $0=0$: $\mathbf A$ is singular but the system is consistent. Set $z=\lambda$. Row 2 gives $-3y-\lambda=-14$, so $y=\frac{14-\lambda}{3}$, and row 1 gives

$$
\begin{aligned}
x&=10-2y-z\\
&=10-\frac{28-2\lambda}{3}-\lambda\\
&=\frac{30-28+2\lambda-3\lambda}{3}\\
&=\frac{2-\lambda}{3}.
\end{aligned}
$$

With $\lambda=2$ the solution is $(0,4,2)$, and $0+8+2=10$, $0+4+2=6$, $0-4+6=2$ all hold.

### Pivoting

A zero pivot stops the algorithm, and a small pivot is nearly as bad, because dividing by it magnifies rounding errors. **Partial pivoting** swaps rows before each column is cleared so that the pivot is the entry of largest magnitude in that column on or below the diagonal. Every library solver does this. In Example 5.35, for

$$
\left[\begin{array}{cccc|c}1&2&3&1&4\\2&1&1&1&3\\1&3&1&0&2\\0&1&1&2&1\end{array}\right],
$$

rows 1 and 2 are swapped before column 1 is cleared (pivot 2, not 1), and rows 2 and 3 before column 2 (pivot $\frac52$, not $\frac32$); back-substitution then gives $(x,y,z,t)=(1,0,1,0)$, which satisfies all four original equations.

## 6. The inverse by elimination (booklet section 7)

To find $\mathbf A^{-1}$ by elimination, write the $n\times2n$ matrix $[\mathbf A\,|\,\mathbf I]$ and apply row operations until the left half is $\mathbf I$. The right half is then $\mathbf A^{-1}$:

$$
[\mathbf A\,|\,\mathbf I]\;\longrightarrow\;[\mathbf I\,|\,\mathbf A^{-1}].
$$

Unlike Gaussian elimination, this clears entries above the diagonal as well as below (the variant is often called **Gauss–Jordan** elimination). Work column by column: scale the pivot to 1, then clear every other entry in its column.

Why it works: each elementary row operation is the same as pre-multiplying by an **elementary matrix** $\mathbf E$, the identity with that operation applied to it. For example, $R_2\to R_2+mR_1$ on a $3\times3$ is pre-multiplication by $\begin{bmatrix}1&0&0\\m&1&0\\0&0&1\end{bmatrix}$. If the operations $\mathbf E_1,\mathbf E_2,\dots,\mathbf E_k$ turn $\mathbf A$ into $\mathbf I$, then

$$
\mathbf E_k\cdots\mathbf E_2\mathbf E_1\mathbf A=\mathbf I ,
$$

so the product $\mathbf P=\mathbf E_k\cdots\mathbf E_1$ is $\mathbf A^{-1}$. The same operations applied to the right half turn $\mathbf I$ into $\mathbf P\mathbf I=\mathbf P=\mathbf A^{-1}$. If $\mathbf A$ is singular, a row of zeros appears on the left and the reduction cannot reach $\mathbf I$, which is the elimination method's own singularity test.

For large $n$ this costs of order $n^3$ operations against the factorial growth of the cofactor method.

### Inverse by elimination, a 3 by 3 example

Find $\mathbf A^{-1}$ for $\mathbf A=\begin{pmatrix}1&2&3\\-1&1&1\\0&1&-1\end{pmatrix}$ (the matrix of Example 5.31).

$$
\left(\begin{array}{ccc|ccc}1&2&3&1&0&0\\-1&1&1&0&1&0\\0&1&-1&0&0&1\end{array}\right)\xrightarrow{R_2+R_1}\left(\begin{array}{ccc|ccc}1&2&3&1&0&0\\0&3&4&1&1&0\\0&1&-1&0&0&1\end{array}\right)
$$

Column 1 is done. In column 2, scale the pivot to 1 and clear above and below it:

$$
\xrightarrow{\frac13R_2}\left(\begin{array}{ccc|ccc}1&2&3&1&0&0\\0&1&\frac43&\frac13&\frac13&0\\0&1&-1&0&0&1\end{array}\right)\xrightarrow[R_3-R_2]{R_1-2R_2}\left(\begin{array}{ccc|ccc}1&0&\frac13&\frac13&-\frac23&0\\0&1&\frac43&\frac13&\frac13&0\\0&0&-\frac73&-\frac13&-\frac13&1\end{array}\right)
$$

In column 3, scale by $-\frac37$ and clear above:

$$
\xrightarrow{-\frac37R_3}\left(\begin{array}{ccc|ccc}1&0&\frac13&\frac13&-\frac23&0\\0&1&\frac43&\frac13&\frac13&0\\0&0&1&\frac17&\frac17&-\frac37\end{array}\right)\xrightarrow[R_2-\frac43R_3]{R_1-\frac13R_3}\left(\begin{array}{ccc|ccc}1&0&0&\frac27&-\frac57&\frac17\\0&1&0&\frac17&\frac17&\frac47\\0&0&1&\frac17&\frac17&-\frac37\end{array}\right)
$$

So

$$
\mathbf A^{-1}=\frac17\begin{pmatrix}2&-5&1\\1&1&4\\1&1&-3\end{pmatrix}.
$$

As a check, $\mathbf A^{-1}(10,0,1)^{\mathrm T}=\frac17(20+1,\;10+4,\;10-3)^{\mathrm T}=(3,2,1)^{\mathrm T}$, the solution of Example 5.31.

**Booklet Exercise B(i).** For $\begin{pmatrix}1&2\\2&1\end{pmatrix}$:

$$
\left(\begin{array}{cc|cc}1&2&1&0\\2&1&0&1\end{array}\right)\xrightarrow{R_2-2R_1}\left(\begin{array}{cc|cc}1&2&1&0\\0&-3&-2&1\end{array}\right)\xrightarrow{-\frac13R_2}\left(\begin{array}{cc|cc}1&2&1&0\\0&1&\frac23&-\frac13\end{array}\right)\xrightarrow{R_1-2R_2}\left(\begin{array}{cc|cc}1&0&-\frac13&\frac23\\0&1&\frac23&-\frac13\end{array}\right),
$$

the same inverse as Booklet Exercise A by cofactors.

**Booklet Exercise B(ii)** is the Exercise 63 matrix. The sequence $R_3+R_1$, $R_3-6R_2$, $\frac1{12}R_3$, $R_2+2R_3$, $R_1-R_3$, $R_1-2R_2$, $-R_1$ reaches the same $\mathbf A^{-1}$ as the cofactor method in section 3.

**Specimen Test 17, Q5.** For $\mathbf A=\begin{pmatrix}1&1&1\\2&0&2\\2&-2&1\end{pmatrix}$ the rows of $[\mathbf A\,|\,\mathbf I]$ evolve as

| Step | Operation | Row produced |
|---|---|---|
| 1 | $R_2-2R_1$ | $(0,-2,0\,\vert\,-2,1,0)$ |
| 2 | $R_3-2R_1$ | $(0,-4,-1\,\vert\,-2,0,1)$ |
| 3 | $R_3-2R_2$ | $(0,0,-1\,\vert\,2,-2,1)$ |
| 4 | $-R_3$ | $(0,0,1\,\vert\,-2,2,-1)$ |
| 5 | $-\frac12R_2$ | $(0,1,0\,\vert\,1,-\frac12,0)$ |
| 6 | $R_1-R_2-R_3$ | $(1,0,0\,\vert\,2,-\frac32,1)$ |

so

$$
\mathbf A^{-1}=\begin{pmatrix}2&-\frac32&1\\1&-\frac12&0\\-2&2&-1\end{pmatrix},
$$

consistent with $|\mathbf A|=2$ and $|\mathbf A^{-1}|=\frac12$.

## 7. Ill-conditioning (James §5.5.2)

A system is **ill-conditioned** when a small change in its coefficients produces a large change in its solution. **Example 5.36** solves

$$
\begin{bmatrix}2&1\\1&0.5001\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix}=\begin{bmatrix}0.3\\0.6\end{bmatrix}
$$

and the same system with $0.4999$ in place of $0.5001$. Eliminating with $R_2-\frac12R_1$ leaves $(0.5001-0.5)y=0.6-0.15$, that is $\pm0.0001\,y=0.45$:

| Coefficient | $y$ | $x=\frac{0.3-y}{2}$ | $\lvert\mathbf A\rvert$ |
|---|---|---|---|
| $0.5001$ | $4500$ | $-2249.85$ | $+0.0002$ |
| $0.4999$ | $-4500$ | $2250.15$ | $-0.0002$ |

A change of $0.0002$ in one coefficient reverses the solution. The cause is the subtraction of two nearly equal numbers, $0.5001-0.5$, which happens because the two rows are almost proportional: the determinant is almost zero, and the lines are almost parallel.

The geometry shows it directly. Solve $2x+y=0.3$ with $x-ay=0$, where $a=1\pm0.05$: then

$$
x=\frac{0.3a}{1+2a},\qquad y=\frac{0.3}{1+2a},
$$

so $0.0983\le x\le0.1016$ and $0.0968\le y\le0.1034$, errors of about 2% and 3% from a 5% error in $a$. Now solve $2x+y=0.3$ with $x+ay=0.3$, where $a=0.4\pm0.05$:

$$
x=\frac{0.3(1-a)}{1-2a},\qquad y=\frac{-0.3}{1-2a},
$$

so $0.65\le x\le1.65$ and $-3\le y\le-1$: a 12% error in $a$ gives errors up to 100%. In the second case the lines meet at a shallow angle, so tilting one slightly slides the intersection a long way, and the determinant $2a-1=-0.2\pm0.1$ is small compared with the entries.

![[m1054_m17_ill_conditioning.png|900]]

A small determinant is one warning sign, though it must be judged relative to the size of the entries (scaling every entry by 10 scales a $2\times2$ determinant by 100 without changing the conditioning). Proper measures, the condition number, belong to numerical analysis. In practice, use partial pivoting and treat any nearly singular system with suspicion.

## Terminology and alternative names

| Term here | Alternatives |
|---|---|
| direct method, cofactor method, $\mathbf A^{-1}=\operatorname{adj}\mathbf A/\lvert\mathbf A\rvert$ | adjoint method; adjugate (the modern name for $\operatorname{adj}\mathbf A$, which James and the booklet call the adjoint) |
| elimination method for the inverse, $[\mathbf A\,\vert\,\mathbf I]\to[\mathbf I\,\vert\,\mathbf A^{-1}]$ | Gauss–Jordan elimination |
| inhomogeneous system ($\mathbf b\neq\mathbf0$) | non-homogeneous system (James) |
| non-singular matrix | invertible matrix |
| back-substitution | back substitution |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M17 Solutions - Matrices II]]
- Previous: [[MATH1054 M16 - Matrices I]] (determinants, cofactors, the adjoint) · Next: [[MATH1054 M18 - Matrices III]] (rank and consistency, eigenvalues)
- Concepts: [[Matrix Inverse]] · [[Gaussian Elimination]] · [[Determinants and Cofactors]] · [[Matrix Algebra]] · [[Rank and Consistency of Linear Systems]] · [[Eigenvalues and Eigenvectors]]
- Later in the vault: [[Jacobi, Gauss-Seidel and SOR Iteration]] (iterative alternatives to elimination), [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] (Gaussian elimination on a tridiagonal finite-difference system), [[Finite Difference Approximations]], [[Global Stiffness Matrix Assembly]] and [[Matrix Displacement Method]] (large linear systems from finite elements), [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]] (matrix inverse in state-space models)

## Sources

- MATH1054 Module Booklet, Module 17 (work scheme pp. 1–4 of the module, Specimen Test 17 on p. 5; PDF pp. 62–66), including the inverse-by-elimination method of section 7, which James does not cover.
- James, *Modern Engineering Mathematics* (6th ed.): §5.4 pp. 339–341 (inverse, uniqueness, $(\mathbf{AB})^{-1}$); §5.5.1 pp. 345–350 (the four cases, Examples 5.25–5.28, Cramer's rule); §5.5.2 pp. 354–356 (elimination and row operations), Examples 5.31, 5.33–5.35 and ill-conditioning pp. 363–368.

## Self-study tasks

### Core

- [ ] Exercise 51 and Booklet Exercise A: singular or non-singular, and inverses by the direct method (Module 17 work scheme). → [[MATH1054 M17 Solutions - Matrices II#Exercise 51: Singular or non-singular? Find the inverses]]
- [ ] Exercise 63: invert by cofactors, then solve the system (Module 17 work scheme). → [[MATH1054 M17 Solutions - Matrices II#Exercise 63: Invert, then solve the system]]
- [ ] Exercise 64: the two values of α giving non-trivial solutions, and the solutions (Module 17 work scheme). → [[MATH1054 M17 Solutions - Matrices II#Part B: Assigned exercises]] (Exercise 64)
- [ ] Exercise 73 by the standard elimination method (Module 17 work scheme). → [[MATH1054 M17 Solutions - Matrices II#Exercise 73: Standard elimination (not the tridiagonal algorithm)]]
- [ ] Booklet Exercise B: inverses by elimination (Module 17 work scheme). → [[MATH1054 M17 Solutions - Matrices II#Booklet Exercise B: Inverses by elimination]]

### Further practice

- [ ] Specimen Test 17, Q1–Q5, timed. → [[MATH1054 M17 Solutions - Matrices II#Part C: Specimen Test 17]]
- [ ] Specimen Test 17, Q4: a singular but consistent system by elimination. → [[MATH1054 M17 Solutions - Matrices II#Q4: Elimination]]
- [ ] Examples 5.27 and 5.28, filling in the determinant expansions (Module 17 work scheme, item 4). → [[#Worked examples: homogeneous systems with a parameter]]
- [ ] Examples 5.33 and 5.34 by elimination without looking (Module 17 work scheme, item 6). → [[#Worked examples: elimination]]
- [ ] Example 5.36 and the ill-conditioning section (Module 17 work scheme, item 8). → [[#7. Ill-conditioning (James §5.5.2)]]
