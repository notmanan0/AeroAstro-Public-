---
title: "Jacobi, Gauss-Seidel and SOR Iteration"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["Jacobi method", "Gauss-Seidel", "successive over-relaxation", "SOR", "under-relaxation", "GMRES", "conjugate gradient"]
tags: [sesa2029, concept, numerical-methods, iterative-methods]
status: complete
parent_lectures: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]", "[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]"]
related_concepts: ["[[Residual vs Solution Error]]", "[[Pressure-Velocity Coupling and SIMPLE]]", "[[Direct Substitution and Newton-Raphson]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L4–L5, L11)", "02 - Sources/CFD/CFD.txt"]
---

# Jacobi, Gauss-Seidel and SOR Iteration

## Definition

> [!note] Definition
> Iterative methods for large sparse linear systems. Each unknown is updated from its discrete equation:
> $$\text{Jacobi: }T_j^{n+1} = \tfrac12(T_{j-1}^n+T_{j+1}^n),\qquad\text{Gauss–Seidel: }T_j^{n+1} = \tfrac12(T_{j-1}^{n+1}+T_{j+1}^n),\qquad\text{SOR: }T_j^{n+1} = (1-\omega)T_j^n+\omega\tilde T_j^{n+1}$$

## Explanation

- **Why iterate?** Direct Gaussian elimination costs about $n^3$ operations and a lot of memory. With $10^5$–$10^8$ unknowns in 3D CFD it is impossible, so solvers iterate from a guess.
- **Jacobi** uses only old values and needs two stored arrays. It is simple, still used as a multigrid smoother, and slow.
- **Gauss–Seidel** uses the freshest values: in a loop over increasing $j$, $T_{j-1}$ is already updated. It needs one array and roughly halves the iteration count.
- **SOR** blends the old value with the Gauss–Seidel provisional value $\tilde T$:
  - $\omega>1$ over-relaxes: bigger steps when convergence is smooth;
  - $0<\omega<1$ **under-relaxes**: damping when the iterates oscillate. This is the "under-relaxation factor" of pressure-based CFD solvers, $\phi_{new} = \phi_{old}+\alpha\Delta\phi$.
- **Krylov methods**: conjugate gradient (symmetric systems), BiCGSTAB and **GMRES** (general, robust). They search several directions cleverly, like descending a mountain diagonally, and live inside commercial solvers as library routines.
- **In 2D/3D**, Jacobi for Laplace's equation averages the 4 (or 6) neighbours.

## Examples

- 1D steady heat equation, $N = 8$: reaching $R<10^{-5}$ took 215 iterations (Jacobi), 105 (Gauss–Seidel), 35 (SOR, $\omega = 1.4$) and 26 (SOR, $\omega = 1.5$).

![[dam_heat_iterative_residuals.png|520]]

## Related

- Parent lectures: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] · [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Related concepts: [[Residual vs Solution Error]] · [[Pressure-Velocity Coupling and SIMPLE]] · [[Direct Substitution and Newton-Raphson]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L4–L5, L11)
- 02 - Sources/CFD/CFD.txt
