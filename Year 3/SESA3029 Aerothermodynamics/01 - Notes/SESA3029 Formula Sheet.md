---
title: "SESA3029 Formula Sheet"
module: "SESA3029 Aerothermodynamics"
type: formula
aliases: ["SESA3029 formulae", "Aerothermodynamics formula sheet"]
tags: [sesa3029, formula, exam-prep]
status: in-progress
coverage: "Week 1 and Lectures 2.1–2.7, 3.1–3.4, 4.1–4.6 (lectured); Lectures 5.1–5.10, heat transfer, written ahead from the slides (5.1 checked against last year's recording; this year's awaited)"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures"]
---

# SESA3029 Formula Sheet

Current coverage: **Week 1, Lectures 2.1–2.7, 3.1–3.4 and 4.1–4.6** (lectured), plus **Lectures 5.1–5.10, heat transfer, written ahead** from the slides (5.1 checked against last year's recording; this year's recordings awaited). For what the **official** exam sheet provides, see [[#What the exam formula sheet gives you]].

## Which relation? Given → choose → check

The official sheet gives equations, not the decisions between them. This table lists the choices that come up repeatedly.

| Given | Choose | Check |
|---|---|---|
| Pitot pressure $p_{02}$ and a static pressure from a tapping **ahead of** the probe ($p_1$) | Form $p_{02}/p_1$. If $\le1.893$ the flow is subsonic: isentropic $p_0/p$ gives $M_1$. If $>1.893$: supersonic, so use the Rayleigh Pitot formula (NST $p_{02}/p_1$ column) | 1.893 is $p_0/p$ at $M=1$. A supersonic answer must give $M_1>1$ ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#7. Pitot probe: three regimes|W01 §7]]) |
| Pitot pressure and a static tapping **on the probe, behind** the bow shock ($p_2$) | Isentropic $p_{02}/p_2$ gives $M_2$; then the normal-shock relations backwards give $M_1$ | $M_2<1$; $M_1>1$; $p_2>p_1$ ([[SESA3029 Test 1 - Solutions#Q5. Supersonic Pitot probe with the static tapping moved behind the shock|Test 1 Q5]]) |
| A wall turns **into** the flow (concave corner, wedge, ramp) | Oblique shock: $\theta$–$\beta$–$M$, weak solution, then normal-shock relations with $M_{n1}$ | $\theta\le\theta_{max}(M_1)$, else detached (bow) shock; $p$ and $s$ rise; $M_2<M_1$ |
| A wall turns **away from** the flow (convex corner) | Prandtl–Meyer fan: $\nu_2=\nu_1+\theta$, isentropic ratios | $p$ falls; $p_0$ unchanged; $\nu_2\le\nu_{max}$ |
| Shock normal to the stream (duct, nose of a blunt body on the stagnation line, starting shock) | Normal shock: NST with $M_1$ | $M_1>1$; $T_0$ and $\dot m$ unchanged, $p_0$ falls |
| An area ratio $A/A^*$ in a nozzle | **Subsonic root** upstream of the throat, or anywhere if the throat is unchoked or downstream of a shock; **supersonic root** downstream of a choked throat with no shock upstream | Compare $p_b$ with $p_{b3}$, $p_{b5}$, $p_{b6}$; the 0.528 is a **throat** pressure, not a back pressure ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]) |
| Nozzle exit pressure $p_e$ vs ambient $p_\infty$ (supersonic exit) | $p_e<p_\infty$: over-expanded, oblique lip shocks. $p_e>p_\infty$: under-expanded, lip fans. Equal: design | Lip-shock $M_{n1}$ relation; lip-fan $\nu(M_j)-\nu(M_e)$ |
| MoC point P from A (below) and B (above) | Along the $C^+$ from A carry $R^+_A=\nu-\theta$; along the $C^-$ from B carry $R^-_B=\nu+\theta$ | Recompute $R^\pm$ from $\nu_P,\theta_P$; slopes use **averaged** $\theta\pm\mu$ |
| MoC point on a wall or the centreline | Wall: the one arriving invariant plus $\theta_W$. Centreline: $\theta_P=0$ plus the arriving $R^-$ | A wall reflects only if $\theta_A\neq\theta_W$ |
| Thin aerofoil, subsonic $M_\infty$, incompressible $C_{p0}$ or $C_{l0}$ known | Prandtl–Glauert: divide by $\sqrt{1-M_\infty^2}$ (Kármán–Tsien if asked) | $M_\infty$ below about 0.8 and below $M_{crit}$ ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation\|W07b]]) |
| Thin aerofoil, supersonic, small angles, "linear" or "Ackeret" | $C_p=2\theta/\lambda$ face by face; $C_l=4\alpha/\lambda$ | Radians; $\theta$ from $\vec U_\infty$, + for compression (face and nearby streamline form a converging duct), − for expansion (diverging duct). "Exact" means shock-expansion instead ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils\|W07c]]) |
| Steady 1-D conduction through composite walls, pipes or insulation | Thermal resistance network in series/parallel; check $r_{cr}=k/h$ (cylinder) or $2k/h$ (sphere) when adding insulation | Units of $R_{\rm th}$ are K/W; cylindrical wall uses $\ln(r_o/r_i)/(2\pi kL)$; adding insulation raises $\dot Q$ while $r_o<r_{cr}$ ([[SESA3029 W09a - Heat Conduction and Thermal Resistance\|W09a]], [[SESA3029 W09c - Critical Thickness of Insulation and Fins\|W09c]]) |
| Flat plate in external flow (forced convection) | Check $\mathrm{Re}_L$ against $\mathrm{Re}_{cr}=3\times10^5$ (slides; or tripped $x_t$): all-laminar ($\overline{\mathrm{Nu}}_L=2\mathrm{Nu}_L$), all-turbulent ($\overline{\mathrm{Nu}}_L=1.25\mathrm{Nu}_L$), or split the integral at $x_t$ | Properties at $T_f=(T_s+T_\infty)/2$; use the correlation the paper prints if it differs from $0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy\|W09b]]) |
| Fin heat transfer and tip condition | Compute $a=\sqrt{hp/(kA_c)}$ and $aL$: adiabatic tip if insulated/thin ($\tanh aL$), infinite fin if $aL\gtrsim2.65$, or exact tip convection | Check whether $\eta_{\mathrm{fin}}$ and $\epsilon_{\mathrm{fin}}$ are asked; fin only helps if $\epsilon_{\mathrm{fin}}>1$ ([[SESA3029 W09c - Critical Thickness of Insulation and Fins\|W09c]]) |
| Thermal radiation between surfaces or to space | Temperatures in kelvin; small grey body in large surroundings $\epsilon\sigma A(T_1^4-T_2^4)$, or two black surfaces $A_1F_{12}\sigma(T_1^4-T_2^4)$ via reciprocity and $\sum_jF_{ij}=1$ | °C in $T^4$ gives a wrong answer even for a temperature difference; $F_{ii}=0$ for flat/convex surfaces; openings count as imaginary black surfaces ([[SESA3029 W09d - Thermal Radiation\|W09d]]) |
| Finite-difference conduction node (steady or explicit transient) | Interior: check $\Delta x=\Delta y$ vs non-square $s=(\Delta y/\Delta x)^2$, or 1-D radial $(i\pm\tfrac12)/(2i)$. Boundary/corner: control-volume energy balance (half cell inside solid) | Steady face inflows sum to 0; explicit stability needs every old-$T$ coefficient $\ge0$ ($\mathcal F\le\tfrac12$ in 1-D, $\tfrac14$ in 2-D, $\mathcal F(1+\mathrm{Bi})\le\tfrac12$ at convective end) ([[SESA3029 W09e - Numerical Methods in Conduction\|W09e]]) |
| Heat exchanger: sizing vs rating | All 4 temperatures known (or 2 + energy balance) → LMTD for $A_s$ or $L$. Hardware $UA_s$ and inlets known → $\epsilon$–NTU for outlets | Use $c=0$ ($\epsilon=1-e^{-\mathrm{NTU}}$) for condensers/boilers and $\epsilon=\mathrm{NTU}/(1+\mathrm{NTU})$ for counter-flow $c=1$; use counter-flow relations on multi-pass exam questions when the paper prescribes them or gives no $F$-chart ([[SESA3029 W09f - Heat Exchangers\|W09f]]) |

## Mach number and gas properties

$$
M=\frac{U}{a},\qquad a=\sqrt{\gamma RT},\qquad p=\rho RT,
$$

$$
e=c_vT,\qquad h=c_pT,\qquad R=c_p-c_v,
\qquad \gamma=\frac{c_p}{c_v}.
$$

## Aerodynamic coefficients

$$
q_\infty=\frac12\rho_\infty U_\infty^2,
\qquad
C_L=\frac{L}{q_\infty S},\quad
C_D=\frac{D}{q_\infty S},\quad
C_M=\frac{M}{q_\infty S\bar c}.
$$

$$
L=F_n\cos\alpha-F_t\sin\alpha,\qquad
D=F_t\cos\alpha+F_n\sin\alpha.
$$

Exact, for a point $x$ aft of the LE **along the chord** ($C_n=F_n'/q_\infty c$, nose-up positive):

$$
C_{m,x}=C_{m,LE}+\frac{x}{c}C_n,\qquad
\frac{x_{CP}}{c}=-\frac{C_{m,LE}}{C_n},\qquad
\frac{x_{AC}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_n}.
$$

Lecture form (small $\alpha$, $C_n\approx C_l$): $C_{m,x}\approx C_{m,LE}+(x/c)C_l$, $x_{CP}/c\approx-C_{m,LE}/C_l$, $x_{AC}/c\approx-\mathrm dC_{m,LE}/\mathrm dC_l$. At $10^\circ$ supersonic these differ by 1–5% ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]]).

## Isentropic and stagnation relations

$$
s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}.
$$

$$
\frac{p_2}{p_1}
=\left(\frac{\rho_2}{\rho_1}\right)^\gamma
=\left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)}.
$$

$$
h+\frac{U^2}{2}=h_0,\qquad
\frac{T_0}{T}=1+\frac{\gamma-1}{2}M^2.
$$

For isentropic deceleration:

$$
\frac{p_0}{p}=\left(1+\frac{\gamma-1}{2}M^2\right)^{\gamma/(\gamma-1)},\qquad
\frac{\rho_0}{\rho}=\left(1+\frac{\gamma-1}{2}M^2\right)^{1/(\gamma-1)}.
$$

## Normal shock

$$
\rho_1U_1=\rho_2U_2,\qquad
p_1+\rho_1U_1^2=p_2+\rho_2U_2^2,\qquad
h_1+\frac{U_1^2}{2}=h_2+\frac{U_2^2}{2}.
$$

$$
U_1U_2=\frac{2a_0^2}{\gamma+1}.
$$

$$
\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2},\qquad
\frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}(M_1^2-1),
$$

$$
\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1},\qquad
M_2^2=\frac{2+(\gamma-1)M_1^2}{2\gamma M_1^2-(\gamma-1)}.
$$

Stagnation-pressure ratio (from $p_{02}/p_2\cdot p_2/p_1\cdot p_1/p_{01}$; [[SESA3029 Test 2 - Solutions#Q1. Mach number from the stagnation-pressure loss|Test 2 Q1]]):

$$
\frac{p_{02}}{p_{01}}=\left[\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\right]^{\gamma/(\gamma-1)}\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}.
$$

Strong-shock limits:

$$
M_2^2\to\frac{\gamma-1}{2\gamma},\qquad
\frac{\rho_2}{\rho_1}\to\frac{\gamma+1}{\gamma-1}.
$$

## Linear interpolation

$$
\sigma=\frac{x_t-x_a}{x_b-x_a},\qquad
y_t=y_a+\sigma(y_b-y_a).
$$

## Pitot relations

Incompressible:

$$
U=\sqrt{\frac{2(p_0-p)}{\rho}}.
$$

Compressible subsonic:

$$
M^2=\frac{2}{\gamma-1}\left[\left(\frac{p_0}{p}\right)^{(\gamma-1)/\gamma}-1\right],
$$

$$
U=\sqrt{\frac{2\gamma RT}{\gamma-1}\left[\left(\frac{p_0}{p}\right)^{(\gamma-1)/\gamma}-1\right]}.
$$

Supersonic ([[Rayleigh Pitot Formula]]):

$$
\frac{p_{02}}{p_1}
=\left[\frac{(\gamma+1)M_1^2}{2}\right]^{\gamma/(\gamma-1)}
\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}.
$$

For air, the sonic discriminator is

$$
\left.\frac{p_0}{p}\right|_{M=1}=1.8929.
$$

## Oblique shock (Week 2)

Angles $\theta$ (deflection) and $\beta$ (shock) are both measured from $\mathbf V_1$.

$$
M_{n1}=M_1\sin\beta,\qquad M_{t1}=M_1\cos\beta,\qquad
M_{n2}=M_2\sin(\beta-\theta),\qquad U_{t1}=U_{t2}.
$$

Use every normal-shock relation above with $M_1\to M_{n1}$ and $M_2\to M_{n2}$, including $p_{02}/p_{01}$. Then

$$
M_2=\frac{M_{n2}}{\sin(\beta-\theta)},\qquad
\frac{\rho_2}{\rho_1}=\frac{\tan\beta}{\tan(\beta-\theta)}.
$$

$\theta$–$\beta$–$M$ relation ([[Theta-Beta-Mach Relation]]):

$$
\tan\theta=2\cot\beta\left[\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}\right],
\qquad \mu\le\beta\le90^\circ.
$$

Maximum deflection for air: $\theta_{max}=12.1^\circ,\ 23.0^\circ,\ 34.1^\circ,\ 41.1^\circ,\ 45.6^\circ$ at $M_1=1.5,\ 2,\ 3,\ 5,\ \infty$.

Derived in [[SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation]] (perfect gas):

$$
\frac{\rho_2}{\rho_1}=\frac{\tan\beta}{\tan(\beta-\theta)}=\frac{(\gamma+1)M_1^2\sin^2\beta}{2+(\gamma-1)M_1^2\sin^2\beta},\qquad
U_{n1}U_{n2}=\frac{2a_0^2-(\gamma-1)U_t^2}{\gamma+1}\ (\text{oblique Prandtl relation}).
$$

Cubic in $\tan\beta$ (weak, strong and one rejected negative root):

$$
\left(1+\tfrac{\gamma-1}{2}M_1^2\right)\tan\theta\,\tan^3\beta-\left(M_1^2-1\right)\tan^2\beta+\left(1+\tfrac{\gamma+1}{2}M_1^2\right)\tan\theta\,\tan\beta+1=0 .
$$

Shock angle at $\theta_{max}$ and on the sonic line ($M_2=1$):

$$
\sin^2\beta_{\theta_{max}}=\frac{(\gamma+1)M_1^2-4+\sqrt{(\gamma+1)\left[(\gamma+1)M_1^4+8(\gamma-1)M_1^2+16\right]}}{4\gamma M_1^2},
$$

$$
\sin^2\beta^*=\frac{(\gamma+1)M_1^2-(3-\gamma)+\sqrt{(\gamma+1)\left[(\gamma+1)M_1^4-2(3-\gamma)M_1^2+\gamma+9\right]}}{4\gamma M_1^2} .
$$

$\beta^*<\beta_{\theta_{max}}$, so the strong branch is always subsonic; the weak branch is subsonic only in the thin band between them ($22.71^\circ<\theta<22.97^\circ$ at $M_1=2$). Limits: $\theta_{max}\to0$ as $M_1\to1$; $\theta_{max}\to\sin^{-1}(1/\gamma)=45.58^\circ$ at $\sin^2\beta=(\gamma+1)/(2\gamma)$ as $M_1\to\infty$.

Weak-shock limit (small $\theta$, radians): the shock leaves the Mach line linearly and its pressure is Ackeret's:

$$
\beta-\mu\approx\frac{(\gamma+1)M_1^2}{4\left(M_1^2-1\right)}\,\theta,\qquad C_p\approx\frac{2\theta}{\sqrt{M_1^2-1}} .
$$

Given $\theta$ and $\beta$, the relation is linear in $M_1^2$ ([[SESA3029 Test 2 - Solutions#Q3. Mach number from the oblique-shock chart|Test 2 Q3]]):

$$
M_1^2=\frac{2\left(\cot\beta+\tan\theta\right)}{\sin2\beta-\tan\theta\,(\gamma+\cos2\beta)}.
$$

## Mach angle

$$
\mu=\sin^{-1}\!\left(\frac1M\right).
$$

## Shock chains, reflections and slip lines

Ratios across successive shocks multiply:

$$
\frac{p_3}{p_1}=\frac{p_3}{p_2}\frac{p_2}{p_1},
\qquad
\frac{p_{03}}{p_{01}}=\frac{p_{03}}{p_{02}}\frac{p_{02}}{p_{01}}.
$$

- **Wall reflection:** the same $\theta$ again, from $M_2$. Then $\phi=\beta_B-\theta$. Regular only while $\theta\le\theta_{max}(M_2)$.
- **Slip line:** $p$ and flow direction equal on both sides; $V$, $T$, $\rho$ and $s$ may jump.

Entropy across a shock, with $m=M_{n1}^2-1$ ([[Entropy Change Across a Shock]]):

$$
\frac{s_2-s_1}{c_v}=\ln\frac{p_2}{p_1}-\gamma\ln\frac{\rho_2}{\rho_1}\approx\frac{2\gamma(\gamma-1)}{3(\gamma+1)^2}\,m^3,
\qquad
\frac{p_{02}}{p_{01}}=e^{-(s_2-s_1)/R}.
$$

## Prandtl–Meyer expansion

$$
\mathrm d\nu=\sqrt{M^2-1}\,\frac{\mathrm dU}{U},
\qquad
\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}(M^2-1)}-\tan^{-1}\sqrt{M^2-1}.
$$

$$
\nu(M_2)=\nu(M_1)+\theta,
\qquad
\phi_{fan}=\mu_1-\mu_2+\theta.
$$

As $M\to\infty$, $\nu_{max}=90^\circ\left(\sqrt{\tfrac{\gamma+1}{\gamma-1}}-1\right)$: **130.45° for $\gamma=1.4$** (air, the IFT), but 163.3° for the coursework's CO₂ ($\gamma=1.289$).

Across a fan, $p_0$ and $T_0$ are constant: use the isentropic ratios. Assumes a steady, planar, isentropic turn of a supersonic stream ($M_1>1$); $\nu$ and $\theta$ in degrees with the IFT, radians in any calculus.

## Shock-expansion method

Flat plate at incidence $\alpha$, with $q_\infty=\tfrac12\gamma p_\infty M_\infty^2$ and $\Delta p=p_L-p_U$:

$$
C_l=\frac{\Delta p\cos\alpha}{q_\infty},
\qquad
C_d=\frac{\Delta p\sin\alpha}{q_\infty},
\qquad
C_{m,LE}=-\frac{\Delta p}{2q_\infty},
\qquad
x_{cp}=\frac c2.
$$

Moment transfer and the two centres. Exact along the chord, with $C_n=\Delta p/q_\infty$ for the plate:

$$
C_{m,x}=C_{m,LE}+\frac xc\,C_n,
\qquad
\frac{x_{cp}}{c}=-\frac{C_{m,LE}}{C_n},
\qquad
\frac{x_{ac}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_n}\approx-\frac{\Delta C_{m,LE}}{\Delta C_n}.
$$

The lecture form uses $C_l$ in place of $C_n$ (small-$\alpha$ form): flat plate $x_{cp}/c=1/(2\cos\alpha)=0.508$ at $10^\circ$ against exactly 0.5 along the chord; triangular wing (Tutorial 1) $-\Delta C_m/\Delta C_l=0.487$ against $-\Delta C_m/\Delta C_n=0.468$.

Supersonic ac $\approx c/2$; subsonic $\approx c/4$. Thick section: resolve **each face's** force; with normal force $N'$ and chordwise force $A'$, $L'=N'\cos\alpha-A'\sin\alpha$ and $D'=N'\sin\alpha+A'\cos\alpha$.

Linear (Ackeret) limit, previewing Weeks 7–8. Thin aerofoil, small angles, $M$ supersonic but not close to 1 or hypersonic; $\theta$, $\alpha$, $\varepsilon$ in **radians**:

$$
C_p=\frac{2\theta}{\sqrt{M^2-1}},
\qquad
C_l=\frac{4\alpha}{\sqrt{M^2-1}},
\qquad
C_d=\frac{4(\alpha^2+\varepsilon^2)}{\sqrt{M^2-1}}\ \ (\text{diamond}).
$$

## Quasi-1D nozzle flow

The mass, momentum and isentropic relations (the momentum balance includes the side-wall force $(p+\tfrac12\mathrm dp)\,\mathrm dA$):

$$
\frac{\mathrm d\rho}{\rho}+\frac{\mathrm dU}{U}+\frac{\mathrm dA}{A}=0,
\qquad
\rho U\,\mathrm dU=-\mathrm dp,
\qquad
\mathrm dp=a^2\,\mathrm d\rho\ \ (p=C\rho^\gamma).
$$

$$
\frac{\mathrm dA}{A}=(M^2-1)\frac{\mathrm dU}{U},
\qquad
\frac{A}{A^*}=\frac{1}{M}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}.
$$

$$
\dot m=\frac{p_0A^*}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}=0.0404\,\frac{p_0A^*}{\sqrt{T_0}}\ \text{(air, SI)},
\qquad
\frac{p^*}{p_0}=0.5283.
$$

Sonic state ($\gamma=1.4$): $T_0/T^*=1.2$, $\rho_0/\rho^*=1.5774$, $p_0/p^*=1.8929$. The 0.528 is a **throat** pressure: a C-D nozzle chokes at the much higher back pressure $p_{b3}$.

Thrust (rocket, control volume round the engine): $T=\dot m\,u_e+(p_e-p_a)A_e$; at the design point $T=\dot m\,u_e$.

Across a shock $\dot m$ and $T_0$ are unchanged:

$$
\frac{A_2^*}{A_1^*}=\frac{p_{01}}{p_{02}}.
$$

**Shock inside the nozzle.** Solve $\dfrac{p_e}{p_{0e}}\dfrac{A_e}{A_e^*}=\dfrac{p_bA_e}{p_{01}A_t}$ for $M_e$. Then $p_{0e}/p_{01}$ gives $M_s$ (from the normal-shock table), and $A_s=A/A^*(M_s)\,A_t$.

**Critical back pressures**, for a nozzle of exit area ratio $A_e/A_t$:

- $p_{b3}$: the subsonic root of $A_e/A_t$;
- $p_{b6}$: the supersonic root;
- $p_{b5}$: $p_{b6}\times(p_2/p_1)_{NS}(M_e)$.

## Jets and wind tunnels

Lip shock for an over-expanded jet:

$$
M_{n1}=\sqrt{1+\frac{\gamma+1}{2\gamma}\left(\frac{p_\infty}{p_e}-1\right)}.
$$

Lip fan for an under-expanded jet: a turn of $\nu(M_j)-\nu(M_e)$, with $(p/p_0)_{M_j}=p_\infty/p_0$.

Wind-tunnel starting, with the normal shock at $M_{test}$:

$$
\frac{A_{t2}}{A_{t1}}\ge\frac{p_{01}}{p_{02}},
$$

which is 3.046 at $M=3$.

## Method of characteristics

Valid for steady, **planar** (2-D), homentropic, irrotational flow with $M>1$. $\theta$ is the flow **inclination** to $x$. The invariants below are exact only under these assumptions: in an axisymmetric nozzle the compatibility relations gain a $1/r$ term, so $\nu\mp\theta$ are no longer constant along characteristics (the Supplementary Note for MoC, p. 1, treats only the planar case and points elsewhere for the axisymmetric extension). The IFT values are $\gamma=1.4$ only; the CO₂ coursework needs the general-$\gamma$ forms at the end of this section.

Governing pair, and the compatibility conditions:

$$
\frac{\partial\nu}{\partial l}-\tan\mu\frac{\partial\theta}{\partial n}=0,\quad\frac{\partial\theta}{\partial l}-\tan\mu\frac{\partial\nu}{\partial n}=0
\quad\Longrightarrow\quad
R^+=\nu-\theta\ \text{on }C^+\ (\theta+\mu),\qquad R^-=\nu+\theta\ \text{on }C^-\ (\theta-\mu).
$$

Anderson: $K^+=-R^+$, $K^-=R^-$.

Unit process (A below, B above):

$$
\nu_P=\tfrac12(R^+_A+R^-_B),\qquad\theta_P=\tfrac12(R^-_B-R^+_A),\qquad\mu_P=\sin^{-1}(1/M_P),
$$

$$
\alpha_{AP}=\tfrac12[(\theta+\mu)_A+(\theta+\mu)_P],\qquad\alpha_{BP}=\tfrac12[(\theta-\mu)_B+(\theta-\mu)_P],
$$

$$
x_P=\frac{x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}-(y_B-y_A)}{\tan\alpha_{BP}-\tan\alpha_{AP}},\qquad y_P=y_A+(x_P-x_A)\tan\alpha_{AP}.
$$

Boundary conditions:

| Boundary | State | Position |
|---|---|---|
| prescribed top wall (reflecting) | $\nu_W=R^+_A+\theta_W$, reflected $R^-_W=R^+_A+2\theta_W$ | intersect the $C^+$ with the wall |
| designed wall (non-reflecting) | $\theta_W=\theta_A$, $M_W=M_A$ | $\alpha_{AW}=(\theta+\mu)_A$, $\alpha_{BW}=\tfrac12(\theta_B+\theta_W)$ |
| centreline | $\theta_P=0$, $\nu_P=R^-_B$, $R^+_P=R^-_P$ | $x_P=x_B-y_B/\tan\alpha_{BP}$, $\alpha_{BP}=\tfrac12[(\theta-\mu)_B-\mu_P]$ |

A prescribed wall reflects **only if** $\theta_A\neq\theta_W$. If the arriving flow is already parallel to the wall, nothing leaves, whatever the table says (point 3 of the generic example).

Minimum-length nozzle:

$$
\theta_{max}=\frac{\nu(M_e)}{2},\qquad\text{expansion-fan lines: }\nu=\theta,\ R^-=2\theta,\qquad \frac{y_e}{r_a}\to\frac{A_e}{A^*}.
$$

$\theta_{max}$ is the wall's maximum slope; $r_a$ is the throat half-width and $y_e$ the exit half-width.

$M_e=2.4$: $\theta_{max}=18.373^\circ$, $x_e/r_a=8.069$, $y_e/r_a=2.400$ (four lines).

With $n$ lines the net has $n(n+3)/2$ points: 14 for $n=4$, 20 for $n=5$ (the coursework).

General $\gamma$ (the coursework uses CO₂, $\gamma=1.289$; the IFT is $\gamma=1.4$ only):

$$
\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}(M^2-1)}-\tan^{-1}\sqrt{M^2-1},\qquad
\frac{A}{A^*}=\frac{1}{M}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}.
$$

$\mu=\sin^{-1}(1/M)$ is independent of $\gamma$.

Reading the exit Mach number off the maximum slope at a **sharp** expansion corner: $\nu(M_e)=2\theta_{max}$, e.g. $26.74^\circ\Rightarrow M_e=3.20$. A gradual-expansion nozzle has $\theta_{max}\le\nu(M_e)/2$, so the trick fails there. This $\theta_{max}$ is a wall slope, not the oblique-shock limit.

Four-variable rule: any two of $R^+$, $R^-$, $\nu$, $\theta$ fix the other two. Interior points use $R^+$ and $R^-$; walls and the centreline use one invariant and $\theta$.

## Euler equations and compressible aerofoils

4.1–4.6 and Tutorial 2 lectured ([[SESA3029 Tutorial Lecture 2 - Diamond Aerofoil by Ackeret Theory|Tutorial 2]], [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]], [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation|W07b]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]).

2D Euler equations (inviscid, no heat conduction, unit span; perfect gas):

$$
\frac{\partial\mathbf Q}{\partial t}+\frac{\partial\mathbf F}{\partial x}+\frac{\partial\mathbf G}{\partial y}=\mathbf 0,\quad
\mathbf Q=\begin{bmatrix}\rho\\ \rho u\\ \rho v\\ \rho e_t\end{bmatrix},\
\mathbf F=\begin{bmatrix}\rho u\\ \rho u^2+p\\ \rho uv\\ (\rho e_t+p)u\end{bmatrix},\
\mathbf G=\begin{bmatrix}\rho v\\ \rho uv\\ \rho v^2+p\\ (\rho e_t+p)v\end{bmatrix},\quad
e_t=c_vT+\tfrac12(u^2+v^2).
$$

The letters $\mathbf Q,\mathbf F,\mathbf G$ are shorthand. The energy flux is $(\rho e_t+p)u$, not $\rho u(e_t+p)$.

Mach-number effects, 4.2 (perfect gas, $\gamma=1.4$ for numbers). Lift per unit span at a fixed altitude scales with $C_LM_\infty^2$, since $L'=\tfrac12\rho_\infty U_\infty^2cC_L=\tfrac12\gamma p_\infty M_\infty^2cC_L$. On the centre line ahead of the leading edge at $M_\infty>1$ the turning angle is $\theta=0$, so the bow shock there is the normal-shock branch $\beta=90^\circ$ (the other $\theta=0$ solution, $\beta=\mu$, is a Mach wave); e.g. $M_\infty=1.2$: $M_2=0.842$, $\mu=56.4^\circ$. At fixed $\theta$ the weak-branch $\beta$ falls as $M_1$ rises, so the bow shock leans back at higher $M_\infty$. At the trailing edge both streams must leave along one slip line at one pressure (Kutta condition), so each is turned compressively and carries an oblique shock. Sweep: the section sees $M_\infty\cos\Lambda$ (infinite swept wing).

Linearised compressible potential equation and pressure coefficient (steady, isentropic, irrotational, thin body, $u',v'\ll U_\infty$; not near $M_\infty=1$, not hypersonic; $\phi$ is the **perturbation** potential, $u'=\phi_x$, $v'=\phi_y$):

$$
(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0,\qquad C_p=-\frac{2u'}{U_\infty},\qquad a^2=a_\infty^2-(\gamma-1)u'U_\infty .
$$

Pressure coefficient in terms of the free-stream Mach number (exact, perfect gas; a past exam question):

$$
C_p=\frac{p-p_\infty}{\tfrac12\rho_\infty U_\infty^2}=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right),\qquad \tfrac12\rho_\infty U_\infty^2=\tfrac12\gamma p_\infty M_\infty^2 .
$$

Validity of the linear equation: $M_\infty<0.8$ (elliptic, Prandtl–Glauert) or $M_\infty>1.2$ (hyperbolic, Ackeret); 0.9 and 1.1 are also quoted.

Full potential equation (exact for steady, shock-free flow from a uniform stream; elliptic where the local $M<1$, hyperbolic where $M>1$), from [[SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert]]:

$$
\left(\Phi_x^2-a^2\right)\Phi_{xx}+2\Phi_x\Phi_y\Phi_{xy}+\left(\Phi_y^2-a^2\right)\Phi_{yy}=0,\qquad a^2=a_\infty^2-\frac{\gamma-1}{2}\left(\Phi_x^2+\Phi_y^2-U_\infty^2\right).
$$

Order-of-magnitude validity for thickness ratio $\tau$ (boundaries are orders of magnitude, not sharp): subsonic $(\gamma+1)M_\infty^2\tau\ll(1-M_\infty^2)^{3/2}$; supersonic $(\gamma+1)M_\infty^4\tau\ll(M_\infty^2-1)^{3/2}$, best at $M_\infty=2$, failing near 1 and when $M_\infty\tau\sim1$ (hypersonic). Near $M_\infty=1$ keep one term (transonic small-disturbance equation, not lectured): $\left[1-M_\infty^2-(\gamma+1)M_\infty^2\phi_x/U_\infty\right]\phi_{xx}+\phi_{yy}=0$.

Pressure coefficient to second order: $C_p\approx-\dfrac{2u'}{U_\infty}-\left(1-M_\infty^2\right)\dfrac{u'^2}{U_\infty^2}-\dfrac{v'^2}{U_\infty^2}$.

Prandtl–Glauert (subsonic, $M_\infty<0.8$; same aerofoil, $\beta=\sqrt{1-M_\infty^2}$, $\phi_0=\beta\phi$, $y_0=\beta y$):

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}},\qquad C_l=\frac{C_{l0}}{\sqrt{1-M_\infty^2}},\qquad C_m=\frac{C_{m0}}{\sqrt{1-M_\infty^2}}\quad(\text{flat plate: }C_{l0}=2\pi\alpha).
$$

Subscript 0 = incompressible ($M_\infty\to0$), not stagnation. $C_l$ and $C_m$ come from the chordwise integrals ($x$ along the chord from the LE; small $\alpha$, so $L'\approx N'$; nose-up positive), and $\beta$ comes out because $x_0=x$:

$$
C_l\approx\frac1c\int_0^c\left(C_{p,l}-C_{p,u}\right)\mathrm dx,\qquad
C_{m,LE}=-\frac{1}{c^2}\int_0^c\left(C_{p,l}-C_{p,u}\right)x\,\mathrm dx .
$$

No rule for $C_d$: inviscid subcritical drag is zero, and real drag below $M_{crit}$ is viscous (W07b §7).

Kármán–Tsien:

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}+\dfrac{M_\infty^2}{1+\sqrt{1-M_\infty^2}}\dfrac{C_{p0}}{2}} .
$$

Critical Mach number (isentropic flow to the surface; the sonic point taken at $C_{p0,min}$):

$$
\frac{C_{p0,min}}{\sqrt{1-M_{crit}^2}}=C_{p,cr}=\frac{2}{\gamma M_{crit}^2}\left[\left(\frac{1+\frac{\gamma-1}{2}M_{crit}^2}{1+\frac{\gamma-1}{2}}\right)^{\gamma/(\gamma-1)}-1\right].
$$

$C_{p0,min}=-0.4$, $\gamma=1.4$: $M_{crit}=0.747$ (P–G), $0.733$ (K–T). $-1.0$: 0.606, 0.585. $-2.5$ (ES2 Q6): 0.448 (P–G).

Ackeret (supersonic, $1.2<M_\infty\lesssim3$–4; $\lambda=\sqrt{M_\infty^2-1}$; angles in **radians**; $\theta$ from $\vec U_\infty$, + for compression):

$$
u'=-\frac{v'}{\lambda}\ (\text{upper}),\qquad C_p=\frac{2\theta}{\sqrt{M_\infty^2-1}} .
$$

Thin aerofoil $y_{u,l}=\pm h+y_c-\alpha x$, with $\theta_u=y_u'$, $\theta_l=-y_l'$, and $h=y_c=0$ at LE and TE:

$$
C_l=\frac{4\alpha}{\sqrt{M_\infty^2-1}},\qquad
C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\frac1c\int_0^c h'^2\,\mathrm dx+\frac1c\int_0^c y_c'^2\,\mathrm dx\right].
$$

General solution (characteristic coordinates): $\phi=f(x-\lambda y)+g(x+\lambda y)$; only $f$ above the aerofoil and only $g$ below, so $C_p(x,y)=2y_u'(x-\lambda y)/\lambda$ above. Drag polar ([[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]]):

$$
C_d=\frac{\lambda}{4}C_l^2+\frac{4}{\lambda}\left[\overline{h'^2}+\overline{y_c'^2}\right],\qquad \overline{q}=\frac1c\int_0^cq\,\mathrm dx .
$$

Flat plate: $C_d=4\alpha^2/\lambda$, $x_{cp}=c/2$. Diamond (thickest at $c/2$, the minimum-drag symmetric section): $C_d=\frac4\lambda[\alpha^2+(t/c)^2]$; $(L/D)_{max}=c/(2t)$ at $\alpha=t/c$, for any $M_\infty$. Biconvex: thickness term $\tfrac43(t/c)^2$.

$M_\infty=2$, $\alpha=10^\circ$ flat plate: Ackeret $C_l=0.4031$, $C_d=0.0703$; shock-expansion $0.4075$, $0.0719$.

Diamond face by face (Tutorial 2; chord $c$, thickness $t$ at $c/2$, half vertex angle $\phi=\tan^{-1}(t/c)$, faces 1 front and 2 rear, u upper and l lower; $\theta$ from $\vec U_\infty$, valid as written for $0\le\alpha<\phi$):

$$
\theta_{1u}=+(\phi-\alpha),\quad\theta_{1l}=+(\phi+\alpha),\quad\theta_{2u}=-(\phi+\alpha),\quad\theta_{2l}=-(\phi-\alpha),\qquad p=p_\infty\left(1+\tfrac12\gamma M_\infty^2C_p\right),
$$

$$
N'=(p_{1l}-p_{1u}+p_{2l}-p_{2u})\frac c2,\quad A'=(p_{1u}+p_{1l}-p_{2u}-p_{2l})\frac t2,\quad L'=N'\cos\alpha-A'\sin\alpha,\quad D'=A'\cos\alpha+N'\sin\alpha,
$$

$$
M'_{LE}=(p_{1u}-p_{1l})\frac{c^2}{8}+(p_{2u}-p_{2l})\frac{3c^2}{8}\quad(\text{nose-up }+),\qquad \frac{x_{CP}}{c}=-\frac{M'_{LE}}{L'c}.
$$

ES2 Q5 ($t/c=0.05$, $\alpha=2^\circ$, $M_\infty=1.8$, $p_\infty=50$ kPa, $c=1$ m): 52.3, 62.9, 37.1, 47.7 kPa; $L'=10.55$, $D'=1.13$ kN/m; $M'_{LE}=-5.29$ kN m/m; $x_{CP}=0.50c$.

Aerodynamic centre in Ackeret theory (thin, small $\alpha$, $L'\simeq N'$): $C_{m,LE}=-\tfrac12C_l-\dfrac{4}{\lambda c^2}\displaystyle\int_0^cy_c\,\mathrm dx$, so $x_{AC}=c/2$ for every thin aerofoil; symmetric sections also have $x_{CP}=c/2$.

Weak oblique shock, small deflection $\theta$ (radians), perfect gas: $M_{n1}^2-1\simeq\dfrac{(\gamma+1)M_1^2\theta}{2\lambda}$ and $1-\dfrac{p_{02}}{p_{01}}\simeq\dfrac{\gamma(\gamma+1)M_1^6\theta^3}{12\lambda^3}$ (third order, against Ackeret's first-order relative error). $p_{02}/p_{01}$: 0.9986 at $M_{n1}=1.11$, 0.99 at 1.23, 0.979 at 1.3, 0.930 at 1.5.

Wing sweep (simple sweep theory): the section sees $M_\infty\cos\Lambda$, with $\Lambda$ the leading-edge sweep (written $\beta$ in the course).

## Heat transfer (Block 5)

Lectures 5.1–5.10 are written ahead from the slides. Lecture 5.1 is checked against last year's (2025–26) recording, which differs from this year's lecture; the others have no transcripts yet. The official exam sheet gives only the four thermal resistances ([[#What the exam formula sheet gives you]]); everything else in this block has to be known or derived.

## Conduction and thermal resistance (Lectures 5.1–5.2)

5.1–5.2 written ahead from the slides ([[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]]); 5.1 checked against last year's recording.

Heat flux and Fourier's law ($x$ along the heat flow; minus sign: heat flows down the gradient; 3-D form for an isotropic material) ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#2. Fourier's law of heat conduction|W09a §2]]):

$$
\dot q=\frac{\dot Q}{A}\ (\text{W/m}^2),\qquad \dot Q=-kA\frac{\mathrm dT}{\mathrm dx},\qquad \dot{\mathbf q}=-k\nabla T,\qquad k\ \text{in W/(m K)}.
$$

Plane wall (steady, 1-D, constant $k$, no heat generation; linear profile) ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#4. Conduction through a plane wall|W09a §4]]):

$$
T(x)=T_1-(T_1-T_2)\frac xL,\qquad \dot Q=\frac{kA}{L}(T_1-T_2)=\frac{\Delta T}{R_\text{th}},\qquad R_\text{th}=\frac{L}{kA}\ (\text{K/W}).
$$

Electrical analogy ($\Delta T\sim$ voltage, $\dot Q\sim$ current). Series: $R_\text{total}=\sum R_j$, same $\dot Q$ through each, $\Delta T_j=\dot QR_j$. Parallel (no sideways exchange between paths): $1/R_\text{total}=\sum 1/R_j$, same $\Delta T$ across each. Per unit area of plane layers: $R''=RA=L/k$ (m² K/W), $\dot q=\Delta T/R''$ ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#5. The electrical analogy and thermal resistance|W09a §5]]).

Long hollow cylinder, length $L$ (steady, radial, constant $k$; logarithmic profile) ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#6. Radial conduction in a long hollow cylinder|W09a §6]]):

$$
\dot Q_r=\frac{2\pi kL(T_i-T_o)}{\ln(r_o/r_i)},\qquad R_\text{th}=\frac{\ln(r_o/r_i)}{2\pi kL},\qquad T(r)=T_i-(T_i-T_o)\frac{\ln(r/r_i)}{\ln(r_o/r_i)}.
$$

Thin wall $t\ll r_i$: $R_\text{th}\to t/(kA_i)$ (+10 % at $r_o/r_i=1.2$; mean-radius area −0.3 %).

Spherical shell (steady, radial, constant $k$) ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#8. Conduction in a spherical shell|W09a §8]]):

$$
\dot Q_r=\frac{4\pi k(T_i-T_o)}{1/r_i-1/r_o},\qquad R_\text{th}=\frac{1}{4\pi k}\left(\frac1{r_i}-\frac1{r_o}\right)=\frac{r_o-r_i}{4\pi kr_ir_o}.
$$

Newton's law of cooling (forced and free convection; $A_s$ the surface in contact with the fluid, $T_\infty$ far from it) and convection resistance ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#9. Convection heat transfer|W09a §9]]):

$$
\dot Q=hA_s(T_s-T_\infty),\qquad R_\text{th}=\frac{1}{hA_s},\qquad h\ \text{in W/(m}^2\text{ K)}.
$$

Wall or tube between two fluids (series; each convection term uses its own surface: $2\pi r_1L$ inside, $2\pi r_3L$ outside for a tube) ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#10. Walls and tubes with convection on both sides|W09a §10]]):

$$
\text{plane: }R_\text{total}=\frac1{h_1A}+\sum\frac{L_j}{k_jA}+\frac1{h_2A},\qquad
\text{tube: }R_\text{total}=\frac{1}{h_12\pi r_1L}+\sum\frac{\ln(r_{j+1}/r_j)}{2\pi k_jL}+\frac{1}{h_22\pi r_NL},\qquad \dot Q=\frac{T_{\infty,1}-T_{\infty,2}}{R_\text{total}}.
$$

Nusselt number ($k$ of the **fluid**; $L$ a characteristic length): $\text{Nu}=hL/k$. For a fluid layer of thickness $L$, $\text{Nu}=\dot Q_\text{conv}/\dot Q_\text{cond}$, and $\text{Nu}=1$ is pure conduction (no bulk motion) ([[SESA3029 W09a - Heat Conduction and Thermal Resistance#11. The Nusselt number|W09a §11]]).

L5.1 insulated block (3 + 10 + 3 cm; $k=0.048$, 0.69, 0.048; 150 → 10 °C): $R''=1.3949$ m² K/W, $\dot q=100.36$ W/m², $T_2=87.27$ °C, $T_3=72.73$ °C; block B alone 966 W/m². With steel bolts (ES3 Q1): 127.8 W/m².

## Convection (Lecture 5.3)

Newton's law of cooling (defines $h$, W m⁻² K⁻¹; $A_s$ the wetted area; °C differences = K differences), and $h$ from the wall gradient ($k$ of the **fluid**, $y$ into the fluid) ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#2. The thermal boundary layer|W09b §2]]):

$$
\dot Q=hA_s(T_s-T_\infty),\qquad h=\frac{-k\,(\partial T/\partial y)_{y=0}}{T_s-T_\infty}.
$$

Boundary-layer thicknesses: $\delta$ at $u=0.99V$; $\delta_t$ at $T-T_s=0.99(T_\infty-T_s)$. Laminar flat plate, zero pressure gradient, $0.6\lesssim\mathrm{Pr}\lesssim50$: $\delta_{99}=4.91x/\sqrt{\mathrm{Re}_x}$, $\delta_t/\delta\approx\mathrm{Pr}^{-1/3}$.

Dimensionless groups ($L$ the correlation's length: $x$ along a plate, $D$ for a pipe or a cylinder in cross-flow) ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#4. Nusselt and Stanton numbers|W09b §§3–4]]):

$$
\mathrm{Re}=\frac{\rho VL}{\mu},\quad \mathrm{Pr}=\frac{\mu c_p}{k}=\frac{\nu}{\alpha},\quad \mathrm{Nu}=\frac{hL}{k},\quad \mathrm{St}=\frac{h}{\rho Vc_p},\qquad \mathrm{Nu}=\mathrm{St}\,\mathrm{Re}\,\mathrm{Pr}.
$$

Correlations (constant properties; local $\mathrm{Nu}_x$ on plates; laminar plate $\mathrm{Re}_x<3\times10^5$, laminar pipe $\mathrm{Re}_D<2000$) ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#5. Correlations for the Nusselt number|W09b §5]]):

| Flow | Uniform wall heat flux | Uniform wall temperature |
|---|---|---|
| Laminar pipe, fully developed | $\mathrm{Nu}_D=4.364$ | $\mathrm{Nu}_D=3.658$ |
| Laminar plate | $0.453\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ | $0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$ |
| Turbulent pipe ($\mathrm{Re}_D>2000$ on the slides; usually quoted $\gtrsim10^4$) | $0.023\,\mathrm{Re}_D^{4/5}\mathrm{Pr}^n$, $n=0.3$ fluid cooled, 0.4 heated | (same) |
| Turbulent plate, $\mathrm{Re}_x>3\times10^5$ | $0.0308\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ | $0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$ |
| Cylinder in cross-flow, average, $4\times10^4<\mathrm{Re}_D<4\times10^5$ | | $\overline{\mathrm{Nu}}_D=0.027\,\mathrm{Re}_D^{0.805}\mathrm{Pr}^{1/3}$ |

General form $\mathrm{Nu}_x=C\,\mathrm{Re}_x^n\mathrm{Pr}^m$ ("Reynolds analogy" in the course). Averages: $\bar h=\frac1L\int_0^Lh\,\mathrm dx$; laminar plate $\bar h=2h(L)$, $\overline{\mathrm{Nu}}_L=0.664\,\mathrm{Re}_L^{1/2}\mathrm{Pr}^{1/3}$; plate turbulent from the leading edge $\bar h=\tfrac54h(L)$, $\overline{\mathrm{Nu}}_L=0.037\,\mathrm{Re}_L^{4/5}\mathrm{Pr}^{1/3}$.

Reynolds analogy (flat plate, zero pressure gradient, low speed) ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#7. The Reynolds analogy|W09b §7]]): $\mathrm{St}=c_f/2$ for $\mathrm{Pr}=1$; Chilton–Colburn $\mathrm{St}\,\mathrm{Pr}^{2/3}=c_f/2$ for $0.6<\mathrm{Pr}<60$. With $c_{f,x}=0.664\,\mathrm{Re}_x^{-1/2}$ (laminar) it gives $0.332\,\mathrm{Re}_x^{1/2}\mathrm{Pr}^{1/3}$; with $0.0592\,\mathrm{Re}_x^{-1/5}$ (turbulent) $0.0296\,\mathrm{Re}_x^{4/5}\mathrm{Pr}^{1/3}$.

Examples: pipe in cross-flow ($D=0.1$ m, 8 m/s, 110 °C/10 °C): $\mathrm{Re}=4.219\times10^4$, $\mathrm{Nu}=128$, $h=35.94$, 1128.5 W/m. Parallel plates (2 bar, 15 °C, 8 m/s, $L=0.15$, $W=0.1$, 40 °C): $\rho=2.42$, $\mathrm{Re}_L=1.63\times10^5$ laminar, $\bar h=39.74$, 14.9 W per plate.

## Critical radius and fins (Lecture 5.4)

Critical radius of insulation (cylinder, steady, radial, constant $k$ of the insulation and $h$ outside; $\dot Q$ is a **maximum** there) ([[SESA3029 W09c - Critical Thickness of Insulation and Fins#1. Critical thickness of insulation|W09c §1]]):

$$
\dot Q=\frac{2\pi L(T_i-T_\infty)}{\ln(r_o/r_i)/k+1/(r_oh)},\qquad r_{cr}=\frac kh\quad(\text{sphere: }2k/h).
$$

$r_i>r_{cr}$: insulation always reduces the loss; $r_i<r_{cr}$: it raises the loss up to $r_o=r_{cr}$.

Fin of constant cross-section (steady, 1-D along $x$, constant $k$ and $h$; $p$ perimeter, $A_c$ cross-section; $\theta=T-T_\infty$, $\theta_b=T_b-T_\infty$) ([[SESA3029 W09c - Critical Thickness of Insulation and Fins#2. Fins: the energy balance|W09c §§2–5]]):

$$
\frac{\mathrm d^2\theta}{\mathrm dx^2}-a^2\theta=0,\qquad a^2=\frac{hp}{kA_c},\qquad \theta=C_1e^{ax}+C_2e^{-ax}.
$$

| Tip | $\theta/\theta_b$ | $\dot Q_{\mathrm{fin}}$ | $\eta_{\mathrm{fin}}$ ($A_{\mathrm{fin}}=pL$) | $\epsilon_{\mathrm{fin}}$ ($A_b=A_c$) |
|---|---|---|---|---|
| infinitely long ($aL\gtrsim2.65$) | $e^{-ax}$ | $\sqrt{hpkA_c}\,\theta_b$ | $1/(aL)$ | $\sqrt{kp/hA_c}$ |
| insulated tip | $\cosh a(L-x)/\cosh aL$ | $\sqrt{hpkA_c}\,\theta_b\tanh aL$ | $\tanh(aL)/aL$ | $\sqrt{kp/hA_c}\,\tanh aL$ |

$\eta_{\mathrm{fin}}=\dot Q_{\mathrm{fin}}/hA_{\mathrm{fin}}\theta_b$, $\epsilon_{\mathrm{fin}}=\dot Q_{\mathrm{fin}}/hA_b\theta_b=(A_{\mathrm{fin}}/A_b)\eta_{\mathrm{fin}}$ ([[SESA3029 W09c - Critical Thickness of Insulation and Fins#6. Fin efficiency|W09c §§6–7]]). $1/(aL)>1$ for $aL<1$: the long-fin forms apply only to long fins. Pin fin: $p=\pi D$, $A_c=\pi D^2/4$; rectangular: $p=2(w+t)$, $A_c=wt$.

## Thermal radiation (Lectures 5.5–5.6)

Temperatures in kelvin throughout. Surfaces diffuse and opaque ($\tau=0$) unless stated; no absorbing gas between surfaces. Derivations: [[SESA3029 W09d - Thermal Radiation]].

Pathways at a surface (energy conservation): $\rho+\alpha+\tau=1$; opaque: $\alpha=1-\rho$ ([[SESA3029 W09d - Thermal Radiation#2. Reflection, absorption and transmission|W09d §2]]).

Kirchhoff (equilibrium; spectral form always, totals for a grey surface or same-temperature source): $\alpha=\epsilon$ ([[SESA3029 W09d - Thermal Radiation#3. Kirchhoff's law of thermal radiation|§3]]).

Planck (blackbody, $\lambda$ in μm, $T$ in K):

$$
E_{b,\lambda}=\frac{C_1}{\lambda^5\left[\exp(C_2/\lambda T)-1\right]}\ \ [\mathrm{W\,m^{-2}\,\mu m^{-1}}],\qquad C_1=2\pi hc_0^2=3.742\times10^8\ \mathrm{W\,\mu m^4\,m^{-2}},\quad C_2=hc_0/k_B=1.439\times10^4\ \mathrm{\mu m\,K}
$$

([[SESA3029 W09d - Thermal Radiation#4. The blackbody and Planck's law|§4]]). $E=h\nu$, $h=6.626\times10^{-34}$ J s.

Wien (peak of the blackbody spectrum; from $x=5(1-e^{-x})$, $x=4.9651$): $\lambda_{max}T=2897.8$ μm K ([[SESA3029 W09d - Thermal Radiation#5. Wien's displacement law|§5]]). Sun 5800 K → 0.50 μm; 300 K → 9.66 μm.

Stefan–Boltzmann (blackbody, all wavelengths): $E_b=\sigma T^4$, $\sigma=\pi^4C_1/(15C_2^4)=5.67\times10^{-8}$ W m⁻² K⁻⁴; emission from area $A$: $\dot Q=\sigma AT^4$ (emitted, not net) ([[SESA3029 W09d - Thermal Radiation#6. The Stefan–Boltzmann law|§6]]).

Emissivity: $\epsilon=E/E_b$; grey body ($\epsilon_\lambda$ independent of $\lambda$): $E=\epsilon\sigma T^4$ ([[SESA3029 W09d - Thermal Radiation#7. Emissivity and grey bodies|§7]]). Small body in large surroundings: $\dot Q_{net}=\epsilon\sigma A(T_1^4-T_2^4)$.

Solid angle: $\omega=S/r^2$ (sr); sphere $4\pi$, hemisphere $2\pi$; $\mathrm d\omega=\sin\theta\,\mathrm d\theta\,\mathrm d\phi=\mathrm dA\cos\theta/R^2$ ([[SESA3029 W09d - Thermal Radiation#8. Solid angle|§8]]).

Shape factor $F_{ij}$ = fraction of radiation leaving $i$ that reaches $j$ (diffuse surfaces): $F_{12}=\dfrac{1}{A_1}\displaystyle\int_{A_1}\!\int_{A_2}\frac{\cos\theta_1\cos\theta_2}{\pi R^2}\,\mathrm dA_2\,\mathrm dA_1$; reciprocity $A_iF_{ij}=A_jF_{ji}$; summation rule (enclosure, openings as black imaginary surfaces) $\sum_jF_{ij}=1$; $F_{ii}=0$ for flat or convex $i$ ([[SESA3029 W09d - Thermal Radiation#9. The shape factor|§§9–11]]).

Net exchange between two black surfaces (no other reflecting surface): $\dot Q_{1-2}=A_1F_{12}\sigma(T_1^4-T_2^4)$ ([[SESA3029 W09d - Thermal Radiation#10. Reciprocity relation|§10]]).

Standard cases: infinite parallel plates $F_{12}=F_{21}=1$; concentric spheres $F_{12}=1$, $F_{21}=(r_1/r_2)^2$, $F_{22}=1-(r_1/r_2)^2$; element facing coaxial disk of radius $a$ at distance $H$: $a^2/(a^2+H^2)$; small distant sphere seen from a source sphere: $F_{S\to E}=R_E^2/(4d^2)$ ([[SESA3029 W09d - Thermal Radiation#12. Worked example: two concentric spheres|§§12–13]]).

Black, airless planet in steady state ($d$ centre to centre, uniform $T_E$): $T_E=T_S\sqrt{R_S/2d}$; with albedo $a$: $\times(1-a)^{1/4}$. Earth: 278.75 K (5.60 °C); $a=0.3$: 255.0 K (−18.2 °C) ([[SESA3029 W09d - Thermal Radiation#13. Worked example: steady temperature of the Earth|§13]]).

## Numerical methods in conduction (Lecture 5.7)

Constant $k$, $\rho$, $c_p$; uniform grid. Derivations: [[SESA3029 W09e - Numerical Methods in Conduction]].

Heat diffusion equation (2-D/3-D, generation $\dot g$ in W/m³): $\nabla^2T+\dot g/k=(1/\alpha)\,\partial T/\partial t$, thermal diffusivity $\alpha=k/(\rho c_p)$ [m²/s] ([[SESA3029 W09e - Numerical Methods in Conduction#1. The heat conduction equation in 2-D|W09e §§1–2]]). Diffusion time across $L$: $\sim L^2/\alpha$.

Boundary conditions at $x=0$, solid in $x\ge0$: $T(0,t)=T_s$; $-k\,\partial T/\partial x=\dot q_x$; $\partial T/\partial x=0$ (insulated, symmetry); $-k\,\partial T/\partial x=h(T_\infty-T)$; $-k\,\partial T/\partial x=\epsilon\sigma(T_{surr}^4-T_0^4)$ (K) ([[SESA3029 W09e - Numerical Methods in Conduction#3. Boundary conditions|§3]]).

Differences (Taylor series): $T'_i=(T_{i+1}-T_i)/\Delta x+\mathcal O(\Delta x)$; $T''_i=(T_{i+1}-2T_i+T_{i-1})/\Delta x^2+\mathcal O(\Delta x^2)$ (leading error $-\Delta x^2T''''/12$). Error $\sim\Delta x^p$: doubling the points divides the error by $2^p$. Richardson extrapolation (grid refinement ratio $r$, spacings $r^2h,rh,h$): observed order $p=\ln[(T_{r^2h}-T_{rh})/(T_{rh}-T_h)]/\ln r$, extrapolated value $T_{\rm exact}\approx T_h+(T_h-T_{rh})/(r^p-1)$ ([[SESA3029 W09e - Numerical Methods in Conduction#7. Order of accuracy|§7]]).

Steady interior nodes: 1-D planar $T_i=(T_{i+1}+T_{i-1})/2$; 1-D radial cylindrical ($r_i=i\,\Delta r$) $T_i=[(i-\tfrac12)T_{i-1}+(i+\tfrac12)T_{i+1}]/(2i)$; 2-D non-square grid ($s=(\Delta y/\Delta x)^2$) $T_P=[s(T_E+T_W)+T_N+T_S]/[2(1+s)]+\dot g\Delta y^2/[2k(1+s)]$, reducing for a square grid ($\Delta x=\Delta y$) to $T_P=\tfrac14(T_E+T_W+T_N+T_S)+\dot g\Delta x^2/(4k)$ ([[SESA3029 W09e - Numerical Methods in Conduction#4. Discretising the heat equation|§4]], [[SESA3029 W09e - Numerical Methods in Conduction#5. Boundary and corner nodes by energy balance|§5]]).

Transient, Fourier number $\mathcal F=\alpha\Delta t/\Delta x^2$ ([[SESA3029 W09e - Numerical Methods in Conduction#9. Transient conduction: explicit and implicit schemes|§9]]):
explicit $T_i^{n+1}=T_i^n+\mathcal F(T_{i+1}^n-2T_i^n+T_{i-1}^n)$; implicit $T_{i+1}^{n+1}-(2+1/\mathcal F)T_i^{n+1}+T_{i-1}^{n+1}=-T_i^n/\mathcal F$ (tridiagonal). Both $\mathcal O(\Delta t,\Delta x^2)$.

Stability (uniform grid, constant $\alpha$, fixed-temperature ends): explicit 1-D $\mathcal F\le\tfrac12$, 2-D square grid $\mathcal F\le\tfrac14$; explicit 1-D convective end node $\mathcal F(1+\mathrm{Bi})\le\tfrac12$, $\mathrm{Bi}=h\Delta x/k$; implicit unconditionally stable. Von Neumann: explicit $G=1-4\mathcal F\sin^2(k\Delta x/2)$, implicit $G=1/[1+4\mathcal F\sin^2(k\Delta x/2)]$ ([[SESA3029 W09e - Numerical Methods in Conduction#10. Stability of the explicit scheme|§10]]).

Boundary nodes by energy balance on the node's control volume (half cell inside the solid; unit depth; flows into P positive): conduction $k\,(\text{face length})(T_{nb}-T_P)/\Delta x$, convection $h\,(\text{exposed length})(T_\infty-T_P)$. Square grid, $\mathrm{Bi}=h\Delta x/k$: plane surface with convection $T_P=(2T_W+T_N+T_S+2\mathrm{Bi}\,T_\infty)/(4+2\mathrm{Bi})$ (insulated: $\mathrm{Bi}=0$); exterior corner, convection on both faces $T_P=(T_W+T_S+2\mathrm{Bi}\,T_\infty)/(2+2\mathrm{Bi})$; internal corner with flux $\dot q$ on both edges $6T_P=2T_N+2T_W+T_E+T_S+2\dot q\Delta x/k$ ([[SESA3029 W09e - Numerical Methods in Conduction#5. Boundary and corner nodes by energy balance|§5]]).

Rod $T_L$ at $x=0$, $T_R$ at $x=L$, initially at $T_L$: $T=T_L+(T_R-T_L)\dfrac xL+\displaystyle\sum_{n\ge1}\frac{2(T_R-T_L)(-1)^n}{n\pi}\sin\frac{n\pi x}{L}\,e^{-\alpha(n\pi/L)^2t}$ ([[SESA3029 W09e - Numerical Methods in Conduction#11. Worked example: 1-D transient conduction|§11]]).

## Heat exchangers (Lectures 5.8–5.10)

5.8–5.10, written ahead from the slides ([[SESA3029 W09f - Heat Exchangers|W09f]]). Steady flow; constant $\dot m$, $c_p$ and $U$; outer surface insulated; axial conduction negligible. None of this is on the official exam sheet (it gives only the thermal resistances), so memorise or derive it.

Overall heat transfer coefficient (resistances in series; $U$ always tied to an area, [[SESA3029 W09f - Heat Exchangers#1. The overall heat transfer coefficient|W09f §1]]):

$$
\frac{1}{UA_s}=\frac{1}{U_iA_i}=\frac{1}{U_oA_o}=\frac{1}{h_iA_i}+\frac{\ln(r_o/r_i)}{2\pi kL}+\frac{1}{h_oA_o},
\qquad
\frac1U\approx\frac1{h_i}+\frac1{h_o}\quad(\text{thin wall, }A_i\approx A_o=A_s).
$$

Energy balance and heat capacity rate (W K⁻¹; condensing or boiling stream: $C\to\infty$, [[SESA3029 W09f - Heat Exchangers#3. Energy balance and the heat capacity rate|W09f §3]]):

$$
\dot Q=C_h\left(T_{h,\rm in}-T_{h,\rm out}\right)=C_c\left(T_{c,\rm out}-T_{c,\rm in}\right),\qquad C=\dot mc_p .
$$

LMTD method (parallel and counter flow, same formula; [[SESA3029 W09f - Heat Exchangers#4. The log mean temperature difference method|W09f §4]]):

$$
\dot Q=UA_s\Delta T_{\rm lm},\qquad \Delta T_{\rm lm}=\frac{\Delta T_1-\Delta T_2}{\ln(\Delta T_1/\Delta T_2)}\quad(\to\Delta T\text{ when }\Delta T_1=\Delta T_2),
$$

| | $\Delta T_1$ | $\Delta T_2$ |
|---|---|---|
| parallel flow | $T_{h,\rm in}-T_{c,\rm in}$ | $T_{h,\rm out}-T_{c,\rm out}$ |
| counter flow | $T_{h,\rm in}-T_{c,\rm out}$ | $T_{h,\rm out}-T_{c,\rm in}$ |

Same four terminal temperatures (both streams changing temperature): $\Delta T_{\rm lm,CF}>\Delta T_{\rm lm,PF}$, so counter flow needs less area; equal when one stream is at constant temperature.

Effectiveness–NTU ($c=C_{\min}/C_{\max}$, written $C_r$ in textbooks and ES3; [[SESA3029 W09f - Heat Exchangers#5. Effectiveness and the number of heat transfer units|W09f §5]]):

$$
\epsilon=\frac{\dot Q}{\dot Q_{\max}},\quad \dot Q_{\max}=C_{\min}\left(T_{h,\rm in}-T_{c,\rm in}\right),\quad \mathrm{NTU}=\frac{UA_s}{C_{\min}},
$$

$$
\epsilon_{\text{parallel-flow}}=\frac{1-\exp\left[-\mathrm{NTU}(1+c)\right]}{1+c},\qquad
\epsilon_{\text{counter-flow}}=\frac{1-\exp\left[-\mathrm{NTU}(1-c)\right]}{1-c\exp\left[-\mathrm{NTU}(1-c)\right]} .
$$

Limits ([[SESA3029 W09f - Heat Exchangers#5.5 Limiting cases|W09f §5.5]]): $c=0$ (condenser/boiler, **any** arrangement) $\epsilon=1-e^{-\mathrm{NTU}}$, $\mathrm{NTU}=-\ln(1-\epsilon)$; counter flow $c=1$ (formula $0/0$, $\Delta T$ constant) $\epsilon=\mathrm{NTU}/(1+\mathrm{NTU})$; parallel flow $c=1$: $\epsilon=\tfrac12(1-e^{-2\mathrm{NTU}})\le\tfrac12$; $\mathrm{NTU}\to\infty$: PF $\to1/(1+c)$, CF $\to1$; $\mathrm{NTU}\to0$: $\epsilon\approx\mathrm{NTU}$.

Inversions for sizing ([[SESA3029 W09f - Heat Exchangers#6. Choosing the method|W09f §6]]): $\mathrm{NTU}_{\rm PF}=-\ln[1-\epsilon(1+c)]/(1+c)$; $\mathrm{NTU}_{\rm CF}=\dfrac{1}{c-1}\ln\dfrac{\epsilon-1}{\epsilon c-1}$ ($c\ne1$).

Annulus hydraulic diameter: $D_h=4A_c/P=D_o-D_i$. Tube length: $A_s=N\pi DL'$, pass length $L'/n_{\rm passes}$.

Course examples: counter flow $C_c=1500$, $C_h=3000$ W K⁻¹, $U=162.96$ W m⁻² K⁻¹: $A_s=10.06$ m² ($\Delta T_{\rm lm}=73.19$ K) and back again by NTU ($\mathrm{NTU}=1.093$, $c=0.5$, $\epsilon=0.5926$, outlets 110 and 95 °C). Oil–water concentric tube: $U=38.25$, $\Delta T_{\rm lm}=43.2$ K, $L=65.67$ m. Condenser (30 000 tubes, 2 passes, $\dot Q=2$ GW): $T_{c,o}=35.95$ °C, $\epsilon=0.5318$, $\mathrm{NTU}=0.7588$, $L=4.512$ m per pass.

## What the exam formula sheet gives you

The official `Aerothermodynamics Formula Sheet.pdf` (3 pages, filed on 6 Oct) is provided in the exam together with the isentropic-flow table (`IFT.pdf`, with $\nu$ and $A/A^*$ columns), the normal-shock table (`NST.pdf`, including $p_{02}/p_1$) and the oblique-shock chart (`OSC.pdf`, $M_1=1.5$–$3$ only). Knowing what is **not** on it tells you what to memorise or be able to derive.

| Given on the official sheet | Not given: memorise or derive |
|---|---|
| $p=\rho RT$, $a=\sqrt{\gamma RT}$ | $p_0/p$ and $\rho_0/\rho$ in terms of $M$ (combine $T_0/T$ with the isentropic line) |
| adiabatic $T_0/T=1+\tfrac{\gamma-1}{2}M^2$ | $T_{01}=T_{02}$ across a shock; $p_{02}/p_{01}$ (or use the NST) |
| isentropic $p_2/p_1=(\rho_2/\rho_1)^\gamma=(T_2/T_1)^{\gamma/(\gamma-1)}$ | Rayleigh Pitot formula (use the NST $p_{02}/p_1$ column) |
| shock jumps $\rho_2/\rho_1$, $p_2/p_1$, $T_2/T_1$, $M_{n2}^2$ | $M_{n1}=M_1\sin\beta$, $M_2=M_{n2}/\sin(\beta-\theta)$ |
| θ–β–M equation | $\theta_{max}$ (read from the chart) |
| $\mu=\sin^{-1}(1/M)$ | expansion-fan angle $\phi=\mu_1-\mu_2+\theta$ |
| Prandtl–Meyer $\nu(M)$ | $\nu(M_2)=\nu(M_1)+\theta$ |
| Riemann invariants $R^\pm=\nu\mp\theta$; MoC intersection formulae $\alpha_{AP}$, $\alpha_{BP}$, $x_P$, $y_P$ | MoC procedure (Block 3) |
| $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$; $C_p=-2u'/U_\infty$; Prandtl–Glauert; Ackeret $C_p=2\theta/\sqrt{M_\infty^2-1}$ | $C_l$, $C_d$ for thin aerofoils (Block 4) |
| thermal resistances: plane $L/kA$, cylinder $\ln(r_o/r_i)/2\pi kL$, sphere $\tfrac{1}{4\pi k}(1/r_i-1/r_o)$, convection $1/hA$ | Nusselt correlations are given in the question if needed. Not given: $r_{cr}=k/h$ and the fin results; $E_b=\sigma T^4$, Wien, the shape-factor rules; finite-difference node equations and $\mathcal F\le\tfrac12$; $1/U=1/h_i+1/h_o$, the LMTD, $\epsilon$–NTU and $\dot Q_{\max}=C_{\min}\Delta T_{\max}$ (Block 5) |

**Not on the sheet at all:** $A/A^*(M)$ (use the IFT column), choked mass flow $\dot m=\dfrac{p_0A^*}{\sqrt{T_0}}\sqrt{\dfrac{\gamma}{R}}\left(\dfrac{2}{\gamma+1}\right)^{(\gamma+1)/(2(\gamma-1))}$, the entropy jump, and the over-expanded lip-shock relation above.

## Related

- [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]
- [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]
- [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]
- [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- [[SESA3029 W05a - Method of Characteristics]]
- [[SESA3029 W05b - Minimum-Length Nozzle Design]]
- [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]
- [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]
- [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]
- [[SESA3029 W09a - Heat Conduction and Thermal Resistance]]
- [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]
- [[SESA3029 W09c - Critical Thickness of Insulation and Fins]]
- [[SESA3029 W09d - Thermal Radiation]]
- [[SESA3029 W09e - Numerical Methods in Conduction]]
- [[SESA3029 W09f - Heat Exchangers]]
- [[SESA3029 Aerothermodynamics Hub]]

