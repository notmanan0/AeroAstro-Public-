---
title: "SESA2025 Past Paper 2015-16 - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: past-paper-solutions
tags: [sesa3047, sesa2025, past-paper, solutions, sweep, aspect-ratio, manoeuvre-margin, high-lift, pull-up, winglets, trim-drag, stick-free, coordinated-turn, dutch-roll, spiral, roll-subsidence, time-response]
paper: "2015-16"
theory_notes: ["[[SESA3047 5.4 - Time-Domain Solution and Stability]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]", "[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]", "[[SESA1015 M11 - Longitudinal Trim and Static Stability]]", "[[Lateral and Directional Stability]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/SESA2025 Mechanics of Flight/SESA2025-201516-02-SESA2025W1.pdf"]
---

# SESA2025 Past Paper 2015-16 - Solutions

> [!abstract] Paper info
> SESA2025 Mechanics of Flight, Semester 2 examination 2015-16 (120 min, equations sheet on pp. 8–10, the same as 2014-15), four questions of 25 marks, answer all. Q1 and Q2 are static stability and trim drag; Q3 and Q4 are entirely lateral dynamics, which SESA3047 reaches on Thu 19 Nov 2026 (§§6.7–6.10). Q3 also needs the free response of a state equation ([[SESA3047 5.4 - Time-Domain Solution and Stability|5.4]]). Every number was computed in Python; Q4(i) is read from the printed response plots, so its answers are estimates.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 25 | Effects of sweep; aspect ratio and Concorde's nose; tail aspect ratio for a stick-fixed $H_m=0.3$; trim at $C_{L\max}$ in a pull-up | [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#4. Manoeuvre stability|SESA2022 T6 §4]], [[SESA2025 Past Paper 2013-14 - Solutions#Q1. Sweep, induced drag, adverse yaw, wave drag and the stick-free manoeuvre margin (25 marks)|2013-14 Q1]], [[SESA1015 M10 - Turning Flight and Manoeuvre Performance|SESA1015 M10]] |
| 2 | 25 | Winglets; drag polar at minimum trim drag; stick-free trim at $(C_L^{*3/2}/C_D)_{\max}$ | [[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2]], [[SESA2025 Past Paper 2014-15 - Solutions#Q2. Winglet drag, drag polar and optimal trim (25 marks)|2014-15 Q2]] |
| 3 | 25 | Coordinated turn controls; recovery from a turn with controls centred; simulating the free response; Dutch roll mode shape | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[SESA3047 5.4 - Time-Domain Solution and Stability|SESA3047 5.4]], [[Matrix Exponential and Modal Solution]] |
| 4 | 25 | Mode properties from response plots; Dutch roll approximation in dimensional derivatives | SESA3047 §§6.7–6.10 (lateral modes, due Thu 19 Nov 2026; no note yet), [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]] (same method) |

---

## Q1. Sweep, aspect ratio, manoeuvre margin and high-lift trim (25 marks)

> (i) Discuss the impact of wing sweep on (a) lateral stability, (b) longitudinal stability, (c) wave drag, (d) lift for a given wing area. [8]
> (ii) Explain the influence of aspect ratio on the lift-curve slope and how this links with Concorde's variable-incidence nose. [3]
> (iii) With $Ae=6$, $S=8$ m², $c=1$ m, $e_T=2/3$, $S_T=2$ m², $l=4$ m, $h=0.35$, $h_0=0.25$, $\rho=1$ kg/m³, $m=320\pi$ kg and $C_{L_T}=2\pi\alpha_{T_{eff}}+3.345\eta$, find the tailplane aspect ratio that gives $H_m=0.3$, stick fixed (Figure Q.1). [7]
> (iv) Calculate $V$, $\alpha$, $\alpha_{T_{eff}}$ and $\eta$ for trim at maximum lift with flaps and slats, with $C_{L\max}=3.9$, $\theta=15.245^\circ$, $R=100$ m, $g=9.81$ m/s², $C_{M_0}=0$, $\alpha_s=-2.155^\circ$, $\alpha_0=-15.906^\circ$. [7]

### (i) Effects of sweep [8 marks]

![[amc_pp_201314_q1_sweep_sideslip.png|900]]

(a) Lateral stability. In sideslip the leading wing of a swept wing sees a larger velocity component normal to its leading edge, $V\cos(\Lambda-\beta)$ against $V\cos(\Lambda+\beta)$, so it lifts more and rolls the aircraft away from the sideslip. Sweep therefore adds an effective dihedral ($L_v$ more negative), roughly in proportion to $C_L\sin2\Lambda$, so it is strongest at low speed and high $C_L$. Highly swept aircraft often need anhedral to avoid excessive roll in sideslip and a poorly damped Dutch roll.

(b) Longitudinal stability. Sweeping the wing back moves its outboard lift, and so the wing aerodynamic centre, aft, which raises the static margin for a given CG. Near the stall the effect reverses: spanwise flow thickens the tip boundary layer, the tips stall first, the lift moves forward and inboard and the aircraft pitches up, which is statically unstable at high $\alpha$. Fences, saw-tooth leading edges and wash-out are used against it.

(c) Wave drag. Compressibility depends on the Mach number normal to the leading edge, $M\cos\Lambda$, so sweep raises the critical and drag-divergence Mach numbers and lowers the peak wave drag; a leading edge swept behind the Mach cone ($\Lambda>90^\circ-\mu$) is subsonic and keeps the wave drag low in supersonic flight.

(d) Lift. Only the normal component generates lift, so the lift-curve slope and $C_{L\max}$ fall (simple sweep theory gives a factor near $\cos\Lambda$). For the same wing area a swept wing gives less lift at a given $\alpha$, needs a higher incidence or more powerful high-lift devices at low speed, and lands faster.

### (ii) Aspect ratio and Concorde's droop nose [3 marks]

The finite-wing slope is $C_{L_\alpha}=2\pi Ae/(Ae+2)$: the trailing vortices induce a downwash that reduces the effective incidence, and the smaller the aspect ratio the larger the downwash for a given lift, so a low-aspect-ratio wing has a much lower slope ($Ae=1.5$ gives $0.43\times2\pi$ against $0.75\times2\pi$ at $Ae=6$). Concorde's slender delta, chosen for supersonic flight, has $A\approx1.7$, so it needs a very high incidence (about $13$–$17^\circ$, using vortex lift) to make enough lift at take-off and landing speeds. At that attitude the long nose would hide the runway, so the nose and visor were drooped (about $5^\circ$ for take-off and $12.5^\circ$ for landing) to give the pilots a forward view, and raised for a low-drag shape in cruise.

### (iii) Tail aspect ratio for a stick-fixed manoeuvre margin of 0.3 [7 marks]

The manoeuvre margin is ([[SESA2025 Past Paper 2013-14 - Solutions#Q1. Sweep, induced drag, adverse yaw, wave drag and the stick-free manoeuvre margin (25 marks)|2013-14 Q1(e)]] for the simplification of $C^*_{L_\alpha}$, here with the stick-fixed $k$)

$$
H_m=h_0-h+\frac{Kk(1-\epsilon_\alpha+\Phi C_{L_\alpha})}{C_{L_\alpha}+sk(1-\epsilon_\alpha)},\qquad k=\frac{2\pi A_Te_T}{A_Te_T+2}.
$$

All terms except $k$ are known, and $H_m$ is linear in $k$. With $H_m+h-h_0=0.4$:

$$
Kk(1-\epsilon_\alpha+\Phi C_{L_\alpha})=0.4\left[C_{L_\alpha}+sk(1-\epsilon_\alpha)\right],
$$

$$
k=\frac{0.4\,C_{L_\alpha}}{K(1-\epsilon_\alpha+\Phi C_{L_\alpha})-0.4\,s(1-\epsilon_\alpha)}.
$$

The wing and tail constants:

$$
C_{L_\alpha}=\frac{2\pi(6)}{8}=\frac{3\pi}{2}=4.7124,\qquad\epsilon_\alpha=\frac28=0.25,
$$

$$
K=\frac{S_Tl}{Sc}=\frac{2\times4}{8\times1}=1,\qquad s=\frac{S_T}{S}=0.25,\qquad\Phi=\frac{\rho Sl}{2m}=\frac{1\times8\times4}{640\pi}=\frac{1}{20\pi}=0.015915,
$$

$$
\Phi C_{L_\alpha}=\frac{1}{20\pi}\times\frac{3\pi}{2}=0.075.
$$

So

$$
k=\frac{0.4\times4.7124}{1\times(0.75+0.075)-0.4\times0.25\times0.75}=\frac{1.8850}{0.825-0.075}=2.5133=0.8\pi.
$$

Invert $k=2\pi A_Te_T/(A_Te_T+2)$:

$$
k(A_Te_T+2)=2\pi A_Te_T\quad\Rightarrow\quad A_Te_T=\frac{2k}{2\pi-k}=\frac{1.6\pi}{1.2\pi}=\frac43,
$$

$$
A_T=\frac{4/3}{e_T}=\frac{4/3}{2/3}=\boxed{2}.
$$

> [!check] Back-substitution
> $k=0.8\pi$: $C_{L_{T\alpha}}=2.5133\times0.825/(1-2.5133\times0.015915\times0.25)=2.0944$, $C^*_{L_\alpha}=4.7124+0.25\times2.0944=5.2360$, $H_m=0.25-0.35+2.0944/5.2360=0.300$.

### (iv) Trim at maximum lift in the pull-up [7 marks]

**Assumptions.** The aircraft of part (iii) ($A_Te_T=4/3$) at the instant shown in Figure Q.1, on a circular path of radius $R$ at pitch attitude $\theta$; lift at $C_{L\max}$ on the wing; the sheet's notation $C_L^*=C_W(\cos\theta+n)$ with $n=V^2/(gR)$.

The total lift coefficient at wing $C_{L\max}$ follows from the moment balance $C_{M_0}+C_L^*(h-h_0)-KC_{L_T}=0$ with $C_{L_T}=(C_L^*-C_{L\max})S/S_T$ and $KS/S_T=l/c$:

$$
C_L^*(h-h_0)=\frac lc\left(C_L^*-C_{L\max}\right)-C_{M_0},
$$

$$
C_L^*\left[\frac lc-(h-h_0)\right]=\frac lcC_{L\max}+C_{M_0},
$$

$$
C^*_{L\max}=\frac{C_{L\max}+C_{M_0}c/l}{1-(c/l)(h-h_0)}=\frac{3.9+0}{1-0.25\times0.1}=\frac{3.9}{0.975}=4.000.
$$

Normal to the path, $L^*-mg\cos\theta=mV^2/R$, so with $L^*=\tfrac12\rho V^2SC_L^*$:

$$
V^2\left(\frac{C_L^*\rho S}{2m}-\frac1R\right)=g\cos\theta,
$$

$$
V=\sqrt{\frac{g\cos\theta}{C^*_{L\max}\rho S/(2m)-1/R}}=\sqrt{\frac{9.81\cos15.245^\circ}{4\times\frac{8}{640\pi}-0.01}}=\sqrt{\frac{9.4648}{0.015915-0.01}}=\boxed{40.0\ \text{m/s}}.
$$

Check: $n=40^2/(9.81\times100)=1.631$, $C_W=2mg/(\rho V^2S)=1.5410$, $C_W(\cos\theta+n)=4.000$.

The tail lift:

$$
C_{L_T}=\frac{C^*_{L\max}-C_{L\max}}{s}=\frac{4.0-3.9}{0.25}=0.400.
$$

The wing incidence, with the flapped zero-lift angle:

$$
\alpha=\alpha_0+\frac{C_{L\max}}{C_{L_\alpha}}=-15.906^\circ+\frac{3.9}{4.7124}\ \text{rad}=-15.906^\circ+47.418^\circ=\boxed{31.51^\circ}\ (0.5500\ \text{rad}).
$$

The effective tail incidence, including the pitch-rate term $l/R$:

$$
\alpha_{T_{eff}}=(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}+\frac lR,
$$

$$
\alpha_{T_{eff}}=0.75(0.55000)+0.25(-0.27761)-0.03761-\frac{0.4}{\pi(4/3)}+0.04,
$$

$$
\alpha_{T_{eff}}=0.41250-0.06940-0.03761-0.09549+0.04=0.24999\ \text{rad}=\boxed{14.32^\circ}.
$$

Stick fixed:

$$
\eta=\frac{C_{L_T}-2\pi\alpha_{T_{eff}}}{3.345}=\frac{0.400-1.5707}{3.345}=-0.3500\ \text{rad}=\boxed{-20.05^\circ}.
$$

The tail sits at a high effective incidence because of the large wing incidence and the pitch rate, so a large up-elevator is needed to keep its lift down to $C_{L_T}=0.4$.

---

## Q2. Winglets, drag polar and stick-free trim (25 marks)

> A conventional aircraft without winglets cruises with its CG at the minimum-trim-drag position, stick free. Table Q.2: $A=6$, $e=0.9$, $S=6$ m²; $A_T=3$, $e_T=0.6$, $S_T=3$ m²; $h_0=0.25$, $C_{M_0}=-0.01$, $C_{D_0}=0.02$; $\alpha_s=-6^\circ$, $c=1$ m, $l=3.5$ m; $\rho=1.225$ kg/m³, $m=1500$ kg, $g=9.81$ m/s²; $C_{L_T}=2\pi\alpha_{T_{eff}}+3.5\eta+1.1\beta$, $C_H=-0.6\alpha_{T_{eff}}-0.9\eta-1.3\beta$.
> (i) Describe with a sketch how winglets work (assumptions and equations) and discuss four drawbacks. [9]
> (ii) Work out the drag polar. [6]
> (iii) The aircraft cruises at $(C_L^{*3/2}/C_D)_{\max}$. Calculate $\alpha$, $\eta$, $\beta$ and the speed. [10]

### (i) How winglets work [9 marks]

![[amc_pp_201314_q2_winglet.png|900]]

The pressure difference across the wing drives a flow round each tip, so the tip vortex induces a sidewash $v_w$ that runs inboard above the wing. A winglet in that sidewash meets a local flow inclined inboard by $\alpha_w=v_w/V$ and makes a lift $L_w$ normal to it, pointing inboard and tilted forward by $\alpha_w$. Its forward component is a thrust; the winglet also partly blocks the flow round the tip, so the trailing vorticity is spread and the wing's downwash weakens, as with a slightly larger span.

Assumptions and equations ([[SESA2025 Past Paper 2014-15 - Solutions#Q2. Winglet drag, drag polar and optimal trim (25 marks)|full derivation in 2014-15 Q2(i)]]): the sidewash angle equals the wing's induced angle, $\alpha_w=C_L/(\pi Ae)$; the winglet is a small finite wing with $C_{L_w}=2\pi\kappa\alpha_w$, $\kappa=A_we_w/(A_we_w+2)$; small angles; profile drag $C_{D_{w0}}$. Resolving streamwise, per unit $qS_w$,

$$
\frac{\Delta D}{qS_w}=C_{D_{w0}}+\frac{C_{L_w}^2}{\pi A_we_w}-C_{L_w}\alpha_w=C_{D_{w0}}-2\pi\kappa^2\alpha_w^2,
$$

$$
\Delta C_D=\frac{S_w}{S}\left[C_{D_{w0}}-\frac{2C_{D_i}}{Ae}\left(\frac{A_we_w}{A_we_w+2}\right)^2\right].
$$

Four drawbacks: the winglet's own profile and interference drag, so the net saving is positive only at high $C_L$ (take-off, climb, slow cruise) and can be negative at high speed; extra weight and a large tip bending moment, needing a stronger, heavier wing root; changed aeroelastic and flutter behaviour from a mass and load at the tip; and a fixed geometry optimised for one $C_L$, which also changes the lateral-directional derivatives (side force aft of or above the CG adds directional and lateral stability, which affects the Dutch roll and crosswind handling). Ground clearance and gate-span limits are practical constraints too.

### (ii) Drag polar [6 marks]

With the CG at the optimum, the tail carries $1/\sigma$ of the lift and the induced drag of wing plus tail is $C^*_{D_i}(1-1/\sigma)$ ([[SESA2025 Past Paper 2013-14 - Solutions#Q2. Winglets, trim drag and stick-free trim (25 marks)|2013-14 Q2(b)]]); there are no winglets, so

$$
C_D=C_{D_0}+\left(1-\frac1\sigma\right)\frac{C_L^{*2}}{\pi Ae},\qquad\sigma=\frac{SAe}{S_TA_Te_T}+1.
$$

With $Ae=5.4$ and $A_Te_T=1.8$:

$$
\sigma=\frac{6\times5.4}{3\times1.8}+1=6+1=7,\qquad\frac{1-1/7}{\pi\times5.4}=\frac{0.85714}{16.965}=0.050525,
$$

$$
\boxed{C_D=0.020+0.05053\,C_L^{*2}.}
$$

Trimming at the optimum CG lowers the induced-drag factor by $1/\sigma=14\,\%$ below the untrimmed $1/(\pi Ae)=0.05895$.

### (iii) Trim at the maximum of the endurance parameter [10 marks]

For $C_D=C_{D_0}+K'C_L^{*2}$, the maximum of $C_L^{*3/2}/C_D$ satisfies (setting the logarithmic derivative to zero, as in [[SESA2025 Past Paper 2014-15 - Solutions#Q2. Winglet drag, drag polar and optimal trim (25 marks)|2014-15 Q2(iii)]] with $x=3/2$)

$$
\frac{3}{2C_L^*}=\frac{2K'C_L^*}{C_{D_0}+K'C_L^{*2}}\quad\Rightarrow\quad K'C_L^{*2}=3C_{D_0},
$$

$$
C_L^*=\sqrt{\frac{3\times0.02}{0.050525}}=1.0897,\qquad C_D=4C_{D_0}=0.080.
$$

**Speed.**

$$
V=\sqrt{\frac{2mg}{\rho SC_L^*}}=\sqrt{\frac{2\times1500\times9.81}{1.225\times6\times1.0897}}=\boxed{60.6\ \text{m/s}}.
$$

**Incidence.** $\alpha_0$ is not given and is taken as zero. At the optimum CG,

$$
C_{L_T}=\frac{C_L^*S}{\sigma S_T}=\frac{1.0897\times6}{7\times3}=0.31135,\qquad C_L=\frac67C_L^*=0.93406,
$$

and with $C_{L_\alpha}=2\pi(5.4)/7.4=4.5850$,

$$
\alpha=\frac{0.93406}{4.5850}=0.20372\ \text{rad}=\boxed{11.67^\circ}.
$$

The CG for this condition is $h_{opt}=0.25+0.01/1.0897+3.5/7=0.759$, and the moment balance $-0.01+1.0897(0.509)-1.75(0.31135)=0$ checks.

**Tail.** With $\epsilon_\alpha=2/7.4=0.27027$,

$$
\alpha_{T_{eff}}=0.72973(0.20372)-0.10472-\frac{0.31135}{\pi(1.8)},
$$

$$
\alpha_{T_{eff}}=0.14866-0.10472-0.05506=-0.01112\ \text{rad}\ (-0.64^\circ).
$$

Stick free, the lift and zero-hinge-moment equations are

$$
3.5\eta+1.1\beta=C_{L_T}-2\pi\alpha_{T_{eff}}=0.31135+0.06986=0.38122,
$$

$$
0.9\eta+1.3\beta=-0.6\,\alpha_{T_{eff}}=0.006671.
$$

The determinant is $3.5(1.3)-1.1(0.9)=3.56$:

$$
\eta=\frac{0.38122(1.3)-1.1(0.006671)}{3.56}=0.13715\ \text{rad}=\boxed{7.86^\circ},
$$

$$
\beta=\frac{3.5(0.006671)-0.9(0.38122)}{3.56}=-0.08982\ \text{rad}=\boxed{-5.15^\circ}.
$$

---

## Q3. Coordinated turn, recovery and the Dutch roll (25 marks)

> Lateral model (radians):
> $$\dot v=-0.02v-68r+9.81\phi+2.4\delta_R,\qquad\dot p=-0.06v-1.9p+0.5r-2.2\delta_A+1.2\delta_R,$$
> $$\dot r=0.02v-0.25p-0.3r-0.6\delta_R,\qquad\dot\phi=p.$$
> (i) Find $\delta_R$ and $\delta_A$ for a coordinated turn to starboard with $R=800$ m at $U_0=68$ m/s, and the bank angle in degrees. [10]
> (ii) With controls fixed and centred the eigenvalues are $\lambda_1=-0.019$, $\lambda_2=-2.147$, $\lambda_{3,4}=-0.027\pm1.393i$. At $t=t_1$ the pilot centres the controls sharply and holds them. What happens in the short and long term? [5]
> (iii) Discuss how to simulate this for $t\ge t_1$ in the time domain, with attention to initial conditions and the state equation. [5]
> (iv) Discuss the mode given by $\lambda_{3,4}$, with a graph of bank and yaw angles against time. [5]

### (i) Controls for the coordinated turn [10 marks]

**Assumptions.** Steady turn (all derivatives zero); coordinated, $v=0$; constant bank, $p=0$; small bank angle so the body yaw rate is the turn rate, $r=U_0/R$; the linear model holds at the turn.

$$
r=\frac{U_0}{R}=\frac{68}{800}=0.0850\ \text{rad/s}.
$$

The yaw equation with $v=p=0$:

$$
0=-0.3r-0.6\delta_R\quad\Rightarrow\quad\delta_R=-0.5r=\boxed{-0.0425\ \text{rad}\ (-2.44^\circ)}.
$$

The roll equation:

$$
0=0.5r-2.2\delta_A+1.2\delta_R\quad\Rightarrow\quad\delta_A=\frac{0.5r+1.2\delta_R}{2.2}=\frac{0.04250-0.05100}{2.2}=\boxed{-0.00386\ \text{rad}\ (-0.22^\circ)}.
$$

The side-force equation:

$$
0=-68r+9.81\phi+2.4\delta_R\quad\Rightarrow\quad\phi=\frac{68r-2.4\delta_R}{9.81}=\frac{5.780+0.102}{9.81}=\boxed{0.5996\ \text{rad}=34.4^\circ}.
$$

The rudder holds off the yaw damping in the steady yaw rate; the aileron is tiny because the rolling moment from yaw rate ($L_r$) and from the rudder nearly cancel. The bank exceeds the point-mass value $\tan^{-1}(U_0^2/gR)=30.5^\circ$ partly because the rudder side force points out of the turn and partly because $34^\circ$ is not a small angle for the linear model.

### (ii) Centring the controls: short- and long-term motion [5 marks]

The given eigenvalues match the model: spiral $-0.0188$ (computed), roll subsidence $-2.147$, Dutch roll $-0.0271\pm1.393i$. At $t_1$ the aircraft is in the turn trim state ($v=p=0$, $r=0.085$, $\phi=0.600$) and the controls step back to zero, so the subsequent motion is the free response from that state. Decomposed onto the eigenvectors, almost all of the bank sits in the spiral mode (coefficient 0.604 of the 0.600 rad), with small Dutch-roll and roll-subsidence parts.

![[amc_pp_201516_q3_return_from_turn.png|900]]

In the short term the roll-subsidence part dies in about a second (time constant 0.47 s). Removing the rudder excites the Dutch roll: the sideslip oscillates up to about $1.7^\circ$ with a period of 4.5 s, and with $\zeta=0.019$ it halves only every 25.6 s, so the aircraft wallows in yaw and sideslip for a minute or more, while the bank angle falls only slowly (from $34.4^\circ$ to about $29^\circ$ in the first 10 s).

In the long term the stable spiral returns the wings to level, but slowly: the bank halves every 37 s, falling to about $13^\circ$ after 50 s, $5^\circ$ after 100 s and under $1^\circ$ after 200 s. The aircraft keeps turning throughout and swings through about $260^\circ$ of heading before it straightens out. Centring the controls is therefore a poor way to recover; opposite aileron and rudder are needed to roll out promptly.

### (iii) Simulating the recovery [5 marks]

The state equation with the controls centred is the free system

$$
\dot{\mathbf x}=\mathbf A\mathbf x,\qquad\mathbf x=[v,p,r,\phi]^T,\qquad\mathbf A=\begin{bmatrix}-0.02&0&-68&9.81\\-0.06&-1.9&0.5&0\\0.02&-0.25&-0.3&0\\0&1&0&0\end{bmatrix},
$$

because $\mathbf B\mathbf u=\mathbf0$ for $t\ge t_1$. The initial condition is the steady-turn trim state found in (i), not zero:

$$
\mathbf x(t_1)=[0,\ 0,\ U_0/R,\ \phi_{\text{turn}}]^T=[0,\ 0,\ 0.085,\ 0.5996]^T.
$$

The input step is already in that state: the controls held it in equilibrium, and removing them leaves $\dot{\mathbf x}(t_1)=\mathbf A\mathbf x(t_1)\neq\mathbf 0$. The solution is

$$
\mathbf x(t)=e^{\mathbf A(t-t_1)}\mathbf x(t_1)=\mathbf V e^{\boldsymbol\Lambda(t-t_1)}\mathbf V^{-1}\mathbf x(t_1),
$$

the modal form of [[SESA3047 5.4 - Time-Domain Solution and Stability#1. Solving the free state equation (5.40–5.42)|5.4 §1]], with $\mathbf V^{-1}\mathbf x(t_1)$ giving the amount of each mode excited. Numerically, the same response comes from `initial(ss(A,B,C,D), x0)` or `lsim` with zero input in MATLAB, `expm` at each time, or a time-stepping integrator such as `ode45` on $\dot{\mathbf x}=\mathbf A\mathbf x$. Time is measured from $t_1$ ($\tau=t-t_1$). To plot the heading, augment the state with $\dot\psi=r$; the linear model is only approximate at $34^\circ$ of bank, so a nonlinear 6-DOF simulation would refine the long-term answer.

### (iv) The Dutch roll mode [5 marks]

![[amc_pp_201516_q3_dutch_roll.png|900]]

$\lambda_{3,4}=-0.027\pm1.393i$ is the Dutch roll: an oscillation with $\omega_n=1.393$ rad/s, $\zeta=0.019$, period $T=2\pi/1.393=4.51$ s and halving time $\ln2/0.027=25.7$ s. It is stable but very lightly damped, which pilots and passengers find objectionable (a yaw damper would normally be fitted).

The fin's weathercock stiffness ($N_v$) swings the nose back and forth across the flight path; each yaw produces sideslip, and the sideslip rolls the aircraft through the dihedral effect ($L_v$), while the faster outer wing in a yaw adds roll through $L_r$. In the eigenvector the bank and yaw angles have similar sizes, $|\psi/\phi|=0.71$, and are out of phase by about $120^\circ$ (yaw leading), so the aircraft yaws one way while rolling the other way, and the wingtip traces an ellipse as seen from the cockpit. Damping comes mainly from the yaw damping $N_r$ of the fin.

---

## Q4. Lateral response from plots and the Dutch roll approximation (25 marks)

> Figure Q.4 shows the response to a 2° aileron pulse held for 5 s: (A) roll rate $p$ over 0–5 s, (B) bank angle $\phi$ over 0–100 s.
> (i) Estimate the roll-damping time constant, the Dutch roll undamped natural frequency $\omega_n$ and the spiral half-life. [15]
> (ii) From the stick-fixed lateral equations
> $$\begin{bmatrix}m&0&0&0\\0&I_{xx}&-I_{xz}&0\\0&-I_{xz}&I_{zz}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot v\\\dot p\\\dot r\\\dot\phi\end{bmatrix}=\begin{bmatrix}\mathring Y_v&0&-mU_0&mg\\\mathring L_v&\mathring L_p&\mathring L_r&0\\\mathring N_v&\mathring N_p&\mathring N_r&0\\0&1&0&0\end{bmatrix}\begin{bmatrix}v\\p\\r\\\phi\end{bmatrix},$$
> derive approximations for the Dutch roll $\zeta$ and $\omega_n$ in terms of the mass, inertias and derivatives. [10]

### (i) Mode properties from the plots [15 marks]

Readings were taken from the printed plots at high magnification; they are good to about 5 %.

| Feature read from the plot | Reading |
|---|---|
| Fig. Q.4A, quasi-steady roll rate after the initial rise | $p_{ss}\approx-0.100$ rad/s |
| Fig. Q.4A, time to reach 63 % of $p_{ss}$ ($p\approx-0.063$) | $t\approx0.09$ s |
| Fig. Q.4A, extremes of the oscillation | $-0.114$ at 0.45 s, $-0.092$ at 1.53 s, $-0.105$ at 2.90 s, $-0.097$ at 4.28 s |
| Fig. Q.4B, bank angle on the slow recovery | $-0.48$ rad at 10 s, $-0.44$ at 20 s, $-0.31$ at 60 s, $-0.222$ at 100 s |

**Roll subsidence.** The roll rate rises as $p=p_{ss}(1-e^{-t/\tau})$, so $\tau$ is the time to reach 63 % of the final value, or equivalently the intercept of the initial tangent with $p_{ss}$. Both give

$$
\tau_{\text{roll}}\approx\boxed{0.1\ \text{s}}\quad(\lambda\approx-10\ \text{s}^{-1}).
$$

**Dutch roll.** The oscillation superimposed on the roll rate has a period from successive peaks (1.53 s to 4.28 s) and troughs:

$$
T_d\approx4.28-1.53=2.75\ \text{s},\qquad\omega_d=\frac{2\pi}{2.75}=2.28\ \text{rad/s}.
$$

The peak-to-trough heights are $0.022$, $0.013$ and $0.008$ rad/s, a half-cycle ratio of about $0.60$, so the half-cycle logarithmic decrement is $\delta=\ln(1/0.60)=0.51$ and

$$
\zeta=\frac{\delta}{\sqrt{\pi^2+\delta^2}}=\frac{0.51}{3.18}\approx0.16,
$$

$$
\omega_n=\frac{\omega_d}{\sqrt{1-\zeta^2}}=\frac{2.28}{0.987}\approx\boxed{2.3\ \text{rad/s}}.
$$

The damping only shifts $\omega_n$ by about 1 %, so $\omega_n\approx\omega_d$ is a fair estimate.

**Spiral.** After the aileron returns to zero at 5 s, the bank angle (reaching $-0.50$ rad) decays slowly with no oscillation: the stable spiral. For $\phi\propto e^{\lambda t}$,

$$
\lambda=\frac{\ln(0.222/0.48)}{100-10}=\frac{-0.771}{90}=-0.0086\ \text{s}^{-1},
$$

$$
t_{1/2}=\frac{\ln2}{0.0086}\approx\boxed{80\ \text{s}}.
$$

Other pairs of points (20 s and 60 s; 40 s and 100 s) give 79–81 s. During the 5 s pulse the bank grows almost linearly at about $0.1$ rad/s, consistent with the roll rate in Fig. Q.4A.

### (ii) Dutch roll approximation [10 marks]

**Assumptions.** The Dutch roll is treated as a yaw–sideslip oscillation: the rolling motion is neglected, $p=\phi=0$, and the rolling-moment equation is dropped; $I_{xz}$ is negligible (principal-like axes), so the yaw equation is $I_{zz}\dot r=\mathring N_vv+\mathring N_rr$; $\mathring Y_r$ is already absorbed (the matrix carries $-mU_0$ only). This is the same reduction to a $2\times2$ system as the SPO approximation of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#7. The SPO approximation (6.22–6.27)|6.1 §7]].

The two remaining equations:

$$
m\dot v=\mathring Y_vv-mU_0r,
$$

$$
I_{zz}\dot r=\mathring N_vv+\mathring N_rr.
$$

Set $v=v_0e^{\lambda t}$, $r=r_0e^{\lambda t}$ and collect on the left:

$$
\begin{bmatrix}m\lambda-\mathring Y_v&mU_0\\-\mathring N_v&I_{zz}\lambda-\mathring N_r\end{bmatrix}\begin{bmatrix}v_0\\r_0\end{bmatrix}=\mathbf0.
$$

A non-trivial solution needs a zero determinant:

$$
(m\lambda-\mathring Y_v)(I_{zz}\lambda-\mathring N_r)+mU_0\mathring N_v=0.
$$

Expand:

$$
mI_{zz}\lambda^2-\left(m\mathring N_r+I_{zz}\mathring Y_v\right)\lambda+\mathring Y_v\mathring N_r+mU_0\mathring N_v=0.
$$

Divide by $mI_{zz}$:

$$
\lambda^2-\left(\frac{\mathring N_r}{I_{zz}}+\frac{\mathring Y_v}{m}\right)\lambda+\frac{\mathring Y_v\mathring N_r+mU_0\mathring N_v}{mI_{zz}}=0.
$$

Compare with $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2=0$:

$$
\boxed{\omega_n^2=\frac{\mathring Y_v\mathring N_r+mU_0\mathring N_v}{mI_{zz}}\approx\frac{U_0\mathring N_v}{I_{zz}},\qquad\zeta=-\frac{m\mathring N_r+I_{zz}\mathring Y_v}{2\sqrt{mI_{zz}\left(\mathring Y_v\mathring N_r+mU_0\mathring N_v\right)}}.}
$$

The frequency is set mainly by the weathercock stiffness $\mathring N_v>0$ (fin size and arm); the damping by the yaw damping $\mathring N_r<0$ and the side-force derivative $\mathring Y_v<0$. Neglecting roll usually overestimates the frequency slightly and misjudges the damping, because the rolling motion that $\mathring L_v$ couples in feeds energy back into the yaw.

---

## Paper slips and ambiguities

- Q1(iv). The incidence comes out at $31.5^\circ$ with the given $\alpha_0=-15.906^\circ$ and $C_{L\max}=3.9$; the data are clearly designed (they give $C^*_{L\max}=4.000$, $V=40.0$ m/s and $\eta=-20.05^\circ$), so the large $\alpha$ is part of the question, though unrealistic for a real wing. The aircraft of part (iii) is assumed, including $A_Te_T=4/3$.
- Q2(iii). $\alpha_0$ is not given and is taken as zero. The pdftotext layer of the paper shows $C_{M_0}=0.01$, but the printed table has $C_{M_0}=-0.01$, which is used.
- Q2, stick-free convention. The sheet's $\bar a_1=2\pi-a_3b_1/b_3$ is not needed here (no margin is asked); the trim angles come from the two equations and do not depend on it.
- Q3(i). A bank of $34^\circ$ is outside the small-angle range of the linear model, so the controls and bank angle are estimates.
- Q4(i). All values are graphical estimates; the roll time constant is the least certain because the rise is steep and partly masked by the Dutch roll.
