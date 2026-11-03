---
title: "Law of the Wall"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["wall units", "inner units", "log law", "viscous sublayer", "skin friction velocity", "friction velocity", "plus units", "y plus"]
tags: [sesa2022, concept, boundary-layers, turbulence]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf", "02 - Sources/Lectures/SESA2022 Lecture 5.txt … Lecture 10.txt (2025-26 transcripts)"]
---

# Law of the Wall

Near the wall, the mean velocity in a turbulent boundary layer depends only on the wall shear stress and the viscosity, so in wall (inner) units

$$
u_\tau = \sqrt{\tau_w/\rho} = U_\infty\sqrt{C_f/2},\qquad u^+ = \frac{u}{u_\tau},\qquad y^+ = \frac{yu_\tau}{\nu}
$$

the profiles from all flows collapse onto one universal curve.

| Region | Range | Law | Physics |
|---|---|---|---|
| Viscous sub-layer | $y^+<5$ | $u^+ = y^+$ | viscous stress dominates |
| Buffer layer | $5<y^+<30$ | neither law fits | turbulence production peaks |
| Log layer | $y^+>30$–$50$, $y/\delta<0.2$ | $u^+ = \frac1\kappa\ln y^++B$ | Reynolds stress dominates |
| Outer / wake | $y/\delta>0.2$ | power law or Coles wake | large eddies, depends on history |

The constants are $\kappa\approx0.39$–$0.41$ and $B\approx4.3$–$5.0$; the 2024-25 rubric uses $\kappa = 0.39$ and $B = 4.3$. The inner scaling is needed because a power law, $u\propto y^{1/n}$, has an infinite gradient at the wall and so can't give $\tau_w$. The Clauser method turns this round: choose $u_\tau$ so that the measured points fall on the log law, and $C_f$ follows from a velocity profile alone. Wall units are also how near-wall devices and meshes are sized. Riblets and roughness are specified in wall units (10 wall units is $h = 10\nu/u_\tau$), and CFD first-cell heights aim for $y^+\approx1$.

![[bl_law_of_wall.png|520]]

Past-paper uses: a sketch of the structure ([[SESA2022 Exam 2013-14 Solutions]] Q1(i)); an inner-unit plot from pitot data and riblet sizing ([[SESA2022 Exam 2023-24 Solutions]] Q1(iii)–(vi)).

## Related

- Full derivation and worked examples: [[SESA2022 T2 - Boundary Layers#6. Law of the wall|T2 §6]]
- [[Displacement and Momentum Thickness]] · [[Momentum Integral Equation]]
