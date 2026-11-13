---
title: "SESA2025 Past Paper 2018-19 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, stick-fixed, stick-free, trim-tab, high-lift, dihedral, manoeuvre-stability, static-margin, stability-quartic, spo, phugoid, handling-qualities, aerodynamic-derivatives, spiral]
paper: "2018-19"
theory_notes: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[Stick-Fixed vs Stick-Free Stability]]", "[[Lateral and Directional Stability]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-201819-02-SESA2025W1.pdf"]
---

# SESA2025 Past Paper 2018-19 - Solutions

> [!abstract] Paper info
> SESA2025 Mechanics of Flight, Semester 2 examination 2018-19 (120 min, equations sheet on pp. 7–8), four questions of 25 marks, answer all. From this year the sheet follows the [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability|SESA2022 T6]] notation: $C_{L^*}=C_W\cos\gamma$, $n=L^*/W$, $\bar a_1=a_1-a_2b_1/b_2$, and the manoeuvre term $(n-1)C_W\Phi$. Q3 is the longitudinal stability quartic (SESA3047 6.1); Q4 is lateral derivatives and the spiral approximation (SESA3047 §§6.7–6.10, Thu 19 Nov 2026). All numbers were checked in Python; the matrix in Q4(iii) has a sign problem in $\mathring L_p$ (see [[#Paper slips and ambiguities]]).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Stick fixed and stick free; elevator and tab angles; $C_L$–$\alpha$ with high-lift devices; dihedral; manoeuvre stability and altitude; why stick free is less stable | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#2. Trim: stick fixed and stick free|SESA2022 T6 §2, §4, §6]], [[Stick-Fixed vs Stick-Free Stability]], [[Manoeuvre Point and Manoeuvre Margin]] |
| 2 | 25 | Stick-free cruise trim ($\alpha$, $\eta$, $\beta$); tab and elevator signs; stick-free static margin | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Solution algorithm for trim problems|SESA2022 T6 §2–3]], [[Neutral Point and Static Margin]] |
| 3 | 25 | Factored quartic: SPO and phugoid stability, period and half-life; handling qualities; pitch-rate step response | [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#3. Damping ratio and natural frequency (6.13–6.16)|SESA3047 6.1 §2–3]], [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|SESA2027 A3]] |
| 4 | 25 | Strip-theory $L_r$; spiral-mode approximation; spiral eigenvalue from a dimensional lateral model | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[Lateral and Directional Stability]] |

---

## Q1. Stick-fixed and stick-free flight, high-lift devices and stability (25 marks)

> (i) Define stick-fixed and stick-free conditions. [4]
> (ii) From the tailplane lift and elevator hinge-moment equations derive (a) the elevator position stick fixed, (b) the elevator and trim-tab positions stick free. [6]
> (iii) Sketch $C_L$ against $\alpha$ for (a) a clean wing, (b) slats only, (c) flaps only, and discuss the differences. [4]
> (iv) With a diagram, explain how wing dihedral increases lateral stability. [4]
> (v) Explain how manoeuvre stability changes with altitude and how this affects handling. [3]
> (vi) For a conventional elevator, why is an aircraft less stable stick free than stick fixed, and how can this be modified? [4]

### (i) Stick fixed and stick free [4 marks]

**Stick fixed**: the pilot (or an irreversible control system) holds the elevator at a fixed angle $\eta$, whatever the hinge moment; the elevator does not move when the aircraft is disturbed, and the tab is normally taken as $\beta=0$. The pilot must supply a stick force to balance any hinge moment, $C_{M_H}\neq0$.

**Stick free**: the pilot lets go of the stick, so the elevator is free to rotate about its hinge and floats to the angle at which its hinge moment is zero, $C_{M_H}=0$. The trim tab $\beta$ is set so that this floating angle is the one needed to trim, and the aircraft then flies hands-off. When disturbed, the elevator floats to a new angle and changes the tail's contribution to stability.

### (ii) Elevator and tab angles [6 marks]

The tail lift and hinge moment are

$$
C_{L_T}=a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\qquad C_{M_H}=b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta,
$$

with $C_{L_T}$ known from the trim (moment) equation and $\alpha_{T_{eff}}$ from the wing incidence.

(a) Stick fixed, $\beta=0$ (or set), so the lift equation alone gives

$$
\boxed{\eta=\frac{C_{L_T}-a_1\alpha_{T_{eff}}-a_3\beta}{a_2}=\frac{C_{L_T}-a_1\alpha_{T_{eff}}}{a_2}\quad(\beta=0).}
$$

(b) Stick free, $C_{M_H}=0$ adds a second equation:

$$
\begin{bmatrix}a_2&a_3\\b_2&b_3\end{bmatrix}\begin{bmatrix}\eta\\\beta\end{bmatrix}=\begin{bmatrix}C_{L_T}-a_1\alpha_{T_{eff}}\\-b_1\alpha_{T_{eff}}\end{bmatrix}.
$$

The determinant is $\Delta=a_2b_3-a_3b_2$. By Cramer's rule,

$$
\eta=\frac{(C_{L_T}-a_1\alpha_{T_{eff}})b_3-a_3(-b_1\alpha_{T_{eff}})}{\Delta},
$$

$$
\boxed{\eta=\frac{b_3\left(C_{L_T}-a_1\alpha_{T_{eff}}\right)+a_3b_1\alpha_{T_{eff}}}{a_2b_3-a_3b_2},}
$$

$$
\beta=\frac{a_2(-b_1\alpha_{T_{eff}})-b_2(C_{L_T}-a_1\alpha_{T_{eff}})}{\Delta},
$$

$$
\boxed{\beta=-\frac{b_2\left(C_{L_T}-a_1\alpha_{T_{eff}}\right)+a_2b_1\alpha_{T_{eff}}}{a_2b_3-a_3b_2}.}
$$

### (iii) Lift curves with high-lift devices [4 marks]

![[amc_pp_201819_q1_cl_alpha_hld.png|900]]

- Clean wing: a straight line through the zero-lift angle $\alpha_0$ (slightly negative for a cambered section), stalling at around $12$–$15^\circ$.
- Slats only: the leading-edge slot re-energises the boundary layer and lowers the suction peak, delaying separation. The linear part is almost unchanged (same $\alpha_0$, nearly the same slope, a little higher if the slat extends the chord), but the stall moves to a higher $\alpha$, so $C_{L\max}$ rises at a larger stalling angle.
- Flaps only: a trailing-edge flap adds camber, which shifts the whole line upwards (more negative $\alpha_0$, more lift at every $\alpha$). $C_{L\max}$ rises but is reached at a lower stalling angle, and a slotted or Fowler flap also adds area and slightly raises the slope.

Slats raise $C_{L\max}$ by extending the usable incidence; flaps raise it by adding camber. Combined, they give the highest $C_{L\max}$ at a moderate attitude. Flaps also move the aerodynamic centre aft and make $C_{M_0}$ more nose-down, which needs more tail download to trim.

### (iv) Dihedral and lateral stability [4 marks]

![[amc_pp_201819_q1_dihedral.png|900]]

When a wing drops, the lift tilts and the aircraft sideslips towards the low wing, so the air arrives with a sideways component $v$ from that side. With dihedral $\Gamma$, the leading (low) wing is inclined so that this sideways flow has a component $v\sin\Gamma$ up through it, raising its incidence by about $v\Gamma/V$; the trailing wing sees the same component downwards and loses incidence. The leading wing therefore gains lift and the trailing wing loses it, which gives a rolling moment that raises the low wing: the aircraft returns towards wings-level, which is lateral stability ($L_v<0$). Too much dihedral makes the Dutch roll poorly damped.

### (v) Manoeuvre stability and altitude [3 marks]

The extra stability in a manoeuvre comes from the pitch-rate increment in tail incidence, $(n-1)C_W\Phi$ with $\Phi=\rho Sl/(2m)$ ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability|SESA2022 T6 §4]]). As altitude rises, $\rho$ and $\Phi$ fall, so the pitch damping from the tail weakens and the manoeuvre point moves forward towards the neutral point: the manoeuvre margin decreases. At high altitude the aircraft therefore needs less elevator and stick force per $g$, feels lighter and more responsive in pitch and is easier to over-stress; it also has less natural damping, so the short period is less damped. At low altitude the opposite holds: it feels heavier and more sluggish.

### (vi) Why stick free is less stable [4 marks]

With a conventional elevator both $b_1$ and $b_2$ are negative. When a disturbance raises the tail's incidence, the hinge moment $b_1\Delta\alpha_{T_{eff}}$ makes a free elevator float trailing-edge up by $\Delta\eta=-(b_1/b_2)\Delta\alpha_{T_{eff}}$, which reduces the tail lift increment. The stick-free tail lift slope is therefore

$$
\bar a_1=a_1-a_2\frac{b_1}{b_2}<a_1,
$$

so the tail's restoring moment, the neutral point and the static margin are all smaller stick free ([[Stick-Fixed vs Stick-Free Stability]]). For Q2's aircraft $\bar a_1=5.93$ against $a_1=6.28$, and the margin falls from 0.288 to 0.273.

The loss is reduced by cutting the floating tendency $|b_1/b_2|$: aerodynamic balance (a horn balance or a set-back hinge) reduces $|b_1|$, and with enough balance $b_1$ can be made zero or positive, so the elevator floats against the disturbance. Mechanical devices also help: an anti-balance (geared) tab that deflects to oppose the elevator, or a down-spring or bobweight, which add a stick-force gradient that restores stick-free stability.

---

## Q2. Stick-free cruise trim and static margin (25 marks)

> A conventional aircraft (Table 1) cruises stick free at 10 000 m: $A=7.79$, $S=830$ m², $e=0.95$; $A_T=4.4$, $S_T=215$ m², $e_T=0.9$; $l=34$ m, $\alpha_s=-4.0^\circ$, $h=0.40$; $V=230$ m/s, $\alpha_0=-3.0^\circ$, $h_0=0.25$; $m=480\times10^3$ kg, $\rho=0.414$ kg/m³, $g=9.81$ m/s²; $C_{M_0}=-0.11$, $C_{L_T}=2\pi\alpha_{T_{eff}}+2.5\eta+1.2\beta$, $C_{D_0}=0.015$; $c=11.4$ m, $C_{M_H}=-0.1\alpha_{T_{eff}}-0.7\eta-1.3\beta$, $a_0=2\pi$ rad⁻¹.
> (i) Determine $\alpha$, $\eta$ and $\beta$ for trim. [11]
> (ii) Explain with a diagram why $\beta$ has the opposite sign to $\eta$. [6]
> (iii) Find the stick-free static margin. [8]

### (i) Trim angles [11 marks]

**Assumptions.** Level cruise ($\gamma=0$, so $C_{L^*}=C_W$); thrust and drag through the CG; the sheet's linear models.

The constants:

$$
\pi Ae=\pi(7.79)(0.95)=23.249,\qquad C_{L_\alpha}=a_0\frac{\pi Ae}{\pi Ae+a_0}=6.2832\times\frac{23.249}{29.533}=4.9464,
$$

$$
\epsilon_\alpha=\frac{C_{L_\alpha}}{\pi Ae}=0.21275,\qquad\pi A_Te_T=\pi(4.4)(0.9)=12.441,
$$

$$
K=\frac{S_Tl}{Sc}=\frac{215\times34}{830\times11.4}=0.77256,\qquad s=\frac{S_T}{S}=0.25904.
$$

The weight coefficient, with $q=\tfrac12(0.414)(230^2)=10\,950$ Pa:

$$
C_{L^*}=C_W=\frac{480\times10^3\times9.81}{10\,950\times830}=0.51809.
$$

The moment equation gives the tail lift:

$$
C_{L_T}=\frac{C_{M_0}+C_{L^*}(h-h_0)}{K}=\frac{-0.11+0.51809\times0.15}{0.77256}=\frac{-0.03229}{0.77256}=-0.04179.
$$

The tail pushes down because the wing's nose-down $C_{M_0}$ outweighs the nose-up moment of the lift aft of the AC. The wing lift and incidence:

$$
C_L=C_{L^*}-sC_{L_T}=0.51809+0.25904\times0.04179=0.52892,
$$

$$
\alpha=\alpha_0+\frac{C_L}{C_{L_\alpha}}=-0.05236+\frac{0.52892}{4.9464}=-0.05236+0.10693=0.05457\ \text{rad}=\boxed{3.13^\circ}.
$$

The effective tail incidence:

$$
\alpha_{T_{eff}}=(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T},
$$

$$
\alpha_{T_{eff}}=0.78725(0.05457)+0.21275(-0.05236)-0.06981+\frac{0.04179}{12.441},
$$

$$
\alpha_{T_{eff}}=0.04296-0.01114-0.06981+0.00336=-0.03463\ \text{rad}\ (-1.98^\circ).
$$

Stick free, the lift and zero-hinge-moment equations (Q1(ii)(b)):

$$
2.5\eta+1.2\beta=C_{L_T}-2\pi\alpha_{T_{eff}}=-0.04179+0.21761=0.17582,
$$

$$
0.7\eta+1.3\beta=-0.1\,\alpha_{T_{eff}}=-0.1(-0.03463)=0.003463.
$$

With $\Delta=2.5(1.3)-1.2(0.7)=2.41$:

$$
\eta=\frac{0.17582(1.3)-1.2(0.003463)}{2.41}=\frac{0.22441}{2.41}=0.09312\ \text{rad}=\boxed{5.34^\circ},
$$

$$
\beta=\frac{2.5(0.003463)-0.7(0.17582)}{2.41}=\frac{-0.11442}{2.41}=-0.04748\ \text{rad}=\boxed{-2.72^\circ}.
$$

Both equations check to $10^{-17}$.

### (ii) Why the tab opposes the elevator [6 marks]

![[amc_pp_201819_q2_trim_tab.png|900]]

The tab is a small surface at the elevator's trailing edge, the furthest point from the hinge, so a small tab force has a large moment about the hinge. To hold the elevator deflected one way with zero stick force, the tab must create a hinge moment the other way: deflecting the tab down makes an upward force on it, which rotates the elevator trailing edge up. In the figure the elevator is held up ($\eta<0$) by a tab deflected down ($\beta>0$).

In equations, $C_{M_H}=0$ gives

$$
\beta=-\frac{b_2}{b_3}\eta-\frac{b_1}{b_3}\alpha_{T_{eff}}.
$$

For a conventional elevator $b_2$ and $b_3$ are both negative, so $-b_2/b_3<0$, and $|b_1|$ is small (a well-balanced elevator), so the first term dominates and $\beta$ has the opposite sign to $\eta$. In Q2(i), $-b_2/b_3=-0.538$, $\eta=+5.34^\circ$ and $\beta=-2.72^\circ$, a ratio of $-0.51$; the small difference is the $b_1$ term.

### (iii) Stick-free static margin [8 marks]

Stick free the elevator floats, so the tail lift slope uses (sheet)

$$
\bar a_1=a_1-a_2\frac{b_1}{b_2}=2\pi-2.5\times\frac{-0.1}{-0.7}=6.2832-0.3571=5.9260,
$$

$$
\bar k=\bar a_1\frac{\pi A_Te_T}{\pi A_Te_T+\bar a_1}=5.9260\times\frac{12.441}{12.441+5.926}=4.0140,
$$

$$
C_{L_{T,\alpha}}=\bar k(1-\epsilon_\alpha)=4.0140\times0.78725=3.1600,
$$

$$
C_{L^*_\alpha}=C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}=4.9464+3.1600\times0.25904=5.7650.
$$

$$
H_S=h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}=0.25-0.40+0.77256\times\frac{3.1600}{5.7650}=-0.15+0.42347=\boxed{0.273}.
$$

The stick-free neutral point is at $h_n=0.673$, so the CG at 0.40 is $27\,\%$ of the chord ahead of it. Stick fixed ($k=4.1747$) the margin is 0.288: freeing the elevator costs 0.015, small because $|b_1|=0.1$ is small.

---

## Q3. SPO and phugoid from the factored quartic (25 marks)

> The stability quartic factors as $(\lambda^2+1.40\lambda+9.49)(\lambda^2-0.0016\lambda+0.0016)=0$.
> (i) Identify the SPO quadratic, state whether it is stable and find its period and half-life. [5]
> (ii) Repeat for the phugoid. [5]
> (iii) Describe the main features of the SPO and phugoid and discuss their handling-quality requirements. [8]
> (iv) Sketch the short- and long-term pitch-rate response to a small positive elevator step, marking the periods and half-lives. [7]

### (i) The SPO [5 marks]

The SPO is the high-frequency, well-damped factor, $\lambda^2+1.40\lambda+9.49$. All its coefficients are positive, so it is stable. Its roots:

$$
\lambda=-0.70\pm i\sqrt{9.49-0.49}=-0.70\pm3.00i.
$$

$$
T=\frac{2\pi}{3.00}=\boxed{2.09\ \text{s}},\qquad t_{1/2}=\frac{\ln2}{0.70}=\boxed{0.99\ \text{s}},
$$

with $\omega_n=\sqrt{9.49}=3.081$ rad/s and $\zeta=1.40/(2\times3.081)=0.227$.

### (ii) The phugoid [5 marks]

The phugoid is the slow factor, $\lambda^2-0.0016\lambda+0.0016$. Its middle coefficient is negative, so the real part of its roots is positive and the mode is **unstable**:

$$
\lambda=0.0008\pm i\sqrt{0.0016-0.00000064}=0.0008\pm0.03999i,
$$

$$
T=\frac{2\pi}{0.03999}=\boxed{157\ \text{s}}.
$$

A half-life does not exist; the amplitude doubles every

$$
t_2=\frac{\ln2}{0.0008}=\boxed{866\ \text{s}},
$$

about 5.5 cycles. Here $\omega_n=0.040$ rad/s and $\zeta=-0.0008/0.04=-0.020$.

### (iii) Features and handling qualities [8 marks]

The **SPO** is a fast pitching oscillation about the CG at nearly constant speed; incidence and pitch attitude change together, so the flight path barely bends. Its stiffness comes from the static margin ($M_w$) and its damping from the tail's pitch damping ($M_q$), downwash lag ($M_{\dot w}$) and lift slope ($Z_w$). It sets the response to stick inputs and gusts, so it must be well damped with a suitable frequency: MIL-F-8785C Level 1 asks for $0.35\le\zeta_{sp}\le1.30$ in precision and terminal phases (0.30 to 2.0 in cruise), and CS-25 requires the short period to be heavily damped. This aircraft's $\zeta_{sp}=0.23$ is below the Level 1 minimum: it overshoots by about 48 % ($e^{-\pi\zeta/\sqrt{1-\zeta^2}}$) and would bob in turbulence, so a pitch damper would be needed.

The **phugoid** is a slow exchange of kinetic and potential energy along an undulating path at nearly constant incidence ($\theta\approx\gamma$). Being slow, it is easily corrected by the pilot, so the requirements are lenient: Level 1 needs $\zeta_{ph}\ge0.04$, Level 2 $\zeta_{ph}\ge0$, and Level 3 accepts an unstable phugoid if its time to double is at least 55 s. This phugoid ($t_2=866$ s) is unstable but very slowly so, which meets the Level 3 limit and adds pilot workload on long instrument legs; an autopilot speed or height hold removes it.

### (iv) Pitch-rate response to an elevator step [7 marks]

![[amc_pp_201819_q3_pitch_rate_step.png|900]]

*Step response of an illustrative pitch-rate transfer function with the paper's denominator and assumed numerator zeros at $s=-0.03$ and $s=-0.9$; the paper gives only the denominator, so the amplitudes are schematic but the periods and decay rates are those of parts (i) and (ii).*

A positive elevator step (trailing edge down) pitches the nose down, so $q$ goes negative. In the short term (left) the SPO dominates: the pitch rate overshoots to a peak in about 0.5 s and oscillates with period $T_{sp}=2.09$ s, the oscillation halving every $t_{1/2}=0.99$ s, so it has gone after two or three cycles and $q$ settles at a quasi-steady value while the attitude changes. In the long term (right) the phugoid takes over: the speed and flight path begin to oscillate with period $T_{ph}=157$ s, and because the mode is unstable the oscillation in $q$ grows, doubling every 866 s, instead of settling to the new trim. On the long-term plot the SPO transient is a spike at $t=0$.

---

## Q4. Lateral derivatives and the spiral mode (25 marks)

> (i) By considering lift on a strip $dy$ at distance $y$ from the centreline, derive
> $$L_r=\frac{2}{Sb^2}\int_{-s}^{s}c(y)\,C_L\,y^2\,dy.$$ [8]
> (ii) From the lateral state equation
> $$\begin{bmatrix}m&0&0&0\\0&I_{xx}&-I_{xz}&0\\0&-I_{xz}&I_{zz}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot v\\\dot p\\\dot r\\\dot\phi\end{bmatrix}=\begin{bmatrix}\mathring Y_v&\mathring Y_p&\mathring Y_r-mU_\infty&mg\\\mathring L_v&\mathring L_p&\mathring L_r&0\\\mathring N_v&\mathring N_p&\mathring N_r&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix},$$
> state the assumptions and show that the slow spiral eigenvalue is $\lambda=-\dfrac{g}{U_\infty}\,\dfrac{\mathring L_v\mathring N_r-\mathring L_r\mathring N_v}{\mathring L_v\mathring N_p-\mathring L_p\mathring N_v}$. [9]
> (iii) An aircraft at 50 m/s has
> $$\begin{bmatrix}1500&0&0&0\\0&1700&-250&0\\0&-250&9500&0\\0&0&0&1\end{bmatrix}\dot{\mathbf x}=\begin{bmatrix}-320&0&-75000&14715\\-450&12000&3000&0\\500&-2000&-4000&0\\0&1&0&0\end{bmatrix}\mathbf x.$$
> Identify the quantities (with units) needed for the spiral approximation and calculate the eigenvalue. [8]

### (i) Rolling moment due to yaw rate [8 marks]

**Assumptions.** Strip theory (each strip acts as a 2D section in its local flow); the yaw rate changes the local speed but not the incidence, so each strip keeps its local $C_L$; drag forces lie in the wing plane and give no rolling moment; $ry\ll V$; positive $r$ is nose to starboard, positive rolling moment is starboard wing down.

Yawing at $r$, a strip at $y$ (positive to starboard) has local airspeed

$$
V_y=V-ry:
$$

the port wing ($y<0$) moves forward and goes faster, the starboard wing slower. The strip's lift is

$$
dL=\tfrac12\rho V_y^2\,c(y)\,C_L\,dy=\tfrac12\rho\left(V^2-2Vry+r^2y^2\right)c\,C_L\,dy.
$$

Neglect $r^2y^2$ and keep the part due to $r$:

$$
\delta(dL)=-\rho Vr\,y\,c\,C_L\,dy.
$$

The extra lift is upward on the port wing and downward on the starboard wing, so it rolls the starboard wing down. The rolling moment of the strip is $-y\,\delta(dL)$:

$$
d\mathcal L=\rho Vr\,c\,C_L\,y^2\,dy.
$$

Integrate over the span:

$$
\mathcal L=\rho Vr\int_{-s}^{s}c(y)\,C_L\,y^2\,dy,\qquad\mathring L_r=\frac{\partial\mathcal L}{\partial r}=\rho V\int_{-s}^{s}c\,C_L\,y^2\,dy.
$$

Non-dimensionalise with $\tfrac12\rho VSb^2$:

$$
\boxed{L_r=\frac{\mathring L_r}{\tfrac12\rho VSb^2}=\frac{2}{Sb^2}\int_{-s}^{s}c(y)\,C_L\,y^2\,dy.}
$$

$L_r$ is positive (a yaw to starboard rolls the aircraft to starboard) and proportional to $C_L$, so it is largest at low speed.

### (ii) The spiral approximation [9 marks]

**Assumptions.** The spiral is a very slow, non-oscillatory mode, so over its time scale the accelerations are negligible: $\dot v\approx\dot p\approx\dot r\approx0$ (which also removes the $I_{xz}$ terms); the motion is close to a coordinated turn, so in the side-force equation $\mathring Y_vv$ and $\mathring Y_pp$ are small and $\mathring Y_r\ll mU_\infty$; level trim. Only $\dot\phi=p$ keeps its time derivative.

The side-force equation becomes

$$
0=-mU_\infty r+mg\phi\quad\Rightarrow\quad r=\frac{g}{U_\infty}\phi,
$$

the turn rate of a coordinated turn at bank $\phi$. The rolling and yawing moment equations become algebraic:

$$
0=\mathring L_vv+\mathring L_pp+\mathring L_rr,
$$

$$
0=\mathring N_vv+\mathring N_pp+\mathring N_rr.
$$

Eliminate $v$: multiply the first by $\mathring N_v$ and the second by $\mathring L_v$, and subtract:

$$
0=\left(\mathring L_v\mathring N_p-\mathring L_p\mathring N_v\right)p+\left(\mathring L_v\mathring N_r-\mathring L_r\mathring N_v\right)r.
$$

So

$$
p=-\frac{\mathring L_v\mathring N_r-\mathring L_r\mathring N_v}{\mathring L_v\mathring N_p-\mathring L_p\mathring N_v}\,r.
$$

Substitute $p=\dot\phi$ and $r=g\phi/U_\infty$:

$$
\dot\phi=-\frac{g}{U_\infty}\,\frac{\mathring L_v\mathring N_r-\mathring L_r\mathring N_v}{\mathring L_v\mathring N_p-\mathring L_p\mathring N_v}\,\phi=\lambda\phi,
$$

$$
\boxed{\lambda=-\frac{g}{U_\infty}\,\frac{\mathring L_v\mathring N_r-\mathring L_r\mathring N_v}{\mathring L_v\mathring N_p-\mathring L_p\mathring N_v}.}
$$

With the usual signs the denominator is positive, so the spiral is stable when $\mathring L_v\mathring N_r>\mathring L_r\mathring N_v$: enough dihedral effect ($\mathring L_v<0$) and yaw damping against the weathercock stiffness ($\mathring N_v$) and the roll due to yaw rate ($\mathring L_r$).

### (iii) Spiral eigenvalue of the given aircraft [8 marks]

Reading the matrices against part (ii): $m=1500$ kg (and $mg=1500\times9.81=14\,715$ N checks), $U_\infty=50$ m/s, $mU_\infty=75\,000$ kg m/s so $\mathring Y_r=0$, $I_{xx}=1700$, $I_{zz}=9500$ and $I_{xz}=250$ kg m² (not needed). The required derivatives:

| Quantity | Value | Units |
|---|---:|---|
| $\mathring L_v$ | $-450$ | N s (N m per m/s) |
| $\mathring L_p$ | $12\,000$ (as printed) | N m s/rad |
| $\mathring L_r$ | $3000$ | N m s/rad |
| $\mathring N_v$ | $500$ | N s |
| $\mathring N_p$ | $-2000$ | N m s/rad |
| $\mathring N_r$ | $-4000$ | N m s/rad |
| $g/U_\infty$ | $9.81/50=0.1962$ | s⁻¹ |

Numerator:

$$
\mathring L_v\mathring N_r-\mathring L_r\mathring N_v=(-450)(-4000)-(3000)(500)=1.8\times10^6-1.5\times10^6=0.3\times10^6.
$$

Denominator, as printed:

$$
\mathring L_v\mathring N_p-\mathring L_p\mathring N_v=(-450)(-2000)-(12\,000)(500)=0.9\times10^6-6.0\times10^6=-5.1\times10^6.
$$

$$
\lambda=-0.1962\times\frac{0.3\times10^6}{-5.1\times10^6}=\boxed{+0.0115\ \text{s}^{-1}},
$$

an unstable spiral that doubles its bank every $\ln2/0.0115=60$ s.

> [!warning] The sign of $\mathring L_p$
> Roll damping is always negative, and with $\mathring L_p=+12\,000$ the full model has an unstable roll mode at $+7.0$ s⁻¹, so the printed sign is almost certainly a slip. With $\mathring L_p=-12\,000$ N m s/rad the denominator is $0.9\times10^6+6.0\times10^6=6.9\times10^6$ and
> $$\lambda=-0.1962\times\frac{0.3\times10^6}{6.9\times10^6}=-0.00853\ \text{s}^{-1},$$
> a stable spiral with half-life 81 s. The full $4\times4$ model with that sign has its spiral at $-0.00742$ s⁻¹ (roll $-7.18$, Dutch roll $-0.262\pm1.834i$), so the approximation is 15 % fast but correctly stable. The numerator is positive either way ($\mathring L_v\mathring N_r>\mathring L_r\mathring N_v$), which is the spiral stability condition.

---

## Paper slips and ambiguities

- Q4(iii). $\mathring L_p=+12\,000$ is printed; roll damping must be negative. As printed, the spiral approximation gives $+0.0115$ s⁻¹ (unstable) and the full model has an unstable roll mode; with $\mathring L_p=-12\,000$ the approximation gives $-0.00853$ s⁻¹ (half-life 81 s) against $-0.00742$ s⁻¹ from the full model.
- Q2(i). $\rho=0.414$ kg/m³ matches the ISA density at 10 000 m (0.4135 kg/m³).
- Q3(iv). Only the characteristic polynomial is given, so the response sketch uses an assumed numerator; the periods and growth rates are exact.
