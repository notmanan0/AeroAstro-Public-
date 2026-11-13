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

Every modelling simplification in SESA2027 is justified by one of three design and analysis principles. DAP1 is George Box's "all models are wrong, but some models are useful". DAP2 is Occam's razor: prefer the simplest model that explains the behaviour of interest. DAP3 is divide and conquer: split a problem recursively into simpler, independent parts.

Behind all three is the observation that model accuracy grows with complexity but with diminishing returns, while each extra detail costs parameters, identification effort and insight. The question to ask of a model is not whether it is true but whether it is useful for the decision at hand, and where it breaks.

| Principle | Where it is used |
|---|---|
| DAP1 | Rigid body, flat Earth, constant mass; first-order Taylor aerodynamic derivatives; the rigid body with fixed CG ignores fuel slosh |
| DAP2 | The SPO approximation (2 states, 7 parameters); most sensors modelled as 0th, 1st or 2nd order; linear, model-based PID control |
| DAP3 | Longitudinal and lateral decoupling; the Laplace route (ODE → algebra → inverse); studying P, I and D actions separately; analysing the sensing chain apart from the aircraft and the control loop |

The F-4C shows how well DAP2 can pay off: the full 4×4 model gives $\omega_n = 1.4052$ rad/s and $\zeta = 0.2626$, and the two-state SPO approximation gives 1.4115 and 0.2637, under 0.5 % out ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]). For DAP1 the A380 numbers are a 10 s burn using 0.005 % of MTOW and a flat-Earth error of 0.020 % ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]).

## Related

- [[Small Perturbation Linearisation]] · [[Short Period Oscillation]] · [[Sensor Dynamic Models]]
