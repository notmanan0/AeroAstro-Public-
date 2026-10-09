---
title: "MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 2: Fourier Series"
order: 6
tags:
  - math2048
  - fourier-series
  - complex-fourier-series
aliases: ["MATH2048 Lecture 7", "MATH2048 Lecture 8", "Term-by-term differentiation"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
next_topics: ["[[MATH2048 TR1 - Fourier Transforms]]"]
key_concepts: ["[[Complex Fourier Series]]", "[[Fourier's Theorem]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture7_FourierSeries4.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture8_FourierSeries5.pdf"]
---

# MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series

> [!abstract] Summary
> - **Integration** term by term is *always* allowed. It is a quick way to build new series, e.g. $x^2\to x^3$.
> - **Differentiation** term by term needs $f$ to be **continuous including across the period ends**, and $f'$ to be piecewise smooth. Differentiating the sawtooth series gives nonsense, a divergent series for $1$.
> - The **complex Fourier series** $f=\sum_{-\infty}^{\infty}c_ne^{jn\pi x/\ell}$ with $c_n=\frac1{2\ell}\int f e^{-jn\pi x/\ell}dx$ packs $a_n,b_n$ into one formula. It is the stepping stone to the Fourier transform.

## Key Concepts
- [[Complex Fourier Series]] · [[Fourier's Theorem]] · [[Fourier Series]]

---

## 1. Differentiation (L7)
**Example: $x^2$ on $[-\pi,\pi]$** (even, so it has a cosine series).
- $a_0=\frac2\pi\int_0^\pi x^2dx=\frac{2\pi^2}3$.
- $a_n=\frac2\pi\int_0^\pi x^2\cos nx\,dx$. Integrate by parts twice:

$$
\int x^2\cos nx\,dx=\frac{x^2\sin nx}{n}+\frac{2x\cos nx}{n^2}-\frac{2\sin nx}{n^3},
$$

so $a_n=\frac2\pi\cdot\frac{2\pi(-1)^n}{n^2}=\frac{4(-1)^n}{n^2}$.

$$
x^2=\frac{\pi^2}{3}+\sum_{n=1}^\infty\frac{4(-1)^n}{n^2}\cos nx,\qquad -\pi\leq x\leq\pi .
$$

This extension is continuous, because $(-\pi)^2=\pi^2$. At $x=\pi$: $\pi^2=\frac{\pi^2}3+4\sum\frac1{n^2}$, so $\displaystyle\sum_{n=1}^\infty\frac1{n^2}=\frac{\pi^2}6$ (the Basel sum).

**Differentiate term by term**: $2x=\sum\frac{4(-1)^{n+1}}{n}\sin nx$, i.e. $x=\sum\frac{2(-1)^{n+1}}n\sin nx$. This is exactly the sawtooth series ✔. It is legitimate because $x^2$ is continuous and periodic, with a piecewise-smooth derivative.

**Differentiate again**: "$1=\sum2(-1)^{n+1}\cos nx$". At $x=0$ the partial sums are $2,0,2,0,\dots$, which **do not converge** ✘. The correct series for $1$ is just $1$.

> [!important] When can you differentiate term by term?
> The Dirichlet conditions plus two more:
> 4. $f$ is **continuous everywhere**, including $f(-\ell)=f(\ell)$ (no hidden jump at the period ends).
> 5. $f'$ is piecewise smooth.
>
> - The sawtooth $x$ fails condition 4: it jumps from $\pi$ to $-\pi$.
> - The tent $|x|$ and $x^2$ pass.
>
> *Why*: differentiating multiplies $b_n$ by $n$. The sawtooth's $1/n$ coefficients become $O(1)$, which cannot converge.

> [!example] Lecture Notes §2.5.1: a legitimate differentiation
> On $(-\pi,\pi)$, $f=x\sin x$ is even and continuous, with $f(\pm\pi)=0$. Its series is
>
> $$x\sin x=1-\tfrac12\cos x-2\sum_{n\geq2}\frac{(-1)^n}{n^2-1}\cos nx=1-\tfrac12\cos x-\frac{2\cos2x}{1\cdot3}+\frac{2\cos3x}{2\cdot4}-\dots$$
>
> Differentiating is allowed (conditions 4 and 5 hold), and it gives $\sin x+x\cos x$. Subtracting the $\sin x$ leaves
>
> $$x\cos x=-\tfrac12\sin x+\sum_{n\geq2}\frac{2n(-1)^n}{n^2-1}\sin nx .$$
>
> SymPy checks both sets of coefficients ✔.

> [!example] Lecture Notes §2.5.1: a failed differentiation
> The period-$2\pi$ extension of $x$ on $(0,2\pi)$ is $x=\pi-2\sum\frac{\sin nx}{n}$. But $f(0)=0\neq f(2\pi)=2\pi$, so there is a hidden jump.
> Differentiating gives $-2\sum\cos nx$, whose terms do not tend to $0$. The series diverges instead of giving $1$.

**Notes' summary of the conditions**: term-by-term differentiation needs (a) $f$ continuous on $(-\ell,\ell)$, (b) $f'$ to have a Fourier series, and (c) $f(-\ell)=f(\ell)$.

## 2. Integration (L7)
Integrating $\frac12a_0+\sum(a_n\cos nx+b_n\sin nx)$ term by term gives

$$
\int f\,dx=C+\frac12a_0x+\sum_{n=1}^\infty\frac{a_n\sin nx-b_n\cos nx}{n}.
$$

This is always valid, because integration *divides* by $n$ and so improves convergence. The $\frac12a_0x$ term is not itself a Fourier term: replace it with the sawtooth series for $x$.

**Example: $x^3$ from $x^2$.**
1. Integrate the $x^2$ series from $0$ to $x$: $\frac{x^3}3=\frac{\pi^2}3x+\sum\frac{4(-1)^n}{n^3}\sin nx$. The constant $C=0$, which you can see by setting $x=0$.
2. Substitute $x=\sum\frac{2(-1)^{n+1}}{n}\sin nx$ and multiply by 3:

$$
x^3=\sum_{n=1}^\infty\Big[\frac{2\pi^2(-1)^{n+1}}{n}+\frac{12(-1)^n}{n^3}\Big]\sin nx=\sum_{n=1}^\infty\frac{2(-1)^n\big(6-n^2\pi^2\big)}{n^3}\sin nx .
$$

3. Checks: the series is odd ✔, and it matches direct integration in SymPy ✔.

> [!example] Lecture Notes route: $x^2$ by integrating from $-\pi$
> Integrate $x=2\sum\frac{(-1)^{n-1}}{n}\sin nx$ from $-\pi$ to $x$:
>
> $$\frac{x^2-\pi^2}{2}=2\sum\frac{(-1)^n}{n^2}\big[\cos nx-(-1)^n\big],\qquad\text{so}\qquad x^2=\frac{a_0}2+4\sum\frac{(-1)^n}{n^2}\cos nx .$$
>
> The constant is best found directly: $a_0=\frac1\pi\int_{-\pi}^{\pi}x^2dx=\frac{2\pi^2}3$. The alternative, using the known value of $\sum\frac1{n^2}$, also works.

## 3. Complex Fourier series (L8)
Use $\cos\theta=\frac{e^{j\theta}+e^{-j\theta}}2$ and $\sin\theta=\frac{e^{j\theta}-e^{-j\theta}}{2j}$, with $\theta=n\pi x/\ell$:

$$
a_n\cos\theta+b_n\sin\theta=\frac{a_n-jb_n}{2}e^{j\theta}+\frac{a_n+jb_n}{2}e^{-j\theta}.
$$

Reindex the $e^{-j\theta}$ sum with $n\to-n$ and define

$$
c_n=\begin{cases}\tfrac12(a_n-jb_n)&n>0\\ \tfrac12a_0&n=0\\ \tfrac12(a_{-n}+jb_{-n})&n<0\end{cases}
\qquad\Longrightarrow\qquad
\boxed{f(x)=\sum_{n=-\infty}^{\infty}c_ne^{jn\pi x/\ell},\qquad c_n=\frac1{2\ell}\int_{-\ell}^{\ell}f(x)\,e^{-jn\pi x/\ell}\,dx}
$$

**Derivation of the single formula for $c_n$**: for $n>0$,

$$
\tfrac12(a_n-jb_n)=\frac1{2\ell}\int f\Big(\cos\tfrac{n\pi x}\ell-j\sin\tfrac{n\pi x}\ell\Big)dx=\frac1{2\ell}\int fe^{-jn\pi x/\ell}dx .
$$

The cases $n<0$ and $n=0$ give the same expression.

**Orthogonality**: $\int_{-\ell}^{\ell}e^{jm\pi x/\ell}\,\overline{e^{jn\pi x/\ell}}\,dx=2\ell\,\delta_{mn}$.

**Converting back to real form**:
- $a_n=c_n+c_{-n}=2\,\mathrm{Re}\,c_n$.
- $b_n=j(c_n-c_{-n})=-2\,\mathrm{Im}\,c_n$.

For real $f$, $c_{-n}=\overline{c_n}$.

> [!tip] "Complex" doesn't mean $f$ is complex
> A real function has a complex series too. The imaginary parts cancel in conjugate pairs.

### Example (L8): $f(x)=e^x$ on $(-\pi,\pi)$

$$
c_n=\frac1{2\pi}\int_{-\pi}^{\pi}e^{(1-jn)x}dx=\frac1{2\pi}\cdot\frac{e^{(1-jn)\pi}-e^{-(1-jn)\pi}}{1-jn}.
$$

Since $e^{\mp jn\pi}=(-1)^n$, the numerator is $(-1)^n(e^\pi-e^{-\pi})=2(-1)^n\sinh\pi$. So

$$
c_n=\frac{(-1)^n\sinh\pi}{\pi(1-jn)},\qquad e^x=\frac{\sinh\pi}{\pi}\sum_{n=-\infty}^{\infty}\frac{(-1)^n}{1-jn}e^{jnx}.
$$

Numerically, $c_1=-1.838-1.838j$ ✔. In real form, multiplying by $\frac{1+jn}{1+jn}$ gives $c_n=\frac{(-1)^n\sinh\pi(1+jn)}{\pi(1+n^2)}$, so $a_n=\frac{2(-1)^n\sinh\pi}{\pi(1+n^2)}$ and $b_n=-\frac{2n(-1)^n\sinh\pi}{\pi(1+n^2)}$. This is exactly PS3 Q1.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]] · Next: [[MATH2048 TR1 - Fourier Transforms]]
- Practice: [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]] (PS4 Q1–2)

## Sources
- Lectures 7–8; Lecture Notes Ch. 2. Checked in SymPy/NumPy: the $x^3$ coefficients, the Basel sum, the divergent derivative series, and a reconstruction of the $e^x$ complex series.
