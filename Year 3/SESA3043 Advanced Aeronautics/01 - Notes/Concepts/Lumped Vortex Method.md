---
title: "Lumped Vortex Method"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["LV method", "lumped vortex", "LVM"]
tags: [sesa3043, concept, potential-flow, lumped-vortex]
status: complete
parent_lectures: ["[[SESA3043 2.2 - Lumped Vortex Method]]"]
related_concepts: ["[[Method of Images]]", "[[Kutta-Joukowski Theorem]]", "[[Panel Method]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf", "02 - Sources/Lectures/Ch2_Notes_LVM_Tandem Aerofoils.pdf"]
---

# Lumped Vortex Method

## Definition

> [!note] Definition
> Model each thin lifting element by a point vortex $\Gamma$ at its $1/4$-chord and impose flow tangency at its $3/4$-chord control point. For one flat plate: $U_\infty\alpha=\dfrac{\Gamma}{2\pi(c/2)}$, so $\Gamma=\pi U_\infty\alpha c$ and $C_L=2\pi\alpha$.

## Procedure

1. Vortex at $\bar x=1/4$, control point at $\bar x=3/4$ of each element.
2. Downwash at every control point from every vortex (and images).
3. Tangency: upwash $U_\infty(\alpha-\mathrm dz_c/\mathrm dx)$ = total downwash.
4. Solve the linear system; $L_i=\rho U_\infty\Gamma_i$.

## Standard results

| Case | Result |
|---|---|
| tandem, gap $c/2$ | $\Gamma_1:\Gamma_2=2:1$, total unchanged |
| tandem, gap $\varepsilon c$ | $L_1/L_2=(2\varepsilon+3)/(2\varepsilon+1)$ |
| ground effect | $\Gamma/\Gamma_\infty=1+(4h/c)^{-2}$ |
| biplane, gap $c/2$ | each wing $\tfrac23\Gamma_\infty$ |
| parabolic camber $0.24\bar x(1-\bar x)$ | $C_L=2\pi(\alpha+0.12)$ for any $N$ |

## Limitations

2-D, no thickness, singular point loads (ill-conditioned with many vortices). Panel methods fix all three.

## Related

- [[SESA3043 2.2 - Lumped Vortex Method]] · [[Method of Images]] · [[SESA2022 T4 - Thin Aerofoil Theory]]
