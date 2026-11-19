---
title: "Controllability"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 7: Controllability, Observability and Pole Placement"
aliases: ["controllable", "fully controllable", "controllability matrix", "reachability", "reachable", "Kalman rank test"]
tags: [sesa3047, concept, control, state-space, controllability]
status: written-ahead
coverage: "Chapter 7 §7.1, Eqs. 7.1–7.6; written ahead from the handout, not yet lectured"
parent_lectures: ["[[SESA3047 7.1 - Controllability and Observability]]"]
related_concepts: ["[[Observability]]", "[[Pole Placement]]", "[[Rank and Consistency of Linear Systems]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 7.pdf"]
---

# Controllability

A linear system $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$ is controllable if its inputs can move the state from any initial state to any final state in a finite time.

With $n$ states, the test is the rank of the controllability matrix:

$$
\mathcal C=\begin{bmatrix}\mathbf B&\mathbf A\mathbf B&\mathbf A^2\mathbf B&\cdots&\mathbf A^{n-1}\mathbf B\end{bmatrix},\qquad\text{fully controllable}\iff\operatorname{rank}\mathcal C=n .
$$

For a single input $\mathcal C$ is square and the test is $\det\mathcal C\neq0$. The powers stop at $n-1$ because, by the Cayley–Hamilton theorem, $\mathbf A^n$ and every higher power are combinations of the lower ones; so the forced response $\int e^{\mathbf A(t-\tau)}\mathbf B\mathbf u\,d\tau$ always lies in the column space of $\mathcal C$. If the rank falls short, some combination $\mathbf w^T\mathbf x$ evolves as if there were no input at all, and the mode it belongs to cannot be moved by any feedback.

Controllability is what makes [[Pole Placement]] possible: a fully controllable single-input system can have its closed-loop poles put anywhere (real, or in conjugate pairs). Having fewer actuators than states does not make a system uncontrollable: one aileron alone controls all four lateral states of the Navion, because roll couples into yaw and sideslip. The rank answers yes or no; how much input it takes is a separate question, which a nearly singular $\mathcal C$ flags. MATLAB forms the matrix with `ctrb(A,B)`.

## Related

- Test, proof and examples: [[SESA3047 7.1 - Controllability and Observability#3. Controllability (7.1)|7.1 §3]]
- [[Observability]] (the dual property) · [[Pole Placement]] · [[Rank and Consistency of Linear Systems]] · [[Matrix Exponential and Modal Solution]]
- Exam practice: [[SESA3047 Cambridge Solutions - 7 Controllability, Observability and Pole Placement]] · [[SESA3047 Cambridge Solutions - Controllability, Gramians and Realisations]]
