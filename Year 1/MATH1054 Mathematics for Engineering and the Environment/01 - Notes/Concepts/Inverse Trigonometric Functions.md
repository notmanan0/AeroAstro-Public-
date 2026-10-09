---
title: "Inverse Trigonometric Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["arcsin", "arccos", "arctan", "sin^{-1}", "cos^{-1}", "tan^{-1}"]
tags: [math1054, concept, functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]", "[[MATH1054 M03 - Differentiation I]]"]
related_concepts: ["[[Inverse Functions]]", "[[Hyperbolic Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.6.7, §8.3.11", "MATH1054 Module Booklet, Module 7"]
---

# Inverse Trigonometric Functions

## Definition

> [!note] Definition
> | | principal range | derivative |
> |---|---|---|
> | $\sin^{-1}x$, $\lvert x\rvert\le1$ | $[-\frac\pi2,\frac\pi2]$ | $\frac1{\sqrt{1-x^2}}$ |
> | $\cos^{-1}x$, $\lvert x\rvert\le1$ | $[0,\pi]$ | $-\frac1{\sqrt{1-x^2}}$ |
> | $\tan^{-1}x$, $x\in\mathbb R$ | $(-\frac\pi2,\frac\pi2)$ | $\frac1{1+x^2}$ |

## Explanation
- **Principal branches**: restricting the trig functions to these ranges makes them one-to-one.
- **Identity**: $\sin^{-1}x+\cos^{-1}x=\frac\pi2$.
- $\sin^{-1}(\sin x)=x$ **only** on $[-\frac\pi2,\frac\pi2]$. Elsewhere it is a triangular wave.
- **Integral forms** (the reason these functions matter in calculus): $\int\frac{\mathrm dx}{\sqrt{a^2-x^2}}=\sin^{-1}\frac xa$ and $\int\frac{\mathrm dx}{a^2+x^2}=\frac1a\tan^{-1}\frac xa$.

## Examples
- $\cos^{-1}(-\tfrac12)=\frac{2\pi}3$ (Specimen Test 7, Q2).
- $\frac{\mathrm d}{\mathrm dx}\sin^{-1}\frac x2=\frac1{\sqrt{4-x^2}}$ (Ex 35(a)).
- $\sin^{-1}0.35=0.3576$, $\cos^{-1}0.35=1.2132$, $\tan^{-1}0.35=0.3367$ (Ex 2.50).

## Related
- Topics: [[MATH1054 M07 - Functions]] · [[MATH1054 M03 - Differentiation I]]
- Concepts: [[Inverse Functions]] · [[Hyperbolic Functions]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §2.6.7, §8.3.11
- MATH1054 Module Booklet, Module 7
