---
title: "SESA2025 Past Paper 2014-15 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, aileron-reversal, induced-drag, static-margin, manoeuvre-margin, stick-free, winglets, trim-drag, spo, phugoid, stability-augmentation, lateral-modes, roll-subsidence]
paper: "2014-15"
theory_notes: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-201415-02-SESA2025W1.pdf"]
---

# SESA2025 Past Paper 2014-15 - Solutions

> [!abstract] Paper info
> SESA2025 Mechanics of Flight, Semester 2 examination 2014-15 (120 min, equations sheet on pp. 8–10), four questions of 25 marks, answer all. Q1(iv) uses the aircraft of [[SESA2025 Past Paper 2013-14 - Solutions#Q1. Sweep, induced drag, adverse yaw, wave drag and the stick-free manoeuvre margin (25 marks)|2013-14 Q1(e)]], and Q3 uses the 2013-14 longitudinal matrix with a pitch-damper term $\mu$. Q4 is the lateral modes (SESA3047 §§6.7–6.10, Thu 19 Nov 2026). All numbers were checked in Python; the printed phugoid eigenvalues in Q3 do not match the matrix.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Aileron reversal; induced-drag ratio; static-margin derivation; mass for a stick-free manoeuvre margin $H_m=0.2$ | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#3. Longitudinal static stability|SESA2022 T6 §3–4]], [[Neutral Point and Static Margin]], [[Manoeuvre Point and Manoeuvre Margin]] |
| 2 | 25 | Winglet drag derivation, drag polar at minimum trim drag, cruise exponent $x$ for $h_{opt}=0.685$, stick-fixed trim | [[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2]] (trim-drag derivation), [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|SESA1015 M05]] |
| 3 | 25 | Longitudinal modes; SPO approximation with pitch damping $\mu$; pitch-equilibrium phugoid approximation | [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|SESA3047 6.1]], [[SESA3047 6.2 - Phugoid Approximation#4. The improved approximation (6.34–6.38)|6.2 §4]] (§6.6, due Mon 16 Nov) |
| 4 | 25 | Lateral modes, effect of dihedral, yaw-only wind-tunnel oscillation, pure-roll step response | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[Lateral and Directional Stability]] |

---

## Q1. Aileron reversal, induced drag, static margin and manoeuvre margin (25 marks)

> (i) Describe using a sketch the aileron reversal phenomenon and list two ways to eliminate it. [3]
> (ii) Aircraft A cruises at 50 m/s with span 10 m and mass 1000 kg; aircraft B cruises at 70 m/s with span 15 m and mass 2500 kg; both at 3000 m with the same Oswald efficiency. Find the ratio of their induced drags $(C^*_{D_{iA}}/C^*_{D_{iB}})$. [5]
> (iii) Using Figure Q.1 (wing AC at $h_0c$, CG at $hc$, tail AC a distance $l$ behind the wing AC) and the equations sheet, derive the static margin equation. [7]
> (iv) The aircraft (Table Q.1: $A=7$, $S=25$ m², $c=1.8$ m, $e=0.85$, $l=5$ m, $\rho=1$ kg/m³, $e_T=0.75$, $S_T=4$ m², $A_T=5$, $h=0.40$, $h_0=0.25$, $C_{L_T}=2\pi\alpha_{T_{eff}}+3\eta+0.9\beta$, $C_H=-0.5\alpha_{T_{eff}}-0.75\eta-1.25\beta$) manoeuvres stick free. Find the mass that gives $H_m^{free}=0.2$. [10]

### (i) Aileron reversal [3 marks]

![[amc_pp_201415_q1_aileron_reversal.png|900]]

A down-going aileron adds camber and lift to the outer wing, but that extra lift acts near the trailing edge, well behind the wing's flexural axis. It therefore also twists the flexible wing nose-down, which lowers the incidence of the whole outer section and removes lift. The aileron lift grows with $q=\tfrac12\rho V^2$, and so does the twisting moment, while the torsional stiffness stays fixed, so the loss from twist grows faster with speed than the gain from camber. At the reversal speed the two cancel and the aileron produces no rolling moment; above it the aircraft rolls the wrong way.

Two remedies: stiffen the wing in torsion (or move the flexural axis aft, closer to the aileron load), and move roll control inboard at high speed, using inboard ailerons or spoilers (which act near the stiff root and produce less twist), or an all-moving tail differentially (taileron).

### (ii) Ratio of induced drags [5 marks]

From [[SESA2025 Past Paper 2013-14 - Solutions#Q1. Sweep, induced drag, adverse yaw, wave drag and the stick-free manoeuvre margin (25 marks)|2013-14 Q1(b)]], in level cruise ($L=W$)

$$
D_i=\frac{W^2}{\pi e\,q\,b^2},\qquad q=\tfrac12\rho V^2.
$$

Both aircraft fly at 3000 m with the same $e$, so $\rho$ and $\pi e$ cancel in the ratio:

$$
\frac{D_{iA}}{D_{iB}}=\left(\frac{W_A}{W_B}\right)^2\left(\frac{V_B}{V_A}\right)^2\left(\frac{b_B}{b_A}\right)^2.
$$

Substitute ($g$ cancels in the weight ratio):

$$
\frac{D_{iA}}{D_{iB}}=\left(\frac{1000}{2500}\right)^2\left(\frac{70}{50}\right)^2\left(\frac{15}{10}\right)^2=0.16\times1.96\times2.25=\boxed{0.706}.
$$

Aircraft A, although lighter, has 71 % of B's induced drag, because it is slower (higher $C_L$) and has a shorter span. The ratio of induced drag coefficients needs the wing areas, which are not given: since $C_{D_i}=D_i/(qS)$,

$$
\frac{C_{D_{iA}}}{C_{D_{iB}}}=\frac{D_{iA}}{D_{iB}}\,\frac{q_BS_B}{q_AS_A}=0.706\times1.96\times\frac{S_B}{S_A}=1.38\,\frac{S_B}{S_A}.
$$

### (iii) Derivation of the static margin [7 marks]

**Assumptions.** Small angles; thrust and drag act through the CG; the tail is symmetric ($M_{T_0}=0$); lift slopes are linear; distances are measured aft from the datum as fractions of $c$; nose-up moments positive.

Take moments about the CG. The wing lift $L$ acts at $h_0c$, a distance $(h-h_0)c$ ahead of the CG, so it pitches the nose up; the tail lift $L_T$ acts $l-(h-h_0)c$ behind the CG and pitches the nose down; the wing has its zero-lift moment $M_0$:

$$
M_{CG}=M_0+L(h-h_0)c-L_T\left[l-(h-h_0)c\right].
$$

Collect the $(h-h_0)c$ terms:

$$
M_{CG}=M_0+(L+L_T)(h-h_0)c-L_Tl.
$$

Divide by $\tfrac12\rho V^2Sc$, with $C_L^*=C_L+C_{L_T}S_T/S$ and $K=S_Tl/(Sc)$:

$$
C_{M_{CG}}=C_{M_0}+C_L^*(h-h_0)-KC_{L_T}.
$$

Static stability requires a nose-down moment when $\alpha$ increases. Differentiate, with $C_{M_0}$ constant (moment about the AC):

$$
\frac{dC_{M_{CG}}}{d\alpha}=C^*_{L_\alpha}(h-h_0)-KC_{L_{T\alpha}},\qquad C^*_{L_\alpha}=C_{L_\alpha}+C_{L_{T\alpha}}\frac{S_T}{S}.
$$

The neutral point $h_n$ is the CG position that makes this slope zero:

$$
C^*_{L_\alpha}(h_n-h_0)=KC_{L_{T\alpha}}\quad\Rightarrow\quad h_n=h_0+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}.
$$

The static margin is the distance of the CG ahead of the neutral point:

$$
\boxed{H=h_n-h=h_0-h+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}},\qquad\frac{dC_{M_{CG}}}{d\alpha}=-C^*_{L_\alpha}H,
$$

so the aircraft is statically stable when $H>0$.

The tail slope comes from $C_{L_T}=2\pi\alpha_{T_{eff}}+a_2\eta$ (stick fixed) with the sheet's $\alpha_{T_{eff}}=(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-C_{L_T}/(\pi A_Te_T)$ in straight flight. $C_{L_T}$ appears on both sides:

$$
C_{L_T}\left(1+\frac{2\pi}{\pi A_Te_T}\right)=2\pi\left[(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s\right]+a_2\eta.
$$

Differentiate at fixed $\eta$ and simplify $1+2/(A_Te_T)=(A_Te_T+2)/(A_Te_T)$:

$$
C_{L_{T\alpha}}=\frac{2\pi A_Te_T}{A_Te_T+2}(1-\epsilon_\alpha),
$$

the sheet's stick-fixed entry. Stick free, $2\pi$ is replaced by $\bar a_1$ ([[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Tail lift slope, stick fixed: derivation|SESA2022 T6 §3]]).

### (iv) Mass for a stick-free manoeuvre margin of 0.2 [10 marks]

The algebra is that of [[SESA2025 Past Paper 2013-14 - Solutions#Q1. Sweep, induced drag, adverse yaw, wave drag and the stick-free manoeuvre margin (25 marks)|2013-14 Q1(e)]], which showed that in a manoeuvre

$$
K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=\frac{K\bar k(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)}.
$$

Now $l$ is known and $m$ enters only through $\Phi=\rho Sl/(2m)$, so the equation is linear in $\Phi$. Setting $H_m=0.2$:

$$
1-\epsilon_\alpha+\Phi C_{L_\alpha}=\frac{(H_m+h-h_0)\left[C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)\right]}{K\bar k}.
$$

The aircraft constants are those of 2013-14 Q1(e): $C_{L_\alpha}=4.7025$, $\epsilon_\alpha=0.25157$, $\bar a_1=2\pi-a_3b_1/b_3=5.9232$, $\bar k=3.9415$, $s=0.16$, and $C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)=5.1745$. The tail volume is

$$
K=\frac{S_Tl}{Sc}=\frac{4\times5}{25\times1.8}=0.44444.
$$

So

$$
1-\epsilon_\alpha+\Phi C_{L_\alpha}=\frac{0.35\times5.1745}{0.44444\times3.9415}=\frac{1.81108}{1.75178}=1.03385,
$$

$$
\Phi=\frac{1.03385-0.74843}{4.7025}=0.060695,
$$

$$
m=\frac{\rho Sl}{2\Phi}=\frac{1\times25\times5}{2\times0.060695}=\boxed{1030\ \text{kg}}.
$$

> [!check] Back-substitution
> $C_{L_{T\alpha}}=3.9415(0.74843+0.28542)/(1-3.9415\times0.060695\times0.16)=4.0749/0.96172=4.2371$, $C^*_{L_\alpha}=4.7025+0.16\times4.2371=5.3804$, and $H_m=0.25-0.40+0.44444\times4.2371/5.3804=0.200$.

A heavier aircraft has a smaller $\Phi$, less pitch damping from the tail and a smaller manoeuvre margin; at $m=1030$ kg the margin is 0.2, while the straight-flight stick-free margin of the same aircraft is only $H=0.103$. With a floating elevator ($\bar a_1=4.2832$) the required mass is 560 kg (see [[#Paper slips and ambiguities]]).

---

## Q2. Winglet drag, drag polar and optimal trim (25 marks)

> A conventional aircraft with winglets cruises with its CG at the position that minimises trim drag, stick fixed. Table Q.2: $A=6.5$, $e=0.9$, $S=12$ m²; $A_T=4$, $e_T=0.8$, $S_T=4$ m²; $A_w=4$, $e_w=0.6$, $S_w=1.5$ m²; $h_0=0.25$, $C_{M_0}=0.015$, $C_{D_0}=0.006$, $C_{D_{w0}}=0.002$; $\alpha_s=-5^\circ$, $c=2$ m, $l=6$ m; $\rho=0.9$ kg/m³, $m=1500$ kg, $g=9.81$ m/s²; $C_{L_T}=2\pi\alpha_{T_{eff}}+4\eta$.
> (i) Using Figure Q.2 (winglet in the sidewash $v_w$, at incidence $\alpha_w$, with lift $L_w$ and drag $D_w$) derive the winglet drag and show that
> $$\Delta C_D=\frac{S_w}{S}\left[C_{D_{w0}}-\frac{8\pi\alpha^2}{(Ae+2)^2}\left(\frac{A_we_w}{A_we_w+2}\right)^2\right].$$ [8]
> (ii) Work out the drag polar. [5]
> (iii) The aircraft cruises at $(C_L^{*x}/C_D)_{\max}$. Find $x$ for $h_{opt}=0.685$. [7]
> (iv) Calculate $\alpha$, $\eta$ and the cruising speed. [5]

### (i) Winglet drag [8 marks]

![[amc_pp_201314_q2_winglet.png|900]]

**Assumptions.** The winglet sits in the wing's tip sidewash, and that sidewash angle equals the wing's induced angle; the winglet behaves as a small finite wing with lift slope $2\pi A_we_w/(A_we_w+2)$; small angles; winglet force coefficients are based on $S_w$ and converted to the wing area $S$ at the end.

The wing's induced angle, with the sheet's lift slope $C_{L_\alpha}=2\pi Ae/(Ae+2)$ and $\alpha_0=0$, is

$$
\alpha_w=\frac{C_L}{\pi Ae}=\frac{1}{\pi Ae}\,\frac{2\pi Ae}{Ae+2}\,\alpha=\frac{2\alpha}{Ae+2}.
$$

The winglet meets the local flow (free stream plus inboard sidewash $v_w$) at $\alpha_w=v_w/V$, so its lift coefficient is

$$
C_{L_w}=\frac{2\pi A_we_w}{A_we_w+2}\,\alpha_w.
$$

The lift is normal to the local flow, which is inclined inboard by $\alpha_w$, so $L_w$ is tilted forwards by $\alpha_w$ and has a thrust component $L_w\sin\alpha_w\approx L_w\alpha_w$. The drag $D_w$ acts along the local flow and has a rearward component $D_w\cos\alpha_w\approx D_w$. The net streamwise force (drag positive), per unit $qS_w$, is

$$
\frac{\Delta D}{qS_w}=C_{D_{w0}}+\frac{C_{L_w}^2}{\pi A_we_w}-C_{L_w}\alpha_w,
$$

with the winglet's profile and induced drag in $D_w$. Write $\kappa\equiv A_we_w/(A_we_w+2)$, so $C_{L_w}=2\pi\kappa\alpha_w$. The induced term is

$$
\frac{C_{L_w}^2}{\pi A_we_w}=\frac{4\pi^2\kappa^2\alpha_w^2}{\pi A_we_w}=\frac{4\pi\kappa^2\alpha_w^2}{A_we_w}.
$$

Use $\kappa/(A_we_w)=1/(A_we_w+2)$:

$$
\frac{C_{L_w}^2}{\pi A_we_w}=\frac{4\pi\kappa\alpha_w^2}{A_we_w+2}.
$$

The thrust term is $C_{L_w}\alpha_w=2\pi\kappa\alpha_w^2$. Combine the two:

$$
\frac{4\pi\kappa\alpha_w^2}{A_we_w+2}-2\pi\kappa\alpha_w^2=2\pi\kappa\alpha_w^2\left[\frac{2}{A_we_w+2}-1\right]=-2\pi\kappa\alpha_w^2\,\frac{A_we_w}{A_we_w+2}=-2\pi\kappa^2\alpha_w^2.
$$

So

$$
\frac{\Delta D}{qS_w}=C_{D_{w0}}-2\pi\kappa^2\alpha_w^2.
$$

Substitute $\alpha_w=2\alpha/(Ae+2)$, so $2\pi\alpha_w^2=8\pi\alpha^2/(Ae+2)^2$, and refer to the wing area by multiplying by $S_w/S$:

$$
\boxed{\Delta C_D=\frac{S_w}{S}\left[C_{D_{w0}}-\frac{8\pi\alpha^2}{(Ae+2)^2}\left(\frac{A_we_w}{A_we_w+2}\right)^2\right].}
$$

Because $2\pi\alpha_w^2=2\pi C_L^2/(\pi Ae)^2=2C_{D_i}/(Ae)$, this is the sheet's form $\frac{S_w}{S}\left[C_{D_{w0}}-\frac{2C_{D_i}}{Ae}\left(\frac{A_we_w}{A_we_w+2}\right)^2\right]$. The winglet pays off when the induced saving exceeds its profile drag, which needs a high $C_L$.

### (ii) Drag polar [5 marks]

At the minimum-trim-drag CG the tail carries $C_{L_T}S_T/(C_L^*S)=1/\sigma$ of the lift, the wing carries $C_L=(1-1/\sigma)C_L^*$, and the induced drag of wing plus tail is $C^*_{D_i}(1-1/\sigma)$ (derived in [[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2(b)]]). With $\alpha=C_L/C_{L_\alpha}$ in the winglet term,

$$
C_D=C_{D_0}+\frac{S_w}{S}C_{D_{w0}}+\left[\frac{1-1/\sigma}{\pi Ae}-\frac{S_w}{S}\,\frac{8\pi}{(Ae+2)^2}\left(\frac{A_we_w}{A_we_w+2}\right)^2\left(\frac{1-1/\sigma}{C_{L_\alpha}}\right)^2\right]C_L^{*2}.
$$

The data give $Ae=5.85$, $A_Te_T=3.2$, $A_we_w=2.4$:

$$
\sigma=\frac{12\times5.85}{4\times3.2}+1=5.4844+1=6.4844,\qquad 1-\frac1\sigma=0.84578,
$$

$$
C_{L_\alpha}=\frac{2\pi(5.85)}{7.85}=4.6824,\qquad\left(\frac{2.4}{4.4}\right)^2=0.29752,
$$

$$
\frac{1-1/\sigma}{\pi Ae}=\frac{0.84578}{18.378}=0.046021,
$$

$$
\frac{1.5}{12}\times\frac{8\pi}{7.85^2}\times0.29752\times\left(\frac{0.84578}{4.6824}\right)^2=0.125\times0.40785\times0.29752\times0.032627=0.000495,
$$

$$
C_{D_0}+\frac{S_w}{S}C_{D_{w0}}=0.006+0.125\times0.002=0.00625,
$$

$$
\boxed{C_D=0.00625+0.04553\,C_L^{*2}.}
$$

### (iii) Cruise exponent for the given optimum CG [7 marks]

The optimum CG fixes $C_L^*$:

$$
h_{opt}=h_0-\frac{C_{M_0}}{C_L^*}+\frac{l}{c\sigma}\quad\Rightarrow\quad C_L^*=\frac{C_{M_0}}{h_0+l/(c\sigma)-h_{opt}}.
$$

With $l/(c\sigma)=3/6.4844=0.46265$:

$$
C_L^*=\frac{0.015}{0.25+0.46265-0.685}=\frac{0.015}{0.027651}=0.54248.
$$

For a polar $C_D=C_{D_0}'+K'C_L^{*2}$, maximise $f=C_L^{*x}/C_D$ through its logarithm:

$$
\frac{d\ln f}{dC_L^*}=\frac{x}{C_L^*}-\frac{2K'C_L^*}{C_{D_0}'+K'C_L^{*2}}=0,
$$

$$
x=\frac{2K'C_L^{*2}}{C_{D_0}'+K'C_L^{*2}}.
$$

(For $x=1$ this gives $K'C_L^{*2}=C_{D_0}'$, the familiar best $L/D$.) Substitute $K'C_L^{*2}=0.045526\times0.54248^2=0.013398$:

$$
x=\frac{2\times0.013398}{0.00625+0.013398}=\frac{0.026796}{0.019648}=\boxed{1.36}.
$$

The cruise point lies between best $L/D$ ($x=1$, $C_L^*=0.371$) and the propeller-endurance condition $C_L^{3/2}/C_D$ ($x=1.5$, $C_L^*=0.642$, which would put $h_{opt}$ at 0.689). See [[#Paper slips and ambiguities]].

### (iv) Incidence, elevator angle and speed [5 marks]

**Assumption.** $\alpha_0=0$ (not given).

$$
V=\sqrt{\frac{2mg}{\rho SC_L^*}}=\sqrt{\frac{2\times1500\times9.81}{0.9\times12\times0.54248}}=\boxed{70.9\ \text{m/s}}.
$$

The lift split:

$$
C_{L_T}=\frac{C_L^*S}{\sigma S_T}=\frac{0.54248\times12}{6.4844\times4}=0.25098,\qquad C_L=0.84578\times0.54248=0.45882.
$$

With $K=S_Tl/(Sc)=24/24=1$, the moment check is $0.015+0.54248(0.435)-0.25098=0.0000$. The incidence:

$$
\alpha=\frac{C_L}{C_{L_\alpha}}=\frac{0.45882}{4.6824}=0.09799\ \text{rad}=\boxed{5.61^\circ}.
$$

With $\epsilon_\alpha=2/7.85=0.25478$,

$$
\alpha_{T_{eff}}=(1-\epsilon_\alpha)\alpha+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}=0.74522(0.09799)-0.08727-\frac{0.25098}{\pi(3.2)},
$$

$$
\alpha_{T_{eff}}=0.07302-0.08727-0.02497=-0.03921\ \text{rad}\ (-2.25^\circ).
$$

Stick fixed, $C_{L_T}=2\pi\alpha_{T_{eff}}+4\eta$:

$$
\eta=\frac{C_{L_T}-2\pi\alpha_{T_{eff}}}{4}=\frac{0.25098+0.24635}{4}=0.12433\ \text{rad}=\boxed{7.12^\circ}.
$$

---

## Q3. Longitudinal modes with a pitch damper (25 marks)

> The UAS longitudinal model at 60 m/s is the 2013-14 matrix with the $(3,3)$ entry $-4.0-\mu$, $\mu\ge0$; for $\mu=0$ the eigenvalues are given as $\lambda_{1,2}=-3.1503\pm3.3572i$ and $\lambda_{3,4}=-0.0247\pm0.0974i$.
> (i) For $\mu=0$, identify the phugoid and SPO eigenvalues, find $\omega_n$ and $\zeta$ and comment on stability. [3]
> (ii) Explain with sketches the SPO and phugoid, with the relationships between pitch, incidence, climb angle and vertical displacement. [6]
> (iii) Assuming $u$ small in the SPO, derive an approximate eigenvalue including $\mu$, find the range of $\mu$ for oscillatory motion and comment on the damping at the upper end. [7]
> (iv) Explain pitch equilibrium and derive simplified phugoid equations; find $\omega_n$ and $\zeta$, setting $\mu=0$ and the $-4.0$ entry to zero. [9]

### (i) Modes with the damper off [3 marks]

The SPO is the fast pair, $-3.1503\pm3.3572i$:

$$
\omega_n=\sqrt{3.1503^2+3.3572^2}=\boxed{4.604\ \text{rad/s}},\qquad\zeta=\frac{3.1503}{4.604}=\boxed{0.684}.
$$

The phugoid is the slow pair, as printed $-0.0247\pm0.0974i$:

$$
\omega_n=\sqrt{0.0247^2+0.0974^2}=\boxed{0.1005\ \text{rad/s}},\qquad\zeta=\frac{0.0247}{0.1005}=\boxed{0.246}.
$$

Both real parts are negative, so both modes are stable; the SPO is well damped and the phugoid lightly damped.

> [!warning] The printed phugoid pair is not the matrix's
> The matrix with $\mu=0$ is the 2013-14 Q3 matrix, whose phugoid is $-0.0211\pm0.2072i$: $\omega_n=0.2083$ rad/s, $\zeta=0.101$, $T=30.3$ s. The SPO pair is correct to four figures.

### (ii) Characteristics of the two modes [6 marks]

![[amc_pp_201314_q3_spo.png|900]]

The **short-period oscillation** is a rapid pitching about the CG at almost constant speed, period about 1.9 s here. A disturbance in incidence meets the restoring moment of the static margin ($M_w<0$), overshoots and is damped mainly by the tail's pitch damping ($M_q$) and the lift slope ($Z_w$). The incidence and pitch attitude change together, $\Delta\alpha\approx\Delta\theta$, so the climb angle $\gamma=\theta-\alpha$ stays small and the flight path, and so the height, hardly changes: the aircraft rotates about a nearly straight path. In this example the mode is almost dead-beat ($\zeta=0.68$).

![[amc_pp_201314_q3_phugoid.png|900]]

The **phugoid** is a slow exchange of kinetic and potential energy at nearly constant incidence, period about 30 s. The aircraft climbs and slows, then dives and speeds up, along an undulating path. Since $\alpha\approx$ const, $\theta\approx\gamma$: the nose follows the path. The height swings are large (tens of metres for a couple of degrees of pitch) and the speed is lowest at the top and highest at the bottom, a quarter-cycle ahead of $\gamma$. The vertical displacement is $\dot h=U_\infty\gamma$, so $h$ lags $\gamma$ by $90^\circ$.

### (iii) SPO approximation with pitch damping [7 marks]

**Assumptions.** $u\approx0$ over the SPO (speed cannot change in a couple of seconds), so the $\dot u$ row is dropped; level trim, so $\theta$ does not appear in the $\dot w$ and $\dot q$ rows. ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]].)

$$
\frac{d}{dt}\begin{bmatrix}w\\q\end{bmatrix}=\begin{bmatrix}-2.3&60\\-0.2&-4.0-\mu\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix}.
$$

The characteristic equation:

$$
(-2.3-\lambda)(-4.0-\mu-\lambda)-60(-0.2)=0,
$$

$$
\lambda^2+(6.3+\mu)\lambda+2.3(4.0+\mu)+12=0,
$$

$$
\boxed{\lambda^2+(6.3+\mu)\lambda+(21.2+2.3\mu)=0,\qquad\lambda=-\frac{6.3+\mu}{2}\pm\frac12\sqrt{(6.3+\mu)^2-4(21.2+2.3\mu)}.}
$$

At $\mu=0$ this gives $-3.150\pm3.358i$, against the printed $-3.150\pm3.357i$. The motion is oscillatory while the discriminant is negative:

$$
(6.3+\mu)^2<4(21.2+2.3\mu),
$$

$$
\mu^2+12.6\mu+39.69<84.8+9.2\mu,
$$

$$
\mu^2+3.4\mu-45.11<0.
$$

The roots of the quadratic in $\mu$ are $\mu=\tfrac12\left(-3.4\pm\sqrt{3.4^2+4\times45.11}\right)=\tfrac12(-3.4\pm13.856)$, that is $5.228$ and $-8.628$. With $\mu\ge0$,

$$
\boxed{0\le\mu<5.23.}
$$

![[amc_pp_201415_q3_spo_mu_locus.png|900]]

Raising $\mu$ moves the SPO roots to the left and towards the real axis. At $\mu=5.23$ the two roots meet at $\lambda=-(6.3+5.228)/2=-5.76$ s⁻¹: the damping ratio reaches $\zeta=1$, critical damping, the fastest return without overshoot. Beyond it the mode splits into two real roots, one of which moves back towards the origin, so extra damping makes the slower part of the response more sluggish. (The full $4\times4$ model at $\mu=5.23$ still has a tiny imaginary part, $-5.77\pm0.10i$, because of the weak coupling through $u$.)

### (iv) Pitch-equilibrium phugoid [9 marks]

The phugoid is so slow that the fast pitching dynamics are always in balance: at each instant the pitching moment is close to zero and $\dot q\approx0$. This is **pitch equilibrium**, the assumption behind the improved phugoid approximation of [[SESA3047 6.2 - Phugoid Approximation#4. The improved approximation (6.34–6.38)|6.2 §4]], which also neglects $M_q$. With $\mu=0$ and the $(3,3)$ entry set to zero, the $\dot q$ row becomes an algebraic constraint:

$$
0=0.006u-0.2w\quad\Rightarrow\quad w=0.03u,\qquad\dot w=0.03\dot u.
$$

The speed equation with $w=0.03u$:

$$
\dot u=-0.05u+0.04(0.03u)-9.81\theta=-0.0488u-9.81\theta.
$$

The normal-force equation with $q=\dot\theta$:

$$
0.03\dot u=-0.40u-2.3(0.03u)+60\dot\theta,
$$

$$
\dot\theta=\frac{0.03\dot u+0.469u}{60}.
$$

Differentiate the speed equation and substitute $\dot\theta$:

$$
\ddot u=-0.0488\dot u-9.81\,\frac{0.03\dot u+0.469u}{60},
$$

$$
\ddot u=-0.0488\dot u-0.004905\dot u-0.076682u,
$$

$$
\ddot u+0.053705\,\dot u+0.076682\,u=0.
$$

Matching $\ddot u+2\zeta\omega_n\dot u+\omega_n^2u=0$:

$$
\omega_n=\sqrt{0.076682}=\boxed{0.277\ \text{rad/s}},\qquad\zeta=\frac{0.053705}{2\times0.27691}=\boxed{0.097},
$$

with $\lambda=-0.0269\pm0.2756i$ and period 22.8 s. The same coefficients come from the general result $\omega_n^2=g(\mathring M_u\mathring Z_w-\mathring M_w\mathring Z_u)/(mU_\infty\mathring M_w)$ of the Deep Dive.

The damping ratio agrees with the full model ($0.101$), but the frequency is 33 % above the full model's $0.208$ rad/s (and well above the printed pair's $0.100$ rad/s). The error comes from dropping $M_q$, which is large here: the full $4\times4$ model with only the $-4.0$ set to zero has a phugoid of $-0.0195\pm0.2766i$, almost exactly the approximation. Lanchester's $\sqrt2g/U_\infty=0.231$ rad/s is closer for this aircraft.

---

## Q4. Lateral modes, dihedral, yaw-only oscillation and pure roll (25 marks)

> Lateral UAS model at 50 m/s:
> $$\frac{d}{dt}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}=\begin{bmatrix}-0.26&0&-50&9.81\\-0.4&-7.8&-2.3&0\\0.09&-0.35&-0.80&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}+\begin{bmatrix}2.5&0\\1.0&-2.5\\-0.5&0\\0&0\end{bmatrix}\begin{bmatrix}\delta_R\\\delta_A\end{bmatrix},$$
> eigenvalues $\lambda_{1,2}=-0.3389\pm2.3681i$, $\lambda_3=-8.0704$, $\lambda_4=-0.1119$.
> (i) Associate each mode with its eigenvalues, give $\omega_n$ and $\zeta$ as appropriate and comment on stability. [3]
> (ii) Explain the three lateral modes with sketches and the qualitative effect on each of increasing the sideslip-to-roll derivative (more dihedral). [6]
> (iii) In a wind tunnel at 50 m/s the UAS can only yaw. Show that $\ddot\psi+a\dot\psi+b\psi=0$, find $a$, $b$, the period and halving time, sketch $v$ and $\psi$ against time and comment on estimating derivatives from the test. [8]
> (iv) In pure roll from $\phi=0$, $\delta_A=0$, the aileron steps to $\delta_A=+1$ at $t=0$. Find the time for the roll rate to reach half its limiting value. [8]

These eigenvalues are confirmed by Python to four figures. Lateral modes are SESA3047 §§6.7–6.10 (Thu 19 Nov 2026).

### (i) Mode identification [3 marks]

- Dutch roll, $-0.3389\pm2.3681i$: $\omega_n=\sqrt{0.3389^2+2.3681^2}=\boxed{2.392\ \text{rad/s}}$, $\zeta=0.3389/2.392=\boxed{0.142}$ (period 2.65 s).
- Roll subsidence, $-8.0704$: real, time constant $1/8.0704=0.124$ s.
- Spiral, $-0.1119$: real, time constant 8.94 s (halving time 6.19 s).

All real parts are negative, so all three modes are stable; the Dutch roll is lightly damped.

### (ii) The three lateral modes and the effect of dihedral [6 marks]

![[amc_pp_201314_q4_lateral_modes.png|900]]

The roll subsidence is a fast, non-oscillatory roll that settles at the roll rate set by the ailerons; the down-going wing gains incidence and lift and the up-going wing loses them, so the roll is strongly damped ($L_p<0$). The spiral is a slow, non-oscillatory change of bank and heading: a wing drops, the aircraft sideslips towards it, the fin yaws the nose into the turn (which steepens the bank) while the dihedral effect rolls the wings level, and the balance between these decides whether the bank decays or grows into a spiral dive. The Dutch roll is a yaw–sideslip oscillation driven by the fin's weathercock stiffness, with roll coupled in through the dihedral effect; seen from the cockpit the wingtip traces an ellipse.

Increasing the sideslip-to-roll derivative (making $L_v$ more negative, for example with more dihedral):

- roll subsidence: almost unchanged, since it is governed by $L_p$ (the root moves from $-8.07$ to $-8.23$ when $L_v$ doubles);
- spiral: more stable, since the restoring roll from sideslip now beats the yaw into the turn (the spiral criterion $L_vN_r>L_rN_v$ is met more easily); the root moves from $-0.112$ to $-0.146$;
- Dutch roll: less damped and slightly faster, because the larger rolling motion in each yaw cycle couples back into yaw; the pair moves from $-0.339\pm2.368i$ to $-0.243\pm2.615i$, and too much dihedral can make the Dutch roll unstable.

This is the classic conflict: dihedral that fixes the spiral spoils the Dutch roll.

### (iii) Yaw-only wind-tunnel test [8 marks]

**Assumptions.** Only yaw is free, so $p=\phi=0$ and the side-force row is replaced by the kinematic constraint; the tunnel flow is fixed, so yawing the model by $\psi$ (nose to starboard) puts the relative wind on its port side and produces the sideslip velocity $v=-U\psi$; the yaw rate is $r=\dot\psi$.

The yaw row of the model is

$$
\dot r=0.09v-0.35p-0.80r.
$$

Substitute $p=0$, $r=\dot\psi$ and $v=-50\psi$:

$$
\ddot\psi=0.09(-50\psi)-0.80\dot\psi,
$$

$$
\boxed{\ddot\psi+0.80\,\dot\psi+4.5\,\psi=0},\qquad a=0.80\ \text{s}^{-1},\quad b=4.5\ \text{s}^{-2}.
$$

The roots are $\lambda=-0.4\pm i\sqrt{4.5-0.16}=-0.4\pm2.0833i$, so

$$
\omega_n=\sqrt{4.5}=2.121\ \text{rad/s},\qquad\zeta=\frac{0.80}{2(2.121)}=0.189,
$$

$$
T=\frac{2\pi}{2.0833}=\boxed{3.02\ \text{s}},\qquad t_{1/2}=\frac{\ln2}{0.4}=\boxed{1.73\ \text{s}}.
$$

![[amc_pp_201415_q4_yaw_oscillation.png|900]]

The model weathercocks: yaw and sideslip oscillate in antiphase ($v=-U\psi$) with the same decaying envelope, halving roughly every 0.6 cycles. Compared with the free-flight Dutch roll ($T=2.65$ s, $\zeta=0.142$) the tunnel oscillation is slower, because the sideslip here comes only from yaw, and better damped, because there is no rolling to feed energy back.

From a recorded $\psi(t)$, the period gives the damped frequency $\omega_d=2\pi/T$ and the ratio of successive peaks gives the decay rate $\sigma=\ln(\psi_k/\psi_{k+1})/T$. Then $a=2\sigma$ and $b=\sigma^2+\omega_d^2$, and the model equation identifies $a=-\mathring N_r/I_{zz}$ (yaw damping) and $b=U\mathring N_v/I_{zz}$ (weathercock stiffness), with $I_{zz}$ from a separate swing test. Repeating at several tunnel speeds checks the expected scaling ($b\propto U^2$, $a\propto U$).

### (iv) Pure roll after a step aileron [8 marks]

**Assumptions.** Only roll is free ($v=r=0$); the roll row reduces to

$$
\dot p=-7.8p-2.5\delta_A.
$$

With $\delta_A=1$ for $t\ge0$ and $p(0)=0$, the solution of this first-order equation is

$$
p(t)=p_\infty\left(1-e^{-7.8t}\right),\qquad p_\infty=-\frac{2.5}{7.8}=-0.3205\ \text{rad/s per unit }\delta_A.
$$

The roll rate reaches half its limit when $e^{-7.8t}=\tfrac12$:

$$
t=\frac{\ln2}{7.8}=\boxed{0.089\ \text{s}}.
$$

The time constant is $1/7.8=0.128$ s; the pure-roll eigenvalue $-7.8$ is within 3.5 % of the full-model roll subsidence $-8.07$. The negative $p_\infty$ is the model's sign convention (positive $\delta_A$ rolls to port).

---

## Paper slips and ambiguities

- Q3(i). The printed phugoid eigenvalues $-0.0247\pm0.0974i$ do not belong to the matrix; with $\mu=0$ the matrix is that of 2013-14 Q3, phugoid $-0.0211\pm0.2072i$ ($\omega_n=0.208$ rad/s, $\zeta=0.101$).
- Q1(ii). The ratio is written as $C^*_{D_{iA}}/C^*_{D_{iB}}$, but the wing areas needed for a ratio of coefficients are not given; the answer above is the ratio of induced drag forces, 0.706, and the coefficient ratio is $1.38\,S_B/S_A$.
- Q1(iv), stick-free convention. The sheet's $\bar a_1=2\pi-a_3b_1/b_3$ eliminates the tab angle; with the elevator floating ($\bar a_1=2\pi-a_2b_1/b_2=4.283$, $\bar k=3.141$) the mass for $H_m=0.2$ is 560 kg. See [[SESA2025 Past Paper 2013-14 - Solutions#Paper slips and ambiguities|2013-14 slips]].
- Q2(iii). The exponent comes out at $x=1.36$, not a named value. Ignoring the winglet in the polar gives 1.37 and using the untrimmed $K'=1/(\pi Ae)$ gives 1.44; $x=1.5$ (propeller endurance) would need $h_{opt}=0.689$. The paper probably intended $x=3/2$ with rounded data.
- Q2(iv) and Q2(ii). $\alpha_0$ is not given and is taken as zero.
- Q4(iv). The units of $\delta_A=+1$ are not stated; the response scales linearly, and the half-time does not depend on the size of the step.
