---
title: "Linear Stability and Transition Prediction"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 3: Methods for Boundary Layers"
aliases: ["Orr-Sommerfeld equation", "e^n method", "en method", "e^N method", "thumb plot", "Tollmien-Schlichting waves", "TS waves", "neutral stability curve", "neutral curve", "stability diagram", "instability diagram", "n factor", "N-factor", "amplification factor", "critical Reynolds number", "roadmap to transition", "transition prediction"]
tags: [sesa3043, concept, transition, stability]
status: complete
parent_lectures: ["[[SESA3043 3.4 - Transition to Turbulence]]"]
related_concepts: ["[[Pohlhausen Method]]", "[[Boundary Layer Separation]]", "[[Viscous-Inviscid Interaction]]", "[[Von Neumann Stability Analysis]]"]
sources: ["02 - Sources/Lectures/CH3-4 Transition to Turbulence(1).pdf"]
---

# Linear Stability and Transition Prediction

Linear stability theory asks whether a small disturbance to a laminar boundary layer grows. Perturb a parallel flow $\bar u(y)$ with a small wave $v'=\hat v(y)e^{i(\alpha x-\omega t)}$ and linearise Navier–Stokes; the amplitude then obeys the **Orr–Sommerfeld equation**

$$(\bar u-c_{ph})(\hat v''-\alpha^2\hat v)-\bar u''\hat v=-\frac{i\nu}{\alpha}\left(\hat v''''-2\alpha^2\hat v''+\alpha^4\hat v\right),\qquad c_{ph}=\frac\omega\alpha.$$

Taking $\omega$ real and $\alpha=\alpha_r+i\alpha_i$, the wave grows downstream wherever $\alpha_i<0$.

The $\alpha_i=0$ contour, plotted against $\log Re_{\delta^*}$ and the frequency parameter $F=\omega\nu/U_e^2$, is the thumb-shaped neutral curve. It encloses the unstable region, and its tip is the critical Reynolds number, $Re_{\delta^*}\approx520$ for Blasius. Following one frequency downstream, its amplification is $n=\ln(A/A_0)=-\int_{x_0}^x\alpha_i\,\mathrm dx$. The $e^n$ method then predicts transition where the envelope of $n$ over all frequencies reaches $n_{crit}\approx9$ ($A/A_0\approx8100$), with a lower $n_{crit}$ in noisier flows.

The method ignores receptivity and the nonlinear stages, handles non-parallel effects only partly, and can't predict bypass transition.

Pressure gradient has a strong effect. An adverse gradient enlarges the unstable region, lowers $Re_{crit}$ and puts an inflection point in the profile. That allows inviscid (Rayleigh) instability, which stability calculations confirm for typical adverse-gradient profiles and which persists as $Re\to\infty$ (slide 46). An inflection point is necessary but not sufficient, so the instability is a computed result rather than automatic. A favourable gradient is stabilising, which is what natural-laminar-flow aerofoils exploit.

## Related

- [[SESA3043 3.4 - Transition to Turbulence]] (derivation and roadmap)
- [[Pohlhausen Method]] (inflectional APG profiles) · [[Viscous-Inviscid Interaction]] (XFOIL's "Ncrit") · [[Von Neumann Stability Analysis]] (the same normal-mode idea)
