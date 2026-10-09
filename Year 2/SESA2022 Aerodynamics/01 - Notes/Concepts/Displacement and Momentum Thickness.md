---
title: "Displacement and Momentum Thickness"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["delta star", "momentum thickness", "shape factor", "δ*", "θ"]
tags: [sesa2022, concept, boundary-layers]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Momentum Integral Equation]]", "[[Virtual Origin Method]]", "[[Law of the Wall]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf"]
---

# Displacement and Momentum Thickness

## Definition

> [!note] Definition
> The **displacement thickness** $\delta^*$ is how far the wall would have to move outward, in an inviscid flow, to carry the same mass-flow deficit as the boundary layer. The **momentum thickness** $\theta$ is the thickness of freestream fluid that carries the momentum lost to the wall.
> $$\delta^* = \int_0^\infty\left(1-\frac{u}{U_e}\right)dy,\qquad \theta = \int_0^\infty\frac{u}{U_e}\left(1-\frac{u}{U_e}\right)dy,\qquad H = \frac{\delta^*}{\theta}$$

## Explanation
- $\delta_{99}$ (where $u = 0.99U_e$) is arbitrary and hard to measure. $\delta^*$ and $\theta$ are **integral** measures, so they are robust to noise at the edge of the layer.
- **Physical meaning**: $\delta^*$ is the amount the external flow is pushed away, which is why it is used in viscous–inviscid coupling. $\theta$ is directly proportional to the drag: $D' = \rho U_\infty^2\theta$ for a flat plate (see [[Momentum Integral Equation]]).
- The **shape factor** $H$ measures how "full" the profile is:

| Profile | $H$ |
|---|---|
| Blasius (laminar) | 2.59 |
| Parabolic $2\eta-\eta^2$ | 2.50 |
| Turbulent (1/7 law) | 1.29 |
| Near separation | > 3.5 (laminar), about 2.4 (turbulent) |

For a similarity profile $u/U_e = f(\eta)$ with $\eta = y/\delta$, the thicknesses are fixed fractions of $\delta$:

$$
\frac{\delta^*}{\delta} = \int_0^1(1-f)\,d\eta,\qquad \frac{\theta}{\delta} = \int_0^1f(1-f)\,d\eta
$$

Power law $f = \eta^{1/n}$: $\delta^*/\delta = 1/(n+1)$ and $\theta/\delta = n/[(n+1)(n+2)]$.

## Examples
- Sine profile: $\delta^*/\delta = 1-2/\pi$ ([[SESA2022 Exam 2014-15 Solutions]] Q1).
- Parabolic profile: $H = 2.5$ ([[SESA2022 Exam 2024-25 Solutions]] Q1).
- From measured data by the trapezium rule, including the $(0,0)$ wall point: [[SESA2022 Exam 2021-22 Solutions]], [[SESA2022 Exam 2022-23 Solutions]], [[SESA2022 Exam 2023-24 Solutions]].
- [[SESA2022 Tutorial 2 - Viscous Flow Solutions]].

## Related
- Parent lectures: [[SESA2022 T2 - Boundary Layers]]
- Related concepts: [[Momentum Integral Equation]], [[Virtual Origin Method]], [[Boundary Layer Separation]]

## Sources
- `02 - Sources/BL/Topic 2 Boundary layers.pdf`
