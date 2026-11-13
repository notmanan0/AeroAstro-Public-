---
title: "SESA2025 Past Paper 2022-23 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, trim, static-stability, neutral-point, drag-polar, dihedral, tail-setting, static-margin, body-axes, linearisation, phugoid, short-period, roll-subsidence, dutch-roll, spiral, directional-stability]
paper: "2022-23"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]", "[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]", "[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]", "[[SESA3047 5.1 - State-Space Form and Linearisation]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-202223-02-SESA2025.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# SESA2025 Past Paper 2022-23 - Solutions

> [!abstract] Paper info
> 2022-23 Semester 2 examination (2 h, on campus), four questions of 25 marks, all compulsory. The equations sheet has a Part A (static stability in the notation of [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability|SESA2022 T6]]) and a Part B ($\lambda=\sigma\pm j\omega$, $\omega_n=\sqrt{\sigma^2+\omega^2}$, $\zeta=-\sigma/\omega_n$, $\omega=2\pi f$, $T=2\pi/\omega$, $t_{1/2}=\ln0.5/\sigma$, $t_2=\ln2/\sigma$). Q1 and Q2 are static stability and performance; Q3 is the equations of motion and the longitudinal modes; Q4 is roll, directional stability and the lateral modes, which SESA3047 lectures from Thu 19 Nov. All numbers were checked in Python with $g=9.81$ m/s².

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Trim equations; propeller range and $C_{D_0}$; static stability and the neutral point; anhedral in sideslip | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability\|SESA2022 T6]], [[SESA1015 M05 - Minimum Drag, Power and Performance Curves\|SESA1015 M05]], [[SESA1015 M07 - Propeller Aircraft Range and Endurance\|M07]], [[Lateral and Directional Stability]] |
| 2 | 25 | Tail setting for trim in a descent, elevator to make up a limited stabiliser; static margin of a UAV with a larger tail | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Solution algorithm for trim problems\|T6 §2]], [[Neutral Point and Static Margin]] |
| 3 | 25 | Body axes, linearisation, $w$ and $\alpha$, longitudinal quartic, phugoid parameters and mode shape | [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion\|SESA2027 A1]], [[SESA3047 5.1 - State-Space Form and Linearisation\|5.1]], [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation\|6.1]]; phugoid physics in [[Phugoid Mode]] and §6.6, lectured Mon 16 Nov |
| 4 | 25 | 1D roll equation, $\mathring N_v$, lateral quartic, Dutch roll | Not yet lectured: Chapter 6 §§6.7–6.10 ([[Lecture Notes - Chapter 6.pdf]]), lectured from Thu 19 Nov; background in [[Lateral and Directional Stability]] |

---

## Q1. Trim, range, static stability and dihedral (25 marks)

> (i) Sketch the forces and moments on a conventional aircraft in straight level flight (forces along the path may be omitted); derive the dimensional equilibrium equations normal to the path and for moments about the CG; derive the non-dimensional force equation, justifying the normalisation of the tail lift. [5]
> (ii) A propeller aircraft flies at its maximum-range speed ($d=1$). Use a sketch of the drag polar to show how the optimal speed changes when $C_{D_0}$ is reduced. [6]
> (iii) Define a statically stable system in general and for longitudinal static stability, with diagrams. Define the neutral point and explain why it moves aft when the tailplane area is increased. [8]
> (iv) With a diagram, show how anhedral produces lateral instability when the aircraft sideslips. [6]

### (i) Equilibrium equations [5 marks]

![[amc_pp_202223_q1_forces_moments.png|900]]

The wing lift $L$ acts at the wing aerodynamic centre, at $h_0c$ from the datum, together with the wing's zero-lift moment $M_0$ (constant about the AC). The tail lift $L_T$ acts at the tail AC, a distance $l$ behind the wing AC, and the weight acts at the CG, at $hc$. Thrust and drag are taken to act through the CG, and the tailplane is symmetric, so its own moment about its AC is zero.

Forces normal to the flight path, level flight:

$$
L+L_T-W=0.
$$

Moments about the CG, nose-up positive. With $h>h_0$ the wing lift acts $(h-h_0)c$ ahead of the CG (nose-up), and the tail lift acts $l-(h-h_0)c$ behind it (nose-down):

$$
M_0+L(h-h_0)c-L_T\left[l-(h-h_0)c\right]=0.
$$

Collect the $(h-h_0)c$ terms:

$$
M_0+(L+L_T)(h-h_0)c-L_Tl=0.
$$

For the non-dimensional force equation, the tail lift is written with the tail's own area, $L_T=\tfrac12\rho V^2S_TC_{L_T}$, so that $C_{L_T}$ is a property of the tail surface, comparable with the wing's $C_L$ and given by the same lifting-line expressions with $A_T$ and $e_T$. The wing lift and the weight use the wing area. Divide the force equation by $\tfrac12\rho V^2S$:

$$
\boxed{C_{L^*}=C_L+C_{L_T}\frac{S_T}{S}=C_W},\qquad C_W=\frac{W}{\tfrac12\rho V^2S}.
$$

The factor $S_T/S$ converts the tail coefficient to the common reference area. The tail is assumed to see the free-stream dynamic pressure. Dividing the moment equation by $\tfrac12\rho V^2Sc$ in the same way gives $C_{M_0}+C_{L^*}(h-h_0)-C_{L_T}K=0$ with $K=S_Tl/Sc$.

### (ii) Maximum-range speed and the zero-lift drag [6 marks]

For a propeller aircraft the range is $R=(\eta_p/c)(L/D)\ln(W_0/W_1)$ ([[SESA1015 M07 - Propeller Aircraft Range and Endurance|SESA1015 M07]]), so maximum range is flown at maximum $L/D$ ($d=1$ on the equations sheet). With the parabolic polar $C_D=C_{D_0}+KC_L^2$, maximum $L/D$ is the point where a line from the origin touches the polar ([[SESA1015 M05 - Minimum Drag, Power and Performance Curves|SESA1015 M05]]):

$$
C_L^\star=\sqrt{\frac{C_{D_0}}{K}},\qquad C_D^\star=2C_{D_0},\qquad\left(\frac LD\right)_{\max}=\frac{1}{2\sqrt{KC_{D_0}}}.
$$

The speed follows from $W=\tfrac12\rho V^2SC_L^\star$:

$$
V^\star=\sqrt{\frac{2W}{\rho S}}\left(\frac{K}{C_{D_0}}\right)^{1/4}.
$$

![[amc_pp_202223_q1_drag_polar_cd0.png|900]]

Reducing $C_{D_0}$ shifts the polar to the left. The tangent from the origin becomes steeper (higher $L/D$) and touches the new polar at a lower $C_L$, so the optimum speed rises as $C_{D_0}^{-1/4}$. In the sketch $C_{D_0}$ falls from 0.025 to 0.015 with $K=0.04$: $C_L^\star$ falls from 0.79 to 0.61, the speed rises by $(0.025/0.015)^{1/4}=1.136$, i.e. 13.6 %, and $(L/D)_{\max}$ rises from 15.8 to 20.4.

### (iii) Static stability and the neutral point [8 marks]

A system is statically stable if, when it is disturbed from equilibrium, the forces and moments it generates initially tend to return it towards equilibrium. Static stability concerns this initial tendency only, not the subsequent motion (which is dynamic stability). A ball in a bowl is stable, on a flat surface neutral, on a hill unstable.

For an aircraft in longitudinal trim, a disturbance that raises the angle of attack ($\Delta\alpha>0$) must produce a nose-down moment about the CG:

$$
\frac{dC_{M_{CG}}}{d\alpha}<0,
$$

and for the aircraft to trim at a useful positive $\alpha$, $C_{M_{CG}}$ must be positive at zero lift.

![[amc_pp_202223_q1_static_stability.png|900]]

Differentiating the moment equation, $dC_{M_{CG}}/d\alpha=C_{L^*_\alpha}(h-h_0)-KC_{L_{T,\alpha}}$. The neutral point $h_n$ is the CG position at which this slope is zero, so the aircraft is neutrally stable:

$$
h_n=h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad\frac{dC_{M_{CG}}}{d\alpha}=-C_{L^*_\alpha}(h_n-h).
$$

It is the aerodynamic centre of the whole aircraft: the point about which the total pitching moment does not change with $\alpha$. The CG must lie ahead of it.

Write $x=S_T/S$. Then $K=xl/c$ and $C_{L^*_\alpha}=C_{L_\alpha}+xC_{L_{T,\alpha}}$, so

$$
h_n-h_0=\frac lc\,\frac{xC_{L_{T,\alpha}}}{C_{L_\alpha}+xC_{L_{T,\alpha}}}.
$$

Differentiate with respect to $x$:

$$
\frac{d h_n}{dx}=\frac lc\,\frac{C_{L_{T,\alpha}}\left(C_{L_\alpha}+xC_{L_{T,\alpha}}\right)-xC_{L_{T,\alpha}}^2}{\left(C_{L_\alpha}+xC_{L_{T,\alpha}}\right)^2}=\frac lc\,\frac{C_{L_\alpha}C_{L_{T,\alpha}}}{\left(C_{L_\alpha}+xC_{L_{T,\alpha}}\right)^2}>0.
$$

So a larger tailplane moves the neutral point aft. Physically, the lift increment from a gust acts at the neutral point, a lift-weighted average of the wing AC and the tail AC; enlarging the tail puts more of that increment at the tail, far aft, and pulls the average backwards. For the UAV of Q2(ii), 15 % more tail area moves $h_n$ from $0.794$ to $0.852$.

### (iv) Anhedral in sideslip [6 marks]

![[amc_pp_202223_q1_anhedral_sideslip.png|900]]

Take a sideslip to starboard, $v>0$, so the air arrives from the right. Each wing panel inclined at the dihedral angle $\Gamma$ sees a component $v\sin\Gamma$ of the sideslip normal to its surface. With dihedral ($\Gamma>0$) this component flows up through the leading (starboard) wing and raises its incidence, giving a rolling moment that lifts that wing and rolls the aircraft away from the sideslip: $L_v<0$, stable. With anhedral ($\Gamma<0$) the sign reverses: the starboard wing's incidence falls by about $v|\Gamma|/V$ and the port wing's rises, so the aircraft rolls towards the starboard wing, $L_v>0$. The extra bank tilts the lift vector to starboard, which increases the sideslip to starboard, which increases the rolling moment: the disturbance feeds itself and the aircraft is laterally unstable. Anhedral is used only on aircraft whose high wing or sweep already gives too much lateral stability.

---

## Q2. Tail setting for trim, and the static margin of a UAV (25 marks)

> (i) A civil aircraft ($a_0=a_1=2\pi$ rad⁻¹, $a_2=2.9$ rad⁻¹, $e=0.92$, $e_T=0.90$, $A=11$, $A_T=8$, $S=90$ m², $S_T=10$ m², $h=0.27$, $h_0=0.22$, $l=34$ m, $c=4.8$ m, $m=120\,000$ kg, $C_{M_0}=-0.2$, $\alpha_0=-7^\circ$, $\rho=1.0$ kg/m³) descends steadily at $\gamma=-8^\circ$ and 192 m/s. Its tail lift is $C_{L_T}=a_1(\alpha+\alpha_s-\epsilon-\epsilon_T)+a_2\eta$. Find the stabiliser setting that trims it with $\eta=0$. The stabiliser can only reach $-1^\circ$: find the additional elevator deflection needed. [12]
> (ii) A UAV ($a_0=a_1=2\pi$ rad⁻¹, $e=0.8$, $e_T=0.7$, $A=13.6$, $A_T=9$, $S=3.4$ m², $S_T=0.31$ m², $l=3.2$ m, $c=0.5$ m, $h=0.57$, $h_0=0.38$) must have a stick-fixed static margin of at least 0.25. (a) Check the preliminary design. (b) Check a design with 15 % more tail area, whose CG moves aft by 2 % of the MAC. [13]

### (i) Stabiliser setting and elevator [12 marks]

Follow the trim algorithm of [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Solution algorithm for trim problems|T6 §2]]. Angles are in radians; $\epsilon=\epsilon_\alpha(\alpha-\alpha_0)$ is the wing downwash at the tail and $\epsilon_T=C_{L_T}/\pi A_Te_T$ the tail's own induced angle.

Weight and total lift coefficients:

$$
\tfrac12\rho V^2=\tfrac12\times1.0\times192^2=18\,432\ \text{Pa},
$$

$$
C_W=\frac{120\,000\times9.81}{18\,432\times90}=\frac{1\,177\,200}{1\,658\,880}=0.709635,
$$

$$
C_{L^*}=C_W\cos\gamma=0.709635\times\cos(-8^\circ)=0.702729.
$$

Tail volume:

$$
K=\frac{S_Tl}{Sc}=\frac{10\times34}{90\times4.8}=\frac{340}{432}=0.787037.
$$

Tail lift from the moment equation:

$$
C_{L_T}=\frac{C_{M_0}+C_{L^*}(h-h_0)}{K}=\frac{-0.2+0.702729\times0.05}{0.787037}=\frac{-0.164864}{0.787037}=-0.209474.
$$

Wing lift:

$$
C_L=C_{L^*}-C_{L_T}\frac{S_T}{S}=0.702729+0.209474\times\frac{10}{90}=0.726004.
$$

Wing lift-curve slope and incidence:

$$
C_{L_\alpha}=2\pi\frac{\pi\times11\times0.92}{\pi\times11\times0.92+2\pi}=2\pi\times\frac{10.12}{12.12}=5.246356\ \text{rad}^{-1},
$$

$$
\alpha-\alpha_0=\frac{0.726004}{5.246356}=0.138383\ \text{rad}=7.929^\circ,
$$

$$
\alpha=-7^\circ+7.929^\circ=0.929^\circ=0.016210\ \text{rad}.
$$

Downwash at the tail:

$$
\epsilon_\alpha=\frac{C_{L_\alpha}}{\pi Ae}=\frac{5.246356}{\pi\times10.12}=0.165017,
$$

$$
\epsilon=0.165017\times0.138383=0.022835\ \text{rad}.
$$

Tail induced angle:

$$
\epsilon_T=\frac{C_{L_T}}{\pi A_Te_T}=\frac{-0.209474}{\pi\times8\times0.90}=-0.009261\ \text{rad}.
$$

With $\eta=0$ the tail lift equation gives $\alpha+\alpha_s-\epsilon-\epsilon_T=C_{L_T}/a_1$:

$$
\frac{C_{L_T}}{a_1}=\frac{-0.209474}{2\pi}=-0.033339\ \text{rad},
$$

$$
\alpha_s=\frac{C_{L_T}}{a_1}-\alpha+\epsilon+\epsilon_T=-0.033339-0.016210+0.022835-0.009261,
$$

$$
\boxed{\alpha_s=-0.035975\ \text{rad}=-2.06^\circ}.
$$

The CG and $C_{L^*}$ are unchanged, so the trimmed $C_{L_T}$ is unchanged, and so are $\alpha$, $\epsilon$ and $\epsilon_T$. If the stabiliser stops at $\alpha_s=-1^\circ$, the elevator must provide the tail lift that the missing $-1.06^\circ$ of setting would have given:

$$
a_1\left(\alpha_{s,\text{avail}}-\alpha_{s,\text{req}}\right)+a_2\eta=0,
$$

$$
\eta=-\frac{a_1}{a_2}\left(\alpha_{s,\text{avail}}-\alpha_{s,\text{req}}\right)=-\frac{2\pi}{2.9}\left(-0.017453+0.035975\right)=-\frac{2\pi}{2.9}\times0.018521,
$$

$$
\boxed{\eta=-0.04013\ \text{rad}=-2.30^\circ}\quad(\text{trailing edge up}).
$$

The elevator angle is larger than the setting it replaces because the elevator is less effective than the whole stabiliser ($a_2/a_1=0.46$).

### (ii) Static margin of the UAV [13 marks]

The stick-fixed static margin is

$$
H_s=h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad C_{L_{T,\alpha}}=k(1-\epsilon_\alpha),\qquad C_{L^*_\alpha}=C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}.
$$

Wing ($\pi Ae=\pi\times10.88$):

$$
C_{L_\alpha}=2\pi\times\frac{10.88}{12.88}=5.30754\ \text{rad}^{-1},\qquad\epsilon_\alpha=\frac{5.30754}{\pi\times10.88}=0.15528.
$$

Tail ($\pi A_Te_T=\pi\times6.3$):

$$
k=2\pi\times\frac{6.3}{8.3}=4.76916\ \text{rad}^{-1},\qquad C_{L_{T,\alpha}}=4.76916\times(1-0.15528)=4.02861\ \text{rad}^{-1}.
$$

#### (a) Preliminary design

$$
K=\frac{0.31\times3.2}{3.4\times0.5}=0.58353,\qquad C_{L^*_\alpha}=5.30754+4.02861\times\frac{0.31}{3.4}=5.67485,
$$

$$
h_n=0.38+0.58353\times\frac{4.02861}{5.67485}=0.38+0.41425=0.79425,
$$

$$
H_s=0.79425-0.57=\boxed{0.224<0.25}.
$$

The team mate is right: the preliminary design misses the requirement by 0.026.

#### (b) Larger tail with the CG moved aft

With $S_T=1.15\times0.31=0.3565$ m² and $l$ (measured from the wing AC) unchanged:

$$
K=\frac{0.3565\times3.2}{3.4\times0.5}=0.67106,\qquad C_{L^*_\alpha}=5.30754+4.02861\times\frac{0.3565}{3.4}=5.72995,
$$

$$
h_n=0.38+0.67106\times\frac{4.02861}{5.72995}=0.38+0.47181=0.85181.
$$

The CG moves to $h=0.57+0.02=0.59$:

$$
H_s=0.85181-0.59=\boxed{0.262\ge0.25}.
$$

The modified design meets the requirement, with a margin of 0.012. The aft CG shift costs 0.02 of the 0.058 gained from the larger tail: without it $H_s$ would be 0.282.

---

## Q3. Equations of motion and the longitudinal modes (25 marks)

> (i) Why is a body-fixed coordinate system convenient for deriving the aircraft equations of motion? [4]
> (ii) Of the terms $I_{yy}\dot q$ and $I_{yy}qr$, which is set to zero in the linearisation? Explain both. [2]
> (iii) With a diagram, explain the relation between $w$ and $\alpha$. [2]
> (iv) The longitudinal quartic is $(\lambda^2+0.014\lambda+0.032)(\lambda^2+1.1\lambda+1.3)=0$. Calculate the eigenvalues and identify the SPO and phugoid. [4]
> (v) Phugoid: stable or not, frequency in Hz, half-life, $\omega_n$ in rad/s, damping factor. [4]
> (vi) Physical interpretation of the undamped natural frequency. [3]
> (vii) Plot $\theta$ and $\alpha$ when the phugoid alone is excited, annotated. [4]
> (viii) Why does $\alpha$ change much less than $\theta$ in the phugoid? [2]

### (i) Body-fixed axes [4 marks]

In axes fixed to the aircraft, the inertia tensor is constant, because the mass distribution does not move relative to the axes; in Earth axes it would change every time the aircraft rotated. The $x$–$z$ plane is a plane of symmetry, so $I_{xy}=I_{yz}=0$ and only $I_{xz}$ remains off the diagonal. The aerodynamic forces and moments depend on the motion relative to the aircraft ($u$, $v$, $w$, $\alpha$, $\beta$, $p$, $q$, $r$), and the engine thrust is fixed in the body, so both are naturally expressed in body axes. The on-board sensors (accelerometers, rate gyros) also measure body-axis quantities. The price is the extra $\boldsymbol\omega\times$ terms from differentiating in a rotating frame ([[Transport Theorem]]).

### (ii) Which term is linearised away [2 marks]

$I_{yy}qr$ (which appears in the rolling-moment equation, $(I_{zz}-I_{yy})qr$) is set to zero. In trimmed straight flight the trim rates are zero, so $q$ and $r$ are both small perturbations and their product is second order. $I_{yy}\dot q$ is retained: it is the pitching inertia times the pitch acceleration, first order in a single perturbation, and it is the left-hand side of the pitching-moment equation ([[SESA3047 5.1 - State-Space Form and Linearisation|5.1]]).

### (iii) w and the angle of attack [2 marks]

![[amc_pp_202223_q3_w_alpha_triangle.png|900]]

The velocity of the aircraft relative to the air, resolved in body axes, has components $u$ along $x$ and $w$ along $z$ (in the plane of symmetry). The angle of attack is the angle between the body $x$ axis and this velocity, so $\tan\alpha=w/u$. With $u\approx U_\infty$ and $\alpha$ small (in radians), $w\approx U_\infty\alpha$: a perturbation $w$ is a change of incidence $\Delta\alpha=w/U_\infty$.

### (iv) Eigenvalues and identification [4 marks]

$$
\lambda^2+1.1\lambda+1.3=0:\quad\lambda=\frac{-1.1\pm\sqrt{1.21-5.2}}{2}=\boxed{-0.55\pm0.9987j},
$$

$$
\lambda^2+0.014\lambda+0.032=0:\quad\lambda=\frac{-0.014\pm\sqrt{0.000196-0.128}}{2}=\boxed{-0.007\pm0.1787j}.
$$

The first pair is the SPO: larger roots, fast (period 6.3 s) and well damped ($\zeta=0.48$). The second is the phugoid: small roots, slow (period 35 s) and lightly damped ($\zeta=0.039$).

### (v) Phugoid parameters [4 marks]

Stable, since $\sigma=-0.007$ s⁻¹ is negative.

$$
\omega=0.17875\ \text{rad/s},\qquad f=\frac{\omega}{2\pi}=\boxed{0.0284\ \text{Hz}}\quad(T=35.2\ \text{s}),
$$

$$
t_{1/2}=\frac{\ln0.5}{\sigma}=\frac{-0.6931}{-0.007}=\boxed{99.0\ \text{s}},
$$

$$
\omega_n=\sqrt{0.032}=\boxed{0.1789\ \text{rad/s}},
$$

$$
\zeta=-\frac{\sigma}{\omega_n}=\frac{0.007}{0.17889}=\boxed{0.0391}.
$$

### (vi) Meaning of the undamped natural frequency [3 marks]

$\omega_n$ is the frequency at which the mode would oscillate if all its damping were removed: the square root of stiffness over inertia, $\sqrt{k/m}$ for a mass–spring system. It measures how strongly the restoring effect acts compared with the inertia resisting it, so a stiffer system responds faster. It is also the magnitude of the eigenvalue, $|\lambda|$, the distance of the pole from the origin; the actual oscillation runs at the damped frequency $\omega=\omega_n\sqrt{1-\zeta^2}$, which for the lightly damped phugoid is almost the same ($0.17875$ against $0.17889$ rad/s). For the phugoid the "stiffness" is gravity trading speed for height: Lanchester's estimate is $\omega_n\approx\sqrt2\,g/U_\infty$.

### (vii) Phugoid response [4 marks]

The plot uses the paper's phugoid eigenvalue and the F-4C phugoid mode shape of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]], scaled to a $2^\circ$ initial pitch.

![[amc_pp_202223_q3_phugoid_theta_alpha.png|900]]

Features to annotate: a slow, lightly damped oscillation of $\theta$ with period $T=2\pi/\omega=35.2$ s; an exponential envelope $e^{-0.007t}$ halving every 99 s; and an $\alpha$ trace that is almost flat (peak $0.19^\circ$ for $2^\circ$ of $\theta$). Speed and height (not plotted) oscillate in antiphase, with speed highest at the bottom of each cycle, and both are a quarter-cycle out of phase with $\theta$.

### (viii) Why the angle of attack barely changes [2 marks]

The phugoid is an exchange between kinetic and potential energy at almost constant incidence. Its period is long compared with the SPO, and the SPO's strong pitch stiffness ($M_w$) holds $\alpha$ at the value that balances the pitching moment throughout. The aircraft therefore follows its flight path like a car on a roller-coaster: as the path angle $\gamma$ rises and falls, the attitude $\theta=\gamma+\alpha$ follows it, and the change in lift that curves the path comes from the change in speed, not in $\alpha$.

---

## Q4. Roll, directional stability and the lateral modes (25 marks)

> (i) From the full lateral state-space equation, derive a 1D equation of motion for roll about $x$, with all other motion constrained, explaining why terms vanish. [3]
> (ii) What is the externally applied moment in this 1D equation? [1]
> (iii) What does $\mathring N_v$ represent, and what are its units? [3]
> (iv) Calculate the magnitude of $\mathring N_v$ from $N_v=\frac{S_F}{S}C_{L_{F,\alpha}}\frac{l_F}{b}$ with $S=10$ m², $S_F=2.5$ m², $V=200$ m/s, $b=9$ m, $\rho=0.6$ kg/m³, $C_{L_{F,\alpha}}=2\pi$ rad⁻¹, $c=3$ m, $l_F=2.4$ m. [3]
> (v) How can each of the three terms in $N_v$ be modified to increase it? [4]
> (vi) The lateral quartic is $(\lambda+1.8214)(\lambda+0.0049)(\lambda^2-0.6389\lambda+24.0541)=0$. Calculate the eigenvalues and identify the three modes. [6]
> (vii) Explain how the Dutch roll develops after an initial yaw perturbation such as a side gust. [5]

These lateral topics are Chapter 6 §§6.7–6.10 of the SESA3047 lecture notes, lectured from Thu 19 Nov.

### (i) One-degree-of-freedom roll [3 marks]

The lateral equation is

$$
\begin{bmatrix}m&0&0&0\\0&I_{xx}&-I_{xz}&0\\0&-I_{xz}&I_{zz}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot v\\\dot p\\\dot r\\\dot\phi\end{bmatrix}=\begin{bmatrix}\mathring Y_v&\mathring Y_p&\mathring Y_r-mU_\infty&mg\\\mathring L_v&\mathring L_p&\mathring L_r&0\\\mathring N_v&\mathring N_p&\mathring N_r&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}.
$$

With sideslip and yaw constrained, $v=\dot v=0$ and $r=\dot r=0$. Row 1 (side force) and row 3 (yawing moment) then describe the constraint forces and moments and are dropped. In row 2, $\mathring L_vv=0$ and $\mathring L_rr=0$, and the product-of-inertia term $-I_{xz}\dot r=0$, leaving

$$
\boxed{I_{xx}\dot p=\mathring L_pp},\qquad\dot\phi=p.
$$

The bank angle does not appear in the rolling-moment equation (it only enters the side force through $mg\phi$), so roll rate decays as $p=p_0e^{(\mathring L_p/I_{xx})t}$.

### (ii) The applied moment [1 mark]

The external moment is the aerodynamic rolling moment due to roll rate, the roll damping moment $\mathring L_pp$ (plus $\mathring L_{\delta_A}\delta_A$ if the ailerons are deflected): $I_{xx}\dot p=\sum L$.

### (iii) The derivative N_v [3 marks]

$\mathring N_v=\partial N/\partial v$ is the yawing moment per unit sideslip velocity: the directional (weathercock) stability derivative. A sideslip $v>0$ puts the fin at an incidence $v/V$; its side force, a distance $l_F$ behind the CG, yaws the nose towards the relative wind, so $\mathring N_v>0$ for a stable aircraft. Units: moment per velocity, N m/(m/s) = N s (kg m/s).

### (iv) Magnitude of the dimensional N_v [3 marks]

$$
N_v=\frac{S_F}{S}C_{L_{F,\alpha}}\frac{l_F}{b}=\frac{2.5}{10}\times2\pi\times\frac{2.4}{9}=0.41888.
$$

The dimensional derivative multiplies $v$ (reference $V$) and gives a moment (reference $\tfrac12\rho V^2Sb$), so

$$
\mathring N_v=N_v\times\tfrac12\rho VSb=0.41888\times\tfrac12\times0.6\times200\times10\times9=0.41888\times5400,
$$

$$
\boxed{\mathring N_v=2262\ \text{N s}}.
$$

> [!check] Directly from the fin
> Substituting $N_v$ into the scaling, $S$ and $b$ cancel: $\mathring N_v=\tfrac12\rho VS_FC_{L_{F,\alpha}}l_F=\tfrac12\times0.6\times200\times2.5\times2\pi\times2.4=2262$ N s. The chord $c=3$ m is not needed.

### (v) Increasing N_v [4 marks]

- $S_F/S$: increase the fin area. A larger fin, or a second fin, gives more side force per unit sideslip.
- $C_{L_{F,\alpha}}$: increase the fin's lift-curve slope, by a higher effective fin aspect ratio (taller fin, or an end-plate effect from a T-tail or a tailplane at the fin root), less sweep, or by keeping the fin out of the fuselage wake and sidewash at high incidence.
- $l_F/b$: increase the fin arm, by mounting the fin further aft on a longer fuselage or tail boom (or sweeping the fin back, which moves its aerodynamic centre aft).

Reducing $S$ or $b$ would raise the dimensionless coefficient, but as the check above shows, the dimensional $\mathring N_v$ depends only on the fin.

### (vi) Eigenvalues and the three modes [6 marks]

$$
\lambda_1=\boxed{-1.8214\ \text{s}^{-1}},\qquad\lambda_2=\boxed{-0.0049\ \text{s}^{-1}},
$$

$$
\lambda^2-0.6389\lambda+24.0541=0:\quad\lambda_{3,4}=\frac{0.6389\pm\sqrt{0.40819-96.2164}}{2}=\boxed{0.3194\pm4.8941j}.
$$

- $-1.8214$: roll subsidence, the large real root (time constant 0.55 s, $t_{1/2}=0.38$ s). Stable.
- $-0.0049$: spiral mode, the real root nearest zero ($t_{1/2}=141$ s). Stable, slowly convergent.
- $0.3194\pm4.8941j$: Dutch roll, the oscillatory pair, with $\omega_n=\sqrt{24.0541}=4.905$ rad/s, period $1.28$ s and $\zeta=-0.6389/(2\times4.905)=-0.065$. The positive real part makes it unstable, doubling in $\ln2/0.3194=2.17$ s.

### (vii) Development of the Dutch roll [5 marks]

A side gust yaws the aircraft, say nose to port, so the aircraft sideslips to starboard ($v>0$, relative wind from the right). Directional stability ($\mathring N_v>0$) from the fin yaws the nose back to starboard towards the relative wind. Because of the yaw inertia $I_{zz}$, the nose swings past the wind direction, producing a sideslip to port, which reverses the fin's restoring moment; the nose oscillates in yaw. Each sideslip also produces a rolling moment through the dihedral effect ($\mathring L_v<0$), rolling the aircraft away from the sideslip, and the yaw rate rolls it further through $\mathring L_r$ (the advancing wing is faster). The roll lags the yaw, so the aircraft yaws, rolls and sideslips together with the wingtips tracing ellipses. Yaw damping ($\mathring N_r$, mainly the fin) and side force ($\mathring Y_v$) damp the motion; strong dihedral effect relative to directional stability weakens the damping, which is why the Dutch roll of (vi) diverges.

---

## Paper slips and ambiguities

- Q2(i). The tail-lift model includes $\epsilon_T$, the tail's own induced angle, which is read as $C_{L_T}/\pi A_Te_T$ from the equations sheet. "Can only be deflected down to $-1$ degrees" is read as a stabiliser travel limit of $\alpha_s\ge-1^\circ$ against the required $-2.06^\circ$.
- Q2(ii). The tail arm $l$ is measured from the wing aerodynamic centre in the course's moment equation, so the 2 % CG shift does not change $K$; only $h$ changes.
- Q4(iv). Table 3 gives $c=3$ m, which is not needed. The question asks for the magnitude; the dimensional derivative is positive.
- Q4(vi). The Dutch-roll quadratic has a negative $\lambda$ coefficient, so the mode is unstable, a result an answer should state.
