---
title: "Linear Stability and Transition Prediction"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["Orr-Sommerfeld equation", "e^n method", "en method", "thumb plot", "Tollmien-Schlichting waves", "TS waves", "neutral stability curve", "transition prediction"]
tags: [sesa3043, concept, transition, stability]
status: complete
parent_lectures: ["[[SESA3043 3.4 - Transition to Turbulence]]"]
related_concepts: ["[[Pohlhausen Method]]", "[[Boundary Layer Separation]]", "[[Viscous-Inviscid Interaction]]", "[[Von Neumann Stability Analysis]]"]
sources: ["02 - Sources/Lectures/CH3-4 Transition to Turbulence(1).pdf"]
---

# Linear Stability and Transition Prediction

## Statement

> [!note] Definition
> Perturb a parallel laminar flow $\bar u(y)$ with a small wave $v'=\hat v(y)e^{i(\alpha x-\omega t)}$ and linearise Navier–Stokes. The amplitude obeys the **Orr–Sommerfeld equation**
> $$(\bar u-c_{ph})(\hat v''-\alpha^2\hat v)-\bar u''\hat v=-\frac{i\nu}{\alpha}\left(\hat v''''-2\alpha^2\hat v''+\alpha^4\hat v\right),\qquad c_{ph}=\frac\omega\alpha.$$
> With real $\omega$ and $\alpha=\alpha_r+i\alpha_i$, the wave grows downstream where $\alpha_i<0$.

## The chain of ideas

1. **Thumb plot:** the $\alpha_i=0$ contour in $(\log Re_{\delta^*},\,F=\omega\nu/U_e^2)$ encloses the unstable region; its tip is $Re_{crit}$ (Blasius: $Re_{\delta^*}\approx520$).
2. **Amplification:** $n=\ln(A/A_0)=-\int_{x_0}^x\alpha_i\,\mathrm dx$ for each frequency.
3. **$e^n$ method:** transition where the envelope of $n$ over all frequencies reaches $n_{crit}\approx9$ ($A/A_0\approx8100$); lower $n_{crit}$ in noisy flow.
4. **Limitations:** ignores receptivity and nonlinear stages; partial non-parallel effects; cannot predict bypass transition.

## Pressure gradients

Adverse: larger unstable region, lower $Re_{crit}$, and inflectional (Rayleigh) instability that persists as $Re\to\infty$. Favourable: stabilising, the basis of natural-laminar-flow aerofoils.

## Related

- [[SESA3043 3.4 - Transition to Turbulence]] (derivation and roadmap)
- [[Pohlhausen Method]] (inflectional APG profiles) · [[Viscous-Inviscid Interaction]] (XFOIL's "Ncrit") · [[Von Neumann Stability Analysis]] (the same normal-mode idea)
