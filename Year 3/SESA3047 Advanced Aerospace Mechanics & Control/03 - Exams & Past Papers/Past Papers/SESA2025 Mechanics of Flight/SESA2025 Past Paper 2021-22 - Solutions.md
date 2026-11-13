---
title: "SESA2025 Past Paper 2021-22 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, stick-free, trim-drag, trim-tab, neutral-point, flight-test, cg-trim, stability-quartic, short-period, phugoid, dutch-roll, spiral, roll-subsidence]
paper: "2021-22"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[Stick-Fixed vs Stick-Free Stability]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-202122-02-SESA2025.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# SESA2025 Past Paper 2021-22 - Solutions

> [!abstract] Paper info
> 2021-22 Semester 2 examination (2 h, on campus), four questions of 25 marks, all compulsory, with an equations sheet for the static-stability part (equilibrium and manoeuvring flight, trim drag, tail derivatives) and no sheet for the dynamics. Q1 and Q2 are static stability in the notation of [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability|SESA2022 T6]] ($C_{L^*}$, $K$, $H_s$). Q3 is the longitudinal modes from a factorised quartic. Q4 is the lateral modes, which SESA3047 lectures from Thu 19 Nov. All numbers were checked in Python with $g=9.81$ m/s².

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Stick-free stability, trim drag, tail aspect ratio, stick-free tail lift and the trim-tab coefficient | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability\|SESA2022 T6]], [[Stick-Fixed vs Stick-Free Stability]], [[Downwash and Induced Drag]] |
| 2 | 25 | Neutral point from flight tests; CG position for trim with no control deflection | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#5. Neutral point from flight tests\|T6 §5]], [[SESA1015 M11 - Longitudinal Trim and Static Stability\|SESA1015 M11]] |
| 3 | 25 | Longitudinal quartic: SPO and phugoid parameters, gust response, $M_q$ | [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation\|6.1]], [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid\|SESA2027 A3]], [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives\|SESA2027 A2 §4]] |
| 4 | 25 | Lateral quartic, the three lateral modes, Dutch-roll approximation | Not yet lectured: Chapter 6 §§6.7–6.9 ([[Lecture Notes - Chapter 6.pdf]]), lectured from Thu 19 Nov; background in [[Lateral and Directional Stability]] |

---

## Q1. Stick-free stability, trim drag and the tailplane (25 marks)

> (i) Explain, with equations, why a conventional aircraft is less stable stick free than stick fixed, and why the effect is larger when the elevator chord is large relative to the tailplane chord. [7]
> (ii) Define trim drag and sketch it against tailplane lift coefficient. Explain physically why the minimum trim drag can be negative, and why trim drag is positive when the tail lift is negative. [7]
> (iii) A team member suggests decreasing the tailplane aspect ratio at constant tail area to improve stability. Discuss and show whether this is a good idea. [4]
> (iv) Derive the stick-free tailplane lift equation, and explain with diagrams why its coefficient is expected to be negative for a conventional tailplane. [7]

### (i) Stick-free against stick-fixed stability [7 marks]

The stick-fixed static margin is ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Neutral point and static margin|T6 §3]])

$$
H_s=h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad C_{L_{T,\alpha}}=k(1-\epsilon_\alpha),\qquad k=a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}.
$$

Stick free, the pilot holds no force, so the hinge moment is zero, $C_{M_H}=b_1\alpha_{T\text{eff}}+b_2\eta+b_3\beta=0$, and the elevator takes up the floating angle

$$
\eta=-\frac{b_1\alpha_{T\text{eff}}+b_3\beta}{b_2}.
$$

A change in tail incidence $\Delta\alpha_{T\text{eff}}$ therefore moves the elevator by $\Delta\eta=-(b_1/b_2)\Delta\alpha_{T\text{eff}}$. Both $b_1$ and $b_2$ are negative, so $b_1/b_2>0$ and the elevator floats trailing edge up when the tail incidence increases. The tail lift slope becomes

$$
\bar a_1=a_1-a_2\frac{b_1}{b_2}<a_1,
$$

so $\bar k<k$, $C_{L_{T,\alpha}}$ is smaller, the neutral point $h_0+KC_{L_{T,\alpha}}/C_{L^*_\alpha}$ moves forward, and $H_{s,\text{free}}<H_{s,\text{fixed}}$. The restoring tail lift after a nose-up disturbance is partly cancelled by the floating elevator.

The loss is $a_2b_1/b_2$. A larger elevator-to-tail chord ratio $E$ increases both factors. The elevator effectiveness from thin-aerofoil theory is $a_2/a_1=1-(\theta_h-\sin\theta_h)/\pi$ with $\cos\theta_h=2E-1$, which rises from 0.66 at $E=0.3$ to 0.82 at $E=0.5$. And with more of the tail's chord free to rotate, the hinge moment generated by incidence ($b_1$) grows relative to the hinge stiffness to deflection ($b_2$), so the elevator floats further. With a very large elevator most of the tailplane floats and the stick-free tail contributes little stability.

### (ii) Trim drag [7 marks]

Trim drag $C_{D_m}$ is the change in induced drag caused by sharing the total lift $L^*$ between wing and tailplane, compared with the wing carrying all of it. Ignoring interference between the surfaces, the induced drag of the pair is

$$
C_{D_i}=\frac{C_L^2}{\pi Ae}+\frac{S_T}{S}\frac{C_{L_T}^2}{\pi A_Te_T}.
$$

Write $r=C_{L_T}S_T/(C_{L^*}S)$ for the tail's share of the lift, so that $C_L=C_{L^*}(1-r)$ and $C_{L_T}=rC_{L^*}S/S_T$. The wing term is

$$
\frac{C_{L^*}^2(1-r)^2}{\pi Ae}=C_{D_{L^*}}(1-r)^2,\qquad C_{D_{L^*}}=\frac{C_{L^*}^2}{\pi Ae}.
$$

The tail term is

$$
\frac{S_T}{S}\frac{r^2C_{L^*}^2S^2/S_T^2}{\pi A_Te_T}=C_{D_{L^*}}\,r^2\frac{S\,\pi Ae}{S_T\,\pi A_Te_T}=C_{D_{L^*}}\,r^2(\sigma-1),\qquad\sigma=1+\frac{S\pi Ae}{S_T\pi A_Te_T}.
$$

Subtract $C_{D_{L^*}}$ and expand:

$$
C_{D_m}=C_{D_{L^*}}\left[(1-r)^2+r^2(\sigma-1)-1\right]=C_{D_{L^*}}\left[-2r+\sigma r^2\right],
$$

$$
\boxed{C_{D_m}=C_{D_{L^*}}\,r\,(\sigma r-2)},
$$

the formula on the equations sheet. It is a parabola in $r$ (and so in $C_{L_T}$ at fixed $C_{L^*}$), zero at $r=0$ and $r=2/\sigma$, with minimum $-C_{D_{L^*}}/\sigma$ at $r=1/\sigma$.

![[amc_pp_202122_q1_trim_drag_vs_tail_lift.png|900]]

Induced drag grows with the square of each surface's lift. A small upward tail lift takes a little load off the wing; the wing's induced drag falls in proportion to $2r$, while the tail's rises only in proportion to $r^2$, so for $0<r<2/\sigma$ the pair makes less induced drag than the wing alone and $C_{D_m}<0$. Two lifting surfaces spread the lift over more span, as a biplane does. When the tail lift is negative ($r<0$), the wing must carry the weight plus the tail's download, so its induced drag rises ($-2r>0$) and the tail adds its own induced drag on top: both terms are positive and $C_{D_m}>0$.

### (iii) Lower tailplane aspect ratio [4 marks]

It is a poor idea. At constant $S_T$ the tail volume $K$ is unchanged, but the tail's 3D lift slope falls with aspect ratio:

$$
k=a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}.
$$

With $a_1=2\pi$ and $e_T=0.9$, $k=4.59$ rad⁻¹ at $A_T=6$, $4.04$ at $A_T=4$ and $3.61$ at $A_T=3$, a 21 % loss from 6 to 3. $C_{L_{T,\alpha}}=k(1-\epsilon_\alpha)$ falls by the same fraction, so $h_n=h_0+KC_{L_{T,\alpha}}/C_{L^*_\alpha}$ moves forward and the static margin shrinks. A lower-aspect-ratio tail also has more induced drag for the same lift ($\sigma$ rises, so the trim-drag saving $-C_{D_{L^*}}/\sigma$ falls) and costs pitch damping ($M_q\propto C_{L_{T,\alpha}}$). Its only advantage is a later stall, which matters for control at high incidence, not for static stability.

### (iv) Stick-free tail lift and the sign of the tab coefficient [7 marks]

Start from the linear tail lift and hinge-moment models

$$
C_{L_T}=a_1\alpha_{T\text{eff}}+a_2\eta+a_3\beta,\qquad C_{M_H}=b_1\alpha_{T\text{eff}}+b_2\eta+b_3\beta.
$$

Stick free, $C_{M_H}=0$. Solve for $\eta$:

$$
\eta=-\frac{b_1}{b_2}\alpha_{T\text{eff}}-\frac{b_3}{b_2}\beta.
$$

Substitute into the lift equation:

$$
C_{L_T}=a_1\alpha_{T\text{eff}}-a_2\frac{b_1}{b_2}\alpha_{T\text{eff}}-a_2\frac{b_3}{b_2}\beta+a_3\beta.
$$

Collect terms:

$$
\boxed{C_{L_T}=\bar a_1\alpha_{T\text{eff}}+\bar a_3\beta,\qquad\bar a_1=a_1-a_2\frac{b_1}{b_2},\qquad\bar a_3=a_3-a_2\frac{b_3}{b_2}}.
$$

With $\alpha_{T\text{eff}}$ from the equations sheet, solving for $C_{L_T}$ as in the stick-fixed case gives $C_{L_T}=\bar k\left[(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s+(\bar a_3/\bar a_1)\beta\right]$ with $\bar k=\bar a_1\pi A_Te_T/(\pi A_Te_T+\bar a_1)$.

The coefficient expected to be negative is $\bar a_3$. Deflecting the tab by itself adds a little lift, $a_3>0$, but the tab is small and $a_3$ is the smallest of the $a$ coefficients. Its main effect is on the hinge moment: the tab sits at the trailing edge, the longest arm from the hinge, so $|b_3|$ is the largest of the $b$ coefficients, and $b_3$ and $b_2$ are both negative, making $b_3/b_2>0$ and $a_2b_3/b_2$ larger than $a_3$. Physically, a tab deflected down ($\beta>0$) carries an upward load far behind the hinge, which drives the elevator trailing edge up until the hinge moment is zero. The elevator, much larger than the tab, then loses more lift than the tab gained, so the net tail lift change is negative.

![[amc_pp_202122_q1_stick_free_tab.png|900]]

---

## Q2. Neutral point from flight tests and trim by moving the CG (25 marks)

> (i) A UAV ($m=1500$ kg, $S=32$ m², $g=9.81$ m/s², $\rho=1.225$ kg/m³) is flown stick fixed in straight level flight. Elevator angles: $h=0.34$: $\eta=-1^\circ$ at 80 m/s, $1^\circ$ at 90 m/s; $h=0.37$: $\eta=-0.5^\circ$ at 80 m/s, $1.2^\circ$ at 90 m/s. Estimate the neutral point as a percentage of the MAC. [12]
> (ii) An aircraft with $A=8$, $S=3.78$ m², $e=0.9$, $m=45$ kg, $S_T=0.54$ m², $a_0=2\pi$ rad⁻¹, $l=5$ m, $c=0.7$ m, $C_{M_0}=-0.006$, $\alpha_0=-0.9^\circ$, $\rho=1.225$ kg/m³, $V=20$ m/s, $\alpha=4.6^\circ$, $h_0=0.25$ trims by pumping fuel, with no control deflection. Find the CG position for trim as a percentage of the MAC. [13]

### (i) Neutral point [12 marks]

As in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#5. Neutral point from flight tests|T6 §5]], $d\eta/dC_{L^*}=(h-h_n)/(Kka_2/a_1)$ is linear in $h$ and zero at $h_n$. In level flight $C_{L^*}=C_W=W/(\tfrac12\rho V^2S)$, with $W=1500\times9.81=14\,715$ N.

At 80 m/s:

$$
C_{L^*}=\frac{14\,715}{\tfrac12\times1.225\times80^2\times32}=\frac{14\,715}{125\,440}=0.117307.
$$

At 90 m/s:

$$
C_{L^*}=\frac{14\,715}{\tfrac12\times1.225\times90^2\times32}=\frac{14\,715}{158\,760}=0.092687.
$$

So $\Delta C_{L^*}=0.092687-0.117307=-0.024620$ from 80 to 90 m/s, the same for both CG positions because the weight did not change. The slopes are

$$
\frac{d\eta}{dC_{L^*}}\bigg|_{h=0.34}=\frac{1-(-1)}{-0.024620}=-81.23^\circ,
$$

$$
\frac{d\eta}{dC_{L^*}}\bigg|_{h=0.37}=\frac{1.2-(-0.5)}{-0.024620}=-69.05^\circ.
$$

Both are negative, so the aircraft is stable at both CG positions, and moving the CG aft flattens the curve. Extrapolate linearly to zero slope:

$$
h_n=0.34+(0.37-0.34)\frac{-81.23}{-81.23-(-69.05)}=0.34+0.03\times\frac{81.23}{12.18}.
$$

The common $\Delta C_{L^*}$ cancels, so the ratio is just $2/(2-1.7)=6.667$:

$$
h_n=0.34+0.03\times6.667=0.34+0.20=\boxed{0.54=54\ \%\ \text{of the MAC}}.
$$

![[amc_pp_202122_q2_eta_vs_CL.png|900]]

The static margins in the tests were $0.20$ and $0.17$. The long extrapolation (from a CG range of 0.03 to a point 0.17 beyond it) magnifies any error in $\eta$: reading $1.1^\circ$ instead of $1.2^\circ$ at $h=0.37$, 90 m/s, gives $\Delta\eta=1.6^\circ$ and $h_n=0.34+0.03\times2/0.4=0.49$, and $1.3^\circ$ gives $0.64$.

### (ii) CG position for trim with no control deflection [13 marks]

The force and moment equations of the equations sheet are

$$
C_{L^*}=C_L+C_{L_T}\frac{S_T}{S}=C_W\cos\gamma,\qquad0=C_{M_0}+C_{L^*}(h-h_0)-C_{L_T}K.
$$

The angle of attack is given, so the wing lift is known; the tail must supply the rest of the lift, and the moment equation then fixes $h$. The flight is level ($\gamma=0$) and the angles are in radians.

Weight coefficient:

$$
\tfrac12\rho V^2=\tfrac12\times1.225\times20^2=245\ \text{Pa},
$$

$$
C_{L^*}=C_W=\frac{45\times9.81}{245\times3.78}=\frac{441.45}{926.10}=0.47668.
$$

Wing lift-curve slope:

$$
C_{L_\alpha}=a_0\frac{\pi Ae}{\pi Ae+a_0}=2\pi\times\frac{\pi\times7.2}{\pi\times7.2+2\pi}=2\pi\times\frac{7.2}{9.2}=4.9173\ \text{rad}^{-1}.
$$

Wing lift at $\alpha-\alpha_0=4.6^\circ+0.9^\circ=5.5^\circ=0.095993$ rad:

$$
C_L=4.9173\times0.095993=0.47202.
$$

Tail lift from the force balance:

$$
C_{L_T}\frac{S_T}{S}=0.47668-0.47202=0.00466,
$$

$$
C_{L_T}=0.00466\times\frac{3.78}{0.54}=0.03256.
$$

Tail volume:

$$
K=\frac{S_Tl}{Sc}=\frac{0.54\times5}{3.78\times0.7}=\frac{2.70}{2.646}=1.0204.
$$

Moment equation, solved for $h$:

$$
h=h_0+\frac{C_{L_T}K-C_{M_0}}{C_{L^*}}=0.25+\frac{0.03256\times1.0204+0.006}{0.47668},
$$

$$
h=0.25+\frac{0.03323+0.006}{0.47668}=0.25+0.08229=\boxed{0.332=33.2\ \%\ \text{of the MAC}}.
$$

> [!warning] A small difference of two nearly equal numbers
> $C_{L_T}$ comes from $0.47668-0.47202$, so rounding $C_{L_\alpha}$ or $C_W$ to three figures changes $C_{L_T}$ by tens of per cent. Carry five significant figures until $h$; $h$ itself is less sensitive, since $C_{L_T}K$ is only 85 % of the numerator.

---

## Q3. Longitudinal modes from the stability quartic (25 marks)

> The longitudinal quartic factorises as $(\lambda^2+0.006\lambda+0.003)(\lambda^2+2.2\lambda+3.3)=0$.
> (i) Calculate the eigenvalues and identify the SPO and phugoid quadratics. [4] (ii) SPO: stable or not, angular frequency, half-life, $\omega_n$, $\zeta$. [4] (iii) The same for the phugoid. [4] (iv) Plot the pitch-angle response to a vertical gust $w_g$ over a short and a long time, and annotate the features of both modes. [8] (v) Physical meaning of $M_q$ and the part of the aircraft that affects it. [3] (vi) If $M_q$ is halved, what happens to the damping of the two modes? [2]

### (i) Eigenvalues and identification [4 marks]

Each quadratic $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2=0$ has roots $\lambda=-\zeta\omega_n\pm j\omega_n\sqrt{1-\zeta^2}$.

$$
\lambda^2+2.2\lambda+3.3=0:\quad\lambda=\frac{-2.2\pm\sqrt{4.84-13.2}}{2}=\boxed{-1.1\pm1.4457j},
$$

$$
\lambda^2+0.006\lambda+0.003=0:\quad\lambda=\frac{-0.006\pm\sqrt{0.000036-0.012}}{2}=\boxed{-0.003\pm0.05469j}.
$$

$\lambda^2+2.2\lambda+3.3$ is the SPO: its roots are larger (fast, period about 4 s) and heavily damped. $\lambda^2+0.006\lambda+0.003$ is the phugoid: small roots (period about two minutes) and very light damping. The separation of time scales, a factor of 33 in $\omega_n$, is what lets the quartic split into these two factors ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1 §2]]).

### (ii) SPO [4 marks]

Stable, because the real part $\sigma=-1.1$ s⁻¹ is negative.

$$
\omega=1.446\ \text{rad/s},
$$

$$
t_{1/2}=\frac{\ln0.5}{\sigma}=\frac{-0.6931}{-1.1}=0.630\ \text{s},
$$

$$
\omega_n=\sqrt{3.3}=1.817\ \text{rad/s},
$$

$$
\zeta=\frac{2.2}{2\times1.8166}=0.606.
$$

### (iii) Phugoid [4 marks]

Stable, because $\sigma=-0.003$ s⁻¹ is negative, though only just.

$$
\omega=0.0547\ \text{rad/s}\quad(T=2\pi/\omega=114.9\ \text{s}),
$$

$$
t_{1/2}=\frac{-0.6931}{-0.003}=231.0\ \text{s},
$$

$$
\omega_n=\sqrt{0.003}=0.0548\ \text{rad/s},
$$

$$
\zeta=\frac{0.006}{2\times0.05477}=0.0548.
$$

> [!check] Consistency
> For each pair, $\omega_n^2=\sigma^2+\omega^2$: $1.1^2+1.4457^2=3.300$ and $0.003^2+0.05469^2=0.003000$.

### (iv) Pitch response to a vertical gust [8 marks]

A sharp upward gust changes the relative wind so that $w$ jumps by $w_g$ and the incidence by $w_g/U_\infty$. The response below is the free response from $w(0)=w_g=5$ m/s, computed with the F-4C mode shapes of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]] and this paper's two eigenvalue pairs.

![[amc_pp_202122_q3_pitch_gust_response.png|900]]

The features to annotate:

- Short term (first few seconds): the SPO. The increased incidence produces a nose-down pitching moment through the static stability ($M_w<0$), so $\theta$ moves quickly to weathercock into the new relative wind, overshoots slightly and settles within about two seconds ($\zeta=0.61$, $t_{1/2}=0.63$ s, period 4.3 s). Speed barely changes on this time scale.
- Long term (minutes): the phugoid. The SPO leaves the aircraft with a changed attitude and flight path, which trades height for speed in a lightly damped oscillation of $\theta$ with period $T=115$ s, decaying with envelope $e^{-0.003t}$ and halving every 231 s. Incidence stays almost constant during this motion.
- The two time scales differ so much that on the long plot the SPO is a near-instantaneous step at $t=0$, and on the short plot the phugoid is a slow drift.

### (v) Meaning of M_q [3 marks]

$M_q$ is the pitch damping derivative: the change in pitching moment per unit pitch rate, $\mathring M_q=\partial M/\partial q$, normalised as $M_q=\mathring M_q/(\tfrac12\rho U_\infty Sc^2)$. When the aircraft pitches nose-up at rate $q$, the tailplane, a distance $l$ behind the CG, moves downwards at $ql$ and sees an extra incidence $ql/U_\infty$. The extra tail lift acts on the arm $l$ and opposes the rotation, so $M_q<0$. The tailplane provides most of it ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives|SESA2027 A2 §4]]):

$$
M_q\approx-K\,C_{L_{T,\alpha}}\frac{l}{c},
$$

which grows with tail area, tail lift slope and (as $l^2$) tail arm; the wing and fuselage add a smaller part.

### (vi) Halving M_q [2 marks]

The SPO damping decreases. In the SPO approximation $2\zeta\omega_n=-\left[\mathring M_q/I_{yy}+\mathring Z_w/m+U_\infty\mathring M_{\dot w}/I_{yy}\right]$, so $\mathring M_q$ is one of the three damping terms. The phugoid damping is essentially unchanged, because the phugoid is an exchange of speed and height at nearly constant incidence, with $q$ very small, and its damping comes from the drag change with speed ($\mathring X_u$). For the F-4C model, halving $\mathring M_q$ lowers the SPO $\zeta$ from $0.263$ to $0.210$ and moves the phugoid $\zeta$ only from $0.083$ to $0.085$.

---

## Q4. Lateral modes (25 marks)

> (i) The lateral quartic factorises as $(\lambda+7.1758)(\lambda+0.0074)(\lambda^2-0.5235\lambda+3.4336)=0$. Calculate the eigenvalues and identify the three lateral modes. [6]
> (ii) Explain the characteristics of the three modes. [6]
> (iii) From the lateral state-space equation, stating all assumptions, show that the Dutch-roll approximation is $mI_{zz}\lambda^2-(m\mathring N_r+I_{zz}\mathring Y_v)\lambda+\mathring Y_v\mathring N_r+mU_\infty\mathring N_v=0$. [9]
> (iv) By inspection, find the two derivatives responsible for Dutch-roll damping at fixed $\omega_n$; discuss their meaning and the part of the aircraft that affects them. [4]

These lateral modes are Chapter 6 §§6.7–6.9 of the SESA3047 lecture notes, lectured from Thu 19 Nov.

### (i) Eigenvalues and the three modes [6 marks]

$$
\lambda_1=\boxed{-7.1758\ \text{s}^{-1}},\qquad\lambda_2=\boxed{-0.0074\ \text{s}^{-1}},
$$

$$
\lambda^2-0.5235\lambda+3.4336=0:\quad\lambda_{3,4}=\frac{0.5235\pm\sqrt{0.27405-13.7344}}{2}=\boxed{0.2618\pm1.8344j}.
$$

- $\lambda_1=-7.1758$: roll subsidence. Large, real and negative: a fast, non-oscillatory decay (time constant $1/7.18=0.139$ s, $t_{1/2}=0.097$ s). Stable.
- $\lambda_2=-0.0074$: spiral mode. Real and very close to zero: a very slow, non-oscillatory motion ($t_{1/2}=93.7$ s). Stable here (slowly convergent).
- $\lambda_{3,4}=0.2618\pm1.8344j$: Dutch roll, the only complex pair, so the only oscillatory mode. Its real part is positive, so it is unstable: $\omega_n=\sqrt{3.4336}=1.853$ rad/s, $\zeta=-0.5235/(2\times1.853)=-0.141$, period $2\pi/1.8344=3.43$ s and time to double $\ln2/0.2618=2.65$ s.

### (ii) Characteristics of the lateral modes [6 marks]

Roll subsidence is almost a pure rolling motion. A roll rate makes the down-going wing see more incidence and the up-going wing less, giving a rolling moment that opposes the rate ($L_p<0$), so $p$ decays exponentially with time constant $\tau\approx-I_{xx}/\mathring L_p$. It stops the roll rate but does not restore the bank angle.

The spiral mode is a slow divergence or convergence of bank angle, heading and height. A banked aircraft sideslips towards the low wing; the fin turns the nose into the sideslip ($N_v$), which yaws the aircraft into a turn, and the faster outer wing (through $L_r$) increases the bank, while dihedral ($L_v$) tries to level the wings. If the dihedral effect wins the mode converges; if the yaw-roll coupling wins the aircraft enters a tightening descending spiral. It is so slow that a pilot corrects it without noticing, but it is dangerous in cloud.

The Dutch roll is a coupled yawing, sideslipping and rolling oscillation. Directional stability ($N_v$) swings the nose back after a sideslip, the yaw inertia makes it overshoot, and each sideslip rolls the aircraft through the dihedral effect, so the wingtips trace ellipses. It is damped mainly by yaw damping ($N_r$) and side force ($Y_v$). In this aircraft it is unstable, which is typical of strong dihedral effect combined with weak yaw damping, and would need a yaw damper.

### (iii) Dutch-roll approximation [9 marks]

The lateral state-space equation is

$$
\begin{bmatrix}m&0&0&0\\0&I_{xx}&-I_{xz}&0\\0&-I_{xz}&I_{zz}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot v\\\dot p\\\dot r\\\dot\phi\end{bmatrix}=\begin{bmatrix}\mathring Y_v&\mathring Y_p&\mathring Y_r-mU_\infty&mg\\\mathring L_v&\mathring L_p&\mathring L_r&0\\\mathring N_v&\mathring N_p&\mathring N_r&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}.
$$

Assumptions (Chapter 6 §6.9):

- The Dutch roll is treated as yaw and sideslip only, so roll is neglected: $p=\dot p=0$ and $\phi=\dot\phi=0$. The roll equation (row 2) and the kinematic row 4 are dropped. This also removes $\mathring Y_pp$, $mg\phi$, $\mathring N_pp$, and the product-of-inertia term $-I_{xz}\dot p$ from row 3.
- $\mathring Y_r\ll mU_\infty$, so $\mathring Y_r-mU_\infty\approx-mU_\infty$.
- Small perturbations about straight, level, wings-level trim, as in the full linear model.

Rows 1 and 3 become

$$
m\dot v=\mathring Y_vv-mU_\infty r,
$$

$$
I_{zz}\dot r=\mathring N_vv+\mathring N_rr.
$$

Try $v=v_0e^{\lambda t}$, $r=r_0e^{\lambda t}$, so $\dot v=\lambda v$ and $\dot r=\lambda r$, and cancel $e^{\lambda t}$:

$$
m\lambda v_0=\mathring Y_vv_0-mU_\infty r_0,
$$

$$
I_{zz}\lambda r_0=\mathring N_vv_0+\mathring N_rr_0.
$$

Collect on the left:

$$
\begin{bmatrix}m\lambda-\mathring Y_v&mU_\infty\\-\mathring N_v&I_{zz}\lambda-\mathring N_r\end{bmatrix}\begin{bmatrix}v_0\\r_0\end{bmatrix}=\begin{bmatrix}0\\0\end{bmatrix}.
$$

A non-trivial solution needs a zero determinant:

$$
(m\lambda-\mathring Y_v)(I_{zz}\lambda-\mathring N_r)-mU_\infty(-\mathring N_v)=0.
$$

Expand the product:

$$
mI_{zz}\lambda^2-m\mathring N_r\lambda-I_{zz}\mathring Y_v\lambda+\mathring Y_v\mathring N_r+mU_\infty\mathring N_v=0.
$$

Group by powers of $\lambda$:

$$
\boxed{mI_{zz}\lambda^2-\left(m\mathring N_r+I_{zz}\mathring Y_v\right)\lambda+\mathring Y_v\mathring N_r+mU_\infty\mathring N_v=0}.
$$

Dividing by $mI_{zz}$ and matching with $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2=0$ gives

$$
\omega_n^2=\frac{\mathring Y_v\mathring N_r+mU_\infty\mathring N_v}{mI_{zz}},\qquad\zeta=-\frac{1}{2\omega_n}\left(\frac{\mathring N_r}{I_{zz}}+\frac{\mathring Y_v}{m}\right).
$$

Because roll is suppressed, this approximation cannot reproduce the destabilising dihedral coupling ($\mathring L_v$) that makes the Dutch roll of Q4(i) unstable; with $\mathring N_r<0$ and $\mathring Y_v<0$ it always predicts a stable Dutch roll. For the Navion of the Chapter 6 notes it gives $-0.508\pm2.108j$ against the exact $-0.487\pm2.338j$.

### (iv) The two damping derivatives [4 marks]

At fixed $\omega_n$ the damping is set by the $\lambda$ coefficient,

$$
2\zeta\omega_n=-\left(\frac{\mathring N_r}{I_{zz}}+\frac{\mathring Y_v}{m}\right),
$$

so the two derivatives are $\mathring N_r$ and $\mathring Y_v$; both are negative, and making either more negative increases the damping.

- $\mathring N_r$, yaw damping: the yawing moment per unit yaw rate. A yaw rate $r$ swings the fin sideways at $rl_F$, giving it an incidence $rl_F/U_\infty$ and a side force that opposes the rotation on the arm $l_F$; the fin dominates ($N_r\propto S_Fl_F^2$), with a smaller part from the difference in wing drag between the advancing and retreating wings. Increased by a larger fin or a longer tail arm.
- $\mathring Y_v$, side-force derivative: the side force per unit sideslip velocity. Sideslip puts the fin and the fuselage side at incidence and produces a side force opposing the sideslip. It comes mainly from the fin and the fuselage side area, and increases with fin area and fin lift slope.

---

## Paper slips and ambiguities

- Q1(iv). "The coefficient appearing in this equation" is singular, but the stick-free lift equation has two, $\bar a_1$ and $\bar a_3$. $\bar a_1$ is positive (reduced from $a_1$); the one expected to be negative, and the one a diagram of the tab explains, is $\bar a_3$.
- Q3(ii)–(iii). "Angular frequency" is taken as the damped frequency $|\text{Im}\,\lambda|$, as distinct from $\omega_n$.
- Q4(i). The Dutch-roll quadratic has a negative $\lambda$ coefficient, so the mode is unstable. That is a legitimate result for the data given, not a misprint, but it should be stated explicitly in an answer.
