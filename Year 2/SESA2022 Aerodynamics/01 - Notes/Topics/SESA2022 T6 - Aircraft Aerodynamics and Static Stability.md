---
title: "SESA2022 T6 - Aircraft Aerodynamics and Static Stability"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
order: 6
tags:
  - sesa2022
  - static-stability
  - trim
  - tailplane
aliases: ["Static Stability", "Aircraft Trim", "Longitudinal Static Stability"]
date: 2026-09-23
status: complete
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
next_topics: []
key_concepts: ["[[Neutral Point and Static Margin]]", "[[Stick-Fixed vs Stick-Free Stability]]", "[[Manoeuvre Point and Manoeuvre Margin]]", "[[Lateral and Directional Stability]]"]
tutorial_sheets: ["[[SESA2022 Examples Sheet 6 - Static Stability Solutions]]", "[[SESA2022 Static Stability Past Paper Questions Solutions]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf", "02 - Sources/Stability/Static Stability.txt"]
---

# SESA2022 T6 - Aircraft Aerodynamics and Static Stability

> [!abstract] Summary
> A conventional aircraft trims in pitch using a **tailplane**. Vertical force and moment balance about the CG give two **trim equations**. The tail lift is modelled linearly in the tail effective angle of attack $\alpha_{T_{eff}}$, the elevator angle $\eta$ and the trim-tab angle $\beta$, including **wing downwash** $\epsilon$ and **tail downwash** $\epsilon_T$. **Static stability** requires $dC_{M_{CG}}/d\alpha<0$, which is equivalent to the CG ahead of the **neutral point**, i.e. a positive **static margin** $H_s = h_n-h$. **Stick-free** flight (a floating elevator) lowers the tail lift slope and so the margin. **Manoeuvring** (pitch rate) adds pitch damping, so the **manoeuvre point** lies behind the neutral point. Lateral and directional stability come from the fin, dihedral, high wing and sweep.

## Key Concepts
- [[Neutral Point and Static Margin]]
- [[Stick-Fixed vs Stick-Free Stability]]
- [[Manoeuvre Point and Manoeuvre Margin]]
- [[Lateral and Directional Stability]]
- Wing downwash model: [[Downwash and Induced Drag]]

---

## 6.1 Tailplane aerodynamics

**Means of trim in pitch** (roll and yaw already trimmed): **canard**, **tailless** (e.g. B-2), **tailplane**. This course focuses on the tailplane.

### Forces and simplifications (steady, trimmed flight)
- Thrust and drag act along the same axis through the CG, so they produce no moment. Along the path: $T = D + D_T + W\sin\gamma$.
- The tailplane is symmetric and small, so $M_{T_0} = 0$.
- Moments from $T$, $D$ and $D_T$ are neglected.

**Sign conventions and geometry**:
- $M_0$: wing pitching moment about the wing AC (constant with $\alpha$, **nose-up positive**).
- $l$: distance from the wing AC to the tail AC.
- $hc$ and $h_0c$: distances of the CG and the wing AC from a datum, as fractions of the MAC $c$ (**positive downstream**).
- Forces are positive upward.

### Trim equations

$$
L + L_T - W\cos\gamma = 0\quad\Rightarrow\quad L^* \equiv L+L_T = W\cos\gamma
$$

$$
M_0 + L(h-h_0)c - L_T\big(l-(h-h_0)c\big) = 0\quad\text{or}\quad M_0 + (L+L_T)(h-h_0)c - L_Tl = 0
$$

Non-dimensionalise with $\tfrac12\rho V^2S$ (and $S_T$ for the tail, $Sc$ for moments):

$$
\boxed{C_{L^*} = C_L + C_{L_T}\frac{S_T}{S} = C_W\cos\gamma}\qquad\boxed{C_{M_0} + C_{L^*}(h-h_0) - C_{L_T}K = 0},\quad K \equiv \frac{S_Tl}{Sc}\;(\text{tail volume ratio})
$$

with $C_W = \dfrac{W}{\tfrac12\rho V^2S}$.

**Tail lift can be positive or negative.** With a small $M_0$, a CG behind the AC needs positive tail lift and a CG ahead needs negative tail lift. A forward CG helps stability but gives poor handling at low speed. Tail sections may be symmetric or negatively cambered.

### Tailplane components
- **Horizontal stabiliser** (fixed or adjustable setting $\alpha_s$).
- **Elevator** ($\eta$, positive trailing-edge down) to control tail lift.
- **Trim tab** ($\beta$) to cancel the hinge moment so the pilot can fly hands-off.
- **Horn balance** (shielded or unshielded) to reduce stick forces.

### Tail angle of attack including downwash

$$
\alpha_T = \alpha+\alpha_s,\qquad \alpha_{T_{eff}} = \alpha+\alpha_s-\epsilon-\epsilon_T
$$

The downwash models come from [[SESA2022 T5 - Finite Wing Theory|lifting-line theory]]:

$$
\epsilon \approx \frac{C_L}{\pi Ae} = \epsilon_\alpha(\alpha-\alpha_0),\quad \epsilon_\alpha = \frac{C_{L_\alpha}}{\pi Ae},\qquad \epsilon_T = \frac{C_{L_T}}{\pi A_Te_T}
$$

$$
\boxed{\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}},\qquad \frac{\partial\alpha_{T_{eff}}}{\partial\alpha} = 1-\epsilon_\alpha
$$

**Wing lift**, using the finite-wing slope with $e$:

$$
C_L = C_{L_\alpha}(\alpha-\alpha_0),\qquad C_{L_\alpha} = a_0\frac{\pi Ae}{\pi Ae+a_0}
$$

### Tail lift and hinge-moment models (linear)

$$
C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\qquad a_1 = \frac{\partial C_{L_T}}{\partial\alpha_{T_{eff}}},\ a_2 = \frac{\partial C_{L_T}}{\partial\eta},\ a_3 = \frac{\partial C_{L_T}}{\partial\beta}
$$

$$
C_{M_H} = b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta
$$

- $b_1$ and $b_2$ are normally **negative**.
- A horn balance reduces $|b_1|$ and $|b_2|$.
- The coefficients can be estimated from TAT (flap theory, see [[Trailing-Edge Flap in Thin Aerofoil Theory]]), wind tunnels or CFD.

**Trim tab principle**: to get negative tail lift the elevator must go up. Deflecting the tab down ($\beta>0$) creates a hinge moment that pushes the elevator up until $C_{M_H}=0$ ($\eta<0$, $L_T<0$). The stick is then free and the aircraft is trimmed.

## 6.2 Trim: stick fixed vs stick free

See [[Stick-Fixed vs Stick-Free Stability]].

| | Stick fixed | Stick free |
|---|---|---|
| How | Pilot holds the elevator at $\eta$ against the hinge moment | Trim tab set so $C_{M_H}=0$ and the pilot applies zero force |
| Hinge moment | $C_{M_H}\neq0$ | $C_{M_H}=0$ |
| Tab | $\beta = 0$ (assumed) | $\beta\neq0$ |
| Tail lift | $C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta$ | $C_{L_T} = \bar a_1\alpha_{T_{eff}}+\bar a_3\beta$ |

Eliminating $\eta$ with $C_{M_H} = 0$, i.e. $\eta = -(b_1\alpha_{T_{eff}}+b_3\beta)/b_2$, gives

$$
\bar a_1 \equiv a_1 - a_2\frac{b_1}{b_2},\qquad \bar a_3\equiv a_3-a_2\frac{b_3}{b_2}
$$

**Floating tendency**: a gust with $\Delta\alpha_{T_{eff}}>0$ and $\Delta\beta = 0$ gives $\Delta\eta = -\Delta\alpha_{T_{eff}}\,b_1/b_2 < 0$. The elevator floats up, so the tail produces **less lift per unit $\alpha$**. For example $a_1 = 6.28$ rad$^{-1}$ (fixed) versus $\bar a_1 = 5.78$ rad$^{-1}$ (free). This lowers pitch stiffness, and a horn balance helps.

**Other ways to trim**:
- **Fixed tail**: light, cheap, simple, safe; limited control, trim drag.
- **All-moving tail (stabilator)**: high trimming power, wide CG range, low trim drag, highly manoeuvrable; structurally harder.
- **Adjustable tail** (airliners, e.g. E-170): changes $\alpha_s$ for trim and uses the elevator for control.
- **Moving the CG**: Concorde pumped fuel aft at supersonic speed because the centre of pressure moves aft.

**Tail setting angle for zero elevator** ($\eta = \beta = 0$): solve the trim equations for $C_L$ and $C_{L_T}$, get $\alpha$ from $C_L = C_{L_\alpha}(\alpha-\alpha_0)$, then solve $C_{L_T} = a_1\alpha_{T_{eff}}$ for $\alpha_s$.

### Solution algorithm for trim problems

1. $C_W = \dfrac{mg}{\tfrac12\rho V^2S}$, $C_{L^*} = C_W\cos\gamma$, $K = \dfrac{S_Tl}{Sc}$.
2. Moment equation gives $C_{L_T} = \dfrac{C_{M_0}+C_{L^*}(h-h_0)}{K}$.
3. $C_L = C_{L^*} - C_{L_T}S_T/S$.
4. $C_{L_\alpha} = a_0\dfrac{\pi Ae}{\pi Ae+a_0}$, so $\alpha = \alpha_0 + C_L/C_{L_\alpha}$.
5. $\epsilon_\alpha = C_{L_\alpha}/(\pi Ae)$, then compute $\alpha_{T_{eff}}$.
6. Solve for the controls:
   - Stick fixed: $\eta = (C_{L_T}-a_1\alpha_{T_{eff}})/a_2$.
   - Stick free: solve $\begin{pmatrix}a_2&a_3\\b_2&b_3\end{pmatrix}\begin{pmatrix}\eta\\\beta\end{pmatrix} = \begin{pmatrix}C_{L_T}-a_1\alpha_{T_{eff}}\\-b_1\alpha_{T_{eff}}\end{pmatrix}$.

This algorithm reproduces all the Examples Sheet 6 answers: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]].

## 6.3 Longitudinal static stability

**Static stability**: if the system is disturbed from equilibrium, the forces and moments created *initially* tend to return it. ("Static" as opposed to dynamic.) Pictures: a ball in a bowl (stable), on a flat surface (neutral), on a hill (unstable).

For an aircraft disturbed by $\Delta\alpha>0$, stability needs a nose-down moment $\Delta C_{M_{CG}}<0$:

$$
\boxed{\frac{dC_{M_{CG}}}{d\alpha}<0}
$$

For trim at a useful positive $\alpha_e$ we also need $C_{M_{CG}}(\alpha=0) > 0$.

![[stab_cm_alpha.png|520]]

**Contributions**:
- Main: wing/fuselage lift, wing pitching moment, tail lift.
- Minor: power effects, drag, other components.

A steeper negative slope means a more stable aircraft with more pitch stiffness. This is the **stability versus manoeuvrability trade-off** (X-29 unstable, A380 stable).

### Moment derivative

$$
\frac{dC_{M_{CG}}}{d\alpha} = C_{L^*_\alpha}(h-h_0)-C_{L_{T,\alpha}}K,\qquad C_{L^*_\alpha} = C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}
$$

- The first term is **destabilising** if the AC is ahead of the CG ($h>h_0$).
- The second term is **stabilising** if $l>0$ (tail aft).

### Neutral point and static margin

See [[Neutral Point and Static Margin]].

$$
\frac{dC_{M_{CG}}}{d\alpha}\Big|_{h=h_n} = 0\quad\Rightarrow\quad \boxed{h_n = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}}
$$

$$
\boxed{H_s \equiv h_n-h = h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}}\qquad H_s \propto -\frac{dC_{M_{CG}}}{d\alpha},\qquad \text{stable} \iff H_s>0
$$

The CG must be **ahead of the neutral point**.

### Tail lift slope

**Stick fixed**: substitute $\alpha_{T_{eff}}$ into $C_{L_T}$ and solve (the $C_{L_T}$ appears on both sides through $\epsilon_T$):

$$
C_{L_T} = k\left((1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s+\frac{a_2}{a_1}\eta\right),\qquad k\equiv a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}
$$

$$
\boxed{C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)}
$$

The chain is: 2D aerofoil slope $a_1$, then 3D tail slope $k$, then 3D tail with wing downwash, $k(1-\epsilon_\alpha)$.

**Stick free**: replace $a_1\to\bar a_1$, giving $\bar k = \bar a_1\dfrac{\pi A_Te_T}{\pi A_Te_T+\bar a_1}$ and $C_{L_{T,\alpha}} = \bar k(1-\epsilon_\alpha)$.

Because $\bar k<k$, the stick-free neutral point is further forward:

$$
H_{s,\text{stick fixed}} > H_{s,\text{stick free}}
$$

## 6.4 Manoeuvre stability

See [[Manoeuvre Point and Manoeuvre Margin]].

**Steady pull-up** (constant radius $R$, velocity $V$, pitch rate $q = V/R$, level at the bottom):

$$
L^*-W = m\frac{V^2}{R},\qquad n\equiv\frac{L^*}{W} = \frac{C_{L^*}}{C_W},\qquad n-1 = \frac{V^2}{gR}
$$

**Pitch rate increases the tail angle of attack.** The tail moves downward at speed $q(l-(h-h_0)c)\approx ql$:

$$
\Delta\alpha_{T_q}\approx\frac{ql}{V} = \frac{l}{R} = \frac{(n-1)gl}{V^2} = (n-1)C_W\Phi,\qquad C_W = \frac{mg}{\tfrac12\rho V^2S},\quad \Phi\equiv\frac{\rho Sl}{2m}\ (\text{mass parameter})
$$

This is **pitch damping**, which increases stability. Therefore

$$
\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}+(n-1)C_W\Phi
$$

With $n$ depending on $\alpha$ via $\dfrac{d}{d\alpha}(n-1)C_W\Phi = C_{L^*_\alpha}\Phi$, where $C_{L^*_\alpha} = C_{L_\alpha}+C_{L_{T,\alpha}}S_T/S$:

$$
C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)+k\Phi\left(C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}\right)\quad\Rightarrow\quad\boxed{C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}}}
$$

$$
\boxed{h_m = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}}},\qquad H_m = h_m-h
$$

- $C_{L_{T,\alpha}}$ is higher during a manoeuvre, so the **manoeuvre point lies aft of the neutral point** and the aircraft is **more stable while manoeuvring**.
- The effect shrinks with altitude ($\Phi\propto\rho$). At altitude the aircraft feels less stable and more responsive.
- Lighter aircraft are more affected.

## 6.5 Neutral point from flight tests

Only in-flight quantities are known ($W$, $V$, $\eta$, $\beta$, CG). Compare **two trimmed speeds** $V$ and $V+\Delta V$ with elevator angles $\eta$ and $\eta+\Delta\eta$:
- The tail lift change is $\Delta C_{L_T} = k\left((1-\epsilon_\alpha)\Delta\alpha+\frac{a_2}{a_1}\Delta\eta\right)$, with $\Delta\alpha = \Delta C_{L^*}/C_{L^*_\alpha}$.
- The moment equation gives $\dfrac{\Delta C_{L_T}}{\Delta C_{L^*}} = \dfrac{h-h_0}{K}$.

Equating these:

$$
\boxed{h_n - h = H_{s,\text{fixed}} = -Kk\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}}}
$$

- $d\eta/dC_{L^*}$ is **easy to measure**. $K$, $k$ and $a_2/a_1$ are uncertain.
- **Procedure**: plot $\eta$ vs $C_{L^*}$ for several CG positions and find the slope $d\eta/dC_{L^*}$ for each. Plot the slope against $h$ and **extrapolate to zero slope**. That value of $h$ is $h_n$.
- CG location is measured on scales: $F_fh_fc+F_rh_rc-(F_f+F_r)hc = 0$.

## 6.6 Lateral and directional stability

See [[Lateral and Directional Stability]].

- **Controls**: elevator for pitch ($\theta$, $q$), ailerons for roll ($\phi$, $p$), rudder for yaw ($\psi$, $r$). Body axes: $x$ forward, $y$ starboard, $z$ down.
- **Directional stability**: when the aircraft yaws, the **vertical fin** creates a side force $F_{vt}$ aft of the CG, which gives a restoring moment. The **fuselage is destabilising** (side force ahead of the CG).
- **Crosswind landing**: the aircraft weathercocks into the wind. The rudder alters the fin camber, analogous to the elevator.
- **Fin sizing**: set by directional stability, dynamic handling qualities, and rudder authority for crosswind take-off/landing and **asymmetric engine failure**.
- **Yaw-to-roll coupling**: yawing makes one wing faster, giving more lift and a rolling moment. This underlies the **Dutch roll** oscillation.
- **Roll damping**: the down-going wing sees a higher $\alpha$ and more lift, which opposes the roll.
- **Roll-to-yaw coupling**: bank leads to sideslip, which yaws the aircraft through the fin. Without enough lateral stability this gives the **spiral mode**.
- **Lateral stability** (restoring roll moment in sideslip):
  - **Dihedral**: sideslip gives a wing-normal velocity component with higher $\alpha$ on the leading wing.
  - **High wing**: a side force from skin friction acts above the CG, plus fuselage interference that increases $\alpha$ on the upwind wing (a low wing is destabilising).
  - **Sweep**: the leading wing has a larger normal velocity and more lift.
- **Too stable** (high wing + dihedral + sweep) gives poor controllability. The fix is **anhedral** (Harrier).

---

## Exam formula sheet (provided in the Mechanics of Flight paper)

$$
C_{L^*} = C_L+C_{L_T}\tfrac{S_T}{S} = C_W\cos\gamma,\quad C_{M_0}+C_{L^*}(h-h_0)-C_{L_T}K=0,\quad K=\tfrac{S_Tl}{Sc}
$$

$$
C_L = a_0\tfrac{\pi Ae}{\pi Ae+a_0}(\alpha-\alpha_0),\quad \epsilon = \tfrac{C_L}{\pi Ae} = \epsilon_\alpha(\alpha-\alpha_0),\quad C_{L_T}=a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\quad C_{M_H}=b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta
$$

$$
H_s = h_0-h+K\tfrac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\quad C_{L_{T,\alpha}} = k(1-\epsilon_\alpha),\quad k = a_1\tfrac{\pi A_Te_T}{\pi A_Te_T+a_1},\quad \bar k:\ a_1\to\bar a_1 = a_1-a_2\tfrac{b_1}{b_2}
$$

$$
n = \tfrac{L^*}{W} = \tfrac{V^2}{gR}+1,\quad \Phi=\tfrac{\rho Sl}{2m},\quad C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}}
$$

## Links
- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T5 - Finite Wing Theory]]
- Problems: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] · [[SESA2022 Static Stability Past Paper Questions Solutions]]
- Related: dynamic stability and control in [[SESA2027 Aerospace Mechanics & Control Hub|SESA2027]] and [[SESA3047 Advanced Aerospace Mechanics & Control]]

## Sources
- `02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf` (slides 1–119), transcript `Static Stability.txt`
