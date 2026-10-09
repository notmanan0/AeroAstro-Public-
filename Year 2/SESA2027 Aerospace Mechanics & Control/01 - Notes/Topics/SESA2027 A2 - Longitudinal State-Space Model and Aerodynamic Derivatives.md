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
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]"]
next_topics: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
key_concepts: ["[[Aerodynamic Stability Derivatives]]", "[[State-Space Representation]]", "[[Transfer Function]]"]
tutorial_sheets: ["[[SESA2027 Practice Problems 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture 1.04.pdf", "02 - Sources/Lectures/Lecture 1.10.pdf", "02 - Sources/Lectures/Lecture 1.11.pdf"]
---

# SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives

> [!abstract] Summary
> The out-of-balance forces are **gravitational** plus **aerodynamic**. The aerodynamic part is modelled as a first-order Taylor expansion in the perturbations, whose coefficients are the **aerodynamic derivatives** ($\mathring X_u$, $\mathring Z_w$, $\mathring M_q$, ...). This gives the linear state equation $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x + \mathbf B'\mathbf u$, i.e. $\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u$, with $\mathbf x = [u,\,w,\,q,\,\theta]^T$. Adding an output $y = \mathbf C\mathbf x+\mathbf D\mathbf u$ gives the transfer function $G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D$. The derivatives are estimated analytically, by CFD, in wind tunnels and in free flight.

## Key Concepts
- [[Aerodynamic Stability Derivatives]]
- [[State-Space Representation]]
- [[Transfer Function]]

---

## 1. Gravitational contributions (L1.04)
In trim with climb angle $\gamma_0$: $X_{g0} = -mg\sin\gamma_0$ and $Z_{g0} = mg\cos\gamma_0$. After a small pitch perturbation $\theta$ (so $\sin\theta\approx\theta$, $\cos\theta\approx1$):

$$
X_g = -mg\sin(\gamma_0+\theta) \approx X_{g0} - mg\theta\cos\gamma_0\;\Rightarrow\;\Delta X_g = -mg\theta\cos\gamma_0,\qquad \Delta Z_g = -mg\theta\sin\gamma_0
$$

## 2. Aerodynamic contributions
**DAP1**: keep only the first-order Taylor terms. A ring (°) denotes a **dimensional** derivative.

$$
\Delta X_a = \mathring X_u u+\mathring X_w w,\qquad \Delta Z_a = \mathring Z_u u+\mathring Z_w w+\mathring Z_q q+\mathring Z_{\dot w}\dot w,\qquad \Delta M_a = \mathring M_u u+\mathring M_w w+\mathring M_q q+\mathring M_{\dot w}\dot w
$$

- $u$: velocity perturbation.
- $w$: normal velocity perturbation, i.e. angle of attack, since $\alpha\approx w/U_\infty$.
- $q$: pitch rate. $\dot w$: rate of change of $\alpha$ (downwash lag at the tail, which turns out to be important).
- Neglected as small: $\mathring X_q$ and $\mathring X_{\dot w}$. At low speed also $\mathring M_u = 0$.

## 3. The longitudinal state equation
Combine $\Delta X = m\dot u$, $\Delta Z = m(\dot w-qU_\infty)$, $\Delta M = I_{yy}\dot q$ with $\dot\theta = q$ and rearrange:

$$
\underbrace{\begin{bmatrix}m&0&0&0\\0&m-\mathring Z_{\dot w}&0&0\\0&-\mathring M_{\dot w}&I_{yy}&0\\0&0&0&1\end{bmatrix}}_{\mathbf M}\begin{bmatrix}\dot u\\\dot w\\\dot q\\\dot\theta\end{bmatrix} = \underbrace{\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\cos\gamma_0\\\mathring Z_u&\mathring Z_w&\mathring Z_q+mU_\infty&-mg\sin\gamma_0\\\mathring M_u&\mathring M_w&\mathring M_q&0\\0&0&1&0\end{bmatrix}}_{\mathbf A'}\begin{bmatrix}u\\w\\q\\\theta\end{bmatrix}
$$

$$
\boxed{\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x\quad\Longrightarrow\quad\dot{\mathbf x} = \mathbf A\mathbf x,\qquad \mathbf A = \mathbf M^{-1}\mathbf A'}
$$

The model contains the climb angle, speed, mass, inertia and aerodynamic derivatives.

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

> [!example] F-4C Phantom (L1.06 slide 6)
> $\rho=0.3809$, $U_\infty=178$ m/s, $S=49.239$ m², $\bar c = 4.889$ m, so $\tfrac12\rho U_\infty^2S = 297119$ N.
>
> - $\mathring M_w = -0.2169\,(0.5\rho U_\infty S\bar c) = -1770.07$ N s
> - $\mathring M_q = -1.2732\,(0.5\rho U_\infty S\bar c^2) = -50798$ N m s
> - $\mathring M_{\dot w} = -0.591\,(0.5\rho S\bar c^2) = -132.47$ N s²
> - $\mathring Z_w = -3.1245\,(0.5\rho U_\infty S) = -5215.44$ N s/m

## 4. Estimating the derivatives from physics (L1.10)
Consider a perturbation in which the direction of motion is unchanged ($q = \dot w = 0$), with small angles $\theta = \Delta\alpha = w/U_\infty$ and $\Delta(U^2) \approx 2uU_\infty$.

**Thrust**: model it as $T = c_tU^\Lambda$, so $\Delta T = \Lambda D\,u/U_\infty$ (since $T = D$ in trim).
- Jet engine: $T$ constant, so $\Lambda = 0$.
- Piston/propeller: $TU$ constant, so $\Lambda = -1$.

**Drag and lift**:

$$
\Delta D = \tfrac12\rho U_\infty^2S\left(C_D\frac{2u}{U_\infty}+C_{D_\alpha}\frac{w}{U_\infty}\right),\qquad \Delta L^* = \tfrac12\rho U_\infty^2S\left(C_{L^*}\frac{2u}{U_\infty}+C_{L^*_\alpha}\frac{w}{U_\infty}\right)
$$

**Force balance** (after minus before), resolved along body $x$ and $z$. The lift tilts forward by $w/U_\infty$ and the drag tilts down:
- $\Delta X_a = \Delta T-\Delta D+L^*\,w/U_\infty$
- $\Delta Z_a = -\Delta L^*-D\,w/U_\infty$

Compare with the definitions:

$$
\boxed{X_u = (\Lambda-2)C_D,\quad X_w = C_{L^*}-C_{D_\alpha},\quad Z_u = -2C_{L^*},\quad Z_w = -(C_{L^*_\alpha}+C_D)}
$$

**Moment derivatives** (linking back to SESA2022 T6 static stability):

$$
M_w = -H_sC_{L^*_\alpha},\qquad M_u = 0\ (\text{low Mach}),\qquad M_q = -KC_{L_{T,\alpha}}\frac{l}{\bar c}
$$

- $H_s$ is the stick-fixed static margin (see [[Neutral Point and Static Margin]]), so **pitch stiffness $M_w<0$ requires $H_s>0$**.
- $M_q$ comes from the tail angle of attack induced by pitch rate, $\Delta\alpha_T\approx ql/U_\infty$.
- $K = S_Tl/(S\bar c)$ is the tail volume ratio.

### Estimation methods

| Quantity | Methods |
|---|---|
| Mass, CG | CAD/3D model, direct weighing, plumb line, reaction forces on scales ($x_{cg} = \int x\,dW/W$) |
| Moments of inertia | Analytical or CAD; **bifilar/trifilar pendulum** (period of oscillation gives $I$) |
| Aero derivatives | Back-of-envelope, ESDU / DATCOM, CFD (AVL vortex lattice, XFLR5, RANS), wind tunnel, **free flight** with an EKF |

The full-cycle UAV example (Mini Skyhunter) compares simulation, wind tunnel and free flight:
- AVL gave $C_{L_\alpha}=5.03$ and the wind tunnel $5.44$ rad⁻¹.
- $C_{L_q}$ ($9.16$ rad⁻¹ in simulation, $7.66$ from free flight) **cannot be obtained from static wind-tunnel tests**. It needs dynamic or flight data.
- Free-flight data are noisy (gusts, sensor noise, structural vibration), so they were filtered with a 4th-order zero-phase Butterworth filter.

## 5. Adding control inputs (L1.11)
Extend the homogeneous model with forcing terms: $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u$.

$$
\Delta X = \Delta X_g+\Delta X_a+\Delta X_c,\qquad \Delta X_c = \mathring X_\eta\eta+\mathring X_T\Delta T+\mathring X_u u_g+\mathring X_w w_g
$$

$$
\mathbf B' = \begin{bmatrix}\mathring X_\eta&\mathring X_T&\mathring X_u&\mathring X_w\\\mathring Z_\eta&\mathring Z_T&\mathring Z_u&\mathring Z_w\\\mathring M_\eta&\mathring M_T&\mathring M_u&\mathring M_w\\0&0&0&0\end{bmatrix},\qquad \mathbf u = \begin{bmatrix}\eta\\\Delta T\\u_g\\w_g\end{bmatrix},\qquad \mathbf A = \mathbf M^{-1}\mathbf A',\ \mathbf B = \mathbf M^{-1}\mathbf B'
$$

Gusts enter through the same aerodynamic derivatives as the states.

### Elevator derivatives
The tail lift is $C_{L_T} = a_0+a_1\alpha_T+a_2\eta$ and the tail drag is $C_{D_T} = C_{D_{0T}}+k_TC_{L_T}^2$.
- **Axial**: $X_T = -D_T$, so $\mathring X_\eta = -\rho V_0^2S_Tk_TC_{L_T}a_2$, giving $X_\eta = -2\frac{S_T}{S}k_TC_{L_T}a_2$.
- **Normal**: $Z_T = -L_T$ gives $Z_\eta = -\frac{S_T}{S}a_2$ (PS2 Q2).
- **Moment**: $M_\eta = -\frac{S_Tl_T}{S\bar c}a_2 = -\bar V_Ta_2$, where $\bar V_T$ is the tail volume ratio.

A trailing-edge-down elevator ($\eta>0$) gives more tail lift, so $Z_\eta<0$ (lift is $-z$), and a **nose-down** moment, so $M_\eta<0$.

## 6. From state space to transfer function
Add an output equation: $\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u$, $\mathbf y = \mathbf C\mathbf x+\mathbf D\mathbf u$. Take the Laplace transform with zero initial conditions:

$$
(s\mathbf I-\mathbf A)\mathbf X(s) = \mathbf B\mathbf U(s)\;\Rightarrow\;\mathbf Y(s) = [\mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D]\mathbf U(s)
$$

$$
\boxed{G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D = \frac{\mathbf C\,\mathrm{adj}(s\mathbf I-\mathbf A)\mathbf B+\mathbf D|s\mathbf I-\mathbf A|}{|s\mathbf I-\mathbf A|}}
$$

- The denominator $|s\mathbf I-\mathbf A|$ is the **characteristic polynomial**.
- **SISO case**: one input ($\eta$) and one output (e.g. $\mathbf C = [0,0,1,0]$ for $q$). Set $\mathbf D = 0$ because sensors are not directly affected by the inputs.
- Longitudinal elevator transfer functions (Cook's "concise" derivatives):

$$
\frac{q(s)}{\eta(s)} = \frac{k_qs(s+1/T_{\theta_1})(s+1/T_{\theta_2})}{(s^2+2\zeta_p\omega_ps+\omega_p^2)(s^2+2\zeta_s\omega_ss+\omega_s^2)},\qquad \frac{\theta(s)}{\eta(s)} = \frac{1}{s}\frac{q(s)}{\eta(s)}
$$

  The quartic denominator factors into the **phugoid** ($p$) and **short-period** ($s$) modes. The full form is used for controller validation. The SPO approximation (see [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]) is used for design.

> [!example] PS2 Q3: SPO state space to $G(s)$
> For $\mathbf A = \begin{bmatrix}-0.2956&178\\-0.1045&-0.4490\end{bmatrix}$, $\mathbf B = \begin{bmatrix}-6.300\\-4.888\end{bmatrix}$, $\mathbf C = [0\ 1]$:
>
> $$G(s) = \frac{-4.888(s+0.1609)}{s^2+0.7446s+18.73}$$
>
> Worked in [[SESA2027 Practice Problems 2 Solutions]].

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Previous: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · Next: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]
- Static stability link: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Maths: matrix inverse and adjoint, Laplace transforms (MATH2048)

## Sources
- Lectures 1.04, 1.10, 1.11; Cook (2013) *Flight Dynamics Principles*, Ch. 4–5 and 13.4
