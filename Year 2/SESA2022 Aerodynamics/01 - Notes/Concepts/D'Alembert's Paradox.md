---
title: "D'Alembert's Paradox"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["d'Alembert paradox", "zero drag in potential flow"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]", "[[SESA2022 T2 - Boundary Layers]]"]
related_concepts: ["[[Flow Past a Cylinder]]", "[[Boundary Layer Separation]]", "[[Kutta-Joukowski Theorem]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# D'Alembert's Paradox

## Definition

> [!note] Definition
> In steady, inviscid, incompressible, irrotational 2D flow, a closed body experiences **zero drag**. The fore–aft symmetric pressure distribution integrates to no net streamwise force, which contradicts every real observation.

## Explanation
- For the cylinder, $C_p = 1-4\sin^2\theta$ is symmetric about $\theta = 90^\circ$. The front stagnation pressure is exactly balanced by the rear stagnation pressure, so $D' = -\oint p\cos\theta\,R\,d\theta = 0$.
- Adding circulation creates **lift** ($L' = \rho V_\infty\Gamma$) but still **no drag**.
- **Resolution (Prandtl, 1904)**: viscosity is confined to a thin boundary layer, but that layer **separates** under the rear adverse pressure gradient. The rear pressure never recovers, so the pressure imbalance gives **form drag**, and wall shear adds **skin-friction drag**.
- **Lesson**: potential flow predicts lift and forward-facing pressures well, but not drag or the leeward side of bluff bodies.

## Examples
- Cylinder pressure integration: [[SESA2022 Exam 2016-17 Solutions]] Q1(ii).
- Hangar and dune validity comments: [[SESA2022 Exam 2018-19 Solutions]] and [[SESA2022 Exam 2023-24 Solutions]].

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]], [[SESA2022 T2 - Boundary Layers]]
- Related concepts: [[Flow Past a Cylinder]], [[Boundary Layer Separation]], [[Kutta-Joukowski Theorem]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`
