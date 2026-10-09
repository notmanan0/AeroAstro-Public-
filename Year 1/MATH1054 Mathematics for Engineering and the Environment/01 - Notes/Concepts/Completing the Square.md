---
title: "Completing the Square"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Complete the square"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M10 - Integration III]]"]
related_concepts: ["[[Partial Fractions]]", "[[Integration by Substitution]]", "[[Inverse Trigonometric Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8", "MATH1054 Module Booklet, Module 10"]
---

# Completing the Square

## Definition

> [!note] Definition
>
> $$ax^2+bx+c=a\Big[\Big(x+\frac b{2a}\Big)^2+\frac{4ac-b^2}{4a^2}\Big]$$

## Explanation
It turns a quadratic into one of the standard forms $u^2\pm k^2$ or $k^2-u^2$, which then integrate by table:

| After completing the square | Integral |
|---|---|
| $\frac1{u^2+k^2}$ | $\frac1k\tan^{-1}\frac uk$ |
| $\frac1{\sqrt{k^2-u^2}}$ | $\sin^{-1}\frac uk$ |
| $\frac1{\sqrt{u^2+k^2}}$ | $\sinh^{-1}\frac uk$ |
| $\frac1{\sqrt{u^2-k^2}}$ | $\cosh^{-1}\frac uk$ |

It also finds the centres of circles in complex-number loci, e.g. $x^2+y^2-4x-6y+9=0$ is centre $(2,3)$, radius 2.

## Examples
- $3+2x-x^2=4-(x-1)^2$, so $\int_0^2\frac{\mathrm dx}{\sqrt{3+2x-x^2}}=\frac\pi3$ (Ex 105(e)).
- $x^2+6x+13=(x+3)^2+4$, so $\int=\frac12\tan^{-1}\frac{x+3}2$ (Ex 106(l)).

## Related
- Topics: [[MATH1054 M10 - Integration III]]
- Concepts: [[Partial Fractions]] · [[Integration by Substitution]] · [[Inverse Trigonometric Functions]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.8
- MATH1054 Module Booklet, Module 10
