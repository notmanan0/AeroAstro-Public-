---
title: "FEEG1002 D7 - Kinematics of Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 7
tags: [feeg1002, dynamics, rigid-body, kinematics, instantaneous-centre, rolling, mechanisms]
aliases: ["Dynamics Lecture 7", "Rigid body kinematics", "Planar motion", "Relative velocity", "Instantaneous centre"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 7 (slides pp. 1-48): types of planar motion, translation, rotation about a fixed axis, absolute motion analysis (rolling without slip, cam and platform), relative velocity analysis with the relative velocity equation, the instantaneous centre of rotation, the gear-and-pulley and sliding-bar examples. Section 7.4, relative acceleration (slides pp. 45-47), was declared optional and not assessed and is summarised briefly. Live lectures L17b (26 Mar 2025) and L18b (27 Mar 2025, ll. 1-255); pre-recorded DAMS7-1 to DAMS7-4."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
next_topics: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
key_concepts: ["[[Relative Velocity Equation for Rigid Bodies]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 07 - Kinematics of Rigid Bodies.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-26.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-27.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS-7-RigidBodiesKinematics_1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS-7-RigidBodiesKinematics_1b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_2b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_3.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_3b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_4.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 07 - Kinematics of Rigid Bodies.pdf"]
---

# FEEG1002 D7 - Kinematics of Rigid Bodies

> [!abstract] Summary
> A rigid body moving in a plane has three degrees of freedom, two translations and one rotation, and every line on it turns with the same angular velocity $\omega$ and angular acceleration $\alpha$. A point at distance $r$ from a fixed axis moves at $v=\omega r$ with $a_t=\alpha r$ and $a_n=\omega^2r$. For general plane motion, the velocity of any point B follows from that of another point A by the relative velocity equation $\mathbf v_B=\mathbf v_A+\boldsymbol\omega\times\mathbf r_{B/A}$, and at any instant there is a point, the instantaneous centre of rotation, about which the body is momentarily in pure rotation. Alternatively, an absolute motion analysis writes a geometric relation between a position and an angle and differentiates it; a wheel rolling without slip has $s_G=r\theta$, $v_G=r\omega$, $a_G=r\alpha$.

> [!summary]- Exam use: quick path
> - **Use it when:** you need velocities (or accelerations) of points on linkages, wheels, cams, sliding bars or gears, or the angular velocity of a member.
> - **Assumptions:** planar motion; rigid body; counter-clockwise positive with $\mathbf k$ out of the page; translating (non-rotating) reference frames; rolling means rolling without slip.
> - **Method:** 1. Classify each body's motion: translation, rotation about a fixed axis, or general plane motion. 2. For a single coordinate relation (cam, rolling, hydraulic cylinder), write the geometry $s=f(\theta)$ and differentiate with the chain rule. 3. Otherwise pick two points A and B with known directions of motion and write $\mathbf v_B=\mathbf v_A+\omega\mathbf k\times\mathbf r_{B/A}$ in $\mathbf i$, $\mathbf j$ components. 4. Or find the IC from the perpendiculars to two known velocity directions and use $v=\omega r_{P/IC}$. 5. Check directions against a sketch.
> - **Common mistakes:** applying $v=\omega r$ to any point of a rolling wheel measured from its centre (it holds only for the centre, measured from the contact point); treating the IC as a fixed pivot when finding accelerations.
> - **Practise:** [[#Sliding bar between wall and floor]] · [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]] (Q5 crank and connecting rod)

A particle has no size, and only its centre of mass moves. Two identical rods pivoted at one end, one with a mass attached part-way along, do not fall together when released, although gravity accelerates every particle equally; the difference lies in how the mass is distributed about the pivot. To deal with that, bodies need size, and their rotation needs describing, which is kinematics (how rigid bodies move); [[FEEG1002 D8 - Kinetics of Rigid Bodies|D8]] adds the forces.

A rigid body cannot stretch, so the distance between any two of its points is fixed. That single constraint means the motion of the whole body is known once the motion of one point and the rotation are known. The relative velocity equation is the statement of this: seen by an observer moving with point A without rotating, every other point B goes round A on a circle, so its velocity relative to A is $\omega$ times its distance from A, at right angles to AB.

---

## 1. Types of planar motion

A rigid body in a plane has three degrees of freedom: two translations and one rotation. Its motion falls into one of three types (slides pp. 6–9). In **translation**, every line segment on the body stays parallel to its original direction. If the points move on straight lines it is rectilinear translation; on curves, curvilinear translation. The equations are the same for both. In **rotation about a fixed axis**, every particle off the axis moves on a circle in a plane perpendicular to the axis; the axis need not pass through the body's centre. **General plane motion** is translation plus rotation, the rotation being about an axis perpendicular to the plane.

A crank-slider mechanism (an engine's piston and crankshaft) has all three: the crank rotates about a fixed axis, the piston translates in a straight line and the connecting rod is in general plane motion.

### Translation

Let A and B be two points on the body, with absolute positions $\mathbf r_A$ and $\mathbf r_B$ from a fixed origin and relative position $\mathbf r_{B/A}$:

$$
\mathbf r_B=\mathbf r_A+\mathbf r_{B/A}
$$

In translation $\mathbf r_{B/A}$ has constant length (the body is rigid) and constant direction (no rotation), so $d\mathbf r_{B/A}/dt=\mathbf 0$ and

$$
\mathbf v_B=\mathbf v_A,\qquad\mathbf a_B=\mathbf a_A
$$

Every point of a translating body has the same velocity and acceleration, so the body can be treated as a particle.

## 2. Rotation about a fixed axis

### Angular quantities

The angular position $\theta$ of a line in the body is measured from a fixed reference; an angular displacement $d\theta$ is a vector perpendicular to the plane of motion, directed by the right-hand rule (fingers curled in the sense of rotation, thumb along the vector). Counter-clockwise is taken as positive, so a counter-clockwise rotation points out of the page.

The **angular velocity** and **angular acceleration** are

$$
\omega=\frac{d\theta}{dt}=\dot\theta\ \ (\mathrm{rad/s}),\qquad\alpha=\frac{d\omega}{dt}=\dot\omega=\ddot\theta\ \ (\mathrm{rad/s^2})
$$

and, by the chain rule exactly as for $a=v\,dv/ds$ in [[FEEG1002 D1 - Linear Motion of Particles#1. Position, velocity and acceleration|D1]],

$$
\alpha=\frac{d\omega}{d\theta}\frac{d\theta}{dt}=\omega\frac{d\omega}{d\theta}
$$

The vector $\boldsymbol\alpha$ acts along the same line as $\boldsymbol\omega$; it points the same way if the rotation is speeding up and the opposite way if it is slowing down. Every line on a rigid body rotates through the same angle, so a body has one $\omega$ and one $\alpha$, not one per point. For constant $\alpha=\alpha_C$, the constant-acceleration equations of [[FEEG1002 D2 - Curvilinear Motion#Circular paths|D2]] apply:

$$
\omega=\omega_0+\alpha_Ct,\qquad\theta=\theta_0+\omega_0t+\tfrac12\alpha_Ct^2,\qquad\omega^2=\omega_0^2+2\alpha_C(\theta-\theta_0)
$$

A pivoted rod falling under gravity does not have constant $\alpha$: gravity stays vertical while the rod turns, so its moment changes.

### Velocity of a point

A point P at perpendicular distance $r$ from the axis moves on a circle. As the body turns through $d\theta$, P moves through an arc $ds=r\,d\theta$, so

$$
v=\frac{ds}{dt}=r\frac{d\theta}{dt}=\omega r
$$

tangent to P's circle. In vector form, with $\mathbf r_P$ from any point on the axis to P,

$$
\mathbf v=\boldsymbol\omega\times\mathbf r_P
$$

The magnitude is $\omega r_P\sin\phi=\omega r$, since $r_P\sin\phi$ is the perpendicular distance from the axis, and the direction by the right-hand rule (thumb along $\boldsymbol\omega$, index finger along $\mathbf r$, middle finger along $\mathbf v$) is tangent to the circle. In plane problems with $\boldsymbol\omega=\omega\mathbf k$ and $\mathbf r$ in the plane, $\mathbf v=\omega\mathbf k\times\mathbf r$ is $\mathbf r$ turned 90° counter-clockwise and scaled by $\omega$. $v=\omega r$ is the result to remember.

### Acceleration of a point

From [[FEEG1002 D2 - Curvilinear Motion#Circular paths|D2]], a point on a circle of radius $r$ has

$$
a_t=\alpha r,\qquad a_n=\omega^2r
$$

the tangential part changing the size of the velocity and the normal part, towards the axis, changing its direction; $a_n=v^2/r=(\omega r)^2/r$ is present even when $\alpha=0$. In vector form, differentiate $\mathbf v=\boldsymbol\omega\times\mathbf r_P$ with the product rule:

$$
\mathbf a=\frac{d\boldsymbol\omega}{dt}\times\mathbf r_P+\boldsymbol\omega\times\frac{d\mathbf r_P}{dt}=\boldsymbol\alpha\times\mathbf r_P+\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r_P)
$$

In plane motion, $\boldsymbol\omega=\omega\mathbf k$ and $\mathbf r$ lies in the plane, and $\mathbf k\times(\mathbf k\times\mathbf r)=-\mathbf r$ (two quarter turns), so

$$
\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)=\omega^2\,\mathbf k\times(\mathbf k\times\mathbf r)=-\omega^2\mathbf r
$$

$$
\mathbf a=\boldsymbol\alpha\times\mathbf r-\omega^2\mathbf r=\mathbf a_t+\mathbf a_n
$$

with magnitude $a=\sqrt{a_t^2+a_n^2}$. The vector derivation need not be memorised (L17b, ll. 305–310); the scalar results must be.

## 3. Absolute motion analysis

Many mechanisms have one degree of freedom: a geometric constraint ties the position $s$ of a point to the rotation $\theta$ of a line in the body. The method (slide p. 26) is:

1. Choose the angle $\theta$ of a line fixed in the body and the coordinate $s$ of a point.
2. Relate them through the geometry of the constraints.
3. Differentiate with respect to time, using the chain rule, e.g. $\frac{d}{dt}\sin\theta=\cos\theta\,\dot\theta=\omega\cos\theta$ and $\frac{d}{dt}s^2=2s\dot s$.

Terms such as $\sin\theta$ make these problems nonlinear. The same approach works for bodies that only rotate (a hydraulic cylinder opening a window, Tutorial 7 Q4), since pure rotation is a special case of general plane motion.

### Rolling without slip

A wheel of radius $r$ rolls along a flat surface without slipping. Its centre G moves on a straight line. Because nothing slips, the arc of the rim that has touched the ground equals the distance the centre has moved:

$$
s_G=r\theta
$$

Differentiating once and twice,

$$
v_G=r\dot\theta=r\omega,\qquad a_G=r\ddot\theta=r\alpha
$$

valid only for rolling without slip. These look like the pure-rotation formulas but describe something different: the centre is moving, and the relations link the centre's motion to $\omega$ and $\alpha$ only. Other points of the wheel do not obey them.

## 4. Relative velocity analysis

### The relative velocity equation

Let A and B be two points on a rigid body in general plane motion, and attach to A a frame $x'$-$y'$ that translates with A but does not rotate. In a time $dt$ the body's movement can be split into a translation, in which every point moves by $d\mathbf r_A$, and a rotation about A through $d\theta$, in which B moves by $d\mathbf r_{B/A}$ (slide p. 34):

$$
d\mathbf r_B=d\mathbf r_A+d\mathbf r_{B/A}
$$

To the translating observer at A, B keeps a fixed distance $r_{B/A}$ (the body is rigid), so B can only go round A on a circle: its motion relative to A is pure rotation with the body's angular velocity. By section 2, that relative velocity is

$$
\mathbf v_{B/A}=\frac{d\mathbf r_{B/A}}{dt}=\boldsymbol\omega\times\mathbf r_{B/A},\qquad v_{B/A}=\omega r_{B/A}
$$

Dividing the displacement equation by $dt$:

$$
\boxed{\mathbf v_B=\mathbf v_A+\boldsymbol\omega\times\mathbf r_{B/A}}
$$

the **relative velocity equation**, with $\boldsymbol\omega=\omega\mathbf k$ in plane motion. The first term is the contribution of translation and the second that of rotation. It is a vector equation, so it gives two scalar equations ($\mathbf i$ and $\mathbf j$) and can be solved for two unknowns; alternatively the three vectors form a closed triangle solvable by trigonometry. The cross product can be evaluated as a determinant,

$$
\omega\mathbf k\times\mathbf r_{B/A}=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\0&0&\omega\\r_x&r_y&0\end{vmatrix}=-\omega r_y\,\mathbf i+\omega r_x\,\mathbf j
$$

or by the right-hand rule.

A and B should be points whose motion is partly known, usually pins in a linkage. Each velocity is tangent to its point's path, so its direction comes from the constraints: horizontal for a slider on a horizontal guide, tangent to the circle for the pin of a crank.

### Rolling wheel by relative velocity

For a wheel of radius $r$ rolling without slip, the contact point A has momentarily zero velocity: it must move with the ground it touches. Taking A as the reference point with $\mathbf v_A=\mathbf 0$, the centre B at $\mathbf r_{B/A}=r\mathbf j$ has, for a clockwise $\omega$ ($\boldsymbol\omega=-\omega\mathbf k$),

$$
\mathbf v_B=\mathbf 0+(-\omega\mathbf k)\times r\mathbf j=\omega r\,\mathbf i
$$

the rolling result. Any other point P has $\mathbf v_P=\boldsymbol\omega\times\mathbf r_{P/A}$, perpendicular to the line from A to P with magnitude $\omega r_{P/A}$. The top point C, at $2r$ from A, moves forward at $2\omega r$: the top of a bicycle wheel moves at twice the bicycle's speed. A point P at the 9 o'clock position has $\mathbf r_{P/A}=-r\mathbf i+r\mathbf j$ and

$$
\mathbf v_P=(-\omega\mathbf k)\times(-r\mathbf i+r\mathbf j)=\omega r\,\mathbf i+\omega r\,\mathbf j
$$

of magnitude $\sqrt2\,\omega r$ at 45°.

![[d_t7_q3_rolling_wheel.png|900]]

A rim point traces a cycloid; its velocity is tangent to that path and falls to zero each time the point touches the ground. Its acceleration there is not zero: relative to the centre it is $r\omega^2$ towards the centre, and the centre's acceleration $r\alpha$ is cancelled at the contact point by the tangential term, leaving $r\omega^2$ upwards.

### Instantaneous centre of rotation

The contact point of a rolling wheel is a special case of a general fact: at any instant a body in plane motion with non-zero angular velocity has a point with zero velocity, the **instantaneous centre of rotation** (IC), also called the instantaneous centre of zero velocity. Taking it as the reference point in the relative velocity equation,

$$
\mathbf v_P=\boldsymbol\omega\times\mathbf r_{P/IC},\qquad v_P=\omega r_{P/IC}
$$

so at that instant the body moves as if in pure rotation about the IC, every point moving perpendicular to its line from the IC.

To locate it, take two points whose velocities are not parallel and whose lines of action are known (usually from the constraints). The velocity of each is perpendicular to its line to the IC, so the IC lies on the perpendicular to each velocity through its point; it is where the two perpendiculars meet. The IC is only instantaneous: it moves as the body moves, which is why it gives velocities but must not be used as a pivot for accelerations.

![[d_sliding_rod_ic.png|900]]

## 5. Relative acceleration analysis

Section 7.4 is optional and not assessed (L18b, ll. 228–237; DAMS7-4, ll. 3–9); accelerations in this module are found by absolute motion analysis instead. Differentiating the relative velocity equation with the product rule gives, in plane motion,

$$
\frac{d}{dt}(\boldsymbol\omega\times\mathbf r_{B/A})=\boldsymbol\alpha\times\mathbf r_{B/A}+\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r_{B/A})
$$

$$
\mathbf a_B=\mathbf a_A+\boldsymbol\alpha\times\mathbf r_{B/A}-\omega^2\mathbf r_{B/A}
$$

with a tangential relative part of magnitude $\alpha r_{B/A}$ and a normal (centripetal) part $\omega^2r_{B/A}$ directed from B towards A.

---

## Worked examples

### Gears driving a hoist

Gear A ($r_A=75$ mm) starts from rest with a clockwise angular acceleration of 4.5 rad/s² and meshes with gear B ($r_B=225$ mm). Pulley D ($r_D=125$ mm) is fixed to gear B, and a cord wound round D carries cylinder C. Find C's acceleration, and its speed and the distance it rises in 3 s (slides pp. 20–23; DAMS7-1b).

At the meshing point the gear teeth do not slip, so the two contact points share their speed and their tangential acceleration (their normal accelerations differ, as the radii differ):

$$
\alpha_Ar_A=\alpha_Br_B
$$

$$
\alpha_B=\frac{4.5\times75}{225}=1.5\ \mathrm{rad/s^2}
$$

counter-clockwise. D turns with B, so $\alpha_D=1.5$ rad/s². The cord is inextensible and does not slip, so C has the tangential acceleration of the point P′ where the cord leaves D:

$$
a_C=\alpha_Dr_D=1.5\times0.125=0.1875\ \mathrm{m/s^2}
$$

upwards. The acceleration is constant, so from rest

$$
v_C=a_Ct=0.1875\times3=0.563\ \mathrm{m/s},\qquad s_C=\tfrac12a_Ct^2=\tfrac12\times0.1875\times9=0.844\ \mathrm m
$$

### Cam and platform

A circular cam of radius $r$, pinned at a point O on its rim, rotates at constant $\omega$ and lifts a platform P that moves in vertical guides. With $\theta$ the angle from the horizontal through O to the line from O to the cam's centre, find the platform's velocity and acceleration (slides pp. 31–32; DAMS7-2b; L17b, ll. 450–496).

The platform rests on the top of the cam, a radius $r$ above the cam's centre, which is itself $r\sin\theta$ above O. So, measuring $y$ from O,

$$
y=r+r\sin\theta
$$

which ranges from 0 to $2r$. Differentiating, with $r$ constant ($\dot r=0$):

$$
v_P=\dot y=r\cos\theta\,\dot\theta=r\omega\cos\theta
$$

$$
a_P=\dot v_P=r\dot\omega\cos\theta-r\omega\sin\theta\,\dot\theta=r\alpha\cos\theta-r\omega^2\sin\theta
$$

and with constant $\omega$ ($\alpha=0$), $a_P=-r\omega^2\sin\theta$.

![[d_cam_platform.png|900]]

The platform moves fastest when $\theta=0$ or 180°, half-way up, and its acceleration is greatest at the top and bottom of its travel. In [[FEEG1002 D8 - Kinetics of Rigid Bodies|D8]] this kinematics feeds the single equation of motion of a cam driven by a torque (Tutorial 8 Q2).

### Sliding bar between wall and floor

A 1.5 m bar AB slides with end A on the floor and end B on a wall. At the instant when the bar makes 30° with the floor, A moves away from the wall at 3 m/s. Find the bar's angular velocity and the velocity of B, by relative velocity and by the IC (slides pp. 41–44; DAMS7-3b).

Take $x$ along the floor away from the wall, $y$ up the wall and $\boldsymbol\omega=\omega\mathbf k$. A moves horizontally and B vertically. From A to B,

$$
\mathbf r_{B/A}=-1.5\cos30°\,\mathbf i+1.5\sin30°\,\mathbf j
$$

$$
\omega\mathbf k\times\mathbf r_{B/A}=-1.5\omega\sin30°\,\mathbf i-1.5\omega\cos30°\,\mathbf j
$$

The relative velocity equation, $v_B\mathbf j=3\,\mathbf i+\omega\mathbf k\times\mathbf r_{B/A}$, in components:

$$
\mathbf i:\ 0=3-1.5\omega\sin30°\quad\Rightarrow\quad\omega=4\ \mathrm{rad/s}
$$

$$
\mathbf j:\ v_B=-1.5\times4\cos30°=-5.20\ \mathrm{m/s}
$$

$\omega$ is positive, so the bar turns counter-clockwise, and B moves down the wall at 5.20 m/s.

By the IC: the velocity of A is horizontal, so the IC lies on the vertical through A; that of B is vertical, so the IC lies on the horizontal through B. They meet at the corner of the rectangle with the bar as diagonal, at distances

$$
r_{A/IC}=1.5\sin30°=0.75\ \mathrm m,\qquad r_{B/IC}=1.5\cos30°=1.299\ \mathrm m
$$

$$
\omega=\frac{v_A}{r_{A/IC}}=\frac{3}{0.75}=4\ \mathrm{rad/s},\qquad v_B=\omega r_{B/IC}=4\times1.299=5.20\ \mathrm{m/s}
$$

The same answer follows from absolute motion: with $\beta=180°-\theta$, $x_A=-L\cos\beta$ and $y_B=L\sin\beta$, so $\dot x_A=L\dot\beta\sin\beta$ gives $\dot\beta=4$ rad/s and $\dot y_B=L\dot\beta\cos\beta=-5.20$ m/s.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D6 - Single Degree of Freedom Vibration]] · Next: [[FEEG1002 D8 - Kinetics of Rigid Bodies]]
- Concepts: [[Relative Velocity Equation for Rigid Bodies]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Background: [[FEEG1002 D2 - Curvilinear Motion]] (circular motion and relative motion of particles)
- Used again in: [[FEEG1002 D8 - Kinetics of Rigid Bodies|D8]] (the kinematics behind every rigid-body equation of motion) · [[FEEG1002 D9 - Work and Energy for Rigid Bodies|D9]] (kinetic energy about the IC) · [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (rotating reference frames) · [[Euler Angles and Rotation Matrices]] (rotation in three dimensions)

## Sources

- `Lecture 07 - Kinematics of Rigid Bodies.pdf`: slides pp. 1–48 (7.1 planar motion pp. 4–23, 7.2 absolute motion pp. 24–32, 7.3 relative velocity pp. 33–44, 7.4 relative acceleration pp. 45–47, not assessed).
- Transcript labels used in this note:
  - L17b = `FEEG1002 Lecture 2025-03-26.txt` (26 Mar 2025): falling-rods demo (ll. 15–78), motion types, rotation, absolute motion, cam, relative velocity (ll. 92–548).
  - L18b = `FEEG1002 Lecture 2025-03-27.txt` (27 Mar 2025): rolling wheel by relative velocity (ll. 48–148), IC (ll. 149–224), section 7.4 dropped (ll. 228–237). The rest of this lecture is D8.
  - DAMS7-1, DAMS7-1b = `FEEG1002 Lecture 2021-03-06 - DAMS-7-RigidBodiesKinematics_1.txt`, `..._1b.txt`; DAMS7-2, DAMS7-2b, DAMS7-3, DAMS7-3b, DAMS7-4 = `FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_2.txt`, `..._2b.txt`, `..._3.txt`, `..._3b.txt`, `..._4.txt`.
- `Tutorial Sheet 07 - Kinematics of Rigid Bodies.pdf`: Q1–Q5, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Work through the gears example with numbers (DAMS7-1b, l. 55; L17b, ll. 315–330). Targets 0.1875 m/s², 0.563 m/s, 0.844 m. → [[#Gears driving a hoist]]
- [ ] Differentiate the cam geometry yourself for the platform's acceleration (L17b, ll. 477–480). → [[#Cam and platform]]
- [ ] Take time to digest the relative velocity idea (L17b, l. 552). → [[#The relative velocity equation]]
- [ ] Sliding bar by relative velocity, IC and absolute motion (DAMS7-3b; revision task at L18b, ll. 207–224). → [[#Sliding bar between wall and floor]]
- [ ] Tutorial 7 Q1–Q3 (rotation about a fixed axis, rolling wheel). → [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]]
- [ ] Tutorial 7 Q4, the hydraulic window by absolute motion (DAMS7-2, ll. 132–136; L17b, ll. 436–440). → [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]]
- [ ] Tutorial 7 Q5, crank and connecting rod by relative velocity (L18b, ll. 43–48). → [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]]

### Further practice

- [ ] Check with your hand that $\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)$ points to the centre (DAMS7-1, l. 273). → [[#Acceleration of a point]]
- [ ] Practise the chain rule on $\sin\theta$ and $s^2$ (DAMS7-2, l. 41). → [[#3. Absolute motion analysis]]
- [ ] Scotch-yoke past-paper question, by absolute motion (L17b, ll. 448–449; solution on Blackboard). → [[#3. Absolute motion analysis]]

## Transcript and slide slips

> [!warning] Slide slip (Lecture 07 slides, p. 44)
> Where: [[#Sliding bar between wall and floor]].
>
> The IC solution writes $\omega=v_A/r_{A/IC}=1.5\cdot4/3=4$ rad/s; $1.5\times4/3=2$. The intended working is $3/0.75=3\times4/3=4$ rad/s, and the answer is right.

### Transcript slips (L17b, L18b, DAMS7)

| Ref | Said | Correct |
|---|---|---|
| DAMS7-1, ll. 255–256 | $a_n$ is related to the change in direction of the acceleration | of the velocity |
| DAMS7-1b, l. 17 | P "is at 2.25 mm from the centre of D" | 225 mm, the radius of gear B |
| DAMS7-2, l. 166 | the Scotch yoke "could be studied by relative motion" | absolute motion (slide p. 30) |
| DAMS7-2b, l. 17 | the platform is "constrained to move horizontally" | vertically |
| DAMS7-3b, ll. 65–66 | vertical and horizontal components $-1.5\omega\sin\theta$ and $-1.5\omega\cos\theta$ | the other way round (slide p. 42) |
| DAMS7-3b, l. 82 | "VB equal VA plus omega cross VA" | $\boldsymbol\omega\times\mathbf r_{B/A}$ |
| DAMS7-4, l. 26 | the normal relative term is "omega r" in magnitude | $\omega^2r_{B/A}$ |
| L17b, l. 479 | "left with this r omega squared sine theta" | $-r\omega^2\sin\theta$ |
