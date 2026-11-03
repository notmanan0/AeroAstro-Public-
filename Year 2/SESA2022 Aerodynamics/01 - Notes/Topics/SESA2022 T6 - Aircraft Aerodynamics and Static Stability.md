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
status: lectured
coverage: "Lectures 14–25 Nov 2025 (six lectures)"
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA2022 T4 - Thin Aerofoil Theory]]", "[[SESA2022 T5 - Finite Wing Theory]]"]
next_topics: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]"]
key_concepts: ["[[Neutral Point and Static Margin]]", "[[Stick-Fixed vs Stick-Free Stability]]", "[[Manoeuvre Point and Manoeuvre Margin]]", "[[Lateral and Directional Stability]]"]
tutorial_sheets: ["[[SESA2022 Examples Sheet 6 - Static Stability Solutions]]", "[[SESA2022 Static Stability Past Paper Questions Solutions]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-14.txt … 2025-11-25.txt", "02 - Sources/Stability/Static Stability.txt (earlier-year recording)"]
---

# SESA2022 T6 - Aircraft Aerodynamics and Static Stability

> [!abstract] Summary
> A conventional aircraft trims in pitch with a tailplane, using force balance normal to the flight path and moment balance about the CG, with the tail lift linear in its effective incidence, the elevator angle and the trim-tab angle, and the wing and tail downwash taken from [[SESA2022 T5 - Finite Wing Theory|lifting-line theory]]. Static stability needs $dC_{M_{CG}}/d\alpha<0$, which means the CG ahead of the neutral point and a positive static margin $H_s = h_n-h$; a floating elevator (stick free) reduces the margin, and pitch rate in a manoeuvre adds damping that puts the manoeuvre point behind the neutral point. Lateral and directional stability come from the fin, dihedral, a high wing and sweep.

> [!summary]- Exam use: quick path
> - **Use it when:** you are given a table of aircraft data ($A$, $e$, $S$, $c$, $l$, $h_0$, $h$, $C_{M_0}$, $a_1$–$a_3$, $b_1$–$b_3$, $m$, $V$, $\rho$) and asked for trim ($\alpha$, $\eta$, $\beta$), neutral points, static margins or a manoeuvre margin. *"Mostly a module about doing calculations with numbers and explaining physical phenomena"*, with short proofs at most (21 Nov, ll. 45–52).
> - **Assumptions:** steady, trimmed, small angles in radians; thrust and drag through the CG; symmetric tail ($M_{T_0} = 0$); linear lift and hinge-moment models; downwash $\epsilon\approx C_L/\pi Ae$; $h$ measured downstream from the datum as a fraction of $c$.
> - **Method:** 1. $C_W$, $C_{L^*} = C_W\cos\gamma$, $K = S_Tl/Sc$. 2. $C_{L_T}$ from the moment equation, then $C_L$, then $\alpha$. 3. $\epsilon_\alpha$, $\alpha_{T_{eff}}$, then $\eta$ (and $\beta$ if stick free). 4. Margins: $k$ (or $\bar k$ with $\bar a_1$), $C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)$, $H_s = h_0-h+KC_{L_{T,\alpha}}/C_{L^*_\alpha}$. 5. Manoeuvre: $\Phi = \rho Sl/2m$ in the manoeuvre $C_{L_{T,\alpha}}$.
> - **Common mistakes:** using the 2D slope $a_1$ instead of $k$ (3D tail with its own downwash); forgetting $\cos\gamma$ in a climb.
> - **Plan the order before you calculate**: *"you need to have a plan for how you're going to... the order in which you're going to address these"*, otherwise you meet equations with more than one unknown (21 Nov, ll. 443–447). The data tables include quantities you do not need (18 Nov, ll. 395–397; 20 Nov, l. 443).
> - Revision-lecture advice (7 Jan revision, ll. 15–31, 451–580): Q5 is new to SESA2022; past SESA2025 Q2s are relevant, but this year's questions are about two-thirds as long, and parts on trim drag were not covered. *"It really is just algebra"*: start from the static-margin definition or the $\alpha_{T_{eff}}$ equation. Trim questions need more intermediate numbers than static margins.
> - **Practise:** [[#Worked example: the Examples Sheet 6 aircraft]] · [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]

An aircraft balances on its centre of gravity like a seesaw. The wing's lift acts near the wing's aerodynamic centre, close to the CG; the wing also produces a pitching moment that usually tries to tip the nose down. The tailplane, far behind on a long lever arm $l$, needs only a small force to balance everything. That is trim (14 Nov lecture).

Now let a gust tip the nose up. Every lifting surface sees more angle of attack and makes more lift. Lift added at the wing, a little ahead of or behind the CG, pushes the nose further up or down; lift added at the tail, far behind, always pushes the nose back down. If the net effect is nose-down, the aircraft returns by itself: it is statically stable, like a ball in a bowl rather than on a hill (19 Nov, ll. 21–41).

There is one point, the neutral point, where the extra lift from a gust effectively acts. Put the CG ahead of it and the aircraft weathercocks back into the wind; put the CG behind it and every disturbance grows. The distance between them, the static margin, is the safety factor of longitudinal stability (19 Nov, l. 15). A very large margin makes the aircraft stable but sluggish and hard to manoeuvre; fighters such as the X-29 are deliberately unstable and flown by computer (19 Nov, l. 230).

---

## 1. Tailplane aerodynamics and trim (14 and 18 Nov lectures)

Means of trim in pitch (roll and yaw already trimmed): canard (military deltas: the stick rotates the canard), tailless with elevons at the tips (e.g. B-2: deflected together for pitch, differentially for roll), tailplane. This course does only the conventional tailplane (14 Nov, ll. 43–63). Compared with the earlier theory, *"this part of the module is really just Newton's laws of equilibrium"* (14 Nov, ll. 14–19).

![[stab_trim_geometry.png|900]]

### Forces, simplifications and conventions

- Thrust and drag act along the same axis through the CG, so they produce no moment. Along the path: $T = D + D_T + W\sin\gamma$. Real aircraft often have high- or low-mounted engines whose offset adds a moment; the course ignores it (14 Nov, ll. 103–112; 19 Nov, ll. 137–142).
- The tailplane is symmetric and small, so its own moment about its AC, $M_{T_0}$, is zero. Most tailplanes are symmetric, but some are cambered to give positive lift most of the time (14 Nov, ll. 112–116, 211–220).
- $M_0$: wing pitching moment about the wing AC, constant with $\alpha$ (T4), nose-up positive (14 Nov, ll. 92, 137).
- $l$: distance from the wing AC to the tail AC.
- $hc$ and $h_0c$: distances of the CG and the wing AC from a datum, as fractions of the MAC $c$, positive downstream (14 Nov, l. 133).
- Forces positive upward; $\gamma$ = flight-path angle (positive climbing); pitch angle $\theta = \gamma+\alpha$ (14 Nov, ll. 64–86).
- Tail lift can be either sign. With the CG aft of the wing AC the lift–weight couple pitches the nose up and the tail must lift upwards; with a forward CG it must push down. A forward CG helps stability but can spoil handling (14 Nov, ll. 197–211).

### Trim equations: derivation

**Force balance normal to the flight path:**

$$
L + L_T - W\cos\gamma = 0\quad\Rightarrow\quad L^* \equiv L+L_T = W\cos\gamma
$$

Moment balance about the CG (nose-up positive). The wing lift acts $(h-h_0)c$ ahead of the CG when $h>h_0$, so it gives a nose-up moment. The tail lift acts $l-(h-h_0)c$ behind the CG, so positive $L_T$ gives a nose-down moment (14 Nov, ll. 155–170):

$$
M_0 + L(h-h_0)c - L_T\big(l-(h-h_0)c\big) = 0
$$

Expand the bracket and collect the $(h-h_0)c$ terms:

$$
M_0 + (L+L_T)(h-h_0)c - L_Tl = 0
$$

Non-dimensionalise by $\tfrac12\rho V^2S$ for forces (with $L_T = \tfrac12\rho V^2S_TC_{L_T}$) and $\tfrac12\rho V^2Sc$ for moments:

$$
\boxed{C_{L^*} = C_L + C_{L_T}\frac{S_T}{S} = C_W\cos\gamma},\qquad C_W = \frac{W}{\tfrac12\rho V^2S}
$$

$$
\boxed{C_{M_0} + C_{L^*}(h-h_0) - C_{L_T}K = 0},\qquad K \equiv \frac{S_Tl}{Sc}\ \text{(tail volume ratio)}
$$

The term $L_Tl$ becomes $\tfrac12\rho V^2S_TC_{L_T}l$, and dividing by $\tfrac12\rho V^2Sc$ gives $C_{L_T}S_Tl/(Sc) = C_{L_T}K$.

**Tail lift can be positive or negative.** With a small $C_{M_0}$, a CG behind the wing AC ($h>h_0$) needs positive tail lift and a CG ahead needs negative tail lift. A forward CG helps stability but needs more tail force (trim drag) and gives poor handling at low speed. Tail sections may be symmetric or negatively cambered (14 Nov, ll. 199–215).

### Tailplane components

- Horizontal stabiliser (fixed, or adjustable setting $\alpha_s$).
- Elevator ($\eta$, positive trailing-edge down) to control tail lift.
- Trim tab ($\beta$) to cancel the hinge moment so the pilot can fly hands-off: *"The trim tab is then to be lazy"* (14 Nov, ll. 246–249). In equilibrium flight the elevator is effectively the speed control and the throttle the climb control (14 Nov, ll. 242–245; 18 Nov, ll. 104–106).
- Horn balance (shielded or unshielded) to reduce stick forces (14 Nov, ll. 361–372).

### Downwash and the tail angle of attack

The tail flies in the wing's downwash $\epsilon$, and its own trailing vortices give it a further induced angle $\epsilon_T$ (14 Nov, ll. 270–320):

$$
\alpha_T = \alpha+\alpha_s,\qquad \alpha_{T_{eff}} = \alpha+\alpha_s-\epsilon-\epsilon_T
$$

The course models both with the lifting-line induced angle (18 Nov, ll. 515–527):

$$
\epsilon \approx \frac{C_L}{\pi Ae} = \frac{C_{L_\alpha}(\alpha-\alpha_0)}{\pi Ae} = \epsilon_\alpha(\alpha-\alpha_0),\quad \epsilon_\alpha \equiv \frac{d\epsilon}{d\alpha} = \frac{C_{L_\alpha}}{\pi Ae},\qquad \epsilon_T = \frac{C_{L_T}}{\pi A_Te_T}
$$

> [!warning] A modelling choice, not a law
> The downwash a long way behind an elliptic wing is $2\alpha_i$, not $\alpha_i$; real tails sit in between and above or below the wake. $\epsilon\approx C_L/\pi Ae$ is the course model and is what the exam formula sheet uses. In practice $\epsilon_\alpha$ *"might be something you want to"* measure (18 Nov, ll. 515–518).

Substitute and collect the $\alpha$ terms:

$$
\alpha_{T_{eff}} = \alpha+\alpha_s-\epsilon_\alpha\alpha+\epsilon_\alpha\alpha_0-\frac{C_{L_T}}{\pi A_Te_T}
$$

$$
\boxed{\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}},\qquad \frac{\partial\alpha_{T_{eff}}}{\partial\alpha} = 1-\epsilon_\alpha\ (\text{at fixed }C_{L_T})
$$

Wing lift with the finite-wing slope from T5 (elliptic form with $e$):

$$
C_L = C_{L_\alpha}(\alpha-\alpha_0),\qquad C_{L_\alpha} = \frac{a_0}{1+a_0/(\pi Ae)} = a_0\frac{\pi Ae}{\pi Ae+a_0}
$$

Note $\alpha_0$ here is the zero-lift angle, $\alpha_{L=0}$ in T4–T5, and $A$ is the aspect ratio, $AR$ in T5: past mechanics-of-flight papers use $A$ (18 Nov, ll. 398–401).

### Tail lift and hinge-moment models (linear)

$$
C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta,\qquad a_1 = \frac{\partial C_{L_T}}{\partial\alpha_{T_{eff}}},\ a_2 = \frac{\partial C_{L_T}}{\partial\eta},\ a_3 = \frac{\partial C_{L_T}}{\partial\beta}
$$

$$
C_{M_H} = b_1\alpha_{T_{eff}}+b_2\eta+b_3\beta
$$

- $a_1$ is a 2D lift slope (often $2\pi$); $a_2$ is the flap effectiveness of [[SESA2022 T4 - Thin Aerofoil Theory#7. Trailing-edge flaps (31 Oct lecture)|T4 §7]]; these are "aerodynamic derivatives" (14 Nov, ll. 322–360). Expect $a_1>a_2>a_3$: the elevator and tab cover smaller parts of the tail (18 Nov, ll. 203–211).
- *"The Bs tend to all be negative"* (18 Nov, l. 160), so a gust is opposed by the hinge moment (18 Nov, l. 199). $|b_3|$ is the largest because the tab has the longest arm about the hinge (18 Nov, ll. 214–220). A horn balance reduces $|b_1|$ and $|b_2|$.
- Coefficients come from TAT (see [[Trailing-Edge Flap in Thin Aerofoil Theory]]), wind tunnels or CFD.

**Trim tab principle**: to get negative tail lift the elevator must go up. Deflecting the tab down ($\beta>0$) creates a hinge moment that pushes the elevator up until $C_{M_H}=0$ ($\eta<0$, $L_T<0$). The stick force is then zero and the aircraft is trimmed.

## 2. Trim: stick fixed and stick free

See [[Stick-Fixed vs Stick-Free Stability]].

| | Stick fixed | Stick free |
|---|---|---|
| How | Pilot holds the elevator at $\eta$ against the hinge moment | Trim tab set so $C_{M_H}=0$ and the pilot applies zero force |
| Hinge moment | $C_{M_H}\neq0$ | $C_{M_H}=0$ |
| Tab | $\beta = 0$ (assumed) | $\beta\neq0$ |
| Tail lift | $C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta$ | $C_{L_T} = \bar a_1\alpha_{T_{eff}}+\bar a_3\beta$ |

### Stick-free tail lift: derivation

Set $C_{M_H} = 0$ and solve for the floating elevator angle:

$$
\eta = -\frac{b_1\alpha_{T_{eff}}+b_3\beta}{b_2}
$$

Substitute into $C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta+a_3\beta$:

$$
C_{L_T} = a_1\alpha_{T_{eff}}-\frac{a_2b_1}{b_2}\alpha_{T_{eff}}-\frac{a_2b_3}{b_2}\beta+a_3\beta
$$

Collect terms:

$$
C_{L_T} = \bar a_1\alpha_{T_{eff}}+\bar a_3\beta,\qquad \boxed{\bar a_1 \equiv a_1 - a_2\frac{b_1}{b_2},\quad \bar a_3\equiv a_3-a_2\frac{b_3}{b_2}}
$$

**Floating tendency**: with $b_1/b_2>0$ (both negative) a gust $\Delta\alpha_{T_{eff}}>0$ gives $\Delta\eta = -\Delta\alpha_{T_{eff}}b_1/b_2<0$: the elevator floats up, so the tail makes less lift per unit $\alpha$. That opposes the gust and smooths the response, but too negative a $b_1$ costs pitch stiffness (18 Nov, ll. 173–202). For the Examples Sheet 6 aircraft, $a_1 = 6.28$ rad⁻¹ (fixed) versus $\bar a_1 = 5.78$ rad⁻¹ (free), an 8% loss (the lecture says *"something like a 10% reduction"*): the tail would have to sit about that much further aft to give the same restoring moment (18 Nov, ll. 223–245). A horn balance reduces $b_1$ and helps.

Other ways to trim (18 Nov, ll. 246–385):
- Fixed tail (e.g. Pilatus PC-6): light, cheap, simple, safe; but the elevator is deflected in almost every flight state, which costs drag.
- All-moving tail (stabilator), e.g. the Hawk: high trimming power, wide CG range, low trim drag, highly manoeuvrable; heavier structure.
- Adjustable tail (airliners, e.g. E-170): slowly changes $\alpha_s$ for trim and uses the elevator for control; useful when flaps and slats move the AC, but it needs powered actuation.
- **Wing trailing-edge devices**: little moment arm about the CG, except on large swept wings (18 Nov, ll. 346–364).
- **Moving the CG**: Concorde pumped fuel between trim tanks because the aerodynamic centre moves aft through Mach 1 (18 Nov, ll. 365–385).

Tail setting for zero elevator ($\eta = \beta = 0$, the all-moving-tail case, 18 Nov, ll. 322–341): solve the trim equations for $C_L$ and $C_{L_T}$, get $\alpha$ from $C_L = C_{L_\alpha}(\alpha-\alpha_0)$, then solve $C_{L_T} = a_1\alpha_{T_{eff}}$ for $\alpha_s$.

### Solution algorithm for trim problems

1. $C_W = \dfrac{mg}{\tfrac12\rho V^2S}$, $C_{L^*} = C_W\cos\gamma$, $K = \dfrac{S_Tl}{Sc}$.
2. Moment equation: $C_{L_T} = \dfrac{C_{M_0}+C_{L^*}(h-h_0)}{K}$ (18 Nov, l. 460).
3. $C_L = C_{L^*} - C_{L_T}S_T/S$.
4. $C_{L_\alpha} = a_0\dfrac{\pi Ae}{\pi Ae+a_0}$, so $\alpha = \alpha_0 + C_L/C_{L_\alpha}$.
5. $\epsilon_\alpha = C_{L_\alpha}/(\pi Ae)$, then $\alpha_{T_{eff}}$.
6. Controls:
   - Stick fixed: $\eta = (C_{L_T}-a_1\alpha_{T_{eff}})/a_2$.
   - Stick free: solve $\begin{pmatrix}a_2&a_3\\b_2&b_3\end{pmatrix}\begin{pmatrix}\eta\\\beta\end{pmatrix} = \begin{pmatrix}C_{L_T}-a_1\alpha_{T_{eff}}\\-b_1\alpha_{T_{eff}}\end{pmatrix}$.

This algorithm reproduces all the Examples Sheet 6 answers: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]].

## 3. Longitudinal static stability (19 Nov lecture)

**Static stability**: if the system is disturbed from equilibrium, the forces and moments created *initially* tend to return it. ("Static", as opposed to the time history of the motion, which is dynamic stability in [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|SESA2027]].) Pictures: a ball bearing in a channel (stable), on a flat surface (neutral), on a hill (unstable) (19 Nov, ll. 21–41). The static analysis *"says nothing about the modes"* (phugoid, short period, Dutch roll and so on), which need the full six-degree-of-freedom small-perturbation analysis of a later flight-dynamics module (19 Nov, ll. 42–69).

For an aircraft disturbed by $\Delta\alpha>0$, stability needs a nose-down moment $\Delta C_{M_{CG}}<0$:

$$
\boxed{\frac{dC_{M_{CG}}}{d\alpha}<0}
$$

For trim at a useful positive $\alpha_e$ we also need $C_{M_{CG}}(\alpha=0) > 0$ (so that the negative slope crosses zero at positive $\alpha$).

![[stab_cm_alpha.png|520]]

**Contributions**: main — wing/fuselage lift, wing pitching moment, tail lift; minor — power effects, drag, other components. $dC_{M_{CG}}/d\alpha$ is the pitch stiffness (19 Nov, ll. 218–219); a steeper negative slope means more of it: the stability versus manoeuvrability trade-off. Moving the CG aft flattens the curve towards neutral (19 Nov, ll. 212–227). The forward-swept X-29 was deliberately unstable for manoeuvrability and flyable only through fly-by-wire with no manual backup; canard fighters are usually unstable too (19 Nov, ll. 228–241).

> [!example] Wind-tunnel $C_M$–$\alpha$ (19 Nov, ll. 147–200)
> Measured about the CG: the wing contribution rises with $\alpha$, the tail contribution falls, and the total has a negative slope. The model is naturally trimmed only where the total crosses $C_{M_{CG}} = 0$, *"somewhere just below six degrees"*; at every other $\alpha$ a pilot would need elevator or tab. Trim means both the vertical force balance and $C_{M_{CG}} = 0$ (l. 190).

### Moment derivative

Away from trim the left-hand side of the moment equation is the residual moment:

$$
C_{M_{CG}} = C_{M_0} + C_{L^*}(h-h_0) - C_{L_T}K
$$

Differentiate with respect to $\alpha$; $C_{M_0}$ is constant (it is about the AC):

$$
\frac{dC_{M_{CG}}}{d\alpha} = C_{L^*_\alpha}(h-h_0)-C_{L_{T,\alpha}}K,\qquad C_{L^*_\alpha} = C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}
$$

- The first term is destabilising if the CG is behind the wing AC ($h>h_0$).
- The second term is stabilising for a tail behind the CG ($K>0$). For a canard $l<0$, so $K<0$ and the term is destabilising (19 Nov, ll. 306–318).

### Neutral point and static margin

See [[Neutral Point and Static Margin]]. The neutral point $h_n$ is the CG position that makes the slope zero:

$$
C_{L^*_\alpha}(h_n-h_0)-C_{L_{T,\alpha}}K = 0\quad\Rightarrow\quad \boxed{h_n = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}}
$$

Substitute $h_0 = h_n-KC_{L_{T,\alpha}}/C_{L^*_\alpha}$ back into the slope:

$$
\frac{dC_{M_{CG}}}{d\alpha} = C_{L^*_\alpha}(h-h_n)+KC_{L_{T,\alpha}}-KC_{L_{T,\alpha}} = -C_{L^*_\alpha}(h_n-h)
$$

So with the static margin $H_s\equiv h_n-h$:

$$
\boxed{H_s = h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}}},\qquad \frac{dC_{M_{CG}}}{d\alpha} = -C_{L^*_\alpha}H_s,\qquad \text{stable} \iff H_s>0
$$

The neutral point is the aerodynamic centre of the whole aircraft (14 Nov, l. 423): the CG must be ahead of it (19 Nov, ll. 355–371). Too large a margin makes the aircraft unresponsive and needs large stick forces (19 Nov, ll. 390–394); the margin should stay positive stick fixed, stick free and in manoeuvres (19 Nov, ll. 407–416).

### Tail lift slope, stick fixed: derivation

Stick fixed, $\beta = 0$. Substitute $\alpha_{T_{eff}}$ into $C_{L_T} = a_1\alpha_{T_{eff}}+a_2\eta$; $C_{L_T}$ appears on both sides through $\epsilon_T$:

$$
C_{L_T} = a_1\left[(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s\right]-\frac{a_1}{\pi A_Te_T}C_{L_T}+a_2\eta
$$

Move the $C_{L_T}$ term to the left:

$$
C_{L_T}\left(1+\frac{a_1}{\pi A_Te_T}\right) = a_1\left[(1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s+\frac{a_2}{a_1}\eta\right]
$$

Divide:

$$
C_{L_T} = k\left((1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s+\frac{a_2}{a_1}\eta\right),\qquad k\equiv \frac{a_1}{1+a_1/(\pi A_Te_T)} = a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}
$$

Differentiate at fixed $\eta$:

$$
\boxed{C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)}
$$

> [!warning] Write out $C_{L_T}$ in full first
> *"Good to write down the equation explicitly for CLT before you do the partial differentiation, otherwise you would have missed this factor K"* (19 Nov, ll. 505–511). Differentiating $a_1\alpha_{T_{eff}}$ directly loses the tail's own downwash.

The chain is: 2D aerofoil slope $a_1$ → 3D tail slope $k$ (the same finite-wing correction as $C_{L_\alpha}$) → 3D tail in the wing's downwash, $k(1-\epsilon_\alpha)$ (19 Nov, ll. 513–527). The model $\epsilon_\alpha\approx C_{L_\alpha}/\pi Ae$ is *"not a very accurate model"*: by the tail the sheet is rolling up into tip vortices, so in practice $\epsilon_\alpha$ is measured or found by CFD (19 Nov, ll. 527–550; 14 Nov, ll. 318–321).

**Stick free**: replace $a_1\to\bar a_1$, giving $\bar k = \bar a_1\dfrac{\pi A_Te_T}{\pi A_Te_T+\bar a_1}$ and $C_{L_{T,\alpha}} = \bar k(1-\epsilon_\alpha)$. Because $\bar k<k$ (when $b_1/b_2>0$), the stick-free neutral point is further forward:

$$
H_{s,\text{stick fixed}} > H_{s,\text{stick free}}
$$

*"You have to do the numbers to really find that out"* (19 Nov, ll. 594–603).

![[stab_margins_axis.png|900]]

## 4. Manoeuvre stability (20 Nov lecture)

See [[Manoeuvre Point and Manoeuvre Margin]].

![[stab_pullup.png|620]]

### Steady pull-up

Constant radius $R$, speed $V$, pitch rate $q = V/R$, level at the bottom of the circle (20 Nov, ll. 57–127). $p$, $q$, $r$ are the body rates in roll, pitch and yaw, signed by the right-hand rule (20 Nov, ll. 71–90). Newton's second law towards the centre:

$$
L^*-W = m\frac{V^2}{R}
$$

Divide by $W = mg$ and define the load factor $n\equiv L^*/W = C_{L^*}/C_W$:

$$
n-1 = \frac{V^2}{gR}
$$

### Pitch rate increases the tail angle of attack

The aircraft rotates nose-up at $q$ about the CG, so the tail, a distance $l-(h-h_0)c\approx l$ behind it, moves down at about $ql$. The tail therefore sees an extra upward relative flow and an extra angle (20 Nov, ll. 128–170). Two assumptions: small angles ($\tan\Delta\alpha\approx\Delta\alpha$) and $l\gg(h-h_0)c$:

$$
\Delta\alpha_{T_q}\approx\frac{ql}{V}
$$

Use $q = V/R$:

$$
\Delta\alpha_{T_q} = \frac lR
$$

Use $1/R = (n-1)g/V^2$:

$$
\Delta\alpha_{T_q} = \frac{(n-1)gl}{V^2}
$$

Write $g/V^2$ with $C_W = \frac{mg}{\frac12\rho V^2S}$, i.e. $\frac{g}{V^2} = C_W\frac{\rho S}{2m}$:

$$
\Delta\alpha_{T_q} = (n-1)C_W\frac{\rho Sl}{2m} = (n-1)C_W\Phi,\qquad \boxed{\Phi\equiv\frac{\rho Sl}{2m}}\ (\text{mass parameter})
$$

(20 Nov, ll. 232–246.) The extra tail lift opposes the pitch rate: pitch damping. So

$$
\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\frac{C_{L_T}}{\pi A_Te_T}+(n-1)C_W\Phi
$$

### Manoeuvre tail lift slope: derivation

At fixed speed, $C_W$ is constant and $(n-1)C_W = C_{L^*}-C_W$, so

$$
\frac{d}{d\alpha}\left[(n-1)C_W\Phi\right] = \Phi\,C_{L^*_\alpha} = \Phi\left(C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}\right).
$$

Repeat the stick-fixed derivation with the extra term; the factor $k$ is unchanged (written out in full in the lecture, 20 Nov, ll. 264–356):

$$
C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)+k\Phi\left(C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}\right)
$$

Collect $C_{L_{T,\alpha}}$:

$$
C_{L_{T,\alpha}}\left(1-k\Phi\frac{S_T}{S}\right) = k\left(1-\epsilon_\alpha+\Phi C_{L_\alpha}\right)
$$

$$
\boxed{C_{L_{T,\alpha}} = k\frac{1-\epsilon_\alpha+\Phi C_{L_\alpha}}{1-k\Phi\frac{S_T}{S}}}
$$

The manoeuvre point follows exactly as the neutral point did, with this larger $C_{L_{T,\alpha}}$:

$$
\boxed{h_m = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}\frac{S_T}{S}}},\qquad H_m = h_m-h
$$

- $C_{L_{T,\alpha}}$ is higher in a manoeuvre, so the manoeuvre point lies aft of the neutral point: the aircraft is more stable while manoeuvring.
- $\Phi\propto\rho$: the effect shrinks with altitude, where the aircraft feels less stable and more responsive. Lighter aircraft (small $m$) are more affected (20 Nov, ll. 361–390).
- The aircraft therefore *"is going to feel less responsive to a pilot"* in a manoeuvre (20 Nov, ll. 413–414). If manoeuvring had reduced stability, it would have been the design case; since it increases stability, level flight is the critical case (20 Nov, ll. 33–37).
- Three points to know: stick-fixed NP, stick-free NP and stick-fixed MP. The stick-free manoeuvre point is skipped *"in the interest of sanity"* (20 Nov, ll. 428–434). For stick free only $k\to\bar k$ changes; $C_{L_\alpha}$, $K$, $\epsilon_\alpha$ and $\Phi$ are reused (20 Nov, ll. 546–594).
- Small rolling or yawing does not change this: for small perturbations the longitudinal and lateral problems decouple (20 Nov, ll. 457–473).

## 5. Neutral point from flight tests (21 Nov lecture)

Only in-flight quantities are known ($W$, $V$ from a pitot probe, $\eta$ and $\beta$ from calibrated transducers, CG) (21 Nov, ll. 125–130). Before flight test, estimates come from back-of-envelope theory, ESDU data sheets, CFD and wind tunnels (an order of magnitude dearer than computation), with a trend towards less testing (21 Nov, ll. 97–122). The flight-test course (a Saab 340B at Southampton Airport, after the exams) does this exercise (21 Nov, ll. 1–6, 366–390).

**CG from scales.** With the aircraft on front and rear scales at $h_fc$ and $h_rc$ from the datum, moments about the datum (21 Nov, ll. 125–153):

$$
F_fh_fc+F_rh_rc-(F_f+F_r)hc = 0\quad\Rightarrow\quad h = \frac{F_fh_f+F_rh_r}{F_f+F_r}
$$

Any moment centre works; the datum is just a common reference. Measure the empty aircraft, then add pilots and payload as point masses (21 Nov, ll. 152–161).

**Derivation of the flight-test formula.** Trim at two speeds. Differencing the moment equation (constant $C_{M_0}$, $h$):

$$
(h-h_0)\,\Delta C_{L^*} = K\,\Delta C_{L_T}\quad\Rightarrow\quad\frac{\Delta C_{L_T}}{\Delta C_{L^*}} = \frac{h-h_0}{K}
$$

Differencing the stick-fixed tail lift (fixed $\alpha_s$, $\alpha_0$), with $\Delta\alpha\approx\Delta C_{L^*}/C_{L^*_\alpha}$:

$$
\Delta C_{L_T} = k\left((1-\epsilon_\alpha)\frac{\Delta C_{L^*}}{C_{L^*_\alpha}}+\frac{a_2}{a_1}\Delta\eta\right)
$$

Divide by $\Delta C_{L^*}$ and equate with the first result:

$$
\frac{h-h_0}{K} = \frac{k(1-\epsilon_\alpha)}{C_{L^*_\alpha}}+k\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}}
$$

The first term on the right is $C_{L_{T,\alpha}}/C_{L^*_\alpha} = (h_n-h_0)/K$. Multiply by $K$ and subtract:

$$
h-h_n = Kk\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}}\quad\Rightarrow\quad\boxed{h_n - h = H_{s,\text{fixed}} = -Kk\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}}}
$$

- $d\eta/dC_{L^*}$ is easy to measure; $K$, $k$ and $a_2/a_1$ are uncertain.
- **Procedure**: plot $\eta$ against $C_{L^*}$ for several CG positions; find the slope for each; plot the slope against $h$ and extrapolate to zero slope. That $h$ is $h_n$ (21 Nov, ll. 296–355). Positive margin means $d\eta/dC_{L^*}<0$: more up-elevator to fly slower. The upper end of each line is $C_{L,max}$ (minimum speed).
- **Do not fly near zero slope**: there the speed changes with no control input, the limit of static stability (21 Nov, ll. 334–345). Moving the CG aft flattens the lines (21 Nov, ll. 348–351).
- The slope of the second plot measures $a_1/(Kka_2)$, a check on the theoretical estimates (21 Nov, ll. 356–364).
- **Stick free**: plot $d\beta/dC_{L^*}$ against $h$ instead; the slopes have the opposite sign (21 Nov, ll. 368–372).

## 6. Lateral and directional stability (25 Nov lecture)

See [[Lateral and Directional Stability]].

This lecture is *"entirely qualitative"* (25 Nov, ll. 1–3).

- **Controls**: elevator for pitch ($\theta$, $q$), ailerons for roll ($\phi$, $p$), rudder for yaw ($\psi$, $r$). Body axes: $x$ forward, $y$ starboard, $z$ down, unlike the aerodynamic axes used so far ($x$ streamwise, $z$ up) (25 Nov, ll. 25–47).
- **Directional stability**: in sideslip the vertical fin makes a side force $F_{vt}$ aft of the CG, giving a restoring yawing moment. The fuselage is destabilising (side force ahead of the CG), so the fin must be bigger (25 Nov, ll. 60–91). A positive yaw angle corresponds to a negative sideslip (ll. 79–80).
- **Crosswind take-off**: tyre friction holds the aircraft on the centreline until lift unloads the wheels; then the fin weathercocks it into the wind and it drifts downwind (25 Nov, ll. 92–116). The rudder alters the fin camber, the same TAT flap physics as the elevator (l. 119).
- **Fin sizing**: directional stability, dynamic handling qualities, and rudder authority for crosswind take-off/landing and asymmetric engine failure (one engine out on take-off can size the rudder; 25 Nov, ll. 128–149).
- **Yaw-to-roll coupling**: yawing makes one wing faster, giving more lift and a rolling moment; this underlies the Dutch roll, a short-period yaw–roll–sideslip oscillation that must be stable; looking out of the right window, the wingtip traces a circle (ll. 150–213).
- **Roll damping (roll subsidence)**: the down-going wing sees a higher $\alpha$ and more lift, which opposes the roll: $L_p<0$; bigger wings need bigger ailerons (ll. 214–238).
- **Roll-to-yaw coupling**: bank leads to sideslip, which yaws the aircraft through the fin. Without enough lateral stability this gives the spiral mode: nearly neutral, with a doubling time of the order of minutes, so a pilot can correct it, but dangerous for a pilot without instrument training in cloud (ll. 239–297).
- Lateral stability (restoring roll moment in sideslip):
  - **Dihedral**: sideslip gives a wing-normal velocity component with higher $\alpha$ on the leading wing.
  - **High wing**: side force acts above the CG, plus fuselage cross-flow interference that raises $\alpha$ on the upwind wing (a low wing is destabilising) (ll. 329–362). The lecture attributes the first part to skin friction along the wing acting above the CG; textbooks usually call it the pendulum or keel effect of the side force.
  - **Sweep**: the leading wing has a larger normal velocity and more lift.
- Too stable (high wing + dihedral + sweep) gives poor controllability; the fix is anhedral, typically on high-wing aircraft (Antonov transports; the Harrier on the slides) (ll. 381–390).

---

## Worked example: the Examples Sheet 6 aircraft

Data (Table 1): $A = 8$, $e = 0.90$, $S = 20$ m², $l = 7.0$ m, $c = 1.58$ m, $h_0 = 0.25$, $h = 0.40$, $C_{M_0} = -0.01$, $\alpha_0 = -2^\circ$, $a_0 = 2\pi$, $\alpha_s = -6^\circ$, $A_T = 7$, $e_T = 0.85$, $S_T = 3$ m², $a_1 = 2\pi$, $a_2 = 3.5$, $a_3 = 1.1$, $b_1 = -0.1$, $b_2 = -0.7$, $b_3 = -1.3$ (rad⁻¹), $m = 1500$ kg, $V = 50$ m/s. Worked in lecture (18, 20 and 21 Nov).

**Constants.** $K = \frac{3(7)}{20(1.58)} = 0.6646$; $\pi Ae = 22.62$; $C_{L_\alpha} = 2\pi\frac{22.62}{22.62+6.283} = 4.917$; $\epsilon_\alpha = 4.917/22.62 = 0.2174$; $\pi A_Te_T = 18.69$.

Trim in a 20° climb, stick fixed, sea level (Q1):
1. $C_W = \frac{1500(9.81)}{0.5(1.225)(50^2)(20)} = 0.4805$; $C_{L^*} = 0.4805\cos20^\circ = 0.4515$.
2. $C_{L_T} = \frac{-0.01+0.4515(0.15)}{0.6646} = 0.0869$.
3. $C_L = 0.4515-0.0869(0.15) = 0.4385$; $\alpha = -0.0349+0.4385/4.917 = 0.0543$ rad $= 3.11^\circ$.
4. $\alpha_{T_{eff}} = 0.7826(0.0543)+0.2174(-0.0349)-0.1047-0.0869/18.69 = -0.0745$ rad.
5. $\eta = \frac{0.0869+2\pi(0.0745)}{3.5} = 0.1585$ rad $= 9.08^\circ$.

The lecture quotes $C_{L^*} = 0.452$, $C_{L_T} = 0.087$, $C_L = 0.438$, $a = 4.917$ (18 Nov, l. 477).

Low-altitude cruise, stick free (Q2, $\gamma = 0$, sea level; 21 Nov, ll. 393–463):
1. $C_{L^*} = C_W = 0.480$; $C_{L_T} = \frac{-0.01+0.4805(0.15)}{0.6646} = 0.0934$; $C_L = 0.466$.
2. $\alpha = -0.0349+0.4665/4.917 = 0.0600$ rad $= 3.44^\circ$.
3. $\alpha_{T_{eff}} = 0.7826(0.0600)+0.2174(-0.0349)-0.1047-0.0934/18.69 = -0.0704$ rad.
4. Solve $a_2\eta+a_3\beta = C_{L_T}-a_1\alpha_{T_{eff}}$ and $b_2\eta+b_3\beta = -b_1\alpha_{T_{eff}}$: $\beta = -5.31^\circ$, $\eta = 10.44^\circ$ ($\bar a_1 = 5.783$).

> [!check] Python check (Q2)
> $K = 0.6646$, $C_W = 0.4805$, $C_{L_T} = 0.09341$, $C_L = 0.4665$, $\alpha = 3.435^\circ$, $\alpha_{T_{eff}} = -0.0704$ rad, $\beta = -5.310^\circ$, $\eta = 10.437^\circ$ ✔, matching the lecture's $-0.071$ rad, $-5.31^\circ$ and $10.44^\circ$.

Static margins (Q3a, b):
1. Stick fixed: $k = 2\pi\frac{18.69}{18.69+6.283} = 4.703$; $C_{L_{T,\alpha}} = 4.703(0.7826) = 3.680$; $C_{L^*_\alpha} = 4.917+3.680(0.15) = 5.469$; $H_s = -0.15+0.6646(3.680/5.469) = 0.297$.
2. Stick free: $\bar a_1 = 2\pi-3.5(0.1/0.7) = 5.783$; $\bar k = 4.417$; $C_{L_{T,\alpha}} = 3.457$; $H_s = 0.273$.
3. Slope check: $dC_{M_{CG}}/d\alpha = -C_{L^*_\alpha}H_s = -1.63$ rad⁻¹ (fixed).

Manoeuvre margin, stick fixed (Q3c, $\rho = 0.855$): $\Phi = \frac{0.855(20)(7)}{2(1500)} = 0.0399$; $C_{L_{T,\alpha}} = 4.703\frac{0.7826+0.0399(4.917)}{1-4.703(0.0399)(0.15)} = 4.736$; $H_m = -0.15+0.6646\frac{4.736}{4.917+0.710} = 0.409$. At sea level ($\Phi = 0.0572$) the same aircraft has $H_m = 0.458$: the margin falls with altitude.

> [!check] Python check
> $H_s$ (fixed, free) $= 0.2972$, $0.2726$; $H_m$ (fixed) $= 0.4090$ at $\rho = 0.855$ and $0.4578$ at sea level; $h_n = 0.697$, $0.673$; $\alpha = 3.11^\circ$, $\eta = 9.083^\circ$ ✔ (figure script `examples6_points`).

More: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] (including the stick-free trim with the $2\times2$ system) and [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Exam formula sheet (provided)

The exam paper's formula pages include the static margin definitions, $k$ and $\bar k$, $\bar a_1$, the manoeuvre equation, the mass parameter and the tail volume ratio (21 Nov, ll. 12–37):

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

## Transcript slips (14–25 Nov)

> [!warning] Slips in `SESA2022 Lecture 2025-11-14.txt` to `2025-11-25.txt` (Whisper transcripts)
> Recurring transcriptions: *"aerodynamic sensor"* = aerodynamic centre, *"CESA"* = SESA, *"tail plane"* = tailplane, *"stick-fix"* = stick-fixed, *"stick 3"*/*"stick three"* = stick free, *"camard"* = canard, *"Iter"*/*"ITER"* = eta ($\eta$). Self-corrected slips (e.g. 19 Nov, ll. 214–215; 21 Nov, ll. 401–402; 25 Nov, l. 39) are not listed.
>
> | Line | Said | Correct |
> |---|---|---|
> | 20 Nov, l. 205 | *"We can take V is equal to the pitch rate times Q"* | $V = qR$ (pitch rate times radius), so $q = V/R$ ([[#Pitch rate increases the tail angle of attack]]) |
> | 19 Nov, l. 605; 20 Nov, l. 421 | *"the aerodynamic sensor of the wing"* | aerodynamic centre |
> | 21 Nov, l. 27 | *"the maneuver equation with the extra terminate"* | the manoeuvre equation with the extra term in it ($(n-1)C_W\Phi$) |
> | 25 Nov, l. 413 | *"the maca thin airfoil question"* | the NACA (2412) thin-aerofoil question on Examples Sheet 4 |
> | 25 Nov, ll. 417–418 | *"CESA 2025"* | SESA2025 (the former flight-mechanics module whose part A covered static stability) |
> | 14 Nov, l. 278 | *"For thin airfoil, for thin wings, that was just alpha i minus alpha i"* | the downwash angle at the wing is $\alpha_i$ ($\epsilon = w/V_\infty$) |
> | 18 Nov, ll. 224–225 | $\bar a_1 = 5.78$, *"something like a 10% reduction"* | $1-5.783/2\pi = 8.0\%$ |
> | 18 Nov, l. 324 | *"we're assuming that there's just one tail, so eta and beta are equal to zero"* | an all-moving tail (no elevator or tab) |
> | 19 Nov, l. 434 | *"an elevated deflection angle, beta"* | elevator deflection angle $\eta$ (and trim-tab angle $\beta$) |
> | 19 Nov, l. 442 | *"effective angle of attack for the main wings"* | of the tailplane |
> | 19 Nov, ll. 476–477 | *"A1 is your main wing lift slope"* | $a_1$ is the tailplane section lift slope |
> | 20 Nov, l. 55 | *"keep the manoeuvre margin positive to avoid stability"* | to avoid instability |
> | 20 Nov, ll. 375–376 | *"the increase gets higher for heavier aircraft. So we increase the mass of the aircraft, we get a bigger effect"* | lighter aircraft: $\Phi = \rho Sl/2m$ grows as $m$ falls (corrected at ll. 377–379) |
> | 20 Nov, l. 579 | *"a1 minus and then there's a B3 over B1"* | $\bar a_1 = a_1-a_2b_1/b_2$ (corrected at l. 585) |
> | 21 Nov, l. 367 | *"try and figure out what your CG position is"* | the neutral point (the CG is weighed on the ground) |
> | 25 Nov, l. 168 | *"as you try to yaw to the left you're actually going to roll"* | yaw to the right (as in ll. 153–167) |
> | 25 Nov, ll. 179–182 | Dutch roll period *"five or ten seconds"*, then *"three or five seconds"* | inconsistent; the point is a short period of a few seconds |
> | 25 Nov, ll. 232–233 | *"The right-hand wing generates the opposite"* | the left-hand wing |
> | 19 Nov, ll. 362–365 | CG behind the neutral point gives *"…sorry a positive moment"* | corrected in the lecture: a nose-up (destabilising) moment |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| tail volume ratio $K = S_Tl/Sc$ | tail volume fraction (as said on 14 Nov), horizontal tail volume coefficient $\bar V_H$ | 14 Nov, l. 188; 18 Nov, l. 460 | |
| static margin $H_s$ | stability margin, "safety factor" | 19 Nov, l. 15 | Often quoted as % MAC |
| neutral point $h_n$ | aircraft aerodynamic centre, stick-fixed / stick-free neutral point | 14 Nov, l. 423; 19 Nov | |
| manoeuvre point $h_m$, margin $H_m$ | manoeuvre margin | 20 Nov | |
| mass parameter $\Phi = \rho Sl/2m$ | relative density parameter ($1/\mu$ in other texts) | 20 Nov, l. 232 | |
| $C_{L^*}$ | total (trim) lift coefficient | 14 Nov, l. 177; 18 Nov, l. 40 | |
| $\epsilon_\alpha = d\epsilon/d\alpha$ | downwash gradient | 14 Nov, ll. 296–318 | |
| $A$ (aspect ratio) | $AR$ in T5 | 14 Nov, ll. 310–313; 18 Nov, ll. 398–400 | The lecturer mixes the two deliberately *"so you're used to using both"* (20 Nov, ll. 284–286) |
| $\alpha_0$ | $\alpha_{L=0}$ in T4–T5 | 14 Nov | |
| stick fixed / stick free | controls fixed / controls free | 14 Nov, ll. 263–265; 18 Nov | |
| pitch stiffness $dC_{M_{CG}}/d\alpha$ | $C_{M_\alpha}$, longitudinal static stability derivative | 19 Nov, ll. 218–219 | |
| floating tendency ($b_1$) | | 18 Nov, ll. 200–212 | |
| roll damping / roll subsidence | $L_p$ | 25 Nov, ll. 214–238 | |
| weathercock stability | directional stability, $N_\beta$ | 25 Nov, ll. 67–69 | |
| trim tab $\beta$ | | 14 Nov | |
| all-moving tail | stabilator | 18 Nov | |

## Links

- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T5 - Finite Wing Theory]]
- Concepts: [[Neutral Point and Static Margin]] · [[Stick-Fixed vs Stick-Free Stability]] · [[Manoeuvre Point and Manoeuvre Margin]] · [[Lateral and Directional Stability]] · [[Downwash and Induced Drag]]
- Problems: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] · [[SESA2022 Static Stability Past Paper Questions Solutions]] · Formulae: [[SESA2022 Formula Sheet]]
- **Feeds into**:
  - [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] and [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]: the static margin reappears as the pitch-stiffness derivative ($M_w = -H_sC_{L^*_\alpha}$ in SESA2027 notation).
  - [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]: lateral/directional dynamics (Dutch roll, spiral, roll subsidence).

## Sources

- `02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf` (slides 1–119), `Examples6.pdf`, `Past_paper_questions_static_stability.pdf`.
- 2025-26 transcripts in `02 - Sources/Lectures/`, cited by date: `SESA2022 Lecture 2025-11-14.txt` (trim, tailplane, downwash), `2025-11-18.txt` (trim methods, Examples Sheet 6 trim), `2025-11-19.txt` (static stability, neutral point, stick fixed/free), `2025-11-20.txt` (manoeuvre point), `2025-11-21.txt` (flight test, exam formula sheet), `2025-11-25.txt` (lateral and directional stability, revision advice). Line numbers refer to these files.
- All six 2025-26 lectures above were read in full (second pass, 28 Oct 2026); every set task, exam remark and slip found is cited in this note.
- Revision lecture 2 (`SESA2022 Lecture 2026-01-07.txt`, Part B), read in full and cited as "7 Jan revision"; it works a 2024-25 SESA2025 trim and static-margin question.
- Earlier-year recording `02 - Sources/Stability/Static Stability.txt`.
- Figures: `generate_aero_t6_figures.py` (`stab_trim_geometry`, `stab_margins_axis`, `stab_pullup`); `stab_cm_alpha` predates the script. Numbers recomputed in Python (NumPy).

## Self-study tasks

*"The example sheets for sections 3, 4, 5 are pretty much what you're going to get on the exam"* (25 Nov, ll. 407–414). Static stability was previously part A of SESA2025 (flight mechanics), whose past papers are relevant (25 Nov, ll. 415–419). Attempt each task closed-book first.

### Core

- [ ] Trim equations from force and moment balance, including the non-dimensionalisation; $K$ *"should be revision"* from first year (14 Nov, ll. 147–195). → [[#Trim equations: derivation]]
- [ ] Examples Sheet 6 Q1–Q2 (trim, stick fixed and stick free) — *"recommend doing the examples sheet to see the methodology"* (19 Nov, ll. 580–590). → [[#Worked example: the Examples Sheet 6 aircraft]] · [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]
- [ ] Neutral point and static margin, stick fixed and free; confirm $H_{s,\text{fixed}}>H_{s,\text{free}}$ (19 Nov, ll. 594–603, 623–626). → [[#Neutral point and static margin]]
- [ ] Manoeuvre margin, stick fixed and free — *"if you work through all three cases, you should be reusing all the same numbers"* (20 Nov, l. 594). → [[#4. Manoeuvre stability (20 Nov lecture)]]
- [ ] Examples Sheet 6 Q2 (stick-free cruise trim), worked through in lecture with intermediate numbers (21 Nov, ll. 393–463). → [[#Worked example: the Examples Sheet 6 aircraft]]
- [ ] Explain the floating elevator in a gust and why $b_1$ should be negative but not too negative (18 Nov, ll. 173–202, 237–245). → [[#Stick-free tail lift: derivation]]
- [ ] Explain why manoeuvring raises the margin, and why the effect falls with altitude and is larger for light aircraft (20 Nov, ll. 361–414). → [[#Manoeuvre tail lift slope: derivation]]
- [ ] Static stability past-paper questions. → [[SESA2022 Static Stability Past Paper Questions Solutions]]
- [ ] Find the current exam formula sheet on Blackboard and practise locating each formula quickly (21 Nov, ll. 33–40). → [[#Exam formula sheet (provided)]]

### Further practice

- [ ] Derive $\bar a_1 = a_1-a_2b_1/b_2$ and $C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)$: short proofs of the kind that could appear (21 Nov, ll. 45–52). → [[#Stick-free tail lift: derivation]] · [[#Tail lift slope, stick fixed: derivation]]
- [ ] Derive the flight-test result $H_s = -Kk(a_2/a_1)\,d\eta/dC_{L^*}$ and sketch the extrapolation plot (21 Nov, ll. 194–355). Find the CG from two scale readings (21 Nov, ll. 131–154). → [[#5. Neutral point from flight tests (21 Nov lecture)]]
- [ ] Explain dihedral, high-wing and sweep effects, the yaw–roll couplings behind the Dutch roll and spiral modes, and why high-wing aircraft often have anhedral (25 Nov, ll. 150–390; qualitative, no equations). → [[#6. Lateral and directional stability (25 Nov lecture)]]
- [ ] SESA2025 past papers, part A (static stability), in the module's past-paper archive (25 Nov, ll. 415–419).
- [ ] *(Suggested, not lecturer-set)* For the Examples Sheet 6 aircraft, find the most aft CG for $H_s = 0.05$ stick free. Target: $h = 0.623$. → [[#Neutral point and static margin]]
