---
title: "SESA2025 Past Paper 2024-25 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, static-stability, skin-friction, trim-drag, manoeuvre-point, zero-lift-angle, static-margin, aspect-ratio, phugoid, aerodynamic-derivatives, roll-subsidence, roll-damping, spiral, dutch-roll]
paper: "2024-25"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[Manoeuvre Point and Manoeuvre Margin]]", "[[SESA2022 T2 - Boundary Layers]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-202425-02-SESA2025.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# SESA2025 Past Paper 2024-25 - Solutions

> [!abstract] Paper info
> 2024-25 Semester 2 examination (2 h, on campus), four questions of 25 marks, all compulsory. The equations sheet is the same as 2023-24: the static-stability set of [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability|SESA2022 T6]], trim drag with the minimum-trim-drag condition, performance optimisation, and the Part B modal formulas. Q1 is five short discussions; Q2 designs an air racer's static margin through its zero-lift angle and wing aspect ratio (with a blank $H_s$–$A$ grid to fill in); Q3 is the phugoid; Q4 is roll damping and the lateral modes, which SESA3047 lectures from Thu 19 Nov. All numbers were checked in Python with $g=9.81$ m/s².

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Reference area of $C_{L^*}$, factors in pitch stiffness, skin-friction reduction, minimum-trim-drag lift split, manoeuvre point and altitude | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability\|SESA2022 T6]], [[Manoeuvre Point and Manoeuvre Margin]], [[SESA2022 T2 - Boundary Layers\|SESA2022 T2]] |
| 2 | 25 | Zero-lift angle for trim at $\eta=0$; static margin; effect of wing aspect ratio and interpolation to $H_s=0.28$ | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Solution algorithm for trim problems\|T6 §2]], [[Neutral Point and Static Margin]] |
| 3 | 25 | $w=\alpha U_\infty$, $Z_w$, phugoid identification and parameters, phugoid mode shape and damping | [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives\|SESA2027 A2]], [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation\|6.1]]; the phugoid damping approximation is §6.6, lectured Mon 16 Nov ([[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes\|Deep Dive §9]], written ahead) |
| 4 | 25 | Lateral quartic, roll subsidence and $L_p$, incidence from roll rate, aileron response, spiral doubling time | Not yet lectured: Chapter 6 §§6.7–6.10 ([[Lecture Notes - Chapter 6.pdf]]), lectured from Thu 19 Nov; background in [[Lateral and Directional Stability]] |

---

## Q1. Short discussions (25 marks)

> (i) Is it appropriate to normalise the total lift $L^*=L+L_T$ by the wing area $S$ to obtain $C_{L^*}$? [5]
> (ii) With a free-body diagram, explain three main factors that affect longitudinal static stability, in terms of $dC_{M_{CG}}/d\alpha$. [5]
> (iii) Discuss two strategies to reduce skin-friction drag, with sketches. [5]
> (iv) For the minimum-trim-drag condition, discuss how the wing ($S$, $A$, $e$) and tailplane ($S_T$, $A_T$, $e_T$) characteristics affect the optimal lift split $C_{L_T}/C_{L^*}$. [5]
> (v) Explain, with a diagram, how the manoeuvre point changes with altitude. [5]

### (i) The reference area for the total lift [5 marks]

It is appropriate, provided it is used consistently. Any single reference area makes the force balance non-dimensional; $S$ is the natural choice because the wing carries most of the lift and is the reference for $C_W$, the drag coefficients and the aerodynamic derivatives. The tail lift is first written with its own area, $L_T=\tfrac12\rho V^2S_TC_{L_T}$, so that $C_{L_T}$ is a genuine property of the tail surface, and is then referred to $S$ through the factor $S_T/S$:

$$
C_{L^*}=\frac{L+L_T}{\tfrac12\rho V^2S}=C_L+C_{L_T}\frac{S_T}{S}=C_W\cos\gamma.
$$

The weight coefficient on the right uses the same $S$, so the equation is exact. The price is that $C_{L^*}$ is not the lift coefficient of any real surface: it cannot be compared directly with a section or wing $C_{L,\max}$, because the wing works at $C_L=C_{L^*}-C_{L_T}S_T/S$, which is higher than $C_{L^*}$ when the tail lifts downward. Normalising by $S+S_T$ would give smaller numbers with the same physics. For a canard or tandem layout with surfaces of similar size the choice is arbitrary, and the key requirement is only that every coefficient in the analysis uses the same reference.

### (ii) Factors in the pitch stiffness [5 marks]

![[amc_pp_202425_q1_fbd_static_stability.png|900]]

After a disturbance $\Delta\alpha$, each surface's lift changes and acts on its own arm about the CG. Differentiating the moment equation:

$$
\frac{dC_{M_{CG}}}{d\alpha}=C_{L^*_\alpha}(h-h_0)-K\,C_{L_{T,\alpha}},\qquad C_{L_{T,\alpha}}=k(1-\epsilon_\alpha).
$$

Stability needs this to be negative. Three factors:

1. CG position relative to the wing aerodynamic centre, $h-h_0$. With the CG behind the wing AC, the wing's lift increment acts ahead of the CG and pitches the nose further up: destabilising. Moving the CG forward is the most direct way to add stability.
2. Tail volume and tail lift slope, $K=S_Tl/Sc$ and $k=a_1\pi A_Te_T/(\pi A_Te_T+a_1)$. The tail's lift increment acts on the long arm $l$ behind the CG and pitches the nose down: stabilising, in proportion to tail area, tail arm and the tail's 3D lift slope (higher with tail aspect ratio).
3. Downwash gradient, $\epsilon_\alpha=C_{L_\alpha}/\pi Ae$. The wing's downwash grows with $\alpha$, so the tail sees only $(1-\epsilon_\alpha)\Delta\alpha$; a strong downwash gradient weakens the tail's stabilising contribution.

The fuselage (usually destabilising, its lift acting ahead of the CG), power effects and stick-free floating of the elevator also contribute.

### (iii) Reducing skin-friction drag [5 marks]

![[amc_pp_202425_q1_skin_friction.png|900]]

Skin friction is the wall shear stress $\tau_w=\mu\,\partial u/\partial y|_w$ integrated over the wetted area. A turbulent boundary layer has a much fuller profile, so its wall gradient and $\tau_w$ are several times those of a laminar layer at the same Reynolds number ([[SESA2022 T2 - Boundary Layers|SESA2022 T2]]).

The first strategy is to keep the boundary layer laminar for longer (laminar flow control). Natural laminar flow aerofoils are shaped so that the pressure keeps falling over a long forward portion of the chord, which damps the instabilities that cause transition; very smooth, rigid, clean surfaces without steps, gaps or rivet heads help, as does a low sweep. Active laminar flow control sucks the low-momentum air near the wall through a porous skin. At $Re_L=10^7$ the laminar flat-plate $C_F=1.328/\sqrt{Re_L}=0.00042$ against $0.074/Re_L^{1/5}=0.0029$ turbulent, a factor of seven.

The second strategy is to reduce the friction of the turbulent layer that cannot be avoided. Riblets, fine streamwise grooves about 50 µm apart, restrict the spanwise motion of the near-wall streaks and reduce turbulent skin friction by around 5–8 %; other options are reducing the wetted area (a smaller, more compact fuselage and fewer protuberances) and compliant or slippery coatings.

### (iv) Optimal lift split for minimum trim drag [5 marks]

The minimum-trim-drag condition on the equations sheet is

$$
\frac{C_{L_T}}{C_{L^*}}\frac{S_T}{S}=\frac1\sigma,\qquad\sigma=1+\frac{SAe}{S_TA_Te_T}.
$$

Multiply by $S/S_T$:

$$
\frac{C_{L_T}}{C_{L^*}}=\frac{S}{S_T}\cdot\frac{1}{1+\dfrac{SAe}{S_TA_Te_T}}=\frac{1}{\dfrac{S_T}{S}+\dfrac{Ae}{A_Te_T}}.
$$

In terms of forces, the ratio of tail lift to wing lift at the optimum is

$$
\frac{L_T}{L}=\frac{1/\sigma}{1-1/\sigma}=\frac{1}{\sigma-1}=\frac{S_TA_Te_T}{SAe}=\frac{e_Tb_T^2}{e\,b^2},
$$

using $SA=b^2$. Each surface should carry lift in proportion to its span squared times its span efficiency: the same rule that minimises the induced drag of any group of lifting surfaces. The trends:

- A higher wing aspect ratio $A$ or efficiency $e$ makes the wing the more efficient surface, so it should carry more: $C_{L_T}/C_{L^*}$ falls.
- A higher tail aspect ratio $A_T$ or efficiency $e_T$ makes the tail more efficient, so it should carry more: $C_{L_T}/C_{L^*}$ rises.
- A larger tail area $S_T$ raises the tail's share of the force, $L_T/L$, but spreads it over more area, so the coefficient ratio $C_{L_T}/C_{L^*}$ falls.
- A larger wing area $S$ lowers the tail's share of the force but raises $C_{L_T}/C_{L^*}$, which tends to the limit $A_Te_T/(Ae)$ as $S_T/S\to0$.

For the racer of Q2 ($A=9$, $e=0.85$, $A_T=3$, $e_T=0.7$, $S_T/S=0.2$), $C_{L_T}/C_{L^*}=1/(0.2+3.643)=0.260$ and the tail should carry 5.2 % of the total lift.

### (v) Manoeuvre point and altitude [5 marks]

In a steady pull-up the pitch rate adds an incidence $(n-1)C_W\Phi$ at the tail, with mass parameter $\Phi=\rho Sl/2m$, and the stick-fixed manoeuvre lift slope is ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability|T6 §4]])

$$
C_{L_{T,\alpha}}=k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi S_T/S},\qquad h_m=h_0+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}S_T/S}.
$$

$\Phi$ is proportional to density, which falls with altitude. As $\Phi\to0$ the manoeuvre slope tends to the equilibrium value $k(1-\epsilon_\alpha)$, so the manoeuvre point moves forward towards the neutral point and the manoeuvre margin $H_m=h_m-h$ shrinks. Physically, the pitch damping that the tail provides in a pull-up depends on the tail's lift per unit pitch rate, which scales with the air density for a given true airspeed and load factor; in thin air the aircraft needs less elevator per $g$ and feels less stable and more responsive. Heavier aircraft (larger $m$) show the effect less at any altitude.

![[amc_pp_202425_q1_manoeuvre_point_altitude.png|900]]

For the racer of Q2 at its CG $h=0.20$, the manoeuvre point moves from $0.616$ at sea level ($\Phi=0.0295$) to $0.573$ at 12 km ($\Phi=0.0075$), approaching $h_n=0.559$.

---

## Q2. Air-racer design: zero-lift angle, static margin and aspect ratio (25 marks)

> Data (Table 1): $g=9.81$ m/s², $m=726$ kg, $\rho=1.225$ kg/m³, $A=9$, $S=10$ m², $e=0.85$, $A_T=3$, $S_T=2$ m², $e_T=0.70$, $h_0=0.25$, $h=0.20$, $l=3.5$ m, $\gamma=0$, $C_{M_0}=-0.01$, $a_0=a_1=2\pi$ rad⁻¹, $a_2=3.5$ rad⁻¹, $\alpha_s=0$; rectangular wing with $c=\sqrt{S/A}$.
> (i) Find the zero-lift angle $\alpha_0$ needed to trim with $\eta=0$ at $V=86$ m/s, stick fixed. [9]
> (ii) Compute the static margin and discuss the stability. [5]
> (iii) The customer wants $H_s=28.0$ %: discuss a couple of design alternatives. [2]
> (iv) Only the wing aspect ratio may change (same $S$): compute $H_s$ for $A=5$. [5]
> (v) Interpolate between $A=5$ and $A=9$ for the $A$ that gives $H_s=28.0$ %, plotting on Figure 1. [4]

### (i) Zero-lift angle for trim with zero elevator [9 marks]

The unknowns are $\alpha$, $\alpha_0$ and $C_{L_T}$. The force and moment equations fix $C_{L_T}$ and $C_L$, which give $\alpha-\alpha_0$; the tail-lift equation with $\eta=0$ then fixes $\alpha$ itself, and $\alpha_0$ follows.

Geometry:

$$
c=\sqrt{\frac{S}{A}}=\sqrt{\frac{10}{9}}=1.05409\ \text{m},\qquad K=\frac{S_Tl}{Sc}=\frac{2\times3.5}{10\times1.05409}=0.66408.
$$

Weight coefficient, level flight:

$$
\tfrac12\rho V^2=\tfrac12\times1.225\times86^2=4530.05\ \text{Pa},\qquad C_{L^*}=C_W=\frac{726\times9.81}{4530.05\times10}=0.157218.
$$

Tail lift from the moment equation:

$$
C_{L_T}=\frac{C_{M_0}+C_{L^*}(h-h_0)}{K}=\frac{-0.01+0.157218\times(-0.05)}{0.66408}=\frac{-0.017861}{0.66408}=-0.026896.
$$

The CG is ahead of the wing AC, so the tail must push down. Wing lift:

$$
C_L=C_{L^*}-C_{L_T}\frac{S_T}{S}=0.157218+0.026896\times0.2=0.162597.
$$

Wing slope and incidence above zero lift ($\pi Ae=\pi\times7.65$):

$$
C_{L_\alpha}=2\pi\times\frac{7.65}{9.65}=4.98097\ \text{rad}^{-1},\qquad\alpha-\alpha_0=\frac{0.162597}{4.98097}=0.032644\ \text{rad}.
$$

Downwash and tail induced angle:

$$
\epsilon_\alpha=\frac{4.98097}{\pi\times7.65}=0.20725,\qquad\epsilon=\epsilon_\alpha(\alpha-\alpha_0)=0.006766\ \text{rad},
$$

$$
\epsilon_T=\frac{C_{L_T}}{\pi A_Te_T}=\frac{-0.026896}{\pi\times2.1}=-0.004077\ \text{rad}.
$$

With $\eta=0$ and $\alpha_s=0$ the stick-fixed tail lift is $C_{L_T}=a_1\alpha_{T\text{eff}}$ with $\alpha_{T\text{eff}}=\alpha-\epsilon-\epsilon_T$:

$$
\alpha=\frac{C_{L_T}}{a_1}+\epsilon+\epsilon_T=\frac{-0.026896}{2\pi}+0.006766-0.004077,
$$

$$
\alpha=-0.004281+0.006766-0.004077=-0.001592\ \text{rad}=-0.091^\circ.
$$

Then

$$
\alpha_0=\alpha-(\alpha-\alpha_0)=-0.001592-0.032644,
$$

$$
\boxed{\alpha_0=-0.03424\ \text{rad}=-1.96^\circ}.
$$

> [!check] Back-substitution
> $\alpha_{T\text{eff}}=(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-C_{L_T}/\pi A_Te_T=0.79275\times(-0.001592)+0.20725\times(-0.034236)+0.004077=-0.004281$ rad, and $2\pi\times(-0.004281)=-0.026896=C_{L_T}$. A wing camber giving $\alpha_0\approx-2^\circ$ is typical of a moderately cambered section.

### (ii) Static margin [5 marks]

$$
k=a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}=2\pi\times\frac{2.1}{4.1}=3.21822\ \text{rad}^{-1},
$$

$$
C_{L_{T,\alpha}}=k(1-\epsilon_\alpha)=3.21822\times0.79275=2.55123\ \text{rad}^{-1},
$$

$$
C_{L^*_\alpha}=4.98097+2.55123\times0.2=5.49122\ \text{rad}^{-1},
$$

$$
H_s=h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}=0.25-0.20+0.66408\times\frac{2.55123}{5.49122}=0.05+0.30853,
$$

$$
\boxed{H_s=0.359=35.9\ \%}.
$$

The aircraft is statically stable with a large margin: the CG is ahead of the wing AC (which already gives $+0.05$) and the tail volume is generous. For an air racer that must pitch quickly around an obstacle course this is too much. A large margin means a stiff pitch response, large elevator angles and stick forces per $g$, and more trim drag from the downward tail load needed to balance the forward CG.

### (iii) Ways to reach H_s = 28 % [2 marks]

The margin must fall by 0.0785. The options are to move the CG aft by $0.0785c$ (relocate equipment, ballast or the pilot's seat), to reduce the tail volume (smaller $S_T$ or shorter tail arm $l$), to reduce the tail's lift slope (lower $A_T$), or to change the wing so that $K=S_Tl/Sc$ falls (larger chord at the same area, i.e. lower aspect ratio, which is the option pursued in (iv)).

### (iv) Static margin with A = 5 [5 marks]

With $S$ unchanged, $A=5$ changes the chord, and with it $K$, $C_{L_\alpha}$ and $\epsilon_\alpha$; the tail is unchanged ($k=3.21822$).

$$
c=\sqrt{\frac{10}{5}}=1.41421\ \text{m},\qquad K=\frac{2\times3.5}{10\times1.41421}=0.49497,
$$

$$
C_{L_\alpha}=2\pi\times\frac{\pi\times5\times0.85}{\pi\times5\times0.85+2\pi}=2\pi\times\frac{4.25}{6.25}=4.27257\ \text{rad}^{-1},
$$

$$
\epsilon_\alpha=\frac{4.27257}{\pi\times4.25}=0.32000,\qquad C_{L_{T,\alpha}}=3.21822\times0.68=2.18839\ \text{rad}^{-1},
$$

$$
C_{L^*_\alpha}=4.27257+2.18839\times0.2=4.71024\ \text{rad}^{-1},
$$

$$
H_s=0.05+0.49497\times\frac{2.18839}{4.71024}=0.05+0.22996=\boxed{0.2800=28.0\ \%}.
$$

> [!tip] Why the ratio did not change
> $C_{L_{T,\alpha}}/C_{L^*_\alpha}=0.4646$ for both aspect ratios. With the course's downwash model, $1-\epsilon_\alpha=\pi Ae/(\pi Ae+a_0)$, so $C_{L_\alpha}=a_0(1-\epsilon_\alpha)$ and $C_{L_{T,\alpha}}/C_{L^*_\alpha}=k/(a_0+kS_T/S)$, independent of $A$: a higher-aspect-ratio wing has a steeper lift slope but also more downwash at the tail, in exactly compensating proportion. The aspect ratio therefore acts only through the chord in $K\propto1/c=\sqrt{A/S}$, and $H_s=0.05+0.30853\sqrt{A/9}$.

### (v) Interpolating for H_s = 28 % [4 marks]

Linear interpolation between $(A,H_s)=(5,0.27997)$ and $(9,0.35853)$:

$$
A=5+(9-5)\frac{0.280-0.27997}{0.35853-0.27997}=5+4\times\frac{0.00003}{0.07856}=\boxed{A\approx5.0}.
$$

![[amc_pp_202425_q2_hs_vs_aspect_ratio.png|900]]

The exact relation $H_s=0.05+0.30853\sqrt{A/9}$ gives $A=5.0015$, so the required aspect ratio is 5. The curve is concave, so straight-line interpolation over a wider interval would slightly overestimate the required $A$; here the end point already meets the target. The shorter span also raises the roll rate available (Q4(v)), which suits a racer, at the cost of more induced drag ($\pi Ae$ falls from 24.0 to 13.4).

---

## Q3. The phugoid (25 marks)

> (i) With a velocity triangle, explain why $w=\alpha U_\infty$ and state the assumption. [3]
> (ii) $Z_w=-(C_{L^*_\alpha}+C_D)$: what does $Z_w$ represent, which term dominates for a conventional aircraft, and how can its magnitude be changed? [4]
> (iii) The quartic factorises as $(\lambda^2+1.397\lambda+1.901)(\lambda^2+0.023\lambda+0.031)=0$. Identify the phugoid, its stability, its frequency in Hz and its half-life. [8]
> (iv) Plot $\theta$ and $\alpha$ against time when the phugoid alone is excited, annotated. [5]
> (v) With $\mathring M_u=0$ the phugoid damping is $\zeta=\frac{1}{2\omega_n}\frac1m(-\mathring X_u)$. Explain the physical meaning of the derivative responsible. [3]
> (vi) Explain why $M_u=0$ can be assumed for a fixed-wing UAV. [2]

### (i) The w–α relation [3 marks]

![[amc_pp_202425_q3_w_alpha_triangle.png|900]]

The aircraft's velocity relative to the air has body components $u$ along $x$ and $w$ along $z$. The angle of attack is the angle between the body $x$ axis and that velocity, so

$$
\tan\alpha=\frac wu,\qquad w=u\tan\alpha.
$$

For small perturbations about trim, $u\approx U_\infty$, and for small angles in radians $\tan\alpha\approx\alpha$, so $w\approx\alpha U_\infty$. The assumption is small $\alpha$ (and small perturbations, so that $u\approx U_\infty$); the error of $\tan\alpha\approx\alpha$ is about 1 % at $\alpha=10^\circ$.

### (ii) The derivative Z_w [4 marks]

$Z_w$ is the dimensionless derivative of the normal force $Z$ (positive down) with respect to the vertical velocity $w$, i.e. with respect to angle of attack. An increase in $w$ raises $\alpha$ by $w/U_\infty$, which raises the lift (acting in $-z$), so $Z_w<0$: it is the heave damping that opposes vertical motion and is one of the main SPO damping terms ($-\mathring Z_w/m$ in $2\zeta\omega_n$). $C_D$ enters because the rotation of the wind axes by $\Delta\alpha$ tips a component of the drag into the $z$ direction.

The lift-slope term dominates: $C_{L^*_\alpha}\approx5$ rad⁻¹ against $C_D\approx0.02$–$0.05$, so $Z_w\approx-C_{L^*_\alpha}$. Its magnitude is changed through the lift-curve slope: a higher wing aspect ratio or efficiency ($C_{L_\alpha}=a_0\pi Ae/(\pi Ae+a_0)$), less sweep, and a larger or more efficient tailplane (the $C_{L_{T,\alpha}}S_T/S$ part of $C_{L^*_\alpha}$) all make it larger.

### (iii) Phugoid identification and parameters [8 marks]

$$
\lambda^2+1.397\lambda+1.901=0:\quad\lambda=\frac{-1.397\pm\sqrt{1.95161-7.604}}{2}=-0.6985\pm1.1887j,
$$

$$
\lambda^2+0.023\lambda+0.031=0:\quad\lambda=\frac{-0.023\pm\sqrt{0.000529-0.124}}{2}=-0.0115\pm0.17569j.
$$

The phugoid is $\lambda^2+0.023\lambda+0.031$: its natural frequency $\sqrt{0.031}=0.176$ rad/s is eight times lower than the other quadratic's $\sqrt{1.901}=1.379$ rad/s, and its damping ratio $0.023/(2\times0.176)=0.065$ is far lower than $0.507$. Slow and lightly damped is the phugoid; fast and well damped is the SPO.

It is stable, because the real part $\sigma=-0.0115$ s⁻¹ is negative: the oscillation decays.

$$
f=\frac{\omega}{2\pi}=\frac{0.17569}{2\pi}=\boxed{0.0280\ \text{Hz}}\quad(T=35.8\ \text{s}),
$$

$$
t_{1/2}=\frac{\ln0.5}{\sigma}=\frac{-0.6931}{-0.0115}=\boxed{60.3\ \text{s}}.
$$

### (iv) Phugoid response [5 marks]

The plot uses this paper's phugoid eigenvalue and the F-4C phugoid eigenvector of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]] for the relative size and phase of $\theta$ and $\alpha$, scaled to a $2^\circ$ initial pitch.

![[amc_pp_202425_q3_phugoid_theta_alpha.png|900]]

Annotate: the period $T=35.8$ s; the decaying envelope $e^{-0.0115t}$, halving every 60.3 s; the large oscillation in pitch attitude $\theta$ (degrees); and the almost constant angle of attack (peak $0.18^\circ$ for $2^\circ$ of $\theta$), because the aircraft follows its flight path at nearly fixed incidence while speed and height trade against each other.

### (v) The derivative that damps the phugoid [3 marks]

$\mathring X_u=\partial X/\partial u$ is the change in axial force (thrust minus drag) per unit increase in forward speed. In the phugoid the aircraft dives and speeds up, then climbs and slows. When it is fast, the drag is higher than the thrust and decelerates it; when it is slow, the drag is lower and the thrust accelerates it. Because $\mathring X_u<0$, the force always opposes the speed perturbation, so energy is removed every cycle, like a dashpot in a mass–spring system: this is the damping. From $X_u=(\Lambda-2)C_D$, it is proportional to the drag. With $\omega_n\approx\sqrt2\,g/U_\infty$ and $\mathring X_u=\tfrac12\rho U_\infty SX_u$,

$$
\zeta=\frac{-\mathring X_u}{2\omega_nm}=\frac{(2-\Lambda)\tfrac12\rho U_\infty^2SC_D}{2\sqrt2\,mg}=\frac{2-\Lambda}{2\sqrt2}\,\frac{C_D}{C_L},
$$

so a clean, high-$L/D$ aircraft has a poorly damped phugoid (for a jet, $\zeta\approx1/(\sqrt2\,L/D)$).

### (vi) Why M_u = 0 for the UAV [2 marks]

$M_u$ is the change in pitching moment with forward speed at constant incidence. In trim the total pitching moment is zero, so a pure change in dynamic pressure scales a zero moment and leaves it zero; $M_u$ is non-zero only if the moment coefficients themselves change with speed. A small fixed-wing UAV flies at low Mach number (no compressibility shift of the aerodynamic centre), has a stiff structure at low dynamic pressure (no aeroelastic twist), and usually has its thrust line close to the CG, so a speed-dependent thrust produces no pitching moment. Hence $\mathring M_u\approx0$.

---

## Q4. Roll damping and the lateral modes (25 marks)

> (i) The lateral quartic is $(\lambda+9.8815)(\lambda-0.0049)(\lambda^2+0.6525\lambda+24.8503)=0$. Calculate the eigenvalues, identify the modes and state their stability, with reasons. [6]
> (ii) With a diagram, explain the roll-subsidence mode and its mechanism. [4]
> (iii) With a diagram, derive the change in wing incidence $\alpha_p$ at a spanwise strip $y$ due to a roll rate $p$ about the CG. [4]
> (iv) With $L_p=-\frac{1}{Sb^2}\int_{-b/2}^{b/2}C_{l_\alpha}(y)c(y)y^2dy$, what design changes decrease the roll damping? [4]
> (v) Why might a designer want to decrease the stability of the roll mode? Use $p=-\frac{\mathring L_{\delta_A}\delta_A}{\mathring L_p}\left(1-e^{\frac{\mathring L_p}{I_{xx}}t}\right)$. [3]
> (vi) Calculate the time to double of the unstable spiral mode. [2]
> (vii) Is the unstable spiral a handling-quality issue for this aircraft? [2]

These lateral topics are Chapter 6 §§6.7–6.10 of the SESA3047 lecture notes, lectured from Thu 19 Nov.

### (i) Eigenvalues and the three modes [6 marks]

$$
\lambda_1=\boxed{-9.8815\ \text{s}^{-1}},\qquad\lambda_2=\boxed{+0.0049\ \text{s}^{-1}},
$$

$$
\lambda^2+0.6525\lambda+24.8503=0:\quad\lambda_{3,4}=\frac{-0.6525\pm\sqrt{0.42576-99.4012}}{2}=\boxed{-0.3263\pm4.9743j}.
$$

- $-9.8815$: roll subsidence. Large, real and negative, so a fast non-oscillatory decay (time constant $0.101$ s). Stable, because the real part is negative.
- $+0.0049$: spiral mode. Real and very close to zero, so very slow and non-oscillatory. Unstable, because it is positive: a disturbance grows, but only slowly.
- $-0.3263\pm4.9743j$: Dutch roll, the only complex pair, so the only oscillation ($\omega_n=4.985$ rad/s, $\zeta=0.065$, period 1.26 s). Stable, because the real part is negative, though lightly damped.

### (ii) The roll-subsidence mode [4 marks]

![[amc_pp_202425_q4_roll_strip.png|900]]

Roll subsidence is a fast, non-oscillatory decay of roll rate. When the aircraft rolls with $p>0$ (starboard wing down), every strip of the down-going wing moves downward and meets the air at a higher incidence, so its lift rises; every strip of the up-going wing loses incidence and lift. The lift difference, acting on arms up to $b/2$ either side of the roll axis, makes a rolling moment that opposes the roll rate: $\mathring L_p<0$, roll damping. Neglecting sideslip and yaw, $I_{xx}\dot p=\mathring L_pp$, so $p=p_0e^{(\mathring L_p/I_{xx})t}$ decays with time constant $\tau=-I_{xx}/\mathring L_p$. The mode removes roll rate but not bank angle: the aircraft stops rolling at whatever bank it has reached.

### (iii) Incidence from roll rate [4 marks]

A strip at distance $y$ from the roll axis moves with velocity $\boldsymbol\omega\times\mathbf r=(p,0,0)\times(0,y,0)=(0,0,py)$, i.e. downwards (body $+z$) at speed $py$ on the starboard side for $p>0$. Relative to the strip, the air therefore has an upward component $py$ added to the oncoming $V$, which tilts the relative wind upwards by

$$
\alpha_p=\tan^{-1}\frac{py}{V}\approx\boxed{\frac{py}{V}}\quad(\text{small angles, radians}).
$$

On the port side $y<0$ and $\alpha_p<0$. The strip's lift changes by $\delta L=\tfrac12\rho V^2c(y)\,\delta y\,C_{l_\alpha}(y)\,py/V$, and its rolling moment about $x$ is $-y\,\delta L$ (an upward force on the starboard side rolls the aircraft to port). Integrating over the span:

$$
\Delta L=-\tfrac12\rho Vp\int_{-b/2}^{b/2}C_{l_\alpha}(y)c(y)y^2dy,
$$

and dividing by $\tfrac12\rho VSb^2\,p$ gives the $L_p$ formula of part (iv).

### (iv) Reducing the roll damping [4 marks]

The integrand weights each strip's lift slope and chord by $y^2$, so the outer wing dominates. The roll damping is reduced by

- a shorter span: the dimensional derivative $\mathring L_p=\tfrac12\rho VSb^2L_p=-\tfrac12\rho V\int C_{l_\alpha}cy^2dy$ grows roughly as the cube of the span for a given chord (clipped wings on aerobatic aircraft);
- moving area inboard: high taper or small tip chords put less chord where $y^2$ is large (for a rectangular wing $L_p=-C_{l_\alpha}/12$ exactly; taper reduces it);
- a lower local lift slope, especially outboard: sweep or a lower aspect ratio reduces $C_{l_\alpha}$, and washout or tip stall reduces the tips' contribution;
- smaller tail surfaces far from the roll axis (a tall fin or a wide tailplane adds a little roll damping).

### (v) Why reduce roll damping [3 marks]

For a step aileron input the roll rate rises to the steady value

$$
p_{ss}=-\frac{\mathring L_{\delta_A}\delta_A}{\mathring L_p},
$$

so for a given aileron power and deflection, a smaller $|\mathring L_p|$ gives a higher maximum roll rate. A fighter or an air racer needs high roll rates to change direction quickly, so the designer may accept weaker roll damping (less negative eigenvalue $\mathring L_p/I_{xx}$). The cost is a longer time constant $\tau=-I_{xx}/\mathring L_p$: the roll rate takes longer to build up and to stop, so the response feels less crisp, and the aircraft is more easily rolled by gusts. The initial roll acceleration $\mathring L_{\delta_A}\delta_A/I_{xx}$ is unaffected.

### (vi) Spiral doubling time [2 marks]

$$
t_2=\frac{\ln2}{\sigma}=\frac{0.6931}{0.0049}=\boxed{141\ \text{s}}.
$$

### (vii) Is the unstable spiral a problem? [2 marks]

No. Handling-quality specifications such as MIL-F-8785C allow an unstable spiral as long as the bank angle takes long enough to double, typically at least 12–20 s for Level 1 (good) handling. A doubling time of 141 s is far longer: the divergence is so slow that the pilot corrects it without noticing, by small aileron inputs. It is a concern only without visual references (in cloud) or with no pilot attention, where an autopilot's wing-levelling function deals with it.

---

## Paper slips and ambiguities

- Q2(iv)–(v). With the Table 1 data, $H_s$ at $A=5$ is already $0.27997$, so the target sits at one end of the interpolation interval and (v) returns $A\approx5.0$ without real interpolation.
- Q2(i). "Zero-lift angle of attack required to trim" is read as the wing's zero-lift angle $\alpha_0$ (a camber choice) that makes $\eta=0$ at 86 m/s, with $\alpha_s=0$, so that the tail incidence is set by the wing incidence and downwash alone.
- Q3(v). The formula on the paper is the improved phugoid approximation of Chapter 6 §6.6, lectured on Mon 16 Nov; the solution here relies on the written-ahead derivation in [[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes|the Deep Dive]].
