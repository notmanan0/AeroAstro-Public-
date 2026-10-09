---
title: "Fourier Series"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 2: Fourier Series"
aliases: ["Fourier series", "Euler formulae (Fourier)", "Fourier coefficients"]
tags: [math2048, concept, fourier-series]
status: complete
parent_lectures: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]"]
related_concepts: ["[[Orthogonality of Trigonometric Functions]]", "[[Half-Range Expansions]]", "[[Fourier's Theorem]]", "[[Complex Fourier Series]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture4_FourierSeries1.pdf"]
---

# Fourier Series

## Definition

> [!note] Definition
> For $f$ with period $2\ell$:
> $$f(x)=\tfrac12a_0+\sum_{n=1}^\infty\Big[a_n\cos\tfrac{n\pi x}{\ell}+b_n\sin\tfrac{n\pi x}{\ell}\Big],\qquad a_n=\tfrac1\ell\int_{-\ell}^{\ell}f\cos\tfrac{n\pi x}\ell\,dx,\quad b_n=\tfrac1\ell\int_{-\ell}^{\ell}f\sin\tfrac{n\pi x}\ell\,dx .$$

## Explanation
- The coefficients come from **orthogonality**: multiply by a basis function and integrate, and only one term survives ([[Orthogonality of Trigonometric Functions]]).
- $\tfrac12a_0$ is the **mean** of $f$ over one period.
- **Symmetry shortcuts**: an even $f$ has only cosines, an odd $f$ has only sines.
- **Decay rate**: a jump gives $\sim1/n$, and a continuous $f$ with a kink gives $\sim1/n^2$. Each extra degree of smoothness gives another factor of $1/n$.
- **Summing series**: evaluate the series at a well-chosen point. At a jump, use $\frac12[f^-+f^+]$.

| $f$ on $(-\pi,\pi)$ | Series |
|---|---|
| $x$ | $\sum\frac{2(-1)^{n+1}}{n}\sin nx$ |
| $\lvert x\rvert$ | $\frac\pi2-\frac4\pi\sum_{\text{odd}}\frac{\cos nx}{n^2}$ |
| $x^2$ | $\frac{\pi^2}3+\sum\frac{4(-1)^n}{n^2}\cos nx$ |
| $x^3$ | $\sum\frac{2(-1)^n(6-n^2\pi^2)}{n^3}\sin nx$ |
| $e^x$ | $\frac{\sinh\pi}{\pi}\big[1+2\sum\frac{(-1)^n(\cos nx-n\sin nx)}{1+n^2}\big]$ |

## Examples
- $\sum_{\text{odd}}1/n^2=\pi^2/8$ (the tent at $x=0$).
- $\sum1/n^2=\pi^2/6$ ($x^2$ at $x=\pi$).

## Related
- [[Half-Range Expansions]] · [[Fourier's Theorem]] · [[Complex Fourier Series]] · [[ODE Eigenvalue Problems]]

## Sources
- Lectures 4–8
