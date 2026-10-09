---
title: "Laplace Transform"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["Laplace", "s-domain", "inverse Laplace", "final value theorem", "partial fractions"]
tags: [sesa2027, concept, maths]
status: complete
parent_lectures: ["[[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]"]
related_concepts: ["[[Transfer Function]]", "[[Poles and Zeros]]", "[[Step Response Specifications]]"]
sources: ["02 - Sources/Lectures/Lecture 1.07.pdf"]
---

# Laplace Transform

## Definition

> [!note] Definition
>
> $$\mathcal L\{g(t)\} = G(s) = \int_0^\infty g(t)e^{-st}\,dt,\qquad s = \sigma+j\omega$$
>
> It turns linear constant-coefficient ODEs into **algebraic** equations in $s$: **differentiation becomes multiplication by $s$** and integration becomes division by $s$. Initial conditions are included automatically.

## Explanation
**Route**: ODE → transform → solve the algebra → partial fractions → inverse transform with a table.

| $g(t)$ | $G(s)$ |
|---|---|
| $\delta(t)$ | $1$ |
| Unit step | $1/s$ |
| $t$ | $1/s^2$ |
| $e^{\sigma t}$ | $1/(s-\sigma)$ |
| $\sin\omega t$ | $\omega/(s^2+\omega^2)$ |
| $e^{\sigma t}\cos\omega t$ | $(s-\sigma)/[(s-\sigma)^2+\omega^2]$ |
| $e^{\sigma t}\sin\omega t$ | $\omega/[(s-\sigma)^2+\omega^2]$ |
| $\dot g$ | $sG-g(0)$ |
| $\ddot g$ | $s^2G-sg(0)-\dot g(0)$ |
| $g(t-a)u(t-a)$ | $e^{-as}G(s)$ (a pure delay) |

- **Final value theorem**: $\lim_{t\to\infty}g(t) = \lim_{s\to0}sG(s)$, valid if the limit exists (a stable system).
- **Why use it**: piecewise inputs (steps, pulses) are easy, the classical method (complementary function plus particular integral) is avoided, and it leads naturally to transfer functions.
- A **time delay** $T_d$ transforms to $e^{-sT_d}$. It has unit magnitude and phase $-\omega T_d$, which is how sensor and digital latency erodes the phase margin ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]).

## Examples
- SPO step: $X(s) = \dfrac{K}{s(s^2+0.744s+1.992)}$ gives $x(t) = r_1+r_2e^{\sigma t}\cos\omega t+r_3e^{\sigma t}\sin\omega t$ with $\sigma = -0.372$ and $\omega = 1.362$ ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]).

## Related
- [[Transfer Function]] · [[Poles and Zeros]] · [[Step Response Specifications]]

## Sources
- Lecture 1.07; MATH2048 Lectures 11–13
