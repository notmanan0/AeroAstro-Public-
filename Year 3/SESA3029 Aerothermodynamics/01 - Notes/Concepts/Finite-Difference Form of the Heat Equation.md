---
title: "Finite-Difference Form of the Heat Equation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["finite difference form", "finite-difference heat conduction", "nodal energy balance", "finite difference stencil", "FTCS heat equation"]
tags: [sesa3029, concept, heat-transfer, conduction, numerical-methods]
status: complete
parent_lectures: ["[[SESA3029 W09e - Numerical Methods in Conduction]]"]
related_concepts: ["[[Thermal Diffusivity]]", "[[Finite Difference Approximations]]", "[[Truncation Error and Order of Accuracy]]", "[[Explicit and Implicit Time Integration]]", "[[CFL and Fourier Numbers]]"]
sources: ["02 - Sources/Lectures/Lecture5.7.pdf"]
---

# Finite-Difference Form of the Heat Equation

The finite-difference form of the heat equation replaces each derivative by differences between temperatures at the nodes of a mesh, turning the heat diffusion equation into one algebraic equation per node.

On a uniform 1-D mesh the second derivative is the change of slope between the half points either side of node $i$:

$$
\left.\frac{\partial^2T}{\partial x^2}\right\vert_i\approx\frac{T_{i+1}-2T_i+T_{i-1}}{\Delta x^2}+\mathcal O(\Delta x^2).
$$

For steady conduction without generation each interior node is the average of its neighbours: $T_i=(T_{i+1}+T_{i-1})/2$ in 1-D, $T_P=(T_E+T_W+T_N+T_S)/4$ on a square 2-D grid (plus $\dot g\Delta x^2/4k$ with generation).

For transient conduction, with Fourier number $\mathcal F=\alpha\Delta t/\Delta x^2$:

- **explicit:** $T_i^{n+1}=T_i^n+\mathcal F(T_{i+1}^n-2T_i^n+T_{i-1}^n)$, one node at a time, stable for $\mathcal F\le\tfrac12$ (1-D interior, uniform grid, constant $\alpha$);
- **implicit:** $T_{i+1}^{n+1}-(2+1/\mathcal F)T_i^{n+1}+T_{i-1}^{n+1}=-T_i^n/\mathcal F$, a tridiagonal system each step, stable for any $\mathcal F$.

Both have truncation error $\mathcal O(\Delta t,\Delta x^2)$.

At boundaries and corners the node equation comes from an energy balance on the node's control volume, half a cell in every direction inside the solid: conduction $k\times(\text{face length})\times(T_{nb}-T_P)/\Delta x$ from each neighbour, plus convection, flux and generation, summing to zero (steady) or to the storage rate (transient). A plane surface with convection gives $T_P=(2T_W+T_N+T_S+2\mathrm{Bi}\,T_\infty)/(4+2\mathrm{Bi})$ with $\mathrm{Bi}=h\Delta x/k$, and an explicit 1-D convective end node needs $\mathcal F(1+\mathrm{Bi})\le\tfrac12$.

## Related

- Parent lecture: [[SESA3029 W09e - Numerical Methods in Conduction]]
- Related concepts: [[Thermal Diffusivity]] · [[Heat Equation]] · [[Finite Difference Approximations]] · [[Truncation Error and Order of Accuracy]] · [[Explicit and Implicit Time Integration]] · [[CFL and Fourier Numbers]]
- Earlier: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] · [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]

## Sources

- L5.7 slides 10–17.
