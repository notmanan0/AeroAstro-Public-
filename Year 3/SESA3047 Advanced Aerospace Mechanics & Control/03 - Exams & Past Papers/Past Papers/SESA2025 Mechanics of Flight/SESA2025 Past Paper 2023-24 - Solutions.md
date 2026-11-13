---
title: "SESA2025 Past Paper 2023-24 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, aerodynamic-centre, hinge-moment, drag-divergence, trim-drag, range, static-margin, neutral-point, flight-test, body-axes, inertia-tensor, short-period, adverse-yaw, yaw-damping, dutch-roll, spiral]
paper: "2023-24"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]", "[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]", "[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-202324-02-SESA2025.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# SESA2025 Past Paper 2023-24 - Solutions

> [!abstract] Paper info
> 2023-24 Semester 2 examination (2 h, on campus), four questions of 25 marks, all compulsory. The equations sheet has the static-stability set of [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability|SESA2022 T6]], the trim-drag formulas with the minimum-trim-drag condition, the performance-optimisation formulas $X=C_{D_0}$, $Y=\frac{1}{\pi Ae}\left(1-\frac1\sigma\right)$, $C_{L^*_{\text{opt}}}=\sqrt{\frac XY\frac{d}{2-d}}$, $C_{D_\text{opt}}=X\left(1+\frac{d}{2-d}\right)$, and the Part B modal formulas. Q1 is five short discussions; Q2 is design for range, static margin and a flight-test neutral point (read from a graph); Q3 is equations of motion and the SPO; Q4 is the lateral modes, which SESA3047 lectures from Thu 19 Nov. All numbers were checked in Python with $g=9.81$ m/s².

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Aerodynamic centre, hinge coefficient $b_2$, transonic drag rise, trim drag and CG, roll-to-yaw coupling | [[Aerodynamic Centre and Centre of Pressure]], [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability\|SESA2022 T6]], [[Drag Divergence]], [[Lateral and Directional Stability]] |
| 2 | 25 | Speed and CG for maximum range with minimum trim drag; static margin; range penalty of a required margin; neutral point from a trim graph | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#5. Neutral point from flight tests\|T6 §5]], [[SESA1015 M07 - Propeller Aircraft Range and Endurance\|SESA1015 M07]], [[Neutral Point and Static Margin]] |
| 3 | 25 | Body and inertial frames, $I_{xy}=0$, $X_u$, SPO approximation and its natural frequency, SPO mode shape | [[SESA3047 2.1 - Vector Operations and the Transport Theorem\|2.1]], [[SESA3047 4.1 - Inertia Models and Rotor Dynamics\|4.1]], [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives\|SESA2027 A2]], [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)\|6.1 §7]] |
| 4 | 25 | Adverse yaw, fin incidence from yaw rate, Dutch-roll damping, lateral quartic, unstable spiral | Not yet lectured: Chapter 6 §§6.7–6.10 ([[Lecture Notes - Chapter 6.pdf]]), lectured from Thu 19 Nov; background in [[Lateral and Directional Stability]] |

---

## Q1. Short discussions (25 marks)

> (i) Advantages of using the aerodynamic centres of wing and tail, rather than their centres of pressure, in stability calculations. [5]
> (ii) Why is the tailplane coefficient $b_2$ normally negative? [5]
> (iii) Sketch $C_D$ of an aerofoil against Mach number and explain the rise after a critical Mach number. [5]
> (iv) Why does the total induced drag of an aircraft in equilibrium change with CG position at constant weight? [5]
> (v) How can a roll-angle perturbation induce a yawing moment? [5]

### (i) Aerodynamic centre against centre of pressure [5 marks]

The aerodynamic centre is the point about which the pitching moment does not change with incidence; the centre of pressure is the point through which the resultant force acts, where the moment is zero. Their positions are related by

$$
\frac{x_{cp}}{c}=\frac{x_{ac}}{c}-\frac{C_{M_{ac}}}{C_L},
$$

so the centre of pressure moves with $\alpha$ for any cambered surface, and runs off to infinity as $C_L\to0$; for a symmetric tailplane at zero lift it is undefined ([[Aerodynamic Centre and Centre of Pressure]]). Representing each surface by its lift at a fixed point (the AC) plus a constant moment ($M_0$ for the wing, zero for a symmetric tail) gives moment arms that do not depend on the flight condition. The trim equation $C_{M_0}+C_{L^*}(h-h_0)-C_{L_T}K=0$ is then linear with constant coefficients, it can be differentiated directly to give $dC_{M_{CG}}/d\alpha$ and the neutral point, and the contributions of wing and tail add. The AC is also a nearly fixed property of the geometry (quarter-chord in thin-aerofoil theory, independent of camber), whereas the centre of pressure would have to be recomputed for every $\alpha$.

### (ii) Sign of b2 [5 marks]

$b_2=\partial C_{M_H}/\partial\eta$ is the hinge-moment coefficient due to elevator deflection, with $\eta$ and $C_{M_H}$ both positive trailing edge down. Deflecting the elevator down raises the camber of the tail section and puts an extra upward load on the elevator itself, concentrated behind the hinge line. An upward force behind the hinge rotates the elevator trailing edge up, opposing the deflection, so $\Delta C_{M_H}<0$ for $\Delta\eta>0$ and $b_2<0$. The elevator behaves like a torsional spring that the aerodynamic load tries to return to neutral: the pilot feels a stick force that grows with deflection, which is the basis of control feel. The magnitude is reduced by a horn balance or a set-back hinge, which put part of the elevator area ahead of the hinge, but it is normally kept negative so that the elevator does not overbalance and run to full deflection.

### (iii) Drag against Mach number [5 marks]

![[amc_pp_202324_q1_cd_vs_mach.png|900]]

At low subsonic Mach number $C_D$ is roughly constant: skin friction plus form drag. The flow accelerates over the upper surface, so the local Mach number there is higher than the free stream. The critical Mach number $M_{crit}$ is the free-stream value at which the local flow first reaches $M=1$ ([[Critical Mach Number]]). Above it a supersonic pocket forms and ends in a shock wave. The shock adds wave drag (entropy rise and loss of total pressure across it), and its adverse pressure jump thickens or separates the boundary layer, adding pressure drag. $C_D$ then rises steeply at the drag-divergence Mach number $M_{DD}$, a little above $M_{crit}$ ([[Drag Divergence]]), and peaks near $M=1$ as the shocks move to the trailing edge and a bow shock forms. In supersonic flow the drag falls again as the wave drag decreases roughly as $1/\sqrt{M^2-1}$ ([[Supersonic Wave Drag]]), but stays well above the subsonic level.

### (iv) Induced drag and the CG position [5 marks]

The CG position fixes the tail lift needed for trim. From the moment equation,

$$
C_{L_T}=\frac{C_{M_0}+C_{L^*}(h-h_0)}{K},
$$

so the tail's share of the lift is

$$
r=\frac{C_{L_T}S_T}{C_{L^*}S}=\frac{S_T}{SK}\left(h-h_0+\frac{C_{M_0}}{C_{L^*}}\right)=\frac cl\left(h-h_0+\frac{C_{M_0}}{C_{L^*}}\right).
$$

At constant weight $C_{L^*}$ is fixed, but the split between wing and tail moves linearly with $h$. Induced drag is quadratic in each surface's lift, so the total depends on the split:

$$
C_{D_i}=C_{D_{L^*}}\left[1+r(\sigma r-2)\right],\qquad\sigma=1+\frac{SAe}{S_TA_Te_T}.
$$

A forward CG needs a download on the tail ($r<0$): the wing must lift more than the weight and both surfaces add induced drag. Moving the CG aft raises $r$ and reduces the trim drag until the minimum at $r=1/\sigma$; moving it further aft increases it again. The weight is unchanged throughout; what changes is how the lift is distributed between two surfaces of different span efficiency.

### (v) Yawing moment from a roll angle [5 marks]

A bank angle $\phi$ tilts the lift vector, so the lift no longer balances the weight across the aircraft's $y$ axis. The unbalanced component $mg\sin\phi\approx mg\phi$ (the $mg\phi$ term of the side-force equation) accelerates the aircraft sideways towards the lower wing, producing a sideslip $v$ in that direction. The relative wind then arrives from the low-wing side, and the fin, with $\mathring N_v>0$, makes a side force behind the CG that yaws the nose towards the low wing, $\Delta N=\mathring N_vv$. So the roll angle induces a yawing moment through sideslip and directional stability. The same sideslip produces a rolling moment through the dihedral effect ($\mathring L_vv$) that tends to level the wings; the balance between the two decides the spiral mode. A roll rate (as opposed to angle) gives a further, usually adverse, yawing moment $\mathring N_pp$ (Q4(i)).

---

## Q2. Range, static margin and a flight-test neutral point (25 marks)

> (i) A piston aircraft, always stick fixed, has $A=8$, $A_T=7$, $l=7$ m, $C_{M_0}=-0.01$, $g=9.81$ m/s², $a_0=a_1=2\pi$ rad⁻¹, $e=0.90$, $e_T=0.85$, $c=1.58$ m, $C_{D_0}=0.01$, $m=1500$ kg, $S=20$ m², $S_T=3$ m², $h_0=0.25$, $\gamma=0$, $\rho=1.0$ kg/m³. Find the speed and CG for maximum range; check static stability; for a required $H_s=0.3$, find the percentage range reduction when flying at 60 m/s. [15]
> (ii) Elevator angle against $C_{L^*}$ is measured at $h=0.2$ and $h=0.4$ (Figure 1). Estimate the neutral point and check whether $H_s\ge0.3$ is met at $h=0.27$. [10]

### (i) Maximum range, stability and the cost of the static margin [15 marks]

#### Speed and CG for maximum range

For a piston-propeller aircraft the Breguet range is $R=(\eta_p/c)(L/D)\ln(W_0/W_1)$, so maximum range means maximum $L/D$, $d=1$ ([[SESA1015 M07 - Propeller Aircraft Range and Endurance|SESA1015 M07]]). The trim drag is smallest when the tail share is $r=1/\sigma$, and then the drag polar including trim drag is

$$
C_D=C_{D_0}+C_{D_{L^*}}\left[1+\frac1\sigma\left(\frac\sigma\sigma-2\right)\right]=C_{D_0}+\frac{C_{L^*}^2}{\pi Ae}\left(1-\frac1\sigma\right)=X+YC_{L^*}^2,
$$

which is where the equations-sheet $X$ and $Y$ come from. With $d=1$, $C_{L^*_\text{opt}}=\sqrt{X/Y}$ and $C_{D_\text{opt}}=2X$.

$$
\sigma=1+\frac{SAe}{S_TA_Te_T}=1+\frac{20\times8\times0.90}{3\times7\times0.85}=1+\frac{144}{17.85}=9.06723,
$$

$$
Y=\frac{1}{\pi\times8\times0.90}\left(1-\frac{1}{9.06723}\right)=0.044210\times0.88971=0.039334,
$$

$$
C_{L^*_\text{opt}}=\sqrt{\frac{0.01}{0.039334}}=0.50422,\qquad C_{D_\text{opt}}=0.02,\qquad\left(\frac{L}{D}\right)_{\max}=25.21.
$$

The speed follows from $W=\tfrac12\rho V^2SC_{L^*}$:

$$
V=\sqrt{\frac{2mg}{\rho SC_{L^*}}}=\sqrt{\frac{2\times1500\times9.81}{1.0\times20\times0.50422}}=\sqrt{2918.4}=\boxed{54.0\ \text{m/s}}.
$$

The CG must make the trimmed tail lift equal the minimum-trim-drag value $C_{L_T}=C_{L^*}S/(\sigma S_T)$. Substitute into the moment equation and solve for $h$:

$$
h=h_0+\frac{C_{L_T}K-C_{M_0}}{C_{L^*}}.
$$

With $K=S_Tl/Sc$, the product $C_{L_T}K=C_{L^*}\frac{S}{\sigma S_T}\frac{S_Tl}{Sc}=C_{L^*}\frac{l}{\sigma c}$, so

$$
h=h_0+\frac{l}{\sigma c}-\frac{C_{M_0}}{C_{L^*}}=0.25+\frac{7}{9.06723\times1.58}+\frac{0.01}{0.50422},
$$

$$
h=0.25+0.48861+0.01983=\boxed{0.758}.
$$

#### Static stability

$$
C_{L_\alpha}=2\pi\times\frac{7.2}{9.2}=4.91728,\qquad\epsilon_\alpha=\frac{4.91728}{\pi\times7.2}=0.21739,
$$

$$
k=2\pi\times\frac{5.95}{7.95}=4.70251,\qquad C_{L_{T,\alpha}}=4.70251\times0.78261=3.68023,
$$

$$
C_{L^*_\alpha}=4.91728+3.68023\times\frac{3}{20}=5.46931,\qquad K=\frac{3\times7}{20\times1.58}=0.66456,
$$

$$
h_n=0.25+0.66456\times\frac{3.68023}{5.46931}=0.25+0.44717=0.69717,
$$

$$
H_s=h_n-h=0.69717-0.75845=\boxed{-0.061}.
$$

The CG for minimum trim drag lies behind the neutral point, so this design is statically unstable.

#### Range penalty of a 0.3 static margin at 60 m/s

The CG must move forward to $h=h_n-0.3=0.39717$. At 60 m/s:

$$
C_{L^*}=\frac{2\times14\,715}{1.0\times60^2\times20}=0.40875,
$$

$$
C_{L_T}=\frac{C_{M_0}+C_{L^*}(h-h_0)}{K}=\frac{-0.01+0.40875\times0.14717}{0.66456}=\frac{0.050155}{0.66456}=0.07547,
$$

$$
r=\frac{0.07547\times3}{0.40875\times20}=0.02770,
$$

$$
C_{D_{L^*}}=\frac{0.40875^2}{\pi\times7.2}=0.0073866,
$$

$$
C_{D_m}=C_{D_{L^*}}\,r(\sigma r-2)=0.0073866\times0.02770\times(0.25113-2)=-0.000358,
$$

$$
C_D=0.01+0.0073866-0.000358=0.017029,\qquad\frac LD=\frac{0.40875}{0.017029}=24.00.
$$

Range is proportional to $L/D$ for the same engine and fuel fraction, so

$$
\frac{R}{R_{\max}}=\frac{24.00}{25.21}=0.952,\qquad\boxed{\text{range reduction}=4.8\ \%}.
$$

Of this, 2.2 % comes from flying at 60 m/s instead of 54 m/s ($L/D=24.67$ even with minimum trim drag at 60 m/s), and the rest from the sub-optimal lift split forced by the forward CG.

### (ii) Neutral point from the trim graph [10 marks]

![[amc_pp_202324_q2_neutral_point.png|900]]

Both lines in the paper's Figure 1 are straight and reach $\eta\approx0.244$ rad at $C_{L^*}=0$. The $h=0.2$ line crosses $\eta=0$ at $C_{L^*}\approx0.77$ and the $h=0.4$ line at $C_{L^*}\approx1.29$. The slopes are

$$
\frac{d\eta}{dC_{L^*}}\bigg|_{h=0.2}=\frac{0-0.244}{0.77-0}=-0.317\ \text{rad},
$$

$$
\frac{d\eta}{dC_{L^*}}\bigg|_{h=0.4}=\frac{0-0.244}{1.29-0}=-0.189\ \text{rad}.
$$

The slope is linear in $h$ and zero at the neutral point ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#5. Neutral point from flight tests|T6 §5]]):

$$
h_n=0.2+(0.4-0.2)\frac{-0.317}{-0.317-(-0.189)}=0.2+0.2\times\frac{0.317}{0.128}=0.2+0.495=\boxed{0.70}.
$$

At $h=0.27$:

$$
H_s=0.70-0.27=\boxed{0.43\ge0.3},
$$

so the requirement is met.

> [!check] Digitised figure and the theory of part (i)
> Fitting straight lines to the pixels of the paper's figure gives slopes $-0.3177$ and $-0.1899$ rad and $h_n=0.6972$, against $h_n=0.69717$ computed from the geometry in (i): the figure was generated from the same aircraft model.

---

## Q3. Equations of motion and the short-period mode (25 marks)

> (i) Give an example of an inertial frame for an aircraft. Newton's second law in body axes is $\mathbf F_B=m(\dot{\mathbf v}_B+\boldsymbol\omega_B\times\mathbf v_B)$: what is it in an inertial frame, and why do the extra terms appear in body axes? [4]
> (ii) With a sketch, explain why $I_{xy}=\int xy\,dm$ is zero for a conventional aircraft. [4]
> (iii) What does $X_u=(\Lambda-2)C_D$ represent, and what does $\Lambda$ represent? [4]
> (iv) List the two approximations that reduce the longitudinal equation to the SPO form $\begin{bmatrix}m&0\\-\mathring M_{\dot w}&I_{yy}\end{bmatrix}\begin{bmatrix}\dot w\\\dot q\end{bmatrix}=\begin{bmatrix}\mathring Z_w&mU_\infty\\\mathring M_w&\mathring M_q\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix}$ and justify them. [4]
> (v) With $\omega_n^2=(\mathring M_q\mathring Z_w-mU_\infty\mathring M_w)/(mI_{yy})$ and $\mathring M_q=-1320$ N m s, $I_{yy}=14\,500$ kg m², $\mathring Z_w=-1600$ N s/m, $m=1750$ kg, $U_\infty=150$ m/s, $\mathring M_w=-120$ N s, find $\omega_n$ in rad/s. [2]
> (vi) Which numerator term dominates, and how could $\omega_n$ be raised most effectively for this aircraft? [3]
> (vii) Plot $\theta$ and $u$ against time for a typical transport aircraft when the SPO alone is excited, annotated. [4]

### (i) Inertial frame and Newton's second law [4 marks]

An Earth-fixed frame, for example north-east-down axes with origin on the runway, is treated as inertial under the [[Flat-Earth Model]]: the Earth's rotation and curvature are neglected over the time and distance of a flight-mechanics problem. In an inertial frame Newton's second law has no extra terms:

$$
\mathbf F=m\dot{\mathbf v}_I,
$$

the rate of change of velocity as seen by a non-rotating observer. Body axes rotate with the aircraft at $\boldsymbol\omega_B$, so a vector fixed in magnitude still changes direction relative to them. By the [[Transport Theorem]], $\dot{\mathbf v}_I=\dot{\mathbf v}_B+\boldsymbol\omega_B\times\mathbf v_B$: the derivative seen in the body frame plus the rate at which the frame turns the vector. The $\boldsymbol\omega_B\times\mathbf v_B$ term is the centripetal acceleration, for example $-qU$ in the $z$ equation of a pull-up.

### (ii) Why I_xy is zero [4 marks]

![[amc_pp_202324_q3_ixy_symmetry.png|900]]

A conventional aircraft is (to a very good approximation) mirror-symmetric about its $x$–$z$ plane. For every mass element $dm$ at $(x,y,z)$ there is an equal element at $(x,-y,z)$. Their contributions to $\int xy\,dm$ are $xy\,dm$ and $-xy\,dm$, which cancel, so the integral over the whole aircraft is zero, and the same argument gives $I_{yz}=0$. $I_{xz}$ survives, because the aircraft is not symmetric top to bottom. With $I_{xy}=I_{yz}=0$ the pitching motion decouples from roll and yaw in the linearised equations, which is what allows the separate longitudinal and lateral models ([[Principal Axes of Inertia]]).

### (iii) X_u and the thrust exponent [4 marks]

$X_u$ is the dimensionless derivative of the axial force (thrust minus drag) with respect to a forward-speed perturbation $u$: how much the net force along $x$ changes when the aircraft flies slightly faster. The $-2C_D$ part is the drag rise at constant $C_D$, since drag grows as $V^2$. $\Lambda$ describes the engine: thrust is modelled as $T=c_TU^\Lambda$, so $\Delta T=\Lambda D\,u/U_\infty$ at trim ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives|SESA2027 A2 §4]]). For a jet, thrust is roughly independent of speed, $\Lambda=0$; for a piston-propeller aircraft the power is roughly constant, $T\propto1/U$, $\Lambda=-1$. $X_u$ is negative for both ($-2C_D$ and $-3C_D$): speeding up raises drag more than thrust, which is speed stability, and it is the main source of phugoid damping.

### (iv) The two SPO approximations [4 marks]

The first approximation is that the SPO happens at constant speed and over too short a time for the attitude to change the gravity terms: $u\approx0$ and the $\theta$ terms are dropped. The $X$ equation (row 1) and $\dot\theta=q$ (row 4) are removed, together with the $u$ and $\theta$ columns of rows 2 and 3. This is justified by the separation of time scales: the SPO decays within a few seconds, while speed changes need the phugoid's tens of seconds, and the gravity term $-mg\sin\gamma_0\,\theta$ vanishes for level trim.

The second is that $\mathring Z_{\dot w}\ll m$ and $\mathring Z_q\ll mU_\infty$, so both are neglected in the $Z$ equation. The added-mass and pitch-rate lift terms are small against the aircraft's mass and the centripetal term; for the F-4C they are 0.1 % and 0.3 % ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]]). $\mathring M_{\dot w}$ is kept: it contributes noticeably to the SPO damping.

### (v) SPO natural frequency [2 marks]

$$
\mathring M_q\mathring Z_w=(-1320)(-1600)=2.112\times10^6,
$$

$$
-mU_\infty\mathring M_w=-1750\times150\times(-120)=3.150\times10^7,
$$

$$
mI_{yy}=1750\times14\,500=2.5375\times10^7,
$$

$$
\omega_n^2=\frac{2.112\times10^6+3.150\times10^7}{2.5375\times10^7}=\frac{3.3612\times10^7}{2.5375\times10^7}=1.3246\ \text{s}^{-2},
$$

$$
\boxed{\omega_n=1.151\ \text{rad/s}}.
$$

The numerator has units (N m s)(N s/m) = N² s² = kg² m² s⁻², and so does $mU_\infty\mathring M_w$ (kg · m/s · N s); the denominator is kg · kg m², so $\omega_n^2$ is in s⁻² as required.

### (vi) The dominant term [3 marks]

$-mU_\infty\mathring M_w$ dominates: $3.150\times10^7$ against $0.211\times10^7$, 94 % of the numerator. To a good approximation

$$
\omega_n\approx\sqrt{-\frac{U_\infty\mathring M_w}{I_{yy}}}=\sqrt{1.241}=1.114\ \text{rad/s}.
$$

$\mathring M_w$ is the pitch stiffness, $M_w=-H_sC_{L^*_\alpha}$, set by the static margin. The most effective way to raise $\omega_n$ for this aircraft is therefore to increase the static margin: move the CG forward, or move the neutral point aft with a larger tailplane or a longer tail arm. Increasing pitch damping $\mathring M_q$ would raise only the 6 % term. Raising $U_\infty$ also helps, through the explicit $U_\infty$ and because the dimensional derivatives grow with speed.

### (vii) SPO mode shape [4 marks]

The plot uses the SPO with $\omega_n=1.151$ rad/s from (v) and $\zeta\approx0.44$ (from the same data with $\mathring M_{\dot w}=0$), with the F-4C SPO eigenvector for the relative sizes of $\theta$ and $u$.

![[amc_pp_202324_q3_spo_theta_u.png|900]]

Features to annotate: $\theta$ oscillates quickly (period $2\pi/\omega$ of about 6 s) and is heavily damped, dying out within one or two cycles; the speed perturbation $u$ stays close to zero throughout (peak 0.1 m/s for a $2^\circ$ pitch disturbance), because the SPO is a rotation in pitch with changes in $\alpha$ and $q$ at essentially constant speed.

---

## Q4. Lateral dynamics (25 marks)

> (i) When an aircraft rolls with positive roll rate, what yawing moment is produced? What is the effect called and how can it be counteracted? [4]
> (ii) With a diagram, derive the change in fin incidence $\alpha_{F,r}$ from a yaw rate $r$ about the CG (fin AC at distance $l_F$); explain the resulting yawing moment and its direction for positive $r$. [4]
> (iii) With $\zeta=-\frac{1}{2\omega_n}\left(\frac{\mathring N_r}{I_{zz}}+\frac{\mathring Y_v}{m}\right)$, what physical modifications increase the Dutch-roll damping at fixed mass and inertia? [4]
> (iv) The lateral quartic is $(\lambda+7.4304)(\lambda-0.0064)(\lambda^2+0.4728\lambda+14.1139)=0$. Calculate the eigenvalues, identify the modes and state their stability. [6]
> (v) Describe the response of an aircraft with an unstable spiral mode to an initial sideslip. [5]
> (vi) What modifications would make the spiral mode stable? [2]

These lateral topics are Chapter 6 §§6.7–6.10 of the SESA3047 lecture notes, lectured from Thu 19 Nov.

### (i) Adverse yaw [4 marks]

A positive roll rate (starboard wing going down) produces a negative yawing moment, nose to port, away from the direction of the roll: $\mathring N_p<0$. This is adverse yaw. The down-going starboard wing sees the relative wind coming from below, so its incidence rises and its lift vector tilts forward; the rising port wing's lift tilts backwards. The two tilted lift vectors form a couple that yaws the nose to port. The aileron deflection that started the roll adds to it: the down-going aileron on the rising port wing increases that wing's lift and its induced drag, which also pulls the nose to port. It is counteracted by coordinated rudder (manually, or through an aileron–rudder interconnect), by differential ailerons (the up-going aileron deflects more) or Frise ailerons, which add profile drag on the down-going wing, and by using spoilers for roll control.

### (ii) Fin incidence from yaw rate [4 marks]

![[amc_pp_202324_q4_fin_yaw_rate.png|900]]

With a positive yaw rate $r$ (nose moving to starboard), the fin's aerodynamic centre at $x=-l_F$ moves sideways with velocity

$$
\boldsymbol\omega\times\mathbf r_F=(0,0,r)\times(-l_F,0,0)=(0,\,-rl_F,\,0),
$$

that is, to port at speed $rl_F$. Relative to the fin the air therefore has a component $rl_F$ towards starboard on top of the oncoming $V$, and the fin's incidence changes by

$$
\alpha_{F,r}=\tan^{-1}\frac{rl_F}{V}\approx\frac{rl_F}{V}\quad(\text{small angles, radians}).
$$

The fin lift (side force) acts along the cross-flow, to starboard:

$$
\Delta Y_F=\tfrac12\rho V^2S_Fa_F\frac{rl_F}{V},
$$

and since it acts at $x=-l_F$, the yawing moment is

$$
N=x\,\Delta Y_F=-l_F\,\Delta Y_F=-\tfrac12\rho VS_Fa_Fl_F^2\,r.
$$

For $r>0$ the moment is negative: it opposes the yaw rate. This is the fin's contribution to yaw damping, $\mathring N_r=-\tfrac12\rho VS_Fa_Fl_F^2<0$.

### (iii) Increasing Dutch-roll damping [4 marks]

With $m$ and $I_{zz}$ fixed, the damping term $2\zeta\omega_n=-(\mathring N_r/I_{zz}+\mathring Y_v/m)$ grows if $\mathring N_r$ or $\mathring Y_v$ is made more negative.

- Yaw damping $\mathring N_r\propto S_Fa_Fl_F^2$: a longer tail arm is the most effective, because it enters squared, followed by a larger fin area and a higher fin lift slope (higher fin aspect ratio, end-plate effect of a T-tail).
- Side-force derivative $\mathring Y_v\propto S_Fa_F$ plus the fuselage side area: a larger fin, a ventral fin or strakes.

A larger fin also raises $\mathring N_v$ and so $\omega_n$, which divides the damping sum, so lengthening the tail arm (raising $\mathring N_r$ faster than $\mathring N_v$) is the better change. Reducing the dihedral effect also helps the real Dutch roll, though it does not appear in this two-degree-of-freedom approximation.

### (iv) Eigenvalues and modes [6 marks]

$$
\lambda_1=\boxed{-7.4304\ \text{s}^{-1}},\qquad\lambda_2=\boxed{+0.0064\ \text{s}^{-1}},
$$

$$
\lambda^2+0.4728\lambda+14.1139=0:\quad\lambda_{3,4}=\frac{-0.4728\pm\sqrt{0.22354-56.4556}}{2}=\boxed{-0.2364\pm3.7494j}.
$$

- $-7.4304$: roll subsidence, the large negative real root: fast decay of roll rate (time constant 0.135 s). Stable.
- $+0.0064$: spiral mode, the real root closest to zero. Positive, so unstable, but very slow: time to double $t_2=\ln2/0.0064=108.3$ s.
- $-0.2364\pm3.7494j$: Dutch roll, the only oscillatory pair, with $\omega_n=\sqrt{14.1139}=3.757$ rad/s, period 1.68 s and $\zeta=0.4728/(2\times3.757)=0.063$. Stable, but lightly damped.

### (v) Response with an unstable spiral [5 marks]

Take an initial sideslip to starboard. The fast modes act first: the fin yaws the nose into the sideslip and the dihedral effect rolls the aircraft away from it, a brief, decaying Dutch-roll oscillation, while roll subsidence quickly kills any roll rate. What remains is a small residual bank angle and heading change, now governed by the slow spiral mode. The banked lift has a sideways component that makes the aircraft slip towards the low wing; directional stability turns the nose towards the low wing, so the aircraft yaws into a gentle turn. The yaw rate makes the outer wing faster than the inner one, so it lifts more ($\mathring L_r>0$) and the bank increases. Because the restoring dihedral effect is too weak to overcome this, the loop repeats: more bank, a tighter turn, a larger yaw rate, still more bank. The bank angle, turn rate and nose-down attitude grow exponentially, doubling every 108 s, and the aircraft enters a steepening, accelerating descending spiral (a spiral dive). The divergence is slow enough for a pilot to correct easily with visual references, but in cloud it is a classic cause of loss of control.

### (vi) Making the spiral stable [2 marks]

The spiral approximation (Chapter 6 §6.8) gives $\lambda=-\frac{g}{U_\infty}\frac{L_vN_r-L_rN_v}{L_vN_p-L_pN_v}$, with a positive denominator, so the mode is stable if $L_vN_r>L_rN_v$. That needs a stronger dihedral effect ($|L_v|$ larger: more dihedral, a high wing or sweep), more yaw damping ($|N_r|$ larger: longer tail arm), or less directional stiffness ($N_v$ smaller: a smaller fin). A smaller fin and more dihedral both reduce Dutch-roll damping, so the design is a compromise between the two modes; a slightly unstable spiral is usually accepted.

---

## Paper slips and ambiguities

- Q2(i). "The CG location at which range would be maximised" is read as the CG that gives the minimum-trim-drag lift split at the maximum-$L/D$ condition, which is the condition built into the equations-sheet $X$ and $Y$. The range comparison in the third part assumes the same engine efficiency and fuel fraction, so $R\propto L/D$.
- Q2(ii). The two lines are read by eye from Figure 1; the answer is insensitive to small reading errors because both lines pass through the same $C_{L^*}=0$ intercept.
- Q3(iv). The SPO form printed keeps $\mathring M_{\dot w}$, so "the two approximations" are constant speed (with the $\theta$ terms dropped) and neglect of $\mathring Z_{\dot w}$ and $\mathring Z_q$.
- Q3(v)–(vii). The data give $\omega_n$ but not $\mathring M_{\dot w}$, so the damping used for the sketch ($\zeta\approx0.44$) assumes $\mathring M_{\dot w}=0$.
