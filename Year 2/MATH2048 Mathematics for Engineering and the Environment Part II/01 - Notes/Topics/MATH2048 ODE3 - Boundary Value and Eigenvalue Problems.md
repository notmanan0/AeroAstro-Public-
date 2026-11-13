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
aliases: ["MATH2048 Lecture 3", "Eigenvalue problems", "Boundary value problems"]
date: 2026-10-30
status: lectured
coverage: "Lecture 3 (2 Oct 2024, Ian Hawke): initial against boundary value problems, the three outcomes for y'' + y = 0, and the eigenvalue problem y'' + λy = 0 with y(0) = 0, y'(1) + y(1) = 0 worked through all three cases. The standard eigenproblems in §4 are Problem Sheet 2 Q3 and the lecture notes, previewing the PDE block."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]", "[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
next_topics: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]"]
key_concepts: ["[[Boundary Value Problems]]", "[[ODE Eigenvalue Problems]]", "[[Auxiliary Equation]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 3.txt", "02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture3_(Eigenvalue Problems).pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.2)"]
---

# MATH2048 ODE3 - Boundary Value and Eigenvalue Problems

> [!abstract] Summary
> An initial value problem with the right number of conditions always fixes a unique solution, but a boundary value problem, with conditions at two different points, can have a unique solution, no solution or a one-parameter family of them. An eigenvalue problem is a boundary value problem with an unknown parameter $\lambda$, and the task is to find the values $\lambda_n$ (eigenvalues) for which a non-trivial solution $y_n$ (eigenfunction) exists, by working through $\lambda=0$, $\lambda<0$ and $\lambda>0$ separately. The same step is needed whenever a PDE is solved by separation of variables.

> [!summary]- Exam use: quick path
> - **Use it when:** an ODE comes with conditions at two points, or contains an unknown constant with homogeneous conditions, which is the spatial ODE of every separation-of-variables PDE (exam question A2).
> - **Assumptions:** linear second-order ODE; for eigenproblems the ODE and both boundary conditions are homogeneous, so $y\equiv0$ always works and is discarded; the parameter is real; $k>0$ when writing $\lambda=\pm k^2$.
> - **Method:** 1. Write the auxiliary equation; the root type depends on the sign of $\lambda$. 2. Case $\lambda=0$: general solution $c_1+c_2x$, apply both conditions. 3. Case $\lambda=-k^2$: exponentials or $\cosh$/$\sinh$, apply both conditions. 4. Case $\lambda=k^2$: $\cos$/$\sin$, apply both conditions and get an equation for $k$. 5. State $\lambda_n$, $y_n$ and the range of $n$.
> - **Common mistakes:** skipping the $\lambda=0$ case, which is an eigenvalue for Neumann conditions; stopping at "$c_2=0$" when the other factor ($\sin kL$, say) can vanish instead.
> - **Practise:** [[#Worked example: an eigenvalue problem]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q3: Eigenvalue problems|PS2 Q3]]

Two conditions are needed to fix the two constants of a second-order ODE, and for this purpose there is no conceptual difference between initial and boundary conditions. The difference is in what can go wrong. Initial conditions, both given at one point, launch the solution from a known state with a known slope, and it runs on from there; a unique solution always comes out. Boundary conditions pin the solution at two separate points, and the family of solutions may or may not be able to reach the second point.

The simple harmonic oscillator shows all three possibilities. With $y(0)=0$ every solution of $y''+y=0$ is a sine wave $c_2\sin x$ of adjustable height. Asking for $y(\pi/2)=1$ picks out exactly one height. Asking for $y(\pi)=1$ has no solution, because every sine wave returns to zero at $\pi$. And asking for $y(\pi)=0$ is satisfied by every height at once, so the conditions fix nothing.

That last, degenerate case is the useful one. An eigenvalue problem asks which values of a parameter in the equation produce exactly that degeneracy, a non-zero solution that satisfies homogeneous conditions at both ends. For a string or a rod those solutions are the natural mode shapes, and the PDE block builds every solution out of them.

---

## 1. Initial against boundary value problems

The general solution of a second-order linear ODE ([[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients|ODE1]], [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs|ODE2]]) is

$$
y=c_1y_1+c_2y_2+y_P,
$$

which is of limited use until $c_1$ and $c_2$ have values. Initial conditions are applied at one value of the independent variable, usually $t=0$ for problems in time: the value of $y$, its derivative, or a combination. Boundary conditions are applied at different values, usually the two ends of a spatial domain. An example of a boundary value problem is $y''+2y'+y=0$ with $y(0)+2y'(0)=0$ and $2y(1)-y'(1)=1$, conditions that mix the value and the derivative.

Solving it shows how mixed conditions are handled. The auxiliary equation $m^2+2m+1=(m+1)^2=0$ has the repeated root $m=-1$, so

$$
y=(c_1+c_2x)e^{-x},\qquad y'=\big(c_2-c_1-c_2x\big)e^{-x}.
$$

At $x=0$, $y(0)=c_1$ and $y'(0)=c_2-c_1$:

$$
c_1+2(c_2-c_1)=0\quad\Longrightarrow\quad c_1=2c_2 .
$$

At $x=1$, $y(1)=(c_1+c_2)e^{-1}$ and $y'(1)=-c_1e^{-1}$:

$$
2(c_1+c_2)e^{-1}+c_1e^{-1}=1\quad\Longrightarrow\quad(3c_1+2c_2)e^{-1}=1 .
$$

Substitute $c_1=2c_2$: $8c_2e^{-1}=1$, so $c_2=e/8$ and $c_1=e/4$. Hence

$$
y=\frac{(x+2)\,e^{1-x}}{8}.
$$

Check: $y(0)=e/4$, $y'(0)=-e/8$, and $e/4-2e/8=0$; $y(1)=3/8$, $y'(1)=-2/8$, and $2\cdot\tfrac38+\tfrac28=1$. The solution is unique, and the reason is in §2: the homogeneous version of this problem has only the zero solution.

Three types of boundary condition have standard names, and they become the vocabulary of the PDE block:

| Name | Condition | Meaning for heat in a bar |
|---|---|---|
| Dirichlet | $y=f$ | fixed temperature (or fixed displacement of a string) |
| Neumann | $y'=g$ | fixed heat flux; $y'=0$ is an insulated end (or a free string end) |
| Robin (mixed) | $y+cy'=h$ | heat loss balanced against the end temperature |

## 2. Three outcomes for the same ODE

The same ODE, $y''+y=0$, serves for all three cases. Its auxiliary equation is $m^2+1=0$, so $m=\pm j$ and

$$
y=c_1\cos x+c_2\sin x.
$$

Every case keeps $y(0)=0$, which gives

$$
c_1\cos0+c_2\sin0=0\quad\Longrightarrow\quad c_1=0,
$$

using $\cos0=1$ and $\sin0=0$. These special values, along with $\cos\pi=-1$, $\sin\pi=0$, $\cos\frac\pi2=0$ and $\sin\frac\pi2=1$, are needed throughout the module. Only the second condition changes.

With $y(\pi/2)=1$:

$$
c_1\cos\tfrac\pi2+c_2\sin\tfrac\pi2=1\quad\Longrightarrow\quad 0+c_2=1,
$$

so $c_2=1$ and the unique solution is $y=\sin x$.

With $y(\pi)=1$:

$$
c_1\cos\pi+c_2\sin\pi=1\quad\Longrightarrow\quad -c_1=1,
$$

which contradicts $c_1=0$. There is no solution: the general solution exists, but none of it satisfies both conditions.

With $y(\pi)=0$:

$$
c_1\cos\pi+c_2\sin\pi=0\quad\Longrightarrow\quad -c_1=0,
$$

which repeats $c_1=0$ and says nothing about $c_2$. Every $y=c_2\sin x$ works: a one-parameter family of solutions.

![[m2048_ode_bvp_outcomes.png|900]]

The pattern is general. In the last two cases $\sin x$ itself vanishes at both $0$ and $\pi$, so the homogeneous problem $y''+y=0$, $y(0)=y(\pi)=0$ has a non-zero solution. When that happens the two conditions are not independent, and the data either contradict each other (no solution) or agree (infinitely many). When the homogeneous problem has only $y\equiv0$, the solution is unique. This is the Fredholm alternative.

### Problem Sheet 2, Q2: the same three outcomes with a source

PS2 Q2 adds a source, $y''+\tfrac14y=1$. The complementary function comes from $m^2+\tfrac14=0$, $m=\pm\tfrac j2$, and a constant particular integral $y_P=A$ gives $\tfrac14A=1$, $A=4$, so

$$
y=4+c_1\cos\frac x2+c_2\sin\frac x2,\qquad y'=-\frac{c_1}2\sin\frac x2+\frac{c_2}2\cos\frac x2 .
$$

At $x=\pi$ the half-angle values are $\cos\frac\pi2=0$ and $\sin\frac\pi2=1$, so $y(\pi)=4+c_2$ and $y'(\pi)=-c_1/2$. At $x=0$, $y(0)=4+c_1$ and $y'(0)=c_2/2$.

(a) $y(0)=0$, $y(\pi)=2$: $4+c_1=0$ and $4+c_2=2$, so $c_1=-4$, $c_2=-2$ and the unique solution is $y=4-4\cos\frac x2-2\sin\frac x2$.

(b) $y'(0)=0$, $y'(\pi)=0$: $c_2/2=0$ and $-c_1/2=0$, so $c_1=c_2=0$ and the unique solution is the constant $y=4$.

(c) $y(0)=0$, $y'(\pi)=1$: the first gives $c_1=-4$, the second $-c_1/2=1$, so $c_1=-2$. The two conditions contradict each other and there is no solution.

(d) $y(0)+2y'(0)=0$, $y(\pi)-2y'(\pi)=0$: the first gives $4+c_1+c_2=0$ and the second gives $4+c_2+c_1=0$, the same equation. One constant stays free, so there is a family, $y=4-(4+c_2)\cos\frac x2+c_2\sin\frac x2$ for any $c_2$.

The homogeneous problems explain the pattern. In (c) and (d), with the source and the right-hand data removed, $\sin\frac x2$ (for c) and $\cos\frac x2-\sin\frac x2$ (for d) satisfy the homogeneous conditions, so those two problems can't be uniquely solvable; (c) happens to be inconsistent and (d) consistent. In (a) and (b) the homogeneous problem has only the zero solution, so the answer is unique. SymPy's `solve` on the two linear conditions returns exactly these four outcomes.

## 3. Eigenvalue problems

An eigenvalue problem is a boundary value problem whose ODE contains a parameter whose value isn't known in advance, with a completely specified set of homogeneous boundary conditions. The standard example is

$$
y''+\lambda y=0,\qquad y(0)=0,\qquad y'(1)+y(1)=0,
$$

a model of steady heat conduction in a bar: $y$ is the deviation from ambient temperature, the left end is held at ambient, and the right-hand condition balances the heat flux through the end against the end temperature. The task is to find every $\lambda$ that gives a solution other than $y\equiv0$, the trivial solution, which always works and is never interesting.

The auxiliary equation (with $m$ in place of $\lambda$, which is now taken) is

$$
m^2+\lambda=0\quad\Longrightarrow\quad m=\pm\sqrt{-\lambda},
$$

so the form of the solution depends on the sign of $\lambda$, and there is no shortcut: each case has to be worked separately. Writing $\lambda=-k^2$ or $\lambda=k^2$ with $k>0$ is purely notation that keeps the square roots tidy; the answer is converted back to $\lambda$ at the end.

| Case | Roots | General solution |
|---|---|---|
| $\lambda=0$ | $0$, repeated | $c_1+c_2x$ |
| $\lambda=-k^2<0$ | $\pm k$, real | $c_1e^{kx}+c_2e^{-kx}$ (or $A\cosh kx+B\sinh kx$) |
| $\lambda=k^2>0$ | $\pm jk$ | $c_1\cos kx+c_2\sin kx$ |

Restricting to $k>0$ loses nothing: $\sin(-kx)=-\sin kx$ is just a rescaled eigenfunction, and $\cosh$ is even.

### Worked example: an eigenvalue problem

**Case $\lambda=0$**. The roots are $0$ twice, so

$$
y=c_1+c_2x,\qquad y'=c_2.
$$

At $x=0$:

$$
y(0)=c_1=0.
$$

At $x=1$, using $c_1=0$:

$$
y'(1)+y(1)=c_2+(c_1+c_2)=2c_2=0\quad\Longrightarrow\quad c_2=0.
$$

Only the trivial solution, so $\lambda=0$ is not an eigenvalue.

**Case $\lambda=-k^2<0$**. The roots are $\pm k$, so

$$
y=c_1e^{kx}+c_2e^{-kx},\qquad y'=k\big(c_1e^{kx}-c_2e^{-kx}\big).
$$

At $x=0$:

$$
y(0)=c_1+c_2=0\quad\Longrightarrow\quad c_2=-c_1.
$$

At $x=1$, substituting $c_2=-c_1$:

$$
y'(1)+y(1)=kc_1\big(e^k+e^{-k}\big)+c_1\big(e^k-e^{-k}\big)
$$

$$
=c_1\big[2k\cosh k+2\sinh k\big]=0.
$$

For $k>0$ both $\cosh k$ and $\sinh k$ are positive, so the bracket is positive and $c_1=0$, then $c_2=0$. An argument without hyperbolic functions: for $k>0$, $e^k>1>e^{-k}$, so $e^k+e^{-k}$ and $e^k-e^{-k}$ are both positive. Only the trivial solution, so there are no negative eigenvalues.

**Case $\lambda=k^2>0$**. The roots are $\pm jk$, so

$$
y=c_1\cos kx+c_2\sin kx,\qquad y'=k\big(-c_1\sin kx+c_2\cos kx\big).
$$

At $x=0$:

$$
y(0)=c_1=0.
$$

At $x=1$, with $c_1=0$:

$$
y'(1)+y(1)=kc_2\cos k+c_2\sin k=c_2\big(\sin k+k\cos k\big)=0.
$$

Either $c_2=0$, which is the trivial solution again, or

$$
\sin k+k\cos k=0\quad\Longleftrightarrow\quad k=-\tan k.
$$

This equation has no closed-form solution, but plotting $k$ and $-\tan k$ shows it has infinitely many: $-\tan k$ runs from $+\infty$ to $-\infty$ between successive asymptotes at $\frac\pi2,\frac{3\pi}2,\dots$, so it crosses the line $k$ once in each interval $\big((n-\tfrac12)\pi,\,n\pi\big)$, and the roots can be labelled $k_1<k_2<\dots$ by the integers.

![[m2048_ode_eigen_tan.png|720]]

The eigenvalues and eigenfunctions are

$$
\lambda_n=k_n^2,\qquad y_n(x)=\sin k_nx,\qquad \text{where } k_n=-\tan k_n,\quad n=1,2,3,\dots
$$

> [!check] The first four roots (SciPy `brentq` on each interval)
> $k_n=2.0288,\ 4.9132,\ 7.9787,\ 11.0855$, so $\lambda_n=4.1159,\ 24.139,\ 63.659,\ 122.89$. Each $k_n$ lies just above $(n-\tfrac12)\pi$, by $0.458$, $0.201$, $0.125$ and $0.090$, so the roots approach the asymptotes of $\tan$ as $n$ grows.

The eigenfunctions look like Dirichlet sine modes near $x=0$, but at $x=1$ each ends with a slope equal to minus its value instead of at a zero: the Robin end lets heat leak out at a rate set by the end temperature. $y_n$ has $n-1$ zeros inside $(0,1)$.

![[m2048_ode_robin_eigenfunctions.png|760]]

If a number is wanted, Newton's method on $g(k)=\sin k+k\cos k$ converges fast. The derivative is

$$
g'(k)=\cos k+\cos k-k\sin k=2\cos k-k\sin k,
$$

and the iteration $k\leftarrow k-g(k)/g'(k)$ from $k=2$ gives $2.02905$, $2.028758$, $2.0287578$: six figures in three steps. Bisection on $(\pi/2,\pi)$ also works but gains only one binary digit per step; twelve halvings leave the bracket $(2.02869,\,2.02907)$.

What counts as an answer: the eigenvalue, the eigenfunction, and, when the eigenvalue has no closed form, the condition that determines it. As with eigenvectors in linear algebra, an eigenfunction is only fixed up to a constant multiple, the free $c_2$ here.

## 4. The standard eigenproblems (PS2 Q3, preview of the PDE block)

The same three-case routine gives the eigenproblems that every PDE in the module reduces to. For $y''+\lambda y=0$ on $[0,L]$ with Dirichlet conditions $y(0)=y(L)=0$:

**$\lambda=-k^2$.** With $y=A\cosh kx+B\sinh kx$, $y(0)=A=0$, then $y(L)=B\sinh kL=0$, and $\sinh kL>0$ forces $B=0$. Trivial.

**$\lambda=0$.** With $y=c_1+c_2x$, $y(0)=c_1=0$, then $y(L)=c_2L=0$. Trivial.

**$\lambda=k^2$.** With $y=c_1\cos kx+c_2\sin kx$, $y(0)=c_1=0$, then $y(L)=c_2\sin kL=0$. For $c_2\neq0$, $\sin kL=0$ is required, so $kL=n\pi$ with $n=1,2,\dots$ ($n=0$ would give $k=0$, excluded in this case). Hence

$$
\lambda_n=\Big(\frac{n\pi}{L}\Big)^2,\qquad y_n=\sin\frac{n\pi x}{L},\qquad n=1,2,3,\dots
$$

With $L=\pi$ (PS2 Q3a) this is $\lambda_n=n^2$, $y_n=\sin nx$.

For $y(0)=0$ and $y'(L)=0$ the first two cases are trivial in the same way (in the $\lambda<0$ case $y'(L)=Bk\cosh kL$ with $\cosh kL\geq1$), and the third gives $c_1=0$, then $y'(L)=c_2k\cos kL=0$, so $kL=(n-\tfrac12)\pi$:

$$
\lambda_n=\Big(\frac{(2n-1)\pi}{2L}\Big)^2,\qquad y_n=\sin\frac{(2n-1)\pi x}{2L},\qquad n=1,2,\dots
$$

With $L=\pi$ (PS2 Q3b) this is $\lambda_n=(n-\tfrac12)^2$, $y_n=\sin(n-\tfrac12)x$.

With Neumann conditions at both ends, $y'(0)=y'(L)=0$, the $\lambda=0$ case is not trivial: $y=c_1+c_2x$ has $y'=c_2=0$ at both ends with $c_1$ free, so the constant $y_0=1$ is an eigenfunction with $\lambda_0=0$. The positive case gives $\cos(n\pi x/L)$. This is where the constant term of a Fourier cosine series comes from in an insulated-rod heat problem ([[MATH2048 PDE3 - The Heat Equation|PDE3]]), which is why skipping $\lambda=0$ costs marks.

| Boundary conditions on $[0,L]$ | $\lambda_n$ | $y_n$ | $n$ |
|---|---|---|---|
| $y(0)=y(L)=0$ | $(n\pi/L)^2$ | $\sin(n\pi x/L)$ | $1,2,\dots$ |
| $y'(0)=y'(L)=0$ | $(n\pi/L)^2$ | $\cos(n\pi x/L)$ | $0,1,2,\dots$ |
| $y(0)=0,\ y'(L)=0$ | $\big((2n-1)\pi/2L\big)^2$ | $\sin\big((2n-1)\pi x/2L\big)$ | $1,2,\dots$ |
| $y'(0)=0,\ y(L)=0$ | $\big((2n-1)\pi/2L\big)^2$ | $\cos\big((2n-1)\pi x/2L\big)$ | $1,2,\dots$ |

The table is a summary only: exam questions expect the three cases derived each time. Past papers also write the separated equation as $X''-\lambda X=0$ (2025/26 A2), in which case the oscillatory case is $\lambda=-k^2$ and the eigenvalues come out negative, $\lambda_n=-n^2$; read the given form before choosing signs.

### Properties of the eigenvalues and eigenfunctions

For $y''+\lambda y=0$ with Dirichlet or Neumann conditions, the eigenvalues are real and increase without bound, $\lambda_1<\lambda_2<\dots\to\infty$; $y_n$ has $n-1$ zeros inside the interval; and eigenfunctions belonging to different eigenvalues are orthogonal. The orthogonality can be shown from the ODE alone. Take $y_m''=-\lambda_my_m$ and $y_n''=-\lambda_ny_n$ with the same homogeneous conditions. Multiply the first by $y_n$ and the second by $y_m$:

$$
y_m''y_n=-\lambda_my_my_n,\qquad y_n''y_m=-\lambda_ny_ny_m .
$$

Subtract the first from the second:

$$
y_n''y_m-y_m''y_n=(\lambda_m-\lambda_n)y_my_n .
$$

Integrate over the interval and swap the sign of both sides:

$$
(\lambda_n-\lambda_m)\int_0^Ly_my_n\,dx=\int_0^L\big(y_m''y_n-y_n''y_m\big)\,dx.
$$

Integrate each term on the right by parts, $\int_0^Ly_m''y_n\,dx=\big[y_m'y_n\big]_0^L-\int_0^Ly_m'y_n'\,dx$ and likewise with $m$ and $n$ swapped:

$$
=\Big[y_m'y_n-y_n'y_m\Big]_0^L-\int_0^L\big(y_m'y_n'-y_n'y_m'\big)\,dx.
$$

The last integral is identically zero. With Dirichlet or Neumann conditions every term of the boundary bracket contains a factor that vanishes at the ends, so for $\lambda_m\neq\lambda_n$, $\int_0^Ly_my_n\,dx=0$.

The Robin condition of the worked example works too. At $x=1$ both eigenfunctions satisfy $y'=-y$, so the bracket there is $(-y_m)y_n-(-y_n)y_m=0$, and at $x=0$ both vanish. The functions $\sin k_nx$ with $k_n=-\tan k_n$ are therefore orthogonal on $[0,1]$, even though the $k_n$ are not evenly spaced.

> [!check] Orthogonality of the Robin eigenfunctions
> Numerical quadrature gives $\int_0^1\sin(2.02876x)\sin(4.91318x)\,dx\approx-6\times10^{-17}$, zero to rounding, while $\int_0^1\sin^2(2.02876x)\,dx=0.5977$, not $\tfrac12$: the norm is not the Dirichlet one, so it has to be computed for each problem.

This orthogonality, together with completeness (any reasonable function can be expanded in the $y_n$), is what makes Fourier series work (Block 2).

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]] · Next: [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]
- Used in every separation-of-variables PDE: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]], [[MATH2048 PDE3 - The Heat Equation]], [[MATH2048 PDE5 - Laplace's Equation]]
- Concepts: [[Boundary Value Problems]] · [[ODE Eigenvalue Problems]] · [[Auxiliary Equation]]

## Sources

- Lecture 3 recording, 2 Oct 2024 (Ian Hawke): `MATH2048 Lecture 3.txt`
- Slides `Lecture3_ODE.pdf`; appendix on eigenvalue problems (Gan Khong Wui); appendix to Lectures 1–2 (boundary condition types)
- Lecture notes §1.2
- Problem Sheet 2; worked solutions in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]

## Self-study tasks

Lecture 3 set the $\lambda<0$ case as a slide exercise (then worked it), and pointed to the first two problem sheets and the first STACK assignment for practice (ll. 449–454).

### Core

- [ ] Lecturer-set (slide 13 exercise): show the case $\lambda=-k^2$ of $y''+\lambda y=0$, $y(0)=0$, $y'(1)+y(1)=0$ gives only the trivial solution. → [[#Worked example: an eigenvalue problem]]
- [ ] Solve the slide's mixed-condition example $y''+2y'+y=0$, $y(0)+2y'(0)=0$, $2y(1)-y'(1)=1$ (suggested, not lecturer-set). Answer: $y=\frac18(x+2)e^{1-x}$. → [[#1. Initial against boundary value problems]]
- [ ] PS2 Q2: for $y''+\tfrac14y=1$, decide which of the four boundary value problems has a unique solution, none, or a family. Answers: (a) unique, $y=4-4\cos\frac x2-2\sin\frac x2$; (b) unique, $y=4$; (c) none; (d) a family. → [[#Problem Sheet 2, Q2: the same three outcomes with a source]]
- [ ] PS2 Q3(a)–(b), the Dirichlet and Dirichlet–Neumann eigenproblems on $[0,\pi]$. → [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q3: Eigenvalue problems]]

### Further practice

- [ ] Derive the Neumann–Neumann eigenproblem and explain why $\lambda=0$ is an eigenvalue (suggested, not lecturer-set). → [[#4. The standard eigenproblems (PS2 Q3, preview of the PDE block)]]
- [ ] Find $k_1$ for $k=-\tan k$ to three decimal places by Newton's method or bisection on $(\pi/2,\pi)$, and check it against 2.029 (suggested, not lecturer-set). → [[#Worked example: an eigenvalue problem]]
- [ ] Prove orthogonality of eigenfunctions from the ODE by integrating by parts (suggested, not lecturer-set). → [[#Properties of the eigenvalues and eigenfunctions]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lecture 3 slips
> | Where | Transcript says | Correct |
> |---|---|---|
> | ll. 89–108 | evaluates $\cos m$, $\sin m$ at $\pi/2$, then corrects himself | $c_1\cos\frac\pi2+c_2\sin\frac\pi2=1$; $m$ was $\pm j$ in the exponent, not part of the cosine |
> | l. 112 | "C1 is equal to 1, C2 is equal to 0. Therefore, y is equal to sine x" | $c_1=0$, $c_2=1$, as the slide has |
> | l. 133 | the second condition "tells us that one has to equal C1" | $1=-c_1$, since $\cos\pi=-1$; l. 135 then says "minus 1" |
> | l. 295 | $y'=k(c_1e^{kx}-c_2e^{kx})$ | $k(c_1e^{kx}-c_2e^{-kx})$ |
> | l. 382 | "0 is equal to the derivative evaluated at 0" | at $x=1$ |
