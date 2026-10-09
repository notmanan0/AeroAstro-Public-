---
title: "Unsteady Bernoulli Equation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["unsteady Bernoulli", "Bernoulli for potential flow"]
tags: [sesa3043, concept, potential-flow, bernoulli]
status: complete
parent_lectures: ["[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]"]
related_concepts: ["[[Bernoulli Equation]]", "[[Complex Velocity Potential]]", "[[Incompressible Navier-Stokes Equations]]"]
sources: ["02 - Sources/Lectures/Ch1_Notes_Unsteady Bernoulli Eqn.pdf"]
---

# Unsteady Bernoulli Equation

## Definition

> [!note] Definition
> For incompressible, irrotational flow ($\mathbf u=\nabla\phi$):
>
> $$\frac{\partial\phi}{\partial t}+\frac{q^2}{2}+\frac p\rho\ (+gz)=C(t),$$
>
> the same constant everywhere in the flow at a given instant.

## Derivation in brief

$(\mathbf u\cdot\nabla)\mathbf u=\nabla(q^2/2)+(\nabla\times\mathbf u)\times\mathbf u=\nabla(q^2/2)$; $\nabla^2\mathbf u=\nabla(\nabla\cdot\mathbf u)-\nabla\times(\nabla\times\mathbf u)=\mathbf 0$; $\partial_t\nabla\phi=\nabla\partial_t\phi$. Every term of Navier–Stokes is then a gradient, so the bracket is a function of time only.

## Key points

- Valid between **any** two points (not just along a streamline), because the flow is irrotational.
- The viscous term is identically zero, but no-slip cannot be satisfied: hence boundary layers.
- The $\partial\phi/\partial t$ term is fluid inertia: start-up transients in pipes, and **added mass** ($\pi\rho R^2$ for a cylinder; total force $2\pi\rho R^2\dot U$ in an accelerating stream).
- The Blackboard notes' Eq. (1) omits "$\times\mathbf u$" from the vorticity term.

![[aa_unsteady_bernoulli.png|700]]

## Related

- [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#8. The unsteady Bernoulli equation]] · [[Bernoulli Equation]] (SESA1016)
