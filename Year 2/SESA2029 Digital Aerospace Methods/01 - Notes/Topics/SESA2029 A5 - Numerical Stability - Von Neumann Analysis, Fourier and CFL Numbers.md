---
title: "SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 5
tags: [sesa2029, cfd, stability, von-neumann, cfl]
aliases: ["Von Neumann analysis", "CFL condition", "Fourier number", "CFD Lecture 6"]
date: 2026-10-30
status: lectured
coverage: "Week 3 (2025-10-17)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
next_topics: ["[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]"]
key_concepts: ["[[Von Neumann Stability Analysis]]", "[[CFL and Fourier Numbers]]", "[[Explicit and Implicit Time Integration]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L6)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-17.txt"]
---

# SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers

> [!abstract] Summary
> Stability is judged by the gain $G=|f^{n+1}/f^n|$: a scheme is unstable if some component grows from step to step. For the model equation $df/dt=\lambda f$, explicit Euler is stable only inside a unit circle centred at $\lambda\Delta t=-1$, while implicit Euler is stable everywhere outside a unit circle centred at $+1$. Von Neumann analysis applies the same test to a PDE by assuming a Fourier wave $e^{ikx_j}$; the shortest resolvable wave ($kh=\pi$) is the worst case, which gives $F=\alpha\Delta t/h^2\le\tfrac12$ for explicit diffusion and $C=c\Delta t/h\le1$ for explicit upwind convection.

> [!summary]- Exam use: quick path
> - **Use it when:** you must find the stability limit of a scheme, or explain the Courant or Fourier number.
> - **Assumptions:** linear equation with constant coefficients; uniform grid; periodic or long domain, so Fourier waves are valid.
> - **Method:** 1. Write the update $f_j^{n+1}=\dots$. 2. Substitute $f_j=e^{ikx_j}$, so $f_{j\pm1}=f_je^{\pm ikh}$. 3. Divide by $f_j^n$ to get the amplification factor; $G$ is its modulus. 4. Use $e^{ikh}+e^{-ikh}=2\cos kh$ and check the worst $kh$ (usually $\pi$). 5. Set $G=1$ for the limit.
> - **Common mistakes:** squaring the $i$ when taking a modulus (square the real and imaginary parts); differencing downwind, which is unconditionally unstable.
> - **Practise:** [[#2. Von Neumann analysis of the heat equation]] · [[SESA2029 CFD Worked Examples#Q6: Von Neumann analysis of a new scheme|CFD worked examples Q6]]

The previous lecture found by experiment that the explicit heat-equation scheme became unstable above a Fourier number of about 0.5, while the implicit one never did (2025-10-17, ll. 1–35). This lecture explains why, with what Prof Sandham called "about as difficult as it gets doing numerical analysis" in the module, complete with a "trigger warning" for the bend in the road.

Any error pattern on the grid can be decomposed into sines and cosines of different wavelengths. If the scheme multiplies even one of those waves by more than 1 each step, that wave grows exponentially and eventually swamps the solution: the saw-tooth seen in the experiments is the shortest wave the grid can carry, growing. Stability analysis computes the multiplier for every wave and finds the worst.

## 1. Stability of the model equation

The model equation is $df/dt=\lambda f$ with $\lambda=\sigma+i\omega$, a growth rate and a frequency (ll. 1–70). It covers every dynamic mode in flight mechanics, from the short-period oscillation to the Dutch roll, which is why it is a fair test.

Explicit Euler, a forward difference with the right-hand side at level $n$ (ll. 71–105):

$$
\frac{f^{n+1}-f^n}{\Delta t}=\lambda f^n
\quad\Longrightarrow\quad
f^{n+1}=(1+\lambda\Delta t)f^n.
$$

The gain is the change in amplitude per step:

$$
G=\left|\frac{f^{n+1}}{f^n}\right|=|1+\lambda\Delta t|.
$$

$G>1$ is unstable, $G<1$ stable and $G=1$ neutral. On the boundary, split $\lambda\Delta t$ into real and imaginary parts and take the modulus by squaring each part (ll. 106–140):

$$
1=(1+\sigma\Delta t)^2+(\omega\Delta t)^2.
$$

That is a circle of radius 1 centred at $\sigma\Delta t=-1$ in the $(\sigma\Delta t,\omega\Delta t)$ plane. At its centre $G=0$; inside it $G<1$, so explicit Euler is stable only inside the circle. Too large a time step pushes $\lambda\Delta t$ out of the circle.

> [!warning] Lecture slip (2025-10-17, ll. 135–140)
> The gain is said to be "less than zero inside the circle, and bigger than zero outside". A gain is a modulus and is never negative; the boundary is $G=1$, with $G<1$ inside and $G>1$ outside.

A student asked why the $i$ is not squared when taking the modulus (ll. 176–190): the modulus of a complex number is the length of a vector in the complex plane, so square the real part and the imaginary part, not the $i$.

Implicit Euler puts the right-hand side at $n+1$ (ll. 141–175):

$$
f^{n+1}-\lambda\Delta tf^{n+1}=f^n
\quad\Longrightarrow\quad
G=\frac{1}{|1-\lambda\Delta t|}.
$$

$G=1$ gives $1=(1-\sigma\Delta t)^2+(\omega\Delta t)^2$, a unit circle centred at $+1$, where $G$ is infinite. Implicit Euler is stable everywhere outside it, including the whole left half-plane, so any physically decaying mode is computed as decaying whatever the time step (ll. 176–245). It also damps some physically growing modes in the right half-plane, which is stability without correctness. Neither scheme is accurate in time, since both are first order. On the imaginary axis (pure oscillation, $\sigma=0$) explicit Euler is never stable, which motivates the Runge–Kutta schemes of [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation|A6]].

![[dam_stability_regions.png|520]]

## 2. Von Neumann analysis of the heat equation

The explicit heat scheme is $T_j^{n+1}=T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)$ with $F=\alpha\Delta t/h^2$ (ll. 246–285). Assume the solution is a single Fourier wave of wavenumber $k=2\pi/\lambda$ (long waves have small $k$):

$$
T_j=e^{ikx_j}.
$$

Since $x_{j\pm1}=x_j\pm h$,

$$
T_{j\pm1}=e^{ik(x_j\pm h)}=T_je^{\pm ikh}.
$$

Any continuous error distribution is a sum of such waves, so testing one wavenumber at a time is general (ll. 316–330). Substitute into the scheme:

$$
T_j^{n+1}=T_j^n\left[1+F\left(e^{-ikh}-2+e^{ikh}\right)\right].
$$

With $e^{ikh}=\cos kh+i\sin kh$ and $e^{-ikh}=\cos kh-i\sin kh$, the sum is $2\cos kh$:

$$
T_j^{n+1}=T_j^n\left[1+F(2\cos kh-2)\right].
$$

So

$$
G=|1-2F(1-\cos kh)|.
$$

$1-\cos kh$ is never negative, and the largest value is at $kh=\pi$ (ll. 330–385). That is the shortest wave the grid can represent, two points per wavelength, a saw-tooth; anything shorter cannot be resolved. There $\cos kh=-1$ and

$$
G=|1-4F|,
$$

which equals 1 at $F=\tfrac12$. Hence

$$
\boxed{F=\frac{\alpha\Delta t}{h^2}\le\frac12}
$$

for explicit diffusion, exactly the limit the Python experiments found: $F=0.448$ stable, $F=0.576$ unstable. "That's your solution to yesterday's question" (l. 365).

## 3. Von Neumann analysis of the convection equation

The convection equation $f_t+cf_x=0$ moves any initial shape to the right at speed $c$ without change, $f=f_0(x-ct)$ (ll. 386–420). It is the model for the left-hand side of the Euler and Navier–Stokes equations, as the heat equation models their viscous right-hand side.

Discretise with a forward difference in time and an upwind difference in space, looking into the wind as a weather forecaster looks at the cloud coming towards them (ll. 421–455):

$$
\frac{f_j^{n+1}-f_j^n}{\Delta t}+c\frac{f_j^n-f_{j-1}^n}{h}=0.
$$

Rearrange with the Courant (CFL, for Courant–Friedrichs–Lewy) number $C=c\Delta t/h$:

$$
f_j^{n+1}=f_j^n-C\left(f_j^n-f_{j-1}^n\right).
$$

Substitute $f_{j-1}=f_je^{-ikh}$:

$$
G=\left|1-C\left(1-e^{-ikh}\right)\right|=\left|1-C(1-\cos kh)-iC\sin kh\right|.
$$

At the worst case $kh=\pi$, $\sin kh=0$ and $\cos kh=-1$, so $G=|1-2C|$ (ll. 456–520). A small $C$ is stable; $C=\tfrac12$ gives $G=0$; $C=1$ gives $|{-1}|=1$, the boundary; $C=2$ gives 3, unstable. So

$$
\boxed{C=\frac{c\Delta t}{h}\le1}
$$

The physical meaning is that information must not travel more than one cell per time step, or the stencil cannot see where the solution came from. At exactly $C=1$ the upwind scheme shifts the solution one cell per step, exactly. Below 1 it damps the short waves, which appears as numerical diffusion ([[Convective Interpolation Schemes]]).

> [!warning] Lecture slip (2025-10-17, l. 465)
> The substitution is read as "$e^{ikh}$ is cos minus i sine"; it is $e^{-ikh}=\cos kh-i\sin kh$, as the next line uses.

![[dam_von_neumann_gain.png|760]]

Differencing against the flow, with a forward difference when $c>0$, is unstable for any time step, and so is the explicit central difference for pure convection: the direction of the stencil matters as much as its order.

## 4. What the limits mean for CFD

| Equation | Parameter | Explicit limit |
|---|---|---|
| Convection $f_t+cf_x=0$, upwind | $C=c\Delta t/h$ | $\le1$ |
| Diffusion $T_t=\alpha T_{xx}$, central | $F=\alpha\Delta t/h^2$ | $\le\tfrac12$ |
| Viscous momentum ($\nu$ in place of $\alpha$) | $\nu\Delta t/h^2$ | $\le\tfrac12$ by analogy |

Because the diffusive limit scales with $h^2$, halving the grid spacing cuts the allowable explicit time step by four, which makes explicit schemes very expensive on fine near-wall meshes; that is a major reason steady solvers are implicit. Time-accurate unsteady runs in Fluent still expose the Courant number as a control (ll. 456–470), and explicit time-accurate work typically needs $C\lesssim1$.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]
- Next: [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]
- Concepts: [[Von Neumann Stability Analysis]] · [[CFL and Fourier Numbers]] · [[Explicit and Implicit Time Integration]]
- The same $\sigma\pm i\omega$ plane is the control engineer's s-plane: [[Poles and Zeros]] · [[Characteristic Equation and Eigenvalues]]

## Sources

- `All_lectures_as_delivered.pdf`, L6, with transcript `SESA2029 Lecture 2025-10-17.txt` (Prof N. Sandham)

## Self-study tasks

### Core

- [ ] Derive the stability regions of explicit and implicit Euler for $df/dt=\lambda f$ (2025-10-17, ll. 71–245). → [[#1. Stability of the model equation]]
- [ ] Von Neumann analysis of the explicit heat scheme, showing $F\le\tfrac12$ (ll. 246–385). → [[#2. Von Neumann analysis of the heat equation]]
- [ ] Von Neumann analysis of explicit upwind convection, showing $C\le1$ (ll. 386–520). → [[#3. Von Neumann analysis of the convection equation]]
- [ ] Von Neumann analysis of a new scheme (example sheet). → [[SESA2029 CFD Worked Examples#Q6: Von Neumann analysis of a new scheme|Worked examples Q6]]

### Further practice

- [ ] Time-step limits for given $c$, $\alpha$ and $h$ (example sheet). → [[SESA2029 CFD Worked Examples#Q7: Time-step limits|Worked examples Q7]]
- [ ] Show that downwind differencing of the convection equation is unconditionally unstable. → [[#3. Von Neumann analysis of the convection equation]]
