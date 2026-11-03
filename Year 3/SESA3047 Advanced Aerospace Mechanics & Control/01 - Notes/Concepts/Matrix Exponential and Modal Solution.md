---
title: "Matrix Exponential and Modal Solution"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 5: State-Space Models"
aliases: ["matrix exponential", "state-transition matrix", "expm", "eigenvalue decomposition", "modal decomposition", "eigenvalue stability criterion"]
tags: [sesa3047, concept, state-space, stability, eigenvalues]
status: complete
coverage: "Chapter 5 §5.7; written ahead from the handout, not yet lectured"
parent_lectures: ["[[SESA3047 5.4 - Time-Domain Solution and Stability]]"]
related_concepts: ["[[Characteristic Equation and Eigenvalues]]", "[[Eigenvalues and Eigenvectors]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Chapter_5.pdf"]
---

# Matrix Exponential and Modal Solution

The free linear system $\dot{\mathbf x}=\mathbf A\mathbf x$ has the solution $\mathbf x(t)=e^{\mathbf At}\mathbf x_0$, where $e^{\mathbf At}=\mathbf I+\mathbf At+(\mathbf At)^2/2!+\cdots$ is the matrix exponential, not the exponential of each entry.

When $\mathbf A$ has a full set of eigenvectors, $\mathbf A=\mathbf V\boldsymbol\Lambda\mathbf V^{-1}$ and every power is $\mathbf A^k=\mathbf V\boldsymbol\Lambda^k\mathbf V^{-1}$, so the series collapses to

$$
\mathbf x(t)=\mathbf Ve^{\boldsymbol\Lambda t}\mathbf V^{-1}\mathbf x_0=\sum_ic_ie^{\lambda_it}\mathbf v_i,\qquad\mathbf c=\mathbf V^{-1}\mathbf x_0 .
$$

Each term is a mode: its eigenvector is the shape, its eigenvalue the time behaviour. The system is asymptotically stable exactly when every eigenvalue has a negative real part, and unstable if any has a positive real part. Eigenvalues on the imaginary axis are marginal if they are simple, but a repeated one without enough eigenvectors (a Jordan block) adds a $te^{\lambda t}$ term. The satellite of Chapter 5, with a double zero eigenvalue and one eigenvector, drifts without bound for this reason.

As a check, $e^{\mathbf A}$ for $\mathbf A=[1\ 2;\ 3\ 4]$ is $[51.97\ 74.74;\ 112.10\ 164.07]$, not $[e^1\ e^2;\ e^3\ e^4]$.

## Related

- [[SESA3047 5.4 - Time-Domain Solution and Stability]]
- [[Characteristic Equation and Eigenvalues]] (SESA2027) · [[Eigenvalues and Eigenvectors]] (MATH1054) · [[Routh-Hurwitz Stability Criterion]]
