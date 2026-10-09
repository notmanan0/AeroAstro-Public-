---
title: "Even, Odd and Periodic Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Even function", "Odd function", "Periodic function", "Symmetry"]
tags: [math1054, concept, functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]"]
related_concepts: ["[[Inverse Functions]]", "[[Half-Range Expansions]]", "[[Fourier Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.2.6", "MATH1054 Module Booklet, Module 7"]
---

# Even, Odd and Periodic Functions

## Definition

> [!note] Definition
> - **Even**: $f(-x)=f(x)$, symmetric about the $y$-axis.
> - **Odd**: $f(-x)=-f(x)$, with $180°$ rotational symmetry about O.
> - **Periodic** with period $T$: $f(x+T)=f(x)$ for all $x$.

## Explanation
- Even examples: $x^{2n}$, $\cos x$, $\cosh x$, $|x|$. Odd examples: $x^{2n+1}$, $\sin x$, $\sinh x$, $\tan x$.
- even × even and odd × odd are **even**; even × odd is **odd**.
- **Integrals**: $\int_{-a}^af=2\int_0^af$ for even $f$, and $0$ for odd $f$.
- **Extensions**: a function defined on $[0,L]$ can be extended to an even or odd function of period $2L$. This is exactly the half-range sine and cosine series idea ([[Half-Range Expansions]]).

## Examples
- $\frac{x^2+1}{\sqrt{x^2-1}}$ is even (Specimen Test 7, Q1).
- A triangle on $[0,1]$ extended with period 2, even or odd: see Ex 2.12.
- $\sin^{-1}(\sin x)$ is odd with period $2\pi$; $\cos^{-1}(\cos x)$ is even with period $2\pi$.

## Related
- Topics: [[MATH1054 M07 - Functions]]
- Concepts: [[Inverse Functions]] · [[Half-Range Expansions]] · [[Fourier Series]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §2.2.6
- MATH1054 Module Booklet, Module 7
