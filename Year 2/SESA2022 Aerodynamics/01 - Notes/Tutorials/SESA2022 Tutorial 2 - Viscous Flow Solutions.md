---
title: "SESA2022 Tutorial 2 - Viscous Flow Solutions"
module: "SESA2022 Aerodynamics"
type: tutorial
stream: "Topic 2: Incompressible Viscous Flow"
tags:
  - sesa2022
  - tutorial-solutions
  - boundary-layers
sheet: "Tutorial 2"
theory_notes: ["[[SESA2022 T2 - Boundary Layers]]"]
key_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]", "[[Virtual Origin Method]]"]
status: complete
sources: ["02 - Sources/BL/Tutorial2.pdf", "02 - Sources/BL/Tutorial_2_Solutions.pdf"]
---

# SESA2022 Tutorial 2 - Viscous Flow Solutions

> [!abstract] Sheet Info
> Sheet: Tutorial 2 (Viscous flow) · Given answers: Q2 $\delta\approx30$ mm, Q3 $A=2.5$, $B=-1.7$, Q4 $C_F=0.0073$, Q5 $C_D=0.0125$. All reproduced below ✔.

## Theory Links
- Theory notes: [[SESA2022 T2 - Boundary Layers]]
- Key concepts: [[Displacement and Momentum Thickness]], [[Momentum Integral Equation]], [[Virtual Origin Method]]

## Q1: Can an AUV hold depth as it slows?

> Most AUVs (e.g. Remus-100) have small **positive buoyancy** and use small adjustable-pitch wings to stay submerged.

### Solution
The wings produce a **downforce** $L = \tfrac12\rho A C_L U^2$ that balances the net buoyancy $B_{net}$:

$$
\tfrac12\rho AC_LU^2 = B_{net}\quad\Rightarrow\quad C_{L,req} = \frac{2B_{net}}{\rho AU^2}
$$

- As $U$ decreases, the required $C_L$ grows as $1/U^2$. The vehicle can pitch the wings to raise $C_L$, but only up to $C_{L,max}$ (stall).
- Below $U_{min} = \sqrt{2B_{net}/(\rho AC_{L,max})}$ the downforce cannot balance the buoyancy, so **the vehicle cannot maintain depth** and floats up. At zero speed it always surfaces, which is a deliberate fail-safe.

## Q2: BL thickness at the control surfaces

$L = 1.6$ m, $U = 2$ m/s, $\nu = 10^{-6}$ m²/s.

### Solution

$$
Re_L = \frac{UL}{\nu} = \frac{2(1.6)}{10^{-6}} = 3.2\times10^6
$$

$$
\text{Laminar: }\delta = \frac{4.91L}{\sqrt{Re_L}} = \frac{4.91(1.6)}{1789} = 4.4\text{ mm},\qquad \text{Turbulent: }\delta = \frac{0.38L}{Re_L^{1/5}} = \frac{0.608}{20.0} = \boxed{30.4\text{ mm}}
$$

The two estimates differ by a factor of about 7. Since $Re_L\approx3\times10^6 \gg Re_{x_T}\approx3\times10^5$ to $10^6$, the BL is **turbulent** over most of the hull, so use **$\delta\approx30$ mm**.

**Safety factor**: the correlation is empirical (flat plate, zero pressure gradient), while the hull has curvature, pressure gradients, appendages and roughness. So the control surfaces should extend well beyond 30 mm.

## Q3: Parabolic fit $u/U_\infty = A\eta + B\eta^2$

### (a) Fit and thicknesses
**Method (Python)**:
1. Read the laminar data and find $U_\infty$ and $\delta$ (the first point with $u\ge0.99U_\infty$).
2. Keep only data with $y\le\delta$ and non-dimensionalise.
3. Fit with `scipy.optimize.curve_fit(lambda e,A,B: A*e+B*e**2, eta, uU)`.

The result is **$A = 2.5$, $B = -1.7$** (2 s.f.). The fit is good but not perfect, and note that $A+B = 0.8 \ne 1$.

```python
from scipy.optimize import curve_fit
f = lambda eta, A, B: A*eta + B*eta**2
popt, _ = curve_fit(f, eta, uU)       # popt -> [2.5, -1.7]
```

Analytically, with $\eta = y/\delta$:

$$
\frac{\delta^*}{\delta} = \int_0^1(1-A\eta-B\eta^2)\,d\eta = 1-\frac A2-\frac B3 = 1-1.25+0.5667 = \boxed{0.3167}
$$

$$
\frac{\theta}{\delta} = \int_0^1(A\eta+B\eta^2)(1-A\eta-B\eta^2)\,d\eta = \frac A2+\frac B3-\frac{A^2}{3}-\frac{AB}{2}-\frac{B^2}{5}
$$

$$
= 1.25-0.5667-2.0833+2.125-0.578 = \boxed{0.1470}
$$

$H = 0.3167/0.1470 = 2.15$, which is laminar-like ($H>2$). The numerical `np.trapz` values from the data are very close.

### (b) Downstream station with $\delta = 4$ mm
The profile is **self-similar**, so $\delta^*/\delta$ and $\theta/\delta$ are unchanged:

$$
\delta^* = 0.3167(4) = \boxed{1.27\text{ mm}},\qquad \theta = 0.1470(4) = \boxed{0.588\text{ mm}}
$$

Check: generating a synthetic profile $u = U_\infty(A\eta+B\eta^2)$ on $y\in[0,4\text{ mm}]$ and integrating numerically gives the same values ✔.

## Q4: Thin aerofoil with transition at mid-chord

$Re_c = 6\times10^5$, $\alpha=0$, $x_T = 0.5c$. Find $C_F = D_F/(\tfrac12\rho U_\infty^2c)$.

### Solution
Approximate the foil as a flat plate. We don't know how the pressure gradient would change the BL. The mid-chord Reynolds number is

$$
Re_{x_T} = 0.5Re_c = 3\times10^5
$$

which is typical for transition.

**Step 1: laminar $\theta$ at $x_T$** (Blasius):

$$
\frac{\theta_T}{c} = \frac{0.664(0.5)}{\sqrt{3\times10^5}} = 6.06\times10^{-4}
$$

**Step 2: virtual origin.** Match the turbulent $\theta$ grown from $x_0$:

$$
0.037\frac{(x_T-x_0)/c}{\left[Re_c(x_T-x_0)/c\right]^{1/5}} = 6.06\times10^{-4}
$$

Solving (`fsolve`/`brentq`) gives $x_T-x_0 = 0.163c$, so $x_0 = 0.337c$. The correlation $x_0 = x_T(1-38Re_{x_T}^{-3/8})$ gives $0.331c$, which is close ✔.

**Step 3: TE momentum thickness** from the virtual origin, with $c-x_0 = 0.663c$:

$$
\frac{\theta_{TE}}{c} = \frac{0.037(0.663)}{(6\times10^5\times0.663)^{1/5}} = 1.86\times10^{-3}
$$

**Step 4: drag.** One surface has $D' = \rho U_\infty^2\theta_{TE}$, and there are **two surfaces**:

$$
C_F = \frac{2\rho U_\infty^2\theta_{TE}}{\tfrac12\rho U_\infty^2c} = \frac{4\theta_{TE}}{c} = 4(1.86\times10^{-3}) = 0.0074
$$

With the $0.036$ coefficient (as used in exam papers), $\theta_{TE}/c = 1.82\times10^{-3}$, giving $\boxed{C_F = 0.0073}$ ✔ (matches the given answer).

> [!tip] Sanity check
> Fully laminar gives $C_F = 2\times1.328/\sqrt{6\times10^5} = 0.0034$. Fully turbulent gives $2\times0.074/(6\times10^5)^{0.2} = 0.0105$. The transitional answer sits in between ✔.

## Q5: Drag from a wake survey

$u(z) = U_\infty\left(\tfrac34-\tfrac14\cos\frac{\pi z}{w}\right)$ for $-w\le z\le w$, $w = 0.02c$.

### Solution
Momentum deficit (the momentum-thickness of the wake):

$$
D' = \rho\int_{-w}^{w}u(U_\infty-u)\,dz = \rho U_\infty^2\int_{-w}^w\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dz
$$

Let $C=\cos(\pi z/w)$. Then

$$
\frac{u}{U}\left(1-\frac uU\right) = \left(\tfrac34-\tfrac C4\right)\left(\tfrac14+\tfrac C4\right) = \frac{3}{16}+\frac{C}{8}-\frac{C^2}{16}
$$

Over one full period, $\int_{-w}^wC\,dz = 0$ and $\int_{-w}^wC^2\,dz = w$. So

$$
\int_{-w}^w(\dots)dz = \frac{3}{16}(2w)-\frac{w}{16} = \frac{5w}{16}
$$

$$
C_D = \frac{D'}{\tfrac12\rho U_\infty^2c} = \frac{2(5w/16)}{c} = \frac{5}{8}(0.02) = \boxed{0.0125}\;✔
$$

This is the **total** (pressure + friction) drag, because the wake momentum deficit captures both.

## Sources
- Source sheet: `02 - Sources/BL/Tutorial2.pdf`; lecturer solutions `Tutorial_2_Solutions.pdf`
- Numbers verified in Python (see [[SESA2022 T2 - Boundary Layers]] for the method)
