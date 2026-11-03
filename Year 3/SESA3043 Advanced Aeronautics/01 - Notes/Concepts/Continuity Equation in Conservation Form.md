---
title: "Continuity Equation in Conservation Form"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["Continuity Equation in Conservative Form", "conservative form of continuity", "divergence form of continuity", "differential mass conservation", "conservative continuity equation"]
tags: [sesa3043, concept, continuity]
status: complete
parent_lectures: ["[[SESA3043 1.2 - Conservation Laws and Governing Equations]]"]
related_concepts: ["[[Reynolds Transport Theorem]]", "[[Material Derivative]]", "[[Incompressible Navier-Stokes Equations]]"]
sources: ["02 - Sources/Lectures/CH1-2 Governing Equations(1).pdf", "02 - Sources/Lectures/L2 - SESA3043.txt"]
---

# Continuity Equation in Conservation Form

In conservation form, the continuity equation says that the local rate of mass accumulation plus the net outward mass flux is zero:

$$
\boxed{
\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)=0
}
\qquad\text{or}\qquad
\frac{\partial\rho}{\partial t}+\frac{\partial(\rho u_i)}{\partial x_i}=0.
$$

Expanding the divergence with the product rule gives the material (non-conservation) form,

$$
\boxed{
\frac{D\rho}{Dt}+\rho\nabla\cdot\mathbf u=0
},
$$

and for constant density this reduces to

$$
\boxed{\nabla\cdot\mathbf u=0}.
$$

CH1-2 and the lecture (L2, l. 418) say "conservation form" and "non-conservation form". Other texts call the first one the conservative or divergence form.

## Related

- [[Material Derivative]] · [[Incompressible Navier-Stokes Equations]]
