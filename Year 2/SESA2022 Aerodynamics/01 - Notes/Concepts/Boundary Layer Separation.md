---
title: "Boundary Layer Separation"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 2: Boundary Layers"
aliases: ["separation", "adverse pressure gradient", "flow separation"]
tags: [sesa2022, concept, boundary-layers]
status: complete
parent_lectures: ["[[SESA2022 T2 - Boundary Layers]]", "[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Aerofoil Stall]]", "[[D'Alembert's Paradox]]", "[[Momentum Integral Equation]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf"]
---

# Boundary Layer Separation

## Definition

> [!note] Definition
> A boundary layer **separates** when an **adverse pressure gradient** ($dp/dx>0$) decelerates the near-wall fluid until the wall shear stress vanishes, $\left.\partial u/\partial y\right|_{w} = 0$. Downstream of that point the flow reverses and the layer lifts off the surface.

## Explanation
- At the wall ($u = v = 0$) the momentum equation gives $\mu\left.\dfrac{\partial^2u}{\partial y^2}\right|_w = \dfrac{dp}{dx}$. With $dp/dx>0$ the profile curvature changes sign near the wall (an **inflection point**). The low-momentum fluid can't climb the pressure hill and stops, then reverses.
- **Turbulent layers resist separation better** because mixing brings high-momentum fluid down to the wall. That's why golf-ball dimples and vortex generators *delay* separation.
- **Consequences**:
  - Loss of pressure recovery, giving **pressure (form) drag**.
  - Wakes and unsteady vortex shedding.
  - [[Aerofoil Stall]] at high $\alpha$.
  - This is the real-world resolution of [[D'Alembert's Paradox]].
- **Indicators**: $C_f\to0$ and a rising shape factor $H$ (above about 3.5 laminar, 2.4 turbulent).

## Examples
- Hangar in a wind: leeward separation and wake ([[SESA2022 Exam 2018-19 Solutions]] Q1(iv)).
- River dune: the lee-side separation invalidates potential-flow power estimates ([[SESA2022 Exam 2023-24 Solutions]] Q2(iv)).
- Aerofoil at 16° and 14°: [[SESA2022 Exam 2021-22 Solutions]] and [[SESA2022 Exam 2024-25 Solutions]].

## Related
- Parent lectures: [[SESA2022 T2 - Boundary Layers]], [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Aerofoil Stall]], [[D'Alembert's Paradox]]

## Sources
- `02 - Sources/BL/Topic 2 Boundary layers.pdf`
