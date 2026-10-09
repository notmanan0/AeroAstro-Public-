---
title: "Integrating Factor Method"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Integrating factor", "First-order linear ODE"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Exact Differential Equations]]", "[[Separable First-Order ODEs]]", "[[RC and RL Transients]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.4", "MATH1054 Module Booklet, Module 12"]
---

# Integrating Factor Method

## Definition

> [!note] Definition
> For $\dot x+P(t)x=Q(t)$, multiply by $\mu=e^{\int P\,\mathrm dt}$:
>
> $$\frac{\mathrm d}{\mathrm dt}(\mu x)=\mu Q\quad\Rightarrow\quad x=\frac1\mu\Big[\int\mu Q\,\mathrm dt+C\Big]$$

## Explanation
- **Standard form first**: the coefficient of $\dot x$ must be 1.
- No constant is needed in $\int P\,\mathrm dt$. Note that $e^{\pm\ln t}=t^{\pm1}$.
- The solution is a transient $C/\mu$ plus a particular part. This previews CF + PI.
- It solves **every** first-order linear ODE, including RC and RL circuits and first-order control systems.

## Examples
- $\dot x+tx=t$ gives $x=1+Ce^{-t^2/2}$ (Ex 10.17).
- $\dot x-\frac xt=t^2-3$ with $x(1)=-1$ gives $x=\frac12t^3-3t\ln t-\frac32t$ (Ex 32(c)).
- $\dot x+\frac{2x}t=\cos t$ gives $x=\sin t+\frac{2\cos t}t-\frac{2\sin t}{t^2}+\frac C{t^2}$ (Ex 33(c)).

## Related
- Topics: [[MATH1054 M12 - Differential Equations II]]
- Concepts: [[Exact Differential Equations]] · [[Separable First-Order ODEs]] · [[RC and RL Transients]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §10.5.4
- MATH1054 Module Booklet, Module 12
