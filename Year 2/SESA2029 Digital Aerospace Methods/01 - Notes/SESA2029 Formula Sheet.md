---
title: "SESA2029 Formula Sheet"
module: "SESA2029 Digital Aerospace Methods"
type: formula
aliases: ["SESA2029 formulae", "Digital Aerospace Methods formula sheet"]
tags: [sesa2029, formula, exam-prep]
status: lectured
sources: ["01 - Notes/Topics", "02 - Sources/CFD/All_lectures_as_delivered.pdf", "02 - Sources/FEM Lectures/", "02 - Sources/Lectures/ (lab videos)"]
---

# SESA2029 Formula Sheet

Sections follow the order of the topic notes (A1–A11, B1–B10, C1–C6, then the Navier–Stokes deep dive), and each heading links to its note. The exam paper prints the general formulae and element matrices at the end ([[SESA2029 B10 - FE Verification, Validation and Model Updating#5. The FEA part of the exam|B10 §5]]), so this sheet is for revision and quick lookup.

Notation in Part A: subscript $j$ (or $i,j$ in 2D) is the grid point and $h$ the uniform spacing; superscript $n$ is the time level in A4–A6 and the iteration count in A3, never a power. $F=\alpha\Delta t/h^2$ is the Fourier (diffusion) number, $C=c\Delta t/h$ the Courant number, and $z=\lambda\Delta t$ for the model equation $f'=\lambda f$, $\lambda=\sigma+i\omega$.

## Part A: CFD

### Design checks and first-cell height ([[SESA2029 A1 - Digital Design and the Role of CFD and FEA]])

The design cycle, digital twin and digital thread and the CFD workflow carry no formulae; the numbers below are the sanity checks for the coursework.

$$
AR=\frac{b}{\bar c}=2AR_s,\qquad\bar c=\tfrac12c_r(1+TR),\qquad TR=\frac{c_t}{c_r}
$$

$$
a=\frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)},\qquad C_{D_i}=\frac{C_L^2}{\pi eAR},\qquad e=\frac1{1+\delta}\le1
$$

Lifting line needs the full-span $AR$, not OpenVSP's half-wing $AR_s$; $a_0=2\pi$ per radian (thin aerofoil); $\tau,\delta$ are the non-elliptic loading corrections, $C_L=\pi AR\,B_1$, $\delta=\sum_{n\ge2}n(B_n/B_1)^2$.

First-cell height (zero pressure gradient flat plate, $\nu\approx1.5\times10^{-5}$ m²/s for air):

$$
Re_x=\frac{U_\infty x}{\nu},\quad\tau_w=\tfrac12C_f\rho U_\infty^2,\quad u_\tau=U_\infty\sqrt{\frac{C_f}{2}},\quad y_1=\frac{y_1^+\nu}{u_\tau}=\frac{y_1^+\,x}{Re_x\sqrt{C_f/2}}
$$

| Flow | $\delta$ | $C_f$ | $y_1$ |
|---|---|---|---|
| laminar | $4.91\,x\,Re_x^{-1/2}$ | $0.664\,Re_x^{-1/2}$ | $1.736\,y_1^+x\,Re_x^{-3/4}$ |
| turbulent | $0.38\,x\,Re_x^{-1/5}$ | $0.059\,Re_x^{-1/5}$ | $5.822\,y_1^+x\,Re_x^{-9/10}$ |

Target $y_1^+\approx1$ (resolved sublayer) or $30<y_1^+\lesssim200$ (wall function), never the buffer layer; then check that 10–20 cells fit inside $\delta$. Boundary-layer thickness in first-cell heights: $\delta/y_1=2.83\,Re_x^{1/4}/y_1^+$ (laminar) and $0.0653\,Re_x^{7/10}/y_1^+$ (turbulent).

### Finite differences ([[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]])

$$
f_{j\pm1} = f_j\pm hf'_j+\frac{h^2}{2}f''_j\pm\frac{h^3}{6}f'''_j+\frac{h^4}{24}f''''_j\pm\dots,\qquad f_{j-2} = f_j-2hf'_j+2h^2f''_j-\frac{4h^3}{3}f'''_j+\dots
$$

Each stencil is written as $f'_j=(\text{scheme})+\varepsilon$; the order is the power of $h$ in $\varepsilon$ (uniform $h$, smooth $f$).

| Scheme | Formula | Error $\varepsilon$ | Order |
|---|---|---|---|
| forward | $(f_{j+1}-f_j)/h$ | $-\tfrac h2f''_j$ | 1 |
| backward (upwind for $c>0$) | $(f_j-f_{j-1})/h$ | $+\tfrac h2f''_j$ | 1 |
| central | $(f_{j+1}-f_{j-1})/2h$ | $-\tfrac{h^2}{6}f'''_j$ | 2 |
| 2nd-order backward (three-point upwind) | $(f_{j-2}-4f_{j-1}+3f_j)/2h$ | $+\tfrac{h^2}{3}f'''_j$ | 2 |
| 2nd-order forward | $(-3f_j+4f_{j+1}-f_{j+2})/2h$ | $+\tfrac{h^2}{3}f'''_j$ | 2 |
| central second derivative | $(f_{j-1}-2f_j+f_{j+1})/h^2$ | $-\tfrac{h^2}{12}f''''_j$ | 2 |

Taylor table: multiply the scheme by $h$, expand each $f_{j+k}$ with $kh$ in place of $h$, set as many column sums to zero as there are unknown coefficients; the next column is $h\varepsilon$.

Order from data: $\varepsilon\propto h^p$, so halving $h$ divides the error by $2^p$ and $p=\log_2[\varepsilon(h)/\varepsilon(h/2)]$ (slope $-p$ against $N$ on log–log axes).

Non-uniform grid ($h_+=x_{j+1}-x_j$, $h_-=x_j-x_{j-1}$): $f''_j\approx\left[\frac{f_{j+1}-f_j}{h_+}-\frac{f_j-f_{j-1}}{h_-}\right]\Big/\tfrac12(h_++h_-)$ has leading error $\tfrac13(h_+-h_-)f'''_j$: an abrupt change of cell size drops it to first order locally, so grow cells gradually.

Trapezoid rule: $\int f\,dx\approx h\left[\tfrac12(f_0+f_N)+\sum_{j=1}^{N-1}f_j\right]$ ($N$ intervals, $N+1$ points).

### Heat equation and iteration ([[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]])

$$
\frac{\partial T}{\partial t} = \alpha\frac{\partial^2T}{\partial x^2},\qquad\alpha = \frac{k}{\rho c_p},\qquad\dot q = -k\frac{\partial T}{\partial x}
$$

Steady 1D, Dirichlet ends: $T_{j-1}-2T_j+T_{j+1}=0$ at interior points (tridiagonal, solvable by Gaussian elimination). 2D, equal spacing: $4T_{i,j}=T_{i-1,j}+T_{i+1,j}+T_{i,j-1}+T_{i,j+1}$ (six neighbours in 3D).

$$
\text{Jacobi: }T_j^{n+1} = \tfrac12(T_{j-1}^n+T_{j+1}^n)\qquad\text{Gauss–Seidel: }T_j^{n+1} = \tfrac12(T_{j-1}^{n+1}+T_{j+1}^n)\qquad\text{SOR: }T_j^{n+1} = (1-\omega)T_j^n+\omega\tilde T_j
$$

$\tilde T_j$ is the Gauss–Seidel value: $\omega=1$ is Gauss–Seidel, $1<\omega<2$ over-relaxes a smooth approach, $\omega<1$ under-relaxes an oscillating one. Gauss–Seidel overwrites in place; Jacobi needs a second array.

Residual: $R^n = \sqrt{\sum_j(T^n_{j-1}-2T^n_j+T^n_{j+1})^2}$. It measures how well the discrete equations balance, not the distance from the exact solution: judge convergence on the output quantity as well ([[Residual vs Solution Error]]).

### Time marching ([[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]])

Forward (explicit) or backward (implicit) difference in time, central in space, uniform grid, constant $\alpha$:

$$
\text{Explicit: }T_j^{n+1} = T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)\qquad\text{Implicit: }-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1} = T_j^n
$$

- Implicit means a tridiagonal solve every step.
- Dirichlet boundary: fix the value. Adiabatic (Neumann) boundary $\partial T/\partial x=0$: $T_N=T_{N-1}$.
- Both are first order in time, with opposite leading errors: $+\tfrac{\Delta t}{2}T_{tt}$ (explicit, at $n$) and $-\tfrac{\Delta t}{2}T_{tt}$ (implicit, at $n+1$).
- Explicit needs $\Delta t\le h^2/2\alpha$, so halving $h$ quarters the step. Implicit is stable for any step but not accurate for large ones.
- Model equation $f'=\lambda f$: $f=f_0e^{\sigma t}(\cos\omega t+i\sin\omega t)$, decaying for $\sigma<0$.

### Stability ([[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]])

Model equation:

$$
G_{\text{exp}} = |1+\lambda\Delta t|,\qquad G_{\text{imp}} = \frac{1}{|1-\lambda\Delta t|},\qquad\Delta t_{max}^{\text{exp}}=-\frac{2\sigma}{|\lambda|^2}\ (\sigma<0)
$$

Explicit Euler is stable inside the unit circle centred at $z=-1$ and never on the imaginary axis ($G^2=1+(\omega\Delta t)^2$); implicit Euler is stable outside the unit circle centred at $z=+1$, so for every decaying mode at any step.

Von Neumann (linear, constant coefficients, uniform periodic grid): substitute $f_j=e^{ikx_j}$, $f_{j\pm1}=f_je^{\pm ikh}$, use $e^{ikh}+e^{-ikh}=2\cos kh$, require $G\le1$ for every $kh$ (worst usually $kh=\pi$).

| Scheme | Gain | Stable when |
|---|---|---|
| explicit heat (FTCS) | $G=\lvert1-2F(1-\cos kh)\rvert$ | $F\le\tfrac12$ (1D) |
| explicit heat, 2D, equal spacing | $G=\lvert1-4F[\sin^2\tfrac{k_xh}{2}+\sin^2\tfrac{k_yh}{2}]\rvert$ | $F\le\tfrac14$ |
| implicit heat | $G=1/[1+2F(1-\cos kh)]$ | always |
| upwind convection, $c>0$ | $G^2=1-2C(1-C)(1-\cos kh)$ | $C\le1$ |
| downwind convection | $G^2=1+2C(1+C)(1-\cos kh)$ | never ($kh\ne0$) |
| central convection with forward Euler | $G=1-iC\sin kh$, $G^2=1+C^2\sin^2kh$ | never: unstable for every mode except $kh=0$ and $\pi$ |

| Number | Definition | Explicit limit |
|---|---|---|
| Courant (CFL) | $C=c\Delta t/h$ | $\le1$ (upwind) |
| Fourier | $F=\alpha\Delta t/h^2$ | $\le\tfrac12$ in 1D, $\le\tfrac14$ in 2D |
| viscous CFL | $\nu\Delta t/h^2$ | as $F$, with $\nu$ for $\alpha$ |

Cost of explicit diffusion: halving $h$ quarters $\Delta t$, so in 2D it costs $4\times4=16$ times the work to reach the same time (four times the cells, four times the steps). At $C=1$ upwind shifts the solution exactly one cell per step.

### Higher-order time integration ([[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]])

Three-point backward in time, $df/dt=R$:

$$
\frac{f^{n-1}-4f^n+3f^{n+1}}{2\Delta t}=R^{n+1}\quad(\text{implicit, 2nd order}),\qquad f^{n+1}=\frac{4f^n-f^{n-1}+2\Delta t\,R^n}{3}\quad(\text{explicit, only 1st order})
$$

With $R^{n+1}$, $G=1+z+\tfrac12z^2+\tfrac12z^3+\dots$; with $R^n$, $G=1+z-\tfrac12z^2+\dots$. Both need a one-step starter for the first step.

$$
\text{RK2: }\tilde f^{n+1/2} = f^n+\tfrac{\Delta t}{2}R(f^n),\quad f^{n+1} = f^n+\Delta t\,R(\tilde f^{n+1/2})\qquad\text{RK4: }f^{n+1} = f^n+\frac{\Delta t}{6}\left[R_1+2R_2+2R_3+R_4\right]
$$

RK4 stages: $f^*=f^n+\tfrac{\Delta t}2R(t^n,f^n)$, $f^{**}=f^n+\tfrac{\Delta t}2R(t^{n+1/2},f^*)$, $f^{***}=f^n+\Delta t\,R(t^{n+1/2},f^{**})$, last evaluation at $(t^{n+1},f^{***})$.

$$
G_{RKp} = \sum_{m=0}^{p}\frac{z^m}{m!}\quad(p\le4)
$$

Order $p$ means $G$ matches $e^z$ up to $z^p/p!$ (local error $O(\Delta t^{p+1})$, global $O(\Delta t^p)$).

| Scheme | Real-axis limit $\sigma\Delta t$ | Imaginary-axis limit $\omega\Delta t$ |
|---|---|---|
| Euler (RK1) | −2 | none |
| RK2 | −2 | none ($G^2=1+\tfrac14(\omega\Delta t)^4$) |
| RK3 | −2.51 | $\sqrt3$ |
| RK4 | −2.79 | $2\sqrt2$ |

### Blasius and flat-plate boundary layers ([[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]], [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]])

Laminar, zero pressure gradient, similarity:

$$
f'''+ff'' = 0,\quad f(0) = f'(0) = 0,\ f'(\infty) = 1,\quad\eta = \frac y\delta,\ \delta = \sqrt{\frac{2\nu x}{U_e}},\quad u=U_ef'(\eta),\quad f''(0) = 0.4696
$$

First-order system for shooting: $f_0'=f_1$, $f_1'=f_2$, $f_2'=-f_0f_2$; adjust $f''(0)$ until $f'(\eta_{max})=1$ ($\eta_{max}=4$ is too small).

$$
\delta_{99} = \frac{4.91x}{\sqrt{Re_x}},\quad\delta^* = \frac{1.7208x}{\sqrt{Re_x}},\quad\theta = \frac{0.664x}{\sqrt{Re_x}},\quad H = 2.591,\quad C_f = \frac{0.664}{\sqrt{Re_x}}
$$

Momentum-balance check: $\theta/\delta=f''(0)$. Turbulent: $\delta = 0.38x\,Re_x^{-1/5}$, $C_f = 0.059\,Re_x^{-1/5}$.

### Governing equations ([[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]])

Generic conservation law per unit volume (2D, unit depth, $\phi\in\{\rho,\rho u,\rho v,\rho E\}$):

$$
\frac{\partial\phi}{\partial t}+\frac{\partial(\phi u)}{\partial x}+\frac{\partial(\phi v)}{\partial y} = \text{sources and forces},\qquad\frac{D\rho}{Dt} = -\rho\,\nabla\cdot\mathbf u
$$

Incompressible ($D\rho/Dt=0$): $\partial u/\partial x+\partial v/\partial y=0$. Euler (inviscid), constant $\rho$:

$$
\frac{\partial u}{\partial t}+\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}=-\frac1\rho\frac{\partial p}{\partial x},\qquad\frac{\partial(uu)}{\partial x}+\frac{\partial(uv)}{\partial y}=u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}\ \ (\text{by continuity})
$$

Velocity gradient = strain rate + rotation: $\partial u_i/\partial x_j=S_{ij}+\Omega_{ij}$, $S_{ij}=\tfrac12(\partial u_i/\partial x_j+\partial u_j/\partial x_i)$; only $S_{ij}$ produces stress. Newtonian, incompressible: $\sigma_{ij} = 2\mu S_{ij}=\mu(\partial u_i/\partial x_j+\partial u_j/\partial x_i)$. Vorticity $\omega_z = v_x-u_y$.

Incompressible Navier–Stokes (constant $\rho$ and $\mu$):

$$
\frac{\partial u_i}{\partial x_i} = 0,\qquad\frac{\partial u_i}{\partial t}+\frac{\partial(u_iu_j)}{\partial x_j}+\frac1\rho\frac{\partial p}{\partial x_i} = \nu\frac{\partial^2u_i}{\partial x_j\partial x_j}\qquad\left(\nabla\cdot\mathbf u = 0,\ \ \mathbf u_t+\mathbf u\cdot\nabla\mathbf u+\frac{\nabla p}{\rho} = \nu\nabla^2\mathbf u\right)
$$

Repeated index: sum over 1–3. An Euler solution has slip walls and no boundary layers.

### Turbulence and y-plus guidance ([[SESA2029 A8 - Turbulence, RANS and Turbulence Models]])

$$
\phi = \bar\phi+\phi',\quad\bar\phi = \frac1T\int_0^T\phi\,dt\ (T\gg\text{eddy time}),\quad\overline{\phi'}=0,\quad\overline{\bar u v'}=0,\quad\overline{u'v'}\ne0
$$

RANS $x$-momentum (2D): the laminar equation for $\bar u,\bar v,\bar p$ plus $-\partial\overline{u'u'}/\partial x-\partial\overline{u'v'}/\partial y$ on the right. In 3D, 4 equations and 10 unknowns (6 independent Reynolds stresses): the closure problem.

$$
-\overline{u'v'} = \nu_t\frac{\partial\bar u}{\partial y},\qquad k = \tfrac12\left(\overline{u'^2}+\overline{v'^2}+\overline{w'^2}\right),\qquad\nu_t\ \text{a property of the flow, not the fluid}
$$

| Model | Extra equations | $\nu_t$ | Wall treatment |
|---|---|---|---|
| Spalart–Allmaras | 1 ($\tilde\nu$) | from $\tilde\nu$ | $y_1^+<5$ (wall-function versions $>30$) |
| $k$–$\varepsilon$ | 2 | $C_\mu k^2/\varepsilon$, $C_\mu=0.09$ | wall function, $30<y_1^+\lesssim200$ |
| $k$–$\omega$ | 2 ($\omega\propto\varepsilon/k$) | $k/\omega$ | $y_1^+\lesssim1$; sensitive to free-stream $\omega$ |
| SST | 2, blended | $k$–$\omega$ near wall, $k$–$\varepsilon$ outside | $y_1^+\lesssim1$ |
| Reynolds stress | 7 (6 stresses + $\varepsilon$) | none | wall-resolved |

For aerodynamics use SA or $k$–$\omega$ SST; never change the calibrated constants.

$$
u_\tau = \sqrt{\tau_w/\rho},\quad u^+ = \frac{u}{u_\tau},\quad y^+ = \frac{yu_\tau}{\nu},\quad u^+ = y^+\ (y^+\lesssim5),\quad u^+ = 2.5\ln y^++5.24\ (\text{log law},\ \kappa=0.4)
$$

Buffer layer $8<y^+<30$ in the course convention (from about 5 in many references): no first cell there. In the log layer $\nu_t=\kappa u_\tau y$, so $\nu_t/\nu=\kappa y^+$. Plot $y_1^+$ after solving and refine if needed.

### Finite volumes ([[SESA2029 A9 - Finite Volume Method]])

$$
\frac{\partial}{\partial t}\int_V\rho\,dV+\oint_S\rho\,\mathbf v\cdot\mathbf n\,dS = 0,\qquad(\rho u)_e\Delta y-(\rho u)_w\Delta y+(\rho v)_n\Delta x-(\rho v)_s\Delta x=0\ \ (\text{steady, Cartesian cell})
$$

Midpoint rule (compass notation P, E, W, N, S; faces e, w, n, s):

$$
\int_{-\Delta y/2}^{\Delta y/2}f\,dy = f_e\Delta y+f''_e\frac{\Delta y^3}{24}+\dots\quad(\text{second order});\qquad\int_Vq\,dV\approx q_P\Delta V
$$

Face interpolation (flow from W to E, uniform $h$ for the simplified forms):

| Scheme | $\phi_e$ | Leading error | Order |
|---|---|---|---|
| UDS | $\phi_P$ (flow +), $\phi_E$ (flow −) | $-\tfrac h2\phi'$ | 1, bounded, diffusive |
| CDS | $\lambda_e\phi_E+(1-\lambda_e)\phi_P$, $\lambda_e=\frac{x_e-x_P}{x_E-x_P}$ ($\tfrac12$ uniform) | $+\tfrac{h^2}{8}\phi''$ | 2, can oscillate |
| 2nd-order upwind | $\tfrac12(3\phi_P-\phi_W)$ | $-\tfrac{3h^2}{8}\phi''$ | 2 |
| QUICK | $\tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W$ | $+\tfrac{h^3}{16}\phi'''$ | 3 (flux still 2nd order with the midpoint rule) |

QUICK on a general grid: $\phi_e=\phi_U+g_1(\phi_D-\phi_U)+g_2(\phi_U-\phi_{UU})$ with $g_1=\tfrac38$, $g_2=\tfrac18$ on a uniform grid.

| Boundary | Condition |
|---|---|
| inflow | fluxes $\rho u,\rho v,\rho w$ given on the faces |
| no-slip wall | all velocity components zero on the face |
| symmetry plane $y=0$ (= inviscid wall) | $v=0$, $\partial u/\partial y=0$ |
| pressure outlet | static pressure fixed, the rest extrapolated |
| ghost cell | fictitious cell outside, filled by extrapolation so the interior stencil applies |

Typical Fluent mix: second-order upwind for momentum and pressure, first-order upwind for $k$ and $\varepsilon$; if it will not converge, check the grid, drop to first order to start, then lower the under-relaxation factors.

### Grids and pressure–velocity coupling ([[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]])

Structured: $(i,j,k)$ indexing, 4 (2D) or 6 (3D) neighbours, efficient and accurate, hard for complex shapes. Unstructured: automatic, any shape, slower, poor in boundary layers. Hybrid: inflation layers on walls, unstructured fill. Topologies: H (cascades), O (inviscid aerofoils), C (viscous aerofoils, wake resolved).

Pressure Poisson equation (incompressible, backward Euler, take $\partial/\partial x_i$ of momentum and use continuity at $n$ and $n+1$):

$$
\frac{\partial^2 p}{\partial x_i\partial x_i} = \frac{\partial^2}{\partial x_i\partial x_j}\left(\tau_{ij}-\rho u_iu_j\right)^{n+1},\qquad\nabla^2p=-\rho\left(\frac{\partial^2(uu)}{\partial x^2}+2\frac{\partial^2(uv)}{\partial x\,\partial y}+\frac{\partial^2(vv)}{\partial y^2}\right)\ (\text{2D, constant }\rho,\mu)
$$

Elliptic: pressure is set by the whole velocity field at once. SIMPLE loop: momentum predictor with the current pressure, then pressure correction, then velocity and mass-flux correction, repeated to convergence. SIMPLE needs under-relaxation, SIMPLEC tolerates larger factors, PISO adds correctors and needs none.

| | Segregated (SIMPLE family) | Coupled |
|---|---|---|
| order of solution | $u$, $v$, $w$, $p$, then turbulence, in turn | momentum and $p$ together, then turbulence |
| memory | low | about 4× |
| iterations | more | fewer, each more work |

Under-relaxation: $\phi_{new} = \phi_{old}+\alpha\Delta\phi$, $\alpha<1$ (Fluent defaults about 0.3 pressure, 0.7 momentum, 0.8 turbulence). For a fixed-point iteration $\phi\leftarrow g(\phi)$ the error factor is $1+\alpha(g'-1)$: converges for $0<\alpha<2/(1-g')$, fastest at $\alpha=1/(1-g')$ ($g'<1$).

Pressure-based is the default up to about Mach 4; density-based (march $\rho$, pressure from the equation of state) beyond, e.g. re-entry.

Aerodynamic centre from CFD (moments about the leading edge): $x_{ac}/c=-dC_{m,LE}/dC_L$; centre of pressure $x_{cp}/c=-C_{m,LE}/C_L$.

### Errors, verification, validation and mesh quality ([[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]])

| Error | What it is | Checked by |
|---|---|---|
| modelling | exact solution of the equations ≠ reality (e.g. turbulence model, Euler for a viscous shock) | validation against experiment |
| discretisation | discrete solution ≠ exact solution of the equations | grid study (verification) |
| iteration | iterations not converged to the discrete solution | residuals and outputs settling (verification) |

Round-off: double precision about $10^{-16}$ (use it), single $10^{-8}$. A first-order method halves the truncation error when $h$ halves, a second-order one quarters it.

| Mesh metric | Definition | Acceptable |
|---|---|---|
| skewness | departure from the equilateral cell of the same volume (0 ideal) | max < 0.9; vertex angles within 40°–140° (hex ideal 90°, tet 60°) |
| orthogonal quality | 0–1, 1 ideal (cosine-based rescaling of non-orthogonality) | min > 0.2 |
| non-orthogonality | angle between the centre-to-centre line and the face normal | < 60–70°; > 85° likely to diverge |
| aspect ratio | longest / shortest edge | average < 5 and < 5 in the main flow; < 20–100 in separations and vortices; inside boundary layers up to about 200 (steady) or 20 (unsteady); max < 200–300 |

Grid study: at least three grids with large steps in cell count (e.g. 80k, a few hundred k, 0.8–1M), each output plotted against cells or $N^{1/3}$. With refinement ratio $r$ per direction:

$$
p=\frac{\ln\left[(f_c-f_m)/(f_m-f_f)\right]}{\ln r},\qquad f_0\approx f_f+\frac{f_f-f_m}{r^p-1}
$$

DNS cost (equilibrium turbulence, $\varepsilon\sim U^3/\Lambda$):

$$
\eta = \left(\frac{\nu^3}{\varepsilon}\right)^{1/4},\qquad\frac{\Lambda}{\eta}\sim Re^{3/4},\qquad N_{3D}\sim Re^{9/4},\qquad\text{cost}\sim Re^3
$$

Doubling $Re$ costs about 8×. Hierarchy of rising cost and falling reliance on turbulence models: boundary-element methods (XFOIL), Euler, RANS, URANS, DES (RANS near walls, LES away), LES (resolve large eddies, model small), DNS.

## Part B: FEA

### Matrix displacement method ([[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]])

Linear elastic bar, axial force only, small displacements:

$$
\sigma = \frac FA,\ \varepsilon = \frac uL,\ \sigma = E\varepsilon\;\Rightarrow\;F = \frac{EA}{L}u,\qquad[K]^e_{bar} = \frac{EA}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix},\qquad\{F\} = [K]\{d\}
$$

Assembly: add each element's entries into the global rows and columns of its own DOF; shared nodes sum. Two bars in series on nodes 1–2–3:

$$
[K]=\begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\qquad(\text{square, symmetric, banded; singular until supports are applied})
$$

Inclined bar, $c=\cos\theta$, $s=\sin\theta$ with $\theta$ from the global $x$ axis, DOF $(u_i,v_i,u_j,v_j)$, extension $\delta=c(u_j-u_i)+s(v_j-v_i)$:

$$
[K]^e=\frac{EA}{L}\begin{bmatrix}c^2&cs&-c^2&-cs\\cs&s^2&-cs&-s^2\\-c^2&-cs&c^2&cs\\-cs&-s^2&cs&s^2\end{bmatrix}
$$

Boundary conditions: unknown reactions go in $\{F\}$, supports in $\{d\}$; strike out the row and column of each zero displacement, solve for the free DOF, then back-substitute the struck rows for the reactions and each element equation for member force $F^{(e)}=k_e(u_j-u_i)$ and stress $F^{(e)}/A_e$. Clamp: $v=\theta=0$; simple support: $v=0$ only.

### Linear elastic analysis and yield ([[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]])

Valid while the stress stays below yield everywhere and $[K]$ does not change with displacement.

$$
\text{Tresca: }\max|\sigma_i-\sigma_j| = \sigma_Y,\qquad\text{von Mises: }\sqrt{\tfrac12\left[(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2\right]} = \sigma_Y,\qquad P_Y = P\frac{\sigma_Y}{\sigma_{max}}
$$

$1\le\sigma_{Tresca}/\sigma_e\le2/\sqrt3=1.155$, so Tresca is the more conservative. $P_Y$ scales one linear run to first yield, using whichever criterion's peak.

- Rigid-body modes: 6 in 3D, 3 in 2D. Remove all of them and no more (block on a surface: $u_y=0$ along the bottom, $u_x=0$ at one point or on a symmetry line).
- Symmetry plane: zero displacement normal to the plane, free in it.
- Units: mm–N–MPa needs density in t/mm³, $\rho_{\mathrm{t/mm^3}}=\rho_{\mathrm{kg/m^3}}\times10^{-12}$ (steel $7.85\times10^{-9}$, aluminium $2.7\times10^{-9}$); $\rho=2700$ with mm geometry makes the mass $10^{12}$ too large and the frequencies $10^6$ too low.

### Energy methods ([[SESA2029 B3 - Principle of Minimum Total Potential Energy]])

Linear elastic, conservative loads, small displacements; the trial field satisfies the displacement boundary conditions.

$$
\Pi = U+V,\quad U = \int_V\tfrac12\sigma\varepsilon\,dV\ (\text{spring }\tfrac12k\Delta L^2),\quad V = -\sum F_id_i,\quad\frac{\partial\Pi}{\partial d_i} = 0\Rightarrow\{F\} = [K]\{d\},\quad\Pi_{min}=-\tfrac12\{F\}^T\{d\}=-U
$$

Two-node bar: $\Pi=\tfrac12k(u_{xj}-u_{xi})^2-F_{xi}u_{xi}-F_{xj}u_{xj}$ gives the bar matrix of B1. Strong form needs continuous second derivatives everywhere; the weak (integral) form needs them only on average.

$$
K_t = \frac{\sigma_{max}}{\sigma_{bulk}},\qquad K_t = 1+\frac{2a}{b}\ (\text{elliptical hole in a large plate, }a\text{ across the load; circle}=3),\qquad FoS = \frac{\sigma_Y}{\sigma_{max}}
$$

$\sigma_{bulk}$ is the far-field stress on the loaded boundary, never the minimum stress in the plate. Design standards ask for $FoS$ of 1.5 or 2.

### Shape functions ([[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]])

$$
u = [N]\{d\},\quad\{\varepsilon\} = [B]\{d\},\quad[K]^e = \int_V[B]^T[D][B]\,dV,\qquad N_i(x_j)=\delta_{ij},\quad\textstyle\sum_iN_i=1
$$

Shape functions come from a polynomial $u=a+bx(+cx^2)$ with the nodal values as generalised boundary conditions.

- Linear bar, nodes at $0$ and $L$: $N_1 = 1-\tfrac xL$, $N_2 = \tfrac xL$, $[B]=\left[-\tfrac1L\ \ \tfrac1L\right]$, giving $\tfrac{AE}{L}\left[\begin{smallmatrix}1&-1\\-1&1\end{smallmatrix}\right]$.
- Quadratic bar, three nodes at $-\tfrac L2$, $0$, $\tfrac L2$ (origin at the mid-node): $N_{1,3} = \tfrac{2x^2}{L^2}\mp\tfrac xL$, $N_2 = 1-\tfrac{4x^2}{L^2}$.
- h-refinement: more, smaller elements. p-refinement: higher polynomial order.
- Uniform axial load $q$ on a linear element of length $h$: $qh/2$ to each node. Hanging bar (root fixed, tip free): one quadratic element is exact, $u=\tfrac{q}{2AE}(2Lx-x^2)$; $N$ linear elements give exact nodal displacements but a root strain of $\tfrac{qL}{AE}\left(1-\tfrac1{2N}\right)$, first order in $h$.

### Beam element ([[SESA2029 B5 - Euler-Bernoulli Beam Element]])

Euler–Bernoulli (plane sections stay plane, no shear deformation), slender, small deflection:

$$
\frac MI = \frac\sigma y = \frac ER,\qquad\rho = \frac1R = \frac{d^2v}{dx^2},\qquad M = EI\rho,\qquad U = \frac12\int_0^LEI\rho^2dx
$$

DOF $\{d\}=\{v_1\ \theta_1\ v_2\ \theta_2\}^T$ with $\theta=dv/dx$, cubic $v$, $\xi=x/L$:

$$
N_1 = 1-3\xi^2+2\xi^3,\ N_2 = L(\xi-2\xi^2+\xi^3),\ N_3 = 3\xi^2-2\xi^3,\ N_4 = L(-\xi^2+\xi^3),\qquad[B]=\frac{d^2[N]}{dx^2}
$$

$$
\begin{Bmatrix}F_1\\M_1\\F_2\\M_2\end{Bmatrix} = \frac{EI}{L^3}\begin{bmatrix}12&6L&-12&6L\\6L&4L^2&-6L&2L^2\\-12&-6L&12&-6L\\6L&2L^2&-6L&4L^2\end{bmatrix}\begin{Bmatrix}v_1\\\theta_1\\v_2\\\theta_2\end{Bmatrix}
$$

Keep the force order $(F_1,M_1,F_2,M_2)$ matching the DOF order; overlap element blocks at shared nodes; put nodes at supports and point loads (the cubic element is then exact). Hand checks: tip load $\delta = PL^3/3EI$; UDL $\delta = wL^4/8EI$.

### 2D and 3D elements ([[SESA2029 B6 - 2D and 3D Elements]])

Plane stress ($\sigma_z=\tau_{xz}=\tau_{yz}=0$, thin, loaded in plane) and plane strain ($\varepsilon_z=\gamma_{xz}=\gamma_{yz}=0$, long or thick), linear isotropic, $\{\sigma_x\ \sigma_y\ \tau_{xy}\}^T=[D]\{\varepsilon_x\ \varepsilon_y\ \gamma_{xy}\}^T$:

$$
[D]_{\sigma} = \frac{E}{1-\nu^2}\begin{bmatrix}1&\nu&0\\\nu&1&0\\0&0&\frac{1-\nu}2\end{bmatrix},\qquad[D]_{\varepsilon} = \frac{E}{(1+\nu)(1-2\nu)}\begin{bmatrix}1-\nu&\nu&0\\\nu&1-\nu&0\\0&0&\frac{1-2\nu}2\end{bmatrix}
$$

Plane stress: $\varepsilon_z = -\frac\nu{1-\nu}(\varepsilon_x+\varepsilon_y)$. Plane strain: $\sigma_z = \nu(\sigma_x+\sigma_y)\ne0$.

| Category | Type | Nodes | DOF and capability |
|---|---|---|---|
| 1D | truss (bar) | 2 | axial force only |
| 1D | beam | 2 | 6 per node in 3D |
| 2D | plane stress or strain | 3 or 4 (6 or 8 quadratic) | $u,v$ per node, in plane |
| 2D | membrane | 3 or 4 | in-plane load only, any orientation in 3D |
| 2D | plate | 3, 4 or 8 | $w,\theta_x,\theta_y$; flat; bending |
| 2D | shell | 3 to 8 | membrane + bending, 5 or 6 per node |
| 3D | solid (tet, wedge, hex) | 4 to 20 | 3 translations per node, no rotations |

- Shells when $t\lesssim L/20$; through-thickness normal stress is not accurate in a shell.
- Triangles: CST (3 nodes, constant strain), LST (6 nodes); quads: 4-node bilinear (PLANE182), 8-node (PLANE183).
- Solids: aspect ratio ≤ 3 (linear) or ≤ 5 (quadratic); at least 3 linear or 2 quadratic elements through the thickness for bending.

### Meshing, convergence and mesh checks ([[SESA2029 B7 - Meshing, Convergence and Mesh Checks]])

| FE error | Source |
|---|---|
| numerical | round-off, digits kept, solver tolerance, unit scaling |
| discretisation | element type and number of elements |
| modelling | assumptions of the formulation (e.g. beam theory on a stubby part) |
| user | missing or wrong boundary conditions, mixed units |

| Model purpose | Mesh |
|---|---|
| loads (internal forces, aerodynamic loads) | coarsest |
| displacements; natural frequencies and modes | intermediate (modes need less than stresses) |
| peak stresses | finest, locally refined |

Refinement: global h, local h at stress raisers, p (raise the order, PLANE182 → PLANE183), adaptive; grade element sizes gradually. Converged when further refinement no longer changes the output at a fixed location.

Singularity (sharp re-entrant corner, crack tip, point load or point constraint): the peak never converges. At a 270° re-entrant corner $\sigma\propto r^{-0.456}$, so $\sigma_{peak}\propto h^{-0.456}$ and each halving of $h$ multiplies the peak by $2^{0.456}=1.37$. Read stresses away from it, add a fillet, or spread the load over an area.

Element quality: plane-element aspect ratio below about 2–4 (solids ≤ 3 linear, ≤ 5 quadratic); angles between sides away from 0° and 180°; avoid near-triangular quads, curved sides and off-centre mid-side nodes. Warnings may continue, errors must be fixed.

### Modal analysis ([[SESA2029 B8 - Modal Analysis]])

Linear, undamped, no applied load, harmonic motion $\{u\}=\{\phi\}_i\sin(\omega_it+\theta_i)$:

$$
[M]\{\ddot u\}+[K]\{u\} = 0,\quad([K]-\omega_i^2[M])\{\phi\}_i = 0,\quad\det([K]-\omega^2[M])=0,\quad f_i = \frac{\omega_i}{2\pi},\quad T_i=\frac1{f_i},\quad\omega_0\approx\sqrt{k/m}
$$

$$
\{\phi\}_i^T[M]\{\phi\}_j = \delta_{ij}\ (\text{mass-normalised}),\qquad\gamma_i = \{\phi\}_i^T[M]\{D\},\qquad M_{\mathrm{eff},i} = \frac{\gamma_i^2}{\{\phi\}_i^T[M]\{\phi\}_i}
$$

$\{D\}$ is a unit displacement in one global direction. $\sum_iM_{\mathrm{eff},i}=M_{total}$: extract modes until the cumulative effective mass passes about 90 %. Mode shapes and modal stresses are relative only. No density means $[M]=0$ and no modes. Stiffer or clamped means higher $f$; more mass means lower $f$.

SDOF: $\ddot x+2\zeta\omega_0\dot x+\omega_0^2x = 0$ with $\zeta = c/2m\omega_0$ and $\omega_d = \omega_0\sqrt{1-\zeta^2}$ ($\zeta<1$).

### Nonlinear solution ([[SESA2029 B9 - Nonlinear FE Analysis]])

$\{F(\{d\})\}=[K(\{d\})]\{d\}$. Sources: geometric (large deformation, $[B(\{d\})]$, follower forces), material (plasticity, time-independent; creep, time-dependent; nonlinear elastic, viscoelastic), boundary (contact, friction, deformation-dependent pressure).

Model problem $(k_0+k_N(u))u=P$ ($k_N>0$ hardening, $<0$ softening):

$$
\text{Direct substitution: }u_{i+1} = \frac{P}{k_0+k_N(u_i)},\ u_1=\frac P{k_0}\qquad\text{Newton–Raphson: }u_{i+1} = u_i-\frac{R(u_i)}{K_T(u_i)},\ R = k(u)u-P,\ K_T = \frac{dR}{du}
$$

| Method | Convergence near $u^*$ |
|---|---|
| direct substitution (secant from origin) | linear: $e_{i+1}\approx g'(u^*)e_i$, $g'=-Pk'(u)/k(u)^2$ |
| Newton–Raphson (tangent) | quadratic: $e_{i+1}\approx\dfrac{R''}{2K_T(u^*)}e_i^2$ |
| modified Newton–Raphson | reuses an old tangent; cheaper per step, slower |

Matrix form: $[K_T]\{\Delta d\}=\{F\}-\{F_{int}(\{d\})\}$ each iteration. In ANSYS: large-deflection on, substeps, Newton–Raphson option.

### Validation and model updating ([[SESA2029 B10 - FE Verification, Validation and Model Updating]])

Verification: is the model built right (units, elements, mesh, supports)? Validation: does it match the real structure (test under matching loads and supports)?

| Check | Pass criterion | Detects |
|---|---|---|
| free–free modal | exactly 6 modes at ≈0 Hz, then the flexible modes | unconnected parts (12 zero modes for a loose engine) |
| unit enforced displacement | rigid motion, zero element forces and stress | illegal grounding |
| unit gravity (1 g in $x$, $y$, $z$) | smooth displacements, reactions = weight | loosely connected DOF |
| thermal equilibrium | free expansion without stress under uniform $\Delta T$ | spurious constraints |

Correlation targets: natural frequencies within about 5 %, MAC ≳ 0.8. Model updating: $y_{sim} = M(x)$, $y_{obs} = M(x)+\varepsilon$; find $x$ with $y_{sim}\approx y_{obs}$ (deterministic: direct optimisation or sensitivity-based; stochastic: parameter distributions). Single mode, $f\propto\sqrt E$: $\Delta E/E=2\,\Delta f/f$.

## Part C: the APDL labs at a glance

The exam has no coding, so what transfers to the exam and the coursework report is the element choice, the hand checks and the checks on the output. Workflows: [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals|C1]] (processors, units, pitfalls), [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)|C2]] (lab 1), [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)|C3]] (lab 2), [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)|C4]] (lab 3), [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation|C5]] (sweeps), [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks|C6]] (B10 checks as commands).

| Element | Nodes, interpolation | Used for |
|---|---|---|
| COMBIN14 | 2, spring–damper (stiffness as real constant) | lab 1 spring warm-ups |
| BEAM188 / BEAM189 | 2 linear / 3 quadratic, Timoshenko (shear included) | lab 1 spar |
| PLANE182 / PLANE183 | 4 / 8 nodes; `KEYOPT(3)=3` plane stress with thickness | lab 2 plate |
| SHELL181 / SHELL281 | 4 linear / 8 quadratic, 6 DOF per node | lab 3 wing |

Processor cycle: begin level, `/PREP7` (element, material, geometry, mesh), `/SOLU` (supports, loads, `SOLVE`), `/POST1` (results). Units as in [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield|B2]]: labs 1–2 in mm–N–MPa, lab 3 in SI.

Cantilever spar (lab 1, clamped root, same total load $W$, Euler–Bernoulli hand checks):

$$
\delta_{tip}=\frac{Pa^2(3L-a)}{6EI}\ (\text{point load at }a),\qquad\frac{WL^3}{3EI}\ (\text{tip}),\qquad\frac{WL^3}{8EI}\ (\text{uniform}),\qquad0.0967\frac{WL^3}{EI}\ (\text{elliptical},\ q_0=\tfrac{4W}{\pi L})
$$

I-section about the axis parallel to the flanges: $I=\left[W_1H^3-(W_1-t_w)(H-2t_f)^3\right]/12$; check the section orientation (`/ESHAPE,1`) before using it. BEAM188 is linear, so the tip deflection needs many divisions (20 → 200 → 2000) to converge.

Plate with a hole (lab 2, plane stress, hole of diameter $d$ in width $W$, far-field tension $\sigma$):

$$
\sigma_{net}=\sigma\frac{W}{W-d},\qquad K_{t,net}\approx2+\left(1-\frac dW\right)^3\ (\text{Heywood}),\qquad K_{t,gross}=\frac{K_{t,net}}{1-d/W},\qquad\sigma_{max}=K_{t,net}\,\sigma_{net}=K_{t,gross}\,\sigma
$$

A round hole is not a singularity, so $K_t$ converges; state whether $K_t$ is net or gross. A hole near an edge needs FE.

Shell wing (lab 3, thin skin, clamped root):

$$
m\approx2\,c\,l\,t\,\rho,\qquad\sigma\propto\frac1t,\qquad FoS\propto t,\qquad m\propto t,\qquad\omega\propto\sqrt{\frac{E}{\rho}}\ (\text{independent of uniform }t)
$$

$$
t_{min}=\frac{n\,\sigma_0\,t_0}{\sigma_Y},\qquad m_{min}\propto\frac{\rho}{\sigma_Y}\quad(\text{target }FoS=n,\ \text{reference run }t_0,\sigma_0)
$$

Uniform cantilever first mode (hand check for modal runs, $m$ per unit length): $f_1=\dfrac{1.875^2}{2\pi}\sqrt{\dfrac{EI}{mL^4}}$.

| Symptom | Usual cause |
|---|---|
| no solution, zero pivot | rigid-body mode left: missing supports, or `D` applied to a partial selection |
| displacements $10^6$ too small | mm geometry with $E$ in Pa |
| frequencies absurdly low, or no modes | density in kg/m³ with mm geometry, or no density |
| more than 6 zero-frequency free–free modes | disconnected part, unmerged nodes |
| peak stress rising with every refinement | singularity (wing root corner, point load) |
| wing deflects the wrong way | pressure sign against the area normal |
| crash on a fine mesh | DOF or licence limit, or distorted trailing-edge elements |

## Navier–Stokes deep dive ([[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]])

Not lectured and not set; consistent with A2–A11.

Mass and momentum from a control volume (Reynolds transport and Gauss):

$$
\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)=0,\qquad\rho\frac{D\mathbf u}{Dt}=\nabla\cdot\boldsymbol\sigma+\rho\mathbf g,\qquad\boldsymbol\sigma=-p\mathbf I+\boldsymbol\tau
$$

Compressible Newtonian stress (Stokes' hypothesis); the last term vanishes for $\nabla\cdot\mathbf u=0$:

$$
\tau_{ij}=\mu\left(\frac{\partial u_i}{\partial x_j}+\frac{\partial u_j}{\partial x_i}\right)-\frac23\mu\frac{\partial u_k}{\partial x_k}\delta_{ij}
$$

$$
\frac{\partial\mathbf u^*}{\partial t^*}+(\mathbf u^*\cdot\nabla^*)\mathbf u^*=-\nabla^*p^*+\frac1{Re}\nabla^{*2}\mathbf u^*,\quad Re=\frac{UL}{\nu};\qquad\nabla^2p=-\rho\frac{\partial u_i}{\partial x_j}\frac{\partial u_j}{\partial x_i}\ (\text{incompressible})
$$

Character of each term: convection hyperbolic, diffusion parabolic, pressure elliptic.

| Time scheme | Order | Character |
|---|---|---|
| forward Euler | 1 | explicit, conditionally stable |
| backward Euler | 1 | matrix solve, unconditionally stable |
| Crank–Nicolson, $\tfrac12[\mathcal R(u^n)+\mathcal R(u^{n+1})]$ | 2 | matrix solve, stable, can ring |
| RK4 | 4 | explicit, larger stability region |

Explicit diffusion (5-point Laplacian $[f_{i+1,j}+f_{i-1,j}+f_{i,j+1}+f_{i,j-1}-4f_{i,j}]/h^2$): $G=1-4F\sin^2(kh/2)$ in 1D (one such term per direction in 2D), $F\le\tfrac12$ (1D), $F\le\tfrac14$ (2D), so $\Delta t\le h^2/4\nu$ and halving $h$ costs 16× the work in 2D. Central convection with forward Euler: $|G|^2=1+C^2\sin^2kh>1$ for every mode except $kh=0$ and $\pi$.

Upwind with forward Euler solves the modified equation

$$
f_t+cf_x=\nu_{num}f_{xx},\qquad\nu_{num}=\frac{ch}{2}(1-C),\qquad\frac{\nu_{num}}{\nu}=\frac{Pe_h}{2}(1-C),\qquad Pe_h=\frac{Uh}{\nu}
$$

| Convection scheme | Order | Numerical diffusion | Bounded |
|---|---|---|---|
| 1st-order upwind | 1 | large, $\tfrac{ch}{2}(1-C)$ | always |
| central | 2 | none (dispersive) | only if $Pe_h\le2$ |
| 2nd-order upwind / QUICK | 2 / 3 | small | nearly; needs a limiter |
| TVD / MUSCL with limiter | 2 (1 at extrema) | only near jumps | yes |

Chorin projection (time-accurate, incompressible):

$$
\mathbf u^*=\mathbf u^n+\Delta t\left[-(\mathbf u^n\cdot\nabla)\mathbf u^n+\nu\nabla^2\mathbf u^n\right],\qquad\nabla^2p^{n+1}=\frac{\rho}{\Delta t}\nabla\cdot\mathbf u^*,\qquad\mathbf u^{n+1}=\mathbf u^*-\frac{\Delta t}{\rho}\nabla p^{n+1}
$$

Walls: $\partial p/\partial n=0$, and pin one pressure value (the pure-Neumann Poisson matrix is singular). SIMPLE is the steady, under-relaxed counterpart, solving for a correction $p'$.

Collocated grid with $(p_{i+1}-p_{i-1})/2h$ cannot see a checkerboard $p=(-1)^{i+j}$; cures are the staggered (MAC) grid, with $u$ driven by $(p_{i+1,j}-p_{i,j})/h$ and discrete divergence zero to machine precision, or Rhie–Chow interpolation on a collocated grid (Fluent; PRESTO! is staggered-style). Ghost values for a wall half a cell away: $u_g=2U-u_{int}$ (moving lid), $u_g=-u_{int}$ (stationary wall).

| Explicit central MAC solver limit | Formula | Limit |
|---|---|---|
| CFL | $U\Delta t/h$ | $\lesssim1$ |
| diffusion number | $\nu\Delta t/h^2$ | $\le\tfrac14$ (2D) |
| cell Péclet | $Uh/\nu$ | $\le2$ |

Verification of the cavity solver: observed order $p=\ln[(f_{32}-f_{64})/(f_{64}-f_{128})]/\ln2\approx2$ and $f_\infty\approx f_{128}+(f_{128}-f_{64})/(2^p-1)$, as in [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality|A11]]. A code-to-code benchmark (Ghia et al.) is verification; validation needs experiment.
