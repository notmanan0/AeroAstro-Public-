---
title: "Linearisation about an Equilibrium Point"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 5: State-Space Models"
aliases: ["linearising around an equilibrium point", "operating point", "equilibrium point", "Jacobian linearisation", "tangent approximation", "epsilon expansion"]
tags: [sesa3047, concept, linearisation, state-space]
status: complete
coverage: "Chapter 5 §5.2; lectured in L14 ll. 64–145 and 236–509 (Mon 2 Nov)"
parent_lectures: ["[[SESA3047 5.1 - State-Space Form and Linearisation]]", "[[SESA3047 5.2 - Longitudinal State-Space Model]]"]
related_concepts: ["[[Small Perturbation Linearisation]]", "[[State-Space Representation]]", "[[Linear, Nonlinear and Time-Varying Models]]"]
sources: ["02 - Sources/Lectures/Chapter_5.pdf", "02 - Sources/Lectures/02 November 2026 at 11_53_51.txt"]
---

# Linearisation about an Equilibrium Point

Linearising a nonlinear system means replacing it, near one equilibrium point, by the linear system that matches its value and slope there: the tangent of the function, or in many variables its Jacobian.

The course does it by expansion. Every variable is written as its equilibrium value plus $\epsilon$ times a perturbation, $x=x_0+\epsilon x_1$ with $\epsilon\ll1$, and substituted into the equations. Terms in $\epsilon^0$ must reproduce the equilibrium condition and cancel; if they do not, there is an algebra mistake (L14 ll. 469–489). Terms in $\epsilon^2$ and higher are dropped. What is left, divided by $\epsilon$, is linear in the perturbations. The result is the same as $\mathbf A=\partial\mathbf f/\partial\mathbf x|_0$, $\mathbf B=\partial\mathbf f/\partial\mathbf u|_0$ ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#5. Linear and nonlinear models|1.2 §5]]).

A linearisation is meaningless without its point. $\sin x$ linearises to $x$ about $0$ and to $-(x-\pi)$ about $\pi$; for $\dot x=\sin x$ the first is an unstable equilibrium and the second a stable one (L14 ll. 79–98). For products of variables, the rule L14 drew out is that a product survives at first order only when one factor has a non-zero equilibrium value: $rU$ leaves $U_\infty r_1$, while $qW$ and $rV$ vanish about straight flight.

The linear model is accurate only for small perturbations. For $\sin x\approx x$ the error is 0.5 % at 10° and 2 % at 20°, growing as $\epsilon^2$.

## Related

- [[SESA3047 5.1 - State-Space Form and Linearisation#2. Linearising about an equilibrium: the sine example (L14 ll. 64–145)|5.1 §2]] (sine example) · [[SESA3047 Chapter 5 Practice Problems - Solutions#Problem 1. Equilibria and linearisation of a made-up system|Practice problem 1]]
- [[Small Perturbation Linearisation]] (SESA2027, the aircraft case) · [[State-Space Representation]] · [[Linear, Nonlinear and Time-Varying Models]]
