---
title: "Integration by Parts"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["By parts", "LIATE"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M04 - Integration I]]"]
related_concepts: ["[[Trigonometric Integrals and Power Reduction]]", "[[Integration by Substitution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8.4", "MATH1054 Module Booklet, Module 4"]
---

# Integration by Parts

## Definition

> [!note] Definition
> $$\int u\frac{\mathrm dv}{\mathrm dx}\,\mathrm dx=uv-\int v\frac{\mathrm du}{\mathrm dx}\,\mathrm dx$$
> This is the product rule integrated.

## Explanation
- **Choosing $u$ (LIATE)**: take the first of Logarithmic, Inverse-trig, Algebraic, Trigonometric, Exponential. The aim is that $u'$ is simpler than $u$.
- **Repeated parts**: $\int x^n(\text{trig or exp})$ needs $n$ applications, each lowering the power.
- **The cyclic case**: $\int e^{ax}\sin bx$ returns to itself after two applications. Solve the resulting equation for $I$:
$$\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2},\qquad\int e^{ax}\sin bx\,\mathrm dx=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}$$
- **Definite integrals**: $\big[uv\big]_a^b-\int_a^bvu'\,\mathrm dx$.
- **The "$u=\ln x$, $\mathrm dv=\mathrm dx$" trick**: $\int\ln x\,\mathrm dx=x\ln x-x$.

## Examples
- $\int x^3\ln x\,\mathrm dx=\frac1{16}x^4(4\ln x-1)$ (Ex 110(c)).
- $\int e^{-2x}\sin3x\,\mathrm dx=-\frac1{13}e^{-2x}(2\sin3x+3\cos3x)$ (Ex 110(d)).
- $\int_0^{\pi/2}x^2\sin x\,\mathrm dx=\pi-2$ (Ex 111(a)).

## Related
- Topics: [[MATH1054 M04 - Integration I]]
- Concepts: [[Trigonometric Integrals and Power Reduction]] · [[Integration by Substitution]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.8.4
- MATH1054 Module Booklet, Module 4
