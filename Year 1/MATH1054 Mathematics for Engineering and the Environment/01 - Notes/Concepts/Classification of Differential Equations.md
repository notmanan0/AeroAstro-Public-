---
title: "Classification of Differential Equations"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["ODE classification", "Linear ODE", "Order of an ODE", "Homogeneous ODE"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M06 - Differential Equations I]]"]
related_concepts: ["[[Separable First-Order ODEs]]", "[[Linear Differential Operators and Superposition]]", "[[PDE Classification]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.3", "MATH1054 Module Booklet, Module 6"]
---

# Classification of Differential Equations

## Definition

> [!note] Definition
> - **Order**: the highest derivative present.
> - **Linear**: the dependent variable and its derivatives appear only to the first power, are not multiplied together, and are not inside functions.
> - **Homogeneous** (linear only): there is no term free of the dependent variable.
> - **ODE or PDE**: one independent variable, or several.

## Explanation
- The coefficients may depend on the **independent** variable without breaking linearity: $\ddot x+t\dot x=4\sin t$ is linear.
- **Nonlinear examples**: $\dot x^2$, $x\dot x$, $\sin x$, $\ddot x\,\dot x$.
- The classification decides the method: separable, exact, integrating factor, CF + PI, and so on.
- **Counting constants**: an $n$th-order ODE has $n$ arbitrary constants, and each independent condition removes one.

## Examples
- $\ddot s+(\sin t)\dot s+(t+\cos t)s=e^t$: linear, nonhomogeneous, 2nd order (Ex 2(b)).
- $y_{xx}-y_{tt}=0$: a linear, homogeneous, 2nd-order **PDE** (the wave equation; Specimen Test 6, Q1).

## Related
- Topics: [[MATH1054 M06 - Differential Equations I]]
- Concepts: [[Separable First-Order ODEs]] · [[Linear Differential Operators and Superposition]] · [[PDE Classification]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §10.3
- MATH1054 Module Booklet, Module 6
