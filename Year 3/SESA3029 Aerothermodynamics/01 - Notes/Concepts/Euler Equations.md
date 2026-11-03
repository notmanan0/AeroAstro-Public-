---
title: "Euler Equations"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["Euler equations", "compressible Euler equations", "inviscid flow equations", "vector of conservative variables", "conserved variables", "flux vectors", "conservation form"]
tags: [sesa3029, concept, euler-equations, cfd, governing-equations]
status: complete
parent_lectures: ["[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]"]
related_concepts: ["[[Compressible Navier-Stokes Conservation Form]]", "[[Conservation Form of the Governing Equations]]", "[[Navier-Stokes Equations]]", "[[Normal-Shock Jump Relations]]"]
sources: ["02 - Sources/Lectures/Lecture4-1.pdf", "02 - Sources/Lectures/Lecture4-1.txt"]
---

# Euler Equations

The Euler equations are the conservation laws of mass, momentum and energy for a compressible fluid with no viscosity and no heat conduction: the Navier–Stokes equations with the viscous terms taken out. In 2D Cartesian form, as derived in SESA3029 Lecture 4.1:

$$
\frac{\partial}{\partial t}\begin{bmatrix}\rho\\ \rho u\\ \rho v\\ \rho e_t\end{bmatrix}
+\frac{\partial}{\partial x}\begin{bmatrix}\rho u\\ \rho u^2+p\\ \rho uv\\ (\rho e_t+p)u\end{bmatrix}
+\frac{\partial}{\partial y}\begin{bmatrix}\rho v\\ \rho uv\\ \rho v^2+p\\ (\rho e_t+p)v\end{bmatrix}
=\vec 0,
\qquad e_t=c_vT+\tfrac12(u^2+v^2).
$$

The first column is the vector of "conservative" variables and the other two are the flux vectors (4.1 slide 12). Each row comes from the same balance on a small control volume: the rate of increase inside equals flux in minus flux out, plus the pressure force (momentum) or the pressure work (energy). Pressure enters the $x$-momentum flux in the $x$-derivative and the $y$-momentum flux in the $y$-derivative, because it pushes on the faces normal to each direction. The energy flux $(\rho e_t+p)u=\rho uh_t$ is the energy carried in plus the work done by pressure.

The set is closed by the perfect-gas law $p=\rho RT$. It is nonlinear and coupled, so apart from simple geometries there is no analytical solution, and CFD solves it on a grid. Because it is in conservation (flux) form, a numerical solution captures shocks: the flux balance across a discontinuity is exactly the [[Normal-Shock Jump Relations|normal-shock relations]]. Slide 12 of 4.1 prints the energy flux as $\rho u(e_t+p)$, a slip for $(\rho e_t+p)u$.

Adding viscous stresses and heat conduction gives the [[Compressible Navier-Stokes Conservation Form|compressible Navier–Stokes equations]] of SESA3043 1.2. Going the other way, linearising the steady Euler equations about a uniform stream gives the [[Linearised Compressible Potential Equation]] that Chapter 4's aerofoil theories are built on.

## Related

- [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#5. Vector form and what CFD does with it (4.1 slides 12–13)|W07a §§1–5]] (full derivation)
- [[Conservation Form of the Governing Equations]] · [[Navier-Stokes Equations]] · [[Finite Volume Method]] (SESA2029)
- [[Linearised Compressible Potential Equation]]
