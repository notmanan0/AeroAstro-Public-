---
title: "Longitudinal and Lateral Dynamics"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 5: State-Space Models"
aliases: ["longitudinal dynamics", "lateral dynamics", "lateral-directional dynamics", "symmetric and asymmetric motion", "longitudinal-lateral decoupling"]
tags: [sesa3047, concept, flight-dynamics, state-space]
status: complete
coverage: "Chapter 5 §5.3 and Practice problem 3; the split follows from Eqs. 5.7–5.8, lectured in L14; the aerodynamic part written ahead"
parent_lectures: ["[[SESA3047 5.2 - Longitudinal State-Space Model]]"]
related_concepts: ["[[Aerodynamic Stability Derivatives]]", "[[Small Perturbation Linearisation]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Chapter_5.pdf"]
---

# Longitudinal and Lateral Dynamics

After linearisation about straight, steady flight, a symmetric aircraft's six perturbation equations split into two independent sets: the longitudinal dynamics in $u$, $w$, $q$ (with pitch angle $\theta$) and the lateral dynamics in $v$, $p$, $r$ (with bank angle $\phi$).

The split needs three things. The trim must be symmetric: no sideslip, bank or turn rate. The aircraft must be symmetric about its $x$–$z$ plane, so $J_{xy}=J_{yz}=0$ and the linearised moment equations, Eq. 5.8, keep only $J_{xz}$ coupling roll to yaw. And the aerodynamics must be symmetric too: to first order, sideslip and roll or yaw rate do not change lift, drag or pitching moment, and $u$, $w$, $q$ do not change side force, rolling or yawing moment. A spinning rotor, an asymmetric store or a trim in a steady turn breaks the split.

Each set becomes a $4\times4$ state-space model. The longitudinal one, $\mathbf x=[u,w,q,\theta]^T$, is Eq. 5.18; its eigenvalues are the short-period and phugoid modes. The lateral one, $\mathbf x=[v,p,r,\phi]^T$, is Practice problem 3; in Year 2 its modes were the roll subsidence, spiral and Dutch roll.

## Related

- [[SESA3047 5.2 - Longitudinal State-Space Model#1. The longitudinal–lateral split|5.2 §1]] · [[SESA3047 Chapter 5 Practice Problems - Solutions#Problem 3. The lateral state-space model|Practice problem 3]]
- [[Aerodynamic Stability Derivatives]] · [[Small Perturbation Linearisation]] · [[Lateral and Directional Stability]] (SESA2022) · [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]
