---
title: "Matrix Exponential and Modal Solution"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 5: State-Space Models"
aliases: ["matrix exponential", "state-transition matrix", "expm", "modal solution", "eigenvalue stability criterion"]
tags: [sesa3047, concept, state-space, stability, eigenvalues]
status: complete
coverage: "Chapter 5 §5.7, lectured in L16 (Thu 5 Nov)"
parent_lectures: ["[[SESA3047 5.4 - Time-Domain Solution and Stability]]"]
related_concepts: ["[[Eigenvalue Decomposition]]", "[[Characteristic Equation and Eigenvalues]]", "[[Eigenvalues and Eigenvectors]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Chapter_5.pdf", "02 - Sources/Lectures/05 November 2026 at 15_56_57.txt"]
---

# Matrix Exponential and Modal Solution

The free linear system $\dot{\mathbf x}=\mathbf A\mathbf x$ has the solution $\mathbf x(t)=e^{\mathbf At}\mathbf x_0$, where $e^{\mathbf At}=\mathbf I+\mathbf At+(\mathbf At)^2/2!+\cdots$ is the matrix exponential, not the exponential of each entry.

When $\mathbf A$ has a full set of eigenvectors, the [[Eigenvalue Decomposition]] gives $\mathbf A=\mathbf V\boldsymbol\Lambda\mathbf V^{-1}$ and every power is $\mathbf A^k=\mathbf V\boldsymbol\Lambda^k\mathbf V^{-1}$, so the series collapses to

$$
\mathbf x(t)=\mathbf Ve^{\boldsymbol\Lambda t}\mathbf V^{-1}\mathbf x_0=\sum_ic_ie^{\lambda_it}\mathbf v_i,\qquad\mathbf c=\mathbf V^{-1}\mathbf x_0 .
$$

Each term is a mode: its eigenvector is the shape, its eigenvalue the time behaviour. The imaginary part of $\lambda$ sets the oscillation frequency and the real part alone sets growth or decay, so one eigenvalue with a positive real part is enough to make the system unstable. The poles of a transfer function are the same numbers as the eigenvalues of $\mathbf A$, so this is the Year 2 right-half-plane rule in matrix form. The system is asymptotically stable exactly when every eigenvalue has a negative real part, and unstable if any has a positive real part. Eigenvalues on the imaginary axis are marginal if they are simple, but a repeated one without enough eigenvectors (a Jordan block) adds a $te^{\lambda t}$ term. The satellite of Chapter 5, with a double zero eigenvalue and one eigenvector, drifts without bound for this reason.

As a check, $e^{\mathbf A}$ for $\mathbf A=[1\ 2;\ 3\ 4]$ is $[51.97\ 74.74;\ 112.10\ 164.07]$, not $[e^1\ e^2;\ e^3\ e^4]$. Exponentiating entry by entry is correct only for the diagonal entries of a diagonal matrix, whose off-diagonal zeros stay zero. For the triangular $\mathbf A=[3\ 2;\ 0\ {-1}]$, $e^{\mathbf At}=[e^{3t}\ \ \tfrac12(e^{3t}-e^{-t});\ 0\ \ e^{-t}]$, which grows because of the eigenvalue 3.

## Related

- [[SESA3047 5.4 - Time-Domain Solution and Stability]] · [[Eigenvalue Decomposition]] · [[Eigenvectors as Mode Shapes]] (what each term looks like: [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]])
- [[Characteristic Equation and Eigenvalues]] (SESA2027) · [[Eigenvalues and Eigenvectors]] (MATH1054) · [[Routh-Hurwitz Stability Criterion]]
