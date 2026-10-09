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

## Definition

> [!note] Definition
> Three guiding principles are used throughout SESA2027 to justify every modelling simplification:
> - **DAP1**: "All models are wrong, but some models are useful" (G. Box).
> - **DAP2**: **Occam's razor**. Prefer the simplest model that explains the behaviour of interest.
> - **DAP3**: **Divide and conquer**. Recursively split a problem into simpler, independent parts.

## Explanation
- Model accuracy grows with complexity, but with **diminishing returns**. Extra detail costs parameters, identification effort and insight.
- The module applies the principles repeatedly:

| Principle | Where it is used |
|---|---|
| DAP1 | Rigid body, flat Earth, constant mass; first-order Taylor aerodynamic derivatives; the rigid body with fixed CG ignores fuel slosh |
| DAP2 | The **SPO approximation**: 2 states, 7 parameters, under 0.5 % error for the F-4C. Most sensors are modelled as 0th, 1st or 2nd order. The course uses linear, model-based PID control |
| DAP3 | Longitudinal and lateral decoupling; the Laplace route (ODE → algebra → inverse); studying P, I and D actions separately; a separate sensing part (Part C) |

- The question is not "is the model true?" but "is it **useful** for the decision at hand, and do I know where it breaks?"

## Examples
- F-4C: the full 4×4 model gives $\omega_n = 1.4052$ and $\zeta = 0.2626$; the SPO approximation gives $1.4115$ and $0.2637$. See [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]].
- A380 reality checks: a 10 s burn is $0.004\%$ of MTOW; the flat-Earth error is $0.0126\%$ ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]).

## Related
- [[Small Perturbation Linearisation]] · [[Short Period Oscillation]] · [[Sensor Dynamic Models]]

## Sources
- Lecture 1.01 (Dr S. Araujo-Estrada)
