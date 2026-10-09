---
title: "Laplace's Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Harmonic function", "Maximum principle", "Potential equation"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE5 - Laplace's Equation]]"]
related_concepts: ["[[Separation of Variables]]", "[[Streamfunction and Velocity Potential]]", "[[Divergence, Curl and the Laplacian]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture20_LaplaceEquation1.pdf"]
---

# Laplace's Equation

## Definition

> [!note] Definition
> $$\nabla^2u=u_{xx}+u_{yy}(+u_{zz})=0 .$$
> This is elliptic. Its solutions are called **harmonic** functions.

## Explanation
**Maximum principle**: the maximum and minimum values of $u$ occur on the boundary. So if every BC is zero, $u\equiv0$.

**Separation on a rectangle**: substituting $X''Y+XY''=0$ gives the **opposite-sign** pair $X''=\lambda X$ and $Y''=-\lambda Y$.
- The direction with homogeneous BCs gives sines/cosines, e.g. $X_n=\sin n\pi x$.
- The other direction then gives $\cosh$ and $\sinh$.

**Several non-zero sides**:
1. Subtract a corner-fixing function $\alpha_1+\alpha_2x+\alpha_3y+\alpha_4xy$.
2. Split the problem so that each piece has one non-zero side.
3. Solve each piece and superpose.

**Disk (polar coordinates)**: $\phi=\frac12a_0+\sum r^n(a_n\cos n\theta+b_n\sin n\theta)$.

**Links**:
- Potential flow: $\nabla^2\phi=\nabla^2\psi=0$ ([[Streamfunction and Velocity Potential]]).
- Steady heat conduction.
- Gravitational and electrostatic potentials.
- In vector calculus, $\nabla^2=\nabla\cdot\nabla$ ([[Divergence, Curl and the Laplacian]]).

## Examples
- With $u=x(1-x)$ on $y=1$ and $u=0$ on the other sides:
$$u=\sum_{n\ \text{odd}}\frac{8\sin n\pi x\sinh n\pi y}{(n\pi)^3\sinh n\pi}.$$

![[m2048_pde_laplace_square.png|480]]

## Related
- [[Separation of Variables]] · [[Heat Equation]] · [[PDE Classification]]

## Sources
- Lecture 20; Lecture Notes Ch. 7
