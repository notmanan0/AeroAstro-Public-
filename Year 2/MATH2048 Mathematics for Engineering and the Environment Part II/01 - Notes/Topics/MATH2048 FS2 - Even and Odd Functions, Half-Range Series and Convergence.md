---
title: "MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 2: Fourier Series"
order: 5
tags:
  - math2048
  - fourier-series
  - half-range
  - convergence
aliases: ["MATH2048 Lecture 6", "Half range series", "Sine series", "Cosine series"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]"]
next_topics: ["[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
key_concepts: ["[[Half-Range Expansions]]", "[[Fourier's Theorem]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture6_FourierSeries3.pdf"]
---

# MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence

> [!abstract] Summary
> - **Symmetry**: an even $f$ has a cosine-only series ($b_n=0$); an odd $f$ has a sine-only series ($a_n=0$).
> - **Half-range expansions**: a function given only on $[0,L]$ can be extended three ways, each giving a different valid series:
>   - periodically, with period $L$;
>   - evenly, with period $2L$: a **cosine series**;
>   - oddly, with period $2L$: a **sine series**.
>
>   The sine and cosine series are exactly what separation of variables needs to match initial data in PDEs.
> - **Fourier's theorem**: under the Dirichlet conditions, the series converges to $f$ where $f$ is continuous, and to the **midpoint of the jump** where it isn't.

## Key Concepts
- [[Half-Range Expansions]] · [[Fourier's Theorem]] · [[Fourier Series]]

---

## 1. Even and odd functions
| | Definition | $\int_{-\ell}^{\ell}$ | Examples |
|---|---|---|---|
| even $g$ | $g(-x)=g(x)$ | $2\int_0^\ell g\,dx$ | $\cos$, $x^2$, $\lvert x\rvert$, $1$ |
| odd $h$ | $h(-x)=-h(x)$ | $0$ | $\sin$, $x$, $x^3$ |

**Proof of the odd case**: substitute $x\to-x$ in $\int_{-\ell}^0h\,dx=\int_\ell^0h(-u)(-du)=-\int_0^\ell h\,du$. This cancels the $\int_0^\ell$ part. The even case works the same way.

Products follow sign rules: even × even = even, odd × odd = even, even × odd = odd.

Since $\cos$ is even and $\sin$ is odd:

$$
f\text{ even}:\quad b_n=0,\quad a_n=\frac2\ell\int_0^\ell f\cos\frac{n\pi x}\ell dx;\qquad\qquad f\text{ odd}:\quad a_n=0,\quad b_n=\frac2\ell\int_0^\ell f\sin\frac{n\pi x}\ell dx .
$$

> [!tip] Check symmetry first
> It halves the work, and it also catches algebra errors: if you compute $b_n\neq0$ for an even function, something went wrong.

## 2. Half-range series (L6)
Given $f$ on $0\leq x<L$ only, there are three extensions:

| Extension | Period | Series | Coefficients |
|---|---|---|---|
| (a) **periodic** | $L$ ($\ell=L/2$) | full series in $\cos\frac{2n\pi x}{L}$ and $\sin\frac{2n\pi x}{L}$ | $a_n=\frac2L\int_0^Lf\cos\frac{2n\pi x}L$, $b_n=\frac2L\int_0^Lf\sin\frac{2n\pi x}L$ |
| (b) **even** | $2L$ ($\ell=L$) | cosine series $\frac12a_0+\sum a_n\cos\frac{n\pi x}L$ | $a_n=\frac2L\int_0^Lf\cos\frac{n\pi x}L\,dx$ |
| (c) **odd** | $2L$ ($\ell=L$) | sine series $\sum b_n\sin\frac{n\pi x}L$ | $b_n=\frac2L\int_0^Lf\sin\frac{n\pi x}L\,dx$ |

All three agree with $f$ on $(0,L)$. They differ outside it, and at the endpoints.

### Example (L6): $f(x)=x$ on $0\leq x<\pi$
**(a) Period $\pi$** ($\ell=\pi/2$, so the basis is $\cos2nx$ and $\sin2nx$):
- $a_0=\frac2\pi\int_0^\pi x\,dx=\pi$.
- $a_n=\frac2\pi\Big(\Big[\frac{x\sin2nx}{2n}\Big]_0^\pi-\int_0^\pi\frac{\sin2nx}{2n}dx\Big)=\frac2\pi\Big(0+\Big[\frac{\cos2nx}{4n^2}\Big]_0^\pi\Big)=0$.
- $b_n=\frac2\pi\Big(\Big[-\frac{x\cos2nx}{2n}\Big]_0^\pi+\int_0^\pi\frac{\cos2nx}{2n}dx\Big)=\frac2\pi\Big(-\frac{\pi}{2n}\Big)=-\frac1n$.

$$
x=\frac\pi2-\sum_{n=1}^\infty\frac{\sin2nx}{n}\qquad(0<x<\pi).
$$

**(b) Even extension, period $2\pi$**: this is the tent function, so $a_n=\frac2\pi\int_0^\pi x\cos nx\,dx=\frac{2}{\pi n^2}\big[(-1)^n-1\big]$ and $a_0=\pi$. The same answer as FS1, with half the work and no need to show $b_n=0$ by brute force.

**(c) Odd extension, period $2\pi$**: this is the sawtooth, so $b_n=\frac2\pi\int_0^\pi x\sin nx\,dx=\frac2\pi\Big[-\frac{x\cos nx}{n}\Big]_0^\pi=\frac{2(-1)^{n+1}}n$.

![[m2048_fs_half_range_extensions.png|680]]

### Example (Lecture Notes §2.3.2): half pulse, $f=1$ on $(0,\frac\ell2)$ and $0$ on $(\frac\ell2,\ell)$
**(i) Odd extension (sine series).**

$$b_n=\frac2\ell\int_0^{\ell/2}\sin\frac{n\pi x}\ell\,dx=\frac{2}{n\pi}\Big(1-\cos\frac{n\pi}{2}\Big),$$

so

$$f=\frac2\pi\Big[\sin\frac{\pi x}\ell+\sin\frac{2\pi x}\ell+\frac13\sin\frac{3\pi x}\ell+\frac15\sin\frac{5\pi x}\ell+\frac13\sin\frac{6\pi x}\ell+\dots\Big].$$

**(ii) Even extension (cosine series).** $a_0=1$ and $a_n=\frac{2}{n\pi}\sin\frac{n\pi}2$, so

$$f=\frac12+\frac2\pi\Big[\cos\frac{\pi x}\ell-\frac13\cos\frac{3\pi x}\ell+\frac15\cos\frac{5\pi x}\ell-\dots\Big].$$

Both were checked in SymPy ✔. At the jump $x=\frac\ell2$, both series give $\frac12$.

> [!note] Which extension should you choose?
> - Pick the one whose extension is **continuous**: the even extension here. It converges fastest.
> - In PDEs the **boundary conditions choose for you**:
>   - $u=0$ at both ends (Dirichlet) gives a **sine** series;
>   - $u_x=0$ at both ends (Neumann) gives a **cosine** series.

## 3. Convergence: Fourier's theorem (L6)
**Dirichlet conditions**:
1. $f$ is bounded.
2. $f$ is periodic with period $2\ell$.
3. $f$ has finitely many extrema and discontinuities in one period.

**Theorem**: if $f$ satisfies the Dirichlet conditions, its Fourier series converges at every $x$, to

$$
S(x)=\begin{cases}f(x)&f\text{ continuous at }x,\\[3pt]\tfrac12\big[f(x^-)+f(x^+)\big]&f\text{ jumps at }x.\end{cases}
$$

> [!warning] Hidden discontinuities at the ends of the period
> $f(x)=x$ on $(-\pi,\pi)$ looks continuous, but its periodic extension jumps from $\pi$ to $-\pi$ at $x=\pm\pi$. That jump is why the series gives $0$ there.
>
> So always check whether $f(-\ell^+)=f(\ell^-)$. PS3 Q1 ($e^x$): the series at $x=\pm\pi$ is $\tfrac12(e^{-\pi}+e^\pi)=\cosh\pi$.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]] · Next: [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]
- Practice: [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]] (PS3 Q2 is a cosine half-range series)

## Sources
- Lecture 6; Lecture Notes Ch. 2. All three series verified in SymPy; the slide text lost the sign of $b_n=-1/n$ in (a).
