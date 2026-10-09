---
title: "Compressible Navier-Stokes Conservation Form"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["compressible conservation variables", "Navier-Stokes conservative form"]
tags: [sesa3043, concept, navier-stokes, conservation-form]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Navier-Stokes Equations]]", "[[Continuity Equation in Conservative Form]]", "[[Newtonian Stress Tensor]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L3 - SESA3043.txt"]
---

# Compressible Navier-Stokes Conservation Form

## Compact form

$$
\boxed{
\frac{\partial\mathbf Q}{\partial t}
+\frac{\partial\mathbf F_j}{\partial x_j}=\mathbf S
}.
$$

The conserved state is

$$
\mathbf Q=[\rho,\rho u,\rho v,\rho w,\rho e_t]^T.
$$

The fluxes contain advection, pressure work, viscous stresses and heat conduction. Sources contain body-force contributions.

## Closure

The five conservation equations determine mass, three momentum components and total energy. Primitive variables include $\rho,u,v,w,p$ and a thermal variable. An equation of state and a caloric relation close the system.

## Why conservative form matters

- it preserves the integral conservation law under discretisation;
- it gives the correct weak solution across discontinuities such as shocks;
- it is the standard starting point for finite-volume CFD.

## Related

- [[Navier-Stokes Equations]] · [[Incompressible Navier-Stokes Equations]]

