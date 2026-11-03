---
title: "Linear, Nonlinear and Time-Varying Models"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["model classifications", "LTI and LTV models", "Duffing oscillator", "constant-coefficient model", "distributed-parameter model"]
tags: [sesa3047, concept, linearisation, time-varying]
status: complete
parent_lectures: ["[[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]"]
related_concepts: ["[[Small Perturbation Linearisation]]", "[[Model Fidelity and Validity]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/L3 - SESA3047.txt"]
---

# Linear, Nonlinear and Time-Varying Models

The oscillator

$$
m\ddot x+c\dot x+kx+\mu x^3=0
$$

is nonlinear because of the cubic term. Close to $x=0$ that term is negligible, leaving the linear model

$$
m\ddot x+c\dot x+kx=0,
$$

which satisfies superposition but is only a local approximation to the nonlinear plant.

Separately, a model is time-invariant if its coefficients and relationships don't change explicitly with time, and time-varying if at least one does. For example,

$$
m\ddot x+c\dot x+k(t)x=0
$$

is linear in $x$ but time-varying whenever $k(t)$ changes.

## Related

- [[Small Perturbation Linearisation]] · [[Model Fidelity and Validity]]
