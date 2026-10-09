---
title: "Newtonian Stress Tensor"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["Newtonian viscous stress", "Stokes stress tensor"]
tags: [sesa3043, concept, stress-tensor, viscosity]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Newtonian Fluid and Strain-Rate Tensor]]", "[[Newtonian Fluid and Viscosity]]", "[[Incompressible Navier-Stokes Equations]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L2 - SESA3043.txt", "02 - Sources/Lectures/L3 - SESA3043.txt"]
---

# Newtonian Stress Tensor

## Constitutive law

$$
\tau_{ij}
=\mu\left(
\frac{\partial u_i}{\partial x_j}
+\frac{\partial u_j}{\partial x_i}
\right)
+\lambda\delta_{ij}\nabla\cdot\mathbf u.
$$

With Stokes' hypothesis $\lambda=-2\mu/3$,

$$
\boxed{
\tau_{ij}
=\mu\left(
\frac{\partial u_i}{\partial x_j}
+\frac{\partial u_j}{\partial x_i}
-\frac23\delta_{ij}\frac{\partial u_k}{\partial x_k}
\right)
}.
$$

## Properties

- $\tau_{ij}=\tau_{ji}$ from angular-momentum conservation.
- Diagonal terms are viscous normal stresses.
- Off-diagonal terms are shear stresses.
- For incompressible constant-$\mu$ flow, $\nabla\cdot\mathbf u=0$ and $\nabla\cdot\boldsymbol\tau=\mu\nabla^2\mathbf u$.
- $\nu=\mu/\rho$ is the kinematic viscosity.

## Related

- [[Newtonian Fluid and Strain-Rate Tensor]] · [[Incompressible Navier-Stokes Equations]]

