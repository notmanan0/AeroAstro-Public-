---
title: "SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part A: Dynamic Systems"
order: 2
tags:
  - sesa2027
  - state-space
  - aerodynamic-derivatives
aliases: ["Longitudinal State Equation", "Aerodynamic Derivatives"]
date: 2026-09-23
status: lectured
coverage: "L1.04 (longitudinal state equation), L1.10 (derivative estimation), L1.11 (control derivatives, transfer function)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]"]
next_topics: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
key_concepts: ["[[Aerodynamic Stability Derivatives]]", "[[State-Space Representation]]", "[[Transfer Function]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.04.pdf", "02 - Sources/Lectures/Lecture 1.10.pdf", "02 - Sources/Lectures/Lecture 1.11.pdf", "02 - Sources/Lectures/Lecture 1.04 recording.txt", "02 - Sources/Lectures/Lecture 1.10 recording.txt", "02 - Sources/Lectures/Lecture 1.11 recording.txt"]
---

# SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives

> [!abstract] Summary
> The out-of-balance forces on a perturbed aircraft are gravity plus aerodynamics, and the aerodynamic part is modelled as a first-order Taylor expansion whose coefficients are the aerodynamic derivatives ($\mathring X_u$, $\mathring Z_w$, $\mathring M_q$, …). Substituting them gives the linear state equation $\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u$ with $\mathbf x = [u,\,w,\,q,\,\theta]^T$, and choosing an output gives the transfer function $G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D$. The derivatives themselves come from simple physics, CFD, wind tunnels and free flight.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a Taylor expansion and asks which derivatives are negligible, gives dimensionless derivatives and asks for dimensional ones (with units), asks for an elevator derivative from tail data, or gives a small $\mathbf A$, $\mathbf B$, $\mathbf C$ and asks for $G(s)$.
> - **Assumptions:** stability axes at trim; small perturbations (products dropped); $\alpha\approx w/U_\infty$ and $\theta$ in radians; derivatives evaluated at trim; $\mathbf D=0$ (sensors not driven by the inputs).
> - **Method:** 1. Write $\Delta X$, $\Delta Z$, $\Delta M$ = gravity + aerodynamic (+ control) terms. 2. Drop $\mathring X_q$, $\mathring X_{\dot w}$ and, at low Mach, $\mathring M_u$. 3. Move every $\dot w$ term to the left: that gives $\mathbf M$; the rest is $\mathbf A'$ (and $\mathbf B'$). 4. $\mathbf A=\mathbf M^{-1}\mathbf A'$, $\mathbf B=\mathbf M^{-1}\mathbf B'$. 5. $G(s)=\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\mathbf B/|s\mathbf I-\mathbf A|$.
> - **Common mistakes:** the wrong reference quantity when dimensionalising (rate derivatives carry an extra $\bar c$, $\dot w$ derivatives lose a $U_\infty$); writing $\mathbf A'\mathbf M^{-1}$ instead of $\mathbf M^{-1}\mathbf A'$.
> - **Practise:** [[#Worked example: SPO state space to transfer function (PS2 Q3)]] · [[SESA2027 Mock Questions#Q2. Gravity and derivatives in the longitudinal model|Mock Q2]] · [[SESA2027 Practice Problems 2 Solutions]]

A1 left us with $\Delta X=m\dot u$, $\Delta Z=m(\dot w-qU_\infty)$, $\Delta M=I_{yy}\dot q$: mass times acceleration on the right, but nothing yet on the left. This topic fills in the left-hand side. Two things push a perturbed aircraft: gravity, whose body-axis components change as the nose rises, and aerodynamics, which change as the speed, angle of attack and pitch rate change.

Near trim each aerodynamic change is close to proportional to the perturbation that caused it, so it is a constant times $u$, $w$, $q$ or $\dot w$. Those constants are the aerodynamic derivatives. They carry the aircraft's physics: $\mathring Z_w$ is the extra lift from extra angle of attack, $\mathring M_w$ is the static stability from SESA2022, $\mathring M_q$ is the damping the tailplane provides when the aircraft pitches. Put them into Newton's equations and you get four linear first-order ODEs, $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$. Choose what a sensor measures with $\mathbf C$, and the Laplace transform turns the whole aircraft into one transfer function from elevator to pitch rate.

---

## 1. Gravitational contributions (L1.04)
In trim with climb angle $\gamma_0$: $X_{g0} = -mg\sin\gamma_0$ and $Z_{g0} = mg\cos\gamma_0$. After a small pitch perturbation $\theta$ (so $\sin\theta\approx\theta$, $\cos\theta\approx1$):

$$
X_g = -mg\sin(\gamma_0+\theta) \approx X_{g0} - mg\theta\cos\gamma_0\;\Rightarrow\;\Delta X_g = -mg\theta\cos\gamma_0,\qquad \Delta Z_g = -mg\theta\sin\gamma_0
$$

Line by line (assumptions: stability axes, $g$ constant through the perturbation, $\theta$ small and in radians; L1.04, ll. 63–92). For the axial component:

$$
X_g = -mg\sin(\gamma_0+\theta)
$$

$$
X_g = -mg(\sin\gamma_0\cos\theta+\cos\gamma_0\sin\theta)
$$

$$
X_g \approx -mg\sin\gamma_0-mg\theta\cos\gamma_0\qquad(\cos\theta\approx1,\ \sin\theta\approx\theta)
$$

$$
\Delta X_g = X_g-X_{g0} = -mg\theta\cos\gamma_0
$$

For the normal component:

$$
Z_g = mg\cos(\gamma_0+\theta)
$$

$$
Z_g = mg(\cos\gamma_0\cos\theta-\sin\gamma_0\sin\theta)
$$

$$
Z_g \approx mg\cos\gamma_0-mg\theta\sin\gamma_0
$$

$$
\Delta Z_g = Z_g-Z_{g0} = -mg\theta\sin\gamma_0
$$

In level flight ($\gamma_0 = 0$) the whole gravitational perturbation is axial: $\Delta X_g = -mg\theta$ and $\Delta Z_g = 0$.

> [!example] Climbing trim, $\gamma_0=5°$
> $\Delta X_g=-mg\theta\cos5°=-0.996\,mg\theta$ and $\Delta Z_g=-mg\theta\sin5°=-0.087\,mg\theta$. The axial term is still about 11 times larger ($\cot5°=11.4$). Pitching the nose up tips part of the weight backwards along $x$, which is why a nose-up $\theta$ slows the aircraft: the first half of the phugoid exchange in [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|A3]].

This is the same answer the rotation matrix gives. In A1, $\mathbf g_B=g(-\sin\Theta,\ \sin\phi\cos\Theta,\ \cos\phi\cos\Theta)$ for a total pitch attitude $\Theta$. In stability axes with wings level, $\Theta=\gamma_0+\theta$, so $X_g=-mg\sin(\gamma_0+\theta)$ and $Z_g=mg\cos(\gamma_0+\theta)$, exactly the starting lines above ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion#Euler angles and rotation matrices|A1]]).

## 2. Aerodynamic contributions
**DAP1**: keep only the first-order Taylor terms. A ring (°) denotes a dimensional derivative.

$$
\Delta X_a = \mathring X_u u+\mathring X_w w,\qquad \Delta Z_a = \mathring Z_u u+\mathring Z_w w+\mathring Z_q q+\mathring Z_{\dot w}\dot w,\qquad \Delta M_a = \mathring M_u u+\mathring M_w w+\mathring M_q q+\mathring M_{\dot w}\dot w
$$

- $u$: velocity perturbation.
- $w$: normal velocity perturbation, i.e. angle of attack, since $\alpha\approx w/U_\infty$.
- $q$: pitch rate. $\dot w$: rate of change of $\alpha$ (downwash lag at the tail, which turns out to be important).
- Neglected as small: $\mathring X_q$ and $\mathring X_{\dot w}$. At low speed also $\mathring M_u = 0$.

$\mathring X_q$ and $\mathring X_{\dot w}$ are dropped because $\Delta X_a$ is essentially a drag change, and pitching ($q$) or accelerating in $z$ ($\dot w$) barely changes the drag; it changes the force in $z$, and experimental data back this up (L1.04, ll. 133–169). The lecturer flagged this as a possible exam question: "if an exam question … [gave] the full expansion … which of the elements can be considered small and be negligible, then the correct answer would be those three", meaning $\mathring X_q$, $\mathring X_{\dot w}$ and, at low Mach, $\mathring M_u$. Note too that $\alpha = \tan^{-1}(w/U_\infty)\approx w/U_\infty$ only because $w\ll U_\infty$ (ll. 152–157).

## 3. The longitudinal state equation
Combine $\Delta X = m\dot u$, $\Delta Z = m(\dot w-qU_\infty)$, $\Delta M = I_{yy}\dot q$ with $\dot\theta = q$ and rearrange:

$$
\underbrace{\begin{bmatrix}m&0&0&0\\0&m-\mathring Z_{\dot w}&0&0\\0&-\mathring M_{\dot w}&I_{yy}&0\\0&0&0&1\end{bmatrix}}_{\mathbf M}\begin{bmatrix}\dot u\\\dot w\\\dot q\\\dot\theta\end{bmatrix} = \underbrace{\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\cos\gamma_0\\\mathring Z_u&\mathring Z_w&\mathring Z_q+mU_\infty&-mg\sin\gamma_0\\\mathring M_u&\mathring M_w&\mathring M_q&0\\0&0&1&0\end{bmatrix}}_{\mathbf A'}\begin{bmatrix}u\\w\\q\\\theta\end{bmatrix}
$$

$$
\boxed{\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x\quad\Longrightarrow\quad\dot{\mathbf x} = \mathbf A\mathbf x,\qquad \mathbf A = \mathbf M^{-1}\mathbf A'}
$$

The model contains the climb angle, speed, mass, inertia and aerodynamic derivatives.

How rows 2 and 3 of $\mathbf M$ and $\mathbf A'$ arise (the lecture collected terms on the slide, L1.04, ll. 223–239). Row 2 starts from the $Z$ equation with the aerodynamic and gravitational parts substituted:

$$
m(\dot w-qU_\infty) = \mathring Z_uu+\mathring Z_ww+\mathring Z_qq+\mathring Z_{\dot w}\dot w-mg\theta\sin\gamma_0
$$

Move the $\dot w$ terms to the left and the $q$ term to the right:

$$
(m-\mathring Z_{\dot w})\dot w = \mathring Z_uu+\mathring Z_ww+(\mathring Z_q+mU_\infty)q-mg\sin\gamma_0\,\theta
$$

Row 3 starts from the pitching-moment equation:

$$
I_{yy}\dot q = \mathring M_uu+\mathring M_ww+\mathring M_qq+\mathring M_{\dot w}\dot w
$$

Move the $\dot w$ term to the left:

$$
-\mathring M_{\dot w}\dot w+I_{yy}\dot q = \mathring M_uu+\mathring M_ww+\mathring M_qq
$$

The $\dot w$ derivatives end up in $\mathbf M$ because they multiply a derivative of the state, not the state.

> [!warning] Order matters
> $\mathbf A = \mathbf M^{-1}\mathbf A'$, with $\mathbf M^{-1}$ on the left. $\mathbf A'\mathbf M^{-1}$ is a different matrix (L1.04, ll. 259–262).

### Dimensional vs dimensionless derivatives
With $\tfrac12\rho U_\infty^2 S$ for forces (and an extra $\bar c$ for moments), and states scaled as $u/U_\infty$, $qc/U_\infty$, $\dot wc/U_\infty^2$:

| Derivative | Dimensional form |
|---|---|
| $\mathring Z_u$, $\mathring Z_w$ | $Z_u\cdot\tfrac12\rho U_\infty S$ |
| $\mathring Z_q$ | $Z_q\cdot\tfrac12\rho U_\infty S\bar c$ |
| $\mathring Z_{\dot w}$ | $Z_{\dot w}\cdot\tfrac12\rho S\bar c$ |
| $\mathring M_u$, $\mathring M_w$ | $M_u\cdot\tfrac12\rho U_\infty S\bar c$ |
| $\mathring M_q$ | $M_q\cdot\tfrac12\rho U_\infty S\bar c^2$ |
| $\mathring M_{\dot w}$ | $M_{\dot w}\cdot\tfrac12\rho S\bar c^2$ |

The course keeps both versions for a reason (L1.06, ll. 103–110). Dimensionless derivatives (no ring) are the aerodynamicist's view, useful for comparing across the flight envelope to see which change most with height, speed or configuration. Dimensional derivatives (with ring) are what the equations of motion and the control analysis need. Converting one to the other with this table "might be a question that I ask you maybe in the exam, maybe in the quiz" (ll. 108–109).

> [!example] F-4C Phantom (L1.06 slide 6)
> $\rho=0.3809$, $U_\infty=178$ m/s, $S=49.239$ m², $\bar c = 4.889$ m, so $\tfrac12\rho U_\infty^2S = 297119$ N.
>
> - $\mathring M_w = -0.2169\,(0.5\rho U_\infty S\bar c) = -1770.07$ N s
> - $\mathring M_q = -1.2732\,(0.5\rho U_\infty S\bar c^2) = -50798$ N m s
> - $\mathring M_{\dot w} = -0.591\,(0.5\rho S\bar c^2) = -132.47$ N s²
> - $\mathring Z_w = -3.1245\,(0.5\rho U_\infty S) = -5215.44$ N s/m

**Where each scale factor comes from.** The dimensionless derivative is defined by dividing the force by $\tfrac12\rho U_\infty^2S$ (the moment by $\tfrac12\rho U_\infty^2S\bar c$) and the perturbation by its own reference. For $Z_w$:

$$
\frac{\Delta Z}{\tfrac12\rho U_\infty^2S}=Z_w\,\frac{w}{U_\infty}
$$

Multiply both sides by $\tfrac12\rho U_\infty^2S$:

$$
\Delta Z=Z_w\,\tfrac12\rho U_\infty S\;w
$$

so $\mathring Z_w=Z_w\cdot\tfrac12\rho U_\infty S$, with units $\text{kg/m}^3\cdot\text{m/s}\cdot\text{m}^2=\text{kg/s}=\text{N s/m}$. For a rate derivative the perturbation is $q\bar c/U_\infty$, which brings an extra $\bar c$. For a $\dot w$ derivative it is $\dot w\bar c/U_\infty^2$, which brings a $\bar c$ and removes one $U_\infty$. The table follows from these three patterns, with one more $\bar c$ for every moment.

> [!check] F-4C conversions recomputed (Python)
> $\tfrac12\rho U_\infty S=1669.2$ kg/s, $\tfrac12\rho U_\infty S\bar c=8160.7$ kg m/s, $\tfrac12\rho U_\infty S\bar c^2=39\,898$ kg m²/s and $\tfrac12\rho S\bar c^2=224.15$ kg m. Multiplying by the dimensionless values gives $-5215.4$, $-1770.1$, $-50\,798$ and $-132.47$, matching the slide.

## 4. Estimating the derivatives from physics (L1.10)
Consider a perturbation in which the direction of motion is unchanged ($q = \dot w = 0$), with small angles $\theta = \Delta\alpha = w/U_\infty$ and $\Delta(U^2) \approx 2uU_\infty$.

**Thrust**: model it as $T = c_tU^\Lambda$, so $\Delta T = \Lambda D\,u/U_\infty$ (since $T = D$ in trim).
- Jet engine: $T$ constant, so $\Lambda = 0$.
- Piston/propeller: $TU$ constant, so $\Lambda = -1$.

**Drag and lift**:

$$
\Delta D = \tfrac12\rho U_\infty^2S\left(C_D\frac{2u}{U_\infty}+C_{D_\alpha}\frac{w}{U_\infty}\right),\qquad \Delta L^* = \tfrac12\rho U_\infty^2S\left(C_{L^*}\frac{2u}{U_\infty}+C_{L^*_\alpha}\frac{w}{U_\infty}\right)
$$

Force balance (after minus before), resolved along body $x$ and $z$. The direction of travel is unchanged, so lift and drag stay tied to the wind while the body axes rotate nose-up by $w/U_\infty$. In body axes the lift therefore tilts forward by $w/U_\infty$ and the drag gains a component along $-z$:

![[amc_perturbed_force_tilt.png|760]]
- $\Delta X_a = \Delta T-\Delta D+L^*\,w/U_\infty$
- $\Delta Z_a = -\Delta L^*-D\,w/U_\infty$

Compare with the definitions:

$$
\boxed{X_u = (\Lambda-2)C_D,\quad X_w = C_{L^*}-C_{D_\alpha},\quad Z_u = -2C_{L^*},\quad Z_w = -(C_{L^*_\alpha}+C_D)}
$$

### Full derivation of the force derivatives
The lecture did the thrust step on the board and then skipped the drag, lift and $Z$ steps ("Because I am a little bit behind, I'm going to skip the detailed explanation", L1.10, l. 332; "I'm not going to go through that one", l. 379). Assumptions throughout: level trim with $T = D$ and $L^* = W$, constant $\rho$ and $S$, small perturbations so products of $u$ and $w$ are dropped.

**(a) Speed squared.** Before the perturbation the body-axis velocity is $(U_\infty, 0)$. After it is $(U_\infty+u,\ w)$:

$$
U^2_{\text{after}} = (U_\infty+u)^2+w^2
$$

$$
U^2_{\text{after}} = U_\infty^2+2U_\infty u+u^2+w^2
$$

$$
U^2_{\text{after}} \approx U_\infty^2+2U_\infty u
$$

$$
\Delta(U^2) = U^2_{\text{after}}-U_\infty^2 = 2U_\infty u
$$

(b) Thrust (L1.10, ll. 280–320). Model $T = c_TU^\Lambda$ and differentiate:

$$
\frac{\partial T}{\partial U} = c_T\Lambda U^{\Lambda-1}
$$

$$
\frac{\partial T}{\partial U} = \Lambda\frac{c_TU^\Lambda}{U}
$$

$$
\frac{\partial T}{\partial U} = \Lambda\frac{T}{U}
$$

At trim $T = D$ and $U = U_\infty$, so

$$
\Delta T = \frac{\partial T}{\partial U}u = \Lambda D\frac{u}{U_\infty}
$$

Divide by $\tfrac12\rho U_\infty^2S$:

$$
\frac{\Delta T}{\tfrac12\rho U_\infty^2S} = \Lambda C_D\frac{u}{U_\infty}
$$

**(c) Drag.** $D = \tfrac12\rho U^2SC_D$, and only $U^2$ and $C_D$ change:

$$
\Delta D = \tfrac12\rho S\left[C_D\,\Delta(U^2)+U_\infty^2\,\Delta C_D\right]
$$

$$
\Delta D = \tfrac12\rho S\left[C_D\,2U_\infty u+U_\infty^2\,C_{D_\alpha}\frac{w}{U_\infty}\right]\qquad(\Delta\alpha = w/U_\infty)
$$

$$
\frac{\Delta D}{\tfrac12\rho U_\infty^2S} = 2C_D\frac{u}{U_\infty}+C_{D_\alpha}\frac{w}{U_\infty}
$$

The lift change follows by replacing $D$ with $L^*$: $\Delta L^*/(\tfrac12\rho U_\infty^2S) = 2C_{L^*}u/U_\infty+C_{L^*_\alpha}w/U_\infty$.

**(d) Collect terms in $x$.** Divide $\Delta X_a = \Delta T-\Delta D+L^*w/U_\infty$ by $\tfrac12\rho U_\infty^2S$:

$$
\frac{\Delta X_a}{\tfrac12\rho U_\infty^2S} = \Lambda C_D\frac{u}{U_\infty}-2C_D\frac{u}{U_\infty}-C_{D_\alpha}\frac{w}{U_\infty}+C_{L^*}\frac{w}{U_\infty}
$$

$$
\frac{\Delta X_a}{\tfrac12\rho U_\infty^2S} = (\Lambda-2)C_D\frac{u}{U_\infty}+(C_{L^*}-C_{D_\alpha})\frac{w}{U_\infty}
$$

The definition in dimensionless form is $\Delta X_a/(\tfrac12\rho U_\infty^2S) = X_u\,u/U_\infty+X_w\,w/U_\infty$. Matching coefficients gives $X_u = (\Lambda-2)C_D$ and $X_w = C_{L^*}-C_{D_\alpha}$.

**(e) Collect terms in $z$.** Divide $\Delta Z_a = -\Delta L^*-Dw/U_\infty$ by $\tfrac12\rho U_\infty^2S$:

$$
\frac{\Delta Z_a}{\tfrac12\rho U_\infty^2S} = -2C_{L^*}\frac{u}{U_\infty}-C_{L^*_\alpha}\frac{w}{U_\infty}-C_D\frac{w}{U_\infty}
$$

$$
\frac{\Delta Z_a}{\tfrac12\rho U_\infty^2S} = -2C_{L^*}\frac{u}{U_\infty}-(C_{L^*_\alpha}+C_D)\frac{w}{U_\infty}
$$

Matching coefficients gives $Z_u = -2C_{L^*}$ and $Z_w = -(C_{L^*_\alpha}+C_D)$.

These results make physical sense. $X_u<0$ for both engine types ($\Lambda-2 = -2$ for a jet, $-3$ for a propeller): speeding up raises drag faster than thrust, which is speed stability, and the propeller aircraft is more speed-stable because its thrust falls with speed. $Z_w$ is dominated by $-C_{L^*_\alpha}$, because a nose-up $w$ perturbation creates lift, which acts in $-z$; this is heave damping. The derivatives are evaluated at trim, which is why $T = D$ can be used inside $\partial T/\partial U$ (L1.10, l. 318).

Moment derivatives (linking back to SESA2022 T6 static stability):

$$
M_w = -H_sC_{L^*_\alpha},\qquad M_u = 0\ (\text{low Mach}),\qquad M_q = -KC_{L_{T,\alpha}}\frac{l}{\bar c}
$$

- $H_s$ is the stick-fixed static margin (see [[Neutral Point and Static Margin]]), so pitch stiffness $M_w<0$ requires $H_s>0$.
- $M_q$ comes from the tail angle of attack induced by pitch rate, $\Delta\alpha_T\approx ql/U_\infty$.
- $K = S_Tl/(S\bar c)$ is the tail volume ratio.

Derivation of $M_w$ (slide 16 says "it can be shown"; assumptions: low Mach, linear lift curve, stick fixed). SESA2022 defines the static margin through the slope of the pitching-moment curve:

$$
\frac{dC_M}{dC_{L^*}}=-H_s
$$

A perturbation $w$ changes the angle of attack by $\Delta\alpha=w/U_\infty$, so the lift coefficient changes by

$$
\Delta C_{L^*}=C_{L^*_\alpha}\,\frac{w}{U_\infty}
$$

and the moment coefficient by

$$
\Delta C_M=\frac{dC_M}{dC_{L^*}}\,\Delta C_{L^*}=-H_sC_{L^*_\alpha}\,\frac{w}{U_\infty}
$$

The definition of the dimensionless derivative is $\Delta C_M=M_w\,w/U_\infty$. Matching the coefficients:

$$
M_w=-H_sC_{L^*_\alpha}
$$

Derivation of $M_q$ (assumptions: tail at distance $l$ behind the cg, tail lift slope $a_1=C_{L_{T,\alpha}}$, tail dynamic pressure equal to the free stream, downwash change neglected).

![[amc_pitch_damping_tail.png|900]]

A nose-up pitch rate $q$ moves the tail downwards at speed $ql$. The tail therefore meets air coming up at $ql$, which raises its angle of attack by

$$
\Delta\alpha_T=\frac{ql}{U_\infty}
$$

The extra tail lift is

$$
\Delta L_T=\tfrac12\rho U_\infty^2S_T\,a_1\frac{ql}{U_\infty}
$$

It acts a distance $l$ behind the cg, so it gives a nose-down moment:

$$
\Delta M=-l\,\Delta L_T=-\tfrac12\rho U_\infty^2S_T\,a_1\frac{l^2}{U_\infty}\,q
$$

The dimensionless definition is $\Delta M/(\tfrac12\rho U_\infty^2S\bar c)=M_q\,q\bar c/U_\infty$. Divide the line above by $\tfrac12\rho U_\infty^2S\bar c$:

$$
\frac{\Delta M}{\tfrac12\rho U_\infty^2S\bar c}=-\frac{S_Tl}{S\bar c}\,a_1\,\frac{l}{\bar c}\,\frac{q\bar c}{U_\infty}
$$

so

$$
M_q=-\frac{S_Tl}{S\bar c}\,a_1\,\frac{l}{\bar c}=-K\,C_{L_{T,\alpha}}\,\frac{l}{\bar c}
$$

It is called damping because $\Delta M$ is proportional to $-q$, so it always opposes the rotation, like a dashpot. It grows with $l^2$, one $l$ from the tail's speed and one from its moment arm, which is why a long tail arm damps the short-period mode so well ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid#5. The SPO approximation (L1.06)|A3 §5]]).

### Estimation methods

| Quantity | Methods |
|---|---|
| Mass, CG | CAD/3D model, direct weighing, plumb line, reaction forces on scales ($x_{cg} = \int x\,dW/W$) |
| Moments of inertia | Analytical or CAD; bifilar/trifilar pendulum (period of oscillation gives $I$) |
| Aero derivatives | Back-of-envelope, ESDU / DATCOM, CFD (AVL vortex lattice, XFLR5, RANS), wind tunnel, free flight with an EKF |

The full-cycle UAV example (Mini Skyhunter) compares simulation, wind tunnel and free flight:
- AVL gave $C_{L_\alpha}=5.03$ and the wind tunnel $5.44$ rad⁻¹.
- $C_{L_q}$ ($9.16$ rad⁻¹ in simulation, $7.66$ from free flight) cannot be obtained from static wind-tunnel tests. It needs dynamic or flight data.
- Free-flight data are noisy (gusts, sensor noise, structural vibration), so they were filtered with a 4th-order zero-phase Butterworth filter.

> [!info] Lecturer's practical points on estimation (L1.10)
> - Simulate before you test: "if you just go with blind eyes into experiments, you might expend a lot of time and find nothing" (ll. 421–426). AVL was run over $\alpha\in[-6^\circ,9^\circ]$ because vortex-lattice methods are valid only in the linear lift range (ll. 427–432).
> - Pendulum tests need small angles (otherwise the motion is nonlinear) and low rates (otherwise you also measure aerodynamic damping) (ll. 98–106).
> - The model is mounted upside down so the support struts disturb the lower surface, not the suction side, at the positive angles of attack of interest (ll. 467–475).
> - Free flight is needed because a conventional wind tunnel holds the model fixed, so the rate derivatives ($C_{L_q}$, damping) can't be measured. Pitching quickly delays separation (hysteresis), which a static test can't capture (ll. 476–503).
> - The highest angles of attack were tested only at low speed, because lift grows with $V^2$ and would have broken the model (ll. 449–456).
> - The derivatives found in free flight were fitted with an extended Kalman filter, used as an optimiser that minimises the output error from an initial guess (ll. 505–514).

## 5. Adding control inputs (L1.11)
Extend the homogeneous model with forcing terms: $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u$.

$$
\Delta X = \Delta X_g+\Delta X_a+\Delta X_c,\qquad \Delta X_c = \mathring X_\eta\eta+\mathring X_T\Delta T+\mathring X_u u_g+\mathring X_w w_g
$$

$$
\mathbf B' = \begin{bmatrix}\mathring X_\eta&\mathring X_T&\mathring X_u&\mathring X_w\\\mathring Z_\eta&\mathring Z_T&\mathring Z_u&\mathring Z_w\\\mathring M_\eta&\mathring M_T&\mathring M_u&\mathring M_w\\0&0&0&0\end{bmatrix},\qquad \mathbf u = \begin{bmatrix}\eta\\\Delta T\\u_g\\w_g\end{bmatrix},\qquad \mathbf A = \mathbf M^{-1}\mathbf A',\ \mathbf B = \mathbf M^{-1}\mathbf B'
$$

Gusts enter through the same aerodynamic derivatives as the states.

The last row of $\mathbf B'$ is zero (L1.11, ll. 81–120). The inputs can't change $\theta$ directly, because $\dot\theta = q$ is a kinematic rate, not an acceleration, and forces and moments act only on the acceleration rows $\dot u$, $\dot w$ and $\dot q$; row 1 is the $x$-force, row 2 the $z$-force and row 3 the pitching moment. Expect $\mathring M_\eta$ to dominate the elevator column and $\mathring X_T$ the throttle column, and note that some entries of $\mathbf B'$ in the lab parameter sets are zero (l. 120). $\mathring X_\eta$ is usually negative, since deflecting the elevator either way adds drag; a linear model can't represent that, so be careful with negative deflections (ll. 147–156).

### Elevator derivatives
The tail lift is $C_{L_T} = a_0+a_1\alpha_T+a_2\eta$ and the tail drag is $C_{D_T} = C_{D_{0T}}+k_TC_{L_T}^2$.
- **Axial**: $X_T = -D_T$, so $\mathring X_\eta = -\rho V_0^2S_Tk_TC_{L_T}a_2$, giving $X_\eta = -2\frac{S_T}{S}k_TC_{L_T}a_2$.
- **Normal**: $Z_T = -L_T$ gives $Z_\eta = -\frac{S_T}{S}a_2$ (PS2 Q2).
- **Moment**: $M_\eta = -\frac{S_Tl_T}{S\bar c}a_2 = -\bar V_Ta_2$, where $\bar V_T$ is the tail volume ratio.

A trailing-edge-down elevator ($\eta>0$) gives more tail lift, so $Z_\eta<0$ (lift is $-z$), and a nose-down moment, so $M_\eta<0$.

The three elevator derivatives line by line (slide 6 does the axial one and says "similar procedure for remaining derivatives"; assumptions: tail at trim speed $V_0$, small perturbation so the tail force is resolved along the body axes without tilt, $\eta$ in radians; dimensionless elevator derivatives are divided by $\tfrac12\rho V_0^2S$ because $\eta$ is already dimensionless).

*Axial.* The tail drag is $D_T=\tfrac12\rho V_0^2S_TC_{D_T}$ and $X_T=-D_T$. Only $C_{D_T}$ depends on $\eta$:

$$
\frac{\partial C_{D_T}}{\partial\eta}=2k_TC_{L_T}\frac{\partial C_{L_T}}{\partial\eta}=2k_TC_{L_T}a_2
$$

$$
\mathring X_\eta=-\tfrac12\rho V_0^2S_T\cdot2k_TC_{L_T}a_2=-\rho V_0^2S_Tk_TC_{L_T}a_2
$$

$$
X_\eta=\frac{\mathring X_\eta}{\tfrac12\rho V_0^2S}=-2\frac{S_T}{S}k_TC_{L_T}a_2
$$

*Normal.* $Z_T=-L_T=-\tfrac12\rho V_0^2S_TC_{L_T}$, and $\partial C_{L_T}/\partial\eta=a_2$:

$$
\mathring Z_\eta=-\tfrac12\rho V_0^2S_Ta_2,\qquad Z_\eta=\frac{\mathring Z_\eta}{\tfrac12\rho V_0^2S}=-\frac{S_T}{S}a_2
$$

*Pitching moment.* The tail lift acts $l_T$ behind the cg, so $M_T=-l_TL_T$:

$$
\mathring M_\eta=-l_T\,\tfrac12\rho V_0^2S_Ta_2,\qquad M_\eta=\frac{\mathring M_\eta}{\tfrac12\rho V_0^2S\bar c}=-\frac{S_Tl_T}{S\bar c}a_2=-\bar V_Ta_2
$$

> [!check] Sign and size check
> For $S_T/S=0.2$, $l_T/\bar c=3$ ($\bar V_T=0.6$) and $a_2=2$ rad⁻¹: $Z_\eta=-0.40$ and $M_\eta=-1.20$. The moment derivative is three times the force derivative because the tail arm is three chords. That is why $\mathring M_\eta$ dominates the elevator column of $\mathbf B'$ (L1.11, ll. 81–120). $X_\eta$ has the sign of $C_{L_T}$: with a down-loaded tail ($C_{L_T}<0$), $X_\eta>0$ for small $\eta$ (less tail drag as the download falls), which shows how a linear model hides that any large deflection adds drag.

## 6. From state space to transfer function
Add an output equation: $\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u$, $\mathbf y = \mathbf C\mathbf x+\mathbf D\mathbf u$. Take the Laplace transform with zero initial conditions:

$$
(s\mathbf I-\mathbf A)\mathbf X(s) = \mathbf B\mathbf U(s)\;\Rightarrow\;\mathbf Y(s) = [\mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D]\mathbf U(s)
$$

$$
\boxed{G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D = \frac{\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\mathbf B+\mathbf D|s\mathbf I-\mathbf A|}{|s\mathbf I-\mathbf A|}}
$$

- The denominator $|s\mathbf I-\mathbf A|$ is the characteristic polynomial.
- **SISO case**: one input ($\eta$) and one output (e.g. $\mathbf C = [0,0,1,0]$ for $q$). Set $\mathbf D = 0$ because sensors are not directly affected by the inputs.
- Longitudinal elevator transfer functions (Cook's "concise" derivatives):

$$
\frac{q(s)}{\eta(s)} = \frac{k_qs(s+1/T_{\theta_1})(s+1/T_{\theta_2})}{(s^2+2\zeta_p\omega_ps+\omega_p^2)(s^2+2\zeta_s\omega_ss+\omega_s^2)},\qquad \frac{\theta(s)}{\eta(s)} = \frac{1}{s}\frac{q(s)}{\eta(s)}
$$

  The quartic denominator factors into the phugoid ($p$) and short-period ($s$) modes. The full form is used for controller validation. The SPO approximation (see [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]) is used for design.

> [!info] Exam scope and intuition for this section (L1.11)
> - The MIMO transfer-function derivation "is not going to be part of the exam. So relax" (ll. 269–272). "I'm not going to be asking you to derive them yourselves" (l. 499) for the $q/\eta$ and $\theta/\eta$ functions.
> - **$\mathbf C$ is where sensors enter.** It says which states can be measured, which leads to observability in Year 3 (ll. 285–295). Typical sensors: pitot tube for $u$, gyro for $q$, IMU-derived $\theta$ (ll. 424–427).
> - When would $\mathbf D\ne0$? If a sensor were mounted on a control surface, for example an accelerometer on the elevator (ll. 303–308).
> - Spot the difference between $q/\eta$ and $\theta/\eta$: $\theta$ is the integral of $q$, so $\theta/\eta$ has one factor $s$ fewer, i.e. two zeros instead of three (ll. 474–493).
> - Why SISO only? Changing height can be done with elevator or throttle, and they interact. A two-input design is "a little bit too complicated for a year two module" (ll. 384–401).

### Worked example: SPO state space to transfer function (PS2 Q3)

States $(w,q)$, input $\eta$, output $q$:

$$
\mathbf A = \begin{bmatrix}-0.2956&178\\-0.1045&-0.4490\end{bmatrix},\qquad \mathbf B = \begin{bmatrix}-6.300\\-4.888\end{bmatrix},\qquad \mathbf C = [0\ \ 1],\qquad \mathbf D=0
$$

Form $s\mathbf I-\mathbf A$:

$$
s\mathbf I-\mathbf A=\begin{bmatrix}s+0.2956&-178\\0.1045&s+0.4490\end{bmatrix}
$$

Its determinant is the characteristic polynomial:

$$
|s\mathbf I-\mathbf A|=(s+0.2956)(s+0.4490)+178\times0.1045
$$

$$
|s\mathbf I-\mathbf A|=s^2+0.7446s+0.1327+18.601=s^2+0.7446s+18.734
$$

For a $2\times2$ matrix the adjoint swaps the diagonal and negates the off-diagonal:

$$
\mathrm{adj}(s\mathbf I-\mathbf A)=\begin{bmatrix}s+0.4490&178\\-0.1045&s+0.2956\end{bmatrix}
$$

$\mathbf C=[0\ 1]$ picks the second row:

$$
\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\,\mathbf B=-0.1045\times(-6.300)+(s+0.2956)(-4.888)
$$

$$
\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\,\mathbf B=0.6584-4.888s-1.4449=-4.888s-0.7865
$$

So

$$
G(s)=\frac{q(s)}{\eta(s)}=\frac{-4.888(s+0.1609)}{s^2+0.7446s+18.73}
$$

> [!check] Numerical check (Python, `scipy.signal.ss2tf`)
> Numerator $[-4.888,\ -0.7865]$, denominator $[1,\ 0.7446,\ 18.734]$. ✓ The poles are $-0.372\pm4.312i$: $\omega_n=4.33$ rad/s and $\zeta=0.086$, a lightly damped short-period mode. The negative gain is the sign convention: trailing-edge-down elevator pitches the nose down. Also in [[SESA2027 Practice Problems 2 Solutions]].

> [!warning] Possible slip on the sheet: the $(2,1)$ entry
> The diagonal entries are exactly the F-4C SPO values: $\mathring Z_w/m=-5215.44/17\,642=-0.2956$ and $(\mathring M_q+U_\infty\mathring M_{\dot w})/I_{yy}=-0.4490$, with $U_\infty=178$ m/s. For the F-4C the $(2,1)$ entry is $(\mathring M_w+\mathring M_{\dot w}\mathring Z_w/m)/I_{yy}=(-1770.07+39.16)/165\,669=-1.045\times10^{-2}$. The sheet prints $-1.045\times10^{-1}$, ten times larger. With the F-4C value the denominator would be $s^2+0.7446s+1.992$ ($\omega_n=1.41$ rad/s, $\zeta=0.264$, the [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid#5. The SPO approximation (L1.06)|A3]] result). Answer the sheet as printed, but expect the exponent to be a typo.

## Lecturer emphasis and exam hints (transcripts)

> [!info] Exam signals
> - **Stated exam question type**: given the full Taylor expansion, name the derivatives that can be neglected: $\mathring X_q$, $\mathring X_{\dot w}$ and $\mathring M_u$ (L1.04, ll. 166–169). See [[#2. Aerodynamic contributions]].
> - **Not examined**: the MIMO transfer-function derivation (L1.11, l. 269) and deriving $q/\eta$, $\theta/\eta$ by hand (L1.11, l. 499).
> - The F-4C data come from a 1970s NASA report in dimensionless form, so you must be able to convert to dimensional derivatives with the table in [[#Dimensional vs dimensionless derivatives]] (L1.04, ll. 269–291). The conversion was flagged again as a possible exam or quiz question (L1.06, ll. 108–109).
> - **Admin**: the computer-lab parameter sets e-mailed to each group already contain the $\mathbf B'$ entries for the second lab session (L1.11, ll. 69–76).

> [!info] Lecturer intuition
> - The lateral equations can be treated in exactly the same way; they are skipped only because it would be repetitive (L1.04, ll. 18–24).
> - $M_q$ (pitch damping) comes mostly from the tail. In a pull-up the tail sees an extra angle of attack $ql/U_\infty$ that the wing does not (L1.10, ll. 392–406).
> - Combining simulation, wind-tunnel and free-flight data "improve[s] the accuracy significantly", and second-year projects, IPs and GDPs are the chance to do it (L1.10, ll. 529–537).

## Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L1.04, l. 50 | "flight part angle", "setting at three point" | flight-path angle $\gamma_0$ at the trim point |
> | L1.04, l. 72 | "the closer we're flying to the air center" | the Earth's centre |
> | L1.04, l. 91 | "delta cg" | $\Delta Z_g$ |
> | L1.04, l. 122 | "z circle w u" | $\mathring Z_w w$ |
> | L1.04, l. 150 | "string-wise velocity perturbation" | streamwise |
> | L1.04, ll. 226–228 | "mu dot" | $m\dot u$ |
> | L1.04, l. 234 | "ii multiplying q dot" | $I_{yy}\dot q$ |
> | L1.04, ll. 286–289 | "ZetaQ", "raw U-infinity SC" | $\mathring Z_q$, $\rho U_\infty S\bar c$ |
> | L1.10, l. 22 | "truss derivatives" | thrust derivatives |
> | L1.10, l. 62 | "the planar method" | plumb-line method (l. 64) |
> | L1.10, ll. 130–133 | "digital.com", ".com" | Digital DATCOM |
> | L1.10, ll. 138–150 | "ABL", "ABL wrapper" | AVL (Athena Vortex Lattice) |
> | L1.10, l. 159 | "Navier Stock's" | Navier–Stokes |
> | L1.10, l. 189 | "UABs" | UAVs |
> | L1.10, l. 227 | "strength-free velocity" | free-stream velocity |
> | L1.10, l. 281 | "a city that represents a throttle constant" | $c_T$, the throttle constant |
> | L1.10, l. 301 | "loss of power" | laws of indices |
> | L1.10, l. 355 | the $L^*w/U_\infty$ term "is basically the induced drag that we have from that change, that increase in lift" | it is the forward component of the trim lift once the body axes have rotated by $w/U_\infty$ relative to the flight path; it is a geometric tilt of $L^*$, not induced drag (which is already inside $C_{D_\alpha}$) |
> | L1.10, l. 389 | "logmark numbers" | low Mach numbers |
> | L1.10, l. 402 | "the canary" | the canard |
> | L1.10, l. 404 | "K minus K CLT … L over C" | $M_q = -KC_{L_{T,\alpha}}\,l/\bar c$ |
> | L1.10, l. 430 | "15 minutes per second" | 15 m/s |
> | L1.10, ll. 450–451 | 21° reached "at the high speed" | at the low-speed test; high $\alpha$ was avoided at high speed (ll. 451–456) |
> | L1.10, l. 454 | "lift doesn't square linearly" | lift doesn't scale linearly; it grows with $V^2$ |
> | L1.10, l. 508 | "extended kernel filter" | extended Kalman filter |
> | L1.11, l. 45 | "V prime" | $\mathbf B'$ |
> | L1.11, ll. 138, 262 | "ghosts" | gusts |
> | L1.11, ll. 177–189 | "type plane", "angle of a tag", "kernel" | tailplane, angle of attack, canard |
> | L1.11, l. 194 | "parasite drive" | parasite drag |
> | L1.11, l. 205 | "rho, b squared, and st" | $\rho$, $V_0^2$, $S_T$ |
> | L1.11, ll. 251–253 | "dynamic center", "the core of the main wing" | aerodynamic centre, chord $\bar c$ |
> | L1.11, l. 274 | "H dot equals to AX" | $\dot{\mathbf x} = \mathbf A\mathbf x$ |
> | L1.11, l. 364 | two inputs "the throttle, and … the pitch angle" | throttle and elevator (l. 369) |
> | L1.11, l. 417 | "gust on the y-axis" | gust along $z$ ($w_g$) |
> | L1.11, l. 424 | "we could normally have three inputs" | three outputs (sensors) |
> | L1.11, ll. 437–438 | "a joint matrix", "the determinant is not the thing that the characteristic polynomial" | adjoint matrix; the determinant is the characteristic polynomial |
> | L1.11, l. 454 | "not affected by the control outputs" | control inputs |
> | L1.11, l. 480 | "k subscript k" | $k_q$ |
> | L1.11, l. 482 | "multiplied by x" | multiplied by $s$ |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| aerodynamic derivatives ($\mathring X_u$, $\mathring M_q$, …) | stability derivatives, aerodynamic coefficients, $X_u$ etc. in some texts without the ring | L1.04 slides; L1.10 | the ring marks dimensional; no ring is dimensionless (Cook's convention) |
| concise derivatives ($x_u$, $m_q$, …) | normalised derivatives, entries of $\mathbf A=\mathbf M^{-1}\mathbf A'$ | L1.11 slides 12–13 | |
| control derivatives ($\mathring X_\eta$, $\mathring M_\eta$, $\mathring X_T$) | control-input derivatives, elevator effectiveness ($M_\eta$) | L1.11 slides 4–6 | |
| $M_w$ (pitch stiffness) | $C_{M_\alpha}$, static stability derivative | L1.10 slide 16 | $M_w=C_{M_\alpha}$ for $\alpha\approx w/U_\infty$ |
| $M_q$ (pitch damping derivative) | $C_{M_q}$, pitch-damping coefficient | L1.10 slide 16 | |
| $\mathring Z_{\dot w}$, $\mathring M_{\dot w}$ | $\dot\alpha$ derivatives, downwash-lag derivatives, $C_{M_{\dot\alpha}}$ | L1.04 | |
| stick-fixed static margin $H_s$ | $K_n$, static margin, $h_n-h$ | L1.10 slide 16, SESA2022 T6 | |
| tail volume ratio $K$, $\bar V_T$ | tail volume coefficient $V_H$ | L1.10, L1.11 | |
| state equation $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$ | state-space model, plant model | L1.04, L1.11 | |
| $\mathbf A$ (state), $\mathbf B$ (input), $\mathbf C$ (output), $\mathbf D$ (direct) matrices | system, control, observation, feedthrough matrices | L1.11 slides 7–9 | |
| input vector $\mathbf u=[\eta,\Delta T,u_g,w_g]^T$ | control and gust vector | L1.11 slide 3 | do not confuse with the speed perturbation $u$ |
| characteristic polynomial $\lvert s\mathbf I-\mathbf A\rvert$ | characteristic equation (when set to 0), stability quartic | L1.11 slide 10 | |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · Next: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]
- Concepts: [[Aerodynamic Stability Derivatives]] · [[State-Space Representation]] · [[Transfer Function]] · [[Neutral Point and Static Margin]]
- Static stability link: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Maths: matrix inverse and adjoint, Laplace transforms (MATH2048)

## Sources
- Lectures 1.04, 1.10, 1.11 (Dr S. Araujo-Estrada): slides `Lecture 1.04.pdf`, `Lecture 1.10.pdf`, `Lecture 1.11.pdf`
- Transcripts (speech-to-text): `Lecture 1.04 recording.txt`, `Lecture 1.10 recording.txt`, `Lecture 1.11 recording.txt`
- Cook (2013) *Flight Dynamics Principles*, Ch. 4–5 and 13.4
- Figures: `01 - Notes/Figures/generate_amc_a2_figures.py`

## Self-study tasks

No tasks were set in L1.04, L1.10 or L1.11. The parameter sets e-mailed to each group were for the computer lab (L1.11, ll. 69–76), and Cook §13.4 was recommended for the remaining elevator derivatives (L1.11 slide 6). Every task below is suggested, not lecturer-set, except that the "which derivatives are negligible" question was named as a possible exam question (L1.04, ll. 166–169).

### Core

- [ ] Given the full Taylor expansion, name the negligible derivatives and say why (stated exam question type). → [[#2. Aerodynamic contributions]]
- [ ] Convert the F-4C $Z_w$, $M_w$, $M_q$, $M_{\dot w}$ to dimensional form, with units. → [[#Dimensional vs dimensionless derivatives]]
- [ ] Derive rows 2 and 3 of $\mathbf M$ and $\mathbf A'$ from the $Z$ and $M$ equations. → [[#3. The longitudinal state equation]]
- [ ] Find $G(s)$ for the PS2 Q3 system by hand, then its poles. → [[#Worked example: SPO state space to transfer function (PS2 Q3)]]
- [ ] Explain why the last row of $\mathbf B'$ is zero. → [[#5. Adding control inputs (L1.11)]]
- [ ] PS2 Q2 and Q3 (elevator derivatives, state space to $G(s)$). → [[SESA2027 Practice Problems 2 Solutions]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q2. Gravity and derivatives in the longitudinal model|Mock Q2]]

### Further practice

- [ ] For a climbing trim ($\gamma_0 = 5^\circ$), write $\Delta X_g$ and $\Delta Z_g$ and say which is larger. → [[#1. Gravitational contributions (L1.04)]]
- [ ] Derive $X_u$, $X_w$, $Z_u$, $Z_w$ for a propeller aircraft. → [[#Full derivation of the force derivatives]]
- [ ] Derive $M_w=-H_sC_{L^*_\alpha}$ and $M_q=-KC_{L_{T,\alpha}}l/\bar c$. → [[#4. Estimating the derivatives from physics (L1.10)]]
- [ ] Derive $X_\eta$, $Z_\eta$ and $M_\eta$ from the tailplane lift and drag (Cook §13.4). → [[#Elevator derivatives]]
