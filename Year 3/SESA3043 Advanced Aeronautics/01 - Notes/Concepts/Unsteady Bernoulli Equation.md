---
title: "Unsteady Bernoulli Equation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["unsteady Bernoulli", "Bernoulli for potential flow", "Bernoulli-Euler equation", "Cauchy-Lagrange integral"]
tags: [sesa3043, concept, potential-flow, bernoulli]
status: complete
parent_lectures: ["[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]"]
related_concepts: ["[[Bernoulli Equation]]", "[[Complex Velocity Potential]]", "[[Incompressible Navier-Stokes Equations]]"]
sources: ["02 - Sources/Lectures/Ch1_Notes_Unsteady Bernoulli Eqn.pdf"]
---

# Unsteady Bernoulli Equation

For incompressible, irrotational flow, $\mathbf u=\nabla\phi$, the momentum equation integrates to

$$\frac{\partial\phi}{\partial t}+\frac{q^2}{2}+\frac p\rho\ (+gz)=C(t),$$

where $C(t)$ is the same everywhere in the flow at a given instant. Because the flow is irrotational, it holds between any two points, not just along a streamline.

It comes from turning every term of Navier–Stokes into a gradient. The convective term is $(\mathbf u\cdot\nabla)\mathbf u=\nabla(q^2/2)+(\nabla\times\mathbf u)\times\mathbf u=\nabla(q^2/2)$. The viscous term vanishes identically, since $\nabla^2\mathbf u=\nabla(\nabla\cdot\mathbf u)-\nabla\times(\nabla\times\mathbf u)=\mathbf 0$. And $\partial_t\nabla\phi=\nabla\partial_t\phi$. With everything a gradient, the bracket can only depend on time. (The Blackboard notes' Eq. (1) leaves out the "$\times\mathbf u$" in the vorticity term.)

The viscous term being zero doesn't mean viscosity is irrelevant: potential flow can't satisfy no-slip, which is why boundary layers are needed. The $\partial\phi/\partial t$ term is the inertia of the fluid itself. It drives start-up transients in pipes and gives the added mass of an accelerating body, $\pi\rho R^2$ per unit length for a cylinder, with a total force of $2\pi\rho R^2\dot U$ on a cylinder held in an accelerating stream.

![[aa_unsteady_bernoulli.png|700]]

## Related

- [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#8. The unsteady Bernoulli equation]] · [[Bernoulli Equation]] (SESA1016)
