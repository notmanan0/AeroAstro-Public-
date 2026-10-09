---
title: "Exact Differential Equations"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Exact equation", "Exactness test"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Partial Derivatives]]", "[[Integrating Factor Method]]", "[[Conservative Vector Fields]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.3", "MATH1054 Module Booklet, Module 12"]
---

# Exact Differential Equations

## Definition

> [!note] Definition
> $f(x,t)\,\dot x+g(x,t)=0$ is **exact** if there is an $F(x,t)$ with $F_x=f$ and $F_t=g$. Then $\frac{\mathrm d}{\mathrm dt}F(x,t)=0$, so the solution is $F=C$.
>
> $$\text{Test: }\frac{\partial f}{\partial t}=\frac{\partial g}{\partial x}$$

## Explanation
1. Check the test.
2. Integrate $f$ with respect to $x$, adding an unknown $h(t)$.
3. Differentiate with respect to $t$ and match to $g$ to find $h$.
4. Write $F=C$. It is usually left implicit.

This is the same idea as finding a potential $\phi$ for a conservative field ([[Conservative Vector Fields]]). A non-exact equation can sometimes be made exact with an integrating factor.

## Examples
- $(\ln\sin t-3x^2)\dot x+x\cot t+4t=0$ gives $x\ln\sin t-x^3+2t^2=C$ (Ex 10.16).
- $\cos t\,\dot x-x\sin t+1=0$ with $x(0)=2$ gives $x=\frac{2-t}{\cos t}$ (Ex 24(d)).
- $\sqrt t\,\dot x-xt=0$ is **not** exact (Ex 25(b)).

## Related
- Topics: [[MATH1054 M12 - Differential Equations II]]
- Concepts: [[Partial Derivatives]] · [[Integrating Factor Method]] · [[Conservative Vector Fields]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §10.5.3
- MATH1054 Module Booklet, Module 12
