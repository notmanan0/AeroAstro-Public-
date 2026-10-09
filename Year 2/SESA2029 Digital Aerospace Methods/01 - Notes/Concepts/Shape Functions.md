---
title: "Shape Functions"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["interpolation functions", "shape function matrix", "[N] matrix", "Hermite shape functions", "B matrix"]
tags: [sesa2029, concept, fea, shape-functions]
status: complete
parent_lectures: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]", "[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
related_concepts: ["[[Rayleigh-Ritz Method]]", "[[h- and p-Refinement]]", "[[Euler-Bernoulli Beam Element]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf", "02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Shape Functions

## Definition

> [!note] Definition
> Interpolation functions $N_i(x)$ that express the displacement anywhere in an element in terms of its nodal DOF:
>
> $$u = [N]\{d\} = \sum_iN_iu_i$$
>
> Each $N_i$ equals 1 at its own node (or DOF) and 0 at all the others.

## Explanation

- **Linear 2-node bar**: $N_1 = 1-x/L$, $N_2 = x/L$. The strain is constant in the element.
- **Quadratic 3-node bar** (origin at the mid-node): $N_1 = \tfrac{2x^2}{L^2}-\tfrac xL$, $N_2 = 1-\tfrac{4x^2}{L^2}$, $N_3 = \tfrac{2x^2}{L^2}+\tfrac xL$. The strain varies linearly.
- **Hermite beam** ($\xi = x/L$): $N_1 = 1-3\xi^2+2\xi^3$, $N_2 = L(\xi-2\xi^2+\xi^3)$, $N_3 = 3\xi^2-2\xi^3$, $N_4 = L(-\xi^2+\xi^3)$.
- **Properties**: Kronecker delta at the nodes; partition of unity ($\sum N_i = 1$ for translations), so rigid-body motion is exact; continuity across element boundaries (compatibility).
- **Strain–displacement**: $\{\varepsilon\} = [B]\{d\}$ with $[B]$ = derivatives of $[N]$ ($d/dx$ for bars, $d^2/dx^2$ for beam curvature). Then $[K] = \int[B]^T[D][B]\,dV$.
- **Derivation**:
  1. Assume a polynomial with as many coefficients as DOF.
  2. Impose the generalised BCs at the nodes.
  3. Solve for the coefficients.
  4. Collect the terms multiplying each nodal DOF.
- Linear vs quadratic elements in a code differ **only** in their shape functions.

## Examples

![[dam_bar_shape_functions.png|640]]

![[dam_beam_hermite_shape_functions.png|560]]

## Related

- Parent lectures: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]] · [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- Related concepts: [[Rayleigh-Ritz Method]] · [[h- and p-Refinement]] · [[Euler-Bernoulli Beam Element]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf
- 02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt
