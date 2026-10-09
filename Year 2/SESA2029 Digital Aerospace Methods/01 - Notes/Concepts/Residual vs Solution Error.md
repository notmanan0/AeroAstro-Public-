---
title: "Residual vs Solution Error"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["residual", "iteration error", "convergence monitoring", "residual plot"]
tags: [sesa2029, concept, numerical-methods, validation]
status: complete
parent_lectures: ["[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]", "[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
related_concepts: ["[[Jacobi, Gauss-Seidel and SOR Iteration]]", "[[Mesh Convergence and Grid Independence]]", "[[Verification and Validation]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L4, L12)", "02 - Sources/CFD/CFD.txt"]
---

# Residual vs Solution Error

## Definition

> [!note] Definition
> The **residual** measures how far the current iterate is from satisfying the **discrete** equations. For example
>
> $$R = \sqrt{\sum_j(T_{j-1}-2T_j+T_{j+1})^2}$$
>
> The **solution error** is the distance from the **exact** solution of the PDE. A zero residual means the *iteration* has converged. It says nothing about whether the *grid* is fine enough.

## Explanation

- **Solution error** = discretisation error (grid and time step) + iteration error (unconverged residual) (+ modelling error when compared with reality).
- A CFD solver's first output is the residual history of every equation. Ideally it falls by many orders of magnitude. Real cases often **plateau**, so you must decide when to stop.
- **Judge convergence on the outputs you need.** Monitor lift, drag, pitching moment or heat flux as the iterations proceed. A sensitive quantity, such as pitching moment, may need a lower residual than lift.
- **Converged residuals on a coarse grid can still give wrong answers.** Pair residual convergence with a grid study ([[Mesh Convergence and Grid Independence]]).
- If a case won't converge, look first at the grid, then drop temporarily to first order, then reduce the under-relaxation.

## Examples

- In the heat-equation spreadsheet, both the residual and the RMS error relative to $T = 1200-900x$ fell to about $10^{-5}$. The central scheme is exact for a linear solution, so here zero residual also means zero error.
- On a wing, lift can be converged and grid-independent while induced drag is still changing with grid size ([[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]).

## Related

- Parent lectures: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] · [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Related concepts: [[Jacobi, Gauss-Seidel and SOR Iteration]] · [[Mesh Convergence and Grid Independence]] · [[Verification and Validation]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L4, L12)
- 02 - Sources/CFD/CFD.txt
