---
title: "FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, rigid-body, work-energy, rolling, instantaneous-centre]
sheet: "Dynamics Tutorial sheet 9 (work and energy for rigid bodies)"
theory_notes: ["[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
key_concepts: ["[[Kinetic Energy of a Rigid Body]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]", "[[Work-Energy Principle]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 09 - Work and Energy for Rigid Bodies.pdf"]
---

# FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions

> [!abstract] Sheet info
> Four questions on the work-energy principle for rigid bodies: a pinned rod with a spring, a spool rolled by a cord on its core, a spool unwinding down an incline from a cord tied to a wall, and a diver who rotates about his toes before falling. Each combines $KE=\tfrac12I\omega^2$ about a fixed axis or the instantaneous centre with a careful count of which forces do work. Final answers are printed for all four and are reproduced below; the diver's printed revolution count includes the quarter turn on the board.

## Q1 - Rod released against a spring

A uniform 30 kg rod of length $L=1.5$ m is pinned at O on the ceiling. A spring ($k=80$ N/m) runs from its end A to a ceiling support a distance $a=2$ m from O. The rod is released from rest at $\theta=0$ (horizontal, along the ceiling), where the spring is unstretched. Find $\omega$ at $\theta=30°$ below the horizontal.

Theory: [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rotation about a fixed axis]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#3. Potential energy and the work-energy principle]]

The rod rotates about the fixed pin O, whose reaction does no work. The weight and the spring are conservative, so energy is conserved between the release position and $\theta=30°$. Put the gravity datum at the level of O.

At $\theta=0$ the rod lies along the ceiling, A is 1.5 m from O, and the spring's length is $a-L=0.5$ m, its unstretched length. At $\theta=30°$ the spring's length follows from the cosine rule in the triangle formed by O, A and the spring support:

$$
l_2^2=a^2+L^2-2aL\cos30°=4+2.25-6\times0.866=1.054\ \mathrm{m^2}
$$

$$
l_2=1.027\ \mathrm m
$$

$$
\delta_2=l_2-0.5=0.527\ \mathrm m
$$

G, at the middle of the rod, is then $\tfrac L2\sin30°=0.375$ m below O, so

$$
V_{g2}=-mg\tfrac L2\sin30°=-30\times9.81\times0.375=-110.36\ \mathrm J
$$

$$
V_{e2}=\tfrac12k\delta_2^2=\tfrac12\times80\times0.527^2=11.09\ \mathrm J
$$

The rod rotates about its end, so

$$
I_O=\tfrac13mL^2=\tfrac13\times30\times1.5^2=22.5\ \mathrm{kg\,m^2}
$$

Conservation of energy from rest, with $V_{g1}=V_{e1}=0$:

$$
0=\tfrac12I_O\omega_2^2+V_{g2}+V_{e2}
$$

$$
\tfrac12\times22.5\,\omega_2^2=110.36-11.09=99.27\ \mathrm J
$$

$$
\omega_2=\sqrt{\frac{2\times99.27}{22.5}}
$$

$$
\boxed{\omega_2=2.97\ \mathrm{rad/s}}
$$

The spring takes back only about a tenth of the energy gravity releases over this range, because its stretch grows slowly at first.

## Q2 - Spool pulled by a cord from its core

A 75 kg spool ($k_O=0.675$ m, inner core $R_i=0.6$ m, outer rims $R_e=0.9$ m) rolls without slip on its rims. A cord wound round the core leaves the top of the core horizontally and is pulled with $P=200$ N. Starting from rest, find $\omega$ when the centre O has moved $s=3$ m to the right.

Theory: [[FEEG1002 D9 - Work and Energy for Rigid Bodies#General plane motion and the IC]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling wheels]]

The spool rolls without slip, so its contact point A is the instantaneous centre and every point moves as if rotating about A. The centre is $R_e$ above A and the cord's tangent point at the top of the core is $R_e+R_i$ above A, so

$$
v_O=\omega R_e,\qquad v_{\text{cord}}=\omega(R_e+R_i)
$$

and the cord end moves further than the centre in the ratio $(R_e+R_i)/R_e=1.5/0.9=5/3$. When O moves 3 m the cord is pulled through

$$
s_P=3\times\frac53=5\ \mathrm m
$$

and the work of $P$ is

$$
U_P=Ps_P=200\times5=1000\ \mathrm J
$$

No other force does work. The weight is perpendicular to the horizontal motion, and the normal force and the static friction act at A, which is momentarily at rest. As a check, $P$ moved to O is a force $P$ at O doing $Ps=600$ J plus a couple $PR_i$ turning through $s/R_e$ rad, doing $PR_is/R_e=400$ J, again 1000 J in total.

The kinetic energy about the IC needs the moment of inertia about A:

$$
I_A=m(k_O^2+R_e^2)=75\times(0.4556+0.81)=94.92\ \mathrm{kg\,m^2}
$$

$$
0+U_P=\tfrac12I_A\omega_2^2
$$

$$
\omega_2=\sqrt{\frac{2\times1000}{94.92}}
$$

$$
\boxed{\omega_2=4.59\ \mathrm{rad/s}}
$$

so the centre is then moving at $v_O=4.59\times0.9=4.13$ m/s.

## Q3 - Spool unwinding down an incline

A 60 kg spool ($k_G=0.3$ m, core $R_i=0.3$ m, rims $R_e=0.5$ m) sits on a 30° incline. A cord wound round the core leaves it on the incline side, parallel to the incline, and is tied to a wall up the slope. Released from rest, how far does the centre G travel down the incline before $\omega_2=6$ rad/s, (a) on a smooth incline and (b) with $\mu_k=0.2$ at the rim contact A?

Theory: [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rolling wheels]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#General plane motion and the IC]] · [[Instantaneous Centre of Rotation]]

### Where the instantaneous centre is

The cord is inextensible and tied to a fixed wall, so the point of the core where the cord leaves it cannot move along the cord. It cannot move perpendicular to the incline either, because G moves parallel to the incline and that point lies on the normal through G, so rotation only moves it along the cord direction. Its velocity is therefore zero: the cord's tangent point, a distance $R_i$ from G towards the incline, is the instantaneous centre. A is not, and the spool does not roll on its rims. Hence

$$
v_G=\omega R_i
$$

and a descent $d$ of the centre corresponds to a rotation $\theta=d/R_i$.

The rim contact A lies on the same normal, a further $R_e-R_i=0.2$ m beyond the IC from G, so it moves in the opposite direction to G, up the slope, at

$$
v_A=\omega(R_e-R_i)=\frac{R_e-R_i}{R_i}v_G=\tfrac23v_G
$$

A slides over the incline the whole time, and the slippage distance while G descends $d$ is

$$
\Delta s_{sl}=\tfrac23d
$$

the same as the general formula $\Delta s_{sl}=|x_G-R_e\theta|=|d-\tfrac53d|=\tfrac23d$.

![[d_t9_spools_ic.png|880]]

### Kinetic energy at the end

About the IC, at distance $R_i$ from G,

$$
I_{IC}=m(k_G^2+R_i^2)=60\times(0.09+0.09)=10.8\ \mathrm{kg\,m^2}
$$

$$
KE_2=\tfrac12I_{IC}\omega_2^2=\tfrac12\times10.8\times36=194.4\ \mathrm J
$$

The cord tension acts at the IC and does no work, and the normal force is perpendicular to the motion of A.

### Smooth incline

Only the weight does work, $mgd\sin30°$:

$$
0+mgd\sin30°=KE_2
$$

$$
d=\frac{194.4}{60\times9.81\times0.5}=\frac{194.4}{294.3}
$$

$$
\boxed{d=0.661\ \mathrm m}
$$

### Rough incline

The cord is parallel to the incline and G has no acceleration normal to it, so

$$
N=mg\cos30°=60\times9.81\times0.866=509.7\ \mathrm N
$$

$$
F=\mu_kN=0.2\times509.7=101.9\ \mathrm N
$$

Friction opposes the sliding of A, so it acts down the slope on the spool, and its work is negative over the slippage distance, not over the distance G travels:

$$
U_F=-F\,\Delta s_{sl}=-101.9\times\tfrac23d=-67.97\,d
$$

$$
mgd\sin30°-67.97\,d=KE_2
$$

$$
(294.3-67.97)\,d=194.4
$$

$$
\boxed{d=0.859\ \mathrm m}
$$

> [!warning] The rim contact is not the instantaneous centre
> Treating A as the IC, as for a spool rolling on its rims, gives $I_A=m(k_G^2+R_e^2)$ and $d=1.25$ m for part (a), and puts no work into friction for part (b). The cord fixes the IC at its tangent point; A slides. A kinetics check confirms the energy answers: $a_G=2.45$ m/s² (smooth) and 1.89 m/s² (rough), the cord stays taut (tension 283 N in the rough case), and $\omega=6$ rad/s is reached after the same 0.661 m and 0.859 m.

## Q4 - Diver rotating off the board

A 75 kg diver crouches at the end of a board with $k_G=0.36$ m about his centre of mass and G at $r_G=0.45$ m from his toes A. He rotates rigidly about A from $\theta=0$ (G directly above A) to $\theta=90°$ (G level with A), then leaves the board. How many revolutions, counted from $\theta=0$, does he make before reaching the water $h=10$ m below the board?

Theory: [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rotation about a fixed axis]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#4. Translational or rotational?]]

### On the board

While his toes stay on the board the diver rotates about the fixed point A, and the reaction there does no work. G falls through $r_G(1-\cos\theta)$, which is $r_G$ by $\theta=90°$. Energy conservation from rest:

$$
mgr_G=\tfrac12I_A\omega^2=\tfrac12m(k_G^2+r_G^2)\omega^2
$$

$$
\omega^2=\frac{2gr_G}{k_G^2+r_G^2}=\frac{2\times9.81\times0.45}{0.1296+0.2025}=\frac{8.829}{0.3321}=26.59\ \mathrm{rad^2/s^2}
$$

$$
\omega=5.156\ \mathrm{rad/s}
$$

At $\theta=90°$ the line AG is horizontal, so G's velocity, perpendicular to AG, is vertical and downwards:

$$
v_G=\omega r_G=5.156\times0.45=2.320\ \mathrm{m/s}
$$

### In the air

Once he leaves the board the only force is his weight, which acts through G. It has no moment about G, so $\alpha=0$ and he keeps spinning at $\omega=5.156$ rad/s; gravitational energy now goes only into the translational part of the kinetic energy. G starts at board level moving down at 2.320 m/s and falls $h=10$ m to the water:

$$
h=v_Gt+\tfrac12gt^2
$$

$$
4.905t^2+2.320t-10=0
$$

$$
t=\frac{-2.320+\sqrt{2.320^2+4\times4.905\times10}}{2\times4.905}=\frac{-2.320+14.198}{9.81}=1.211\ \mathrm s
$$

The rotation in the air is

$$
\omega t=5.156\times1.211=6.243\ \mathrm{rad}=0.994\ \mathrm{rev}
$$

and adding the quarter turn on the board,

$$
N=0.25+0.994
$$

$$
\boxed{N=1.24\ \text{revolutions from }\theta=0}
$$

> [!warning] What the printed 1.24 counts
> The printed answer, "1.24 revolutions (from the initial vertical position)", includes the quarter revolution made on the board. The rotation during the flight alone is 0.994 rev, just under one full turn. Both readings use the idealisation that G falls exactly 10 m, from board level to the water surface, with the diver treated as rigid throughout.

![[d_t9_q4_diver.png|880]]

## Links

- Topic note: [[FEEG1002 D9 - Work and Energy for Rigid Bodies]] · moments of inertia from [[FEEG1002 D8 - Kinetics of Rigid Bodies]]
- Concepts: [[Kinetic Energy of a Rigid Body]] · [[Work-Energy Principle]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]] · [[Conservative Forces and Potential Energy]]
- Hub: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous sheet: [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]]

## Sources

- `Tutorial Sheet 09 - Work and Energy for Rigid Bodies.pdf` (Q1–Q4, final answers printed on the sheet).
- The slippage distance needed in Q3 was introduced as something to be worked out in the tutorial in `FEEG1002 Lecture 2021-04-11 - DAMS09-WorkEnergy-RigidBodies-2.txt` (DAMS9-2, ll. 127–130).
