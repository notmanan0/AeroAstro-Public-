---
title: "SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 6
tags: [sesa2029, cfd, runge-kutta, blasius, boundary-layer, shooting-method]
aliases: ["Runge-Kutta", "RK4", "Blasius solution", "CFD Lecture 7"]
date: 2026-10-30
status: lectured
coverage: "Week 4 (2025-10-23)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]"]
next_topics: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
key_concepts: ["[[Runge-Kutta Methods]]", "[[Shooting Method and the Blasius Solution]]", "[[Truncation Error and Order of Accuracy]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L7)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-23.txt"]
---

# SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation

> [!abstract] Summary
> The AIAA expects CFD to be at least second order in space and time, and everything so far has been first order in time. Three remedies are a three-point backward difference in time, a predictor–corrector (RK2), and the classical fourth-order Runge–Kutta scheme, which reproduces the Taylor series of $e^{\lambda\Delta t}$ to the order of the method and enlarges the stability region to include part of the imaginary axis. As an application, the Blasius equation for the laminar flat-plate boundary layer, which has no analytic solution, is solved by shooting with Python's adaptive RK45 integrator, giving $f''(0)=0.4696$ and the shape factor $H=2.591$.

> [!summary]- Exam use: quick path
> - **Use it when:** you must show the order of a time-stepping scheme, write out RK2 or RK4, or set up the Blasius equation for a numerical solver.
> - **Assumptions:** the model equation $df/dt=\lambda f$ for order and stability; laminar, zero-pressure-gradient flow and similarity for Blasius.
> - **Method:** 1. Substitute $R=\lambda f$ into each stage. 2. Collect $f^{n+1}=G(\lambda\Delta t)f^n$. 3. Compare $G$ with $e^{\lambda\Delta t}=1+\lambda\Delta t+(\lambda\Delta t)^2/2+\dots$; the number of matching terms gives the order. 4. For Blasius, write $f_0'=f_1$, $f_1'=f_2$, $f_2'=-f_0f_2$. 5. Shoot on $f''(0)$ until $f'(\eta_{max})=1$.
> - **Common mistakes:** forgetting that a multi-level scheme needs a starting step; choosing $\eta_{max}$ too small (4 is not enough).
> - **Practise:** [[#2. The predictor–corrector scheme (RK2)]] · [[SESA2029 CFD Worked Examples#Q8: RK2 characteristic polynomial|CFD worked examples Q8]]

This lecture closes the numerical-analysis block and opens the boundary-layer physics needed for the third coursework lab (2025-10-23, ll. 1–40). By now most of the class had converged inviscid solutions for their wings in Fluent and were running the three grids at three angles of attack.

Runge–Kutta methods sample the slope more than once per step. A first-order step takes the slope at the start of the interval and walks along it in a straight line, missing any curvature. A Runge–Kutta step tests the slope part-way along, uses that to improve its estimate, and combines several such samples so that the curvature, and then higher derivatives, are captured without ever computing them explicitly.

## 1. The three-point backward scheme in time

The second-order backward difference from [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|A2]] works just as well in time (ll. 41–80). For $df/dt=R$, with $R$ evaluated at level $n$ (explicit),

$$
\frac{f^{n-1}-4f^n+3f^{n+1}}{2\Delta t}=R^n
\quad\Longrightarrow\quad
f^{n+1}=\frac{4f^n-f^{n-1}+2\Delta t\,R^n}{3}.
$$

It is second order but needs two stored past levels, and so a special starting step: at $n=0$ there is no $f^{-1}$, so the first step is taken with a first-order method (ll. 81–100). A careless starter can inject spurious modes. Fluent uses exactly this scheme for unsteady flow with the density-based solver, in dual time stepping: an outer loop in physical time and an inner loop of pseudo-time iterations that converge each implicit step (ll. 81–110).

## 2. The predictor–corrector scheme (RK2)

A predictor estimates the solution at the half step with an explicit Euler half-step, and a corrector uses that estimate to evaluate the slope at the midpoint for the full step (ll. 111–125):

$$
\tilde f^{n+1/2}=f^n+\tfrac12\Delta t\,R(f^n),
\qquad
f^{n+1}=f^n+\Delta t\,R\left(\tilde f^{n+1/2}\right).
$$

For the model equation $R=\lambda f$, the predictor is

$$
\tilde f^{n+1/2}=f^n\left(1+\tfrac12\lambda\Delta t\right).
$$

Substitute into the corrector:

$$
f^{n+1}=f^n+\lambda\Delta t\,f^n\left(1+\tfrac12\lambda\Delta t\right).
$$

Factor out $f^n$:

$$
f^{n+1}=f^n\left(1+\lambda\Delta t+\frac{(\lambda\Delta t)^2}{2}\right).
$$

These are the first three terms of the exact $e^{\lambda\Delta t}$, so the error per step is $O(\Delta t^3)$ and the scheme is second order: halving $\Delta t$ quarters the error (ll. 126–160). Runge–Kutta schemes have the property that for the model equation an order-$m$ scheme reproduces exactly the $m+1$ terms up to $(\lambda\Delta t)^m/m!$ and then stops, with no wrong extra terms (ll. 161–180). Explicit Euler is RK1.

> [!warning] Lecture slip (2025-10-23, ll. 161–175)
> The RK property is stated as giving "exactly the first $n$ terms" and RK2 as giving "the first two terms of a Taylor series". The algebra just done shows RK2 recovering three terms ($1$, $\lambda\Delta t$, $(\lambda\Delta t)^2/2$): an order-$m$ scheme matches $m+1$ terms, counting the leading 1.

## 3. The classical fourth-order Runge–Kutta scheme

The classical RK4 builds four estimates and combines them (ll. 181–240):

$$
f^{*}=f^n+\tfrac{\Delta t}{2}R(t^n,f^n),
$$

$$
f^{**}=f^n+\tfrac{\Delta t}{2}R(t^{n+1/2},f^{*}),
$$

$$
f^{***}=f^n+\Delta t\,R(t^{n+1/2},f^{**}),
$$

$$
f^{n+1}=f^n+\tfrac{\Delta t}{6}\left[R(t^n,f^n)+2R(t^{n+1/2},f^{*})+2R(t^{n+1/2},f^{**})+R(t^{n+1},f^{***})\right].
$$

The first stage is an explicit half-step predictor, the second a backward-type corrector at the half step, the third a full-step midpoint predictor, and the last a Simpson-weighted average of the four slopes. A student asked why $f^{***}$ is at the full step while $f^{**}$ is at the half: $f^{***}$ advances the full $\Delta t$ using the improved midpoint slope (ll. 211–225). Four or five lines of algebra with $R=\lambda f$ give

$$
f^{n+1}=f^n\left(1+\lambda\Delta t+\frac{(\lambda\Delta t)^2}{2}+\frac{(\lambda\Delta t)^3}{6}+\frac{(\lambda\Delta t)^4}{24}\right),
$$

five Taylor terms, so fourth order. It is the default ordinary-differential-equation solver in MATLAB and Python, "the go-to method" for integrating anything in time, from a cannonball to a rocket (ll. 236–255). Each step costs four right-hand-side evaluations and about five stored arrays; low-storage RK3 variants need only two arrays, which makes them popular in large simulations (ll. 271–285).

![[dam_time_order_convergence.png|600]]

The figure integrates the F-4C short-period mode $\lambda=-0.5+1.3i$ to $t=4$; the error slopes are 1, 2 and 4.

### Stability regions

The same gain analysis as in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]], with $G=\sum_{m=0}^{p}(\lambda\Delta t)^m/m!$, gives growing stability regions (ll. 256–300):

| Scheme | Real-axis limit $\sigma\Delta t$ | Imaginary-axis limit $\omega\Delta t$ |
|---|---|---|
| Euler (RK1) | −2 | none |
| RK2 | −2 | none (marginal) |
| RK3 | −2.51 | $\sqrt3\approx1.73$ |
| RK4 | −2.79 | $2\sqrt2\approx2.83$ |

Higher order pays twice: more accuracy and larger stable steps. RK3 and RK4 also include part of the imaginary axis, so they propagate pure waves stably without added dissipation, which matters for aeroacoustics, such as jet noise propagating away from an aircraft (ll. 281–300).

## 4. The Blasius boundary layer

Before 1904, ideal-flow theory predicted zero drag on any body, d'Alembert's paradox, although anyone with a hand out of a car window knows better (ll. 321–360). Prandtl resolved it in 1904 with the no-slip condition and the thin boundary layer where viscosity matters; in 1907 his student Blasius solved the laminar flat-plate case, by series expansion, by assuming the velocity profile has the same shape at every streamwise station, a similarity solution (ll. 361–380). The result is

$$
f'''+ff''=0,
$$

where primes are derivatives with respect to $\eta=y/\delta$, $f=\psi/(U_e\delta)$ is a dimensionless stream function, and the Blasius thickness grows as the square root of distance:

$$
\frac{\delta}{x}=\left(\frac{2}{Re_x}\right)^{1/2}.
$$

The velocity is $u=\partial\psi/\partial y$; with $\psi=U_e\delta f$ and $d\eta/dy=1/\delta$ that gives $f'=u/U_e$, the velocity profile, while $f''$ is proportional to the shear stress (ll. 381–400). The derivation is in SESA3043; here the equation is simply solved.

It looks simple, but the product $ff''$ makes it a nonlinear third-order ODE with no analytic solution, so it must be solved numerically (ll. 300–320). The three boundary conditions are: the wall is a streamline, $f(0)=0$; no slip, $f'(0)=0$; and the free stream is recovered, $f'(\infty)=1$ (ll. 401–420).

The solver expects first-order equations, so define $f_0=f$, $f_1=f'$, $f_2=f''$ (ll. 421–455):

$$
f_0'=f_1,
\qquad
f_1'=f_2,
\qquad
f_2'=-f_0f_2.
$$

The first two just define the variables; the third is the Blasius equation.

Two conditions are known at the wall and one at infinity, so the problem is solved by shooting (ll. 455–480), like adjusting a cannon's elevation until it hits the target: guess $f''(0)$, integrate outwards to a numerical "infinity" $\eta_{max}$, and compare $f'(\eta_{max})$ with 1. In the live demonstration, 0.3 undershoots and 0.6 overshoots, and a minute of trial and error converges on 0.4696 (ll. 511–540).

```python
import numpy as np
from scipy import integrate
from scipy.integrate import trapezoid     # older SciPy: trapz

def blas(eta, f):                         # Blasius as three first-order ODEs
    return (f[1], f[2], -f[0]*f[2])

f0 = (0.0, 0.0, 0.4696)                   # f(0), f'(0), guessed f''(0)
etamax = 8.0                              # numerical infinity
p = integrate.solve_ivp(blas, [0, etamax], f0, t_eval=np.linspace(0, etamax, 1001),
                        rtol=1e-8, atol=1e-10)
eta, u = p.t, p.y[1]
dstar = trapezoid(1 - u, eta); theta = trapezoid(u*(1 - u), eta)
print(u[-1], dstar, theta, dstar/theta)
```

`solve_ivp` uses RK45: a fourth-order and a fifth-order Runge–Kutta step whose difference estimates the error, so the step is shrunk when the error exceeds the tolerance and grown when it is comfortably below, which is adaptive step control (ll. 321–340). The code on Blackboard used `trapz`, which newer SciPy has renamed `trapezoid` (ll. 501–510).

![[dam_blasius_shooting.png|560]]

The results, in units of $\delta$, recomputed: $\delta^*/\delta=1.2168$, $\theta/\delta=0.4696$, and the classic shape factor $H=\delta^*/\theta=2.591$. With $\delta=\sqrt{2\nu x/U_e}$ these become $\delta^*=1.7208x/\sqrt{Re_x}$, $\theta=0.664x/\sqrt{Re_x}$, $\delta_{99}\approx4.91x/\sqrt{Re_x}$ and $C_f=0.664/\sqrt{Re_x}$, the flat-plate formulas used in [[SESA2029 A1 - Digital Design and the Role of CFD and FEA|A1]].

Prof Sandham's advice is to always test the numerical parameters (ll. 541–580). With $\eta_{max}=4$ the shape factor is 2.5933, too small a domain; 6 is the traditional value and 8 is better (2.59112, unchanged at 10). Loosening the tolerance from $10^{-10}$ to $10^{-6}$ changes nothing to five figures. But only 100 output points makes the trapezoid integration give 2.593; 1000 points gives 2.5911.

In the coursework, the CFD laminar profiles can be compared with Blasius by plotting $u/U_e$ against $y/\delta^*$ at several stations, with Blasius as a line and CFD as symbols; if the similarity assumption holds, the profiles collapse (ll. 361–380).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Next: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Concepts: [[Runge-Kutta Methods]] · [[Shooting Method and the Blasius Solution]] · [[Truncation Error and Order of Accuracy]]
- Boundary layers: [[SESA2022 T2 - Boundary Layers]] · [[Displacement and Momentum Thickness]] · [[Momentum Integral Equation]]

## Sources

- `All_lectures_as_delivered.pdf`, L7, with transcript `SESA2029 Lecture 2025-10-23.txt` (Prof N. Sandham; live Blasius demonstration, code on Blackboard)
- Values recomputed with SciPy `solve_ivp`

## Self-study tasks

### Core

- [ ] Show that the predictor–corrector scheme is second order using $R=\lambda f$ (2025-10-23, ll. 126–160). → [[#2. The predictor–corrector scheme (RK2)]] · [[SESA2029 CFD Worked Examples#Q8: RK2 characteristic polynomial|Worked examples Q8]]
- [ ] Run the Blasius code and find $f''(0)$ by shooting, then test $\eta_{max}$, the tolerance and the number of output points ("whenever you do things like this you should just fiddle with the numerical parameters", ll. 541–580). → [[#4. The Blasius boundary layer]]
- [ ] Coursework lab 3: compare your laminar CFD profiles with Blasius (ll. 590–600). → [[#4. The Blasius boundary layer]]
- [ ] Blasius boundary-layer numbers (example sheet). → [[SESA2029 CFD Worked Examples#Q9: Blasius boundary-layer numbers|Worked examples Q9]]

### Further practice

- [ ] Verify that RK4 reproduces five Taylor terms for $R=\lambda f$ ("four or five lines of algebra", ll. 201–215). → [[#3. The classical fourth-order Runge–Kutta scheme]]
- [ ] Explain why the three-point backward scheme needs a starting method. → [[#1. The three-point backward scheme in time]]
