---
title: "FEEG1002 D1 - Linear Motion of Particles"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 1
tags: [feeg1002, dynamics, kinematics, newtons-laws, friction, drag, pulleys, particles]
aliases: ["Dynamics Lecture 1", "Rectilinear motion", "Linear motion", "Dependent motion"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 1 (slides pp. 1-63) in full: kinematics of rectilinear motion, Newton's laws and inertial frames, typical forces (gravitation, weight, dry friction, springs, ropes, drag, buoyancy), dependent motion and pulleys. Live lectures L01 (29 Jan 2025) and L02b (30 Jan 2025); pre-recorded DAMS1-1 to DAMS1-4 with worked examples DAMS1-Ex1 and DAMS1-Ex2; the linear-drag ship from the L12 revision lecture (6 Mar 2025, ll. 59-183)."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
key_concepts: ["[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]", "[[Coulomb Friction]]", "[[Dependent Motion and Pulley Constraints]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-01-29.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-01-30.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-04 - DAMS-1-LinearMotion_1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-04 - DAMS-1-LinearMotion_2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-07.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-12-16.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-06 - DAMS-1-LinearMotion-Example1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2020-12-06 - DAMS-1-LinearMotion-Example2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-06.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 01 - Linear Motion.pdf"]
---

# FEEG1002 D1 - Linear Motion of Particles

> [!abstract] Summary
> A particle has mass but negligible size, so its motion along a straight line is described by one coordinate $s(t)$, with $v=ds/dt$, $a=dv/dt$ and, by the chain rule, $a=v\,dv/ds$. Newton's second law $\sum F=ma$, written in an inertial frame from a free-body diagram and a kinetic diagram, gives $a$ as a function of time, position or velocity depending on the forces present (friction, springs, drag, buoyancy, gravity varying with height), and that dependence decides which integral turns $a$ into $v$ and $s$. Blocks joined by inextensible cords over ideal pulleys have linked motions found by differentiating the constant cord length.

> [!summary]- Exam use: quick path
> - **Use it when:** a body moves along a straight line and you need its speed, position, time or the forces on it; or several blocks are joined by cords and pulleys.
> - **Assumptions:** particle (no rotation), inertial frame (Earth-fixed near the surface), ropes massless and inextensible, pulleys massless and frictionless, dry (Coulomb) friction.
> - **Method:** 1. Choose a positive direction and an origin. 2. Draw the free-body diagram and the kinetic diagram ($ma$ in the positive direction). 3. Write $\sum F=ma$ and see whether $a$ depends on $t$, $s$ or $v$. 4. Separate variables with the matching form ($dv=a\,dt$, $v\,dv=a\,ds$, $ds=v\,dv/a$ or $dt=dv/a$) and integrate between known limits. 5. For pulleys, write the cord length from fixed datums and differentiate it once for velocities and twice for accelerations.
> - **Common mistakes:** using the constant-acceleration (SUVAT) equations when a spring, drag or buoyancy makes $a$ vary; putting $\mu_sN$ into the equation of motion as if it were the static friction force.
> - **Practise:** [[#Block pulled through a pulley]] · [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]] (Q5 bungee, Q11 log and block)

Dynamics replaces the equilibrium of statics, $\sum F=0$, with $\sum F=ma$. The free-body diagram is drawn as in [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain|A1]], but the forces no longer balance and the unbalanced part accelerates the body. Kinematics describes the motion (position, velocity, acceleration) without asking what causes it; kinetics links that motion to forces.

The simplest model of a body is a particle: a point carrying all the mass. A car accelerating along a straight road, a rocket sled or an aircraft seen from far away can be treated this way as long as its rotation does not matter, because then the motion of its centre of mass describes the body completely. Rigid bodies, whose rotation does matter, come in [[FEEG1002 D7 - Kinematics of Rigid Bodies|D7]].

The central task is to recognise what the acceleration depends on. Gravity near the ground and kinetic friction give a constant acceleration, so the familiar constant-acceleration formulae apply. A spring or buoyancy force depends on position, drag depends on speed, and gravity far from the Earth depends on altitude; in each of these cases the constant-acceleration formulae give wrong answers and the equation of motion has to be integrated.

---

## 1. Position, velocity and acceleration

Take a straight line with an origin $O$ and a positive direction. The **position** $s$ of the particle is its signed distance from $O$, and the **displacement** over an interval is the change of position, $\Delta s=s'-s$. Both are really vectors along the line, but on a single axis the sign carries the direction.

The **velocity** is the rate of change of position. The average over $\Delta t$ is $\Delta s/\Delta t$, and in the limit

$$
v=\lim_{\Delta t\to0}\frac{\Delta s}{\Delta t}=\frac{ds}{dt}
$$

The signed scalar $v$ is called the speed here; it can be positive or negative on the line. The **acceleration** is the rate of change of velocity:

$$
a=\frac{dv}{dt}=\frac{d^2s}{dt^2}
$$

The sign of $a$ says which way the velocity is changing, not whether the particle is speeding up. A particle moving in $+s$ with $a<0$ is slowing down (braking at traffic lights); a particle moving in $-s$ with $a<0$ is speeding up. Only when $v>0$ does a negative $a$ mean a falling speed.

A third relation removes time. If the velocity is known as a function of position, $v=v(s)$, the chain rule gives

$$
a=\frac{dv}{dt}
$$

$$
=\frac{dv}{ds}\,\frac{ds}{dt}
$$

$$
\boxed{a=v\,\frac{dv}{ds}}
$$

since $ds/dt=v$. This form is the one to use whenever the force, and so the acceleration, depends on position. Dot notation is used for time derivatives only: $\dot s=v$, $\ddot s=\dot v=a$.

## 2. Choosing the integral

Differentiating a known $s(t)$ to get $v$ and $a$ is routine. The harder and more common job is the reverse, where Newton's second law gives $a$ and the motion is wanted. Which integral to use depends on what $a$ is a function of, and in every case the variables are separated so that each side contains only one of them. The limits are the values at $t=0$ ($s_0$, $v_0$) and at the general state.

**Acceleration given as a function of time**, $a(t)$. From $a=dv/dt$:

$$
dv=a(t)\,dt
$$

$$
\int_{v_0}^{v}dv=\int_0^t a(t)\,dt
$$

$$
v=v_0+\int_0^t a(t)\,dt
$$

and then $s$ follows from $ds=v\,dt$, i.e. $s=s_0+\int_0^t v(t)\,dt$.

**Acceleration given as a function of position**, $a(s)$: springs, buoyancy, gravity with altitude. From $a=v\,dv/ds$:

$$
v\,dv=a(s)\,ds
$$

$$
\int_{v_0}^{v}v\,dv=\int_{s_0}^{s}a(s)\,ds
$$

$$
\tfrac12v^2-\tfrac12v_0^2=\int_{s_0}^{s}a(s)\,ds
$$

**Acceleration given as a function of velocity**, $a(v)$: drag. Use $a=v\,dv/ds$ to get position,

$$
ds=\frac{v\,dv}{a(v)}
$$

$$
s-s_0=\int_{v_0}^{v}\frac{v}{a(v)}\,dv
$$

or $a=dv/dt$ to get time,

$$
dt=\frac{dv}{a(v)}
$$

$$
t=\int_{v_0}^{v}\frac{dv}{a(v)}
$$

**Velocity given as a function of position**, $v(s)$: from $v=ds/dt$, $dt=ds/v(s)$ and $t=\int_{s_0}^{s}ds/v(s)$.

The time form for $a(v)$ is the one used for the marble falling in water, so both $a(v)$ forms are used.

## 3. Constant acceleration

When $a=a_c$ is constant, the integrals above can be done once and for all. Starting from $dv=a_c\,dt$ with $v=v_0$ at $t=0$:

$$
\int_{v_0}^{v}dv=a_c\int_0^t dt
$$

$$
v=v_0+a_ct
$$

Then $ds=v\,dt$, substituting this $v$:

$$
\int_{s_0}^{s}ds=\int_0^t(v_0+a_ct)\,dt
$$

$$
s=s_0+v_0t+\tfrac12a_ct^2
$$

and from $v\,dv=a_c\,ds$:

$$
\int_{v_0}^{v}v\,dv=a_c\int_{s_0}^{s}ds
$$

$$
\tfrac12\left(v^2-v_0^2\right)=a_c(s-s_0)
$$

$$
v^2=v_0^2+2a_c(s-s_0)
$$

These are the **SUVAT equations**. They are valid only if the acceleration is constant: free fall without drag ($a_c=-g$ with $s$ up), sliding with kinetic friction on a flat or inclined surface, a constant applied force. With a spring, drag, partial buoyancy or gravity varying with altitude, $a$ changes as the body moves and the equations give wrong numbers, so the first question in any problem is whether $a$ is constant.

## 4. Newton's laws and the equation of motion

Newton's three laws:

1. A particle at rest, or moving in a straight line at constant velocity, stays so if the resultant force on it is zero (the law of inertia).
2. A non-zero resultant force gives the particle an acceleration in the direction of the force, proportional to the force and inversely proportional to the mass: $\sum\mathbf F=m\mathbf a$.
3. The forces two particles exert on each other are equal, opposite and collinear.

The **mass** $m$ in the second law is a positive scalar measuring inertia, the resistance of a body to a change in its velocity; it is defined by $m=F/a$ and measured in kg. The law fails near the speed of light and at atomic scales, neither of which arises here. Zero acceleration does not mean zero motion: a particle with no resultant force keeps whatever constant velocity it has.

The equation of motion is set up the same way for every problem:

1. Choose the positive direction of the coordinate.
2. Draw the **free-body diagram** (FBD): the particle isolated with every external force on it.
3. Draw the **kinetic diagram**: the vector $m\mathbf a$, drawn in the positive direction.
4. Equate the two, component by component, e.g. $F_1+F_2-F_3=ma$.

The FBD supplies the left-hand side and the kinetic diagram the right-hand side. Exam questions almost always start by asking for these two diagrams.

### Inertial frames

$\sum\mathbf F=m\mathbf a$ holds only if the acceleration is measured in an **inertial** (Newtonian) frame, one that is not itself accelerating, so that the law of inertia holds in it. A ball dropped from the mast of a cart moving at constant velocity lands at the foot of the mast, exactly as it would if the cart were at rest; in a cart that is speeding up or braking it does not, and an observer riding with the cart would have to invent a sideways force to explain the curved fall. Such invented forces are called fictitious (or inertial) forces, and they are never drawn on an FBD.

Near the Earth's surface the frame is taken as fixed to the Earth and the Earth's rotation is neglected. For satellites and rockets the frame is fixed to the stars.

## 5. Forces met in particle dynamics

### Gravitational attraction and weight

Two particles attract each other with

$$
F_g=G\frac{m_1m_2}{r^2}
$$

where $r$ is the distance between their centres and $G=6.674\times10^{-11}$ m³ kg⁻¹ s⁻². For a particle of mass $m$ at distance $r$ from the centre of the Earth (mass $M_e$), the force per unit mass is

$$
g(r)=\frac{F_g}{m}=\frac{GM_e}{r^2}
$$

At the surface, $r=R_e=6371$ km and $M_e=5.97\times10^{24}$ kg give $g_0=GM_e/R_e^2=9.82$ m/s², rounded to 9.81 m/s². Near the surface the **weight** $\mathbf W=m\mathbf g$ acts at the centre of mass, pointing down. Mass is a property of the body; weight depends on where the body is, so a 10 kg mass on the Moon weighs about one sixth of its weight on Earth.

To see how $g$ falls with height $y$ above the surface, take $y$ positive away from the Earth, so that gravity is negative, and divide $g(r)$ by $g_0$:

$$
\frac{g(r)}{g_0}=\frac{GM_e/r^2}{GM_e/R_e^2}=\frac{R_e^2}{r^2}
$$

With $r=R_e+y$ the acceleration of a particle under gravity alone is

$$
a=-g_0\frac{R_e^2}{(R_e+y)^2}
$$

which depends on position. At the International Space Station ($y\approx400$ km) this is still 0.885 $g_0$; astronauts are weightless because they are in free fall, not because gravity has vanished.

### Dry friction

Coulomb's model of dry friction distinguishes two regimes.

While the surfaces do not slide, the friction force $F_s$ is whatever is needed to keep them together, up to a limit:

$$
F_s\le\mu_sN
$$

where $\mu_s$ is the coefficient of static friction and $N$ the normal reaction. This inequality cannot be used to calculate $F_s$. The static friction force comes from equilibrium (for a block pushed horizontally by $F$ on a level floor, $F_s=F$ and $N=mg$) and is then checked against $\mu_sN$. At $F_s=\mu_sN$ sliding is impending but the bodies are still at rest.

Once sliding starts, the friction force is

$$
F_k=\mu_kN
$$

an equation, with $\mu_k<\mu_s$ in general. It always opposes the sliding. For the block pushed by $F$ on a level floor the equation of motion becomes

$$
F-\mu_kN=ma,\qquad N=mg
$$

![[d_coulomb_friction.png|900]]

As the applied force rises from zero, the friction force follows it with slope 1 up to $\mu_sN$, then drops to the constant $\mu_kN$ once the block moves. The model holds for dry, unlubricated surfaces and treats the friction coefficients as independent of contact area, normal load and speed. It does not describe a rolling tyre on a road.

> [!warning] Static friction is not $\mu_sN$
> Writing $F_s=\mu_sN$ in an equation of motion is the most common error in this topic. Use $\mu_sN$ only as the upper limit of the static friction found from equilibrium, or at the instant of impending sliding. A body sliding on a surface always has $F_k=\mu_kN$.

### Springs

A linear spring, treated as massless, pulls or pushes with

$$
F_e=k\,\Delta l=k(l-l_0)
$$

where $l$ is its current length, $l_0$ its natural (unstretched) length and $k$ its stiffness in N/m (Hooke's law). A block pulled by $F$ against a spring therefore has $F-k\Delta l=ma$, and since $\Delta l$ changes as the block moves, $a=a(s)$.

### Ropes and cords

Ropes and cords are massless and inextensible, and their tension $T$ can only pull ($T\ge0$). For a mass hanging on a rope, with $x$ positive up,

$$
-mg+T=ma
$$

At rest $T=mg$, but when the mass accelerates upwards $T=m(g+a)$, which is how a rope that holds a load statically can break when the load is jerked.

### Drag and terminal velocity

A body moving through a fluid feels a drag force opposing its motion,

$$
F_D=\tfrac12\rho_fSC_Dv^2=Cv^2
$$

where $\rho_f$ is the fluid density, $S$ the frontal (section) area and $C_D$ the drag coefficient, measured in a wind tunnel and dependent on shape; $C$ lumps them together. For a small sphere moving slowly the drag is linear instead, $F_D=cv$. Either way $a=a(v)$.

For a body falling from rest with quadratic drag, take $y$ positive down. The equation of motion is

$$
mg-Cv^2=m\frac{dv}{dt}
$$

The **terminal velocity** $v_t$ is reached when drag balances weight and the acceleration is zero:

$$
mg-Cv_t^2=0\quad\Rightarrow\quad v_t=\sqrt{\frac{mg}{C}}
$$

To find $v(t)$, write the equation as $dv/dt=g(1-v^2/v_t^2)$ and separate variables:

$$
\int_0^v\frac{dv}{1-v^2/v_t^2}=\int_0^t g\,dt
$$

$$
v_t\,\mathrm{artanh}\!\left(\frac{v}{v_t}\right)=gt
$$

$$
v=v_t\tanh\!\left(\frac{gt}{v_t}\right)
$$

The speed approaches $v_t$ but never reaches it. The linear-drag version is in [[#Ship and marble with linear drag]].

![[d_drag_terminal_velocity.png|900]]

### Buoyancy

A body immersed in a fluid of density $\rho_f$ feels an upward force equal to the weight of the fluid it displaces (Archimedes' principle):

$$
F_B=\rho_fV_sg
$$

where $V_s$ is the submerged volume. The body's own mass is $m=\rho_mV_{tot}$. With $y$ positive down, $mg-\rho_fV_sg=ma$. A fully submerged body has constant $F_B$, but for a partly submerged one $V_s$ depends on how deep it sits, so $a=a(s)$ and the buoyancy acts like a spring (Tutorial 1 Q14).

## 6. Dependent motion and pulleys

When blocks are connected by inextensible cords running over pulleys, their positions are not independent. The pulleys are treated as massless and frictionless (lossless) and the cords as inextensible, so the tension is the same all along one cord.

To find the kinematic link:

1. Measure each block's position from a fixed datum, positive in its direction of motion.
2. Write the total length of each cord as the sum of its variable segments plus constant ones (arcs over pulleys, fixed lengths). The constant parts can be dropped.
3. With several cords, write one equation per cord and eliminate the intermediate coordinates.
4. Differentiate once for velocities and again for accelerations, keeping the signs.

![[d_pulley_constraints.png|940]]

For two blocks on inclines joined by one cord over a pulley, $s_A+l_{CD}+s_B=l_T$, so $v_B=-v_A$ and $a_B=-a_A$: one block goes up its slope as fast as the other comes down. With a movable pulley carrying block B, the cord passes down to B's pulley, back up, and over to A, so

$$
2s_B+h+s_A=l_T
$$

$$
2v_B+v_A=0
$$

$$
2a_B=-a_A
$$

where $h$ and $l_T$ are constant. Measuring $s_B$ up from the lower pulley instead gives $2(h-s_B)+h+s_A=l_T$ and $2v_B=v_A$; this is the same physical statement in a different coordinate.

### Pulley kinetics and mechanical advantage

For the movable-pulley system, block A (on a smooth horizontal surface, pulled by $F$ away from the pulley) and block B (hanging, $s_B$ positive down) give

$$
F-T=m_Aa_A
$$

$$
m_Bg-2T=m_Ba_B
$$

$$
a_A=-2a_B
$$

where B carries two strands of the cord, so $2T$. Substituting the constraint into the first equation, $T=F+2m_Aa_B$, and then into the second:

$$
m_Bg-2F-4m_Aa_B=m_Ba_B
$$

$$
a_B=\frac{m_Bg-2F}{m_B+4m_A},\qquad T=\frac{m_B(F+2m_Ag)}{m_B+4m_A}
$$

A pulley that carries $n$ strands gives a **mechanical advantage** of $n$: the force on the load is $nT$, but the load moves $n$ times more slowly than the cord. The anchoring points carry the sum of all strand tensions, so they must be checked too. With one fixed pulley redirecting the pull, the load sees $F$ and the ceiling $2F$; with a movable pulley the load sees $2F$, moves at half the speed, and the anchors carry $F+2F=3F$.

For a compound system with two cords, cord 1 gives $s_A+2s_C=l_1$ and cord 2 gives $s_B+(s_B-s_C)=l_2$. Eliminating $s_C$:

$$
s_C=2s_B-l_2
$$

$$
s_A+2(2s_B-l_2)=l_1
$$

$$
s_A+4s_B=l_1+2l_2
$$

$$
v_A=-4v_B,\qquad a_A=-4a_B
$$

The load hangs from four strands of cord 1's tension $T$, so $4T-m_Bg=m_Ba_B$ (B positive up), and the ceiling carries $5T$. Pulling A down at 2 m/s lifts B at 0.5 m/s.

---

## Worked examples

### Block pulled through a pulley

A block of mass $m$ on a rough horizontal floor is pulled by a cord that passes round a pulley attached to it, so that the force on the block is $2P$. Find the value $P_0$ at which sliding is impending, the acceleration when $P=3P_0$, and the speed and distance after a time $\Delta t$ from rest (DAMS1-Ex1). The data are not recorded in the source; $m=4$ kg, $\mu_s=0.3$, $\mu_k=0.2$ and $\Delta t=1.3$ s reproduce every quoted answer, so they are used here.

Take $x$ positive in the direction of the pull. In the static case the FBD has $2P$, $mg$, $N$ and the static friction $F_s$, and vertical equilibrium gives $N=mg$. At impending sliding the friction reaches its limit:

$$
2P_0-\mu_sN=0
$$

$$
P_0=\frac{\mu_smg}{2}=\frac{0.3\times4\times9.81}{2}=5.89\ \mathrm N
$$

At $P=3P_0$ the block slides, so friction is kinetic:

$$
2(3P_0)-\mu_kmg=ma
$$

$$
3\mu_smg-\mu_kmg=ma
$$

$$
a=g(3\mu_s-\mu_k)=9.81\times(0.9-0.2)=6.87\ \mathrm{m/s^2}
$$

This is constant, so SUVAT applies from rest:

$$
v=a\Delta t=6.867\times1.3=8.93\ \mathrm{m/s},\qquad s=\tfrac12a\Delta t^2=\tfrac12\times6.867\times1.3^2=5.80\ \mathrm m
$$

> [!check] Units and limits
> $P_0$ does not depend on $\mu_k$ and $a$ does not depend on $m$, as the algebra shows; solving symbolically first and substituting at the end makes such checks possible.

### Escape velocity

A particle is launched vertically from the Earth's surface at speed $v_0$. Allowing for the variation of gravity with altitude and neglecting drag, find its speed at altitude $y_1$ and the launch speed needed for it never to return (DAMS1-Ex2).

With $y$ positive up from the surface, [[#Gravitational attraction and weight]] gives $a(y)=-g_0R_e^2/(R_e+y)^2$, a function of position, so use $v\,dv=a\,dy$:

$$
\int_{v_0}^{v_1}v\,dv=-g_0R_e^2\int_0^{y_1}\frac{dy}{(R_e+y)^2}
$$

$$
\tfrac12\left(v_1^2-v_0^2\right)=-g_0R_e^2\left[-\frac{1}{R_e+y}\right]_0^{y_1}
$$

$$
\tfrac12\left(v_1^2-v_0^2\right)=-g_0R_e^2\left(\frac{1}{R_e}-\frac{1}{R_e+y_1}\right)
$$

$$
\tfrac12\left(v_1^2-v_0^2\right)=-g_0R_e\frac{y_1}{R_e+y_1}
$$

$$
v_1=\sqrt{v_0^2-\frac{2g_0R_ey_1}{R_e+y_1}}
$$

The particle stops where the quantity under the root reaches zero, which gives the maximum altitude $y_{max}=R_ev_0^2/(2g_0R_e-v_0^2)$. For $v_0=5$ km/s, $v_1=3.99$ km/s at 500 km and $y_{max}=1593$ km.

For the particle never to return, $v$ must stay positive as $y\to\infty$. Setting $v_1=0$ as $y_1\to\infty$, where $y_1/(R_e+y_1)\to1$:

$$
0=v_0^2-2g_0R_e
$$

$$
v_{esc}=\sqrt{2g_0R_e}=\sqrt{2\times9.81\times6.371\times10^6}=11.2\ \mathrm{km/s}
$$

![[d_escape_velocity.png|900]]

In practice this speed cannot be reached instantaneously at launch, and drag in the atmosphere would take a large share of it, so the result is an idealisation (DAMS1-Ex2).

> [!check] Numerical check
> Integrating $\ddot y=-g_0R_e^2/(R_e+y)^2$ numerically from $v_0=5$ km/s gives 3988 m/s at 500 km, the same as the closed form.

### Ship and marble with linear drag

A ship of mass $m$ is driven by a constant propulsive force $F$ against a drag $F_D=bv$. Find $v(t)$ from rest (a 2020–21 past-paper question; no numerical data are recorded). The same equation describes a marble sinking in water, with $mg-F_B$ in place of $F$ and $c$ in place of $b$.

The FBD has the propulsion $F$ forwards, drag $bv$ backwards, and weight and buoyancy balancing vertically. Horizontally,

$$
F-bv=m\frac{dv}{dt}
$$

The acceleration depends on $v$, so SUVAT does not apply. Separate variables:

$$
\int_0^t dt=m\int_0^{v_1}\frac{dv}{F-bv}
$$

$$
t=-\frac mb\Big[\ln(F-bv)\Big]_0^{v_1}
$$

$$
t=-\frac mb\ln\frac{F-bv_1}{F}
$$

$$
1-\frac{bv_1}{F}=e^{-bt/m}
$$

$$
v_1=\frac Fb\left(1-e^{-bt/m}\right)
$$

The speed rises towards the terminal value $F/b$, where drag balances propulsion, with time constant $m/b$; a heavy ship approaches it slowly. With constant drag instead (the earlier part of the same question), $F-F_D=ma$ is constant and $v=(F-F_D)t/m$ grows without limit. For the marble, the terminal velocity is $v_t=(mg-F_B)/c$ and $v=v_t(1-e^{-ct/m})$.

> [!check] Limits
> For small $t$, $e^{-bt/m}\approx1-bt/m$ and $v_1\approx Ft/m$, the drag-free result. As $t\to\infty$, $v_1\to F/b$.

### Pulley system with a movable pulley

Take the system of [[#Pulley kinetics and mechanical advantage]] with illustrative values $m_A=10$ kg, $m_B=20$ kg and $F=50$ N. Then

$$
a_B=\frac{20\times9.81-2\times50}{20+4\times10}=\frac{96.2}{60}=1.60\ \mathrm{m/s^2}
$$

downwards, $a_A=-2a_B=-3.21$ m/s² (A is dragged towards the pulley, against $F$), and

$$
T=\frac{20\,(50+2\times10\times9.81)}{60}=82.1\ \mathrm N
$$

> [!check] Back-substitution
> $F-T=50-82.1=-32.1$ N $=m_Aa_A=10\times(-3.21)$, and $m_Bg-2T=196.2-164.1=32.1$ N $=m_Ba_B$. As $m_A\to0$ the formula gives $T=F$, as it must for a massless block.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] (free-body diagrams) · Next: [[FEEG1002 D2 - Curvilinear Motion]]
- Concepts: [[Kinematic Relations for Rectilinear Motion]] · [[Newton's Laws of Motion]] · [[Coulomb Friction]] · [[Dependent Motion and Pulley Constraints]] · [[Free Body Diagram and Equilibrium]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 D2 - Curvilinear Motion|D2]] (the same laws in two dimensions) · [[FEEG1002 D6 - Single Degree of Freedom Vibration|D6]] (the spring force leads to the vibration equation) · [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (the same law written in a body-fixed, non-inertial frame) · [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] (gravitation and orbits)

## Sources

- `Lecture 01 - Linear Motion.pdf`: slides pp. 1–63 (1.1 kinematics pp. 4–13, 1.2 Newton's laws pp. 15–22, 1.3 typical forces pp. 24–45, 1.4 dependent motion pp. 47–63).
- Transcript labels used in this note:
  - L01 = `FEEG1002 Lecture 2025-01-29.txt` (29 Jan 2025): kinematics (ll. 88–253), Newton's laws and inertial frames (ll. 254–426), gravitation and friction (ll. 442–578).
  - L02b = `FEEG1002 Lecture 2025-01-30.txt` (30 Jan 2025): forces (ll. 17–541), pulleys (ll. 546–708), marble quizzes and terminal velocity (ll. 709–851).
  - DAMS1-1 = `FEEG1002 Lecture 2020-12-04 - DAMS-1-LinearMotion_1.txt`; DAMS1-2 = `..._2.txt`; DAMS1-3 = `FEEG1002 Lecture 2020-12-07.txt`; DAMS1-4 = `FEEG1002 Lecture 2021-12-16.txt` (pre-recorded, kinematics, Newton's laws, forces, pulleys).
  - DAMS1-Ex1 = `FEEG1002 Lecture 2020-12-06 - DAMS-1-LinearMotion-Example1.txt`; DAMS1-Ex2 = `...-Example2.txt` (worked examples).
  - L12 = `FEEG1002 Lecture 2025-03-06.txt` (6 Mar 2025 revision lecture): ship with constant and linear drag, ll. 59–183.
- `Tutorial Sheet 01 - Linear Motion.pdf`: Q1–Q14, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Work through the other integral forms of the table yourself (L01, l. 176). → [[#2. Choosing the integral]]
- [ ] Compute $g_0$ from $G$, $M_e$ and $R_e$ (DAMS1-3, ll. 42–44; L01, l. 472). Target 9.82 m/s². → [[#Gravitational attraction and weight]]
- [ ] Repeat the block-and-pulley example and get the same numbers (DAMS1-Ex1, l. 99). → [[#Block pulled through a pulley]]
- [ ] Prove $a_B=-a_A$ for the inclines and that the alternative datum gives the same motion (slides pp. 50, 53; DAMS1-4, ll. 55–58). → [[#6. Dependent motion and pulleys]]
- [ ] Eliminate $s_C$ for the compound pulley and draw its tension map (DAMS1-4, ll. 158, 172). → [[#Pulley kinetics and mechanical advantage]]
- [ ] Integrate the marble-in-water equation for $v(t)$, the weekend challenge (L02b, ll. 842–847). → [[#Ship and marble with linear drag]]
- [ ] Tutorial 1 Q1–Q4 (differentiating and integrating kinematics). → [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]
- [ ] Tutorial 1 Q5, the bungee stiffness design task set in L02b, ll. 324–338. → [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]
- [ ] Tutorial 1 Q9–Q12 (friction and pulleys). → [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]

### Further practice

- [ ] Plot $v(y_1)$ for several launch speeds (DAMS1-Ex2, ll. 87–88). → [[#Escape velocity]]
- [ ] Recreate the ship's $v(t)$ plot and see what happens after 60 min (L12, ll. 155–172). → [[#Ship and marble with linear drag]]
- [ ] Tutorial 1 Q6–Q8 and Q13–Q14 (drag, gravity with distance, buoyancy). → [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 01 slides)
> Where: [[#1. Position, velocity and acceleration]] · [[#Gravitational attraction and weight]].
>
> Slide p. 8 says acceleration is "positive (speed increasing) or negative (speed decreasing)"; this holds only for motion in $+s$ (repeated at L01, ll. 137–138). Slide p. 28 gives $g_0\cong9.81$ m/s², while its own constants give 9.816 m/s². Slide p. 27 writes $g(r)=+GM_e/r^2$ and p. 30 writes $-GM_e/r^2$; the sign changes because p. 30 takes $y$ positive away from the Earth.

### Transcript slips (L01, L02b, DAMS1)

| Ref | Said | Correct |
|---|---|---|
| L01, ll. 269–270 | inertia holds "unless other forces are acting" | unless the resultant force is non-zero |
| L02b, l. 32 | gravitation is "inversely proportional to the distance" | to the square of the distance |
| L02b, ll. 243–245 | for a rolling tyre "we can really use our simplified approach" | cannot (slide p. 35) |
| DAMS1-3, l. 36 | "G is not a constant" | $g$ varies; $G$ is constant |
| DAMS1-Ex2, ll. 86, 128–133 | "terminal velocity" | escape velocity |
| DAMS1-Ex2, l. 84 | "the square root can become negative" | the quantity under the root |
| L12, l. 149 | "Can you use the SUVAT equations? Absolutely." | no: with linear drag the acceleration is not constant (ll. 148, 151) |

Whisper renderings to read through: "Suvart", "subat" = SUVAT; "appendix sliding" = impending sliding; "drug" = drag; "three-body diagram" = free-body diagram.
