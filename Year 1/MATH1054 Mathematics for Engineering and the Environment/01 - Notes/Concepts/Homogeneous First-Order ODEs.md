---
title: "Homogeneous First-Order ODEs"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Homogeneous-type equation", "x = vt substitution", "Equations of the form dx/dt = f(x/t)"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Separable First-Order ODEs]]", "[[Exact Differential Equations]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.2", "MATH1054 Module Booklet, Module 12"]
---

# Homogeneous First-Order ODEs

## Definition

> [!note] Definition
> An equation of the form $\dot x=F(x/t)$. The substitution $x=vt$, so $\dot x=v+t\dot v$, makes it separable:
> $$t\frac{\mathrm dv}{\mathrm dt}=F(v)-v$$

## Explanation
- **Test**: replace $x\to\lambda x$ and $t\to\lambda t$. If $\lambda$ cancels, the equation is of this type. Equivalently, all the terms have the same total degree.
- This is **not** the same as a "homogeneous linear" equation, which has no forcing term. The word is overloaded.

## Examples
- $t^2\dot x=x^2+xt$ gives $x=\frac{t}{A-\ln t}$ (Ex 10.14).
- $t\dot x=x+t\tan\frac xt$ gives $x=t\sin^{-1}(At)$ (Ex 20(d)).

## Related
- Topics: [[MATH1054 M12 - Differential Equations II]]
- Concepts: [[Separable First-Order ODEs]] · [[Exact Differential Equations]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §10.5.2
- MATH1054 Module Booklet, Module 12
