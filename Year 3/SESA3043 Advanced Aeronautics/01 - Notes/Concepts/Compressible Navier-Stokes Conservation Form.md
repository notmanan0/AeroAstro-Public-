---
title: "Compressible Navier-Stokes Conservation Form"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["compressible conservation variables", "Navier-Stokes conservative form", "conservative form", "conserved variables", "state vector", "flux vector form"]
tags: [sesa3043, concept, navier-stokes, conservation-form]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Navier-Stokes Equations]]", "[[Continuity Equation in Conservation Form]]", "[[Newtonian Stress Tensor]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L3 - SESA3043.txt"]
---

# Compressible Navier-Stokes Conservation Form

The compressible Navier–Stokes equations can be packed into one vector equation,

$$
\boxed{
\frac{\partial\mathbf Q}{\partial t}
+\frac{\partial\mathbf F_j}{\partial x_j}=\mathbf S
},
$$

where the **conservation variables** (CH1-2 slide 75; elsewhere called conserved variables or the state vector) are

$$
\mathbf Q=[\rho,\rho u,\rho v,\rho w,\rho E_T]^T.
$$

The fluxes $\mathbf F_j$ carry advection, pressure work, viscous stresses and heat conduction, and the source $\mathbf S$ holds the body-force terms.

The five equations govern mass, the three momentum components and total energy. The primitive variables are $\rho,u,v,w,p$ and a thermal variable, so an equation of state and a caloric relation are needed to close the system.

Writing the equations this way matters numerically. Discretising the conservation form keeps the integral conservation law exact, gives the correct weak solution across discontinuities such as shocks, and is the usual starting point for finite-volume CFD.

## Related

- [[Navier-Stokes Equations]] · [[Incompressible Navier-Stokes Equations]]
