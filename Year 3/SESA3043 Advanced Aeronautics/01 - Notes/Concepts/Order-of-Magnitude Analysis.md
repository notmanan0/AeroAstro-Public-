---
title: "Order-of-Magnitude Analysis"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["scale analysis", "scaling analysis"]
tags: [sesa3043, concept, boundary-layer, scaling]
status: complete
parent_lectures: ["[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]"]
related_concepts: ["[[Prandtl Boundary-Layer Equations]]"]
sources: ["02 - Sources/Lectures/CH1-4 2D Incompressible BL(1).pdf"]
---

# Order-of-Magnitude Analysis

## Definition

> [!note] Definition
> Estimate every term of an equation by its typical size, $\mathcal O(\cdot)$, using characteristic scales (here $x\sim L$, $y\sim\delta$, $u\sim U_e$, $p\sim\rho U_e^2$). Derivatives are "change over distance": $\partial u/\partial y\sim U_e/\delta$. Keep the largest terms; drop terms smaller by a factor of the small parameter.

## Rules used

1. Two terms that must cancel (e.g. in continuity) are the **same order**: this fixes $v\sim U_e\delta/L$.
2. A term needed for the physics (viscosity, for no-slip) must be the same order as the dominant terms: this fixes $\delta/L\sim Re^{-1/2}$.
3. If a term is larger than everything else in its equation, it must itself be small: this gives $\partial p/\partial y\approx0$.

## Key points

- It gives **scalings and exponents**, never constants: the analysis gives $\delta\propto\sqrt{\nu x/U}$, and Blasius supplies 4.91.
- The same method gives the thermal boundary layer, lubrication theory and slender-body theory.

## Related

- [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#3. Order-of-magnitude analysis, step by step]] · [[Prandtl Boundary-Layer Equations]]
