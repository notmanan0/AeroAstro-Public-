---
title: "Derivative from First Principles"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["First principles", "Definition of the derivative", "Difference quotient"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M03 - Differentiation I]]"]
related_concepts: ["[[Product, Quotient and Chain Rules]]", "[[Partial Derivatives]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.2", "MATH1054 Module Booklet, Module 3"]
---

# Derivative from First Principles

## Definition

> [!note] Definition
> The derivative of $f$ at $x$ is the limit of the difference quotient:
>
> $$f'(x)=\frac{\mathrm df}{\mathrm dx}=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}$$

## Explanation
- **Geometrically**, it is the slope of the tangent: the limit of the chord slopes as the chord shrinks to a point.
- **Physically**, it is an instantaneous rate: velocity $\dot s$, acceleration $\ddot s$.
- **Recipe**:
  1. Expand $f(x+\Delta x)$.
  2. Subtract $f(x)$. Everything without a $\Delta x$ cancels.
  3. Divide by $\Delta x$.
  4. Let $\Delta x\to0$.
- **Tangent** at $x_0$: $y-y_0=f'(x_0)(x-x_0)$. **Normal**: gradient $-1/f'(x_0)$.
- The standard derivatives and the rules are all proved this way once. After that, you use them directly.

## Examples
- $f=x^2$: $\dfrac{(x+\Delta x)^2-x^2}{\Delta x}=2x+\Delta x\to2x$.
- $f=\frac1x$: $\dfrac{-1}{x(x+\Delta x)}\to-\dfrac1{x^2}$.
- $f=25x-5x^2$: $f'=25-10x$. The tangent at $(1,20)$ is $y=15x+5$ (Ex 8.2).

## Related
- Topics: [[MATH1054 M03 - Differentiation I]]
- Concepts: [[Product, Quotient and Chain Rules]] · [[Partial Derivatives]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.2
- MATH1054 Module Booklet, Module 3
