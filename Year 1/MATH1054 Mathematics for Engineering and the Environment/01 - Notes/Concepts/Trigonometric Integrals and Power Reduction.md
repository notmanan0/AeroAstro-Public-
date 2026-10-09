---
title: "Trigonometric Integrals and Power Reduction"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Product-to-sum", "Power reduction", "Trig integrals"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M09 - Integration II]]"]
related_concepts: ["[[Integration by Parts]]", "[[Integration by Substitution]]", "[[Orthogonality of Trigonometric Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8.5", "MATH1054 Module Booklet, Modules 4 and 9"]
---

# Trigonometric Integrals and Power Reduction

## Definition

> [!note] Definition
> Use identities to turn powers and products of sines and cosines into **sums of single sines and cosines**, which integrate directly:
>
> $$\cos^2x=\tfrac12(1+\cos2x),\quad\sin^2x=\tfrac12(1-\cos2x),\quad2\sin A\cos B=\sin(A+B)+\sin(A-B)$$

## Explanation
| Integrand | Technique |
|---|---|
| $\sin^2x$, $\cos^2x$, $\cos^4x$ | double-angle identities, applied repeatedly |
| $\sin mx\cos nx$, $\cos mx\cos nx$, $\sin mx\sin nx$ | product-to-sum |
| $\sin^mx\cos^nx$ with one power odd | save one factor, convert the rest, substitute $u=\sin x$ or $\cos x$ |

- **Orthogonality**: $\int_0^\pi\sin mx\sin nx\,\mathrm dx=0$ for $m\neq n$, and $\frac\pi2$ for $m=n$. This is the engine of Fourier series ([[Orthogonality of Trigonometric Functions]]).

## Examples
- $\int\cos^4x\,\mathrm dx=\frac38x+\frac14\sin2x+\frac1{32}\sin4x$ (Booklet Ex A, M04).
- $\int\cos7x\cos5x\,\mathrm dx=\frac1{24}\sin12x+\frac14\sin2x$ (Ex 119(b)).
- $\int\sin^2x\cos^3x\,\mathrm dx=\frac13\sin^3x-\frac15\sin^5x$ (Ex 122(b)).

## Related
- Topics: [[MATH1054 M04 - Integration I]] · [[MATH1054 M09 - Integration II]]
- Concepts: [[Integration by Parts]] · [[Integration by Substitution]] · [[Orthogonality of Trigonometric Functions]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.8.5
- MATH1054 Module Booklet, Modules 4 and 9
