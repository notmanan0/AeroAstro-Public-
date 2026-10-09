---
title: "MATH2048 PDE5 - Laplace's Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 14
tags:
  - math2048
  - pdes
  - laplace-equation
  - elliptic
aliases: ["MATH2048 Lecture 20", "Harmonic functions", "Maximum principle"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
next_topics: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]"]
key_concepts: ["[[Laplace's Equation]]", "[[Separation of Variables]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture20_LaplaceEquation1.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 7)"]
---

# MATH2048 PDE5 - Laplace's Equation

> [!abstract] Summary
> $\nabla^2u=u_{xx}+u_{yy}=0$ describes **steady states**: it is the $t\to\infty$ limit of the heat equation. It needs **one condition on every boundary** and no initial data.
>
> The **maximum principle** says the extreme values of $u$ occur on the boundary. So homogeneous BCs everywhere force $u\equiv0$, and all the interesting solutions come from inhomogeneous BCs.
>
> **Method**:
> 1. Separate $u=X(x)Y(y)$.
> 2. Solve the eigenproblem in the direction that has two homogeneous BCs.
> 3. The other direction gives $\cosh$/$\sinh$, **not** $\cos$/$\sin$.
> 4. Fit the one inhomogeneous side with a Fourier series.
> 5. If several sides are inhomogeneous, split the problem into one sub-problem per side and **superpose**.

## Key Concepts
- [[Laplace's Equation]] · [[Separation of Variables]] · [[Half-Range Expansions]]

---

## 1. Setup and boundary conditions (L20)
- $\nabla^2u=0$ in 2D or 3D. Solutions are called **harmonic functions**.
- Every boundary needs exactly one condition, of Dirichlet ($u$), Neumann ($\partial_nu$) or mixed type.
- **Link to fluid dynamics**: SESA2022 potential flow ($\nabla^2\phi=0$, $\nabla^2\psi=0$) is exactly this equation. See [[Streamfunction and Velocity Potential]].

**What $\phi$ represents (Lecture Notes §7.1)**:
- In 1D, $\phi''=0$: the static shape of a taut string, or the steady temperature in a bar.
- In 2D: a stretched membrane (a soap film), or the steady temperature in a conducting sheet.
- In 3D: the steady temperature in a solid, the **velocity potential of an inviscid flow**, the electrostatic potential in a charge-free region, or the gravitational potential in a mass-free region.

In each case $\phi$ is the *potential* and $\mathbf F=\pm\nabla\phi$ is the corresponding *field*. The boundary data is either $\phi$ itself (Dirichlet) or $\hat{\mathbf n}\cdot\nabla\phi$ (Neumann), given at every point of the boundary.

**How this differs from wave and heat problems**: here *both* separated ODEs are boundary-value problems. For the wave and heat equations, only the spatial one is.

## 2. All boundaries homogeneous: only $u\equiv0$ (L20)
On the unit square, with $u=0$ on all four sides:
- Separating gives $X''-\lambda X=0$ and $Y''+\lambda Y=0$. Note the **opposite signs**, which come from $X''Y+XY''=0$.
- $X(0)=X(1)=0$ gives $X_n=\sin n\pi x$ and $\lambda_n=-(n\pi)^2$.
- Then $Y''-(n\pi)^2Y=0$, so $Y_n=a_ne^{n\pi y}+b_ne^{-n\pi y}$.
- $Y_n(0)=0$ gives $b_n=-a_n$. Then $Y_n(1)=a_n(e^{n\pi}-e^{-n\pi})=0$, so $a_n=0$.

So $u\equiv0$, just as the maximum principle predicts.

## 3. One inhomogeneous side (L20)
BCs: $u(0,y)=u(1,y)=0$, $u(x,0)=0$ and $u(x,1)=x(1-x)$.
1. **$x$-direction** (two homogeneous BCs): $X_n=\sin n\pi x$, the same as before.
2. **$y$-direction**: write $Y_n=\alpha_n\cosh n\pi y+\beta_n\sinh n\pi y$. The cosh/sinh form is easier here because $\cosh0=1$ and $\sinh0=0$. Then $Y_n(0)=0$ gives $\alpha_n=0$.
3. **Superpose**: $u=\sum\beta_n\sinh(n\pi y)\sin(n\pi x)$.
4. **Fit the top edge**: $x(1-x)=\sum\underbrace{\beta_n\sinh n\pi}_{B_n}\sin n\pi x$. This is a sine series, so $B_n=\frac{4[1-(-1)^n]}{(n\pi)^3}$.

$$
\boxed{u(x,y)=\sum_{n\ \mathrm{odd}}\frac{8}{(n\pi)^3\sinh n\pi}\sin(n\pi x)\sinh(n\pi y)}
$$

**Checks**: the series reproduces the top BC to $10^{-7}$. Its interior values, e.g. $u(0.5,0.9)=0.185$, stay below the boundary maximum of $0.25$ ✔ (maximum principle).

![[m2048_pde_laplace_square.png|520]]

> [!tip] Use $\sinh$ around the zero edge
> If the zero BC is at $y=b$ rather than $y=0$, write $Y_n=\sinh\big(n\pi(b-y)\big)$ so that it vanishes automatically. This saves algebra.

## 4. Several inhomogeneous sides (Notes §7.2.1)
1. **Corners.** Subtract a difference function $v=\alpha_1+\alpha_2x+\alpha_3y+\alpha_4xy$, which is harmonic. Choose it to match the four corner values, so the remaining BCs vanish at the corners.
2. **Split.** Write $u=u_1+u_2+u_3+u_4$, where each $u_i$ carries one side's BC and is zero on the other three sides.
3. **Solve and add.** Solve each $u_i$ as in §3, then add them.

This works because Laplace's equation is **linear**.

**Other domains** (disk or annulus, polar coordinates):
- The equation becomes $\frac1r(r\phi_r)_r+\frac{1}{r^2}\phi_{\theta\theta}=0$.
- $2\pi$-periodicity in $\theta$ gives $\cos n\theta$ and $\sin n\theta$.
- The radial part is an Euler equation (Block 1), with solutions $r^{\pm n}$. Finiteness at $r=0$ keeps only $r^n$:

$$
\phi=\tfrac12a_0+\sum r^n(a_n\cos n\theta+b_n\sin n\theta) .
$$

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]] · Next: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]
- Related: [[Euler-Cauchy Equation]] (polar radial part) · SESA2022 [[Elementary Potential Flows]]

## Sources
- Lecture 20; Lecture Notes Ch. 7. Coefficients verified in SymPy; series checked numerically.
