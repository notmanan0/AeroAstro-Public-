---
title: "SESA3043 Formula Sheet"
module: "SESA3043 Advanced Aeronautics"
type: formula
aliases: ["SESA3043 formulae", "Advanced Aeronautics formula sheet"]
tags: [sesa3043, formula, exam-prep]
status: in-progress
coverage: "Chapters 1–3 (Ch 3 from the slides)"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures"]
---

# SESA3043 Formula Sheet

Current coverage: **Week 1**.

## Operators and material derivative

$$
\nabla=\mathbf e_i\frac{\partial}{\partial x_i},\qquad
\nabla\cdot\mathbf u=\frac{\partial u_i}{\partial x_i},\qquad
\boldsymbol\omega=\nabla\times\mathbf u.
$$

$$
\frac{D}{Dt}=\frac{\partial}{\partial t}+\mathbf u\cdot\nabla
=\frac{\partial}{\partial t}+u_j\frac{\partial}{\partial x_j}.
$$

## Transport

$$
u_n=\mathbf u\cdot\mathbf n,\qquad
\dot B=\int_A\rho b(\mathbf u\cdot\mathbf n)\,\mathrm dA.
$$

$$
\frac{\mathrm dB_{sys}}{\mathrm dt}
=\frac{\partial}{\partial t}\int_{CV}\rho b\,\mathrm dV
+\oint_{CS}\rho b(\mathbf u\cdot\mathbf n)\,\mathrm dA.
$$

## Continuity

$$
\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)=0,
$$

$$
\frac{D\rho}{Dt}+\rho\nabla\cdot\mathbf u=0,
\qquad
\nabla\cdot\mathbf u=-\frac1\rho\frac{D\rho}{Dt}.
$$

Incompressible:

$$
\nabla\cdot\mathbf u=0.
$$

## Momentum

$$
\frac{\partial(\rho u_i)}{\partial t}
+\frac{\partial(\rho u_i u_j)}{\partial x_j}
=\rho f_i-\frac{\partial p}{\partial x_i}
+\frac{\partial\tau_{ij}}{\partial x_j}.
$$

$$
\rho\frac{Du_i}{Dt}
=\rho f_i-\frac{\partial p}{\partial x_i}
+\frac{\partial\tau_{ij}}{\partial x_j}.
$$

## Newtonian stress

$$
\tau_{ij}=\mu\left(
\frac{\partial u_i}{\partial x_j}
+\frac{\partial u_j}{\partial x_i}
-\frac23\delta_{ij}\frac{\partial u_k}{\partial x_k}
\right),\qquad
\tau_{ij}=\tau_{ji},\qquad
\nu=\frac\mu\rho.
$$

## Total energy

$$
e_t=e+\frac12u_i u_i,
$$

$$
\frac{\partial(\rho e_t)}{\partial t}
+\nabla\cdot[(\rho e_t+p)\mathbf u]
=\rho\mathbf f\cdot\mathbf u
+\nabla\cdot(\boldsymbol\tau\cdot\mathbf u)
-\nabla\cdot\mathbf q.
$$

## Incompressible Navier–Stokes

$$
\nabla\cdot\mathbf u=0,
$$

$$
\frac{\partial\mathbf u}{\partial t}
+(\mathbf u\cdot\nabla)\mathbf u
=\mathbf f-\frac1\rho\nabla p+\nu\nabla^2\mathbf u.
$$

## Potential flow

$$
\nabla\times\mathbf u=0,\qquad
\mathbf u=\nabla\phi,\qquad
\nabla^2\phi=0.
$$

$$
\frac{\partial\phi}{\partial t}+\frac12|\mathbf u|^2+\frac p\rho+gz=C(t).
$$

For two-dimensional incompressible flow:

$$
u=\frac{\partial\psi}{\partial y},\qquad
v=-\frac{\partial\psi}{\partial x},\qquad
\nabla^2\psi=0,\qquad
q'=\psi_2-\psi_1.
$$

## Superposition and the cylinder

$$
\Phi=U\left(z+\frac{R^2}{z}\right),\quad R=\sqrt{\frac{\mu}{2\pi U}},\quad q_\theta\big|_R=-2U\sin\theta,\quad C_p=1-4\sin^2\theta.
$$

Lifting cylinder (counter-clockwise $\Gamma$): $\Phi=U(z+R^2/z)-\dfrac{i\Gamma}{2\pi}\ln z$, $\sin\theta_s=\dfrac{\Gamma}{4\pi UR}$, $|L'|=\rho U|\Gamma|$.

## Complex potential

$$
\Phi=\phi+i\psi,\qquad\frac{\mathrm d\Phi}{\mathrm dz}=u-iv,\qquad q=\left|\frac{\mathrm d\Phi}{\mathrm dz}\right|,\qquad z=re^{i\theta}.
$$

| Flow | $\Phi$ |
|---|---|
| uniform at $\alpha$ | $Ue^{-i\alpha}z$ |
| source $m$ | $\frac{m}{2\pi}\ln z$ |
| vortex (counter-clockwise $\Gamma$) | $-\frac{i\Gamma}{2\pi}\ln z$ |
| doublet (source upstream) | $\frac{\mu}{2\pi z}$ |
| general doublet | $-\frac{\mu}{2\pi}\frac{e^{i\nu}}{z}$, $u=\frac{\mu\cos(2\theta-\nu)}{2\pi r^2}$, $v=\frac{\mu\sin(2\theta-\nu)}{2\pi r^2}$ |
| wedge | $-kz^{m+1}$, walls $\theta=\pm\frac{\pi}{m+1}$, $\beta=\frac{2m}{m+1}$, $U_e=k(m+1)s^m$ |

Unsteady force on a cylinder in an accelerating stream: $F=2\pi\rho R^2\,\mathrm dU/\mathrm dt$ (added mass $\pi\rho R^2$).

## Boundary layers

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0,\qquad u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=U_e\frac{\mathrm dU_e}{\mathrm dx}+\nu\frac{\partial^2u}{\partial y^2},\qquad\frac{\partial p}{\partial y}=0.
$$

$v\sim U_e\delta/L$; $\delta/L\sim Re^{-1/2}$; $-\frac1\rho\frac{\mathrm dp}{\mathrm dx}=U_e\frac{\mathrm dU_e}{\mathrm dx}$. Blasius: $\delta_{99}=4.91x/\sqrt{Re_x}$, $\delta^*=1.721x/\sqrt{Re_x}$, $\theta=0.664x/\sqrt{Re_x}$, $C_f=0.664/\sqrt{Re_x}$.

## Conformal mapping

$u-iv=\dfrac{\mathrm d\Phi/\mathrm d\bar z}{\mathrm dz/\mathrm d\bar z}$. Joukowski $z=\bar z+b^2/\bar z$:

- plate normal to the stream ($z=\bar z-a^2/\bar z$): $\Phi=\pm U\sqrt{z^2+4a^2}$, $C_p=1-\dfrac{y^2}{4a^2-y^2}$;
- aerofoil: $a\cos\beta=b(1+\varepsilon)$, $\bar z_0=-\varepsilon b+ia\sin\beta$, $\dfrac bc=\dfrac{1+2\varepsilon}{4(1+\varepsilon)^2}$;
- Kutta: $\Gamma=4\pi aU\sin(\alpha+\beta)$, $C_L=\dfrac{8\pi a}{c}\sin(\alpha+\beta)$.

Kármán–Trefftz: $z=2b\dfrac{(\bar z+b)^p+(\bar z-b)^p}{(\bar z+b)^p-(\bar z-b)^p}$, $p=2-\tau/\pi$, $\dfrac bc=\dfrac{(1+\varepsilon)^p-\varepsilon^p}{4(1+\varepsilon)^p}$; far field $z\approx(2/p)\bar z$.

## Lumped vortex method

Vortex at $c/4$, control point at $3c/4$: $\Gamma_\infty=\pi U\alpha c$, $C_L=2\pi\alpha$. Downwash from a vortex a distance $d$ upstream: $\Gamma/2\pi d$. $\bar x_{cp}=-C_{M,LE}/C_L$.

| Case | Result |
|---|---|
| tandem, gap $\varepsilon c$ | $L_1/L_2=(2\varepsilon+3)/(2\varepsilon+1)$ (2 at $\varepsilon=\tfrac12$); $\Gamma_1+\Gamma_2=2\Gamma_\infty$ |
| ground effect | $\Gamma/\Gamma_\infty=1+1/(4h/c)^2$ |
| camber $0.24\bar x(1-\bar x)$ | $C_L=2\pi(\alpha+0.12)$ |
| biplane, gap $c/2$ | $\Gamma=\tfrac23\Gamma_\infty$ each |

## Panel methods

| Panel | Induced | Self-induced |
|---|---|---|
| source | $u=\frac{\sigma}{2\pi}\ln\frac{r_1}{r_2}$, $w=\frac{\sigma}{2\pi}(\theta_2-\theta_1)$ | $w_\pm=\pm\sigma/2$ |
| vortex | $u=\frac{\gamma}{2\pi}(\theta_2-\theta_1)$, $w=\frac{\gamma}{2\pi}\ln\frac{r_2}{r_1}$ | $u_\pm=\pm\gamma/2$ |
| doublet | $\phi=\frac{\mu}{2\pi}(\theta_1-\theta_2)$ | $\phi_\pm=\mp\mu/2$ |

Doublet method: $\sum_ja_{ij}\mu_j+a_{i,w}\mu_w=-U(x_i\cos\alpha+y_i\sin\alpha)$; Kutta $\mu_1-\mu_N-\mu_w=0$; $C_L=2\mu_w/(Uc)$; $q_{t,i}=-\dfrac{\mu_i-\mu_{i-1}}{(l_i+l_{i-1})/2}$; $C_p=1-(q_t/U)^2$.

## Chapter 3: boundary-layer measures (3.1)

$$
\delta^*=\int_0^\infty\left(1-\frac{u}{U_e}\right)\mathrm dy,\qquad
\theta=\int_0^\infty\frac{u}{U_e}\left(1-\frac{u}{U_e}\right)\mathrm dy,\qquad
H=\frac{\delta^*}{\theta},
$$

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_0,\qquad C_f=\frac{\tau_w}{\tfrac12\rho U_e^2},\qquad
D=\rho U_e^2\theta\ \text{(flat plate)},\qquad\frac{\mathrm d\theta}{\mathrm dx}=\frac{C_f}{2}.
$$

Linear profile: $\delta^*=\delta/2$, $\theta=\delta/6$, $H=3$, $C_f=2/Re_\delta$.

## Blasius and Falkner–Skan (3.2)

$$
\xi=\sqrt{\frac{2\nu x}{(m+1)U_e}},\quad\eta=\frac y\xi,\quad f=\frac{\psi}{U_e\xi},\quad\frac u{U_e}=f',\quad U_e=cx^m,\quad\beta=\frac{2m}{m+1}.
$$

$$
f'''+ff''+\beta(1-f'^2)=0,\qquad f(0)=f'(0)=0,\ f'(\infty)=1\qquad(\beta=0:\ \text{Blasius}).
$$

$$
\delta^*=\xi\eta^*,\qquad\theta=\xi\theta^*,\qquad C_f=\frac{2\nu}{U_e\xi}f''(0).
$$

Blasius: $f''(0)=\theta^*=0.4696$, $\eta^*=1.217$, $\eta_{99}=3.47$ (slides 3.5);
$\delta_{99}/x=4.91/\sqrt{Re_x}$ (slides 5.0), $\delta^*/x=1.721/\sqrt{Re_x}$, $\theta/x=C_f=0.664/\sqrt{Re_x}$, $H=2.59$.
Separation: $\beta=-0.19884$. Stagnation ($\beta=1$): $\xi=\sqrt{\nu/c}$, $\eta_{99}\approx2.4$.

## Pohlhausen (3.3)

$$
\frac u{U_e}=2\eta-2\eta^3+\eta^4+\frac\lambda6\eta(1-\eta)^3,\qquad\eta=\frac y\delta,\qquad\lambda=\frac{\delta^2}{\nu}\frac{\mathrm dU_e}{\mathrm dx}=-\left.\frac{\mathrm d^2(u/U_e)}{\mathrm d\eta^2}\right|_0.
$$

$\delta^*/\delta=\frac{3}{10}-\frac{\lambda}{120}$, $\theta/\delta=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072}$, $\tau_w\delta/(\mu U_e)=2+\lambda/6$; separation $\lambda=-12$; valid $|\lambda|\le12$.

## Transition (3.4)

$$
(\bar u-c_{ph})(\hat v''-\alpha^2\hat v)-\bar u''\hat v=-\frac{i\nu}{\alpha}(\hat v''''-2\alpha^2\hat v''+\alpha^4\hat v),\qquad v'=\hat v\,e^{i(\alpha_rx-\omega t)}e^{-\alpha_ix},
$$

$$
F=\frac{\omega\nu}{U_e^2},\qquad n=\ln\frac{A}{A_0}=-\int_{x_0}^x\alpha_i\,\mathrm dx,\qquad n_{crit}\approx9.
$$

## Momentum integral equation (3.5)

$$
\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{C_f}{2}\qquad\text{(laminar and turbulent)}.
$$

Thwaites (extension): $\theta^2=\dfrac{0.45\nu}{U_e^6}\displaystyle\int_0^xU_e^5\,\mathrm dx$.

## Viscous–inviscid interaction (3.6)

$$
v_s=\frac{\mathrm d(U_e\delta^*)}{\mathrm dx}\qquad\text{(STM blowing velocity)}.
$$

## Related

- [[SESA3043 1.1 - Mathematical Tools and Flow Description]]
- [[SESA3043 1.2 - Conservation Laws and Governing Equations]]
- [[SESA3043 1.3 - Potential-Flow Review]]
- [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]
- [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]
- [[SESA3043 2.1 - Complex Functions and Conformal Mapping]]
- [[SESA3043 2.2 - Lumped Vortex Method]]
- [[SESA3043 2.3 - Panel Methods]]
- [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]
- [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]
- [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]
- [[SESA3043 3.4 - Transition to Turbulence]]
- [[SESA3043 3.5 - Momentum Integral Equation]]
- [[SESA3043 3.6 - Viscous-Inviscid Interaction]]
