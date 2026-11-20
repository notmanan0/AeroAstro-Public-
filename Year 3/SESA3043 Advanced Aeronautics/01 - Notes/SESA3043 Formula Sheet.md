---
title: "SESA3043 Formula Sheet"
module: "SESA3043 Advanced Aeronautics"
type: formula
aliases: ["SESA3043 formulae", "Advanced Aeronautics formula sheet"]
tags: [sesa3043, formula, exam-prep]
status: in-progress
coverage: "Chapters 1–3; Chapter 4 (4.1–4.3, rotor aerodynamics) written ahead from the slides, with 4.1 slides 1–22 (lectured 19 Nov) checked against the transcript"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures"]
---

# SESA3043 Formula Sheet

Current coverage: **Chapters 1–4**. Chapters 1–3 are checked against the transcripts. Chapter 4 (rotor aerodynamics, 4.1–4.3) is written ahead from the slides; the 4.1 actuator-disc, standard-parameter and annular-wake formulae (CH4 slides 1–22) are checked against the first Chapter 4 transcript (19 Nov), and the rest awaits its lectures.

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
Flat plate $F(0)=148/315$: $\theta/x=C_f=0.685/\sqrt{Re_x}$, $\delta/x=5.84/\sqrt{Re_x}$, $\delta^*/x=1.751/\sqrt{Re_x}$. Stagnation start $F=0$: $\lambda_0=7.05$, $K_0=0.0770$. Separation $\lambda=-12$ is $K=-0.157$ (Thwaites: $K=-0.09$). Howarth flow $U_e=U_0(1-x/L)$: $x_s/L=0.156$ (Pohlhausen), 0.123 (Thwaites), 0.120 (exact).

Thwaites (extension; laminar only; outside the scope of 3.5): $\theta^2=\dfrac{0.45\nu}{U_e^6}\displaystyle\int_0^xU_e^5\,\mathrm dx$.

Mean skin friction of a flat plate of length $L$ (laminar or turbulent, but **zero pressure gradient**; ship example): $\overline{C_f}=\dfrac{2\,\theta(L)}{L}$. Fully rough wall (extension): $\sqrt{2/C_f}=\kappa^{-1}\ln(\delta/k_s)+8.5+2\Pi/\kappa$, independent of $\nu$.

## Viscous–inviscid interaction (3.6)

$$
v_s=\frac{\mathrm d(U_e\delta^*)}{\mathrm dx}\qquad\text{(STM blowing velocity)}.
$$

Incompressible, attached layers; $\delta^*$ and $U_e$ evaluated on the original panels.

## Coursework: order of accuracy (3.6 §6)

$$
\varepsilon\approx K\,N^{-n}\quad\Longrightarrow\quad\log\varepsilon=\log K-n\log N,\qquad n=\frac{\ln(\varepsilon_1/\varepsilon_2)}{\ln(N_2/N_1)}.
$$

$\varepsilon$ is the relative $C_L$ error against the exact conformal-mapping value; fit only the straight-line (asymptotic) range of $N$.

## Chapter 4: rotor in hover (4.1)

Actuator disc in hover (steady, incompressible, irrotational outside the disc; uniform $v_i$; no swirl; $p_\infty$ far up- and downstream; air at rest far upstream) ([[SESA3043 4.1 - Rotor in Hover#2. Rotor thrust from Bernoulli|4.1 §2]]–[[SESA3043 4.1 - Rotor in Hover#4. Induced power and rotor efficiency|§4]]):

$$
T=A(p_l-p_u)=\tfrac12\rho v_2^2A=\rho Av_iv_2,\qquad v_2=2v_i,\qquad A_2=\tfrac12A,
$$

$$
v_0=v_i=\left(\frac{T}{2\rho A}\right)^{1/2},\qquad P_i=Tv_0=T\left(\frac{T}{2\rho A}\right)^{1/2},\qquad\frac{T}{P_i}=\frac1{v_0}\ \text{(rotor efficiency, N/W)}.
$$

$v_0$ is the hover induced velocity at the same thrust, the reference for 4.2 and 4.3. Disc loading $T/A$; in hover $T=mg$.

Standard parameters ([[SESA3043 4.1 - Rotor in Hover#6. Standard parameters|4.1 §6]]); $V_T=\Omega R$ (rad/s), $A=\pi R^2$, **course convention with $\tfrac12$** (US texts use $T/\rho A(\Omega R)^2$, half of this):

$$
\lambda_i=\frac{v_i}{V_T}=\frac{C_T^{1/2}}{2},\qquad C_T=\frac{T}{\tfrac12\rho V_T^2A}=4\lambda_i^2,\qquad C_P=\frac{P}{\tfrac12\rho V_T^3A},\qquad C_{P_i}=C_T\lambda_i=\frac{C_T^{3/2}}{2}\ \text{(hover, uniform inflow)}.
$$

Annular wake division (each annulus an independent actuator disc with $v_2=2v_i(r)$; $v_i=v_i^{T_s}(r/R)^n$, $v_i^{T_s}$ the tip value) ([[SESA3043 4.1 - Rotor in Hover#8. Annular wake division|4.1 §8]]):

$$
T=4\pi\rho\int_0^Rv_i^2r\,\mathrm dr=\frac{2\rho A\left(v_i^{T_s}\right)^2}{n+1},\qquad P_i=4\pi\rho\int_0^Rv_i^3r\,\mathrm dr=\frac{4\rho A\left(v_i^{T_s}\right)^3}{3n+2},\qquad v_i^{T_s}=\sqrt{n+1}\,v_0,
$$

$$
k_i=\frac{P_i}{P_{iIDEAL}}=\frac{(n+1)^{3/2}}{1+3n/2}\geq1:\quad n=0,\,0.5,\,1,\,2,\,3,\,5\ \to\ 1.00,\,1.05,\,1.13,\,1.30,\,1.45,\,1.73.
$$

Blade element theory (small $\phi\approx v_i/r\Omega$ in radians, so not near the root; $C_L=a\alpha$, $\alpha=\theta-\phi$; $U\approx\Omega r$; constant chord; blades to the centre; uniform $v_i$; $C_D$ constant) ([[SESA3043 4.1 - Rotor in Hover#10. Blade element theory|4.1 §10]]–[[SESA3043 4.1 - Rotor in Hover#11. Coefficients and the figure of merit|§11]]):

$$
s=\frac{Nc}{\pi R},\qquad T=\tfrac12\rho V_T^2NcRa\left(\frac{\theta_0}{3}-\frac{\lambda_i}{2}\right),\qquad\frac{C_T}{sa}=\frac{\theta_0}{3}-\frac{\lambda_i}{2},
$$

$$
Q=\tfrac12\rho\Omega^2NcR^4a\left(\frac{\theta_0}{3}-\frac{\lambda_i}{2}\right)\lambda_i+\tfrac18\rho\Omega^2NcR^4C_D,\qquad P=Q\Omega=Tv_i+\tfrac18\rho V_T^3NcRC_D,
$$

$$
C_P=C_T\lambda_i+\tfrac14sC_{D0},\qquad\mathrm{FM}=\frac{C_T\lambda_i}{C_T\lambda_i+sC_{D0}/4}=\frac{C_T^{3/2}}{C_T^{3/2}+sC_{D0}/2}\ \text{(typically 0.7–0.8)}.
$$

Induced power from the disc area, profile power from the blade area. FM rises with $C_T$; compare rotors at the same disc loading.

Linear twist $\theta=\theta_0-\kappa r/R$ (radians, $\kappa>0$ washout) ([[SESA3043 4.1 - Rotor in Hover#12. Blade twist|4.1 §12]]): $\dfrac{C_T}{sa}=\dfrac{\theta_0}{3}-\dfrac\kappa4-\dfrac{\lambda_i}{2}=\dfrac{\theta_{0.75}}{3}-\dfrac{\lambda_i}{2}$.

Annulus theory (momentum = BET on each annulus) ([[SESA3043 4.1 - Rotor in Hover#13. Annulus theory|4.1 §13]]):

$$
v_i^2(r)=\frac18V_T^2\frac{Nc(r)}{\pi R}a(r)\left(\frac{\theta r}{R}-\frac{v_i(r)}{V_T}\right);\quad\text{constant }c,a:\ \lambda_i(x)=\frac{sa}{16}\left[\sqrt{1+\frac{32\theta x}{sa}}-1\right].
$$

Uniform inflow ($k_i=1$) needs the ideal twist $\theta=\theta_{tip}R/r$.

Lynx in hover ([[SESA3043 4.1 - Rotor in Hover#7. Worked example: Westland Lynx in hover|4.1 §7]]; $R=6.4$ m, $V_T=218.69$ m/s, $\rho=1.2256$): max take-off 5330 kg → $T/A=406$ N/m², $C_T=0.01386$, $\lambda_i=0.0589$, $v_0=12.9$ m/s, $C_{P_i}=8.16\times10^{-4}$, $P_i=673$ kW, $T/P_i=77.7$ N/kW; empty 3291 kg → $C_T=0.00856$, $v_0=10.1$ m/s, $P_i=327$ kW, 98.8 N/kW.

## Rotor in axial flight (4.2)

Notation: $v_i$, $v_2$ positive downward through the disc; climb speed $V_C$ (relative stream down), descent speed $V_D$ (relative stream up), both positive; $v_0=\sqrt{T/2\rho A}$ is the hover induced velocity at the same thrust; $\bar v_i=v_i/v_0$, $\bar V_C=V_C/v_0$, $\bar V_D=V_D/v_0$. Actuator-disc assumptions of 4.1 (steady, incompressible, uniform $v_i$, no swirl, $p_\infty$ at both ends of the streamtube); axial flight only.

$$
v_2=2v_i\qquad\text{(climb and descent, as in hover).}
$$

Climb ([[SESA3043 4.2 - Rotor in Axial Flight#2. Climb|4.2 §2]]), valid for $V_C\geq0$:
$$
T=\rho A(V_C+v_i)\,2v_i,\qquad \bar v_i^2+\bar V_C\bar v_i-1=0,\qquad \bar v_i=-\frac{\bar V_C}{2}+\sqrt{\frac{\bar V_C^2}{4}+1}\ \ (\text{positive root}).
$$

Descent, windmill brake state ([[SESA3043 4.2 - Rotor in Axial Flight#4. Descent at high rate: the windmill brake slipstream|4.2 §4]]), valid only for $\bar V_D\geq2$:
$$
T=\rho A(V_D-v_i)\,2v_i,\qquad \bar v_i^2-\bar V_D\bar v_i+1=0,\qquad \bar v_i=\frac{\bar V_D}{2}-\sqrt{\frac{\bar V_D^2}{4}-1}\ \ (\text{smaller root; the larger reverses the wake}).
$$

No momentum solution for $0<V_D<2v_0$ ($-2<\bar V_C<0$): vortex ring and turbulent wake states ([[SESA3043 4.2 - Rotor in Axial Flight#5. Where momentum theory fails|4.2 §5]]). Fast climb or descent: $\bar v_i\approx1/|\bar V|$.

Power ([[SESA3043 4.2 - Rotor in Axial Flight#7. Power for axial motion of the disc|4.2 §7]]), profile power excluded:
$$
P=T(V_C+v_i)\ \text{(climb)},\qquad P=T(-V_D+v_i)\ \text{(descent)},\qquad \frac{P}{Tv_0}=\bar V_C+\bar v_i,\qquad \frac{C_P}{C_T}=\mu_z+\lambda_i,\ \mu_z=\frac{V_C}{V_T}.
$$
Slow climb: $P/(Tv_0)\approx1+\bar V_C/2$. Windmill brake: $P\leq-Tv_0$.

Autorotation (zero power): $\bar v_i=\bar V_D$, outside momentum theory; $\bar V_D\approx1.7$ (ideal), $1.8$ (real). Drag model $T=\tfrac12\rho V_D^2AC_D$: $\bar V_D=2/\sqrt{C_D}$ ([[SESA3043 4.2 - Rotor in Axial Flight#Autorotation|4.2 §7]]).

## Rotor in forward flight (4.3)

Disc axes: $x$ forward in the disc plane, $z$ normal to the disc; disc tilt $\gamma$ forward from the horizontal ([[SESA3043 4.3 - Rotor in Forward Flight#1. Co-ordinate system and disc tilt|4.3 §1]]).
$$
V_x=V\cos\gamma,\qquad V_z=V\sin\gamma\ (\text{down through the disc}),\qquad V'=\sqrt{V_x^2+(V_z+v_i)^2}.
$$
$\mu=V/V_T$, $\mu_x=V_x/V_T$, $\mu_z=V_z/V_T$, $\lambda_i=v_i/V_T$, $\mu_{zD}=\mu_z+\lambda_i$.

Induced velocity ([[SESA3043 4.3 - Rotor in Forward Flight#3. Actuator disc theory in forward flight|4.3 §3]]); assumes mass flow $\rho AV'$, uniform $v_i$ normal to the disc, $v_2=2v_i$:
$$
T=\rho AV'\cdot2v_i,\qquad v_i=\left(\frac{T}{2\rho A}\right)\frac{1}{\sqrt{V_x^2+(V_z+v_i)^2}},\qquad \lambda_i=\frac{C_T}{4}\frac{1}{\sqrt{\mu_x^2+(\mu_z+\lambda_i)^2}}.
$$
High speed ($V\gg v_0$): $v_i\approx T/(2\rho AV)$. Zero tilt: $\bar v_i^2=\left(-\bar V^2+\sqrt{\bar V^4+4}\right)/2$.

Newton–Raphson ([[SESA3043 4.3 - Rotor in Forward Flight#4. Solving for the induced velocity by Newton–Raphson|4.3 §4]]), $k=T/2\rho A$, start from $v_0$:
$$
v_{i,n+1}=v_{i,n}-\frac{v_{i,n}-k/V'_n}{1+k\,(V_z+v_{i,n})/V'^3_n}.
$$

Disc tilt, steady level flight, thrust normal to the disc, drag horizontal ([[SESA3043 4.3 - Rotor in Forward Flight#5. Disc tilt from the force balance|4.3 §5]]):
$$
\tan\gamma=\frac DW,\qquad T=\sqrt{W^2+D^2}.
$$

Power ([[SESA3043 4.3 - Rotor in Forward Flight#6. Power consumption|4.3 §6]]):
$$
P=\underbrace{Tv_i}_{\text{induced}}+\underbrace{TV_z}_{\text{parasite}\,=\,DV\ \text{(level)}}+\underbrace{\tfrac18\rho V_T^3NcRC_D}_{\text{profile (BET, hover value)}},\qquad C_P=C_T(\lambda_i+\mu_z)+\tfrac14sC_{D0}.
$$
Reverse-flow region: circle of diameter $\mu_xR$ on the retreating side (azimuth from the tail, textbook convention).

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
- [[SESA3043 4.1 - Rotor in Hover]]
- [[SESA3043 4.2 - Rotor in Axial Flight]]
- [[SESA3043 4.3 - Rotor in Forward Flight]]
- Deep dives: [[SESA3043 Deep Dive - Joukowski and Kármán-Trefftz Aerofoils, Full Derivation]] · [[SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation]] · [[SESA3043 Deep Dive - Linear Stability and the Orr-Sommerfeld Equation]] · [[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method]]
