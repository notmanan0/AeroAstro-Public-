---
title: "Virtual Origin Method"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["virtual origin", "transition matching"]
tags: [sesa2022, concept, boundary-layers, transition]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf"]
---

# Virtual Origin Method

## Definition

> [!note] Definition
> When a boundary layer transitions at $x_T$, the turbulent correlations (written for a layer starting at the leading edge) are applied from a fictitious **virtual origin** $x_0<x_T$. $x_0$ is chosen so that the **momentum thickness is continuous** at transition:
>
> $$\theta_{lam}(x_T) = \theta_{turb}(x_T-x_0)$$

## Explanation
- Momentum can't jump, because $\theta$ is proportional to the accumulated drag. $\delta$ and $\delta^*$ *do* jump at transition, since $H$ drops from about 2.6 to 1.3.
- The laminar layer is thin, so the turbulent layer "pretends" to have started downstream of the LE: $x_0>0$.

**Recipe** (with typical correlations):
1. $x_T = Re_{tr}\nu/U_\infty$, then $\theta_T = 0.664x_T/\sqrt{Re_{x_T}}$.
2. Solve $0.036$ (or $0.037$) $\times(x_T-x_0)\left(\frac{U_\infty(x_T-x_0)}{\nu}\right)^{-1/5} = \theta_T$ for $x_T-x_0$. Some papers give the closed form $x_0 = x_T\left(1-38.22Re_{x_T}^{-3/8}\right)$ for the 0.036 correlation.
3. Downstream: $\theta(x) = 0.036(x-x_0)Re_{x-x_0}^{-1/5}$.
4. Drag on one side is $D' = \rho U_\infty^2\theta(L)$, so $C_D = 2\theta(L)/L$ per side.

**Reverse problem**: given a measured $\theta$ at $x$, invert step 3 to get $x_0$, then solve for $x_T$.

![[bl_virtual_origin.png|520]]

## Examples
- Aerofoil drag with mid-chord transition: [[SESA2022 Exam 2018-19 Solutions]] and [[SESA2022 Exam 2019-20 Solutions]] Q4(ii).
- Finding $x_0$ and $x_T$ from a measured profile: [[SESA2022 Exam 2021-22 Solutions]] Part C Q1.
- Measurement location on an untripped plate: [[SESA2022 Exam 2022-23 Solutions]] Q1(v).
- Near-laminar plus turbulent plate drag: [[SESA2022 Exam 2024-25 Solutions]] Q1(c).
- UAV wing skin friction: [[SESA2022 Exam 2020-21 Solutions]] Part B Q4.

## Related
- Parent lectures: [[SESA2022 T2 - Boundary Layers]]
- Related concepts: [[Displacement and Momentum Thickness]], [[Momentum Integral Equation]]

## Sources
- `02 - Sources/BL/Topic 2 Boundary layers.pdf`
