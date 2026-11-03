---
title: "ODE Eigenvalue Problems"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 1: Ordinary Differential Equations"
aliases: ["Eigenfunctions", "Eigenvalue problem", "Sturm-Liouville", "Three-case method"]
tags: [math2048, concept, odes, pdes]
status: complete
parent_lectures: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
related_concepts: ["[[Boundary Value Problems]]", "[[Auxiliary Equation]]", "[[Natural Frequencies and Mode Shapes]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture3_(Eigenvalue Problems).pdf", "02 - Sources/Lectures/MATH2048 Lecture 3.txt"]
---

# ODE Eigenvalue Problems

An **eigenvalue problem** is a homogeneous boundary value problem containing a parameter, such as $y''+\lambda y=0$ with homogeneous boundary conditions. The **eigenvalues** $\lambda_n$ are the values for which a non-trivial solution exists, and the matching solutions $y_n$ are the **eigenfunctions**, each fixed only up to a constant multiple.

The method is to treat the three signs of $\lambda$ separately, because each gives a different form of solution: $\lambda=-k^2<0$ gives $A\cosh kx+B\sinh kx$, $\lambda=0$ gives $c_1+c_2x$, and $\lambda=k^2>0$ gives $c_1\cos kx+c_2\sin kx$. In each case the boundary conditions either force $c_1=c_2=0$, so there are no eigenvalues of that sign, or produce an equation for $k$.

| Conditions on $[0,L]$ | $\lambda_n$ | $y_n$ |
|---|---|---|
| $y=0$, $y=0$ | $(n\pi/L)^2$, $n\geq1$ | $\sin(n\pi x/L)$ |
| $y'=0$, $y'=0$ | $(n\pi/L)^2$, $n\geq0$ | $\cos(n\pi x/L)$, including the constant |
| $y=0$, $y'=0$ | $\big((2n-1)\pi/2L\big)^2$ | $\sin\big((2n-1)\pi x/2L\big)$ |
| $y(0)=0$, $y'(1)+y(1)=0$ | $k_n^2$ with $\tan k=-k$ | $\sin k_nx$ |

The last row is the lecture's example: its eigenvalues have no closed form, but the first is $\lambda_1=k_1^2\approx4.116$, and there is one root in each interval $((n-\frac12)\pi,n\pi)$. The eigenvalues are real and increase without bound, $y_n$ has $n-1$ interior zeros, and eigenfunctions of different eigenvalues are orthogonal and together complete, which is the foundation of Fourier series.

Separation of variables always produces one of these problems, and a vibrating string's mode shapes are exactly these eigenfunctions (compare SESA2029 [[Natural Frequencies and Mode Shapes]]). Exam questions sometimes write $X''-\lambda X=0$, which flips the signs of the cases and gives $\lambda_n=-n^2$.

## Related

- [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] · [[Boundary Value Problems]] · [[Auxiliary Equation]]
