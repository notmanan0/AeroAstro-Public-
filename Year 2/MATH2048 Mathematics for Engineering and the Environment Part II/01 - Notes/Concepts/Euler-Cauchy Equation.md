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
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf"]
---

# Euler-Cauchy Equation

## Definition

> [!note] Definition
>
> $$ax^2y''+bxy'+cy=0,\qquad x>0 .$$
>
> Substituting $y=x^n$ gives the **indicial equation** $an(n-1)+bn+c=0$, i.e. $an^2+(b-a)n+c=0$.

## Explanation
Each derivative lowers the power of $x$ by one, and the coefficient $x^k$ restores it. So $x^n$ maps to a multiple of $x^n$, just as $e^{\lambda x}$ does for constant coefficients.

| Roots | $y$ |
|---|---|
| $n_1\neq n_2$ real | $c_1x^{n_1}+c_2x^{n_2}$ |
| $n$ repeated | $x^n(c_1+c_2\ln x)$ |
| $\alpha\pm j\beta$ | $x^\alpha\big[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\big]$ |

**The substitution** $t=\ln x$ gives $xy'=\dot y$ and $x^2y''=\ddot y-\dot y$. So the equation becomes $a\ddot y+(b-a)\dot y+cy=0$, a constant-coefficient ODE. This substitution *proves* the repeated and complex rows of the table: $te^{nt}=x^n\ln x$.

> [!warning] Common slips
> - Using $b$ instead of $b-a$ as the middle coefficient.
> - Forgetting to convert back from $t$ to $x$.

## Examples
- $x^2y''-6y=0$: $n^2-n-6=0$ gives $n=3,-2$, so $y=c_1x^3+c_2x^{-2}$.
- $x^2y''+3xy'+10y=0$: $n=-1\pm3j$, so $y=x^{-1}\big[c_1\cos(3\ln x)+c_2\sin(3\ln x)\big]$.
- $r^2X''+2rX'-\ell(\ell+1)X=0$ gives $X=c_1r^\ell+c_2r^{-(\ell+1)}$ (pulsating star; also Laplace's equation in spherical and polar coordinates).

## Related
- [[Auxiliary Equation]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] (PS1 Q2)

## Sources
- Lecture 2; Appendix L1–2; Lecture Notes §1.1.1
