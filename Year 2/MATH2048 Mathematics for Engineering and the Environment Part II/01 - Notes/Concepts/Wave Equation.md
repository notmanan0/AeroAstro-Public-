---
title: "Wave Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["1D wave equation", "Vibrating string", "D'Alembert", "Damped wave equation"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]", "[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]"]
related_concepts: ["[[Separation of Variables]]", "[[PDE Classification]]", "[[Natural Frequencies and Mode Shapes]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture14_Hyperbolic1.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture16_Hyperbolic3.pdf"]
---

# Wave Equation

## Definition

> [!note] Definition
>
> $$y_{tt}=c^2y_{xx},\qquad c=\sqrt{T/\rho}\ \text{(string under tension }T\text{, with mass per unit length }\rho).$$

## Explanation
- **Derivation**: apply Newton's second law to a string element. For small slopes the net vertical force is $T[y_x]_x^{x+\Delta x}$, which gives the equation above ([[MATH2048 PDE1 - Classification of PDEs and the Wave Equation|PDE1]]).
- **Infinite string**: d'Alembert's solution $y=f(x+ct)+g(x-ct)$ is a pair of travelling waves.
- **Fixed ends** at $x=0$ and $L$:

$$y=\sum_{n\ge1}\big[C_n\cos\omega_nt+D_n\sin\omega_nt\big]\sin\frac{n\pi x}{L},\qquad\omega_n=\frac{n\pi c}{L}.$$

  The frequencies are harmonics, $\omega_n=n\omega_1$.
- **Initial data**: $C_n$ are the sine coefficients of $y(x,0)$. $D_n$ are the sine coefficients of $y_t(x,0)$, divided by $\omega_n$.
- **Damped version** (2025/26 exam): $u_{tt}+2\kappa u_t=u_{xx}$. The time ODE becomes $\ddot T+2\kappa\dot T+n^2T=0$, which is under-damped for $n>\kappa$. Its solution is $e^{-\kappa t}\big[\cos\big(\sqrt{n^2-\kappa^2}\,t\big)+\dots\big]$.

## Examples
- Plucked string: $C_n=\dfrac{8h}{n^2\pi^2}\sin\dfrac{n\pi}2$ (PS6 Q1).
- The mode shapes $\sin\frac{n\pi x}L$ are the continuous analogue of structural mode shapes in SESA2029: [[Natural Frequencies and Mode Shapes]].

## Related
- [[Separation of Variables]] · [[PDE Classification]] · [[ODE Eigenvalue Problems]]

## Sources
- Lectures 14–16; PS6
