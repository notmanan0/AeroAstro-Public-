---
title: "SESA2022 Formula Sheet"
module: "SESA2022 Aerodynamics"
type: formula
aliases: ["SESA2022 formulae", "Aerodynamics formula sheet"]
tags: [sesa2022, formula, exam-prep]
status: complete
coverage: "Topics 2–6, all lectured (2025-26); legacy compressible flow at the end"
sources: ["03 - Exams & Past Papers/SESA2022-202425-01-SESA2022.pdf (rubric, pp. 9–18)", "01 - Notes/Topics", "01 - Notes/Tutorials", "SESA2022 T6 formula-page list (21 Nov, ll. 12–37)"]
---

# SESA2022 Formula Sheet

Sections follow the topic notes, T2 to T6. Items marked ★ are not on the exam's formula pages, so learn them: for T2–T5 that means not on the 2024-25 rubric (pp. 9–18 of the paper), for T6 not in the list of static-stability formulae given in the exam (21 Nov, ll. 12–37). Angles in radians throughout unless stated.

## T2 Boundary layers ([[SESA2022 T2 - Boundary Layers]])

Incompressible, steady, 2D flat plate at zero pressure gradient ($U_e = U_\infty$) unless stated.

$$
\tau_w = \mu\left.\frac{\partial u}{\partial y}\right|_{y=0},\qquad c_f = \frac{\tau_w}{\tfrac12\rho U_\infty^2} = \frac{2\nu}{U_\infty^2}\left.\frac{\partial u}{\partial y}\right|_{y=0},\qquad Re_x = \frac{U_\infty x}{\nu}
$$

$$
\delta^* = \int_0^\infty\left(1-\frac{u}{U_\infty}\right)dy,\qquad \theta = \int_0^\infty\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dy,\qquad H = \frac{\delta^*}{\theta}
$$

With $\eta = y/\delta$ and $u/U_\infty = f(\eta)$: $\dfrac{\delta^*}{\delta} = \displaystyle\int_0^1(1-f)\,d\eta$, $\dfrac{\theta}{\delta} = \displaystyle\int_0^1f(1-f)\,d\eta$. $\delta = \delta_{99}$, where $u = 0.99U_\infty$ (interpolate in data). Laminar $H>2$, turbulent $H<2$.

Momentum integral equation (flat plate, laminar or turbulent, from a control volume):

$$
c_f = 2\frac{d\theta}{dx},\qquad D'(x) = \int_0^x\tau_w\,dx = \rho U_\infty^2\theta(x),\qquad C_F = \frac{D'}{\tfrac12\rho U_\infty^2L} = \frac{2\theta(L)}{L} = \frac1L\int_0^Lc_f\,dx
$$

$D'$ and $C_F$ are per unit span and per side: double for a plate wetted on both sides, multiply by span $b$ for $D$. The same $D' = \rho U_\infty^2\theta$ gives body drag from a wake traverse, taken where $p = p_\infty$.

★ Any assumed laminar profile $f(\eta)$, with $\hat\theta = \int_0^1f(1-f)\,d\eta$:

$$
\frac{\theta}{x} = c_f = \frac{\sqrt{2f'(0)\hat\theta}}{\sqrt{Re_x}},\qquad \frac{\delta}{x} = \frac{\theta/x}{\hat\theta},\qquad \frac{\delta^*}{x} = H\frac{\theta}{x}
$$

| Profile $u/U_\infty$ | $\delta/x$ | $\delta^*/x$ | $\theta/x$ and $c_f$ | $H$ |
|---|---|---|---|---|
| ★ Linear, $\eta$ | $3.46Re_x^{-1/2}$ | $1.732Re_x^{-1/2}$ | $0.577Re_x^{-1/2}$ | 3 |
| ★ Parabolic, $2\eta-\eta^2$ | $5.48Re_x^{-1/2}$ | $1.83Re_x^{-1/2}$ | $0.730Re_x^{-1/2}$ | 2.5 |
| Blasius (exact) | $4.91Re_x^{-1/2}$ | $1.721Re_x^{-1/2}$ | $0.664Re_x^{-1/2}$ | 2.59 |

Flat-plate correlations, used only when no profile or data is given (a question that says only "laminar" means Blasius):

| | Laminar (Blasius) | Turbulent ($n = 7$ power law + data) |
|---|---|---|
| $\delta/x$ | $4.91Re_x^{-1/2}$ | $0.38Re_x^{-1/5}$ |
| $\delta^*/x$ | $1.72Re_x^{-1/2}$ | $0.048Re_x^{-1/5}$ |
| $\theta/x$ | $0.664Re_x^{-1/2}$ | $0.037Re_x^{-1/5}$ (some papers $0.036$) |
| $c_f$ | $0.664Re_x^{-1/2}$ | $0.059Re_x^{-1/5}$ |
| $C_F$ (one side) | $1.328Re_L^{-1/2}$ | $0.074Re_L^{-1/5}$ |
| $H$ | 2.59 | 1.29 |

- ★ Reynolds-number ranges (smooth plate): laminar $Re_x<3\times10^5$, transitional $3\times10^5$–$10^6$, turbulent above. Laminar $\delta\propto x^{1/2}$, turbulent $\delta\propto x^{4/5}$.
- ★ Power law $u/U_\infty = \eta^{1/n}$ ($n$ an integer, fitted to points with $y/\delta\le1$; $n = 7$ only when no data): $\delta^*/\delta = \dfrac{1}{n+1}$, $\theta/\delta = \dfrac{n}{(n+1)(n+2)}$, $H = \dfrac{n+2}{n}$. It gives infinite $\tau_w$, so $c_f$ comes from a correlation.
- Wall units: $U_\tau = \sqrt{\tau_w/\rho} = U_\infty\sqrt{c_f/2}$, $y^+ = yU_\tau/\nu$, $U^+ = U/U_\tau$, viscous length $\nu/U_\tau$. Viscous sub-layer $U^+ = y^+$ for $y^+<5$; buffer layer $5<y^+<50$; log layer $U^+ = \frac1\kappa\ln y^++B$ for $y^+>50$ and $y/\delta<0.2$, with $\kappa = 0.39$, $B = 4.3$ (2024-25 rubric) or $\kappa = 0.4$, $B = 5.0$ (slides): use the paper's values. CFD wall grid: first point at $y^+\lesssim1$–$5$.
- [[Virtual Origin Method|Virtual origin]] (transition at $x_T$): $\theta$ is continuous, $\theta_{lam}(x_T) = \theta_{turb}(x_T-x_0)$, and the turbulent formulae use $x-x_0$. ★ Explicit with Blasius and $0.037$: $x_0 = x_T\left(1-36.9\,Re_{x_T}^{-3/8}\right)$; with $0.036$ the constant is $38.2$ ([[SESA2022 T2 - Boundary Layers#Matching condition|derivation]]). Check $0<x_0<x_T$.
- ★ Transitional plate, chord $c$, one side: $\theta(c) = 0.037(c-x_0)Re_{c-x_0}^{-1/5}$, $D' = \rho U_\infty^2\theta(c)$, $C_F = 0.074\left(1-\dfrac{x_0}{c}\right)Re_{c-x_0}^{-1/5}$. It must lie between the all-laminar and all-turbulent values.
- Separation: an adverse pressure gradient ($dp/dx>0$) drives $\partial u/\partial y|_0\to0$, so $\tau_w = 0$ at separation; a turbulent layer separates later (descriptive, [[SESA2022 T2 - Boundary Layers#8. Pressure gradients and separation|T2 §8]]).

## T3 Potential flow ([[SESA2022 T3 - Potential Flow]])

Steady, inviscid, irrotational, incompressible, 2D. Course convention: $x$–$z$ plane, $y$ into the page, $\Gamma>0$ clockwise, $\theta$ and $V_\theta$ anticlockwise from $+x$ ([[SESA2022 T3 - Potential Flow#1. Coordinates and conventions (important for signs)|T3 §1]]). Pre-2020 papers use $x$–$y$ with $v$ for $w$.

$$
u = \frac{\partial\psi}{\partial z} = \frac{\partial\phi}{\partial x},\quad w = -\frac{\partial\psi}{\partial x} = \frac{\partial\phi}{\partial z};\qquad V_r = \frac1r\frac{\partial\psi}{\partial\theta} = \frac{\partial\phi}{\partial r},\quad V_\theta = -\frac{\partial\psi}{\partial r} = \frac1r\frac{\partial\phi}{\partial\theta}
$$

$$
\frac{\partial u}{\partial x}+\frac{\partial w}{\partial z} = 0,\qquad \omega_y = \frac{\partial u}{\partial z}-\frac{\partial w}{\partial x}\ (\text{clockwise positive}),\qquad \nabla^2\psi = \nabla^2\phi = 0
$$

Polar continuity $\frac1r\frac{\partial(rV_r)}{\partial r}+\frac1r\frac{\partial V_\theta}{\partial\theta} = 0$; polar vorticity $\frac1r\frac{\partial(rV_\theta)}{\partial r}-\frac1r\frac{\partial V_r}{\partial\theta}$, which is anticlockwise positive ($= -\omega_y$), so only its zero matters for an irrotationality test. $x = r\cos\theta$, $z = r\sin\theta$; $u = V_r\cos\theta-V_\theta\sin\theta$, $w = V_r\sin\theta+V_\theta\cos\theta$. Element at $(x_0,z_0)$: $r = \sqrt{(x-x_0)^2+(z-z_0)^2}$, $\theta = \tan^{-1}\frac{z-z_0}{x-x_0}$.

| Element | $\psi$ | $\phi$ | Velocity |
|---|---|---|---|
| Uniform flow at $\alpha$ | $U_\infty(z\cos\alpha-x\sin\alpha)$ | $U_\infty(x\cos\alpha+z\sin\alpha)$ | $(U_\infty\cos\alpha,\,U_\infty\sin\alpha)$ |
| Source $\Lambda>0$ / sink $\Lambda<0$ (papers: $Q$) | $\dfrac{\Lambda}{2\pi}\theta$ | $\dfrac{\Lambda}{2\pi}\ln r$ | $V_r = \dfrac{\Lambda}{2\pi r}$ |
| Vortex, $\Gamma>0$ clockwise | $\dfrac{\Gamma}{2\pi}\ln r$ | $-\dfrac{\Gamma}{2\pi}\theta$ | $V_\theta = -\dfrac{\Gamma}{2\pi r}$ |
| Doublet $\kappa = \Lambda l$ (source left, sink right) | $-\dfrac{\kappa}{2\pi}\dfrac{\sin\theta}{r}$ | $\dfrac{\kappa}{2\pi}\dfrac{\cos\theta}{r}$ | $V_r = -\dfrac{\kappa\cos\theta}{2\pi r^2}$, $V_\theta = -\dfrac{\kappa\sin\theta}{2\pi r^2}$ |
| ★ Corner, wedge angle $\pi/n$ (past papers) | $U r^n\sin n\theta$ | $U r^n\cos n\theta$ | $V_r = nUr^{n-1}\cos n\theta$, $V_\theta = -nUr^{n-1}\sin n\theta$ |

$$
p+\tfrac12\rho V^2 = p_\infty+\tfrac12\rho U_\infty^2,\qquad C_p = \frac{p-p_\infty}{\tfrac12\rho U_\infty^2} = 1-\frac{u^2+w^2}{U_\infty^2} = 1-\frac{V_r^2+V_\theta^2}{U_\infty^2}
$$

With no freestream, use the stated $U_{ref}$, $p_{ref}$. Body streamline: $\psi_{body} = \psi(\text{stagnation point})$, or the streamline through a given point; no flow crosses a streamline.

- ★ Rankine half-body (uniform + source at the origin): stagnation point $r_s = \dfrac{\Lambda}{2\pi U_\infty}$ at $\theta = \pi$; body $\psi = \Lambda/2$, $r = \dfrac{\Lambda(1-\theta/\pi)}{2U_\infty\sin\theta}$; width far downstream $\Lambda/U_\infty$; $C_p = -4/\pi^2$ on the body above the source.
- ★ Cylinder (uniform + doublet), $R^2 = \kappa/(2\pi V_\infty)$: $\psi = V_\infty r\sin\theta\left(1-\dfrac{R^2}{r^2}\right)$; on $r = R$, $V_\theta = -2V_\infty\sin\theta$ and $C_p = 1-4\sin^2\theta$ (stagnation at $0,\pi$; $C_p = -3$ at the top; $C_p = 0$ at $30^\circ$, $150^\circ$).
- ★ Rankine oval (uniform $V_\infty$, source $\Lambda$ at $x = -b$, sink at $+b$), body $\psi = 0$: ends $x = \pm\sqrt{b^2+\Lambda b/(\pi V_\infty)}$; top from $V_\infty z_{top}+\frac\Lambda\pi\tan^{-1}\frac{z_{top}}{b}-\frac\Lambda2 = 0$ (solve numerically), slender ($z_{top}\ll b$) $z_{top}\approx\dfrac{\pi b}{2+2\pi bV_\infty/\Lambda}$; top speed $u_{top} = V_\infty+\dfrac{\Lambda}{\pi}\dfrac{b}{b^2+z_{top}^2}$.
- ★ Lifting cylinder (uniform + doublet + vortex): $\psi = V_\infty r\sin\theta\left(1-\dfrac{R^2}{r^2}\right)+\dfrac{\Gamma}{2\pi}\ln\dfrac rR$, surface $V_\theta = -2V_\infty\sin\theta-\dfrac{\Gamma}{2\pi R}$, $C_p = 1-\left(2\sin\theta+\dfrac{\Gamma}{2\pi RV_\infty}\right)^2$. Stagnation points on the surface at $\sin\theta = -\Gamma/(4\pi V_\infty R)$ if $\Gamma\le4\pi V_\infty R$; otherwise off it at $\theta = -\pi/2$, $r = \dfrac{\Gamma}{4\pi V_\infty}+\sqrt{\left(\dfrac{\Gamma}{4\pi V_\infty}\right)^2-R^2}$.
- ★ Forces from surface $C_p$ (cylinder, reference length $2R$): $c_d = -\frac12\int_0^{2\pi}C_p\cos\theta\,d\theta = 0$, $c_l = -\frac12\int_0^{2\pi}C_p\sin\theta\,d\theta = \dfrac{\Gamma}{RV_\infty}$.
- Kutta–Joukowski, any 2D body with circulation $\Gamma$: $L' = \rho V_\infty\Gamma$. D'Alembert: zero drag on any closed 2D body in this flow.
- ★ [[Method of Images|Images]] at a plane wall: a source or sink reflects with the same sign, a vortex (or a doublet with axis normal to the wall) with the opposite sign; a 90° corner needs three images. Vortex $\Gamma$ at height $a$ above a wall in $U_\infty$: $u(x,0) = U_\infty-\dfrac{\Gamma a}{\pi(x^2+a^2)}$, $C_p(x,0) = 2\Delta-\Delta^2$ with $\Delta = \dfrac{\Gamma a}{\pi U_\infty(x^2+a^2)}$.

## T4 Thin aerofoil theory ([[SESA2022 T4 - Thin Aerofoil Theory]])

Inviscid, incompressible; thin section with small camber $z(x)$; small $\alpha$ in radians; flap angle $\eta$ positive trailing edge down (past papers write $\delta$ or $\phi$); lower case $c_l$, $c_m$ for sections.

$$
L' = \tfrac12\rho V_\infty^2c\,c_l = \rho V_\infty\Gamma,\qquad \Gamma = \int_0^c\gamma\,dx,\qquad \gamma = V_{upper}-V_{lower},\qquad \Delta C_p = C_{p,l}-C_{p,u} = \frac{2\gamma}{V_\infty}
$$

- ★ Linearised pressure coefficient ($v\ll V_\infty$ along the stream): $C_p\approx-2v/V_\infty$.
- Kutta condition: $\gamma(TE) = V_1-V_2 = 0$. Kelvin: $D\Gamma/Dt = 0$, so a starting vortex $-\Gamma$ is shed.
- ★ Fundamental equation (tangency on the chord, $\gamma(c) = 0$): $\dfrac{1}{2\pi}\displaystyle\int_0^c\frac{\gamma(\xi)\,d\xi}{x-\xi} = V_\infty\left(\alpha-\frac{dz}{dx}\right)$.
- Transformation: $\xi = \frac c2(1-\cos\theta)$, $x = \frac c2(1-\cos\theta_0)$, LE at $\theta = 0$, TE at $\pi$. Hinge or point at $x/c$: $\cos\theta_0 = 1-2x/c$.
- ★ Glauert integrals (principal values; given in the exam, 29 Oct, ll. 485–493): $\displaystyle\int_0^\pi\frac{\cos n\theta\,d\theta}{\cos\theta-\cos\theta_0} = \frac{\pi\sin n\theta_0}{\sin\theta_0}$, $\displaystyle\int_0^\pi\frac{\sin n\theta\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = -\pi\cos n\theta_0$. Orthogonality: $\int_0^\pi\cos m\theta\cos n\theta\,d\theta = \int_0^\pi\sin m\theta\sin n\theta\,d\theta = \frac\pi2\delta_{mn}$ ($m,n\ge1$); $\int_0^\pi\cos n\theta\,d\theta = 0$.
- ★ Flat plate: $\gamma(\theta) = 2V_\infty\alpha\dfrac{1+\cos\theta}{\sin\theta}$, i.e. $\gamma(x) = 2V_\infty\alpha\sqrt{(c-x)/x}$; $c_l = 2\pi\alpha$, $c_{m,le} = -c_l/4$, $x_{cp} = c/4$.

General cambered section:

$$
\gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum_{n=1}^\infty A_n\sin n\theta\right),\qquad A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}\,d\theta_0,\qquad A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0\ (n\ge1)
$$

$$
c_l = \pi(2A_0+A_1) = 2\pi(\alpha-\alpha_{L=0}),\qquad \alpha_{L=0} = \frac1\pi\int_0^\pi\frac{dz}{dx}(1-\cos\theta_0)\,d\theta_0,\qquad \frac{dc_l}{d\alpha} = 2\pi
$$

$$
c_{m,c/4} = c_{m,le}+\frac{c_l}{4} = \frac\pi4(A_2-A_1)\ (\text{independent of }\alpha:\ c/4\text{ is the AC}),\qquad c_{m,le} = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right)
$$

- ★ Centre of pressure: $\dfrac{x_{cp}}{c} = -\dfrac{c_{m,le}}{c_l} = \dfrac14-\dfrac{c_{m,c/4}}{c_l}$; it moves with $\alpha$ and runs to $\pm\infty$ as $c_l\to0$.
- ★ Ideal angle (no LE loading, $A_0 = 0$): $\alpha_{ideal} = \dfrac1\pi\displaystyle\int_0^\pi\frac{dz}{dx}\,d\theta_0$.
- ★ Circulation: $\Gamma = \tfrac12cV_\infty c_l = \pi cV_\infty\left(A_0+\tfrac12A_1\right)$.
- ★ Parabolic camber $z/c = \epsilon\,(x/c)(1-x/c)$ (NACA $m$5xx: $\epsilon = 4m$): $dz/dx = \epsilon\cos\theta_0$, $A_0 = \alpha$, $A_1 = \epsilon$, $A_{n\ge2} = 0$, $c_l = 2\pi\alpha+\pi\epsilon$, $\alpha_{L=0} = -\epsilon/2$, $\alpha_{ideal} = 0$, $c_{m,c/4} = -\pi\epsilon/4$, maximum camber $\epsilon/4$ at $c/2$.
- ★ Plain trailing-edge flap, flap-chord ratio $E$, hinge at $x_h = c(1-E)$, $\cos\theta_h = 2E-1$: $A_0 = \alpha+\dfrac\eta\pi(\pi-\theta_h)$, $A_n = \dfrac{2\eta}{n\pi}\sin n\theta_h$, so

$$
\frac{\partial c_l}{\partial\eta} = 2(\pi-\theta_h+\sin\theta_h),\qquad \frac{\partial c_{m,c/4}}{\partial\eta} = \tfrac12\sin\theta_h(\cos\theta_h-1),\qquad \alpha_{L=0} = -\frac\eta\pi(\pi-\theta_h+\sin\theta_h)
$$

| Flap | $\theta_h$ | $\partial c_l/\partial\eta$ | $\partial c_{m,c/4}/\partial\eta$ | $\partial\alpha_{L=0}/\partial\eta$ |
|---|---|---|---|---|
| 20 % ($E = 0.2$) | 2.214 rad | 3.455 | $-0.640$ | $-0.550$ |
| 25 % ($E = 0.25$) | $2\pi/3$ | $2\pi/3+\sqrt3 = 3.826$ | $-3\sqrt3/8 = -0.6495$ | $-0.609$ |

- ★ Stall speed: $V_{stall} = \sqrt{2W/(\rho_\infty SC_{L,max})}$. Flaps make $\alpha_{L=0}$ more negative and raise $C_{L,max}$; slats leave $\alpha_{L=0}$ unchanged and delay stall.

## T5 Finite wing theory ([[SESA2022 T5 - Finite Wing Theory]])

High aspect ratio, unswept, incompressible, attached flow; radians; downwash $w<0$; $AR = b^2/S$; $y$ from $-b/2$ to $b/2$.

- ★ Biot–Savart, straight segment at perpendicular distance $h$: $V = \dfrac{\Gamma}{4\pi h}(\cos\theta_1-\cos\theta_2)$; infinite filament $\Gamma/(2\pi h)$, semi-infinite starting opposite the point $\Gamma/(4\pi h)$. Helmholtz: a filament cannot end in the fluid, and $\Gamma$ is constant along it.
- ★ Horseshoe vortex, trailing legs at $y = \pm s$, point at distances $h_1 = s+y_0$ and $h_2 = s-y_0$: $w(y_0) = -\dfrac{\Gamma}{4\pi}\dfrac{h_1+h_2}{h_1h_2}$; at the centre $-\Gamma/(\pi b)$.

$$
\alpha_{eff} = \alpha-\alpha_i,\qquad \alpha_i = -\frac{w(y_0)}{V_\infty},\qquad c_l = a_0(\alpha_{eff}-\alpha_{L=0}),\qquad D_i' = L'\alpha_i,\qquad L = \rho V_\infty\int_{-b/2}^{b/2}\Gamma\,dy
$$

$a_0 = 2\pi$ from TAT unless given. ★ Section lift $c_l(y_0) = \dfrac{2\Gamma(y_0)}{V_\infty c(y_0)}$.

- ★ Trailing-sheet downwash: $w(y_0) = -\dfrac{1}{4\pi}\displaystyle\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y}$, $\alpha_i(y_0) = \dfrac{1}{4\pi V_\infty}\displaystyle\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y}$.
- ★ Prandtl's lifting-line equation ($\Gamma = 0$ at both tips): $\dfrac{2\Gamma(y_0)}{a_0V_\infty c(y_0)}+\dfrac{1}{4\pi V_\infty}\displaystyle\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y} = \alpha(y_0)-\alpha_{L=0}(y_0)$.

Fourier solution, $y = -\frac b2\cos\theta$:

$$
\Gamma(\theta) = 2bV_\infty\sum_{n=1}^N B_n\sin n\theta,\qquad \sum_n B_n\sin n\theta_0\left[\frac{4b}{a_0c(\theta_0)}+\frac{n}{\sin\theta_0}\right] = \alpha(\theta_0)-\alpha_{L=0}(\theta_0),\qquad \alpha_i(\theta_0) = \sum_n nB_n\frac{\sin n\theta_0}{\sin\theta_0}
$$

$$
C_L = \pi AR\,B_1,\qquad C_{D_i} = \pi AR\sum_n nB_n^2 = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi eAR},\qquad \delta = \sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2\ge0,\qquad e = \frac{1}{1+\delta}
$$

★ Not on the rubric: the Fourier form of the lifting-line equation, the $\alpha_i$ series, $C_L = \pi AR\,B_1$ (a short derivation that can be asked) and $C_{D_i} = \pi AR\sum nB_n^2$. The rubric gives $\Gamma(\theta)$, $C_{D_i}$, $e$ and $\delta$.

Typical $\delta\approx0.05$ ($0$ to $0.3$); $e = 0.75$ to $1$; $\delta$ is smallest near taper ratio $0.3$–$0.4$. $\delta$ (induced-drag factor) and $\tau$ (lift-slope factor) are different: $\tau\approx3\delta$, so $\delta = \tau$ is a rough assumption used only when a question states it.

Elliptic lift distribution ($B_1$ only, $\delta = 0$, minimum $C_{D_i}$ for a given span and lift):

$$
\Gamma(y) = \Gamma_0\sqrt{1-\left(\frac{2y}{b}\right)^2},\quad \Gamma_0 = 2bV_\infty B_1,\quad \alpha_i = \frac{C_L}{\pi AR}\ \text{and}\ w = -\frac{\Gamma_0}{2b}\ \text{(constant)},\quad L = \frac\pi4\rho V_\infty\Gamma_0b,\quad C_{D_i} = \frac{C_L^2}{\pi AR}
$$

★ Only $\Gamma(y)$ is on the rubric; the rest follows from $B_1$ alone.

- ★ Reached by an untwisted elliptic planform ($c\propto\Gamma$, every section at $c_l = C_L$) or by twisting a rectangular wing: $\alpha(y_0)-\alpha_{L=0}(y_0) = \dfrac{C_L}{\pi AR}\left[1+\dfrac{4AR}{a_0}\sqrt{1-(2y_0/b)^2}\right]$, so $c_l(0) = \dfrac4\pi C_L$ and washout $= \dfrac{4C_L}{\pi a_0}$ ($= \dfrac{2C_L}{\pi^2}$ for $a_0 = 2\pi$). Exact at one $C_L$ only.

Lift slope:

$$
a = \frac{dC_L}{d\alpha} = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)},\qquad C_L = a(\bar\alpha-\bar\alpha_{L=0}),\qquad \bar\alpha = \frac1S\int_{-b/2}^{b/2}\alpha\,c\,dy,\quad \bar\alpha_{L=0} = \frac1S\int_{-b/2}^{b/2}\alpha_{L=0}\,c\,dy
$$

- Elliptic wing: $\tau = 0$, $a = a_0/(1+a_0/\pi AR)$. ★ Run backwards for the section slope: $a_0 = \dfrac{a}{1-a(1+\tau)/(\pi AR)}$.
- ★ Mean induced angle consistent with the lift slope: $\bar\alpha_i = C_L(1+\tau)/(\pi AR)$, so a typical section works at $\alpha_{eff} = \alpha-\bar\alpha_i$ with $c_l\approx C_L$ (e.g. untwisted $AR = 8$, $\tau = 0.055$, $\alpha = 5^\circ$: $C_L = 0.434$, $\bar\alpha_i = 1.04^\circ$, $\alpha_{eff} = 3.96^\circ$). The rubric writes $\alpha_i = C_L/(\pi eAR)$, the same thing when $\delta = \tau$.
- ★ Helmbold (low $AR$ blend): $a = \dfrac{a_0}{\sqrt{1+(a_0/\pi AR)^2}+a_0/(\pi AR)}$.

Drag:

$$
C_D = C_{D_0}+C_{D_i} = C_{D_0}+\frac{C_L^2}{\pi eAR},\qquad C_{D_0} = C_F+C_{D_p},\qquad \left(\frac LD\right)_{max} = \frac12\sqrt{\frac{\pi eAR}{C_{D_0}}}\ \text{at}\ C_L^* = \sqrt{\pi eAR\,C_{D_0}}
$$

- ★ At $(L/D)_{max}$, $C_{D_i} = C_{D_0}$ and $C_D = 2C_{D_0}$.
- ★ Span loading, level flight ($L = W$): $D_i = \dfrac{W^2}{\pi e\,qb^2} = \dfrac{2}{\pi e\rho V^2}\left(\dfrac{W}{b}\right)^2$ ($e = 1$ for elliptic loading). Power $P = DV$.

## T6 Static stability ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]])

Steady, small angles in radians, thrust and drag through the CG, symmetric tail ($M_{T_0} = 0$), linear lift and hinge-moment models; $h$, $h_0$ are CG and wing-AC positions aft of the datum as fractions of $c$; nose-up moments positive; $A$ is the aspect ratio and $\alpha_0$ the zero-lift angle (T5: $AR$, $\alpha_{L=0}$).

Trim (force normal to the path, moment about the CG):

$$
C_{L^*} = C_L+C_{L_T}\frac{S_T}{S} = C_W\cos\gamma,\qquad C_W = \frac{W}{\tfrac12\rho V^2S},\qquad C_{M_0}+C_{L^*}(h-h_0)-C_{L_T}K = 0,\qquad K = \frac{S_Tl}{Sc}
$$

$$
C_L = C_{L_\alpha}(\alpha-\alpha_0),\quad C_{L_\alpha} = a_0\frac{\pi Ae}{\pi Ae+a_0},\qquad \epsilon = \frac{C_L}{\pi Ae} = \epsilon_\alpha(\alpha-\alpha_0),\quad \epsilon_\alpha = \frac{C_{L_\alpha}}{\pi Ae}
$$

$$
\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T},\qquad C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\qquad C_{M_H} = b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta
$$

- ★ Trim order: $C_W$, $C_{L^*}$, $K$; $C_{L_T} = [C_{M_0}+C_{L^*}(h-h_0)]/K$; $C_L = C_{L^*}-C_{L_T}S_T/S$; $\alpha = \alpha_0+C_L/C_{L_\alpha}$; $\alpha_{T_{eff}}$; then the controls. Rearranged for the CG: $h = h_0+(C_{L_T}K-C_{M_0})/C_{L^*}$; for the speed: $V = \sqrt{2W\cos\gamma/(\rho SC_{L^*})}$.
- ★ Stick fixed ($\beta = 0$): $\eta = (C_{L_T}-a_1\alpha_{T_{eff}})/a_2$.
- Stick free ($C_{M_H} = 0$): ★ floating elevator $\eta = -(b_1\alpha_{T_{eff}}+b_3\beta)/b_2$, so $C_{L_T} = \bar a_1\alpha_{T_{eff}}+\bar a_3\beta$ with $\bar a_1 = a_1-a_2\dfrac{b_1}{b_2}$ and ★ $\bar a_3 = a_3-a_2\dfrac{b_3}{b_2}$; ★ trim from $\begin{pmatrix}a_2&a_3\\b_2&b_3\end{pmatrix}\begin{pmatrix}\eta\\\beta\end{pmatrix} = \begin{pmatrix}C_{L_T}-a_1\alpha_{T_{eff}}\\-b_1\alpha_{T_{eff}}\end{pmatrix}$.

Longitudinal static stability ($dC_{M_{CG}}/d\alpha<0$, with $C_{M_{CG}}(\alpha = 0)>0$ for trim at positive $\alpha$):

$$
\frac{dC_{M_{CG}}}{d\alpha} = C_{L^*_\alpha}(h-h_0)-C_{L_{T,\alpha}}K = -C_{L^*_\alpha}H_s,\qquad C_{L^*_\alpha} = C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}
$$

$$
h_n = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad H_s = h_n-h = h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}\ (\text{stable if }H_s>0),\qquad C_{L_{T,\alpha}} = k(1-\epsilon_\alpha),\qquad k = a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}
$$

Stick free: $a_1\to\bar a_1$ in $k$, giving $\bar k$; with $b_1/b_2>0$, $\bar k<k$ and $H_{s,\text{free}}<H_{s,\text{fixed}}$. Use $k$, not the 2D $a_1$, in $C_{L_{T,\alpha}}$.

Manoeuvre (steady pull-up, radius $R$, pitch rate $q = V/R$, stick fixed, fixed speed):

$$
n = \frac{L^*}{W} = 1+\frac{V^2}{gR},\qquad \Phi = \frac{\rho Sl}{2m},\qquad C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}},\qquad h_m = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}},\quad H_m = h_m-h
$$

- ★ Pitch-rate tail incidence: $\Delta\alpha_{T_q} = ql/V = l/R = (n-1)C_W\Phi$, added to $\alpha_{T_{eff}}$. $h_m>h_n$; $\Phi\propto\rho$, so the manoeuvre margin falls with altitude. Stick-free manoeuvre point not covered.
- ★ Flight test: $H_{s,\text{fixed}} = h_n-h = -Kk\dfrac{a_2}{a_1}\dfrac{d\eta}{dC_{L^*}}$; plot $d\eta/dC_{L^*}$ against $h$ and extrapolate to zero slope for $h_n$ (stick free: $d\beta/dC_{L^*}$). CG from scales: $h = (F_fh_f+F_rh_r)/(F_f+F_r)$.
- Lateral and directional stability are qualitative only: fin (directional), dihedral, high wing and sweep (lateral); see [[Lateral and Directional Stability]].

## Legacy compressible (now [[Isentropic Nozzle Flow|SESA2023]])

Examined up to 2019-20 only; perfect gas, $\gamma = 1.4$, $R = 287$ J/(kg K) in the mass-flow constant.

$$
\frac{T_0}{T} = 1+\frac{\gamma-1}2M^2,\qquad \frac{dA}{A} = (M^2-1)\frac{dV}{V},\qquad V_1V_2 = a^{*2}\ (\text{normal shock}),\qquad \dot m = 0.0404\frac{p_0A^*}{\sqrt{T_0}}\ (\text{choked, SI})
$$

## Related
- [[SESA2022 Aerodynamics Hub]] · [[SESA2022 Past Paper Map]]
