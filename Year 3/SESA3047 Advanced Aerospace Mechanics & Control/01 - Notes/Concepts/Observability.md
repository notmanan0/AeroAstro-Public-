---
title: "Observability"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 7: Controllability, Observability and Pole Placement"
aliases: ["observable", "fully observable", "observability matrix", "observer", "state estimator"]
tags: [sesa3047, concept, control, state-space, observability, sensors]
status: written-ahead
coverage: "Chapter 7 §7.2, Eqs. 7.7–7.9; written ahead from the handout, not yet lectured"
parent_lectures: ["[[SESA3047 7.1 - Controllability and Observability]]"]
related_concepts: ["[[Controllability]]", "[[Pole Placement]]", "[[State, Input, Output and Parameter]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 7.pdf"]
---

# Observability

A linear system $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$, $\mathbf y=\mathbf C\mathbf x$ is observable if its internal state can be determined from its outputs (and known inputs) over a finite time.

With $n$ states, the test is the rank of the observability matrix:

$$
\mathcal O=\begin{bmatrix}\mathbf C\\\mathbf C\mathbf A\\\vdots\\\mathbf C\mathbf A^{n-1}\end{bmatrix},\qquad\text{fully observable}\iff\operatorname{rank}\mathcal O=n .
$$

The matrix comes from differentiating the output: for the free response $\mathbf y=\mathbf Ce^{\mathbf At}\mathbf x_0$, the values of $\mathbf y,\dot{\mathbf y},\dots,\mathbf y^{(n-1)}$ at $t=0$ are $\mathcal O\mathbf x_0$, so $\mathbf x_0$ can be solved for exactly when $\mathcal O$ has rank $n$. If it does not, some initial state produces zero output for all time and is invisible to the sensors. Observability is the dual of [[Controllability]]: $(\mathbf A,\mathbf C)$ is observable exactly when $(\mathbf A^T,\mathbf C^T)$ is controllable.

On an aircraft, gyroscopes measure $p$, $q$, $r$ directly, while the velocities come from air data ($u=V\cos\alpha\cos\beta$, $v=V\sin\beta$, $w=V\sin\alpha\cos\beta$) combined with inertial and GPS measurements, and the attitude angles from integrated gyro rates combined with accelerometers. Fewer sensors than states can still be enough: a single measured state that the others drive, directly or through a chain, often makes the system observable, as pitch attitude alone does for the phugoid model of practice problem 2. Whether it does in a given case is decided by the rank, not by counting sensors. When a system is observable but its states are not measured, an observer such as a Kalman filter reconstructs them. SESA3047 assumes full observability throughout; MATLAB forms the matrix with `obsv(A,C)`.

## Related

- Test, derivation and examples: [[SESA3047 7.1 - Controllability and Observability#4. Observability (7.7–7.9)|7.1 §4]]
- [[Controllability]] · [[Pole Placement]] · [[State, Input, Output and Parameter]]
- Exam practice: [[SESA3047 Cambridge Solutions - 7 Controllability, Observability and Pole Placement#3F2 EP3 Q3 - Inverted pendulum state measurements|Cambridge 3F2 EP3 Q3]] · [[SESA3047 Cambridge Solutions - Observers and Estimated-State Feedback I]]
