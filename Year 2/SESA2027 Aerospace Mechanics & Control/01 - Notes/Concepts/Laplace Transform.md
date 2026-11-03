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

The Laplace transform

$$
\mathcal L\{g(t)\} = G(s) = \int_0^\infty g(t)e^{-st}\,dt,\qquad s = \sigma+j\omega,
$$

turns linear constant-coefficient ODEs into algebraic equations in $s$: differentiation becomes multiplication by $s$, integration becomes division by $s$, and the initial conditions come along automatically.

The route through a problem is always the same: transform the ODE, solve the algebra for the output, split it into partial fractions and invert term by term from a table. Compared with the classical complementary-function-plus-particular-integral method, it handles piecewise inputs such as steps and pulses easily, and it leads straight to transfer functions. The SPO step response in A4 is a typical case: $X(s) = K/[s(s^2+0.744s+1.992)]$ inverts to $x(t) = r_1+r_2e^{\sigma t}\cos\omega t+r_3e^{\sigma t}\sin\omega t$ with $\sigma = -0.372$ and $\omega = 1.362$ ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]).

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

The final value theorem, $\lim_{t\to\infty}g(t) = \lim_{s\to0}sG(s)$, gives the steady state directly, provided the limit exists, which in practice means the system is stable. The delay entry matters later in the module: $e^{-sT_d}$ has unit magnitude and phase $-\omega T_d$, which is how sensor and digital latency erode the phase margin ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]). MATH2048 Lectures 11–13 cover the transform itself.

## Related

- [[Transfer Function]] · [[Poles and Zeros]] · [[Step Response Specifications]]
- MATH2048: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]
