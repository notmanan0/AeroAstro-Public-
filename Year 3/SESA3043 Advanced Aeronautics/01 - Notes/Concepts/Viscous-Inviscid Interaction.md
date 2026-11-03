---
title: "Viscous-Inviscid Interaction"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["VII", "surface transpiration method", "STM", "surface displacement method", "SDM", "blowing velocity", "blowing/suction velocity", "transpiration velocity", "displacement body", "apparent body", "effective body", "repanelling", "viscous-inviscid coupling", "interactive boundary-layer method"]
tags: [sesa3043, concept, boundary-layer, panel-method]
status: complete
parent_lectures: ["[[SESA3043 3.6 - Viscous-Inviscid Interaction]]"]
related_concepts: ["[[Panel Method]]", "[[Momentum Integral Equation]]", "[[Displacement and Momentum Thickness]]", "[[Linear Stability and Transition Prediction]]"]
sources: ["02 - Sources/Lectures/CH3-6 Viscous Inviscid Interaction.pdf"]
---

# Viscous-Inviscid Interaction

Viscous–inviscid interaction couples an inviscid solver, usually a panel method giving $U_e(x)$ and $C_L$, with a boundary-layer solver (the momentum integral equation or Thwaites) giving $\delta^*(x)$ and $C_D$. The two are iterated until $\delta^*$ stops changing. The layer is fed back to the inviscid flow in one of two ways: the surface displacement method (SDM) moves the panels out by $\delta^*$ and repanels, while the surface transpiration method (STM) keeps the original panels and blows through them at

$$v_s=\frac{\mathrm d(U_e\delta^*)}{\mathrm dx}.$$

That transpiration velocity comes from a mass balance on the strip between the wall and the displacement surface, from $x$ to $x+\Delta x$: $U_e\delta^*|_x+v_s\Delta x=U_e\delta^*|_{x+\Delta x}$, then $\Delta x\to0$.

STM avoids rebuilding the influence matrix each iteration, which is why XFOIL uses it (together with $e^n$ transition and separate laminar and turbulent closures). Revision question 3.6 Q3 shows the effect in a wind tunnel: in a $15\times15$ cm, 2 m long test section at 15 m/s, the boundary layers on the four walls displace the core enough to accelerate it to 17.18 m/s at the exit.

## Related

- [[SESA3043 3.6 - Viscous-Inviscid Interaction]] · [[Panel Method]] · [[Momentum Integral Equation]] · [[Displacement and Momentum Thickness]]
