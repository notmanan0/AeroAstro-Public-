---
title: "SESA2025 Past Paper 2020-21 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, neutral-point, flight-test, canard, downwash, state-space, eigenvalues, short-period, phugoid, lateral-modes, roll-subsidence, dutch-roll, spiral]
paper: "2020-21"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA2022 T5 - Finite Wing Theory]]", "[[SESA3047 5.2 - Longitudinal State-Space Model]]", "[[SESA3047 5.4 - Time-Domain Solution and Stability]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-202021-02-SESA2025.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# SESA2025 Past Paper 2020-21 - Solutions

> [!abstract] Paper info
> 2020-21 Semester 2 final assessment, run online as a 24-hour open-book paper (about 4 h of work), four questions worth 30 + 20 + 25 + 25 = 100 marks, with word limits on the discursive parts and no formula sheet. Each student downloaded an individual data set from Blackboard (Table 1 for Q1, Table 2 for Q3 and Q4), and those tables are not in the filed PDF. Q1(i) and Q2 need no data set and are solved exactly. Q1(ii) is solved in general and illustrated with stated values. Q3 and Q4 are worked with the two data sets of the SESA3047 Chapter 6 lecture notes as stand-ins: the F-4C Phantom of Table 6.1 for the longitudinal model and the Navion of Table 6.2 for the lateral model, so every number can be checked against [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]] and the Chapter 6 PDF. All numbers were computed in Python with $g=9.81$ m/s².

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 30 | Stick-fixed neutral point from two-speed, two-CG trim flights; tail lift-curve slope from $h_n$ | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#5. Neutral point from flight tests\|SESA2022 T6 §5]], [[Neutral Point and Static Margin]], [[SESA1015 M11 - Longitudinal Trim and Static Stability\|SESA1015 M11]] |
| 2 | 20 | Canard and wing lift-curve slopes with canard downwash inboard and upwash outboard | [[SESA2022 T5 - Finite Wing Theory\|SESA2022 T5]], [[Downwash and Induced Drag]], [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability\|T6]] |
| 3 | 25 | Longitudinal state space: assumptions, dimensional derivatives, eigenvalues, SPO and phugoid, effect of halving $H_s$ | [[SESA3047 5.2 - Longitudinal State-Space Model\|5.2]], [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation\|6.1]], [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives\|SESA2027 A2]]; the phugoid approximation is §6.6, lectured Mon 16 Nov ([[SESA3047 6.2 - Phugoid Approximation\|6.2]]) |
| 4 | 25 | Lateral state space: dimensional derivatives, eigenvalues, roll subsidence, fin-area reduction | Not yet lectured: lateral modes are Chapter 6 §§6.7–6.10 ([[Lecture Notes - Chapter 6.pdf]]), lectured from Thu 19 Nov; qualitative background in [[Lateral and Directional Stability]] |

---

## Q1. Neutral point from flight tests and the tail lift-curve slope (30 marks)

> (i) A new aeroplane is flight-tested to find the stick-fixed neutral point $h_n$. Flight 1: $W=1100$ N, $h=0.3$, trimmed at $V=25$ m/s with $\eta=4^\circ$ and at $V=40$ m/s with $\eta=6^\circ$. Flight 2: a 150 N payload is added and $h=0.2$; trimmed at the same two speeds with $\eta=5^\circ$ and $8^\circ$. Estimate $h_n$. [15]
> (ii) Using $h_n$ and $C_{L_\alpha}=a_0(\pi Ae)/(\pi Ae+a_0)$, estimate $C_{L_{T,\alpha}}$ (use $h_n=0.4$ if unsure). [15]

### (i) Neutral point from the trim curves [15 marks]

The method is the extrapolation of [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#5. Neutral point from flight tests|SESA2022 T6 §5]]. Differencing the stick-fixed trim equations between two speeds at a fixed CG gives

$$
h_n-h=-Kk\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}},
$$

so the slope of the trim curve is linear in $h$ and vanishes at $h=h_n$:

$$
\frac{d\eta}{dC_{L^*}}=\frac{h-h_n}{Kk\,a_2/a_1}.
$$

$K$, $k$ and $a_2/a_1$ are properties of the airframe and are the same in both flights. The assumptions are level flight ($C_{L^*}=C_W$), the same density and wing area in both flights, a linear trim curve between the two speeds, and no change of $K$, $k$ or $a_2/a_1$ with payload.

In level flight

$$
C_{L^*}=\frac{W}{\tfrac12\rho V^2S}=\frac{2}{\rho S}\,\frac{W}{V^2},
$$

and the weight is different in the two flights ($1100$ N, then $1250$ N), so the slope must be taken against $C_{L^*}$, not against $V$. Between 25 and 40 m/s,

$$
\frac{1}{40^2}-\frac{1}{25^2}=0.000625-0.0016=-0.000975\ \text{s}^2/\text{m}^2.
$$

Flight 1 ($h=0.3$, $W=1100$ N):

$$
\Delta C_{L^*}=\frac{2}{\rho S}\times1100\times(-0.000975)=-\frac{2}{\rho S}\times1.0725,
$$

$$
\frac{d\eta}{dC_{L^*}}\bigg|_{h=0.3}=\frac{6^\circ-4^\circ}{-\frac{2}{\rho S}\times1.0725}=-1.8648\,\frac{\rho S}{2}\ \text{deg}.
$$

Flight 2 ($h=0.2$, $W=1250$ N):

$$
\Delta C_{L^*}=\frac{2}{\rho S}\times1250\times(-0.000975)=-\frac{2}{\rho S}\times1.21875,
$$

$$
\frac{d\eta}{dC_{L^*}}\bigg|_{h=0.2}=\frac{8^\circ-5^\circ}{-\frac{2}{\rho S}\times1.21875}=-2.4615\,\frac{\rho S}{2}\ \text{deg}.
$$

Both slopes are negative (more up-elevator to fly slower), so the aircraft is statically stable at both CG positions. The unknown factor $\rho S/2$ is common to both and cancels in the ratio:

$$
\frac{0.3-h_n}{0.2-h_n}=\frac{1.8648}{2.4615}=\frac{2/1100}{3/1250}=\frac{25}{33}.
$$

Cross-multiply:

$$
33(0.3-h_n)=25(0.2-h_n).
$$

Expand:

$$
9.9-33h_n=5-25h_n.
$$

Collect:

$$
8h_n=4.9,
$$

$$
\boxed{h_n=0.6125}.
$$

![[amc_pp_202021_q1_eta_slope_vs_h.png|900]]

> [!warning] The weight changed between the flights
> Using $\Delta\eta$ alone, as if $C_{L^*}$ were the same function of $V$ in both flights, gives a slope ratio of $2/3$ and $h_n=0.5$. The 150 N payload raises $C_{L^*}$ at each speed by 13.6 %, which steepens the flight-2 curve on its own account, and has to be divided out.

> [!check] Static margins
> $H_s=h_n-h$ is $0.3125$ in flight 1 and $0.4125$ in flight 2, in the ratio $0.758=25/33$, the same as the two slopes, as the linear relation requires.

### (ii) Tail lift-curve slope from the neutral point [15 marks]

The stick-fixed neutral point is ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Neutral point and static margin|T6 §3]])

$$
h_n=h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad C_{L^*_\alpha}=C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S},\qquad K=\frac{S_Tl}{Sc}.
$$

$C_{L_{T,\alpha}}$ appears in the denominator as well, so solve for it. Multiply out:

$$
(h_n-h_0)\left(C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}\right)=K\,C_{L_{T,\alpha}}.
$$

Collect the $C_{L_{T,\alpha}}$ terms on the right:

$$
(h_n-h_0)\,C_{L_\alpha}=C_{L_{T,\alpha}}\left[K-(h_n-h_0)\frac{S_T}{S}\right].
$$

Divide:

$$
\boxed{C_{L_{T,\alpha}}=\frac{(h_n-h_0)\,C_{L_\alpha}}{K-(h_n-h_0)\,S_T/S}},\qquad C_{L_\alpha}=a_0\frac{\pi Ae}{\pi Ae+a_0}.
$$

The data needed ($h_0$, $A$, $e$, $a_0$, $S$, $S_T$, $l$, $c$) were in the individual Table 1 and are not in the filed paper. With illustrative values $a_0=2\pi$ rad⁻¹, $A=8$, $e=0.9$, $h_0=0.25$, $K=0.6$ and $S_T/S=0.2$:

$$
C_{L_\alpha}=2\pi\times\frac{\pi\times8\times0.9}{\pi\times8\times0.9+2\pi}=2\pi\times\frac{7.2}{9.2}=4.917\ \text{rad}^{-1},
$$

$$
C_{L_{T,\alpha}}=\frac{(0.6125-0.25)\times4.917}{0.6-(0.6125-0.25)\times0.2}=\frac{1.7825}{0.5275}=3.379\ \text{rad}^{-1}.
$$

With the fallback $h_n=0.4$ the same values give $0.7376/0.57=1.294$ rad⁻¹. Substituting either result back into $h_0+KC_{L_{T,\alpha}}/C_{L^*_\alpha}$ returns the $h_n$ used, which checks the algebra. If the tail contribution to $C_{L^*_\alpha}$ is neglected (the form a quick answer often uses), $C_{L_{T,\alpha}}\approx(h_n-h_0)C_{L_\alpha}/K=2.971$ rad⁻¹, 12 % low.

---

## Q2. Canard lift-curve slopes with downwash and upwash on the wing (20 marks)

> A canard aeroplane with a rectangular wing (Figure 1 of the paper) uses tailplane notation for the canard. The canard's trailing vortices induce downwash $v_T$ on the inboard wing ($|y|<b_T/2$) and upwash $\tfrac12v_T$ outboard; the canard is not influenced by the wing. $a_0=a_1=2\pi$, elevator only. With
> $L=2\pi\rho V^2c\left[\int_0^{b_T/2}\alpha_{\text{eff}}^{(\text{in})}dy+\int_{b_T/2}^{b/2}\alpha_{\text{eff}}^{(\text{out})}dy\right]$,
> (i) derive $C_{L_{T,\alpha}}$ and $C_{L_\alpha}$; [15]
> (ii) find the limiting $b_T/b$ for which $C_{L_\alpha}$ is not adversely affected by the canard. [5]

The paper's Figure 1 gives the effective incidences: canard $\alpha_T=\alpha+\alpha_s$ and $\alpha_{T\text{eff}}=\alpha_T-\epsilon_T$; wing inboard $\alpha^{(\text{in})}_{\text{eff}}=\alpha-\epsilon-\epsilon_T$; wing outboard $\alpha^{(\text{out})}_{\text{eff}}=\alpha-\epsilon+\tfrac12\epsilon_T$. Here $\epsilon=C_L/\pi Ae$ is the wing's own induced angle and $\epsilon_T=C_{L_T}/\pi A_Te_T$ the canard's, both from lifting-line theory ([[SESA2022 T5 - Finite Wing Theory|T5]]), with $\alpha$ measured from the zero-lift line in radians.

### (i) Lift-curve slopes of the canard and the wing [15 marks]

#### Canard

The canard flies in undisturbed air, so only its own trailing vortices reduce its incidence. With $\eta$ the canard elevator angle,

$$
C_{L_T}=a_1\alpha_{T\text{eff}}+a_2\eta=a_1\left(\alpha+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}\right)+a_2\eta.
$$

Move the $C_{L_T}$ term to the left:

$$
C_{L_T}\left(1+\frac{a_1}{\pi A_Te_T}\right)=a_1\left(\alpha+\alpha_s\right)+a_2\eta.
$$

Divide and differentiate at fixed $\eta$ and $\alpha_s$:

$$
\boxed{C_{L_{T,\alpha}}=\frac{a_1\,\pi A_Te_T}{\pi A_Te_T+a_1}=\frac{2\pi A_Te_T}{A_Te_T+2}}\quad(a_1=2\pi).
$$

This is the finite-wing slope $k$ of the canard on its own, with no $(1-\epsilon_\alpha)$ factor, because no downwash from the wing reaches it. The canard's induced angle then varies with $\alpha$ at the rate

$$
\epsilon_{T,\alpha}=\frac{d\epsilon_T}{d\alpha}=\frac{C_{L_{T,\alpha}}}{\pi A_Te_T}=\frac{a_1}{\pi A_Te_T+a_1}=\frac{2}{A_Te_T+2}.
$$

#### Wing

Both integrands are uniform in $y$ over their ranges, so the integrals are lengths times constants:

$$
L=2\pi\rho V^2c\left[\left(\alpha-\epsilon-\epsilon_T\right)\frac{b_T}{2}+\left(\alpha-\epsilon+\tfrac12\epsilon_T\right)\frac{b-b_T}{2}\right].
$$

Collect the $\alpha-\epsilon$ terms, whose lengths add to $b/2$:

$$
L=2\pi\rho V^2c\left[\left(\alpha-\epsilon\right)\frac b2-\epsilon_T\frac{b_T}{2}+\tfrac12\epsilon_T\frac{b-b_T}{2}\right].
$$

Take out $b/2$ and write $r=b_T/b$:

$$
L=2\pi\rho V^2c\,\frac b2\left[\alpha-\epsilon-r\,\epsilon_T+\tfrac12(1-r)\,\epsilon_T\right].
$$

Combine the canard terms, $-r+\tfrac12-\tfrac12r=\tfrac12(1-3r)$:

$$
L=\pi\rho V^2cb\left[\alpha-\epsilon+\tfrac12(1-3r)\,\epsilon_T\right].
$$

Divide by $\tfrac12\rho V^2S$ with $S=bc$:

$$
C_L=2\pi\left[\alpha-\epsilon+\tfrac12(1-3r)\,\epsilon_T\right].
$$

Substitute $\epsilon=C_L/\pi Ae$ and move it to the left:

$$
C_L\left(1+\frac{2\pi}{\pi Ae}\right)=2\pi\left[\alpha+\tfrac12(1-3r)\,\epsilon_T\right].
$$

Divide:

$$
C_L=\frac{2\pi\,\pi Ae}{\pi Ae+2\pi}\left[\alpha+\tfrac12(1-3r)\,\epsilon_T\right].
$$

Differentiate with respect to $\alpha$, using $d\epsilon_T/d\alpha=\epsilon_{T,\alpha}$:

$$
C_{L_\alpha}=\frac{a_0\,\pi Ae}{\pi Ae+a_0}\left[1+\tfrac12\left(1-3\frac{b_T}{b}\right)\epsilon_{T,\alpha}\right].
$$

With $a_0=a_1=2\pi$, $\tfrac12\epsilon_{T,\alpha}=1/(A_Te_T+2)$, so

$$
\boxed{C_{L_\alpha}=\frac{2\pi Ae}{Ae+2}\left[1+\frac{1-3\,b_T/b}{A_Te_T+2}\right]}.
$$

The first factor is the isolated finite wing; the bracket is the canard's effect. The inboard part of the wing loses the full canard downwash $\epsilon_T$ over a fraction $b_T/b$ of the span, and the outboard part gains half of it over the remaining $1-b_T/b$.

> [!check] Numerical check
> With $A=8$, $e=0.9$, $A_T=5$, $e_T=0.9$ the isolated wing has $C_{L_\alpha}=4.917$ rad⁻¹. The formula gives $5.220$ at $b_T/b=0.2$, $4.917$ at $1/3$ and $4.539$ at $0.5$. Integrating $2\pi\alpha_{\text{eff}}(y)$ numerically over the half-span at $\alpha=0.05$ rad and $b_T/b=0.5$ gives $C_L=0.226952$, against $0.226951$ from the closed form.

### (ii) Span ratio at which the wing is not penalised [5 marks]

The canard leaves the wing's slope unchanged or raises it when the bracket is at least 1, that is when

$$
1-3\frac{b_T}{b}\ge0,
$$

$$
\boxed{\frac{b_T}{b}\le\frac13}.
$$

At $b_T/b=1/3$ the downwash lost inboard ($\epsilon_T$ over one third of the span) exactly balances the upwash gained outboard ($\tfrac12\epsilon_T$ over two thirds). A canard with a smaller span puts more of the wing in its upwash and increases $C_{L_\alpha}$; a wider canard reduces it. The result holds only for the idealised step distribution of Figure 1, in which the canard downwash at the wing equals that at the canard and the upwash outboard is uniform.

---

## Q3. Longitudinal state space, eigenvalues and the effect of the static margin (25 marks)

> The longitudinal model is
> $\begin{bmatrix}m&0&0&0\\0&m&0&0\\0&0&I_{yy}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot u\\\dot w\\\dot q\\\dot\theta\end{bmatrix}=\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\\\mathring Z_u&\mathring Z_w&mU_\infty&-mg\\\mathring M_u&\mathring M_w&\mathring M_q&0\\0&0&1&0\end{bmatrix}\begin{bmatrix}u\\w\\q\\\theta\end{bmatrix}$.
> (i) List the four assumptions that reduce the full equation to this form and their implications [4, max 80 words]. (ii) Calculate the seven dimensional derivatives from Table 2, with units, to 1 d.p. [7] (iii) Calculate the eigenvalues to 3 d.p., with code. [2] (iv) SPO: identify the eigenvalue, stability, angular frequency, half-life or doubling time, $\omega_n$ and $\zeta$. [3] (v) The same for the phugoid. [3] (vi) $H_s$ is halved: updated eigenvalues and discussion using the simplified modes [6, max 200 words].

Table 2 is replaced by the F-4C data of SESA3047 Table 6.1: $U_\infty=178$ m/s, $\rho=0.3809$ kg/m³, $S=49.239$ m², $c=4.889$ m, $m=17642$ kg, $I_{yy}=165669$ kg m², level trim, and the seven dimensionless derivatives in the table below.

### (i) The four assumptions [4 marks]

Starting from the full equation of [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives|SESA2027 A2]] (mass matrix with $m-\mathring Z_{\dot w}$ and $-\mathring M_{\dot w}$, and $\mathring Z_q+mU_\infty$ in $\mathbf A'$), a model answer within 80 words:

- $\mathring Z_{\dot w}\ll m$: added-mass effect ignored, so the $\dot w$ coefficient is $m$.
- $\mathring M_{\dot w}=0$: downwash lag at the tail ignored, so $\mathbf M$ is diagonal and the SPO loses that damping contribution.
- $\mathring Z_q\ll mU_\infty$: lift from pitch rate is negligible against the centripetal term.
- Level trim, $\gamma_0=0$: $-mg\cos\gamma_0\to-mg$ in the $X$ row and $-mg\sin\gamma_0\to0$ in the $Z$ row.

The last assumption makes the $(2,4)$ entry zero, not $-mg$ as printed (see [[#Paper slips and ambiguities]]).

### (ii) The seven dimensional derivatives [7 marks]

Force derivatives are scaled by $\tfrac12\rho U_\infty^2S$, moment derivatives by $\tfrac12\rho U_\infty^2Sc$, and each is divided by the reference for its variable, $U_\infty$ for $u$ and $w$ and $U_\infty/c$ for $q$ ([[SESA3047 5.2 - Longitudinal State-Space Model#6. Dimensional and dimensionless derivatives (appendix, 5.51–5.56)|5.2 §6]]). The three factors are

$$
\tfrac12\rho U_\infty S=\tfrac12\times0.3809\times178\times49.239=1669.2\ \text{kg/s},
$$

$$
\tfrac12\rho U_\infty Sc=1669.2\times4.889=8160.8\ \text{kg m/s},
$$

$$
\tfrac12\rho U_\infty Sc^2=8160.8\times4.889=39\,897.9\ \text{kg m}^2\text{/s}.
$$

| Derivative | Dimensionless | Factor | Dimensional |
|---|---:|---|---:|
| $\mathring X_u$ | $-0.0760$ | $\tfrac12\rho U_\infty S$ | $-126.9$ N s/m |
| $\mathring X_w$ | $0.0483$ | $\tfrac12\rho U_\infty S$ | $80.6$ N s/m |
| $\mathring Z_u$ | $-0.7273$ | $\tfrac12\rho U_\infty S$ | $-1214.0$ N s/m |
| $\mathring Z_w$ | $-3.1245$ | $\tfrac12\rho U_\infty S$ | $-5215.4$ N s/m |
| $\mathring M_u$ | $0.0340$ | $\tfrac12\rho U_\infty Sc$ | $277.5$ N s |
| $\mathring M_w$ | $-0.2169$ | $\tfrac12\rho U_\infty Sc$ | $-1770.1$ N s |
| $\mathring M_q$ | $-1.2732$ | $\tfrac12\rho U_\infty Sc^2$ | $-50\,798.0$ N m s |

The units follow from what each derivative multiplies: a force per unit velocity is N s/m, a moment per unit velocity is N m/(m/s) = N s, and a moment per unit pitch rate is N m s.

### (iii) Eigenvalues [2 marks]

With $mU_\infty=3\,140\,276$ kg m/s and $mg=173\,068$ N, $\mathbf A=\mathbf M^{-1}\mathbf A'$ is

$$
\mathbf A=\begin{bmatrix}-0.007191&0.004570&0&-9.81\\-0.06881&-0.2956&178&0\\0.001675&-0.01068&-0.3066&0\\0&0&1&0\end{bmatrix}.
$$

```python
import numpy as np
m, U, Iyy, g = 17642.0, 178.0, 165669.0, 9.81
Xu, Xw, Zu, Zw, Mu, Mw, Mq = -126.9, 80.6, -1214.0, -5215.4, 277.5, -1770.1, -50798.0
M  = np.diag([m, m, Iyy, 1.0])
Ap = np.array([[Xu, Xw, 0, -m*g], [Zu, Zw, m*U, 0], [Mu, Mw, Mq, 0], [0, 0, 1, 0]])
print(np.linalg.eigvals(np.linalg.solve(M, Ap)))
```

$$
\boxed{\lambda_{1,2}=-0.298\pm1.376j,\qquad\lambda_{3,4}=-0.007\pm0.078j}
$$

(to four places, $-0.2982\pm1.3763j$ and $-0.0065\pm0.0777j$).

### (iv) SPO [3 marks]

The SPO is $\lambda=-0.298\pm1.376j$: the larger, faster and better-damped complex pair. Its real part is negative, so it is stable, and

$$
\omega=1.376\ \text{rad/s},
$$

$$
t_{1/2}=\frac{\ln0.5}{\sigma}=\frac{-0.6931}{-0.2982}=2.324\ \text{s},
$$

$$
\omega_n=\sqrt{0.2982^2+1.3763^2}=1.408\ \text{rad/s},
$$

$$
\zeta=-\frac{\sigma}{\omega_n}=\frac{0.2982}{1.4083}=0.212.
$$

### (v) Phugoid [3 marks]

The phugoid is $\lambda=-0.0065\pm0.0777j$: the small, slow, lightly damped pair. It is stable (negative real part), with

$$
\omega=0.078\ \text{rad/s},
$$

$$
t_{1/2}=\frac{-0.6931}{-0.00652}=106.310\ \text{s},
$$

$$
\omega_n=\sqrt{0.00652^2+0.07774^2}=0.078\ \text{rad/s},
$$

$$
\zeta=\frac{0.00652}{0.07801}=0.084.
$$

$\omega_n$ agrees with Lanchester's $\sqrt2\,g/U_\infty=0.0779$ rad/s ([[SESA3047 6.2 - Phugoid Approximation#2. Lanchester's approximation (6.28–6.33)|6.2 §2]]). Without $\mathring Z_{\dot w}$, $\mathring Z_q$ and $\mathring M_{\dot w}$ the SPO damping is $0.212$ against $0.263$ for the full F-4C model of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1 §7]]: the downwash-lag term $\mathring M_{\dot w}$ is a real part of the SPO damping. The phugoid is almost unaffected.

### (vi) Halving the static margin [6 marks]

The pitch stiffness derivative is proportional to the static margin ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives|SESA2027 A2 §4]]):

$$
M_w=-H_s\,C_{L^*_\alpha},
$$

so halving $H_s$ halves $M_w$: $\mathring M_w=-1770.1\to-885.0$ N s, with every other derivative unchanged. The new eigenvalues are

$$
\boxed{\text{SPO: }\lambda=-0.296\pm0.970j\ (\omega_n=1.014\ \text{rad/s},\ \zeta=0.292),\qquad\text{phugoid: }\lambda=-0.009\pm0.090j\ (\omega_n=0.091\ \text{rad/s},\ \zeta=0.095).}
$$

![[amc_pp_202021_q3_pole_map.png|900]]

Discussion (model answer, under 200 words). The SPO approximation gives

$$
\omega_n^2=\frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mI_{yy}},\qquad2\zeta\omega_n=-\left(\frac{\mathring M_q}{I_{yy}}+\frac{\mathring Z_w}{m}\right).
$$

The stiffness term $-U_\infty\mathring M_w/I_{yy}$ falls from $1.902$ to $0.951$ s⁻² while $\mathring M_q\mathring Z_w/mI_{yy}=0.091$ s⁻² is unchanged, so $\omega_n$ drops by nearly $1/\sqrt2$ ($1.41\to1.02$ rad/s). The damping sum contains no $\mathring M_w$, so the real part stays at about $-0.30$ s⁻¹ and $\zeta$ rises ($0.21\to0.29$): a slower, softer but better-damped pitch response, the trade of stability for manoeuvrability. The improved phugoid approximation gives $\omega_n^2=(g/mU_\infty)(\mathring M_u\mathring Z_w/\mathring M_w-\mathring Z_u)$; with $\mathring M_u\ne0$ the $\mathring M_u/\mathring M_w$ ratio doubles, so the phugoid speeds up ($0.078\to0.091$ rad/s) and its damping term $\tfrac{\mathring M_u}{\mathring M_w}(\mathring X_w-mg/U_\infty)$ grows ($\zeta$ $0.084\to0.095$). With $\mathring M_u=0$ the phugoid would be unaffected, as Lanchester's model predicts.

> [!check] Approximations against the full model
> SPO approximation: $\omega_n=1.412\to1.021$ rad/s and $\zeta=0.213\to0.295$, within 1 % of the full values. Improved phugoid: $\omega_n=0.080\to0.094$ rad/s and $\zeta=0.095\to0.122$, which captures the trend but overstates the damping.

---

## Q4. Lateral state space, roll subsidence and fin size (25 marks)

> The lateral model is
> $\begin{bmatrix}m&0&0&0\\0&I_{xx}&-I_{xz}&0\\0&-I_{xz}&I_{zz}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot v\\\dot p\\\dot r\\\dot\phi\end{bmatrix}=\begin{bmatrix}\mathring Y_v&\mathring Y_p&\mathring Y_r-mU_\infty&mg\\\mathring L_v&\mathring L_p&\mathring L_r&0\\\mathring N_v&\mathring N_p&\mathring N_r&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}$.
> (i) Seven non-zero dimensional derivatives from Table 2, with units, 1 d.p. [7] (ii) Eigenvalues to 3 d.p. with code. [2] (iii) Name the mode for each eigenvalue, with reasons [2, max 50 words]. (iv) Compare the roll-mode eigenvalue with $\lambda=\mathring L_p/I_{xx}$. [1] (v) With a plot, discuss how the approximate and exact eigenvalues affect the maximum roll rate and the time to about 60 % of it for a fixed aileron deflection [3, max 100 words]. (vi) $S_F$ is cut to 75 %: list the derivatives that change and any neglected or not estimable. [2] (vii) Updated derivatives (1 d.p.) and eigenvalues (3 d.p.). [4] (viii) Effect of the smaller fin on the lateral modes [4, max 100 words].

Table 2 is replaced by the Navion data of SESA3047 Table 6.2: $U_\infty=53.75$ m/s, $\rho=1.225$ kg/m³, $S=17.09$ m², $b=10.18$ m, $m=1247$ kg, $I_{xx}=1421$ kg m², $I_{zz}=4787$ kg m², $I_{xz}=0$. These lateral modes are Chapter 6 §§6.7–6.10, lectured from Thu 19 Nov.

### (i) The seven dimensional derivatives [7 marks]

Lateral derivatives use the span: a derivative with respect to $v$ is scaled by $\tfrac12\rho U_\infty S$ (force) or $\tfrac12\rho U_\infty Sb$ (moment), and one with respect to $p$ or $r$ by a further $b$, consistent with the course's $L_p=-\frac{1}{Sb^2}\int C_{l_\alpha}c\,y^2dy$. The factors are

$$
\tfrac12\rho U_\infty S=\tfrac12\times1.225\times53.75\times17.09=562.63\ \text{kg/s},
$$

$$
\tfrac12\rho U_\infty Sb=562.63\times10.18=5727.6\ \text{kg m/s},
$$

$$
\tfrac12\rho U_\infty Sb^2=5727.6\times10.18=58\,307.2\ \text{kg m}^2\text{/s}.
$$

| Derivative | Dimensionless | Factor | Dimensional |
|---|---:|---|---:|
| $\mathring Y_v$ | $-0.564$ | $\tfrac12\rho U_\infty S$ | $-317.3$ N s/m |
| $\mathring L_v$ | $-0.074$ | $\tfrac12\rho U_\infty Sb$ | $-423.8$ N s |
| $\mathring N_v$ | $0.0701$ | $\tfrac12\rho U_\infty Sb$ | $401.5$ N s |
| $\mathring L_p$ | $-0.205$ | $\tfrac12\rho U_\infty Sb^2$ | $-11\,953.0$ N m s |
| $\mathring L_r$ | $0.0535$ | $\tfrac12\rho U_\infty Sb^2$ | $3119.4$ N m s |
| $\mathring N_p$ | $-0.02875$ | $\tfrac12\rho U_\infty Sb^2$ | $-1676.3$ N m s |
| $\mathring N_r$ | $-0.0625$ | $\tfrac12\rho U_\infty Sb^2$ | $-3644.2$ N m s |

$\mathring Y_p$ and $\mathring Y_r$ are zero in this data set, which is why seven derivatives are non-zero.

### (ii) Eigenvalues [2 marks]

```python
import numpy as np
m, U, Ixx, Izz, Ixz, g = 1247.0, 53.75, 1421.0, 4787.0, 0.0, 9.81
Yv, Lv, Nv, Lp, Lr, Np, Nr = -317.3, -423.8, 401.5, -11953.0, 3119.4, -1676.3, -3644.2
M  = np.array([[m, 0, 0, 0], [0, Ixx, -Ixz, 0], [0, -Ixz, Izz, 0], [0, 0, 0, 1.0]])
Ap = np.array([[Yv, 0, -m*U, m*g], [Lv, Lp, Lr, 0], [Nv, Np, Nr, 0], [0, 1, 0, 0]])
print(np.linalg.eigvals(np.linalg.solve(M, Ap)))
```

$$
\boxed{\lambda_1=-8.444,\qquad\lambda_{2,3}=-0.487\pm2.338j,\qquad\lambda_4=-0.009}
$$

The characteristic polynomial factorises as $(\lambda+0.0087)(\lambda+8.44)(\lambda^2+0.974\lambda+5.70)$, Eq. 6.40 of the Chapter 6 notes.

### (iii) Which mode is which [2 marks]

A model answer within 50 words: $-8.444$ is roll subsidence (large, real, fast decay of roll rate by roll damping). $-0.487\pm2.338j$ is the Dutch roll, the only oscillatory pair ($\omega_n=2.39$ rad/s, $\zeta=0.20$). $-0.009$ is the spiral mode, real and close to zero (here slowly convergent, $t_{1/2}=79$ s).

### (iv) Roll-subsidence approximation [1 mark]

$$
\lambda\approx\frac{\mathring L_p}{I_{xx}}=\frac{-11\,953.0}{1421}=\boxed{-8.412\ \text{s}^{-1}},
$$

$0.4$ % smaller in magnitude than the exact $-8.444$ s⁻¹ (the notes quote $-8.41$).

### (v) Roll-rate response to a step aileron [3 marks]

The single-degree-of-freedom roll equation $I_{xx}\dot p=\mathring L_pp+\mathring L_{\delta_A}\delta_A$ has the step solution

$$
p(t)=-\frac{\mathring L_{\delta_A}\delta_A}{\mathring L_p}\left(1-e^{\lambda t}\right),\qquad\lambda=\frac{\mathring L_p}{I_{xx}}.
$$

![[amc_pp_202021_q4_roll_rate_response.png|900]]

Model answer within 100 words. The maximum (steady) roll rate $p_{ss}=-\mathring L_{\delta_A}\delta_A/\mathring L_p$ depends only on the ratio of control power to roll damping, not on the eigenvalue, so both curves level off at the same value. The eigenvalue sets the lag: $p$ reaches $1-e^{-1}=63$ % of $p_{ss}$ at the time constant $\tau=-1/\lambda$, which is $0.1184$ s for the exact eigenvalue and $0.1189$ s for the approximation. The 0.4 % difference is invisible on the plot, because the roll mode is almost uncoupled from sideslip and yaw.

### (vi) Derivatives affected by a smaller fin [2 marks]

The fin contributes to every derivative involving sideslip or yaw rate at the fin. The fin estimates, with fin lift slope $a_F$, area $S_F$ and arm $l_F$, are

$$
Y_v=-\frac{S_F}{S}a_F,\qquad N_v=\frac{S_F}{S}a_F\frac{l_F}{b},\qquad N_r=-\frac{S_F}{S}a_F\left(\frac{l_F}{b}\right)^2,\qquad Y_r=\frac{S_F}{S}a_F\frac{l_F}{b},
$$

all proportional to $S_F$. The last two follow from the fin incidence $rl_F/U_\infty$ induced by yaw rate (derived in Q4(ii) of [[SESA2025 Past Paper 2023-24 - Solutions]]). Changed: $Y_v$, $N_v$ and $N_r$ (and $Y_r$, which is zero in this data set). Neglected or not estimable without the fin height above the roll axis, which is not given: the fin parts of $L_v$, $L_r$ and $L_p$, and the small fin contributions to $Y_p$ and $N_p$. $L_p$ and $N_p$ are dominated by the wing and are taken as unchanged.

### (vii) Updated derivatives and eigenvalues [4 marks]

Treating $Y_v$, $N_v$ and $N_r$ as entirely fin contributions, each scales by $0.75$:

| Derivative | Dimensionless | Dimensional |
|---|---:|---:|
| $\mathring Y_v$ | $-0.564\times0.75=-0.423$ | $-238.0$ N s/m |
| $\mathring N_v$ | $0.0701\times0.75=0.05258$ | $301.1$ N s |
| $\mathring N_r$ | $-0.0625\times0.75=-0.04688$ | $-2733.1$ N m s |

$$
\boxed{\lambda_1=-8.443,\qquad\lambda_{2,3}=-0.361\pm2.089j,\qquad\lambda_4=-0.008}
$$

### (viii) Effect of the smaller fin [4 marks]

| Mode | Original | Fin at 75 % |
|---|---|---|
| Roll subsidence | $-8.444$ s⁻¹ | $-8.443$ s⁻¹ |
| Dutch roll | $\omega_n=2.388$ rad/s, $\zeta=0.204$ | $\omega_n=2.120$ rad/s, $\zeta=0.170$ |
| Spiral | $-0.00875$ s⁻¹ ($t_{1/2}=79.3$ s) | $-0.00832$ s⁻¹ ($t_{1/2}=83.3$ s) |

Model answer within 100 words. The Dutch roll suffers most. Its approximation $\omega_n^2\approx(\mathring Y_v\mathring N_r+mU_\infty\mathring N_v)/mI_{zz}$ is dominated by the weathercock stiffness $\mathring N_v$, so the frequency falls by about $\sqrt{0.75}$, and its damping $2\zeta\omega_n=-(\mathring N_r/I_{zz}+\mathring Y_v/m)$ loses a quarter of both yaw damping and side-force damping, so $\zeta$ drops from 0.20 to 0.17. Roll subsidence depends on the wing through $\mathring L_p$ and is unchanged. The spiral stays marginally stable and slightly slower, because $N_v$ and $N_r$ fall together in $L_vN_r-L_rN_v$.

---

## Paper slips and ambiguities

- Format. The filed paper is the 2020-21 online 24-hour assessment, with marks 30/20/25/25 and individual Blackboard data sets, not a 2-hour 4 × 25 paper with a formula sheet. Q1(ii), Q3 and Q4 cannot be reproduced with the original numbers; the F-4C and Navion stand-ins are labelled throughout.
- Q3, the printed model. The $(2,4)$ entry is $-mg$, the same as the $(1,4)$ entry. For level trim it should be $-mg\sin\gamma_0=0$. Kept as printed, it turns the stand-in phugoid unstable ($\lambda=+0.020\pm0.073j$) while barely moving the SPO ($-0.324\pm1.383j$), so it is a typesetting slip and the solution uses zero.
- Q3(iv)–(v). "Angular frequency" is read as the damped frequency $\omega=|\text{Im}\,\lambda|$, distinct from $\omega_n$, as on the later papers' formula sheets.
- Q4(v). "Approximately 60 %" is the 63.2 % reached at one time constant.
- Q4(viii) says "tailplane" but means the fin of Q4(vi).
