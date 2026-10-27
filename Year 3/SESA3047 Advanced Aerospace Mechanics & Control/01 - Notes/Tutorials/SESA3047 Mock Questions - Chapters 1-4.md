---
title: "SESA3047 Mock Questions - Chapters 1-4"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: tutorial
subtype: self-written-mock
lecturer_set: false
stream: "Chapters 1–4: Fundamentals, Kinematics, Rigid-Body Dynamics, Flat-Earth 6-DOF Model"
tags: [sesa3047, tutorial-solutions, mock-questions, self-written, exam-prep, dcm, euler-angles, transport-theorem, rigid-body-dynamics, 6dof]
sheet: "Self-written mock questions (not lecturer-set)"
theory_notes: ["[[SESA3047 1.1 - Dynamic Systems and Control Architectures]]", "[[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]", "[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]", "[[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]", "[[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]]", "[[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]]", "[[SESA3047 3.3 - Rigid-Body Rotational Dynamics]]", "[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]", "[[SESA3047 4.2 - Translational Dynamics]]", "[[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]"]
parent: ["[[SESA3047 Advanced Aerospace Mechanics & Control Hub]]"]
status: complete
coverage: "Chapters 1–4 as lectured to Thu 22 Oct 2026 (L2–L13)"
date: 2026-10-24
sources: ["01 - Notes/Topics", "01 - Notes/SESA3047 Formula Sheet.md", "02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/Chapter_4.pdf"]
---

# SESA3047 Mock Questions - Chapters 1-4

> [!warning] Self-written mock questions, not lecturer-set
> **Self-written mock questions, not lecturer-set; written from lectured content of Chapters 1–4 (to 22 Oct 2026).** Format, marks and timings are guesses at an exam style. They are not the real SESA3047 paper.
>
> **What was checked before writing these (24 Oct 2026):**
> - `02 - Sources/Lectures`: the four chapter handouts and the L2–L13 transcripts. No tutorial sheet, revision questions or problem sheet was set or mentioned in any transcript. The only in-lecture "left to you" items are two matrix multiplications in Chapter 4 (Eqs. 4.11–4.14, L12 ll. 142–144; Eq. 4.23, L13 ll. 3–5), already worked in [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Self-study tasks|4.1]].
> - `03 - Exams & Past Papers`: empty, so there is no past paper or specimen paper.
> - `04 - Labs & Coursework`: **Lab 1** (MATLAB exercises feeding the 20 % lab report) and **Coursework 1** (20 marks, 10 % of the module, due Thu 29 Oct, 23:00; L12 ll. 352–357). Both are **assessed**, so neither is solved here. The numbers below deliberately differ from both. Where a question practises the same skill (Q4, Q10), it uses its own data and its own attitude, so nothing here is a coursework answer.

> [!info] How to use this sheet
> - **Timing:** marks are converted at **≈1.8 min per mark** (about a 2-hour paper of 65–70 marks). The SESA3047 exam format had not been announced by 22 Oct, so treat this rate as an assumption. The whole sheet is 118 marks, about 3.5 hours: do two or three questions per sitting.
> - Attempt each question closed-book, then compare. Each solution links back to the section of the topic note it tests.
> - Conventions follow the lectures: $\mathbf C=\mathbf C_{FRD/NED}=\mathbf C_x(\phi)\mathbf C_y(\theta)\mathbf C_z(\psi)$, $\mathbf u^{FRD}=\mathbf C\mathbf u^{NED}$, $\boldsymbol\omega^{FRD}=[p,q,r]^T$, $\mathbf v^{FRD}=[u,v,w]^T$, $g=9.81$ m/s², angles in radians inside trigonometric functions.
> - Every number in a `[!check]` callout was recomputed in Python (numpy/scipy).

| Q | Topic | Marks | Time |
|---|---|---:|---:|
| 1 | Classifying and linearising a drone altitude model; control architecture | 13 | 23 min |
| 2 | Frames, notation and the flat-Earth model (mostly explain) | 10 | 18 min |
| 3 | The transport theorem | 10 | 18 min |
| 4 | Building and inverting a 3-2-1 DCM | 14 | 25 min |
| 5 | Gimbal lock | 8 | 14 min |
| 6 | Euler-angle rates from gyro rates | 10 | 18 min |
| 7 | Coriolis and transport acceleration in a spinning station | 12 | 22 min |
| 8 | Inertia matrix, principal axes and Euler's equations | 14 | 25 min |
| 9 | Propeller rotor contribution | 12 | 22 min |
| 10 | Body-axis translational dynamics and the 12-state model | 15 | 27 min |

---

## Q1. Classifying and linearising a drone altitude model

**[13 marks, ≈23 min]**

A crop-spraying quadcopter is modelled in vertical motion only. Its height $h$ above the ground obeys

$$
m\ddot h=T-mg-d\,\dot h|\dot h|,
$$

with $m=1.2$ kg, drag coefficient $d=0.05$ kg/m and total rotor thrust $T$. A laser altimeter measures height; vertical gusts are the main unknown influence.

**(a)** Identify a minimum state set, the input, the output, the parameters and the disturbance. **[3]**

**(b)** Classify the model (linear or nonlinear, time-invariant or time-varying, lumped or continuum, static or dynamic). How does the classification change once the spray tank drains in flight? **[3]**

**(c)** Write the model in first-order state form and linearise it about a steady climb at $\dot h_0=2$ m/s. Find the trim thrust $T_0$ and the $\mathbf A$ and $\mathbf B$ matrices. A thrust step of $\delta T=0.5$ N is applied: compare the new steady climb rate from the linear and the nonlinear model. **[4]**

**(d)** The drone must hold 30 m above rising terrain. Sketch a control architecture using the altimeter and a forward-looking radar. Label $r$, $e$, $y_m$ and $d$, and say why feedforward alone is not enough. **[3]**

### Solution

**(a)** The equation is second order in $h$, so two states are needed ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#2. Variables, parameters, inputs, outputs and states|1.2 §2]]):

- states $x_1=h$, $x_2=\dot h$ (height alone cannot predict the future: the climb rate is also needed);
- input $T$ (commanded through the motor speeds);
- output $y=h$, measured as $y_m$ by the altimeter (with noise and bias);
- parameters $m$, $d$, $g$;
- disturbance: vertical gusts, i.e. an unmeasured force added to the right-hand side.

**(b)** ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#5. Linear and nonlinear models|1.2 §5]], [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#6. Time-invariant and time-varying models|§6]])

- **Nonlinear**, because of $\dot h|\dot h|$. Superposition fails: doubling $\dot h$ quadruples the drag.
- **Time-invariant** while $m$, $d$ are constant.
- **Lumped-parameter** (one ODE, not a PDE), and **dynamic** (it evolves from initial conditions).
- With the tank draining, $m=m(t)$ changes explicitly with time, so the model becomes **nonlinear time-varying**. (Over a short manoeuvre the mass change is small, so it can still be approximated as time-invariant.)

**(c)** State form:

$$
\dot x_1=x_2,
$$

$$
\dot x_2=\frac{T-mg-d\,x_2|x_2|}{m}=f_2(x_2,T).
$$

For $x_2>0$, $x_2|x_2|=x_2^2$. Trim needs $\dot x_2=0$ at $x_2=\dot h_0$:

$$
0=T_0-mg-d\dot h_0^2,
$$

$$
T_0=mg+d\dot h_0^2,
$$

$$
T_0=1.2(9.81)+0.05(2)^2=11.772+0.200=11.972\ \text{N}.
$$

Partial derivatives at the trim point:

$$
\frac{\partial f_2}{\partial x_2}=-\frac{2d\,x_2}{m}\bigg|_0=-\frac{2(0.05)(2)}{1.2}=-0.1667\ \text{s}^{-1},
$$

$$
\frac{\partial f_2}{\partial T}=\frac1m=0.8333\ \text{kg}^{-1}.
$$

$f_1$ gives the row $[0,\ 1]$ and does not depend on $T$. So

$$
\delta\dot{\mathbf x}=\underbrace{\begin{bmatrix}0&1\\0&-0.1667\end{bmatrix}}_{\mathbf A}\delta\mathbf x+\underbrace{\begin{bmatrix}0\\0.8333\end{bmatrix}}_{\mathbf B}\delta T,
\qquad\text{i.e.}\qquad m\,\delta\ddot h+0.2\,\delta\dot h=\delta T.
$$

The climb rate settles with time constant $m/(2d\dot h_0)=6$ s.

**Step response.** Linear steady state ($\delta\ddot h=0$):

$$
\delta\dot h_{lin}=\frac{\delta T}{2d\dot h_0}=\frac{0.5}{0.2}=2.5\ \text{m/s}.
$$

Nonlinear steady state:

$$
d\dot h^2=T_0+\delta T-mg=0.2+0.5=0.7,
$$

$$
\dot h=\sqrt{0.7/0.05}=\sqrt{14}=3.742\ \text{m/s},
$$

$$
\delta\dot h_{nl}=3.742-2=1.742\ \text{m/s}.
$$

The linear model over-predicts by 44 %. A 0.5 N step is not a small perturbation here (it is 2.5 times the trim drag). The linear model is valid only near the point at which it was built ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#Worked example — linearising the cubic oscillator|1.2, linearising the cubic oscillator]]).

**(d)** ([[SESA3047 1.1 - Dynamic Systems and Control Architectures#4. Anatomy of an active aerospace control system|1.1 §4]], [[SESA3047 1.1 - Dynamic Systems and Control Architectures#7. Feedforward control|§7]])

- **Feedback loop:** $r=30$ m → comparison point $\Sigma$ → $e=r-y_m$ → controller (flight computer) → actuators (motors/rotors) → thrust $T$ → plant (drone) → $y=h$ → altimeter → $y_m$ (the feedback signal) back to the comparison point.
- **Disturbance $d$:** gusts enter at the plant. Rising terrain changes the measured height above ground directly.
- **Feedforward path:** the radar measures the terrain ahead, and a model converts it into a climb (thrust) command that is added to the controller output **before** a height error develops.
- **Why not feedforward alone:** it relies on the model ($m$ falls as the tank drains, $d$ is uncertain) and cannot see unmeasured gusts. Only feedback corrects the residual error. The combined arrangement anticipates the terrain and then cleans up the remaining error.

> [!check] Python check
> $T_0=11.972$ N; finite-difference drag slope at $\dot h_0=2$: $0.2000$ N s/m; $\mathbf A_{22}=-0.16667$, $\mathbf B_2=0.83333$; $\delta\dot h_{lin}=2.500$, $\delta\dot h_{nl}=1.7417$ m/s.

---

## Q2. Frames, notation and the flat-Earth model

**[10 marks, ≈18 min]** (mostly explanation)

**(a)** Explain the difference between a reference frame and a coordinate system. State in words what ${}^{e}\dot{\mathbf p}^{NED}_{cm/Q}$ means, label by label. **[2]**

**(b)** State the three flat-Earth assumptions. For each, give one consequence for the equations of motion. **[3]**

**(c)** A survey UAV flies straight and level at 60 m/s for 30 s over Southampton (latitude 50.9°N). Estimate (i) the Coriolis acceleration neglected by the flat-Earth model, as a fraction of $g$, and the position error it could cause in 30 s and in 10 min; (ii) the drop of the Earth's surface below the tangent plane over the 30 s leg. Use $\Omega=7.292\times10^{-5}$ rad/s and $R=6371$ km. Comment. **[3]**

**(d)** For each quantity, say whether NED or FRD coordinates are the natural choice, and why: gravity; propeller thrust; aerodynamic force; ground-track position; angular velocity measured by gyros. **[2]**

### Solution

**(a)** A **reference frame** is an observer: an origin, plus axes with a given motion. Velocities, accelerations and time derivatives are defined relative to a frame. A **coordinate system** is a way of writing a vector's components (Cartesian NED, FRD, spherical, …). The same physical vector has different components in different coordinate systems ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#9. Reference frame, coordinate system and vector|1.2 §9]]).

${}^{e}\dot{\mathbf p}^{NED}_{cm/Q}$ reads as follows ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#Where each label goes (L4, ll. 44–117)|1.2, where each label goes]]):

- right subscript $cm/Q$: position **of** the centre of mass **relative to** the point $Q$ (the NED origin);
- left superscript $e$: the time derivative is taken by an observer fixed in the Earth frame $F_e$;
- right superscript $NED$: the components are written in NED axes.

So it is the Earth-relative velocity of the cm in north, east, down components, $\mathbf v^{NED}_{cm/e}=[\dot x,\dot y,\dot z]^T$.

**(b)** ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#11. Flat-Earth model|1.2 §11]], [[SESA3047 4.2 - Translational Dynamics#2. Apply the flat-Earth assumptions (4.32)|4.2 §2]])

| Assumption | Consequence |
|---|---|
| Earth rotation neglected, $\boldsymbol\omega_{e/i}=\mathbf 0$ | the Earth frame is inertial: $\mathbf a_{P/i}=\mathbf a_{P/e}$, no centrifugal or Coriolis terms, and $\boldsymbol\omega_{b/e}=\boldsymbol\omega_{b/i}$ |
| Curvature neglected (tangent plane) | NED axes keep the same directions everywhere; position is integrated as $\dot{\mathbf p}^{NED}=\mathbf C^T\mathbf v$ with a fixed origin |
| Gravity constant in size and direction | $\mathbf g^{NED}=[0,0,g]^T$ for all positions and heights |

**(c)(i)** Horizontal flight: the Coriolis size is $2\Omega V\sin\lambda$:

$$
a_{cor}=2(7.292\times10^{-5})(60)\sin50.9^\circ,
$$

$$
a_{cor}=6.79\times10^{-3}\ \text{m/s}^2=0.069\,\%\ \text{of } g.
$$

Treating it as a constant uncorrected acceleration, $\Delta s=\tfrac12a t^2$:

$$
\Delta s_{30\,s}=\tfrac12(6.79\times10^{-3})(30)^2=3.06\ \text{m},
$$

$$
\Delta s_{10\,min}=\tfrac12(6.79\times10^{-3})(600)^2=1.22\ \text{km}.
$$

**(c)(ii)** Distance flown $s=60\times30=1800$ m. Surface drop below the tangent plane:

$$
\delta\approx\frac{s^2}{2R}=\frac{1800^2}{2(6.371\times10^6)}=0.254\ \text{m},
$$

about 0.014 % of the distance flown.

**Comment.** For a 30 s handling or control problem both effects are negligible, so flat Earth is justified. For navigation over many minutes the error grows as $t^2$ and is not negligible: long-range navigation, ballistic and orbital problems keep the rotating, curved Earth ([[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#How big are they? (suggested numbers)|3.2, how big are they]]).

**(d)** ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models#12. NED and FRD coordinates|1.2 §12]])

- gravity: **NED**, where it is $[0,0,g]^T$ whatever the attitude;
- thrust: **FRD**, since it is fixed to the airframe (usually along $x_b$);
- aerodynamic force: **FRD**, since it depends on the body's orientation to the flow;
- ground-track position: **NED** (north, east, down from a fixed origin);
- angular velocity from gyros: **FRD**, since the gyros are strapped to the body and measure $p,q,r$.

> [!check] Python check
> $2\Omega V\sin\lambda=6.7907\times10^{-3}$ m/s² $=0.0692\,\%\,g$; drifts 3.056 m and 1222 m; $s^2/2R=0.25428$ m (exact $R(\sec(s/R)-1)=0.25428$ m); centrifugal $\Omega^2R\cos\lambda=0.0214$ m/s² for comparison.

---

## Q3. The transport theorem

**[10 marks, ≈18 min]**

**(a)** Derive the transport theorem ${}^a\dot{\mathbf p}={}^b\dot{\mathbf p}+\boldsymbol\omega_{b/a}\times\mathbf p$ by differentiating the components of $\mathbf p$ in a basis fixed in $F_b$. **[4]**

**(b)** A survey aircraft rotates relative to the Earth with $\boldsymbol\omega^{FRD}_{b/e}=[0.2,\ 0.1,\ -0.3]^T$ rad/s. A camera sits on a telescopic boom. At the instant considered its position from the cm is $\mathbf p^{FRD}=[2,\ 0,\ 0.3]^T$ m, and the boom is extending along $x_b$ at 0.5 m/s. Write $\tilde{\boldsymbol\omega}$, and find the rate of change of $\mathbf p$ seen from the Earth, in FRD components. **[4]**

**(c)** (i) What is the answer if the boom is locked? (ii) Apply the theorem to $\boldsymbol\omega_{b/a}$ itself, and state what it implies. **[2]**

### Solution

**(a)** ([[SESA3047 2.1 - Vector Operations and the Transport Theorem#Derivation 2: differentiate the components (recommended for exams)|2.1, derivation 2]]) Let $\mathbf b_1,\mathbf b_2,\mathbf b_3$ be unit vectors fixed in $F_b$, and write

$$
\mathbf p=p_1\mathbf b_1+p_2\mathbf b_2+p_3\mathbf b_3=\sum_i p_i\mathbf b_i .
$$

Differentiate in $F_a$ with the product rule:

$$
{}^a\dot{\mathbf p}=\sum_i\dot p_i\,\mathbf b_i+\sum_i p_i\,{}^a\dot{\mathbf b}_i .
$$

An observer in $F_b$ sees the $\mathbf b_i$ as constant, so the first sum is the $F_b$ derivative:

$$
\sum_i\dot p_i\,\mathbf b_i={}^b\dot{\mathbf p}.
$$

Each $\mathbf b_i$ is a fixed-length vector rotating with $F_b$, so its rate seen from $F_a$ is (definition of angular velocity)

$$
{}^a\dot{\mathbf b}_i=\boldsymbol\omega_{b/a}\times\mathbf b_i .
$$

Substitute, then take the constant $\boldsymbol\omega_{b/a}$ out of the sum:

$$
\sum_i p_i\,\boldsymbol\omega_{b/a}\times\mathbf b_i=\boldsymbol\omega_{b/a}\times\sum_i p_i\mathbf b_i=\boldsymbol\omega_{b/a}\times\mathbf p .
$$

Hence

$$
\boxed{{}^a\dot{\mathbf p}={}^b\dot{\mathbf p}+\boldsymbol\omega_{b/a}\times\mathbf p.}
$$

**(b)** The cross-product matrix ([[SESA3047 2.1 - Vector Operations and the Transport Theorem#The cross-product (skew) matrix|2.1, skew matrix]]):

$$
\tilde{\boldsymbol\omega}=\begin{bmatrix}0&-\omega_z&\omega_y\\\omega_z&0&-\omega_x\\-\omega_y&\omega_x&0\end{bmatrix}=\begin{bmatrix}0&0.3&0.1\\-0.3&0&-0.2\\-0.1&0.2&0\end{bmatrix}.
$$

Row by row:

$$
\tilde{\boldsymbol\omega}\mathbf p=\begin{bmatrix}0(2)+0.3(0)+0.1(0.3)\\-0.3(2)+0(0)-0.2(0.3)\\-0.1(2)+0.2(0)+0(0.3)\end{bmatrix}=\begin{bmatrix}0.03\\-0.66\\-0.20\end{bmatrix}\ \text{m/s}.
$$

The boom extension is the body-frame rate, ${}^b\dot{\mathbf p}=[0.5,0,0]^T$ m/s. Add:

$$
{}^e\dot{\mathbf p}=\begin{bmatrix}0.5\\0\\0\end{bmatrix}+\begin{bmatrix}0.03\\-0.66\\-0.20\end{bmatrix}=\begin{bmatrix}0.53\\-0.66\\-0.20\end{bmatrix}\ \text{m/s},\qquad|{}^e\dot{\mathbf p}|=0.870\ \text{m/s}.
$$

This is an Earth-frame derivative, but written in FRD components. The frame of differentiation and the coordinates are separate choices.

**(c)** ([[SESA3047 2.1 - Vector Operations and the Transport Theorem#Special cases (Eqs. 2.23–2.25)|2.1, special cases]])

(i) Locked boom: ${}^b\dot{\mathbf p}=\mathbf 0$, so ${}^e\dot{\mathbf p}=\boldsymbol\omega\times\mathbf p=[0.03,-0.66,-0.20]^T$ m/s. This is the rigid-body result $\mathbf v_P-\mathbf v_{cm}=\boldsymbol\omega\times\mathbf p$.

(ii) Put $\mathbf p=\boldsymbol\omega_{b/a}$:

$$
{}^a\dot{\boldsymbol\omega}_{b/a}={}^b\dot{\boldsymbol\omega}_{b/a}+\underbrace{\boldsymbol\omega_{b/a}\times\boldsymbol\omega_{b/a}}_{=\mathbf 0}={}^b\dot{\boldsymbol\omega}_{b/a}.
$$

Angular acceleration is the same seen from either frame. That is why $\dot p,\dot q,\dot r$ need no frame label ([[SESA3047 2.1 - Vector Operations and the Transport Theorem#7. The angular velocity vector|2.1 §7]]).

> [!check] Python check
> `np.cross([0.2,0.1,-0.3],[2,0,0.3])` $=[0.03,-0.66,-0.20]$, identical to $\tilde{\boldsymbol\omega}\mathbf p$; sum $[0.53,-0.66,-0.20]$, norm $0.86977$ m/s.

---

## Q4. Building and inverting a 3-2-1 DCM

**[14 marks, ≈25 min]**

An aircraft has attitude $\phi=-25^\circ$, $\theta=35^\circ$, $\psi=140^\circ$ (aerospace 3-2-1 sequence).

**(a)** Write $\mathbf C_z(\psi)$, $\mathbf C_y(\theta)$, $\mathbf C_x(\phi)$ numerically, and form $\mathbf C_{FRD/NED}$. Check three entries against the closed-form matrix. **[4]**

**(b)** Verify that $\mathbf C$ is orthogonal with $\det\mathbf C=+1$, and explain why both must hold. **[2]**

**(c)** Recover the three Euler angles from $\mathbf C$. Show what goes wrong if $\psi$ is computed as $\arctan(C_{12}/C_{11})$. **[4]**

**(d)** The Earth-relative velocity is $\mathbf v^{NED}=[-140,\ 110,\ -115]^T$ m/s. Find $\mathbf v^{FRD}$ and $\mathbf g^{FRD}$, and interpret the signs. **[4]**

### Solution

**(a)** With $\cos140^\circ=-0.7660$, $\sin140^\circ=0.6428$, $\cos35^\circ=0.8192$, $\sin35^\circ=0.5736$, $\cos(-25^\circ)=0.9063$, $\sin(-25^\circ)=-0.4226$ ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#4. The three elementary rotations|2.2 §4]]):

$$
\mathbf C_z=\begin{bmatrix}-0.7660&0.6428&0\\-0.6428&-0.7660&0\\0&0&1\end{bmatrix},\quad
\mathbf C_y=\begin{bmatrix}0.8192&0&-0.5736\\0&1&0\\0.5736&0&0.8192\end{bmatrix},\quad
\mathbf C_x=\begin{bmatrix}1&0&0\\0&0.9063&-0.4226\\0&0.4226&0.9063\end{bmatrix}.
$$

Multiply in the right order: yaw first, so $\mathbf C_z$ sits on the right. First step:

$$
\mathbf C_y\mathbf C_z=\begin{bmatrix}-0.6275&0.5265&-0.5736\\-0.6428&-0.7660&0\\-0.4394&0.3687&0.8192\end{bmatrix}.
$$

Second step:

$$
\mathbf C=\mathbf C_x(\mathbf C_y\mathbf C_z)=\begin{bmatrix}-0.6275&0.5265&-0.5736\\-0.3969&-0.8501&-0.3462\\-0.6699&0.0104&0.7424\end{bmatrix}.
$$

Check against the closed form ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Multiplying it out (the step the notes compress into one line)|2.2, multiplying it out]]):

- $C_{11}=c_\theta c_\psi=0.8192(-0.7660)=-0.6275$ ✓;
- $C_{23}=s_\phi c_\theta=-0.4226(0.8192)=-0.3462$ ✓;
- $C_{32}=-s_\phi c_\psi+c_\phi s_\theta s_\psi=-0.3237+0.3341=0.0104$ ✓.

**(b)** ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#3. Properties of a DCM (§2.3.2), with the reasons|2.2 §3]]) Row 1 length:

$$
0.6275^2+0.5265^2+0.5736^2=0.3938+0.2772+0.3290=1.0000 .
$$

Rows 1 and 2 are orthogonal:

$$
(-0.6275)(-0.3969)+(0.5265)(-0.8501)+(-0.5736)(-0.3462)=0.2490-0.4476+0.1986=0.0000 .
$$

The other rows behave the same way, so $\mathbf C\mathbf C^T=\mathbf I$ and $\det\mathbf C=+1$.

**Why both must hold.** Each row is an FRD unit vector written in NED components. The three are unit length and mutually perpendicular, so $\mathbf C\mathbf C^T=\mathbf I$ and $\mathbf C^{-1}=\mathbf C^T$: a rotation preserves lengths and angles. $\det\mathbf C=+1$ (not $-1$) because FRD is right-handed like NED. The DCM is a proper rotation, not a reflection.

**(c)** Extraction formulas ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#7. Extracting Euler angles from a DCM (§2.4.4)|2.2 §7]]):

$$
\theta=-\arcsin C_{13}=-\arcsin(-0.5736)=35.0^\circ,
$$

$$
\phi=\mathrm{atan2}(C_{23},C_{33})=\mathrm{atan2}(-0.3462,\ 0.7424)=-25.0^\circ,
$$

$$
\psi=\mathrm{atan2}(C_{12},C_{11})=\mathrm{atan2}(0.5265,\ -0.6275)=140.0^\circ .
$$

With a plain arctangent:

$$
\arctan\frac{C_{12}}{C_{11}}=\arctan\frac{0.5265}{-0.6275}=\arctan(-0.8391)=-40.0^\circ .
$$

This is $180^\circ$ out: north-west instead of south-east. The ratio loses the signs. $C_{11}=c_\theta c_\psi<0$ with $c_\theta>0$ says $\cos\psi<0$, so $\psi$ is in the second quadrant. atan2 reads both signs ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Why atan2, not arctan (the L6 question)|2.2, why atan2]]).

**(d)** NED to FRD is $\mathbf v^{FRD}=\mathbf C\mathbf v^{NED}$ ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#The two directions of transformation (Eqs. 2.40–2.41)|2.2, two directions]]). Row by row:

$$
u=(-0.6275)(-140)+(0.5265)(110)+(-0.5736)(-115)=87.85+57.92+65.96=211.73\ \text{m/s},
$$

$$
v=(-0.3969)(-140)+(-0.8501)(110)+(-0.3462)(-115)=55.56-93.51+39.81=1.86\ \text{m/s},
$$

$$
w=(-0.6699)(-140)+(0.0104)(110)+(0.7424)(-115)=93.78+1.14-85.38=9.55\ \text{m/s}.
$$

The speed is unchanged, $|\mathbf v|=211.96$ m/s. Almost all of it is along the nose. The small positive $w$ means the flow meets the aircraft slightly from below (a small positive angle between the velocity and the nose), and the small $v$ means a slight sideslip. In NED the same vector is climbing south-east: $\dot z=-115$ m/s.

Gravity is $g$ times the third column of $\mathbf C$ ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Gravity in body axes (derivation)|2.2, gravity in body axes]]):

$$
\mathbf g^{FRD}=g\begin{bmatrix}-s_\theta\\s_\phi c_\theta\\c_\phi c_\theta\end{bmatrix}=9.81\begin{bmatrix}-0.5736\\-0.3462\\0.7424\end{bmatrix}=\begin{bmatrix}-5.627\\-3.396\\7.283\end{bmatrix}\ \text{m/s}^2.
$$

$g_x<0$: nose up, so weight has a rearward component. $g_y<0$: left wing down ($\phi<0$), so weight pulls towards the left wing. $g_z$ is reduced to $g\cos\phi\cos\theta$.

> [!check] Python check
> $\mathbf C$ as above (full precision $C_{32}=0.010400$); $\mathbf C\mathbf C^T=\mathbf I$ to $10^{-16}$, $\det\mathbf C=1.000000$; recovered $(-25.000^\circ,35.000^\circ,140.000^\circ)$; $\arctan$ gives $-40.000^\circ$; $\mathbf v^{FRD}=[211.732,\ 1.864,\ 9.550]^T$, $\mathbf C^T\mathbf v^{FRD}$ returns $[-140,110,-115]^T$; $\mathbf g^{FRD}=[-5.6268,-3.3961,7.2830]^T$.

---

## Q5. Gimbal lock

**[8 marks, ≈14 min]**

**(a)** Substitute $\theta=90^\circ$ into the 3-2-1 DCM and show that it depends on $\phi$ and $\psi$ only through $\phi-\psi$. **[4]**

**(b)** Evaluate $\mathbf C$ for $(\phi,\theta,\psi)=(50^\circ,90^\circ,20^\circ)$ and $(40^\circ,90^\circ,10^\circ)$. What do the extraction formulas return? What happens at $\theta=89^\circ$? **[2]**

**(c)** Explain gimbal lock physically, relate it to the Euler-rate equations, and name a remedy. **[2]**

### Solution

**(a)** ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#8. The singularity: gimbal lock (§2.4.5)|2.2 §8]]) Put $s_\theta=1$, $c_\theta=0$ into the closed-form matrix (formula sheet):

$$
\mathbf C=\begin{bmatrix}0&0&-1\\-c_\phi s_\psi+s_\phi c_\psi&c_\phi c_\psi+s_\phi s_\psi&0\\s_\phi s_\psi+c_\phi c_\psi&-s_\phi c_\psi+c_\phi s_\psi&0\end{bmatrix}.
$$

Use $\sin(\phi-\psi)=s_\phi c_\psi-c_\phi s_\psi$ on $C_{21}$ and $-C_{32}$:

$$
C_{21}=\sin(\phi-\psi),\qquad C_{32}=-\sin(\phi-\psi).
$$

Use $\cos(\phi-\psi)=c_\phi c_\psi+s_\phi s_\psi$ on $C_{22}$ and $C_{31}$:

$$
C_{22}=C_{31}=\cos(\phi-\psi).
$$

Hence

$$
\mathbf C(\theta=90^\circ)=\begin{bmatrix}0&0&-1\\\sin(\phi-\psi)&\cos(\phi-\psi)&0\\\cos(\phi-\psi)&-\sin(\phi-\psi)&0\end{bmatrix}.
$$

Only the difference $\phi-\psi$ appears. Every pair with the same difference gives the same attitude. (At $\theta=-90^\circ$ it is $\phi+\psi$.)

**(b)** Both sets have $\phi-\psi=30^\circ$, so

$$
\mathbf C=\begin{bmatrix}0&0&-1\\0.5&0.8660&0\\0.8660&-0.5&0\end{bmatrix}
$$

for both. Extraction gives $\theta=-\arcsin(-1)=90^\circ$. But $\phi=\mathrm{atan2}(0,0)$ and $\psi=\mathrm{atan2}(0,0)$ are undefined: the matrix fixes only $\phi-\psi$.

At $\theta=89^\circ$: $C_{23}=0.01337$, $C_{33}=0.01122$, so $\phi=\mathrm{atan2}(0.01337,0.01122)=50.0^\circ$. The angle is still recoverable in principle, but from entries of size $|\cos\theta|=0.0175$. Small errors in $\mathbf C$ therefore become large errors in $\phi$ and $\psi$.

**(c)** At $\theta=\pm90^\circ$ the pitch rotation has turned the roll axis $x_b$ onto the original yaw axis (vertical). Yaw and roll then rotate about the same line, and one degree of freedom of the description is lost. The body itself is fine: only the three-angle coordinates fail.

The same singularity appears in the kinematics: $\det\mathbf E=\cos\theta=0$. $\mathbf H=\mathbf E^{-1}$ contains $\tan\theta$ and $1/\cos\theta$, so finite $p,q,r$ demand infinite $\dot\phi,\dot\psi$ ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#8. The singularity at θ = ±90° (extension)|3.1 §8]]).

Remedy: use a non-singular attitude representation such as **quaternions** (or propagate the DCM itself). For conventional aircraft that never reach vertical, Euler angles remain fine.

> [!check] Python check
> $\max|\mathbf C(50,90,20)-\mathbf C(40,90,10)|=1.1\times10^{-16}$; $(60,90,30)$ gives the same matrix; at $-90^\circ$, $(50,-90,20)$ and $(40,-90,30)$ agree to $1.1\times10^{-16}$; at $89^\circ$: $C_{11}=0.01640$, $C_{12}=0.00597$, $C_{23}=0.01337$, $C_{33}=0.01122$.

---

## Q6. Euler-angle rates from gyro rates

**[10 marks, ≈18 min]**

**(a)** Starting from $\boldsymbol\omega^{FRD}=[\dot\phi,0,0]^T+\mathbf C_x(\phi)\left([0,\dot\theta,0]^T+\mathbf C_y(\theta)[0,0,\dot\psi]^T\right)$, derive $\mathbf E(\boldsymbol\Phi)$ in $\boldsymbol\omega=\mathbf E\dot{\boldsymbol\Phi}$. Explain why $\dot\psi$ is rotated twice and $\dot\phi$ not at all. **[4]**

**(b)** Invert to obtain $\dot\phi$, $\dot\theta$, $\dot\psi$. A gyro package reads $p=0.15$, $q=-0.08$, $r=0.25$ rad/s at $\phi=30^\circ$, $\theta=-20^\circ$. Compute the Euler rates. **[4]**

**(c)** Compare with the small-angle approximation, and estimate the attitude change over the next 0.2 s. **[2]**

### Solution

**(a)** ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#3. Composing the three rotation rates (§3.1.2, L7 ll. 160–194)|3.1 §3]], [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#4. Multiplying it out, one step at a time (Appendix §3.4.1, L7 ll. 200–300)|§4]])

$\dot\psi$ is about the NED down axis, which is the first axis in the sequence. To reach FRD it must pass through the pitch and then the roll rotation. $\dot\theta$ is about the intermediate $y$ axis and only needs the roll rotation. $\dot\phi$ is already about body $x$.

Innermost product first:

$$
\mathbf C_y(\theta)\begin{bmatrix}0\\0\\\dot\psi\end{bmatrix}=\begin{bmatrix}-s_\theta\dot\psi\\0\\c_\theta\dot\psi\end{bmatrix}.
$$

Add the pitch rate:

$$
\begin{bmatrix}-s_\theta\dot\psi\\\dot\theta\\c_\theta\dot\psi\end{bmatrix}.
$$

Apply $\mathbf C_x(\phi)$ (rows $[1,0,0]$, $[0,c_\phi,s_\phi]$, $[0,-s_\phi,c_\phi]$):

$$
\begin{bmatrix}-s_\theta\dot\psi\\c_\phi\dot\theta+s_\phi c_\theta\dot\psi\\-s_\phi\dot\theta+c_\phi c_\theta\dot\psi\end{bmatrix}.
$$

Add the roll rate and collect into a matrix:

$$
\begin{bmatrix}p\\q\\r\end{bmatrix}=\underbrace{\begin{bmatrix}1&0&-s_\theta\\0&c_\phi&s_\phi c_\theta\\0&-s_\phi&c_\phi c_\theta\end{bmatrix}}_{\mathbf E}\begin{bmatrix}\dot\phi\\\dot\theta\\\dot\psi\end{bmatrix}.
$$

**(b)** ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#6. Inverting: the rotational kinematic equation (§3.1.3, Eqs. 3.10–3.11; L7 ll. 323–341)|3.1 §6]]) Rows 2 and 3:

$$
q=c_\phi\dot\theta+s_\phi c_\theta\dot\psi,\qquad r=-s_\phi\dot\theta+c_\phi c_\theta\dot\psi .
$$

Multiply the first by $s_\phi$, the second by $c_\phi$, and add. The $\dot\theta$ terms cancel:

$$
qs_\phi+rc_\phi=(s_\phi^2+c_\phi^2)c_\theta\dot\psi=c_\theta\dot\psi\ \Rightarrow\ \dot\psi=\frac{qs_\phi+rc_\phi}{c_\theta}.
$$

Multiply the first by $c_\phi$, the second by $s_\phi$, and subtract. The $\dot\psi$ terms cancel:

$$
qc_\phi-rs_\phi=(c_\phi^2+s_\phi^2)\dot\theta\ \Rightarrow\ \dot\theta=qc_\phi-rs_\phi .
$$

Row 1, then substitute $\dot\psi$:

$$
\dot\phi=p+s_\theta\dot\psi=p+(qs_\phi+rc_\phi)\tan\theta .
$$

Numbers ($s_\phi=0.5$, $c_\phi=0.8660$, $c_\theta=0.9397$, $\tan\theta=-0.3640$):

$$
qs_\phi+rc_\phi=(-0.08)(0.5)+(0.25)(0.8660)=-0.0400+0.2165=0.1765\ \text{rad/s},
$$

$$
\dot\psi=\frac{0.1765}{0.9397}=0.1878\ \text{rad/s}=10.76^\circ/\text{s},
$$

$$
\dot\theta=(-0.08)(0.8660)-(0.25)(0.5)=-0.0693-0.1250=-0.1943\ \text{rad/s}=-11.13^\circ/\text{s},
$$

$$
\dot\phi=0.15+(0.1765)(-0.3640)=0.15-0.0642=0.0858\ \text{rad/s}=4.91^\circ/\text{s}.
$$

**(c)** ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#7. Physical interpretation and the small-angle form (§3.1.4)|3.1 §7]]) The small-angle form $\dot{\boldsymbol\Phi}\approx[p,q,r]^T=[8.59,-4.58,14.32]^\circ$/s is badly wrong here. It is 75 % high in roll rate, 59 % low in pitch rate and 33 % high in yaw rate. At a $30^\circ$ roll angle, yaw and pitch rates are shared between $q$ and $r$.

One Euler step of 0.2 s:

$$
\Delta\boldsymbol\Phi\approx0.2\,\dot{\boldsymbol\Phi}=[0.98^\circ,\ -2.23^\circ,\ 2.15^\circ].
$$

> [!check] Python check
> $\mathbf H\boldsymbol\omega=[0.085757,\ -0.194282,\ 0.187834]$ rad/s $=[4.9135,-11.1315,10.7621]^\circ$/s; $\mathbf E\dot{\boldsymbol\Phi}$ returns $[0.15,-0.08,0.25]$; $\det\mathbf E=0.93969=\cos(-20^\circ)$. Integrating $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ for 0.2 s with constant $p,q,r$ (`solve_ivp`) gives $[0.945^\circ,-2.243^\circ,2.148^\circ]$, so the single Euler step is within $0.04^\circ$.

---

## Q7. Coriolis and transport acceleration in a spinning station

**[12 marks, ≈22 min]**

![[amc_mock_station_coriolis.png|900]]

A space station spins about its axis at a constant $\omega=0.2$ rad/s; its centre $Q$ is unaccelerated in inertial space. In the station frame $F_b$ take $x_b$ radially outward along a ladder, $z_b$ along the spin axis and $y_b=z_b\times x_b$ (the spin direction). An 80 kg astronaut climbs the ladder towards the hub. At $r=40$ m she moves inward at 1.5 m/s and is slowing at 0.1 m/s² (relative to the ladder).

**(a)** Starting from $\mathbf r_P=\mathbf r_Q+\mathbf p_{P/Q}$, derive the five-term expression for $\mathbf a_{P/a}$ when $F_b$ moves relative to $F_a$. Name each term. **[5]**

**(b)** Evaluate each term and the inertial acceleration in $F_b$ components. Find the force the ladder must exert on the astronaut, and explain its sideways component physically. **[5]**

**(c)** Repeat if the station is being spun up at $\alpha=0.01$ rad/s² at that instant. Relate the result to what the flat-Earth model throws away. **[2]**

### Solution

**(a)** ([[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#2. Acceleration of a point in a moving frame (§3.2.1, Eqs. 3.24–3.26)|3.2 §2]]) Write $\boldsymbol\omega=\boldsymbol\omega_{b/a}$, $\boldsymbol\alpha={}^a\dot{\boldsymbol\omega}$, $\mathbf p=\mathbf p_{P/Q}$. Differentiate the position in $F_a$:

$$
\mathbf v_{P/a}=\mathbf v_{Q/a}+{}^a\dot{\mathbf p}.
$$

$\mathbf p$ is described in $F_b$, so use the transport theorem:

$$
\mathbf v_{P/a}=\mathbf v_{Q/a}+\mathbf v_{P/b}+\boldsymbol\omega\times\mathbf p .
$$

Differentiate again in $F_a$, term by term. The relative velocity needs the transport theorem:

$$
{}^a\dot{\mathbf v}_{P/b}=\mathbf a_{P/b}+\boldsymbol\omega\times\mathbf v_{P/b}.
$$

The origin term is already an $F_a$ quantity:

$$
{}^a\dot{\mathbf v}_{Q/a}=\mathbf a_{Q/a}.
$$

The cross product needs the product rule, then the velocity relation for ${}^a\dot{\mathbf p}$:

$$
{}^a\tfrac{\mathrm d}{\mathrm dt}(\boldsymbol\omega\times\mathbf p)=\boldsymbol\alpha\times\mathbf p+\boldsymbol\omega\times(\mathbf v_{P/b}+\boldsymbol\omega\times\mathbf p).
$$

Add the three and collect the two $\boldsymbol\omega\times\mathbf v_{P/b}$ terms:

$$
\boxed{\mathbf a_{P/a}=\underbrace{\mathbf a_{P/b}}_{\text{relative}}+\underbrace{\mathbf a_{Q/a}+\boldsymbol\alpha\times\mathbf p+\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf p)}_{\text{transport}}+\underbrace{2\boldsymbol\omega\times\mathbf v_{P/b}}_{\text{Coriolis}}}
$$

The **transport** acceleration is the acceleration a point fixed in $F_b$ at P would have: the origin's acceleration, the angular-acceleration term $\boldsymbol\alpha\times\mathbf p$ and the centripetal term. The **Coriolis** term exists only when P moves within $F_b$. Its factor 2 comes from two equal contributions: one from the rotation of $\mathbf v_{P/b}$, the other from P moving to where the transport velocity is different.

**(b)** Data in $F_b$: $\boldsymbol\omega=[0,0,0.2]^T$, $\mathbf p=[40,0,0]^T$, $\mathbf v_{P/b}=[-1.5,0,0]^T$, $\mathbf a_{P/b}=[+0.1,0,0]^T$ (slowing an inward motion means an outward acceleration), $\mathbf a_{Q/a}=\mathbf 0$, $\boldsymbol\alpha=\mathbf 0$.

Centripetal, inner product first:

$$
\boldsymbol\omega\times\mathbf p=[0(0)-0.2(0),\ 0.2(40)-0(0),\ 0]^T=[0,\ 8,\ 0]^T\ \text{m/s},
$$

$$
\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf p)=[0(0)-0.2(8),\ 0.2(0)-0(0),\ 0]^T=[-1.6,\ 0,\ 0]^T\ \text{m/s}^2 .
$$

This points to the hub, with size $\omega^2r=0.04\times40=1.6$ m/s² ✓.

Coriolis:

$$
\boldsymbol\omega\times\mathbf v_{P/b}=[0,\ 0.2(-1.5),\ 0]^T=[0,\ -0.3,\ 0]^T,
$$

$$
2\boldsymbol\omega\times\mathbf v_{P/b}=[0,\ -0.6,\ 0]^T\ \text{m/s}^2 .
$$

Sum:

$$
\mathbf a_{P/i}=\begin{bmatrix}0.1\\0\\0\end{bmatrix}+\begin{bmatrix}-1.6\\0\\0\end{bmatrix}+\begin{bmatrix}0\\-0.6\\0\end{bmatrix}=\begin{bmatrix}-1.5\\-0.6\\0\end{bmatrix}\ \text{m/s}^2 .
$$

Newton's law holds in the inertial frame:

$$
\mathbf F=m\mathbf a_{P/i}=80[-1.5,\ -0.6,\ 0]^T=[-120,\ -48,\ 0]^T\ \text{N}.
$$

The ladder pulls her **120 N towards the hub**. That is less than the 128 N she would need standing still, because she is braking her climb. It also pushes her **48 N against the spin direction**. She moves to a smaller radius where the ladder's tangential speed $\omega r$ is lower, but she still carries her old tangential speed. Without the sideways push she would drift ahead of the ladder, in the spin direction, i.e. the apparent Coriolis force $-2m\boldsymbol\omega\times\mathbf v_{P/b}=+48$ N $\mathbf y_b$. Here the Coriolis term is 37.5 % of the centripetal term.

**(c)** Spin-up adds the angular-acceleration term $\boldsymbol\alpha\times\mathbf p$:

$$
\boldsymbol\alpha\times\mathbf p=[0,0,0.01]^T\times[40,0,0]^T=[0,\ 0.4,\ 0]^T\ \text{m/s}^2,
$$

$$
\mathbf a_{P/i}=[-1.5,\ -0.2,\ 0]^T\ \text{m/s}^2,\qquad\mathbf F=[-120,\ -16,\ 0]^T\ \text{N}.
$$

The spin-up drags the ladder forward and partly cancels the Coriolis push.

The flat-Earth model sets exactly these frame terms to zero for the Earth ([[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#Rotating Earth (Eqs. 3.27–3.31)|3.2, rotating Earth]], [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#Flat Earth (Eqs. 3.32–3.33)|flat Earth]]). On Earth, $\Omega=7.29\times10^{-5}$ rad/s, 2700 times smaller than here, so the terms are of order $10^{-2}$ m/s², not 1 m/s².

> [!check] Python check
> `np.cross` gives $\boldsymbol\omega\times\mathbf p=[0,8,0]$, centripetal $[-1.6,0,0]$, Coriolis $[0,-0.6,0]$; $\mathbf a_{P/i}=[-1.5,-0.6,0]$, $\mathbf F=[-120,-48,0]$ N; with spin-up $[-1.5,-0.2,0]$, $[-120,-16,0]$ N; Coriolis/centripetal $=0.375$.

---

## Q8. Inertia matrix, principal axes and Euler's equations

**[14 marks, ≈25 min]**

A small satellite has, in its body axes $B$,

$$
\mathbf J_B=\begin{bmatrix}120&-15&0\\-15&80&0\\0&0&150\end{bmatrix}\ \text{kg m}^2 .
$$

**(a)** State the integral definitions of $J_{xx}$ and $J_{xy}$, and the value of $J_{xy}$ for this satellite. **[2]**

**(b)** Find the principal moments of inertia and a right-handed set of principal axes. Through what angle about $z_B$ are they rotated? **[4]**

**(c)** In principal axes the satellite has $\boldsymbol\omega_P=[0.05,\ 0.02,\ 0.1]^T$ rad/s, and its thrusters apply $\mathbf M_P=[0.5,\ 0,\ -0.2]^T$ N m. Use Euler's equations to find $\dot{\boldsymbol\omega}_P$. **[4]**

**(d)** Show that the full-matrix equation in body axes $B$ gives the same answer, and that $\mathbf h$ is not parallel to $\boldsymbol\omega$. **[2]**

**(e)** With the thrusters off, about which principal axes is a pure spin stable? **[2]**

### Solution

**(a)** ([[SESA3047 3.3 - Rigid-Body Rotational Dynamics#Step 5: the inertia matrix (Eqs. 3.60–3.63)|3.3, the inertia matrix]])

$$
J_{xx}=\int_B(y^2+z^2)\,\mathrm dm,\qquad J_{xy}=\int_B xy\,\mathrm dm,
$$

The products enter the matrix with a minus sign, $\mathbf J=\begin{bmatrix}J_{xx}&-J_{xy}&-J_{xz}\\\cdot&J_{yy}&-J_{yz}\\\cdot&\cdot&J_{zz}\end{bmatrix}$. An entry of $-15$ therefore means $J_{xy}=+15$ kg m², with $J_{xz}=J_{yz}=0$.

**(b)** ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#3. Principal axes and diagonal inertia (4.6–4.9)|4.1 §3]]) $z_B$ is already principal, with $\lambda_3=150$. For the $x$–$y$ block:

$$
\det\begin{bmatrix}120-\lambda&-15\\-15&80-\lambda\end{bmatrix}=(120-\lambda)(80-\lambda)-225=0,
$$

$$
\lambda^2-200\lambda+9600-225=0,
$$

$$
\lambda=100\pm\sqrt{100^2-9375}=100\pm25,
$$

$$
\lambda_1=125,\qquad\lambda_2=75\ \text{kg m}^2 .
$$

Eigenvectors. For $\lambda_1=125$: $(120-125)x-15y=0$, so $y=-x/3$. For $\lambda_2=75$: $(120-75)x-15y=0$, so $y=3x$. Normalised:

$$
\mathbf e_1=\tfrac{1}{\sqrt{10}}[3,-1,0]^T,\quad\mathbf e_2=\tfrac{1}{\sqrt{10}}[1,3,0]^T,\quad\mathbf e_3=[0,0,1]^T .
$$

Right-handedness check: $\mathbf e_1\times\mathbf e_2=\tfrac1{10}[0,0,3\cdot3-(-1)\cdot1]^T=[0,0,1]^T=\mathbf e_3$ ✓, so $\det\mathbf Q=+1$ for $\mathbf Q=[\mathbf e_1\ \mathbf e_2\ \mathbf e_3]$. The principal $x$ axis lies at $\arctan(-1/3)=-18.43^\circ$ about $z_B$. Check: $\tan2\vartheta=2(-15)/(120-80)=-0.75$ gives $\vartheta=-18.43^\circ$ ✓. Then

$$
\mathbf J_P=\mathbf Q^T\mathbf J_B\mathbf Q=\operatorname{diag}(125,\ 75,\ 150)\ \text{kg m}^2 .
$$

**(c)** Euler's equations ([[SESA3047 3.3 - Rigid-Body Rotational Dynamics#Step 5: principal axes, Euler's equations (extension)|3.3, Euler's equations]]), with $J_x=125$, $J_y=75$, $J_z=150$:

$$
\dot p=\frac{L+(J_y-J_z)qr}{J_x}=\frac{0.5+(75-150)(0.02)(0.1)}{125}=\frac{0.5-0.15}{125}=2.80\times10^{-3}\ \text{rad/s}^2,
$$

$$
\dot q=\frac{M+(J_z-J_x)rp}{J_y}=\frac{0+(150-125)(0.1)(0.05)}{75}=\frac{0.125}{75}=1.667\times10^{-3}\ \text{rad/s}^2,
$$

$$
\dot r=\frac{N+(J_x-J_y)pq}{J_z}=\frac{-0.2+(125-75)(0.05)(0.02)}{150}=\frac{-0.2+0.05}{150}=-1.000\times10^{-3}\ \text{rad/s}^2 .
$$

$\dot q\neq0$ with $M=0$: pitch acceleration comes purely from inertia coupling of $r$ and $p$ ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Inertia coupling with no external moment (L12 ll. 22–119)|4.1, inertia coupling]]).

**(d)** Transform to $B$: $\boldsymbol\omega_B=\mathbf Q\boldsymbol\omega_P=[0.05376,\ 0.00316,\ 0.1]^T$ and $\mathbf M_B=\mathbf Q\mathbf M_P=[0.4743,\ -0.1581,\ -0.2]^T$. Solving $\dot{\boldsymbol\omega}_B=\mathbf J_B^{-1}(\mathbf M_B-\tilde{\boldsymbol\omega}_B\mathbf J_B\boldsymbol\omega_B)$ ([[SESA3047 3.3 - Rigid-Body Rotational Dynamics#4. The rotational dynamic equation (§3.3.3, Eqs. 3.64–3.71)|3.3 §4]]) gives $[3.183,\ 0.696,\ -1.000]^T\times10^{-3}$ rad/s². This equals $\mathbf Q\dot{\boldsymbol\omega}_P$ ✓: the physics does not depend on the axes chosen.

Angular momentum: $\mathbf h_P=[6.25,\ 1.5,\ 15]^T$ and $\mathbf h_B=[6.404,\ -0.553,\ 15]^T$, both of size 16.32 kg m²/s. The angle between $\mathbf h$ and $\boldsymbol\omega$ is $6.24^\circ$. They are parallel only for spin about a principal axis.

**(e)** Spin about the **largest** ($\mathbf e_3$, 150) or the **smallest** ($\mathbf e_2$, 75) principal moment is stable. Spin about the **intermediate** axis ($\mathbf e_1$, 125) is an equilibrium but unstable: the tennis-racket effect ([[SESA3047 3.3 - Rigid-Body Rotational Dynamics#5.3 Torque-free motion and the intermediate-axis theorem (suggested)|3.3 §5.3]]). (Energy dissipation in a real satellite makes only the maximum axis stable in the long run.)

> [!check] Python check
> `np.linalg.eigh` gives $(75,125,150)$; $\mathbf Q^T\mathbf J\mathbf Q=\operatorname{diag}(125,75,150)$, $\det\mathbf Q=1$; $\dot{\boldsymbol\omega}_P=[0.0028,\ 0.0016667,\ -0.0010]$; full $B$-axis solve $[0.003183,\ 0.000696,\ -0.001]=\mathbf Q\dot{\boldsymbol\omega}_P$; $|\mathbf h|=16.3191$ in both bases; angle $6.243^\circ$.

---

## Q9. Propeller rotor contribution

**[12 marks, ≈22 min]**

A single-engine turboprop has $J_{xx}=12\,000$, $J_{yy}=25\,000$, $J_{zz}=34\,000$, $J_{xz}=1\,500$ kg m² ($J_{xy}=J_{yz}=0$). The propeller and turbine have $I_R=8$ kg m² about the body $x$ axis and turn at a constant 1200 rpm, clockwise seen from behind. The locked rotor inertia is already in $\mathbf J$.

**(a)** Starting from $\mathbf h=\mathbf J\boldsymbol\omega+\mathbf h_R$, derive $\dot{\boldsymbol\omega}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)-\mathbf J^{-1}\tilde{\boldsymbol\omega}\mathbf h_R$, stating each assumption. **[4]**

**(b)** In a pull-up with $p=r=0$, $q=0.2$ rad/s and no aerodynamic moments, find $\dot p$, $\dot q$, $\dot r$. Which way does the nose swing? **[4]**

**(c)** Estimate the yaw rate after 2 s if nothing is done, and the rudder yaw moment that would cancel the effect. **[2]**

**(d)** Why do the rigid-body equations still apply with a spinning rotor? How do twin counter-rotating propellers change the result? **[2]**

### Solution

**(a)** ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#5. Spinning internal rotors (4.15–4.25)|4.1 §5]]) Moment balance about the cm, with the derivative moved to the body frame by the transport theorem:

$$
\mathbf M={}^b\dot{\mathbf h}+\boldsymbol\omega\times\mathbf h .
$$

Substitute $\mathbf h=\mathbf J\boldsymbol\omega+\mathbf h_R$:

$$
\mathbf M={}^b\tfrac{\mathrm d}{\mathrm dt}(\mathbf J\boldsymbol\omega+\mathbf h_R)+\boldsymbol\omega\times(\mathbf J\boldsymbol\omega+\mathbf h_R).
$$

Rigid body with a balanced axisymmetric rotor, so $\mathbf J$ is constant in body axes:

$$
\mathbf M=\mathbf J\dot{\boldsymbol\omega}+{}^b\dot{\mathbf h}_R+\boldsymbol\omega\times\mathbf J\boldsymbol\omega+\boldsymbol\omega\times\mathbf h_R .
$$

Constant rotor speed on a body-fixed axis gives ${}^b\dot{\mathbf h}_R=\mathbf 0$:

$$
\mathbf J\dot{\boldsymbol\omega}=\mathbf M-\boldsymbol\omega\times\mathbf J\boldsymbol\omega-\boldsymbol\omega\times\mathbf h_R .
$$

Premultiply by $\mathbf J^{-1}$ and write the cross products as skew matrices:

$$
\dot{\boldsymbol\omega}=\underbrace{\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)}_{\dot{\boldsymbol\omega}_{base}}\ \underbrace{-\ \mathbf J^{-1}\tilde{\boldsymbol\omega}\mathbf h_R}_{\dot{\boldsymbol\omega}_{add}} .
$$

**(b)** Rotor momentum: clockwise seen from behind is a right-handed rotation about $+x_b$, so

$$
\Omega_R=1200\times\frac{2\pi}{60}=125.66\ \text{rad/s},\qquad h_x=I_R\Omega_R=8(125.66)=1005.3\ \text{kg m}^2/\text{s}.
$$

**Base part.** $\mathbf J\boldsymbol\omega=[-J_{xz}r,\ J_{yy}q,\ J_{zz}r-J_{xz}p]^T=[0,\ 5000,\ 0]^T$, which is parallel to $\boldsymbol\omega$. So $\boldsymbol\omega\times\mathbf J\boldsymbol\omega=\mathbf 0$ and, with $\mathbf M=\mathbf 0$, $\dot{\boldsymbol\omega}_{base}=\mathbf 0$.

**Rotor part** ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Step 4: explicit aircraft rotor corrections|4.1, aircraft rotor corrections]]):

$$
-\tilde{\boldsymbol\omega}\mathbf h_R=\begin{bmatrix}rh_y-qh_z\\ph_z-rh_x\\qh_x-ph_y\end{bmatrix}=\begin{bmatrix}0\\0\\0.2(1005.3)\end{bmatrix}=\begin{bmatrix}0\\0\\201.06\end{bmatrix}\ \text{N m}.
$$

Aircraft inverse ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#4. Aircraft symmetry and the roll–yaw inverse (4.10–4.14)|4.1 §4]]):

$$
\Gamma=J_{xx}J_{zz}-J_{xz}^2=12\,000(34\,000)-1500^2=4.0575\times10^8\ \text{kg}^2\text{m}^4 .
$$

Row 1:

$$
\dot p=\frac{J_{zz}(0)+J_{xz}(201.06)}{\Gamma}=\frac{1500(201.06)}{4.0575\times10^8}=7.43\times10^{-4}\ \text{rad/s}^2 .
$$

Row 2:

$$
\dot q=\frac{ph_z-rh_x}{J_{yy}}=0 .
$$

Row 3:

$$
\dot r=\frac{J_{xz}(0)+J_{xx}(201.06)}{\Gamma}=\frac{12\,000(201.06)}{4.0575\times10^8}=5.95\times10^{-3}\ \text{rad/s}^2=0.341^\circ/\text{s}^2 .
$$

$\dot r>0$: the nose swings to the **right** in a pull-up. This is the rotor contribution $\dot{\boldsymbol\omega}_{add}$ (textbooks: the gyroscopic precession of a clockwise propeller). The small $\dot p$ appears only through $J_{xz}$.

**(c)** Held for 2 s at constant rates:

$$
r\approx5.95\times10^{-3}(2)=0.0119\ \text{rad/s}=0.68^\circ/\text{s}.
$$

To cancel it, $\mathbf M$ must equal $\boldsymbol\omega\times\mathbf h_R$, which makes the bracket zero:

$$
\mathbf M=\boldsymbol\omega\times\mathbf h_R=[0,\ 0,\ -201.1]^T\ \text{N m},
$$

i.e. a left-yawing rudder moment $N=-201$ N m.

**(d)** A balanced, axisymmetric rotor on a fixed axis does not move the cm and presents the same inertia at every rotor angle, so $\mathbf J$ stays constant. Its relative spin enters only through $\mathbf h_R$ (L12 ll. 234–242). With twin propellers turning in opposite senses at equal speed, the two $\mathbf h_R$ cancel. Then $\dot{\boldsymbol\omega}_{add}=\mathbf 0$, as with a quadcopter's alternating rotors ([[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Diagonal inertia: the quadcopter form (L13 ll. 82–86)|4.1, quadcopter form]]). A changing rotor speed would add $-\mathbf J^{-1}\,{}^b\dot{\mathbf h}_R$ (handout only, Eq. 4.25).

> [!check] Python check
> $h_x=1005.310$; $\Gamma=4.0575\times10^8$; `np.linalg.solve(J, -cross(w,hR))` $=[7.433\times10^{-4},\ 0,\ 5.9464\times10^{-3}]$; base term $[0,0,0]$; with $\mathbf M=\boldsymbol\omega\times\mathbf h_R=[0,0,-201.06]$ the total $\dot{\boldsymbol\omega}$ is $[0,0,0]$; $r(2\,\text{s})=0.011893$ rad/s $=0.681^\circ$/s.

---

## Q10. Body-axis translational dynamics and the 12-state model

**[15 marks, ≈27 min]**

A 25 kg fixed-wing UAV is modelled as a rigid body over a flat Earth, with principal body axes. At one instant:

- attitude $\phi=15^\circ$, $\theta=5^\circ$, $\psi=60^\circ$;
- $\mathbf v^{FRD}=[30,\ 1.5,\ 2.0]^T$ m/s, $\boldsymbol\omega^{FRD}=[0.10,\ 0.05,\ 0.08]^T$ rad/s;
- aerodynamic plus propulsive force (gravity excluded) $\mathbf F^{FRD}=[-20,\ -5,\ -230]^T$ N;
- moment $\mathbf M^{FRD}=[0.3,\ -0.2,\ 0.1]^T$ N m, with $\mathbf J=\operatorname{diag}(2.0,\ 3.5,\ 5.0)$ kg m².

**(a)** List the twelve states in the handout order, write the four equation groups, and say which are kinematics and which dynamics. **[3]**

**(b)** Find $\mathbf g^{FRD}$. **[2]**

**(c)** Find $\dot u$, $\dot v$, $\dot w$. **[3]**

**(d)** Find $\dot p$, $\dot q$, $\dot r$. **[2]**

**(e)** Find $\dot x$, $\dot y$, $\dot z$ (with the climb rate and ground track) and the Euler rates. **[3]**

**(f)** Explain why $[\dot u,\dot v,\dot w]^T$ is not the aircraft's acceleration, and what must be recomputed every time a solver evaluates the right-hand side. **[2]**

### Solution

**(a)** ([[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model#1. State order and assumptions (4.41)|4.3 §1]], [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model#2. Assemble the four equation groups (4.42)|§2]])

$$
\mathbf x=[x,y,z,\ \phi,\theta,\psi,\ u,v,w,\ p,q,r]^T,
$$

$$
\begin{aligned}
\dot{\mathbf p}^{NED}&=\mathbf C^T\mathbf v &&\text{translational kinematics}\\
\dot{\boldsymbol\Phi}&=\mathbf H(\boldsymbol\Phi)\boldsymbol\omega &&\text{rotational kinematics}\\
\dot{\mathbf v}&=\mathbf F/m+\mathbf C\mathbf g^{NED}-\tilde{\boldsymbol\omega}\mathbf v &&\text{translational dynamics}\\
\dot{\boldsymbol\omega}&=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega) &&\text{rotational dynamics}
\end{aligned}
$$

Six degrees of freedom need twelve first-order states: one coordinate (kinematic) and one rate (dynamic) state per degree of freedom (L13 ll. 339–340).

**(b)** ([[SESA3047 4.2 - Translational Dynamics#Step 3: rotate gravity|4.2, rotate gravity]])

$$
\mathbf g^{FRD}=g\begin{bmatrix}-s_\theta\\s_\phi c_\theta\\c_\phi c_\theta\end{bmatrix}=9.81\begin{bmatrix}-0.08716\\0.25783\\0.96225\end{bmatrix}=\begin{bmatrix}-0.8550\\2.5294\\9.4397\end{bmatrix}\ \text{m/s}^2 .
$$

**(c)** ([[SESA3047 4.2 - Translational Dynamics#3. Derive the body-velocity equation (4.33–4.37)|4.2 §3]]) Non-gravitational force per unit mass:

$$
\mathbf F/m=[-20,\ -5,\ -230]^T/25=[-0.8,\ -0.2,\ -9.2]^T\ \text{m/s}^2 .
$$

Frame-rotation term, row by row:

$$
\boldsymbol\omega\times\mathbf v=\begin{bmatrix}qw-rv\\ru-pw\\pv-qu\end{bmatrix}=\begin{bmatrix}0.05(2)-0.08(1.5)\\0.08(30)-0.1(2)\\0.1(1.5)-0.05(30)\end{bmatrix}=\begin{bmatrix}-0.02\\2.20\\-1.35\end{bmatrix}\ \text{m/s}^2 .
$$

Assemble $\dot{\mathbf v}=\mathbf F/m+\mathbf g^{FRD}-\boldsymbol\omega\times\mathbf v$:

$$
\dot u=-0.8-0.8550+0.02=-1.635\ \text{m/s}^2,
$$

$$
\dot v=-0.2+2.5294-2.20=0.129\ \text{m/s}^2,
$$

$$
\dot w=-9.2+9.4397+1.35=1.590\ \text{m/s}^2 .
$$

**(d)** Principal axes, so Euler's equations apply. First $\mathbf J\boldsymbol\omega=[0.2,\ 0.175,\ 0.4]^T$, then

$$
\boldsymbol\omega\times\mathbf J\boldsymbol\omega=[0.05(0.4)-0.08(0.175),\ 0.08(0.2)-0.1(0.4),\ 0.1(0.175)-0.05(0.2)]^T=[0.006,\ -0.024,\ 0.0075]^T,
$$

$$
\dot p=\frac{0.3-0.006}{2.0}=0.1470,\qquad\dot q=\frac{-0.2+0.024}{3.5}=-0.0503,\qquad\dot r=\frac{0.1-0.0075}{5.0}=0.0185\ \text{rad/s}^2 .
$$

**(e)** The DCM at $(15^\circ,5^\circ,60^\circ)$ is

$$
\mathbf C=\begin{bmatrix}0.4981&0.8627&-0.0872\\-0.8252&0.5025&0.2578\\0.2662&-0.0565&0.9623\end{bmatrix}.
$$

Position rates: the transpose takes FRD to NED ([[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#5. The position state equation (§3.2.3, Eqs. 3.35–3.40)|3.2 §5]]):

$$
\dot x=0.4981(30)-0.8252(1.5)+0.2662(2)=14.94-1.24+0.53=14.24\ \text{m/s},
$$

$$
\dot y=0.8627(30)+0.5025(1.5)-0.0565(2)=25.88+0.75-0.11=26.52\ \text{m/s},
$$

$$
\dot z=-0.0872(30)+0.2578(1.5)+0.9623(2)=-2.61+0.39+1.92=-0.30\ \text{m/s}.
$$

So the UAV climbs at $-\dot z=0.30$ m/s with ground speed 30.10 m/s along a track of $\arctan(26.52/14.24)=61.8^\circ$. That is not exactly its heading of 60°, because $v$ and $w$ also project horizontally.

Euler rates, with $qs_\phi+rc_\phi=0.05(0.2588)+0.08(0.9659)=0.0902$:

$$
\dot\phi=0.10+0.0902\tan5^\circ=0.1079,\quad
\dot\theta=0.05(0.9659)-0.08(0.2588)=0.0276,\quad
\dot\psi=\frac{0.0902}{\cos5^\circ}=0.0906\ \text{rad/s}.
$$

**(f)** FRD axes rotate with the aircraft. $[\dot u,\dot v,\dot w]^T$ is only the rate of change of the components; the inertial acceleration is $\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v=\mathbf F/m+\mathbf g=[-1.655,\ 2.329,\ 0.240]^T$ m/s² ([[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#4. Differentiating the velocity in the body frame (§3.2.2 Eq. 3.34, §3.2.4 Eqs. 3.41–3.42)|3.2 §4]]). For example, $\dot v$ is only $0.13$ m/s², while the lateral inertial acceleration is $2.33$ m/s²: most of the sideways force goes into turning the velocity vector with the rotating axes ($ru=2.4$ m/s²). At every solver evaluation, recompute $\mathbf C$ and $\mathbf H$ from the **current trial** Euler angles, recompute $\mathbf F$ and $\mathbf M$ from the current state and controls, and evaluate all four groups together ([[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model#3. Evaluate the derivative for a numerical solver|4.3 §3]]).

> [!check] Python check
> $\mathbf g^{FRD}=[-0.85500,\ 2.52935,\ 9.43967]$; $\boldsymbol\omega\times\mathbf v=[-0.02,\ 2.2,\ -1.35]$; $\dot{\mathbf v}=[-1.634998,\ 0.129353,\ 1.589674]$; $\dot{\boldsymbol\omega}=[0.147000,\ -0.050286,\ 0.018500]$; $\mathbf C^T\mathbf v=[14.2375,\ 26.5226,\ -0.3034]$, track $61.773^\circ$; $\mathbf H\boldsymbol\omega=[0.107893,\ 0.027591,\ 0.090560]$; $\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v=\mathbf F/m+\mathbf g=[-1.654998,\ 2.329353,\ 0.239674]$.

---

## Links

- Parent: [[SESA3047 Advanced Aerospace Mechanics & Control Hub]]
- Formula sheet: [[SESA3047 Formula Sheet]]
- Figure script: `01 - Notes/Figures/generate_amc_mock_figures.py`

## Sources

- Lectured content of `Chapter 1.pdf` to `Chapter_4.pdf` and transcripts L2–L13, through the topic notes linked in each solution.
- Checked for set questions: `02 - Sources/Lectures` (no tutorial or revision sheet), `03 - Exams & Past Papers` (empty), `04 - Labs & Coursework/Lab 1/Lab_1.pdf` and `Coursework 1/Coursework_1.pdf` (assessed; not solved here).
- All numbers: numpy/scipy checks run on 24 Oct 2026.

## Self-study tasks

> [!info] Nothing here was lecturer-set
> These tasks are **suggested, not lecturer-set**. No tutorial or revision questions had been issued for SESA3047 by 22 Oct 2026.

- [ ] *(Suggested)* Q4, Q6 and Q10 closed-book under timed conditions (≈70 min). → [[#Q4. Building and inverting a 3-2-1 DCM]] · [[#Q6. Euler-angle rates from gyro rates]] · [[#Q10. Body-axis translational dynamics and the 12-state model]]
- [ ] *(Suggested)* Q3(a), Q7(a) and Q9(a) as derivation-only practice, one move per line. → [[#Q3. The transport theorem]] · [[#Q7. Coriolis and transport acceleration in a spinning station]] · [[#Q9. Propeller rotor contribution]]
- [ ] *(Suggested)* Q1, Q2 and Q5 as written explanations, then compare wording. → [[#Q1. Classifying and linearising a drone altitude model]] · [[#Q2. Frames, notation and the flat-Earth model]] · [[#Q5. Gimbal lock]]
- [ ] *(Suggested)* Q8, then rework (c) with $\mathbf M=\mathbf 0$ and explain the sign of each $\dot\omega$. → [[#Q8. Inertia matrix, principal axes and Euler's equations]]
