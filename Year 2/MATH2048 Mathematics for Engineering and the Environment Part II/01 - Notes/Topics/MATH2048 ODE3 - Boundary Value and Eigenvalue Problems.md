---
title: "MATH2048 ODE3 - Boundary Value and Eigenvalue Problems"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 1: Ordinary Differential Equations"
order: 3
tags:
  - math2048
  - odes
  - boundary-value-problems
  - eigenvalue-problems
aliases: ["MATH2048 Lecture 3", "BVPs", "Eigenfunctions"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]", "[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
next_topics: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]"]
key_concepts: ["[[Boundary Value Problems]]", "[[ODE Eigenvalue Problems]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture3_(Eigenvalue Problems).pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.2)"]
---
a
# MATH2048 ODE3 - Boundary Value and Eigenvalue Problems

> [!abstract] Summary
> - An **IVP** fixes $y$ and $y'$ at one point, and always has a unique solution.
> - A **BVP** fixes conditions at two points. It can have a **unique** solution, **no** solution, or a **one-parameter family** of solutions, depending on whether the $2\times2$ system for $c_1,c_2$ is solvable.
> - An **eigenvalue problem** is a homogeneous BVP containing a parameter $\lambda$, e.g. $y''+\lambda y=0$ with $y(0)=y(L)=0$. The task is to find the special values $\lambda_n$ (the **eigenvalues**) for which a **non-trivial** solution $y_n$ (the **eigenfunction**) exists.
> - The method is always the same: check $\lambda=0$, $\lambda=-k^2<0$ and $\lambda=k^2>0$ separately.
>
> This is *the* step in every separation-of-variables PDE question: 9 of the 25 marks in 2025/26 A2(b).

## Key Concepts
- [[Boundary Value Problems]] · [[ODE Eigenvalue Problems]] · [[Auxiliary Equation]]

---

## 1. IVPs vs BVPs
| | Conditions | Typical form |
|---|---|---|
| **IVP** | at one point $x_0$ | $y(x_0)=C$, $y'(x_0)=D$ |
| **BVP** | at two points $x_0,x_1$ | $a_0y(x_0)+b_0y'(x_0)=\alpha$, $a_1y(x_1)+b_1y'(x_1)=\beta$ |

Types of boundary condition (Appendix L1–2):

| Name | Condition | Physical meaning (heat in a bar) |
|---|---|---|
| **Dirichlet** | $y=f$ | fixed temperature or displacement |
| **Neumann** | $y'=g$ | fixed flux ($y'=0$: insulated end, or free end of a string) |
| **Robin** (mixed, or radiation) | $y+cy'=h$ | convective or radiating end |

### Why a BVP can fail
The general solution is $y=c_1y_1+c_2y_2+y_p$. Two boundary conditions give a linear system

$$
\underbrace{\begin{pmatrix}B_0[y_1]&B_0[y_2]\\B_1[y_1]&B_1[y_2]\end{pmatrix}}_{M}\begin{pmatrix}c_1\\c_2\end{pmatrix}=\begin{pmatrix}\alpha-B_0[y_p]\\\beta-B_1[y_p]\end{pmatrix},
$$

where $B_0,B_1$ are the boundary operators, e.g. $B_0[y]=a_0y(x_0)+b_0y'(x_0)$.
- $\det M\neq0$: **unique** solution.
- $\det M=0$ and the equations are **inconsistent**: **no** solution.
- $\det M=0$ and the equations are **consistent** (they are the same condition): **infinitely many**, a one-parameter family.

This is the **Fredholm alternative**. The BVP has a unique solution **iff** the homogeneous problem ($r=0$, $\alpha=\beta=0$) has only the trivial solution $y\equiv0$. So the no-solution and infinitely-many cases occur precisely when the homogeneous problem has an eigenfunction.

> [!example] L3: $y''+y=0$, general solution $y=c_1\cos x+c_2\sin x$
> | BCs | Equations | Outcome |
> |---|---|---|
> | $y(0)=0$, $y(\tfrac\pi2)=1$ | $c_1=0$, $c_2=1$ | **unique**: $y=\sin x$ |
> | $y(0)=0$, $y(\pi)=1$ | $c_1=0$, $-c_1=1$ | **no solution** (contradiction) |
> | $y(0)=0$, $y(\pi)=0$ | $c_1=0$, $-c_1=0$ | **family**: $y=c_2\sin x$ |
>
> In the last two rows $\sin x$ vanishes at *both* ends. It is an eigenfunction of the homogeneous problem, so $\det M=0$.

## 2. Eigenvalue problems: the three-case method
**Problem**: find $\lambda$ such that $y''+\lambda y=0$ with homogeneous BCs has a solution $y\not\equiv0$. The trivial solution $y\equiv0$ always works and is never interesting.

**Method**: the auxiliary equation $m^2+\lambda=0$ gives $m=\pm\sqrt{-\lambda}$, so the solution form depends on the sign of $\lambda$. Always cover all three cases:

| Case | Auxiliary roots | General solution |
|---|---|---|
| $\lambda=-k^2<0$ ($k>0$) | $\pm k$ (real, distinct) | $y=c_1e^{kx}+c_2e^{-kx}=A\cosh kx+B\sinh kx$ |
| $\lambda=0$ | $0,0$ (repeated) | $y=c_1x+c_2$ |
| $\lambda=k^2>0$ ($k>0$) | $\pm jk$ (imaginary) | $y=c_1\sin kx+c_2\cos kx$ |

Then impose the BCs. In each case, either the only solution is $c_1=c_2=0$ (so no eigenvalue in that range), or a condition on $k$ emerges. That condition is the **eigenvalue equation**.

> [!tip] Taking $k>0$ loses nothing
> $\sin(-kx)=-\sin kx$ is just a rescaled eigenfunction, and $\cosh$ is even. So restricting to $k>0$ (and $n\geq1$) is enough.

### 2a. Dirichlet–Dirichlet: $y(0)=0$, $y(L)=0$. Derivation in full
**Case $\lambda=-k^2<0$.** $y=A\cosh kx+B\sinh kx$.
- $y(0)=A=0$.
- $y(L)=B\sinh kL=0$. But $\sinh kL>0$ for $k,L>0$, so $B=0$.
- Only the trivial solution: **no negative eigenvalues**.

**Case $\lambda=0$.** $y=c_1x+c_2$.
- $y(0)=c_2=0$.
- $y(L)=c_1L=0$, so $c_1=0$.
- Only the trivial solution: **$\lambda=0$ is not an eigenvalue**.

**Case $\lambda=k^2>0$.** $y=c_1\sin kx+c_2\cos kx$.
- $y(0)=c_2=0$.
- $y(L)=c_1\sin kL=0$. For a non-trivial solution take $c_1\neq0$, so $\sin kL=0$.
- Then $kL=n\pi$ for $n=1,2,3,\dots$ ($n=0$ gives $k=0$, which is excluded here).

$$
\boxed{\lambda_n=\Big(\frac{n\pi}{L}\Big)^2,\qquad y_n(x)=\sin\frac{n\pi x}{L},\qquad n=1,2,3,\dots}
$$

With $L=\pi$ (PS2 Q3a): $\lambda_n=n^2$ and $y_n=\sin nx$. Any constant multiple of $y_n$ is also an eigenfunction: the eigenvalues are unique, the eigenfunctions are not.

### 2b. Dirichlet–Neumann: $y(0)=0$, $y'(L)=0$
- $\lambda<0$: $A=0$, then $y'(L)=Bk\cosh kL=0$ with $\cosh kL\geq1$, so $B=0$. Trivial.
- $\lambda=0$: $c_2=0$, then $y'=c_1=0$. Trivial.
- $\lambda=k^2$: $c_2=0$, then $y'(L)=c_1k\cos kL=0$, so $\cos kL=0$ and $kL=\big(n-\tfrac12\big)\pi$.

$$
\lambda_n=\Big(\frac{(2n-1)\pi}{2L}\Big)^2,\qquad y_n=\sin\frac{(2n-1)\pi x}{2L},\qquad n=1,2,\dots
$$

With $L=\pi$ (PS2 Q3b): $\lambda_n=\big(n-\tfrac12\big)^2$ and $y_n=\sin\big(n-\tfrac12\big)x$.

### 2c. Neumann–Neumann: $y'(0)=0$, $y'(L)=0$. Here $\lambda=0$ *is* an eigenvalue
- $\lambda<0$: $y'=k(A\sinh kx+B\cosh kx)$. $y'(0)=kB=0$, then $y'(L)=kA\sinh kL=0$, so $A=0$. Trivial.
- $\lambda=0$: $y=c_1x+c_2$ with $y'=c_1=0$. **$c_2$ is free**, so $y_0=1$ is an eigenfunction with $\lambda_0=0$.
- $\lambda=k^2$: $y'=k(c_1\cos kx-c_2\sin kx)$. $y'(0)=0$ gives $c_1=0$, then $y'(L)=-kc_2\sin kL=0$, so $kL=n\pi$.

$$
\lambda_n=\Big(\frac{n\pi}{L}\Big)^2,\qquad y_n=\cos\frac{n\pi x}{L},\qquad n=0,1,2,\dots
$$

> [!warning] Always do the $\lambda=0$ case
> It is where the constant term $a_0/2$ of a Fourier cosine series comes from, e.g. in an insulated-rod heat problem. Skipping it loses marks.

### 2d. Robin condition: L3 $y(0)=0$, $y'(1)+y(1)=0$
- $\lambda=0$: $y=c_1x+c_2$. $c_2=0$, then $c_1+c_1=0$. Trivial.
- $\lambda=-k^2$: $y=c_1e^{kx}+c_2e^{-kx}$ with $c_2=-c_1$, i.e. $y=2c_1\sinh kx$. Then $y'(1)+y(1)=2c_1(k\cosh k+\sinh k)=0$. But $k\cosh k+\sinh k>0$ for $k>0$, so $c_1=0$. Trivial.
- $\lambda=k^2$: $y=c_1\sin kx$ (from $y(0)=0$). Then $y'(1)+y(1)=c_1(k\cos k+\sin k)=0$, so

$$
k\cos k+\sin k=0\iff \tan k=-k .
$$

This has no closed form. The roots are the intersections of the graphs of $k$ and $-\tan k$, and there is one in each interval $\big((n-\tfrac12)\pi,\,n\pi\big)$:

$$
k_1=2.029,\ k_2=4.913,\ k_3=7.979,\ k_4=11.086\ \Rightarrow\ \lambda_n=k_n^2=4.116,\ 24.139,\ 63.66,\ 122.89,\qquad y_n=\sin k_nx.
$$

As $n\to\infty$, $k_n\to\big(n-\tfrac12\big)\pi$: the roots approach the asymptotes of $\tan$.

![[m2048_ode_eigen_tan.png|640]]

### Standard eigenproblem table ($X''+\lambda X=0$ on $[0,L]$). Memorise this, but derive it in the exam
| BCs | $\lambda_n$ | $X_n$ | $n$ |
|---|---|---|---|
| $X(0)=X(L)=0$ | $(n\pi/L)^2$ | $\sin(n\pi x/L)$ | $1,2,\dots$ |
| $X'(0)=X'(L)=0$ | $(n\pi/L)^2$ | $\cos(n\pi x/L)$ | $0,1,2,\dots$ |
| $X(0)=0,\ X'(L)=0$ | $\big((2n-1)\pi/2L\big)^2$ | $\sin\big((2n-1)\pi x/2L\big)$ | $1,2,\dots$ |
| $X'(0)=0,\ X(L)=0$ | $\big((2n-1)\pi/2L\big)^2$ | $\cos\big((2n-1)\pi x/2L\big)$ | $1,2,\dots$ |
| periodic on $[-L,L]$ | $(n\pi/L)^2$ | $\cos(n\pi x/L)$ and $\sin(n\pi x/L)$ | $0,1,\dots$ |

> [!important] Sign convention in PDE questions
> Exams often write the separated equation as $X''-\lambda X=0$ (2025/26 A2). Then the oscillatory case is $\lambda=-k^2<0$ and the eigenvalues come out **negative**: $\lambda_n=-n^2$. Read the given form carefully and adapt the three cases to it.

## 3. Properties of eigenvalues and eigenfunctions (Notes §1.2.1)
For $y''+\lambda y=0$, $y(0)=y(\pi)=0$ (and, via Sturm–Liouville, far more generally):
1. The eigenvalues are **real**.
2. Eigenfunctions of different eigenvalues are **orthogonal**: $\int_0^\pi\sin mx\sin nx\,dx=0$ for $m\neq n$.
3. $\lambda_1<\lambda_2<\dots\to\infty$.
4. $y_n$ has exactly $n-1$ zeros strictly inside the interval.
5. The eigenfunctions are **complete**, so any reasonable $f$ can be expanded as $\sum a_ny_n$. **This is exactly a Fourier series** and leads into Block 2.

**Proof of orthogonality** (from the ODE, without integrating trig products). Let $y_m''=-\lambda_my_m$ and $y_n''=-\lambda_ny_n$ with the same homogeneous BCs. Then
$$
(\lambda_n-\lambda_m)\int_0^Ly_my_n\,dx=\int_0^L\big(y_m''y_n-y_n''y_m\big)dx=\Big[y_m'y_n-y_n'y_m\Big]_0^L-\int_0^L(y_m'y_n'-y_n'y_m')\,dx .
$$
The last integral is identically zero. For Dirichlet or Neumann BCs the boundary bracket also vanishes, because every term contains a factor $y$ or $y'$ that is zero at the ends. So $\lambda_m\neq\lambda_n\Rightarrow\int_0^Ly_my_n\,dx=0$ ∎.

*(Not examinable: Sturm–Liouville form $(py')'-qy+\lambda wy=0$ generalises all of this with weight $w(x)$.)*

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]
- Practice: [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] (PS2 Q1–Q3)
- Used in: wave, heat and Laplace equations (Block 4)

## Sources
- Lecture 3; Appendix L3 Eigenvalue Problems (Gan Khong Wui); Appendix L1–2 (BC types); Lecture Notes §1.2
