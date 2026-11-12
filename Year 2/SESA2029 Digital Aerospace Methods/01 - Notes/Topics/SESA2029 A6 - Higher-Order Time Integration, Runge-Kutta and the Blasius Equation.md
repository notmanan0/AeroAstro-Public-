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
> CFD should be at least formally second order in space and time (AIAA publication policy), but the explicit and implicit Euler time advances are only first order. Three remedies are a three-point backward difference in time, a predictor–corrector (RK2), and the classical fourth-order Runge–Kutta scheme (RK4); the Runge–Kutta schemes reproduce the Taylor series of $e^{\lambda\Delta t}$ up to the order of the method, and RK3 and RK4 also enlarge the stability region to include part of the imaginary axis. As an application, the Blasius equation for the laminar flat-plate boundary layer, which has no exact solution, is solved by shooting with Python's adaptive RK45 integrator, giving $f''(0)=0.4696$ and the shape factor $H=2.591$.

> [!summary]- Exam use: quick path
> - **Use it when:** you must show the order of a time-stepping scheme, write out RK2 or RK4, or set up the Blasius equation for a numerical solver.
> - **Assumptions:** the model equation $\mathrm df/\mathrm dt=\lambda f$ for order and stability; laminar, zero-pressure-gradient flow and similarity for Blasius.
> - **Method:** 1. Substitute $R=\lambda f$ into each stage, writing $z=\lambda\Delta t$. 2. Collect $f^{n+1}=G(z)f^n$. 3. Compare $G$ with $e^{z}=1+z+z^2/2+\dots$; matching up to $z^p/p!$ means order $p$. 4. For Blasius, write $f_0'=f_1$, $f_1'=f_2$, $f_2'=-f_0f_2$. 5. Shoot on $f''(0)$ until $f'(\eta_{max})=1$.
> - **Common mistakes:** forgetting that a multi-level scheme needs a starting step; choosing $\eta_{max}$ too small (4 is not enough).
> - **Practise:** [[#2. The predictor–corrector scheme (RK2)]] · [[#RK4 in four lines]] · [[SESA2029 CFD Worked Examples#Q8: RK2 characteristic polynomial|CFD worked examples Q8]]

The AIAA publication policy recommends that methods for PDEs be at least formally second order in space for smooth solutions and that time-difference methods for initial-value problems be at least formally second order (L7 slide 3). The space discretisations of A2 to A5 meet that; the explicit and implicit Euler time advances do not. The Blasius boundary-layer problem (§4) is the reference solution for the laminar profiles of coursework lab 3.

Runge–Kutta methods sample the slope more than once per step. A first-order step takes the slope at the start of the interval and walks along it in a straight line, missing any curvature. A Runge–Kutta step tests the slope part-way along, uses that to improve its estimate, and combines several such samples so that the curvature, and then higher derivatives, are captured without ever computing them explicitly.

## 1. The three-point backward scheme in time

The second-order backward difference from [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|A2]], $(f_{j-2}-4f_{j-1}+3f_j)/2h$, works just as well in time, with $\Delta t$ in place of $h$ and the derivative taken at the new level $n+1$ (L7 slide 4). For $\mathrm df/\mathrm dt=R$,

$$
\frac{f^{n-1}-4f^n+3f^{n+1}}{2\Delta t}=R.
$$

The left-hand side approximates $\mathrm df/\mathrm dt$ at $t_{n+1}$ with error $O(\Delta t^2)$. Where $R$ is evaluated decides whether the scheme is second order.

With $R$ at the new level, $R^{n+1}$, the two sides are consistent at $t_{n+1}$ and the scheme is second order. It is implicit, because $f^{n+1}$ appears inside $R$. For the model equation, write $z=\lambda\Delta t$ and $f^{n+1}=Gf^n=G^2f^{n-1}$:

$$
1-4G+3G^2=2zG^2,
$$

whose physical root expands as $G=1+z+\tfrac12z^2+\tfrac12z^3+\dots$; it matches $e^z$ to the $z^2$ term, so the scheme is second order. This is the implicit second-order three-point backward method used in Fluent for unsteady flow with the density-based solver, in dual time stepping: an outer loop in physical time, and an inner loop of pseudo-time iterations that converges the implicit equation at each physical step.

With $R$ at the known level $n$ the update can be written down explicitly,

$$
f^{n+1}=\frac{4f^n-f^{n-1}+2\Delta t\,R^n}{3},
$$

but then the left side is centred at $t_{n+1}$ and the right side at $t_n$, which costs a whole order. For the model equation $3G^2-(4+2z)G+1=0$, whose physical root is $G=1+z-\tfrac12z^2+\dots$: the $z^2$ coefficient is wrong, so this explicit form is only first order (the slides' second-order label is covered in [[#Transcript and slide slips]]).

Either way the scheme needs two stored past levels. At $n=0$ there is no $f^{-1}$, so a special starting method is needed: the first step is taken with a one-step method such as explicit Euler, after which two levels exist. A careless starter can inject a spurious mode, the second root of the quadratic for $G$.

## 2. The predictor–corrector scheme (RK2)

A predictor estimates the solution at the half step with an explicit Euler half-step, and a corrector uses that estimate to evaluate the slope at the midpoint for the full step (L7 slide 5):

$$
\tilde f^{n+1/2}=f^n+\tfrac12\Delta t\,R(f^n),
\qquad
f^{n+1}=f^n+\Delta t\,R\left(\tilde f^{n+1/2}\right).
$$

For the model equation $R=\lambda f$, the predictor is

$$
\tilde f^{n+1/2}=f^n+\tfrac12\Delta t\,\lambda f^n=f^n\left(1+\tfrac12\lambda\Delta t\right).
$$

Substitute into the corrector:

$$
f^{n+1}=f^n+\Delta t\,\lambda\,f^n\left(1+\tfrac12\lambda\Delta t\right).
$$

Expand the product:

$$
f^{n+1}=f^n+\lambda\Delta t\,f^n+\tfrac12(\lambda\Delta t)^2f^n.
$$

Factor out $f^n$:

$$
f^{n+1}=f^n\left(1+\lambda\Delta t+\frac{(\lambda\Delta t)^2}{2}\right).
$$

The exact solution over one step is $f^{n+1}=e^{\lambda\Delta t}f^n=\left(1+\lambda\Delta t+\tfrac{(\lambda\Delta t)^2}{2}+\tfrac{(\lambda\Delta t)^3}{6}+\dots\right)f^n$. RK2 matches up to the $(\lambda\Delta t)^2$ term, so the error per step is $O(\Delta t^3)$; over a fixed time the $t/\Delta t$ steps add up to an error $O(\Delta t^2)$, and the scheme is second order: halving $\Delta t$ quarters the error. For the model equation, the Runge–Kutta schemes of this section (RK1 to RK4, with as many stages as their order) reproduce the series exactly up to $(\lambda\Delta t)^p/p!$ and then stop, with no wrong extra terms. Explicit Euler is RK1.

## 3. The classical fourth-order Runge–Kutta scheme

The classical RK4 builds three intermediate estimates and combines four slopes (L7 slide 6):

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

The first stage is an explicit half-step predictor, the second a corrector at the half step using the predicted slope, the third a full-step estimate using the improved midpoint slope, and the last a weighted average of the four slopes with weights $1,2,2,1$ over 6, the same weights as Simpson's rule. $f^{***}$ is at the full step while $f^{**}$ is at the half because $f^{***}$ advances the full $\Delta t$ from $f^n$ using the slope at the midpoint.

### RK4 in four lines

Set $R=\lambda f$ and $z=\lambda\Delta t$ (the exercise on L7 slide 6). Each stage multiplies $f^n$ by a polynomial in $z$:

$$
f^{*}=f^n\left(1+\tfrac z2\right),
$$

$$
f^{**}=f^n+\tfrac z2f^{*}=f^n\left(1+\tfrac z2+\tfrac{z^2}{4}\right),
$$

$$
f^{***}=f^n+zf^{**}=f^n\left(1+z+\tfrac{z^2}{2}+\tfrac{z^3}{4}\right).
$$

The four slopes, each multiplied by $\Delta t$, are $zf^n$, $zf^*$, $zf^{**}$ and $zf^{***}$, so

$$
\frac{f^{n+1}}{f^n}=1+\frac16\left[z+2z\left(1+\tfrac z2\right)+2z\left(1+\tfrac z2+\tfrac{z^2}4\right)+z\left(1+z+\tfrac{z^2}2+\tfrac{z^3}4\right)\right].
$$

Collect powers inside the bracket: $z$ terms $1+2+2+1=6$; $z^2$ terms $1+1+1=3$; $z^3$ terms $\tfrac12+\tfrac12=1$; $z^4$ term $\tfrac14$. Dividing by 6,

$$
f^{n+1}=f^n\left(1+z+\frac{z^2}{2}+\frac{z^3}{6}+\frac{z^4}{24}\right),
$$

five Taylor terms of $e^z$, so fourth order. RK4 is the go-to method in science and engineering, the default ordinary-differential-equation solver in MATLAB and Python, used for anything integrated in time from a cannonball to a rocket, and in Fluent's density-based unsteady calculations. Each step costs four right-hand-side evaluations and about five stored arrays; low-storage RK3 variants need only two arrays, which makes them popular in large simulations.

![[dam_time_order_convergence.png|900]]

The figure integrates the F-4C short-period mode $\lambda=-0.5+1.3i$ to $t=4$. The error slopes are 1, 2 and 4 for Euler, RK2 and RK4. The two three-point backward variants, started from the exact value at the first step, show slope 2 with $R$ at $n+1$ and slope 1 with $R$ at $n$.

### Stability regions

The same gain analysis as in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]], with $G=\sum_{m=0}^{p}z^m/m!$, gives growing stability regions (L7 slide 7):

| Scheme | Real-axis limit $\sigma\Delta t$ | Imaginary-axis limit $\omega\Delta t$ |
|---|---|---|
| Euler (RK1) | −2 | none |
| RK2 | −2 | none |
| RK3 | −2.51 | $\sqrt3\approx1.73$ |
| RK4 | −2.79 | $2\sqrt2\approx2.83$ |

![[dam_stability_regions.png|760]]

The imaginary-axis entries follow from $z=i\omega\Delta t$. For RK2, $G=1-\tfrac12(\omega\Delta t)^2+i\,\omega\Delta t$, so $G^2=1+\tfrac14(\omega\Delta t)^4>1$ for every step: unstable, though only weakly for small steps. For RK4, $G^2=1-\tfrac{(\omega\Delta t)^6}{72}+\tfrac{(\omega\Delta t)^8}{576}$, which is at most 1 while $(\omega\Delta t)^2\le8$, giving the $2\sqrt2$ limit. Higher order pays twice: more accuracy and larger stable steps. RK3 and RK4 include part of the imaginary axis, so they propagate pure waves stably, which matters for wave-propagation problems such as aeroacoustics, for example jet noise travelling away from an aircraft.

## 4. The Blasius boundary layer

Ideal-flow theory predicts zero drag on any body, d'Alembert's paradox. Prandtl resolved it in 1904 with the boundary-layer concept: no slip at the wall and a thin layer where viscosity matters, governed by the boundary-layer equations, a simplification of Navier–Stokes. In 1907 his student Blasius solved the laminar flat-plate case by assuming the velocity profile has the same shape at every downstream station, a similarity solution (L7 slide 9). The result is

$$
f'''+ff''=0,
$$

where primes are derivatives with respect to $\eta=y/\delta$, $f=\psi/(U_e\delta)$ is a normalised stream function, and the Blasius thickness grows as the square root of distance:

$$
\frac{\delta}{x}=\left(\frac{2}{Re_x}\right)^{1/2},
\qquad\text{i.e.}\qquad
\delta=\sqrt{\frac{2\nu x}{U_e}}.
$$

The velocity is $u=\partial\psi/\partial y$. With $\psi=U_e\delta f(\eta)$ and $\partial\eta/\partial y=1/\delta$ at fixed $x$,

$$
u=U_e\delta\,f'(\eta)\,\frac{1}{\delta}=U_ef'(\eta),
$$

so $f'=u/U_e$ is the velocity profile. Differentiating again, $\partial u/\partial y=U_ef''/\delta$, so $f''$ is proportional to the shear stress. The derivation of the equation itself is in SESA3043 ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]).

The product $ff''$ makes the equation a nonlinear third-order ODE with no exact solution. The three boundary conditions are (L7 slide 10): the wall is a streamline, $f(0)=0$; no slip, $f'(0)=0$; and the free stream is recovered far away, $f'(\infty)=1$.

### Reformulation as a first-order system

A library ODE solver expects first-order equations, so define $f_0=f$, $f_1=f'$, $f_2=f''$. Then

$$
f_0'=f_1,
\qquad
f_1'=f_2,
\qquad
f_2'=f'''=-ff''=-f_0f_2.
$$

The first two define the variables; the third is the Blasius equation.

### Shooting

Two conditions are known at the wall and one at infinity, so the problem is solved by shooting (L7 slide 11): guess $f''(0)$, integrate outwards to a numerical "infinity" $\eta_{max}$ (6–8 should be enough), and compare $f'(\eta_{max})$ with 1. A guess of 0.3 gives $f'(8)=0.742$, too low; 0.6 gives 1.177, too high; trial and error converges on 0.4696.

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

`solve_ivp` uses RK45: a fourth-order and a fifth-order Runge–Kutta step whose difference estimates the error, so the step is shrunk when the error exceeds the tolerance and grown when it is comfortably below, which is adaptive step control. The name `trapz` used in the Blackboard code is `trapezoid` in newer SciPy.

The trial and error can be automated (L7 slide 13) by putting the integration inside a root finder for $r(g)=f'(\eta_{max};g)-1$. The secant method, starting from 0.3 and 0.6, gives

| Iteration | $f''(0)$ | $f'(8)-1$ |
|---|---|---|
| 1 | 0.477808 | $+1.16\times10^{-2}$ |
| 2 | 0.469248 | $-5.0\times10^{-4}$ |
| 3 | 0.469601 | $+1.5\times10^{-6}$ |
| 4 | 0.4695999885 | $+1.8\times10^{-10}$ |

converging in four iterations to $f''(0)=0.469600$.

![[dam_blasius_shooting.png|900]]

### Results and the flat-plate formulas

The thicknesses, in units of $\delta$, are $\delta^*/\delta=\int_0^\infty(1-f')\,\mathrm d\eta=1.2168$, $\theta/\delta=\int_0^\infty f'(1-f')\,\mathrm d\eta=0.4696$, and the classic shape factor $H=\delta^*/\theta=2.591$. The edge of the layer, $u/U_e=0.99$, is at $\eta=3.47$.

These give the flat-plate formulas of [[SESA2029 A1 - Digital Design and the Role of CFD and FEA|A1]]. Since $\delta=\sqrt2\,x/\sqrt{Re_x}$,

$$
\frac{\delta^*}{x}=1.2168\sqrt2\,Re_x^{-1/2}=1.7208\,Re_x^{-1/2},
\qquad
\frac{\theta}{x}=0.4696\sqrt2\,Re_x^{-1/2}=0.6641\,Re_x^{-1/2},
$$

$$
\frac{\delta_{99}}{x}=3.472\sqrt2\,Re_x^{-1/2}=4.91\,Re_x^{-1/2}.
$$

The wall shear stress is $\tau_w=\mu U_ef''(0)/\delta$, so

$$
C_f=\frac{\tau_w}{\tfrac12\rho U_e^2}=\frac{2\nu f''(0)}{U_e\delta}=\frac{2f''(0)}{\sqrt{2Re_x}}=\sqrt2\times0.4696\,Re_x^{-1/2}=0.664\,Re_x^{-1/2}.
$$

> [!check] Momentum balance: $\theta/\delta$ must equal $f''(0)$
> For zero pressure gradient the momentum integral equation is $\mathrm d\theta/\mathrm dx=C_f/2$ ([[Momentum Integral Equation]]). With $\theta=(\theta/\delta)\sqrt{2\nu x/U_e}$, $\mathrm d\theta/\mathrm dx=(\theta/\delta)\,\delta/2x$; with $C_f/2=\nu f''(0)/(U_e\delta)$, equating gives $\theta/\delta=2x\nu f''(0)/(U_e\delta^2)=f''(0)$ because $\delta^2=2\nu x/U_e$. The numerical $\theta/\delta=0.46960$ and $f''(0)=0.46960$ agree to five figures, an independent check on both the integration and the trapezoid rule.

The numerical parameters need testing. With $\eta_{max}=4$ the converged $f''(0)$ becomes 0.4712 and the shape factor 2.5934, because the domain is too small; 6 is the traditional value and 8 is better (2.59112, unchanged at 10). Loosening the tolerance from $10^{-10}$ to $10^{-6}$ changes nothing to five figures. But only 101 output points makes the trapezoid integration give 2.593; 1001 points give 2.5911.

In the coursework, the CFD laminar profiles can be compared with Blasius by plotting $u/U_e$ against $y/\delta^*$ at several stations, with Blasius as a line and CFD as symbols. If the similarity assumption holds, the profiles collapse once the boundary layer is fully developed.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]
- Next: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Concepts: [[Runge-Kutta Methods]] · [[Shooting Method and the Blasius Solution]] · [[Truncation Error and Order of Accuracy]]
- Boundary layers: [[SESA2022 T2 - Boundary Layers]] · [[Displacement and Momentum Thickness]] · [[Momentum Integral Equation]]

## Sources

- `All_lectures_as_delivered.pdf`, L7 (slides 3–14), with transcript `SESA2029 Lecture 2025-10-23.txt` (Prof N. Sandham; live Blasius demonstration, code `Lecture7_Blasius_solution.py` on Blackboard)
- The RK4 polynomial and the three-point backward gains checked in SymPy; Blasius values, secant iterations and parameter tests recomputed with SciPy `solve_ivp`. Figures: `01 - Notes/Figures/generate_dam_a6_figures.py`

## Self-study tasks

### Core

- [ ] Show that the predictor–corrector scheme is second order using $R=\lambda f$ (L7 slide 5; 2025-10-23, ll. 126–160). → [[#2. The predictor–corrector scheme (RK2)]] · [[SESA2029 CFD Worked Examples#Q8: RK2 characteristic polynomial|Worked examples Q8]]
- [ ] Verify that RK4 reproduces five Taylor terms for $R=\lambda f$ (exercise, L7 slide 6). → [[#RK4 in four lines]]
- [ ] Run the Blasius code and find $f''(0)$ by shooting, then vary the tolerances, the output array size and $\eta_{max}$ (L7 slide 13; 2025-10-23, ll. 541–580). → [[#Shooting]] · [[#Results and the flat-plate formulas]]
- [ ] Coursework lab 3: compare your laminar CFD profiles with Blasius (L7 slide 9). → [[#Results and the flat-plate formulas]]
- [ ] Blasius boundary-layer numbers (example sheet). → [[SESA2029 CFD Worked Examples#Q9: Blasius boundary-layer numbers|Worked examples Q9]]

### Further practice

- [ ] Explain why the three-point backward scheme needs a starting method, and show that it is second order only with $R$ at $n+1$ (suggested, not lecturer-set). → [[#1. The three-point backward scheme in time]]
- [ ] Show that RK2 is unstable on the imaginary axis and find the RK4 limit $2\sqrt2$ (suggested, not lecturer-set). → [[#Stability regions]]
- [ ] Automate the shooting with a secant or bisection root finder (L7 slide 13, option a). → [[#Shooting]]

## Transcript and slide slips

> [!warning] Slide and lecture slip: the explicit three-point backward scheme is first order (L7 slide 4; 2025-10-23, ll. 55–83)
> Where: [[#1. The three-point backward scheme in time]].
>
> Slide 4 writes the three-point backward scheme with "RHS at n" as an explicit method and labels it "2nd order in time", and the lecture says the same. Slide 3 lists it as "2nd order implicit", which is the correct version. With $R$ at $n$ the left side is centred at $t_{n+1}$ but the right side at $t_n$; the model equation gives $G=1+z-\tfrac12z^2+\dots$, first order, and the convergence test confirms slope 1. With $R$ at $n+1$, $G=1+z+\tfrac12z^2+\dots$, second order. Fluent's dual time stepping uses the implicit form, which is why it needs the inner pseudo-time loop.

> [!warning] Slide and lecture slip: how many Taylor terms RK recovers (L7 slide 5; 2025-10-23, ll. 161–175)
> Where: [[#2. The predictor–corrector scheme (RK2)]].
>
> The slide says the predictor–corrector "recovers the first 2 terms in a Taylor series" and that RK methods of order $n$ "recover the first $n$ terms". The algebra on the same slide shows RK2 recovering three terms ($1$, $\lambda\Delta t$, $(\lambda\Delta t)^2/2$): an order-$p$ scheme matches the series up to and including $(\lambda\Delta t)^p/p!$, which is $p+1$ terms counting the leading 1, or the first $p$ terms after it.
