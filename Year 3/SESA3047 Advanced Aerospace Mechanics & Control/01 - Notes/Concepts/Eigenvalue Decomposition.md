---
title: "Eigenvalue Decomposition"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 5: State-Space Models"
aliases: ["eigenvalue decomposition", "eigendecomposition", "diagonalisation", "modal decomposition", "spectral decomposition", "A = V Lambda V^-1"]
tags: [sesa3047, concept, state-space, eigenvalues, linear-algebra]
status: complete
coverage: "Chapter 5 §5.7, lectured in L16 (Thu 5 Nov) with the triangular-matrix example"
parent_lectures: ["[[SESA3047 5.4 - Time-Domain Solution and Stability]]"]
related_concepts: ["[[Matrix Exponential and Modal Solution]]", "[[Eigenvalues and Eigenvectors]]", "[[Characteristic Equation and Eigenvalues]]"]
sources: ["02 - Sources/Lectures/Chapter_5.pdf", "02 - Sources/Lectures/05 November 2026 at 15_56_57.txt"]
---

# Eigenvalue Decomposition

The eigenvalue decomposition writes a square matrix as $\mathbf A=\mathbf V\boldsymbol\Lambda\mathbf V^{-1}$, with the eigenvectors of $\mathbf A$ as the columns of $\mathbf V$ and the matching eigenvalues on the diagonal of $\boldsymbol\Lambda$.

It exists only for an $n\times n$ matrix, and only when $\mathbf A$ has $n$ independent eigenvectors so that $\mathbf V$ can be inverted. Distinct eigenvalues guarantee this; a repeated eigenvalue may or may not supply enough eigenvectors, and when it does not the matrix is defective and needs a Jordan form instead. The decomposition follows from $\mathbf A\mathbf v_i=\lambda_i\mathbf v_i$ written for all columns at once, $\mathbf A\mathbf V=\mathbf V\boldsymbol\Lambda$, multiplied on the right by $\mathbf V^{-1}$.

To compute it by hand, solve $\det(\mathbf A-\lambda\mathbf I)=0$ for the eigenvalues, then solve $(\mathbf A-\lambda_i\mathbf I)\mathbf v_i=\mathbf 0$ for each eigenvector. That system is singular by construction ($\det(\mathbf A-\lambda_i\mathbf I)=0$), so at least one component is free; for a simple eigenvalue exactly one is, and it is usually set to 1. Check each vector by multiplying it by $\mathbf A$. For a triangular matrix the eigenvalues are the main-diagonal entries, because the determinant of a triangular matrix is the product of its diagonal. The triangular matrix $[3\ 2;\ 0\ {-1}]$ (L16) gives $\lambda=3,-1$ with $\mathbf v_1=[1,0]^T$ and $\mathbf v_2=[1,-2]^T$, so $\mathbf V=[1\ 1;\ 0\ {-2}]$ and $\mathbf V^{-1}=[1\ \tfrac12;\ 0\ {-\tfrac12}]$.

Eigenvectors are fixed only up to scale and sign. MATLAB and Python return unit-length vectors, so $[1,-2]^T$ comes back as $\pm[0.447,-0.894]^T$; $\mathbf V$ changes but $\mathbf V\boldsymbol\Lambda\mathbf V^{-1}$ does not.

The decomposition leads from $\dot{\mathbf x}=\mathbf A\mathbf x$ to its solution: because $\mathbf A^k=\mathbf V\boldsymbol\Lambda^k\mathbf V^{-1}$, the matrix exponential becomes $\mathbf Ve^{\boldsymbol\Lambda t}\mathbf V^{-1}$, in which every eigenvalue acts as an independent mode $e^{\lambda_it}$ ([[Matrix Exponential and Modal Solution]]). For an aircraft those modes are the phugoid, short-period, Dutch roll, roll subsidence and spiral.

## Related

- [[SESA3047 5.4 - Time-Domain Solution and Stability#6. Worked example: eigenvectors of a triangular matrix|5.4 §6, worked example]] · [[Matrix Exponential and Modal Solution]]
- [[Eigenvalues and Eigenvectors]] (MATH1054) · [[Characteristic Equation and Eigenvalues]] (SESA2027)
