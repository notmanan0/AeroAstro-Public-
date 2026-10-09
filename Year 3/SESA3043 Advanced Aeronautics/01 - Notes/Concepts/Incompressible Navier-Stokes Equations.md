---
title: "Incompressible Navier-Stokes Equations"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["incompressible NS equations"]
tags: [sesa3043, concept, navier-stokes, incompressible-flow]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]", "[[SESA3043 1.3 - Potential-Flow Review]]"]
related_concepts: ["[[Continuity Equation in Conservative Form]]", "[[Newtonian Stress Tensor]]", "[[Streamfunction and Velocity Potential]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L3 - SESA3043.txt"]
---

# Incompressible Navier-Stokes Equations

## Equations

For constant $\rho$ and $\mu$,

$$
\boxed{\nabla\cdot\mathbf u=0},
$$

$$
\boxed{
\frac{\partial\mathbf u}{\partial t}
+(\mathbf u\cdot\nabla)\mathbf u
=\mathbf f-\frac1\rho\nabla p+\nu\nabla^2\mathbf u
}.
$$

## Derivation points

1. Constant density reduces continuity to zero velocity divergence.
2. The product-rule term proportional to $\nabla\cdot\mathbf u$ drops from momentum.
3. The dilatational part of the Newtonian stress vanishes.
4. For constant viscosity, stress divergence becomes $\mu\nabla^2\mathbf u$.
5. Divide momentum by $\rho$ and use $\nu=\mu/\rho$.

## Further reductions

- steady: remove $\partial\mathbf u/\partial t$;
- two-dimensional: $w=0$ and $\partial/\partial z=0$;
- inviscid: set $\nu=0$ to obtain Euler;
- irrotational: introduce $\mathbf u=\nabla\phi$ and obtain potential flow.

## Related

- [[Newtonian Stress Tensor]] · [[Streamfunction and Velocity Potential]]

