---
title: "Pohlhausen Method"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["Pohlhausen solution", "Pohlhausen equation", "Pohlhausen profile", "Pohlhausen quartic", "Karman-Pohlhausen method", "pressure-gradient parameter lambda", "dimensionless pressure gradient parameter", "Pohlhausen parameter", "BL equation at the wall", "compatibility condition"]
tags: [sesa3043, concept, boundary-layer, separation]
status: complete
parent_lectures: ["[[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]"]
related_concepts: ["[[Momentum Integral Equation]]", "[[Boundary Layer Separation]]", "[[Blasius and Falkner-Skan Similarity Solutions]]"]
sources: ["02 - Sources/Lectures/CH3-3 Pohlhausen.pdf", "02 - Sources/Lectures/Ch3_Notes_Pohlhausen.pdf"]
---

# Pohlhausen Method

The Pohlhausen method assumes a quartic velocity profile in $\eta=y/\delta$ and fixes its coefficients with no slip at the wall, the matched edge velocity, zero slope and curvature at the edge, and the boundary-layer momentum equation applied at the wall. The result is

$$\frac{u}{U_e}=\underbrace{2\eta-2\eta^3+\eta^4}_{F(\eta)}+\lambda\underbrace{\tfrac16\eta(1-\eta)^3}_{G(\eta)},\qquad\lambda=\frac{\delta^2}{\nu}\frac{\mathrm dU_e}{\mathrm dx}.$$

The shape parameter $\lambda=Re_\delta\frac{\delta}{U_e}U_e'$ measures pressure force against viscous force: positive is favourable, negative adverse. From the profile,

$$\frac{\delta^*}{\delta}=\frac{3}{10}-\frac{\lambda}{120},\qquad\frac{\theta}{\delta}=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072},\qquad\frac{\tau_w\delta}{\mu U_e}=2+\frac{\lambda}{6}.$$

The wall shear vanishes at $\lambda=-12$ (with $H=3.5$), which is the method's separation point. It is valid for $-12\le\lambda\le12$; above 12 the profile overshoots $U_e$. On a flat plate, combined with the momentum integral equation, it gives $\theta/x=0.685/\sqrt{Re_x}$, against Blasius's 0.664.

The wall condition is the important one. At the wall $u=v=0$, so the momentum equation reduces to $\nu\,\partial^2u/\partial y^2|_0=-U_eU_e'$: the pressure gradient sets the curvature of the profile at the wall. In an adverse gradient that curvature is positive, so the profile must have an inflection point, which ties together separation ([[Boundary Layer Separation]]) and instability ([[Linear Stability and Transition Prediction]]).

## Related

- [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] (full derivation)
- [[Momentum Integral Equation]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Displacement and Momentum Thickness]]
