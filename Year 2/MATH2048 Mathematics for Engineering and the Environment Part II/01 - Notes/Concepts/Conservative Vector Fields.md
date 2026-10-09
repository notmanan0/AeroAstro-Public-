---
title: "Conservative Vector Fields"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Potential function", "Path independence", "Curl-free field", "Irrotational field", "Scalar potential"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
related_concepts: ["[[Line Integrals]]", "[[Gradient and Directional Derivative]]", "[[Stokes' Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture26_vector06.pdf"]
---

# Conservative Vector Fields

## Definition

> [!note] Definition
> $\mathbf F$ is **conservative** if $\mathbf F=\nabla\phi$ for some scalar potential $\phi$. In a **simply connected** region the following are equivalent:
> 1. line integrals of $\mathbf F$ are path-independent;
> 2. $\oint\mathbf F\cdot d\mathbf r=0$ around every closed curve;
> 3. $\mathbf F=\nabla\phi$;
> 4. $\nabla\times\mathbf F=\mathbf 0$.

## Explanation
**To show a field is NOT conservative**: compute $\nabla\times\mathbf F$ and exhibit a point where it is non-zero (2025/26 B1a). Alternatively, find two paths between the same points that give different integrals.

**To find $\phi$**:
1. Integrate $\phi_x=F_1$ with respect to $x$. The integration "constant" is $f(y,z)$.
2. Differentiate the result with respect to $y$ and match it with $F_2$ to find $f$, up to a new function $g(z)$.
3. Differentiate with respect to $z$ and match it with $F_3$ to find $g$.
4. Check that $\nabla\phi=\mathbf F$.

**The simply-connected caveat**: the field $\frac{(-y,x)}{x^2+y^2}$ has zero curl away from the axis, but its circulation around the axis is $2\pi$. This field is the potential vortex.

**Physics**: for a force $\mathbf F=-\nabla V$, the work done equals the drop in potential energy, so energy is conserved.

## Examples
- $\mathbf F=(2xy+\cos2y,\ x^2+2y-2x\sin2y)$ has potential $\phi=x^2y+x\cos2y+y^2$.
- $\mathbf F=xyz\,\mathbf i+z^2\mathbf j+y^2\mathbf k$ has $\nabla\times\mathbf F=(2y-2z,\ xy,\ -xz)\neq\mathbf 0$, so it is not conservative (2025/26 exam).

## Related
- [[Line Integrals]] · [[Gradient and Directional Derivative]] · [[Stokes' Theorem]] · [[Divergence, Curl and the Laplacian]]

## Sources
- Lecture 26; Lecture Notes §8.3.2–8.3.3
