---
title: "MATH1054 M10 - Integration III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 10
tags:
  - math1054
  - integration
  - partial-fractions
  - improper-integrals
aliases: ["MATH1054 Module 10", "Integration III"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M09 - Integration II]]"]
next_topics: ["[[MATH1054 M11 - Integration IV]]"]
key_concepts: ["[[Partial Fractions]]", "[[Completing the Square]]", "[[Improper Integrals]]"]
tutorial_sheets: ["[[MATH1054 M10 Solutions - Integration III]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 10)", "02 - Sources/Modern Engineering Mathematics.pdf (pp.114–119, §8.8, §9.2)"]
---

# MATH1054 M10 - Integration III

> [!abstract] Summary
> Two tools finish off single-variable integration:
> - **Rational functions** $P(x)/Q(x)$ always integrate: divide if improper, split $Q$ into partial fractions, then each piece gives a $\ln$, a power or a $\tan^{-1}$.
> - **Improper integrals**, where the range is infinite or the integrand blows up, are defined as limits. Some converge and some do not.
>
> Partial fractions come back in a big way for inverse Laplace transforms in MATH2048 and SESA2027.

## Key Concepts
- [[Partial Fractions]] · [[Completing the Square]] · [[Improper Integrals]] · Later: [[Partial Fractions for Inverse Laplace]]

---

## 1. Partial fractions (James pp.114–119)
**Step 0**: if $\deg P\ge\deg Q$, do polynomial division first. For example, $\frac{2x^3}{x^3-1}=2+\frac2{x^3-1}$.

| Factor of $Q$ | Terms |
|---|---|
| linear $(x-a)$ | $\dfrac{A}{x-a}$ |
| repeated $(x-a)^2$ | $\dfrac{A}{x-a}+\dfrac{B}{(x-a)^2}$ |
| irreducible quadratic $x^2+bx+c$ ($b^2<4c$) | $\dfrac{Bx+C}{x^2+bx+c}$ |

**Finding the constants**:
1. **Cover-up** gives each simple-pole coefficient instantly: cover the factor and substitute its root.
2. For the rest, compare coefficients, usually of the highest power or the constant term.

**Integrating each term**:

$$
\int\frac{\mathrm dx}{x-a}=\ln|x-a|,\qquad\int\frac{\mathrm dx}{(x-a)^2}=-\frac1{x-a},\qquad\int\frac{Bx+C}{x^2+bx+c}\,\mathrm dx\to\text{a }\ln\text{ part}+\text{a }\tan^{-1}\text{ part}
$$

For the quadratic, write $Bx+C=\frac B2(2x+b)+\big(C-\frac{Bb}2\big)$. The first part is $f'/f$, which gives a $\ln$. For the second, complete the square to get a $\tan^{-1}$.

## 2. Completing the square (James §8.8)

$$
ax^2+bx+c=a\Big[\Big(x+\frac b{2a}\Big)^2+\frac{4ac-b^2}{4a^2}\Big]
$$

Then match a standard form:

| Form after completing the square | Integral |
|---|---|
| $\dfrac1{u^2+a^2}$ | $\dfrac1a\tan^{-1}\dfrac ua$ |
| $\dfrac1{\sqrt{a^2-u^2}}$ | $\sin^{-1}\dfrac ua$ |
| $\dfrac1{\sqrt{u^2+a^2}}$ | $\sinh^{-1}\dfrac ua$ |
| $\dfrac1{\sqrt{u^2-a^2}}$ | $\cosh^{-1}\dfrac ua$ |

For example, $3+2x-x^2=4-(x-1)^2$, so $\int_0^2\frac{\mathrm dx}{\sqrt{3+2x-x^2}}=\frac\pi3$.

## 3. Improper integrals (James §9.2)

$$
\int_a^\infty f\,\mathrm dx=\lim_{R\to\infty}\int_a^Rf\,\mathrm dx,\qquad\int_0^1f\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_\varepsilon^1f\,\mathrm dx\ \text{(when $f$ is unbounded at 0)}
$$

The integral **converges** if the limit exists and is finite, and **diverges** otherwise.

**The $p$-test** is worth memorising:

| Integral | Converges iff |
|---|---|
| $\displaystyle\int_1^\infty\frac{\mathrm dx}{x^p}$ | $p>1$ |
| $\displaystyle\int_0^1\frac{\mathrm dx}{x^p}$ | $p<1$ |

$p=1$ (i.e. $\ln$) diverges at both ends.

![[m1054_improper_integrals.png|760]]

> [!warning] Interior singularities
> Split at every point where the integrand blows up. $\int_{-1}^1x^{-2}\,\mathrm dx$ is **undefined**. The naive antiderivative gives $-2$, which is negative for a positive integrand and therefore obviously wrong.

**Useful limits**: $\varepsilon\ln\varepsilon\to0$, $R^ne^{-R}\to0$, and $\tan^{-1}R\to\frac\pi2$.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M10 Solutions - Integration III]]
- Prev: [[MATH1054 M09 - Integration II]] · Next: [[MATH1054 M11 - Integration IV]]
- Used later: the Laplace transform $\int_0^\infty e^{-st}f(t)\,\mathrm dt$ is an improper integral ([[Laplace Transform]], [[Partial Fractions for Inverse Laplace]])

## Sources
- MATH1054 Module Booklet, Module 10; James pp.114–119, §8.8, §9.2
