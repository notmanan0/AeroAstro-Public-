---
title: "Separation of Time Scales"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["time-scale separation", "separation of timescales", "reduced-order model", "reduced-order approximation", "quasi-static approximation", "singular perturbation"]
tags: [sesa3047, concept, modes, reduced-order-model, flight-dynamics]
status: complete
coverage: "Chapter 6 §§6.5–6.6 (key idea, p. 8); SPO approximation set as reading after L17, phugoid approximations lectured in L18 (Mon 16 Nov)"
parent_lectures: ["[[SESA3047 6.2 - Phugoid Approximation]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]"]
related_concepts: ["[[Short Period Oscillation]]", "[[Phugoid Mode]]", "[[State Coupling]]", "[[Eigenvectors as Mode Shapes]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/16 November 2026 at 11_51_48.txt"]
---

# Separation of Time Scales

When the modes of a system evolve on very different time scales, each mode can be approximated by a smaller set of equations: on the fast scale the slow states are treated as frozen, and on the slow scale the fast states are treated as having already settled.

The longitudinal aircraft model is the standard example. The F-4C's short-period oscillation has a period of 4.6 s and halves in 1.9 s; its phugoid has a period of 81 s, 17 times longer. Over one SPO cycle the speed $u$ and attitude $\theta$ hardly move, so the SPO approximation drops them and keeps $w$ and $q$ (Eqs. 6.23–6.27). Over one phugoid cycle the SPO has died away many times over, so the pitching moment is always in balance ($\dot q\approx0$) and the terms in $q$ and $\dot w$ are negligible; the phugoid approximation keeps $u$, $w$ and $\theta$ with $w$ slaved to $u$ by the moment balance (Eqs. 6.34–6.38).

Mathematically, setting a fast derivative to zero turns a differential equation into an algebraic constraint. The reduced system $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$ then has a singular $\mathbf M$, and it has fewer eigenvalues than states: the 3×3 phugoid system of Eq. 6.36 has two. The method is known in applied mathematics as singular perturbation; its error grows as the time scales move closer together.

The payoff is formulae in a handful of aerodynamic derivatives, which show which physical effects set each mode's frequency and damping and give usable estimates when only those derivatives are known.

## Related

- The phugoid case: [[SESA3047 6.2 - Phugoid Approximation#3. Which states matter: time scales and coupling|6.2 §3]]; the SPO case: [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]]
- [[Short Period Oscillation]] · [[Phugoid Mode]] · [[Lanchester's Phugoid Approximation]] · [[State Coupling]] · [[Eigenvectors as Mode Shapes]]
