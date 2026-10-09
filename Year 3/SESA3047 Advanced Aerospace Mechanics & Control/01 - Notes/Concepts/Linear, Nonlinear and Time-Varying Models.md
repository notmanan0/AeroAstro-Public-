---
title: "Linear, Nonlinear and Time-Varying Models"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["model classifications", "LTI and LTV models"]
tags: [sesa3047, concept, linearisation, time-varying]
status: complete
parent_lectures: ["[[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]"]
related_concepts: ["[[Small Perturbation Linearisation]]", "[[Model Fidelity and Validity]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/L3 - SESA3047.txt"]
---

# Linear, Nonlinear and Time-Varying Models

## Nonlinear and linear

$$
m\ddot x+c\dot x+kx+\mu x^3=0
$$

is nonlinear. Near $x=0$, neglecting $\mu x^3$ gives

$$
m\ddot x+c\dot x+kx=0.
$$

The linear model satisfies superposition but is only a local approximation of the nonlinear plant.

## Time invariant and time varying

- time invariant: coefficients and relationships do not change explicitly with time;
- time varying: at least one coefficient or relationship changes explicitly with time.

Example:

$$
m\ddot x+c\dot x+k(t)x=0
$$

is linear in $x$ but time varying when $k(t)$ changes.

## Related

- [[Small Perturbation Linearisation]] · [[Model Fidelity and Validity]]

