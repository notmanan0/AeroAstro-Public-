---
title: "SESA2029 Formula Sheet"
module: "SESA2029 Digital Aerospace Methods"
type: formula
aliases: ["SESA2029 formulae", "Digital Aerospace Methods formula sheet"]
tags: [sesa2029, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources/CFD/All_lectures_as_delivered.pdf", "02 - Sources/FEM Lectures/"]
---

# SESA2029 Formula Sheet

Everything on one page, organised by part. Each heading links to its topic note. The exam provides the key matrices; this sheet is for revision and quick lookup.

## Part A: CFD

### Finite differences ([[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]])
$$
f_{j\pm1} = f_j\pm hf'_j+\frac{h^2}{2}f''_j\pm\frac{h^3}{6}f'''_j+\dots,\qquad f_{j-2} = f_j-2hf'_j+2h^2f''_j-\frac{4h^3}{3}f'''_j+\dots
$$

| Scheme | Formula | Leading error |
|---|---|---|
| forward | $(f_{j+1}-f_j)/h$ | $-\tfrac h2f''$ |
| backward (upwind) | $(f_j-f_{j-1})/h$ | $+\tfrac h2f''$ |
| central | $(f_{j+1}-f_{j-1})/2h$ | $-\tfrac{h^2}{6}f'''$ |
| 2nd-order backward | $(f_{j-2}-4f_{j-1}+3f_j)/2h$ | $+\tfrac{h^2}{3}f'''$ |
| 2nd-order forward | $(-3f_j+4f_{j+1}-f_{j+2})/2h$ | $-\tfrac{h^2}{3}f'''$ |
| central 2nd derivative | $(f_{j-1}-2f_j+f_{j+1})/h^2$ | $-\tfrac{h^2}{12}f''''$ |

Order $p$: the error scales as $h^p$, so halving $h$ reduces it by $2^p$ (slope $-p$ against $N$ on log–log axes).

Trapezoid rule: $\int f\,dx\approx\sum\tfrac12(f_j+f_{j+1})h$.

### Heat equation and iteration ([[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]])
$$
\frac{\partial T}{\partial t} = \alpha\frac{\partial^2T}{\partial x^2},\qquad\alpha = \frac{k}{\rho c},\qquad\dot q = -k\frac{\partial T}{\partial x}
$$

$$
\text{Jacobi: }T_j^{n+1} = \tfrac12(T_{j-1}^n+T_{j+1}^n)\qquad\text{GS: }T_j^{n+1} = \tfrac12(T_{j-1}^{n+1}+T_{j+1}^n)\qquad\text{SOR: }T^{n+1} = (1-\omega)T^n+\omega\tilde T^{n+1}
$$

Residual: $R = \sqrt{\sum_j(T_{j-1}-2T_j+T_{j+1})^2}$. Under-relaxation: $\phi_{new} = \phi_{old}+\alpha\Delta\phi$ with $\alpha<1$.

### Time marching and stability ([[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]], [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]])
$$
\text{Explicit: }T_j^{n+1} = T_j^n+F(T_{j-1}^n-2T_j^n+T_{j+1}^n)\qquad\text{Implicit: }-FT_{j-1}^{n+1}+(1+2F)T_j^{n+1}-FT_{j+1}^{n+1} = T_j^n
$$

$$
f' = \lambda f,\ \lambda = \sigma+i\omega:\quad G_{\text{exp}} = |1+\lambda\Delta t|,\qquad G_{\text{imp}} = \frac{1}{|1-\lambda\Delta t|}
$$

$$
\text{FTCS heat: }G = |1-2F(1-\cos kh)|\Rightarrow F = \frac{\alpha\Delta t}{h^2}\le\frac12;\qquad\text{upwind: }G = |1-C(1-e^{-ikh})|\Rightarrow C = \frac{c\Delta t}{h}\le1
$$

Viscous CFL: $\nu\Delta t/h^2$. Worst mode: $kh = \pi$.

### Higher-order time integration ([[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]])
$$
\text{BDF2: }f^{n+1} = \frac{4f^n-f^{n-1}+2\Delta tR^n}{3}\qquad\text{RK2: }\tilde f = f^n+\tfrac{\Delta t}{2}R(f^n),\ f^{n+1} = f^n+\Delta tR(\tilde f)
$$

$$
\text{RK4: }f^{n+1} = f^n+\frac{\Delta t}{6}\left[R_1+2R_2+2R_3+R_4\right],\qquad G_{RKn} = \sum_{m=0}^{n}\frac{(\lambda\Delta t)^m}{m!}
$$

RK stability on the real axis: −2 (RK1, RK2), −2.51 (RK3), −2.79 (RK4). On the imaginary axis: $\sqrt3$ (RK3), $2\sqrt2$ (RK4).

### Blasius and flat-plate boundary layers ([[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]], [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]])
$$
f'''+ff'' = 0,\quad f(0) = f'(0) = 0,\ f'(\infty) = 1,\quad\eta = \frac y\delta,\ \delta = \sqrt{\frac{2\nu x}{U_e}},\quad f''(0) = 0.4696
$$

$$
\delta_{99} = \frac{4.91x}{\sqrt{Re_x}},\quad\delta^* = \frac{1.7208x}{\sqrt{Re_x}},\quad\theta = \frac{0.664x}{\sqrt{Re_x}},\quad H = 2.591,\quad C_f = \frac{0.664}{\sqrt{Re_x}}
$$

Turbulent: $\delta = 0.38x\,Re_x^{-1/5}$ and $C_f = 0.059\,Re_x^{-1/5}$.

### Governing equations ([[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]])
$$
\frac{\partial\phi}{\partial t}+\frac{\partial(\phi u)}{\partial x}+\frac{\partial(\phi v)}{\partial y} = \text{RHS},\quad\phi\in\{\rho,\rho u,\rho v,\rho E\};\qquad\frac{D\rho}{Dt} = -\rho\,\nabla\cdot\mathbf u
$$

$$
\frac{\partial u_i}{\partial x_i} = 0,\qquad\frac{\partial u_i}{\partial t}+\frac{\partial(u_iu_j)}{\partial x_j}+\frac1\rho\frac{\partial p}{\partial x_i} = \nu\frac{\partial^2u_i}{\partial x_j\partial x_j}\qquad\left(\nabla\cdot\mathbf u = 0,\ \ \mathbf u_t+\mathbf u\cdot\nabla\mathbf u+\frac{\nabla p}{\rho} = \nu\nabla^2\mathbf u\right)
$$

Newtonian fluid: $\sigma_{ij} = \mu\left(\dfrac{\partial u_i}{\partial x_j}+\dfrac{\partial u_j}{\partial x_i}\right)$ (i.e. $2\mu S_{ij}$). Vorticity: $\omega_z = v_x-u_y$.

### Turbulence ([[SESA2029 A8 - Turbulence, RANS and Turbulence Models]])
$$
\phi = \bar\phi+\phi',\quad\bar\phi = \lim_{T\to\infty}\frac1T\int_0^T\phi\,dt,\qquad-\overline{u'v'} = \nu_t\frac{\partial\bar u}{\partial y}
$$

$$
k\text{–}\varepsilon:\ \nu_t = C_\mu\frac{k^2}{\varepsilon},\ C_\mu = 0.09;\qquad k\text{–}\omega:\ \nu_t = \frac{k}{\omega};\qquad k = \tfrac12\overline{u_i'u_i'}
$$

$$
u_\tau = \sqrt{\tau_w/\rho},\quad u^+ = \frac{u}{u_\tau},\quad y^+ = \frac{yu_\tau}{\nu},\quad u^+ = y^+\ (y^+\lesssim5),\quad u^+ = 2.5\ln y^++5.24\ (\text{log law})
$$

First-cell sizing: $\tau_w = \tfrac12C_f\rho U^2$, then $y_1 = y_1^+\nu/u_\tau$. Resolved: $y_1^+\lesssim1$–5. Wall function: $30<y_1^+\lesssim200$. Never $8<y_1^+<30$.

### Finite volumes ([[SESA2029 A9 - Finite Volume Method]])
$$
\frac{\partial}{\partial t}\int_V\rho\,dV+\oint_S\rho\,\mathbf v\cdot\mathbf n\,dS = 0,\qquad\int_{-\Delta y/2}^{\Delta y/2}f\,dy = f_e\Delta y+f''_e\frac{\Delta y^3}{24}+\dots
$$

- UDS: $\phi_e = \phi_P$ (flow +) or $\phi_E$.
- CDS: $\phi_e = \lambda_e\phi_E+(1-\lambda_e)\phi_P$.
- 2nd-order upwind: $\phi_e = \tfrac12(3\phi_P-\phi_W)$.
- QUICK: $\phi_e = \tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W$.

### Pressure Poisson, mesh quality, DNS cost ([[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]], [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]])
$$
\frac{\partial}{\partial x_i}\left(\frac{\partial p}{\partial x_i}\right)^{n+1} = \frac{\partial}{\partial x_i}\left(\frac{\partial\tau_{ij}}{\partial x_j}-\frac{\partial(\rho u_iu_j)}{\partial x_j}\right)^{n+1}
$$

Mesh quality targets: skewness < 0.9; orthogonal quality > 0.2; non-orthogonality < 70°; aspect ratio average < 5, BL up to 10–200.

$$
\eta = (\nu^3/\varepsilon)^{1/4},\qquad\Lambda/\eta\propto Re^{3/4},\qquad N_{3D}\propto Re^{9/4},\qquad\text{cost}\propto Re^3
$$

### Finite-wing checks ([[SESA2029 A1 - Digital Design and the Role of CFD and FEA]])
$$
a = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)},\qquad C_{D_i} = \frac{C_L^2}{\pi eAR},\quad e = \frac1{1+\delta}
$$

## Part B: FEA

### Matrix displacement method ([[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]])
$$
\sigma = \frac FA,\ \varepsilon = \frac uL,\ \sigma = E\varepsilon\;\Rightarrow\;F = \frac{EA}{L}u,\qquad[K]^e_{bar} = \frac{EA}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix},\qquad\{F\} = [K]\{d\}
$$

Inclined bar: $\dfrac{EA}{L}\begin{bmatrix}c^2&cs&-c^2&-cs\\cs&s^2&-cs&-s^2\\-c^2&-cs&c^2&cs\\-cs&-s^2&cs&s^2\end{bmatrix}$. Strike rows and columns for zero DOF, then back-substitute for the reactions.

### Linear elastic analysis and yield ([[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]])
$$
\text{Tresca: }\max|\sigma_i-\sigma_j| = \sigma_Y,\qquad\text{von Mises: }\frac1{\sqrt2}\sqrt{(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2} = \sigma_Y,\qquad P_Y = P\frac{\sigma_Y}{\sigma_{e,max}}
$$

Rigid-body modes: 6 in 3D, 3 in 2D.

### Energy methods ([[SESA2029 B3 - Principle of Minimum Total Potential Energy]])
$$
\Pi = U+V,\quad U = \int_V\tfrac12\sigma\varepsilon\,dV\ (\text{spring }\tfrac12ku^2),\quad V = -\sum F_id_i,\quad\frac{\partial\Pi}{\partial d_i} = 0\Rightarrow\{F\} = [K]\{d\}
$$

$$
K_t = \frac{\sigma_{max}}{\sigma_{bulk}},\quad K_t = 1+\frac{2a}{b}\ (\text{ellipse};\ \text{circle}=3),\quad FoS = \frac{\sigma_Y}{\sigma_{max}},\quad K_{t,net}\approx2+(1-d/W)^3
$$

### Shape functions ([[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]])
$$
u = [N]\{d\},\quad\{\varepsilon\} = [B]\{d\},\quad[K] = \int_V[B]^T[D][B]\,dV
$$

- Linear: $N_1 = 1-\tfrac xL$, $N_2 = \tfrac xL$.
- Quadratic (origin at the mid-node): $N_{1,3} = \tfrac{2x^2}{L^2}\mp\tfrac xL$, $N_2 = 1-\tfrac{4x^2}{L^2}$.

### Beam element ([[SESA2029 B5 - Euler-Bernoulli Beam Element]])
$$
\frac MI = \frac\sigma y = \frac ER,\qquad\rho = \frac1R = v'',\qquad M = EI\rho,\qquad U = \frac12\int_0^LEI\rho^2dx
$$

$$
N_1 = 1-3\xi^2+2\xi^3,\ N_2 = L(\xi-2\xi^2+\xi^3),\ N_3 = 3\xi^2-2\xi^3,\ N_4 = L(-\xi^2+\xi^3)
$$

$$
\begin{Bmatrix}F_1\\M_1\\F_2\\M_2\end{Bmatrix} = \frac{EI}{L^3}\begin{bmatrix}12&6L&-12&6L\\6L&4L^2&-6L&2L^2\\-12&-6L&12&-6L\\6L&2L^2&-6L&4L^2\end{bmatrix}\begin{Bmatrix}v_1\\\theta_1\\v_2\\\theta_2\end{Bmatrix}
$$

Hand checks: tip load $\delta = PL^3/3EI$; UDL $\delta = wL^4/8EI$.

### 2D elements ([[SESA2029 B6 - 2D and 3D Elements]])
$$
[D]_{\sigma} = \frac{E}{1-\nu^2}\begin{bmatrix}1&\nu&0\\\nu&1&0\\0&0&\frac{1-\nu}2\end{bmatrix},\qquad[D]_{\varepsilon} = \frac{E}{(1+\nu)(1-2\nu)}\begin{bmatrix}1-\nu&\nu&0\\\nu&1-\nu&0\\0&0&\frac{1-2\nu}2\end{bmatrix}
$$

- Plane stress: $\varepsilon_z = -\frac\nu{1-\nu}(\varepsilon_x+\varepsilon_y)$. Plane strain: $\sigma_z = \nu(\sigma_x+\sigma_y)$.
- Shells when $t\le L/20$.
- Solid aspect ratio ≤ 3 (linear) or ≤ 5 (quadratic); ≥ 3 linear or 2 quadratic elements through the thickness.
- 2D element aspect ratio ≲ 2–4.

### Modal analysis ([[SESA2029 B8 - Modal Analysis]])
$$
[M]\{\ddot u\}+[K]\{u\} = 0,\quad([K]-\omega_i^2[M])\{\phi\}_i = 0,\quad f_i = \frac{\omega_i}{2\pi},\quad\omega_0\approx\sqrt{k/m}
$$

$$
\{\phi\}_i^T[M]\{\phi\}_j = \delta_{ij},\qquad\gamma_i = \{\phi\}_i^T[M]\{D\},\qquad M_{\mathrm{eff},i} = \frac{\gamma_i^2}{\{\phi\}_i^T[M]\{\phi\}_i}\quad(\textstyle\sum\to M_{total};\ \text{aim}>90\%)
$$

SDOF: $\ddot x+2\zeta\omega_0\dot x+\omega_0^2x = 0$ with $\zeta = c/2m\omega_0$ and $\omega_d = \omega_0\sqrt{1-\zeta^2}$.

### Nonlinear solution ([[SESA2029 B9 - Nonlinear FE Analysis]])
$$
\text{Direct substitution: }u_{i+1} = [k_0+k_N(u_i)]^{-1}P\qquad\text{Newton–Raphson: }u_{i+1} = u_i-\frac{R(u_i)}{K_T(u_i)},\ R = k(u)u-P,\ K_T = \frac{dR}{du}
$$

### Validation and model updating ([[SESA2029 B10 - FE Verification, Validation and Model Updating]])
- Free–free modal: exactly 6 modes at ≈0 Hz.
- Unit gravity: reactions equal the weight.
- Unit displacement: rigid motion with zero stress.
- Model updating: $y_{sim} = M(x)$, $y_{obs} = M(x)+\varepsilon$; find $x$ such that $y_{sim}\approx y_{obs}$. Frequencies within about 5%, MAC ≳ 0.8.
