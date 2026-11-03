---
title: "Incompressible Navier-Stokes Equations"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["incompressible NS equations", "incompressible N-S equations", "divergence-free flow", "solenoidal velocity field"]
tags: [sesa3043, concept, navier-stokes, incompressible-flow]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]", "[[SESA3043 1.2b - Potential-Flow Review]]"]
related_concepts: ["[[Continuity Equation in Conservation Form]]", "[[Newtonian Stress Tensor]]", "[[Streamfunction and Velocity Potential]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L3 - SESA3043.txt"]
---

# Incompressible Navier-Stokes Equations

For constant density and viscosity the Navier–Stokes equations become

$$
\boxed{\nabla\cdot\mathbf u=0},
\qquad
\boxed{
\frac{\partial\mathbf u}{\partial t}
+(\mathbf u\cdot\nabla)\mathbf u
=\mathbf f-\frac1\rho\nabla p+\nu\nabla^2\mathbf u
}.
$$

Getting there from the general equations takes a few steps. Constant density reduces continuity to zero velocity divergence, which removes the product-rule term proportional to $\nabla\cdot\mathbf u$ from the momentum equation and kills the dilatational part of the Newtonian stress. With constant viscosity the stress divergence becomes $\mu\nabla^2\mathbf u$, and dividing by $\rho$ with $\nu=\mu/\rho$ gives the form above.

From here the usual reductions are steady flow (drop $\partial\mathbf u/\partial t$), two-dimensional flow ($w=0$, $\partial/\partial z=0$), inviscid flow ($\nu=0$, giving Euler), and irrotational flow ($\mathbf u=\nabla\phi$, giving potential flow).

## Related

- [[Newtonian Stress Tensor]] · [[Streamfunction and Velocity Potential]]
