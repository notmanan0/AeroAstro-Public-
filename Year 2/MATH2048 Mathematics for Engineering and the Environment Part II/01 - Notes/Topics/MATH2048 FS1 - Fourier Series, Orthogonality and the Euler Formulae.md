---
title: "MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 2: Fourier Series"
order: 4
tags:
  - math2048
  - fourier-series
  - orthogonality
aliases: ["MATH2048 Lecture 4", "MATH2048 Lecture 5", "Euler formulae (Fourier)"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
next_topics: ["[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
key_concepts: ["[[Fourier Series]]", "[[Orthogonality of Trigonometric Functions]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture4_FourierSeries1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture5_FourierSeries2.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 2)"]
---

# MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae

> [!abstract] Summary
> A periodic function can be written as a sum of sines and cosines:
> $$f(x)=\tfrac12a_0+\sum_{n=1}^\infty\big[a_n\cos\tfrac{n\pi x}{\ell}+b_n\sin\tfrac{n\pi x}{\ell}\big],\qquad \text{period }2\ell .$$
> The coefficients come from **orthogonality**: multiply by one basis function and integrate over a period, and every term but one vanishes. This gives the **Euler formulae**. In practice a Fourier series question is 90% integration by parts plus two identities, $\sin n\pi=0$ and $\cos n\pi=(-1)^n$.

## Key Concepts
- [[Fourier Series]] · [[Orthogonality of Trigonometric Functions]] · [[ODE Eigenvalue Problems]] (the sines and cosines *are* eigenfunctions)

---

## 1. Definition (L4)
Let $f$ be $2\pi$-periodic: $f(x+2\pi)=f(x)$, and hence $f(x+2k\pi)=f(x)$ for all $k\in\mathbb Z$. Its Fourier series is

$$
f(x)=\frac12a_0+\sum_{n=1}^{\infty}\big[a_n\cos nx+b_n\sin nx\big].
$$

Every term has period $2\pi$ (because $\cos n(x+2\pi)=\cos nx$), so **only periodic functions** can be represented. A function given on a finite interval is implicitly **extended periodically**.

**General period $2\ell$** (L6 onwards): replace $nx$ by $n\pi x/\ell$. The $2\pi$ case is $\ell=\pi$.

### Identities you will use constantly
| | $n\in\mathbb Z$ |
|---|---|
| $\sin n\pi$ | $0$ |
| $\cos n\pi$ | $(-1)^n$ |
| $\sin\big(n+\tfrac12\big)\pi$ | $(-1)^n$ |
| $\cos\big(n+\tfrac12\big)\pi$ | $0$ |
| $1-(-1)^n$ | $0$ ($n$ even), $2$ ($n$ odd) |

## 2. Orthogonality (L4–5, PS2 FS Q1)
For integers $m,n\geq1$:

$$
\int_{-\ell}^{\ell}\cos\frac{m\pi x}{\ell}\cos\frac{n\pi x}{\ell}\,dx=\ell\,\delta_{mn},\qquad
\int_{-\ell}^{\ell}\sin\frac{m\pi x}{\ell}\sin\frac{n\pi x}{\ell}\,dx=\ell\,\delta_{mn},\qquad
\int_{-\ell}^{\ell}\cos\frac{m\pi x}{\ell}\sin\frac{n\pi x}{\ell}\,dx=0 ,
$$

with the exception $\int_{-\ell}^{\ell}\cos^2(0)\,dx=2\ell$ for $m=n=0$. Here $\delta_{mn}$ is the Kronecker delta ($1$ if $m=n$, else $0$).

**Proof** (write $k=\pi/\ell$ for brevity).

*Case $m\neq n$*: use the product-to-sum identities.
$$
2\cos mkx\cos nkx=\cos(m-n)kx+\cos(m+n)kx .
$$
$m\pm n$ is a non-zero integer, and $\int_{-\ell}^{\ell}\cos pkx\,dx=\Big[\dfrac{\sin pkx}{pk}\Big]_{-\ell}^{\ell}=\dfrac{2\sin p\pi}{pk}=0$ for every integer $p\neq0$. So the integral is $0$. The sine product works the same way using $2\sin A\sin B=\cos(A-B)-\cos(A+B)$.

*Mixed product*: $\cos mkx\,\sin nkx$ is (even) × (odd) = odd, and the integral of an odd function over a symmetric interval is $0$, for **all** $m,n$ including $m=n$.

*Case $m=n\geq1$*: $\cos^2A=\tfrac12(1+\cos2A)$, so
$$
\int_{-\ell}^{\ell}\cos^2nkx\,dx=\frac12\int_{-\ell}^{\ell}dx+\frac12\underbrace{\int_{-\ell}^{\ell}\cos2nkx\,dx}_{=0}=\ell .
$$
Likewise $\sin^2A=\tfrac12(1-\cos2A)$ gives $\ell$. ∎

> [!note] Analogy with vectors
> $\{\cos nkx,\sin nkx\}$ behave like $\hat{\mathbf i},\hat{\mathbf j},\dots$ with the inner product $\langle f,g\rangle=\int_{-\ell}^{\ell}fg\,dx$. The Euler formulae are just "components equal dot products": $b_m=\langle f,\sin\rangle/\langle\sin,\sin\rangle$.
>
> These functions are the eigenfunctions of $y''+\lambda y=0$ with **periodic** BCs $y(-\ell)=y(\ell)$, $y'(-\ell)=y'(\ell)$. Their orthogonality is the Sturm–Liouville property from [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]].

## 3. The Euler formulae: derivation (L4)
Multiply the series by $\sin\frac{m\pi x}\ell$ and integrate over one period. Swapping $\int$ and $\sum$ is allowed for these series:

$$
\int_{-\ell}^{\ell}f\sin\tfrac{m\pi x}{\ell}\,dx=\tfrac12a_0\underbrace{\int\sin\tfrac{m\pi x}\ell}_{0}+\sum_n a_n\underbrace{\int\cos\tfrac{n\pi x}\ell\sin\tfrac{m\pi x}\ell}_{0}+\sum_n b_n\underbrace{\int\sin\tfrac{n\pi x}\ell\sin\tfrac{m\pi x}\ell}_{\ell\delta_{mn}}=\ell\,b_m .
$$

Only the $n=m$ term survives. The cosine case is identical.

$$
\boxed{a_n=\frac1\ell\int_{-\ell}^{\ell}f(x)\cos\frac{n\pi x}{\ell}\,dx,\qquad b_n=\frac1\ell\int_{-\ell}^{\ell}f(x)\sin\frac{n\pi x}{\ell}\,dx,\qquad n=0,1,2,\dots}
$$

**Why $\tfrac12a_0$?** Multiplying by $1$ and integrating gives $\int f=\tfrac12a_0\cdot2\ell$, so $a_0=\tfrac1\ell\int f$. This is exactly the $a_n$ formula at $n=0$, and the $\tfrac12$ in the series makes one formula work for all $n$. Also, **$\tfrac12a_0$ is the mean value of $f$ over a period**.

*Check*: $f\equiv1$ gives $a_0=\tfrac1\pi\cdot2\pi=2$, all other coefficients are $0$, and $f=\tfrac12\cdot2=1$ ✔.

> [!tip] Any full period works
> The integral can be over **any** interval of length $2\ell$, e.g. $[0,2\ell]$ instead of $[-\ell,\ell]$. Pick whichever matches the definition of $f$.

## 4. Worked examples (L5), by brute force
### Sawtooth: $f(x)=x$ on $(-\pi,\pi)$, period $2\pi$
- $a_0=\frac1\pi\int_{-\pi}^\pi x\,dx=\frac1\pi\big[\tfrac{x^2}2\big]_{-\pi}^{\pi}=0$.
- $a_n$: with $u=x$ and $dv=\cos nx\,dx$,
$$
a_n=\frac1\pi\Big(\Big[\frac{x\sin nx}{n}\Big]_{-\pi}^{\pi}-\int_{-\pi}^{\pi}\frac{\sin nx}{n}dx\Big)=\frac1\pi\Big(0+\Big[\frac{\cos nx}{n^2}\Big]_{-\pi}^{\pi}\Big)=\frac1\pi\cdot\frac{(-1)^n-(-1)^n}{n^2}=0 .
$$
- $b_n$: with $u=x$ and $dv=\sin nx\,dx$,
$$
b_n=\frac1\pi\Big(\Big[-\frac{x\cos nx}{n}\Big]_{-\pi}^{\pi}+\int_{-\pi}^{\pi}\frac{\cos nx}{n}dx\Big)=\frac1\pi\Big(-\frac{\pi(-1)^n+\pi(-1)^n}{n}+0\Big)=\frac{2(-1)^{n+1}}{n}.
$$

$$
x=2\Big(\sin x-\frac{\sin2x}2+\frac{\sin3x}3-\dots\Big)=\sum_{n=1}^\infty\frac{2(-1)^{n+1}}{n}\sin nx,\qquad -\pi<x<\pi .
$$

![[m2048_fs_sawtooth_gibbs.png|680]]

At the jumps $x=\pm\pi$ the series gives $0$, the average of $\pi$ and $-\pi$ ([[Fourier's Theorem]]). Near each jump the partial sums overshoot by about **8.95% of the jump size**. For the sawtooth that is $\approx0.56$ above $\pi$; numerically, $N=50$ gives 8.0%, $N=200$ gives 8.7% and $N=1000$ gives 8.9%. The overshoot does not shrink as $N$ grows, it only gets narrower. This is the **Gibbs phenomenon** (not examinable, but it explains the plots).

### Tent: $f(x)=|x|$ on $(-\pi,\pi)$
- $a_0=\frac1\pi\Big[\int_{-\pi}^0(-x)dx+\int_0^\pi x\,dx\Big]=\frac1\pi\Big[\frac{\pi^2}2+\frac{\pi^2}2\Big]=\pi$.
- $a_n=\frac1\pi\Big[\int_{-\pi}^0(-x)\cos nx\,dx+\int_0^\pi x\cos nx\,dx\Big]$. Integrating each by parts, using $\int x\cos nx\,dx=\frac{x\sin nx}n+\frac{\cos nx}{n^2}$:
$$
a_n=\frac1\pi\Big[-\Big(\frac{1}{n^2}-\frac{(-1)^n}{n^2}\Big)+\Big(\frac{(-1)^n}{n^2}-\frac1{n^2}\Big)\Big]=\frac{2}{\pi n^2}\big[(-1)^n-1\big]=\begin{cases}-\dfrac{4}{\pi n^2}&n\text{ odd}\\[4pt]0&n\text{ even}\end{cases}
$$
- $b_n=0$. This is quickest by symmetry ([[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence|FS2]]).

$$
|x|=\frac\pi2-\frac4\pi\Big(\cos x+\frac{\cos3x}{9}+\frac{\cos5x}{25}+\dots\Big)
$$

![[m2048_fs_tent_convergence.png|680]]

> [!note] Smoothness sets the decay rate
> - The sawtooth has a **jump**, and $b_n\sim1/n$: slow, with Gibbs overshoot.
> - The tent is **continuous** but has a kink, and $a_n\sim1/n^2$: fast, uniform convergence.
>
> Rule of thumb: each extra degree of smoothness buys another factor of $1/n$.

## 5. Summing series with Fourier series (L5)
Evaluate a known series at a clever point.

Tent at $x=0$: $0=\frac\pi2-\frac4\pi\sum_{n\text{ odd}}\frac1{n^2}$, so
$$
\sum_{n\text{ odd}}\frac1{n^2}=1+\frac19+\frac1{25}+\dots=\frac{\pi^2}{8}.
$$

Sawtooth at $x=\frac\pi2$ (Notes §2.3.1): the series gives $2\big(1-\frac13+\frac15-\dots\big)=f(\tfrac\pi2)=\frac\pi2$, so
$$
1-\frac13+\frac15-\frac17+\dots=\frac\pi4\qquad\text{(Leibniz; SymPy ✔)}.
$$

Similarly, the series for $x^2$ at $x=\pi$ gives $\sum_{n\geq1}\frac1{n^2}=\frac{\pi^2}6$ ([[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series|FS3]]).

> [!warning] At a jump the series gives the average, not $f$
> If the chosen point is a discontinuity, set the series equal to $\frac12[f(x^-)+f(x^+)]$. PS3 Q1 depends on this.

> [!note] Extra points from the Lecture Notes (§2.2–2.3)
> - **Uniqueness**: the Euler formulae are explicit, so the Fourier series of a function is **unique**. This is why matching coefficients "by inspection" is legitimate.
> - **Any full period works** for the integrals, e.g. $\int_0^{2L}$ instead of $\int_{-L}^{L}$.
> - **Why the $\sin$ and $\cos$ functions are orthogonal**: they are Sturm–Liouville eigenfunctions (property 3). For other expansions, such as Fourier–Bessel series for vibrating plates, that general theory is much easier than explicit integration.
> - **Parseval's theorem** (not examinable): $\int_{-L}^{L}f^2\,dx=L\big[\tfrac12a_0^2+\sum(a_n^2+b_n^2)\big]$. In words, the "power" of $f$ equals the sum of squares of its components.

## Method checklist
1. Identify the period $2\ell$ and sketch the extended function.
2. Check for even or odd symmetry, which kills half the coefficients ([[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence|FS2]]).
3. Compute $a_0$ **separately**. The general $a_n$ formula often has $n$ in the denominator.
4. Integrate by parts. Simplify with $\sin n\pi=0$ and $\cos n\pi=(-1)^n$.
5. Write out the series, and state what it converges to at any jumps.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] · Next: [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]
- Practice: [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

## Sources
- Lectures 4–5; Lecture Notes Ch. 2. Coefficients verified in SymPy.
