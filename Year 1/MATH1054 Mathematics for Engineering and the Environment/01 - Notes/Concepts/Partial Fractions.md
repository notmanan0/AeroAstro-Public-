---
title: "Partial Fractions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Partial fraction decomposition", "Cover-up rule"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M10 - Integration III]]"]
related_concepts: ["[[Completing the Square]]", "[[Partial Fractions for Inverse Laplace]]", "[[Integration by Substitution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) pp.114–119, §8.8", "MATH1054 Module Booklet, Module 10"]
---

# Partial Fractions

## Definition

> [!note] Definition
> A proper rational function $P/Q$ splits into simple terms, one group per factor of $Q$:
> $$\frac{A}{x-a},\qquad\frac{A}{x-a}+\frac{B}{(x-a)^2},\qquad\frac{Bx+C}{x^2+bx+c}\ (\text{irreducible})$$

## Explanation
- **Improper first**: if $\deg P\ge\deg Q$, do polynomial division before anything else.
- **Cover-up rule**: for a simple factor $(x-a)$, cover it and substitute $x=a$ into the rest. That gives its coefficient instantly.
- **Remaining constants**: compare coefficients, usually of the highest power or the constant term.
- **Integrating**: the linear terms give $\ln$; the repeated terms give $-\frac{1}{x-a}$; the quadratic terms give $\ln$ plus $\tan^{-1}$ ([[Completing the Square]]).
- The same algebra drives inverse Laplace transforms ([[Partial Fractions for Inverse Laplace]]).

## Examples
- $\frac{9}{(x-1)(x+2)^2}=\frac1{x-1}-\frac1{x+2}-\frac3{(x+2)^2}$ (Ex 8.53(b)).
- $\int_0^6\frac{\mathrm dx}{x^2+5x+6}=\ln\frac43$ (Ex 8.53(c)).
- $\frac{2x^3}{x^3-1}=2+\frac{2/3}{x-1}-\frac23\cdot\frac{x+2}{x^2+x+1}$ (Ex 117(i)).

## Related
- Topics: [[MATH1054 M10 - Integration III]]
- Concepts: [[Completing the Square]] · [[Partial Fractions for Inverse Laplace]] · [[Integration by Substitution]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) pp.114–119, §8.8
- MATH1054 Module Booklet, Module 10
