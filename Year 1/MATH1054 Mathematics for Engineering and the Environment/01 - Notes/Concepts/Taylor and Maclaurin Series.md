---
title: "Taylor and Maclaurin Series"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Maclaurin series", "Taylor series", "Lagrange remainder", "Maclaurin's theorem"]
tags: [math1054, concept, series]
status: complete
parent_lectures: ["[[MATH1054 M08 - Differentiation II]]", "[[MATH1054 M20 - Further Calculus II]]"]
related_concepts: ["[[Convergence Tests for Series]]", "[[L'Hôpital's Rule]]", "[[Truncation Error and Order of Accuracy]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.4", "MATH1054 Module Booklet, Modules 8 and 20"]
---

# Taylor and Maclaurin Series

The Taylor series of $f$ about $x=a$ is the power series $\sum_{n\geq0}\frac{f^{(n)}(a)}{n!}(x-a)^n$ built from the derivatives of $f$ at one point; the Maclaurin series is the case $a=0$.

The coefficients follow from differentiating a power series term by term. If $f(x)=c_0+c_1x+c_2x^2+\cdots$, then after $n$ differentiations the $x^n$ term has become the constant $n!\,c_n$, lower powers have vanished and higher powers still carry a factor $x$, so $f^{(n)}(0)=n!\,c_n$ and $c_n=f^{(n)}(0)/n!$. Stopping after $n$ terms gives Maclaurin's (Taylor's) theorem with the Lagrange remainder:

$$
f(x)=\sum_{k=0}^{n}\frac{f^{(k)}(0)}{k!}x^k+R_n(x),\qquad R_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1}\ \ (0<\theta<1).
$$

The Taylor series about $a$ replaces $x$ by $x-a$ and evaluates the derivatives at $a$. The infinite series equals $f(x)$ only where $R_n(x)\to0$, so every series has an interval of validity.

| $f$ | Series | Radius |
|---|---|---|
| $e^x$ | $\sum\frac{x^n}{n!}$ | $\infty$ |
| $\sin x$ | $x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$ | $\infty$ |
| $\cos x$ | $1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$ | $\infty$ |
| $\ln(1+x)$ | $x-\frac{x^2}2+\frac{x^3}3-\cdots$ | 1 |
| $(1+x)^\alpha$ | $1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+\cdots$ | 1 ($\infty$ if $\alpha=0,1,2,\dots$) |

Products and compositions of known series are usually quicker than repeated differentiation, within their common interval of validity. The Lagrange remainder gives guaranteed error bounds once $|f^{(n+1)}|$ is bounded on the interval. The same remainders are the truncation errors of finite-difference formulae in SESA2029 ([[Truncation Error and Order of Accuracy]], [[Taylor Table Method]]), and the first-order Taylor polynomial is the basis of Newton–Raphson and of small-perturbation linearisation.

Worked examples:

- $e^x\sin x=x+x^2+\frac{x^3}3-\frac{x^5}{30}+\cdots$, from $f^{(k)}(0)=(\sqrt2)^k\sin\frac{k\pi}4=0,1,2,2,0,-4,\dots$ or by multiplying the series for $e^x$ and $\sin x$ (Example 9.10).
- $(1+x)\sin x=x+x^2-\frac{x^3}6-\frac{x^4}6+\cdots$ (Booklet Ex B, M08).
- $\sqrt{4+h}\approx2+\frac h4-\frac{h^2}{64}+\frac{h^3}{512}$ about $a=4$ gives $\sqrt{4.1}\approx2.0248457$, in error by $3\times10^{-8}$.
- $\cos x\approx1-\frac{x^2}2$ with $0<R_3<\frac{x^4}{24}$ for $0<|x|<\frac\pi2$; $\sqrt{1.02}\approx1.01$ with error $<5\times10^{-5}$ (M20 Booklet Ex B, C).

![[m1054_maclaurin_cos.png|800]]

The common trap is using a series outside its interval of validity: $\ln(1+x)$ and $(1+x)^\alpha$ ($\alpha$ not a non-negative integer) expanded about 0 diverge for $|x|>1$, and even a series valid for all $x$, such as $\sin x$, needs many terms far from the expansion point. Expand about a point close to where the value is wanted, and check that the angle is in radians.

## Related

- Topics: [[MATH1054 M08 - Differentiation II]] (coefficients derived, Example 9.10, Booklet Exercises A and B) · [[MATH1054 M20 - Further Calculus II]] (remainder bounds, convergence)
- Concepts: [[Convergence Tests for Series]] · [[L'Hôpital's Rule]] · [[Truncation Error and Order of Accuracy]] · [[Stationary Points and Inflection]] · [[Direct Substitution and Newton-Raphson]] · [[Small Perturbation Linearisation]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §9.4; MATH1054 Module Booklet, Modules 8 and 20
