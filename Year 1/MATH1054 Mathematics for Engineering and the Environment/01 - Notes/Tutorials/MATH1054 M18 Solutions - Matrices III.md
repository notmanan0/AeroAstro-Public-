---
title: "MATH1054 M18 Solutions - Matrices III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 4: Vectors and Matrices"
tags:
  - math1054
  - tutorial-solutions
  - matrices
  - rank
  - eigenvalues
sheet: "Specimen Test 18 (booklet) + Module 18 work scheme: Examples 5.37–5.44; Exercises 88, 90(a),(b); Booklet Exercise A"
theory_notes: ["[[MATH1054 M18 - Matrices III]]"]
key_concepts: ["[[Rank and Consistency of Linear Systems]]", "[[Eigenvalues and Eigenvectors]]", "[[Characteristic Equation and Eigenvalues]]"]
status: complete
sources: ["tmp/md/module_18_matrices_iii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§5.6–5.7)"]
---

# MATH1054 M18 Solutions - Matrices III

> [!abstract] Sheet Info
> The whole Module 18 work scheme. Ranks, RREFs, solution sets and eigen-pairs were checked with SymPy (`rank`, `rref`, `linsolve`, `eigenvects`). Eigenvectors are determined only up to a non-zero scalar multiple.
>
> **Consistency rule**: $\mathbf{AX}=\mathbf b$ is solvable iff $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]$. When it is, there are $n-\operatorname{rank}$ free parameters, where $n$ is the number of unknowns.

## Theory Links
- [[MATH1054 M18 - Matrices III]] · [[Rank and Consistency of Linear Systems]] · [[Eigenvalues and Eigenvectors]] · [[Characteristic Equation and Eigenvalues]] (SESA2027)

---

# Part A: Worked examples

## Example 5.37: Rank
**(a)** $\begin{bmatrix}1&1&-1\\2&-1&2\\0&-3&4\end{bmatrix}\xrightarrow{R_2-2R_1}\begin{bmatrix}1&1&-1\\0&-3&4\\0&-3&4\end{bmatrix}\xrightarrow{R_3-R_2}\begin{bmatrix}1&1&-1\\0&-3&4\\0&0&0\end{bmatrix}$. Two non-zero rows, so the rank is $\boxed2$.

**(b)** $R_2+2R_1=\mathbf0$ and $R_3+R_1=\mathbf0$. Every row is a multiple of $(1,-1,1)$, so the rank is $\boxed1$.

**(c)** $\begin{vmatrix}1&0&0\\0&1&1\\2&0&1\end{vmatrix}=1(1-0)=1\neq0$. The matrix is non-singular, so the rank is $\boxed3$.

## Example 5.38: Echelon form, rank and solutions
**(a)** Swap $R_1\leftrightarrow R_2$, then eliminate:
$$\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\2&1&5&4&7\\1&-2&0&2&2\end{array}\right]\xrightarrow[R_4-R_1]{R_3-2R_1}\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\0&1&-1&0&1\\0&-2&-3&0&-1\end{array}\right]\xrightarrow[R_4+2R_2]{R_3-R_2}\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\0&0&-2&0&0\\0&0&-1&0&1\end{array}\right]$$
Finally, $R_4-\frac12R_3$ gives the echelon form
$$\left[\begin{array}{cccc|c}1&0&3&2&3\\0&1&1&0&1\\0&0&-2&0&0\\0&0&0&0&1\end{array}\right]$$
The last row reads $0=1$. So $\operatorname{rank}\mathbf A=3$ but $\operatorname{rank}[\mathbf A|\mathbf b]=4$, and there is **no solution** (inconsistent).

**(b)**
- $R_3-R_1$ gives $(0,1,1,-1,1\,|\,1)$, which equals $R_2$.
- $R_4-2R_1$ gives $3\times R_2$.
- $R_5-2R_1$ gives $2\times R_2$.

After subtracting these multiples of $R_2$, only two non-zero rows remain:
$$\left[\begin{array}{ccccc|c}1&0&-1&1&-1&0\\0&1&1&-1&1&1\end{array}\right]$$
So $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]=2$: the system is **consistent**, with $5-2=3$ free parameters. Let $x_3=\alpha$, $x_4=\beta$, $x_5=\gamma$:
$$\boxed{x_1=\alpha-\beta+\gamma,\quad x_2=1-\alpha+\beta-\gamma,\quad x_3=\alpha,\ x_4=\beta,\ x_5=\gamma}$$

## Example 5.40: $\mathbf A=\begin{bmatrix}-2&1\\1&-2\end{bmatrix}$
$$|\mathbf A-\lambda\mathbf I|=(-2-\lambda)^2-1=\lambda^2+4\lambda+3=0\ \Rightarrow\ \boxed{\lambda=-1,\ -3}$$
**Check**: the trace is $-4$, which equals the sum of the eigenvalues; the determinant is $3$, which equals their product ✔.

## Example 5.41: The characteristic equation of $\mathbf A=\begin{bmatrix}1&1&-2\\-1&2&1\\0&1&-1\end{bmatrix}$
Expand along the first row:
$$|\mathbf A-\lambda\mathbf I|=(1-\lambda)\big[(2-\lambda)(-1-\lambda)-1\big]-1\big[(1+\lambda)\big]-2\big[-1\big]$$
$$=(1-\lambda)(\lambda^2-\lambda-3)-\lambda+1=(1-\lambda)(\lambda^2-\lambda-2)$$
$$\boxed{\lambda^3-2\lambda^2-\lambda+2=0}\quad\text{i.e. }(\lambda-1)(\lambda-2)(\lambda+1)=0$$

## Example 5.42: Verify the eigenvectors
$$\mathbf A\begin{bmatrix}1\\1\end{bmatrix}=\begin{bmatrix}-1\\-1\end{bmatrix}=-1\begin{bmatrix}1\\1\end{bmatrix}\ (\lambda=-1),\qquad\mathbf A\begin{bmatrix}1\\-1\end{bmatrix}=\begin{bmatrix}-3\\3\end{bmatrix}=-3\begin{bmatrix}1\\-1\end{bmatrix}\ (\lambda=-3)\ ✔$$
Two coupled masses on springs have exactly this matrix. The two eigenvectors are the **in-phase** and **anti-phase** modes ([[Natural Frequencies and Mode Shapes]]).

## Example 5.43: $\mathbf A=\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ (rotation by $90°$)
$\lambda^2+1=0$ gives $\boxed{\lambda=\pm\mathrm j}$.
- $\lambda=\mathrm j$: $-\mathrm jx-y=0$, so $\mathbf X=\begin{bmatrix}1\\-\mathrm j\end{bmatrix}$.
- $\lambda=-\mathrm j$: $\mathbf X=\begin{bmatrix}1\\\mathrm j\end{bmatrix}$.

The eigenvalues are complex because a rotation leaves **no real direction** unchanged.

## Example 5.44: Eigenvectors for Example 5.41
| $\lambda$ | $\mathbf A-\lambda\mathbf I$ reduces to | Eigenvector |
|---|---|---|
| $-1$ | $2x+y-2z=0$, $y=0$ | $(1,0,1)$ |
| $1$ | $y-2z=0$, $-x+y+z=0$ | $(3,2,1)$ |
| $2$ | $-x+y-2z=0$, $-x+z=0$ | $(1,3,1)$ |

**Check** $\lambda=1$: $\mathbf A(3,2,1)^{\mathrm T}=(3+2-2,\ -3+4+1,\ 0+2-1)=(3,2,1)$ ✔.

---

# Part B: Assigned exercises

## Exercise 88: Echelon form, rank and solution
**(a)**
$$\left[\begin{array}{ccc|c}1&2&3&8\\3&2&1&4\\1&1&1&3\end{array}\right]\xrightarrow[R_3-R_1]{R_2-3R_1}\left[\begin{array}{ccc|c}1&2&3&8\\0&-4&-8&-20\\0&-1&-2&-5\end{array}\right]\xrightarrow{R_3-\frac14R_2}\left[\begin{array}{ccc|c}1&2&3&8\\0&-4&-8&-20\\0&0&0&0\end{array}\right]$$
$\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]=2<3$, so there are **infinitely many** solutions, with one free parameter. Let $z=\alpha$. Then $y=5-2\alpha$ and $x=8-2y-3z=\alpha-2$:
$$\boxed{(x,y,z)=(\alpha-2,\ 5-2\alpha,\ \alpha)}$$

**(b)**
$$\left[\begin{array}{cccc|c}1&2&-1&1&0\\1&1&0&0&1\\0&1&-1&1&-1\\1&0&1&-1&1\end{array}\right]\xrightarrow[R_4-R_1]{R_2-R_1}\left[\begin{array}{cccc|c}1&2&-1&1&0\\0&-1&1&-1&1\\0&1&-1&1&-1\\0&-2&2&-2&1\end{array}\right]\xrightarrow[R_4-2R_2]{R_3+R_2}\left[\begin{array}{cccc|c}1&2&-1&1&0\\0&-1&1&-1&1\\0&0&0&0&0\\0&0&0&0&-1\end{array}\right]$$
The last row reads $0=-1$. So $\operatorname{rank}\mathbf A=2\neq\operatorname{rank}[\mathbf A|\mathbf b]=3$, and there is **no solution**.

## Exercise 90: Non-square systems
**(a)** Two equations in three unknowns:
$$x+3y+4z=1,\qquad-x+3y+4z=3$$
Subtracting gives $2x=-2$, so $x=-1$ and $3y+4z=2$. The rank is $2=\operatorname{rank}[\mathbf A|\mathbf b]$, leaving one free parameter:
$$\boxed{x=-1,\quad y=\tfrac{2-4\alpha}{3},\quad z=\alpha}$$

**(b)** Three equations in two unknowns (overdetermined):
- $2x+y=1$ and $4x+6y=4$ give $4y=2$, so $y=\frac12$ and $x=\frac14$.
- The third equation needs $3x+5y=\frac34+\frac52=\frac{13}4$, but it should equal $-2$. ✘

So $\operatorname{rank}\mathbf A=2$ but $\operatorname{rank}[\mathbf A|\mathbf b]=3$: **no solution**.

## Booklet Exercise A: Eigenvalues and eigenvectors
**(i)** $\begin{pmatrix}5&1\\0&4\end{pmatrix}$ is triangular, so its eigenvalues are its diagonal entries: $\lambda=5,4$.
- $\lambda=5$: $\begin{pmatrix}0&1\\0&-1\end{pmatrix}\mathbf X=\mathbf0$ gives $y=0$, so $\mathbf X=\alpha\begin{pmatrix}1\\0\end{pmatrix}$.
- $\lambda=4$: $\begin{pmatrix}1&1\\0&0\end{pmatrix}\mathbf X=\mathbf0$ gives $x+y=0$, so $\mathbf X=\beta\begin{pmatrix}1\\-1\end{pmatrix}$.

**(ii)** $\begin{pmatrix}1&0&0\\0&3&0\\0&2&4\end{pmatrix}$ is lower triangular, so $\lambda=1,3,4$.
- $\lambda=1$: $2y=0$ and $2y+3z=0$, so $y=z=0$ and $\mathbf X=(1,0,0)$.
- $\lambda=3$: $-2x=0$ and $2y+z=0$, so $\mathbf X=(0,1,-2)$.
- $\lambda=4$: $-3x=0$ and $-y=0$, so $\mathbf X=(0,0,1)$.

**(iii)** $\mathbf A=\begin{pmatrix}-3&1&-1\\1&-5&1\\-1&1&-3\end{pmatrix}$ is **symmetric**.
$$|\mathbf A-\lambda\mathbf I|=(-3-\lambda)\big[(\lambda+5)(\lambda+3)-1\big]-\big[-(3+\lambda)+1\big]-\big[1-(5+\lambda)\big]$$
$$=-(\lambda+3)(\lambda^2+8\lambda+14)+(\lambda+2)+(\lambda+4)=-(\lambda^3+11\lambda^2+36\lambda+36)=-(\lambda+2)(\lambda+3)(\lambda+6)$$
So $\boxed{\lambda=-2,-3,-6}$. Check: they sum to $-11$, the trace ✔.

| $\lambda$ | Equations | Eigenvector |
|---|---|---|
| $-2$ | $-x+y-z=0$, $x-3y+z=0$ | $(1,0,-1)$ |
| $-3$ | $y-z=0$, $x-2y+z=0$ | $(1,1,1)$ |
| $-6$ | $3x+y-z=0$, $x+y+z=0$ | $(1,-2,1)$ |

The three eigenvectors are **mutually orthogonal**: $(1,0,-1)\cdot(1,1,1)=0$, and so on. This always happens for a symmetric matrix.

---

# Part C: Specimen Test 18

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 18), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Rank
$$\begin{pmatrix}1&1&-1&1\\2&3&-3&3\\-1&1&0&0\\2&3&-2&2\end{pmatrix}\xrightarrow[R_4-2R_1]{R_2-2R_1,\ R_3+R_1}\begin{pmatrix}1&1&-1&1\\0&1&-1&1\\0&2&-1&1\\0&1&0&0\end{pmatrix}\xrightarrow[R_4-R_2]{R_3-2R_2}\begin{pmatrix}1&1&-1&1\\0&1&-1&1\\0&0&1&-1\\0&0&1&-1\end{pmatrix}$$
Now $R_4-R_3=\mathbf0$, leaving three non-zero rows. The rank is $\boxed3$.

## Q2
**(i)** $2x+y+z=3$ and $4x+2y+2z=5$. Twice the first gives $6\neq5$, so the equations are **inconsistent**: **no solution**. (The ranks are $\operatorname{rank}\mathbf A=1$ and $\operatorname{rank}[\mathbf A|\mathbf b]=2$.)

**(ii)** From the first two equations: $x=2$ and $y=-1$. Check the third: $3(2)+4(-1)=2$ ✔. So $\boxed{x=2,\ y=-1}$, a unique solution.

## Q3: Eigenvalues and eigenvectors of $\begin{pmatrix}3&0&1\\0&3&1\\1&1&2\end{pmatrix}$
$$|\mathbf A-\lambda\mathbf I|=(3-\lambda)\big[(3-\lambda)(2-\lambda)-1\big]+1\big[0-(3-\lambda)\big]=(3-\lambda)(\lambda^2-5\lambda+4)=(3-\lambda)(\lambda-1)(\lambda-4)$$

| $\lambda$ | Equations | Eigenvector |
|---|---|---|
| 1 | $2x+z=0$, $2y+z=0$ | $(1,1,-2)$ |
| 3 | $z=0$, $x+y=0$ | $(1,-1,0)$ |
| 4 | $-x+z=0$, $-y+z=0$ | $(1,1,1)$ |

The matrix is symmetric, so the eigenvectors are mutually orthogonal ✔.

## Sources
- Transcribed problem statements: `tmp/md/module_18_matrices_iii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §5.6–5.7; MATH1054 Module Booklet, Module 18
