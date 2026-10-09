---
title: "Von Neumann Stability Analysis"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["von Neumann analysis", "Fourier stability analysis", "amplification factor", "gain function"]
tags: [sesa2029, concept, numerical-methods, stability]
status: complete
parent_lectures: ["[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]"]
related_concepts: ["[[CFL and Fourier Numbers]]", "[[Explicit and Implicit Time Integration]]", "[[Finite Difference Approximations]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L6)", "02 - Sources/CFD/CFD.txt"]
---

# Von Neumann Stability Analysis

## Definition

> [!note] Definition
> A test for whether a linear discretised PDE amplifies errors. Substitute a single Fourier mode $f_j^n = G^ne^{ikx_j}$, so that $f_{j\pm1} = f_je^{\pm ikh}$, and find the **amplification factor** $G(kh) = f_j^{n+1}/f_j^n$. The scheme is stable if $|G|\le1$ for all $kh\in[0,\pi]$.

## Explanation

**Procedure**:
1. Write the scheme's update.
2. Replace the neighbours using $e^{\pm ikh}$ and use $e^{ikh}+e^{-ikh} = 2\cos kh$.
3. Factor out $f_j^n$ to get $G$.
4. Find the worst $kh$, usually $\pi$: the 2-point-per-wavelength saw-tooth, the shortest wave the grid can hold.
5. Set $|G| = 1$ to get the limit.

**Results**:
- **Heat equation, FTCS**: $G = 1-2F(1-\cos kh)$. At $kh = \pi$, $G = 1-4F$, so the scheme needs $F = \alpha\Delta t/h^2\le\tfrac12$.
- **Convection, explicit upwind**: $G = 1-C(1-e^{-ikh})$. At $kh = \pi$, $|G| = |1-2C|$, so it needs $C = c\Delta t/h\le1$.
- **Explicit central differencing of pure convection** (and explicit downwind) is unconditionally unstable.
- **ODE version** ($f' = \lambda f$): explicit Euler has $G = |1+\lambda\Delta t|$, a stable disc centred at $-1$. Implicit Euler has $G = 1/|1-\lambda\Delta t|$, stable outside a disc centred at $+1$.

## Examples

![[dam_von_neumann_gain.png|680]]

- Python experiments confirmed the theory: $F = 0.448$ was stable and $F = 0.576$ blew up as $1.30^n$ ([[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]).

## Related

- Parent lectures: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Related concepts: [[CFL and Fourier Numbers]] · [[Explicit and Implicit Time Integration]] · [[Finite Difference Approximations]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L6)
- 02 - Sources/CFD/CFD.txt
