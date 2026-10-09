---
title: "MATH1054 M17 Solutions - Matrices II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 4: Vectors and Matrices"
tags:
  - math1054
  - tutorial-solutions
  - matrices
  - linear-systems
sheet: "Specimen Test 17 (booklet) + Module 17 work scheme: Examples 5.22–5.36; Exercises 51, 63, 64, 73; Booklet Exercises A, B"
theory_notes: ["[[MATH1054 M17 - Matrices II]]"]
key_concepts: ["[[Matrix Inverse]]", "[[Gaussian Elimination]]"]
status: complete
sources: ["tmp/md/module_17_matrices_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§5.4–5.5)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 17)"]
---

# MATH1054 M17 Solutions - Matrices II

> [!abstract] Sheet Info
> The whole Module 17 work scheme. Inverses, determinants, null spaces and solutions were checked with SymPy (`inv`, `det`, `nullspace`, `linsolve`), and every elimination sequence was traced by hand.
>
> **Terminology** (booklet):
> - The **direct** (cofactor) method is $\mathbf A^{-1}=\dfrac{\operatorname{adj}\mathbf A}{|\mathbf A|}$.
> - The **elimination** method row-reduces $[\mathbf A\,|\,\mathbf I]\to[\mathbf I\,|\,\mathbf A^{-1}]$.

## Theory Links
- [[MATH1054 M17 - Matrices II]] · [[Matrix Inverse]] · [[Gaussian Elimination]] · [[Determinants and Cofactors]]

---

# Part A: Worked examples

## Example 5.22: Inverses by the cofactor method
**(a)** $\mathbf A=\begin{bmatrix}1&2\\2&3\end{bmatrix}$ has $|\mathbf A|=3-4=-1$. For a $2\times2$, swap the diagonal and negate the off-diagonal:

$$\mathbf A^{-1}=\frac1{-1}\begin{bmatrix}3&-2\\-2&1\end{bmatrix}=\boxed{\begin{bmatrix}-3&2\\2&-1\end{bmatrix}}$$

**(b)** $\mathbf B=\begin{bmatrix}5&2&4\\3&-1&2\\1&4&-3\end{bmatrix}$ has $|\mathbf B|=5(3-8)-2(-9-2)+4(12+1)=-25+22+52=49$. The cofactors give

$$\operatorname{adj}\mathbf B=\begin{bmatrix}-5&22&8\\11&-19&2\\13&-18&-11\end{bmatrix},\qquad\mathbf B^{-1}=\boxed{\frac1{49}\begin{bmatrix}-5&22&8\\11&-19&2\\13&-18&-11\end{bmatrix}}$$

**Check**: row 1 of $\mathbf B$ times column 1 of $\operatorname{adj}\mathbf B$ is $5(-5)+2(11)+4(13)=49$ ✔.

## Example 5.23: $(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}$
- $\mathbf{AB}=\begin{bmatrix}2&3\\1&3\end{bmatrix}$, with $|\mathbf{AB}|=3$, so $(\mathbf{AB})^{-1}=\frac13\begin{bmatrix}3&-3\\-1&2\end{bmatrix}=\begin{bmatrix}1&-1\\-\frac13&\frac23\end{bmatrix}$.
- $\mathbf A^{-1}=-\frac13\begin{bmatrix}1&-2\\-2&1\end{bmatrix}$ and $\mathbf B^{-1}=\begin{bmatrix}-1&1\\1&0\end{bmatrix}$.
- $\mathbf B^{-1}\mathbf A^{-1}=\begin{bmatrix}1&-1\\-\frac13&\frac23\end{bmatrix}=(\mathbf{AB})^{-1}$ ✔
- $\mathbf A^{-1}\mathbf B^{-1}=\begin{bmatrix}1&-\frac13\\-1&\frac23\end{bmatrix}$ is **different**. The order reverses, like taking off your socks and shoes.

## Example 5.25: Do solutions exist?
Write each system as $\mathbf{AX}=\mathbf b$.

| | $\lvert\mathbf A\rvert$ | $\mathbf b$ | Outcome |
|---|---|---|---|
| (a) $\begin{smallmatrix}2&1\\1&-2\end{smallmatrix}$ | $-5\neq0$ | $(5,-5)$ | **unique**: $x=1$, $y=3$ |
| (b) same matrix | $-5$ | $\mathbf0$ | only the **trivial** solution, $x=y=0$ |
| (c) $\begin{smallmatrix}-3&6\\1&-2\end{smallmatrix}$ | $0$ | $(15,-5)$ | equation 1 is $-3\times$ equation 2, so they are **consistent**: **infinitely many**, $x=2y-5$ |
| (d) same matrix | $0$ | $(10,-5)$ | $-3\times(-5)=15\neq10$, so **inconsistent: no solution** |
| (e) same matrix | $0$ | $\mathbf0$ | **infinitely many** non-trivial solutions: $x=2y$ |

## Example 5.26

$$x+y+z=6,\quad x+2y+3z=14,\quad x+4y+9z=36$$

- $R_2-R_1$: $y+2z=8$.
- $R_3-R_1$: $3y+8z=30$.
- Subtract 3 times the first new equation from the second: $2z=6$, so $z=3$. Then $y=2$ and $x=1$.

$$\boxed{(x,y,z)=(1,2,3)}$$

Here $|\mathbf A|=2\neq0$, so the solution is unique.

## Example 5.27: Find $k$ for a non-trivial solution
A homogeneous system has non-trivial solutions iff $|\mathbf A|=0$:

$$\begin{vmatrix}1&5&3\\5&1&-k\\1&2&k\end{vmatrix}=1(k+2k)-5(5k+k)+3(10-1)=27-27k=0\ \Rightarrow\ \boxed{k=1}$$

With $k=1$, the solution is $(x,y,z)=\alpha(1,-2,3)$. Check equation 1: $1-10+9=0$ ✔.

## Example 5.28: Values of $\lambda$ with $(\mathbf A-\lambda\mathbf I)\mathbf X=\mathbf0$ non-trivial

$$\begin{vmatrix}3-\lambda&1\\-2&-\lambda\end{vmatrix}=\lambda^2-3\lambda+2=(\lambda-1)(\lambda-2)=0$$

- $\lambda=1$: $2x+y=0$, so $\mathbf X=\alpha\begin{bmatrix}1\\-2\end{bmatrix}$.
- $\lambda=2$: $x+y=0$, so $\mathbf X=\beta\begin{bmatrix}1\\-1\end{bmatrix}$.

This is the **eigenvalue problem**, continued in [[MATH1054 M18 - Matrices III|M18]].

## Example 5.31: Elimination

$$\left[\begin{array}{ccc|c}1&2&3&10\\-1&1&1&0\\0&1&-1&1\end{array}\right]\xrightarrow{R_2+R_1}\left[\begin{array}{ccc|c}1&2&3&10\\0&3&4&10\\0&1&-1&1\end{array}\right]\xrightarrow{R_3-\frac13R_2}\left[\begin{array}{ccc|c}1&2&3&10\\0&3&4&10\\0&0&-\frac73&-\frac73\end{array}\right]$$

**Back substitution**: $z=1$; then $3y=10-4$, so $y=2$; then $x=10-4-3=3$.

$$\boxed{(3,2,1)}$$

## Example 5.33

$$\left[\begin{array}{ccc|c}2&3&4&1\\1&2&3&1\\1&4&5&2\end{array}\right]\xrightarrow[R_3-\frac12R_1]{R_2-\frac12R_1}\left[\begin{array}{ccc|c}2&3&4&1\\0&\frac12&1&\frac12\\0&\frac52&3&\frac32\end{array}\right]\xrightarrow{R_3-5R_2}\left[\begin{array}{ccc|c}2&3&4&1\\0&\frac12&1&\frac12\\0&0&-2&-1\end{array}\right]$$

**Back substitution**: $z=\frac12$; then $\frac12y=\frac12-\frac12=0$, so $y=0$; then $2x=1-2$, so $x=-\frac12$.

$$\boxed{(x,y,z)=\big(-\tfrac12,0,\tfrac12\big)}$$

## Example 5.34: A $4\times4$ system
Row operations:
- $R_2-2R_1$ gives $(0,-3,-5,-1\,|\,-7)$.
- $R_3-R_1$ gives $(0,0,-2,-1\,|\,-1)$.
- $R_4+\frac13R_2$ gives $(0,0,-\frac23,\frac53\,|\,-\frac73)$.
- Then $R_4-\frac13R_3$ gives $(0,0,0,2\,|\,-2)$.

**Back substitution**:
- $t=-1$
- $-2z+1=-1$, so $z=1$
- $-3y-5+1=-7$, so $y=1$
- $x=5-2-3+1=1$

$$\boxed{(x,y,z,t)=(1,1,1,-1)}$$

## Example 5.36: Ill-conditioning
Solve $\begin{bmatrix}2&1\\1&0.5001\end{bmatrix}\mathbf X=\begin{bmatrix}0.3\\0.6\end{bmatrix}$, and the same system with $0.4999$.

$R_2-\frac12R_1$ leaves $(0.5001-0.5)\,y=0.6-0.15$, i.e. $\pm0.0001\,y=0.45$.

| | $y$ | $x=\frac{0.3-y}{2}$ |
|---|---|---|
| (a) $0.5001$ | $4500$ | $-2249.85$ |
| (b) $0.4999$ | $-4500$ | $2250.15$ |

A change of $0.0002$ in **one coefficient** flips the solution completely. The rows are almost parallel ($|\mathbf A|=\pm0.0002\approx0$), so the system is **ill-conditioned**. Rounding errors in such systems are catastrophic, which is why partial pivoting and condition numbers matter numerically.

---

# Part B: Assigned exercises

## Exercise 51: Singular or non-singular? Find the inverses
**(a)** $\begin{bmatrix}1&2\\2&1\end{bmatrix}$: $|\cdot|=-3$, non-singular.

$$\mathbf A^{-1}=-\frac13\begin{bmatrix}1&-2\\-2&1\end{bmatrix}=\begin{bmatrix}-\frac13&\frac23\\\frac23&-\frac13\end{bmatrix}$$

**(b)** $\begin{bmatrix}1&2&3\\2&2&1\\5&6&5\end{bmatrix}$: $|\cdot|=1(10-6)-2(10-5)+3(12-10)=0$, so it is **singular**. Indeed $R_3=R_1+2R_2$.

**(c, the $4\times4$)** $\begin{bmatrix}1&0&0&1\\0&1&0&1\\0&0&1&1\\0&0&0&1\end{bmatrix}$ is upper triangular with $|\cdot|=1$, so non-singular.

$$\mathbf A^{-1}=\begin{bmatrix}1&0&0&-1\\0&1&0&-1\\0&0&1&-1\\0&0&0&1\end{bmatrix}$$

This undoes "add the last coordinate to the others".

**(d, the $3\times3$ with a repeated row)** $\begin{bmatrix}1&0&1\\0&1&0\\1&0&1\end{bmatrix}$: rows 1 and 3 are equal, so $|\cdot|=0$ and it is **singular**.

**(c, complex)** $\begin{bmatrix}1&\mathrm j\\-\mathrm j&2\end{bmatrix}$: $|\cdot|=2-(\mathrm j)(-\mathrm j)=2-1=1$, non-singular.

$$\mathbf A^{-1}=\begin{bmatrix}2&-\mathrm j\\\mathrm j&1\end{bmatrix}$$

**(d, the second $3\times3$)** $\begin{bmatrix}1&2&3\\0&1&2\\2&3&1\end{bmatrix}$: $|\cdot|=1(1-6)-2(0-4)+3(0-2)=-3$, non-singular.

$$\operatorname{adj}=\begin{bmatrix}-5&7&1\\4&-5&-2\\-2&1&1\end{bmatrix},\qquad\mathbf A^{-1}=-\frac13\operatorname{adj}=\begin{bmatrix}\frac53&-\frac73&-\frac13\\-\frac43&\frac53&\frac23\\\frac23&-\frac13&-\frac13\end{bmatrix}$$

## Booklet Exercise A: The direct (cofactor) method for $\begin{pmatrix}1&2\\2&1\end{pmatrix}$
- Minors: $M_{11}=1$, $M_{12}=2$, $M_{21}=2$, $M_{22}=1$.
- Cofactors: $A_{11}=1$, $A_{12}=-2$, $A_{21}=-2$, $A_{22}=1$.
- $|\mathbf A|=1-4=-3$.

$$\operatorname{adj}\mathbf A=\begin{pmatrix}1&-2\\-2&1\end{pmatrix}^{\mathrm T}=\begin{pmatrix}1&-2\\-2&1\end{pmatrix},\qquad\mathbf A^{-1}=\frac{\operatorname{adj}\mathbf A}{|\mathbf A|}=\boxed{\begin{pmatrix}-\frac13&\frac23\\\frac23&-\frac13\end{pmatrix}}$$

**Check**: $\mathbf A\mathbf A^{-1}=\frac13\begin{pmatrix}-1+4&2-2\\-2+2&4-1\end{pmatrix}=\mathbf I$ ✔.

## Exercise 63: Invert, then solve the system
$\mathbf A=\begin{bmatrix}-1&2&1\\0&1&-2\\1&4&-1\end{bmatrix}$ has $|\mathbf A|=-1(-1+8)-2(0+2)+1(0-1)=-12$.

The cofactor matrix is $\begin{bmatrix}7&-2&-1\\6&0&6\\-5&-2&-1\end{bmatrix}$, so

$$\operatorname{adj}\mathbf A=\begin{bmatrix}7&6&-5\\-2&0&-2\\-1&6&-1\end{bmatrix},\qquad\mathbf A^{-1}=-\frac1{12}\operatorname{adj}\mathbf A=\begin{bmatrix}-\frac7{12}&-\frac12&\frac5{12}\\\frac16&0&\frac16\\\frac1{12}&-\frac12&\frac1{12}\end{bmatrix}$$

Then

$$\mathbf X=\mathbf A^{-1}\begin{bmatrix}2\\-3\\4\end{bmatrix}=\begin{bmatrix}-\frac{7}{6}+\frac32+\frac53\\\frac13+0+\frac23\\\frac16+\frac32+\frac13\end{bmatrix}=\boxed{\begin{bmatrix}2\\1\\2\end{bmatrix}}$$

**Check**: $-2+2+2=2$ ✔, $1-4=-3$ ✔, $2+4-2=4$ ✔.

## Exercise 64: Two values of $\alpha$ with non-trivial solutions

$$\begin{vmatrix}\alpha&-3&1+\alpha\\2&1&-\alpha\\\alpha+2&-2&\alpha\end{vmatrix}=\alpha(\alpha-2\alpha)+3\big(2\alpha+\alpha(\alpha+2)\big)+(1+\alpha)\big(-4-(\alpha+2)\big)$$

$$=-\alpha^2+3\alpha^2+12\alpha-(\alpha+1)(\alpha+6)=\alpha^2+5\alpha-6=(\alpha-1)(\alpha+6)$$

Non-trivial solutions exist iff this is zero, so $\boxed{\alpha=1\text{ or }\alpha=-6}$.

- **$\alpha=1$**: the system is $x-3y+2z=0$, $2x+y-z=0$, $3x-2y+z=0$. From the first two, $x:y:z=1:5:7$, so $\boxed{(x,y,z)=\lambda(1,5,7)}$. Check the third: $3-10+7=0$ ✔.
- **$\alpha=-6$**: the system is $-6x-3y-5z=0$, $2x+y+6z=0$, $-4x-2y-6z=0$. The second and third give $z=0$ and $y=-2x$, so $\boxed{(x,y,z)=\mu(1,-2,0)}$. Check the first: $-6+6-0=0$ ✔.

## Exercise 73: Standard elimination (not the tridiagonal algorithm)

$$\left[\begin{array}{cccc|c}4&-1&0&0&2\\-1&4&-1&0&5\\0&-1&4&-1&3\\0&0&-1&4&10\end{array}\right]$$

Eliminate below the diagonal, one column at a time:
- $R_2+\frac14R_1$ gives $(0,\frac{15}4,-1,0\,|\,\frac{11}2)$.
- $R_3+\frac4{15}R_2$ gives $(0,0,\frac{56}{15},-1\,|\,\frac{67}{15})$.
- $R_4+\frac{15}{56}R_3$ gives $(0,0,0,\frac{209}{56}\,|\,\frac{627}{56})$.

**Back substitution**:
- $t=\frac{627}{209}=3$
- $\frac{56}{15}z=\frac{67}{15}+3$, so $z=2$
- $\frac{15}4y=\frac{11}2+2$, so $y=2$
- $4x=2+2$, so $x=1$

$$\boxed{(x,y,z,t)=(1,2,2,3)}$$

Because the matrix is tridiagonal, only one element needs eliminating per step. That is exactly why the tridiagonal (Thomas) algorithm is so cheap.

## Booklet Exercise B: Inverses by elimination
Row-reduce $[\mathbf A\,|\,\mathbf I]$ to $[\mathbf I\,|\,\mathbf A^{-1}]$.

**(i)**

$$\left[\begin{array}{cc|cc}1&2&1&0\\2&1&0&1\end{array}\right]\xrightarrow{R_2-2R_1}\left[\begin{array}{cc|cc}1&2&1&0\\0&-3&-2&1\end{array}\right]\xrightarrow{-\frac13R_2}\left[\begin{array}{cc|cc}1&2&1&0\\0&1&\frac23&-\frac13\end{array}\right]\xrightarrow{R_1-2R_2}\left[\begin{array}{cc|cc}1&0&-\frac13&\frac23\\0&1&\frac23&-\frac13\end{array}\right]$$

This agrees with Exercise A ✔.

**(ii)** $\begin{pmatrix}-1&2&1\\0&1&-2\\1&4&-1\end{pmatrix}$:

| Step | Row operation | Result |
|---|---|---|
| 1 | $R_3+R_1$ | $R_3=(0,6,0\,\vert\,1,0,1)$ |
| 2 | $R_3-6R_2$ | $R_3=(0,0,12\,\vert\,1,-6,1)$ |
| 3 | $\frac1{12}R_3$ | $R_3=(0,0,1\,\vert\,\frac1{12},-\frac12,\frac1{12})$ |
| 4 | $R_2+2R_3$ | $R_2=(0,1,0\,\vert\,\frac16,0,\frac16)$ |
| 5 | $R_1-R_3$ | $R_1=(-1,2,0\,\vert\,\frac{11}{12},\frac12,-\frac1{12})$ |
| 6 | $R_1-2R_2$ | $R_1=(-1,0,0\,\vert\,\frac7{12},\frac12,-\frac5{12})$ |
| 7 | $-R_1$ | $R_1=(1,0,0\,\vert\,-\frac7{12},-\frac12,\frac5{12})$ |

$$\mathbf A^{-1}=\begin{pmatrix}-\frac7{12}&-\frac12&\frac5{12}\\\frac16&0&\frac16\\\frac1{12}&-\frac12&\frac1{12}\end{pmatrix}$$

This is the same as in Exercise 63 ✔.

---

# Part C: Specimen Test 17

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 17), then solved and checked with SymPy, NumPy or SciPy.

## Q1: The inverse by cofactors
**(i)**

$$\mathbf A^{-1}=\frac{1}{|\mathbf A|}\operatorname{adj}\mathbf A=\frac1{|\mathbf A|}[A_{ij}]^{\mathrm T}\qquad(|\mathbf A|\neq0)$$

**(ii)** $\left|\begin{smallmatrix}1&3\\2&4\end{smallmatrix}\right|=-2$, so

$$\mathbf A^{-1}=-\frac12\begin{pmatrix}4&-3\\-2&1\end{pmatrix}=\boxed{\begin{pmatrix}-2&\frac32\\1&-\frac12\end{pmatrix}}$$

## Q2
(i) $\mathbf{AX}=\mathbf b$ has a unique solution iff $|\mathbf A|\neq0$.
(ii) $\mathbf{AX}=\mathbf0$ has a non-trivial solution iff $|\mathbf A|=0$.

## Q3: Find $\alpha$

$$\begin{vmatrix}\alpha&1&-1\\2&3&3\\4&5&1\end{vmatrix}=\alpha(3-15)-1(2-12)-1(10-12)=-12\alpha+12=0\ \Rightarrow\ \boxed{\alpha=1}$$

## Q4: Elimination

$$\left[\begin{array}{ccc|c}1&2&1&10\\2&1&1&6\\10&-1&3&2\end{array}\right]\xrightarrow[R_3-10R_1]{R_2-2R_1}\left[\begin{array}{ccc|c}1&2&1&10\\0&-3&-1&-14\\0&-21&-7&-98\end{array}\right]\xrightarrow{R_3-7R_2}\left[\begin{array}{ccc|c}1&2&1&10\\0&-3&-1&-14\\0&0&0&0\end{array}\right]$$

The last row is $0=0$. So the matrix is **singular** ($|\mathbf A|=0$) but the system is **consistent**, and there are **infinitely many** solutions. Let $z=\lambda$:

$$\boxed{x=\frac{2-\lambda}3,\quad y=\frac{14-\lambda}3,\quad z=\lambda}$$

**Check** with $\lambda=2$, i.e. $(0,4,2)$: $0+8+2=10$ ✔, $0+4+2=6$ ✔, $0-4+6=2$ ✔.

## Q5: The inverse of $\begin{pmatrix}1&1&1\\2&0&2\\2&-2&1\end{pmatrix}$ by elimination
| Step | Operation | Result |
|---|---|---|
| 1 | $R_2-2R_1$ | $(0,-2,0\,\vert\,-2,1,0)$ |
| 2 | $R_3-2R_1$ | $(0,-4,-1\,\vert\,-2,0,1)$ |
| 3 | $R_3-2R_2$ | $(0,0,-1\,\vert\,2,-2,1)$ |
| 4 | $-R_3$ | $(0,0,1\,\vert\,-2,2,-1)$ |
| 5 | $-\frac12R_2$ | $(0,1,0\,\vert\,1,-\frac12,0)$ |
| 6 | $R_1-R_2-R_3$ | $(1,0,0\,\vert\,2,-\frac32,1)$ |

$$\mathbf A^{-1}=\boxed{\begin{pmatrix}2&-\frac32&1\\1&-\frac12&0\\-2&2&-1\end{pmatrix}}$$

## Sources
- Transcribed problem statements: `tmp/md/module_17_matrices_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §5.4–5.5; MATH1054 Module Booklet, Module 17
