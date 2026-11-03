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
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/Lectures/SESA2022 Lecture 11.txt … Lecture 16.txt (2025-26 transcripts)"]
---

# D'Alembert's Paradox

In steady, inviscid, incompressible, irrotational two-dimensional flow, a closed body feels **zero drag**: its fore–aft symmetric pressure distribution integrates to no net streamwise force, which contradicts every real observation.

For the cylinder, $C_p = 1-4\sin^2\theta$ is symmetric about $\theta = 90^\circ$, so the pressure at the front stagnation point is exactly balanced by the pressure at the rear one and $D' = -\oint p\cos\theta\,R\,d\theta = 0$ ([[SESA2022 Exam 2016-17 Solutions]] Q1(ii) does the integration). Adding circulation produces lift, $L' = \rho V_\infty\Gamma$, but still no drag.

Prandtl resolved the paradox in 1904. Viscosity is confined to a thin boundary layer, but that layer separates under the adverse pressure gradient at the rear, so the rear pressure never recovers. The resulting pressure imbalance is form drag, and the wall shear adds skin-friction drag. The lesson for using potential flow is that it predicts lift and the pressures on forward-facing surfaces well, but not drag or the leeward side of a bluff body, which is the point of the validity comments in the hangar and dune questions ([[SESA2022 Exam 2018-19 Solutions]], [[SESA2022 Exam 2023-24 Solutions]]).

## Related

- Full derivation and worked examples: [[SESA2022 T3 - Potential Flow#10. D'Alembert's paradox and the Kutta–Joukowski theorem|T3 §10]]; the viscous resolution in [[SESA2022 T2 - Boundary Layers]]
- [[Flow Past a Cylinder]] · [[Boundary Layer Separation]] · [[Kutta-Joukowski Theorem]]
