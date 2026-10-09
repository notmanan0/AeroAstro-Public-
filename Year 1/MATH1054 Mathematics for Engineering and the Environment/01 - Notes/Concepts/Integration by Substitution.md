---
title: "Integration by Substitution"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Substitution", "Change of variable", "u-substitution"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M09 - Integration II]]"]
related_concepts: ["[[Integration by Parts]]", "[[Trigonometric Integrals and Power Reduction]]", "[[Hyperbolic Functions]]", "[[Completing the Square]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8.2–8.8.3", "MATH1054 Module Booklet, Module 9"]
---

# Integration by Substitution

## Definition

> [!note] Definition
>
> $$\int f(g(x))\,g'(x)\,\mathrm dx=\int f(u)\,\mathrm du,\qquad u=g(x);\qquad\int_a^b\cdots\,\mathrm dx=\int_{g(a)}^{g(b)}\cdots\,\mathrm du$$

## Explanation
| Spot | Substitute |
|---|---|
| a function together with its derivative | $u$ = that function |
| $\frac{f'}{f}$ | integrates directly to $\ln\lvert f\rvert$ |
| $\sqrt{ax+b}$ | $u=\sqrt{ax+b}$ |
| $\sqrt{a^2-x^2}$ | $x=a\sin\theta$ |
| $\sqrt{x^2+a^2}$ | $x=a\sinh u$ (or $a\tan\theta$) |
| $\sqrt{x^2-a^2}$ | $x=a\cosh u$ |

**Change the limits** in definite integrals, then there is no need to substitute back.

## Examples
- $\int_{-2}^2\frac{\sqrt{x+2}}{x+6}\,\mathrm dx=4-\pi$ with $u=\sqrt{x+2}$ (Ex 8.62).
- $\int\sqrt{1-x^2}\,\mathrm dx=\frac12\sin^{-1}x+\frac12x\sqrt{1-x^2}$ (Ex 8.60).
- $\int_1^4\frac{e^{\sqrt x}}{\sqrt x}\,\mathrm dx=2(e^2-e)$ (Ex 115(d)).

## Related
- Topics: [[MATH1054 M09 - Integration II]]
- Concepts: [[Integration by Parts]] · [[Trigonometric Integrals and Power Reduction]] · [[Hyperbolic Functions]] · [[Completing the Square]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.8.2–8.8.3
- MATH1054 Module Booklet, Module 9
