---
title: "FEEG1002 D3 - Work, Energy and Power"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 3
tags: [feeg1002, dynamics, work, energy, potential-energy, power, efficiency]
aliases: ["Dynamics Lecture 3", "Work-energy principle", "Conservation of energy", "Power and efficiency"]
date: 2026-11-05
status: lectured
coverage: "Dynamics Lecture 3 (slides pp. 1-43) in full: work of a force, work of weight, gravitational attraction, springs and friction, conservative forces and potential energy, the work-energy principle, conservation of energy, friction and heat, systems of particles, power and efficiency, with the incline, loop and motor-and-pulley examples. Live lectures L05 and L05b (12 Feb 2025, the same lecture to two groups) and L06 (13 Feb 2025, examples, submarine quizzes and the Box Hill cycling activity); pre-recorded DAMS3-1 to DAMS3-3; the pendulum energy step from the L12 revision lecture (6 Mar 2025, ll. 349-509); the collar-on-a-shaft past-paper question from the L11 revision lecture (5 Mar 2025, ll. 20-411)."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
next_topics: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
key_concepts: ["[[Work-Energy Principle]]", "[[Conservative Forces and Potential Energy]]", "[[Power and Efficiency]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 03 - Work, Energy and Power.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-12 - Dynamics - 05 - 12 February 2025 at 10 51 59.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-12 - Dynamics 05b - 12 February 2025 at 11 57 32.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-02-13.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-06.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2025-03-05.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-01-26 - DAMS-3-WorkEnergyPower1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-12-07.txt", "02 - Sources/Lectures/FEEG1002 Lecture 2021-01-26 - DAMS-3-WorkEnergyPower3.txt", "02 - Sources/Dynamics/Tutorials/Tutorial Sheet 03 - Work, Energy and Power.pdf"]
---

# FEEG1002 D3 - Work, Energy and Power

> [!abstract] Summary
> A force does work $U=\int\mathbf F\cdot d\mathbf r$ on a particle when its point of application moves along the force's line of action; only the tangential component $F_t$ counts. Integrating Newton's second law along the path gives the work-energy principle, $KE_1+\sum U_{1-2}=KE_2$ with $KE=\tfrac12mv^2$, a scalar equation that links forces, speeds and displacements without time. The work of weight and springs depends only on the end positions, so it can be moved to the other side as potential energy ($V_g=mgy$, $V_g=-Gm_1m_2/r$, $V_e=\tfrac12k\Delta l^2$); when only such conservative forces act, $KE+V$ is conserved. Power is the rate of doing work, $P=\mathbf F\cdot\mathbf v$, and efficiency is output over input power.

> [!summary]- Exam use: quick path
> - **Use it when:** a question links speeds, forces and distances (how far, how fast at a point) and asks nothing about time or acceleration; use power when a rate of working or a motor rating is involved.
> - **Assumptions:** particle; potential energies measured from a chosen datum; friction does work $-\mu_kNs$ (Coulomb model); internal forces of a rigid system do no net work.
> - **Method:** 1. Choose the two states 1 and 2 and a datum for $V_g$. 2. Draw the FBD and sort the forces: weight and springs go into $V$, forces doing no work are dropped, the rest go into $\sum U_{1-2}$. 3. Write $KE_1+V_{g1}+V_{e1}+\sum U_{1-2}=KE_2+V_{g2}+V_{e2}$. 4. Get $N$ (for friction) or a speed condition (for a loop) from Newton's law in the right direction. 5. Solve, and check the sign and size of the answer.
> - **Common mistakes:** counting the weight both as work and as potential energy; for a loop, taking the minimum speed at the top as zero instead of $\sqrt{gR}$.
> - **Practise:** [[#Block sliding down a rough incline]] · [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]] (Q9 pendulum regimes)

Newton's second law relates force to acceleration at an instant. In many problems the acceleration is not wanted, only how far a block slides before stopping, or how fast a car must enter a loop. Integrating Newton's law along the path gets straight from the forces to the change in speed, through the work done.

A force does work only to the extent that its point of application moves along it; a force perpendicular to the motion, such as the normal reaction on a block sliding along a floor, does none. The work done by all the forces on a particle equals the change of its kinetic energy. Some forces, notably gravity and springs, do work that depends only on where the particle starts and finishes, so the work can be stored and recovered; such forces have a potential energy. Friction and drag are different: the work they do depends on the distance travelled and cannot be recovered, and it ends up as heat.

---

## 1. Work of a force

### Definition

The dot product of two vectors at angle $\theta$ is

$$
\mathbf a\cdot\mathbf b=ab\cos\theta=a_xb_x+a_yb_y
$$

(writing $a_x=a\cos\theta_1$, $b_x=b\cos\theta_2$ and so on gives $ab\cos(\theta_2-\theta_1)$, the angle between them). As a particle moves along its path, an infinitesimal displacement $d\mathbf r$ lies along the tangent and its magnitude is the arc length, $|d\mathbf r|=ds$.

A force $\mathbf F$ does an amount of **work**

$$
dU=\mathbf F\cdot d\mathbf r=F\,ds\cos\theta
$$

on the particle, where $\theta$ is the angle between the force and the displacement. Over a finite movement from position 1 to position 2,

$$
U_{1-2}=\int_{\mathbf r_1}^{\mathbf r_2}\mathbf F\cdot d\mathbf r=\int_{s_1}^{s_2}F\cos\theta\,ds=\int_{s_1}^{s_2}F_t\,ds
$$

where $F_t=F\cos\theta$ is the component of the force tangent to the path. Work is a scalar measured in joules (1 J = 1 N m). It shares its unit with the moment of a force but has nothing else in common with it: a moment is a vector. The normal component $F_n$ does no work, because it is perpendicular to the displacement.

![[d_work_area.png|900]]

The work is the area under the curve of $F\cos\theta$ against $s$. If $F$ and $\theta$ are both constant and the path is straight,

$$
U_{1-2}=F\cos\theta\,(s_2-s_1)
$$

but this needs both conditions; otherwise the integral has to be done.

### Work of the weight

With $y$ vertical and positive up, the weight is $m\mathbf g=-mg\,\mathbf j$ and $d\mathbf r=dx\,\mathbf i+dy\,\mathbf j$, so

$$
U_{1-2}=\int(-mg\,\mathbf j)\cdot(dx\,\mathbf i+dy\,\mathbf j)
$$

$$
=-mg\int_{y_1}^{y_2}dy
$$

$$
=-mg(y_2-y_1)
$$

The work done by the weight depends only on the change of height, not on the path, and is negative when the particle rises.

### Work of gravitational attraction

Far from the Earth's surface the weight is not constant. The attraction of $m_1$ on $m_2$ is $\mathbf F_g=-G\frac{m_1m_2}{r^2}\mathbf u_r$, with $\mathbf u_r$ pointing from $m_1$ to $m_2$. Only the radial part of $d\mathbf r$, which is $dr\,\mathbf u_r$, contributes:

$$
U_{1-2}=\int_{r_1}^{r_2}-G\frac{m_1m_2}{r^2}\,dr
$$

$$
=\left[G\frac{m_1m_2}{r}\right]_{r_1}^{r_2}
$$

$$
=G\frac{m_1m_2}{r_2}-G\frac{m_1m_2}{r_1}
$$

This form is needed when the change in distance is significant compared with the Earth's radius: satellites and planets ([[FEEG1002 D5 - Angular Impulse and Momentum|D5]]).

### Work of a spring

Measure $s$ from the unstretched position, positive in the direction of stretching. The spring pulls back with $ks$, opposite to $s$, so

$$
U_{1-2}=-\int_{s_1}^{s_2}ks\,ds
$$

$$
=-\left(\tfrac12ks_2^2-\tfrac12ks_1^2\right)
$$

Stretching a spring further from its natural length takes work from the particle; the $\tfrac12$ comes from integrating a force that grows linearly with $s$.

### Work of friction

Kinetic friction $F_k=\mu_kN$ always opposes the sliding, so on a straight path of length $s$ with constant $N$,

$$
U_{1-2}=-\mu_kNs
$$

For a block slid from A to B and back to A, a distance $s$ each way, the friction reverses with the velocity and does $-\mu_kNs$ both ways, so the round trip costs $-2\mu_kNs$. For a mass lifted from A to B and back down, the weight does $-mgs$ then $+mgs$, a total of zero. Friction can only take energy away; the weight can add or remove it.

Static friction generally does no work, because the point of contact does not move relative to the surface. It does do work when it drags a body along with an accelerating support: a crate on the bed of an accelerating lorry is accelerated by static friction, $F_s=ma$ with $F_s\le\mu_sN$, and over a distance $s$ that friction does work $F_ss$ on the crate. It does equal and opposite work on the lorry, so for the crate and lorry together it is an internal force doing no net work.

## 2. Conservative forces and potential energy

A force is **conservative** if the work it does between two points is independent of the path. Equivalently, it does no work round any closed path:

$$
\oint\mathbf F\cdot d\mathbf r=0
$$

For such a force there is a function of position, the **potential energy** $V$, with

$$
\int_A^B\mathbf F\cdot d\mathbf r=-(V_B-V_A)
$$

The minus sign means that when a conservative force does positive work its potential energy falls. The work of a conservative force depends only on position, never on velocity or acceleration.

The three potentials used in mechanics are:

$$
V_g=mgy\qquad\text{(weight, constant }g\text{, }y\text{ up from a datum)}
$$

$$
V_g=-G\frac{m_1m_2}{r}\qquad\text{(gravitational attraction)}
$$

$$
V_e=\tfrac12k\,\Delta l^2,\quad\Delta l=l-l_0\qquad\text{(spring)}
$$

The datum for $V_g=mgy$ is arbitrary, because only changes of $V_g$ enter any calculation. The gravitational $V_g=-Gm_1m_2/r$ is always negative and tends to zero as $r\to\infty$. The elastic $V_e$ is always positive, for stretching and compression alike.

Kinetic friction, drag and a propulsive force are **non-conservative**: their work depends on the path. They are handled by evaluating $\int\mathbf F\cdot d\mathbf r$ directly.

## 3. The work-energy principle

### Derivation

Resolve Newton's second law along the tangent, the direction in which the speed changes:

$$
\sum F_t=ma_t
$$

Use $a_t=v\,dv/ds$ from [[FEEG1002 D2 - Curvilinear Motion#Acceleration|D2]]:

$$
\sum F_t=mv\frac{dv}{ds}
$$

Separate variables and integrate from state 1 to state 2:

$$
\sum\int_{s_1}^{s_2}F_t\,ds=\int_{v_1}^{v_2}mv\,dv
$$

$$
\sum U_{1-2}=\tfrac12mv_2^2-\tfrac12mv_1^2
$$

The **kinetic energy** of the particle is $KE=\tfrac12mv^2$, always positive, and the principle reads

$$
\boxed{KE_1+\sum U_{1-2}=KE_2}
$$

The work of all the forces on the particle equals its change of kinetic energy. The normal forces do not appear because they do no work. The equation is a scalar one, so it gives one unknown; it is the natural tool for problems involving forces, speeds and displacements, and the wrong one for finding a time or an acceleration.

### With potential energy

Split the work into the part done by conservative forces, written as $-\Delta V$, and the rest. Moving the conservative part to the potential-energy side:

$$
KE_1+\sum V_1+\sum U_{1-2}=KE_2+\sum V_2
$$

where $\sum U_{1-2}$ now contains only the non-conservative forces. In mechanics this is

$$
\boxed{KE_1+V_{g1}+V_{e1}+\sum U_{1-2}=KE_2+V_{g2}+V_{e2}}
$$

$V_g+V_e$ is the mechanical potential energy. Each force is counted once: the weight appears either as $V_g$ or as work, never both.

### Conservation of energy

If only conservative forces do work, $\sum U_{1-2}=0$ and

$$
KE_1+V_{g1}+V_{e1}=KE_2+V_{g2}+V_{e2}
$$

For a particle falling with initial speed $v_1$ through a height $\Delta h$, with the datum at the lower point:

$$
\tfrac12mv_1^2+mg\Delta h=\tfrac12mv_2^2
$$

$$
v_2^2=v_1^2+2g\Delta h
$$

which is the constant-acceleration result of [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration|D1]], recovered without time.

Energy conservation also answers the quarter-circle race of [[FEEG1002 D2 - Curvilinear Motion|D2]] (L04, ll. 322–435): on a frictionless quarter circle and on the straight chord between the same two points, the normal force does no work and the weight's work is $mgR$ on both, so the speeds at the bottom are equal. The times are not, and energy alone cannot give them.

### Friction and heat

For a block pulled at constant speed across a rough floor with a force $P$, the work-energy principle gives

$$
\tfrac12mv^2+Ps-\mu_kNs=\tfrac12mv^2
$$

$$
Ps=\mu_kNs
$$

The work done by $P$ is cancelled by the work of friction, but the block warms up and no heat appears in the equation. The resolution is that the surfaces are rough on a small scale: the asperities deform and stick, so the friction force acts through a displacement smaller than $s$, and the difference becomes internal energy. The particle model lumps this together, counting $\mu_kNs$ as both the work of friction and the heat produced (slides pp. 23–24). This does not change how problems are solved.

### Systems of particles

For several particles, write the principle for each and add. The internal forces $\mathbf f_i$ between particles come in equal, opposite, collinear pairs, and if the particles do not move relative to each other along the line joining them (no deformation), each pair does equal and opposite work. So

$$
\sum KE_1+\sum V_{mech,1}+\sum U_{1-2}=\sum KE_2+\sum V_{mech,2}
$$

with $\sum U_{1-2}$ the work of the external non-conservative forces only.

## 4. Power and efficiency

**Power** is the rate of doing work:

$$
P=\frac{dU}{dt}=\frac{\mathbf F\cdot d\mathbf r}{dt}=\mathbf F\cdot\mathbf v=Fv\cos\theta
$$

with $\theta$ the angle between the force and the velocity. It is measured in watts (1 W = 1 J/s = 1 N m/s); 1 hp = 746 W.

The **efficiency** of a machine is

$$
\eta=\frac{\text{power output}}{\text{power input}}=\frac{P_o}{P_i}
$$

always less than 1 because some of the input is lost to friction. Power problems need not use the work-energy principle at all: $P=Fv$ needs only the force and the speed at the instant, and these may come from any earlier tool.

The same idea gives a power balance for a vehicle at constant speed. A cyclist riding up a constant slope $\theta$ at speed $v$ against rolling resistance $C_RN$ (modelled like friction, with $C_R$ about a hundred times smaller than $\mu_k$, and arising from tyre deformation) and with drag neglected has $KE_1=KE_2$, so the propulsive work over a distance $d$ balances the weight and rolling resistance. Dividing by the time $d/v$:

$$
P=mgv(\sin\theta+C_R\cos\theta)
$$

$$
t=\frac dv=\frac{mgd(\sin\theta+C_R\cos\theta)}{P}
$$

The time to climb depends on the mass and the power only through $m/P$: losing mass and training harder are equivalent (L06, ll. 314–468).

---

## Worked examples

### Block sliding down a rough incline

A 50 kg block passes point A moving down a 10° incline at 6 m/s. The coefficient of kinetic friction is 0.5. How far past A does it slide before stopping? What if its mass were doubled, and what if the incline were 30° (slides pp. 26–30; DAMS3-2, ll. 69–147; L06, ll. 14–101)?

Take state 1 at A and state 2 at the stopping point B, a distance $s$ down the slope, and put the datum for $V_g$ at B, so $V_{gA}=mgs\sin\theta$. The FBD has the weight, the normal force and friction up the slope. Perpendicular to the incline there is no acceleration, so $N=mg\cos\theta$, and the friction does $-\mu_kmg\cos\theta\,s$. The normal force does no work. Then

$$
\tfrac12mv_A^2+mgs\sin\theta-\mu_kmg\cos\theta\,s=0
$$

$$
s=\frac{v_A^2}{2g(\mu_k\cos\theta-\sin\theta)}
$$

$$
s=\frac{36}{2\times9.81\times(0.5\times0.9848-0.1736)}=\frac{36}{6.254}=5.76\ \mathrm m
$$

![[d_incline_stopping_distance.png|900]]

The mass cancels, so doubling it changes nothing. At 30°, $\mu_k\cos\theta-\sin\theta=0.433-0.5<0$ and the formula gives $s=-27.4$ m.

> [!tip] A negative distance
> The question is wrongly posed at 30°: friction cannot hold the block, which accelerates down the slope at $g(\sin\theta-\mu_k\cos\theta)=0.657$ m/s² and never stops. The negative answer is the distance above A at which a block starting from rest would have had to set off to pass A at 6 m/s. Combining the energy result with Newton's law in this way shows what the numbers mean.

### Minimum speed for a loop

A particle enters a frictionless vertical circular loop of radius $R=1.5$ m at the bottom, A. Find the minimum entry speed for it to stay on the track, and the speed at C where it leaves the loop at the bottom again (slides pp. 31–35; DAMS3-2, ll. 148–200; L06, ll. 102–188).

![[d_loop_the_loop.png|900]]

The track can only push (the normal reaction is unilateral), so the particle stays on as long as $N\ge0$. The critical point is the top, B. There, with n-t axes and $n$ pointing down towards the centre, both $N$ and the weight point along $+n$:

$$
N+mg=m\frac{v_B^2}{R}
$$

and the tangential acceleration is zero at the top. The minimum speed has $N=0$:

$$
v_B=\sqrt{gR}=\sqrt{9.81\times1.5}=3.84\ \mathrm{m/s}
$$

Conservation of energy from B to A, with the datum at A (the normal force does no work), gives

$$
\tfrac12mv_B^2+mg(2R)=\tfrac12mv_A^2
$$

$$
v_A=\sqrt{v_B^2+4gR}=\sqrt{5gR}=8.58\ \mathrm{m/s}
$$

and by the same argument $v_C=v_A=8.58$ m/s.

> [!warning] The tempting wrong answer
> Setting $v_B=0$ gives $\tfrac12mv_A^2=mg(2R)$ and $v_A=\sqrt{4gR}=7.67$ m/s. A particle with that speed leaves the track before the top: at angle $\varphi$ from the top its height above A is $R(1+\cos\varphi)$, so $v^2=4gR-2gR(1+\cos\varphi)$, and the normal equation $N+mg\cos\varphi=mv^2/R$ gives $N=0$ when $3\cos\varphi=2$, i.e. $\varphi=48.2°$ from the top, at a height $5R/3=2.5$ m. It then flies as a projectile inside the loop.

### Motor hoisting a block through a pulley

A 50 kg block A is lifted by a cable that passes round a pulley attached to A, with one end fixed above and the other end, P, wound in by a motor of efficiency 0.8. At the instant shown P moves down at 12 m/s with an acceleration of 6 m/s². Find the power supplied to the motor (slides pp. 40–43; DAMS3-3, ll. 21–43).

The pulley and cable are massless. With positions measured down from the fixed support, the cable gives $s_P+2s_A=l$, so

$$
a_A=-\tfrac12a_P=-3\ \mathrm{m/s^2},\qquad v_A=-6\ \mathrm{m/s}
$$

(the block rises). The block carries two strands, so with down positive

$$
m_Ag-2T=m_Aa_A
$$

$$
50\times9.81-2T=50\times(-3)
$$

$$
T=\frac{490.5+150}{2}=320.25\ \mathrm N
$$

The motor's output power goes into the cable at P:

$$
P_o=Tv_P=320.25\times12=3843\ \mathrm W
$$

and the power that must be supplied to the motor is

$$
P_i=\frac{P_o}{\eta}=\frac{3843}{0.8}=4.80\ \mathrm{kW}
$$

> [!check] Power at the block
> The two strands at the block deliver $2Tv_A=2\times320.25\times6=3843$ W, the same output power: the cable only transmits it.

### Pendulum speed from energy

A pendulum of length $L$ is released from rest at $\theta_0$. Find $\dot\theta$ as a function of $\theta$ and, for small swings, the period (L12, ll. 349–509).

With the datum at the lowest point, the height of the bob is $L(1-\cos\theta)$ and its speed is $L\dot\theta$. The cable tension is perpendicular to the motion and does no work, so energy is conserved:

$$
mgL(1-\cos\theta_0)=\tfrac12m(L\dot\theta)^2+mgL(1-\cos\theta)
$$

$$
\dot\theta^2=\frac{2g}{L}(\cos\theta-\cos\theta_0)
$$

the same result as integrating $a_t\,ds=v\,dv$ in [[FEEG1002 D2 - Curvilinear Motion#Simple pendulum|D2]], obtained without any integration. For small angles, $\cos\theta\approx1-\theta^2/2$, so

$$
\dot\theta^2\approx\frac gL(\theta_0^2-\theta^2)
$$

Separating variables, with $\int d\theta/\sqrt{\theta_0^2-\theta^2}=\arcsin(\theta/\theta_0)$, and starting at $\theta=\theta_0$:

$$
\theta=\theta_0\cos\left(\sqrt{\frac gL}\,t\right),\qquad T=2\pi\sqrt{\frac Lg}
$$

For $L=1.2$ m, $T=2.20$ s, so five swings take about 11 s (L12, ll. 510–585).

### Collar on a rough vertical shaft

A collar of mass $m$ rests at A on a rough vertical shaft (kinetic friction $\mu_k$). A spring of stiffness $k$ and unstretched length $L/2$ joins it to a fixed point O at the same height as A, a horizontal distance $L$ away. A downward impulse $I$ sets the collar moving, and it comes to rest at C, where the spring makes $\psi=60°$ with the horizontal. Find the speed at A, the spring force at angle $\psi$, the equations of motion, and the work done by friction from A to C (L11, ll. 20–411, a 2016–17 exam question worth 25 marks; symbolic only).

The impulse acts over a very short time, so gravity and friction are non-impulsive and the collar starts from rest ([[FEEG1002 D4 - Linear Impulse and Momentum#Impulsive and non-impulsive forces|D4]]):

$$
0+I=mv_A\quad\Rightarrow\quad v_A=\frac Im\ \text{(downwards)}
$$

When the spring makes angle $\psi$ with the horizontal its length is $L_B$ with $L_B\cos\psi=L$, so its extension is measured from the unstretched length $L/2$, not from the initial length:

$$
F_s=k\left(\frac{L}{\cos\psi}-\frac L2\right)
$$

The FBD has $F_s$ along the spring towards O, the shaft's horizontal reaction $N$, the weight $mg$, and kinetic friction $\mu_kN$ upwards, since the collar slides down. With $x$ horizontal away from O (the direction of $N$) and $y$ up, there is no horizontal acceleration:

$$
\sum F_x:\ N-F_s\cos\psi=0
$$

$$
\sum F_y:\ \mu_kN+F_s\sin\psi-mg=ma
$$

These are not solved for $a$; the work of friction comes more directly from energy. Put the datum for $V_g$ at A. C is $L\tan60°=\sqrt3L$ below A, so $V_{gC}=-\sqrt3mgL$. The spring extensions are $L/2$ at A and $L/\cos60°-L/2=3L/2$ at C. With $KE_C=0$ and $U$ the work of friction:

$$
\tfrac12mv_A^2+\tfrac12k\left(\frac L2\right)^2+U=-\sqrt3mgL+\tfrac12k\left(\frac{3L}2\right)^2
$$

$$
U=\frac{9kL^2}{8}-\frac{kL^2}{8}-\sqrt3mgL-\frac{I^2}{2m}
$$

$$
U=kL^2-\sqrt3mgL-\frac{I^2}{2m}
$$

which must come out negative for a consistent set of data, since friction only removes energy.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 D2 - Curvilinear Motion]] · Next: [[FEEG1002 D4 - Linear Impulse and Momentum]]
- Concepts: [[Work-Energy Principle]] · [[Conservative Forces and Potential Energy]] · [[Power and Efficiency]]
- Worked sheet: [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 D5 - Angular Impulse and Momentum|D5]] (orbital energy with $V_g=-GMm/r$) · [[FEEG1002 D6 - Single Degree of Freedom Vibration|D6]] (energy exchange in a vibrating system) · [[FEEG1002 D9 - Work and Energy for Rigid Bodies|D9]] (rotational kinetic energy and the work of a couple) · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] · [[SESA2028 S7 - Strain Energy and Conservation of Energy]]

## Sources

- `Lecture 03 - Work, Energy and Power.pdf`: slides pp. 1–43 (work and potential energy pp. 2–17, work-energy principle pp. 18–25, incline pp. 26–30, loop pp. 31–35, power and efficiency pp. 36–43).
- Transcript labels used in this note:
  - L05 = `FEEG1002 Lecture 2025-02-12 - Dynamics - 05 - 12 February 2025 at 10 51 59.txt` and L05b = `...Dynamics 05b - 12 February 2025 at 11 57 32.txt` (12 Feb 2025, the same lecture to two groups): work, potentials, work-energy principle, friction and heat, systems.
  - L06 = `FEEG1002 Lecture 2025-02-13.txt` (13 Feb 2025): incline (ll. 14–101), loop (ll. 102–188), power (ll. 189–233), submarine quizzes (ll. 234–313), Box Hill (ll. 314–468).
  - L12 = `FEEG1002 Lecture 2025-03-06.txt` (6 Mar 2025 revision): pendulum by energy (ll. 349–509).
  - L11 = `FEEG1002 Lecture 2025-03-05.txt` (5 Mar 2025 revision): collar on a rough shaft, a 2016–17 exam question (ll. 20–411).
  - DAMS3-1 = `FEEG1002 Lecture 2021-01-26 - DAMS-3-WorkEnergyPower1.txt`; DAMS3-2 = `FEEG1002 Lecture 2021-12-07.txt`; DAMS3-3 = `FEEG1002 Lecture 2021-01-26 - DAMS-3-WorkEnergyPower3.txt`.
- `Tutorial Sheet 03 - Work, Energy and Power.pdf`: Q1–Q11, worked in the tutorial note.

## Self-study tasks

### Core

- [ ] Substitute the numbers in the incline example and store the formula (DAMS3-2, l. 104; L06, ll. 15, 57–58). Target 5.76 m. → [[#Block sliding down a rough incline]]
- [ ] Explain the negative distance at 30° (slide p. 29; L06, ll. 76–80). → [[#Block sliding down a rough incline]]
- [ ] Redo the loop with pen and paper and say why setting $v_B=0$ is wrong (DAMS3-2, ll. 185–187). → [[#Minimum speed for a loop]]
- [ ] Study the motor-and-pulley power example (L06, ll. 202, 229–233). Target 4.80 kW. → [[#Motor hoisting a block through a pulley]]
- [ ] Quiz: does static friction do work? (L05, ll. 337–341). → [[#Work of friction]]
- [ ] Tutorial 3 Q1–Q5 (work-energy with springs and friction). → [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]
- [ ] Tutorial 3 Q8–Q9 (pendulum regimes; Q9 extends the loop challenge). → [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]
- [ ] Past-paper collar on a rough shaft, all five parts (L11, ll. 20–411; on Blackboard, ll. 109–111). → [[#Collar on a rough vertical shaft]]

### Further practice

- [ ] Loop challenge: where does the particle leave the track if $v_A=\sqrt{4gR}$? (slide p. 35; DAMS3-2, ll. 184, 190; L06, ll. 167–187). Target 48.2° from the top. → [[#Minimum speed for a loop]]
- [ ] Do the Taylor substitution for the pendulum and integrate for $\theta(t)$ (L12, ll. 436–437). → [[#Pendulum speed from energy]]
- [ ] Predict your own time up Box Hill with your mass, power and a value of $C_R$ (L06, ll. 429–439). → [[#4. Power and efficiency]]
- [ ] Tutorial 3 Q6–Q7, Q10–Q11 (roller coaster, vehicle power). → [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]

## Transcript and slide slips

> [!warning] Slide slips (Lecture 03 slides)
> Where: [[#Motor hoisting a block through a pulley]].
>
> Slide p. 41 asks for the power "supplied by the motor", but the boxed answer of 4.8 kW on p. 43 is the power supplied to it; the motor supplies 3.84 kW. Slide p. 43's $P_o=3844$ W comes from rounding $T$ to 320.3 N.

### Transcript slips (L05, L05b, L06, L12, DAMS3)

| Ref | Said | Correct |
|---|---|---|
| DAMS3-1, l. 95 | conservative work depends "on the position and the path followed" | it is independent of the path |
| DAMS3-2, ll. 40–41 | energy is conserved when "the work done by all the forces is zero" | when only conservative forces do work |
| DAMS3-2, l. 71 | "66 meters per second" | 6 m/s |
| DAMS3-2, l. 181 | wrong-approach speed "7.54 m per second" | 7.67 m/s (slide p. 35) |
| DAMS3-3, l. 12 | power is force "divided by" velocity | multiplied |
| L05, l. 204; L05, l. 297 | work of weight "mg times y2 minus y1"; friction round trip "twice mu k N" | both need a minus sign |
| L05, l. 455 | block pulled at constant speed: "there is acceleration" | no acceleration |
| L05b, l. 213 | $V_g$ = "G m1 m2 divided by r" | $-Gm_1m_2/r$ |
| L05b, l. 432 | "mechanical energy and kinetic energy are conserved" | their sum is conserved |
| L06, l. 157 | loop entry speed "8.5 m/s" | 8.58, i.e. 8.6 m/s |
| L12, l. 333 | "g l sine theta" in the pendulum equation | $(g/L)\sin\theta$ |
