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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture4_FourierSeries1.pdf", "02 - Sources/Lectures/MATH2048 Lecture 4.txt", "02 - Sources/Lectures/MATH2048 Lecture 5.txt"]
---

# Fourier Series

A **Fourier series** represents a function of period $2\ell$ as a constant plus a sum of sines and cosines,

$$
f(x)\sim\tfrac12a_0+\sum_{n=1}^\infty\Big[a_n\cos\tfrac{n\pi x}{\ell}+b_n\sin\tfrac{n\pi x}{\ell}\Big],\qquad a_n=\tfrac1\ell\int_{-\ell}^{\ell}f\cos\tfrac{n\pi x}\ell\,dx,\quad b_n=\tfrac1\ell\int_{-\ell}^{\ell}f\sin\tfrac{n\pi x}\ell\,dx .
$$

The coefficients come from [[Orthogonality of Trigonometric Functions|orthogonality]]: multiply by one basis function, integrate over a period, and only one term of the infinite sum survives. $\frac12a_0$ is the mean of $f$ over a period, and the sines and cosines carry the fluctuations about it. Where a Taylor series describes a function near one point, a Fourier series describes it over the whole period, which is why it suits boundary value problems.

Symmetry halves the work: an even $f$ has only cosines and an odd $f$ only sines. The coefficients also show how smooth the function is. A jump in the periodic extension makes them fall like $1/n$, a continuous function with a kink like $1/n^2$, and each further degree of smoothness gives another factor of $1/n$. Because the series is an identity, evaluating it at a convenient point sums infinite series: the tent at $x=0$ gives $\sum_{\text{odd}}1/n^2=\pi^2/8$, and $x^2$ at $x=\pi$ gives $\sum1/n^2=\pi^2/6$. At a jump the series takes the average of the two sides ([[Fourier's Theorem]]).

| $f$ on $(-\pi,\pi)$ | Series |
|---|---|
| $x$ | $\sum\frac{2(-1)^{n+1}}{n}\sin nx$ |
| $\lvert x\rvert$ | $\frac\pi2-\frac4\pi\sum_{\text{odd}}\frac{\cos nx}{n^2}$ |
| $x^2$ | $\frac{\pi^2}3+\sum\frac{4(-1)^n}{n^2}\cos nx$ |
| $x^3$ | $\sum\frac{2(-1)^n(6-n^2\pi^2)}{n^3}\sin nx$ |
| $e^x$ | $\frac{\sinh\pi}{\pi}\big[1+2\sum\frac{(-1)^n(\cos nx-n\sin nx)}{1+n^2}\big]$ |

## Related

- Derivations: [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]] · [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]] · [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]
- [[Half-Range Expansions]] · [[Fourier's Theorem]] · [[Complex Fourier Series]] · [[ODE Eigenvalue Problems]]
