---
title: "Separation of Variables"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Six-step method", "Normal modes", "Product solution"]
tags: [math2048, concept, pdes, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]", "[[MATH2048 PDE3 - The Heat Equation]]", "[[MATH2048 PDE5 - Laplace's Equation]]"]
related_concepts: ["[[ODE Eigenvalue Problems]]", "[[Half-Range Expansions]]", "[[Wave Equation]]", "[[Heat Equation]]", "[[Laplace's Equation]]", "[[Eigenfunction Expansion Method]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture15_Hyperbolic2.pdf", "02 - Sources/Lectures/MATH2048 Lecture 15.txt", "02 - Sources/Lectures/MATH2048 Lecture 16.txt"]
---

# Separation of Variables

**Separation of variables** solves a linear homogeneous PDE by looking for product solutions such as $u=X(x)T(t)$, finding which products work, and adding them all up.

Substituting the product and dividing by it leaves a function of one variable equal to a function of another. Fixing either variable shows both must equal the same constant $\lambda$, so the PDE splits into ODEs coupled only through $\lambda$. The boundary conditions on $u$ become conditions on $X$, because the alternative is $T\equiv0$, and the spatial ODE with those conditions is an eigenvalue problem: non-zero solutions exist only for special $\lambda_n$. Each of the cases $\lambda=0$, $\lambda>0$ and $\lambda<0$ must be checked, since which ones survive depends on the boundary conditions.

The lecture's six steps are: separate; turn the boundary conditions into conditions on $X$; solve the eigenvalue problem; solve for $T_n$ with each $\lambda_n$; superpose $\sum X_nT_n$; and fit the initial data, which is a Fourier series problem. Step 1 depends only on the PDE and step 2 only on the boundary conditions, so changing one leaves the other alone.

| Boundary conditions on $[0,L]$ | $\lambda_n$ | $X_n$ |
|---|---|---|
| $u=0$ at both ends | $-(n\pi/L)^2$, $n\geq1$ | $\sin\frac{n\pi x}L$ |
| $u_x=0$ at both ends | $-(n\pi/L)^2$, $n\geq0$ | $\cos\frac{n\pi x}L$ (constant for $n=0$) |
| $u=0$ at $0$, $u_x=0$ at $L$ | $-\big((n-\frac12)\pi/L\big)^2$, $n\geq1$ | $\sin\frac{(n-\frac12)\pi x}L$ |

The time part distinguishes the PDEs: $\cos$ and $\sin$ for the wave equation, a decaying exponential for the heat equation, and $\cosh$ and $\sinh$ in the second space direction for Laplace's equation. The method needs a linear PDE and one pair of homogeneous boundary conditions; sources and non-zero boundary values are handled by the [[Eigenfunction Expansion Method]].

## Related

- [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]] · [[MATH2048 PDE3 - The Heat Equation]] · [[MATH2048 PDE5 - Laplace's Equation]]
- [[ODE Eigenvalue Problems]] · [[Half-Range Expansions]] · [[Eigenfunction Expansion Method]]
