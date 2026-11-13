---
title: "FEEG1002 D9 - Work and Energy for Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 9
tags: [feeg1002, dynamics, rigid-body, work, energy, rolling]
aliases: ["Dynamics Lecture 9", "Rigid body energy", "Rotational kinetic energy", "Work of a couple"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 9 (slides pp. 1-52) in full: kinetic energy of a rigid body in translation, rotation about a fixed axis and general plane motion (including the IC form), systems of bodies, work of forces and moments, forces that do no work, rolling with and without slip, rolling resistance, internal forces, potential energy, the work-energy principle and conservation of energy, with the disc, rod-in-slots and rod-and-spring examples. Pre-recorded DAMS9-1 to DAMS9-5 only; no live 2025 lecture covered this chapter. The rolling race from L18b (27 Mar 2025, ll. 248-321)."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
next_topics: []
key_concepts: ["[[Kinetic Energy of a Rigid Body]]", "[[Work-Energy Principle]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-2b.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-3.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-4.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-5.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-27.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 09 - Work and Energy for Rigid Bodies.pdf"]
---

# FEEG1002 D9 - Work and Energy for Rigid Bodies

> [!abstract] Summary
> The kinetic energy of a rigid body in plane motion is the sum of a translational part and a rotational part, $KE=\tfrac12mv_G^2+\tfrac12I_G\omega^2$; for rotation about a fixed axis O it reduces to $\tfrac12I_O\omega^2$, and at any instant it can be written $\tfrac12I_{IC}\omega^2$ about the instantaneous centre. Forces do work $\int\mathbf F\cdot d\mathbf r$ and couples do work $\int M\,d\theta$; pin reactions, normal forces and the friction on a wheel rolling without slip do none. With weight and springs as potential energy, the work-energy principle $KE_1+V_{g1}+V_{e1}+\sum U_{1-2}=KE_2+V_{g2}+V_{e2}$ gives the speed of a mechanism in one scalar equation, and how the energy splits between translation and rotation follows from the kinematics.

> [!summary]- Exam use: quick path
> - **Use it when:** a body or mechanism moves between two positions and a speed or angular velocity (or a distance) is wanted, with no time or acceleration asked.
> - **Assumptions:** rigid bodies, planar motion; weight acts at G; rolling without slip unless stated; potential energy from a stated datum.
> - **Method:** 1. Choose states 1 and 2 and the datum for $V_g$ (height of G). 2. Write each body's kinetic energy: $\tfrac12mv_G^2$, $\tfrac12I_O\omega^2$, $\tfrac12mv_G^2+\tfrac12I_G\omega^2$ or $\tfrac12I_{IC}\omega^2$, using the kinematics to express everything in one unknown. 3. Draw the FBD; drop forces that do no work, put weight and springs into $V$, and find the work of the rest ($Fs\cos\theta$, $M\Delta\theta$, $-\mu_kN\Delta s_{sl}$). 4. Write the principle and solve. 5. Check the sign and compare with an obvious limit.
> - **Common mistakes:** forgetting the rotational kinetic energy of a rolling wheel; counting work for the friction on a wheel that rolls without slip.
> - **Practise:** [[#Rod sliding in two slots]] · [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]] (Q2 spool)

The work-energy principle of [[FEEG1002 D3 - Work, Energy and Power|D3]] carries over to rigid bodies with two additions. A rotating body stores kinetic energy in its spin as well as in the motion of its centre of mass, and a couple does work as it turns the body. A solid cylinder rolling down a slope converts its loss of potential energy into both forms; a frictionless block sliding down the same slope puts all of it into translation and so arrives faster, and a hollow cylinder, with more of its mass at the rim, puts a larger share into spin and arrives slowest.

The energy method is particularly attractive for mechanisms with one degree of freedom (a rod sliding in slots, a crank and piston, a spool on a cord), because the kinematics of [[FEEG1002 D7 - Kinematics of Rigid Bodies|D7]] expresses every body's motion in terms of one angular velocity, and a single scalar equation then gives it. The internal pin forces between parts do no net work, so they never need to be found.

---

## 1. Kinetic energy of a rigid body

### Derivation

The kinetic energy of a body is the sum of the kinetic energies of its elements:

$$
KE=\tfrac12\int v^2\,dm
$$

Write each element's velocity with the relative velocity equation of [[FEEG1002 D7 - Kinematics of Rigid Bodies#The relative velocity equation|D7]], taking G as the reference point and $\boldsymbol\rho$ as the element's position from G:

$$
\mathbf v=\mathbf v_G+\boldsymbol\omega\times\boldsymbol\rho
$$

$$
v^2=\mathbf v\cdot\mathbf v=v_G^2+2\mathbf v_G\cdot(\boldsymbol\omega\times\boldsymbol\rho)+|\boldsymbol\omega\times\boldsymbol\rho|^2
$$

In plane motion $\boldsymbol\omega\perp\boldsymbol\rho$, so $|\boldsymbol\omega\times\boldsymbol\rho|=\omega\rho$. Integrating over the body:

$$
KE=\tfrac12v_G^2\int dm+\mathbf v_G\cdot\left(\boldsymbol\omega\times\int\boldsymbol\rho\,dm\right)+\tfrac12\omega^2\int\rho^2\,dm
$$

The middle integral is zero because G is the centre of mass, and the last is $I_G$:

$$
\boxed{KE=\tfrac12mv_G^2+\tfrac12I_G\omega^2}
$$

the translational and rotational kinetic energies. The total alone does not say how it is split; that needs the kinematics or a further equation (section 4).

### Translation

With $\omega=0$, every point moves at $v_G$ and $KE=\tfrac12mv_G^2$, as for a particle.

### Rotation about a fixed axis

A body rotating about a fixed axis O has $v_G=r_G\omega$, so

$$
KE=\tfrac12m(r_G\omega)^2+\tfrac12I_G\omega^2=\tfrac12\left(mr_G^2+I_G\right)\omega^2
$$

$$
KE=\tfrac12I_O\omega^2
$$

by the parallel-axis theorem. If O is at G, $v_G=0$ and $KE=\tfrac12I_G\omega^2$. A body rotating about an axis away from G has translational kinetic energy as well as rotational; the $I_O$ form packages both, which is possible because the kinematics ties $v_G$ to $\omega$.

### General plane motion and the IC

In general both terms are needed. If the instantaneous centre is known, then at that instant $v_G=\omega r_{G/IC}$, and the same step gives

$$
KE=\tfrac12\left(mr_{G/IC}^2+I_G\right)\omega^2=\tfrac12I_{IC}\omega^2
$$

valid only at the instant considered, because the IC moves. It is the convenient form at the start and end positions of a work-energy calculation.

### Systems of bodies

Energy is a scalar, so for several connected bodies the kinetic energies add: $KE=\sum KE_i$. For a crank mechanism, the crank disc rotating about its centre has $\tfrac12I_G\omega^2$, the connecting rod in general plane motion has $\tfrac12mv_G^2+\tfrac12I_G\omega_{rod}^2$, and the translating piston has $\tfrac12mv^2$.

## 2. Work of forces and couples

The work of a force is as for particles:

$$
U_F=\int\mathbf F\cdot d\mathbf r=\int F\cos\theta\,ds
$$

and for a constant force on a straight path $U=F\cos\theta\,s$.

### Work of a couple

A couple of moment $M$ can be represented by two equal and opposite forces $F$ a distance $d$ apart, $M=Fd$. As the body turns through $d\theta$ about the midpoint between them, each force's point of application moves through an arc $(d/2)\,d\theta$ in the direction of the force, so the pair does work

$$
dU_M=2F\frac d2\,d\theta=Fd\,d\theta=M\,d\theta
$$

Any translation of the body moves both forces equally, and their works cancel. So

$$
\boxed{U_M=\int_{\theta_1}^{\theta_2}M\,d\theta}
$$

and for a constant moment $U_M=M(\theta_2-\theta_1)$. The work is positive when the moment and the rotation are in the same sense, and negative when they oppose, as for a brake.

### Forces that do no work

A force does no work if its point of application does not move, or moves perpendicular to the force. That rules out:

- the pin reaction at a fixed axis of rotation;
- the normal reaction on a body moving along a surface;
- the weight, for motion in a horizontal plane;
- the friction (and normal force) on a wheel rolling without slip, since the contact point is instantaneously at rest;
- internal forces in equal and opposite pairs, between points that do not move apart, with exceptions noted below.

### Rolling wheels

For a wheel rolling without slip and pulled by a force $P$ at its centre, the weight is perpendicular to the motion, the normal force and the static friction act at the contact point, which has zero velocity, and only $P$ does work; the friction points backwards. If a torque $M$ drives the wheel instead, only $M$ does work and the friction points forwards. A wheel rolling freely on level ground with no applied load has only its weight and the normal force on it, neither of which does work, so a rigid wheel would roll for ever. It cannot have a friction force either, since a friction force with no other horizontal load would decelerate it.

Real wheels slow down because of **rolling resistance** $R_r$, caused by deformation and hysteresis of the wheel and the ground. It is modelled as an external force opposing the motion, a fraction of the weight, and it does negative work. To keep a constant speed against it, an external force or moment must act, and then a static friction force exists even at constant speed.

If the wheel slips, the friction is kinetic and does negative work over the distance actually slid at the contact, the **slippage distance**:

$$
U=-F_k\,\Delta s_{sl},\qquad\Delta s_{sl}=|x_G-R\theta|
$$

where $x_G$ is the actual displacement of the centre and $R\theta$ the displacement it would have had rolling without slip. This is not the displacement of the wheel. A wheel pulled hard at the hub slides far and turns little; one driven hard by a torque spins a lot and moves little. Slip can also come from the initial conditions, as when an aircraft wheel touches down without turning, or a ball is thrown with backspin.

### Internal forces

The internal forces holding a rigid body together do no work, because its points do not move apart. Between bodies in relative motion they can. A crate on an accelerating lorry is accelerated by static friction, which does positive work on the crate and equal negative work on the lorry, so none for the two together. Inside a vehicle, the pistons and the engine casing, the drive shaft and the chassis, and the brake pads and the wheels all move relative to each other, and the internal forces between them do work; that is how a vehicle accelerates and brakes.

## 3. Potential energy and the work-energy principle

The weight's potential energy uses the height of the centre of mass above the datum, $V_g=mgy_G$; far from the Earth, $-Gm_1m_2/r$ still applies. A spring has $V_e=\tfrac12k(l-l_0)^2$, with its length $l$ found from the geometry, often by the cosine rule $l^2=b^2+c^2-2bc\cos\theta$.

The work-energy principle for a rigid body or system of bodies is, as in [[FEEG1002 D3 - Work, Energy and Power#3. The work-energy principle|D3]],

$$
KE_1+\sum U_{1-2}=KE_2
$$

with $KE$ now including rotation, or in the form preferred for problems,

$$
\boxed{KE_1+V_{g1}+V_{e1}+\sum U_{1-2}=KE_2+V_{g2}+V_{e2}}
$$

where $\sum U_{1-2}$ is the work of the non-conservative forces and couples. With only conservative forces, energy is conserved: $KE_1+V_{g1}+V_{e1}=KE_2+V_{g2}+V_{e2}$.

## 4. Translational or rotational?

The energy equation gives the total kinetic energy only. To split it, use kinematics (for pure rotation about an end, $v_G=(l/2)\dot\theta$) or kinetics, a second equation such as $\sum M_G=I_G\alpha$.

A bar thrown upwards while spinning shows this. Gravity acts at G, so $\sum M_G=0$, $\alpha=0$ and the spin $\omega$ stays constant throughout the flight. The rotational kinetic energy never changes; the potential energy is exchanged only with the translational part, so G rises exactly as high as a non-spinning bar thrown at the same speed.

---

## Worked examples

### Disc turned by a couple and a cord

A 30 kg uniform disc of radius 0.2 m, pinned at its centre O, starts from rest. A constant couple of 5 N m and a constant 10 N pull on a cord wrapped round its rim both turn it the same way. How many revolutions does it make before reaching 20 rad/s (DAMS9-3)?

The disc rotates about a fixed axis through G:

$$
I_O=\tfrac12mR^2=\tfrac12\times30\times0.2^2=0.6\ \mathrm{kg\,m^2}
$$

$$
KE_2=\tfrac12I_O\omega_2^2=\tfrac12\times0.6\times20^2=120\ \mathrm J
$$

The pin reaction and the weight act at the fixed centre and do no work. The couple does $M\theta$. The cord does not slip, so its end moves $R\theta$ as the disc turns through $\theta$, and the force does $FR\theta$. Both are positive. With $KE_1=0$:

$$
0+M\theta+FR\theta=KE_2
$$

$$
\theta=\frac{120}{5+10\times0.2}=\frac{120}{7}=17.14\ \mathrm{rad}=2.73\ \mathrm{rev}
$$

### Rod sliding in two slots

A uniform 10 kg rod of length 0.8 m has its ends A and B in a vertical and a horizontal slot respectively, with light blocks and no friction. It starts from rest vertical ($\theta=0$, measured from the vertical) and a constant 50 N force pulls B horizontally. Find $\omega$ when $\theta=45°$, with the mechanism in a vertical plane and in a horizontal plane (DAMS9-4).

![[d_rod_in_slots_example.png|900]]

The rod is in general plane motion. A moves vertically and B horizontally, so the IC is where the horizontal through A meets the vertical through B. G, the midpoint of the rod, is the midpoint of the hypotenuse of the right triangle A-IC-B, so $r_{G/IC}=L/2$ for every $\theta$ (a property of this geometry, not a general one). Hence

$$
KE_2=\tfrac12\left(m\frac{L^2}{4}+\frac{mL^2}{12}\right)\omega_2^2=\tfrac12\times\frac{mL^2}{3}\omega_2^2=\tfrac12\times2.133\,\omega_2^2
$$

The same follows from absolute motion: with $x_G=\tfrac12L\sin\theta$ and $y_G=\tfrac12L\cos\theta$, $\dot x_G=\tfrac12L\dot\theta\cos\theta$ and $\dot y_G=-\tfrac12L\dot\theta\sin\theta$, so $v_G^2=\tfrac14L^2\dot\theta^2$.

The datum for $V_g$ is at the level of the horizontal slot, so $V_{g1}=mgL/2$ and $V_{g2}=mg(L/2)\cos45°$. The slot reactions do no work. B moves $L\sin45°$ in the direction of $P$, so $U_P=PL\sin45°=50\times0.8\times0.7071=28.28$ J. In the vertical plane:

$$
0+mg\frac L2+U_P=\tfrac12I_{IC}\omega_2^2+mg\frac L2\cos45°
$$

$$
\omega_2=\sqrt{\frac{2\left[mg\frac L2(1-\cos45°)+PL\sin45°\right]}{mL^2/3}}=\sqrt{\frac{2(11.49+28.28)}{2.133}}=6.11\ \mathrm{rad/s}
$$

In the horizontal plane the weight does no work and only $P$ counts:

$$
\omega_2=\sqrt{\frac{2\times28.28}{2.133}}=5.15\ \mathrm{rad/s}
$$

The vertical-plane answer is larger because gravity does positive work as the rod falls.

### Rod and spring released from rest

A uniform 10 kg rod AB, 0.4 m long, has end A in a horizontal slot and end B in a vertical slot, with light pistons. A spring of stiffness 800 N/m on B is unstretched when the rod is horizontal ($\theta=0$, measured from the horizontal). The rod is released from rest at $\theta=30°$. Find $\omega$ as it passes $\theta=0$, in a vertical and in a horizontal plane (DAMS9-5).

Only the weight and the spring do work, both conservative, so energy is conserved. The datum is the rod's position at $\theta=0$, so $V_{g2}=V_{e2}=0$. At $\theta_1=30°$, G is $\tfrac12L\sin30°$ below the datum and the spring is stretched by the drop of B, $L\sin30°$:

$$
V_{g1}=-mg\frac L2\sin30°=-9.81\ \mathrm J,\qquad V_{e1}=\tfrac12k(L\sin30°)^2=\tfrac12\times800\times0.2^2=16.0\ \mathrm J
$$

At $\theta=0$, B moves vertically and A momentarily has zero velocity (it is at the end of its travel), so A is the IC and $r_{G/IC}=L/2$:

$$
KE_2=\tfrac12\left(m\frac{L^2}{4}+\frac{mL^2}{12}\right)\omega_2^2=\tfrac12\times\frac{10\times0.16}{3}\omega_2^2=\tfrac12\times0.5333\,\omega_2^2
$$

In the vertical plane:

$$
0-9.81+16.0=\tfrac12\times0.5333\,\omega_2^2
$$

$$
\omega_2=\sqrt{\frac{2\times6.19}{0.5333}}=4.82\ \mathrm{rad/s}
$$

In the horizontal plane there is no gravity term:

$$
\omega_2=\sqrt{\frac{2\times16.0}{0.5333}}=7.75\ \mathrm{rad/s}
$$

larger, because the spring does not have to lift the rod. The motion carries on past $\theta=0$ as an undamped oscillation.

### Rolling race down a slope

A solid cylinder, a thin-walled hollow cylinder and a frictionless block are released together down the same slope and drop through a height $h$. Which arrives first, and how is the energy shared?

Each round body rolls without slip, so friction does no work and energy is conserved. With radius $r$, radius of gyration $k$ and $v=r\omega$:

$$
mgh=\tfrac12mv^2+\tfrac12mk^2\frac{v^2}{r^2}=\tfrac12mv^2\left(1+\frac{k^2}{r^2}\right)
$$

$$
v=\sqrt{\frac{2gh}{1+k^2/r^2}}
$$

The mass and the size cancel; only $k/r$ matters. The fraction of kinetic energy in translation is $1/(1+k^2/r^2)$.

| Body | $k^2/r^2$ | $v$ for $h=1$ m | Translational share |
|---|---|---|---|
| frictionless block | 0 | 4.43 m/s | 100% |
| solid cylinder | 1/2 | 3.62 m/s | 2/3 |
| hollow cylinder | 1 | 3.13 m/s | 1/2 |

The speed at every height is in the same ratio, so the order of arrival is the same: block, solid cylinder, hollow cylinder. Since $v^2\propto h$ for each, the accelerations are constant at $g\sin\theta/(1+k^2/r^2)$, which is $\tfrac23g\sin\theta$ for the solid cylinder and $\tfrac12g\sin\theta$ for the hollow one.

![[d_rolling_race_energy_split.png|900]]

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · Next: end of the Dynamics stream
- Concepts: [[Kinetic Energy of a Rigid Body]] · [[Work-Energy Principle]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]] · [[Conservative Forces and Potential Energy]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[SESA2028 S7 - Strain Energy and Conservation of Energy]] (energy methods for structures) · [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

## Sources

- `Lecture 09 - Work and Energy for Rigid Bodies.pdf`: slides pp. 1–52 (9.1 kinetic energy pp. 5–12, 9.2 work and the work-energy principle pp. 13–34, examples pp. 35–52).
- Transcript labels used in this note:
  - DAMS9-1 = `FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-1.txt` (kinetic energy); DAMS9-2 = `...-2.txt` (work, rolling, slip); DAMS9-2b = `...-2b.txt` (internal forces, potential energy, the principle, spinning bar); DAMS9-3, DAMS9-4, DAMS9-5 = `...-3.txt`, `...-4.txt`, `...-5.txt` (examples I–III).
  - L18b = `FEEG1002 Lecture 2025-03-27.txt` (27 Mar 2025): rolling-cylinders race (ll. 248–321).
- `Tutorial Sheet 09 - Work and Energy for Rigid Bodies.pdf`: Q1–Q4, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Find where $I_G=mL^2/12$ comes from (DAMS9-4, ll. 24–25). → [[FEEG1002 D8 - Kinetics of Rigid Bodies#Disc and slender rod]]
- [ ] Rod in slots by the IC and by absolute motion, whichever you prefer (DAMS9-4, l. 63). Targets 6.11 and 5.15 rad/s. → [[#Rod sliding in two slots]]
- [ ] Disc example. Target 2.73 rev. → [[#Disc turned by a couple and a cord]]
- [ ] Rod-and-spring example. Targets 4.82 and 7.75 rad/s. → [[#Rod and spring released from rest]]
- [ ] Tutorial 9 Q1–Q2 (rod and spring, spool on a cord). → [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]
- [ ] Tutorial 9 Q3, the spool on an incline including the slippage distance (DAMS9-2, l. 129). → [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]

### Further practice

- [ ] Read the full kinetic-energy derivation (optional, DAMS9-1, ll. 44–46). → [[#Derivation]]
- [ ] Redo the rod-and-spring example including the piston masses (DAMS9-5, ll. 16–18). → [[#Rod and spring released from rest]]
- [ ] Tutorial 9 Q4, the diver. → [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 09 slides)
> Where: [[#Rolling wheels]] · [[#3. Potential energy and the work-energy principle]].
>
> Slide p. 23 writes the slippage distance as $\Delta s_{sl}$ in the text and $\Delta_{sl}=|x_G-R\theta|$ in its box. Slide p. 30 refers to "$V_g$ and $V_k$" where $V_e$ is meant. Slides pp. 37 and 38 call the same disc's moment of inertia $I_O$ and $I_G$ (they coincide here). Slide p. 40 gives $P=50$ N only in the figure, not in the list of data.

### Transcript slips (DAMS9)

| Ref | Said | Correct |
|---|---|---|
| DAMS9-2b, l. 127 | "the angular velocity of the bar is zero" | the angular acceleration is zero, so the angular speed is constant (l. 128) |
| DAMS9-2b, l. 130 | energy exchanged "between elastic gravitational potential energy and kinetic energy" | gravitational only; there is no spring |
| DAMS9-5, l. 8 | stiffness "800 newton meter" | 800 N/m |
