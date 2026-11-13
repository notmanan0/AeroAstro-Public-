---
title: "SESA2025 Past Paper 2016-17 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, manoeuvre-margin, pull-up, trim-drag, spo, phugoid, lanchester, handling-qualities, coordinated-turn, dutch-roll, yaw-damping]
paper: "2016-17"
theory_notes: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-201617-02-SESA2025W1.pdf"]
---

# SESA2025 Past Paper 2016-17 - Solutions

> [!abstract] Paper info
> SESA2025 Mechanics of Flight, Semester 2 examination 2016-17 (120 min, formula sheet on pp. 5–6). Unlike the other papers of this period it has three questions, Q1 worth 40 marks and Q2 and Q3 worth 30 each, all compulsory. The sheet now defines $\bar a_1=2\pi-a_2b_1/b_2$ (floating elevator). Q2 reuses the longitudinal matrix of [[SESA2025 Past Paper 2013-14 - Solutions#Q3. Longitudinal modes, SPO approximation and Lanchester's phugoid (25 marks)|2013-14 Q3]] and Q3 the lateral matrix of [[SESA2025 Past Paper 2013-14 - Solutions#Q4. Lateral modes, a coordinated turn and the pure-roll approximation (25 marks)|2013-14 Q4]]. All numbers were checked in Python.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 40 | Effective tail incidence in curved flight; load factor; stick-fixed manoeuvre margin; elevator angle in a pull-up; trim drag | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability|SESA2022 T6 §4]], [[Manoeuvre Point and Manoeuvre Margin]], [[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2]] (trim drag) |
| 2 | 30 | Longitudinal modes, SPO approximation, Lanchester phugoid, handling qualities | [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|SESA3047 6.1]], [[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes#Lanchester's energy argument (6.28–6.33)|Deep Dive §9]] (§6.6, due Mon 16 Nov), [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|SESA2027 A3]] |
| 3 | 30 | Coordinated turn at given bank; Dutch roll approximation; flight-test excitation; yaw damping $N_r$ | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[Lateral and Directional Stability]] |

---

## Q1. Manoeuvre margin, pull-up trim and trim drag (40 marks)

> (i) Define each term in $\alpha_{T_{eff}}=\alpha+\alpha_s-\epsilon-\epsilon_T+l/R$. [6]
> (ii) Define the load factor $n$ and show that $l/R=nC_W\Phi$. [4]
> (iii) With $A=8$, $S=25$ m², $e=0.9$, $A_T=5$, $S_T=6$ m², $e_T=0.75$, $c=1.8$ m, $l=6$ m, $\alpha_s=-6.0^\circ$, $C_{M_0}=-0.01$, $h=0.50$, $h_0=0.25$, $\rho=1.225$ kg/m³, $m=1400$ kg, $V=60$ m/s, $g=9.81$ m/s², $C_{L_T}=2\pi\alpha_{T_{eff}}+3\eta$, $\gamma=0^\circ$, find the stick-fixed manoeuvre margin $H_m$. [10]
> (iv) How does a pilot experience a large $H_m$? [3]
> (v) Find the elevator angle $\eta$ for a trimmed pull-up with $R=600$ m. [10]
> (vi) Define the trim drag coefficient $C_{D_m}$ and calculate it for the aircraft of part (iii). [7]

### (i) Terms in the effective tail incidence [6 marks]

- $\alpha_{T_{eff}}$: the effective incidence of the tailplane, the angle between the tail chord line and the local flow it actually meets, which sets its lift through $C_{L_T}=2\pi\alpha_{T_{eff}}+a_2\eta+a_3\beta$.
- $\alpha$: the wing incidence, the angle between the wing chord (or zero-lift reference) and the free stream.
- $\alpha_s$: the tailplane setting angle, the fixed rigging angle of the tail chord relative to the wing chord (negative here, nose-down).
- $\epsilon$: the downwash angle at the tail produced by the wing's trailing vortices, $\epsilon=C_L/(\pi Ae)=\epsilon_\alpha(\alpha-\alpha_0)$, which reduces the tail incidence.
- $\epsilon_T$: the tail's own induced angle from its finite span, $\epsilon_T=C_{L_T}/(\pi A_Te_T)$.
- $l/R$: the extra tail incidence in curved flight. The aircraft pitches at $q=V/R$, so the tail, a distance $l$ behind, moves downwards at $ql$ relative to the CG and meets an extra upflow angle $ql/V=l/R$.

### (ii) Load factor and the pitch-rate term [4 marks]

The sheet writes the normal force balance in a pull-up of radius $R$ as $L^*=W\cos\gamma+mV^2/R$, that is $C_L^*=C_W(\cos\gamma+n)$, so in this course

$$
n\equiv\frac{V^2}{gR}
$$

is the centripetal acceleration in units of $g$, the increment above the 1-g value at the bottom of a level pull-up. (The conventional load factor is $L^*/W=\cos\gamma+n$.) With $C_W=mg/(\tfrac12\rho V^2S)$ and $\Phi=\rho Sl/(2m)$:

$$
nC_W\Phi=\frac{V^2}{gR}\times\frac{2mg}{\rho V^2S}\times\frac{\rho Sl}{2m}.
$$

Cancel $V^2$, $g$, $2m$ and $\rho S$:

$$
nC_W\Phi=\frac lR.
$$

For part (v): $n=60^2/(9.81\times600)=0.6116$, $C_W=0.24914$, $\Phi=0.065625$, and $nC_W\Phi=0.01000=6/600$.

### (iii) Stick-fixed manoeuvre margin [10 marks]

The wing and tail constants:

$$
Ae=7.2,\qquad C_{L_\alpha}=\frac{2\pi(7.2)}{9.2}=4.9173,\qquad\epsilon_\alpha=\frac{2}{9.2}=0.21739,
$$

$$
A_Te_T=3.75,\qquad k=\frac{2\pi(3.75)}{5.75}=4.0977,
$$

$$
K=\frac{S_Tl}{Sc}=\frac{6\times6}{25\times1.8}=0.8,\qquad s=\frac{6}{25}=0.24,\qquad\Phi=\frac{\rho Sl}{2m}=\frac{1.225\times25\times6}{2800}=0.065625.
$$

The manoeuvre tail slope:

$$
C_{L_{T\alpha}}=\frac{k(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{1-k\Phi s}=\frac{4.0977(0.78261+0.32270)}{1-4.0977\times0.065625\times0.24}=\frac{4.5292}{0.93546}=4.8417.
$$

Then

$$
C^*_{L_\alpha}=C_{L_\alpha}+sC_{L_{T\alpha}}=4.9173+0.24\times4.8417=6.0793,
$$

$$
H_m=h_0-h+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=0.25-0.50+0.8\times\frac{4.8417}{6.0793}=-0.25+0.63714=\boxed{0.387}.
$$

The straight-flight stick-fixed margin is $H=0.201$ (with $C_{L_{T\alpha}}=k(1-\epsilon_\alpha)=3.2069$), so pitch damping in the manoeuvre moves the manoeuvre point well aft, to $h_m=0.887$.

### (iv) What a large manoeuvre margin feels like [3 marks]

The elevator angle, and so the stick force, needed per $g$ of normal acceleration is proportional to the manoeuvre margin. A large $H_m$ therefore makes the aircraft heavy and sluggish in pitch: the pilot must pull hard and use a lot of elevator for a modest pull-up, may run out of elevator authority at forward CG (for example in the landing flare), and tires in sustained manoeuvres. A small $H_m$ gives light, sensitive controls and the risk of over-stressing the airframe.

### (v) Elevator angle in a pull-up of radius 600 m [10 marks]

**Assumptions.** At the bottom of the pull-up, $\gamma=0$; speed 60 m/s; $\alpha_0=0$ (not given); stick fixed, $\beta=0$.

The total lift coefficient:

$$
C_L^*=C_W(\cos\gamma+n)=0.24914(1+0.61162)=0.40152.
$$

The moment balance gives the tail lift:

$$
C_{L_T}=\frac{C_{M_0}+C_L^*(h-h_0)}{K}=\frac{-0.01+0.40152\times0.25}{0.8}=0.11298.
$$

The wing lift and incidence:

$$
C_L=C_L^*-sC_{L_T}=0.40152-0.24\times0.11298=0.37441,
$$

$$
\alpha=\frac{C_L}{C_{L_\alpha}}=\frac{0.37441}{4.9173}=0.07614\ \text{rad}\ (4.36^\circ).
$$

The effective tail incidence, now with the pitch-rate term $l/R=0.01$:

$$
\alpha_{T_{eff}}=(1-\epsilon_\alpha)\alpha+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}+\frac lR,
$$

$$
\alpha_{T_{eff}}=0.78261(0.07614)-0.10472-\frac{0.11298}{\pi(3.75)}+0.01,
$$

$$
\alpha_{T_{eff}}=0.05959-0.10472-0.00959+0.01=-0.04472\ \text{rad}\ (-2.56^\circ).
$$

The elevator:

$$
\eta=\frac{C_{L_T}-2\pi\alpha_{T_{eff}}}{3}=\frac{0.11298+0.28099}{3}=0.13132\ \text{rad}=\boxed{7.52^\circ}.
$$

In level flight at the same speed the same steps give $\eta=10.02^\circ$, so the pull-up needs $2.50^\circ$ more up-elevator, about $4.1^\circ$ per unit $n$.

### (vi) Trim drag coefficient [7 marks]

The **trim drag coefficient** $C_{D_m}$ is the extra induced drag caused by splitting the total lift between wing and tailplane, measured against the induced drag the wing alone would have if it carried all of it ($C^*_{D_i}=C_L^{*2}/(\pi Ae)$). With $x=C_{L_T}S_T/(C_L^*S)$ the tail's share and $\sigma=SAe/(S_TA_Te_T)+1$ (derivation in [[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2(b)]]):

$$
C_{D_m}=\frac{C_L^2}{\pi Ae}+\frac{S_T}{S}\frac{C_{L_T}^2}{\pi A_Te_T}-C^*_{D_i}=C^*_{D_i}\,x\left(\sigma x-2\right).
$$

For the aircraft of part (iii) in level flight at 60 m/s ($C_L^*=C_W=0.24914$):

$$
C_{L_T}=\frac{-0.01+0.24914\times0.25}{0.8}=0.065357,\qquad x=\frac{0.065357\times6}{0.24914\times25}=0.062959,
$$

$$
\sigma=\frac{25\times7.2}{6\times3.75}+1=8+1=9,\qquad C^*_{D_i}=\frac{0.24914^2}{\pi(7.2)}=0.0027442,
$$

$$
C_{D_m}=0.0027442\times0.062959\times(9\times0.062959-2)=0.0027442\times0.062959\times(-1.43337),
$$

$$
\boxed{C_{D_m}=-2.48\times10^{-4}.}
$$

It is negative: with the CG well aft ($h=0.5$) the tail lifts upwards and relieves the wing, so the pair has less induced drag than the wing alone. The minimum possible is $-C^*_{D_i}/\sigma=-3.05\times10^{-4}$, at $x=1/\sigma$, which would need $h_{opt}=0.661$. A direct check, $C_L^2/(\pi Ae)+sC_{L_T}^2/(\pi A_Te_T)-C^*_{D_i}$, gives the same $-2.48\times10^{-4}$.

---

## Q2. Longitudinal modes and handling qualities (30 marks)

> The longitudinal model of a UAV at 60 m/s is the matrix of 2013-14 Q3, with eigenvalues $\lambda_{1,2}=-3.154\pm3.358i$ and $\lambda_{3,4}=-0.021\pm0.207i$.
> (i) Identify the phugoid and SPO eigenvalues, comment on stability and find $\omega_n$ and $\zeta$ for each. [8]
> (ii) Stating all assumptions, simplify the matrix to estimate the SPO and compute its eigenvalue. [8]
> (iii) Derive Lanchester's approximation, stating assumptions, and calculate $\omega_n$. [8]
> (iv) Discuss the handling quality requirements of the phugoid and SPO. [6]

### (i) Identifying the modes [8 marks]

The SPO is the fast, well-damped pair, the phugoid the slow, lightly damped pair ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#3. Damping ratio and natural frequency (6.13–6.16)|6.1 §3]]: $\omega_n=|\lambda|$, $\zeta=-\operatorname{Re}\lambda/|\lambda|$).

| Mode | $\lambda$ | $\omega_n$ (rad/s) | $\zeta$ | Period (s) | Halving time (s) |
|---|---|---:|---:|---:|---:|
| SPO | $-3.154\pm3.358i$ | 4.607 | 0.685 | 1.87 | 0.22 |
| Phugoid | $-0.021\pm0.207i$ | 0.208 | 0.101 | 30.4 | 33.0 |

For example, $\omega_n=\sqrt{3.154^2+3.358^2}=\sqrt{21.224}=4.607$ and $\zeta=3.154/4.607=0.685$. Both real parts are negative, so both modes are stable: the SPO is almost dead-beat, while the phugoid decays only slowly, losing half its amplitude in about one cycle. The SPO is 22 times faster than the phugoid, which is why each can be approximated separately.

### (ii) SPO approximation [8 marks]

**Assumptions.** The speed does not change over the short period, so $u=\dot u=0$ and the $X$ equation is dropped; level trim, so $\theta$ does not enter the $Z$ and $M$ equations and the $\dot\theta$ equation is not needed; the remaining derivatives are those printed (the matrix is already in $\dot{\mathbf x}=\mathbf A\mathbf x$ form). These are the SPO assumptions of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]].

$$
\frac{d}{dt}\begin{bmatrix}w\\q\end{bmatrix}=\begin{bmatrix}-2.3&60\\-0.2&-4.0\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix},
$$

$$
\det\begin{bmatrix}-2.3-\lambda&60\\-0.2&-4.0-\lambda\end{bmatrix}=(2.3+\lambda)(4.0+\lambda)+12=0,
$$

$$
\lambda^2+6.3\lambda+21.2=0,
$$

$$
\lambda=-3.15\pm i\sqrt{21.2-9.9225}=\boxed{-3.150\pm3.358i},
$$

with $\omega_n=4.604$ rad/s and $\zeta=0.684$, within 0.1 % of the full model. Full working and the comparison table are in [[SESA2025 Past Paper 2013-14 - Solutions#Q3. Longitudinal modes, SPO approximation and Lanchester's phugoid (25 marks)|2013-14 Q3(b)]].

### (iii) Lanchester's approximation [8 marks]

**Assumptions.** Total energy is constant (thrust cancels drag, nothing is dissipated); incidence, and so $C_L$, stay at the trim value; the path is close to horizontal so lift is vertical; $h$ is measured from the trim height where the speed is $U_\infty$.

Energy:

$$
\tfrac12mU^2+mgh=\tfrac12mU_\infty^2\quad\Rightarrow\quad U^2=U_\infty^2-2gh.
$$

Lift at constant $C_L$, using $\tfrac12\rho U_\infty^2SC_L=mg$:

$$
L=\tfrac12\rho SC_L\left(U_\infty^2-2gh\right)=mg-\rho SC_Lg\,h.
$$

Vertical motion:

$$
m\ddot h=L-mg=-\rho SC_Lg\,h.
$$

With $C_L=2mg/(\rho U_\infty^2S)$, $\rho SC_Lg=2mg^2/U_\infty^2$, so

$$
\ddot h+\frac{2g^2}{U_\infty^2}h=0,\qquad\boxed{\omega_n=\frac{\sqrt2\,g}{U_\infty}=\frac{1.4142\times9.81}{60}=0.231\ \text{rad/s}},
$$

a period of 27.2 s and $\zeta=0$. The full model gives 0.208 rad/s (11 % lower). Lanchester gets the frequency roughly right from energy alone but cannot predict the damping. The constant-incidence assumption is what makes $\theta\approx\gamma$ in the phugoid ([[SESA2025 Past Paper 2013-14 - Solutions#Q3. Longitudinal modes, SPO approximation and Lanchester's phugoid (25 marks)|2013-14 Q3(c)]] has the mode-shape figure).

### (iv) Handling-quality requirements [6 marks]

The SPO governs how the aircraft answers the stick in pitch and how it rides gusts, so it must be well damped and neither too fast nor too slow. Light damping gives overshoot, a bobbing ride in turbulence and a risk of pilot-induced oscillation; heavy damping or a low frequency makes the response sluggish; a very high frequency makes it twitchy. MIL-F-8785C (Level 1) asks for $0.35\le\zeta_{sp}\le1.30$ in precision and terminal phases (0.30 to 2.0 in cruise), with $\omega_{sp}$ inside limits that scale with the normal acceleration per unit incidence; CS-25/FAR-25 requires the short period to be heavily damped with the primary controls free and fixed. This aircraft's $\zeta=0.68$ is comfortably inside.

The phugoid is so slow that a pilot corrects it without noticing, so the requirement is light: Level 1 needs only $\zeta_{ph}\ge0.04$, Level 2 $\zeta_{ph}\ge0$, and Level 3 even accepts an unstable phugoid whose time to double is at least 55 s. It matters for workload in long instrument flight and for autopilot design (height and speed hold). This aircraft's $\zeta=0.10$ meets Level 1.

---

## Q3. Coordinated turn, Dutch roll and yaw damping (30 marks)

> The lateral-directional model is the matrix and control matrix of 2013-14 Q4 (rows $\dot v,\dot p,\dot r,\dot\phi$; inputs $\delta_R,\delta_A$).
> (i) The aircraft flies level at 50 m/s in a coordinated turn to the right of radius $R$ with bank angle 0.2 rad. Find $\delta_R$, $\delta_A$ and $R$. [9]
> (ii) Simplify the matrix to a Dutch roll approximation, stating the assumptions, and find the frequency $\omega$ and half-life $t_{1/2}$. [9]
> (iii) Give suitable control inputs to excite the Dutch roll in a flight test and explain the mode's essential characteristics. [6]
> (iv) Derive the dimensionless derivative $N_r$ in terms of the fin area $S_F$, fin arm $l_F$ and other parameters. What role does it play in the Dutch roll? [6]

### (i) Turn radius and controls for a bank of 0.2 rad [9 marks]

**Assumptions.** Steady, coordinated, constant bank: all derivatives zero, $v=p=0$; body yaw rate equal to the turn rate, $r=V/R$; linear model.

The three non-trivial rows are

$$
0=-50r+9.81\phi+2.5\delta_R,\qquad0=-2.0r+1.0\delta_R-3.0\delta_A,\qquad0=-0.80r-0.5\delta_R.
$$

The yaw row gives $\delta_R=-1.6r$. Substitute into the side-force row with $\phi=0.2$:

$$
0=-50r+1.962-4.0r\quad\Rightarrow\quad r=\frac{1.962}{54}=0.036333\ \text{rad/s}.
$$

Then

$$
R=\frac Vr=\frac{50}{0.036333}=\boxed{1376\ \text{m}},
$$

$$
\delta_R=-1.6(0.036333)=\boxed{-0.0581\ \text{rad}\ (-3.33^\circ)},
$$

$$
\delta_A=\frac{-2.0r+\delta_R}{3.0}=\frac{-0.07267-0.05813}{3.0}=\boxed{-0.0436\ \text{rad}\ (-2.50^\circ)}.
$$

The point-mass relation $\tan\phi=V^2/(gR)$ would give $R=1257$ m; the rudder side force, which points out of the turn, makes the model's turn about 9 % wider at the same bank.

### (ii) Dutch roll approximation [9 marks]

**Assumptions.** The Dutch roll is treated as a yawing and sideslipping oscillation with no roll: $p=\phi=0$, the $\dot p$ and $\dot\phi$ rows are dropped, and the roll terms vanish from the $\dot v$ and $\dot r$ rows; controls fixed.

$$
\frac{d}{dt}\begin{bmatrix}v\\r\end{bmatrix}=\begin{bmatrix}-0.26&-50\\0.09&-0.80\end{bmatrix}\begin{bmatrix}v\\r\end{bmatrix}.
$$

The characteristic equation:

$$
(-0.26-\lambda)(-0.80-\lambda)-(-50)(0.09)=0,
$$

$$
\lambda^2+1.06\lambda+0.208+4.5=0,
$$

$$
\lambda^2+1.06\lambda+4.708=0,
$$

$$
\lambda=-0.53\pm i\sqrt{4.708-0.2809}=-0.53\pm2.104i.
$$

So

$$
\omega=\boxed{2.10\ \text{rad/s}}\ (T=2.99\ \text{s}),\qquad t_{1/2}=\frac{\ln2}{0.53}=\boxed{1.31\ \text{s}},
$$

with $\omega_n=2.170$ rad/s and $\zeta=0.244$. The full $4\times4$ matrix has its Dutch roll at $-0.352\pm2.335i$ ($T=2.69$ s, $t_{1/2}=1.97$ s): the approximation is 10 % low in frequency and overestimates the damping by half, because it leaves out the roll that the dihedral effect ($L_v=-0.31$) couples into the motion. (The eigenvalues printed with this matrix in 2013-14 Q4, $-1.338\pm2.223i$, do not belong to it.)

### (iii) Exciting the Dutch roll in flight test [6 marks]

A rudder doublet is the standard input: a sharp rudder deflection one way, then the other, then centred, each lasting about half a Dutch roll period (here about 1.5 s per half), which puts the input energy near the mode's frequency while exciting little spiral or roll subsidence. A single rudder pulse or a step-and-release also works, and an aileron doublet or a release from a steady-heading sideslip are alternatives. After the input the controls are held fixed (or released, for the controls-free mode) and sideslip, yaw rate, roll rate and bank are recorded; period and decay give $\omega_n$ and $\zeta$.

The mode itself is a lightly damped oscillation in yaw and sideslip with coupled roll. The fin's weathercock stiffness swings the nose back and forth across the flight path; each sideslip rolls the aircraft through the dihedral effect, roll lagging yaw, so the aircraft wags its nose and rocks its wings out of phase and the wingtip traces an ellipse. The period is a few seconds; damping comes mainly from the fin through $N_r$. Strong dihedral or sweep and low directional stiffness make it worse, and a yaw damper is often fitted.

### (iv) The yaw-damping derivative [6 marks]

**Assumptions.** The fin, of area $S_F$ and lift slope $a_F$, has its aerodynamic centre a distance $l_F$ behind the CG; the fin's contribution dominates $N_r$ (wing and fuselage terms neglected); small angles; sidewash at the fin neglected.

When the aircraft yaws nose to starboard at rate $r$, the fin swings to port at speed $rl_F$. Relative to the fin the air then arrives from the port side, at an extra angle

$$
\Delta\alpha_F=\frac{rl_F}{V}.
$$

The fin side force (to starboard) is

$$
Y_F=\tfrac12\rho V^2S_Fa_F\,\frac{rl_F}{V}=\tfrac12\rho VS_Fa_Fl_F\,r.
$$

It acts $l_F$ behind the CG, so it yaws the nose to port, opposing $r$:

$$
N_F=-l_FY_F=-\tfrac12\rho VS_Fa_Fl_F^2\,r\quad\Rightarrow\quad\mathring N_r=\frac{\partial N}{\partial r}=-\tfrac12\rho VS_Fa_Fl_F^2.
$$

Non-dimensionalise with the lateral reference $\tfrac12\rho VSb^2$ (the same as for $L_p$):

$$
N_r=\frac{\mathring N_r}{\tfrac12\rho VSb^2}=-a_F\frac{S_Fl_F^2}{Sb^2}=\boxed{-a_F\,V_F\,\frac{l_F}{b}},\qquad V_F=\frac{S_Fl_F}{Sb},
$$

with $V_F$ the fin volume ratio. $N_r$ grows with the square of the fin arm.

$N_r$ is the yaw damping, the main source of Dutch roll damping: in the approximation of part (ii), $2\zeta\omega_n=-(n_r+y_v)=0.80+0.26$, so $N_r$ supplies three-quarters of the damping, while $N_v$ sets the frequency. A larger fin or longer tail arm raises both, and a yaw damper adds artificial $N_r$ through the rudder.

---

## Paper slips and ambiguities

- Q1(v). No zero-lift angle is given; $\alpha_0=0$ is used. A non-zero $\alpha_0$ would raise $\alpha$ and $\alpha_{T_{eff}}$ by $\alpha_0$ and change $\eta$ by $-2\pi\alpha_0/3$.
- Q1(vi). "The aircraft data in part (iii)" is taken as level flight at 60 m/s ($n=0$); in the 600 m pull-up of part (v) the same formula gives $C_{D_m}=-6.70\times10^{-4}$.
- Q1(ii). The sheet's $n=V^2/(gR)$ is the incremental normal acceleration, not the conventional load factor $L/W$; both are given above.
- Q3. The matrix is that of 2013-14 Q4, whose printed eigenvalues are wrong; no eigenvalues are printed here, and the comparison in (ii) uses the computed ones.
