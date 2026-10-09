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
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture3_(Eigenvalue Problems).pdf"]
---

# ODE Eigenvalue Problems

## Definition

> [!note] Definition
> A homogeneous BVP containing a parameter, e.g. $y''+\lambda y=0$ with homogeneous BCs. The values $\lambda_n$ for which a **non-trivial** solution exists are the **eigenvalues**. The solutions $y_n$ are the **eigenfunctions**, which are unique only up to a constant multiple.

## Explanation
**Three-case method**:

| Case | General solution |
|---|---|
| $\lambda=-k^2<0$ | $A\cosh kx+B\sinh kx$ |
| $\lambda=0$ | $c_1x+c_2$ |
| $\lambda=k^2>0$ | $c_1\sin kx+c_2\cos kx$ |

In each case impose the BCs. Either you get only $c_1=c_2=0$, or you get an equation for $k$.

| BCs on $[0,L]$ | $\lambda_n$ | $y_n$ |
|---|---|---|
| $y=0$, $y=0$ | $(n\pi/L)^2$, $n\geq1$ | $\sin(n\pi x/L)$ |
| $y'=0$, $y'=0$ | $(n\pi/L)^2$, $n\geq0$ | $\cos(n\pi x/L)$ (incl. constant) |
| $y=0$, $y'=0$ | $\big((2n-1)\pi/2L\big)^2$ | $\sin\big((2n-1)\pi x/2L\big)$ |
| $y(0)=0$, $y'(1)+y(1)=0$ | $k_n^2$ with $\tan k=-k$ | $\sin k_nx$ |

**Properties**:
- the eigenvalues are real and increase to $\infty$;
- eigenfunctions of distinct eigenvalues are orthogonal;
- $y_n$ has $n-1$ interior zeros;
- the set is complete, which is the basis of **Fourier series**.

> [!important] In PDE questions
> Separation of variables always produces one of these. Watch the sign convention: $X''-\lambda X=0$ flips the cases, giving $\lambda_n=-n^2$.

## Examples
- PS2 Q3: $\lambda_n=n^2$ with $\sin nx$, and $\lambda_n=(n-\tfrac12)^2$ with $\sin(n-\tfrac12)x$.
- A vibrating string's mode shapes are these eigenfunctions. Compare SESA2029 [[Natural Frequencies and Mode Shapes]].

## Related
- [[Boundary Value Problems]] · [[Auxiliary Equation]] · [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]

## Sources
- Lecture 3; Appendix L3; Lecture Notes §1.2.1–1.2.2
