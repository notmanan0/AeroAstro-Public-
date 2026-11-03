---
title: "Model Fidelity and Validity"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 1: Fundamental Concepts"
aliases: ["model fidelity", "model validity range"]
tags: [sesa3047, concept, modelling]
status: complete
parent_lectures: ["[[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]"]
related_concepts: ["[[Dynamic System, Plant and Model]]", "[[Linear, Nonlinear and Time-Varying Models]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/L3 - SESA3047.txt"]
---

# Model Fidelity and Validity

**Fidelity** is how much relevant physical detail a model represents. **Validity** is whether its assumptions make its predictions credible for a particular purpose and operating range. The working rule is

$$
\boxed{\text{Use the simplest credible model for the stated purpose and range}.}
$$

More detail means more data and more computation, and it doesn't guarantee accuracy if the parameters are poor or the model answers the wrong question. A rigid-body model is fine when structural deformation has negligible effect; a flexible multibody model is needed when bending, vibration or rigid–flexible coupling materially changes the response.

## Related

- [[Dynamic System, Plant and Model]] · [[Linear, Nonlinear and Time-Varying Models]]
