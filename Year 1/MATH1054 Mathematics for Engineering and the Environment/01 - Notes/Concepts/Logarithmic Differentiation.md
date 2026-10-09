---
title: "Logarithmic Differentiation"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Log differentiation"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M08 - Differentiation II]]"]
related_concepts: ["[[Implicit and Parametric Differentiation]]", "[[Product, Quotient and Chain Rules]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.3.14", "MATH1054 Module Booklet, Module 8"]
---

# Logarithmic Differentiation

## Definition

> [!note] Definition
> Take $\ln$ of both sides, differentiate implicitly, then multiply through by $y$:
> $$\ln y=\ln f(x)\ \Rightarrow\ \frac{y'}{y}=\frac{\mathrm d}{\mathrm dx}\ln f(x)\ \Rightarrow\ y'=y\,\frac{\mathrm d}{\mathrm dx}\ln f(x)$$

## Explanation
**Use it when**:
1. The variable is in both the base and the exponent: $x^x$, $(\sin x)^x$, $(\ln x)^x$, $a^x$.
2. There is a long product or quotient of powers. The log laws turn it into a sum.

## Examples
- $(\sin x)^x$ gives $(\sin x)^x(\ln\sin x+x\cot x)$ (Ex 8.25).
- $10^x$ gives $10^x\ln10$ (Ex 53(a)).
- $(1-x^2)^{1/2}(2x^2+3)^{-4/3}$ gives $\dfrac{5x(2x^2-5)}{3(1-x^2)^{1/2}(2x^2+3)^{7/3}}$ (Ex 58(c)).

## Related
- Topics: [[MATH1054 M08 - Differentiation II]]
- Concepts: [[Implicit and Parametric Differentiation]] · [[Product, Quotient and Chain Rules]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.3.14
- MATH1054 Module Booklet, Module 8
