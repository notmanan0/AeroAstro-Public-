---
title: "FEEG1002 D4 - Linear Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 4
tags: [feeg1002, dynamics, impulse, momentum, impact, restitution]
aliases: ["Dynamics Lecture 4", "Impulse and momentum", "Impacts", "Coefficient of restitution", "Galilean cannon"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 4, sections 4.1-4.2 (slides pp. 1-37): principle of linear impulse and momentum, impulse and average force, impulse-momentum diagrams, systems of particles, conservation of linear momentum, central impact, coefficient of restitution, plastic and elastic impacts, Newton's cradle and the Galilean cannon. Section 4.3, oblique impact (slides pp. 38-46), was declared optional and not assessed and is summarised briefly. Live lectures L07 and L07b (19 Feb 2025, the same lecture to two groups), L08 and L08b (20 Feb 2025, Galilean cannon derivation and quizzes); pre-recorded DAMS4-1 to DAMS4-3."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
next_topics: ["[[FEEG1002 D5 - Angular Impulse and Momentum]]"]
key_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Coefficient of Restitution]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 04 - Linear Impulse and Momentum.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-19 - Dynamics 07 - 19 February 2025 at 10 50 43.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-19 - Dynamics 07b - 19 February 2025 at 11 58 06.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-20 - Dynamics 08 - 20 February 2025 at 11 56 36.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-20 - Dynamics 08b - 20 February 2025 at 13 53 10.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-02-05 - DAMS-4-LinearImpulseMomentum1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-02-05 - DAMS-4-LinearImpulseMomentum2.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-02-05 - DAMS-4-LinearImpulseMomentum3.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 04 - Linear Impulse and Momentum.pdf"]
---

# FEEG1002 D4 - Linear Impulse and Momentum

> [!abstract] Summary
> Integrating Newton's second law over time gives the principle of linear impulse and momentum, $m\mathbf v_1+\sum\int\mathbf F\,dt=m\mathbf v_2$: the impulse of the forces over an interval equals the change in linear momentum $m\mathbf v$. When the external impulses on a system sum to zero, as they do for a collision or explosion between bodies over the short contact time, the total momentum is conserved. Momentum alone cannot fix both velocities after an impact, so the coefficient of restitution $e$, the ratio of the relative speeds of separation and approach, supplies the second equation; $e=1$ is elastic (no energy lost) and $e=0$ is plastic (the bodies move together).

> [!summary]- Exam use: quick path
> - **Use it when:** forces act over a known time (a force-time history, a thrust for 2.5 s) or a short impact or explosion happens, and velocities before and after are wanted.
> - **Assumptions:** constant mass; inertial frame; during an impact only impulsive forces matter (weight and other finite, steady forces are neglected over the short contact time); central impact, velocities along the line of impact, positive in one stated direction.
> - **Method:** 1. Choose axes and draw the initial momentum, impulse and final momentum diagrams. 2. For a long event keep every force; for an impact, decide which forces are impulsive. 3. Write $m(v_x)_1+\sum\int F_x\,dt=m(v_x)_2$ per axis, or conservation of momentum for the system. 4. For an impact add $e=(v_{B2}-v_{A2})/(v_{A1}-v_{B1})$. 5. Find energy lost, if asked, by comparing kinetic energies.
> - **Common mistakes:** assuming momentum is conserved when a body bounces off rigid ground (the ground's impulse is external); calling the average force the maximum force.
> - **Practise:** [[#Tennis ball bouncing off the ground]] · [[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]] (Q2 half-sine impact)

[[FEEG1002 D3 - Work, Energy and Power|Work and energy]] integrate Newton's law over distance and remove time. Integrating over time instead removes position: force, time and speed are the quantities that remain. Two kinds of problem need it. In one, a force acts over a long, known time, such as the thrust of a rocket sled or the braking force on a car. In the other, two bodies collide or an explosion separates them; the contact forces are huge and act for milliseconds, their detailed history is unknown, but their total effect, the impulse, is what changes the velocities.

The power of the method for impacts is that the large, unknown contact forces between two colliding bodies are internal to the pair. They are equal and opposite at every instant, so their impulses cancel and the total momentum of the pair is unchanged, even though each body's own momentum changes a great deal. Energy is a different matter: most collisions turn some kinetic energy into heat, sound and permanent deformation, which is why momentum, not energy, is the conserved quantity to reach for, and why an extra piece of information about the collision (the coefficient of restitution) is needed.

---

## 1. Principle of linear impulse and momentum

### Derivation

Start from Newton's second law for a particle of constant mass:

$$
\sum\mathbf F=m\mathbf a=m\frac{d\mathbf v}{dt}
$$

Separate the variables and integrate from $\mathbf v=\mathbf v_1$ at $t_1$ to $\mathbf v=\mathbf v_2$ at $t_2$:

$$
\sum\mathbf F\,dt=m\,d\mathbf v
$$

$$
\sum\int_{t_1}^{t_2}\mathbf F\,dt=m\int_{\mathbf v_1}^{\mathbf v_2}d\mathbf v=m\mathbf v_2-m\mathbf v_1
$$

$$
\boxed{m\mathbf v_1+\sum\int_{t_1}^{t_2}\mathbf F\,dt=m\mathbf v_2}
$$

The **linear momentum** $\mathbf L=m\mathbf v$ is a vector along the velocity, in kg m/s (equivalently N s). The **linear impulse** $\mathbf I=\int\mathbf F\,dt$ is a vector in N s. The impulse is usually written $\int\mathbf F\,dt$ and the momentum $m\mathbf v$ in full, because $I$ is used later for the mass moment of inertia. Since $m$ is constant, Newton's second law can also be written

$$
\sum\mathbf F=\frac{d(m\mathbf v)}{dt}=\frac{d\mathbf L}{dt}
$$

the net force is the rate of change of momentum.

Unlike the work-energy principle, this is a vector equation. In components,

$$
m(v_x)_1+\sum\int_{t_1}^{t_2}F_x\,dt=m(v_x)_2
$$

and likewise for $y$ and $z$.

### Impulse and average force

The impulse of a force is the area under its force-time curve, $I=\int_{t_1}^{t_2}F(t)\,dt$. The **average force** is the constant force that would give the same area over the same time:

$$
I=F_{avg}(t_2-t_1)
$$

Only if the force really is constant, $F=F_0$, is $I=F_0(t_2-t_1)$ with $F_0$ the actual force; for a pulse, the peak force is larger than the average.

![[d_impulse_force_time.png|900]]

### Impulse-momentum diagrams

The principle is drawn as three diagrams: the initial momentum diagram ($m\mathbf v_1$) plus the impulse diagram equals the final momentum diagram ($m\mathbf v_2$). The impulse diagram is like an FBD but each force is multiplied by the time over which it acts. To use it:

1. Choose the axes.
2. Choose directions for $\mathbf v_1$ and $\mathbf v_2$; a wrong guess just gives a negative answer.
3. Draw the three diagrams.
4. Resolve and apply the scalar equations.
5. Integrate time-varying forces; a constant force contributes $F\,\Delta t$.

### Impulsive and non-impulsive forces

During an impact lasting a few milliseconds, a finite steady force such as the weight contributes almost nothing:

$$
\int_{t_1}^{t_2}mg\,dt=mg(t_2-t_1)\approx0
$$

because $t_2-t_1\approx0$, whereas the contact force is so large that its impulse is finite. Forces that are present and unchanged before, during and after the impact are **non-impulsive** and can be neglected over the impact. This applies only to short events. Over a finite time every force counts: a rocket accelerating vertically for 6 s must include the impulse of its weight, and for a block pushed up a rough incline for 3 s the weight, normal force and friction all contribute.

> [!warning] Rigid ground breaks momentum conservation
> A ball bouncing off the ground does not conserve its momentum: the ground, treated as having infinite mass, applies an external impulse. Momentum is conserved only for a system on which the external impulses cancel; perpendicular to rigid ground you need either the ground's impulse or information about the collision itself.

### Systems of particles

For a system of particles, write Newton's law for each and add. The internal forces $\mathbf f_i$ cancel in pairs by Newton's third law, leaving only the external forces $\mathbf F_i$:

$$
\sum m_i(\mathbf v_i)_1+\sum\int_{t_1}^{t_2}\mathbf F_i\,dt=\sum m_i(\mathbf v_i)_2
$$

The centre of mass G is defined by $m\mathbf r_G=\sum m_i\mathbf r_i$ with $m=\sum m_i$. Differentiating,

$$
m\mathbf v_G=\sum m_i\mathbf v_i
$$

so the system behaves like a single particle of mass $m$ at G:

$$
m(\mathbf v_G)_1+\sum\int\mathbf F_i\,dt=m(\mathbf v_G)_2
$$

## 2. Conservation of linear momentum

If the sum of the external impulses on a system is zero over the interval,

$$
\sum m_i(\mathbf v_i)_1=\sum m_i(\mathbf v_i)_2,\qquad\text{i.e.}\quad(\mathbf v_G)_1=(\mathbf v_G)_2
$$

This is the usual situation in collisions and explosions, where only the impulsive internal forces act and the non-impulsive external ones are neglected.

### Central impact

Two particles collide along the **line of impact**, the line through their mass centres; the **plane of contact** is perpendicular to it. The impact is **central** if the mass centres move along the line of impact, and **oblique** otherwise. Friction between the bodies during the impact is usually neglected.

For a central impact take the velocities positive in one direction along the line of impact, with A behind B and $v_{A1}>v_{B1}$ so that they collide. During contact:

1. In the deformation phase, A pushes B with an impulse $\int P\,dt$ and B pushes A with $-\int P\,dt$.
2. At maximum deformation the two move with a common velocity $v$.
3. In the restitution phase they push apart with impulses $\int R\,dt$ and $-\int R\,dt$, and separate with $v_{B2}>v_{A2}$.

At every instant the forces on A and B are equal and opposite, so for the pair

$$
m_Av_{A1}+m_Bv_{B1}=m_Av_{A2}+m_Bv_{B2}
$$

while each particle's own momentum changes. With the initial velocities known, this one equation has two unknowns.

### Coefficient of restitution

The second equation comes from experiment. The **coefficient of restitution** is

$$
\boxed{e=\frac{v_{B2}-v_{A2}}{v_{A1}-v_{B1}}=\frac{\text{relative velocity of separation}}{\text{relative velocity of approach}}}
$$

with all velocities positive in the same direction. It depends on the materials, the shapes and sizes, and the impact speed, and is treated as a given constant. For ordinary collisions $0\le e\le1$; the limits are:

- $e=1$, an **elastic** impact: kinetic energy is conserved;
- $e=0$, a **plastic** impact: the bodies stick and move together after the impact, and the energy lost is the greatest possible.

For other values the energy lost is found by comparing the kinetic energies before and after. An impact problem therefore uses momentum plus kinetic energy (elastic), momentum alone with a common final velocity (plastic), or momentum plus $e$ (any case, including both limits).

### Velocities after a central impact

Solve momentum and restitution together. From the definition of $e$,

$$
v_{B2}=v_{A2}+e(v_{A1}-v_{B1})
$$

Substitute into momentum:

$$
m_Av_{A1}+m_Bv_{B1}=m_Av_{A2}+m_Bv_{A2}+em_B(v_{A1}-v_{B1})
$$

$$
(m_A+m_B)v_{A2}=m_Av_{A1}+m_Bv_{B1}-em_Bv_{A1}+em_Bv_{B1}
$$

$$
\boxed{v_{A2}=\frac{(m_A-em_B)v_{A1}+m_B(1+e)v_{B1}}{m_A+m_B}}
$$

and then

$$
\boxed{v_{B2}=\frac{m_A(1+e)v_{A1}+(m_B-em_A)v_{B1}}{m_A+m_B}}
$$

With $e=0$ both reduce to the plastic result

$$
v_2=\frac{m_Av_{A1}+m_Bv_{B1}}{m_A+m_B}
$$

and with $e=1$ to the elastic one, $v_{A2}=[(m_A-m_B)v_{A1}+2m_Bv_{B1}]/(m_A+m_B)$ and $v_{B2}=[2m_Av_{A1}+(m_B-m_A)v_{B1}]/(m_A+m_B)$.

The elastic result can also be reached from momentum and energy. Write both with A's terms on the left:

$$
m_A(v_{A1}-v_{A2})=m_B(v_{B2}-v_{B1})
$$

$$
m_A(v_{A1}^2-v_{A2}^2)=m_B(v_{B2}^2-v_{B1}^2)
$$

Factor the squares and divide the second equation by the first (allowed provided $v_{A2}\neq v_{A1}$):

$$
v_{A1}+v_{A2}=v_{B2}+v_{B1}
$$

$$
v_{B2}-v_{A2}=v_{A1}-v_{B1}
$$

which is $e=1$. The excluded root $v_{A2}=v_{A1}$, $v_{B2}=v_{B1}$ corresponds to the particles passing through each other, and is discarded. This derivation is not assessed; the general-$e$ formulae are the ones to note down.

### Energy lost in an impact

Substituting the two velocities into $\Delta KE=KE_1-KE_2$ and simplifying (or, more quickly, working in the frame of the centre of mass, where the relative speed is multiplied by $e$ and the kinetic energy of relative motion by $e^2$) gives

$$
\Delta KE=\frac12\,\frac{m_Am_B}{m_A+m_B}\,(1-e^2)\,(v_{A1}-v_{B1})^2
$$

This is zero for $e=1$ and greatest for $e=0$. The loss can always be found by comparing kinetic energies; the formula is a compact way of doing that comparison and is checked against direct subtraction in [[#Collisions of a 2m and an m particle]].

![[d_restitution_sweep.png|900]]

### Newton's cradle

With equal masses and $e=1$, the elastic formulae give $v_{A2}=v_{B1}$ and $v_{B2}=v_{A1}$: the particles swap velocities. A ball striking a stationary row of touching balls passes its momentum along the row and stops, and the last ball leaves at the incoming speed. Releasing two balls sends two out, because only that outcome conserves both momentum and energy (one ball at twice the speed would need twice the energy).

## 3. Oblique impact

Oblique impact is optional and not assessed. In outline: for a ball striking smooth ground obliquely, take $x$ along the plane of contact and $y$ along the line of impact. Momentum is conserved along $x$ (no impulse there), the ground's impulse acts along $y$, and $e$ applies to the $y$ components only. For two smooth particles, take $x$ along the line of impact; then the system's momentum is conserved along $x$, each particle's momentum is conserved separately along $y$, and $e$ applies along $x$: four equations for the four unknown velocity components. Tutorial 4 Q7 (billiard balls) is of this kind.

---

## Worked examples

### Tennis ball bouncing off the ground

A 60 g tennis ball hits the ground at 6 m/s. The contact force rises linearly to $F_m=160$ N in 1 ms, stays there for 3 ms and falls linearly to zero in 1 ms. Find the rebound speed and the average force (DAMS4-1).

Take up as positive. The weight is non-impulsive over 5 ms ($mg\,\Delta t=0.06\times9.81\times0.005=0.003$ N s, against an impulse of 0.64 N s), so it is neglected. The impulse is the area of the trapezium; moving one ramp triangle onto the other makes a rectangle of height $F_m$ and width 4 ms:

$$
I=F_m(\Delta t_2+\Delta t_1)=160\times(0.003+0.001)=0.64\ \mathrm{N\,s}
$$

Impulse and momentum, with the ball arriving downwards:

$$
-mv_1+I=mv_2
$$

$$
v_2=\frac Im-v_1=\frac{0.64}{0.06}-6=4.67\ \mathrm{m/s}
$$

upwards. The average force over the 5 ms contact is

$$
F_{avg}=\frac{I}{\Delta t}=\frac{m(v_1+v_2)}{\Delta t}=\frac{0.06\times10.67}{0.005}=128\ \mathrm N
$$

which is less than the 160 N peak. Momentum is not conserved here, because the ground supplies the impulse.

### Collisions of a 2m and an m particle

Particle A of mass $2m$ moving at $+1$ m/s collides centrally with particle B of mass $m$ moving at $-1$ m/s. Find the velocities after impact for $e=1$, $e=0$ and $e=0.4$, and the energy lost (DAMS4-2).

With $m_A=2m$, $m_B=m$, $v_{A1}=1$ and $v_{B1}=-1$:

$$
v_{A2}=\frac{(2-e)(1)+(1+e)(-1)}{3}=\frac{1-2e}{3},\qquad v_{B2}=\frac{2(1+e)(1)+(1-2e)(-1)}{3}=\frac{1+4e}{3}
$$

| $e$ | $v_{A2}$ (m/s) | $v_{B2}$ (m/s) | $\Delta KE$ |
|---|---|---|---|
| 1 | $-1/3$ | $5/3$ | 0 |
| 0 | $1/3$ | $1/3$ | $\tfrac43m$ |
| 0.4 | $1/15$ | $13/15$ | $1.12m$ |

The energy loss from the formula is $\tfrac12\cdot\tfrac{2m\cdot m}{3m}(1-e^2)(2)^2=\tfrac43m(1-e^2)$, matching direct subtraction from $KE_1=\tfrac12(2m)(1)^2+\tfrac12m(1)^2=1.5m$: for $e=0.4$, $KE_2=\tfrac12(2m)(1/15)^2+\tfrac12m(13/15)^2=0.38m$, a loss of $1.12m$ J (with $m$ in kg).

### Galilean cannon

A tennis ball B rests on top of a basketball A and the pair is dropped from height $h_0$. How high can the tennis ball bounce (DAMS4-2)?

Treat the balls as particles with no size, take up as positive, and label the states: 0 at release; 1 just before A hits the ground; 2 just after A rebounds, before it meets B; 3 just after A and B collide; 4 with B at its highest point. From 0 to 1 both fall freely, so

$$
v_{A1}=v_{B1}=-\sqrt{2gh_0}
$$

A bounces off the ground with coefficient $e_G$, so $v_{A2}=e_G\sqrt{2gh_0}$ (up), while B still has $v_{B2}=-\sqrt{2gh_0}$. The A-B collision, from 2 to 3, uses the general formula with the subscripts shifted:

$$
v_{B3}=\frac{m_A(1+e)v_{A2}+(m_B-em_A)v_{B2}}{m_A+m_B}
$$

For a tennis ball on a basketball, $m_B\ll m_A$; dividing through by $m_A$ and letting $m_B/m_A\to0$:

$$
v_{B3}=(1+e)v_{A2}-ev_{B2}
$$

With $e=e_G=1$:

$$
v_{B3}=2\sqrt{2gh_0}+\sqrt{2gh_0}=3\sqrt{2gh_0}
$$

From 3 to 4 only the weight acts, so energy is conserved:

$$
\tfrac12m_B\left(3\sqrt{2gh_0}\right)^2=m_Bgh_4
$$

$$
h_4=9h_0
$$

This is an upper limit: it assumes no size, a vanishing mass ratio and perfectly elastic collisions. For a finite mass ratio $r=m_B/m_A$ with $e=1$, the same steps give $v_{B3}=\sqrt{2gh_0}\,(3-r)/(1+r)$ and

$$
\frac{h_4}{h_0}=\left(\frac{3-r}{1+r}\right)^2
$$

which falls from 9 at $r=0$ to 1 at $r=1$ and to 0 at $r=3$: if the upper ball is three times heavier, it stops dead and the lower ball is driven back down at twice its arrival speed. With $e<1$ for both collisions, $v_{A2}=e\sqrt{2gh_0}$ and $v_{B3}=e(e+2)\sqrt{2gh_0}$, so $h_4=[e(e+2)]^2h_0$; for $e=0.5$ this is $1.56h_0$.

![[d_galilean_cannon.png|900]]

The tennis ball gains its extra height at the basketball's expense: after the collision the basketball rises far less than it would alone, because it has handed most of its momentum on.

### Crash test

A 1500 kg car hits a barrier at 3 m/s and rebounds at 1 m/s after 0.4 s of contact. Find the average force and average deceleration (Tutorial 4 Q1).

Take the approach direction as positive. The barrier's impulse changes the velocity from $+3$ to $-1$ m/s:

$$
m(3)+F_{avg}(0.4)=m(-1)
$$

$$
F_{avg}=\frac{1500\times(-4)}{0.4}=-15.0\ \mathrm{kN}
$$

directed away from the barrier, and $a_{avg}=\Delta v/\Delta t=-4/0.4=-10$ m/s². The velocity change is 4 m/s, not 2: the rebound counts. The maximum force cannot be found without the force-time history.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D3 - Work, Energy and Power]] · Next: [[FEEG1002 D5 - Angular Impulse and Momentum]]
- Concepts: [[Principle of Linear Impulse and Momentum]] · [[Coefficient of Restitution]] · [[Work-Energy Principle]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 D5 - Angular Impulse and Momentum|D5]] (the angular counterpart) · [[FEEG1002 D8 - Kinetics of Rigid Bodies|D8]] (impulse and momentum for rigid bodies) · [[SESA1016 T12 - Conservation of Momentum]] (the same law for a fluid control volume) · [[SESA2024 07 - Spacecraft Propulsion]] (rocket thrust from momentum)

## Sources

- `Lecture 04 - Linear Impulse and Momentum.pdf`: slides pp. 1–46 (4.1 principle pp. 3–17, 4.2 conservation and central impact pp. 19–37, 4.3 oblique impact pp. 38–46, not assessed).
- Transcript labels used in this note:
  - L07 = `FEEG1002 Lecture 2025-02-19 - Dynamics 07 - 19 February 2025 at 10 50 43.txt` and L07b = `...Dynamics 07b - 19 February 2025 at 11 58 06.txt` (19 Feb 2025, the same lecture to two groups): principle, tennis ball, incline, systems, conservation, restitution, Newton's cradle, Galilean cannon demo.
  - L08 = `FEEG1002 Lecture 2025-02-20 - Dynamics 08 - 20 February 2025 at 11 56 36.txt` and L08b = `...Dynamics 08b - 20 February 2025 at 13 53 10.txt` (20 Feb 2025): Galilean cannon derivation (L08, ll. 41–256), quizzes (L08, ll. 265–420).
  - DAMS4-1, DAMS4-2, DAMS4-3 = `FEEG1002 Lecture 2021-02-05 - DAMS-4-LinearImpulseMomentum1.txt`, `...2.txt`, `...3.txt`.
- `Tutorial Sheet 04 - Linear Impulse and Momentum.pdf`: Q1–Q7, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Discuss why $\int mg\,dt\approx0$ during the bounce (L07, ll. 194–234; L07b, ll. 172–213). → [[#Impulsive and non-impulsive forces]]
- [ ] Put your own numbers into the block-on-an-incline example, keeping all forces (DAMS4-1, ll. 167–168). → [[#Impulsive and non-impulsive forces]]
- [ ] Verify the slide p. 29 results with the general-$e$ formulae (DAMS4-2, ll. 145–149; L07b, ll. 437–457). → [[#Collisions of a 2m and an m particle]]
- [ ] Derive the general-$e$ formulae and check that $e=1$ gives the elastic case (DAMS4-2, ll. 139–144). → [[#Velocities after a central impact]]
- [ ] Prove that the tennis ball cannot rise above $9h_0$, and say what happens if it is three times heavier than the lower ball (L07, ll. 577–598; solved in L08, ll. 104–217). → [[#Galilean cannon]]
- [ ] Quiz: the crash test, average deceleration $-10$ m/s² (L08, ll. 371–394). → [[#Crash test]]
- [ ] Quiz: rocket propelled upwards for 6 s; include the weight's impulse (L08, ll. 335–357). Target 121 m/s against 180 m/s without gravity. → [[#Impulsive and non-impulsive forces]]
- [ ] Tutorial 4 Q2 (half-sine impact force), Q3–Q4 (cannon fixed and free). → [[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]]

### Further practice

- [ ] Plot $h_4/h_0$ against $m_B/m_A$ in Python (L08, ll. 235–248). → [[#Galilean cannon]]
- [ ] Newton's cradle: show why two balls released send two out (DAMS4-2, ll. 159–173). → [[#Newton's cradle]]
- [ ] Optional derivation of the elastic formulae from momentum and energy (DAMS4-2, ll. 127–134; not assessed). → [[#Velocities after a central impact]]
- [ ] Tutorial 4 Q5 (plastic 2D impact), Q6 (boy throwing bricks), Q7 (oblique, not assessed). → [[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 04 slides)
> Where: [[#Galilean cannon]] · [[#Collisions of a 2m and an m particle]].
>
> Slide p. 37 gives $h_4=[e(e+2)^2]h_0$ and "$e=0.5$, $h_4=6.25h_0$". With $v_{B3}=e(e+2)\sqrt{2gh_0}$ (which the slide has right) the height is $[e(e+2)]^2h_0=1.5625h_0$ at $e=0.5$; 6.25 matches neither form. Slide p. 29 prints "$v_{A1}=v_{B1}=1$ m/s"; the particles move in opposite directions, so $v_{B1}=-1$ m/s, as its plots show. Slide p. 44 has $v_{AB_x}$ in a denominator where $v_{B1x}$ is meant.

### Transcript slips (L07, L07b, L08, DAMS4)

| Ref | Said | Correct |
|---|---|---|
| DAMS4-1, ll. 42, 45; L07, l. 85 | impulse in "newton per second"; momentum in "kilogram per meter divided by seconds" | N s; kg m/s |
| DAMS4-2, ll. 33–34 | A's speed before must exceed B's speed "after" the impact | B's speed before |
| L07b, ll. 253–256 | the average force acts "over 4 milliseconds" | 128 N acts over the full 5 ms; it is $F_m=160$ N that fills the equivalent 4 ms rectangle |
| L07, ll. 401–404, 419–424 | "total impulse of the system is conserved" | total momentum |
| L07b, l. 339 | central impact means the line of impact is perpendicular to the plane of contact | true of every impact; central means the velocities lie along the line of impact |
| L07, l. 452; L07b, ll. 384–386 | $e$ "can only be between 0 and 1" | for ordinary collisions; $e>1$ needs stored energy released at impact |
| L08, l. 314; L08b, l. 259 | horizontal rocket quiz "after two seconds" / "after 2.5 seconds" | one of the two is a misstatement; the quiz slide is not available |
