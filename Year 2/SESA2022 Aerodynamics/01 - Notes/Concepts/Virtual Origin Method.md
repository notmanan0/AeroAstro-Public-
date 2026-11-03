---
title: "Virtual Origin Method"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["virtual origin", "transition matching", "method of virtual origin"]
tags: [sesa2022, concept, boundary-layers, transition]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf", "02 - Sources/Lectures/SESA2022 Lecture 5.txt … Lecture 10.txt (2025-26 transcripts)"]
---

# Virtual Origin Method

When a boundary layer transitions at $x_T$, the turbulent correlations, which are written for a layer starting at the leading edge, are applied from a fictitious **virtual origin** $x_0<x_T$, chosen so that the momentum thickness is continuous at transition: $\theta_{lam}(x_T) = \theta_{turb}(x_T-x_0)$.

Momentum thickness can't jump because it is proportional to the drag accumulated so far, whereas $\delta$ and $\delta^*$ do jump at transition as $H$ drops from about 2.6 to 1.3. The laminar layer is thin, so the turbulent layer behaves as if it had started some way downstream of the leading edge, $x_0>0$.

With typical correlations the method runs as follows. Find $x_T = Re_{tr}\nu/U_\infty$ and $\theta_T = 0.664x_T/\sqrt{Re_{x_T}}$. Solve $0.036$ (or $0.037$) $\times(x_T-x_0)\left(U_\infty(x_T-x_0)/\nu\right)^{-1/5} = \theta_T$ for $x_T-x_0$; some papers give the closed form $x_0 = x_T(1-38.22Re_{x_T}^{-3/8})$ for the 0.036 correlation. Downstream, $\theta(x) = 0.036(x-x_0)Re_{x-x_0}^{-1/5}$, and the drag on one side is $D' = \rho U_\infty^2\theta(L)$, so $C_D = 2\theta(L)/L$ per side. The reverse problem, given a measured $\theta$ at $x$, inverts the downstream formula for $x_0$ and then solves for $x_T$.

![[bl_virtual_origin.png|520]]

Past-paper uses: aerofoil drag with mid-chord transition ([[SESA2022 Exam 2018-19 Solutions]], [[SESA2022 Exam 2019-20 Solutions]] Q4(ii)); $x_0$ and $x_T$ from a measured profile ([[SESA2022 Exam 2021-22 Solutions]] Part C Q1); the measurement location on an untripped plate ([[SESA2022 Exam 2022-23 Solutions]] Q1(v)); near-laminar plus turbulent plate drag ([[SESA2022 Exam 2024-25 Solutions]] Q1(c)); UAV wing skin friction ([[SESA2022 Exam 2020-21 Solutions]] Part B Q4).

## Related

- Full derivation and worked examples: [[SESA2022 T2 - Boundary Layers#7. Transition and the virtual origin method|T2 §7]]
- [[Displacement and Momentum Thickness]] · [[Momentum Integral Equation]]
