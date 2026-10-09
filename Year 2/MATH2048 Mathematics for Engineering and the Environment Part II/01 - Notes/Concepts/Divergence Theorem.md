---
title: "Divergence Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Gauss's theorem", "Gauss divergence theorem"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
related_concepts: ["[[Flux Integrals]]", "[[Jacobian and Volume Elements]]", "[[Stokes' Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture29_vector09.pdf"]
---

# Divergence Theorem

## Definition

> [!note] Definition
> $$\iiint_V\nabla\cdot\mathbf F\,dV=\oiint_{\partial V}\mathbf F\cdot d\mathbf S\qquad(\text{closed surface, outward normal}).$$

## Explanation
**Meaning**: total source strength inside $V$ equals the net outflow through its boundary.

**When to use it**:
- the flux through a closed surface made of several awkward faces;
- the flux through an **open** surface: close it off (for example with a disc), apply Gauss, then subtract the flux through the lid.

**Corollaries**:
- $\oiint\mathbf r\cdot d\mathbf S=3V$.
- $\oiint(\nabla\times\mathbf G)\cdot d\mathbf S=0$, because $\nabla\cdot(\nabla\times\mathbf G)=0$.

**Pitfalls**:
- Every face must use the **outward** normal.
- The volume integral normally needs cylindrical or spherical coordinates, so include the Jacobian.

## Examples
- $\mathbf F=\mathbf r$ on a cylinder: $3\pi a^2h$.
- $\mathbf F=2xy^2\,\mathbf i+z^3\mathbf j-x^2y\,\mathbf k$ through a hemisphere: $\frac{4\pi a^5}{15}$.
- PS11 Q3, quarter cylinder: $3\pi/4$ both ways.
- 2025/26 B2, $\mathbf F=\nabla(x^2+y^2+z^3)$ over the unit upper hemisphere: $\iiint(4+6z)\,dV=\frac{25\pi}{6}$ ([[MATH2048 Past Paper Solutions]]).

## Related
- [[Flux Integrals]] · [[Jacobian and Volume Elements]] · [[Stokes' Theorem]]

## Sources
- Lecture 29; Lecture Notes §8.3.6
