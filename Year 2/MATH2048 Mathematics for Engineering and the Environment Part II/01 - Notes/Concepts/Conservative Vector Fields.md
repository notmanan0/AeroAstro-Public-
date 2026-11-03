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
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture26_vector06.pdf", "02 - Sources/Lectures/MATH2048 Lecture 22.txt", "02 - Sources/Lectures/MATH2048 Lecture 26.txt"]
---

# Conservative Vector Fields

A vector field is **conservative** if it is the gradient of a scalar potential. MATH2048 uses $\mathbf F=-\nabla\phi$, so that a force pushes towards lower potential energy; then $\int_C\mathbf F\cdot d\mathbf r=\phi(A)-\phi(B)$ for any curve from $A$ to $B$.

The proof is the chain rule: along the curve, $\mathbf F\cdot\frac{d\mathbf r}{dt}=-\frac{d\phi}{dt}$, which integrates to the change in $\phi$. So the work is path-independent and zero round every closed loop. The potential is fixed only up to a constant, since only differences of potential energy matter; set it to zero, or to vanish somewhere meaningful such as infinity.

To test a field, use $\nabla\times\nabla\phi=\mathbf 0$: a field with non-zero curl is not conservative. Zero curl is enough when the field is smooth everywhere in a region without holes; it fails, for example, at a point charge where the potential blows up. To find $\phi$, integrate the simplest component equation, such as $-\partial\phi/\partial z=F_3$, keeping the "constant" as a function of the other variables, then differentiate in another variable and match, and repeat until no unknown functions remain. Lecture 26's $\mathbf F=(2xy+\cos2y)\,\mathbf i+(x^2-2x\sin2y+2y)\,\mathbf j$ has $\phi=-x^2y-x\cos2y-y^2$. In fluids, a velocity with zero curl is irrotational, $\mathbf v=\nabla\phi$, and if it is also incompressible the potential obeys [[Laplace's Equation]]: potential flow.

## Related

- Derivation and examples: [[MATH2048 VC3 - Line Integrals and Conservative Fields]]
- [[Line Integrals]] · [[Gradient and Directional Derivative]] · [[Divergence, Curl and the Laplacian]]
