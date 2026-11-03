---
title: "Flux Integrals"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Surface integral", "dS", "Vector area element", "Surface area element"]
tags: [math2048, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]"]
related_concepts: ["[[Divergence Theorem]]", "[[Stokes' Theorem]]", "[[Jacobian and Volume Elements]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture27_vector07.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture28_vector08.pdf", "02 - Sources/Lectures/MATH2048 Lecture 27.txt", "02 - Sources/Lectures/MATH2048 Lecture 28.txt"]
---

# Flux Integrals

The **flux** of a vector field through a surface is $\iint_S\mathbf F\cdot\hat{\mathbf n}\,dA=\iint\mathbf F\cdot d\mathbf S$, the amount of the field passing through it. For a surface parametrised by $\mathbf r(s,t)$, $d\mathbf S=\mathbf N\,ds\,dt$ with $\mathbf N=\mathbf r_s\times\mathbf r_t$.

The tangent vectors $\mathbf r_s$ and $\mathbf r_t$ span a small parallelogram of area $|\mathbf r_s\times\mathbf r_t|\,ds\,dt$, so $dA=|\mathbf N|\,ds\,dt$ for areas and scalar integrals, and $\mathbf N$ is normal to the surface. In the flux, $\hat{\mathbf n}\,dA=\mathbf N\,ds\,dt$, so no normalising is needed. Swapping the order of the cross product reverses $\mathbf N$ and the sign of the flux, so always check the direction against what the question wants. For the course's parametrisations, $\mathbf N=a\cos s\,\mathbf i+a\sin s\,\mathbf j$ on a cylinder (outward, $|\mathbf N|=a$) and $|\mathbf N|=a^2\sin t$ on a sphere, giving areas $2\pi ah$ and $4\pi a^2$. For a graph $z=f(x,y)$, $d\mathbf S=(-f_x,-f_y,1)\,dx\,dy$, pointing up.

Lecture 28's example, $\mathbf F=x\,\mathbf i+y\,\mathbf j+(z-2y)\,\mathbf k$ through the helicoid $(s\cos t,s\sin t,t)$, has $\mathbf N=(\sin t,-\cos t,s)$ and flux $\pi^2$. For a closed surface the [[Divergence Theorem]] usually gives the flux more quickly.

![[m2048_vc_helicoid.png|480]]

## Related

- Derivation and examples: [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]
- [[Divergence Theorem]] · [[Stokes' Theorem]] · [[Jacobian and Volume Elements]]
