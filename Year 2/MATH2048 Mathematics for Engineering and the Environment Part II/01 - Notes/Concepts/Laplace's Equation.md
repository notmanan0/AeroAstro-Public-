---
title: "Laplace's Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Harmonic function", "Maximum principle", "Potential equation"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE5 - Laplace's Equation]]"]
related_concepts: ["[[Separation of Variables]]", "[[Streamfunction and Velocity Potential]]", "[[Divergence, Curl and the Laplacian]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture20_LaplaceEquation1.pdf", "02 - Sources/Lectures/MATH2048 Lecture 20.txt"]
---

# Laplace's Equation

**Laplace's equation** $\nabla^2u=0$, in two-dimensional Cartesian coordinates $u_{xx}+u_{yy}=0$, is the prototype elliptic PDE. With a source, $\nabla^2u=f$, it is Poisson's equation.

It is the static limit of both the wave and heat equations, $u_{tt}=c^2\nabla^2u$ and $u_t=\kappa^2\nabla^2u$, with the time derivatives set to zero. The Laplacian $\nabla^2=\nabla\cdot\nabla$ is coordinate-free, so the equation holds in any coordinates even though its Cartesian form does not. All its conditions are boundary conditions, one on each part of the boundary, and they cannot all be Neumann.

On a rectangle, separation gives trig functions in the direction with homogeneous conditions on both sides and $\cosh$ and $\sinh$ in the other, so on the unit square with $u=x(1-x)$ on $y=1$ and zero elsewhere, $u=\sum\frac{4(1-(-1)^n)}{(n\pi)^3\sinh n\pi}\sin n\pi x\,\sinh n\pi y$. The maximum principle says that without a source a solution takes its maximum and minimum on the boundary, so zero boundary values force $u\equiv0$, and a value inside larger than any on the boundary means there is a source.

![[m2048_pde_laplace_square.png|480]]

## Related

- [[MATH2048 PDE5 - Laplace's Equation]] · [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]
- [[PDE Classification]] · [[Separation of Variables]] · [[Divergence, Curl and the Laplacian]]
