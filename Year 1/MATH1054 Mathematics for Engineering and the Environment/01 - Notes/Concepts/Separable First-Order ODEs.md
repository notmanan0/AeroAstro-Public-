---
title: "Separable First-Order ODEs"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Separation of variables (ODE)", "Separable equation", "Variables separable"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M06 - Differential Equations I]]"]
related_concepts: ["[[Homogeneous First-Order ODEs]]", "[[Integrating Factor Method]]", "[[Classification of Differential Equations]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.1", "MATH1054 Module Booklet, Module 6"]
---

# Separable First-Order ODEs

## Definition

> [!note] Definition
>
> $$\frac{\mathrm dx}{\mathrm dt}=f(t)g(x)\quad\Longrightarrow\quad\int\frac{\mathrm dx}{g(x)}=\int f(t)\,\mathrm dt+C$$

## Explanation
- Separate, integrate with **one** constant, apply the initial condition, then solve for $x$, choosing the sign from the data.
- **Lost solutions**: where $g(x)=0$ (e.g. $x\equiv0$).
- **Non-uniqueness**: if $g$ is singular at the initial point, more than one solution can fit (Ex 14(a)).
- **Finite-time blow-up**: nonlinear equations can escape to infinity, e.g. $\dot x=e^{x+t}$.
- Not to be confused with separation of variables for PDEs ([[Separation of Variables]]).

## Examples
- $\dot x=4xt$ gives $x=Ae^{2t^2}$ (Ex 10.13).
- $t^2\dot x=1/x$ with $x(4)=9$ gives $x=\sqrt{\frac{163}2-\frac2t}$ (Ex 12(b)).
- $\dot x=\frac{t+1}{x+1}$ with $x(0)=1$ gives $x=\sqrt{t^2+2t+4}-1$ (Specimen Test 6, Q3).

## Related
- Topics: [[MATH1054 M06 - Differential Equations I]]
- Concepts: [[Homogeneous First-Order ODEs]] · [[Integrating Factor Method]] · [[Classification of Differential Equations]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §10.5.1
- MATH1054 Module Booklet, Module 6
