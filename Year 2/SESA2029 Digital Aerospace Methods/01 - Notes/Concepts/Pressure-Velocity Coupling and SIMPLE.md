---
title: "Pressure-Velocity Coupling and SIMPLE"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["SIMPLE", "SIMPLEC", "PISO", "pressure-based solver", "segregated solver", "coupled solver", "pressure Poisson equation"]
tags: [sesa2029, concept, solvers]
status: complete
parent_lectures: ["[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]"]
related_concepts: ["[[Navier-Stokes Equations]]", "[[Jacobi, Gauss-Seidel and SOR Iteration]]", "[[Residual vs Solution Error]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L11)", "02 - Sources/CFD/CFD.txt"]
---

# Pressure-Velocity Coupling and SIMPLE

## Definition

> [!note] Definition
> In incompressible flow the continuity equation is a **constraint** ($\nabla\cdot\mathbf u = 0$), not an evolution equation for density. Taking the divergence of the (implicit) momentum equation gives an elliptic **pressure Poisson equation**. Pressure-based algorithms such as **SIMPLE** iterate between momentum and pressure until both are satisfied.

## Explanation

**The SIMPLE loop**:
1. Start from a divergence-free $u^n$.
2. Solve momentum for intermediate velocities $u^*$ with the current pressure.
3. Solve the pressure (correction) equation.
4. Correct the velocities and mass fluxes.
5. Repeat until converged.

- **Family**: SIMPLE (needs under-relaxation, e.g. pressure 0.3, momentum 0.7), SIMPLEC (consistent; larger factors) and PISO (extra correctors; transients; no under-relaxation needed).
- **Segregated** solvers do $u$, $v$, $w$, then $p$, then the scalars in sequence. They are memory-light, but convergence is slow.
- **Coupled** solvers do momentum + pressure together. They converge in fewer iterations but need about 4× the memory. Choosing between them is problem-dependent.
- **Pressure-based vs density-based**: pressure-based is the default for low-Mach flow and now reaches transonic flow. Density-based (with dual time-stepping and RK) is still preferred for hypersonic flow.

## Examples

- If residuals oscillate in a steady SIMPLE run, lower the pressure and momentum under-relaxation factors. That is the SOR idea with $\omega<1$.

## Related

- Parent lectures: [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Related concepts: [[Navier-Stokes Equations]] · [[Jacobi, Gauss-Seidel and SOR Iteration]] · [[Residual vs Solution Error]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L11)
- 02 - Sources/CFD/CFD.txt
