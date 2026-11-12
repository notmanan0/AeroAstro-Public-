---
title: "FEEG1002 D5 - Angular Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 5
tags: [feeg1002, dynamics, angular-momentum, central-force, orbits]
aliases: ["Dynamics Lecture 5", "Angular momentum", "Conservation of angular momentum", "Central force motion"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 5 (slides pp. 1-33) in full: moment of a vector, angular momentum of a particle, the right-hand rule, the moment equation sum M_O = dH_O/dt, the principle of angular impulse and momentum, conservation of angular momentum and central forces, with the amusement-park ride and elliptical-orbit examples. Pre-recorded DAMS6-1 to DAMS6-3 (the theory); live problem class L10b (27 Feb 2025) with quizzes; the fun-fair game from the L11 revision lecture (5 Mar 2025, ll. 412-629). The live theory lecture of 26 Feb 2025 has no transcript."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
next_topics: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
key_concepts: ["[[Principle of Angular Impulse and Momentum]]", "[[Orbital Angular Momentum]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 05 - Angular Impulse and Momentum.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-27.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-05.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-02-19 - DAMS-6-AngImpMom_1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-02-19 - DAMS-6-AngImpMom_2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-02-19 - DAMS-6-AngImpMom_3.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 05 - Angular Impulse and Momentum.pdf"]
---

# FEEG1002 D5 - Angular Impulse and Momentum

> [!abstract] Summary
> The angular momentum of a particle about a point O is the moment of its linear momentum, $\mathbf H_O=\mathbf r\times m\mathbf v$, which in a plane has magnitude $mvd$ with $d$ the perpendicular distance from O to the line of the velocity. Taking the moment of Newton's second law about a fixed point gives $\sum\mathbf M_O=d\mathbf H_O/dt$, and integrating over time gives the principle of angular impulse and momentum, $(\mathbf H_O)_1+\sum\int\mathbf M_O\,dt=(\mathbf H_O)_2$. If the forces have no net moment about O, angular momentum about O is conserved; this is always so for a central force, which is why a body pulled inwards on a cord speeds up and a satellite moves fastest at perigee.

> [!summary]- Exam use: quick path
> - **Use it when:** a particle moves on a curved path under a force directed at a fixed point (cord to a pivot, spring pinned at one end, gravity of a planet), or moments, speeds and times are linked.
> - **Assumptions:** O is a fixed point in an inertial frame; plane motion, so all moments are about the $z$ axis; anticlockwise (out of the page) positive.
> - **Method:** 1. Name the point O about which the forces have no moment (the centre of attraction, the pivot). 2. Resolve each velocity into its radial component and the component $v'$ perpendicular to $\mathbf r$. 3. Write $r_1mv_1'=r_2mv_2'$ (or include $\int M_O\,dt$ if there is a moment). 4. Add energy conservation or the work-energy principle for the second unknown. 5. Recover the full speed from both components.
> - **Common mistakes:** saying "angular momentum is conserved" without naming the point; using the full speed instead of its component perpendicular to $\mathbf r$ on a non-circular path.
> - **Practise:** [[#Amusement-park ride pulled in on a cable]] · [[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]] (Q4 satellite)

Linear momentum is conserved when no net external impulse acts, but many particles move under a force that is far from zero. A satellite is pulled by gravity throughout its orbit; a ball whirled on a string is pulled by the string. In both cases the force always points at one fixed point. A force through a point has no moment about that point, so although the momentum $m\mathbf v$ keeps changing, its moment about the point does not.

That moment, the angular momentum, is the rotational counterpart of linear momentum. Pulling the string in shortens the lever arm, so to keep the product of lever arm and momentum constant the speed must rise: the shorter the faster. The same reasoning says a satellite in an elliptical orbit is fastest closest to the Earth and slowest furthest away, and combined with energy conservation it fixes both the speed and the distance at the far point.

---

## 1. Moment of a vector

The moment of a vector about a point O is itself a vector, $\mathbf r\times(\text{vector})$, where $\mathbf r$ runs from O to the point of application. O is chosen for convenience and need not be on any body. Two cases are used.

The **moment of a force** (torque) about O is

$$
\mathbf M_O=\mathbf r\times\mathbf F
$$

It can be calculated whether or not anything rotates.

The **moment of linear momentum**, or **angular momentum**, about O is

$$
\mathbf H_O=\mathbf r\times m\mathbf v
$$

in kg m²/s. In three dimensions both are found from a determinant,

$$
\mathbf M_O=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\r_x&r_y&r_z\\F_x&F_y&F_z\end{vmatrix}=(r_yF_z-r_zF_y)\mathbf i-(r_xF_z-r_zF_x)\mathbf j+(r_xF_y-r_yF_x)\mathbf k
$$

and the same with $mv_x$, $mv_y$, $mv_z$ in the bottom row for $\mathbf H_O$.

### Plane motion

In the $x$-$y$ plane $r_z=F_z=0$ and only the $\mathbf k$ term survives:

$$
\mathbf M_O=(r_xF_y-r_yF_x)\,\mathbf k
$$

Writing $r_x=r\cos\theta_1$, $r_y=r\sin\theta_1$, $F_x=F\cos\theta_2$, $F_y=F\sin\theta_2$:

$$
r_xF_y-r_yF_x=rF(\cos\theta_1\sin\theta_2-\sin\theta_1\cos\theta_2)
$$

$$
=rF\sin(\theta_2-\theta_1)
$$

$$
=Fr\sin\theta
$$

where $\theta$ is the angle between $\mathbf r$ and $\mathbf F$. This can be read two ways: the component of the force perpendicular to $\mathbf r$, $F\sin\theta$, times $r$; or the force times its perpendicular distance from O, $d=r\sin\theta$. The moment is zero when the force passes through O ($\theta=0°$ or 180°).

The angular momentum of a particle in plane motion is likewise

$$
\mathbf H_O=(r_xmv_y-r_ymv_x)\,\mathbf k=mvr\sin\theta\,\mathbf k=mv'r\,\mathbf k=mvd\,\mathbf k
$$

where $v'=v\sin\theta$ is the component of the velocity perpendicular to $\mathbf r$ and $d$ is the perpendicular distance from O to the line of the velocity. The radial component of the velocity contributes nothing.

### Sign convention and the right-hand rule

The direction of a cross product follows the right-hand rule: with the thumb along $\mathbf r$ and the index finger along $m\mathbf v$ (or $\mathbf F$), the middle finger gives $\mathbf H_O$ (or $\mathbf M_O$); equivalently, curl the fingers of the right hand from $\mathbf r$ towards $m\mathbf v$ and the thumb points along the result. In plane problems the $z$ axis ($\mathbf k$) points out of the page and anticlockwise moments and angular momenta are positive; clockwise ones point into the page and are negative.

A particle moving in a straight line at constant speed has constant angular momentum about any fixed point O, even as it moves away, because $mv$ and the perpendicular distance $d$ from O to its line of motion are both constant. About a point on its line of motion, its angular momentum is zero (L10b quizzes, ll. 517–545).

## 2. The moment equation

Start from Newton's second law in momentum form ([[FEEG1002 D4 - Linear Impulse and Momentum|D4]]):

$$
\sum\mathbf F=m\dot{\mathbf v}
$$

Take the cross product of both sides with $\mathbf r$, the position of the particle from a fixed point O:

$$
\sum\mathbf r\times\mathbf F=\mathbf r\times m\dot{\mathbf v}
$$

The left-hand side is $\sum\mathbf M_O$. Differentiating the angular momentum with the product rule gives:

$$
\dot{\mathbf H}_O=\frac{d}{dt}(\mathbf r\times m\mathbf v)=\dot{\mathbf r}\times m\mathbf v+\mathbf r\times m\dot{\mathbf v}
$$

Because O is fixed, $\dot{\mathbf r}$ is the particle's velocity $\mathbf v$, and the first term is $m\,\mathbf v\times\mathbf v=\mathbf 0$ (the cross product of parallel vectors). So

$$
\dot{\mathbf H}_O=\mathbf r\times m\dot{\mathbf v}
$$

$$
\boxed{\sum\mathbf M_O=\dot{\mathbf H}_O}
$$

The sum of the moments about a fixed point O equals the rate of change of angular momentum about O. It is Newton's second law seen another way, suited to curvilinear motion. If O moved, $\dot{\mathbf r}$ would be the velocity relative to O and the first term would not vanish, which is why O must be fixed in an inertial frame.

## 3. Principle of angular impulse and momentum

Multiply the moment equation by $dt$ and integrate from $t_1$ to $t_2$:

$$
\sum\int_{t_1}^{t_2}\mathbf M_O\,dt=\int_{(\mathbf H_O)_1}^{(\mathbf H_O)_2}d\mathbf H_O=(\mathbf H_O)_2-(\mathbf H_O)_1
$$

$$
\boxed{(\mathbf H_O)_1+\sum\int_{t_1}^{t_2}\mathbf M_O\,dt=(\mathbf H_O)_2}
$$

The term $\sum\int\mathbf M_O\,dt$ is the **angular impulse**. In plane motion everything is along $\mathbf k$, so the principle is one scalar equation about the $z$ axis.

### Conservation of angular momentum

If the angular impulses sum to zero over the interval, either because they cancel or because the forces have no moment about O,

$$
(\mathbf H_O)_1=(\mathbf H_O)_2
$$

for a particle or a system of particles. Forces may be acting, provided their moment about the chosen point is zero. The most important case is a **central force**, one that always points towards (or away from) a fixed point. Taking O at that point, $\mathbf F$ is parallel to $\mathbf r$ and $\mathbf r\times\mathbf F=\mathbf 0$. Examples are a cord pulling a particle towards a fixed pivot, a spring pinned at one end, and the gravitational attraction of a planet on a satellite.

Conservation is always about a named point. A satellite's angular momentum is conserved about the centre of the Earth, but about any other point gravity has a moment and it is not. "Is angular momentum conserved?" has no answer until the point is given (L10b, ll. 318–379).

> [!tip] Choosing the point
> The point O is yours to choose. Put it where the unknown forces act (a pivot) or where they point (a centre of attraction), so that they have no moment; the equation then contains only the quantities you want.

When the path is not circular, the velocity is not perpendicular to $\mathbf r$, and only the perpendicular component $v'$ enters $H_O$. The radial component is found from the rest of the problem (how fast a cord is pulled in), and the speed is $v=\sqrt{v'^2+v_r^2}$. Where the velocity is perpendicular to $\mathbf r$, as at the nearest and furthest points of an orbit, $H_O=mvr$.

For central forces the work done is easiest to find from the work-energy principle, $U_{1-2}=\tfrac12m(v_2^2-v_1^2)$, rather than by integrating a force that varies along a spiral path.

---

## Worked examples

### Amusement-park ride pulled in on a cable

A 120 kg car moves in a horizontal circle of radius 3.6 m at 1.2 m/s, held by a cable to a central pivot. The cable is then pulled in at a constant 0.15 m/s. Neglecting friction and treating the car as a particle, find its speed after 3 s and the work done by the pulling force (slides pp. 21–25; DAMS6-2; L10b, ll. 46–298).

![[d_central_force_ride.png|900]]

The motion is in the horizontal plane (a top view), so the weight is balanced by the floor and plays no part. After 3 s the radius is

$$
r_2=3.6-0.15\times3=3.15\ \mathrm m
$$

The only horizontal force is the cable tension, which always points at the pivot O: a central force, so angular momentum about O is conserved. At position 1 the car moves on a circle, so $\mathbf v_1\perp\mathbf r_1$. At position 2 the velocity has a radial component $v_2''=0.15$ m/s (inwards, the rate at which the cable shortens) and a perpendicular component $v_2'$. Only $v_2'$ contributes:

$$
r_1mv_1=r_2mv_2'
$$

$$
v_2'=\frac{r_1v_1}{r_2}=\frac{3.6\times1.2}{3.15}=1.371\ \mathrm{m/s}
$$

$$
v_2=\sqrt{v_2'^2+v_2''^2}=\sqrt{1.371^2+0.15^2}=1.380\ \mathrm{m/s}
$$

The car speeds up as the radius falls. The cable tension does work, because the car moves inwards along the cable while the tension pulls inwards. Integrating the varying tension along the spiral would be hard, but the work-energy principle gives it directly:

$$
U_{1-2}=\tfrac12m(v_2^2-v_1^2)=\tfrac12\times120\times(1.3796^2-1.2^2)=27.8\ \mathrm J
$$

### Satellite in an elliptical orbit

A satellite is at perigee A, $r_A=6.976\times10^6$ m from the centre of the Earth, moving at $v_A=8333.3$ m/s perpendicular to $\mathbf r_A$. With $M=5.976\times10^{24}$ kg and $G=66.73\times10^{-12}$ m³/(kg s²), find its speed and distance at apogee B (slides pp. 30–33; DAMS6-3; L10b, ll. 302–463).

![[d_elliptical_orbit_example.png|900]]

Treat the Earth as fixed. Gravity is conservative, so energy is conserved with $V_g=-GMm/r$ from [[FEEG1002 D3 - Work, Energy and Power#2. Conservative forces and potential energy|D3]]; gravity is also central, so angular momentum about the centre of the Earth is conserved. At A and B the velocity is perpendicular to $\mathbf r$:

$$
\tfrac12mv_A^2-\frac{GMm}{r_A}=\tfrac12mv_B^2-\frac{GMm}{r_B} \tag{1}
$$

$$
mv_Ar_A=mv_Br_B \tag{2}
$$

The satellite's mass cancels. From (2), $r_B=v_Ar_A/v_B$. Substitute into (1) and divide by $m$:

$$
\tfrac12v_A^2-\frac{GM}{r_A}=\tfrac12v_B^2-\frac{GMv_B}{v_Ar_A}
$$

$$
v_B^2-\frac{2GM}{v_Ar_A}v_B-v_A^2+\frac{2GM}{r_A}=0
$$

This quadratic has two roots. One is $v_B=v_A$ (substituting it gives $v_A^2-2GM/r_A-v_A^2+2GM/r_A=0$), because A itself satisfies both equations. Since the product of the roots is $-v_A^2+2GM/r_A$, the other is

$$
v_B=\frac{2GM}{v_Ar_A}-v_A
$$

With $GM=66.73\times10^{-12}\times5.976\times10^{24}=3.988\times10^{14}$ m³/s²:

$$
v_B=\frac{2\times3.988\times10^{14}}{8333.3\times6.976\times10^6}-8333.3=13\,719.5-8333.3=5386\ \mathrm{m/s}
$$

$$
r_B=\frac{v_Ar_A}{v_B}=\frac{8333.3\times6.976\times10^6}{5386}=10.79\times10^6\ \mathrm m
$$

> [!check] Is it an ellipse?
> The circular-orbit speed at $r_A$ is $\sqrt{GM/r_A}=7561$ m/s and the escape speed is $\sqrt{2GM/r_A}=10\,692$ m/s. Since $v_A$ lies between them, the orbit is a closed ellipse with A as its perigee, consistent with $r_B>r_A$. The specific energy $\tfrac12v^2-GM/r$ is $-2.244\times10^7$ J/kg at both A and B.

### Fun-fair game with an elastic cord

A puck of mass $m$ on a horizontal table is tied by an elastic cord to a fixed point O. The cord's natural length equals the radius $R$ of a rough circular region centred on O (kinetic friction $\mu_k$); outside the circle the table is frictionless and the cord is taut, inside it the cord is slack. The puck is struck at A on the edge of the circle, leaving with speed $v_A$ at angle $\theta$ between $\mathbf r_A$ and $\mathbf v_A$ ($-90°<\theta<90°$, so it moves outwards). It swings round outside the circle, re-enters at B and slides across the rough region. Find $v_A(\theta)$ for it to stop exactly at C on the far edge (L11, ll. 412–629, adapted from an assignment).

From A to B the puck is outside the circle, in a top view with no friction. The only horizontal force is the cord tension, which is conservative and central about O. At A and B the cord is at its natural length $R$, so $V_e=0$ at both, and energy conservation gives

$$
\tfrac12mv_A^2=\tfrac12mv_B^2\quad\Rightarrow\quad v_B=v_A
$$

Angular momentum about O, with $\beta$ the angle between $\mathbf r_B$ and $\mathbf v_B$:

$$
Rmv_A\sin\theta=Rmv_B\sin\beta
$$

so $\sin\beta=\sin\theta$. The puck is now moving inwards, so $\beta=180°-\theta$: it re-enters at the same angle to the radius at which it left.

From B to C the cord is slack and the puck slides in a straight line with friction $\mu_kmg$, a constant deceleration $\mu_kg$. The chord BC makes angle $\theta$ with the radius OB, so its perpendicular distance from O is $R\sin\theta$ and its length is

$$
s_{BC}=2\sqrt{R^2-R^2\sin^2\theta}=2R\cos\theta
$$

For the puck to stop at C:

$$
0=v_B^2-2\mu_kg\,s_{BC}
$$

$$
v_A^2=2\mu_kg\,(2R\cos\theta)
$$

$$
v_A=2\sqrt{\mu_kgR\cos\theta}
$$

The mass cancels, so a 3 kg and a 9 kg puck struck at the same angle need the same speed. Their paths outside the circle differ, because the same cord acts on different masses, so they re-enter at different points B; each still stops exactly on the edge of the circle (L11, ll. 618–628). A radial strike ($\theta=0$) needs the most speed, crossing a full diameter; a tangential one ($\theta\to90°$) needs none.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D4 - Linear Impulse and Momentum]] · Next: [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
- Concepts: [[Principle of Angular Impulse and Momentum]] · [[Orbital Angular Momentum]] · [[Conservative Forces and Potential Energy]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 D8 - Kinetics of Rigid Bodies|D8]] ($H_G=I_G\omega$ and angular impulse for rigid bodies) · [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] (Kepler's second law is conservation of $H$) · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] · [[SESA2024 06 - Attitude Control]] (angular momentum of spacecraft)

## Sources

- `Lecture 05 - Angular Impulse and Momentum.pdf`: slides pp. 1–33 (theory pp. 5–19, ride example pp. 20–28, orbit example pp. 29–33).
- Transcript labels used in this note:
  - DAMS6-1 = `FEEG1002 Lecture 2021-02-19 - DAMS-6-AngImpMom_1.txt` (theory, ll. 16–250; mug-and-pencil demo, ll. 251–277); DAMS6-2 = `..._2.txt` (ride); DAMS6-3 = `..._3.txt` (orbit).
  - L10b = `FEEG1002 Lecture 2025-02-27.txt` (27 Feb 2025 problem class): recap (ll. 8–38), ride (ll. 46–298), orbit (ll. 302–463), quizzes (ll. 468–576).
  - L11 = `FEEG1002 Lecture 2025-03-05.txt` (5 Mar 2025 revision): fun-fair game (ll. 412–629). Its first problem (a 2016–17 exam question, ll. 20–411) uses D3 and D4 and is in [[FEEG1002 D3 - Work, Energy and Power#Collar on a rough vertical shaft|D3]].
- `Tutorial Sheet 05 - Angular Impulse and Momentum.pdf`: Q1–Q5, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Quiz set (L10b, ll. 484–576): the sign of a clockwise moment (negative), the moment of a force through O (zero), the angular momentum of a particle in a straight line about O and about a point on its line. → [[#Sign convention and the right-hand rule]]
- [ ] Derive $\sum\mathbf M_O=\dot{\mathbf H}_O$ and say where the fixed point is used (slide p. 13). → [[#2. The moment equation]]
- [ ] Rework the ride example. Targets 1.38 m/s and 27.8 J. → [[#Amusement-park ride pulled in on a cable]]
- [ ] Solve the orbit quadratic with a calculator (DAMS6-3, l. 28; L10b, ll. 435–438). Targets 5386 m/s and $10.79\times10^6$ m. → [[#Satellite in an elliptical orbit]]
- [ ] Discuss why energy and $H_O$ are both conserved from A to B in the fun-fair game (L11, ll. 469–471). → [[#Fun-fair game with an elastic cord]]
- [ ] Tutorial 5 Q1–Q4. → [[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]]

### Further practice

- [ ] Prove $r_xF_y-r_yF_x=Fr\sin\theta$ (DAMS6-1, l. 95; optional). → [[#Plane motion]]
- [ ] Add to the list of central-force systems (DAMS6-1, ll. 230, 243–244). → [[#Conservation of angular momentum]]
- [ ] Tutorial 5 Q5, the forward version of the fun-fair game. → [[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 05 slides)
> Where: [[#Amusement-park ride pulled in on a cable]] · [[#Satellite in an elliptical orbit]].
>
> Slide p. 25 gives $U_{1-2}=27.9$ J, from the rounded $v_2=1.38$ m/s; with $v_2=1.3796$ m/s it is 27.8 J. Slide p. 32 gives $v_B=5382.2$ m/s and $r_B=10.804\times10^6$ m; the data give 5386.2 m/s and $10.793\times10^6$ m, and the slide's own pair is inconsistent ($v_Ar_A/5382.2=10.801\times10^6$ m). Slide p. 5 is headed "6.1" in a chapter numbered 5.

### Transcript slips (DAMS6, L10b, L11)

| Ref | Said | Correct |
|---|---|---|
| DAMS6-3, l. 30 | $v_B$ "5,392" | 5386 m/s |
| L10b, ll. 280–282 | the car can regain its initial speed on returning to the old radius because "energy is conserved" | the car's energy is not conserved (the tension does +27.8 J pulling in); recovery follows from conservation of $H_O$ |
| L10b, l. 195 | $v_2'$ "you get 1.3" | 1.371 m/s |
| L11, l. 478 | "the inner circle is frictionless" (a student, uncorrected) | the outer region is frictionless; the inner circle is rough |

Whisper renderings to read through: "inputs" = impulse; "concerned", "in concert" = conserved.
