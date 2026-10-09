---
title: "Pohlhausen Method"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["Pohlhausen profile", "Pohlhausen quartic", "pressure-gradient parameter lambda", "Pohlhausen parameter"]
tags: [sesa3043, concept, boundary-layer, separation]
status: complete
parent_lectures: ["[[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]"]
related_concepts: ["[[Momentum Integral Equation]]", "[[Boundary Layer Separation]]", "[[Blasius and Falkner-Skan Similarity Solutions]]"]
sources: ["02 - Sources/Lectures/CH3-3 Pohlhausen.pdf", "02 - Sources/Lectures/Ch3_Notes_Pohlhausen.pdf"]
---

# Pohlhausen Method

## Statement

> [!note] Definition
> Assume a quartic profile in $\eta=y/\delta$ and fix its coefficients with no slip, matched edge velocity, zero slope and curvature at the edge, and the BL momentum equation at the wall. Result:
> $$\frac{u}{U_e}=\underbrace{2\eta-2\eta^3+\eta^4}_{F(\eta)}+\lambda\underbrace{\tfrac16\eta(1-\eta)^3}_{G(\eta)},\qquad\lambda=\frac{\delta^2}{\nu}\frac{\mathrm dU_e}{\mathrm dx}.$$

## Key results

- $\delta^*/\delta=\frac{3}{10}-\frac{\lambda}{120}$, $\theta/\delta=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072}$, $\tau_w\delta/\mu U_e=2+\lambda/6$.
- **Separation at $\lambda=-12$** ($\tau_w=0$, $H=3.5$); valid for $-12\le\lambda\le12$ (overshoot above 12).
- $\lambda>0$ favourable, $\lambda<0$ adverse. $\lambda=Re_\delta\frac{\delta}{U_e}U_e'$: pressure force over viscous force.
- With the flat-plate MIE: $\theta/x=0.685/\sqrt{Re_x}$ (Blasius 0.664).

## Why the wall condition matters

At the wall $u=v=0$, so $\nu\,\partial^2u/\partial y^2|_0=-U_eU_e'$: the pressure gradient fixes the profile's curvature at the wall. In an adverse gradient that curvature is positive, so the profile has an inflection point, which links separation ([[Boundary Layer Separation]]) and instability ([[Linear Stability and Transition Prediction]]).

## Related

- [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] (full derivation)
- [[Momentum Integral Equation]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Displacement and Momentum Thickness]]
