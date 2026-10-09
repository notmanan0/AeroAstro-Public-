---
title: "SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 6
tags:
  - sesa2029
  - cfd
  - numerical-methods
  - runge-kutta
  - boundary-layers
aliases: ["Time-accurate methods", "RK4", "Blasius solution"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]"]
next_topics: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
key_concepts: ["[[Runge-Kutta Methods]]", "[[Shooting Method and the Blasius Solution]]", "[[Truncation Error and Order of Accuracy]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L7, pp. 87–100)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation

> [!abstract] Summary
> The AIAA expects **at least second-order** accuracy in both space and time, but Euler schemes are first order in time. Three upgrades:
> 1. **3-point backward** (BDF2), used in dual time-stepping;
> 2. the **predictor–corrector** midpoint scheme, which is RK2;
> 3. classical **RK4**, the go-to ODE solver.
>
> An order-$n$ Runge–Kutta scheme reproduces exactly the first $n+1$ terms of the Taylor series of $e^{\lambda\Delta t}$, and nothing more. Higher-order RK also **enlarges the stable region**, and RK3/RK4 cover part of the imaginary axis, so they can propagate waves.
>
> **Application**: the Blasius laminar boundary layer $f'''+ff'' = 0$ has no closed-form solution. Rewrite it as three first-order ODEs, integrate outward with RK45, and **shoot** on the unknown wall shear until $f'(\infty) = 1$. This gives $f''(0) = 0.4696$ and shape factor $H = 2.591$.

## Key Concepts
- [[Runge-Kutta Methods]] · [[Shooting Method and the Blasius Solution]] · [[Truncation Error and Order of Accuracy]]

---

## 1. 3-point backward in time (L7)
Take the second-order backward difference from A2 and apply it in time to $df/dt = R$:

$$
\frac{f^{n-1}-4f^n+3f^{n+1}}{2\Delta t} = R^n\;\Rightarrow\;f^{n+1} = \frac{4f^n-f^{n-1}+2\Delta t R^n}{3}
$$

- It is second order in time, but it needs **two stored past levels** and a **special starting step** (e.g. one Euler step first).
- A poor starter can inject spurious modes.
- It is used in density-based solvers inside **dual time-stepping**: an outer physical-time loop, with inner pseudo-time iterations that converge each implicit step.

## 2. Predictor–corrector = explicit RK2 (L7)

$$
\tilde f^{n+1/2} = f^n+\tfrac12\Delta t\,R(f^n)\ \ \text{(half-step predictor)},\qquad f^{n+1} = f^n+\Delta t\,R(\tilde f^{n+1/2})\ \ \text{(midpoint corrector)}
$$

Substituting $R = \lambda f$:

$$
f^{n+1} = f^n\left(1+\lambda\Delta t+\frac{(\lambda\Delta t)^2}{2}\right)
$$

These are exactly the first three terms of $e^{\lambda\Delta t}$, so the scheme is second order.

**General rule**: an order-$n$ RK method recovers exactly $n+1$ Taylor terms (up to $(\lambda\Delta t)^n/n!$) with **no additional terms**. Explicit Euler is RK1.

## 3. Classical RK4 (L7)

$$
\begin{aligned}
f^{*} &= f^n+\tfrac{\Delta t}{2}R(t^n,f^n)\\
f^{**} &= f^n+\tfrac{\Delta t}{2}R(t^{n+1/2},f^{*})\\
f^{***} &= f^n+\Delta t\,R(t^{n+1/2},f^{**})\\
f^{n+1} &= f^n+\tfrac{\Delta t}{6}\Big[R(t^n,f^n)+2R(t^{n+1/2},f^*)+2R(t^{n+1/2},f^{**})+R(t^{n+1},f^{***})\Big]
\end{aligned}
$$

The four stages are:
1. an explicit half-step predictor;
2. a backward-type half-step corrector;
3. a full-step midpoint predictor;
4. a Simpson-weighted combination of the four slopes.

For $R = \lambda f$:

$$
f^{n+1} = f^n\left(1+\lambda\Delta t+\frac{(\lambda\Delta t)^2}{2}+\frac{(\lambda\Delta t)^3}{6}+\frac{(\lambda\Delta t)^4}{24}\right)\quad\Rightarrow\quad O(\Delta t^4)
$$

The cost is four right-hand-side evaluations and about five storage arrays per step. **Low-storage RK3** variants need only two arrays, which makes them popular for large simulations.

![[dam_time_order_convergence.png|600]]

The figure integrates the F-4C short-period mode $\lambda = -0.5+1.3i$ to $t = 4$. The measured slopes are 1, 2 and 4.

## 4. Stability regions of RK schemes (L7)
Stable where $|G(\lambda\Delta t)|\le1$, with $G = \sum_{m=0}^{n}(\lambda\Delta t)^m/m!$:

| Scheme | Real-axis limit $\sigma\Delta t$ | Imaginary-axis limit $\omega\Delta t$ |
|---|---|---|
| Euler (RK1) | −2 | 0 (unstable for pure waves) |
| RK2 | −2 | 0 (marginally unstable) |
| RK3 | −2.51 | $\sqrt3\approx1.73$ |
| RK4 | −2.79 | $2\sqrt2\approx2.83$ |

Because RK3 and RK4 enclose a segment of the imaginary axis, they propagate **waves** stably (aeroacoustics, vortex shedding) without added dissipation. RK4 is also the time integrator in density-based unsteady solvers. See the region plot in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]].

## 5. The Blasius boundary layer (L7)
**History**:
- Prandtl (1904) introduced the boundary layer and no-slip. This resolved [[D'Alembert's Paradox]]: ideal flow predicts zero drag.
- Blasius (1907) solved the laminar flat-plate boundary-layer equations by assuming **similarity**: the profile shape is the same at every $x$.

$$
f'''+ff'' = 0,\qquad f = \frac{\psi}{U_e\delta},\quad f' = \frac{u}{U_e},\quad \eta = \frac y\delta,\quad \frac{\delta}{x} = \left(\frac{2}{Re_x}\right)^{1/2}
$$

$\psi$ is the stream function, so $u = \partial\psi/\partial y = U_e f'$ ([[Streamfunction and Velocity Potential]]). The equation is a **nonlinear third-order ODE** with no analytic solution: the $ff''$ term kills every textbook method.

**Boundary conditions**:
- $f(0) = 0$: the wall is a streamline;
- $f'(0) = 0$: no slip;
- $f'(\infty) = 1$: the free stream is recovered.

**Reformulate as a first-order system** for the solver. With $f_0 = f$, $f_1 = f'$ and $f_2 = f''$:

$$
f_0' = f_1,\qquad f_1' = f_2,\qquad f_2' = -f_0f_2
$$

```python
import numpy as np
from scipy import integrate
from scipy.integrate import trapezoid           # older SciPy: trapz

def blas(eta, f):                               # Blasius as 3 first-order ODEs
    return (f[1], f[2], -f[0]*f[2])

f0 = (0.0, 0.0, 0.4696)                          # wall: f, f', guessed f''(0)
etamax = 8.0                                     # numerical "infinity"
p = integrate.solve_ivp(blas, [0, etamax], f0, t_eval=np.linspace(0, etamax, 1001),
                        rtol=1e-8, atol=1e-10)   # RK45 with adaptive steps
eta, u = p.t, p.y[1]
dstar = trapezoid(1 - u, eta); theta = trapezoid(u*(1 - u), eta)
print(u[-1], dstar, theta, dstar/theta)
```

`solve_ivp` defaults to **RK45**: embedded 4th- and 5th-order RK. The difference between the two estimates is an error estimate; steps are shrunk when it exceeds the tolerance and grown when it is comfortably below. This is **adaptive time stepping**.

**Shooting.** Two conditions are known at the wall and one at infinity. Guess $f''(0)$, integrate outward, and compare $f'(\eta_{max})$ with 1, like adjusting a cannon's elevation:

| Guess $f''(0)$ | $f'(8)$ |
|---|---|
| 0.30 | 0.742 (under-shoot, so raise) |
| 0.60 | 1.177 (over-shoot, so lower) |
| **0.4696** | **1.000** |

The trial and error can be automated with a root-finder, or removed with a scaling transformation.

![[dam_blasius_shooting.png|560]]

**Results** in $\eta = y/\delta$ units, with $\delta = \sqrt{2\nu x/U_e}$:
- $\delta^*/\delta = 1.2168$, so $\delta^* = 1.7208\,x/\sqrt{Re_x}$;
- $\theta/\delta = 0.4696$, so $\theta = 0.664\,x/\sqrt{Re_x}$;
- shape factor $H = \delta^*/\theta = 2.591$;
- $u/U_e = 0.99$ at $\eta\approx3.47$, so $\delta_{99}\approx4.91\,x/\sqrt{Re_x}$;
- wall shear $C_f = 2f''(0)/\sqrt{2Re_x} = 0.664/\sqrt{Re_x}$.

These are the flat-plate formulas quoted in [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]].

**Numerical-parameter sensitivity (always test it):**
- $\eta_{max} = 4$ gives $H = 2.593$, which is too short. 6–8 is enough (8 gives 2.5911).
- Only 100 output points makes the trapezoid integration give $H = 2.593$; 1000 points gives 2.5911.
- Loosening the tolerance from $10^{-10}$ to $10^{-6}$ changes nothing at 4 decimal places.

> [!tip] Comparing a Navier–Stokes solution with Blasius
> Plot $u/U_e$ against $y/\delta^*$ at several $x$ stations. The profiles should **collapse** once the layer is developed; that is the similarity assumption. Draw Blasius as a solid line and CFD as symbols on the same axes.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]] · Next: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Boundary-layer background: [[SESA2022 T2 - Boundary Layers]] · [[Displacement and Momentum Thickness]] · [[Momentum Integral Equation]]

## Sources
- CFD Lecture 7, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 87–100; transcript `CFD.txt` (live Blasius demonstration)
- Values recomputed with SciPy `solve_ivp`
