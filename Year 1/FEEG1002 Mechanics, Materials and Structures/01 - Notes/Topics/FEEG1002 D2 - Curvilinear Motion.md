---
title: "FEEG1002 D2 - Curvilinear Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 2
tags: [feeg1002, dynamics, curvilinear-motion, projectiles, normal-tangential, centripetal, relative-motion]
aliases: ["Dynamics Lecture 2", "Projectile motion", "n-t coordinates", "Curvilinear motion of particles"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 2 (slides pp. 1-45): general curvilinear kinematics, rectangular components, projectiles (with a qualitative look at drag), normal and tangential coordinates, circular motion, equations of motion in n-t-b, the car-on-a-hill example. Live lectures L03 (5 Feb 2025) and L04 (6 Feb 2025); pre-recorded DAMS2-1, DAMS2-1-1, DAMS2-2, DAMS2-4 and solved examples DAMS2-Ex1, DAMS2-Ex2 (pendulum). Relative motion of particles (translating axes) comes only from the pre-recorded DAMS2-3; it is not in the 2025 slides but Tutorial 2 Q9-Q11 need it."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
next_topics: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
key_concepts: ["[[Projectile Motion]]", "[[Normal and Tangential Coordinates]]", "[[Newton's Laws of Motion]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 02 - Curvilinear Motion.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-05.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-06.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion1-1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-01-11.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion4.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion-SolvedExample1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion-SolvedExample2.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 02 - Curvilinear Motion.pdf"]
---

# FEEG1002 D2 - Curvilinear Motion

> [!abstract] Summary
> A particle moving along a curved path has a velocity that is always tangent to the path, but an acceleration that generally is not. In rectangular components the $x$ and $y$ motions are independent, which turns a projectile into two straight-line problems: constant velocity horizontally and constant acceleration $-g$ vertically. When the path is known, normal and tangential axes riding on the particle split the acceleration into $a_t=\dot v$, which changes the speed, and $a_n=v^2/\rho$ towards the centre of curvature, which changes the direction; Newton's second law then reads $\sum F_t=ma_t$, $\sum F_n=mv^2/\rho$, $\sum F_b=0$.

> [!summary]- Exam use: quick path
> - **Use it when:** a particle follows a curved path: projectiles (rectangular axes), or vehicles on hills, loops, banked curves, pendulums and circles (n-t axes).
> - **Assumptions:** particle, inertial observer at a fixed point; no air resistance for projectiles unless stated; $\theta$ in radians in $s=R\theta$.
> - **Method:** 1. Pick rectangular axes if the forces are fixed in direction (projectiles), n-t axes if the path is known. 2. Put the n-t origin on the particle, $t$ along the motion, $n$ towards the centre of curvature. 3. Draw the FBD and the kinetic diagram with $ma_t$ and $ma_n$ (always towards $+n$). 4. Write $\sum F_t=ma_t$, $\sum F_n=mv^2/\rho$ (and $\sum F_b=0$). 5. Get $\rho$ from the geometry or from $\rho=[1+(dy/dx)^2]^{3/2}/|d^2y/dx^2|$, and $v$ from $a_t\,ds=v\,dv$ if needed.
> - **Common mistakes:** including $mg$ in the FBD of a problem in the horizontal plane (top view); adding a "centrifugal force" to the FBD.
> - **Practise:** [[#Car over a parabolic hill]] · [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]] (Q5 banked curve)

On a straight path ([[FEEG1002 D1 - Linear Motion of Particles|D1]]) one coordinate is enough. On a curved path the velocity changes direction even if its magnitude does not, and changing direction needs a force just as much as changing speed does. A car rounding a bend at constant speed is accelerating towards the centre of the bend, and the friction between tyres and road supplies the force.

Two coordinate systems are used. Rectangular ($x$-$y$) axes are fixed in space and suit forces that keep a fixed direction, as gravity does for a projectile. Normal and tangential (n-t) axes move with the particle and suit problems where the path is known: they separate the part of the acceleration that changes the speed from the part that turns the velocity, and the second part, $v^2/\rho$, depends only on the speed and the curvature of the path. The observer stays at a fixed point throughout, so Newton's law is still written in an inertial frame; the moving axes only decide the directions along which vectors are resolved.

---

## 1. Position, velocity and acceleration on a curved path

The particle's position is given by the position vector $\mathbf r(t)$ from a fixed origin, whose magnitude and direction may both change. Along the path the distance travelled is the path coordinate $s$, measured from a fixed point on the path. Over a time $\Delta t$ the displacement is the vector difference $\Delta\mathbf r=\mathbf r'-\mathbf r$, while the distance travelled along the path is $\Delta s$.

The velocity is

$$
\mathbf v=\lim_{\Delta t\to0}\frac{\Delta\mathbf r}{\Delta t}=\frac{d\mathbf r}{dt}
$$

As $\Delta t\to0$ the chord $\Delta\mathbf r$ lines up with the path and its length tends to $\Delta s$, so $\mathbf v$ is tangent to the path and its magnitude, the speed, is

$$
v=\frac{ds}{dt}
$$

The velocity vector is always tangent to the path. The acceleration $\mathbf a=d\mathbf v/dt=d^2\mathbf r/dt^2$ is in general not: it points into the concave side of the path, because the velocity is turning that way.

## 2. Rectangular components

With fixed axes,

$$
\mathbf r=x\mathbf i+y\mathbf j+z\mathbf k
$$

Because $\mathbf i$, $\mathbf j$, $\mathbf k$ are constant in magnitude and direction, they come straight out of the time derivatives:

$$
\mathbf v=\dot x\mathbf i+\dot y\mathbf j+\dot z\mathbf k=v_x\mathbf i+v_y\mathbf j+v_z\mathbf k
$$

$$
\mathbf a=\ddot x\mathbf i+\ddot y\mathbf j+\ddot z\mathbf k=a_x\mathbf i+a_y\mathbf j+a_z\mathbf k
$$

The magnitudes follow from Pythagoras, e.g. $v=\sqrt{v_x^2+v_y^2+v_z^2}$, and the direction from the ratio of the components. Newton's second law gives three scalar equations (two in a plane) to be solved together:

$$
\sum F_x=ma_x,\qquad \sum F_y=ma_y,\qquad \sum F_z=ma_z
$$

Two particles collide only if they are at the same place at the same time; crossing paths is not enough. In [[#Collision of two particles]] both coordinate equations must be satisfied by the same $t$.

## 3. Projectiles

Take $x$ horizontal and $y$ vertically up, and neglect air resistance. The only force is the weight, so the FBD has $mg$ down and the kinetic diagram has $ma_x$ and $ma_y$:

$$
\sum F_x:\ 0=ma_x\quad\Rightarrow\quad a_x=0
$$

$$
\sum F_y:\ -mg=ma_y\quad\Rightarrow\quad a_y=-g
$$

The two directions are independent, and each is a constant-acceleration problem from [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration|D1]]. With launch speed $v_0$ at angle $\theta_0$ above the horizontal from $(x_0,y_0)$,

$$
v_{0x}=v_0\cos\theta_0,\qquad v_{0y}=v_0\sin\theta_0
$$

Horizontally the velocity is constant:

$$
v_x=v_{0x},\qquad x=x_0+v_{0x}t \tag{1}
$$

Vertically the acceleration is $-g$:

$$
v_y=v_{0y}-gt,\qquad y=y_0+v_{0y}t-\tfrac12gt^2 \tag{2}
$$

$$
v_y^2=v_{0y}^2-2g(y-y_0)
$$

A ball dropped and a ball thrown horizontally from the same height land at the same time, because the horizontal motion has no effect on the vertical one; a ball fired straight up from a cart moving at constant speed lands back in the cannon.

### Trajectory

Eliminate $t$ between (1) and (2). From (1), $t=(x-x_0)/(v_0\cos\theta_0)$. Substituting into (2):

$$
y=y_0+v_0\sin\theta_0\frac{x-x_0}{v_0\cos\theta_0}-\frac g2\frac{(x-x_0)^2}{v_0^2\cos^2\theta_0}
$$

$$
y=y_0+\tan\theta_0\,(x-x_0)-\frac{g}{2v_0^2\cos^2\theta_0}(x-x_0)^2
$$

a parabola.

### Time of flight and range

The time of flight $t_f$ is when the particle reaches the landing height $y_{end}$. Put $y=y_{end}$ in (2) and rearrange into a quadratic in $t$:

$$
\tfrac12gt^2-v_0\sin\theta_0\,t-(y_0-y_{end})=0
$$

$$
t=\frac{v_0\sin\theta_0\pm\sqrt{v_0^2\sin^2\theta_0+2g(y_0-y_{end})}}{g}
$$

$$
t_f=\frac{v_0\sin\theta_0}{g}+\sqrt{\frac{v_0^2\sin^2\theta_0}{g^2}+\frac2g(y_0-y_{end})}
$$

taking the positive root. The other root is the earlier time at which the same parabola passes $y_{end}$: before launch if $y_{end}$ is below the launch height, or on the way up if it is above. If the landing height equals the launch height, the square root equals $v_0\sin\theta_0/g$ and

$$
t_f=\frac{2v_0\sin\theta_0}{g}
$$

The range is the horizontal distance covered in that time, from (1):

$$
x_{end}-x_0=v_0\cos\theta_0\,t_f
$$

which for equal heights becomes

$$
x_{end}-x_0=v_0\cos\theta_0\frac{2v_0\sin\theta_0}{g}=\frac{v_0^2\sin2\theta_0}{g}
$$

using $2\sin\theta_0\cos\theta_0=\sin2\theta_0$. The range is greatest at $\theta_0=45°$, and angles symmetric about 45° give the same range.

![[d_projectile_range_angle.png|900]]

The trajectory, time of flight and range follow from equations (1) and (2) and are better derived for each problem than memorised, since the equal-height forms fail as soon as the launch and landing heights differ.

### Projectiles with drag

With drag $F_D=Cv^2$ acting along the tangent, opposite to $\mathbf v$, the equations become

$$
-Cv^2\cos\theta=ma_x,\qquad -mg-Cv^2\sin\theta=ma_y
$$

with $v\cos\theta=v_x$, $v\sin\theta=v_y$ and $v=\sqrt{v_x^2+v_y^2}$. The drag rotates with the velocity while the weight does not, so the two equations are coupled and nonlinear and have no analytical solution. They can be stepped forward numerically by holding the acceleration constant over each small time step. For a launch at 60 m/s and 60° the drag-free range is 318 m, and a realistic drag term cuts it to under 100 m; at 6 m/s the effect is negligible (DAMS2-1-1, ll. 160–169). Drag is not assessed numerically, but the qualitative effect is: the projectile slows faster, rises less and flies for a shorter time (L03, ll. 394–439).

## 4. Normal and tangential coordinates

When the path is known it is more convenient to resolve vectors along it. The n-t axes have their origin on the particle and move with it (slide p. 22). The $t$ axis is tangent to the path, positive in the direction of motion, with unit vector $\mathbf u_t$. The $n$ axis is perpendicular to it and positive towards the **centre of curvature** $O'$, with unit vector $\mathbf u_n$. $O'$ always lies on the concave side of the path. The **radius of curvature** $\rho$ is the distance from the path to $O'$; it varies along a general path, but over an infinitesimal arc $ds$ the path is part of a circle of radius $\rho$, so $ds=\rho\,d\theta$, where $d\theta$ is the angle through which the tangent turns.

![[d_nt_coordinates.png|900]]

### Velocity

The velocity is tangent to the path, so it has one component only:

$$
\mathbf v=v\,\mathbf u_t,\qquad v=\dot s
$$

### Acceleration

Differentiate with the product rule. Unlike $\mathbf i$ and $\mathbf j$, the unit vector $\mathbf u_t$ has constant magnitude but changes direction as the particle moves, so its derivative is not zero:

$$
\mathbf a=\frac{d}{dt}(v\,\mathbf u_t)=\dot v\,\mathbf u_t+v\,\dot{\mathbf u}_t
$$

To find $\dot{\mathbf u}_t$, consider an arc $ds$ travelled during $dt$. The tangent turns through $d\theta$, from $\mathbf u_t$ to $\mathbf u_t'$, and the change $d\mathbf u_t=\mathbf u_t'-\mathbf u_t$ closes a thin isosceles triangle with two sides of length 1. As $d\theta\to0$ the third side becomes perpendicular to $\mathbf u_t$ and points towards $O'$, i.e. along $\mathbf u_n$, and its length is the arc of a unit circle:

$$
|d\mathbf u_t|=1\cdot d\theta
$$

$$
d\mathbf u_t=d\theta\,\mathbf u_n
$$

Using $d\theta=ds/\rho$ and dividing by $dt$:

$$
\frac{d\mathbf u_t}{dt}=\frac1\rho\frac{ds}{dt}\,\mathbf u_n=\frac{v}{\rho}\,\mathbf u_n
$$

Substituting back,

$$
\mathbf a=\dot v\,\mathbf u_t+v\frac v\rho\,\mathbf u_n
$$

$$
\boxed{\mathbf a=a_t\mathbf u_t+a_n\mathbf u_n,\qquad a_t=\dot v,\qquad a_n=\frac{v^2}{\rho}}
$$

with magnitude $a=\sqrt{a_t^2+a_n^2}$. The **tangential** component $a_t$ changes the speed and can be positive or negative; with $a_t=dv/dt=v\,dv/ds$ it obeys the same rules as straight-line motion, including $a_t\,ds=v\,dv$. The **normal** (centripetal) component $a_n$ changes the direction of the velocity and always points towards the centre of curvature. A particle moving at constant speed on a curve has $a_t=0$ but $a_n\neq0$: constant speed is not constant velocity. The graphical argument is not assessed (L03, ll. 573–581), but the result is used in every problem.

### Radius of curvature

For a path given as $y=f(x)$, the curvature $1/\rho$ is the rate at which the tangent angle $\theta$ turns per unit arc length, $1/\rho=d\theta/ds$. The tangent angle satisfies $\tan\theta=dy/dx$. Differentiating with respect to $x$:

$$
\sec^2\theta\,\frac{d\theta}{dx}=\frac{d^2y}{dx^2}
$$

$$
\frac{d\theta}{dx}=\frac{d^2y/dx^2}{1+(dy/dx)^2}
$$

using $\sec^2\theta=1+\tan^2\theta$. The arc length element is $ds=\sqrt{dx^2+dy^2}$, so

$$
\frac{ds}{dx}=\sqrt{1+\left(\frac{dy}{dx}\right)^2}
$$

Dividing the two,

$$
\frac1\rho=\frac{d\theta}{ds}=\frac{d\theta/dx}{ds/dx}=\frac{d^2y/dx^2}{\left[1+(dy/dx)^2\right]^{3/2}}
$$

$$
\boxed{\rho=\frac{\left[1+(dy/dx)^2\right]^{3/2}}{\left|d^2y/dx^2\right|}}
$$

The modulus makes $\rho$ positive; the sign of $d^2y/dx^2$ only says which side the centre of curvature is on. Both derivatives are with respect to $x$, not time. The proof is in a calculus text (result on slide p. 28).

### The third axis

In three dimensions the binormal $b$, with unit vector $\mathbf u_b=\mathbf u_t\times\mathbf u_n$, completes the set. There is no motion along $b$, so the $b$ equation is one of equilibrium. For a car on a banked track at constant altitude, $n$ is horizontal towards the centre of the bend, $b$ is vertical and $t$ points along the track. Drawing $n$ down the slope of the bank is a common mistake: the centre of the circular path is at the car's own height.

### Circular paths

On a circle of radius $R$, $\rho=R$ is constant and the path coordinate is $s=R\theta$, with $\theta$ in radians from a fixed reference. Then

$$
\mathbf v=\dot s\,\mathbf u_t=R\dot\theta\,\mathbf u_t
$$

$$
\mathbf a=R\ddot\theta\,\mathbf u_t+\frac{(R\dot\theta)^2}{R}\mathbf u_n=R\ddot\theta\,\mathbf u_t+R\dot\theta^2\,\mathbf u_n
$$

The **angular velocity** is $\omega=\dot\theta$ (rad/s) and the **angular acceleration** $\alpha=\dot\omega=\ddot\theta$ (rad/s²), so

$$
v=R\omega,\qquad a_t=R\alpha,\qquad a_n=R\omega^2
$$

The angular quantities obey the same relations as straight-line motion, with $s\to\theta$, $v\to\omega$, $a\to\alpha$: $\omega=d\theta/dt$, $\alpha=d\omega/dt$ and $\alpha=\omega\,d\omega/d\theta$. For constant $\alpha=\alpha_c$, integrating exactly as in [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration|D1]]:

$$
\omega=\omega_0+\alpha_ct,\qquad \theta=\theta_0+\omega_0t+\tfrac12\alpha_ct^2,\qquad \omega^2=\omega_0^2+2\alpha_c(\theta-\theta_0)
$$

valid only for constant $\alpha$. A particle that turns once in 4 s at constant speed has $\omega=2\pi/4=\pi/2$ rad/s whatever the radius (L04, ll. 92–115).

## 5. Equations of motion in n-t coordinates

Newton's second law resolved along the moving axes is

$$
\sum F_t\,\mathbf u_t+\sum F_n\,\mathbf u_n+\sum F_b\,\mathbf u_b=ma_t\,\mathbf u_t+ma_n\,\mathbf u_n
$$

so

$$
\boxed{\sum F_t=ma_t,\qquad \sum F_n=m\frac{v^2}{\rho},\qquad \sum F_b=0}
$$

The normal equation says that a particle follows a curved path only if the forces on it have an unbalanced component towards the centre of curvature: the **centripetal force**. In an inertial frame there is no centrifugal force. The outward push felt in a turning car is the body's tendency to continue in a straight line, seen from a frame that is turning with the car; a fixed observer needs no such force, and it never goes on an FBD.

Whether the weight appears depends on the plane of the motion. In a problem drawn in the horizontal plane (a top view, such as a block whirled on a string on a table), the weight is perpendicular to the drawing and is balanced by the normal reaction, so $mg$ is left out of the FBD. In the vertical plane (a car over a hill, a loop, a pendulum) the weight has components along $t$ and $n$ and must be included.

The procedure:

1. Set up n-t axes on the particle, $t$ along the motion and $n$ towards $O'$.
2. Draw the FBD and the kinetic diagram; $ma_n$ always points along $+n$, while $ma_t$ may be either way.
3. Write the scalar equations.
4. Use $a_t=dv/dt=v\,dv/ds$ and $a_n=v^2/\rho$ to link them to the motion.

An unknown force such as friction can be drawn in a guessed direction; a negative answer means it acts the other way, and the diagram need not be redrawn (L04, ll. 225–231).

## 6. Relative motion of two particles

Tutorial 2 Q9–Q11 use this section (source: the pre-recorded DAMS2-3 only).

Let $A$ and $B$ be two particles with positions $\mathbf r_A$ and $\mathbf r_B$ measured from the same fixed origin. The position of $B$ relative to $A$, as seen by an observer translating with $A$ (moving with it but not rotating), is

$$
\mathbf r_{B/A}=\mathbf r_B-\mathbf r_A
$$

and the three vectors form a closed triangle, $\mathbf r_B=\mathbf r_A+\mathbf r_{B/A}$. Differentiating with respect to time, with the observer's axes not rotating:

$$
\mathbf v_B=\mathbf v_A+\mathbf v_{B/A}
$$

and again:

$$
\mathbf a_B=\mathbf a_A+\mathbf a_{B/A}
$$

Also $\mathbf v_{A/B}=-\mathbf v_{B/A}$. These vector equations can be solved by components or by trigonometry on the velocity (or acceleration) triangle, using the sine rule $a/\sin A=b/\sin B=c/\sin C$ and the cosine rule $a^2=b^2+c^2-2bc\cos A$. For two vehicles on the same line the triangle collapses to a line: approaching head-on, the relative speed is $v_A+v_B$.

---

## Worked examples

### Collision of two particles

Particles A and B move in a plane with $\mathbf r_A=3t\,\mathbf i+9t(2-t)\,\mathbf j$ m and $\mathbf r_B=3(t^2-2t+2)\,\mathbf i+3(t-2)\,\mathbf j$ m. Do they collide, and if so where and at what speeds? (DAMS2-1, ll. 79–140; the position functions are reconstructed to reproduce the quoted roots and speeds.)

Equal $x$ coordinates:

$$
3t=3(t^2-2t+2)
$$

$$
t^2-3t+2=0\quad\Rightarrow\quad t=1\ \text{or}\ 2\ \mathrm s
$$

Equal $y$ coordinates:

$$
9t(2-t)=3(t-2)
$$

$$
3t^2-5t-2=0\quad\Rightarrow\quad t=2\ \text{or}\ -\tfrac13\ \mathrm s
$$

Only $t=2$ s satisfies both, so they collide then, at $\mathbf r=(6,0)$ m. Differentiating,

$$
\mathbf v_A=3\,\mathbf i+(18-18t)\,\mathbf j=3\,\mathbf i-18\,\mathbf j,\qquad \mathbf v_B=(6t-6)\,\mathbf i+3\,\mathbf j=6\,\mathbf i+3\,\mathbf j
$$

at $t=2$ s, so $v_A=\sqrt{9+324}=18.2$ m/s and $v_B=\sqrt{36+9}=6.71$ m/s.

### Particle accelerating on a circle

A particle starts from rest on a circle of radius $R=2$ m with constant angular acceleration $\alpha_c=1.5$ rad/s². Find its velocity and acceleration after it has travelled half way round, $s=\pi R$ (DAMS2-2, ll. 184–239; the radius is implied by the quoted answers).

Half a revolution is $\theta=\pi$. From rest, $\theta=\tfrac12\alpha_ct^2$:

$$
t=\sqrt{\frac{2\pi}{1.5}}=2.047\ \mathrm s
$$

$$
\omega=\alpha_ct=1.5\times2.047=3.07\ \mathrm{rad/s}
$$

$$
v=R\omega=6.14\ \mathrm{m/s},\qquad \mathbf v=6.14\,\mathbf u_t\ \mathrm{m/s}
$$

The acceleration components are

$$
a_t=R\alpha_c=3.00\ \mathrm{m/s^2},\qquad a_n=R\omega^2=2\times3.07^2=18.85\ \mathrm{m/s^2}
$$

so $a=\sqrt{3^2+18.85^2}=19.1$ m/s², pointing inwards at $\arctan(3/18.85)=9.0°$ from $\mathbf u_n$, tilted forwards. Halfway round, the centripetal part already dominates.

### Car over a parabolic hill

A car of mass 800 kg travels over a hill $y=20(1-x^2/6400)$ m. At A, where $x=80$ m and the car is coming down, its speed is 9 m/s and increasing at 3 m/s². Find the resultant normal force and friction force on the car from the road (slides pp. 39–43; DAMS2-Ex1; L04, ll. 193–307).

![[d_hill_car_example.png|900]]

Treat the car as a particle. Put the n-t axes on it with $t$ down the slope (the direction of motion) and $n$ into the hill towards the centre of curvature, which lies below the road because the hill is convex. The FBD has $mg$, the normal force $N$ (along $-n$) and friction $F$, guessed up the slope. Resolving:

$$
\sum F_n:\ mg\cos\theta-N=m\frac{v^2}{\rho}
$$

$$
\sum F_t:\ mg\sin\theta-F=ma_t
$$

The slope at A:

$$
\frac{dy}{dx}=-\frac{40x}{6400}=-\frac{x}{160}=-0.5
$$

$$
\theta=|\arctan(-0.5)|=26.57°
$$

and

$$
\frac{d^2y}{dx^2}=-\frac1{160}
$$

$$
\rho=\frac{(1+0.25)^{3/2}}{1/160}=223.6\ \mathrm m
$$

Then

$$
N=mg\cos\theta-m\frac{v^2}{\rho}=800\times9.81\times0.8944-800\times\frac{81}{223.6}=7019.5-289.8=6730\ \mathrm N
$$

$$
F=mg\sin\theta-ma_t=800\times9.81\times0.4472-800\times3=3509.7-2400=1110\ \mathrm N
$$

$F$ is positive, so friction acts up the slope as guessed. On a frictionless road the car would gain speed at $g\sin\theta=4.39$ m/s²; it gains only 3 m/s², so the road is holding it back (the driver is braking). The normal force is less than the weight component $mg\cos\theta$ because part of that component is used to turn the car over the crest.

### Simple pendulum

A mass $m$ on a light cable of length $L$ is released from rest at angle $\theta_0$ from the vertical. Find its speed and the cable tension as functions of $\theta$, and the period of small oscillations (DAMS2-Ex2).

Put n-t axes on the mass, with $n$ along the cable towards the pivot. The FBD has the tension $T$ along $+n$ and the weight $mg$. With $\theta$ measured from the vertical and the tangent in the direction of increasing $\theta$,

$$
\sum F_n:\ T-mg\cos\theta=m\frac{v^2}{L} \tag{3}
$$

$$
\sum F_t:\ -mg\sin\theta=ma_t \tag{4}
$$

so $a_t=-g\sin\theta$, independent of mass and not constant. Use $a_t\,ds=v\,dv$ with $ds=L\,d\theta$:

$$
\int_0^v v\,dv=-gL\int_{\theta_0}^{\theta}\sin\theta\,d\theta
$$

$$
\tfrac12v^2=gL(\cos\theta-\cos\theta_0)
$$

$$
v=\pm\sqrt{2gL(\cos\theta-\cos\theta_0)}
$$

the sign depending on the direction of swing. Substituting $v^2$ into (3):

$$
T=mg\cos\theta+\frac mL\,2gL(\cos\theta-\cos\theta_0)
$$

$$
T=mg(3\cos\theta-2\cos\theta_0)
$$

The tension is greatest at the bottom, $T_{max}=mg(3-2\cos\theta_0)$, and least at the extremes, $T_{min}=mg\cos\theta_0$.

For the period, write $s=L\theta$, so $a_t=L\ddot\theta$ and (4) becomes

$$
\ddot\theta+\frac gL\sin\theta=0
$$

which is nonlinear. For small angles (in radians) $\sin\theta\approx\theta$, which linearises it:

$$
\ddot\theta+\frac gL\theta=0
$$

The general solution is $\theta=A\sin(\sqrt{g/L}\,t)+B\cos(\sqrt{g/L}\,t)$. At $t=0$, $\theta=\theta_0$ gives $B=\theta_0$, and $\dot\theta=0$ gives $A\sqrt{g/L}=0$, so $A=0$:

$$
\theta=\theta_0\cos\left(\sqrt{\frac gL}\,t\right),\qquad T_{period}=2\pi\sqrt{\frac Lg}
$$

independent of the mass and, for small swings, of the amplitude. With $L=9.22$ m, $T_{period}=6.09$ s (DAMS2-Ex2, ll. 467–491); for $m=1.2$ kg released at 12.5°, the tension ranges from 11.5 N to 12.3 N. The same equation of motion reappears as the undamped oscillator of [[FEEG1002 D6 - Single Degree of Freedom Vibration|D6]].

### Two boats leaving a shore

Two boats leave the same point together, A at 6 m/s heading 30° to the left of the normal to the shore and B at 4.5 m/s at 45° to the shore, so that their headings are 75° apart. Find the velocity of A relative to B and when they are 240 m apart (DAMS2-3, ll. 73–129).

With $x$ along the shore and $y$ out from it,

$$
\mathbf v_A=6(-\sin30°\,\mathbf i+\cos30°\,\mathbf j)=-3.00\,\mathbf i+5.196\,\mathbf j\ \mathrm{m/s}
$$

$$
\mathbf v_B=4.5(\cos45°\,\mathbf i+\sin45°\,\mathbf j)=3.182\,\mathbf i+3.182\,\mathbf j\ \mathrm{m/s}
$$

$$
\mathbf v_{A/B}=\mathbf v_A-\mathbf v_B=-6.182\,\mathbf i+2.014\,\mathbf j\ \mathrm{m/s}
$$

so $v_{A/B}=6.50$ m/s at $\arctan(2.014/6.182)=18.0°$ to the shore. The cosine rule on the velocity triangle gives the same magnitude: $\sqrt{6^2+4.5^2-2\times6\times4.5\cos75°}=6.50$ m/s. Both boats move at constant velocity from the same point, so their separation grows at this rate:

$$
t=\frac{240}{6.50}=36.9\ \mathrm s
$$

### Mine car hoisted by its own motor

A 100 kg mine car C on an incline is hoisted by a motor M mounted on the car itself, which pulls in the cable with a relative acceleration $a_{P/C}=1.2$ m/s², where P is the point of the cable entering the motor. Find the car's acceleration (DAMS2-3, ll. 130–171; Tutorial 2 Q9).

Measure positions down the incline from the fixed point at the top. In the arrangement of the sheet the car hangs on two strands of the cable and the third length runs to P, so the constant cable length gives $s_P+2s_C=\text{const}$ and

$$
a_P=-2a_C
$$

Relative acceleration gives $a_P=a_C+a_{P/C}$. Equating:

$$
-2a_C=a_C+1.2
$$

$$
a_C=-0.4\ \mathrm{m/s^2}
$$

The car accelerates at 0.4 m/s² up the incline, and $a_P=0.8$ m/s² down. The cable tension then follows from the car's equation of motion (Tutorial 2 Q9).

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D1 - Linear Motion of Particles]] · Next: [[FEEG1002 D3 - Work, Energy and Power]]
- Concepts: [[Projectile Motion]] · [[Normal and Tangential Coordinates]] · [[Newton's Laws of Motion]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 D3 - Work, Energy and Power|D3]] (the loop: n-t at the top plus energy) · [[FEEG1002 D7 - Kinematics of Rigid Bodies|D7]] ($v=\omega r$, $a_t=\alpha r$, $a_n=\omega^2r$ for points on a rotating body; relative velocity becomes $\boldsymbol\omega\times\mathbf r_{B/A}$) · [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (rotating axes) · [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] (orbits as curvilinear motion)

## Sources

- `Lecture 02 - Curvilinear Motion.pdf`: slides pp. 1–45 (general kinematics pp. 5–7, rectangular components pp. 8–12, projectiles pp. 14–20, n-t coordinates pp. 21–32, equations of motion pp. 33–37, car on a hill pp. 39–43, sine and cosine rules pp. 44–45).
- Transcript labels used in this note:
  - L03 = `FEEG1002 Lecture 2025-02-05.txt` (5 Feb 2025): kinematics, projectiles, quizzes, n-t acceleration (ll. 24–597).
  - L04 = `FEEG1002 Lecture 2025-02-06.txt` (6 Feb 2025): binormal and banked curves, circular motion, equations of motion, car on a hill, quarter-circle race (ll. 1–435).
  - DAMS2-1 = `FEEG1002 Lecture 2020-12-23 - DAMS-2-CurvilinearMotion1.txt`; DAMS2-1-1 = `...CurvilinearMotion1-1.txt`; DAMS2-2 = `...CurvilinearMotion2.txt`; DAMS2-4 = `...CurvilinearMotion4.txt`.
  - DAMS2-3 = `FEEG1002 Lecture 2021-01-11.txt` (relative motion).
  - DAMS2-Ex1 = `...CurvilinearMotion-SolvedExample1.txt` (car on a hill); DAMS2-Ex2 = `...SolvedExample2.txt` (pendulum).
- `Tutorial Sheet 02 - Curvilinear Motion.pdf`: Q1–Q11, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Derive the trajectory, time of flight and range from equations (1) and (2) (DAMS2-1-1, ll. 62–66, 100–103; L03, ll. 330, 361). → [[#Trajectory]] · [[#Time of flight and range]]
- [ ] Quiz: a ball thrown horizontally at 10 m/s from a 45 m cliff, $g=10$ m/s²; how long until it lands? Target 3 s (L03, ll. 364–391). → [[#3. Projectiles]]
- [ ] Redo the car-on-a-hill example (L04, ll. 215, 304–306). Targets 6.73 kN and 1.11 kN. → [[#Car over a parabolic hill]]
- [ ] Work through the $\dot{\mathbf u}_t$ derivation (not assessed, L03, ll. 573–581). → [[#Acceleration]]
- [ ] Tutorial 2 Q1 (projectile from a cliff) and Q2–Q3 (circular motion, pointed to at L04, l. 92). → [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]
- [ ] Tutorial 2 Q5, the banked curve (L04, ll. 17–36). → [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]
- [ ] Tutorial 2 Q9, mine car: find the cable tension (DAMS2-3, l. 170). → [[#Mine car hoisted by its own motor]]

### Further practice

- [ ] Plot a projectile trajectory in Python and find its maximum height and range (L03, ll. 330–341). → [[#3. Projectiles]]
- [ ] Pendulum: put in numbers, quantify the error of $\sin\theta\approx\theta$, and plot $T(\theta)$ for $m=1.2$ kg (DAMS2-Ex2, ll. 250, 346–348, 487–491). → [[#Simple pendulum]]
- [ ] Quarter circle against straight chord between the same two points (L04, ll. 322–435): show the speeds at the bottom are equal, and integrate numerically for the times; the curve is about 7% faster. → [[FEEG1002 D3 - Work, Energy and Power#Conservation of energy]]
- [ ] Tutorial 2 Q4, Q6–Q8, Q10–Q11. → [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 02 slides)
> Where: [[#Car over a parabolic hill]] · [[#Circular paths]].
>
> Slide p. 43 gives $N=6728$ N and $F=1114$ N, from rounding $\theta$ to 26.6° before using it; with $\theta=26.565°$ the answers are 6730 N and 1110 N. Slides pp. 39–40 and 43 call $N$ and $F$ the forces "on the road"; the FBD is of the car, so they are the forces on the car. Slide p. 31 writes $\dot v=a$ where it means $a_t$.

### Transcript slips (L03, L04, DAMS2)

| Ref | Said | Correct |
|---|---|---|
| DAMS2-Ex1, l. 117; L04, ll. 259–263 | the car "is slowing down" / "decelerating" | it speeds up at 3 m/s², less than the 4.39 m/s² of free rolling |
| L03, l. 595; L04, ll. 281–284 | the $\rho$ formula uses the first and second time derivatives | derivatives with respect to $x$ |
| L03, l. 519 | $\dot{\mathbf u}_t$ is rotated 90° from the initial direction $n$ | from $\mathbf u_t$ |
| L03, l. 541 | the tangential term is the rate of change of velocity | of speed |
| L04, ll. 73–75 | the constant-$\alpha$ equations introduced via motion "at constant speed" | constant speed is only the case $\alpha=0$ |
| DAMS2-1, l. 25 | average velocity is the change in velocity over time | change in position |
| DAMS2-3, l. 84 | B heads at "40 degrees" | 45° |
| DAMS2-3, l. 112 | separation from the constant-acceleration equations | constant velocity |
| DAMS2-Ex2, ll. 400–404 | $\dot\theta$ written without the factor $\sqrt{g/L}$ | the conclusion $A=0$ is unchanged |

Whisper renderings to read through: "anti-system", "empty system" = n-t system; "binomial" = binormal; "Suvart" = SUVAT; "drug" = drag; "law of signs" = law of sines.
