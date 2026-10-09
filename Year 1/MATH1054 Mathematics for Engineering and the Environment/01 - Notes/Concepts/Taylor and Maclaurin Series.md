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

## Definition

> [!note] Definition
>
> $$f(x)=\sum_{k=0}^{n}\frac{f^{(k)}(0)}{k!}x^k+R_n(x),\qquad R_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1}\ \ (0<\theta<1)$$
>
> The Taylor series about $a$ replaces $x$ by $x-a$ and evaluates the derivatives at $a$.

## Explanation
| $f$ | Series | Radius |
|---|---|---|
| $e^x$ | $\sum\frac{x^n}{n!}$ | $\infty$ |
| $\sin x$ | $x-\frac{x^3}{3!}+\frac{x^5}{5!}-\cdots$ | $\infty$ |
| $\cos x$ | $1-\frac{x^2}{2!}+\frac{x^4}{4!}-\cdots$ | $\infty$ |
| $\ln(1+x)$ | $x-\frac{x^2}2+\frac{x^3}3-\cdots$ | 1 |
| $(1+x)^\alpha$ | $1+\alpha x+\frac{\alpha(\alpha-1)}{2!}x^2+\cdots$ | 1 |

- **Products of series**: multiply the known series instead of differentiating repeatedly.
- **The Lagrange remainder gives guaranteed error bounds**. Bound $|f^{(n+1)}|$ on the interval.
- The truncation errors of finite differences in SESA2029 are exactly these remainders.

## Examples
- $e^x\sin x=x+x^2+\frac{x^3}3-\frac{x^5}{30}+\cdots$ (Ex 9.10).
- $(1+x)\sin x=x+x^2-\frac{x^3}6-\frac{x^4}6+\cdots$ (Booklet Ex B, M08).
- $\cos x\approx1-\frac{x^2}2$ with $0<R_3<\frac{x^4}{24}$; $\sqrt{1.02}\approx1.01$ with error $<5\times10^{-5}$ (M20 Booklet Ex B, C).

## Related
- Topics: [[MATH1054 M08 - Differentiation II]] · [[MATH1054 M20 - Further Calculus II]]
- Concepts: [[Convergence Tests for Series]] · [[L'Hôpital's Rule]] · [[Truncation Error and Order of Accuracy]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §9.4
- MATH1054 Module Booklet, Modules 8 and 20
