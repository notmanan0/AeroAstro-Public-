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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture8_FourierSeries5.pdf"]
---

# Complex Fourier Series

## Definition

> [!note] Definition
>
> $$f(x)=\sum_{n=-\infty}^{\infty}c_ne^{jn\pi x/\ell},\qquad c_n=\frac1{2\ell}\int_{-\ell}^{\ell}f(x)e^{-jn\pi x/\ell}dx .$$

## Explanation
**Conversion to and from the real series**:
- $c_n=\frac12(a_n-jb_n)$ for $n>0$, $c_0=\frac12a_0$, and $c_{-n}=\frac12(a_n+jb_n)$.
- $a_n=2\,\mathrm{Re}\,c_n$ and $b_n=-2\,\mathrm{Im}\,c_n$.

**Symmetry**:
- For real $f$, $c_{-n}=\overline{c_n}$.
- An even $f$ gives real $c_n$. An odd $f$ gives purely imaginary $c_n$.

**Why use it**:
- It is often *easier* than the real form: one exponential integral replaces two trig integrations by parts.
- Letting $\ell\to\infty$ turns the sum into the integral of the [[Fourier Transform]].

## Examples
| $f$ | $c_n$ |
|---|---|
| $x$ on $(-\pi,\pi)$ | $j(-1)^n/n$, with $c_0=0$ |
| $x^2$ on $(-\pi,\pi)$ | $2(-1)^n/n^2$, with $c_0=\pi^2/3$ |
| $e^x$ on $(-\pi,\pi)$ | $\dfrac{(-1)^n\sinh\pi}{\pi(1-jn)}$ |
| $0$ on $(-2,0)$, $1$ on $(0,2)$ | $\dfrac{1-(-1)^n}{2jn\pi}$, with $c_0=\frac12$ |

## Related
- [[Fourier Series]] · [[Fourier Transform]]

## Sources
- Lecture 8; PS4
