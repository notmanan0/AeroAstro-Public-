---
title: "Boundary Layer Separation"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["separation", "adverse pressure gradient", "flow separation", "favourable pressure gradient", "tripping"]
tags: [sesa2022, concept, boundary-layers]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Aerofoil Stall]]", "[[D'Alembert's Paradox]]", "[[Momentum Integral Equation]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf", "02 - Sources/Lectures/SESA2022 Lecture 5.txt … Lecture 10.txt (2025-26 transcripts)"]
---

# Boundary Layer Separation

A boundary layer **separates** when an adverse pressure gradient ($dp/dx>0$) slows the near-wall fluid until the wall shear stress vanishes, $\left.\partial u/\partial y\right|_{w} = 0$. Downstream of that point the flow reverses and the layer lifts off the surface.

The mechanism shows up in the momentum equation at the wall, where $u = v = 0$ leaves $\mu\left.\partial^2u/\partial y^2\right|_w = dp/dx$. With $dp/dx>0$ the profile's curvature changes sign near the wall, giving an inflection point, and the low-momentum fluid there can't climb the pressure hill; it stops, then reverses. The warning signs are $C_f\to0$ and a rising shape factor $H$, above about 3.5 for a laminar layer and 2.4 for a turbulent one. Turbulent layers resist separation better because mixing brings high-momentum fluid down to the wall, which is why golf-ball dimples and vortex generators delay it.

Separation is behind most of what potential flow gets wrong. The pressure no longer recovers behind the body, giving pressure (form) drag, the wake becomes unsteady with vortex shedding, and at high $\alpha$ the aerofoil stalls ([[Aerofoil Stall]]). It is the real-world resolution of [[D'Alembert's Paradox]].

Past-paper uses: the leeward separation and wake of a hangar in a wind ([[SESA2022 Exam 2018-19 Solutions]] Q1(iv)); lee-side separation on a river dune, which invalidates potential-flow power estimates ([[SESA2022 Exam 2023-24 Solutions]] Q2(iv)); aerofoils at 16° and 14° ([[SESA2022 Exam 2021-22 Solutions]], [[SESA2022 Exam 2024-25 Solutions]]).

## Related

- Full derivation and worked examples: [[SESA2022 T2 - Boundary Layers#8. Pressure gradients and separation|T2 §8]]; stall in [[SESA2022 T4 - Thin Aerofoil Theory]]
- [[Aerofoil Stall]] · [[D'Alembert's Paradox]]
