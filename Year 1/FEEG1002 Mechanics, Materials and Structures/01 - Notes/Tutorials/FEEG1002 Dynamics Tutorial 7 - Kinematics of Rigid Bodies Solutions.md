---
title: "FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, rigid-body, kinematics, rolling, mechanisms]
sheet: "Dynamics Problem sheet 7 (kinematics of rigid bodies)"
theory_notes: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
key_concepts: ["[[Relative Velocity Equation for Rigid Bodies]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 07 - Kinematics of Rigid Bodies.pdf"]
---

# FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions

> [!abstract] Sheet info
> Five questions on rigid-body kinematics: a cam in fixed-axis rotation, a plate spun up from rest, a wheel rolling without slip, a window opened by a hydraulic cylinder (absolute motion analysis) and a crank and connecting rod (relative velocity). Final answers are printed on the sheet and every one is reproduced below. The only difference is in the optional Q3(d), whose printed accelerations use $\alpha=\pi$ rather than the stated 3.14 rad/s².

Throughout, counter-clockwise is positive, $\mathbf k$ points out of the page, and angles are in radians unless given in degrees.

## Q1 - Cam angular position, velocity and acceleration

The cam's angular position is $\theta=t^3-4t^2-3t+10$ (rad, $t$ in s). Find $\theta$, $\omega$ and $\alpha$ at $t=0$ and $t=2$ s, and the first positive time at which $\omega=0$.

Theory: [[FEEG1002 D7 - Kinematics of Rigid Bodies#Angular quantities]]

Every line of the cam turns through the same angle, so one $\theta(t)$ describes the whole body and $\omega$ and $\alpha$ follow by differentiating it, exactly as $v$ and $a$ follow from $s(t)$ for a particle:

$$
\omega=\frac{d\theta}{dt}=3t^2-8t-3
$$

$$
\alpha=\frac{d\omega}{dt}=6t-8
$$

At $t=0$:

$$
\theta=10\ \mathrm{rad},\qquad\omega=-3\ \mathrm{rad/s},\qquad\alpha=-8\ \mathrm{rad/s^2}
$$

At $t=2$ s:

$$
\theta=8-16-6+10=-4\ \mathrm{rad}
$$

$$
\omega=12-16-3=-7\ \mathrm{rad/s}
$$

$$
\alpha=12-8=4\ \mathrm{rad/s^2}
$$

For part (ii), set $\omega=0$ and factorise:

$$
3t^2-8t-3=0
$$

$$
(3t+1)(t-3)=0
$$

$$
t=3\ \mathrm s\quad(\text{rejecting }t=-\tfrac13\ \mathrm s)
$$

and at that instant

$$
\theta=27-36-9+10=-8\ \mathrm{rad},\qquad\alpha=18-8=10\ \mathrm{rad/s^2}
$$

$$
\boxed{t=3\ \mathrm s:\quad\theta=-8\ \mathrm{rad},\quad\alpha=10\ \mathrm{rad/s^2}}
$$

The cam starts turning clockwise ($\omega<0$) and speeds up in that sense until $\alpha$ changes sign at $t=4/3$ s; from then on $\alpha>0$ slows it, it stops at $t=3$ s, 18 rad clockwise of where it started, and then reverses. The printed answer labels the $t=2$ s values "ii)" as well as the $t=3$ s values; both $t=0$ and $t=2$ s belong to part (i).

## Q2 - Plate accelerated from rest

A circular plate starts from rest with constant angular acceleration $\alpha$. Find the total acceleration of a point B at radius $r$ from the centre A at time $t$, and its angle $\gamma$ to the line AB.

Theory: [[FEEG1002 D7 - Kinematics of Rigid Bodies#Acceleration of a point]]

B moves on a circle of radius $r$, so its acceleration has a tangential part from the change of speed and a normal part, towards A, from the change of direction. With constant $\alpha$ from rest,

$$
\omega=\alpha t
$$

$$
a_t=r\alpha\quad(\perp\text{ to AB})
$$

$$
a_n=r\omega^2=r\alpha^2t^2\quad(\text{along BA, towards A})
$$

The two parts are perpendicular, so

$$
a=\sqrt{a_t^2+a_n^2}=\sqrt{r^2\alpha^2+r^2\alpha^4t^4}
$$

$$
\boxed{a=r\alpha\sqrt{1+\alpha^2t^4}}
$$

The angle to the line AB is set by the component across AB divided by the component along it:

$$
\tan\gamma=\frac{a_t}{a_n}=\frac{r\alpha}{r\alpha^2t^2}
$$

$$
\boxed{\gamma=\tan^{-1}\!\left(\frac{1}{\alpha t^2}\right)}
$$

$\alpha t^2$ is an angle in radians, so the argument is dimensionless, as it must be. At $t=0$ the acceleration is purely tangential ($\gamma=90°$); as $t$ grows, $a_n$ grows as $t^2$ while $a_t$ stays fixed, and the acceleration swings round to point almost straight at the centre.

## Q3 - Wheel rolling without slip

A wheel of radius $R=0.5$ m rolls without slipping, starting from rest with a constant clockwise $\alpha=3.14$ rad/s². A is the contact point, B the centre and P the right-hand end of the horizontal diameter. Find the velocities of A, B and P at $t=2$ s, the acceleration of B, a sketch of P's path for $0\le t\le2$ s, and (optional) the accelerations of A and P.

Theory: [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling wheel by relative velocity]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling without slip]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#5. Relative acceleration analysis]]

Take $x$ to the right (the direction of travel) and $y$ up. The rotation is clockwise, so $\boldsymbol\omega=-\omega\mathbf k$ and $\boldsymbol\alpha=-\alpha\mathbf k$. At $t=2$ s,

$$
\omega=\alpha t=3.14\times2=6.28\ \mathrm{rad/s}
$$

and the wheel has turned through

$$
\theta=\tfrac12\alpha t^2=\tfrac12\times3.14\times4=6.28\ \mathrm{rad}
$$

which is one revolution (0.003 rad short of $2\pi$ with $\alpha=3.14$; exactly $2\pi$ with $\alpha=\pi$). P is therefore back at the 3 o'clock position at $t=2$ s, which is the geometry the sheet's figure shows.

### Velocities at t = 2 s

The contact point does not slip, so it moves with the ground: $\mathbf v_A=\mathbf 0$, and A is the instantaneous centre. Every other velocity follows from the relative velocity equation with A as the reference point. For the centre, $\mathbf r_{B/A}=R\mathbf j$:

$$
\mathbf v_B=\mathbf 0+(-\omega\mathbf k)\times R\mathbf j=\omega R\,\mathbf i
$$

$$
\boxed{v_B=6.28\times0.5=3.14\ \mathrm{m/s}\ \text{to the right}}
$$

For P, $\mathbf r_{P/A}=R\mathbf i+R\mathbf j$:

$$
\mathbf v_P=(-\omega\mathbf k)\times(R\mathbf i+R\mathbf j)=-\omega R\,\mathbf j+\omega R\,\mathbf i
$$

$$
\mathbf v_P=3.14\,\mathbf i-3.14\,\mathbf j\ \mathrm{m/s}
$$

$$
\boxed{v_P=\sqrt2\,\omega R=4.44\ \mathrm{m/s},\ 45°\ \text{below the horizontal, forwards}}
$$

perpendicular to AP, as it must be for a point turning about the IC.

### Acceleration of the centre

The centre moves on a straight line at height $R$, and rolling without slip gives $x_B=R\theta$. Differentiating twice,

$$
a_B=R\ddot\theta=R\alpha=0.5\times3.14
$$

$$
\boxed{a_B=1.57\ \mathrm{m/s^2}\ \text{to the right}}
$$

with no normal component, because B's path is straight.

![[d_t7_q3_rolling_wheel.png|920]]

### Path of P

With $\phi=\tfrac12\alpha t^2$ the clockwise angle turned, the centre is at $(R\phi,R)$ and P is at $(R\cos\phi,-R\sin\phi)$ relative to it:

$$
x_P=R\phi+R\cos\phi,\qquad y_P=R-R\sin\phi
$$

This is a cycloid (the path of any rim point of a rolling wheel); the time law $\phi=\tfrac12\alpha t^2$ only sets how fast P moves along it. P starts at centre height, comes down to touch the ground at $\phi=\pi/2$, which is $t=\sqrt{\pi/\alpha}=1.0$ s, where the path has a cusp and P is momentarily at rest. It then rises to the top of the wheel at $\phi=3\pi/2$ ($t=1.73$ s) and returns to centre height at $t=2$ s, $2\pi R=3.14$ m further along. Because the wheel is accelerating, the first quarter-arc takes 1 s and the remaining three quarters only 1 s.

### Accelerations of A and P (optional)

This part needs the relative acceleration equation, which this module treats as optional. With B as the reference point,

$$
\mathbf a_X=\mathbf a_B+\boldsymbol\alpha\times\mathbf r_{X/B}-\omega^2\mathbf r_{X/B}
$$

For the contact point, $\mathbf r_{A/B}=-R\mathbf j$:

$$
\boldsymbol\alpha\times\mathbf r_{A/B}=(-\alpha\mathbf k)\times(-R\mathbf j)=-\alpha R\,\mathbf i
$$

$$
-\omega^2\mathbf r_{A/B}=\omega^2R\,\mathbf j
$$

$$
\mathbf a_A=\alpha R\,\mathbf i-\alpha R\,\mathbf i+\omega^2R\,\mathbf j=\omega^2R\,\mathbf j
$$

$$
\boxed{a_A=6.28^2\times0.5=19.72\ \mathrm{m/s^2}\ \text{straight up}}
$$

The contact point has zero velocity but not zero acceleration: the forward acceleration of the centre is cancelled exactly by the tangential term, leaving the centripetal part pointing up at the centre.

For P, $\mathbf r_{P/B}=R\mathbf i$:

$$
\boldsymbol\alpha\times\mathbf r_{P/B}=(-\alpha\mathbf k)\times R\mathbf i=-\alpha R\,\mathbf j
$$

$$
-\omega^2\mathbf r_{P/B}=-\omega^2R\,\mathbf i
$$

$$
\mathbf a_P=(\alpha R-\omega^2R)\,\mathbf i-\alpha R\,\mathbf j=(1.57-19.72)\,\mathbf i-1.57\,\mathbf j
$$

$$
\mathbf a_P=-18.15\,\mathbf i-1.57\,\mathbf j\ \mathrm{m/s^2}
$$

$$
\boxed{a_P=18.22\ \mathrm{m/s^2},\ \text{pointing back towards B and }4.9°\text{ below the horizontal}}
$$

> [!warning] Printed answers to Q3(d) use $\alpha=\pi$
> The sheet prints $a_A=19.74$ m/s² and $a_P=18.24$ m/s². These come from $\alpha=\pi$, so $\omega=2\pi$ rad/s and $\omega^2R=19.74$ m/s². With the stated $\alpha=3.14$ rad/s² the values are 19.72 and 18.22 m/s². Either reading is acceptable; the difference is rounding of $\pi$, not a different method. Parts (a) and (b) agree to the printed precision on both readings.

## Q4 - Window opened by a hydraulic cylinder

A window of length $2l$ is hinged at O; a hydraulic cylinder runs from a fixed point A, a distance $b$ below O, to a point B on the window at distance $l$ from O. With $l=1$ m, $b=2$ m and the cylinder extending at a constant $\dot s=0.5$ m/s, find $\dot\theta$ and $\ddot\theta$ when $\theta=30°$ (measured from the vertical OA), and comment on the design for $0\le\theta\le90°$.

Theory: [[FEEG1002 D7 - Kinematics of Rigid Bodies#3. Absolute motion analysis]]

The window only rotates about O, but one coordinate of the mechanism, the cylinder length $s$, is driven, so the job is to relate $s$ to $\theta$ through the geometry and differentiate. The triangle OAB has sides $OA=b$, $OB=l$ and $AB=s$, with the angle $\theta$ at O, so by the cosine rule

$$
s^2=b^2+l^2-2bl\cos\theta
$$

At $\theta=30°$,

$$
s=\sqrt{4+1-4\cos30°}=\sqrt{1.536}=1.239\ \mathrm m
$$

Differentiate with respect to time, with $b$ and $l$ constant:

$$
2s\dot s=2bl\sin\theta\,\dot\theta
$$

$$
\dot\theta=\frac{s\dot s}{bl\sin\theta}=\frac{1.239\times0.5}{2\times1\times0.5}
$$

$$
\boxed{\dot\theta=0.620\ \mathrm{rad/s}}
$$

For the angular acceleration, differentiate $s\dot s=bl\sin\theta\,\dot\theta$ once more with the product rule:

$$
\dot s^2+s\ddot s=bl\left(\cos\theta\,\dot\theta^2+\sin\theta\,\ddot\theta\right)
$$

The cylinder extends at a constant rate, so $\ddot s=0$:

$$
\ddot\theta=\frac{\dot s^2-bl\cos\theta\,\dot\theta^2}{bl\sin\theta}=\frac{0.25-2\times0.866\times0.384}{1}=\frac{0.25-0.665}{1}
$$

$$
\boxed{\ddot\theta=-0.415\ \mathrm{rad/s^2}}
$$

The window is slowing down at 30° even though the cylinder runs at constant speed, because the geometry gives the cylinder steadily more leverage as $\theta$ grows from small angles.

![[d_t7_q4_window.png|700]]

### Design comment

Twice the area of triangle OAB is $bl\sin\theta$, and it is also $s$ times the perpendicular distance $d$ from O to the line of the cylinder. That distance is the cylinder's moment arm about the hinge:

$$
d=\frac{bl\sin\theta}{s}
$$

At $\theta=0$, B lies on OA, the cylinder points straight at the hinge and $d=0$. The cylinder then has no moment about O and cannot start the window opening from the closed position, whatever force it produces; the same singularity appears as $\dot\theta=s\dot s/(bl\sin\theta)\to\infty$, so a constant $\dot s$ is impossible near $\theta=0$. The arm is only 0.17 m at 5° and 0.34 m at 10°, against 0.81 m at 30°, 1.0 m at 60° and 0.89 m at 90°, so the force needed is very large over the first few degrees. The stroke is a second problem: $s$ runs from $b-l=1$ m closed to $\sqrt{b^2+l^2}=2.24$ m at 90°, an extension of 1.24 m from a retracted length of 1 m, which a single-stage cylinder (whose stroke is shorter than its closed length) cannot provide.

A better layout moves the cylinder's base A off the line OA, to the side away from the opening, so that the cylinder has a moment arm about O when the window is closed, and chooses the attachment points so that the ratio of extended to retracted length is below about 2; a telescopic cylinder is the alternative if the geometry cannot be changed.

## Q5 - Crank, connecting rod and piston

A crank AB ($r=60$ mm) turns anticlockwise at a constant 1000 rpm and drives the piston C through a connecting rod BC ($l=160$ mm). Find the piston velocity and the rod's angular velocity for $\theta=0°$, 90° and 180°, by the relative velocity method.

Theory: [[FEEG1002 D7 - Kinematics of Rigid Bodies#The relative velocity equation]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Instantaneous centre of rotation]]

Put the origin at A with $x$ along the line of the piston towards C and $y$ up. The crank speed is

$$
\omega=1000\times\frac{2\pi}{60}=104.7\ \mathrm{rad/s}
$$

The crank rotates about A, so with $\mathbf r_B=r(\cos\theta\,\mathbf i+\sin\theta\,\mathbf j)$,

$$
\mathbf v_B=\omega\mathbf k\times\mathbf r_B=r\omega(-\sin\theta\,\mathbf i+\cos\theta\,\mathbf j),\qquad r\omega=0.06\times104.7=6.28\ \mathrm{m/s}
$$

C stays on the $x$ axis, so the rod makes an angle $\beta$ with it, where $l\sin\beta=r\sin\theta$, and

$$
\mathbf r_{C/B}=l\cos\beta\,\mathbf i-r\sin\theta\,\mathbf j
$$

The piston moves horizontally, $\mathbf v_C=v_C\mathbf i$. The relative velocity equation for the rod is

$$
v_C\mathbf i=\mathbf v_B+\omega_{CB}\mathbf k\times\mathbf r_{C/B}
$$

and with $\mathbf k\times(l\cos\beta\,\mathbf i-r\sin\theta\,\mathbf j)=l\cos\beta\,\mathbf j+r\sin\theta\,\mathbf i$ its two components are

$$
\mathbf i:\quad v_C=-r\omega\sin\theta+\omega_{CB}\,r\sin\theta
$$

$$
\mathbf j:\quad 0=r\omega\cos\theta+\omega_{CB}\,l\cos\beta
$$

so

$$
\omega_{CB}=-\frac{r\omega\cos\theta}{l\cos\beta}
$$

At $\theta=0°$, B lies on the line AC, $\beta=0$ and $\mathbf v_B=r\omega\,\mathbf j$ is vertical:

$$
\omega_{CB}=-\frac{r\omega}{l}=-\frac{6.28}{0.16}=-39.3\ \mathrm{rad/s},\qquad v_C=0
$$

$$
\boxed{\boldsymbol\omega_{CB}=-39.3\,\mathbf k\ \mathrm{rad/s},\qquad\mathbf v_C=\mathbf 0}
$$

At $\theta=90°$, B is directly above A, $\cos\theta=0$ and $\mathbf v_B=-r\omega\,\mathbf i$:

$$
\omega_{CB}=0,\qquad v_C=-r\omega
$$

$$
\boxed{\boldsymbol\omega_{CB}=\mathbf 0,\qquad\mathbf v_C=-6.28\,\mathbf i\ \mathrm{m/s}}
$$

At $\theta=180°$, B is on the line on the far side of A, $\beta=0$, $\cos\theta=-1$ and $\mathbf v_B=-r\omega\,\mathbf j$:

$$
\omega_{CB}=+\frac{r\omega}{l}=+39.3\ \mathrm{rad/s},\qquad v_C=0
$$

$$
\boxed{\boldsymbol\omega_{CB}=+39.3\,\mathbf k\ \mathrm{rad/s},\qquad\mathbf v_C=\mathbf 0}
$$

The instantaneous centre of the rod confirms all three. At 0° and 180° the perpendicular to $\mathbf v_B$ through B is the line AC itself and the perpendicular to $\mathbf v_C$ through C is the vertical through C, so the IC is C: the piston is momentarily at rest (the two dead centres) and the rod swings about it at $v_B/l=39.3$ rad/s, clockwise when B moves up and anticlockwise when B moves down. At 90° the velocities of B and C are parallel, the perpendiculars never meet, the IC is at infinity and the rod translates for an instant, so C moves with B at 6.28 m/s towards A.

![[d_t7_q5_crank_slider.png|760]]

Between the three marked angles the piston speed is not $r\omega\sin\theta$, because the rod has finite length. Substituting $\omega_{CB}$ into the $\mathbf i$ equation gives $v_C=-r\omega\sin\theta\left(1+\dfrac{r\cos\theta}{l\cos\beta}\right)$, and the speed peaks at 6.72 m/s when $\theta=71.6°$, where the crank is roughly perpendicular to the rod, not at 90°.

## Links

- Topic note: [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Concepts: [[Relative Velocity Equation for Rigid Bodies]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]]
- Hub: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Next sheet: [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]

## Sources

- `Tutorial Sheet 07 - Kinematics of Rigid Bodies.pdf` (Q1–Q5, final answers printed on the sheet).
- Q4 was set as a tutorial problem for absolute motion analysis in `FEEG1002 Lecture 2025-03-26.txt` (L17b, ll. 436–440) and `FEEG1002 Lecture 2021-03-06 - DAMS7-RigidBodiesKinematics_2.txt` (ll. 132–136).
- Q5 was pointed to as the relative velocity tutorial problem in `FEEG1002 Lecture 2025-03-27.txt` (L18b, ll. 43–48).
