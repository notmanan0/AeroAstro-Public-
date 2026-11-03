---
title: "PDE Classification"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Hyperbolic", "Parabolic", "Elliptic", "Discriminant b^2-ac", "Tricomi equation"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]"]
related_concepts: ["[[Wave Equation]]", "[[Heat Equation]]", "[[Laplace's Equation]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture14_Hyperbolic1.pdf", "02 - Sources/Lectures/MATH2048 Lecture 14.txt"]
---

# PDE Classification

A linear second-order PDE $au_{xx}+2bu_{xy}+cu_{yy}+du_x+eu_y+fu=0$ is **hyperbolic** if $b^2-ac>0$, **parabolic** if $b^2-ac=0$ and **elliptic** if $b^2-ac<0$. Only the principal part, the coefficients $a$, $b$ and $c$ of the second derivatives, decides the type.

The test is the discriminant of a quadratic, written $b^2-ac$ rather than $B^2-4AC$ because the mixed term carries a factor 2. If a PDE is given with $B\,u_{xy}$, use $b=B/2$.

The three types behave differently, and that is why the classification matters. Hyperbolic equations, like the wave equation $u_{tt}=c^2u_{xx}$, carry information at a finite speed and describe gas dynamics, acoustics and electromagnetism. Parabolic equations, like the heat equation $u_t=ku_{xx}$, come from averaging over small-scale behaviour; they smooth things out and spread any disturbance over the whole domain at once. Elliptic equations, like Laplace's equation $u_{xx}+u_{yy}=0$, are static, and are the steady-state limit of the other two.

Each type needs different data for a unique solution. A hyperbolic equation needs $u$ and $u_t$ initially and a condition at each end; a parabolic one needs only $u$ initially and a condition at each end; an elliptic one needs a condition on every part of the boundary, and not all of them can be Neumann, or the solution is fixed only up to a constant.

When $a$, $b$ and $c$ vary, the type can change across the domain. The Tricomi equation, a model of transonic flow written on the slides as $yu_{xx}=u_{yy}$, has $b^2-ac=y$: hyperbolic above $y=0$ and elliptic below. Problems of mixed type are hard and best avoided.

## Related

- Derivation and examples: [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]
- [[Wave Equation]] · [[Heat Equation]] · [[Laplace's Equation]]
