---
title: "SESA2025 Past Paper 2013-14 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, manoeuvre-margin, stick-free, trim-drag, winglets, spo, phugoid, lanchester, lateral-modes, coordinated-turn, roll-subsidence]
paper: "2013-14"
theory_notes: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]]", "[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M11 - Longitudinal Trim and Static Stability]]", "[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-201314-02-SESA2025W1.pdf"]
---

# SESA2025 Past Paper 2013-14 - Solutions

> [!abstract] Paper info
> SESA2025 Mechanics of Flight, Semester 2 examination 2013/14 (120 min), four questions of 25 marks, answer all. This paper has no formula sheet; the solutions use the equations sheet printed with the 2014-15 and 2015-16 papers, from the same course, with the same notation (Q1(e) here and Q1(iv) of 2014-15 use the same aircraft). Q3 is SESA3047 Chapter 6 material; Q4 is the lateral modes, which SESA3047 reaches on Thu 19 Nov 2026 (§§6.7–6.10). Every number was computed in Python; the printed Q4 eigenvalues do not belong to the printed matrix (see [[#Paper slips and ambiguities]]).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Sweep and lateral stability, induced drag and span loading, adverse yaw, wave drag; tail arm for a stick-free manoeuvre margin $H_m=0.3$ | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability|SESA2022 T6 §4]], [[Lateral and Directional Stability]], [[Downwash and Induced Drag]] |
| 2 | 25 | Winglets, drag polar at the minimum-trim-drag CG, stick-free static margin, trim $\alpha$, $\eta$, $\beta$ and speed | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#2. Trim: stick fixed and stick free|SESA2022 T6 §2–3]], [[SESA1015 M11 - Longitudinal Trim and Static Stability|SESA1015 M11]]; trim drag is derived below |
| 3 | 25 | Longitudinal eigenvalues, SPO approximation, Lanchester phugoid | [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|SESA3047 6.1]], [[SESA3047 6.2 - Phugoid Approximation#2. Lanchester's approximation (6.28–6.33)|6.2 §2]] (§6.6, due Mon 16 Nov) |
| 4 | 25 | Lateral modes, controls for a coordinated turn, pure-roll approximation | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[Longitudinal and Lateral Dynamics]] |

---

## Q1. Sweep, induced drag, adverse yaw, wave drag and the stick-free manoeuvre margin (25 marks)

> (a) Describe using a diagram the impact of wing sweep on the lateral stability of an aircraft and list three drawbacks associated with sweep. [4]
> (b) Express the total induced drag in terms of span loading (weight per span) in cruise, and find the change in induced drag if the span is increased by 10 % with all other terms fixed. [4]
> (c) Discuss the reason for the adverse yawing moment generated as an aircraft rolls and describe three ways to eliminate it. [4]
> (d) List and discuss three techniques to reduce wave drag. [3]
> (e) With $A=7$, $e=0.85$, $e_T=0.75$, $h=0.40$, $S=25$ m², $m=2000$ kg, $S_T=4$ m², $h_0=0.25$, $c=1.8$ m, $\rho=1$ kg/m³, $A_T=5$, $C_{L_T}=2\pi\alpha_{T_{eff}}+3\eta+0.9\beta$, $C_H=-0.5\alpha_{T_{eff}}-0.75\eta-1.25\beta$, find the distance between the wing and tailplane aerodynamic centres that gives $H_m=0.3$ in stick-free manoeuvring flight. [10]

### (a) Sweep and lateral stability [4 marks]

![[amc_pp_201314_q1_sweep_sideslip.png|900]]

In a sideslip to starboard the relative wind arrives from ahead and to the right. On a swept-back wing the starboard (leading) wing then sits more nearly square to the stream: the velocity component normal to its leading edge is $V\cos(\Lambda-\beta)$, while the port (trailing) wing sees $V\cos(\Lambda+\beta)$. Lift depends on the normal component, so the leading wing lifts more and the aircraft rolls away from the sideslip, which levels the wings. Sweep therefore acts like dihedral (it makes $L_v$ more negative), and the effect grows with $C_L$, so a swept wing can need anhedral to avoid too much lateral stability and a poorly damped Dutch roll.

Three drawbacks of sweep:

- a lower lift-curve slope and lower $C_{L\max}$ (roughly in proportion to $\cos\Lambda$), so higher approach speeds or more powerful high-lift devices;
- spanwise boundary-layer drift that makes the tips stall first, which moves the lift forward and gives a pitch-up at the stall, and costs aileron effectiveness there;
- a heavier, more flexible structure: the swept box is longer for the same span, and bending twists the tips nose-down (aeroelastic wash-out and aileron reversal at lower speed).

### (b) Induced drag in terms of span loading [4 marks]

In level cruise $L=W$, so $C_L=W/(qS)$ with $q=\tfrac12\rho V^2$. The induced drag is

$$
D_i=qS\,C_{D_i}=qS\,\frac{C_L^2}{\pi Ae}.
$$

Substitute $C_L=W/(qS)$:

$$
D_i=qS\,\frac{W^2}{q^2S^2\,\pi Ae}=\frac{W^2}{q\,\pi e\,AS}.
$$

The aspect ratio is $A=b^2/S$, so $AS=b^2$:

$$
\boxed{D_i=\frac{1}{\pi e\,q}\left(\frac{W}{b}\right)^2=\frac{2}{\pi e\rho V^2}\left(\frac{W}{b}\right)^2.}
$$

Induced drag depends on the span loading $W/b$, not on the wing area. With $W$, $e$, $\rho$ and $V$ fixed, $D_i\propto b^{-2}$:

$$
\frac{D_{i,\text{new}}}{D_{i,\text{old}}}=\frac{1}{1.1^2}=0.826,
$$

a reduction of $\boxed{17.4\ \%}$.

### (c) Adverse yaw [4 marks]

To roll to starboard the port aileron goes down and the starboard aileron goes up. The down-going aileron raises the local $C_L$ on the rising (port) wing, and induced drag rises with $C_L^2$, so the port wing has more drag and yaws the nose to port, away from the turn. A second contribution comes from the roll rate itself: the rising wing sees its incidence reduced, so its lift vector tilts rearwards, and the falling wing's lift tilts forwards; both again yaw the nose away from the turn. Three remedies:

- differential aileron deflection, with the up-going aileron moving further than the down-going one, so that the profile drag of the up aileron balances the induced drag of the down one;
- Frise ailerons, whose nose protrudes below the wing when raised and adds drag on the down-going wing;
- spoilers for roll control, which kill lift and add drag on the down-going wing, so the yawing moment is proverse; and rudder coordination, either by the pilot or through an aileron–rudder interconnect.

### (d) Wave drag [3 marks]

- Sweep: the shock strength depends on the Mach number normal to the leading edge, $M\cos\Lambda$, so sweep delays the drag rise and lowers the wave-drag peak.
- Thin or supercritical sections: a low thickness-to-chord ratio raises the critical Mach number; a supercritical section has a flat upper surface that keeps the supersonic pocket weak and ends it in a weak shock.
- Area ruling: shaping the fuselage so that the total cross-sectional area (fuselage plus wing plus nacelles) varies smoothly along the length, waisting the fuselage where the wing joins, minimises the wave drag of the whole configuration (Whitcomb's area rule). A high fineness ratio helps for the same reason.

### (e) Tail arm for a stick-free manoeuvre margin of 0.3 [10 marks]

**Assumptions.** Linear lift and hinge-moment models; downwash $\epsilon_\alpha=2/(Ae+2)$; the stick-free tail lift slope uses the sheet's $\bar a_1$ (the convention is discussed in [[#Paper slips and ambiguities]]); $l$ is measured from the wing AC to the tail AC.

The wing quantities are

$$
Ae=7\times0.85=5.95,\qquad C_{L_\alpha}=\frac{2\pi Ae}{Ae+2}=\frac{2\pi(5.95)}{7.95}=4.7025\ \text{rad}^{-1},\qquad \epsilon_\alpha=\frac{2}{7.95}=0.25157.
$$

Stick free the hinge moment is zero. With the sheet's convention,

$$
\bar a_1=2\pi-\frac{a_3b_1}{b_3}=2\pi-\frac{0.9(-0.5)}{-1.25}=6.2832-0.36=5.9232,
$$

and with $A_Te_T=5\times0.75=3.75$,

$$
\bar k=\frac{\bar a_1A_Te_T}{A_Te_T+\bar a_1/\pi}=\frac{5.9232\times3.75}{3.75+1.8854}=3.9415\ \text{rad}^{-1}.
$$

The manoeuvre margin is

$$
H_m=h_0-h+K\,\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}},\qquad C_{L_{T\alpha}}=\frac{\bar k(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{1-\bar k\Phi s},\qquad C^*_{L_\alpha}=C_{L_\alpha}+sC_{L_{T\alpha}},
$$

with $s=S_T/S$, $K=S_Tl/(Sc)$ and $\Phi=\rho Sl/(2m)$. Both $K$ and $\Phi$ contain the unknown $l$. The denominator simplifies first. Put $C_{L_{T\alpha}}$ over its common denominator:

$$
C^*_{L_\alpha}=\frac{C_{L_\alpha}(1-\bar k\Phi s)+s\bar k(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{1-\bar k\Phi s}.
$$

The two $\Phi$ terms in the numerator cancel:

$$
C^*_{L_\alpha}=\frac{C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)}{1-\bar k\Phi s}.
$$

So

$$
K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=\frac{K\bar k(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)}.
$$

Write $K=\kappa l$ and $\Phi=\phi_1l$ with $\kappa=S_T/(Sc)$ and $\phi_1=\rho S/(2m)$, and set $H_m=0.3$:

$$
\kappa l\,\bar k\left(1-\epsilon_\alpha+\phi_1C_{L_\alpha}l\right)=(H_m+h-h_0)\left[C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)\right].
$$

This is a quadratic in $l$:

$$
\left(\kappa\bar k\phi_1C_{L_\alpha}\right)l^2+\kappa\bar k(1-\epsilon_\alpha)\,l-(H_m+h-h_0)\left[C_{L_\alpha}+s\bar k(1-\epsilon_\alpha)\right]=0.
$$

The numbers are $\kappa=4/(25\times1.8)=0.088889$ m⁻¹, $\phi_1=25/4000=0.00625$ m⁻¹, $s=0.16$ and $H_m+h-h_0=0.45$:

$$
\kappa\bar k\phi_1C_{L_\alpha}=0.088889\times3.9415\times0.00625\times4.7025=0.010297,
$$

$$
\kappa\bar k(1-\epsilon_\alpha)=0.088889\times3.9415\times0.74843=0.26222,
$$

$$
0.45\left[4.7025+0.16\times3.9415\times0.74843\right]=0.45\times5.1745=2.3285.
$$

So

$$
0.010297\,l^2+0.26222\,l-2.3285=0,
$$

$$
l=\frac{-0.26222+\sqrt{0.26222^2+4(0.010297)(2.3285)}}{2(0.010297)}=\frac{-0.26222+0.40581}{0.020594}=\boxed{6.97\ \text{m}}.
$$

> [!check] Back-substitution
> With $l=6.972$ m: $\Phi=0.04357$, $K=0.6197$, $C_{L_{T\alpha}}=3.9415(0.74843+0.20489)/(1-3.9415\times0.04357\times0.16)=3.7575/0.97252=3.8637$, $C^*_{L_\alpha}=4.7025+0.16\times3.8637=5.3207$, and $H_m=0.25-0.40+0.6197\times3.8637/5.3207=0.300$.

With the physically floating elevator ($\bar a_1=2\pi-a_2b_1/b_2=4.2832$, $\bar k=3.1412$) the same steps give $l=8.26$ m: a smaller stick-free tail slope needs a longer arm for the same margin.

---

## Q2. Winglets, trim drag and stick-free trim (25 marks)

> A conventional aircraft with winglets cruises with its CG at the position that minimises trim drag, stick free. Table Q.2: $A=7$, $e=0.9$, $S=7$ m²; $A_T=3$, $e_T=0.8$, $S_T=3$ m²; $A_w=5$, $e_w=0.6$, $S_w=1$ m²; $h_0=0.25$, $C_{M_0}=0.01$, $C_{D_0}=0.005$, $C_{D_{0w}}=0.002$; $\alpha_s=-4^\circ$, $c=1$ m, $l=3$ m; $\rho=1$ kg/m³, $m=1200$ kg, $g=9.81$ m/s²; $C_{L_T}=2\pi\alpha_{T_{eff}}+3\eta+0.9\beta$, $C_H=-0.5\alpha_{T_{eff}}-0.75\eta-1.25\beta$.
> (a) Describe with a diagram the impact of winglets on induced drag and three drawbacks. [5]
> (b) Derive the drag coefficient as a function of $C_L^*$ only. [5]
> (c) Given $h=h_0-C_{M_0}/C_L^*+(l/c)\left(SAe/(S_TA_Te_T)+1\right)^{-1}$, estimate the static margin at $(C_L^*/C_D)_{\max}$ and list three ways to increase it. [5]
> (d) Find $\alpha$, $\eta$, $\beta$ and the cruising speed. [5]
> (e) List three factors that affect skin-friction drag and discuss how direct boundary-layer control reduces it. [5]

### (a) How winglets reduce induced drag [5 marks]

![[amc_pp_201314_q2_winglet.png|900]]

The pressure difference between the lower and upper surfaces drives air round the tip, so above the wing near the tip the flow moves inboard: the tip vortex produces a sidewash $v_w$. A winglet set in that sidewash meets the local flow at an incidence $\alpha_w\approx v_w/V$ and makes a lift $L_w$ normal to the local flow, pointing inboard. Because the local flow is inclined inboard, $L_w$ is tilted forwards, and its forward component $L_w\sin\alpha_w$ is a thrust that offsets part of the induced drag. The winglet also partly blocks the flow round the tip, which spreads the trailing vorticity and weakens the downwash, much like a small increase in effective span. The quantitative model is derived in [[SESA2025 Past Paper 2014-15 - Solutions#Q2. Winglet drag, drag polar and optimal trim (25 marks)|2014-15 Q2(i)]].

Three drawbacks: the winglet adds its own profile drag $C_{D_{0w}}S_w/S$, so the net gain is positive only at high $C_L$ (climb, slow cruise) and can be negative at high speed; it adds weight and a large bending moment at the tip, so the wing root must be strengthened, which can also lower flutter speeds; and it is a fixed design for one condition, while the sidewash, and so the benefit, varies with $C_L$ (at low $C_L$ the winglet is nearly unloaded and only adds drag). Interference drag at the wing–winglet junction and side-force effects on the lateral-directional stability are further penalties.

### (b) Drag coefficient as a function of the total lift coefficient [5 marks]

**Trim drag.** Write $C_L^*$ for the total lift coefficient, $C_L^*=C_L+C_{L_T}S_T/S=C_W$ in level flight. The induced drag of wing plus tail, referred to $S$, is

$$
C_{D_i,\text{tot}}=\frac{C_L^2}{\pi Ae}+\frac{S_T}{S}\frac{C_{L_T}^2}{\pi A_Te_T}.
$$

Define the tail share $x\equiv C_{L_T}S_T/(C_L^*S)$, so $C_L=C_L^*(1-x)$ and $C_{L_T}=xC_L^*S/S_T$. Substitute into the first term:

$$
\frac{C_L^2}{\pi Ae}=\frac{C_L^{*2}}{\pi Ae}(1-x)^2=C_{D_i}^*(1-x)^2,\qquad C_{D_i}^*\equiv\frac{C_L^{*2}}{\pi Ae}.
$$

Substitute into the second term:

$$
\frac{S_T}{S}\frac{C_{L_T}^2}{\pi A_Te_T}=\frac{S_T}{S}\,\frac{x^2C_L^{*2}S^2}{S_T^2\,\pi A_Te_T}=C_{D_i}^*\,x^2\frac{SAe}{S_TA_Te_T}.
$$

The trim drag coefficient $C_{D_m}$ is the induced drag above that of the whole lift carried by the wing:

$$
C_{D_m}=C_{D_i,\text{tot}}-C^*_{D_i}=C^*_{D_i}\left[(1-x)^2-1+x^2\frac{SAe}{S_TA_Te_T}\right].
$$

Expand $(1-x)^2-1=-2x+x^2$ and collect, with $\sigma\equiv SAe/(S_TA_Te_T)+1$:

$$
C_{D_m}=C^*_{D_i}\,x\left(\sigma x-2\right).
$$

This is the sheet's general trim drag equation. At fixed $C_L^*$ it is a parabola in $x$. Setting $\partial C_{D_m}/\partial x=C^*_{D_i}(2\sigma x-2)=0$ gives

$$
x_{\text{opt}}=\frac1\sigma,\qquad (C_{D_m})_{\min}=-\frac{C^*_{D_i}}{\sigma}.
$$

The minimum is negative: sharing the lift between wing and tail lowers the total induced drag, as a biplane does. The CG that produces this split follows from the moment balance $C_{M_0}+C_L^*(h-h_0)-C_{L_T}K=0$ with $C_{L_T}K=xC_L^*\,l/c$:

$$
h_{\text{opt}}=h_0-\frac{C_{M_0}}{C_L^*}+\frac{l}{c}\,\frac1\sigma,
$$

which is the expression given in part (c).

**Winglets.** The winglet increment on the 2014-15 and 2015-16 sheets is

$$
\Delta C_D=\frac{S_w}{S}\left[C_{D_{0w}}-\frac{2C_{D_i}}{Ae}\left(\frac{A_we_w}{A_we_w+2}\right)^2\right],
$$

where $C_{D_i}=C_L^2/(\pi Ae)$ is the wing's induced drag, the source of the tip sidewash. At the optimum CG, $C_L=(1-1/\sigma)C_L^*$.

**Total.** Adding the zero-lift drag, the induced drag at optimum trim $C^*_{D_i}(1-1/\sigma)$ and the winglet term:

$$
\boxed{C_D=C_{D_0}+\frac{S_w}{S}C_{D_{0w}}+\frac{C_L^{*2}}{\pi Ae}\left[\left(1-\frac1\sigma\right)-\frac{S_w}{S}\,\frac{2}{Ae}\left(\frac{A_we_w}{A_we_w+2}\right)^2\left(1-\frac1\sigma\right)^2\right].}
$$

With the data, $Ae=6.3$, $A_Te_T=2.4$, $A_we_w=3$:

$$
\sigma=\frac{7\times6.3}{3\times2.4}+1=6.125+1=7.125,\qquad 1-\frac1\sigma=0.85965,\qquad \left(\frac{3}{5}\right)^2=0.36,
$$

$$
\frac{S_w}{S}\frac{2}{Ae}(0.36)\left(1-\frac1\sigma\right)^2=\frac17\times0.31746\times0.36\times0.73900=0.012065,
$$

$$
\frac{1}{\pi Ae}\left[0.85965-0.01207\right]=0.050525\times0.84758=0.042824,
$$

$$
C_{D_0}+\frac{S_w}{S}C_{D_{0w}}=0.005+\frac{0.002}{7}=0.0052857,
$$

$$
\boxed{C_D=0.005286+0.04282\,C_L^{*2}.}
$$

The trim saving ($1/\sigma=14\,\%$ of $C^*_{D_i}$) is far larger than the winglet's induced-drag saving (1.2 % of $C^*_{D_i}$), which is outweighed here by its own profile drag at cruise.

### (c) Static margin at the best lift-to-drag ratio [5 marks]

For a polar $C_D=C_{D_0}'+K'C_L^{*2}$, $C_L^*/C_D$ is greatest where the two drag terms are equal:

$$
C_L^*=\sqrt{\frac{C_{D_0}'}{K'}}=\sqrt{\frac{0.0052857}{0.042824}}=0.35132,\qquad C_D=2C_{D_0}'=0.010571,\qquad \frac{C_L^*}{C_D}=33.2.
$$

The CG is at the optimum:

$$
h=0.25-\frac{0.01}{0.35132}+\frac{3}{1}\times\frac{1}{7.125}=0.25-0.02846+0.42105=0.64259.
$$

The stick-free static margin uses the straight-flight stick-free slope,

$$
C_{L_{T\alpha}}=\frac{\bar a_1A_Te_T}{A_Te_T+\bar a_1/\pi}(1-\epsilon_\alpha)=\bar k(1-\epsilon_\alpha).
$$

Here $C_{L_\alpha}=2\pi(6.3)/8.3=4.7692$, $\epsilon_\alpha=2/8.3=0.24096$, $\bar a_1=5.9232$ (as in Q1(e)), and

$$
\bar k=\frac{5.9232\times2.4}{2.4+1.8854}=3.3172,\qquad C_{L_{T\alpha}}=3.3172\times0.75904=2.5179.
$$

With $K=S_Tl/(Sc)=9/7=1.2857$ and $s=3/7=0.42857$,

$$
C^*_{L_\alpha}=4.7692+0.42857\times2.5179=5.8483,
$$

$$
H=h_0-h+K\frac{C_{L_{T\alpha}}}{C^*_{L_\alpha}}=0.25-0.64259+1.2857\times\frac{2.5179}{5.8483}=0.25-0.64259+0.55355=\boxed{0.161}.
$$

The neutral point is at $h_n=0.804$, so the minimum-trim-drag CG is stable stick free, with a margin of 16 % of the chord. (With a floating elevator, $\bar a_1=4.2832$, the margin is 0.079.)

Three ways to increase the static margin: move the CG forward (ballast, payload or fuel placement); increase the tail volume $K=S_Tl/(Sc)$ with a bigger tailplane or a longer tail arm; raise the tail lift slope, stick free, by reducing $|b_1|$ (a horn or set-back balance lowers the elevator's floating tendency) or by a higher tail aspect ratio. Reducing the downwash at the tail, for example with a T-tail, also helps.

### (d) Trim angles and cruise speed [5 marks]

**Assumption.** The wing's zero-lift angle is not given, so $\alpha_0=0$ (and the $\epsilon_\alpha\alpha_0$ term vanishes).

Speed from $C_L^*=C_W$:

$$
V=\sqrt{\frac{2mg}{\rho SC_L^*}}=\sqrt{\frac{2\times1200\times9.81}{1\times7\times0.35132}}=\boxed{97.8\ \text{m/s}}.
$$

The lift split at the optimum CG:

$$
C_{L_T}=\frac{C_L^*S}{\sigma S_T}=\frac{0.35132\times7}{7.125\times3}=0.11505,\qquad C_L=\left(1-\frac1\sigma\right)C_L^*=0.30201.
$$

The moment balance checks: $0.01+0.35132(0.39259)-0.11505(1.2857)=0.0000$. The wing incidence is

$$
\alpha=\frac{C_L}{C_{L_\alpha}}=\frac{0.30201}{4.7692}=0.06333\ \text{rad}=\boxed{3.63^\circ}.
$$

The effective tail incidence:

$$
\alpha_{T_{eff}}=(1-\epsilon_\alpha)\alpha+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}=0.75904(0.06333)-0.06981-\frac{0.11505}{\pi(2.4)},
$$

$$
\alpha_{T_{eff}}=0.04807-0.06981-0.01526=-0.03701\ \text{rad}\ (-2.12^\circ).
$$

Stick free, both the lift and hinge-moment equations hold:

$$
3\eta+0.9\beta=C_{L_T}-2\pi\alpha_{T_{eff}}=0.11505+0.23252=0.34757,
$$

$$
-0.75\eta-1.25\beta=0.5\,\alpha_{T_{eff}}\quad\Rightarrow\quad 0.75\eta+1.25\beta=0.01850.
$$

The determinant is $3(1.25)-0.9(0.75)=3.075$, so

$$
\eta=\frac{0.34757(1.25)-0.9(0.01850)}{3.075}=0.13587\ \text{rad}=\boxed{7.78^\circ},
$$

$$
\beta=\frac{3(0.01850)-0.75(0.34757)}{3.075}=-0.06672\ \text{rad}=\boxed{-3.82^\circ}.
$$

The tab is deflected opposite to the elevator, which is what holds the elevator at zero hinge moment.

### (e) Skin-friction drag and boundary-layer control [5 marks]

Skin friction depends on the Reynolds number (it falls as $Re$ rises, roughly as $Re^{-1/2}$ laminar and $Re^{-1/5}$ turbulent), on the state of the boundary layer (a turbulent layer has several times the wall shear of a laminar one, so the transition position matters most), and on the wetted area and surface finish (roughness, steps and gaps trip transition and raise turbulent friction). The pressure gradient also matters, since a favourable gradient keeps the layer laminar.

Direct boundary-layer control acts on the layer itself. Distributed suction through a porous or slotted skin removes the low-momentum air near the wall, thins the layer and stabilises it against Tollmien–Schlichting waves, so laminar flow is kept much further aft (laminar flow control); the price is the pump power, ducting weight and clogging of the pores. Other direct methods are compliant or riblet surfaces, which damp the near-wall turbulent structures, and blowing or wall heating/cooling to change the near-wall profile. Indirect (natural laminar flow) methods shape the section to keep a favourable pressure gradient over more of the chord.

---

## Q3. Longitudinal modes, SPO approximation and Lanchester's phugoid (25 marks)

> For small disturbances about steady level flight at 60 m/s,
> $$\frac{d}{dt}\begin{bmatrix}u\\w\\q\\\theta\end{bmatrix}=\begin{bmatrix}-0.05&0.04&0&-9.81\\-0.40&-2.3&60&0\\0.006&-0.2&-4.0&0\\0&0&1&0\end{bmatrix}\begin{bmatrix}u\\w\\q\\\theta\end{bmatrix},$$
> with eigenvalues $\lambda_{1,2}=-3.154\pm3.358i$ and $\lambda_{3,4}=-0.0211\pm0.2072i$.
> (a) Identify the phugoid and SPO eigenvalues, find $\omega_n$ and $\zeta$ for each and comment on stability. [5]
> (b) Approximate the SPO by neglecting $u$, compute the approximate eigenvalues and compare. [10]
> (c) Outline Lanchester's approximation for the phugoid, calculate the approximate $\omega_n$, explain the phugoid with sketches and comment on the relation between pitch, incidence and climb angle. [10]

### (a) Identifying the modes [5 marks]

The SPO is the fast, well-damped pair (large $|\lambda|$) and the phugoid the slow, lightly damped pair. For a complex pair $\lambda=\sigma\pm i\omega$, $\omega_n=|\lambda|$ and $\zeta=-\sigma/\omega_n$ ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#3. Damping ratio and natural frequency (6.13–6.16)|6.1 §3]]).

SPO, $\lambda_{1,2}=-3.154\pm3.358i$:

$$
\omega_n=\sqrt{3.154^2+3.358^2}=\sqrt{9.948+11.276}=\boxed{4.607\ \text{rad/s}},\qquad \zeta=\frac{3.154}{4.607}=\boxed{0.685}.
$$

Phugoid, $\lambda_{3,4}=-0.0211\pm0.2072i$:

$$
\omega_n=\sqrt{0.0211^2+0.2072^2}=\boxed{0.2083\ \text{rad/s}},\qquad \zeta=\frac{0.0211}{0.2083}=\boxed{0.101}.
$$

Both pairs have negative real parts, so both modes are stable. The SPO has period $2\pi/3.358=1.87$ s and halves in $\ln2/3.154=0.22$ s, so it is almost dead-beat. The phugoid has period $2\pi/0.2072=30.3$ s and halves in $\ln2/0.0211=32.9$ s, about one cycle, a light damping typical of the phugoid. Python returns the same eigenvalues from the matrix.

### (b) SPO approximation [10 marks]

**Assumptions.** The SPO is over in a couple of seconds, much faster than the speed can change, so $u\approx0$ and the $\dot u$ row is dropped. The pitch attitude $\theta$ appears only in the $\dot u$ row (level trim, $\gamma_0=0$), so dropping it removes $\theta$ from the $w$ and $q$ equations as well. This is the approximation of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]], here applied directly to the state matrix.

Rows 2 and 3 with $u=0$:

$$
\frac{d}{dt}\begin{bmatrix}w\\q\end{bmatrix}=\begin{bmatrix}-2.3&60\\-0.2&-4.0\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix}.
$$

The characteristic equation $\det(\mathbf A_{sp}-\lambda\mathbf I)=0$ is

$$
(-2.3-\lambda)(-4.0-\lambda)-60(-0.2)=0.
$$

Expand the product:

$$
\lambda^2+6.3\lambda+9.2+12=0,
$$

$$
\lambda^2+6.3\lambda+21.2=0.
$$

So $2\zeta\omega_n=-\operatorname{tr}\mathbf A_{sp}=6.3$ and $\omega_n^2=\det\mathbf A_{sp}=21.2$:

$$
\omega_n=\sqrt{21.2}=4.604\ \text{rad/s},\qquad \zeta=\frac{6.3}{2(4.604)}=0.684,
$$

$$
\lambda=-3.15\pm i\sqrt{21.2-3.15^2}=-3.15\pm i\sqrt{11.2775}=\boxed{-3.150\pm3.358i}.
$$

| | Full $4\times4$ | SPO approximation | Error |
|---|---:|---:|---:|
| Real part | $-3.154$ | $-3.150$ | 0.1 % |
| Imaginary part | $3.358$ | $3.358$ | 0.0 % |
| $\omega_n$ (rad/s) | 4.607 | 4.604 | 0.06 % |
| $\zeta$ | 0.685 | 0.684 | 0.1 % |

The approximation is almost exact because the coupling into the fast pair through $u$ is tiny: $X_w=0.04$ and $M_u=0.006$ are small, and the two time scales differ by a factor of twenty.

### (c) Lanchester's phugoid approximation [10 marks]

**Assumptions** ([[SESA3047 6.2 - Phugoid Approximation#2. Lanchester's approximation (6.28–6.33)|6.2 §2]]): the total energy is constant (thrust balances drag throughout, no dissipation); the incidence, and so $C_L$, stay at the trim value; the flight path stays close to horizontal so lift acts vertically; $h$ is measured from the trim height, where the speed is $U_\infty$.

Constant energy:

$$
\tfrac12mU_\infty^2=\tfrac12mU^2+mgh\quad\Rightarrow\quad U^2=U_\infty^2-2gh.
$$

Multiply by $\tfrac12\rho SC_L$ and use $\tfrac12\rho U_\infty^2SC_L=mg$ (trim):

$$
L=\tfrac12\rho U^2SC_L=mg-\rho SC_Lg\,h.
$$

Newton's law for the height:

$$
m\ddot h=L-mg=-\rho SC_Lg\,h.
$$

Substitute $C_L=2mg/(\rho U_\infty^2S)$:

$$
\ddot h+\frac{2g^2}{U_\infty^2}h=0,\qquad\boxed{\omega_n=\frac{\sqrt2\,g}{U_\infty}},\qquad\zeta=0.
$$

At $U_\infty=60$ m/s,

$$
\omega_n=\frac{1.4142\times9.81}{60}=\boxed{0.231\ \text{rad/s}},\qquad T=\frac{2\pi}{0.2312}=27.2\ \text{s}.
$$

The full model gives $\omega_n=0.208$ rad/s and $T=30.3$ s, so Lanchester is 11 % high in frequency, and it says nothing about damping ($\zeta=0$ by construction).

![[amc_pp_201314_q3_phugoid.png|900]]

*Phugoid eigenvector of the Q3 matrix, released with $\theta=2^\circ$: pitch and climb angle overlie each other while the incidence barely moves; speed is lowest when the aircraft is highest.*

The phugoid is a slow exchange of kinetic and potential energy. The aircraft climbs and slows, noses over, dives and speeds up, pulls up again, and so on, along a gently undulating path. Because the incidence is almost constant, the extra speed at the bottom of the path gives extra lift that curves the path upwards, and the deficit at the top lets it curve down. In the Q3 eigenvector $|\alpha/\theta|=0.046$ and $|\gamma/\theta|=0.994$, with $\gamma$ within $3^\circ$ of $\theta$ in phase, so

$$
\theta\approx\gamma,\qquad\alpha\approx0:
$$

the nose follows the flight path. The speed perturbation leads the climb angle by about $90^\circ$ (at the top of the climb the speed is falling fastest), and $u$ and $h$ are in antiphase.

![[amc_pp_201314_q3_spo.png|900]]

*For contrast, the SPO eigenvector: the incidence and pitch move together and the climb angle stays small, the opposite of the phugoid.*

---

## Q4. Lateral modes, a coordinated turn and the pure-roll approximation (25 marks)

> $$\frac{d}{dt}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}=\begin{bmatrix}-0.26&0&-50&9.81\\-0.31&-7.5&-2.0&0\\0.09&-0.40&-0.80&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix}+\begin{bmatrix}2.5&0\\1.0&-3.0\\-0.5&0\\0&0\end{bmatrix}\begin{bmatrix}\delta_R\\\delta_A\end{bmatrix},$$
> with eigenvalues $\lambda_{1,2}=-1.338\pm2.223i$, $\lambda_3=-7.803$, $\lambda_4=-0.0799$.
> (a) Explain with sketches the three lateral modes, associate each with an eigenvalue, give period and halving time and comment on stability. [5]
> (b) For a coordinated level turn to the right at 50 m/s with $R=750$ m, find $\delta_R$, $\delta_A$ and $\phi$. [10]
> (c) Using a pure-roll approximation, derive the roll-angle equation, outline the step-aileron response, find the roll eigenvalue and the aileron deflection for a limiting roll rate of 15 deg/s with $\delta_R=0$. [10]

Lateral modes are SESA3047 §§6.7–6.10, due Thu 19 Nov 2026; the static background is [[Lateral and Directional Stability]].

### (a) The three lateral modes [5 marks]

![[amc_pp_201314_q4_lateral_modes.png|900]]

*Left: roll subsidence after a step aileron (pure-roll model, $L_p=-7.5$). Centre: spiral, a slow divergence or convergence of bank. Right: the Dutch roll eigenvector of the printed matrix, with yaw, sideslip and bank oscillating out of phase.*

- **Roll subsidence**, $\lambda_3=-7.803$: a fast, non-oscillatory, heavily damped roll. A rolling wing meets a raised incidence on the down-going side and a lowered one on the up-going side, which produces a large opposing rolling moment ($L_p<0$), so the roll rate settles quickly to a steady value. Time constant $1/7.803=0.128$ s, halving time $\ln2/7.803=0.089$ s. No period.
- **Spiral**, $\lambda_4=-0.0799$: a slow, non-oscillatory change of bank and heading. When a wing drops, the resulting sideslip meets the fin (weathercock stability, which yaws the nose into the turn and steepens it) and the dihedral effect (which levels the wings); the balance decides whether the bank slowly grows into a tightening spiral dive or decays. Here it decays: time constant 12.5 s, halving time $\ln2/0.0799=8.68$ s. No period.
- **Dutch roll**, $\lambda_{1,2}=-1.338\pm2.223i$: an oscillation in yaw and sideslip with coupled roll, the wingtip tracing an ellipse as seen by the pilot. The fin makes the nose oscillate about the flight path; the sideslip drives roll through the dihedral effect, and yaw lags roll. Period $2\pi/2.223=2.83$ s, halving time $\ln2/1.338=0.52$ s, with $\omega_n=2.595$ rad/s and $\zeta=0.516$.

All three eigenvalues have negative real parts, so the aircraft is laterally stable with controls fixed.

> [!warning] Printed eigenvalues
> The printed matrix actually has eigenvalues $-0.352\pm2.335i$ (Dutch roll: $T=2.69$ s, $t_{1/2}=1.97$ s, $\zeta=0.149$), $-7.759$ (roll, $t_{1/2}=0.089$ s) and $-0.0970$ (spiral, $t_{1/2}=7.14$ s). The identification and the stability conclusion are unchanged; the Dutch roll is much less damped than the printed values suggest.

### (b) Controls and bank angle for a coordinated turn [10 marks]

**Assumptions.** Steady turn, so all rates of change are zero; coordinated, so no sideslip, $v=0$; steady bank, so $p=\dot\phi=0$; small bank angle, so the body yaw rate equals the turn rate, $r=V/R$; the linear model holds at the turn condition.

$$
r=\frac VR=\frac{50}{750}=0.06667\ \text{rad/s}.
$$

With $\dot{\mathbf x}=\mathbf0$, $v=p=0$, the three non-trivial rows are

$$
0=-50r+9.81\phi+2.5\delta_R,
$$

$$
0=-2.0r+1.0\delta_R-3.0\delta_A,
$$

$$
0=-0.80r-0.5\delta_R.
$$

The yaw row gives the rudder directly:

$$
\delta_R=-\frac{0.80}{0.5}r=-1.6(0.06667)=\boxed{-0.1067\ \text{rad}\ (-6.11^\circ)}.
$$

The roll row gives the aileron:

$$
\delta_A=\frac{-2.0r+\delta_R}{3.0}=\frac{-0.13333-0.10667}{3.0}=\boxed{-0.0800\ \text{rad}\ (-4.58^\circ)}.
$$

The side-force row gives the bank:

$$
\phi=\frac{50r-2.5\delta_R}{9.81}=\frac{3.3333+0.2667}{9.81}=\boxed{0.367\ \text{rad}\ (21.0^\circ)}.
$$

Rudder is needed to balance the yaw damping $N_r$ in the steady yaw rate, and aileron to hold off the rolling moment from $L_r$ (the outer wing moves faster) and from the rudder. The bank exceeds the force-balance value $\tan^{-1}(V^2/gR)=18.8^\circ$ because the rudder side force $2.5\delta_R$ acts outwards and the bank must also cancel it.

### (c) Pure roll [10 marks]

**Assumptions.** Only roll freedom: $v=r=0$ and the $\dot v$, $\dot r$ rows are dropped; $\delta_R=0$.

The roll row becomes

$$
\dot p=-7.5p-3.0\delta_A,
$$

and with $p=\dot\phi$,

$$
\boxed{\ddot\phi+7.5\dot\phi=-3.0\,\delta_A.}
$$

The roll eigenvalue is $\lambda=L_p=\boxed{-7.5\ \text{s}^{-1}}$ (time constant 0.133 s), within 4 % of the printed roll eigenvalue $-7.80$ ($-7.76$ from the matrix itself).

For a step $\delta_A$ applied at $t=0$ from rest, the solution of the first-order equation for $p$ is

$$
p(t)=p_{ss}\left(1-e^{-7.5t}\right),\qquad p_{ss}=-\frac{3.0}{7.5}\delta_A=-0.4\,\delta_A,
$$

and integrating once,

$$
\phi(t)=p_{ss}\left[t-\frac{1-e^{-7.5t}}{7.5}\right].
$$

The roll rate rises exponentially to a steady value within about $3\tau=0.4$ s, and the bank angle then grows linearly: the aileron commands a roll rate, not a bank angle.

For a limiting roll rate of $15^\circ/\text{s}=0.2618$ rad/s,

$$
\delta_A=-\frac{p_{ss}}{0.4}=-\frac{0.2618}{0.4}=\boxed{-0.654\ \text{rad}\ (-37.5^\circ)}
$$

for a roll to starboard (opposite sign for a roll to port). This is larger than any practical aileron travel (typically $\pm20$–$25^\circ$), so the model aircraft cannot reach 15 deg/s; the pure-roll model also ignores the sideslip and yaw that the full model couples in.

---

## Paper slips and ambiguities

- No formula sheet is printed with this paper. The solutions use the 2014-15 equations sheet (same course and notation).
- Q1(e) and Q2(c), stick-free convention. The 2014-15 and 2015-16 sheets define $\bar a_1=2\pi-a_3b_1/b_3$, which eliminates the tab angle $\beta$ from $C_H=0$. Stick free, it is the elevator that floats while the tab is set, which gives $\bar a_1=a_1-a_2b_1/b_2$ (the 2016-17 to 2018-19 sheets and [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Stick-free tail lift: derivation|SESA2022 T6]]). The main answers follow the sheet; the floating-elevator values are $l=8.26$ m in Q1(e) and $H=0.079$ in Q2(c). The trim angles of Q2(d) are the same either way.
- Q2(d). No zero-lift angle is given; $\alpha_0=0$ is used.
- Q2(b). Which induced drag drives the winglet term is not stated; the wing's $C_{D_i}=C_L^2/(\pi Ae)$ is used. Using $C^*_{D_i}$ instead changes $K'$ from 0.04282 to 0.04273 and moves the answers only in the third significant figure.
- Q4. The printed eigenvalues ($-1.338\pm2.223i$, $-7.803$, $-0.0799$) are not those of the printed matrix ($-0.352\pm2.335i$, $-7.759$, $-0.0970$). The same matrix in 2016-17 Q3 suggests the matrix is correct and the eigenvalues are from another model.
