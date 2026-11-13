---
title: "SESA3043 Formula Sheet"
module: "SESA3043 Advanced Aeronautics"
type: formula
aliases: ["SESA3043 formulae", "Advanced Aeronautics formula sheet"]
tags: [sesa3043, formula, exam-prep]
status: in-progress
coverage: "Chapters 1–3 (Ch 3.1–3.2 lectured 22–23 Oct; 3.3–3.6 from the slides)"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures"]
---

# SESA3043 Formula Sheet

Current coverage: **Chapters 1–3**. Chapters 1–2, 3.1–3.2 and 3.3 up to the integral properties as functions of $\lambda$ are checked against transcripts; the rest of 3.3 and 3.4–3.6 are written from the slides, ahead of time.

## Which method? Given → method → predicts → main limitation

| Given / asked for | Method | Predicts | Main limitation |
|---|---|---|---|
| A shape that maps from a circle (plate, ellipse, Joukowski, Kármán–Trefftz aerofoil) | Conformal mapping + Kutta ([[SESA3043 2.1 - Complex Functions and Conformal Mapping\|2.1]]) | Exact inviscid $C_p$, $\Gamma$, $C_L$ | Only mappable shapes; inviscid, so no drag |
| Thin lifting surfaces, interference (tandem, biplane, ground effect, flap) | Lumped vortex: vortex at $c/4$, control point at $3c/4$ ([[SESA3043 2.2 - Lumped Vortex Method\|2.2]]) | $\Gamma$ of each element, lift ratios | One vortex per element: no load distribution; thin, small $\alpha$; 2-D |
| An arbitrary aerofoil from coordinates | Panel method: source + vortex, or doublet ([[SESA3043 2.3 - Panel Methods\|2.3]]) | $C_p(x)$, $C_L$ | Inviscid; needs a Kutta row; zero drag |
| Laminar layer, zero pressure gradient | Blasius ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions\|3.2]]) | $\delta_{99}$, $\delta^*$, $\theta$, $C_f$ | Flat plate, laminar, $Re_x$ below transition |
| Laminar layer, $U_e=cx^m$ | Falkner–Skan (3.2) | Similar profiles; separation at $\beta=-0.199$ | Power-law edge velocity only |
| Laminar layer, arbitrary $U_e(x)$ | Pohlhausen or Thwaites with the MIE ([[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients\|3.3]], [[SESA3043 3.5 - Momentum Integral Equation\|3.5]]) | $\theta(x)$, $\lambda$, separation | Approximate profile; Pohlhausen predicts separation late |
| Turbulent layer | MIE with power-law correlations (3.5) | $\theta$, $\delta^*$, drag | Empirical, zero-pressure-gradient correlations |
| Where transition happens | Linear stability (Orr–Sommerfeld) + $e^N$ ([[SESA3043 3.4 - Transition to Turbulence\|3.4]]) | Neutral curve, $Re_{crit}$, $N$-factor | Misses receptivity, nonlinear and bypass routes |
| Boundary-layer effect on the outer flow | Viscous–inviscid interaction: displacement body or STM ([[SESA3043 3.6 - Viscous-Inviscid Interaction\|3.6]]) | Corrected $U_e$, pressure | Iterative; approximate closures; fails with separation |

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

Conservation form, then non-conservation form:

$$
\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)=0,
$$

$$
\frac{D\rho}{Dt}+\rho\nabla\cdot\mathbf u=0,
\qquad
\Delta=-\frac1\rho\frac{D\rho}{Dt}=\nabla\cdot\mathbf u\ \text{(dilatation rate)}.
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

Stokes' hypothesis $\lambda=-\tfrac23\mu$ makes the trace vanish, $\tau_{ii}=(2\mu+3\lambda)\nabla\cdot\mathbf u=0$: zero mean viscous normal stress ([[SESA3043 1.2 - Conservation Laws and Governing Equations#What Stokes' hypothesis does|1.2]]).

## Total energy

$$
E_T=e+\frac12u_i u_i,
$$

$$
\frac{\partial(\rho E_T)}{\partial t}
+\nabla\cdot[(\rho E_T+p)\mathbf u]
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

Irrotational, so a potential exists:

$$
\nabla\times\mathbf u=0\quad\Longrightarrow\quad\mathbf u=\nabla\phi.
$$

**And** incompressible, $\nabla\cdot\mathbf u=0$, gives Laplace's equation (irrotationality alone does not):

$$
\nabla\cdot\nabla\phi=\nabla^2\phi=0.
$$

Unsteady Bernoulli (irrotational, incompressible, inviscid, gravity as the only body force):

$$
\frac{\partial\phi}{\partial t}+\frac12|\mathbf u|^2+\frac p\rho+gz=C(t).
$$

For two-dimensional incompressible flow:

$$
u=\frac{\partial\psi}{\partial y},\qquad
v=-\frac{\partial\psi}{\partial x},\qquad
Q=\psi_2-\psi_1\ \text{(volume flow rate per unit span, m}^2\text{/s)}.
$$

$\psi$ exists for any 2-D incompressible flow; $\nabla^2\psi=0$ needs irrotational flow as well ($\nabla^2\psi=-\omega_z$).

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

- plate normal to the stream ($z=\bar z-a^2/\bar z$): $\Phi=\pm U\sqrt{z^2+4a^2}$, $C_p=1-\dfrac{y^2}{4a^2-y^2}$ (examinable by hand);
- plate along the stream ($z=\bar z+a^2/\bar z$, $a=b$): $z=2a\cos\theta$, $\Phi=Uz$, $u=U$, $v=0$, $C_p=0$ (examinable by hand);
- ellipse ($a>b$): semi-axes $a\pm b^2/a$;
- aerofoil: $a\cos\beta=b(1+\varepsilon)$, $\bar z_0=-\varepsilon b+ia\sin\beta$, $\dfrac bc=\dfrac{1+2\varepsilon}{4(1+\varepsilon)^2}$;
- Kutta: $\Gamma=4\pi aU\sin(\alpha+\beta)$, $C_L=\dfrac{8\pi a}{c}\sin(\alpha+\beta)$.

Kármán–Trefftz: $z=2b\dfrac{(\bar z+b)^p+(\bar z-b)^p}{(\bar z+b)^p-(\bar z-b)^p}$, $p=2-\tau/\pi$, $\dfrac bc=\dfrac{(1+\varepsilon)^p-\varepsilon^p}{4(1+\varepsilon)^p}$; far field $z\approx(2/p)\bar z$. Joukowski and KT are examined as logic, not calculation; $C_p=1-|\mathrm d\Phi/\mathrm dz|^2/U^2$; angles in radians in the code.

From the [[SESA3043 Deep Dive - Joukowski and Kármán-Trefftz Aerofoils, Full Derivation|Joukowski and KT deep dive]]: circle theorem $\Phi=f(\bar z)+\left[f\!\left(a^2/\bar z^*\right)\right]^*$ about the circle's centre. For KT the circle-plane stream is $\bar U_\infty=(2/p)U_\infty$, so $\Gamma=4\pi a\bar U_\infty\sin(\alpha+\beta)$ and
$$
C_L=\frac{16\pi a}{p\,c}\sin(\alpha+\beta)\qquad(p=2:\ \text{Joukowski}),\qquad C_p=1-\frac{16\left[\sin(\theta-\alpha)+\sin(\alpha+\beta)\right]^2}{p^2\left|\mathrm dz/\mathrm d\bar z\right|^2}.
$$
$\dfrac{\mathrm dz}{\mathrm d\bar z}=\dfrac{8b^2p\,AB}{(\bar z^2-b^2)(A-B)^2}$ with $A=(\bar z+b)^p$, $B=(\bar z-b)^p$. Near the trailing edge $z-2b\approx\dfrac{4b}{(2b)^p}(\bar z-b)^p$: included angle $\tau$, bisector at $-p\beta$. Coursework aerofoil ($\varepsilon=0.07$, $\beta=0.06$, $\tau=0.2$) at $\alpha=3^\circ$: $C_L=0.7760$ on ktreff's unit chord.

## Lumped vortex method

Vortex at $c/4$, control point at $3c/4$: $\Gamma_\infty=\pi U\alpha c$, $C_L=2\pi\alpha$. Downwash from a vortex a distance $d$ upstream: $\Gamma/2\pi d$ (from one downstream it is an upwash: enter it as a negative downwash). $\bar x_{cp}=-C_{M,LE}/C_L$. Tandem at gap $c/2$ (lectured): $\Gamma_1=\tfrac43\Gamma_\infty$, $\Gamma_2=\tfrac23\Gamma_\infty$.

| Case | Result |
|---|---|
| tandem, gap $\varepsilon c$ | $L_1/L_2=(2\varepsilon+3)/(2\varepsilon+1)$ (2 at $\varepsilon=\tfrac12$); $\Gamma_1+\Gamma_2=2\Gamma_\infty$ in this equal-chord, equal-incidence model only |
| ground effect | $\Gamma/\Gamma_\infty=1+1/(4h/c)^2$ |
| camber $0.24\bar x(1-\bar x)$ | $C_L=2\pi(\alpha+0.12)$ |
| biplane, gap $c/2$ | $\Gamma=\tfrac23\Gamma_\infty$ each |

## Panel methods

| Panel | Induced | Self-induced |
|---|---|---|
| source | $u=\frac{\sigma}{2\pi}\ln\frac{r_1}{r_2}$, $w=\frac{\sigma}{2\pi}(\theta_2-\theta_1)$ | $w_\pm=\pm\sigma/2$ |
| vortex | $u=\frac{\gamma}{2\pi}(\theta_2-\theta_1)$, $w=\frac{\gamma}{2\pi}\ln\frac{r_2}{r_1}$ | $u_\pm=\pm\gamma/2$ |
| doublet | $\phi=\frac{\mu}{2\pi}(\theta_1-\theta_2)$ | $\phi_\pm=\mp\mu/2$ |

Source + vortex method: tangency $\sum_ja_{ij}\sigma_j+\hat a_i\gamma=U\sin(\beta_i-\alpha)$; Kutta either by equal TE **speeds**, which in signed panel-tangent components is $q_{t,1}=-q_{t,N}$ (panels numbered TE → LE → TE), or by a zero-normal-velocity point on the TE bisector (the course code).

Doublet method: $\sum_ja_{ij}\mu_j+a_{i,w}\mu_w=-U(x_i\cos\alpha+y_i\sin\alpha)$; Kutta $\mu_1-\mu_N-\mu_w=0$; $C_L=2\mu_w/(Uc)$; $q_{t,i}=-\dfrac{\mu_i-\mu_{i-1}}{(l_i+l_{i-1})/2}$; $C_p=1-(q_t/U)^2$.

## Chapter 3: boundary-layer measures (3.1)

$$
\delta^*=\int_0^\infty\left(1-\frac{u}{U_e}\right)\mathrm dy,\qquad
\theta=\int_0^\infty\frac{u}{U_e}\left(1-\frac{u}{U_e}\right)\mathrm dy,\qquad
H=\frac{\delta^*}{\theta},
$$

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_0,\qquad C_f=\frac{\tau_w}{\tfrac12\rho U_e^2},\qquad
D'=\rho U_e^2\theta,\qquad\frac{\mathrm d\theta}{\mathrm dx}=\frac{C_f}{2}.
$$

The last two hold for a **flat plate with zero pressure gradient** ($U_e$ constant), $D'$ per unit span on one side; with a gradient use the full MIE (3.5).

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

Blasius: $f''(0)=\theta^*=0.4696$, $\eta^*=1.217$, $\eta_{99}=3.47$;
$\delta_{99}/x=4.91/\sqrt{Re_x}$, $\delta^*/x=1.721/\sqrt{Re_x}$, $\theta/x=C_f=0.664/\sqrt{Re_x}$, $H=2.59$.
Separation: $\beta=-0.19884$, $m=-0.0904$. Stagnation ($\beta=1$): $\xi=\sqrt{\nu/c}$, $\eta_{99}\approx2.4$.
Cylinder, near the front stagnation point ($x=R\theta$ along the surface, $\theta$ small, in radians): $U_e=2U_\infty\sin\theta\approx2U_\infty x/R$, so $c=2U_\infty/R$, $m=1$ and $\delta_{99}=\eta_{99}\sqrt{\nu R/(2U_\infty)}$, independent of $x$ (worked problem: 0.374 mm).
$\beta\pi$ is the included angle of a symmetric wedge. A single wall turned away by $\delta_w$ has $\beta=-2\delta_w/\pi$, so separation needs only $\delta_w=17.9^\circ$.

From the [[SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation|Falkner–Skan deep dive]]: $\xi\propto x^{(1-m)/2}$ with $\mathrm d\xi/\mathrm dx=\xi(1-m)/(2x)$; the wedge potential $\Phi=-kz^{m+1}$ gives $c=k(m+1)$. At the wall $f'''(0)=-\beta$, i.e. $\nu\,\partial^2u/\partial y^2|_0=-U_e\,\mathrm dU_e/\mathrm dx$. Integrating the Falkner–Skan equation across the layer gives the MIE in similarity form,
$$
f''(0)=(1+\beta)\,\theta^*+\beta\,\eta^*\qquad(\beta=0:\ \theta^*=f''(0)),
$$
so at separation $H=-(1+\beta)/\beta=4.029$. Local scalings: $\delta^*\sqrt{Re_x}/x=\eta^*\sqrt{2/(m+1)}$, $C_f\sqrt{Re_x}=2f''(0)\sqrt{(m+1)/2}$.

## Pohlhausen (3.3)

$$
\frac u{U_e}=2\eta-2\eta^3+\eta^4+\frac\lambda6\eta(1-\eta)^3,\qquad\eta=\frac y\delta,\qquad\lambda=\frac{\delta^2}{\nu}\frac{\mathrm dU_e}{\mathrm dx}=-\left.\frac{\mathrm d^2(u/U_e)}{\mathrm d\eta^2}\right|_0.
$$

$\delta^*/\delta=\frac{3}{10}-\frac{\lambda}{120}$, $\theta/\delta=\frac{37}{315}-\frac{\lambda}{945}-\frac{\lambda^2}{9072}$, $\tau_w\delta/(\mu U_e)=2+\lambda/6$; separation $\lambda=-12$; valid $|\lambda|\le12$; $C_f=(4+\lambda/3)/Re_\delta$; $H=\dfrac{3/10-\lambda/120}{37/315-\lambda/945-\lambda^2/9072}$. Coefficients: $a_0=0$, $a_1=2+\lambda/6$, $a_2=-\lambda/2$, $a_3=-2+\lambda/2$, $a_4=1-\lambda/6$. Shape factor $H=\delta^*/\theta$: 2.25 at $\lambda=12$, 2.55 at $\lambda=0$ (Blasius 2.59), 3.50 at $\lambda=-12$; APG raises $H$, FPG lowers it. In terms of $Re_\delta=U_e\delta/\nu$ (Bernoulli at the edge): $\lambda=Re_\delta\frac{\delta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=-Re_\delta\frac{\delta}{\rho U_e^2}\frac{\mathrm dp_e}{\mathrm dx}$, so at fixed station and with the other factors held fixed, separation is more likely with higher $Re$, a thicker layer, slower $U_e$ and a stronger APG. For geometrically similar laminar flow, $\delta^2\propto\nu L/U_\infty$ cancels the $1/\nu$, so $\lambda(x/L)$ and the laminar separation point do not depend on $Re$; $Re$ matters through transition.

## Transition (3.4)

$$
(\bar u-c_{ph})(\hat v''-\alpha^2\hat v)-\bar u''\hat v=-\frac{i\nu}{\alpha}(\hat v''''-2\alpha^2\hat v''+\alpha^4\hat v),\qquad v'=\hat v\,e^{i(\alpha_rx-\omega t)}e^{-\alpha_ix},
$$

$$
F=\frac{\omega\nu}{U_e^2},\qquad n=\ln\frac{A}{A_0}=-\int_{x_0}^x\alpha_i\,\mathrm dx,\qquad n_{crit}\approx9.
$$

Spatial growth (complex $\alpha$, real $\omega$; boundary layers are convectively unstable): growth rate $-\alpha_i$, unstable for $\alpha_i<0$ with $e^{i(\alpha x-\omega t)}$. $c_{ph}=\omega/\alpha$, $\alpha=2\pi/\lambda$, $\omega=2\pi/T$. Thumb plot: $\log Re_{\delta^*}$ against $F$, neutral curve $\alpha_i=0$, tip = small $Re_{crit}$ (first instability, not transition). Transition where the envelope of the constant-frequency amplification curves reaches $n_{crit}=9$ (Smith & Gamberoni; van Ingen; the XFOIL/XFLR5 default), lower $n_{crit}$ for a noisier environment. Blasius: $Re_{\delta^*}=1.7208\sqrt{Re_x}$. APG: larger unstable region, lower $Re_{crit}$; FPG the opposite.

From the [[SESA3043 Deep Dive - Linear Stability and the Orr-Sommerfeld Equation|Orr–Sommerfeld deep dive]] (lengths scaled by $\delta^*$, speeds by $U_e$; $\hat u=(i/\alpha)\,\mathrm d\hat v/\mathrm dy$; $\hat v=\mathrm d\hat v/\mathrm dy=0$ at the wall and as $y\to\infty$):
$$
\left(\tilde u-\tilde c\right)\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)\hat v-\tilde u''\hat v=-\frac{i}{\tilde\alpha\,Re_{\delta^*}}\left(\tilde{\mathrm D}^2-\tilde\alpha^2\right)^2\hat v,\qquad F=\frac{\omega\delta^*/U_e}{Re_{\delta^*}}.
$$
Blasius, computed: $Re_{\delta^*,crit}=519$, $\alpha_r\delta^*=0.304$, $c_{ph}=0.40U_e$, $F_{crit}=2.32\times10^{-4}$, $Re_{x,crit}=9.1\times10^4$. Envelope $n=9,\ 7,\ 5$ at $Re_x=3.2,\ 2.25,\ 1.45\times10^6$ ($Re_{\delta^*}=3083,\ 2581,\ 2074$).

## Momentum integral equation (3.5)

$$
\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{C_f}{2}\qquad\text{(laminar and turbulent)}.
$$

Conditions: 2-D, steady, incompressible boundary layer. One ODE with three unknowns ($\theta$, $H$ or $\delta^*$, $C_f$), so it needs a closure: an assumed similarity profile or an empirical correlation. Zero pressure gradient ($\mathrm dU_e/\mathrm dx=0$): $\mathrm d\theta/\mathrm dx=C_f/2$.

Dimensional form: $\dfrac{\mathrm d}{\mathrm dx}\left(U_e^2\theta\right)+U_e\dfrac{\mathrm dU_e}{\mathrm dx}\delta^*=\dfrac{\tau_w}{\rho}$.

Kármán–Pohlhausen march (extension, [[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method|MIE and Pohlhausen deep dive]]): with $g=\theta/\delta$, $h=\delta^*/\delta$, $a_1=2+\lambda/6$,
$$
U_e\frac{\mathrm d}{\mathrm dx}\left(\frac{\theta^2}{\nu}\right)=F(K)=2\left[T-(2+H)K\right],\qquad K=\frac{\theta^2}{\nu}\frac{\mathrm dU_e}{\mathrm dx}=g^2\lambda,\qquad T=\frac{\tau_w\theta}{\mu U_e}=a_1g.
$$
Flat plate $F(0)=148/315$: $\theta/x=C_f=0.685/\sqrt{Re_x}$, $\delta/x=5.84/\sqrt{Re_x}$, $\delta^*/x=1.751/\sqrt{Re_x}$. Stagnation start $F=0$: $\lambda_0=7.05$, $K_0=0.0770$. Separation $\lambda=-12$ is $K=-0.157$ (Thwaites: $K=-0.09$). Howarth flow $U_e=U_0(1-x/L)$: $x_s/L=0.157$ (Pohlhausen), 0.123 (Thwaites), 0.120 (exact).

Thwaites (extension; laminar only; outside the scope of 3.5): $\theta^2=\dfrac{0.45\nu}{U_e^6}\displaystyle\int_0^xU_e^5\,\mathrm dx$.

Mean skin friction of a flat plate of length $L$ (laminar or turbulent, but **zero pressure gradient**; ship example): $\overline{C_f}=\dfrac{2\,\theta(L)}{L}$. Fully rough wall (extension): $\sqrt{2/C_f}=\kappa^{-1}\ln(\delta/k_s)+8.5+2\Pi/\kappa$, independent of $\nu$.

## Viscous–inviscid interaction (3.6)

$$
v_s=\frac{\mathrm d(U_e\delta^*)}{\mathrm dx}\qquad\text{(STM blowing velocity)}.
$$

## Related

- [[SESA3043 1.1 - Mathematical Tools and Flow Description]]
- [[SESA3043 1.2 - Conservation Laws and Governing Equations]]
- [[SESA3043 1.2b - Potential-Flow Review]]
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
- Deep dives: [[SESA3043 Deep Dive - Joukowski and Kármán-Trefftz Aerofoils, Full Derivation]] · [[SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation]] · [[SESA3043 Deep Dive - Linear Stability and the Orr-Sommerfeld Equation]] · [[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method]]
