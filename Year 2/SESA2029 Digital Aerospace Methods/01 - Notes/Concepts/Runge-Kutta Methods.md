---
title: "Runge-Kutta Methods"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["RK4", "RK2", "Runge-Kutta", "predictor-corrector", "RK45", "solve_ivp"]
tags: [sesa2029, concept, numerical-methods, time-integration]
status: complete
parent_lectures: ["[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]"]
related_concepts: ["[[Explicit and Implicit Time Integration]]", "[[Truncation Error and Order of Accuracy]]", "[[Shooting Method and the Blasius Solution]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L7)", "02 - Sources/CFD/CFD.txt"]
---

# Runge-Kutta Methods

## Definition

> [!note] Definition
> Multi-stage explicit schemes for $df/dt = R(t,f)$. They combine several right-hand-side evaluations within a step so that, for $R = \lambda f$, the update reproduces the Taylor series of $e^{\lambda\Delta t}$ exactly up to order $n$, with no extra terms.

## Explanation

- **RK2 (midpoint predictor–corrector)**: $\tilde f = f^n+\tfrac12\Delta tR(f^n)$, then $f^{n+1} = f^n+\Delta tR(\tilde f)$. This gives $G = 1+z+z^2/2$ with $z = \lambda\Delta t$.
- **Classical RK4**: four stages ($f^*$, $f^{**}$ at $t^{n+1/2}$ and $f^{***}$ at $t^{n+1}$), combined with weights $\tfrac16,\tfrac26,\tfrac26,\tfrac16$. This gives $G = 1+z+\tfrac{z^2}{2}+\tfrac{z^3}{6}+\tfrac{z^4}{24}$, i.e. **fourth order**. It is the go-to ODE solver (MATLAB, SciPy) and is used in unsteady density-based CFD.
- **Stability**: the regions grow with order. Real-axis limits are −2 (RK1/RK2), −2.51 (RK3) and −2.79 (RK4). RK3 and RK4 include part of the imaginary axis ($|\omega\Delta t|\le\sqrt3$ and $2\sqrt2$), so they propagate waves without artificial dissipation.
- **Storage**: RK4 needs about 5 arrays, while low-storage RK3 variants need only 2.
- **Adaptive RK45** (SciPy `solve_ivp` default) embeds 4th- and 5th-order results. Their difference estimates the error, which controls the step size.

## Examples

![[dam_stability_regions.png|440]]

- Integrating the F-4C short-period mode $\lambda = -0.5+1.3i$ gives the slopes 1, 2 and 4 in [[Truncation Error and Order of Accuracy]].

## Related

- Parent lectures: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Related concepts: [[Explicit and Implicit Time Integration]] · [[Truncation Error and Order of Accuracy]] · [[Shooting Method and the Blasius Solution]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L7)
- 02 - Sources/CFD/CFD.txt
