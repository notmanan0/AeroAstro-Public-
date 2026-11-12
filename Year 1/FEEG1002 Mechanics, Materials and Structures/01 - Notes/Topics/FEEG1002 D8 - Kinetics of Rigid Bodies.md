---
title: "FEEG1002 D8 - Kinetics of Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 8
tags: [feeg1002, dynamics, rigid-body, kinetics, moment-of-inertia, rolling-with-slip, impulse-momentum]
aliases: ["Dynamics Lecture 8", "Rigid body kinetics", "Mass moment of inertia", "Radius of gyration", "Rolling with slip"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 8 (slides pp. 1-52) in full: centre of mass, mass moment of inertia and radius of gyration, the parallel-axis theorem, composite bodies, the planar equations of motion for translation, rotation about a fixed axis and general plane motion, rolling with and without slip, with the handcart, released rod and lawn-roller examples. Impulse and momentum for rigid bodies from the pre-recorded DAMS10-1 to DAMS10-4b (no slides). Live lecture L18b (27 Mar 2025, ll. 248-791); pre-recorded DAMS8-1a to DAMS8-3a; the driven-wheel mock exam question from the final live lecture (15 May 2025)."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]", "[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
key_concepts: ["[[Mass Moment of Inertia and Radius of Gyration]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Rolling Without Slip]]", "[[Parallel Axis Theorem]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-27.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-05-15.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_1a.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_1b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_2a.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_2b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_3.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_3a.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-18 - DAMS-10-impMomRigBod_1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-18 - DAMS-10-impMomRigBod_2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-18 - DAMS-10-impMomRigBod_3.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-18 - DAMS-10-impMomRigBod_4.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-18 - DAMS-10-impMomRigBod_4b.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 08 - Kinetics of Rigid Bodies.pdf"]
---

# FEEG1002 D8 - Kinetics of Rigid Bodies

> [!abstract] Summary
> A rigid body in plane motion obeys three equations: $\sum F_x=m(a_G)_x$ and $\sum F_y=m(a_G)_y$ for its centre of mass G, and a moment equation, $\sum M_G=I_G\alpha$ about G or, about any point P, $\sum M_P=$ the moment of the kinetic diagram ($m\mathbf a_G$ at G plus the couple $I_G\alpha$). The mass moment of inertia $I=\int r^2\,dm$ is the body's resistance to angular acceleration, found by integration ($\tfrac12mR^2$ for a disc, $\tfrac1{12}mL^2$ for a slender rod about G), moved between parallel axes with $I_O=I_G+md^2$ and summarised by the radius of gyration $k=\sqrt{I/m}$. For rotation about a fixed axis $\sum M_O=I_O\alpha$; for a rolling wheel the no-slip assumption $a_G=r\alpha$ must be checked against $F\le\mu_sN$, and if it fails the wheel slips with $F=\mu_kN$.

> [!summary]- Exam use: quick path
> - **Use it when:** forces and moments on a body that rotates are linked to its accelerations: pivoted rods and pendulums, wheels driven by torques or pulled at the hub, hoists with drums, carts that might tip.
> - **Assumptions:** planar motion of a rigid body; weight acts at G (uniform gravity); moment equations about G, about a fixed pivot O, or about any point with the kinetic moments included; the sense taken positive is stated in each problem.
> - **Method:** 1. Classify the motion and write the kinematics ($\alpha=0$; $a_t=r_G\alpha$, $a_n=r_G\omega^2$; or $a_G=r\alpha$ if rolling without slip). 2. Draw the FBD and the kinetic diagram ($m(a_G)_x$, $m(a_G)_y$ at G and $I_G\alpha$). 3. Write the two force equations. 4. Take moments about G, or about a pivot O with $I_O=I_G+mr_G^2$ to eliminate the pin reactions. 5. Solve and check any assumption (no tipping, $N\ge0$, no slip $F\le\mu_sN$).
> - **Common mistakes:** taking $\sum M=0$ about a point other than G for a translating body; writing $F=\mu_sN$ for a wheel assumed to roll without slip.
> - **Practise:** [[#Lawn roller pushed along the ground]] · [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]] (Q4 hoist)

A force through the centre of mass of a free body gives it pure translation; the same force applied off the centre also turns it. A body pinned at its centre of mass balances in any position; pinned anywhere else, its weight swings it round. These observations say that the rotation of a body depends on the moments about its centre of mass, and how hard it is to turn depends on how its mass is spread about the axis of rotation.

That spread is measured by the mass moment of inertia, the rotational counterpart of mass. Two cylinders of the same mass and radius, one solid and one a thin tube, roll down a slope at different rates, because the tube has its mass further from the axis and needs more torque for the same angular acceleration. Neither the mass nor the size decides the race; only the distribution does. The equations of motion for a rigid body add one moment equation, involving $I$, to the two force equations already used for particles.

---

## 1. Centre of mass

The **centre of mass** G is the point about which the mass-weighted relative positions sum to zero. For a plane body with areal density $\rho(x,y)$, write the position of each element P relative to G as $\mathbf r_{P/G}=\mathbf r_P-\mathbf r_G$ and require

$$
\int_A\mathbf r_{P/G}\,\rho\,dx\,dy=\mathbf 0
$$

$$
\int_A\mathbf r_P\,\rho\,dx\,dy-\mathbf r_G\int_A\rho\,dx\,dy=\mathbf 0
$$

$$
x_G=\frac1m\int_Ax\,\rho\,dx\,dy,\qquad y_G=\frac1m\int_Ay\,\rho\,dx\,dy
$$

with $m=\int_A\rho\,dx\,dy$. For uniform density, $m=\rho A$ and G is the centroid of the area. For a composite body made of parts with masses $m_i$ and centres $x_{Gi}$, $x_G=\frac{1}{m}\sum m_ix_{Gi}$, a mass-weighted average.

In uniform gravity the weights of the elements have zero total moment about G, so the weight acts at G on every FBD. A force through G produces only translation; a body pinned at G is in equilibrium in any orientation.

## 2. Mass moment of inertia

### Derivation from the elements

Take a plane body rotating about an axis through O perpendicular to the plane, with angular acceleration $\alpha$. An element of mass $dm$ at distance $r_O$ from the axis has tangential acceleration $a_t=r_O\alpha$ (its normal acceleration points at O and has no moment about it). Newton's law for the element in the tangential direction needs a force $dm\,a_t=\alpha r_O\,dm$, whose moment about O is

$$
dM_O=r_O\cdot\alpha r_O\,dm=\alpha r_O^2\,dm
$$

Sum over the body. Every line of a rigid body has the same $\alpha$, so it comes out of the integral, and the internal forces between elements cancel in pairs, leaving the external moments:

$$
\sum M_O=\alpha\int_Ar_O^2\,dm
$$

$$
\boxed{\sum M_O=I_O\alpha,\qquad I_O=\int_Ar_O^2\,dm=\int_Ar_O^2\rho\,dx\,dy}
$$

The **mass moment of inertia** $I_O$ (kg m²) is the body's resistance to changes in its angular speed, the rotational equivalent of $m$ in $F=ma$. It depends on the axis, and is usually quoted about G ($I_G$) or about the axis of rotation. For a uniform body it is the density times the polar second moment of area of the shape, $I_O=\rho\int r_O^2\,dA$, which is the quantity used in [[FEEG1002 A8 - Torsion of Circular Shafts|torsion]].

### Disc and slender rod

For a thin uniform disc of radius $R$ and areal density $\rho$, about the axis through G perpendicular to its plane, use polar coordinates with $dA=r\,dr\,d\theta$:

$$
I_G=\rho\int_0^{2\pi}\int_0^Rr^2\cdot r\,dr\,d\theta=\rho\int_0^{2\pi}\frac{R^4}{4}d\theta=\frac{2\pi\rho R^4}{4}
$$

and with $m=\rho\pi R^2$,

$$
I_G=\tfrac12mR^2
$$

For a thin uniform rod of length $L$ and linear density $\rho$, about a perpendicular axis through G, with $l$ measured from G:

$$
I_G=\rho\int_{-L/2}^{L/2}l^2\,dl=\rho\left[\frac{l^3}{3}\right]_{-L/2}^{L/2}=\frac{\rho L^3}{12}
$$

and with $m=\rho L$,

$$
I_G=\tfrac1{12}mL^2
$$

![[d_mass_moment_of_inertia.png|900]]

Other standard results (slides pp. 19–22): a thin hoop $I_G=mR^2$; a solid cylinder about its axis $\tfrac12mR^2$; a solid sphere $\tfrac25mR^2$; a thin rectangular plate $a\times b$ about its normal through G $\tfrac1{12}m(a^2+b^2)$. The 3D inertia tensor and products of inertia are not assessed.

### Parallel-axis theorem

Let O be an axis parallel to the one through G, at perpendicular distance $d$. Put the origin at G, with O at $\mathbf d=(d_x,d_y)$, so that an element at $(x,y)$ is at distance $r_O$ from O with

$$
r_O^2=(x-d_x)^2+(y-d_y)^2=x^2+y^2-2xd_x-2yd_y+d^2
$$

Integrating over the body:

$$
I_O=\int(x^2+y^2)\,dm-2d_x\int x\,dm-2d_y\int y\,dm+d^2\int dm
$$

The first integral is $I_G$. The middle two vanish because G is the centre of mass ($\int x\,dm=\int y\,dm=0$ with the origin at G). The last is $md^2$:

$$
\boxed{I_O=I_G+md^2}
$$

So $I_G$ is the smallest moment of inertia about any axis perpendicular to the plane. A rod about its end, for example, has $I=\tfrac1{12}mL^2+m(L/2)^2=\tfrac13mL^2$.

For a composite body: find its centre of mass G, find each part's $I_{Gi}$ about its own centre, move each to the composite G with the parallel-axis theorem, then add. Moments of inertia can be added only when they refer to the same axis.

### Radius of gyration

The **radius of gyration** $k$ about an axis is defined by

$$
I=mk^2,\qquad k=\sqrt{\frac Im}
$$

It is the radius at which all the mass could be concentrated without changing $I$. A uniform disc has $k_G=R/\sqrt2$; a thin hoop has $k_G=R$, its mass all at the rim. That difference is why the hollow cylinder always loses the rolling race, whatever the masses and sizes (L18b, ll. 248–321, 642–685; see [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling race down a slope|D9]]).

## 3. Planar equations of motion

### General plane motion

In an inertial frame, for any point P, the translational equations are those of a particle of mass $m$ at G (the internal forces cancel and the centre of mass moves as in [[FEEG1002 D4 - Linear Impulse and Momentum#Systems of particles|D4]]):

$$
\sum F_x=m(a_G)_x \tag{1}
$$

$$
\sum F_y=m(a_G)_y \tag{2}
$$

For the moment equation, sum the moments about P of $dm\,\mathbf a_i$ for every element. Write each element's position from P as $\bar{\mathbf r}+\boldsymbol\rho_i$, where $\bar{\mathbf r}$ locates G from P and $\boldsymbol\rho_i$ the element from G. From [[FEEG1002 D7 - Kinematics of Rigid Bodies#5. Relative acceleration analysis|D7]], $\mathbf a_i=\mathbf a_G+\boldsymbol\alpha\times\boldsymbol\rho_i-\omega^2\boldsymbol\rho_i$. Then

$$
\sum\mathbf M_P=\int(\bar{\mathbf r}+\boldsymbol\rho)\times(\mathbf a_G+\boldsymbol\alpha\times\boldsymbol\rho-\omega^2\boldsymbol\rho)\,dm
$$

Expand term by term. Every term containing $\int\boldsymbol\rho\,dm$ alone is zero, because G is the centre of mass; $\boldsymbol\rho\times\boldsymbol\rho=\mathbf 0$; and in plane motion $\boldsymbol\rho\times(\alpha\mathbf k\times\boldsymbol\rho)=\alpha\rho^2\mathbf k$. What remains is

$$
\sum\mathbf M_P=\bar{\mathbf r}\times m\mathbf a_G+\alpha\mathbf k\int\rho^2\,dm
$$

$$
\boxed{\sum M_P=\bar{\mathbf r}\times m\mathbf a_G+I_G\alpha} \tag{3}
$$

The left side is the sum of the moments of the external forces about P; the right side, the **kinetic moments**, is the moment about P of everything on the kinetic diagram: the vectors $m(a_G)_x$, $m(a_G)_y$ drawn at G and the couple $I_G\alpha$. In scalar form each component of $m\mathbf a_G$ is multiplied by its perpendicular distance from P. Choosing P at G makes $\bar{\mathbf r}=\mathbf 0$:

$$
\sum M_G=I_G\alpha \tag{3b}
$$

which holds for any type of motion. Equation (3) is useful when P is a point where unknown forces act, since they then drop out.

### Translation

In translation $\alpha=0$ and $\mathbf a_G=\mathbf a$. For rectilinear translation,

$$
\sum F_x=m(a_G)_x,\qquad\sum F_y=m(a_G)_y,\qquad\sum M_G=0
$$

or, about another point A, $\sum M_A=m a_Gd$ with $d$ the perpendicular distance from A to the line of action of $m\mathbf a_G$. For curvilinear translation, use n-t axes: $\sum F_n=m(a_G)_n$, $\sum F_t=m(a_G)_t$ and $\sum M_G=0$. The moment sum is zero only about G; about any other point the kinetic moment of $m\mathbf a_G$ must be included, and forgetting it is a common mistake (DAMS8-2, ll. 93–97).

A translating body must also be checked for tipping: the assumption $\alpha=0$ requires every normal reaction to come out positive. If one is negative, the body tips and the problem becomes general plane motion.

### Rotation about a fixed axis

For a body pinned at a fixed point O with G at distance $r_G$ from O, $(a_G)_t=r_G\alpha$ and $(a_G)_n=r_G\omega^2$ (towards O), so

$$
\sum F_n=mr_G\omega^2,\qquad\sum F_t=mr_G\alpha
$$

$\sum M_G=I_G\alpha$ is valid but inconvenient, because the pin reactions at O have moments about G. Take moments about O instead with equation (3): $m(a_G)_n$ passes through O and has no moment, and $m(a_G)_t$ has arm $r_G$:

$$
\sum M_O=I_G\alpha+m(a_G)_tr_G=I_G\alpha+mr_G^2\alpha
$$

$$
\boxed{\sum M_O=\left(I_G+mr_G^2\right)\alpha=I_O\alpha}
$$

by the parallel-axis theorem. In most fixed-axis problems this is the most convenient form, since the pin reactions drop out.

![[d_pinned_rod_released.png|900]]

### Rolling with and without slip

A wheel rolling on a surface is in general plane motion, and $\sum M_G=I_G\alpha$ holds whatever it does. The friction force at the contact behaves differently depending on whether the wheel slips.

**Without slip**, the kinematics of [[FEEG1002 D7 - Kinematics of Rigid Bodies#Rolling without slip|D7]] apply ($s=r\theta$, $v=r\omega$, $a=r\alpha$) and friction is static: its value comes from the equations, and $F_s\le\mu_sN$ must be satisfied. **With slip**, $a\neq r\alpha$, and friction is kinetic, $F_k=\mu_kN$, opposing the relative sliding at the contact. The friction force against the sliding velocity at the contact can take any value between $-\mu_sN$ and $+\mu_sN$ at zero sliding velocity, then jumps to $\pm\mu_kN$.

The direction of friction depends on how the wheel is driven. A wheel driven by a torque at its axle pushes back on the ground at the contact, so friction on the wheel acts forwards and propels it. A wheel pulled by a force at its centre would slide forwards at the contact, so friction acts backwards and is what makes it turn.

For a disc of mass $m$ and radius $r$ pulled by $P$ at its centre on level ground, the FBD gives

$$
P-F_f=ma_G,\qquad N-mg=0,\qquad F_fr=I_G\alpha
$$

three equations in four unknowns ($F_f$, $N$, $a_G$, $\alpha$). The fourth relation depends on whether the disc slips, which is not known in advance (slide p. 48):

1. Assume no slip and use $a_G=r\alpha$, with no friction law. Solve, then check $F_f\le\mu_sN$.
2. If the check fails, the disc slips: use $F_f=\mu_kN$ instead, with $a_G$ and $\alpha$ independent.

![[d_rolling_slip_check.png|900]]

## 4. Impulse and momentum for rigid bodies

The impulse-momentum principles of [[FEEG1002 D4 - Linear Impulse and Momentum|D4]] and [[FEEG1002 D5 - Angular Impulse and Momentum|D5]] carry over to rigid bodies (DAMS10, no slides). The **linear momentum** is $\mathbf L=m\mathbf v_G$. The **angular momentum** about a point P is the sum of the moments of the elements' momenta; the same expansion as for the kinetic moments, with velocities $\mathbf v_i=\mathbf v_G+\boldsymbol\omega\times\boldsymbol\rho_i$ in place of accelerations, gives

$$
H_P=\bar{\mathbf r}\times m\mathbf v_G+I_G\omega,\qquad H_G=I_G\omega
$$

perpendicular to the plane of motion. A translating body ($\omega=0$) has only the first term, which is zero about any point on the line of $\mathbf v_G$. A body rotating about a fixed axis O has $v_G=r_G\omega$, so $H_O=mr_G^2\omega+I_G\omega=I_O\omega$.

Integrating $\sum\mathbf F=m\mathbf a_G$ and the moment equation over time gives

$$
m(\mathbf v_G)_1+\sum\int_{t_1}^{t_2}\mathbf F\,dt=m(\mathbf v_G)_2
$$

$$
(H_P)_1+\sum\int_{t_1}^{t_2}M_P\,dt=(H_P)_2
$$

with P at G or at a point fixed in space: three scalar equations in plane motion. They are drawn as an initial momentum diagram ($m\mathbf v_G$ and $I_G\omega$), an impulse diagram and a final momentum diagram. If the external impulses (or their moments about P) sum to zero, linear (or angular) momentum is conserved. For collisions, take the whole system so that the impact impulses are internal, and choose P at a pin so that the pin's reaction impulse has no moment; the pin's impulse means that linear momentum is generally not conserved even when angular momentum is. A body that changes its own moment of inertia keeps $I\omega$ constant: a spinning chair speeds up as the arms are pulled in.

---

## Worked examples

### Handcart that must not tip

A 200 kg cart on light frictionless wheels is pushed by $P=50$ N at 60° below the horizontal on its handle. G is 0.2 m above the ground; wheel A is 0.3 m behind G and wheel B 0.2 m in front of it; the push acts at a point 0.5 m high and 0.6 m horizontally from G. Find the cart's acceleration and the wheel reactions (slides pp. 32–37; DAMS8-2a).

Assume the cart translates without tipping, so $\alpha=0$. Horizontally, only the horizontal component of $P$ acts:

$$
P\cos60°=ma_G
$$

$$
a_G=\frac{50\times0.5}{200}=0.125\ \mathrm{m/s^2}
$$

Vertically there is no acceleration:

$$
N_A+N_B=mg+P\sin60°=1962+43.3=2005\ \mathrm N
$$

For a translating body $\sum M_G=0$. Taking clockwise as positive, with the moment arms about G (0.3 m for $N_A$, 0.2 m for $N_B$, $0.5-0.2=0.3$ m for the horizontal component of $P$, and 0.6 m for its vertical component):

$$
0.3N_A-0.2N_B-0.3P\cos60°+0.6P\sin60°=0
$$

$$
0.3N_A-0.2N_B=-18.48\ \mathrm{N\,m}
$$

Solving with the vertical equation,

$$
N_A=765\ \mathrm N,\qquad N_B=1240\ \mathrm N
$$

Both are positive, so the no-tipping assumption holds. Had $N_A$ come out negative, the cart would tip about B and the motion would be general plane motion.

### Rod released from rest about a pivot

A uniform 15 kg rod 0.9 m long is pinned at O, 0.3 m from one end, and held horizontal by a cord at the far end. The cord is cut. Find the angular acceleration and the pin reaction at that instant (slides pp. 39–41; DAMS8-2b).

G is at the middle, $r_G=0.45-0.3=0.15$ m from O. The rod starts from rest, so $\omega=0$ and $(a_G)_n=r_G\omega^2=0$. The normal equation (along the rod) has nothing to balance, so the pin's normal reaction is $R_n=0$. About O, only the weight has a moment:

$$
I_O=\tfrac1{12}mL^2+mr_G^2=\tfrac1{12}\times15\times0.81+15\times0.0225=1.0125+0.3375=1.35\ \mathrm{kg\,m^2}
$$

$$
mgr_G=I_O\alpha
$$

$$
\alpha=\frac{15\times9.81\times0.15}{1.35}=16.35\ \mathrm{rad/s^2}
$$

Then the tangential equation (vertical, downwards positive) gives the pin's tangential reaction:

$$
mg-R_t=mr_G\alpha
$$

$$
R_t=15\times9.81-15\times0.15\times16.35=147.15-36.79=110.4\ \mathrm N
$$

These hold only at the instant of release; once the rod moves, $\omega\neq0$ and the weight's moment changes.

### Lawn roller pushed along the ground

A 40 kg lawn roller of radius 0.2 m and radius of gyration $k_G=R/\sqrt2$ is pushed by a 400 N force along its handle at 45° below the horizontal, applied at the axle. The coefficients of friction are $\mu_s=0.12$ and $\mu_k=0.1$. Does it slip, and what are its accelerations (slides pp. 49–52; DAMS8-3a)?

$I_G=mk_G^2=40\times0.02=0.8$ kg m². The push acts through G, so the roller is pulled at its centre and friction $F_A$ at the contact acts backwards. Take $x$ in the direction of motion and the roller turning forwards:

$$
F\cos\theta-F_A=ma_G \tag{4}
$$

$$
N_A-mg-F\sin\theta=0 \tag{5}
$$

$$
F_AR=I_G\alpha \tag{6}
$$

From (5), $N_A=392.4+282.8=675.2$ N. Assume no slip, $a_G=R\alpha$. From (6), $F_A=I_G\alpha/R$; substitute into (4):

$$
F\cos\theta=mR\alpha+\frac{I_G}{R}\alpha
$$

$$
\alpha=\frac{282.8}{40\times0.2+0.8/0.2}=\frac{282.8}{12}=23.57\ \mathrm{rad/s^2}
$$

$$
F_A=\frac{0.8\times23.57}{0.2}=94.3\ \mathrm N,\qquad a_G=0.2\times23.57=4.71\ \mathrm{m/s^2}
$$

Check: $\mu_sN_A=0.12\times675.2=81.0$ N, less than the 94.3 N needed. The roller slips. With slip, friction is kinetic:

$$
F_A=\mu_kN_A=0.1\times675.2=67.5\ \mathrm N
$$

$$
\alpha=\frac{F_AR}{I_G}=\frac{67.5\times0.2}{0.8}=16.9\ \mathrm{rad/s^2},\qquad a_G=\frac{282.8-67.5}{40}=5.38\ \mathrm{m/s^2}
$$

> [!check] Is the slip in the assumed direction?
> The contact point's velocity changes at $a_G-R\alpha=5.38-3.38=2.00$ m/s², forwards, so the roller slides forwards at the contact and kinetic friction indeed acts backwards. Both accelerations are constant.

### Driven wheel from the mock exam

A wheel of mass $m$, centroidal inertia $I_G$ and radius $R$ rolls without slip. It is driven by a torque $M$ and loaded at its hub by a vertical force $P_0$ (which includes its weight) and a backward horizontal force $H_0$, and a drag force $D$ acts backwards at height $h_D$ above the centre. Find $a_G$, the no-slip condition, and (with $D=bv_G$) the distance needed to reach speed $v_E$ from rest (mock exam, 25 marks, 15 May 2025).

The FBD has $P_0$, $H_0$, $M$, $D$, the normal reaction $N$ and the friction $F_f$, which acts forwards because the wheel is driven by a torque. Do not write $F_f=\mu_sN$. Horizontally and about G, taking the sense of $M$ as positive for $\alpha$:

$$
F_f-H_0-D=ma_G
$$

$$
M-F_fR-Dh_D=I_G\alpha
$$

Rolling without slip gives $\alpha=a_G/R$. From the moment equation,

$$
F_f=\frac MR-\frac{Dh_D}R-\frac{I_Ga_G}{R^2}
$$

and substituting into the force equation,

$$
\frac MR-\frac{Dh_D}{R}-\frac{I_G}{R^2}a_G-H_0-D=ma_G
$$

$$
a_G=\frac{M/R-D(1+h_D/R)-H_0}{m+I_G/R^2}
$$

an equivalent force divided by an equivalent mass that includes the rotational inertia. With $D=H_0=0$, the friction needed is $F_f=ma_G=\frac{m}{m+I_G/R^2}\frac MR$, and rolling without slip requires $F_f\le\mu_sN=\mu_sP_0$.

With $D=bv_G$, the acceleration takes the form $a_G=(A-Bv_G)/C$ with $A=M/R-H_0$ (N), $B=b(1+h_D/R)$ (kg/s) and $C=m+I_G/R^2$ (kg). It depends on speed, so use $a=v\,dv/ds$ from [[FEEG1002 D1 - Linear Motion of Particles#2. Choosing the integral|D1]]:

$$
ds=\frac{Cv_G\,dv_G}{A-Bv_G}
$$

$$
s_E=C\int_0^{v_E}\frac{v_G}{A-Bv_G}\,dv_G=\frac{C}{B^2}\left[A\ln\left|\frac{A}{A-Bv_E}\right|-Bv_E\right]
$$

which requires $v_E<A/B$, the terminal speed. With $A=2$, $B=3$, $C=4$ and $v_E=0.5$ (made-up values for a units check), $s_E=0.566$ m by both the formula and numerical integration.

### Wheel driven by a torque from rest

A wheel with radius 0.6 m and radius of gyration 0.4 m about its centre rolls without slip under a constant torque of 300 N m. Find its angular velocity after 6 s from rest (DAMS10-2, ll. 1–51). The mass is not recorded; 301 kg reproduces the quoted 11.5 rad/s, and 300 kg is used here.

Take angular impulse and momentum about the fixed point A on the ground at the initial contact. Friction acts along the ground, through A, so it has no moment about A. The normal force and the weight act on the same vertical line, through the contact point and G, and are equal and opposite, so their moments about A cancel; G moves parallel to the ground, so its height $r$ above A is the arm of $m\mathbf v_G$. Starting from rest,

$$
0+Mt=mv_Gr+I_G\omega_2
$$

with $v_G=\omega_2r$ and $I_G=mk_G^2$:

$$
Mt=m(r^2+k_G^2)\omega_2
$$

$$
\omega_2=\frac{300\times6}{300\times(0.36+0.16)}=11.5\ \mathrm{rad/s}
$$

### Falling rods with and without a point mass

Two identical uniform rods pivoted at their bottom ends are released from the same small angle; one carries an extra point mass part-way up. Which falls faster (L17b, ll. 15–78; Tutorial 8 Q3)?

About the pivot A, with the rod's combined centre of mass at $l_G$ from A and radius of gyration $k_A$, $mgl_G\sin\theta=mk_A^2\alpha$, so

$$
\alpha=\frac{l_G}{k_A^2}\,g\sin\theta
$$

The mass cancels; only the ratio $l_G/k_A^2$ matters. For a uniform rod of length $L$, $l_G=L/2$ and $k_A^2=L^2/3$, giving $l_G/k_A^2=3/(2L)$. Adding a point mass $m_p$ at distance $x$ from A gives a combined ratio $(mL/2+m_px)/(mL^2/3+m_px^2)$, which equals $3/(2L)$ when

$$
\frac{mL}{2}+m_px=\frac{3}{2L}\left(\frac{mL^2}{3}+m_px^2\right)
$$

$$
m_px=\frac{3m_px^2}{2L}\quad\Rightarrow\quad x=\frac{2L}3
$$

independent of either mass. A mass placed above $2L/3$ slows the rod; one placed below speeds it up. Neither mass nor weight alone decides it, because both the moment of the weight and the moment of inertia change.

![[d_t8_q3_falling_bars.png|900]]

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D7 - Kinematics of Rigid Bodies]] · Next: [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Mass Moment of Inertia and Radius of Gyration]] · [[Planar Rigid-Body Equations of Motion]] · [[Rolling Without Slip]] · [[Parallel Axis Theorem]] · [[Principle of Angular Impulse and Momentum]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Background: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] (second moments of area, the geometric analogue of $I$)
- Used again in: [[FEEG1002 D9 - Work and Energy for Rigid Bodies|D9]] (rotational kinetic energy $\tfrac12I_G\omega^2$) · [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] (rigid aircraft in three dimensions) · [[SESA2024 06 - Attitude Control]] (the inertia matrix of a spacecraft)

## Sources

- `Lecture 08 - Kinetics of Rigid Bodies.pdf`: slides pp. 1–52 (8.1 centre of mass and moment of inertia pp. 3–22, 8.2 equations of motion pp. 24–41, 8.3 rolling with and without slip pp. 43–52). There are no slides for rigid-body impulse and momentum.
- Transcript labels used in this note:
  - L18b = `FEEG1002 Lecture 2025-03-27.txt` (27 Mar 2025): cylinder race (ll. 248–321), centre of mass (ll. 322–453), moment of inertia (ll. 454–641), radius of gyration (ll. 642–685), equations of motion (ll. 722–788).
  - L17b = `FEEG1002 Lecture 2025-03-26.txt` (26 Mar 2025): falling-rods demo (ll. 15–78).
  - Mock = `FEEG1002 Lecture 2025-05-15.txt` (15 May 2025): driven-wheel mock question (ll. 14–566).
  - DAMS8-1a, DAMS8-1b, DAMS8-2, DAMS8-2a, DAMS8-2b, DAMS8-3, DAMS8-3a = `FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_1a.txt`, `..._1b.txt`, `..._2.txt`, `..._2a.txt`, `..._2b.txt`, `..._3.txt`, `..._3a.txt`.
  - DAMS10-1 to DAMS10-4b = `FEEG1002 Lecture 2021-04-18 - DAMS-10-impMomRigBod_1.txt`, `..._2.txt`, `..._3.txt`, `..._4.txt`, `..._4b.txt` (impulse and momentum for rigid bodies).
- `Tutorial Sheet 08 - Kinetics of Rigid Bodies.pdf`: Q1–Q5, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Show that a rod about its end has $I=\tfrac13mL^2$ with the parallel-axis theorem (DAMS8-1b, ll. 180–183). → [[#Parallel-axis theorem]]
- [ ] Prove the parallel-axis theorem (DAMS8-1b, ll. 117–118; L18b, ll. 616–618). → [[#Parallel-axis theorem]]
- [ ] Work out the friction direction for a wheel driven by a torque and one pulled at its centre (DAMS8-3, ll. 104–105). → [[#Rolling with and without slip]]
- [ ] Solve the lawn-roller equations with and without slip yourself (DAMS8-3a, ll. 60, 82–83). → [[#Lawn roller pushed along the ground]]
- [ ] Mock exam: all seven parts of the driven wheel, including the units of $A$, $B$, $C$ (Mock, ll. 14–566). → [[#Driven wheel from the mock exam]]
- [ ] Tutorial 8 Q1–Q2 (composite body, cam with a torque). → [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]
- [ ] Tutorial 8 Q3, falling bars (DAMS8-2b, ll. 76–78; L17b, ll. 59–60). → [[#Falling rods with and without a point mass]]
- [ ] Tutorial 8 Q4–Q5 (hoist, hoop on an incline). → [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]

### Further practice

- [ ] Hand-sliding demo: slide your hands together under a broom and explain why they meet at G (DAMS8-1a, ll. 147–152). → [[#1. Centre of mass]]
- [ ] Rolling race: derive $a=g\sin\theta/(1+k^2/r^2)$ for any round body (L18b, ll. 680–681). → [[#Radius of gyration]]
- [ ] Bar struck at its end by a particle: repeat with a general $e$ and with the pin away from G (DAMS10-4b, ll. 43–45, 63–66). → [[#4. Impulse and momentum for rigid bodies]]
- [ ] Spinning chair at home: arms in, arms out (DAMS10-3, ll. 42–43). → [[#4. Impulse and momentum for rigid bodies]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 08 slides)
> Where: [[#Lawn roller pushed along the ground]] · [[#Rolling with and without slip]].
>
> Slide p. 52 gives $F_A=67.54$ N; $0.1\times675.24=67.52$ N. Slide p. 48 says "DO NOT use $F_f=F_s=\mu_kN$", mixing subscripts; the meaning is that no friction law is used in the no-slip case, and $F_s\le\mu_sN$ is only checked afterwards.

### Transcript slips (L18b, DAMS8, DAMS10, Mock)

| Ref | Said | Correct |
|---|---|---|
| DAMS8-1b, ll. 52–53 | O "doesn't have to be a fixed point"; $\sum M=I\alpha$ holds about any point of the body | $\sum M=I\alpha$ holds about G or a fixed axis; about other points use the kinetic moments |
| DAMS8-1b, l. 145 | disc radius of gyration involves "square root of 2" | $k_G=R/\sqrt2$ |
| DAMS8-3, l. 38 | the normal load is "normally mg" | not in general: the lawn roller has $N_A=675$ N against $mg=392$ N |
| DAMS10-1, ll. 79–80 | P "can be anywhere" for angular impulse and momentum | P at G or a fixed point |
| DAMS10-4b, l. 73 | $\omega_2$ "3.8 something" | garbled; the data were not read out |
| Mock, l. 289 | "D times 1 minus HD over R" | $D(1+h_D/R)$, corrected at l. 297 |
| Mock, ll. 476–482 | $B$ in "1 over seconds" | kg/s |
| Mock, l. 222 | parts 1–3 worth "10 marks" | the stated marks sum to 8 |
