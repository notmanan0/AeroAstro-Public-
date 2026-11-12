---
title: "MATH1054 M18 - Matrices III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 4: Vectors and Matrices"
order: 18
tags:
  - math1054
  - matrices
  - rank
  - eigenvalues
aliases: ["MATH1054 Module 18", "Matrices III"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 18 work scheme; James §5.6 (rank, echelon form, consistency, non-square systems, Figure 5.19, Examples 5.37–5.39), §5.7.1–5.7.2 (characteristic equation, eigenvalues and eigenvectors, Examples 5.40–5.44, normalisation) and §5.7.7 (symmetric matrices)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M17 - Matrices II]]"]
next_topics: ["[[MATH1054 M20 - Further Calculus II]]"]
key_concepts: ["[[Rank and Consistency of Linear Systems]]", "[[Eigenvalues and Eigenvectors]]", "[[Characteristic Equation and Eigenvalues]]"]
tutorial_sheets: ["[[MATH1054 M18 Solutions - Matrices III]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 18)", "02 - Sources/Modern Engineering Mathematics.pdf (§5.6–5.7)"]
---

# MATH1054 M18 - Matrices III

> [!abstract] Summary
> The rank of a matrix is the number of non-zero rows left after row reduction to echelon form, which is the number of genuinely independent rows. For any linear system $\mathbf A\mathbf X=\mathbf b$ in $n$ unknowns, square or not, there is a solution exactly when $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]$, and it then has $n-\operatorname{rank}\mathbf A$ free parameters. An eigenvector of a square matrix is a non-zero $\mathbf X$ that the matrix only scales, $\mathbf A\mathbf X=\lambda\mathbf X$; the eigenvalues are the roots of the characteristic equation $|\mathbf A-\lambda\mathbf I|=0$, and a real symmetric matrix has real eigenvalues and mutually orthogonal eigenvectors.

> [!summary]- Exam use: quick path
> - **Use it when:** deciding whether a system has no, one or infinitely many solutions (especially a non-square system or one with $|\mathbf A|=0$), or finding the eigenvalues and eigenvectors of a $2\times2$ or $3\times3$ matrix.
> - **Assumptions:** exact arithmetic; $n$ is the number of unknowns (columns of $\mathbf A$); in this module the characteristic equation has real, distinct roots (repeated roots are not covered).
> - **Method:** 1. Reduce $[\mathbf A|\mathbf b]$ to echelon form by row operations. 2. Count the non-zero rows of $\mathbf A$ and of $[\mathbf A|\mathbf b]$: unequal means no solution; equal to $r$ means $n-r$ free parameters, found by back substitution. 3. For eigenvalues, expand $|\mathbf A-\lambda\mathbf I|=0$ and check $\sum\lambda_i=\operatorname{tr}\mathbf A$, $\prod\lambda_i=|\mathbf A|$. 4. For each $\lambda$, solve $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$, keeping an arbitrary non-zero constant. 5. Check $\mathbf A\mathbf X=\lambda\mathbf X$.
> - **Common mistakes:** reading a row $(0\ \cdots\ 0\,|\,c)$ with $c\neq0$ as a zero row, which hides an inconsistency; giving an eigenvector without its arbitrary constant, or accepting $\mathbf X=\mathbf0$.
> - **Practise:** [[#A full three-by-three eigenproblem (Example 5.44)]] · [[MATH1054 M18 Solutions - Matrices III#Booklet Exercise A: Eigenvalues and eigenvectors|Booklet Exercise A]]

When $|\mathbf A|\neq0$, $n$ equations in $n$ unknowns have one solution, found by the inverse, Cramer's rule or elimination ([[MATH1054 M17 - Matrices II|Matrices II]]). When $|\mathbf A|=0$ those methods stop working, and when the number of equations differs from the number of unknowns a determinant does not even exist. Rank is the replacement. Row reduction to echelon form turns any system into a staircase of equations; counting the steps gives the rank, and comparing the rank of $\mathbf A$ with that of the augmented matrix settles existence and the number of free parameters at once. The same reduction then produces the solution by back substitution, so the classification costs no extra work.

A second question about a square matrix is which vectors it maps onto multiples of themselves. Most vectors are both stretched and turned by $\mathbf A$; an eigenvector is only stretched, by the factor $\lambda$. Finding them is a homogeneous-system problem, because $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ has a non-zero solution only when $\mathbf A-\lambda\mathbf I$ has rank below $n$, that is when its determinant vanishes.

Engineers meet eigenvalues everywhere a linear system has natural directions or natural rates. For a vibrating structure they give the natural frequencies and the eigenvectors give the mode shapes; for a dynamic system written in state-space form they are the poles that decide stability; for a stress tensor they are the principal stresses and the eigenvectors are the principal directions. All of them rest on the calculation of Sections 5 to 7.

---

## 1. Row operations, echelon form and rank (James §5.6)

Three elementary row operations are used: interchange two rows, multiply a row by a non-zero constant, and add a multiple of one row to another. Applied to the augmented matrix $[\mathbf A|\mathbf b]$ they do not change the solution set, because each can be undone by an operation of the same kind (interchange again, multiply by the reciprocal, subtract the same multiple). Any solution of the new system therefore solves the old one and vice versa.

A matrix is in **echelon form** when the leading (first non-zero) entry of each row lies strictly to the right of the leading entry of the row above, and any zero rows sit at the bottom. Below the staircase every entry is zero. For a non-singular square matrix the staircase has one step per column and the echelon form is upper triangular with non-zero diagonal, which is ordinary Gaussian elimination. For a singular matrix some column has no non-zero entry on or below the diagonal; the procedure then moves on to the next column, and the staircase gains a longer step and the matrix gains zero rows.

The **rank** of $\mathbf A$, written $\operatorname{rank}\mathbf A$, is the number of non-zero rows in its echelon form. It counts the essentially different rows of $\mathbf A$: rows that cannot be written as combinations of the others are the ones that survive elimination.

### The system (5.30), a singular six-by-six example

Take the six equations in six unknowns

$$
\left[\begin{array}{cccccc|c}
1&0&1&1&0&0&1\\
0&1&1&0&1&2&1\\
1&1&2&1&1&2&2\\
1&0&1&0&1&3&0\\
0&0&0&0&1&3&0\\
1&1&2&0&2&5&1
\end{array}\right].
$$

Clear column 1 below the first row with $R_3-R_1$, $R_4-R_1$ and $R_6-R_1$:

$$
\left[\begin{array}{cccccc|c}
1&0&1&1&0&0&1\\
0&1&1&0&1&2&1\\
0&1&1&0&1&2&1\\
0&0&0&-1&1&3&-1\\
0&0&0&0&1&3&0\\
0&1&1&-1&2&5&0
\end{array}\right].
$$

Clear column 2 with $R_3-R_2$ and $R_6-R_2$:

$$
\left[\begin{array}{cccccc|c}
1&0&1&1&0&0&1\\
0&1&1&0&1&2&1\\
0&0&0&0&0&0&0\\
0&0&0&-1&1&3&-1\\
0&0&0&0&1&3&0\\
0&0&0&-1&1&3&-1
\end{array}\right].
$$

Column 3 has only zeros on and below the diagonal, so move to column 4. Interchange $R_3$ and $R_4$, clear column 4 with $R_6-R_3$ (which leaves a zero row), multiply $R_3$ by $-1$ so that its leading entry is 1, and finally interchange rows 4 and 5:

$$
\left[\begin{array}{cccccc|c}
1&0&1&1&0&0&1\\
0&1&1&0&1&2&1\\
0&0&0&1&-1&-3&1\\
0&0&0&0&1&3&0\\
0&0&0&0&0&0&0\\
0&0&0&0&0&0&0
\end{array}\right].
$$

This is the echelon form (5.31). Four rows are non-zero, so $\operatorname{rank}\mathbf A=4$, and the two zero rows have zero right-hand sides, so the system is consistent. Columns 3 and 6 carry no leading entry, so $x_3$ and $x_6$ are free. Back substitution with $x_6=t$ and $x_3=s$:

$$
\begin{aligned}
\text{row 4:}\quad x_5&=-3x_6=-3t,\\
\text{row 3:}\quad x_4&=1+x_5+3x_6=1-3t+3t=1,\\
\text{row 2:}\quad x_2&=1-x_3-x_5-2x_6=1-s+3t-2t=1-s+t,\\
\text{row 1:}\quad x_1&=1-x_3-x_4=1-s-1=-s.
\end{aligned}
$$

So $(x_1,\dots,x_6)=(-s,\ 1-s+t,\ s,\ 1,\ -3t,\ t)$ for any $s$ and $t$: two free parameters, which is $6-4$. James writes the parameters as $\lambda$ and $\mu$; here they are $s$ and $t$ so that $\lambda$ stays free for eigenvalues.

### The determinant definition of rank

An equivalent definition, and the more common one in other books, is that the rank is the order of the largest square submatrix (formed by deleting rows and columns) with non-zero determinant. For (5.30) the $6\times6$ determinant is zero and all 36 of the $5\times5$ minors are zero, but deleting rows 3 and 4 and columns 3 and 6 leaves

$$
\begin{vmatrix}1&0&1&0\\0&1&0&1\\0&0&0&1\\1&1&0&2\end{vmatrix}=1\neq0,
$$

which confirms rank 4. Proving that the two definitions agree is not straightforward, and with many minors to evaluate the echelon form is far quicker in practice.

Two bounds follow directly from the echelon form of an $m\times n$ matrix. The number of non-zero rows cannot exceed the number of rows, and each non-zero row has its leading entry in a different column, so

$$
\operatorname{rank}\mathbf A\le\min(m,n).
$$

For a square matrix, row operations multiply the determinant by non-zero factors only ($-1$ for an interchange, $c$ for scaling a row, $1$ for adding a multiple of a row), so $|\mathbf A|\neq0$ exactly when the echelon form is triangular with non-zero diagonal, which is when $\operatorname{rank}\mathbf A=n$. Full rank and a non-zero determinant are the same statement.

### Three ranks (Example 5.37)

(a) $R_2-2R_1$, then $R_3-R_2$:

$$
\begin{bmatrix}1&1&-1\\2&-1&2\\0&-3&4\end{bmatrix}\to\begin{bmatrix}1&1&-1\\0&-3&4\\0&-3&4\end{bmatrix}\to\begin{bmatrix}1&1&-1\\0&-3&4\\0&0&0\end{bmatrix},
$$

two non-zero rows, so the rank is 2. Its determinant is therefore zero.

(b) $R_2+2R_1$ and $R_3+R_1$ both give zero rows, since every row is a multiple of $(1,-1,1)$:

$$
\begin{bmatrix}1&-1&1\\-2&2&-2\\-1&1&-1\end{bmatrix}\to\begin{bmatrix}1&-1&1\\0&0&0\\0&0&0\end{bmatrix},
$$

rank 1.

(c) $R_3-2R_1$ gives a triangular matrix with non-zero diagonal:

$$
\begin{bmatrix}1&0&0\\0&1&1\\2&0&1\end{bmatrix}\to\begin{bmatrix}1&0&0\\0&1&1\\0&0&1\end{bmatrix},
$$

rank 3. Equivalently, $|\mathbf A|=1\cdot(1\cdot1-1\cdot0)=1\neq0$.

### A four-by-four rank (Specimen Test 18, Q1)

$R_2-2R_1$, $R_3+R_1$, $R_4-2R_1$, then $R_3-2R_2$, $R_4-R_2$, then $R_4-R_3$:

$$
\begin{pmatrix}1&1&-1&1\\2&3&-3&3\\-1&1&0&0\\2&3&-2&2\end{pmatrix}
\to\begin{pmatrix}1&1&-1&1\\0&1&-1&1\\0&2&-1&1\\0&1&0&0\end{pmatrix}
\to\begin{pmatrix}1&1&-1&1\\0&1&-1&1\\0&0&1&-1\\0&0&1&-1\end{pmatrix}
\to\begin{pmatrix}1&1&-1&1\\0&1&-1&1\\0&0&1&-1\\0&0&0&0\end{pmatrix}.
$$

Three non-zero rows: the rank is 3, and the $4\times4$ determinant is zero.

## 2. Consistency of a linear system (James §5.6)

Write the system as $\mathbf A\mathbf X=\mathbf b$, with $\mathbf A$ of size $m\times n$ ($m$ equations, $n$ unknowns), and form the **augmented matrix** $[\mathbf A|\mathbf b]$ by appending $\mathbf b$ as an extra column. James writes it $(\mathbf A:\mathbf b)$. Reduce the augmented matrix to echelon form. If $\operatorname{rank}\mathbf A=r$, the result has $r$ non-zero rows in the $\mathbf A$ part, with leading entries in columns $c_1<c_2<\dots<c_r$, and $m-r$ rows that are zero in the $\mathbf A$ part:

$$
\left[\begin{array}{c|c}\text{staircase with } r \text{ non-zero rows}&\mathbf u\\\hline\text{all zero}&\mathbf v\end{array}\right],
\qquad \mathbf u\in\mathbb R^{r},\quad \mathbf v\in\mathbb R^{m-r}.
$$

Each lower row reads $0x_1+0x_2+\dots+0x_n=v_i$. If any $v_i\neq0$ that equation is $0=v_i$, which nothing satisfies, so the system is **inconsistent**; in that case the augmented matrix has one more non-zero row than $\mathbf A$, so $\operatorname{rank}[\mathbf A|\mathbf b]=r+1$. If $\mathbf v=\mathbf0$, the lower rows say $0=0$ and can be dropped, and $\operatorname{rank}[\mathbf A|\mathbf b]=r$. The $r$ remaining equations can be solved from the bottom up for the leading variables $x_{c_1},\dots,x_{c_r}$, each in terms of the right-hand side and the other $n-r$ variables, which may take any values. So:

| Ranks | Solutions of $\mathbf A\mathbf X=\mathbf b$ |
|---|---|
| $\operatorname{rank}\mathbf A<\operatorname{rank}[\mathbf A\vert\mathbf b]$ | none: some row reads $0=c\neq0$ |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=n$ | exactly one |
| $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A\vert\mathbf b]=r<n$ | infinitely many, with $n-r$ free parameters |

The rule uses only the echelon form, so it holds for every shape of system: square, more unknowns than equations, or more equations than unknowns (Section 3).

A **homogeneous** system $\mathbf A\mathbf X=\mathbf0$ is always consistent, because appending a zero column cannot add a non-zero row, and $\mathbf X=\mathbf0$ is always a solution. It has non-trivial solutions exactly when $\operatorname{rank}\mathbf A<n$; for a square matrix that is $|\mathbf A|=0$, the condition that defines eigenvalues in Section 5.

> [!warning] Read the rank of $\mathbf A$ with the last column covered
> A row $(0\ 0\ \cdots\ 0\,|\,c)$ with $c\neq0$ is a zero row of $\mathbf A$ but a non-zero row of $[\mathbf A|\mathbf b]$. Counting it as non-zero for both gives equal ranks and a wrong claim of consistency; counting it as zero for both does the same. Count the rows of $\mathbf A$ with the right-hand column covered, then uncover it and count again.

Row interchanges are also used for accuracy. When the entries are finite-precision decimals, **partial pivoting** brings the entry of largest magnitude in the current column onto the diagonal before eliminating, then divides that row by it so the pivot is 1. With exact integers it is not needed, and the examples below are worked without it.

### An inconsistent square system (Example 5.38(a))

The system has $n=4$ and

$$
\mathbf A=\begin{bmatrix}0&1&1&0\\1&0&3&2\\2&1&5&4\\1&-2&0&2\end{bmatrix},\qquad\mathbf b=\begin{bmatrix}1\\3\\7\\2\end{bmatrix}.
$$

The $(1,1)$ entry is zero, so interchange $R_1$ and $R_2$, then clear column 1 with $R_3-2R_1$ and $R_4-R_1$:

$$
\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\2&1&5&4&7\\1&-2&0&2&2\end{array}\right]
\to\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\0&1&-1&0&1\\0&-2&-3&0&-1\end{array}\right].
$$

Clear column 2 with $R_3-R_2$ and $R_4+2R_2$, then column 3 with $R_4-\tfrac12R_3$:

$$
\to\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\0&0&-2&0&0\\0&0&-1&0&1\end{array}\right]
\to\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\0&0&-2&0&0\\0&0&0&0&1\end{array}\right].
$$

The last row reads $0=1$. So $\operatorname{rank}\mathbf A=3$ but $\operatorname{rank}[\mathbf A|\mathbf b]=4$, and the equations have no solution. With partial pivoting the last row comes out as $0=\tfrac25$ instead, and the conclusion is the same.

### Five unknowns and rank 2 (Example 5.38(b))

$$
\left[\begin{array}{ccccc|c}1&0&-1&1&-1&0\\0&1&1&-1&1&1\\1&1&0&0&0&1\\2&3&1&-1&1&3\\2&2&0&0&0&2\end{array}\right].
$$

$R_3-R_1$ gives $(0,1,1,-1,1\,|\,1)$, which is $R_2$; $R_4-2R_1$ gives $(0,3,3,-3,3\,|\,3)=3R_2$; and $R_5-2R_1$ gives $(0,2,2,-2,2\,|\,2)=2R_2$. Subtracting those multiples of $R_2$ leaves

$$
\left[\begin{array}{ccccc|c}1&0&-1&1&-1&0\\0&1&1&-1&1&1\\0&0&0&0&0&0\\0&0&0&0&0&0\\0&0&0&0&0&0\end{array}\right].
$$

Both ranks are 2, so the system is consistent with $5-2=3$ free parameters. With $x_3=\alpha$, $x_4=\beta$, $x_5=\gamma$, row 2 gives $x_2=1-\alpha+\beta-\gamma$ and row 1 gives $x_1=\alpha-\beta+\gamma$:

$$
x_1=\alpha-\beta+\gamma,\quad x_2=1-\alpha+\beta-\gamma,\quad x_3=\alpha,\quad x_4=\beta,\quad x_5=\gamma .
$$

Pivoting on the last row first and taking $x_2$ as a free variable instead of $x_3$ gives $x_1=1-\lambda$, $x_2=\lambda$, $x_3=1-\lambda+\mu-\nu$, $x_4=\mu$, $x_5=\nu$. Both describe the same three-parameter family: substituting either into all five equations gives zero residual.

### Infinitely many solutions (Exercise 88(a))

$$
\left[\begin{array}{ccc|c}1&2&3&8\\3&2&1&4\\1&1&1&3\end{array}\right]
\xrightarrow[R_3-R_1]{R_2-3R_1}\left[\begin{array}{ccc|c}1&2&3&8\\0&-4&-8&-20\\0&-1&-2&-5\end{array}\right]
\xrightarrow{R_3-\frac14R_2}\left[\begin{array}{ccc|c}1&2&3&8\\0&-4&-8&-20\\0&0&0&0\end{array}\right].
$$

$\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]=2<3$: one free parameter. With $z=\alpha$, row 2 gives $-4y=-20+8\alpha$, so $y=5-2\alpha$, and row 1 gives

$$
x=8-2y-3z=8-10+4\alpha-3\alpha=\alpha-2 .
$$

So $(x,y,z)=(\alpha-2,\ 5-2\alpha,\ \alpha)$, a straight line of solutions in three-dimensional space.

### No solution (Exercise 88(b))

$$
\left[\begin{array}{cccc|c}1&2&-1&1&0\\1&1&0&0&1\\0&1&-1&1&-1\\1&0&1&-1&1\end{array}\right]
\xrightarrow[R_4-R_1]{R_2-R_1}\left[\begin{array}{cccc|c}1&2&-1&1&0\\0&-1&1&-1&1\\0&1&-1&1&-1\\0&-2&2&-2&1\end{array}\right]
\xrightarrow[R_4-2R_2]{R_3+R_2}\left[\begin{array}{cccc|c}1&2&-1&1&0\\0&-1&1&-1&1\\0&0&0&0&0\\0&0&0&0&-1\end{array}\right].
$$

The last row reads $0=-1$, so $\operatorname{rank}\mathbf A=2$ but $\operatorname{rank}[\mathbf A|\mathbf b]=3$: no solution.

## 3. Systems with more unknowns or more equations (James §5.6)

A system with more unknowns than equations is **underspecified** (also called under-determined), and one with more equations than unknowns is **overspecified** (over-determined). There is no determinant to test, but row reduction and the rank rule work unchanged.

### Underspecified: cases (a) and (b)

Case (a), $x+y+z=1$ and $x+2y+3z=2$. Subtracting row 1 from row 2 gives $y+2z=1$. Put $z=t$; then $y=1-2t$ and $x=1-y-z=t$, so

$$
(x,y,z)=(t,\ 1-2t,\ t),
$$

with $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]=2$ and $n=3$: one free parameter.

Case (b), $x+y+z=1$ and $2x+2y+2z=1$. Subtracting twice row 1 from row 2 gives $0=-1$, so $\operatorname{rank}\mathbf A=1$, $\operatorname{rank}[\mathbf A|\mathbf b]=2$, and there is no solution. Here the clash is obvious, since $x+y+z$ cannot equal both 1 and $\tfrac12$, but in larger systems it rarely is. An underspecified system never has a unique solution, because $\operatorname{rank}\mathbf A\le m<n$ leaves at least one free parameter whenever it is consistent.

### Overspecified: cases (c) and (d)

Case (c): $x+y=-1$, $x+2y=0$, $x+3y=1$. Subtract row 1 from rows 2 and 3, then twice the new row 2 from row 3:

$$
\left[\begin{array}{cc|c}1&1&-1\\1&2&0\\1&3&1\end{array}\right]\to\left[\begin{array}{cc|c}1&1&-1\\0&1&1\\0&2&2\end{array}\right]\to\left[\begin{array}{cc|c}1&1&-1\\0&1&1\\0&0&0\end{array}\right].
$$

Both ranks are $2=n$, so the solution is unique: $y=1$, $x=-2$.

Case (d): the same left-hand sides with right-hand sides $0$, $1$, $-2$:

$$
\left[\begin{array}{cc|c}1&1&0\\1&2&1\\1&3&-2\end{array}\right]\to\left[\begin{array}{cc|c}1&1&0\\0&1&1\\0&2&-2\end{array}\right]\to\left[\begin{array}{cc|c}1&1&0\\0&1&1\\0&0&-4\end{array}\right].
$$

The last row says $0=-4$: $\operatorname{rank}\mathbf A=2$, $\operatorname{rank}[\mathbf A|\mathbf b]=3$, no solution. For overspecified systems this is the usual outcome, since a consistent one needs the extra equations to agree with the others exactly.

![[m1054_m18_overspecified_lines.png|900]]

*Each equation in two unknowns is a line in the $(x,y)$ plane. In case (c) the three lines pass through one point, $(-2,1)$. In case (d) each pair meets, at $(-1,1)$, $(1,-1)$ and $(7,-3)$, but no point lies on all three.*

### The general picture (James Figure 5.19)

For a $p\times q$ matrix $\mathbf A$ ($p$ equations, $q$ unknowns), $\operatorname{rank}\mathbf A\le\min(p,q)$, and with $r=q-\operatorname{rank}\mathbf A$ the rank rule gives:

| Shape | $\operatorname{rank}[\mathbf A\vert\mathbf b]>\operatorname{rank}\mathbf A$ | Equal ranks, $r>0$ | Equal ranks, $r=0$ |
|---|---|---|---|
| $p<q$ (underspecified) | no solution | $r$ free parameters; if $\mathbf b=\mathbf0$, a solution $\mathbf X\neq\mathbf0$ exists | impossible, since $\operatorname{rank}\mathbf A\le p<q$ |
| $p>q$ (overspecified) | no solution | $r$ free parameters; if $\mathbf b=\mathbf0$, a solution $\mathbf X\neq\mathbf0$ exists | unique; if $\mathbf b=\mathbf0$, only $\mathbf X=\mathbf0$ |
| $p=q$ (square) | no solution | $\vert\mathbf A\vert=0$, $r$ free parameters; if $\mathbf b=\mathbf0$, $\mathbf X\neq\mathbf0$ exists | $\vert\mathbf A\vert\neq0$, unique; if $\mathbf b=\mathbf0$, only $\mathbf X=\mathbf0$ |

The square row contains the most used result of the module: $\mathbf A\mathbf X=\mathbf0$ has a non-trivial solution if and only if $|\mathbf A|=0$.

### Two equations in three unknowns (Exercise 90(a))

$$
x+3y+4z=1,\qquad -x+3y+4z=3 .
$$

$R_2+R_1$ gives $6y+8z=4$, i.e. $3y+4z=2$; subtracting the equations gives $2x=-2$. Both ranks are 2 and $n=3$, so there is one free parameter. With $z=\alpha$:

$$
x=-1,\qquad y=\frac{2-4\alpha}{3},\qquad z=\alpha .
$$

### Three equations in two unknowns (Exercise 90(b))

$$
\left[\begin{array}{cc|c}2&1&1\\4&6&4\\3&5&-2\end{array}\right]
\xrightarrow[R_3-\frac32R_1]{R_2-2R_1}\left[\begin{array}{cc|c}2&1&1\\0&4&2\\0&\frac72&-\frac72\end{array}\right]
\xrightarrow{R_3-\frac78R_2}\left[\begin{array}{cc|c}2&1&1\\0&4&2\\0&0&-\frac{21}4\end{array}\right].
$$

The last row reads $0=-\tfrac{21}{4}$, so $\operatorname{rank}\mathbf A=2$, $\operatorname{rank}[\mathbf A|\mathbf b]=3$: no solution. The same conclusion by substitution: the first two equations give $y=\tfrac12$, $x=\tfrac14$, and then $3x+5y=\tfrac34+\tfrac52=\tfrac{13}4$, not $-2$.

### One inconsistent system, one unique solution (Specimen Test 18, Q2)

(i) $2x+y+z=3$ and $4x+2y+2z=5$. $R_2-2R_1$ gives $(0\ 0\ 0\,|\,-1)$, so $\operatorname{rank}\mathbf A=1$, $\operatorname{rank}[\mathbf A|\mathbf b]=2$: no solution. Twice the first equation says $4x+2y+2z=6$, which contradicts the second. Geometrically these are two parallel planes.

(ii) $2x+y=3$, $x+y=1$, $3x+4y=2$. Interchange the first two rows, then clear column 1 and column 2:

$$
\left[\begin{array}{cc|c}1&1&1\\2&1&3\\3&4&2\end{array}\right]
\xrightarrow[R_3-3R_1]{R_2-2R_1}\left[\begin{array}{cc|c}1&1&1\\0&-1&1\\0&1&-1\end{array}\right]
\xrightarrow{R_3+R_2}\left[\begin{array}{cc|c}1&1&1\\0&-1&1\\0&0&0\end{array}\right].
$$

Both ranks are $2=n$: a unique solution, $y=-1$ and $x=1-y=2$. The third equation is satisfied, $3(2)+4(-1)=2$.

## 4. Rank and linear independence (James §5.6, Example 5.39)

Vectors $\mathbf a_1,\dots,\mathbf a_q$ of order $p\times1$ are linearly dependent when $\alpha_1\mathbf a_1+\dots+\alpha_q\mathbf a_q=\mathbf0$ has a solution with the $\alpha_i$ not all zero. Put the vectors in the columns of the $p\times q$ matrix $\mathbf A=[\mathbf a_1,\dots,\mathbf a_q]$ and the coefficients in $\mathbf X=(\alpha_1,\dots,\alpha_q)^{\mathrm T}$; the condition becomes the homogeneous system $\mathbf A\mathbf X=\mathbf0$. By Section 3, the vectors are dependent when $q-\operatorname{rank}\mathbf A>0$ and independent when $\operatorname{rank}\mathbf A=q$. Since $\operatorname{rank}\mathbf A\le p$, any $p+1$ or more vectors with $p$ components are dependent, and for $p$ vectors with $p$ components the test is $|\mathbf A|\neq0$.

(a) $(1,2,3)^{\mathrm T}$ and $(2,3,1)^{\mathrm T}$:

$$
\begin{bmatrix}1&2\\2&3\\3&1\end{bmatrix}\xrightarrow[R_3-3R_1]{R_2-2R_1}\begin{bmatrix}1&2\\0&-1\\0&-5\end{bmatrix}\xrightarrow{R_3-5R_2}\begin{bmatrix}1&2\\0&-1\\0&0\end{bmatrix},
$$

rank $2=q$, so independent.

(b) Adding $(1,2,3)^{\mathrm T}$ and $(2,3,1)^{\mathrm T}$ gives $(3,5,4)^{\mathrm T}$, the third vector. In the matrix of the three vectors, column 3 is column 1 plus column 2, the determinant is zero and the rank is 2, so $q-\operatorname{rank}=1$ and the vectors are dependent.

(c) $(1,2,3)^{\mathrm T}$, $(2,3,4)^{\mathrm T}$, $(0,0,1)^{\mathrm T}$. Expanding down the third column,

$$
\begin{vmatrix}1&2&0\\2&3&0\\3&4&1\end{vmatrix}=1\cdot\begin{vmatrix}1&2\\2&3\end{vmatrix}=3-4=-1\neq0,
$$

so the vectors are independent.

(d) The three vectors of (c) plus $(0,2,1)^{\mathrm T}$ form a $3\times4$ matrix, whose rank is at most 3; it is exactly 3 because its last three columns have determinant

$$
\begin{vmatrix}2&0&0\\3&0&2\\4&1&1\end{vmatrix}=2\,(0\cdot1-2\cdot1)=-4\neq0 .
$$

So $q-\operatorname{rank}=4-3=1$ and the vectors are dependent. The dependence is $(0,2,1)^{\mathrm T}=4(1,2,3)^{\mathrm T}-2(2,3,4)^{\mathrm T}-3(0,0,1)^{\mathrm T}$: the components are $4-4-0=0$, $8-6-0=2$ and $12-8-3=1$.

## 5. The eigenvalue problem and the characteristic equation (James §5.7.1)

For a square $n\times n$ matrix $\mathbf A$, the **eigenvalue problem** is to find the scalars $\lambda$ for which

$$
\mathbf A\mathbf X=\lambda\mathbf X
$$

has a solution $\mathbf X\neq\mathbf0$. Such a $\lambda$ is an **eigenvalue** of $\mathbf A$, and the matching non-zero $\mathbf X$ is an **eigenvector**. The condition turns into a determinant in three moves. Write $\lambda\mathbf X=\lambda\mathbf I\mathbf X$ so that both sides contain a matrix times $\mathbf X$:

$$
\mathbf A\mathbf X=\lambda\mathbf I\mathbf X .
$$

Collect the terms on one side:

$$
(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0 .
$$

This is a homogeneous square system, and by Section 3 it has a non-trivial solution exactly when its matrix is singular:

$$
|\mathbf A-\lambda\mathbf I|=0 .
$$

This is the **characteristic equation**. Expanding the determinant gives a polynomial of degree $n$ in $\lambda$, the **characteristic polynomial**, so an $n\times n$ matrix has exactly $n$ eigenvalues counted with multiplicity (by the fundamental theorem of algebra); they may be real or complex and need not be distinct. The characteristic polynomial is also defined as $c(\lambda)=|\lambda\mathbf I-\mathbf A|$ (James), which makes the coefficient of $\lambda^n$ equal to $+1$. Multiplying each of the $n$ rows by $-1$ gives

$$
|\lambda\mathbf I-\mathbf A|=(-1)^n|\mathbf A-\lambda\mathbf I|,
$$

so the two forms have the same roots.

### The two-by-two case, trace and determinant

For $\mathbf A=\begin{bmatrix}a&b\\c&d\end{bmatrix}$,

$$
\begin{aligned}
|\mathbf A-\lambda\mathbf I|&=\begin{vmatrix}a-\lambda&b\\c&d-\lambda\end{vmatrix}\\
&=(a-\lambda)(d-\lambda)-bc\\
&=\lambda^2-(a+d)\lambda+(ad-bc)\\
&=\lambda^2-(\operatorname{tr}\mathbf A)\lambda+|\mathbf A| ,
\end{aligned}
$$

where the **trace** $\operatorname{tr}\mathbf A$ is the sum of the diagonal entries. If the roots are $\lambda_1,\lambda_2$ the quadratic is also $(\lambda-\lambda_1)(\lambda-\lambda_2)=\lambda^2-(\lambda_1+\lambda_2)\lambda+\lambda_1\lambda_2$, and comparing coefficients gives $\lambda_1+\lambda_2=\operatorname{tr}\mathbf A$ and $\lambda_1\lambda_2=|\mathbf A|$.

The same holds for any $n$. Since $|\mathbf A-\lambda\mathbf I|$ has roots $\lambda_1,\dots,\lambda_n$ and leading coefficient $(-1)^n$,

$$
|\mathbf A-\lambda\mathbf I|=(\lambda_1-\lambda)(\lambda_2-\lambda)\cdots(\lambda_n-\lambda).
$$

Setting $\lambda=0$ gives

$$
|\mathbf A|=\lambda_1\lambda_2\cdots\lambda_n .
$$

For the sum, compare the coefficients of $\lambda^{n-1}$. On the right it is $(-1)^{n-1}(\lambda_1+\dots+\lambda_n)$. On the left, every term of the determinant expansion other than the diagonal product $(a_{11}-\lambda)\cdots(a_{nn}-\lambda)$ leaves out at least two diagonal entries and so has degree at most $n-2$; the diagonal product contributes $(-1)^{n-1}(a_{11}+\dots+a_{nn})\lambda^{n-1}$. Hence

$$
\lambda_1+\lambda_2+\dots+\lambda_n=\operatorname{tr}\mathbf A .
$$

A triangular matrix needs no expansion at all. $\mathbf A-\lambda\mathbf I$ is still triangular, and the determinant of a triangular matrix is the product of its diagonal entries, so $|\mathbf A-\lambda\mathbf I|=(a_{11}-\lambda)\cdots(a_{nn}-\lambda)$ and the eigenvalues are the diagonal entries.

### A symmetric two-by-two (Example 5.40)

$$
\mathbf A=\begin{bmatrix}-2&1\\1&-2\end{bmatrix}:\qquad |\mathbf A-\lambda\mathbf I|=(-2-\lambda)^2-1=\lambda^2+4\lambda+3=(\lambda+1)(\lambda+3)=0,
$$

so $\lambda=-1$ and $\lambda=-3$. The sum $-4$ equals the trace, and the product $3$ equals $|\mathbf A|=4-1$.

### A three-by-three characteristic equation (Example 5.41)

$$
\mathbf A=\begin{bmatrix}1&1&-2\\-1&2&1\\0&1&-1\end{bmatrix}.
$$

Expand $|\mathbf A-\lambda\mathbf I|$ along the first row:

$$
\begin{aligned}
|\mathbf A-\lambda\mathbf I|&=\begin{vmatrix}1-\lambda&1&-2\\-1&2-\lambda&1\\0&1&-1-\lambda\end{vmatrix}\\
&=(1-\lambda)\big[(2-\lambda)(-1-\lambda)-1\big]-1\big[(-1)(-1-\lambda)-0\big]-2\big[(-1)(1)-0\big]\\
&=(1-\lambda)(\lambda^2-\lambda-3)-(1+\lambda)+2\\
&=(1-\lambda)(\lambda^2-\lambda-3)+(1-\lambda)\\
&=(1-\lambda)(\lambda^2-\lambda-2)\\
&=(1-\lambda)(\lambda-2)(\lambda+1).
\end{aligned}
$$

Multiplying out, $|\mathbf A-\lambda\mathbf I|=-(\lambda^3-2\lambda^2-\lambda+2)$, so the characteristic equation is

$$
\lambda^3-2\lambda^2-\lambda+2=0,
$$

with roots $\lambda=2,1,-1$. Expanding $|\lambda\mathbf I-\mathbf A|$ down the first column instead gives $c(\lambda)=(\lambda-1)\big[(\lambda-2)(\lambda+1)-1\big]-\big[2-(\lambda+1)\big]$ and the same cubic. For large matrices direct expansion has too many terms, and other methods are used.

> [!check] Trace and determinant of Example 5.41
> The roots $2+1+(-1)=2$ match $\operatorname{tr}\mathbf A=1+2-1=2$, and $2\cdot1\cdot(-1)=-2$ matches $|\mathbf A|=-2$ (the cubic $(1-\lambda)(\lambda-2)(\lambda+1)$ at $\lambda=0$ is $1\cdot(-2)\cdot1$). A wrong sign anywhere in the expansion almost always breaks one of these.

## 6. Eigenvectors (James §5.7.2)

For each eigenvalue $\lambda_i$, the eigenvectors are the non-zero solutions of

$$
(\mathbf A-\lambda_i\mathbf I)\mathbf e_i=\mathbf0 .
$$

Because $|\mathbf A-\lambda_i\mathbf I|=0$ the equations are dependent. When the eigenvalues are distinct the matrix $\mathbf A-\lambda_i\mathbf I$ has rank $n-1$, so there is exactly one free parameter: drop one equation, solve the others for the ratios of the components, and write the answer with an arbitrary constant. If $\mathbf e_i$ is a solution, so is $\beta\mathbf e_i$ for every scalar $\beta\neq0$, since $\mathbf A(\beta\mathbf e_i)=\beta\mathbf A\mathbf e_i=\lambda_i(\beta\mathbf e_i)$. Answers carry the constant, as in $\mathbf X=\alpha(1,0)^{\mathrm T}$.

> [!warning] An eigenvector is never zero, and is never unique
> $\mathbf X=\mathbf0$ satisfies $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ for every $\lambda$, so it carries no information and is excluded by definition. If elimination on $\mathbf A-\lambda\mathbf I$ forces every component to zero, the $\lambda$ used is not an eigenvalue: recheck the characteristic equation. Conversely, an answer such as $(3,2,1)^{\mathrm T}$ is one representative; $\beta(3,2,1)^{\mathrm T}$ is the full answer.

### Checking eigenvectors (Example 5.42)

For the matrix of Example 5.40,

$$
\begin{bmatrix}-2&1\\1&-2\end{bmatrix}\begin{bmatrix}1\\1\end{bmatrix}=\begin{bmatrix}-1\\-1\end{bmatrix}=-1\begin{bmatrix}1\\1\end{bmatrix},\qquad
\begin{bmatrix}-2&1\\1&-2\end{bmatrix}\begin{bmatrix}1\\-1\end{bmatrix}=\begin{bmatrix}-3\\3\end{bmatrix}=-3\begin{bmatrix}1\\-1\end{bmatrix},
$$

so $(1,1)^{\mathrm T}$ is an eigenvector for $\lambda=-1$ and $(1,-1)^{\mathrm T}$ for $\lambda=-3$. The same matrix describes two masses joined by three springs, and the two vectors are its in-phase and anti-phase modes ([[#8. Where eigenvalues appear in engineering]]).

### A full three-by-three eigenproblem (Example 5.44)

For $\mathbf A$ of Example 5.41, row and column operations can factorise $|\mathbf A-\lambda\mathbf I|$ directly, without expanding. Adding column 1 to column 3 makes a common factor $-(1+\lambda)$ appear in the third column:

$$
\begin{vmatrix}1-\lambda&1&-2\\-1&2-\lambda&1\\0&1&-1-\lambda\end{vmatrix}
=\begin{vmatrix}1-\lambda&1&-1-\lambda\\-1&2-\lambda&0\\0&1&-1-\lambda\end{vmatrix}
=-(1+\lambda)\begin{vmatrix}1-\lambda&1&1\\-1&2-\lambda&0\\0&1&1\end{vmatrix}.
$$

Subtracting row 3 from row 1 makes the matrix lower triangular:

$$
-(1+\lambda)\begin{vmatrix}1-\lambda&0&0\\-1&2-\lambda&0\\0&1&1\end{vmatrix}=-(1+\lambda)(1-\lambda)(2-\lambda).
$$

Taken in decreasing order, the eigenvalues are $\lambda_1=2$, $\lambda_2=1$, $\lambda_3=-1$.

For $\lambda_1=2$, $(\mathbf A-2\mathbf I)\mathbf e_1=\mathbf0$ reads

$$
\begin{bmatrix}-1&1&-2\\-1&0&1\\0&1&-3\end{bmatrix}\begin{bmatrix}e_{11}\\e_{12}\\e_{13}\end{bmatrix}=\mathbf0:\qquad
\begin{aligned}-e_{11}+e_{12}-2e_{13}&=0,\\-e_{11}+e_{13}&=0,\\e_{12}-3e_{13}&=0.\end{aligned}
$$

Choose $e_{13}=\beta_1$. The third equation gives $e_{12}=3\beta_1$ and the second gives $e_{11}=\beta_1$; the first, $-\beta_1+3\beta_1-2\beta_1=0$, is then automatic. So $\mathbf e_1=\beta_1(1,3,1)^{\mathrm T}$, and the check is

$$
\mathbf A\begin{bmatrix}1\\3\\1\end{bmatrix}=\begin{bmatrix}1+3-2\\-1+6+1\\0+3-1\end{bmatrix}=\begin{bmatrix}2\\6\\2\end{bmatrix}=2\begin{bmatrix}1\\3\\1\end{bmatrix}.
$$

For $\lambda_2=1$, $\mathbf A-\mathbf I$ has rows $(0,1,-2)$, $(-1,1,1)$, $(0,1,-2)$, so $e_{22}=2e_{23}$ and $e_{21}=e_{22}+e_{23}=3e_{23}$. With $e_{23}=\beta_2$, $\mathbf e_2=\beta_2(3,2,1)^{\mathrm T}$, and $\mathbf A(3,2,1)^{\mathrm T}=(3+2-2,\ -3+4+1,\ 0+2-1)^{\mathrm T}=(3,2,1)^{\mathrm T}$.

For $\lambda_3=-1$, $\mathbf A+\mathbf I$ has rows $(2,1,-2)$, $(-1,3,1)$, $(0,1,0)$. The third row gives $e_{32}=0$, and then the first gives $e_{31}=e_{33}$. So $\mathbf e_3=\beta_3(1,0,1)^{\mathrm T}$, and $\mathbf A(1,0,1)^{\mathrm T}=(-1,0,-1)^{\mathrm T}=-(1,0,1)^{\mathrm T}$.

### A rotation has complex eigenvalues (Example 5.43)

$$
\mathbf A=\begin{bmatrix}0&-1\\1&0\end{bmatrix}
$$

rotates every vector by $90^\circ$ anticlockwise: $(1,0)^{\mathrm T}\mapsto(0,1)^{\mathrm T}$. No real direction survives a quarter turn, so no real eigenvector can exist, and the algebra agrees:

$$
|\mathbf A-\lambda\mathbf I|=\begin{vmatrix}-\lambda&-1\\1&-\lambda\end{vmatrix}=\lambda^2+1=0\quad\Rightarrow\quad\lambda=\pm\mathrm j .
$$

For $\lambda=\mathrm j$, the first row of $(\mathbf A-\mathrm j\mathbf I)\mathbf X=\mathbf0$ is $-\mathrm jx-y=0$, so $y=-\mathrm jx$ and $\mathbf X\propto(1,-\mathrm j)^{\mathrm T}$. Multiplying by $\mathrm j$ gives the neater form $\mathbf X=A(\mathrm j,1)^{\mathrm T}$; check: $\mathbf A(\mathrm j,1)^{\mathrm T}=(-1,\mathrm j)^{\mathrm T}=\mathrm j(\mathrm j,1)^{\mathrm T}$. For $\lambda=-\mathrm j$, $\mathrm jx-y=0$ gives $y=\mathrm jx$ and $\mathbf X=B(1,\mathrm j)^{\mathrm T}$, with $A$ and $B$ arbitrary non-zero constants. In general eigenvalues are complex; the other examples in this module are built to have real ones.

### Triangular matrices (Booklet Exercise A(i) and (ii))

(i) $\begin{pmatrix}5&1\\0&4\end{pmatrix}$ is upper triangular, so $\lambda=5,4$.

- $\lambda=5$: $\begin{pmatrix}0&1\\0&-1\end{pmatrix}\mathbf X=\mathbf0$ gives $y=0$, so $\mathbf X=\alpha(1,0)^{\mathrm T}$.
- $\lambda=4$: $\begin{pmatrix}1&1\\0&0\end{pmatrix}\mathbf X=\mathbf0$ gives $x+y=0$, so $\mathbf X=\beta(1,-1)^{\mathrm T}$.

(ii) $\begin{pmatrix}1&0&0\\0&3&0\\0&2&4\end{pmatrix}$ is lower triangular, so $\lambda=1,3,4$.

- $\lambda=1$: the rows of $\mathbf A-\mathbf I$ give $2y=0$ and $2y+3z=0$, so $y=z=0$ and $\mathbf X=\alpha(1,0,0)^{\mathrm T}$.
- $\lambda=3$: $-2x=0$ and $2y+z=0$, so $\mathbf X=\beta(0,1,-2)^{\mathrm T}$.
- $\lambda=4$: $-3x=0$ and $-y=0$, so $\mathbf X=\gamma(0,0,1)^{\mathrm T}$.

The two eigenvector directions of (i) are at $45^\circ$ to each other, not $90^\circ$: a non-symmetric matrix has no reason to have orthogonal eigenvectors.

![[m1054_m18_eigen_directions.png|900]]

*Unit vectors (dashed) and their images under $\mathbf A$ (solid). (a) For Booklet Exercise A(i), $(1,0)^{\mathrm T}$ is stretched by 5 and $(-1,1)^{\mathrm T}/\sqrt2$ by 4 without turning, while $(0,1)^{\mathrm T}$ and $(1,1)^{\mathrm T}/\sqrt2$ are turned as well as stretched. (b) For Example 5.40, $\mathbf A$ reverses $\mathbf e_1$ and reverses and triples $\mathbf e_2$; the eigenvectors are perpendicular and lie along the axes of the image ellipse.*

> [!tip] Eigenvectors are the directions a matrix does not turn
> Under a $2\times2$ matrix the unit circle becomes an ellipse, and almost every vector changes direction. An eigenvector is a direction that maps onto its own line, scaled by $\lambda$; a negative $\lambda$ reverses it along that line. The picture explains why a rotation has no real eigenvalue and why the eigenvectors of a symmetric matrix are the axes of the ellipse.

### Normalising eigenvectors

Since each eigenvector is fixed only up to a scale factor, a convention is sometimes imposed. The **normalised** eigenvector divides by the length,

$$
\hat{\mathbf e}=\frac{\mathbf e}{|\mathbf e|},\qquad |\mathbf e|=\sqrt{e_1^2+e_2^2+\dots+e_n^2},
$$

which fixes it up to a factor $\pm1$. For Example 5.44, $|(1,3,1)|=\sqrt{11}$, $|(3,2,1)|=\sqrt{14}$ and $|(1,0,1)|=\sqrt2$, so

$$
\hat{\mathbf e}_1=\Big(\tfrac1{\sqrt{11}},\tfrac3{\sqrt{11}},\tfrac1{\sqrt{11}}\Big)^{\mathrm T},\qquad
\hat{\mathbf e}_2=\Big(\tfrac3{\sqrt{14}},\tfrac2{\sqrt{14}},\tfrac1{\sqrt{14}}\Big)^{\mathrm T},\qquad
\hat{\mathbf e}_3=\Big(\tfrac1{\sqrt2},0,\tfrac1{\sqrt2}\Big)^{\mathrm T}.
$$

Otherwise the simplest integer form, $\beta_i=1$, is the usual way to quote them.

### Distinct eigenvalues give independent eigenvectors

The three eigenvectors of Example 5.44 are linearly independent, since by Section 4 the matrix with them as columns has

$$
\begin{vmatrix}1&3&1\\3&2&0\\1&1&1\end{vmatrix}=1(2-0)-3(3-0)+1(3-2)=-6\neq0 .
$$

This holds generally: an $n\times n$ matrix with $n$ distinct eigenvalues has $n$ linearly independent eigenvectors. For two of them, suppose $c_1\mathbf e_1+c_2\mathbf e_2=\mathbf0$ with $\lambda_1\neq\lambda_2$. Multiplying by $\mathbf A$ gives

$$
c_1\lambda_1\mathbf e_1+c_2\lambda_2\mathbf e_2=\mathbf0 .
$$

Subtract $\lambda_2$ times the original relation:

$$
c_1(\lambda_1-\lambda_2)\mathbf e_1=\mathbf0 .
$$

Since $\lambda_1\neq\lambda_2$ and $\mathbf e_1\neq\mathbf0$, $c_1=0$, and then $c_2\mathbf e_2=\mathbf0$ gives $c_2=0$. The same step, applied repeatedly, removes one vector at a time for any $n$.

## 7. Symmetric matrices (James §5.7.7)

A square matrix is **symmetric** if $\mathbf A^{\mathrm T}=\mathbf A$. Real symmetric matrices occur constantly (stiffness and mass matrices, stress tensors, inertia tensors), and they have two properties that make their eigenproblems especially clean: their eigenvalues are real, and eigenvectors belonging to different eigenvalues are orthogonal, $\mathbf e_i^{\mathrm T}\mathbf e_j=0$ for $i\neq j$. An $n\times n$ real symmetric matrix also always has $n$ mutually orthogonal eigenvectors, even with repeated eigenvalues, though repeated roots are outside this module.

The eigenvalues are real. Let $\mathbf A\mathbf X=\lambda\mathbf X$, allowing $\lambda$ and $\mathbf X$ to be complex, and write a bar for the complex conjugate. Conjugating, and using that $\mathbf A$ is real,

$$
\mathbf A\bar{\mathbf X}=\bar\lambda\bar{\mathbf X}.
$$

Transposing the original equation and using $\mathbf A^{\mathrm T}=\mathbf A$,

$$
\mathbf X^{\mathrm T}\mathbf A=\lambda\mathbf X^{\mathrm T}.
$$

Pre-multiply the conjugated equation by $\mathbf X^{\mathrm T}$ and replace $\mathbf X^{\mathrm T}\mathbf A$ by $\lambda\mathbf X^{\mathrm T}$:

$$
\begin{aligned}
\mathbf X^{\mathrm T}\mathbf A\bar{\mathbf X}&=\bar\lambda\,\mathbf X^{\mathrm T}\bar{\mathbf X},\\
\lambda\,\mathbf X^{\mathrm T}\bar{\mathbf X}&=\bar\lambda\,\mathbf X^{\mathrm T}\bar{\mathbf X}.
\end{aligned}
$$

Now $\mathbf X^{\mathrm T}\bar{\mathbf X}=|x_1|^2+\dots+|x_n|^2>0$ because $\mathbf X\neq\mathbf0$, so $\lambda=\bar\lambda$ and $\lambda$ is real.

Eigenvectors of different eigenvalues are orthogonal. Let $\mathbf A\mathbf e_1=\lambda_1\mathbf e_1$ and $\mathbf A\mathbf e_2=\lambda_2\mathbf e_2$ with $\lambda_1\neq\lambda_2$. Evaluate $\mathbf e_2^{\mathrm T}\mathbf A\mathbf e_1$ in two ways. Using the first equation,

$$
\mathbf e_2^{\mathrm T}\mathbf A\mathbf e_1=\lambda_1\,\mathbf e_2^{\mathrm T}\mathbf e_1 .
$$

Using $\mathbf A=\mathbf A^{\mathrm T}$ and the second equation,

$$
\mathbf e_2^{\mathrm T}\mathbf A\mathbf e_1=(\mathbf A^{\mathrm T}\mathbf e_2)^{\mathrm T}\mathbf e_1=(\mathbf A\mathbf e_2)^{\mathrm T}\mathbf e_1=\lambda_2\,\mathbf e_2^{\mathrm T}\mathbf e_1 .
$$

Subtracting, $(\lambda_1-\lambda_2)\,\mathbf e_2^{\mathrm T}\mathbf e_1=0$, and since $\lambda_1\neq\lambda_2$, $\mathbf e_2^{\mathrm T}\mathbf e_1=0$. If the eigenvectors are also normalised they form an orthonormal set, $\hat{\mathbf e}_i^{\mathrm T}\hat{\mathbf e}_j=\delta_{ij}$, with $\delta_{ij}$ the Kronecker delta.

| Matrix type | Eigenvalues and eigenvectors |
|---|---|
| real symmetric, e.g. Example 5.40, Booklet A(iii) | real eigenvalues; orthogonal eigenvectors |
| rotation $\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ (Example 5.43) | complex $\pm\mathrm j$: no real direction is preserved |
| triangular, e.g. Booklet A(i), A(ii) | eigenvalues are the diagonal entries |

### A symmetric three-by-three (Booklet Exercise A(iii))

$$
\mathbf A=\begin{pmatrix}-3&1&-1\\1&-5&1\\-1&1&-3\end{pmatrix}.
$$

Expand along the first row:

$$
\begin{aligned}
|\mathbf A-\lambda\mathbf I|&=(-3-\lambda)\big[(-5-\lambda)(-3-\lambda)-1\big]-1\big[(1)(-3-\lambda)-(1)(-1)\big]+(-1)\big[(1)(1)-(-5-\lambda)(-1)\big]\\
&=-(\lambda+3)\big[(\lambda+5)(\lambda+3)-1\big]-\big[-(3+\lambda)+1\big]-\big[1-(5+\lambda)\big]\\
&=-(\lambda+3)(\lambda^2+8\lambda+14)+(\lambda+2)+(\lambda+4)\\
&=-(\lambda^3+11\lambda^2+38\lambda+42)+2\lambda+6\\
&=-(\lambda^3+11\lambda^2+36\lambda+36)\\
&=-(\lambda+2)(\lambda+3)(\lambda+6).
\end{aligned}
$$

So $\lambda=-2,-3,-6$. They sum to $-11=\operatorname{tr}\mathbf A$ and multiply to $-36=|\mathbf A|$.

| $\lambda$ | Two independent equations from $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ | Eigenvector |
|---|---|---|
| $-2$ | $-x+y-z=0$, $x-3y+z=0$; adding gives $y=0$, then $z=-x$ | $\alpha(1,0,-1)^{\mathrm T}$ |
| $-3$ | $y-z=0$, $x-2y+z=0$; so $z=y$ and $x=y$ | $\beta(1,1,1)^{\mathrm T}$ |
| $-6$ | $3x+y-z=0$, $x+y+z=0$; subtracting gives $z=x$, then $y=-2x$ | $\gamma(1,-2,1)^{\mathrm T}$ |

The three are mutually orthogonal: $(1,0,-1)\cdot(1,1,1)=0$, $(1,0,-1)\cdot(1,-2,1)=0$ and $(1,1,1)\cdot(1,-2,1)=0$, as the theorem requires.

### Eigenvalues of a symmetric matrix (Specimen Test 18, Q3)

$$
\mathbf A=\begin{pmatrix}3&0&1\\0&3&1\\1&1&2\end{pmatrix}.
$$

Expand along the first row; the middle term vanishes because the $(1,2)$ entry is zero:

$$
\begin{aligned}
|\mathbf A-\lambda\mathbf I|&=(3-\lambda)\big[(3-\lambda)(2-\lambda)-1\big]+1\big[0\cdot1-(3-\lambda)\cdot1\big]\\
&=(3-\lambda)\big[(3-\lambda)(2-\lambda)-1-1\big]\\
&=(3-\lambda)(\lambda^2-5\lambda+4)\\
&=(3-\lambda)(\lambda-1)(\lambda-4).
\end{aligned}
$$

| $\lambda$ | Equations | Eigenvector |
|---|---|---|
| $1$ | $2x+z=0$, $2y+z=0$ | $\alpha(1,1,-2)^{\mathrm T}$ |
| $3$ | $z=0$, $x+y=0$ | $\beta(1,-1,0)^{\mathrm T}$ |
| $4$ | $-x+z=0$, $-y+z=0$ | $\gamma(1,1,1)^{\mathrm T}$ |

> [!check] Specimen Test 18, Q3
> The eigenvalues sum to $1+3+4=8=\operatorname{tr}\mathbf A$ and multiply to $12=|\mathbf A|$. The eigenvectors are mutually orthogonal, $(1,1,-2)\cdot(1,-1,0)=0$, $(1,1,-2)\cdot(1,1,1)=0$, $(1,-1,0)\cdot(1,1,1)=0$, as they must be for a symmetric matrix; a numerical eigen-solver gives the same eigenvalues $1,3,4$ and an orthonormal set of eigenvectors.

## 8. Where eigenvalues appear in engineering

Two equal masses $m$ on a smooth line are joined to each other and to two fixed walls by three equal springs of stiffness $k$. With displacements $x_1,x_2$, the middle spring stretches by $x_2-x_1$, so Newton's second law gives

$$
\begin{aligned}
m\ddot x_1&=-kx_1+k(x_2-x_1)=-2kx_1+kx_2,\\
m\ddot x_2&=-k(x_2-x_1)-kx_2=kx_1-2kx_2,
\end{aligned}
$$

that is, $\ddot{\mathbf x}=\dfrac km\mathbf A\mathbf x$ with $\mathbf A$ the matrix of Example 5.40. A solution in which both masses move at one frequency, $\mathbf x=\mathbf X\cos\omega t$, needs

$$
-\omega^2\mathbf X=\frac km\mathbf A\mathbf X
\quad\Longleftrightarrow\quad
\mathbf A\mathbf X=-\frac{m\omega^2}{k}\mathbf X,
$$

an eigenvalue problem with $\lambda=-m\omega^2/k$. The eigenvalue $\lambda=-1$ gives $\omega=\sqrt{k/m}$ with $\mathbf X=(1,1)^{\mathrm T}$, the masses moving together (in phase, middle spring unstretched); $\lambda=-3$ gives $\omega=\sqrt{3k/m}$ with $\mathbf X=(1,-1)^{\mathrm T}$, the masses moving in opposition (anti-phase). The eigenvalues fix the natural frequencies and the eigenvectors are the mode shapes; Year 2 writes the same problem as $\mathbf M\ddot{\mathbf x}+\mathbf K\mathbf x=\mathbf0$ ([[Natural Frequencies and Mode Shapes]]).

For a linear dynamic system $\dot{\mathbf x}=\mathbf A\mathbf x$ the eigenvalues of the state matrix are the system poles: each mode grows or decays like $e^{\lambda t}$, so the system is stable when every eigenvalue has negative real part ([[State-Space Representation]], [[Characteristic Equation and Eigenvalues]]). In solid mechanics the stress tensor is symmetric, so by Section 7 its eigenvalues, the principal stresses, are real and its eigenvectors, the principal directions, are perpendicular ([[Principal Stresses]]).

## Terminology and alternative names

| Here | Also called |
|---|---|
| eigenvalue | latent root, characteristic root, proper root (James, older usage) |
| eigenvector | latent vector, characteristic vector, proper vector |
| underspecified / overspecified system | under-determined / over-determined system |
| augmented matrix $[\mathbf A\vert\mathbf b]$ | $(\mathbf A:\mathbf b)$ in James |
| characteristic equation $\vert\mathbf A-\lambda\mathbf I\vert=0$ | $c(\lambda)=\vert\lambda\mathbf I-\mathbf A\vert=0$ in James; same roots |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M18 Solutions - Matrices III]]
- Previous: [[MATH1054 M17 - Matrices II]] (determinants, inverse, Gaussian elimination) · Next: [[MATH1054 M20 - Further Calculus II]]
- Concepts: [[Rank and Consistency of Linear Systems]] · [[Eigenvalues and Eigenvectors]] · [[Gaussian Elimination]] · [[Determinants and Cofactors]] · [[Matrix Inverse]]
- Year 1 applications: [[Principal Stresses]] and [[Mohr's Circle]] (FEEG1002); the number of independent dimensionless groups in [[Buckingham Pi Theorem]] (SESA1016) is the number of variables minus the rank of the dimensional matrix (James Exercise 91).
- Year 2: [[Characteristic Equation and Eigenvalues]] and [[State-Space Representation]] (SESA2027); [[Natural Frequencies and Mode Shapes]] (SESA2029); [[ODE Eigenvalue Problems]] (MATH2048), the function-space analogue, where eigenfunctions of different eigenvalues are orthogonal for the same reason as in Section 7.
- Year 3: [[Eigenvalue Decomposition]], [[Matrix Exponential and Modal Solution]] and [[Principal Axes of Inertia]] (SESA3047); [[Method of Characteristics]] (SESA3029), whose characteristic directions are eigen-directions of the coefficient matrix.

## Sources

- MATH1054 Module Booklet, Module 18 (booklet PDF pp. 67–69): work scheme items 1–7 and Exercise A, Specimen Test 18.
- James, *Modern Engineering Mathematics* (6th ed.): §5.6 Rank, pp. 376–386 (system (5.30), Examples 5.37–5.39, Figure 5.19, Exercises 88 and 90); §5.7 introduction, §5.7.1 The characteristic equation and §5.7.2 Eigenvalues and eigenvectors, pp. 387–394 (Examples 5.40–5.44, normalisation); §5.7.7 Symmetric matrices, p. 404.
- Worked solutions to every set item: [[MATH1054 M18 Solutions - Matrices III]].

## Self-study tasks

### Core

- [ ] Exercise 88(a), (b) on p. 386 (Module 18 work scheme, item 3): echelon form, rank and solution. Answers: $(\alpha-2,5-2\alpha,\alpha)$; no solution. → [[#Infinitely many solutions (Exercise 88(a))]] · [[MATH1054 M18 Solutions - Matrices III#Exercise 88: Echelon form, rank and solution|solution]]
- [ ] Exercise 90(a), (b) on p. 386 (Module 18 work scheme, item 3): non-square systems. Answers: $x=-1$, $y=\tfrac{2-4\alpha}3$, $z=\alpha$; no solution. → [[MATH1054 M18 Solutions - Matrices III#Exercise 90: Non-square systems]]
- [ ] Booklet Exercise A(i)–(iii) (Module 18 work scheme, item 7): eigenvalues $5,4$; $1,3,4$; $-2,-3,-6$ with orthogonal eigenvectors. → [[MATH1054 M18 Solutions - Matrices III#Booklet Exercise A: Eigenvalues and eigenvectors]]
- [ ] Example 5.44 (Module 18 work scheme, item 5): eigenvalues $2,1,-1$ and eigenvectors $(1,3,1)$, $(3,2,1)$, $(1,0,1)$, by expansion and by James's column operation. → [[#A full three-by-three eigenproblem (Example 5.44)]] · [[MATH1054 M18 Solutions - Matrices III#Example 5.44: Eigenvectors for Example 5.41|solution]]
- [ ] Specimen Test 18, Q1–Q3, timed. Answers: rank 3; (i) no solution, (ii) $x=2$, $y=-1$; $\lambda=1,3,4$ with $(1,1,-2)$, $(1,-1,0)$, $(1,1,1)$. → [[MATH1054 M18 Solutions - Matrices III#Part C: Specimen Test 18]]

### Further practice

- [ ] Example 5.37(a)–(c) (Module 18 work scheme, item 1): ranks 2, 1, 3. → [[MATH1054 M18 Solutions - Matrices III#Example 5.37: Rank]]
- [ ] Example 5.38(a), (b) (Module 18 work scheme, item 2), with and without partial pivoting. → [[MATH1054 M18 Solutions - Matrices III#Example 5.38: Echelon form, rank and solutions]]
- [ ] Example 5.39(a)–(d) (Module 18 work scheme, item 3, the remainder of §5.6): linear independence by rank. → [[#4. Rank and linear independence (James §5.6, Example 5.39)]]
- [ ] Examples 5.40–5.43 (Module 18 work scheme, items 4–5), including the complex eigenvectors $A(\mathrm j,1)^{\mathrm T}$, $B(1,\mathrm j)^{\mathrm T}$ of the rotation. → [[#A rotation has complex eigenvalues (Example 5.43)]] · [[MATH1054 M18 Solutions - Matrices III#Example 5.42: Verify the eigenvectors]]
- [ ] Normalise the eigenvectors of Example 5.44 and check $|\mathbf P|=-6$ for the matrix of eigenvectors (Module 18 work scheme, item 6). → [[#Normalising eigenvectors]]

## Transcript and slide slips

These are misprints in James that affect the worked examples above; none changes a final answer.

| Where | James prints | Correct |
|---|---|---|
| [[#4. Rank and linear independence (James §5.6, Example 5.39)]], p. 385, Example 5.39(c) | the matrix of vectors as $\mathbf C$ with third row $(3,1,1)$ | third row $(3,4,1)$, from the vectors $(1,2,3)$, $(2,3,4)$, $(0,0,1)$; both determinants happen to be $-1$ |
| same, Example 5.39(d) | $[q-\operatorname{rank}(\mathbf C)]=1$ | $q-\operatorname{rank}(\mathbf D)=1$ |
| [[#Checking eigenvectors (Example 5.42)]], p. 390 | "an eigenvector corresponding to the eigenvector $-1$" (and $-3$) | eigenvalue $-1$ (and $-3$) |
| [[#Distinct eigenvalues give independent eigenvectors]], p. 394 | "the three eigenvalues in Example 5.44 are linearly independent" | the three eigenvectors |
