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
status: lectured
coverage: "L1.01–L1.03 (dynamic systems, 6-DoF EOM, linearisation and decoupling)"
parent: ["[[SESA2027 Aerospace Mechanics & Control Hub]]"]
prerequisites: []
next_topics: ["[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
key_concepts: ["[[Design and Analysis Principles]]", "[[Euler Angles and Rotation Matrices]]", "[[Small Perturbation Linearisation]]", "[[State-Space Representation]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Lecture 1.01.pdf", "02 - Sources/Lectures/Lecture 1.02.pdf", "02 - Sources/Lectures/Lecture 1.03.pdf", "02 - Sources/Lectures/Lecture 1.01 recording.txt", "02 - Sources/Lectures/Lecture 1.02 recording.txt", "02 - Sources/Lectures/Lecture 1.03 recording.txt"]
---

# SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion

> [!abstract] Summary
> A dynamic system has a state that evolves as $\dot{\mathbf x} = f(\mathbf x,\mathbf u)$. For a rigid aircraft, Newton's laws in six degrees of freedom are written in body axes, which adds the $\boldsymbol\omega\times\mathbf v$ and $\boldsymbol\omega\times\mathbf h$ terms. Symmetry about the $xz$-plane and small-perturbation linearisation about trim then split the equations into a longitudinal set in $u, w, q$ and a lateral set in $v, p, r$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks you to name or sign body-axis quantities, justify the rigid-aircraft assumptions, rotate a vector between Earth and body axes, or say which terms survive linearisation. The derivation itself is not examined.
> - **Assumptions:** rigid body, constant mass, flat Earth, cg origin; right-handed body axes ($x$ forward, $y$ starboard, $z$ down); stability axes at trim ($V=W=0$); symmetry about $xz$ ($I_{xy}=I_{yz}=0$); perturbations up to about ±10 % of trim; angles in radians.
> - **Method:** 1. Draw the body axes and label $(U,V,W)$, $(p,q,r)$, $(X,Y,Z)$, $(L,M,N)$. 2. Earth to body: $\mathbf v_B=\mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi)\mathbf v_E$ (yaw, pitch, roll; multiply right to left). 3. Write $\mathbf F=m(\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v)$ and $\mathbf M=\dot{\mathbf h}+\boldsymbol\omega\times\mathbf h$ in components. 4. Substitute $U=U_\infty+u$, $V=v$, $W=w$. 5. Drop every product of two perturbations; keep products with $U_\infty$.
> - **Common mistakes:** dropping $qU_\infty$ (it is first order because $U_\infty$ is large); multiplying the rotation matrices in the wrong order (roll is applied last, so $\mathbf R_x$ is on the left).
> - **Practise:** [[#Worked example: gravity and velocity in body axes]] · [[SESA2027 Mock Questions#Q1. Body axes, rotation and linearisation|Mock Q1]]

An aircraft is a rigid box that can move in three directions and turn about three axes, so it has six degrees of freedom, and its state at any instant takes twelve numbers: three position coordinates, three attitude angles and the six velocities $(U,V,W)$ and $(p,q,r)$. Newton's laws hold only in a frame that is not accelerating. The Earth (flat, for a few seconds of flight) is such a frame, but the forces and the sensors live in the aircraft. So Newton's laws are written in body axes, at the cost of extra terms: as the aircraft turns, its own axes swing round, and a velocity that is constant in space appears to change when it is measured along moving axes. Those are the $\boldsymbol\omega\times\mathbf v$ and $\boldsymbol\omega\times\mathbf h$ terms.

The full equations are nonlinear and coupled. Near trim, though, every perturbation is small. Products of two small things vanish, and only products with the large trim speed $U_\infty$ survive. The six equations then split into two independent sets: longitudinal motion in the plane of symmetry ($u$, $w$, $q$) and lateral motion out of it ($v$, $p$, $r$). That split (DAP3, divide and conquer) lets the longitudinal motion be analysed on its own.

---

## 1. Dynamic systems

A **dynamic system** is a system whose state changes over time according to specific rules or equations, and whose output is a function of both its current input and its history. Its **state** is the set of variables needed to describe the system at any instant (for example position and velocity), and its model is $\dot{\mathbf x}(t) = f(\mathbf x(t),\mathbf u(t))$, where $\mathbf u$ is the external input.

As a block diagram, $f$ takes the state and the input and gives $\dot{\mathbf x}$, an integrator turns $\dot{\mathbf x}$ into $\mathbf x$, and $\mathbf x$ is fed back into $f$. That internal feedback makes the output depend on the history and not just on the current input.

A controlled system has four components: the plant, sensors, actuators and controllers. Sensors include the sun sensor, star tracker, gyroscope, airspeed sensor, AoA vane and IMU. Actuators include the servomotor, thruster, reaction wheel, magnetic torquer, control surfaces and throttle. Controllers include the FCU, FCC, SAS and MCAS. Actuators are lumped into the plant: their dynamics are usually much faster than the aircraft's, so actuator and airframe are treated as one block.

| Classification | Example | Notes |
|---|---|---|
| Nonlinear | $y''+y'^2+\sin(by)=0$ | General, hard to analyse |
| Linear | $y''+cy'+dy=0$, or $\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u$ | Superposition holds; the ODE toolbox applies |
| Time-varying | Rapid mass or configuration changes (rockets) | Coefficients depend on $t$ |
| Time-invariant (LTI) | Slowly changing mass, fixed geometry (aircraft over short intervals) | Constant coefficients |

A control problem has three parts: the dynamic system being controlled, the reason it needs control (stability, performance, handling), and the means of control (sensors, controller, actuators). The model hierarchy runs from the full physics, a set of nonlinear PDEs for a flexible structure in unsteady flow, to nonlinear ODEs once the body is assumed rigid, and finally to the LTI state-space model obtained by linearising about trim.

The analysis methods fall into three groups:

- Behaviour (intrinsic): characteristic polynomial, eigenvalues, stability, $\zeta$, $\omega_n$, poles and zeros.
- Response (to an input): rise time, overshoot, settling time, transfer function, Bode plot (cut-off, bandwidth, peaking).
- Simulation: virtual prototyping, "what-if" studies, verification, and trade-off studies.

### Design and analysis principles (DAP)

1. DAP1: "All models are wrong, but some models are useful" (Box).
2. DAP2: Occam's razor. Start with the simplest explanation or model.
3. DAP3: Divide and conquer. Recursively split the problem into simpler parts.

Model accuracy rises with complexity, but with diminishing returns. Choose the simplest model that captures the behaviour you care about. See [[Design and Analysis Principles]].

## 2. Setting up the 6-DoF model

Each assumption can be checked against Airbus A380 figures:

| Assumption | Reality check (A380, recomputed below) |
|---|---|
| Rigid aircraft (no aeroelasticity) | Wing-tip deflection $\approx\pm4$ m on a 79.8 m span, $\delta/b\approx5\%$ |
| Constant mass over short intervals | A 10 s flight burns $\approx29$ kg, which is $0.005\%$ of MTOW |
| Flat Earth, constant $g$ and density | 10 s at 252 m/s covers 2.5 km; curvature drop is 0.50 m ($0.020\%$) |
| Sensor and controller dynamics neglected | Sensors are modelled in [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design\|C2]] |
| Loads act as point forces and point moments at the cg | Distributed aerodynamic loads are replaced by their resultants |

> [!check] Re-computing the A380 figures from fuel flow and speed
> - Fuel flow: $13\,000\ \text{L/h}\times(1\ \text{h}/3600\ \text{s}) = 3.61$ L/s.
> - Mass flow: $3.61\times0.8 = 2.89$ kg/s.
> - In 10 s: $28.9$ kg, which is $28.9/575\,000 = 0.005\%$ of MTOW.
> - Curvature: $910\ \text{km/h} = 252.8$ m/s, so $d = 2.53$ km in 10 s. The drop below the tangent plane is $\Delta y = d^2/(2R_E) = 0.50$ m, which is $\Delta y/d = 0.020\%$ (see the warning below).

Over a few seconds the mass is constant to better than 0.01 %. The curvature figure needs more care, because the drop does not scale linearly with distance.

> [!warning] Curvature drop grows with distance squared
> The drop below a tangent plane is $\Delta y\approx d^2/(2R_E)$ with $R_E=6371$ km, so it grows with the square of the distance. For $d=2.53$ km that is $\Delta y=0.50$ m, or $0.020\%$ of the distance. The flat-Earth error is still tiny over 10 s, but a fixed rate per kilometre (such as 12.6 cm per km) under-predicts the drop at longer distances, as the 60 s exercise below shows.

### Worked example: when do the assumptions start to bite?

*(Suggested, not lecturer-set.)* Repeat the A380 check for a 60 s interval, using $U_\infty=252.8$ m/s and a fuel burn of 2.89 kg/s.

- Distance: $d=252.8\times60=15.2$ km.
- Fuel burnt: $2.89\times60=173$ kg, which is $173/575\,000=0.030\%$ of MTOW. Constant mass still holds.
- Curvature: $\Delta y=d^2/(2R_E)=(15\,170)^2/(2\times6.371\times10^6)=18.1$ m, or $0.12\%$ of the distance. A fixed rate of 12.6 cm per km would give only 1.9 m.
- Rigidity: wing-tip deflection is a property of the load, not the time, so it is the same $\approx5\%$ of span at any interval.

> [!check] Which assumption fails first?
> Over 60 s the mass and flat-Earth errors are still a fraction of a percent. Constant density is the one to watch: a phugoid (period of order a minute, [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid|A3]]) trades tens of metres of height, and a 600 m climb near sea level changes $\rho$ by about 6 %. That is why the short-period motion is modelled over seconds.

The short flight interval means seconds, not hours. Over much longer simulations the constant-mass and flat-Earth assumptions start to break, so each assumption has to be checked against the time-scale of the motion of interest.

The derivation takes four steps:
1. Write six equations (Newton's laws): three translational and three rotational.
2. Relate the body frame to the inertial (Earth) frame using Tait–Bryan angles.
3. Express the rates of change as seen from the rotating body frame.
4. Define the inertia tensor.

### Body axes and notation

Right-handed, with $x$ forward, $y$ starboard and $z$ down.

| | $x$ (roll) | $y$ (pitch) | $z$ (yaw) |
|---|---|---|---|
| Force | $X$ | $Y$ | $Z$ |
| Moment | $L$ | $M$ | $N$ |
| Velocity of CG | $U$ | $V$ | $W$ |
| Angular rate | $p$ | $q$ | $r$ |
| Attitude angle | $\phi$ | $\theta$ | $\psi$ |
| Moment of inertia | $I_{xx}$ | $I_{yy}$ | $I_{zz}$ |

![[amc_body_axes_notation.png|900]]

Positive rotations follow the right-hand rule about each axis: positive $q$ is nose up, positive $r$ is nose to starboard, positive $p$ is starboard wing down. Positive $W$ points down through the floor, so a nose-up angle of attack gives a positive $W$.

> [!warning] $y$ out of the page in a nose-right side view
> With $x$ to the right and $z$ down the page, $\mathbf j=\mathbf k\times\mathbf i$ points out of the page. A nose-right side view is therefore seen from the starboard side. It is easy to draw $y$ into the page and then get the sign of $q$ wrong.

### Euler angles and rotation matrices
The Earth-to-body sequence is yaw $\psi$, then pitch $\theta$, then roll $\phi$:

$$
\mathbf v_B = \mathbf R_{BE}\mathbf v_E,\qquad \mathbf R_{BE} = \mathbf R_x(\phi)\,\mathbf R_y(\theta)\,\mathbf R_z(\psi)
$$

$$
\mathbf R_x(\phi)=\begin{pmatrix}1&0&0\\0&\cos\phi&\sin\phi\\0&-\sin\phi&\cos\phi\end{pmatrix},\quad \mathbf R_y(\theta)=\begin{pmatrix}\cos\theta&0&-\sin\theta\\0&1&0\\\sin\theta&0&\cos\theta\end{pmatrix},\quad \mathbf R_z(\psi)=\begin{pmatrix}\cos\psi&\sin\psi&0\\-\sin\psi&\cos\psi&0\\0&0&1\end{pmatrix}
$$

- Rotation matrices are orthogonal, so $\mathbf R^{-1} = \mathbf R^T$.
- Body to Earth: undo the rotations in reverse order with negated angles, $\mathbf R_{EB} = \mathbf R_z(-\psi)\,\mathbf R_y(-\theta)\,\mathbf R_x(-\phi)$. Since $\mathbf R_i(-\alpha) = \mathbf R_i(\alpha)^T$, this is $\mathbf R_{EB} = \mathbf R_{BE}^T$.
- Mnemonic: in $\mathbf R_x$, $\mathbf R_y$ and $\mathbf R_z$ the 1 sits in that axis's own row and column, with zeros in the rest of that row and column; the cosines fill the other diagonal places.
- Matrix multiplication is not commutative, so the order of rotations matters.
- Gimbal lock limits the ranges: $\phi,\psi\in[-\pi,\pi]$ and $\theta\in[-\pi/2,\pi/2]$.

Each matrix follows from one line of geometry. For $\mathbf R_z(\psi)$, rotate the axes by $\psi$ about $z$. A vector with Earth components $(v_{x,E},v_{y,E})$ has, along the new $x$ axis, the projection

$$
v_{x,1} = v_{x,E}\cos\psi + v_{y,E}\sin\psi
$$

and along the new $y$ axis

$$
v_{y,1} = -v_{x,E}\sin\psi + v_{y,E}\cos\psi
$$

while $v_{z,1}=v_{z,E}$. Those three lines are the rows of $\mathbf R_z(\psi)$. The same projection about $y$ (pitch) and $x$ (roll) gives $\mathbf R_y(\theta)$ and $\mathbf R_x(\phi)$. The minus sign sits in a different place in $\mathbf R_y$ because the cyclic order is $z\to x$ for a rotation about $y$.

The full Earth-to-body matrix is built by multiplying right to left. First

$$
\mathbf R_y(\theta)\mathbf R_z(\psi)=\begin{pmatrix}\cos\theta\cos\psi&\cos\theta\sin\psi&-\sin\theta\\-\sin\psi&\cos\psi&0\\\sin\theta\cos\psi&\sin\theta\sin\psi&\cos\theta\end{pmatrix}
$$

Then pre-multiply by $\mathbf R_x(\phi)$: row 1 is unchanged, row 2 becomes $\cos\phi\,(\text{row 2})+\sin\phi\,(\text{row 3})$, and row 3 becomes $-\sin\phi\,(\text{row 2})+\cos\phi\,(\text{row 3})$:

$$
\mathbf R_{BE}=\begin{pmatrix}c_\theta c_\psi & c_\theta s_\psi & -s_\theta\\ s_\phi s_\theta c_\psi-c_\phi s_\psi & s_\phi s_\theta s_\psi+c_\phi c_\psi & s_\phi c_\theta\\ c_\phi s_\theta c_\psi+s_\phi s_\psi & c_\phi s_\theta s_\psi-s_\phi c_\psi & c_\phi c_\theta\end{pmatrix}
$$

with $c_\theta=\cos\theta$, $s_\theta=\sin\theta$ and so on. Setting all angles to zero gives $\mathbf I$, as it must.

The last column of $\mathbf R_{BE}$ is gravity in body axes. Gravity is $\mathbf g_E=(0,0,g)$ in Earth axes ($z$ down), so $\mathbf g_B=\mathbf R_{BE}\mathbf g_E$ is $g$ times the third column, $\mathbf g_B=g(-\sin\theta,\ \sin\phi\cos\theta,\ \cos\phi\cos\theta)$. Yaw drops out, as it should, since turning on the spot doesn't change which way is down. These are the gravitational terms that enter the longitudinal model in [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives#1. Gravitational contributions|A2 §1]].

### Worked example: gravity and velocity in body axes

*(Suggested, not lecturer-set.)* An aircraft flies level at 250 m/s on a track of 040° (no wind). Its attitude is $\psi=40°$, $\theta=5°$, $\phi=30°$. Find $\mathbf g_B$ and $\mathbf v_B$.

Gravity, from the third column of $\mathbf R_{BE}$:

$$
\mathbf g_B=9.81\begin{pmatrix}-\sin5°\\ \sin30°\cos5°\\ \cos30°\cos5°\end{pmatrix}=\begin{pmatrix}-0.855\\ 4.886\\ 8.463\end{pmatrix}\ \text{m/s}^2
$$

Velocity: in Earth axes $\mathbf v_E=250(\cos40°,\ \sin40°,\ 0)=(191.5,\ 160.7,\ 0)$ m/s. Multiplying by $\mathbf R_{BE}$:

$$
\mathbf v_B=(U,V,W)=(249.0,\ 10.9,\ 18.9)\ \text{m/s}
$$

> [!check] Numerical check (Python)
> $|\mathbf g_B|=9.810$ and $|\mathbf v_B|=250.0$ m/s: the rotation changes components, never length. $\mathbf R\mathbf R^T=\mathbf I$ to machine precision. The body sees $W=18.9$ m/s, an angle of attack $\alpha=\arctan(W/U)=4.33°$, and $V=10.9$ m/s, a sideslip $\beta=\arcsin(V/V_\infty)=2.50°$. Pitch and bank together turn part of a horizontal velocity into the body $y$ and $z$ directions.

### Rates of change in a rotating frame

The body axes turn with the aircraft, so their unit vectors $\mathbf i,\mathbf j,\mathbf k$ change direction. In a short time $\delta t$, a yaw rate $r$ swings $\mathbf i$ through the angle $r\,\delta t$ towards $+\mathbf j$, and a nose-up pitch rate $q$ swings it through $q\,\delta t$ towards $-\mathbf k$. Roll about $\mathbf i$ itself does not move $\mathbf i$.

![[amc_rotating_unit_vectors.png|820]]

Adding the two small changes and dividing by $\delta t$:

$$
\frac{d\mathbf i}{dt}=r\,\mathbf j-q\,\mathbf k
$$

The same argument for the other two unit vectors gives

$$
\frac{d\mathbf j}{dt}=p\,\mathbf k-r\,\mathbf i,\qquad \frac{d\mathbf k}{dt}=q\,\mathbf i-p\,\mathbf j
$$

Each of these is $\boldsymbol\omega\times(\text{unit vector})$ with $\boldsymbol\omega=p\mathbf i+q\mathbf j+r\mathbf k$. For example $\boldsymbol\omega\times\mathbf i=(p,q,r)\times(1,0,0)=(0,\ r,\ -q)$.

Now differentiate $\mathbf v=U\mathbf i+V\mathbf j+W\mathbf k$ with the product rule:

$$
\frac{d\mathbf v}{dt}=\dot U\mathbf i+\dot V\mathbf j+\dot W\mathbf k+U\frac{d\mathbf i}{dt}+V\frac{d\mathbf j}{dt}+W\frac{d\mathbf k}{dt}
$$

Substitute the three unit-vector rates:

$$
\frac{d\mathbf v}{dt}=\dot U\mathbf i+\dot V\mathbf j+\dot W\mathbf k+U(r\mathbf j-q\mathbf k)+V(p\mathbf k-r\mathbf i)+W(q\mathbf i-p\mathbf j)
$$

Collect by unit vector:

$$
\frac{d\mathbf v}{dt}=(\dot U+qW-rV)\,\mathbf i+(\dot V+rU-pW)\,\mathbf j+(\dot W+pV-qU)\,\mathbf k
$$

The bracketed extras are exactly the components of $\boldsymbol\omega\times\mathbf v$:

$$
\boldsymbol\omega\times\mathbf v=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\p&q&r\\U&V&W\end{vmatrix}=(qW-rV)\,\mathbf i+(rU-pW)\,\mathbf j+(pV-qU)\,\mathbf k
$$

So the inertial acceleration, written in body axes, is

$$
\left.\frac{d\mathbf v}{dt}\right|_{\text{inertial}}=\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v
$$

where $\dot{\mathbf v}=(\dot U,\dot V,\dot W)$ is what an observer riding in the aircraft would measure. This is the transport theorem; SESA3047 gives it a general proof in [[SESA3047 2.1 - Vector Operations and the Transport Theorem]].

### Newton's second law in the body frame

$$
\boxed{\mathbf F_B = m(\dot{\mathbf v}_B+\boldsymbol\omega_B\times\mathbf v_B)}\qquad \boxed{\mathbf M_B = \dot{\mathbf h}_B+\boldsymbol\omega_B\times\mathbf h_B}
$$

The moment equation follows from the same argument applied to $\mathbf h$ instead of $\mathbf v$. Both hold about the cg; the moment equation needs the cg as origin (or an inertially fixed point).

## 3. Inertia tensor and full equations

$$
\mathbf h = \int\mathbf r\times(\boldsymbol\omega\times\mathbf r)\,dm = \mathbf I\boldsymbol\omega,\qquad \mathbf I = \begin{pmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{pmatrix}
$$

$$
I_{xx}=\int(y^2+z^2)dm,\quad I_{yy}=\int(x^2+z^2)dm,\quad I_{zz}=\int(x^2+y^2)dm,\quad I_{xy}=\int xy\,dm,\ \text{etc.}
$$

To derive $\mathbf h = \mathbf I\boldsymbol\omega$, use the vector triple product rather than expanding two cross products. Take the position of $dm$ as $\mathbf r = (x,y,z)$ and the body rates as $\boldsymbol\omega = (p,q,r)$. The velocity of $dm$ due to rotation is $\boldsymbol\omega\times\mathbf r$, so

$$
\mathbf h = \int\mathbf r\times(\boldsymbol\omega\times\mathbf r)\,dm
$$

Apply the identity $\mathbf a\times(\mathbf b\times\mathbf c) = \mathbf b(\mathbf a\cdot\mathbf c)-\mathbf c(\mathbf a\cdot\mathbf b)$ with $\mathbf a = \mathbf c = \mathbf r$ and $\mathbf b = \boldsymbol\omega$:

$$
\mathbf h = \int\left[\boldsymbol\omega(\mathbf r\cdot\mathbf r)-\mathbf r(\mathbf r\cdot\boldsymbol\omega)\right]dm
$$

Substitute $\mathbf r\cdot\mathbf r = x^2+y^2+z^2$ and $\mathbf r\cdot\boldsymbol\omega = xp+yq+zr$. The $x$-component is

$$
h_x = \int\left[p(x^2+y^2+z^2)-x(xp+yq+zr)\right]dm
$$

$$
h_x = \int\left[p(y^2+z^2)-q\,xy-r\,xz\right]dm
$$

$$
h_x = I_{xx}p-I_{xy}q-I_{xz}r
$$

The same steps for $y$ and $z$ give

$$
h_y = -I_{xy}p+I_{yy}q-I_{yz}r,\qquad h_z = -I_{xz}p-I_{yz}q+I_{zz}r
$$

These three lines are the rows of $\mathbf I\boldsymbol\omega$, with the matrix above. It is symmetric because $I_{xy}$ appears in both the $h_x$ and $h_y$ rows.

The inertia matrix can be written in any frame, but in Earth axes its components change every time the aircraft changes attitude. In body axes the mass distribution doesn't move relative to the axes, so the components stay constant. That is the second reason for writing the equations in body axes, after the first, that sensors and pilots measure in the body frame.

This is DAP1 at work: the aircraft is treated as a rigid body with a fixed CG, which fuel sloshing and pumping violate. Concorde pumped fuel fore and aft to move its CG between subsonic and supersonic flight.

The full nonlinear equations are:

$$
X = m(\dot U+qW-rV),\qquad Y = m(\dot V+rU-pW),\qquad Z = m(\dot W+pV-qU)
$$

$$
L = I_{xx}\dot p - I_{xy}\dot q - I_{xz}\dot r + q(-I_{xz}p-I_{yz}q+I_{zz}r) - r(-I_{xy}p+I_{yy}q-I_{yz}r)
$$

All three moment equations expand the same way. In body axes $\mathbf I$ is constant, so $\dot{\mathbf h}=\mathbf I\dot{\boldsymbol\omega}$. The cross product is

$$
\boldsymbol\omega\times\mathbf h=(q\,h_z-r\,h_y)\,\mathbf i+(r\,h_x-p\,h_z)\,\mathbf j+(p\,h_y-q\,h_x)\,\mathbf k
$$

Insert $h_x$, $h_y$, $h_z$ from above:

$$
L = I_{xx}\dot p - I_{xy}\dot q - I_{xz}\dot r + q(-I_{xz}p-I_{yz}q+I_{zz}r) - r(-I_{xy}p+I_{yy}q-I_{yz}r)
$$

$$
M = -I_{xy}\dot p + I_{yy}\dot q - I_{yz}\dot r + r(I_{xx}p-I_{xy}q-I_{xz}r) - p(-I_{xz}p-I_{yz}q+I_{zz}r)
$$

$$
N = -I_{xz}\dot p - I_{yz}\dot q + I_{zz}\dot r + p(-I_{xy}p+I_{yy}q-I_{yz}r) - q(I_{xx}p-I_{xy}q-I_{xz}r)
$$

With the symmetry simplification below ($I_{xy}=I_{yz}=0$) and the brackets multiplied out, these become the standard forms in Cook, Ch. 2:

$$
L = I_{xx}\dot p - I_{xz}\dot r + (I_{zz}-I_{yy})\,qr - I_{xz}\,pq
$$

$$
M = I_{yy}\dot q + (I_{xx}-I_{zz})\,pr + I_{xz}(p^2-r^2)
$$

$$
N = I_{zz}\dot r - I_{xz}\dot p + (I_{yy}-I_{xx})\,pq + I_{xz}\,qr
$$

For $M$, for example, the bracketed terms with $I_{xy}=I_{yz}=0$ multiply out as

$$
r(I_{xx}p-I_{xz}r)-p(-I_{xz}p+I_{zz}r)=I_{xx}pr-I_{xz}r^2+I_{xz}p^2-I_{zz}pr
$$

$$
r(I_{xx}p-I_{xz}r)-p(-I_{xz}p+I_{zz}r)=(I_{xx}-I_{zz})pr+I_{xz}(p^2-r^2)
$$

The equations are coupled through the state products ($qW$, $rV$, $pr$, …) and the product-of-inertia terms ($I_{xz}\dot r$, $I_{xz}pq$, …).

### Simplifications

1. Stability axes: $x$ aligned with $U_\infty$ at trim, so the trim values are $U=U_\infty$, $V=W=0$.
2. Symmetry about the $xz$-plane: $I_{xy}=I_{yz}=0$ (only $I_{xz}\neq0$).
3. Linearisation (see [[Small Perturbation Linearisation]]): perturb about trim, $U=U_\infty+u$, $V=v$, $W=w$ with $u,v,w\ll U_\infty$ (about $\pm10\%$ in practice). Drop products of small quantities (written $=_1$).

   For example, $X = m(\dot U+qW-rV)$ becomes $\Delta X = m\dot u$.

   $=_1$ means "equal to first order": it is a first-order Taylor expansion about trim. The general route is the Jacobian, $\mathbf A = \partial\mathbf f/\partial\mathbf x$ and $\mathbf B = \partial\mathbf f/\partial\mathbf u$ evaluated at trim; dropping products of perturbations by hand gives the same result.
4. Constant mass: true over seconds for an aircraft, but not for a rocket, whose mass falls quickly as it burns propellant. A rocket model is time-varying.

Stability axes and wind axes share the body axes' origin but differ in what they follow. Stability axes are fixed at trim, with $x$ along the trim flight direction, so $V$ and $W$ are zero at trim. Wind axes follow the instantaneous relative wind, which is why a sideslip angle is needed to describe them in yawed flight; aerodynamic forces are defined in wind axes.

Only two products of inertia vanish because an aircraft has one plane of symmetry, the $xz$-plane. It isn't symmetric top to bottom, so $I_{xz}\neq0$ in general. A rocket is close to a body of revolution, with more planes of symmetry, and its equations simplify further; the aircraft is the harder case and the one treated here.

All six equations linearise the same way: substitute the perturbed velocities, then drop products of perturbations (the linearisation itself was not lectured).

*Normal force.* Start from the full equation:

$$
Z = m(\dot W+pV-qU)
$$

Substitute the perturbed velocities $U = U_\infty+u$, $V = v$, $W = w$ (stability axes, so $\dot U_\infty = 0$):

$$
Z = m\left(\dot w+pv-qU_\infty-qu\right)
$$

$pv$ and $qu$ are products of two small perturbations, so drop them ($=_1$):

$$
\Delta Z =_1 m(\dot w-qU_\infty)
$$

The term $qU_\infty$ survives because $U_\infty$ is large. Pitching at rate $q$ turns the large forward velocity, which appears as a normal acceleration in body axes.

![[amc_pullup_qU.png|760]]

> [!example] How big is $qU_\infty$?
> At $U_\infty=250$ m/s, a pitch rate of only $q=5\ °/\text{s}=0.0873$ rad/s gives $qU_\infty=21.8\ \text{m/s}^2=2.22g$. The flight path then curves with radius $R=U_\infty/q=2.86$ km. A "small" rate times a large speed is not small, which is why it is first order.

*Axial force.* Substitute into $X = m(\dot U+qW-rV)$:

$$
X = m(\dot u+qw-rv)
$$

$qw$ and $rv$ are both products of perturbations:

$$
\Delta X =_1 m\dot u
$$

*Side force.* Substitute into $Y = m(\dot V+rU-pW)$:

$$
Y = m(\dot v+rU_\infty+ru-pw)
$$

Drop $ru$ and $pw$:

$$
\Delta Y =_1 m(\dot v+rU_\infty)
$$

*Pitching moment.* In the symmetric form $M = I_{yy}\dot q + (I_{xx}-I_{zz})pr + I_{xz}(p^2-r^2)$, the trim rates are zero in steady straight flight, so $p$, $q$, $r$ are themselves perturbations. Every term after the first is second order:

$$
\Delta M =_1 I_{yy}\dot q
$$

*Yawing moment.* In $N = I_{zz}\dot r - I_{xz}\dot p + (I_{yy}-I_{xx})pq + I_{xz}qr$, drop $pq$ and $qr$:

$$
\Delta N =_1 -I_{xz}\dot p+I_{zz}\dot r
$$

*Rolling moment.* Start from the full $L$ equation above. Apply symmetry, $I_{xy} = I_{yz} = 0$:

$$
L = I_{xx}\dot p-I_{xz}\dot r+q(-I_{xz}p+I_{zz}r)-r(I_{yy}q)
$$

Every term in the last two groups is a product of two perturbation rates ($qp$, $qr$, $rq$), so drop them:

$$
\Delta L =_1 I_{xx}\dot p-I_{xz}\dot r
$$

### Linearised, decoupled equations of motion

$$
\underbrace{\begin{aligned}\Delta X &= m\dot u\\ \Delta Z &= m(\dot w-qU_\infty)\\ \Delta M &= I_{yy}\dot q\end{aligned}}_{\text{longitudinal: }u,\ w,\ q}\qquad\qquad \underbrace{\begin{aligned}\Delta Y &= m(\dot v+rU_\infty)\\ \Delta L &= I_{xx}\dot p-I_{xz}\dot r\\ \Delta N &= -I_{xz}\dot p+I_{zz}\dot r\end{aligned}}_{\text{lateral: }v,\ p,\ r}
$$

This is DAP3 in action: two independent three-equation systems. The out-of-balance forces and moment $\Delta X$, $\Delta Z$, $\Delta M$ of the longitudinal set are modelled in [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]].

The trim point is an equilibrium, $\dot{\bar{\mathbf x}} = 0 = f(\bar{\mathbf x},\bar{\mathbf u})$, the same trim concept as in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]].

## Exam scope and intuition

- The three DAPs are not examined. They are a way of working used all module.
- The body-axis EOM derivation is not examined.
- The full nonlinear moment equations and their linearisation are not examined.
- Recommended reading: Cook, *Flight Dynamics Principles*, chapters 2 and 4.

> [!tip] Intuition
> - Every model is wrong, so note the assumption. The lift curve is linear only while the flow is attached, so a linear lift model is useful but never exact.
> - The body axes are always accelerating, so Newton's laws do not hold in them directly. Newton's laws are applied in the Earth frame, and the $\boldsymbol\omega\times$ terms carry them into the body frame.
> - The body frame is used because sensors and pilots measure in it, so body-frame quantities are the most direct ones to control. Spacecraft often use Earth axes instead, because they point at targets on Earth.
> - Gimbal lock is a property of the maths, not the aircraft. Fighters and spacecraft use quaternions for this reason.
> - Rotation matrices preserve length. Each entry is a sine or cosine, so they change only a vector's components, never its magnitude. A quick check on any matrix you write down: set the angle to zero and you must get $\mathbf I$.
> - An airliner spends more than 80 % of its time in longitudinal flight and its turns are coordinated, so the longitudinal equations cover most of its motion.
> - Coupling needs both motions. The $qW$, $rV$ terms vanish if either the translation or the rotation is zero.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| body axes / body reference frame ($x$ forward, $y$ starboard, $z$ down) | FRD (Forward-Right-Down) coordinates, body-fixed axes | L1.02 slides 5–7 | SESA3047 calls the same axes FRD and separates *frame* from *coordinate system* ([[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]) |
| Earth reference frame (E) | inertial frame, NED (North-East-Down) axes, Earth axes | L1.02 slides 5, 8 | flat Earth, so treated as inertial |
| Tait–Bryan angles: yaw $\psi$, pitch $\theta$, roll $\phi$ | Euler angles, 3-2-1 (z-y-x) sequence, heading/elevation/bank | L1.02 slides 8–9 | strictly, "Euler angles" repeat an axis (z-x-z); aerospace uses the name loosely |
| rotation matrix $\mathbf R_{BE}$ | direction cosine matrix (DCM), $\mathbf C_{b/n}$, transformation matrix | L1.02 slide 8 | SESA3047 writes the DCM with frame subscripts ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]) |
| $(U,V,W)$, $(p,q,r)$ | axial/lateral/normal velocity; roll/pitch/yaw rate | L1.02 slide 6 table | Cook's notation. Here $q$ is pitch rate, not dynamic pressure |
| $(X,Y,Z)$, $(L,M,N)$ | axial/side/normal force; rolling/pitching/yawing moment | L1.02 slide 6 table | $L$ here is rolling moment, not lift |
| inertia matrix (tensor) $\mathbf I$ | inertia tensor, moment-of-inertia matrix | L1.03 slides 6–7 | |
| products of inertia $I_{xy}$, $I_{xz}$, $I_{yz}$ | cross products of inertia | L1.03 slide 6 | the matrix carries minus signs on them with this definition |
| state products ($qW$, $rV$, …) | inertial coupling terms, kinematic coupling, Coriolis-type terms | L1.03 slide 11 | |
| stability axes | — (a body-fixed frame aligned with $U_\infty$ at trim) | L1.03 slide 12 | equal to wind axes in symmetric flight only |
| $=_1$ (first-order approximation) | linearisation, small-perturbation theory | L1.03 slides 15–16 | |
| equilibrium point | trim point, trim condition, operating point | L1.03 slide 14 | "introduced in SESA2022 as trim point" |
| DAP1–3 | Box's maxim, Occam's razor (parsimony), divide and conquer | L1.01 | course-specific labels |

## Links
- Parent: [[SESA2027 Aerospace Mechanics & Control Hub]] · Next: [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]
- Concepts: [[Design and Analysis Principles]] · [[Euler Angles and Rotation Matrices]] · [[Small Perturbation Linearisation]] · [[State-Space Representation]]
- Maths: vector cross products and ODEs (MATH2048)
- Year 3: the same equations with frame notation in [[SESA3047 3.3 - Rigid-Body Rotational Dynamics]] and [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]; hub: [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]]

## Year 1 foundation
- $\sum F = ma$ in an inertial frame ([[FEEG1002 D1 - Linear Motion of Particles]], [[FEEG1002 D2 - Curvilinear Motion]]), rigid-body kinematics with $\boldsymbol\omega\times\mathbf r$ ([[FEEG1002 D7 - Kinematics of Rigid Bodies]]) and $\sum M_G = I_G\alpha$ ([[FEEG1002 D8 - Kinetics of Rigid Bodies]]). They carry over into the rotating body frame of §2.

## Sources
- Lectures 1.01–1.03 (Dr S. Araujo-Estrada): slides `Lecture 1.01.pdf`–`Lecture 1.03.pdf`
- Transcripts (speech-to-text, 2025/26 delivery): `Lecture 1.01 recording.txt`, `Lecture 1.02 recording.txt`, `Lecture 1.03 recording.txt`
- Cook, *Flight Dynamics Principles* (3rd ed.), Ch. 2 and 4.1–4.3
- Figures: `01 - Notes/Figures/generate_amc_a1_figures.py`

## Self-study tasks

No tasks were set in L1.01–L1.03. Derivation notes were promised for interested students (L1.03, ll. 199–200, 326), and Cook Ch. 2 and 4 were recommended (L1.02, ll. 608–609). Every task below is suggested, not lecturer-set. The derivations are not examined, so the Core list focuses on what can be asked: axes, signs, rotations and which terms survive.

### Core

- [ ] Sketch the three views of the body axes from memory, with the positive senses of $p$, $q$, $r$. → [[#Body axes and notation]]
- [ ] Multiply out $\mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi)$ and check that it reduces to $\mathbf I$ when all angles are zero. → [[#Euler angles and rotation matrices]]
- [ ] Find $\mathbf g_B$ and $\mathbf v_B$ for the attitude in the worked example, closed-book. → [[#Worked example: gravity and velocity in body axes]]
- [ ] Linearise all six equations and say why $qU_\infty$ and $rU_\infty$ survive. → [[#Simplifications]]
- [ ] Mock exam question. → [[SESA2027 Mock Questions#Q1. Body axes, rotation and linearisation|Mock Q1]]

### Further practice

- [ ] Derive $d\mathbf j/dt$ and $d\mathbf k/dt$ by the geometric argument, then confirm $d\mathbf v/dt=\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v$. → [[#Rates of change in a rotating frame]]
- [ ] Derive $h_y$, $h_z$ and the full $M$ and $N$ equations. → [[#3. Inertia tensor and full equations]]
- [ ] Redo the A380 reality check for a 60 s interval. Which assumption fails first? → [[#Worked example: when do the assumptions start to bite?]]

## Transcript and slide slips

### Transcript slips

> [!warning] Speech-to-text and spoken slips, with the correct version
> | Where | Transcript says | Correct |
> |---|---|---|
> | L1.01, l. 64; l. 164 | "CISA 1015, CISA 2022", "CESAT 2022" | SESA1015, SESA2022 |
> | L1.01, l. 100 | "John's Multiplane" | Johns Multiplane (slide 5) |
> | L1.01, l. 101 | "Vickers Beaming" | Vickers Vimy |
> | L1.01, l. 318 | "agent values and agent vectors, … dumping" | eigenvalues and eigenvectors, damping |
> | L1.01, l. 324 | "ghost perturbation" | gust perturbation |
> | L1.01, l. 331 | "overshot, … setting time, … body plots" | overshoot, settling time, Bode plots (the same slips recur in every Part A/B transcript) |
> | L1.02, ll. 128–131 | drop of "315 meters", "12.6 percent" | 0.315 m and 0.0126 % (corrected in the lecture and on the slide) |
> | L1.02, l. 100 | "2.3.2 liters per second" | 3.61 L/s from 13 000 L/h (slide: ~3.2 L/s) |
> | L1.02, ll. 178, 375, 530 | "Tate Bryant", "tape-ray and", "tape rayon" | Tait–Bryan |
> | L1.02, l. 237 | third translation "on the x-axis" | on the $z$-axis |
> | L1.02, l. 317 | $r$ is "the rotational rate around the x-axis" | around the $z$-axis |
> | L1.02, l. 324; l. 335 | "jogging moment", "young moment" | yawing moment $N$ |
> | L1.02, l. 365 | "the convention is to do the aircraft first" | yaw first: yaw, then pitch, then roll (ll. 369–371) |
> | L1.02, ll. 380–389 | "subscript b e", "air axis" | $\mathbf v_E$, Earth axes |
> | L1.03, l. 32 | "three for rotational motion, three for rotational motion" | three translational and three rotational (self-corrected, l. 33) |
> | L1.03, l. 103 | $j$ component "minus a1b3 minus a3b1" | $-(a_1b_3-a_3b_1)$ |
> | L1.03, ll. 109–110 | "a cross b cross c … equal to c cross b cross a" | $\mathbf a\times(\mathbf b\times\mathbf c) = \mathbf b(\mathbf a\cdot\mathbf c)-\mathbf c(\mathbf a\cdot\mathbf b)$, as used at l. 117 |
> | L1.03, l. 193 | "the only way that coupling happens is if one of those quantities is zero" | the coupling disappears if one of them is zero |
> | L1.03, ll. 237–238 | stability axes "align themselves immediately" when the aircraft yaws | stability axes are fixed in the body at trim and stay body-fixed during the perturbed motion (slide 12); it is the wind axes that follow the relative wind |
> | L1.03, l. 301 | "n times u dot" | $m\dot u$ |
> | L1.03, l. 324 | "i x x times p dot minus i x x times r dot" | $I_{xx}\dot p-I_{xz}\dot r$ |
> | L1.03, l. 372 | "Math 2048" | MATH2048 |

> [!warning] Transcript slip: the Earth-curvature number (L1.02, ll. 128–161)
> Where: [[#2. Setting up the 6-DoF model]].
>
> The drop was first given as "315 meters", "12.6 percent" of the distance in 10 s (ll. 128–131), then corrected (ll. 135–161): $12.6\ \text{cm/km}\times2.5\ \text{km}$ is only about 0.3 m. The filed slide 3 already shows the corrected values, $\Delta y\approx0.315$ m and $\Delta y/d\approx0.0126\%$. The table in §2 uses the geometric drop instead, 0.50 m and $0.020\%$ (see the slide slip below).

### Slide slips

> [!warning] Slide 3: the A380 reality-check numbers
> Where: [[#2. Setting up the 6-DoF model]].
>
> The slide prints a fuel flow of "~3.2 L/s", a mass flow of 2.5 kg/s and 25 kg burnt in 10 s (0.004 % of MTOW); from 13 000 L/h the values are 3.61 L/s, 2.89 kg/s and 28.9 kg (0.005 %). It also treats the curvature drop as a fixed 12.6 cm per km, which gives 0.315 m in 10 s; the drop grows with the square of the distance and is 0.50 m over 2.53 km. The conclusions do not change.
