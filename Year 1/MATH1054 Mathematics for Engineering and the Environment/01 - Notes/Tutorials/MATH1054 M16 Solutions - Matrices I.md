---
title: "MATH1054 M16 Solutions - Matrices I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 4: Vectors and Matrices"
tags:
  - math1054
  - tutorial-solutions
  - matrices
  - determinants
sheet: "Specimen Test 16 (booklet) + Module 16 work scheme: Examples 5.1–5.21; Exercises 12, 13(a),(b), 34, 35(a),(b), 39, 45(b); Booklet Exercise A"
theory_notes: ["[[MATH1054 M16 - Matrices I]]"]
key_concepts: ["[[Matrix Algebra]]", "[[Determinants and Cofactors]]"]
status: complete
sources: ["tmp/md/module_16_matrices_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§5.2–5.4)"]
---

# MATH1054 M16 Solutions - Matrices I

> [!abstract] Sheet Info
> The whole Module 16 work scheme. Every product, determinant and adjoint was checked with SymPy `Matrix`.
>
> **Notation**:
> - $M_{ij}$ is a **minor**: the determinant left after deleting row $i$ and column $j$.
> - $A_{ij}=(-1)^{i+j}M_{ij}$ is the corresponding **cofactor**.
> - Sign pattern: $\begin{smallmatrix}+&-&+\\-&+&-\\+&-&+\end{smallmatrix}$.

## Theory Links
- [[MATH1054 M16 - Matrices I]] · [[Matrix Algebra]] · [[Determinants and Cofactors]]

---

# Part A: Worked examples

## Example 5.1: Sums, multiples and transposes
Matrices can only be added if they have the **same size**. Here $\mathbf A$ and $\mathbf C$ are $3\times3$, and $\mathbf B$ is $3\times2$.

| | Expression | Result |
|---|---|---|
| (a) | $\mathbf A+\mathbf B$ | **not defined** ($3\times3$ vs $3\times2$) |
| (b) | $\mathbf A+\mathbf C$ | $\begin{bmatrix}1&3&2\\1&1&3\\2&1&1\end{bmatrix}$ |
| (c) | $\mathbf C-\mathbf A$ | $\begin{bmatrix}-1&-1&0\\-1&-1&-1\\0&-1&-1\end{bmatrix}$ |
| (d) | $3\mathbf A$ | $\begin{bmatrix}3&6&3\\3&3&6\\3&3&3\end{bmatrix}$ |
| (e) | $4\mathbf B$ | $\begin{bmatrix}8&4\\4&0\\4&4\end{bmatrix}$ |
| (f) | $\mathbf C+\mathbf B$ | **not defined** |
| (g) | $3\mathbf A+2\mathbf C$ | $\begin{bmatrix}3&8&5\\3&3&8\\5&3&3\end{bmatrix}$ |
| (h) | $\mathbf A^{\mathrm T}+\mathbf A$ | $\begin{bmatrix}2&3&2\\3&2&3\\2&3&2\end{bmatrix}$ (**symmetric**, as $\mathbf A^{\mathrm T}+\mathbf A$ always is) |
| (i) | $\mathbf A+\mathbf C^{\mathrm T}+\mathbf B^{\mathrm T}$ | **not defined** ($\mathbf B^{\mathrm T}$ is $2\times3$) |

## Example 5.4: Products (row × column)
$\mathbf A$ is $2\times3$, $\mathbf B$ is $3\times2$, $\mathbf b$ is $2\times1$, $\mathbf c$ is $3\times1$ and $\mathbf C$ is $3\times2$.

(a) $\mathbf{AB}=\begin{bmatrix}1\cdot2+1\cdot0+0\cdot1&0+1+0\\4+0+1&0+0+3\end{bmatrix}=\begin{bmatrix}2&1\\5&3\end{bmatrix}$, which is $2\times2$.

(b) $\mathbf{BA}=\begin{bmatrix}2&2&0\\2&0&1\\7&1&3\end{bmatrix}$, which is $3\times3$. So $\mathbf{AB}\neq\mathbf{BA}$: they are not even the same size.

(c) $\mathbf B\mathbf b=\begin{bmatrix}-2\\2\\5\end{bmatrix}$

(d) $\mathbf A^{\mathrm T}\mathbf b=\begin{bmatrix}1&2\\1&0\\0&1\end{bmatrix}\begin{bmatrix}-1\\2\end{bmatrix}=\begin{bmatrix}3\\-1\\2\end{bmatrix}$

(e) $\mathbf c^{\mathrm T}(\mathbf A^{\mathrm T}\mathbf b)=3-1-2=[0]$, a $1\times1$ matrix.

(f) $\mathbf{AC}=\begin{bmatrix}0&0\\0&0\end{bmatrix}$. **The product of two non-zero matrices can be the zero matrix.** So $\mathbf{AC}=\mathbf0$ does **not** imply $\mathbf A=\mathbf0$ or $\mathbf C=\mathbf0$.

## Example 5.5: Quadratic forms
(a) $\mathbf X^{\mathrm T}\mathbf X=[x^2+y^2+z^2]$

(b) $\mathbf{AX}=\begin{bmatrix}x+2y\\x+y\\2x+y+z\end{bmatrix}$

(c) $\mathbf X^{\mathrm T}(\mathbf{AX})=x(x+2y)+y(x+y)+z(2x+y+z)=[x^2+y^2+z^2+3xy+2xz+yz]$

(d) $\tfrac12\mathbf X^{\mathrm T}(\mathbf A^{\mathrm T}+\mathbf A)\mathbf X=$ **the same** as (c).

A quadratic form only "sees" the symmetric part $\frac12(\mathbf A+\mathbf A^{\mathrm T})$ of $\mathbf A$.

## Example 5.6: Transpose of a product, and a solution by pre-multiplication
**(a)**
(i) $\mathbf{AB}=\mathbf I_3$.
(ii) $(\mathbf{AB})^{\mathrm T}=\mathbf I$.
(iii) $\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}=\mathbf I$.

This confirms $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$. It also shows $\mathbf B=\mathbf A^{-1}$.

**(b)** Pre-multiply $\mathbf{BX}=\mathbf c$ by $\mathbf A$: $\mathbf{ABX}=\mathbf{IX}=\mathbf X=\mathbf{Ac}$. So

$$\mathbf X=\begin{bmatrix}1&2&2\\0&1&1\\1&0&1\end{bmatrix}\begin{bmatrix}1\\0\\1\end{bmatrix}=\boxed{\begin{bmatrix}3\\1\\2\end{bmatrix}}$$

That is, $x=3$, $y=1$, $z=2$. **Check** in $\mathbf{BX}$: $3-2=1$, $3-1-2=0$, $-3+2+2=1$ ✔.

## Example 5.7: Associative and distributive laws

$$\mathbf{AB}=\begin{bmatrix}1&0&1\\3&6&7\\-2&-2&-3\end{bmatrix},\qquad\mathbf{BC}=\begin{bmatrix}-3&1\\-11&7\\-9&10\end{bmatrix}$$

$$(\mathbf{AB})\mathbf C=\begin{bmatrix}-1&4\\-21&28\\7&-13\end{bmatrix}=\mathbf A(\mathbf{BC})\ ✔\ \text{(associative)}$$

$$(\mathbf A+\mathbf B)\mathbf C=\begin{bmatrix}1&-1&2\\-2&2&6\\1&3&1\end{bmatrix}\mathbf C=\begin{bmatrix}-3&3\\-24&4\\-4&10\end{bmatrix}=\mathbf{AC}+\mathbf{BC}$$

Here $\mathbf{AC}=\begin{bmatrix}0&2\\-13&-3\\5&0\end{bmatrix}$ and $\mathbf{BC}$ is as above ✔ (distributive).

## Example 5.8: A rotation maps the square onto a square
With $\theta=60°$, $\cos\theta=\frac12$ and $\sin\theta=\frac{\sqrt3}2$, so the transformation is $x'=\frac12x+\frac{\sqrt3}2y$ and $y'=-\frac{\sqrt3}2x+\frac12y$.

| Corner | Image |
|---|---|
| $(1,1)$ | $(1.366,\,-0.366)$ |
| $(1,2)$ | $(2.232,\,0.134)$ |
| $(2,2)$ | $(2.732,\,-0.732)$ |
| $(2,1)$ | $(1.866,\,-1.232)$ |

The edges from the first image vertex are $(0.866,0.500)$ and $(0.500,-0.866)$. Both have length 1, and their dot product is $0.433-0.433=0$. So the image is still a unit square ✔.

In general, a rotation matrix $\mathbf R$ satisfies $\mathbf R^{\mathrm T}\mathbf R=\mathbf I$, so it preserves lengths and angles. This is a clockwise rotation by $60°$.

## Example 5.14: Expand along the first row

$$\begin{vmatrix}1&2&4\\-1&0&3\\3&1&-2\end{vmatrix}=1(0-3)-2(2-9)+4(-1-0)=-3+14-4=\boxed7$$

## Example 5.15: Minors and cofactors of the first row

$$M_{11}=\begin{vmatrix}-4&2\\-1&1\end{vmatrix}=-2,\quad M_{12}=\begin{vmatrix}6&2\\2&1\end{vmatrix}=2,\quad M_{13}=\begin{vmatrix}6&-4\\2&-1\end{vmatrix}=2$$

The cofactors are $A_{11}=-2$, $A_{12}=-2$ and $A_{13}=2$. Then

$$|\mathbf A|=3(-2)+4(-2)+5(2)=\boxed{-4}$$

## Example 5.16: Properties of determinants
| | Matrix | Relation to (a) | Value |
|---|---|---|---|
| (a) | $\begin{smallmatrix}1&0&1\\0&1&2\\1&1&0\end{smallmatrix}$ | expand directly: $1(0-2)-0+1(0-1)$ | $-3$ |
| (b) | rows 2 and 3 of (a) swapped | a row swap changes the sign | $+3$ |
| (c) | the transpose of (b) | $\lvert\mathbf A^{\mathrm T}\rvert=\lvert\mathbf A\rvert$ | $+3$ |
| (d) | (a) with row 2 ×2 and row 3 ×3 | a row scale scales the determinant | $-3\times6=-18$ |

## Example 5.17: $|\mathbf{AB}|=|\mathbf A||\mathbf B|$
**(a)** $|\mathbf A|=0$. The rows are in arithmetic progression: $\mathrm R_3-\mathrm R_2=2(\mathrm R_2-\mathrm R_1)$, so the rows are linearly dependent.

**(b)** $|\mathbf B|=1(3-2)-0+1(2-1)=2$.

**(c)** $\mathbf{AB}=\begin{bmatrix}6&8&12\\9&11&17\\15&17&27\end{bmatrix}$, and $|\mathbf{AB}|=0=0\times2$ ✔.

## Example 5.18: A $4\times4$ determinant by row operations
Subtract row 1 from rows 2, 3 and 4. This doesn't change the determinant:

$$D=\begin{vmatrix}1&1&1&1\\0&a&0&0\\0&0&b&0\\0&0&0&c\end{vmatrix}=\boxed{abc}$$

The determinant of a triangular matrix is the product of its diagonal.

## Example 5.21: $\operatorname{adj}\mathbf A$ and $\mathbf A(\operatorname{adj}\mathbf A)=|\mathbf A|\mathbf I$
For $\mathbf A=\begin{bmatrix}1&1&2\\2&0&1\\3&1&1\end{bmatrix}$, the cofactors are:
- row 1: $A_{11}=(0-1)=-1$, $A_{12}=-(2-3)=1$, $A_{13}=(2-0)=2$
- row 2: $A_{21}=-(1-2)=1$, $A_{22}=(1-6)=-5$, $A_{23}=-(1-3)=2$
- row 3: $A_{31}=(1-0)=1$, $A_{32}=-(1-4)=3$, $A_{33}=(0-2)=-2$

$\operatorname{adj}\mathbf A$ is the **transpose** of the cofactor matrix:

$$\operatorname{adj}\mathbf A=\begin{bmatrix}-1&1&1\\1&-5&3\\2&2&-2\end{bmatrix},\qquad|\mathbf A|=1(-1)+1(1)+2(2)=4$$

Multiplying out gives $\mathbf A(\operatorname{adj}\mathbf A)=(\operatorname{adj}\mathbf A)\mathbf A=4\mathbf I$ ✔.

---

# Part B: Assigned exercises

## Exercise 12: Products, and which are special

$$\mathbf{AB}=\begin{bmatrix}2&2&-1\\2&2&-1\end{bmatrix},\quad\mathbf{AC}=\begin{bmatrix}0&2\\0&2\end{bmatrix},\quad\mathbf{BC}=\begin{bmatrix}1&3\\1&3\\1&1\end{bmatrix}$$

$$\mathbf{CA}=\begin{bmatrix}2&2&2\\2&2&2\\-2&-2&-2\end{bmatrix},\quad\mathbf{BA}^{\mathrm T}=\begin{bmatrix}2&2\\2&2\\-1&-1\end{bmatrix}$$

- Only $\mathbf{AC}$ ($2\times2$) and $\mathbf{CA}$ ($3\times3$) are square.
- $\mathbf{AC}$ is not symmetric ($2\neq0$ off the diagonal), and $\mathbf{CA}$ is not symmetric ($(\mathbf{CA})_{13}=2\neq(\mathbf{CA})_{31}=-2$).

So **none** of the products is diagonal, unit or symmetric.

## Exercise 13: Which products exist?
$\mathbf A$ and $\mathbf B$ are $2\times3$, and $\mathbf C$ is $3\times2$. A product exists iff the **inner sizes match**.

| Product | Sizes | Defined? |
|---|---|---|
| $\mathbf{AB}$ | $(2\times3)(2\times3)$ | no |
| $\mathbf{AC}$ | $(2\times3)(3\times2)$ | **yes**, $2\times2$ |
| $\mathbf{BC}$ | $(2\times3)(3\times2)$ | **yes**, $2\times2$ |
| $\mathbf{AB}^{\mathrm T}$ | $(2\times3)(3\times2)$ | **yes**, $2\times2$ |
| $\mathbf{AC}^{\mathrm T}$ | $(2\times3)(2\times3)$ | no |
| $\mathbf{BC}^{\mathrm T}$ | $(2\times3)(2\times3)$ | no |

**(b)**

$$\mathbf{AC}=\begin{bmatrix}1+6+2&2+2+3\\3+0+4&6+0+6\end{bmatrix}=\begin{bmatrix}9&7\\7&12\end{bmatrix},\quad\mathbf{BC}=\begin{bmatrix}13&18\\8&5\end{bmatrix},\quad\mathbf{AB}^{\mathrm T}=\begin{bmatrix}9&5\\18&2\end{bmatrix}$$

## Exercise 35(a),(b): Determinants
**(a)** $\begin{vmatrix}1&7\\4&9\end{vmatrix}=9-28=\boxed{-19}$

**(b)**

$$\begin{vmatrix}1&4&3\\2&-4&1\\3&2&-6\end{vmatrix}=1(24-2)-4(-12-3)+3(4+12)=22+60+48=\boxed{130}$$

## Exercise 34: All minors and cofactors of $\begin{vmatrix}1&2&3\\1&0&1\\1&1&1\end{vmatrix}$

$$\text{Minors }M_{ij}=\begin{bmatrix}-1&0&1\\-1&-2&-1\\2&-2&-2\end{bmatrix},\qquad\text{Cofactors }A_{ij}=\begin{bmatrix}-1&0&1\\1&-2&1\\2&2&-2\end{bmatrix}$$

Expanding along row 1: $1(-1)+2(0)+3(1)=\boxed2$.
**Check** with column 2: $2(0)+0(-2)+1(2)=2$ ✔. Any row or column gives the same value.

## Booklet Exercise A: Exercise 35(c) expanded along the third row
For $\begin{bmatrix}2&-1&3\\4&2&9\\1&3&-4\end{bmatrix}$, row 3 is $(1,3,-4)$ with signs $(+,-,+)$:

$$A_{31}=+\begin{vmatrix}-1&3\\2&9\end{vmatrix}=-15,\quad A_{32}=-\begin{vmatrix}2&3\\4&9\end{vmatrix}=-6,\quad A_{33}=+\begin{vmatrix}2&-1\\4&2\end{vmatrix}=8$$

$$|\mathbf A|=1(-15)+3(-6)+(-4)(8)=\boxed{-65}$$

## Exercise 39: $\operatorname{adj}\mathbf A$ for $\mathbf A=\begin{bmatrix}2&1&1\\3&2&2\\1&1&2\end{bmatrix}$
The cofactor matrix is $\begin{bmatrix}2&-4&1\\-1&3&-1\\0&-1&1\end{bmatrix}$. Transposing it:

$$\operatorname{adj}\mathbf A=\begin{bmatrix}2&-1&0\\-4&3&-1\\1&-1&1\end{bmatrix},\qquad|\mathbf A|=2(2)+1(-4)+1(1)=1$$

Then $\mathbf A(\operatorname{adj}\mathbf A)=\mathbf I=(\operatorname{adj}\mathbf A)\mathbf A$ ✔. Since $|\mathbf A|=1$, $\operatorname{adj}\mathbf A$ **is** $\mathbf A^{-1}$.

## Exercise 45(b): A $4\times4$ determinant
Exploit the symmetry. Do the column operations $C_1\to C_1-C_2$ and $C_3\to C_3-C_4$:

$$\begin{vmatrix}1&4&0&1\\-1&5&0&1\\0&1&2&2\\0&1&-2&4\end{vmatrix}$$

Then do the row operations $R_2\to R_2+R_1$ and $R_4\to R_4+R_3$:

$$\begin{vmatrix}1&4&0&1\\0&9&0&2\\0&1&2&2\\0&2&0&6\end{vmatrix}=1\cdot\begin{vmatrix}9&0&2\\1&2&2\\2&0&6\end{vmatrix}=9(12-0)-0+2(0-4)=\boxed{100}$$

**Cross-check with eigenvalues** (from M18):
- $(1,-1,0,0)$ and $(0,0,1,-1)$ are eigenvectors, with eigenvalues $1$ and $2$.
- On vectors of the form $(a,a,b,b)$, the matrix acts as $\begin{bmatrix}9&2\\2&6\end{bmatrix}$, which has eigenvalues $5$ and $10$.

The determinant is the product of the eigenvalues: $1\cdot2\cdot5\cdot10=100$ ✔.

---

# Part C: Specimen Test 16

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 16), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Orders and which combinations exist
The orders are: $\mathbf A$ is $2\times3$, $\mathbf B$ is $2\times2$, $\mathbf C$ is $2\times2$, and $\mathbf D$ is $3\times2$.

| | Expression | Exists? | Result |
|---|---|---|---|
| (i) | $2\mathbf C-\mathbf B$ | ✔ ($2\times2$) | $\begin{pmatrix}0&-4\\-2&2\end{pmatrix}-\begin{pmatrix}-2&1\\3&2\end{pmatrix}=\begin{pmatrix}2&-5\\-5&0\end{pmatrix}$ |
| (ii) | $\mathbf A^{\mathrm T}-\mathbf D^{\mathrm T}$ | ✘ | $3\times2$ minus $2\times3$ |
| (iii) | $\mathbf{AD}$ | ✔ ($2\times2$) | $\begin{pmatrix}3+4+0&1-2-1\\9+2+0&3-1+4\end{pmatrix}=\begin{pmatrix}7&-2\\11&6\end{pmatrix}$ |
| (iv) | $\mathbf{AB}^{\mathrm T}$ | ✘ | $(2\times3)(2\times2)$: the inner sizes don't match |
| (v) | $\mathbf{DC}$ | ✔ ($3\times2$) | $\begin{pmatrix}-1&-5\\1&-5\\-1&1\end{pmatrix}$ |

## Q2
$\mathbf A$ is symmetric iff $\mathbf A^{\mathrm T}=\mathbf A$, i.e. $a_{ij}=a_{ji}$. It must be square.

## Q3
(i) $(\mathbf A^{\mathrm T})^{\mathrm T}=\mathbf A$
(ii) $(\mathbf A^{\mathrm T}\mathbf B)^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A$

## Q4
(i) **Yes**: the distributive law always holds.
(ii) **No**: matrix multiplication is not commutative in general.

## Q5: $\begin{vmatrix}5&2&-7\\6&11&4\\3&8&1\end{vmatrix}$
**(i)** The minor of $a_{13}$: $M_{13}=\begin{vmatrix}6&11\\3&8\end{vmatrix}=48-33=\boxed{15}$.

**(ii)** The cofactor of $a_{22}$: $A_{22}=+\begin{vmatrix}5&-7\\3&1\end{vmatrix}=5+21=\boxed{26}$.

## Q6: Expand along the third column
The cofactors are:
- $A_{13}=+15$
- $A_{23}=-\begin{vmatrix}5&2\\3&8\end{vmatrix}=-34$
- $A_{33}=+\begin{vmatrix}5&2\\6&11\end{vmatrix}=43$

$$|\cdot|=(-7)(15)+4(-34)+1(43)=-105-136+43=\boxed{-198}$$

## Q7: $\operatorname{adj}\mathbf A$ for $\mathbf A=\begin{pmatrix}1&2&1\\3&0&-1\\-2&1&1\end{pmatrix}$
The cofactor matrix is $\begin{pmatrix}1&-1&3\\-1&3&-5\\-2&4&-6\end{pmatrix}$. Transposing:

$$\operatorname{adj}\mathbf A=\boxed{\begin{pmatrix}1&-1&-2\\-1&3&4\\3&-5&-6\end{pmatrix}}$$

**Check**: $|\mathbf A|=2$ and $\mathbf A(\operatorname{adj}\mathbf A)=2\mathbf I$ ✔.

## Sources
- Transcribed problem statements: `tmp/md/module_16_matrices_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §5.2–5.4; MATH1054 Module Booklet, Module 16
