---
title: "SESA2022 Formula Sheet"
module: "SESA2022 Aerodynamics"
type: formula
aliases: ["SESA2022 formulae", "Aerodynamics formula sheet"]
tags: [sesa2022, formula, exam-prep]
status: complete
sources: ["03 - Exams & Past Papers/SESA2022-202425-01-SESA2022.pdf (rubric)", "01 - Notes/Topics"]
---

# SESA2022 Formula Sheet

One page of everything, organised by topic. Items marked ★ are **not** on the exam rubric, so memorise them.

## T2 Boundary layers ([[SESA2022 T2 - Boundary Layers]])

$$
\delta^* = \int_0^\infty\left(1-\frac{u}{U}\right)dy,\qquad \theta = \int_0^\infty\frac uU\left(1-\frac uU\right)dy,\qquad H = \frac{\delta^*}{\theta}
$$

$$
\tau_w = \mu\left.\frac{\partial u}{\partial y}\right|_0,\qquad C_f = \frac{2\tau_w}{\rho U^2} = 2\frac{d\theta}{dx},\qquad D'(x) = \rho U^2\theta(x),\qquad C_F = \frac{2\theta(L)}{L}\ \text{(per side)}
$$

| | Laminar (Blasius) | Turbulent (1/7 power law) |
|---|---|---|
| $\delta/x$ | $4.91Re_x^{-1/2}$ (5.0) | $0.38Re_x^{-1/5}$ (0.37) |
| $\delta^*/x$ | $1.72Re_x^{-1/2}$ | $0.048Re_x^{-1/5}$ |
| $\theta/x$ | $0.664Re_x^{-1/2}$ | $0.037Re_x^{-1/5}$ (0.036) |
| $C_f$ | $0.664Re_x^{-1/2}$ | $0.059Re_x^{-1/5}$ |
| $C_F$ (whole plate) | $1.328Re_L^{-1/2}$ | $0.074Re_L^{-1/5}$ |
| $H$ | 2.59 | 1.29 |

- ★ Power law: $\delta^*/\delta = 1/(n+1)$ and $\theta/\delta = n/[(n+1)(n+2)]$.
- Wall units: $u_\tau = U\sqrt{C_f/2}$, $y^+ = yu_\tau/\nu$, $u^+ = u/u_\tau$. Sub-layer $u^+ = y^+$ ($y^+<5$). Log layer $u^+ = \frac1\kappa\ln y^++B$.
- [[Virtual Origin Method|Virtual origin]]: $\theta_{lam}(x_T) = \theta_{turb}(x_T-x_0)$. One form is $x_0 = x_T(1-38.22Re_{x_T}^{-3/8})$.
- ★ MIE with a pressure gradient: $\dfrac{d\theta}{dx}+(2+H)\dfrac{\theta}{U_e}\dfrac{dU_e}{dx} = \dfrac{C_f}{2}$.

## T3 Potential flow ([[SESA2022 T3 - Potential Flow]])

$$
u_r = \frac1r\frac{\partial\psi}{\partial\theta} = \frac{\partial\phi}{\partial r},\quad u_\theta = -\frac{\partial\psi}{\partial r} = \frac1r\frac{\partial\phi}{\partial\theta};\qquad \omega_z = \frac1r\frac{\partial(ru_\theta)}{\partial r}-\frac1r\frac{\partial u_r}{\partial\theta},\quad \nabla\cdot\mathbf V = \frac1r\frac{\partial(ru_r)}{\partial r}+\frac1r\frac{\partial u_\theta}{\partial\theta}
$$

| Element | $\psi$ |
|---|---|
| Uniform flow | $V_\infty r\sin\theta$ |
| Source $\Lambda$ | $\frac{\Lambda}{2\pi}\theta$ |
| Vortex $\Gamma$ (clockwise +) | $\frac{\Gamma}{2\pi}\ln r$ |
| Doublet $\kappa$ | $-\frac{\kappa}{2\pi}\frac{\sin\theta}{r}$ |
| Corner, angle $\pi/n$ | $Ur^n\sin n\theta$ |

$$
C_p = 1-\frac{V^2}{V_\infty^2},\qquad L' = \rho V_\infty\Gamma
$$

**Cylinder** (radius $R$, $\kappa = 2\pi V_\infty R^2$): $V_\theta(R) = -2V_\infty\sin\theta-\frac{\Gamma}{2\pi R}$, so $C_p = 1-\left(2\sin\theta+\frac{\Gamma}{2\pi RV_\infty}\right)^2$.

★ **Rankine oval** stagnation points: $x_s = \pm\sqrt{b^2+\Lambda b/(\pi V_\infty)}$.

**Images**: a source reflects to the same sign, a vortex to the opposite sign. A corner needs three images.

## T4 Thin aerofoil theory ([[SESA2022 T4 - Thin Aerofoil Theory]])

$$
x = \tfrac c2(1-\cos\theta_0),\qquad \gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum A_n\sin n\theta\right),\qquad \Delta C_p = \frac{2\gamma}{V_\infty}
$$

$$
A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0,\qquad A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0,\qquad \alpha_{L=0} = -\frac1\pi\int_0^\pi\frac{dz}{dx}(\cos\theta_0-1)\,d\theta_0
$$

$$
C_l = \pi(2A_0+A_1) = 2\pi(\alpha-\alpha_{L=0}),\qquad C_{m,c/4} = \frac\pi4(A_2-A_1),\qquad C_{m,LE} = C_{m,c/4}-\frac{C_l}4,\qquad \frac{x_{cp}}{c} = \frac14-\frac{C_{m,c/4}}{C_l}
$$

- ★ Parabolic camber $z = \epsilon x(1-x/c)$: $A_1 = \epsilon$, $\alpha_{L=0} = -\epsilon/2$, $C_{m,c/4} = -\pi\epsilon/4$, maximum camber $\epsilon/4$ at $c/2$.
- ★ Flap at $\theta_h$: $A_0 = \alpha+\frac\delta\pi(\pi-\theta_h)$ and $A_n = \frac{2\delta}{n\pi}\sin n\theta_h$. For 25 %: $C_l = 2\pi\alpha+3.826\delta$ and $C_{m,c/4} = -0.6495\delta$.

## T5 Finite wing ([[SESA2022 T5 - Finite Wing Theory]])

$$
y = -\tfrac b2\cos\theta,\qquad \Gamma = 2bV_\infty\sum B_n\sin n\theta,\qquad \alpha_i = \sum nB_n\frac{\sin n\theta}{\sin\theta}
$$

$$
C_L = \pi AR\,B_1,\qquad C_{D_i} = \pi AR\sum nB_n^2 = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi eAR},\qquad \delta = \sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2
$$

$$
a = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)},\qquad C_D = C_{D_0}+C_{D_i},\qquad \left(\frac LD\right)_{max} = \frac12\sqrt{\frac{\pi eAR}{C_{D_0}}}\ \text{at}\ C_L = \sqrt{\pi eARC_{D_0}}
$$

**ELD**: $\Gamma = \Gamma_0\sqrt{1-(2y/b)^2}$, $w = -\Gamma_0/(2b)$, $L = \frac\pi4\rho V\Gamma_0b$, $\alpha_i = C_L/(\pi AR)$.

★ **Rectangular ELD**: $C_l(0) = \frac4\pi C_L$ and twist $= \frac{2C_L}{\pi^2}$.

★ **Elliptic loading at fixed lift**: $D_i = \dfrac{L^2}{\pi qb^2}$. Power $P = DV$.

## T6 Static stability ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]])

$$
C_{L^*} = C_L+C_{L_T}\tfrac{S_T}{S} = C_W\cos\gamma,\qquad C_{M_0}+C_{L^*}(h-h_0)-C_{L_T}K = 0,\qquad K = \frac{S_Tl}{Sc}
$$

$$
H_s = h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\quad C_{L_{T,\alpha}} = k(1-\epsilon_\alpha),\quad k = a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1},\quad \bar a_1 = a_1-a_2\frac{b_1}{b_2}
$$

$$
n = 1+\frac{V^2}{gR},\quad \Phi = \frac{\rho Sl}{2m},\quad C_{L_{T,\alpha}}^{(man)} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi S_T/S}
$$

## Legacy compressible (now [[Isentropic Nozzle Flow|SESA2023]])

$$
\frac{T_0}{T} = 1+\frac{\gamma-1}2M^2,\qquad \frac{dA}{A} = (M^2-1)\frac{dV}{V},\qquad V_1V_2 = a^{*2},\qquad \dot m = 0.0404\frac{p_0A^*}{\sqrt{T_0}}
$$

## Related
- [[SESA2022 Aerodynamics Hub]] · [[SESA2022 Past Paper Map]]
