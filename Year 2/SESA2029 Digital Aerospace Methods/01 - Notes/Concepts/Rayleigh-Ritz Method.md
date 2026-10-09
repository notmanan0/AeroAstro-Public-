---
title: "Rayleigh-Ritz Method"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["Rayleigh-Ritz", "Ritz method", "assumed displacement method"]
tags: [sesa2029, concept, fea, energy-methods]
status: complete
parent_lectures: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]"]
related_concepts: ["[[Principle of Minimum Total Potential Energy]]", "[[Shape Functions]]", "[[Strong and Weak Forms]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Rayleigh-Ritz Method

## Definition

> [!note] Definition
> An approximate energy method. Assume the displacement field as a function of the coordinates with a finite number of unknown coefficients, chosen to satisfy the (generalised) displacement BCs. Then minimise the total potential energy with respect to those coefficients.

## Explanation

- It reduces an infinite-DOF continuum to a few DOF (the coefficients).
- **Polynomials** are the usual trial functions: linear $u = a+bx$, quadratic, cubic, and so on.
- **Limitation**: a single trial function must cover the *whole* structure and satisfy all its BCs, which is only practical for simple geometry.
- **FEM = piecewise Rayleigh–Ritz**: apply it to each small element with the coefficients rewritten as nodal DOF (shape functions), then assemble. That removes the geometric limitation.

## Examples

- A bar with $u = a+bx$, $u(0) = u_i$ and $u(L) = u_j$ gives $U = \tfrac{AE}{2L}(u_j-u_i)^2$ and hence the exact bar stiffness.
- A beam with a cubic $v(x)$ and nodal $v$ and $\theta$ gives the Hermite beam element ([[Euler-Bernoulli Beam Element]]).

## Related

- Parent lectures: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]
- Related concepts: [[Principle of Minimum Total Potential Energy]] · [[Shape Functions]] · [[Strong and Weak Forms]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt
