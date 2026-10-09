---
title: "Improper Integrals"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Improper integral", "Convergent integral", "Divergent integral"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M10 - Integration III]]"]
related_concepts: ["[[Partial Fractions]]", "[[Laplace Transform]]", "[[Convergence Tests for Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.2", "MATH1054 Module Booklet, Module 10"]
---

# Improper Integrals

## Definition

> [!note] Definition
> An integral with an **infinite range**, or with an integrand that is **unbounded** on the range, is defined as a limit:
> $$\int_a^\infty f\,\mathrm dx=\lim_{R\to\infty}\int_a^Rf\,\mathrm dx,\qquad\int_0^1f\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_\varepsilon^1f\,\mathrm dx$$
> It **converges** if the limit is finite, and **diverges** otherwise.

## Explanation
- **$p$-test**: $\int_1^\infty x^{-p}\,\mathrm dx$ converges iff $p>1$; $\int_0^1x^{-p}\,\mathrm dx$ converges iff $p<1$.
- **Interior singularities**: split the range at them. $\int_{-1}^1x^{-2}\,\mathrm dx$ is undefined. The naive answer $-2$ is wrong: it is negative for a positive integrand.
- **Useful limits**: $\varepsilon\ln\varepsilon\to0$, $R^ne^{-R}\to0$, $\tan^{-1}R\to\frac\pi2$.
- The Laplace transform $\int_0^\infty e^{-st}f\,\mathrm dt$ is an improper integral ([[Laplace Transform]]).

## Examples
- $\int_0^1x^{-2/3}\,\mathrm dx=3$, $\int_0^1\ln x\,\mathrm dx=-1$, $\int_0^\infty e^{-x}\sin x\,\mathrm dx=\frac12$ (Ex 9.1, 9.4).
- $\int_{-\infty}^\infty e^{3x}e^{-e^x}\,\mathrm dx=\int_0^\infty u^2e^{-u}\,\mathrm du=2$ (Ex 9.4(d)).

## Related
- Topics: [[MATH1054 M10 - Integration III]]
- Concepts: [[Partial Fractions]] · [[Laplace Transform]] · [[Convergence Tests for Series]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §9.2
- MATH1054 Module Booklet, Module 10
