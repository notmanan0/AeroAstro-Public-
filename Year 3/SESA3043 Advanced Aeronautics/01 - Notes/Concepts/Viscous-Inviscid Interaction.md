---
title: "Viscous-Inviscid Interaction"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["VII", "surface transpiration method", "STM", "surface displacement method", "SDM", "blowing velocity"]
tags: [sesa3043, concept, boundary-layer, panel-method]
status: complete
parent_lectures: ["[[SESA3043 3.6 - Viscous-Inviscid Interaction]]"]
related_concepts: ["[[Panel Method]]", "[[Momentum Integral Equation]]", "[[Displacement and Momentum Thickness]]", "[[Linear Stability and Transition Prediction]]"]
sources: ["02 - Sources/Lectures/CH3-6 Viscous Inviscid Interaction.pdf"]
---

# Viscous-Inviscid Interaction

## Statement

> [!note] Definition
> Iterate between an inviscid solver (panel method: $U_e(x)$, $C_L$) and a boundary-layer solver (MIE/Thwaites: $\delta^*(x)$, $C_D$) until $\delta^*$ converges, feeding the layer back to the inviscid flow either by
> - **SDM:** moving the panels out by $\delta^*$ (re-panelling), or
> - **STM:** blowing through the original panels at
> $$v_s=\frac{\mathrm d(U_e\delta^*)}{\mathrm dx}.$$

## Derivation of v_s

Mass balance on the strip between the wall and the displacement surface, from $x$ to $x+\Delta x$: $U_e\delta^*|_x+v_s\Delta x=U_e\delta^*|_{x+\Delta x}$; let $\Delta x\to0$.

## Notes

- STM avoids rebuilding the influence matrix, so it is what XFOIL uses (with transition by the $e^n$ method and separate laminar/turbulent closures).
- Example (revision 3.6 Q3): a $15\times15$ cm, 2 m test section at 15 m/s accelerates to 17.18 m/s at the exit because the four wall layers displace the core.

## Related

- [[SESA3043 3.6 - Viscous-Inviscid Interaction]] · [[Panel Method]] · [[Momentum Integral Equation]] · [[Displacement and Momentum Thickness]]
