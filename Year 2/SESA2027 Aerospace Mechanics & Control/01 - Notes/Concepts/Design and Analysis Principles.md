---
title: "Design and Analysis Principles"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["DAP", "DAP1", "DAP2", "DAP3", "Occam's razor", "divide and conquer"]
tags: [sesa2027, concept, modelling]
status: complete
parent_lectures: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]"]
related_concepts: ["[[Small Perturbation Linearisation]]", "[[Short Period Oscillation]]", "[[Sensor Dynamic Models]]"]
sources: ["02 - Sources/Lectures/Lecture 1.01.pdf"]
---

# Design and Analysis Principles

SESA2027 justifies every modelling simplification with three design and analysis principles (L1.01, Dr S. Araujo-Estrada). DAP1 is George Box's "all models are wrong, but some models are useful". DAP2 is Occam's razor: prefer the simplest model that explains the behaviour of interest. DAP3 is divide and conquer: split a problem recursively into simpler, independent parts.

Behind all three is the observation that model accuracy grows with complexity but with diminishing returns, while each extra detail costs parameters, identification effort and insight. The question to ask of a model is not whether it is true but whether it is useful for the decision at hand, and where it breaks.

| Principle | Where it is used |
|---|---|
| DAP1 | Rigid body, flat Earth, constant mass; first-order Taylor aerodynamic derivatives; the rigid body with fixed CG ignores fuel slosh |
| DAP2 | The SPO approximation (2 states, 7 parameters); most sensors modelled as 0th, 1st or 2nd order; linear, model-based PID control |
| DAP3 | Longitudinal and lateral decoupling; the Laplace route (ODE → algebra → inverse); studying P, I and D actions separately; sensing as a separate Part C |

The F-4C shows how well DAP2 can pay off: the full 4×4 model gives $\omega_n = 1.4052$ rad/s and $\zeta = 0.2626$, and the two-state SPO approximation gives 1.4115 and 0.2637, under 0.5 % out ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]). The A380 checks in A1 do the same for DAP1: a 10 s burn uses 0.004 % of MTOW and the flat-Earth error is 0.0126 % ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]).

## Related

- [[Small Perturbation Linearisation]] · [[Short Period Oscillation]] · [[Sensor Dynamic Models]]
