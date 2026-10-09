---
title: "SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion"
module: "SESA2027 Aerospace Mechanics & Control"
type: topic
stream: "Part A: Dynamic Systems"
order: 1
tags:
  - sesa2027
  - dynamic-systems
  - equations-of-motion
aliases: ["Aircraft Equations of Motion", "Dynamic Systems"]
date: 2026-09-23
status: complete
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: []
next_topics: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
key_concepts: ["[[Design and Analysis Principles]]", "[[Euler Angles and Rotation Matrices]]", "[[Small Perturbation Linearisation]]", "[[State-Space Representation]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Lecture 1.01.pdf", "02 - Sources/Lectures/Lecture 1.02.pdf", "02 - Sources/Lectures/Lecture 1.03.pdf"]
---

# SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion

> [!abstract] Summary
> A **dynamic system** has a state that evolves according to $\dot{\mathbf x} = f(\mathbf x,\mathbf u)$. For a rigid aircraft we apply Newton's laws in six degrees of freedom, written in the **body frame**:
>
> $$\mathbf F_B = m(\dot{\mathbf v}_B + \boldsymbol\omega_B\times\mathbf v_B),\qquad \mathbf M_B = \dot{\mathbf h}_B + \boldsymbol\omega_B\times\mathbf h_B,\quad \mathbf h_B = \mathbf I_B\boldsymbol\omega_B$$
>
> Symmetry ($I_{xy}=I_{yz}=0$) and **small-perturbation linearisation** about trim **decouple** these into longitudinal equations (in $u,w,q$) and lateral equations (in $v,p,r$).

## Key Concepts
- [[Design and Analysis Principles]] (DAP1–3)
- [[Euler Angles and Rotation Matrices]]
- [[Small Perturbation Linearisation]]
- [[State-Space Representation]]

---

## 1. Dynamic systems (L1.01)

**Definition**: a dynamic system is "a system whose state changes over time according to specific rules or equations, and whose output is a function of both its current input and its history".

- **State**: the set of variables needed to describe the system at any instant (for example position and velocity).
- **Model**: $\dot{\mathbf x}(t) = f(\mathbf x(t),\mathbf u(t))$, where $\mathbf u$ is the external input.
- **Components**:
  - Plant
  - **Sensors**: sun sensor, star tracker, gyroscope, airspeed sensor, AoA vane, IMU
  - **Actuators**: servomotor, thruster, reaction wheel, magnetic torquer, control surfaces, throttle
  - **Controllers**: FCU, FCC, SAS, MCAS

| Classification | Example | Notes |
|---|---|---|
| **Nonlinear** | $y''+y'^2+\sin(by)=0$ | General, hard to analyse |
| **Linear** | $y''+cy'+dy=0$, or $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$ | Superposition holds; the ODE toolbox applies |
| **Time-varying** | Rapid mass or configuration changes (rockets) | Coefficients depend on $t$ |
| **Time-invariant (LTI)** | Slowly changing mass, fixed geometry (aircraft over short intervals) | Constant coefficients |

**Analysis toolkit**:
- **Behaviour** (intrinsic): characteristic polynomial, eigenvalues, stability, $\zeta$, $\omega_n$, poles and zeros.
- **Response** (to an input): rise time, overshoot, settling time, transfer function, Bode plot (cut-off, bandwidth, peaking).
- **Simulation**: virtual prototyping, "what-if" studies, verification, and trade-off studies.

### Design and analysis principles (DAP)
1. **DAP1**: "All models are wrong, but some models are useful" (Box).
2. **DAP2**: Occam's razor. Start with the simplest explanation or model.
3. **DAP3**: Divide and conquer. Recursively split the problem into simpler parts.

Model accuracy rises with complexity, but with diminishing returns. Choose the simplest model that captures the behaviour you care about. See [[Design and Analysis Principles]].

## 2. Setting up the 6-DoF model (L1.02)

**Assumptions**, each checked against an Airbus A380 "reality check" in L1.02 slide 3:

| Assumption | Reality check (A380) |
|---|---|
| Rigid aircraft (no aeroelasticity) | Wing-tip deflection $\approx\pm4$ m on a 79.8 m span, $\delta/b\approx5\%$ |
| Constant mass over short intervals | A 10 s flight burns $\approx25$ kg, which is $0.004\%$ of MTOW |
| Flat Earth, constant $g$ and density | 10 s at 252 m/s covers 2.5 km; curvature drop is 0.315 m ($0.0126\%$) |
| Sensor and controller dynamics neglected | Studied separately in Part C |

**Steps**:
1. Write six equations (Newton's laws): three translational and three rotational.
2. Relate the body frame to the inertial (Earth) frame using Tait–Bryan angles.
3. Express the rates of change as seen from the rotating body frame.
4. Define the inertia tensor.

### Body axes and notation (right-handed; $x$ forward, $y$ starboard, $z$ down)

| | $x$ (roll) | $y$ (pitch) | $z$ (yaw) |
|---|---|---|---|
| Force | $X$ | $Y$ | $Z$ |
| Moment | $L$ | $M$ | $N$ |
| Velocity of CG | $U$ | $V$ | $W$ |
| Angular rate | $p$ | $q$ | $r$ |
| Attitude angle | $\phi$ | $\theta$ | $\psi$ |
| Moment of inertia | $I_{xx}$ | $I_{yy}$ | $I_{zz}$ |

### Euler angles and rotation matrices
The Earth-to-body sequence is **yaw $\psi$, then pitch $\theta$, then roll $\phi$**:

$$
\mathbf v_B = \mathbf R_{BE}\mathbf v_E,\qquad \mathbf R_{BE} = \mathbf R_x(\phi)\,\mathbf R_y(\theta)\,\mathbf R_z(\psi)
$$

$$
\mathbf R_x(\phi)=\begin{pmatrix}1&0&0\\0&\cos\phi&\sin\phi\\0&-\sin\phi&\cos\phi\end{pmatrix},\quad \mathbf R_y(\theta)=\begin{pmatrix}\cos\theta&0&-\sin\theta\\0&1&0\\\sin\theta&0&\cos\theta\end{pmatrix},\quad \mathbf R_z(\psi)=\begin{pmatrix}\cos\psi&\sin\psi&0\\-\sin\psi&\cos\psi&0\\0&0&1\end{pmatrix}
$$

- Rotation matrices are orthogonal, so $\mathbf R^{-1} = \mathbf R^T$.
- Matrix multiplication is **not commutative**, so the order of rotations matters.
- **Gimbal lock** limits the ranges: $\phi,\psi\in[-\pi,\pi]$ and $\theta\in[-\pi/2,\pi/2]$.

### Rates of change in a rotating frame
The unit vectors of the body frame rotate. For example $\frac{d\mathbf i}{dt} = r\mathbf j - q\mathbf k$. So

$$
\left(\frac{d\mathbf v}{dt}\right) = \dot U\mathbf i+\dot V\mathbf j+\dot W\mathbf k + U\frac{d\mathbf i}{dt}+V\frac{d\mathbf j}{dt}+W\frac{d\mathbf k}{dt} = \dot{\mathbf v}+\boldsymbol\omega\times\mathbf v
$$

### Newton's second law in the body frame

$$
\boxed{\mathbf F_B = m(\dot{\mathbf v}_B+\boldsymbol\omega_B\times\mathbf v_B)}\qquad \boxed{\mathbf M_B = \dot{\mathbf h}_B+\boldsymbol\omega_B\times\mathbf h_B}
$$

## 3. Inertia tensor and full equations (L1.03)

$$
\mathbf h = \int\mathbf r\times(\boldsymbol\omega\times\mathbf r)\,dm = \mathbf I\boldsymbol\omega,\qquad \mathbf I = \begin{pmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{pmatrix}
$$

$$
I_{xx}=\int(y^2+z^2)dm,\quad I_{yy}=\int(x^2+z^2)dm,\quad I_{zz}=\int(x^2+y^2)dm,\quad I_{xy}=\int xy\,dm,\ \text{etc.}
$$

**DAP1**: this treats the aircraft as a rigid body with fixed CG. Fuel sloshing and pumping violate that. Concorde pumped fuel fore and aft to move the CG between subsonic and supersonic flight.

**Full nonlinear equations**:

$$
X = m(\dot U+qW-rV),\qquad Y = m(\dot V+rU-pW),\qquad Z = m(\dot W+pV-qU)
$$

$$
L = I_{xx}\dot p - I_{xy}\dot q - I_{xz}\dot r + q(-I_{xz}p-I_{yz}q+I_{zz}r) - r(-I_{xy}p+I_{yy}q-I_{yz}r)
$$

The $M$ and $N$ equations are similar. The equations are coupled through the **state products** ($qW$, $rV$, ...) and the **product-of-inertia terms**.

### Simplifications
1. **Stability axes**: $x$ aligned with $U_\infty$ at trim, so the trim values are $U=U_\infty$, $V=W=0$.
2. **Symmetry** about the $xz$-plane: $I_{xy}=I_{yz}=0$ (only $I_{xz}\neq0$).
3. **Linearisation** (see [[Small Perturbation Linearisation]]): perturb about trim, $U=U_\infty+u$, $V=v$, $W=w$ with $u,v,w\ll U_\infty$ (about $\pm10\%$ in practice). Drop products of small quantities (written $=_1$).

   For example, $X = m(\dot U+qW-rV)$ becomes $\Delta X = m\dot u$.

### Linearised, decoupled equations of motion

$$
\underbrace{\begin{aligned}\Delta X &= m\dot u\\ \Delta Z &= m(\dot w-qU_\infty)\\ \Delta M &= I_{yy}\dot q\end{aligned}}_{\text{longitudinal: }u,\ w,\ q}\qquad\qquad \underbrace{\begin{aligned}\Delta Y &= m(\dot v+rU_\infty)\\ \Delta L &= I_{xx}\dot p-I_{xz}\dot r\\ \Delta N &= -I_{xz}\dot p+I_{zz}\dot r\end{aligned}}_{\text{lateral: }v,\ p,\ r}
$$

This is **DAP3** in action: two independent three-equation systems. The rest of Part A studies the longitudinal set. Next, the out-of-balance forces $\Delta X$, $\Delta Z$, $\Delta M$ are modelled in [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]].

> [!tip] Trim point
> Equilibrium means $\dot{\bar{\mathbf x}} = 0 = f(\bar{\mathbf x},\bar{\mathbf u})$. This is the same trim concept as in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]].

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Next: [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]
- Maths: vector cross products and ODEs (MATH2048)
- Year 3: full 6-DoF and lateral dynamics in [[SESA3047 Advanced Aerospace Mechanics & Control]]

## Year 1 foundation
- $\sum F = ma$ in an inertial frame ([[FEEG1002 D1 - Linear Motion of Particles]], [[FEEG1002 D2 - Curvilinear Motion]]), rigid-body kinematics with $\boldsymbol\omega\times\mathbf r$ ([[FEEG1002 D7 - Kinematics of Rigid Bodies]]) and $\sum M_G = I_G\alpha$ ([[FEEG1002 D8 - Kinetics of Rigid Bodies]]). This note moves them into a rotating body frame.

## Sources
- Lectures 1.01–1.03 (Dr S. Araujo-Estrada)
- Cook, *Flight Dynamics Principles* (3rd ed.), Ch. 2 and 4.1–4.3
