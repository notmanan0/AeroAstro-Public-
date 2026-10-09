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
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture17_Parabolic1.pdf"]
---

# Heat Equation

## Definition

> [!note] Definition
> $$u_t=\kappa^2u_{xx}$$
> This is parabolic. Only $u(x,0)$ is needed as initial data.

## Explanation
**Derivations**:
- **Random walk**: $\kappa^2=\lim(\Delta x)^2/(4\Delta t)$.
- **Physical**: energy conservation plus Fourier's law.

**Separated solution**: $T_n=C_ne^{-\kappa^2k_n^2t}$. Every mode decays, and higher modes decay faster, so profiles smooth out over time.

**Steady states**:
- Dirichlet ends at zero: $u\to0$.
- Neumann (insulated) ends: $u\to$ the mean of the initial data, because no heat leaves the rod.
- With a source term or inhomogeneous BCs: $u$ tends to the solution of $\kappa^2u''=-F$ that satisfies the BCs.

**Numerics link**: when this equation is solved with explicit finite differences (SESA2029), stability requires the Fourier number to satisfy $r=\kappa^2\Delta t/\Delta x^2\leq\frac12$. See [[CFL and Fourier Numbers]].

## Examples
- $u_t=\frac14u_{xx}$ on $[0,\pi]$ with insulated ends and $u_0=7+5\cos2x$ gives $u=7+5e^{-t}\cos2x$ (PS7 Q1).
- The same equation with $u_0=\cos^3x$ gives $\frac34e^{-t/4}\cos x+\frac14e^{-9t/4}\cos3x$ (2023/24 exam).

![[m2048_pde_heat_dirichlet_vs_neumann.png|600]]

## Related
- [[Separation of Variables]] · [[Eigenfunction Expansion Method]] · [[Laplace's Equation]] (the steady-state limit)

**Related (SESA2028 materials):** [[Hardenability and Jominy Test]] (quench cooling rates vs section size) · [[Oxidation Rate Laws]] (diffusion-controlled parabolic growth)

## Sources
- Lectures 17–19; PS7
