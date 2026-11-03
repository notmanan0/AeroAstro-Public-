---
title: "Complex Velocity Potential"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["complex potential", "Phi = phi + i psi", "complex velocity", "w(z)", "F(z)", "Cauchy-Riemann equations"]
tags: [sesa3043, concept, potential-flow, complex-analysis]
status: complete
parent_lectures: ["[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]"]
related_concepts: ["[[Streamfunction and Velocity Potential]]", "[[General Doublet]]", "[[Conformal Mapping]]"]
sources: ["02 - Sources/Lectures/CH1-3 Potential Flow.pdf"]
---

# Complex Velocity Potential

In two-dimensional incompressible irrotational flow, the potential and streamfunction combine into one analytic function of $z=x+iy$, the complex velocity potential $\Phi(z)=\phi+i\psi$. Its derivative gives the velocity directly:

$$\frac{\mathrm d\Phi}{\mathrm dz}=u-iv,\qquad q=\left|\frac{\mathrm d\Phi}{\mathrm dz}\right|.$$

Note the minus sign: the imaginary part of $\mathrm d\Phi/\mathrm dz$ is $-v$.

The derivative of a complex function only exists, independent of direction, if the Cauchy–Riemann equations hold: $\phi_x=\psi_y$ and $\phi_y=-\psi_x$. Those are just $u=\phi_x=\psi_y$ and $v=\phi_y=-\psi_x$. So $\phi$ and $\psi$ are both harmonic, their contours cross at right angles, and every analytic function is some potential flow. The main message of the 1 October lecture was that one ordinary derivative replaces two sets of partial derivatives.

| Flow | $\Phi(z)$ |
|---|---|
| uniform, angle $\alpha$ | $Ue^{-i\alpha}z$ |
| source $m$ at $z_0$ | $\frac{m}{2\pi}\ln(z-z_0)$ |
| vortex, counter-clockwise $\Gamma$ | $-\frac{i\Gamma}{2\pi}\ln z$ |
| doublet, source upstream | $\frac{\mu}{2\pi z}$ |
| cylinder | $U(z+R^2/z)$ |
| wedge/corner | $-kz^{m+1}$ |

The slide tables mix vortex sign conventions, so state yours when you use one.

## Related

- Full derivations: [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#3. Complex numbers and the complex velocity potential]]
- [[Streamfunction and Velocity Potential]] · [[General Doublet]] · [[Conformal Mapping]] · [[Elementary Potential Flows]]
