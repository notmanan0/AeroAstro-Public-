---
title: "SESA3029 Formula Sheet"
module: "SESA3029 Aerothermodynamics"
type: formula
aliases: ["SESA3029 formulae", "Aerothermodynamics formula sheet"]
tags: [sesa3029, formula, exam-prep]
status: in-progress
coverage: "Week 1, Lectures 2.1–2.7"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures"]
---

# SESA3029 Formula Sheet

Current coverage: **Week 1 and Lectures 2.1–2.7** (2.1–2.4 lectured; 2.5–2.7 from the slides). This sheet will expand with the module. For what the **official** exam sheet provides, see [[#What the exam formula sheet gives you]].

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

$$
C_{m,x}=C_{m,LE}+\frac{x}{c}C_l,\qquad
\frac{x_{CP}}{c}=-\frac{C_{m,LE}}{C_l},\qquad
\frac{x_{AC}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_l}.
$$

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

## Mach angle

$$
\mu=\sin^{-1}\!\left(\frac1M\right).
$$

## Shock chains, reflections and slip lines (Lecture 2.3)

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

## Prandtl–Meyer expansion (Lecture 2.4)

$$
\mathrm d\nu=\sqrt{M^2-1}\,\frac{\mathrm dU}{U},
\qquad
\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}(M^2-1)}-\tan^{-1}\sqrt{M^2-1}.
$$

$$
\nu(M_2)=\nu(M_1)+\theta,
\qquad
\phi_{fan}=\mu_1-\mu_2+\theta,
\qquad
\nu_{max}=130.45^\circ.
$$

Across a fan, $p_0$ and $T_0$ are constant: use the isentropic ratios.

## Shock-expansion method (Lecture 2.5)

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

Linear (Ackeret) limit, previewing Weeks 7–8:

$$
C_p=\frac{2\theta}{\sqrt{M^2-1}},
\qquad
C_l=\frac{4\alpha}{\sqrt{M^2-1}},
\qquad
C_d=\frac{4(\alpha^2+\varepsilon^2)}{\sqrt{M^2-1}}\ \ (\text{diamond}).
$$

## Quasi-1D nozzle flow (Lecture 2.6)

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

Across a shock $\dot m$ and $T_0$ are unchanged:

$$
\frac{A_2^*}{A_1^*}=\frac{p_{01}}{p_{02}}.
$$

**Shock inside the nozzle.** Solve $\dfrac{p_e}{p_{0e}}\dfrac{A_e}{A_e^*}=\dfrac{p_bA_e}{p_{01}A_t}$ for $M_e$. Then $p_{0e}/p_{01}$ gives $M_s$ (from the normal-shock table), and $A_s=A/A^*(M_s)\,A_t$.

**Critical back pressures**, for a nozzle of exit area ratio $A_e/A_t$:

- $p_{b3}$: the subsonic root of $A_e/A_t$;
- $p_{b6}$: the supersonic root;
- $p_{b5}$: $p_{b6}\times(p_2/p_1)_{NS}(M_e)$.

## Jets and wind tunnels (Lecture 2.7)

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
| thermal resistances: plane $L/kA$, cylinder $\ln(r_o/r_i)/2\pi kL$, sphere $\tfrac{1}{4\pi k}(1/r_i-1/r_o)$, convection $1/hA$ | Nusselt correlations are given in the question if needed |

**Not on the sheet at all:** $A/A^*(M)$ (use the IFT column), choked mass flow $\dot m=\dfrac{p_0A^*}{\sqrt{T_0}}\sqrt{\dfrac{\gamma}{R}}\left(\dfrac{2}{\gamma+1}\right)^{(\gamma+1)/(2(\gamma-1))}$, the entropy jump, and the over-expanded lip-shock relation above.

## Related

- [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]
- [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]
- [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]
- [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- [[SESA3029 Aerothermodynamics Hub]]

