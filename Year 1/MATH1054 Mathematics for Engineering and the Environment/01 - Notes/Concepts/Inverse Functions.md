---
title: "Inverse Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["f^{-1}", "Inverse function", "One-to-one"]
tags: [math1054, concept, functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]"]
related_concepts: ["[[Inverse Trigonometric Functions]]", "[[Hyperbolic Functions]]", "[[Even, Odd and Periodic Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.2.3", "MATH1054 Module Booklet, Module 7"]
---

# Inverse Functions

## Definition

> [!note] Definition
> $f^{-1}$ undoes $f$: $f^{-1}(f(x))=x$. It exists iff $f$ is **one-to-one** on its domain. The domain of $f^{-1}$ is the range of $f$.

## Explanation
- **Finding it**: write $y=f(x)$, solve for $x$, then swap the letters.
- **Graph**: reflect the graph of $f$ in $y=x$. Its asymptotes swap too.
- **Horizontal-line test**: a function is one-to-one iff every horizontal line meets its graph at most once.
- **Restricting the domain** makes a function invertible: $x^2$ on $x\ge0$ gives $\sqrt x$; $\sin x$ on $[-\frac\pi2,\frac\pi2]$ gives $\sin^{-1}$.
- **Derivative**: $\frac{\mathrm d}{\mathrm dx}f^{-1}(x)=\dfrac{1}{f'(f^{-1}(x))}$.

## Examples
- $f=\frac15(4x-3)$ gives $f^{-1}=\frac{5x+3}4$ (Ex 2.6).
- $f=\frac{x+2}{x+1}$ gives $f^{-1}=\frac{2-x}{x-1}$, $x\neq1$ (Ex 2.7).
- $x^2+1$ on $x\ge0$ gives $\sqrt{x-1}$ (Ex 10(c)).

## Related
- Topics: [[MATH1054 M07 - Functions]]
- Concepts: [[Inverse Trigonometric Functions]] · [[Hyperbolic Functions]] · [[Even, Odd and Periodic Functions]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §2.2.3
- MATH1054 Module Booklet, Module 7
