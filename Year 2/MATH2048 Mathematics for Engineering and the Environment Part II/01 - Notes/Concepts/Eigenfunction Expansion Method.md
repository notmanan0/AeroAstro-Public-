---
title: "Eigenfunction Expansion Method"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Series solution for inhomogeneous PDEs", "Source term expansion", "Steady-state subtraction"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
related_concepts: ["[[Separation of Variables]]", "[[Heat Equation]]", "[[Orthogonality of Trigonometric Functions]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture18_Parabolic2.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture19_Parabolic3.pdf"]
---

# Eigenfunction Expansion Method

## Definition

> [!note] Definition
> Consider $u_t=\kappa^2u_{xx}+F(x,t)$ with homogeneous BCs. Expand
>
> $$u=\sum T_n(t)X_n(x),\qquad F=\sum F_n(t)X_n(x),$$
>
> where the $X_n$ are the eigenfunctions selected by the BCs. Orthogonality then decouples the modes:
>
> $$\dot T_n+\kappa^2k_n^2T_n=F_n(t),\qquad T_n=e^{-\kappa^2k_n^2t}\Big[C_n+\int e^{\kappa^2k_n^2t}F_n\,dt\Big].$$

## Explanation
**Why it works**: $\sum_n[\dots]_nX_n=0$ for all $x$ forces every bracket to be zero, because the $X_n$ are orthogonal.

**Inhomogeneous BCs**: first subtract $y_P=f_0(t)+[f_1(t)-f_0(t)]x$. The new variable $v$ then has homogeneous BCs and picks up an extra source $-\partial_ty_P$.

**Other variants**:
- For Neumann-type BCs, subtract a function that matches them. For example, $u(0)=0$ with $u_x(1)=C$ uses $y_P=Cx$.
- A decay term $-ku$ is removed with $u=e^{-kt}v$.

## Examples
- $y_t=y_{xx}+x(1-x)$ with Dirichlet BCs:

$$y=\sum_{\text{odd}}\frac{8}{(n\pi)^5}\big[((n\pi)^2-1)e^{-(n\pi)^2t}+1\big]\sin n\pi x\ \to\ \frac{x-2x^3+x^4}{12}\ \text{as }t\to\infty.$$

- $y(0,t)=\frac12(1-\cos t)$ gives $F_n=-\sin t/(n\pi)$ ([[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions|PDE4]]).

## Related
- [[Separation of Variables]] · [[Heat Equation]] · [[Method of Undetermined Coefficients]] (the ODE analogue)

## Sources
- Lectures 18–19; PS7 Q3–4
