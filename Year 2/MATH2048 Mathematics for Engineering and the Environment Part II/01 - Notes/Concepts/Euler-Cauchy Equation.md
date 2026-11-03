---
title: "Euler-Cauchy Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 1: Ordinary Differential Equations"
aliases: ["Euler equation (ODE)", "Cauchy-Euler equation", "Equidimensional equation"]
tags: [math2048, concept, odes]
status: complete
parent_lectures: ["[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
related_concepts: ["[[Auxiliary Equation]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf", "02 - Sources/Lectures/MATH2048 Lecture 2.txt"]
---

# Euler-Cauchy Equation

An **Euler** (Euler–Cauchy) equation, $ax^2y''+bxy'+cy=0$ on $x>0$, has each derivative multiplied by the matching power of $x$. Substituting $y=x^n$ gives the auxiliary (indicial) equation $an(n-1)+bn+c=0$, that is, $an^2+(b-a)n+c=0$.

Each derivative lowers the power of $x$ by one and the coefficient restores it, so $x^n$ maps to a multiple of itself, exactly as $e^{\lambda x}$ does for constant coefficients. In the course's framing these equations arise when each term is made dimensionally consistent by powers of the length itself, which is typical of cylindrical and spherical coordinates.

| Roots | $y$ |
|---|---|
| $n_1\neq n_2$ real | $c_1x^{n_1}+c_2x^{n_2}$ |
| $n$ repeated | $x^n(c_1+c_2\ln x)$ |
| $\alpha\pm j\beta$ | $x^\alpha\big[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\big]$ |

The substitution $t=\ln x$ explains the table. It gives $xy'=\dot y$ and $x^2y''=\ddot y-\dot y$, so the equation becomes $a\ddot y+(b-a)\dot y+cy=0$, a constant-coefficient ODE in $t$; then $e^{nt}=x^n$ and $te^{nt}=x^n\ln x$. The usual slips are writing $b$ instead of $b-a$ and forgetting to convert back from $t$ to $x$.

Examples: $x^2y''-6y=0$ gives $n=3,-2$ and $y=c_1x^3+c_2x^{-2}$; $x^2y''+3xy'+10y=0$ gives $n=-1\pm3j$; and the pulsating-star equation $r^2X''+2rX'-\ell(\ell+1)X=0$ gives $X=c_1r^\ell+c_2r^{-(\ell+1)}$, the same pair of powers that appears in Laplace's equation in polar and spherical coordinates.

## Related

- Derivations: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]
- [[Auxiliary Equation]] · practice in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] (PS1 Q2)
