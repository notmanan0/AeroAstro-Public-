---
title: "SESA2029 CFD Worked Examples"
module: "SESA2029 Digital Aerospace Methods"
type: tutorial
stream: "Part A: Computational Fluid Dynamics"
tags: [sesa2029, tutorial-solutions, cfd]
sheet: "Lecture worked examples and exam-style practice (CFD)"
theory_notes: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]", "[[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]", "[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]", "[[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]", "[[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]", "[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]", "[[SESA2029 A9 - Finite Volume Method]]", "[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
key_concepts: ["[[Taylor Table Method]]", "[[Jacobi, Gauss-Seidel and SOR Iteration]]", "[[Von Neumann Stability Analysis]]", "[[Runge-Kutta Methods]]", "[[Convective Interpolation Schemes]]"]
status: complete
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 CFD Worked Examples

> [!abstract] Sheet Info
> These are exam-style problems built from the lecture examples and the in-lecture example-sheet walk-throughs. The original example sheet and the mock paper are not in the vault. Every number was checked in Python. Each question lists the note to revise.

## Theory Links
- Theory notes: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] · [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]] · [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]] · [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]] · [[SESA2029 A9 - Finite Volume Method]]
- Key concepts: [[Taylor Table Method]] · [[Von Neumann Stability Analysis]] · [[Jacobi, Gauss-Seidel and SOR Iteration]]

## Q1: Two-point forward difference by Taylor table

*Find $a$ and $b$ in $f'_j = (af_{j+1}-bf_j)/h+\varepsilon$ and the order of the scheme.*

### Solution
1. Move everything except the error to the left: $hf'_j-af_{j+1}+bf_j = h\varepsilon$.
2. Use $f_{j+1} = f_j+hf'_j+\tfrac{h^2}{2}f''_j+\dots$ and tabulate:

| Term | $f_j$ | $hf'_j$ | $\frac{h^2}{2}f''_j$ |
|---|---|---|---|
| $hf'_j$ | 0 | 1 | 0 |
| $-af_{j+1}$ | $-a$ | $-a$ | $-a$ |
| $+bf_j$ | $b$ | 0 | 0 |
| sum | $b-a = 0$ | $1-a = 0$ | $-a\frac{h^2}{2}f''_j = h\varepsilon$ |

3. So $a = b = 1$, and $\varepsilon = -\dfrac h2f''_j$:

$$
f'_j = \frac{f_{j+1}-f_j}{h}-\frac h2f''_j\qquad\Rightarrow\qquad\textbf{first order}
$$

**Trap**: keep the signs consistent between the scheme and the table. A sign slip gives $b = -a$; that is harmless only if you then carry the sign through.

## Q2: Three-point one-sided schemes

*(a) Derive the best 3-point backward (upwind) scheme using $j-2$, $j-1$, $j$. (b) State the matching forward scheme.*

### Solution
(a) The full table is in [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] §5.
- Equations: $a+b+c = 0$, $1+2a+b = 0$, $4a+b = 0$.
- Solution: $a = \tfrac12$, $b = -2$, $c = \tfrac32$.

$$
f'_j = \frac{f_{j-2}-4f_{j-1}+3f_j}{2h}+\frac{h^2}{3}f'''_j\qquad(\text{second order})
$$

(b) By symmetry ($h\to-h$):

$$
f'_j = \frac{-3f_j+4f_{j+1}-f_{j+2}}{2h}-\frac{h^2}{3}f'''_j
$$

**Check with a quadratic**: take $f = x^2$ at $x_j = 0$ with $h = 1$. Then $f_{j-2} = 4$, $f_{j-1} = 1$, $f_j = 0$, and $(4-4+0)/2 = 0 = f'(0)$. ✓ (The scheme is exact for quadratics, since the error involves $f'''$.)

## Q3: Convergence rate from data

*A scheme gives errors 0.0180 and 0.00453 on grids of 32 and 64 points. What is its order? What error would 256 points give?*

### Solution
- Ratio $0.0180/0.00453 = 3.97\approx2^2$, so $p = \log_2(3.97) = 1.99$: **second order**.
- 256 points is two more doublings: $0.00453/16 = 2.8\times10^{-4}$. This matches the lecture table.

## Q4: Steady heat equation: set-up and first iterations

*For $T'' = 0$ on $[0,1]$ with $T_0 = 1200$ K, $T_8 = 300$ K, $h = 0.125$ and an initial guess of 300 K inside: (a) write the discrete equations; (b) do two Jacobi and two Gauss–Seidel sweeps; (c) do one SOR sweep with $\omega = 1.4$.*

### Solution
(a) The interior equations are $T_{j-1}-2T_j+T_{j+1} = 0$ ($j = 1..7$), plus $T_0 = 1200$ and $T_8 = 300$: a $9\times9$ tridiagonal system. The exact solution is $T = 1200-900x$, so $T_4 = 750$ K.

(b)
| Sweep | $T_1$ | $T_2$ | $T_3$ | $T_4$ | $T_5$ | $T_6$ | $T_7$ |
|---|---|---|---|---|---|---|---|
| Jacobi 1 | 750 | 300 | 300 | 300 | 300 | 300 | 300 |
| Jacobi 2 | 750 | 525 | 300 | 300 | 300 | 300 | 300 |
| Gauss–Seidel 1 | 750 | 525 | 412.5 | 356.25 | 328.13 | 314.06 | 307.03 |
| Gauss–Seidel 2 | 862.5 | 637.5 | 496.88 | 412.5 | 363.28 | 335.16 | 317.58 |

Jacobi spreads information one point per sweep. Gauss–Seidel carries it across the whole domain in one sweep, because it uses updated values.

(c) SOR, first point: $T_1 = (1-1.4)(300)+1.4\times\tfrac12(1200+300) = -120+1050 = 930$ K, then $T_2 = 741$, $T_3 = 608.7$, … It overshoots Gauss–Seidel deliberately, and reaches $R<10^{-5}$ in 35 sweeps against 105 for Gauss–Seidel and 215 for Jacobi.

## Q5: Explicit and implicit steps for the unsteady heat equation

*With $\alpha = 0.1$, $h = 0.125$, $\Delta t = 0.06$ and an adiabatic inner wall: (a) compute $F$; (b) take one explicit step from the initial state; (c) write the implicit system for one step.*

### Solution
(a) $F = \alpha\Delta t/h^2 = 0.1\times0.06/0.015625 = 0.384$. This is below $\tfrac12$, so the explicit scheme is stable.

(b) $T_1^1 = 300+0.384(1200-600+300) = 645.6$ K. The other interior points stay at 300 K (their neighbours are all 300). The adiabatic BC gives $T_8 = T_7 = 300$ K.

(c) $-0.384\,T_{j-1}^{1}+1.768\,T_j^{1}-0.384\,T_{j+1}^{1} = T_j^0$ for $j = 1..7$, with $T_0 = 1200$ and $T_8-T_7 = 0$. This is a tridiagonal $9\times9$ solve every step. It is unconditionally stable, first order in time, and gives 334.6 K at $t = 0.72$ against the converged 330.3 K.

## Q6: Von Neumann analysis of a new scheme

*Analyse FTCS for pure convection, $f_j^{n+1} = f_j^n-\tfrac C2(f_{j+1}^n-f_{j-1}^n)$.*

### Solution
Substitute $f_{j\pm1} = f_je^{\pm ikh}$:

$$
G = 1-\frac C2\left(e^{ikh}-e^{-ikh}\right) = 1-iC\sin kh,\qquad|G|^2 = 1+C^2\sin^2kh\ \ge1
$$

$|G|>1$ for every $kh\neq0,\pi$ and every $C>0$. The scheme is **unconditionally unstable**. That is why convection needs upwinding (stable for $C\le1$), Lax–Wendroff, or an RK3/RK4 time integrator, which enclose part of the imaginary axis.

## Q7: Time-step limits

*(a) Explicit upwind convection at $c = 50$ m/s with $h = 1$ mm. (b) Explicit FTCS diffusion of momentum with $\nu = 1.5\times10^{-5}$ m²/s and $h = 10\,\mu$m (a near-wall cell). (c) What changes if $h$ is halved?*

### Solution
(a) $C\le1$ gives $\Delta t\le h/c = 2\times10^{-5}$ s.

(b) $\nu\Delta t/h^2\le\tfrac12$ gives $\Delta t\le h^2/(2\nu) = (10^{-5})^2/(3\times10^{-5}) = 3.3\times10^{-6}$ s.

(c) The convective limit halves, but the diffusive limit **quarters**. Fine near-wall grids therefore make explicit viscous solvers impractical, which is why steady solvers are implicit.

## Q8: RK2 characteristic polynomial

*Show that the midpoint predictor–corrector is second order for $f' = \lambda f$.*

### Solution
- Predictor: $\tilde f = f^n(1+\tfrac12\lambda\Delta t)$.
- Corrector: $f^{n+1} = f^n+\Delta t\lambda\tilde f = f^n\left(1+\lambda\Delta t+\tfrac12(\lambda\Delta t)^2\right)$.

This matches $e^{\lambda\Delta t}$ up to $(\lambda\Delta t)^2/2!$, and the first wrong term is cubic. The local error is $O(\Delta t^3)$, so the global error is $O(\Delta t^2)$: **second order**.

Stability: $|1+z+z^2/2|\le1$ gives the real-axis limit $z = -2$.

## Q9: Blasius boundary-layer numbers

*Air with $U_e = 10$ m/s and $\nu = 1.5\times10^{-5}$ m²/s, at $x = 0.5$ m: find $\delta_{99}$, $\delta^*$, $\theta$, $H$ and $C_f$.*

### Solution
$Re_x = 10\times0.5/1.5\times10^{-5} = 3.33\times10^5$ (laminar), so $\sqrt{Re_x} = 577.4$.

| Quantity | Formula | Value |
|---|---|---|
| $\delta_{99}$ | $4.91x/\sqrt{Re_x}$ | 4.25 mm |
| $\delta^*$ | $1.7208x/\sqrt{Re_x}$ | 1.49 mm |
| $\theta$ | $0.664x/\sqrt{Re_x}$ | 0.575 mm |
| $H$ | $\delta^*/\theta$ | 2.59 |
| $C_f$ | $0.664/\sqrt{Re_x}$ | 0.00115 |

All of these come from the single shooting result $f''(0) = 0.4696$ ([[Shooting Method and the Blasius Solution]]).

## Q10: Expand the index-notation Navier–Stokes equations

*Write out $\dfrac{\partial u_i}{\partial t}+\dfrac{\partial(u_iu_j)}{\partial x_j}+\dfrac1\rho\dfrac{\partial p}{\partial x_i} = \nu\dfrac{\partial^2u_i}{\partial x_j\partial x_j}$ for $i = 2$ in 3D.*

### Solution
$$
\frac{\partial v}{\partial t}+\frac{\partial(vu)}{\partial x}+\frac{\partial(vv)}{\partial y}+\frac{\partial(vw)}{\partial z}+\frac1\rho\frac{\partial p}{\partial y} = \nu\left(\frac{\partial^2v}{\partial x^2}+\frac{\partial^2v}{\partial y^2}+\frac{\partial^2v}{\partial z^2}\right)
$$

$i$ is the free index (one equation per direction). $j$ is repeated, so it is summed over 1, 2, 3. Continuity, $\partial u_i/\partial x_i = u_x+v_y+w_z = 0$, is one equation.

## Q11: QUICK coefficients

*Show that QUICK on a uniform grid (flow left to right) gives $\phi_e = \tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W$.*

### Solution
Take U = P ($x = 0$), D = E ($x = 1$), UU = W ($x = -1$) and $x_e = \tfrac12$:

$$
g_1 = \frac{(\tfrac12-0)(\tfrac12+1)}{(1-0)(1+1)} = \frac38,\qquad g_2 = \frac{(\tfrac12-0)(1-\tfrac12)}{(0+1)(1+1)} = \frac18
$$

$$
\phi_e = \phi_P+\tfrac38(\phi_E-\phi_P)+\tfrac18(\phi_P-\phi_W) = \tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W
$$

**Check**: the coefficients sum to 1, so a uniform field is reproduced exactly. A parabola through W, P, E is also reproduced exactly.

## Q12: Midpoint-rule surface integral error

*Show that approximating $\int_{-\Delta y/2}^{\Delta y/2}f\,dy$ by $f_e\Delta y$ is second order.*

### Solution
Expand $f = f_e+f'_ey+f''_ey^2/2+\dots$ and integrate. The odd term vanishes over the symmetric interval:

$$
\int f\,dy = f_e\Delta y+f''_e\frac{\Delta y^3}{24}+\dots
$$

The error per face is $O(\Delta y^3)$. Summed over $O(1/\Delta y)$ faces, or per unit area, this is $O(\Delta y^2)$: **second order**.

## Q13: Cost of DNS

*By what factor do the grid points and the cost rise when $Re$ increases 10× (e.g. a wind-tunnel model to flight)?*

### Solution
- Points $\propto Re^{9/4}$: $10^{2.25} = 178\times$.
- Cost $\propto Re^3$: $1000\times$.

At constant computing growth this delays full DNS of flight Reynolds numbers by decades. That is why RANS, and increasingly DES/LES, are used ([[DNS, LES and Scale-Resolving Simulation]]).

## Q14: Short explain-questions (model answers)
- **Residual vs error?** The residual is how well the *discrete* equations are satisfied (the iteration measure). The error is the difference from the *exact* solution, and includes discretisation and modelling error. A zero residual on a coarse grid is still wrong.
- **Why no density-based solver for incompressible flow?** $D\rho/Dt = 0$ leaves no evolution equation for $\rho$. Continuity is a constraint, so pressure must be found by a pressure (Poisson) equation.
- **Why do Euler results lack drag rise and stall?** Euler has no viscosity: no no-slip, no boundary layers, no viscous separation.
- **What is the closure problem?** RANS averaging creates 6 Reynolds stresses (in 3D) with no equations. Equations for them need higher correlations without end, so a model is required.
- **Wall functions vs resolved walls?** Resolved: $y_1^+\lesssim1$–5, cells in the sublayer, used with SA or SST. Wall function: $30<y_1^+\lesssim200$, log law assumed, used with $k$–$\varepsilon$. Avoid $8<y_1^+<30$.
- **Structured vs unstructured?** Structured is accurate, efficient and hard to build. Unstructured is automatic and flexible, but less accurate and slower. Hybrid (inflation + tets) is the practical compromise.
- **SIMPLE in one sentence?** Guess the pressure, solve momentum, solve a pressure correction that enforces continuity, correct the velocities, and repeat with under-relaxation.
- **Three error types?** Modelling (equations ≠ reality), discretisation (grid and time step), iteration (unconverged).

## Sources
- Source: CFD lectures L3–L12 worked examples and the in-lecture example-sheet walk-through, `02 - Sources/CFD/All_lectures_as_delivered.pdf`; transcript `CFD.txt`
- Calculation notes: all values reproduced in Python (NumPy, SciPy `solve_ivp`)
