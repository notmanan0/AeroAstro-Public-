---
title: "Lumped Vortex Method"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["LV method", "lumped vortex", "LVM", "lumped-vortex element", "discrete vortex method", "N-LV method", "mirror image method", "method of images", "loading point", "three-quarter-chord point"]
tags: [sesa3043, concept, potential-flow, lumped-vortex]
status: complete
parent_lectures: ["[[SESA3043 2.2 - Lumped Vortex Method]]"]
related_concepts: ["[[Method of Images]]", "[[Kutta-Joukowski Theorem]]", "[[Panel Method]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf", "02 - Sources/Lectures/Ch2_Notes_LVM_Tandem Aerofoils.pdf"]
---

# Lumped Vortex Method

The lumped vortex method models each thin lifting element as a single point vortex $\Gamma$ at its quarter-chord **loading point** $x_L$, and imposes flow tangency at its three-quarter-chord **control point** $x_T$ (the slides' terms). For one flat plate, tangency at the control point gives $U_\infty\alpha=\Gamma/[2\pi(c/2)]$, so $\Gamma=\pi U_\infty\alpha c$ and $C_L=2\pi\alpha$, the thin-aerofoil result.

With several elements, put a vortex at $\bar x=1/4$ and a control point at $\bar x=3/4$ on each, work out the downwash at every control point from every vortex (and any images), set the required upwash $U_\infty(\alpha-\mathrm dz_c/\mathrm dx)$ equal to the total downwash, and solve the linear system; each element's lift is $L_i=\rho U_\infty\Gamma_i$. Write every induced velocity as a downwash and enter an upward one as a negative downwash, to keep the signs straight.

| Case | Result |
|---|---|
| tandem, gap $c/2$ | $\Gamma_1:\Gamma_2=2:1$, total unchanged |
| tandem, gap $\varepsilon c$ | $L_1/L_2=(2\varepsilon+3)/(2\varepsilon+1)$ |
| ground effect | $\Gamma/\Gamma_\infty=1+(4h/c)^{-2}$ |
| biplane, gap $c/2$ | each wing $\tfrac23\Gamma_\infty$ |
| parabolic camber $0.24\bar x(1-\bar x)$ | $C_L=2\pi(\alpha+0.12)$ for any $N$ |

Friday 9 October covered the flat plate, the procedure and the tandem "Red Arrows" example, where with a gap of $c/2$ the front aircraft carries twice the lift of the rear one.

The method is two-dimensional, can represent camber but never thickness (it rests on thin-aerofoil theory), and its point loads are singular, which makes the system ill-conditioned with many vortices. Panel methods fix all three.

## Related

- [[SESA3043 2.2 - Lumped Vortex Method]] · [[Method of Images|Mirror image method]] · [[SESA2022 T4 - Thin Aerofoil Theory]]
