---
title: "Newtonian Stress Tensor"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["Newtonian viscous stress", "Stokes stress tensor", "stress tensor", "viscous stress tensor", "Stokes' hypothesis", "Stokes relation"]
tags: [sesa3043, concept, stress-tensor, viscosity]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Newtonian Fluid and Strain-Rate Tensor]]", "[[Newtonian Fluid and Viscosity]]", "[[Incompressible Navier-Stokes Equations]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L2 - SESA3043.txt", "02 - Sources/Lectures/L3 - SESA3043.txt"]
---

# Newtonian Stress Tensor

In a Newtonian fluid the viscous stress is linear in the velocity gradients:

$$
\tau_{ij}
=\mu\left(
\frac{\partial u_i}{\partial x_j}
+\frac{\partial u_j}{\partial x_i}
\right)
+\lambda\delta_{ij}\nabla\cdot\mathbf u.
$$

Stokes' hypothesis, $\lambda=-2\mu/3$, makes the trace zero ($\tau_{ii}=0$, no mean viscous normal stress) and gives

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

The tensor is symmetric, $\tau_{ij}=\tau_{ji}$, because of angular-momentum conservation. Its diagonal terms are viscous normal stresses and its off-diagonal terms shear stresses. In incompressible flow with constant $\mu$, $\nabla\cdot\mathbf u=0$ and the stress divergence reduces to $\nabla\cdot\boldsymbol\tau=\mu\nabla^2\mathbf u$, with kinematic viscosity $\nu=\mu/\rho$.

There is a worked example, with stresses, vorticity and pressure for a linear velocity field and a compressible stretching flow, in [[SESA3043 1.2 - Conservation Laws and Governing Equations#9. Worked example: stress and momentum in a linear flow (suggested)|SESA3043 1.2 §9]].

## Related

- [[Newtonian Fluid and Strain-Rate Tensor]] · [[Incompressible Navier-Stokes Equations]]
