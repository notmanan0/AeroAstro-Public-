---
title: "Law of the Wall"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["wall units", "inner units", "log law", "viscous sublayer"]
tags: [sesa2022, concept, boundary-layers, turbulence]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf"]
---

# Law of the Wall

## Definition

> [!note] Definition
> Near the wall, a turbulent boundary layer's mean velocity depends only on the wall shear stress and viscosity. Scaled in **wall (inner) units**:
> $$u_\tau = \sqrt{\tau_w/\rho} = U_\infty\sqrt{C_f/2},\qquad u^+ = \frac{u}{u_\tau},\qquad y^+ = \frac{yu_\tau}{\nu}$$
> the profiles from all flows collapse onto one universal curve.

## Explanation

| Region | Range | Law | Physics |
|---|---|---|---|
| Viscous sub-layer | $y^+<5$ | $u^+ = y^+$ | viscous stress dominates |
| Buffer layer | $5<y^+<30$ | neither law fits | turbulence production peaks |
| Log layer | $y^+>30$–$50$, $y/\delta<0.2$ | $u^+ = \frac1\kappa\ln y^++B$ | Reynolds stress dominates |
| Outer / wake | $y/\delta>0.2$ | power law or Coles wake | large eddies, depends on history |

- Constants: $\kappa\approx0.39$–$0.41$ and $B\approx4.3$–$5.0$. The 2024-25 rubric uses $\kappa = 0.39$, $B = 4.3$.
- A power law ($u\propto y^{1/n}$) can't give $\tau_w$, because its gradient is infinite at the wall. That's why the inner scaling is needed.
- **Engineering use**: riblets and roughness are sized in wall units (e.g. 10 wall units, $h = 10\nu/u_\tau$). CFD first-cell heights target $y^+\approx1$.
- **Clauser method**: choose $u_\tau$ so that the measured points fall on the log law. This gives $C_f$ from a velocity profile alone.

![[bl_law_of_wall.png|520]]

## Examples
- Structure sketch: [[SESA2022 Exam 2013-14 Solutions]] Q1(i).
- Inner-unit plot from pitot data, and riblet sizing: [[SESA2022 Exam 2023-24 Solutions]] Q1(iii)–(vi).

## Related
- Parent lectures: [[SESA2022 T2 - Boundary Layers]]
- Related concepts: [[Displacement and Momentum Thickness]], [[Momentum Integral Equation]]

## Sources
- `02 - Sources/BL/Topic 2 Boundary layers.pdf`
