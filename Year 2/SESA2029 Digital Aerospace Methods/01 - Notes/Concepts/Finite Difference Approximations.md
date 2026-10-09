---
title: "Finite Difference Approximations"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["finite differences", "forward difference", "backward difference", "central difference", "upwind difference"]
tags: [sesa2029, concept, numerical-methods]
status: complete
parent_lectures: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]", "[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]"]
related_concepts: ["[[Truncation Error and Order of Accuracy]]", "[[Taylor Table Method]]", "[[Convective Interpolation Schemes]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L3)", "02 - Sources/CFD/CFD.txt"]
---

# Finite Difference Approximations

## Definition

> [!note] Definition
> Approximations to derivatives built from function values at discrete grid points $x_j = jh$. They are obtained by truncating Taylor series:
> $$f'_j\approx\frac{f_{j+1}-f_j}{h}\ (\text{forward}),\quad\frac{f_j-f_{j-1}}{h}\ (\text{backward}),\quad\frac{f_{j+1}-f_{j-1}}{2h}\ (\text{central}),\qquad f''_j\approx\frac{f_{j-1}-2f_j+f_{j+1}}{h^2}$$

## Explanation

- **Direction relative to the flow.** With the flow going left to right, the *backward* difference looks **upwind**, the *forward* difference looks downwind, and the central difference looks both ways. Upwind differencing is what makes explicit convection schemes stable ([[Von Neumann Stability Analysis]]).
- **Accuracy.** Forward and backward are first order, $O(h)$. Central is second order, $O(h^2)$, because the $\pm\tfrac h2f''$ errors cancel. Wider stencils give higher order: one-sided second-order schemes use 3 points, e.g. $(f_{j-2}-4f_{j-1}+3f_j)/2h$.
- **Second derivative** = the difference of first differences taken at $j\pm\tfrac12$.
- **Non-uniform grids**: replace $h$ with local spacings. For example $f''_j\approx\left[\frac{f_{j+1}-f_j}{x_{j+1}-x_j}-\frac{f_j-f_{j-1}}{x_j-x_{j-1}}\right]\big/\tfrac12(x_{j+1}-x_{j-1})$.
- Time derivatives use the same formulas with $\Delta t$: forward is explicit Euler, backward is implicit Euler, and 3-point backward is BDF2.

## Examples

- $d/dx[\sin2\pi x]$: the RMS error halves per doubling of $N$ for the forward scheme and quarters for the central scheme.

![[dam_fd_convergence.png|520]]

- The steady heat equation $T''=0$ discretised with the central second difference gives $T_{j-1}-2T_j+T_{j+1}=0$ ([[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]).

## Related

- Parent lectures: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] · [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]
- Related concepts: [[Truncation Error and Order of Accuracy]] · [[Taylor Table Method]] · [[Convective Interpolation Schemes]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L3)
- 02 - Sources/CFD/CFD.txt
