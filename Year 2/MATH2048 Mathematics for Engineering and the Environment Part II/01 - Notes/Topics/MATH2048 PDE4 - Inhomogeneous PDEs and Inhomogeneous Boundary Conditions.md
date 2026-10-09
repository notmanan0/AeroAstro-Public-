---
title: "MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 13
tags:
  - math2048
  - pdes
  - heat-equation
  - eigenfunction-expansion
aliases: ["MATH2048 Lecture 18", "MATH2048 Lecture 19", "Eigenfunction expansion", "Source terms", "Steady-state subtraction"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE3 - The Heat Equation]]"]
next_topics: ["[[MATH2048 PDE5 - Laplace's Equation]]"]
key_concepts: ["[[Eigenfunction Expansion Method]]", "[[Heat Equation]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture18_Parabolic2.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture19_Parabolic3.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Appendix-PDE_additional slides.pdf"]
---

# MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions

> [!abstract] Summary
> Separation of variables breaks down in two situations. For each, there is a fix.
>
> | Problem | Fix |
> |---|---|
> | A **source** term, $u_t=\kappa^2u_{xx}+F(x,t)$ | **Eigenfunction expansion**: expand both $u$ and $F$ in the eigenfunctions chosen by the (homogeneous) BCs, $u=\sum T_n(t)X_n(x)$ and $F=\sum F_n(t)X_n(x)$. Orthogonality gives one ODE per mode, $\dot T_n+\kappa^2k_n^2T_n=F_n(t)$. |
> | **Inhomogeneous BCs**, $u(0,t)=f_0(t)$, $u(1,t)=f_1(t)$ | **Subtract** a function $y_P$ that already satisfies the BCs (linear in $x$ is enough). Then $v=u-y_P$ has homogeneous BCs, possibly with a new source $-\partial_ty_P$, which you solve by the first fix. |
>
> These methods are universal: they work the same way for wave and Laplace problems.

## Key Concepts
- [[Eigenfunction Expansion Method]] · [[Heat Equation]] · [[Separation of Variables]]

---

## 1. Source terms: the eigenfunction expansion (L18)
Try $u=XT$ in $u_t=u_{xx}+F$. This gives $\frac{\dot T}{T}=\frac{X''}{X}+\frac{F}{XT}$, which does **not** separate.

**Guess** instead. With Dirichlet BCs $u(0)=u(1)=0$, the eigenfunctions are $\sin n\pi x$ (Neumann BCs would give $\cos n\pi x$). So write

$$
u=\sum_nT_n(t)\sin n\pi x,\qquad F=\sum_nF_n(t)\sin n\pi x,\qquad F_n(t)=2\int_0^1F(x,t)\sin n\pi x\,dx .
$$

Substitute into the PDE:

$$
\sum_n\big[\dot T_n+(n\pi)^2T_n-F_n\big]\sin n\pi x=0\quad\forall x .
$$

The $\sin n\pi x$ are orthogonal (multiply by $\sin m\pi x$ and integrate), so **each bracket vanishes separately**:

$$
\boxed{\dot T_n+(n\pi)^2T_n=F_n(t)}
$$

**Solving this first-order linear ODE** (integrating factor $e^{(n\pi)^2t}$):

$$
\frac{d}{dt}\Big(e^{(n\pi)^2t}T_n\Big)=e^{(n\pi)^2t}F_n\quad\Longrightarrow\quad T_n(t)=e^{-(n\pi)^2t}\Big[C_n+\int e^{(n\pi)^2t}F_n(t)\,dt\Big].
$$

*Lecture derivation*: variation of parameters. Set $T_P=T_H\int P\,dt$; substituting gives $P=F_n/T_H$, which is the same result.

### Example (L18): $y_t=y_{xx}+x(1-x)$, $y(0,t)=y(1,t)=0$, $y(x,0)=x(1-x)$
1. **Expand the source.** $F_n=\dfrac{4[1-(-1)^n]}{(n\pi)^3}$. This is the same integral as PDE2 Example 1, and here $F_n$ is constant in time.
2. **Solve for $T_n$.** $\dot T_n+(n\pi)^2T_n=F_n$ gives

$$T_n=C_ne^{-(n\pi)^2t}+\frac{F_n}{(n\pi)^2}.$$

   The second term is the steady particular integral.
3. **Apply the initial data.** At $t=0$, $\sum(C_n+F_n/(n\pi)^2)\sin n\pi x=x(1-x)=\sum F_n\sin n\pi x$. So $C_n=F_n\big(1-\frac1{(n\pi)^2}\big)$.
4. **Result.**

$$
\boxed{y(x,t)=\sum_{n\ \mathrm{odd}}\frac{8}{(n\pi)^5}\Big[\big((n\pi)^2-1\big)e^{-(n\pi)^2t}+1\Big]\sin n\pi x}
$$

5. **Late time.** The "$+1$" term, which comes from the source, survives:

$$y\to\sum\frac{8}{(n\pi)^5}\sin n\pi x=\frac{x-2x^3+x^4}{12}.$$

   This is the steady state, the solution of $y''=-x(1-x)$ with $y=0$ at both ends ✔.
6. **Numerical checks.** The series satisfies the PDE to a residual of $3\times10^{-8}$ and the initial condition to $10^{-8}$ ✔.

![[m2048_pde_inhomogeneous_heat.png|640]]

## 2. Inhomogeneous boundary conditions (L19)
**Constant BCs** $u(0,t)=T_0$, $u(1,t)=T_1$. The steady state solves $u''=0$, so it is $y_P=T_0+(T_1-T_0)x$. Set $u=v+y_P$. Then $v$ solves the homogeneous PDE with $v(0)=v(1)=0$ and the adjusted initial data $v(x,0)=u(x,0)-y_P(x)$.

**Time-dependent BCs** $u(0,t)=f_0(t)$, $u(1,t)=f_1(t)$. Use

$$
y_P(x,t)=f_0(t)+\big[f_1(t)-f_0(t)\big]x .
$$

This does *not* solve the PDE: it only matches the BCs. Setting $u=v+y_P$, and using $\partial_x^2y_P=0$,

$$
v_t=\kappa^2v_{xx}-\partial_ty_P,\qquad v(0,t)=v(1,t)=0,\qquad v(x,0)=u(x,0)-y_P(x,0).
$$

The BC forcing has become a **source term**, which §1 handles.

### Example (L19): $y_t=y_{xx}$, $y(0,t)=\frac12(1-\cos t)$, $y(1,t)=0$, $y(x,0)=0$
1. **Particular function.** $y_P=\frac12(1-x)(1-\cos t)$, so $\partial_ty_P=\frac12(1-x)\sin t$.
2. **Problem for $v$.** $v_t=v_{xx}-\frac12(1-x)\sin t$, with $v=0$ at both ends and $v(x,0)=0$ (because $y_P(x,0)=0$).
3. **Expand the source.**

$$F_n=2\int_0^1\big(-\tfrac12\big)(1-x)\sin t\,\sin n\pi x\,dx=-\frac{\sin t}{n\pi},$$

   using $\int_0^1(1-x)\sin n\pi x\,dx=\frac1{n\pi}$.
4. **Solve for $T_n$.** Solve $\dot T_n+(n\pi)^2T_n=-\frac{\sin t}{n\pi}$ with $T_n(0)=0$. The integral $\int e^{at}\sin t\,dt=\frac{e^{at}(a\sin t-\cos t)}{1+a^2}$, with $a=(n\pi)^2$, gives

$$T_n=\frac{\cos t-(n\pi)^2\sin t-e^{-(n\pi)^2t}}{n\pi\,[1+(n\pi)^4]}$$

   This matches the slide exactly (SymPy `dsolve`) ✔.
5. **Result.**

$$
y=\frac12(1-x)(1-\cos t)+\sum_{n=1}^\infty\frac{\cos t-(n\pi)^2\sin t-e^{-(n\pi)^2t}}{n\pi\,[1+(n\pi)^4]}\sin n\pi x .
$$

   At late times the boundary forcing dominates, and the transient $e^{-(n\pi)^2t}$ dies away.

## 3. Other reductions
- **Decay term** (PS7 Q2): for $u_t=h^2u_{xx}-ku$, set $u=e^{-kt}v$. Then $v_t=h^2v_{xx}$, the plain heat equation.
- **Switched source** (PS7 Q3): $F=f(\tau-t)\sin^2\pi x$ with $f=1-H(t-\tau)$.
  - First write $\sin^2\pi x=\frac12-\frac12\cos2\pi x$. Only the $n=0$ and $n=2$ cosine modes are forced.
  - Then solve each $T_n$ ODE separately for $t<\tau$ and $t>\tau$. A Laplace transform in $t$ also works.
- **Mixed BCs** (PS7 Q4): with $u(0)=0$ and $u_x(1)=C$, subtract $y_P=Cx$. The eigenfunctions are then $\sin(n-\frac12)\pi x$.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE3 - The Heat Equation]] · Next: [[MATH2048 PDE5 - Laplace's Equation]]
- Practice: [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] (PS7 Q2–4)

## Sources
- Lectures 18–19; PDE Appendix; Lecture Notes §6.5. $T_n$ checked with SymPy `dsolve`; the series were checked numerically against the PDE and ICs.
