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
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture18_Parabolic2.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture19_Parabolic3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 18.txt", "02 - Sources/Lectures/MATH2048 Lecture 19.txt"]
---

# Eigenfunction Expansion Method

The **eigenfunction expansion** solves a linear PDE with a source, such as $y_t=\kappa^2y_{xx}+F(x,t)$, by writing both the solution and the source as series in the eigenfunctions of the homogeneous problem, $y=\sum T_n(t)X_n(x)$ and $F=\sum F_n(t)X_n(x)$.

Plain separation fails with a source, because $F/(XT)$ depends on both variables. The eigenfunctions still satisfy the homogeneous boundary conditions, though, so any sum of them does too. Substituting both series and using uniqueness of the Fourier series gives one ODE per mode, $\dot T_n+(n\pi\kappa)^2T_n=F_n(t)$ on $[0,1]$, solved by an integrating factor or undetermined coefficients. The solution typically has a part that balances the source and transients that decay; for a steady source the balancing part is the steady state.

Non-zero boundary values are removed first. Subtract any function $y_p$ that satisfies them, usually the straight line between the end values. Then $v=y-y_p$ has homogeneous boundary conditions, initial data $y(x,0)-y_p(x,0)$, and a source $-\partial_ty_p$ (plus $\kappa^2\partial_x^2y_p$ if $y_p$ is not linear). For constant end values $y_p$ is the steady state and no source appears; for time-dependent ones a source does, and the solution is forced for ever.

## Related

- [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]
- [[Separation of Variables]] · [[Heat Equation]] · [[Method of Undetermined Coefficients]]
