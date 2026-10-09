---
title: "Complex Velocity Potential"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["complex potential", "Phi = phi + i psi"]
tags: [sesa3043, concept, potential-flow, complex-analysis]
status: complete
parent_lectures: ["[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]"]
related_concepts: ["[[Streamfunction and Velocity Potential]]", "[[General Doublet]]", "[[Conformal Mapping]]"]
sources: ["02 - Sources/Lectures/CH1-3 Potential Flow.pdf"]
---

# Complex Velocity Potential

## Definition

> [!note] Definition
> In 2-D incompressible irrotational flow, $\Phi(z)=\phi+i\psi$ with $z=x+iy$, and
>
> $$\frac{\mathrm d\Phi}{\mathrm dz}=u-iv,\qquad q=\left|\frac{\mathrm d\Phi}{\mathrm dz}\right|.$$

## Why it works

The derivative of an analytic function is direction-independent only if the **Cauchy–Riemann** equations hold, $\phi_x=\psi_y$ and $\phi_y=-\psi_x$. These are exactly $u=\phi_x=\psi_y$ and $v=\phi_y=-\psi_x$. Consequences: $\phi$ and $\psi$ are both harmonic, their contours are orthogonal, and **every analytic function is a potential flow**.

## Elementary flows

| Flow | $\Phi(z)$ |
|---|---|
| uniform, angle $\alpha$ | $Ue^{-i\alpha}z$ |
| source $m$ at $z_0$ | $\frac{m}{2\pi}\ln(z-z_0)$ |
| vortex, counter-clockwise $\Gamma$ | $-\frac{i\Gamma}{2\pi}\ln z$ |
| doublet, source upstream | $\frac{\mu}{2\pi z}$ |
| cylinder | $U(z+R^2/z)$ |
| wedge/corner | $-kz^{m+1}$ |

## Key points

- One ordinary derivative replaces two sets of partial derivatives (the 1 Oct lecture's main message).
- Watch the minus sign: the imaginary part of $\mathrm d\Phi/\mathrm dz$ is $-v$.
- The slide tables mix vortex sign conventions; state yours.

## Related

- Full derivations: [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#3. Complex numbers and the complex velocity potential]]
- [[Streamfunction and Velocity Potential]] · [[General Doublet]] · [[Conformal Mapping]] · [[Elementary Potential Flows]]
