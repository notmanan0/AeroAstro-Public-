---
title: "Heat Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Diffusion equation", "Heat conduction", "Insulated rod"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE3 - The Heat Equation]]", "[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
related_concepts: ["[[Separation of Variables]]", "[[Eigenfunction Expansion Method]]", "[[CFL and Fourier Numbers]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture17_Parabolic1.pdf", "02 - Sources/Lectures/MATH2048 Lecture 17.txt"]
---

# Heat Equation

The **heat equation** $y_t=\kappa^2y_{xx}$, also called the diffusion equation, is the prototype parabolic PDE: one time derivative balanced against two space derivatives.

Lecture 17 derived it from a random walk. Particles on a grid stay put with probability $\frac12$ and step left or right with probability $\frac14$ each; Taylor-expanding the exact update and letting $\Delta x,\Delta t\to0$ with $\Delta x^2/\Delta t$ fixed gives the equation with $\kappa^2=\Delta x^2/(4\Delta t)$. That limit is the signature of diffusion: spreading over a distance $\ell$ takes a time of order $\ell^2/\kappa^2$.

Separation of variables gives the same spatial eigenfunctions as the wave equation, but each mode decays as $e^{-(n\pi\kappa/L)^2t}$, faster for higher $n$, so sharp features vanish first and the solution smooths out. Only the initial temperature can be given. With fixed-temperature ends the rod relaxes to the straight line joining the end values; with insulated ends no heat escapes, the constant mode survives, and the rod settles to the mean of its initial temperature. For $y(x,0)=x(1-x)$ on $[0,1]$ with insulated ends, $y=\frac16-\sum\frac{2(1+(-1)^n)}{(n\pi)^2}\cos n\pi x\,e^{-(n\pi\kappa)^2t}$.

![[m2048_pde_heat_dirichlet_vs_neumann.png|600]]

## Related

- [[MATH2048 PDE3 - The Heat Equation]] · [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]
- [[Separation of Variables]] · [[Eigenfunction Expansion Method]] · [[PDE Classification]]
