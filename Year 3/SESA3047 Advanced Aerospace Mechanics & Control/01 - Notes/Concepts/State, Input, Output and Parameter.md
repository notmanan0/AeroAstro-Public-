---
title: "State, Input, Output and Parameter"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["states and model quantities"]
tags: [sesa3047, concept, state-space]
status: complete
parent_lectures: ["[[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]"]
related_concepts: ["[[State-Space Representation]]", "[[Dynamic System, Plant and Model]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/L3 - SESA3047.txt"]
---

# State, Input, Output and Parameter

A model's quantities fall into a few roles. A **variable** is anything in the model that can change, and a **parameter** is a quantity held fixed within one instance of the model. An **input** is an imposed command or disturbance that drives the model, and an **output** is a quantity selected for observation or use. The **state** is a minimum set of variables that, together with the input and the governing equations, determines how the system evolves from now on.

For a second-order oscillator a possible state is

$$
\mathbf x=\begin{bmatrix}x&\dot x\end{bmatrix}^T.
$$

Position alone isn't enough, because two systems at the same position can be moving at different velocities and will then behave differently.

## Related

- [[State-Space Representation]] · [[Model Fidelity and Validity]]
