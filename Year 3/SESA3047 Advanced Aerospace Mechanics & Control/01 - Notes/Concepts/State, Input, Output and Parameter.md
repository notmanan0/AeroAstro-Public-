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

## Definitions

- **Variable:** any model quantity that can change.
- **Parameter:** quantity treated as fixed within one model instance.
- **Input:** imposed command or disturbance that drives the model.
- **Output:** selected quantity exposed for observation or use.
- **State:** a minimum set which, together with the input and governing model, determines future evolution.

For a second-order oscillator, a possible state is

$$
\mathbf x=\begin{bmatrix}x&\dot x\end{bmatrix}^T.
$$

Position alone does not determine the future because two systems at the same position can have different velocities.

## Related

- [[State-Space Representation]] · [[Model Fidelity and Validity]]

