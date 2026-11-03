---
title: "Linearised Compressible Potential Equation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["velocity potential equation", "compressible potential equation", "linearised potential equation", "small-perturbation potential equation", "linearised Euler equation", "small-disturbance equation", "linearised pressure coefficient", "Cp = -2u'/U"]
tags: [sesa3029, concept, potential-flow, linearisation, compressible-flow]
status: complete
parent_lectures: ["[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
related_concepts: ["[[Euler Equations]]", "[[Prandtl-Glauert Transformation]]", "[[Ackeret Theory]]", "[[Streamfunction and Velocity Potential]]", "[[Laplace's Equation]]"]
sources: ["02 - Sources/Lectures/Lecture4-3.pdf"]
---

# Linearised Compressible Potential Equation

For a thin body in a uniform stream, with small disturbances $u=U_\infty+u'$, $v=v'$ ($u',v'\ll U_\infty$), and isentropic, irrotational flow, the steady Euler equations reduce to one linear equation for the perturbation potential $\phi$ ($u'=\phi_x$, $v'=\phi_y$):

$$
(1-M_\infty^2)\frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial y^2}=0,
\qquad
C_p=-\frac{2u'}{U_\infty}.
$$

The derivation (4.3 slides 2–8) has four moves. Write the momentum equations in non-conservative form using mass conservation. Combine them as $u\times(x\text{-mom})+v\times(y\text{-mom})$ and use $\mathrm dp=a^2\,\mathrm d\rho$. Linearise, with the energy equation giving $a^2=a_\infty^2-(\gamma-1)u'U_\infty$. Then introduce the potential. The pressure coefficient follows from the isentropic $p/p_\infty=(a^2/a_\infty^2)^{\gamma/(\gamma-1)}$ and a binomial expansion; $M_\infty$ cancels.

The sign of $1-M_\infty^2$ sets the type. For $M_\infty<1$ the equation is elliptic and a stretch of $y$ turns it into Laplace's equation ([[Prandtl-Glauert Transformation]]). For $M_\infty>1$ it is hyperbolic, a wave equation whose solutions are constant along Mach lines ([[Ackeret Theory]]). It fails near $M_\infty=1$, where the kept term $(1-M_\infty^2)\phi_{xx}$ becomes as small as the dropped ones, and for hypersonic flow ($M_\infty>5$). The course gives the safe ranges as $M_\infty<0.8$ and $M_\infty>1.2$ (4.4 and 4.5 title slides).

## Related

- [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#4. The velocity potential equation (4.3 slides 6–7)|W07b §§1–5]] (full derivation)
- [[Euler Equations]] · [[Prandtl-Glauert Transformation]] · [[Ackeret Theory]]
- [[Streamfunction and Velocity Potential]] · [[Laplace's Equation]] (the $M_\infty\to0$ limit)
