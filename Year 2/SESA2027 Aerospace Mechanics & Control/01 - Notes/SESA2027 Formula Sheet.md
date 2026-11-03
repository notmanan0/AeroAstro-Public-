---
title: "SESA2027 Formula Sheet"
module: "SESA2027 Aerospace Mechanics & Control"
type: formula
aliases: ["SESA2027 formulae", "Mechanics and Control formula sheet"]
tags: [sesa2027, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources/Lectures"]
---

# SESA2027 Formula Sheet

Everything on one page, organised by part. Each section links to its topic note.

## Part A: Dynamic systems

### Equations of motion ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]])

$$
\mathbf F_B = m(\dot{\mathbf v}_B+\boldsymbol\omega_B\times\mathbf v_B),\qquad \mathbf M_B = \dot{\mathbf h}_B+\boldsymbol\omega_B\times\mathbf h_B,\qquad \mathbf h = \mathbf I\boldsymbol\omega
$$

$$
\mathbf R_{BE} = \mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi),\qquad \mathbf R^{-1} = \mathbf R^T,\qquad \mathbf g_B = g\,(-\sin\theta,\ \sin\phi\cos\theta,\ \cos\phi\cos\theta)
$$

$$
\frac{d\mathbf i}{dt} = r\mathbf j-q\mathbf k = \boldsymbol\omega\times\mathbf i,\qquad \boldsymbol\omega\times\mathbf v = (qW-rV,\ rU-pW,\ pV-qU)
$$

Symmetric aircraft ($I_{xy}=I_{yz}=0$): $M = I_{yy}\dot q+(I_{xx}-I_{zz})pr+I_{xz}(p^2-r^2)$; similar for $L$, $N$.

Linearised and decoupled about trim:

$$
\Delta X = m\dot u,\quad \Delta Z = m(\dot w-qU_\infty),\quad \Delta M = I_{yy}\dot q\ \big|\ \Delta Y = m(\dot v+rU_\infty),\quad \Delta L = I_{xx}\dot p-I_{xz}\dot r,\quad \Delta N = -I_{xz}\dot p+I_{zz}\dot r
$$

### State space and derivatives ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]])

$$
\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u,\quad \mathbf A = \mathbf M^{-1}\mathbf A',\quad \mathbf x = [u,w,q,\theta]^T,\qquad G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D
$$

$$
X_u = (\Lambda-2)C_D,\quad X_w = C_{L^*}-C_{D_\alpha},\quad Z_u = -2C_{L^*},\quad Z_w = -(C_{L^*_\alpha}+C_D),\quad M_w = -H_sC_{L^*_\alpha},\quad M_q = -KC_{L_{T,\alpha}}\frac{l}{\bar c}
$$

$$
Z_\eta = -\frac{S_T}{S}a_2,\qquad M_\eta = -\bar V_Ta_2,\qquad X_\eta = -2\frac{S_T}{S}k_TC_{L_T}a_2
$$

Gravity: $\Delta X_g = -mg\theta\cos\gamma_0$ and $\Delta Z_g = -mg\theta\sin\gamma_0$.

Dimensionalising: forces $\times\tfrac12\rho U_\infty^2S$, moments $\times$ an extra $\bar c$; per perturbation divide by $U_\infty$ ($u$, $w$), $U_\infty/\bar c$ ($q$) or $U_\infty^2/\bar c$ ($\dot w$). So $\mathring Z_w = Z_w\tfrac12\rho U_\infty S$, $\mathring M_q = M_q\tfrac12\rho U_\infty S\bar c^2$, $\mathring M_{\dot w} = M_{\dot w}\tfrac12\rho S\bar c^2$.

$2\times2$ shortcut: $\mathrm{adj}\begin{bmatrix}a&b\\c&d\end{bmatrix} = \begin{bmatrix}d&-b\\-c&a\end{bmatrix}$.

### Modes ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]])

$$
\det(\lambda\mathbf I-\mathbf A) = 0,\qquad \lambda = \sigma\pm i\omega,\qquad \omega_n = \sqrt{\sigma^2+\omega^2},\quad \zeta = -\frac{\sigma}{\omega_n}
$$

$$
T = \frac{2\pi}{\omega},\qquad t_{1/2} = \frac{\ln2}{|\sigma|},\qquad t_2 = \frac{\ln2}{\sigma}
$$

**Routh (quartic)**: all coefficients $>0$ and $R = D(BC-AD)-B^2E>0$.

**SPO approximation**:

$$
\omega_n^2 = \frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad \zeta = -\frac{m(\mathring M_q+U_\infty\mathring M_{\dot w})+\mathring Z_wI_{yy}}{2\omega_nmI_{yy}}
$$

**Phugoid (Lanchester)**: $\omega_{ph}\approx\sqrt2\,g/U_\infty$.

### Laplace and step response ([[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]])

$$
\mathcal L\{\dot g\} = sG-g(0),\quad \mathcal L\{\ddot g\} = s^2G-sg(0)-\dot g(0),\quad \mathcal L\{1\} = \frac1s,\quad \mathcal L\{e^{\sigma t}\sin\omega t\} = \frac{\omega}{(s-\sigma)^2+\omega^2},\quad \mathcal L\{g(t-a)\} = e^{-as}G
$$

$$
\lim_{t\to\infty}g = \lim_{s\to0}sG(s)
$$

$$
t_r\approx\frac{1.8}{\omega_n},\qquad OS = 100\,e^{-\zeta\pi/\sqrt{1-\zeta^2}}\,\%,\qquad t_p = \frac{\pi}{\omega_n\sqrt{1-\zeta^2}},\qquad t_s\approx\frac{4.6}{\zeta\omega_n}\ (1\%),\ \frac{3}{\zeta\omega_n}\ (5\%)
$$

| $\zeta$ | 0.2 | 0.35 | 0.4 | 0.5 | 0.7 |
|---|---|---|---|---|---|
| OS | 52.7 % | 30.9 % | 25.4 % | 16.3 % | 4.6 % |

Normalised step response ($0<\zeta<1$, $\omega_d = \omega_n\sqrt{1-\zeta^2}$): $x(t) = 1-e^{-\zeta\omega_nt}\left(\cos\omega_dt+\dfrac{\zeta}{\sqrt{1-\zeta^2}}\sin\omega_dt\right)$. The $t_s$ rule fails for $\zeta>1$.

First order $K/(\tau s+1)$: $y = K(1-e^{-t/\tau})$, $t_r = 2.2\tau$, $t_s = 4.6\tau$ (1 %), no overshoot.

### Frequency response ([[SESA2027 A5 - Frequency Response and Bode Plots]])

$$
x_{ss} = A|G(i\omega)|\sin(\omega t+\angle G(i\omega)),\qquad |G|_{dB} = 20\log_{10}|G|
$$

$$
\omega_r = \omega_n\sqrt{1-2\zeta^2},\qquad M_r = \frac{1}{2\zeta\sqrt{1-\zeta^2}}\ (\zeta<0.707),\qquad |G(i\omega_n)| = \frac{1}{2\zeta},\ \angle = -90^\circ
$$

Bode slopes per factor: real pole −20 dB/dec and −90°; complex pair −40 dB/dec and −180°; zeros are the mirror image. Real pole at its corner: −3.01 dB and −45°.

$$
\omega_b = \omega_n\sqrt{1-2\zeta^2+\sqrt{4\zeta^4-4\zeta^2+2}}\ (-3\ \text{dB}),\qquad \lvert e^{-i\omega T}\rvert = 1,\ \angle e^{-i\omega T} = -\omega T
$$

## Part B: Control

### Closed loop and PID ([[SESA2027 B1 - Control System Fundamentals and PID Control]])

$$
\frac XR = \frac{GC}{1+GCH},\qquad C(s) = K_P+\frac{K_I}{s}+K_Ds = K_p\left(1+\frac{1}{T_Is}+T_Ds\right),\qquad e_{ss,step} = \frac{1}{1+G(0)C(0)}
$$

$$
X = \frac{GC}{1+GCH}R+\frac{G}{1+GCH}U_P-\frac{GCH}{1+GCH}X_N
$$

A quadratic $s^2+bs+c$ is stable iff $b>0$ and $c>0$.

Closed-loop characteristic polynomials with $G = B/A$: P $A+K_PB$; I $As+K_IB$; D $A+K_DBs$.

### Root locus ([[SESA2027 B2 - Root Locus Method]])
- **Real axis**: on the locus where the number of poles plus zeros to the right is odd.
- **Asymptotes**: $n-m$ of them, at angles $\dfrac{(2k+1)\pi}{n-m}$, with centroid $\sigma_a = \dfrac{\sum p-\sum z}{n-m}$.
- **Break-away**: $\dfrac{dK}{ds} = 0$ with $K = -A/B$, i.e. $A'B-AB' = 0$ (keep roots on the locus).
- Negative plant gain (SPO): run $K$ from 0 to $-\infty$.
- **Reading pole positions**: $\zeta = \cos\beta$ and $\omega_n = |s|$.
- **Underlying conditions**: $1+KG = 0\Rightarrow\lvert KG\rvert = 1$ and $\angle G = (2k+1)180°$ for $K>0$ ($k\,360°$ for $K<0$).

### Frequency-response design and ZN ([[SESA2027 B3 - Frequency-Response PID Design and Ziegler-Nichols Tuning]])

$$
GM = -|L(i\omega_{pc})|_{dB},\qquad PM = 180^\circ+\angle L(i\omega_{gc})
$$

$$
\phi_{PD} = PM_{target}-(180^\circ+\angle G(i\omega_{gc})),\qquad T_D = \frac{\tan\phi_{PD}}{\omega_{gc}},\qquad T_I = \frac{3}{\omega_{gc}},\qquad K_p = \frac{1}{|G(i\omega_{gc})|\sqrt{1+(\omega_{gc}T_D)^2}}
$$

Negative-gain plant (corrected L2.05 slides): invert $G$ first; read $\angle G$ at the current crossover; if $\phi_{PD}<0$ only because of the inversion, use $|\phi_{PD}|$; implement $K_p$ with the sign of the real plant's static gain. SPO example: $T_D = 0.342$ s, $T_I = 1.0$ s, $|K_p| = 1.345$. The integral factor costs $\tan^{-1}(1/3) = 18.4°$ at crossover when $T_I = 3/\omega_{gc}$.

| ZN (ultimate) | $K_p$ | $T_I$ | $T_D$ |
|---|---|---|---|
| P | $0.5K_u$ | – | – |
| PI | $0.45K_u$ | $T_u/1.2$ | – |
| PID | $0.6K_u$ | $0.5T_u$ | $0.125T_u$ |

ZN quarter-decay target: $C/A = e^{-2\pi\zeta/\sqrt{1-\zeta^2}} = \tfrac14\Rightarrow\zeta = 0.215$, first overshoot 50 %.

### Robustness ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]])
- MIL-F-9490D: GM ≥ 4.5–6 dB and PM ≥ 30–45°.
- SPO Level 1 damping: Category A 0.35–1.30, B 0.30–2.00, C 0.50–1.30.
- Rules: $T_D>0$ and $T_I>0$; choose the sign of $K_p$ to match the plant. Then $K_I = K_p/T_I$ and $K_D = K_pT_D$ share the sign of $K_p$.
- P control of $K(s+z)/(s^2+2\zeta\omega_ns+\omega_n^2)$: $s^2+(KK_p+2\zeta\omega_n)s+(\omega_n^2+KK_pz)$, with $KK_p>0$ when the signs are matched.
- Sensitivity $S = 1/(1+GC)$, complementary sensitivity $T = GC/(1+GC)$: $S+T = 1$. Reference TF $T$, disturbance TF $GS$, noise TF $-T$ ($H = 1$).

## Part C: Sensing

### Sensing elements ([[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]])

$$
R = \frac{\rho L}{A},\qquad V_G = \left(\frac{R_2}{R_1+R_2}-\frac{R_4}{R_3+R_4}\right)V_s,\qquad \frac{\Delta R}{R}\approx\frac{4V_G}{V_s} = G\varepsilon\ (\text{quarter bridge})
$$

$$
V = \alpha_T(T_h-T_c),\qquad C = \frac{\varepsilon_0\varepsilon A}{d},\qquad L = \frac{n^2}{\mathfrak R_0+kd},\qquad q = dF
$$

Half bridge (bending, adjacent arms): $V_G = \dfrac{V_s}{2}G\varepsilon$ (exactly linear); full bridge $V_sG\varepsilon$.

Gauge factor: $G = \dfrac{dR/R}{\varepsilon} = 1+2\nu+\dfrac{d\rho/\rho}{\varepsilon}\approx2$ for metals ($\nu\approx0.3$ gives 1.6 from geometry alone).

Piezo with leakage $R$: $\dfrac{V}{F} = \dfrac dC\cdot\dfrac{\tau s}{\tau s+1}$, $\tau = RC$ (no static output). Two-gap inductive sensor: $k = 2/(\mu_0\pi r^2)$.

$$
\text{Complementary filter: }\hat\theta_k = \alpha\left(\hat\theta_{k-1}+\omega_k\Delta t\right)+(1-\alpha)\theta_{acc,k},\qquad \alpha = \frac{\tau}{\tau+\Delta t},\qquad \text{gyro-bias error}\to\tau b
$$

### Sensor dynamics ([[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]])

$$
y = Ku,\qquad \frac{K}{\tau s+1}\ (63.2\%\ \text{at}\ t = \tau),\qquad \frac{K\omega_n^2}{s^2+2\zeta\omega_ns+\omega_n^2}\ (\zeta_{opt}\approx0.7)
$$

$$
\mu = \frac1N\sum x_i,\qquad \sigma^2 = \frac{1}{N-1}\sum(x_i-\mu)^2
$$

Accelerometer (base-excited, $z$ relative to the case): $\ddot z+2\zeta\omega_n\dot z+\omega_n^2z = -a$, so $K = -1/\omega_n^2$ and $z\approx-a/\omega_n^2$ below resonance.

RC filter: $G = \dfrac{1}{RCs+1}$, $\omega_c = \dfrac{1}{RC}$, $f_c = \dfrac{\omega_c}{2\pi}$. It is −3 dB and −45° at $\omega_c$, then falls at −20 dB/dec.

Second-order reading at $r = \omega/\omega_n$: $\dfrac{\lvert G\rvert}{K} = \dfrac{1}{\sqrt{(1-r^2)^2+(2\zeta r)^2}}$; low-frequency delay $2\zeta/\omega_n$; within ±2 % up to $r = 0.47$ at $\zeta = 0.7$.

### Digital bridge ([[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]])

$$
V_{out} = A_vV_{in}+V_{os},\quad A_v = \frac{V_{ADC,max}-V_{ADC,min}}{V_{max}-V_{min}},\quad V_{os} = V_{ADC,min}-A_vV_{min}
$$

$$
Q = \frac{V_{range}}{2^n},\quad |e_q|\le\frac Q2,\quad \sigma_q = \frac{Q}{\sqrt{12}}
$$

$$
\frac{V_{meas}}{V_{sensor}} = \frac{Z_{in}}{Z_{out}+Z_{in}},\quad \varepsilon_{load} = \frac{Z_{out}}{Z_{out}+Z_{in}}
$$

$$
f_N = \frac{f_s}2,\quad f_s>2f_{max},\quad f_{alias} = |f-mf_s|,\quad \tau_{AA} = RC\ge\frac{1}{\pi f_s}
$$

$$
T_d = \sum T_i,\qquad \phi_d = -\omega T_d,\qquad PM_{new} = PM_{old}-\omega_{gc}T_d
$$

$$
y_f = \frac1N\sum y[k-i]\ \left(\text{delay}\ \tfrac{N-1}{2}T_s\right),\qquad y_f[k] = \alpha y[k]+(1-\alpha)y_f[k-1],\ \alpha\approx\frac{T_s}{\tau+T_s}
$$

$$
d[k] = \beta d[k-1]+(1-\beta)\frac{y[k]-y[k-1]}{T_s},\qquad I[k] = I[k-1]+T_sy[k]\ \Rightarrow\ \text{bias error } kT_sb
$$

Noise: an $N$-point average divides $\sigma$ by $\sqrt N$; a difference derivative gives $\sigma_{\dot y} = \sqrt2\,\sigma/T_s$.

## Practice
- [[SESA2027 Mock Questions]] (self-written, one question per topic note)

## Related
- [[SESA2027 Aerospace Mechanics & Control Hub]] · [[SESA2027 Practice Problems 1 Solutions]] · [[SESA2027 Practice Problems 2 Solutions]] · [[SESA2027 Part C Problem Sheet Solutions]]
