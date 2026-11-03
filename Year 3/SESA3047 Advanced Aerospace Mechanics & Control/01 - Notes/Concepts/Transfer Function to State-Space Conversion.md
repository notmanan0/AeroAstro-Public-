---
title: "Transfer Function to State-Space Conversion"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 5: State-Space Models"
aliases: ["controllable canonical form", "phase-variable canonical form", "state-space realisation", "converting transfer functions to state-space form", "block diagram to state space"]
tags: [sesa3047, concept, state-space, transfer-function]
status: complete
coverage: "Chapter 5 §§5.4–5.6; written ahead from the handout, not yet lectured"
parent_lectures: ["[[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]]"]
related_concepts: ["[[Transfer Function]]", "[[State-Space Representation]]", "[[Poles and Zeros]]"]
sources: ["02 - Sources/Lectures/Chapter_5.pdf"]
---

# Transfer Function to State-Space Conversion

A strictly proper transfer function $G(s)=N(s)/D(s)$ is put in state-space form by introducing an intermediate signal $V$ with $D(s)V=R$ and $W=N(s)V$: the denominator becomes an $n$th-order ODE in $v$, whose states are $v,\dot v,\dots,v^{(n-1)}$, and the numerator becomes the output equation.

For $G=(5s^2+2s+2)/(s^3+6s^2+9s+3)$ (handout Eq. 5.30) this gives

$$
\mathbf A=\begin{bmatrix}0&1&0\\0&0&1\\-3&-9&-6\end{bmatrix},\quad\mathbf B=\begin{bmatrix}0\\0\\1\end{bmatrix},\quad\mathbf C=\begin{bmatrix}2&2&5\end{bmatrix}.
$$

The pattern holds for this construction in general: the denominator coefficients, negated and in reverse order, fill the last row of $\mathbf A$; the numerator coefficients in reverse order fill $\mathbf C$. In a chain-of-integrators picture the denominator gives feedback gains and the numerator output taps. Textbooks call it the controllable canonical (or phase-variable) form; the course does not name it.

The realisation is not unique. The eigenvalues of $\mathbf A$ (the poles) are the same in every realisation, but where the zeros appear depends on the choice of states: another standard form puts them in $\mathbf B$. If the numerator degree equals the denominator degree, part of the input passes straight through and $\mathbf D\neq0$.

A block diagram is converted the same way, block by block: each first-order block gives one state equation, and every internal signal (an error $u_1=K_1(r_1-y_1)$, an output sum) is replaced by states and reference inputs, so the feedback gains end up inside $\mathbf A$.

## Related

- [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]] · [[SESA3047 Chapter 5 Practice Problems - Solutions#Problem 2. Transfer functions to state space|Practice problem 2]]
- [[Transfer Function]] · [[State-Space Representation]] · [[Poles and Zeros]] · [[Closed-Loop Transfer Function]]
