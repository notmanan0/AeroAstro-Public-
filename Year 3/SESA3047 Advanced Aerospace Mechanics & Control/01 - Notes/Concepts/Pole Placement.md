---
title: "Pole Placement"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 7: Controllability, Observability and Pole Placement"
aliases: ["pole assignment", "eigenvalue assignment", "full-state feedback", "state feedback", "proportional state feedback", "Ackermann's formula"]
tags: [sesa3047, concept, control, state-feedback, pole-placement]
status: written-ahead
coverage: "Chapter 7 §7.3, Eqs. 7.10–7.18; written ahead from the handout, not yet lectured"
parent_lectures: ["[[SESA3047 7.2 - Pole Placement]]"]
related_concepts: ["[[Controllability]]", "[[Observability]]", "[[Root Locus]]", "[[Characteristic Equation and Eigenvalues]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 7.pdf"]
---

# Pole Placement

Pole placement is the design of a proportional state-feedback controller $\mathbf u=-\mathbf K\mathbf x$ whose gains put the closed-loop poles, the eigenvalues of $\mathbf A-\mathbf B\mathbf K$, at chosen locations.

Substituting the control law into $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$ gives $\dot{\mathbf x}=(\mathbf A-\mathbf B\mathbf K)\mathbf x$: the feedback changes the state matrix itself. The gains follow from matching the coefficients of $\det(\lambda\mathbf I-(\mathbf A-\mathbf B\mathbf K))$ to those of $\prod(\lambda-\lambda_i)$ for the desired poles. For the course example $\mathbf A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}$, $\mathbf B=[0\ 1]^T$, the closed-loop polynomial is $\lambda^2+(3+k_2)\lambda+(2+k_1)$, and poles at $-2,-3$ need $\mathbf K=[4\ \ 2]$.

The method works, with a unique $\mathbf K$, when the system is fully [[Controllability|controllable]] and has a single input: there are then $n$ gains for the $n$ coefficients, and a change of variables to companion form shows each gain setting one coefficient. The desired poles must be real or in conjugate pairs, since $\mathbf K$ is real, and an uncontrollable mode cannot be moved. Every state must be available, measured or estimated by an observer ([[Observability]]). With $m>1$ inputs, $\mathbf K$ has $mn$ entries for $n$ conditions, so infinitely many gains give the same poles; SESA3047 then uses the linear-quadratic regulator to choose one. Compared with [[Root Locus]], where one gain moves the poles along fixed curves, proportional control of the whole state has a gain per state and so can reach any pole set. MATLAB computes $\mathbf K$ with `place(A,B,p)`; Ackermann's formula, $\mathbf K=[0\ \cdots\ 0\ 1]\,\mathcal C^{-1}\varphi_d(\mathbf A)$, is the closed-form single-input result.

## Related

- Derivations and worked examples: [[SESA3047 7.2 - Pole Placement]]
- [[Controllability]] · [[Observability]] · [[Root Locus]] · [[Characteristic Equation and Eigenvalues]] · [[Open-Loop, Feedback and Feedforward Control]]
- Exam practice: [[SESA3047 Cambridge Solutions - 7 Controllability, Observability and Pole Placement#3F2 2019 Q1 - Aircraft pole placement with thrust|Cambridge 3F2 2019 Q1]] · [[SESA3047 Cambridge Solutions - Pole Placement, Integral Action and Observability Gramians]]
