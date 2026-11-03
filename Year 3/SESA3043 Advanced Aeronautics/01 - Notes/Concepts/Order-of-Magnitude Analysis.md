---
title: "Order-of-Magnitude Analysis"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["scale analysis", "scaling analysis", "order of magnitude analysis", "big-O estimates"]
tags: [sesa3043, concept, boundary-layer, scaling]
status: complete
parent_lectures: ["[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]"]
related_concepts: ["[[Prandtl Boundary-Layer Equations]]"]
sources: ["02 - Sources/Lectures/CH1-4 2D Incompressible BL(1).pdf"]
---

# Order-of-Magnitude Analysis

Order-of-magnitude analysis estimates every term of an equation by its typical size, $\mathcal O(\cdot)$, from characteristic scales. For the boundary layer these are $x\sim L$, $y\sim\delta$, $u\sim U_e$ and $p\sim\rho U_e^2$, and a derivative is a change over a distance, so $\partial u/\partial y\sim U_e/\delta$. You keep the largest terms and drop anything smaller by a factor of the small parameter.

Three rules do most of the work in 1.4. Two terms that have to cancel, as in continuity, must be the same order, which fixes $v\sim U_e\delta/L$. A term the physics needs, such as viscosity to satisfy no-slip, must be the same order as the dominant terms, which fixes $\delta/L\sim Re^{-1/2}$. And a term larger than everything else in its equation must itself be small, which gives $\partial p/\partial y\approx0$.

The method gives scalings and exponents, never constants: it says $\delta\propto\sqrt{\nu x/U}$, but the 4.91 comes from Blasius. The same approach gives the thermal boundary layer, lubrication theory and slender-body theory.

## Related

- [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#3. Order-of-magnitude analysis, step by step]] · [[Prandtl Boundary-Layer Equations]]
