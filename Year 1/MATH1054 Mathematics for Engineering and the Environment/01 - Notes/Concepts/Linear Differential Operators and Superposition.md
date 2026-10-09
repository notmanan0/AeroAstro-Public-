---
title: "Linear Differential Operators and Superposition"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Linear operator", "Superposition principle", "CF + PI", "Complementary function", "Particular integral"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M13 - Differential Equations III]]"]
related_concepts: ["[[Auxiliary Equation]]", "[[Method of Undetermined Coefficients]]", "[[Classification of Differential Equations]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.8", "MATH1054 Module Booklet, Module 13"]
---

# Linear Differential Operators and Superposition

## Definition

> [!note] Definition
> $\mathrm L=a_n(t)\mathrm D^n+\dots+a_0(t)$, with $\mathrm D=\frac{\mathrm d}{\mathrm dt}$, is **linear**:
> $$\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2]$$

## Explanation
- **Superposition**: solutions of $\mathrm L[x]=0$ can be added and scaled. For $n$ independent solutions, the general solution is $\sum c_ix_i$ (the complementary function).
- **CF + PI**: every solution of $\mathrm L[x]=f$ is $x=x_c+x_p$, for any single particular solution $x_p$.
- **Split the forcing**: if $f=f_1+f_2$, then $x_p=x_{p1}+x_{p2}$.
- $\phi[f]=f^2$ is a nonlinear operator: $\phi[2f]\neq2\phi[f]$.

## Examples
- $\mathrm L=\mathrm D^2+4t\mathrm D-\sin t$ is linear (Ex 10.27).
- $\ddot x+5\dot x-9x=e^{-2t}+2-t$: find the PI for each piece separately (Ex 10.43).

## Related
- Topics: [[MATH1054 M13 - Differential Equations III]]
- Concepts: [[Auxiliary Equation]] · [[Method of Undetermined Coefficients]] · [[Classification of Differential Equations]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §10.8
- MATH1054 Module Booklet, Module 13
