---
title: "SESA2027 Formula Sheet"
module: "SESA2027 Aerospace Mechanics & Control"
type: formula
aliases: ["SESA2027 formulae", "Mechanics and Control formula sheet"]
tags: [sesa2027, formula, exam-prep]
status: complete
coverage: "All twelve topic notes: Part A (A1–A5, L1.01–L1.11), Part B (B1–B4, L2.01–L2.09), Part C (C1–C3, L3.01–L3.08)"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures", "02 - Sources/Problem Sheets"]
---

# SESA2027 Formula Sheet

One page per part, in the order of the topic notes; each section links to its note. Angles are in radians inside every formula unless a degree sign is shown. Body axes are right-handed with $x$ forward, $y$ starboard and $z$ down.

## Part A: Dynamic systems

### Equations of motion ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]])

Dynamic system: $\dot{\mathbf x} = f(\mathbf x,\mathbf u)$; trim is $f(\bar{\mathbf x},\bar{\mathbf u}) = 0$.

Newton in body axes (rigid body, constant mass, flat Earth, origin at the cg):

$$
\mathbf F_B = m(\dot{\mathbf v}_B+\boldsymbol\omega_B\times\mathbf v_B),\qquad \mathbf M_B = \dot{\mathbf h}_B+\boldsymbol\omega_B\times\mathbf h_B,\qquad \mathbf h = \mathbf I\boldsymbol\omega
$$

$$
\frac{d\mathbf i}{dt} = r\mathbf j-q\mathbf k,\quad \frac{d\mathbf j}{dt} = p\mathbf k-r\mathbf i,\quad \frac{d\mathbf k}{dt} = q\mathbf i-p\mathbf j,\qquad \boldsymbol\omega\times\mathbf v = (qW-rV,\ rU-pW,\ pV-qU)
$$

$$
\mathbf I = \begin{bmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{bmatrix},\qquad I_{xx} = \int(y^2+z^2)\,dm,\quad I_{xy} = \int xy\,dm,\ \text{etc.}
$$

$\mathbf I$ is constant in body axes, so $\dot{\mathbf h} = \mathbf I\dot{\boldsymbol\omega}$.

Earth to body (yaw $\psi$, then pitch $\theta$, then roll $\phi$; multiply right to left):

$$
\mathbf v_B = \mathbf R_{BE}\mathbf v_E,\qquad \mathbf R_{BE} = \mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi),\qquad \mathbf R_{EB} = \mathbf R_{BE}^{-1} = \mathbf R_{BE}^T
$$

$$
\mathbf R_x(\phi)=\begin{bmatrix}1&0&0\\0&\cos\phi&\sin\phi\\0&-\sin\phi&\cos\phi\end{bmatrix},\quad \mathbf R_y(\theta)=\begin{bmatrix}\cos\theta&0&-\sin\theta\\0&1&0\\\sin\theta&0&\cos\theta\end{bmatrix},\quad \mathbf R_z(\psi)=\begin{bmatrix}\cos\psi&\sin\psi&0\\-\sin\psi&\cos\psi&0\\0&0&1\end{bmatrix}
$$

Gravity in body axes (third column of $\mathbf R_{BE}$, $\mathbf g_E = (0,0,g)$): $\mathbf g_B = g\,(-\sin\theta,\ \sin\phi\cos\theta,\ \cos\phi\cos\theta)$. Ranges: $\phi,\psi\in[-\pi,\pi]$, $\theta\in[-\pi/2,\pi/2]$ (gimbal lock).

Full nonlinear forces: $X = m(\dot U+qW-rV)$, $Y = m(\dot V+rU-pW)$, $Z = m(\dot W+pV-qU)$. Moments with $xz$-plane symmetry ($I_{xy} = I_{yz} = 0$):

$$
L = I_{xx}\dot p-I_{xz}\dot r+(I_{zz}-I_{yy})qr-I_{xz}pq,\quad M = I_{yy}\dot q+(I_{xx}-I_{zz})pr+I_{xz}(p^2-r^2),\quad N = I_{zz}\dot r-I_{xz}\dot p+(I_{yy}-I_{xx})pq+I_{xz}qr
$$

Linearised and decoupled about trim (stability axes, so $U = U_\infty+u$, $V = v$, $W = w$; products of perturbations dropped; $qU_\infty$ and $rU_\infty$ kept because $U_\infty$ is large):

$$
\underbrace{\Delta X = m\dot u,\quad \Delta Z = m(\dot w-qU_\infty),\quad \Delta M = I_{yy}\dot q}_{\text{longitudinal: }u,\ w,\ q}\qquad \underbrace{\Delta Y = m(\dot v+rU_\infty),\quad \Delta L = I_{xx}\dot p-I_{xz}\dot r,\quad \Delta N = -I_{xz}\dot p+I_{zz}\dot r}_{\text{lateral: }v,\ p,\ r}
$$

Wind-frame angles from body velocities: $\alpha = \tan^{-1}(W/U)\approx w/U_\infty$, $\beta = \sin^{-1}(V/V_\infty)$.

### State space and derivatives ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]])

Gravity, trim climb angle $\gamma_0$, small $\theta$: $X_{g0} = -mg\sin\gamma_0$, $Z_{g0} = mg\cos\gamma_0$, so $\Delta X_g = -mg\theta\cos\gamma_0$ and $\Delta Z_g = -mg\theta\sin\gamma_0$ (level flight: $\Delta X_g = -mg\theta$, $\Delta Z_g = 0$).

Aerodynamic terms (ring = dimensional; $\mathring X_q$, $\mathring X_{\dot w}$ neglected, and $\mathring M_u = 0$ at low Mach):

$$
\Delta X_a = \mathring X_uu+\mathring X_ww,\qquad \Delta Z_a = \mathring Z_uu+\mathring Z_ww+\mathring Z_qq+\mathring Z_{\dot w}\dot w,\qquad \Delta M_a = \mathring M_uu+\mathring M_ww+\mathring M_qq+\mathring M_{\dot w}\dot w
$$

Longitudinal state equation, $\mathbf x = [u,w,q,\theta]^T$ ($\dot w$ terms go into $\mathbf M$):

$$
\underbrace{\begin{bmatrix}m&0&0&0\\0&m-\mathring Z_{\dot w}&0&0\\0&-\mathring M_{\dot w}&I_{yy}&0\\0&0&0&1\end{bmatrix}}_{\mathbf M}\dot{\mathbf x} = \underbrace{\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\cos\gamma_0\\\mathring Z_u&\mathring Z_w&\mathring Z_q+mU_\infty&-mg\sin\gamma_0\\\mathring M_u&\mathring M_w&\mathring M_q&0\\0&0&1&0\end{bmatrix}}_{\mathbf A'}\mathbf x+\mathbf B'\mathbf u
$$

$$
\mathbf A = \mathbf M^{-1}\mathbf A',\qquad \mathbf B = \mathbf M^{-1}\mathbf B'\qquad(\mathbf M^{-1}\text{ on the left; }\mathbf A'\mathbf M^{-1}\text{ is a different matrix})
$$

Inputs $\mathbf u = [\eta,\ \Delta T,\ u_g,\ w_g]^T$; the last row of $\mathbf B'$ is zero because $\dot\theta = q$ is kinematic; gusts enter through the same derivatives as $u$ and $w$.

Dimensional form of the derivatives (forces scaled by $\tfrac12\rho U_\infty^2S$, moments by $\tfrac12\rho U_\infty^2S\bar c$; perturbations by $U_\infty$ for $u$, $w$, by $U_\infty/\bar c$ for $q$, by $U_\infty^2/\bar c$ for $\dot w$):

| Derivative | Dimensional form | Units |
|---|---|---|
| $\mathring X_u$, $\mathring X_w$, $\mathring Z_u$, $\mathring Z_w$ | $(\cdot)\,\tfrac12\rho U_\infty S$ | N s/m |
| $\mathring Z_q$ | $Z_q\,\tfrac12\rho U_\infty S\bar c$ | N s |
| $\mathring Z_{\dot w}$ | $Z_{\dot w}\,\tfrac12\rho S\bar c$ | N s²/m |
| $\mathring M_u$, $\mathring M_w$ | $(\cdot)\,\tfrac12\rho U_\infty S\bar c$ | N s |
| $\mathring M_q$ | $M_q\,\tfrac12\rho U_\infty S\bar c^2$ | N m s |
| $\mathring M_{\dot w}$ | $M_{\dot w}\,\tfrac12\rho S\bar c^2$ | N s² |
| $\mathring X_\eta$, $\mathring Z_\eta$; $\mathring M_\eta$ | $(\cdot)\,\tfrac12\rho V_0^2S$; $M_\eta\,\tfrac12\rho V_0^2S\bar c$ | N/rad; N m/rad |

Dimensionless estimates (level trim, $T = D$, $L^* = W$; thrust $T = c_tU^\Lambda$ with $\Lambda = 0$ jet, $-1$ propeller):

$$
X_u = (\Lambda-2)C_D,\quad X_w = C_{L^*}-C_{D_\alpha},\quad Z_u = -2C_{L^*},\quad Z_w = -(C_{L^*_\alpha}+C_D)
$$

$$
M_w = -H_sC_{L^*_\alpha}\ (H_s\text{ = stick-fixed static margin}),\qquad M_q = -KC_{L_{T,\alpha}}\frac{l}{\bar c},\quad K = \frac{S_Tl}{S\bar c}\ (\Delta\alpha_T\approx ql/U_\infty)
$$

Elevator derivatives (tail $C_{L_T} = a_0+a_1\alpha_T+a_2\eta$, $C_{D_T} = C_{D_{0T}}+k_TC_{L_T}^2$, $\eta$ in rad, trailing edge down positive):

$$
X_\eta = -2\frac{S_T}{S}k_TC_{L_T}a_2,\qquad Z_\eta = -\frac{S_T}{S}a_2,\qquad M_\eta = -\frac{S_Tl_T}{S\bar c}a_2 = -\bar V_Ta_2
$$

State space to transfer function (zero initial conditions; $\mathbf D = 0$ unless a sensor is driven directly by an input):

$$
\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u,\quad \mathbf y = \mathbf C\mathbf x+\mathbf D\mathbf u\quad\Rightarrow\quad G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D = \frac{\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\mathbf B+\mathbf D\lvert s\mathbf I-\mathbf A\rvert}{\lvert s\mathbf I-\mathbf A\rvert}
$$

$2\times2$ shortcut: $\mathrm{adj}\begin{bmatrix}a&b\\c&d\end{bmatrix} = \begin{bmatrix}d&-b\\-c&a\end{bmatrix}$, $\det = ad-bc$. The denominator $\lvert s\mathbf I-\mathbf A\rvert$ is the characteristic polynomial.

Full longitudinal elevator transfer functions (phugoid $p$, short period $s$): $\dfrac{q}{\eta} = \dfrac{k_qs(s+1/T_{\theta_1})(s+1/T_{\theta_2})}{(s^2+2\zeta_p\omega_ps+\omega_p^2)(s^2+2\zeta_s\omega_ss+\omega_s^2)}$ and $\dfrac{\theta}{\eta} = \dfrac1s\dfrac{q}{\eta}$.

### Modes ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]])

Free, stick-fixed response $\mathbf x = \mathbf x_0e^{\lambda t}$:

$$
\det(\lambda\mathbf I-\mathbf A) = 0\ \Rightarrow\ A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0,\qquad \lambda = \sigma\pm i\omega
$$

Expand along the bottom row: with $\theta$ last, row 4 of $\lambda\mathbf I-\mathbf A$ is $[0,\ 0,\ -1,\ \lambda]$, so only the $(4,3)$ and $(4,4)$ cofactors survive.

$$
\omega_n = \sqrt{\sigma^2+\omega^2},\qquad \zeta = -\frac{\sigma}{\omega_n},\qquad \omega = \omega_n\sqrt{1-\zeta^2};\qquad \lambda^2+a\lambda+b:\ \omega_n = \sqrt b,\ \zeta = \frac{a}{2\sqrt b}
$$

$$
T = \frac{2\pi}{\omega},\qquad t_{1/2} = \frac{\ln2}{\lvert\sigma\rvert}\ (\sigma<0),\qquad t_2 = \frac{\ln2}{\sigma}\ (\sigma>0;\ \text{no half-life exists})
$$

Stable iff $\sigma<0$, i.e. $\zeta>0$. Larger-magnitude pair = SPO, smaller = phugoid.

Routh–Hurwitz (quartic): stable if all coefficients $>0$ and the Routh discriminant $R = D(BC-AD)-B^2E>0$; in practice $E>0$ and $R>0$ (state it in words).

SPO approximation ($u = 0$, $\gamma_0 = 0$, $\mathring Z_{\dot w}\ll m$, $\mathring Z_q\ll mU_\infty$):

$$
\begin{bmatrix}m&0\\-\mathring M_{\dot w}&I_{yy}\end{bmatrix}\begin{bmatrix}\dot w\\\dot q\end{bmatrix} = \begin{bmatrix}\mathring Z_w&mU_\infty\\\mathring M_w&\mathring M_q\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix}
$$

$$
\omega_n^2 = \frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad \zeta = -\frac{m(\mathring M_q+U_\infty\mathring M_{\dot w})+\mathring Z_wI_{yy}}{2\omega_nmI_{yy}}
$$

Sensitivity (F-4C, ±10 %): $I_{yy}$ mainly sets $\omega_n$ ($\omega_n\propto1/\sqrt{I_{yy}}$ almost exactly), $m$ mainly sets $\zeta$; increasing either lowers both.

Phugoid: $E = mgh+\tfrac12mV^2\approx$ const at roughly constant $\alpha$; lightly damped (drag only), may be slightly unstable. Flight path: $\gamma = \theta-\alpha$.

Lateral quartic: one complex pair (Dutch roll) and two real roots (spiral, roll subsidence), so three modes; named only here, analysed in SESA3047.

### Laplace and step response ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]])

One-sided transform, $g(t) = 0$ for $t<0$: $G(s) = \displaystyle\int_0^\infty g(t)e^{-st}dt$.

| Property / function | Transform |
|---|---|
| $\dot g$; $\ddot g$ | $sG-g(0)$; $s^2G-sg(0)-\dot g(0)$ |
| $\int_0^tg\,d\tau$ | $G/s$ |
| Impulse $\delta(t)$; step $u(t)$; ramp $t$ | $1$; $1/s$; $1/s^2$ |
| Delay $g(t-a)u(t-a)$ | $e^{-as}G(s)$ |
| $\sin\omega t$ | $\omega/(s^2+\omega^2)$ |
| $e^{\sigma t}\cos\omega t$; $e^{\sigma t}\sin\omega t$ | $(s-\sigma)/[(s-\sigma)^2+\omega^2]$; $\omega/[(s-\sigma)^2+\omega^2]$ |
| Doublet $u(t)-2u(t-t_1)+u(t-2t_1)$ | $(1-e^{-t_1s})^2/s$ (no lasting value) |

Transfer function $G = X/U = B(s)/A(s)$: zeros are the roots of $B$, poles the roots of $A$ (= the eigenvalues).

Final-value theorem (closed loop or system stable): $\displaystyle\lim_{t\to\infty}x(t) = \lim_{s\to0}sX(s)$; for $X = K/[s(s^2+2\zeta\omega_ns+\omega_n^2)]$ it is $K/\omega_n^2$.

Partial fractions: distinct real roots $\to r_ie^{p_it}$; repeated $\to(r_1+r_2t)e^{pt}$; complex pair $\to e^{\sigma t}(r_2\cos\omega t+r_3\sin\omega t)$.

Normalised second-order step ($0<\zeta<1$, $\omega_d = \omega_n\sqrt{1-\zeta^2}$, starts with zero slope):

$$
x(t) = 1-e^{-\zeta\omega_nt}\left(\cos\omega_dt+\frac{\zeta}{\sqrt{1-\zeta^2}}\sin\omega_dt\right),\qquad \text{envelope }1\pm\frac{e^{-\zeta\omega_nt}}{\sqrt{1-\zeta^2}}
$$

$$
t_r\approx\frac{1.8}{\omega_n}\ (\text{10–90 \%, best near }\zeta\approx0.5),\qquad t_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^2}},\qquad OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}\ \%
$$

$$
t_s\approx\frac{4.6}{\zeta\omega_n} = \frac{4.6}{\lvert\sigma\rvert}\ (1\ \%,\ \text{the module default}),\qquad \frac{3}{\zeta\omega_n}\ (5\ \%);\qquad \text{exact envelope: } t_s = \frac{\ln\!\left(100/\sqrt{1-\zeta^2}\right)}{\zeta\omega_n}
$$

| $\zeta$ | 0.2 | 0.35 | 0.4 | 0.5 | 0.7 |
|---|---|---|---|---|---|
| OS | 52.7 % | 30.9 % | 25.4 % | 16.3 % | 4.6 % |

Pole reading: $OS$ from the angle ($\zeta = \cos\beta$), $t_s$ from the real part, $t_p$ from the imaginary part, $t_r$ roughly from $\lvert s\rvert = \omega_n$. The $t_s$ rule fails for $\zeta>1$.

First order $K/(\tau s+1)$: $y = K(1-e^{-t/\tau})$, 63.2 % at $t = \tau$, $t_r = 2.2\tau$, $t_s = 4.6\tau$ (1 %) or $3\tau$ (5 %), no overshoot.

### Frequency response ([[SESA2027 A5 - Frequency Response and Bode Plots]])

Pole–zero map: stable iff every pole is in the left half-plane; physical only if complex poles and zeros come in conjugate pairs; a causal system has no more zeros than poles.

Steady state for $u = A\sin\omega t$ (stable LTI system):

$$
x_{ss} = A\lvert G(i\omega)\rvert\sin\left(\omega t+\angle G(i\omega)\right),\qquad \lvert G\rvert_{dB} = 20\log_{10}\lvert G\rvert,\quad \lvert G\rvert = 10^{\lvert G\rvert_{dB}/20}
$$

$\lvert G\rvert = \lvert\text{num}\rvert/\lvert\text{den}\rvert$ and $\angle G = \angle\text{num}-\angle\text{den}$ (use `atan2` past −90°). Every −20 dB divides the amplitude by 10.

Unit-DC-gain second order $\omega_n^2/(s^2+2\zeta\omega_ns+\omega_n^2)$:

$$
\omega_r = \omega_n\sqrt{1-2\zeta^2},\qquad M_r = \frac{1}{2\zeta\sqrt{1-\zeta^2}}\ (\zeta<0.707),\qquad \lvert G(i\omega_n)\rvert = \frac{1}{2\zeta},\ \angle G(i\omega_n) = -90^\circ
$$

$$
\omega_b = \omega_n\sqrt{1-2\zeta^2+\sqrt{4\zeta^4-4\zeta^2+2}}\ \ (-3.01\ \text{dB = half power}, \times0.707)
$$

Bode factors (dB and phase add):

| Factor | Magnitude slope | Phase |
|---|---|---|
| Gain $k$ | flat at $20\log_{10}\lvert k\rvert$ | 0, or −180° if $k<0$ |
| Zero at origin $s$ / pole at origin $1/s$ | +20 / −20 dB/dec | +90° / −90° |
| Real zero $s-z$ | 0, then +20 dB/dec above $\lvert z\rvert$ | 0 → +90° (phase lead), over $0.1\lvert z\rvert$ to $10\lvert z\rvert$ |
| Real pole $1/(s-p)$ | 0, then −20 dB/dec | 0 → −90°; −3.01 dB and −45° at the corner |
| Complex zero pair | +40 dB/dec | 0 → +90° at $\omega_n$ → +180° |
| Complex pole pair | −40 dB/dec; peak near $\omega_n$ if $\zeta<0.707$ | 0 → −90° at $\omega_n$ → −180°, sharper at low $\zeta$ |

Each zero adds up to +90° of steady-state phase lead; a transfer function with poles only lags at every frequency. A change of high-frequency slope by a further −20 dB/dec marks another pole.

Pure delay: $\lvert e^{-i\omega T}\rvert = 1$, $\angle e^{-i\omega T} = -\omega T$.

## Part B: Control

### Closed loop and PID ([[SESA2027 B1 - Control System Fundamentals and PID Control]])

Error = reference minus measurement, $e = r-y$ (negative feedback). Block equations: $X = G(U_C+U_P)$, $U_C = CE$, $E = R-Y$, $Y = HX_M$, $X_M = X+X_N$.

$$
X = \frac{GC}{1+GCH}R+\frac{G}{1+GCH}U_P-\frac{GCH}{1+GCH}X_N,\qquad \frac XR = \frac{GC}{1+GC}\ (H = 1,\ U_P = X_N = 0)
$$

$$
\frac ER = \frac{1}{1+GC},\qquad e_{ss,\,\text{unit step}} = \frac{1}{1+G(0)C(0)}\ (\text{stable loop; }0\text{ with integral action})
$$

$$
u(t) = K_Pe+K_I\int_0^te\,d\tau+K_D\dot e\quad\Rightarrow\quad C(s) = K_P+\frac{K_I}{s}+K_Ds
$$

Single actions with $G = B/A$ (characteristic polynomial = denominator of $X/R$):

| Action | $X/R$ | Characteristic polynomial | Effect |
|---|---|---|---|
| P | $K_PB/(A+K_PB)$ | $A+K_PB$ | faster; error remains; oscillates at high gain |
| I | $K_IB/(As+K_IB)$ | $As+K_IB$ | removes step error; adds a pole (−90°); slower; wind-up |
| D | $K_DBs/(A+K_DBs)$ | $A+K_DBs$ | adds damping; no change to $\omega_n$ or error; amplifies noise |

SPO with elevator, concise derivatives ($\mathbf A = \mathbf M^{-1}\mathbf A'$ entries, $\mathbf x = [w,q]^T$, $\mathbf C = [0\ 1]$):

$$
\frac{q}{\eta} = \frac{m_\eta s+(m_wz_\eta-m_\eta z_w)}{s^2-(m_q+z_w)s+(z_wm_q-z_qm_w)},\qquad \frac{\theta}{\eta} = \frac1s\frac{q}{\eta}
$$

Course plant: $G = q/\eta = -1.39(s+0.306)/(s^2+0.805s+1.325)$, $G(0) = -0.321$.

Pole placement: match the closed-loop polynomial to $s^2+2\zeta\omega_ns+\omega_n^2$ term by term. Satellite PD on $1/(I_{zz}s^2)$ with $\rho = I_{zz-wh}/I_{zz}$: $k_p = -\omega_n^2/\rho$, $k_d = -2\zeta\omega_n/\rho$.

### Root locus ([[SESA2027 B2 - Root Locus Method]])

Characteristic equation $1+KG(s) = 0$, i.e. $A(s)+KB(s) = 0$, from the open-loop TF in ZPK form. For $K>0$:

$$
\lvert KG(s)\rvert = 1,\qquad \angle G(s) = \sum\angle(s-z_i)-\sum\angle(s-p_j) = (2k+1)\,180^\circ
$$

- Branches: start at the $n$ open-loop poles ($K = 0$), end at the $m$ zeros or at infinity ($K\to\infty$).
- Real axis: on the locus where the number of real poles plus zeros to the right is odd.
- Asymptotes: $n-m$ of them, at $\theta_k = \dfrac{(2k+1)\pi}{n-m}$ ($k = 0,1,\dots$, anticlockwise from $+$real axis), from $\sigma_a = \dfrac{\sum p-\sum z}{n-m}$ (real parts only).
- Departure/arrival angle: $\phi = \pi+\sum\angle(\text{to zeros})-\sum\angle(\text{to poles})$.
- Break-in/away: $\dfrac{dK}{ds} = 0$ with $K = -A/B$, i.e. $A'B-AB' = 0$; keep roots on a real-axis segment.
- Imaginary-axis crossing: Routh on $A+KB$, or substitute $s = i\omega$. Cubic $s^3+a_2s^2+a_1s+a_0$: marginal at $a_2a_1 = a_0$, with $\omega = \sqrt{a_1}$.
- Negative gain ($K<0$ or plant gain $<0$, as for the SPO): $\angle G = k\,360^\circ$, even count to the right, asymptotes at $k\,360^\circ/(n-m)$; run $K$ from 0 to $-\infty$.

Reading pole positions: $\omega_n = \lvert s\rvert$, $\zeta = \cos\beta$ ($\beta$ from the negative real axis); constant-$\zeta$ rays $\omega = \lvert\sigma\rvert\sqrt{1-\zeta^2}/\zeta$.

Double integrator $1/s^2$: P gives $s = \pm i\sqrt{K_P}$ (marginal for every $K_P$). PD with $K_P/K_D = r$: circle of radius $r$ about the zero at $-r$, break-in at $-2r$ when $K_D = 4r$, $\zeta = \sqrt{K_D/(4r)}$ on the circle.

### Frequency-response design and ZN ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]])

Margins on the open loop $L = CG$ (open loop stable, single 0 dB crossing):

$$
GM = -\lvert L(i\omega_{pc})\rvert_{dB}\ \ (\angle L = -180^\circ\text{ at }\omega_{pc}),\qquad PM = 180^\circ+\angle L(i\omega_{gc})\ \ (\lvert L\rvert = 0\ \text{dB at }\omega_{gc})
$$

No phase crossover ($\omega_{pc}\to\infty$) means $GM = \infty$.

Standard form: $C(s) = K_p\left(1+\dfrac{1}{T_Is}+T_Ds\right)$, $T_I = K_p/K_I$, $T_D = K_D/K_p$; $\left(1+\dfrac{1}{T_Is}+T_Ds\right)\approx(1+T_Ds)\left(1+\dfrac{1}{T_Is}\right)$.

Design at a chosen $\omega_{gc}$, $\phi_{current} = \angle G(i\omega_{gc})$:

$$
\phi_{PD} = PM_{target}-(180^\circ+\phi_{current}),\qquad T_D = \frac{\tan\phi_{PD}}{\omega_{gc}},\qquad T_I = \frac{3}{\omega_{gc}},\qquad K_p = \frac{1}{\lvert G(i\omega_{gc})\rvert\sqrt{1+(\omega_{gc}T_D)^2}}
$$

With $T_I = 3/\omega_{gc}$ the integral factor costs $\tan^{-1}(1/3) = 18.4^\circ$ at crossover and its magnitude 1.054 is neglected in $K_p$, so validate the step response and control effort.

Negative-gain plant (corrected L2.05 slides): invert $G$; read $\phi_{current}$ at the current crossover; if $\phi_{PD}<0$ only because of the inversion, use $\lvert\phi_{PD}\rvert$; restore the sign on $K_p$ for the real plant ($T_I$, $T_D$ stay positive). SPO example: $T_D = 0.342$ s, $T_I = 1.0$ s, $K_p = -1.345$.

| ZN ultimate sensitivity ($K_u$, $T_u$ at sustained oscillation, P only) | $K_p$ | $T_I$ | $T_D$ |
|---|---|---|---|
| P | $0.5K_u$ | – | – |
| PI | $0.45K_u$ | $T_u/1.2$ | – |
| PID | $0.6K_u$ | $0.5T_u$ | $0.125T_u$ |

| ZN reaction curve (open-loop S-shaped step: delay $L$, slope $R = A/\tau$) | $K_p$ | $T_I$ | $T_D$ |
|---|---|---|---|
| P | $1/(RL)$ | – | – |
| PI | $0.9/(RL)$ | $L/0.3$ | – |
| PID | $1.2/(RL)$ | $2L$ | $0.5L$ |

ZN quarter-decay target: $C/A = e^{-2\pi\zeta/\sqrt{1-\zeta^2}} = \tfrac14\Rightarrow\zeta = \dfrac{\ln4}{\sqrt{4\pi^2+(\ln4)^2}} = 0.215$, first overshoot $\sqrt{1/4} = 50$ %.

### Robustness ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]])

Gain signs: $T_D>0$ and $T_I>0$ always; $K_p$ takes the sign of the plant's static gain $G(0)$. Then $K_I = K_p/T_I$ and $K_D = K_pT_D$ share the sign of $K_p$.

Quadratic $s^2+bs+c$: stable iff $b>0$ and $c>0$ (Routh for $n = 2$).

P control of $G = K(s+z)/(s^2+2\zeta\omega_ns+\omega_n^2)$:

$$
\frac XR = \frac{KK_p(s+z)}{s^2+(KK_p+2\zeta\omega_n)s+(\omega_n^2+KK_pz)},\qquad KK_p>0\ \text{with matched signs}
$$

so $b>0$ always and only $c$ can fail, when $z<0$ (right-half-plane zero) and $\omega_n^2<KK_p\lvert z\rvert$.

Three closed-loop transfer functions, $H = 1$, $L = GC$:

$$
S = \frac{1}{1+L},\qquad T = \frac{L}{1+L},\qquad S+T = 1;\qquad \text{reference } T,\quad \text{disturbance } GS = \frac{G}{1+GC},\quad \text{noise } -T
$$

$\lvert L\rvert\gg1$ where commands and gusts are, $\lvert L\rvert\ll1$ where noise is. 1-cosine gust: $\alpha_g = \tfrac{A_g}{2}\left[1-\cos(2\pi t/T_g)\right]$.

- MIL-F-9490D: GM ≥ 4.5–6 dB and PM ≥ 30–45° (depending on mode frequency and airspeed); FAA/EASA give no numerical margins.
- SPO Level 1 damping (Cook Table 10.4): Category A 0.35–1.30, B 0.30–2.00, C 0.50–1.30.
- Manoeuvrability: $\lvert\partial q/\partial\eta\rvert_{max}$; DC gain $G(0)$. More stability: $\zeta$ up and/or $\omega_n$ down. More manoeuvrability: $\omega_n$ up, $\zeta$ down.
- Fix with the gain that owns the specification: $K_p\to\omega_n$ and rise time, $T_D\to\zeta$ and overshoot, $T_I\to$ steady state.

## Part C: Sensing

### Sensing elements ([[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]])

Measurement chain: sensor → signal conditioning → data acquisition (sampling, ADC) → processing.

Wheatstone bridge (meter draws no current, balanced when all four arms are equal):

$$
V_G = \left(\frac{R_2}{R_1+R_2}-\frac{R_4}{R_3+R_4}\right)V_s
$$

| Bridge (active gauges) | $V_G$ | Notes |
|---|---|---|
| Quarter ($R_2 = R+\Delta R$) | $\dfrac{\Delta R}{4R+2\Delta R}V_s\approx\dfrac{V_s}{4}G\varepsilon$ | $\Delta R\ll R$; $\varepsilon = 4V_G/(V_sG)$ |
| Half, bending ($R_2 = R+\Delta R$, $R_1 = R-\Delta R$) | $\dfrac{V_s}{2}G\varepsilon$ | exactly linear; temperature cancels |
| Full (four active) | $V_sG\varepsilon$ | |

Gauge factor (uniform wire, $dD/D = -\nu\varepsilon$):

$$
G = \frac{dR/R}{\varepsilon} = 1+2\nu+\frac{d\rho/\rho}{\varepsilon}
$$

Metal foil $G\approx2$: mostly geometry, $1+2\nu\approx1.6$ for $\nu\approx0.3$, plus a small piezoresistive term; semiconductor gauges, piezoresistance dominates ($G\sim100$).

| Principle | Relation | Conditions |
|---|---|---|
| Resistive | $R = \rho L/A$ | constant temperature |
| Thermoelectric (Seebeck) | $V = \alpha_T(T_h-T_c)$ | self-powered |
| Capacitive, gap | $C = \dfrac{\varepsilon_0\varepsilon A}{d+x}$, $\dfrac{\Delta C}{C_0}\approx-\dfrac xd$ | linear only for $x\ll d$; $\varepsilon_0 = 8.85$ pF/m |
| Capacitive, area | $C = \dfrac{\varepsilon_0\varepsilon}{d}(A-wx)$ | linear in $x$ |
| Diaphragm pressure | $\dfrac{\Delta C}{C} = \dfrac{(1-\nu^2)a^4}{16Edt^3}P$ | |
| Inductive | $L = \dfrac{n^2}{\mathfrak R_0+kd}$, $\mathfrak R = \dfrac{l}{\mu\mu_0A}$, $k = \dfrac{2}{\mu_0\pi r^2}$ | two air gaps of length $d$, fringing neglected |
| Piezoelectric | $q = dF$, $C = \varepsilon_0\varepsilon A/t$ | dynamic only |

Piezo with leakage $R$: $\dfrac{V}{F} = \dfrac dC\cdot\dfrac{\tau s}{\tau s+1}$, $\tau = RC$: high-pass, zero DC gain, so no output for a static load (cannot measure 1 g).

Complementary filter (gyro $\omega_g = \dot\theta+b$, accelerometer $\theta_a = \theta+n$, same $\tau$):

$$
\hat\theta = \frac{1}{\tau s+1}\theta_a+\frac{\tau s}{\tau s+1}\frac{\omega_g}{s} = \theta+\frac{n}{\tau s+1}+\frac{\tau b}{\tau s+1}
$$

$$
\hat\theta_k = \alpha\left(\hat\theta_{k-1}+\omega_{g,k}\Delta t\right)+(1-\alpha)\theta_{a,k},\qquad \alpha = \frac{\tau}{\tau+\Delta t}\ \Leftrightarrow\ \tau = \frac{\alpha\Delta t}{1-\alpha}
$$

Steady gyro-bias error $\tau b$ (bounded), against $bt$ for the integrated gyro alone.

### Sensor dynamics ([[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]])

Noise statistics at constant input, with each $x_i$ the error from a trusted reference:

$$
\mu = \frac1N\sum_{i=1}^Nx_i,\qquad \sigma^2 = \frac{1}{N-1}\sum_{i=1}^N(x_i-\mu)^2
$$

$\mu\neq0$ is bias (an accuracy problem); $\sigma$ is the spread (a precision problem); Gaussian noise has 95 % of readings within $\pm2\sigma$.

Span = upper limit − lower limit; sensitivity $S = \Delta V/\Delta P$ in the linear operating range; $S = 0$ at saturation and in a dead zone.

| Order | Model | Step metrics | Frequency |
|---|---|---|---|
| 0th | $y = Ku$ | instantaneous | flat, no phase |
| 1st | $\tau\dot y+y = Ku$, $\dfrac{K}{\tau s+1}$ | 63.2 % at $\tau$; $t_r = 2.2\tau$; $t_s = 4.6\tau$ (1 %); no overshoot | $\dfrac{K}{\sqrt{1+(\omega\tau)^2}}$, phase $-\tan^{-1}\omega\tau\approx-\omega\tau$ (delay $\tau$) |
| 2nd | $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y = K\omega_n^2u$ | $t_r\approx1.8/\omega_n$; $t_s\approx4.6/(\zeta\omega_n)$; $OS$ as in A4 (underdamped only) | see below |

Second-order reading at $r = \omega/\omega_n$:

$$
\frac{\lvert G\rvert}{K} = \frac{1}{\sqrt{(1-r^2)^2+(2\zeta r)^2}},\qquad \phi = -\tan^{-1}\frac{2\zeta r}{1-r^2}\approx-2\zeta r\ \ (\text{delay }2\zeta/\omega_n)
$$

$\zeta = 1/\sqrt2\approx0.7$ removes the $r^2$ term, $\lvert G\rvert/K = 1/\sqrt{1+r^4}$: within ±2 % up to $r = 0.47$ (0.64 at $\zeta\approx0.65$), with nearly constant delay. For $\zeta>1$ the $4.6/(\zeta\omega_n)$ rule under-predicts $t_s$.

Accelerometer (base-excited, $z$ relative to the case): $\ddot z+2\zeta\omega_n\dot z+\omega_n^2z = -a$, so $K = -1/\omega_n^2$ and $z\approx-a/\omega_n^2$ below resonance; a higher $\omega_n$ buys bandwidth at the cost of sensitivity.

RC filter: $G = \dfrac{1}{RCs+1}$, $\omega_c = \dfrac{1}{RC}$, $f_c = \dfrac{1}{2\pi RC}$; −3 dB and −45° at $\omega_c$, then −20 dB/dec.

### Digital bridge ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]])

Range mapping (sensor extremes onto ADC extremes; clipping if $V_{out}$ leaves the window):

$$
V_{out} = A_vV_{in}+V_{os},\qquad A_v = \frac{V_{ADC,max}-V_{ADC,min}}{V_{max}-V_{min}},\qquad V_{os} = V_{ADC,min}-A_vV_{min}
$$

Quantisation ($n$-bit ideal ADC; uniform error for signals spanning many levels):

$$
Q = \frac{V_{ADC,max}-V_{ADC,min}}{2^n},\quad N[k] = \mathrm{round}\!\left(\frac{V_{out}[k]}{Q}\right),\quad \lvert e_q\rvert\le\frac Q2,\quad \sigma_q = \frac{Q}{\sqrt{12}}
$$

Each extra bit halves $Q$ (−6 dB noise floor). DAC: $Q_{DAC} = (V_{DAC,max}-V_{DAC,min})/2^n$, $V_{cmd}[k] = V_{DAC,min}+N[k]Q_{DAC}$ (zero-order hold staircase).

Loading (voltage divider; buffer with a voltage follower):

$$
\frac{V_{meas}}{V_{sensor}} = \frac{Z_{in}}{Z_{out}+Z_{in}},\qquad \varepsilon_{load} = \frac{Z_{out}}{Z_{out}+Z_{in}}\ \ (\varepsilon<1\ \%\ \text{needs}\ Z_{in}>99Z_{out})
$$

Sampling and aliasing ($m$ chosen so the alias lands in $[0,f_N]$; in practice sample at about $10f_{max}$):

$$
f_N = \frac{f_s}{2},\qquad f_s>2f_{max},\qquad f_{alias} = \lvert f-mf_s\rvert\in[0,f_N],\qquad \text{anti-alias RC: }\tau\ge\frac{1}{\pi f_s}\Leftrightarrow f_c\le f_N
$$

Latency (pure delay $e^{-sT_d}$, crossover unchanged):

$$
T_d = T_{sensor}+T_{filter}+T_{ADC}+T_{buffer}+T_{processor}+T_{communication},\qquad PM_{new} = PM_{old}-\omega_{gc}T_d\ \ (\text{rad; }\times180/\pi\text{ for degrees})
$$

Digital processing, signal model $y[k] = x[k]+b[k]+n[k]$:

| Operation | Formula | Cost or property |
|---|---|---|
| Moving average (FIR) | $y_f[k] = \dfrac1N\displaystyle\sum_{i=0}^{N-1}y[k-i]$ | delay $\tfrac{N-1}{2}T_s$ at every frequency; $\sigma\to\sigma/\sqrt N$ |
| Recursive low-pass (IIR) | $y_f[k] = \alpha y[k]+(1-\alpha)y_f[k-1]$, $\alpha\approx\dfrac{T_s}{\tau+T_s}$ | $\tau = T_s(1-\alpha)/\alpha$; low-frequency delay $\tau$ |
| Median | middle value of the window | rejects isolated spikes |
| Difference derivative | $\dfrac{y[k]-y[k-1]}{T_s}$ | white noise gives $\sigma_{\dot y} = \sqrt2\,\sigma/T_s$ |
| Filtered derivative | $d[k] = \beta d[k-1]+(1-\beta)\dfrac{y[k]-y[k-1]}{T_s}$ | trades noise for lag |
| Integral | $I[k] = I[k-1]+T_sy[k]$ | constant bias gives error $kT_sb$ |
| Outlier test | $\lvert y[k]-y[k-1]\rvert>\Delta_{max}$ | hold, interpolate or flag |

In the recursive low-pass $\alpha$ weights the new sample; in the complementary filter (C1) it weights the gyro.

## Practice
- [[SESA2027 Mock Questions]] (self-written, one question per topic note)
- [[SESA2027 Practice Problems 1 Solutions]] (A3–A5) · [[SESA2027 Practice Problems 2 Solutions]] (A2, A5, B1–B3) · [[SESA2027 Part C Problem Sheet Solutions]] (C1–C3)

## Related
- [[SESA2027 Aerospace Mechanics & Control Hub]] · [[SESA2027 Cambridge Part IIA Practice]]
