---
title: "Complex Fourier Series"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 2: Fourier Series"
aliases: ["Exponential Fourier series", "Complex Euler formula"]
tags: [math2048, concept, fourier-series]
status: complete
parent_lectures: ["[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
related_concepts: ["[[Fourier Series]]", "[[Fourier Transform]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture8_FourierSeries5.pdf", "02 - Sources/Lectures/MATH2048 Lecture 8.txt"]
---

# Complex Fourier Series

The **complex Fourier series** writes a periodic function as a sum of complex exponentials over all integers,

$$
f(x)\sim\sum_{n=-\infty}^{\infty}c_ne^{jn\pi x/\ell},\qquad c_n=\frac1{2\ell}\int_{-\ell}^{\ell}f(x)e^{-jn\pi x/\ell}\,dx,
$$

with one Euler formula covering every $n$, including the constant $c_0$.

It is the real series rewritten with $\cos\theta=\frac12(e^{j\theta}+e^{-j\theta})$ and $\sin\theta=\frac1{2j}(e^{j\theta}-e^{-j\theta})$, so the coefficients are related by $c_n=\frac12(a_n-jb_n)$ for $n>0$, $c_0=\frac12a_0$ and $c_{-n}=\frac12(a_n+jb_n)$, or conversely $a_n=2\,\mathrm{Re}\,c_n$ and $b_n=-2\,\mathrm{Im}\,c_n$. For a real function $c_{-n}=\overline{c_n}$; an even function gives real $c_n$ and an odd one purely imaginary $c_n$. Note the opposite signs of the exponentials in the series and in the Euler formula.

The complex form is often easier than the real one, because one exponential integral replaces two integrations by parts; for $e^x$ the whole calculation is a single line. The general formula can fail at particular $n$ when $f$ is itself a basis function, such as $e^{jx}$, which then has to be treated separately. Letting $\ell\to\infty$ turns the sum into the integral of the [[Fourier Transform]].

| $f$ | $c_n$ |
|---|---|
| $x$ on $(-\pi,\pi)$ | $j(-1)^n/n$, with $c_0=0$ |
| $x^2$ on $(-\pi,\pi)$ | $2(-1)^n/n^2$, with $c_0=\pi^2/3$ |
| $e^x$ on $(-\pi,\pi)$ | $\dfrac{(-1)^n\sinh\pi}{\pi(1-jn)}$ |
| $0$ on $(-2,0)$, $1$ on $(0,2)$ | $\dfrac{1-(-1)^n}{2jn\pi}$, with $c_0=\frac12$ |

## Related

- Derivation: [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series#4. Complex Fourier series (L8)|FS3 §4]]
- [[Fourier Series]] · [[Fourier Transform]]
