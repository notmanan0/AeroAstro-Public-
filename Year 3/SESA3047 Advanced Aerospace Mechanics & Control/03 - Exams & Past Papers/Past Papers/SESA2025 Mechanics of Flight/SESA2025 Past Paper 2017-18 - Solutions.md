---
title: "SESA2025 Past Paper 2017-18 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, high-wing, manoeuvre-margin, static-margin, high-lift, take-off, trim-drag, stability-quartic, spo, phugoid, handling-qualities, roll-damping, lateral-modes]
paper: "2017-18"
theory_notes: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M11 - Longitudinal Trim and Static Stability]]", "[[Lateral and Directional Stability]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-201718-02-SESA2025W1.pdf"]
---

# SESA2025 Past Paper 2017-18 - Solutions

> [!abstract] Paper info
> SESA2025 Mechanics of Flight, Semester 2 examination 2017-18 (120 min, formula sheet on pp. 7–8, the same as 2016-17). Three compulsory questions: Q1 is worth 40 marks, Q2 and Q3 30 each. Q1 has no mean chord in its table; $c=S/b=1.961$ m is used throughout (see [[#Paper slips and ambiguities]]). Q2 is the longitudinal stability quartic (SESA3047 6.1); Q3 is roll damping and the lateral modes (SESA3047 §§6.7–6.10, Thu 19 Nov 2026), with Q3(iii) read from the printed response plots. All numbers were checked in Python.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 40 | High wing and lateral stability; tail incidence in curved flight; stick-fixed manoeuvre and static margins at take-off; take-off speed, $\alpha$ and $\eta$ at $C_{L\max}$; optimal trim at $(C_L^{0.5}/C_D)_{\max}$ | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability|SESA2022 T6 §3–4, §6]], [[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2]] (trim drag), [[SESA1015 M11 - Longitudinal Trim and Static Stability|SESA1015 M11]] |
| 2 | 30 | Factorising the stability quartic; SPO and phugoid properties; handling qualities; phugoid height change | [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#Two quadratics, two modes|SESA3047 6.1 §2–3]], [[SESA3047 6.2 - Phugoid Approximation#2. Lanchester's approximation (6.28–6.33)|6.2 §2]] (§6.6, due Mon 16 Nov) |
| 3 | 30 | Strip-theory roll damping $L_p$; roll time constant; lateral modes in a measured response | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[Lateral and Directional Stability]] |

---

## Q1. Take-off stability, high-lift trim and optimal trim (40 marks)

> (i) Discuss two effects of a high wing on lateral stability. [4]
> (ii) Show how for curved flight the effective angle of the tailplane changes by $\Delta\gamma=l/R$. [4]
> (iii) Taking off with slats deployed, with $A=7.8$, $S=30$ m², $e=0.80$, $A_T=5.6$, $S_T=6.0$ m², $e_T=0.65$, $l=5.0$ m, $\alpha_s=-6.0^\circ$, $h=0.50$, $C_{L,\max}=2.1$, $\alpha_0=-9.0^\circ$, $h_{0,\text{slats}}=0.15$, $m=1000$ kg, $\rho=1.2$ kg/m³, $g=9.81$ m/s², $C_{M_0}=-0.010$, $C_{L_T}=2\pi\alpha_{T_{eff}}+2.5\eta$, $C_{D_0}=0.004$, determine the stick-fixed manoeuvre margin $H_m$ at take-off. [9]
> (iv) Is the aircraft safe to fly stick fixed in that configuration? Explain. [8]
> (v) Now taking off with flaps, $h_{0,\text{flaps}}=0.35$, with $R=500$ m: find $V$, $\alpha$ and $\eta$. [8]
> (vi) Cruising at $(C_L^{0.5}/C_D)_{\max}$ with $h_0=0.25$: determine whether it is possible to fly at optimal trim, stick fixed. [7]

### (i) Two effects of a high wing [4 marks]

A high wing behaves like extra dihedral. First, fuselage cross-flow: in a sideslip the flow round the fuselage moves upwards on the upwind side of the body and downwards on the downwind side. On a high wing the upwind wing root sits in that upflow and gains incidence, while the downwind root loses it, so the aircraft rolls away from the sideslip, which is restoring ($L_v$ more negative). On a low wing the effect reverses, which is why low-wing aircraft carry more geometric dihedral. Second, the keel (pendulum) effect: with the wing, and the side force on the fin and fuselage, acting above a low-slung CG, a sideslip produces a side force above the CG and a rolling moment that again lifts the down-going wing. The combination can give too much lateral stability, a poorly damped Dutch roll and heavy roll control, so high-wing transports (An-124, C-5, BAe 146) use anhedral.

### (ii) The tail incidence change in curved flight [4 marks]

On a circular path of radius $R$ at speed $V$ the aircraft rotates at $q=V/R$, the rate at which the flight-path direction turns. The tail, a distance $l$ behind the wing, sits at a point of the circle that is an arc $l$ further back. The arc subtends the angle

$$
\Delta\gamma=\frac lR
$$

at the centre, so the flight-path direction at the tail differs from that at the wing by $l/R$: the local flow at the tail comes up from below more steeply than at the wing. Equivalently, in a frame moving with the wing, the tail moves downwards at $ql$ as the aircraft pitches, and adding that velocity to the stream $V$ inclines the relative wind at the tail by

$$
\tan\Delta\alpha_T=\frac{ql}{V}=\frac{(V/R)\,l}{V}=\frac lR,
$$

so for small angles the tail incidence rises by $\Delta\gamma=l/R$, which is the $+l/R$ term in the sheet's $\alpha_{T_{eff}}$ (assuming $l\gg(h-h_0)c$, so the CG-to-tail arm is close to $l$).

### (iii) Stick-fixed manoeuvre margin at take-off [9 marks]

**Assumption.** $c$ is not given; for a rectangular wing $b=\sqrt{AS}=\sqrt{234}=15.297$ m and $c=S/b=1.9612$ m.

The constants:

$$
Ae=6.24,\qquad C_{L_\alpha}=\frac{2\pi(6.24)}{8.24}=4.7581,\qquad\epsilon_\alpha=\frac{2}{8.24}=0.24272,
$$

$$
A_Te_T=3.64,\qquad k=\frac{2\pi(3.64)}{5.64}=4.0551,
$$

$$
K=\frac{S_Tl}{Sc}=\frac{6\times5}{30\times1.9612}=0.50990,\qquad s=0.2,\qquad\Phi=\frac{\rho Sl}{2m}=\frac{1.2\times30\times5}{2000}=0.090.
$$

The manoeuvre tail slope:

$$
C_{L_{T\alpha}}=\frac{k(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{1-k\Phi s}=\frac{4.0551(0.75728+0.42823)}{1-4.0551\times0.09\times0.2}=\frac{4.8073}{0.92701}=5.1859,
$$

$$
C^*_{L_\alpha}=4.7581+0.2\times5.1859=5.7953,
$$

$$
H_m=h_0-h+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=0.15-0.50+0.50990\times\frac{5.1859}{5.7953}=-0.35+0.45628=\boxed{0.106}.
$$

### (iv) Is it safe to fly stick fixed? [8 marks]

The manoeuvre margin is positive, but manoeuvring is the easy case: pitch damping always adds to the margin, so the critical condition is straight flight. The straight, stick-fixed tail slope is

$$
C_{L_{T\alpha}}=k(1-\epsilon_\alpha)=4.0551\times0.75728=3.0709,\qquad C^*_{L_\alpha}=4.7581+0.2\times3.0709=5.3723,
$$

$$
H=h_0-h+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=0.15-0.50+0.50990\times\frac{3.0709}{5.3723}=-0.35+0.29146=\boxed{-0.059}.
$$

The stick-fixed neutral point is at $h_n=0.441$, ahead of the CG at $h=0.50$, so in straight flight the aircraft is statically unstable: $dC_{M_{CG}}/d\alpha=-C^*_{L_\alpha}H=+0.31$ rad⁻¹, and any nose-up disturbance grows. It is **not safe** to fly in this configuration. Deploying the slats moved the wing AC forward (from $h_0=0.25$ to 0.15), which cut the margin by 0.1. A stick-free margin would be smaller still, and the take-off is the phase where a pilot has least margin for error. The aircraft would need the CG moved forward of $h=0.44$ (by about $0.06c$ for a modest margin, more for a usable one), a larger tail or longer arm, or artificial stability through a flight-control system.

### (v) Take-off with flaps: speed, incidence and elevator [8 marks]

**Assumptions.** Wing at $C_{L,\max}=2.1$ with $\alpha_0=-9^\circ$; level path at the bottom of the rotation arc ($\gamma=0$); stick fixed; $c=1.9612$ m.

Total lift coefficient at wing $C_{L\max}$ (moment balance, as derived in [[SESA2025 Past Paper 2015-16 - Solutions#Q1. Sweep, aspect ratio, manoeuvre margin and high-lift trim (25 marks)|2015-16 Q1(iv)]]):

$$
C^*_{L\max}=\frac{C_{L\max}+C_{M_0}c/l}{1-(c/l)(h-h_0)}=\frac{2.1-0.01(0.39223)}{1-0.39223(0.15)}=\frac{2.09608}{0.94117}=2.2271.
$$

Speed from $C_L^*=C_W(\cos\gamma+n)$ with $n=V^2/(gR)$:

$$
V=\sqrt{\frac{g\cos\gamma}{C^*_{L\max}\rho S/(2m)-1/R}}=\sqrt{\frac{9.81}{2.2271\times0.018-0.002}}=\sqrt{\frac{9.81}{0.038088}}=\boxed{16.0\ \text{m/s}}.
$$

The tail lift and incidence:

$$
C_{L_T}=\frac{C^*_{L\max}-C_{L\max}}{s}=\frac{0.12711}{0.2}=0.63555,
$$

$$
\alpha=\alpha_0+\frac{C_{L\max}}{C_{L_\alpha}}=-9.0^\circ+\frac{2.1}{4.7581}\ \text{rad}=-9.0^\circ+25.29^\circ=\boxed{16.29^\circ}\ (0.28427\ \text{rad}).
$$

The effective tail incidence with $l/R=0.01$:

$$
\alpha_{T_{eff}}=0.75728(0.28427)+0.24272(-0.15708)-0.10472-\frac{0.63555}{\pi(3.64)}+0.01,
$$

$$
\alpha_{T_{eff}}=0.21527-0.03813-0.10472-0.05558+0.01=0.02685\ \text{rad}\ (1.54^\circ).
$$

$$
\eta=\frac{C_{L_T}-2\pi\alpha_{T_{eff}}}{2.5}=\frac{0.63555-0.16870}{2.5}=0.18674\ \text{rad}=\boxed{10.70^\circ}.
$$

With the flaps moving the AC aft ($h_0=0.35$) the tail must carry a large upload ($C_{L_T}=0.64$) and the elevator is deflected trailing-edge down. The speed is low because the wing loading is only 33 kg/m².

### (vi) Optimal trim in cruise [7 marks]

Optimal trim means the CG at $h_{opt}$, where the tail's share of the lift minimises the induced drag ([[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2(b)]]). With $h_0=0.25$ (clean wing):

$$
\sigma=\frac{SAe}{S_TA_Te_T}+1=\frac{30\times6.24}{6\times3.64}+1=8.5714+1=9.5714.
$$

The trimmed polar is $C_D=C_{D_0}+K'C_L^{*2}$ with

$$
K'=\frac{1-1/\sigma}{\pi Ae}=\frac{0.89552}{19.604}=0.045682.
$$

The maximum of $C_L^{1/2}/C_D$ (from $x=2K'C^2/(C_{D_0}+K'C^2)$ with $x=\tfrac12$) is at $K'C_L^{*2}=C_{D_0}/3$:

$$
C_L^*=\sqrt{\frac{0.004}{3\times0.045682}}=0.17084.
$$

The CG for optimal trim:

$$
h_{opt}=h_0-\frac{C_{M_0}}{C_L^*}+\frac{l}{c\sigma}=0.25+\frac{0.010}{0.17084}+\frac{5}{1.9612\times9.5714}=0.25+0.05853+0.26637=0.575.
$$

The stick-fixed neutral point with the clean wing is

$$
h_n=h_0+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=0.25+0.29146=0.541.
$$

So $h_{opt}=0.575$ lies behind $h_n=0.541$: placing the CG there would give $H=-0.033$, a statically unstable aircraft. Optimal trim is **not possible** stick fixed. (At the actual CG, $h=0.50$, the clean aircraft has a margin of $+0.041$, which is stable but not trimmed for minimum drag.) The low $C_L^*$ of this cruise condition makes the $-C_{M_0}/C_L^*$ term large and pushes $h_{opt}$ aft; flying faster than the range speed makes it worse.

---

## Q2. The longitudinal stability quartic (30 marks)

> The stability quartic is $\lambda^4+0.8\lambda^3+1.01\lambda^2+0.008\lambda+0.01=0$.
> (i) Verify that it factors as $(\lambda^2+0.8\lambda+1)(\lambda^2+0.01)=0$ and state which factor is the SPO and which the phugoid. [4]
> (ii) For the SPO find the frequency, half-life, undamped natural frequency and damping factor. [6]
> (iii) Repeat for the phugoid. [6]
> (iv) Describe the main features of the SPO and phugoid and discuss their handling-quality requirements. [8]
> (v) In a phugoid $\theta=0.02\cos(\omega t)$. Ignoring incidence changes and with $\omega=g\sqrt2/U_\infty$, find the change in altitude from lowest to highest point. [6]

### (i) Factorisation [4 marks]

Multiply out:

$$
(\lambda^2+0.8\lambda+1)(\lambda^2+0.01)=\lambda^4+0.01\lambda^2+0.8\lambda^3+0.008\lambda+\lambda^2+0.01,
$$

$$
=\lambda^4+0.8\lambda^3+1.01\lambda^2+0.008\lambda+0.01,
$$

which is the quartic. The factor $\lambda^2+0.8\lambda+1$ has the larger natural frequency and heavy damping, so it is the **SPO**; $\lambda^2+0.01$ is slow and undamped, so it is the **phugoid** ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#Two quadratics, two modes|6.1 §2]]).

### (ii) SPO properties [6 marks]

Compare $\lambda^2+0.8\lambda+1$ with $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2$:

$$
\omega_n=\sqrt1=\boxed{1.0\ \text{rad/s}},\qquad\zeta=\frac{0.8}{2\times1}=\boxed{0.40}.
$$

The roots are

$$
\lambda=-0.4\pm i\sqrt{1-0.16}=-0.4\pm0.9165i,
$$

so the damped frequency is $\omega=\boxed{0.917\ \text{rad/s}}$ (period $2\pi/0.9165=6.86$ s) and the half-life is

$$
t_{1/2}=\frac{\ln2}{0.4}=\boxed{1.73\ \text{s}}.
$$

### (iii) Phugoid properties [6 marks]

Compare $\lambda^2+0\lambda+0.01$:

$$
\omega_n=\sqrt{0.01}=\boxed{0.10\ \text{rad/s}},\qquad\zeta=\boxed{0},\qquad\lambda=\pm0.1i.
$$

The frequency is $\omega=0.10$ rad/s (period 62.8 s). With zero real part the oscillation neither grows nor decays: the phugoid is neutrally stable and its half-life is infinite.

### (iv) Features and handling qualities [8 marks]

The **SPO** is a rapid pitching oscillation about the CG at nearly constant speed: incidence and pitch attitude change together, so the flight path barely bends and the height hardly changes. Its stiffness comes from the static margin ($M_w$) and its damping from the tail's pitch damping ($M_q$), the downwash lag ($M_{\dot w}$) and the lift slope ($Z_w$). It sets the aircraft's response to the stick and to gusts. It must be well damped and of suitable frequency: MIL-F-8785C Level 1 asks for $0.35\le\zeta_{sp}\le1.30$ in precision and terminal phases (0.30 to 2.0 in cruise), with $\omega_{sp}$ within limits tied to the normal acceleration per unit incidence, and CS-25 requires a heavily damped short period. This SPO, $\zeta=0.40$, $\omega_n=1$ rad/s, is acceptable, though slow for a fighter.

The **phugoid** is a slow exchange of kinetic and potential energy at nearly constant incidence: the aircraft climbs and slows, dives and speeds up, with $\theta\approx\gamma$. Drag variation provides its weak damping. Because it is slow, a pilot corrects it almost unconsciously, so the requirements are lenient: Level 1 needs $\zeta_{ph}\ge0.04$, Level 2 $\zeta_{ph}\ge0$, and Level 3 accepts an unstable phugoid with a time to double of at least 55 s. This phugoid, $\zeta=0$, is only Level 2: tolerable in visual flight, but it adds workload on instruments and needs speed or height hold from an autopilot.

### (v) Height change in the phugoid [6 marks]

**Assumptions.** Incidence constant, so the climb angle equals the pitch angle, $\gamma=\theta-\alpha=\theta$ (perturbations); small angles; speed close to $U_\infty$.

The rate of climb is

$$
\dot h=U_\infty\sin\gamma\approx U_\infty\theta=0.02\,U_\infty\cos\omega t.
$$

Integrate:

$$
h=\frac{0.02\,U_\infty}{\omega}\sin\omega t+\text{const},
$$

so the height swings by $\pm0.02U_\infty/\omega$ and the change from lowest to highest point is

$$
\Delta h=\frac{0.04\,U_\infty}{\omega}.
$$

The phugoid frequency is $\omega=0.1$ rad/s from part (iii), so Lanchester's relation gives the speed:

$$
U_\infty=\frac{g\sqrt2}{\omega}=\frac{9.81\times1.4142}{0.1}=138.7\ \text{m/s},
$$

$$
\Delta h=\frac{0.04\times138.7}{0.1}=\boxed{55.5\ \text{m}}.
$$

A pitch swing of only $\pm1.15^\circ$ moves the aircraft through 55 m of height every 63 s.

---

## Q3. Roll damping and the lateral response (30 marks)

> (i) By considering the lift and drag on a strip $dy$ at distance $y$ from the centreline, derive
> $$L_p=-\frac{1}{Sb^2}\int_{-s}^{s}(C_{L_\alpha}+C_D)\,c\,y^2\,dy.$$ [10]
> (ii) A simple rolling model is $I_{xx}\dot p=\mathring L_pp$. A rectangular wing of span $b=8$ m ($b=2s$) and chord $c=1$ m, $I_{xx}=1025$ kg m², flies at 70 m/s near sea level ($\rho=1.225$ kg/m³) with $C_{L_\alpha}=4.7$, $C_D=0.03$. Find (a) $L_p$, (b) $\mathring L_p$, (c) the roll time constant. [12]
> (iii) Figure Q3 shows roll rate and bank angle after a step aileron held for 5 s and then removed, on short, medium and long time scales. Explain the role of the lateral modes, with rough estimates of their properties. [8]

### (i) Strip-theory roll damping [10 marks]

**Assumptions.** Strip theory: each spanwise strip behaves as a two-dimensional section in the local flow, with no induced effects from neighbouring strips; small angles; positive roll rate $p$ puts the starboard wing ($y>0$) down; the section has lift slope $C_{L_\alpha}$ and drag coefficient $C_D$ (independent of the small incidence change).

Rolling at $p$, the strip at $y$ moves downwards at $py$. Relative to the strip the air then comes up from below, so its incidence rises by

$$
\Delta\alpha=\frac{py}{V}.
$$

The lift on the strip, normal to the local relative wind, rises by

$$
dL=\tfrac12\rho V^2c\,dy\,C_{L_\alpha}\Delta\alpha.
$$

The local relative wind is also tilted by $\Delta\alpha$, so the lift (normal to it) and the drag (along it) are both rotated. The force normal to the wing plane is

$$
dZ=dL\cos\Delta\alpha+dD\sin\Delta\alpha\approx dL+dD\,\Delta\alpha,
$$

and with $dD=\tfrac12\rho V^2c\,dy\,C_D$ the increment in normal force is

$$
dZ=\tfrac12\rho V^2c\,dy\left(C_{L_\alpha}+C_D\right)\frac{py}{V}=\tfrac12\rho V\left(C_{L_\alpha}+C_D\right)c\,y\,p\,dy.
$$

This force is upward on the down-going starboard wing and downward on the up-going port wing ($y<0$), so both oppose the roll. Its rolling moment, positive starboard-wing-down, is $-y\,dZ$:

$$
d\mathcal L=-\tfrac12\rho V\left(C_{L_\alpha}+C_D\right)c\,y^2\,p\,dy.
$$

Integrate across the span:

$$
\mathcal L=-\tfrac12\rho V\,p\int_{-s}^{s}\left(C_{L_\alpha}+C_D\right)c\,y^2\,dy,
$$

$$
\mathring L_p=\frac{\partial\mathcal L}{\partial p}=-\tfrac12\rho V\int_{-s}^{s}\left(C_{L_\alpha}+C_D\right)c\,y^2\,dy.
$$

The dimensionless derivative uses the lateral reference $\tfrac12\rho VSb^2$ (rolling moment $\tfrac12\rho V^2Sb$, rate $V/b$):

$$
\boxed{L_p=\frac{\mathring L_p}{\tfrac12\rho VSb^2}=-\frac{1}{Sb^2}\int_{-s}^{s}\left(C_{L_\alpha}+C_D\right)c\,y^2\,dy.}
$$

The $y^2$ weighting shows that the tips provide most of the damping.

### (ii) Roll damping of the rectangular wing [12 marks]

(a) With constant $c$, $C_{L_\alpha}$ and $C_D$:

$$
\int_{-s}^{s}y^2\,dy=\frac{2s^3}{3},\qquad L_p=-\frac{(C_{L_\alpha}+C_D)\,c\,2s^3}{3Sb^2}.
$$

With $S=bc=2sc$ and $b=2s$, this simplifies to $L_p=-(C_{L_\alpha}+C_D)/12$:

$$
L_p=-\frac{4.7+0.03}{12}=\boxed{-0.394}.
$$

(The long form: $2\times4^3/3=42.67$, $(4.73)(1)(42.67)=201.81$, $Sb^2=8\times64=512$, $-201.81/512=-0.3942$.)

(b) The dimensional derivative:

$$
\tfrac12\rho VSb^2=0.5\times1.225\times70\times8\times64=21\,952\ \text{kg m}^2/\text{s},
$$

$$
\mathring L_p=21\,952\times(-0.39417)=\boxed{-8653\ \text{N m s/rad}}.
$$

(c) The model $I_{xx}\dot p=\mathring L_pp$ has the solution $p=p_0e^{\mathring L_pt/I_{xx}}$, so the roll-subsidence time constant is

$$
\tau=\frac{I_{xx}}{|\mathring L_p|}=\frac{1025}{8653}=\boxed{0.118\ \text{s}}
$$

(eigenvalue $-8.44$ s⁻¹, half-time 0.082 s). The roll rate settles within about $3\tau=0.36$ s.

### (iii) The lateral modes in the measured response [8 marks]

The three time scales of Figure Q3 each show one mode. Readings from the printed plots, good to about 5 %:

| Time scale | Reading | Mode and estimate |
|---|---|---|
| 0–0.5 s, roll rate | $p$ rises smoothly to $-0.0328$ rad/s with no overshoot; 63 % ($-0.0207$) at $t\approx0.09$ s | Roll subsidence: $\tau\approx0.1$ s ($\lambda\approx-10$ s⁻¹) |
| 0–0.5 s, bank | $\phi$ starts quadratically, then grows linearly at $\approx-0.033$ rad/s | Steady roll rate integrates to a ramp |
| 0–5 s, roll rate | oscillation about $\approx-0.028$: troughs at 0.45 s and 2.85 s, peaks at 1.53 s and 4.25 s; peak-to-trough 0.0065, 0.0035, 0.0023 rad/s | Dutch roll: $T\approx2.6$–2.8 s, $\omega\approx2.4$ rad/s, half-cycle ratio $\approx0.6$, $\zeta\approx0.16$, half-life $\approx1.8$ s |
| 5–50 s, bank | after the aileron returns at 5 s, $\phi$ peaks at $-0.144$ and decays smoothly: $-0.140$ at 10 s, $-0.097$ at 50 s | Spiral, stable: $\lambda\approx\ln(0.097/0.140)/40=-0.0091$ s⁻¹, half-life $\approx76$ s |

The step aileron first produces the **roll subsidence**: the roll rate builds up exponentially to the value at which roll damping balances the aileron moment, here in about 0.1 s, close to the strip-theory value of part (ii). The bank angle therefore ramps up. Within the first seconds the sideslip produced by the bank excites the **Dutch roll**, which appears as a decaying oscillation of period about 2.7 s superimposed on the roll rate, damped out within about 5 s. When the aileron is removed at 5 s the roll rate drops back towards zero (with a further small Dutch-roll wobble), and the bank of $-0.14$ rad is then left to the **spiral** mode, which here is stable but slow: the bank decays to about two-thirds in 45 s, a half-life of roughly 75 s, during which the aircraft keeps turning. The small positive roll rate seen from 10 s to 50 s is that slow spiral recovery.

---

## Paper slips and ambiguities

- Q1(iii)–(vi). The table gives no mean chord $c$, which is needed for $K=S_Tl/(Sc)$, $C^*_{L\max}$ and $h_{opt}$. A rectangular planform, $c=S/b=S/\sqrt{AS}=1.961$ m, is assumed. With $c=1$ m instead, $K$ nearly doubles and the conclusion of (iv) changes ($H=+0.22$, $H_m=0.55$ at take-off), although in (vi) $h_{opt}=0.831$ would still lie just behind $h_n=0.822$; the answers depend on this assumption.
- Q1(iii). The table's $\alpha_0=-9^\circ$ and $C_{L,\max}=2.1$ are used for the flapped take-off in (v) as well; the paper gives no separate flapped values.
- Q1(v). The flight-path angle at take-off is taken as zero (bottom of the rotation arc).
- Q1(vi). $(C_L^{0.5}/C_D)_{\max}$ is evaluated with the trimmed polar in $C_L^*$; using the wing $C_L$ gives the same $C_L^*$ because $C_L\propto C_L^*$ at optimal trim.
- Q3(ii). The pdftotext layer reads "$C_L=4.7$", but the printed paper has $C_{L_\alpha}=4.7$, which is used.
