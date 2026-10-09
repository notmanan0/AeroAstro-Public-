---
title: "SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 5
tags:
  - sesa2029
  - cfd
  - numerical-methods
  - stability
aliases: ["Numerical stability", "Von Neumann stability", "Amplification factor"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
next_topics: ["[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]"]
key_concepts: ["[[Von Neumann Stability Analysis]]", "[[CFL and Fourier Numbers]]", "[[Explicit and Implicit Time Integration]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L6, pp. 77–86)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers

> [!abstract] Summary
> **Stability** asks whether errors grow from one step to the next. Define the **gain** $G = |f^{n+1}/f^n|$: $G>1$ is unstable, $G<1$ decays and $G = 1$ is neutral.
>
> **For the ODE $f' = \lambda f$**:
> - explicit Euler is stable only **inside** the unit circle centred at $\lambda\Delta t = -1$;
> - implicit Euler is stable everywhere **outside** the unit circle centred at $+1$.
>
> **For a PDE (von Neumann analysis)**, substitute a Fourier mode $T_j = e^{ikx_j}$, find $G(kh)$, and take the worst wave, $kh = \pi$. This gives:
> - heat equation, FTCS: $F = \alpha\Delta t/h^2\le\tfrac12$;
> - convection equation, explicit upwind: $C = c\Delta t/h\le1$ (the **CFL condition**).

## Key Concepts
- [[Von Neumann Stability Analysis]] · [[CFL and Fourier Numbers]] · [[Explicit and Implicit Time Integration]]

---

## 1. Stability of the model ODE (L6)
The model equation is $df/dt = \lambda f$ with $\lambda = \sigma+i\omega$.

**Explicit Euler**:

$$
\frac{f^{n+1}-f^n}{\Delta t} = \lambda f^n\;\Rightarrow\;f^{n+1} = (1+\lambda\Delta t)f^n,\qquad G = |1+\lambda\Delta t|
$$

Setting $G = 1$ and squaring the real and imaginary parts gives $1 = (1+\sigma\Delta t)^2+(\omega\Delta t)^2$. This is a **circle of radius 1 centred at $(\sigma\Delta t,\omega\Delta t) = (-1,0)$**, with $G = 0$ at its centre. The method is stable **only inside** the circle.

**Implicit Euler**:

$$
\frac{f^{n+1}-f^n}{\Delta t} = \lambda f^{n+1}\;\Rightarrow\;f^{n+1}(1-\lambda\Delta t) = f^n,\qquad G = \frac{1}{|1-\lambda\Delta t|}
$$

$G = 1$ gives $1 = (1-\sigma\Delta t)^2+(\omega\Delta t)^2$: a circle centred at $(+1,0)$, with $G = \infty$ at its centre. The method is stable **everywhere outside** the circle.

**Interpretation**:
- The *true* solution decays whenever $\sigma<0$, i.e. in the whole left half-plane.
- **Explicit Euler** covers only a small disc of that half-plane. A physically decaying mode with $|\lambda|\Delta t$ too large is computed as a *growing* one: numerical garbage.
- **Implicit Euler** is stable for every $\sigma<0$ and every $\Delta t$. It even damps some physically growing modes (in the right half-plane outside the circle). That is stability without correctness.
- Neither Euler scheme is stable on the imaginary axis ($\sigma = 0$, pure waves) except trivially. That motivates RK3 and RK4 (see A6).

![[dam_stability_regions.png|520]]

## 2. Von Neumann analysis of the heat equation (L6)
Start from the explicit FTCS scheme $T_j^{n+1} = T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)$. Any smooth error distribution is a sum of Fourier waves, so test one: $T_j = e^{ikx_j}$, where $k = 2\pi/\lambda$ is the wavenumber. Then

$$
T_{j\pm1} = e^{ik(x_j\pm h)} = T_je^{\pm ikh}
$$

$$
T_j^{n+1} = T_j^n\left[1+F\left(e^{-ikh}-2+e^{ikh}\right)\right] = T_j^n\left[1+F(2\cos kh-2)\right]
$$

$$
G = |1-2F(1-\cos kh)|
$$

The **worst case** is $kh = \pi$: the shortest wave the grid can represent, 2 points per wavelength (anything shorter aliases). There $G = |1-4F|$, which reaches 1 at $F = \tfrac12$:

$$
\boxed{F = \frac{\alpha\Delta t}{h^2}\le\frac12\qquad\text{(FTCS heat equation)}}
$$

This matches the Python experiments in A4 exactly: 0.448 was stable and 0.576 was unstable.

## 3. Von Neumann analysis of the convection equation (L6)
$f_t+cf_x = 0$ has exact solution $f(x,t) = f_0(x-ct)$: the initial shape moves right at speed $c$.

Use the **upwind** (backward) space difference, which looks into the wind:

$$
\frac{f_j^{n+1}-f_j^n}{\Delta t}+c\frac{f_j^n-f_{j-1}^n}{h} = 0\;\Rightarrow\;f_j^{n+1} = f_j^n-C\left(f_j^n-f_{j-1}^n\right),\qquad C = \frac{c\Delta t}{h}
$$

$$
G = |1-C(1-e^{-ikh})| = |1-C(1-\cos kh)-iC\sin kh|
$$

At the worst case $kh = \pi$, $G = |1-2C|$, which equals 1 at $C = 1$:

$$
\boxed{C = \frac{c\Delta t}{h}\le1\qquad\text{(CFL / Courant condition)}}
$$

**Physical meaning**: information must not travel more than one cell per time step, otherwise the numerical stencil cannot "see" where the solution came from.

At exactly $C = 1$, upwind reproduces the exact shift ($G\equiv1$ for all $k$). For $C<1$ it damps short waves, which shows up as numerical diffusion ([[Convective Interpolation Schemes]]).

![[dam_von_neumann_gain.png|760]]

> [!warning] Upwind vs downwind
> Differencing **against** the flow (a downwind or forward difference for $c>0$) is unconditionally unstable with explicit Euler. So is the explicit central difference (FTCS) for pure convection. The direction of the stencil matters as much as its order.

## 4. Summary of stability parameters (L6)
| Equation | Parameter | Explicit limit (Euler + 2nd-order central / 1st-order upwind) |
|---|---|---|
| Convection $f_t+cf_x = 0$ | $\mathrm{CFL} = \dfrac{c\Delta t}{h}$ | $\le1$ |
| Diffusion $T_t = \alpha T_{xx}$ | $F = \dfrac{\alpha\Delta t}{h^2}$ | $\le\tfrac12$ |
| Viscous momentum ($\nu$ plays the role of $\alpha$) | $\mathrm{CFL}_\nu = \dfrac{\nu\Delta t}{h^2}$ | $\le\tfrac12$ (by analogy) |

**Consequences for real CFD**:
- $\Delta t\propto h^2$ for diffusion means that refining the grid by 2× cuts the explicit time step by 4×. Viscous near-wall cells therefore make explicit schemes very expensive. This is a major reason steady solvers are implicit.
- Unsteady commercial solvers still expose a **Courant number** setting. Time-accurate explicit work typically needs CFL ≲ 1.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]] · Next: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- The same $\sigma\pm i\omega$ plane is the s-plane of control theory: [[Poles and Zeros]] · [[Characteristic Equation and Eigenvalues]]

## Sources
- CFD Lecture 6, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 77–86; transcript `CFD.txt`
