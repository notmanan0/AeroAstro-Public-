---
title: "Continuity Equation in Conservative Form"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["differential mass conservation", "conservative continuity equation"]
tags: [sesa3043, concept, continuity]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Reynolds Transport Theorem]]", "[[Material Derivative]]", "[[Incompressible Navier-Stokes Equations]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L2 - SESA3043.txt"]
---

# Continuity Equation in Conservative Form

## Equation

$$
\boxed{
\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)=0
}
$$

or

$$
\frac{\partial\rho}{\partial t}+\frac{\partial(\rho u_i)}{\partial x_i}=0.
$$

It states that local mass accumulation plus net outward mass flux is zero.

## Material form

Use the product rule:

$$
\boxed{
\frac{D\rho}{Dt}+\rho\nabla\cdot\mathbf u=0
}.
$$

For constant density,

$$
\boxed{\nabla\cdot\mathbf u=0}.
$$

## Related

- [[Material Derivative]] · [[Incompressible Navier-Stokes Equations]]

