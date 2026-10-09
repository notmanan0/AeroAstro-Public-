---
title: "Direct Substitution and Newton-Raphson"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["Newton-Raphson", "direct substitution", "tangent stiffness", "secant stiffness", "modified Newton-Raphson", "incremental loading"]
tags: [sesa2029, concept, fea, nonlinear, numerical-methods]
status: complete
parent_lectures: ["[[SESA2029 B9 - Nonlinear FE Analysis]]"]
related_concepts: ["[[Sources of Nonlinearity in FEA]]", "[[Jacobi, Gauss-Seidel and SOR Iteration]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Direct Substitution and Newton-Raphson

## Definition

> [!note] Definition
> Iterative solvers for $[K(\{d\})]\{d\} = \{F\}$:
> - **direct substitution** repeats $u_{i+1} = [k(u_i)]^{-1}P$ with the secant stiffness at the last iterate;
> - **Newton–Raphson** corrects with the **tangent** stiffness: $u_{i+1} = u_i-R(u_i)/K_T(u_i)$, with $R = k(u)u-P$ and $K_T = dR/du$.

## Explanation

- **Direct substitution**: start with the linear stiffness $k_0$. It is simple and needs no derivatives, but it converges **linearly**, is slow, and can fail for strong nonlinearity. Relaxation can help.
- **Newton–Raphson**: converges **quadratically** (correct digits roughly double each iteration), but needs a new tangent matrix and factorisation each iteration.
- **Modified NR**: keep an old tangent. Each iteration is cheaper; more iterations are needed.
- **Incremental methods**: apply the load in steps and converge each (substeps). This is essential for path-dependent (plastic) and strongly nonlinear problems.
- **Quasi-Newton** (e.g. inverse Broyden): approximate tangent updates.
- **In ANSYS**: `NLGEOM,ON`, `NSUBST`, `NROPT`, `CNVTOL`, line search; monitor the convergence plot.

## Examples

- Softening spring $k = 100-50u$ with $P = 40$ (exact $u = 0.552786$): direct substitution gives 0.400, 0.500, 0.533, 0.545, 0.550…, while NR gives 0.400, 0.5333, 0.552381, 0.5527862, 0.552786405.

![[dam_nonlinear_solvers.png|640]]

## Related

- Parent lectures: [[SESA2029 B9 - Nonlinear FE Analysis]]
- Related concepts: [[Sources of Nonlinearity in FEA]] · [[Jacobi, Gauss-Seidel and SOR Iteration]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt
