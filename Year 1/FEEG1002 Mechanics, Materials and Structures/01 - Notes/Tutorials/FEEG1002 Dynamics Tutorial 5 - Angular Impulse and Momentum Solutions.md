---
title: "FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, angular-momentum, central-force, orbits]
sheet: "Dynamics Problem sheet 5 (angular impulse and momentum)"
theory_notes: ["[[FEEG1002 D5 - Angular Impulse and Momentum]]"]
key_concepts: ["[[Principle of Angular Impulse and Momentum]]", "[[Work-Energy Principle]]", "[[Orbital Angular Momentum]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 05 - Angular Impulse and Momentum.pdf"]
---

# FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions

> [!abstract] Sheet summary
> Five problems on angular impulse and momentum of particles, each paired with a second law: energy for a disc on an elastic cord (Q1), the normal equation of motion for a block on a cord (Q2), a time-varying moment on a rotor (Q3), energy for a hyperbolic satellite path (Q4), and impulse, energy and friction in a table game (Q5). Final answers are printed for every numerical part and all are reproduced; Q2(a) prints 3.08 s where the data give 3.086 s, and Q5(d) asks for discussion, which is worked out numerically here.

The common thread is choosing the point about which to take moments. In Q1, Q4 and Q5 the force pulling on the particle always passes through a fixed point (a cord's anchor, the centre of the Earth), so angular momentum about that point is conserved and only the velocity component perpendicular to $\mathbf r$ enters it. In Q2 and Q3 there is a net moment, and the angular impulse it delivers gives the speed as a function of time. Angular momentum supplies one equation; the second unknown always needs energy or Newton's law along the radius.

---

## Q1 - Disc on an elastic cord

A 2 kg disc on a smooth horizontal plane is tied to O by an elastic cord ($k=20$ N/m), unstretched at $l_1=0.5$ m. It is given $v_1=1.5$ m/s perpendicular to the cord. Find its speed, and the rate at which the cord lengthens, when the cord has stretched to $l_2=0.7$ m.

The plane is smooth and horizontal, so the weight and normal reaction cancel and the only horizontal force is the cord tension. That force is conservative, so energy is conserved, and it always points at O, so angular momentum about O is conserved. Energy, with the cord stretched by $l_2-l_1=0.2$ m:

$$
\begin{aligned}
\tfrac12mv_1^2&=\tfrac12mv_2^2+\tfrac12k(l_2-l_1)^2\\
v_2^2&=v_1^2-\frac km(l_2-l_1)^2\\
&=1.5^2-\frac{20}{2}(0.2)^2\\
&=2.25-0.40=1.85\ \mathrm{m^2/s^2}
\end{aligned}
$$

$$
\boxed{v_2=1.36\ \mathrm{m/s}}
$$

Angular momentum about O involves only the component $v_2'$ perpendicular to the cord, since $v_1$ was entirely perpendicular:

$$
\begin{aligned}
l_1mv_1&=l_2mv_2'\\
v_2'&=\frac{l_1v_1}{l_2}=\frac{0.5\times1.5}{0.7}\\
&=1.071\ \mathrm{m/s}
\end{aligned}
$$

The rest of the speed is the radial component, which is the rate of change of the cord's length:

$$
\begin{aligned}
\dot l=v_2''&=\sqrt{v_2^2-v_2'^2}\\
&=\sqrt{1.850-1.148}\\
&=\sqrt{0.702}
\end{aligned}
$$

$$
\boxed{\dot l=0.838\ \mathrm{m/s}}
$$

Both match the printed answers.

Theory: [[FEEG1002 D5 - Angular Impulse and Momentum#Conservation of angular momentum]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Amusement-park ride pulled in on a cable]] · [[FEEG1002 D3 - Work, Energy and Power#Work of a spring]]

## Q2 - Block on a cord driven round a rough table

A 5 kg block on a rough horizontal surface ($\mu_k=0.5$) is tied to the centre A by an inextensible cord of length $R=1.2$ m. It is pushed by a radial force $F_1=10$ N and by $F_2=35$ N in the horizontal plane at $\theta=30°$ to the tangent. (a) From $v_1=0.6$ m/s, when does the tension reach 100 N? (b) From rest on a smooth surface, when does the cord break at 150 N, and how fast is the block then going? (c) Give $v(t)$ for both cases.

The block moves on a circle of radius $R$ about A, so its velocity is always tangential and its angular momentum about A is $H_A=mvR$. Take moments about A. The cord tension and $F_1$ are radial and have no moment, nor does the radial component $F_2\sin\theta$. The tangential component $F_2\cos\theta$ drives the block at lever arm $R$, and kinetic friction $\mu_kmg$ (the normal force is the weight, in a horizontal plane) opposes it at the same lever arm. Angular impulse and momentum from 0 to $t$, with the forces constant:

$$
\begin{aligned}
mv_1R+\int_0^t(F_2\cos\theta-\mu_kmg)R\,dt&=mvR\\
mv_1R+(F_2\cos\theta-\mu_kmg)Rt&=mvR\\
v&=v_1+\left(\frac{F_2\cos\theta}{m}-\mu_kg\right)t
\end{aligned}
$$

$$
\boxed{v(t)=v_1+\left(\frac{F_2\cos\theta}{m}-\mu_kg\right)t}
$$

which is part (c) and matches the printed expression. For case (a), $v_1=0.6$ m/s and $\mu_k=0.5$; for case (b), $v_1=0$ and $\mu_k=0$:

$$
\begin{aligned}
\text{(a)}\quad v&=0.6+\left(\frac{35\cos30°}{5}-0.5\times9.81\right)t=0.6+1.157\,t\\
\text{(b)}\quad v&=\frac{35\cos30°}{5}\,t=6.062\,t
\end{aligned}
$$

The tension comes from Newton's law along the normal (towards A). As drawn on the sheet, $F_1$ points radially outwards and $F_2$ is inclined outwards from the tangent, so its radial component $F_2\sin\theta$ also points away from A. With the inward direction positive,

$$
\begin{aligned}
T-F_1-F_2\sin\theta&=\frac{mv^2}{R}\\
T&=\frac{mv^2}{R}+F_1+F_2\sin\theta\\
v&=\sqrt{\frac{R}{m}\,(T-F_1-F_2\sin\theta)}
\end{aligned}
$$

with $F_1+F_2\sin\theta=10+17.5=27.5$ N. For (a), $T=100$ N:

$$
\begin{aligned}
v&=\sqrt{\frac{1.2}{5}\,(100-27.5)}=\sqrt{17.40}=4.171\ \mathrm{m/s}\\
t&=\frac{4.171-0.6}{1.157}=3.086\ \mathrm s
\end{aligned}
$$

$$
\boxed{\text{(a)}\ t=3.09\ \mathrm s,\quad v=4.17\ \mathrm{m/s}}
$$

For (b), $T=150$ N:

$$
\begin{aligned}
v&=\sqrt{\frac{1.2}{5}\,(150-27.5)}=\sqrt{29.40}=5.422\ \mathrm{m/s}\\
t&=\frac{5.422}{6.062}=0.894\ \mathrm s
\end{aligned}
$$

$$
\boxed{\text{(b)}\ t=0.894\ \mathrm s,\quad v=5.42\ \mathrm{m/s}}
$$

The sheet prints 3.08 s for (a); the data give 3.086 s, so the printed value is truncated rather than rounded. The printed answers also confirm the force directions: if $F_2\sin\theta$ pointed inwards instead, the same steps would give 3.87 s and 5.08 m/s for (a).

![[d_t5_q2_cord_tension.png|700]]

Theory: [[FEEG1002 D5 - Angular Impulse and Momentum#3. Principle of angular impulse and momentum]] · [[FEEG1002 D2 - Curvilinear Motion#5. Equations of motion in n-t coordinates]]

## Q3 - Four spheres driven by a growing moment

Four 2.5 kg spheres sit at $R=0.18$ m on a light crossbar that turns about a vertical shaft. From rest a moment $M=1.5(0.5t+0.8)$ N m is applied. Find the speed of each ball as a function of time, its value at 4 s, and the number of revolutions in 4 s.

Treat each sphere as a particle at radius $R$ moving tangentially at speed $v$; the crossbar has negligible mass. The system's angular momentum about the shaft is $H=4mRv$, and the bearing forces pass through the shaft, so the applied moment is the only one. Angular impulse and momentum from rest:

$$
\begin{aligned}
0+\int_0^tM\,dt&=4mRv\\
\int_0^t1.5(0.5t+0.8)\,dt&=4(2.5)(0.18)\,v\\
1.5\left(0.25t^2+0.8t\right)&=1.8\,v\\
v&=\frac{0.375t^2+1.2t}{1.8}
\end{aligned}
$$

$$
\boxed{v(t)=0.2083\,t^2+0.6667\,t\ \ \mathrm{m/s}}
$$

At $t=4$ s:

$$
\begin{aligned}
v&=0.2083(16)+0.6667(4)\\
&=3.333+2.667
\end{aligned}
$$

$$
\boxed{v(4)=6.00\ \mathrm{m/s}}
$$

The distance travelled by a sphere along its circle is the integral of the speed:

$$
\begin{aligned}
s&=\int_0^4v\,dt=\left[\frac{0.2083}{3}t^3+\frac{0.6667}{2}t^2\right]_0^4\\
&=0.06944(64)+0.3333(16)\\
&=4.444+5.333=9.778\ \mathrm m
\end{aligned}
$$

and one revolution is $2\pi R=1.131$ m, so

$$
\boxed{N=\frac{9.778}{2\pi\times0.18}=8.65\ \text{revolutions}}
$$

Both match the printed 6 m/s and 8.6 revs.

Theory: [[FEEG1002 D5 - Angular Impulse and Momentum#3. Principle of angular impulse and momentum]]

## Q4 - Satellite on a free-flight trajectory

A 700 kg satellite at A has $v_A=10$ km/s, $r_A=15\times10^6$ m from the Earth's centre, with $\phi_A=70°$ the angle between $\mathbf r_A$ and $\mathbf v_A$. With $m_e=5.976\times10^{24}$ kg and $G=66.73\times10^{-12}$ m³/(kg s²), find the closest distance $r_B$ and the speed $v_B$ there.

Treat the Earth as fixed. Gravity is central, so angular momentum about the Earth's centre is conserved, and conservative, so energy is conserved with $V_g=-Gm_em_s/r$. At A the velocity is not perpendicular to $\mathbf r_A$, so only its perpendicular component $v_A\sin\phi_A$ enters the angular momentum; at the closest point B the velocity is perpendicular to $\mathbf r_B$. The satellite's mass cancels from both equations, so work per unit mass with $GM=Gm_e=3.988\times10^{14}$ m³/s² and $h=H_O/m_s$:

$$
\begin{aligned}
h&=r_Av_A\sin\phi_A=15\times10^6\times10^4\times\sin70°\\
&=1.4095\times10^{11}\ \mathrm{m^2/s}\\
r_Bv_B&=h
\end{aligned}
$$

Energy from A to B, with $r_B=h/v_B$ substituted:

$$
\begin{aligned}
\tfrac12v_A^2-\frac{GM}{r_A}&=\tfrac12v_B^2-\frac{GM}{r_B}\\
\tfrac12v_A^2-\frac{GM}{r_A}&=\tfrac12v_B^2-\frac{GM\,v_B}{h}\\
v_B^2-\frac{2GM}{h}\,v_B-\left(v_A^2-\frac{2GM}{r_A}\right)&=0
\end{aligned}
$$

The coefficients are $2GM/h=5658$ m/s and $v_A^2-2GM/r_A=10^8-5.317\times10^7=4.683\times10^7$ m²/s², so

$$
\begin{aligned}
v_B&=\frac{5658+\sqrt{5658^2+4\times4.683\times10^7}}{2}\\
&=\frac{5658+14\,810}{2}\\
&=10\,234\ \mathrm{m/s}
\end{aligned}
$$

The other root is negative and is rejected. Then

$$
\begin{aligned}
r_B&=\frac{h}{v_B}=\frac{1.4095\times10^{11}}{10\,234}\\
&=13.77\times10^6\ \mathrm m
\end{aligned}
$$

$$
\boxed{v_B=10.2\ \mathrm{km/s},\qquad r_B=13.8\times10^6\ \mathrm m}
$$

matching the printed answers. Unlike the elliptical-orbit example in the topic note, A is not an apse here, so $v_B=v_A$ is not a root of the quadratic. The radial component of $\mathbf v_A$, $v_A\cos70°=3.42$ km/s, never enters the calculation.

> [!check] Why "NOT an orbit"
> The specific energy is $\tfrac12v_A^2-GM/r_A=+2.34\times10^7$ J/kg, positive, and $v_A=10$ km/s exceeds the escape speed at A, $\sqrt{2GM/r_A}=7.29$ km/s. The path is a hyperbola (eccentricity 2.6): the satellite swings past the Earth once at 13.8 × 10⁶ m and does not return.

Theory: [[FEEG1002 D5 - Angular Impulse and Momentum#Satellite in an elliptical orbit]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Plane motion]]

## Q5 - Table game with an elastic cord and a rough inner circle

A 0.25 kg mass on a horizontal table is tied to O by an elastic cord of natural length $L=0.2$ m and stiffness $k=1500$ N/m (it carries force only when stretched). An inner circle of radius $R=0.2$ m about O is rough ($\mu_k=0.8$); outside it the table is frictionless. At A, with $OA=0.3$ m along $x$, the mass moves at $u_A=1$ m/s in $+y$ and is struck by a bat with an impulse of 0.5 N s in $+y$.

### Part (a) - velocity after the bat

The sheet's figure shows $u_A$ along $+y$, parallel to the impulse; the printed 3 m/s depends on that. The bat's impulse is far larger than anything else acting during the strike, so impulse and momentum along $y$ give

$$
\begin{aligned}
mu_A+J&=mv_A\\
v_A&=u_A+\frac Jm=1+\frac{0.5}{0.25}\\
&=3\ \mathrm{m/s}
\end{aligned}
$$

$$
\boxed{v_A=3\ \mathrm{m/s}\ \text{in }+y}
$$

and the gain in kinetic energy is

$$
\begin{aligned}
\Delta KE&=\tfrac12m(v_A^2-u_A^2)\\
&=\tfrac12(0.25)(9-1)
\end{aligned}
$$

$$
\boxed{\Delta KE=1.0\ \mathrm J}
$$

### Part (b) - speed at B and closest distance OC

From A to B the mass is outside the inner circle, so there is no friction, and the only horizontal force is the cord tension. At A the cord is stretched by $0.3-0.2=0.1$ m; at B, on the edge of the inner circle, it is at its natural length and stores nothing. Energy conservation:

$$
\begin{aligned}
\tfrac12mv_A^2+\tfrac12k(0.1)^2&=\tfrac12mv_B^2\\
v_B^2&=v_A^2+\frac km(0.1)^2\\
&=9+\frac{1500}{0.25}(0.01)\\
&=9+60=69\ \mathrm{m^2/s^2}
\end{aligned}
$$

$$
\boxed{v_B=8.31\ \mathrm{m/s}}
$$

The cord tension always points at O and the outer table is frictionless, so no force has a moment about O between A and B and the angular momentum about O is conserved. At A the velocity is perpendicular to OA. At B write the angular momentum as $mv_Bd$, with $d$ the perpendicular distance from O to the line of $\mathbf v_B$:

$$
\begin{aligned}
m\,(OA)\,v_A&=mv_Bd\\
d&=\frac{OA\,v_A}{v_B}=\frac{0.3\times3}{8.307}\\
&=0.1083\ \mathrm m
\end{aligned}
$$

Inside the inner circle the cord is slack, and the only horizontal force is friction, which acts along the line of motion. The mass therefore travels in a straight line from B, and the closest point C on that line is the foot of the perpendicular from O. Hence

$$
\boxed{OC=d=10.83\ \mathrm{cm}}
$$

Angular momentum conservation can be used to find this distance because the cord force is central about O and the outer surface exerts no friction, so $H_O$ is the same at B as at A; and because the path inside is straight, the perpendicular distance of that line from O, fixed at B, is the closest approach. (Friction changes $H_O$ after B by slowing the mass, but it does not move the line.)

### Part (c) - does the mass exit at D?

Along the straight chord BD the friction force $\mu_kmg=0.8\times0.25\times9.81=1.962$ N acts along the path at the fixed perpendicular distance $d$ from O, so its moment about O is constant, $\mu_kmg\,d=0.2126$ N m. The chord length is

$$
\begin{aligned}
s_{BD}&=2\sqrt{R^2-d^2}=2\sqrt{0.04-0.01174}\\
&=0.3362\ \mathrm m
\end{aligned}
$$

and the friction gives a constant deceleration $\mu_kg=7.848$ m/s², so

$$
\begin{aligned}
v_D^2&=v_B^2-2\mu_kg\,s_{BD}\\
&=69-2(7.848)(0.3362)\\
&=69-5.28=63.72\ \mathrm{m^2/s^2}
\end{aligned}
$$

$$
\boxed{v_D=7.98\ \mathrm{m/s}>0,\ \text{so the mass exits the circle at D}}
$$

matching the printed answer. The same result follows from the angular impulse of the constant friction moment. The time on the chord is $t=(v_B-v_D)/(\mu_kg)=(8.307-7.983)/7.848=0.0413$ s, and

$$
\begin{aligned}
mv_Dd&=mv_Bd-\mu_kmg\,d\,t\\
v_D&=v_B-\mu_kg\,t=7.98\ \mathrm{m/s}
\end{aligned}
$$

which is consistent but needs the time first; the work-energy route is quicker. Stopping inside would need a stopping distance $v_B^2/(2\mu_kg)=4.40$ m, thirteen times the chord.

### Part (d) - making the game playable

The printed answer refers to solutions not provided, so the three changes are assessed here with the same equations, keeping $u_A=1$ m/s, $J=0.5$ N s and the cord unchanged.

A rougher mass raises $\mu_k$ inside the circle only, since the outer table is frictionless. The path to B and the chord are unchanged, so to stop within 0.336 m the mass would need $\mu_k\ge v_B^2/(2g\,s_{BD})=69/(2\times9.81\times0.3362)=10.5$, which no real surface provides. On its own this does not make the game playable.

A heavier mass changes both the speed and the path. The same impulse gives a smaller velocity change $J/m$, and the same 7.5 J of cord energy gives less speed, since $v_B^2=(u_A+J/m)^2+k(0.1)^2/m$. But $d=OA\,v_A/v_B$ grows as $v_B$ falls, so the chord shortens:

| $m$ (kg) | $v_A$ (m/s) | $v_B$ (m/s) | $d$ (cm) | $s_{BD}$ (m) | $v_D$ (m/s) |
|---|---|---|---|---|---|
| 0.25 | 3.00 | 8.31 | 10.8 | 0.336 | 7.98 |
| 1 | 1.50 | 4.15 | 10.8 | 0.336 | 3.46 |
| 6.25 | 1.08 | 1.89 | 17.2 | 0.206 | 0.58 (smallest) |
| 11 | 1.05 | 1.57 | 20.0 | 0 | misses the circle |

The exit speed is smallest, 0.58 m/s, at about 6.2 kg; it never reaches zero, and above 10.98 kg the closest approach exceeds $R$ and the mass never enters the circle at all. A heavier mass brings the game much closer to playable, and combined with a rougher mass it could work (at 6.25 kg, $\mu_k\ge1.89^2/(2\times9.81\times0.206)=0.88$ would stop it), but with $\mu_k=0.8$ alone it does not.

An inextensible cord of length 0.3 m keeps the mass at $r=0.3$ m. With $v_A$ perpendicular to the cord, the tension is perpendicular to the velocity and does no work, and the outer table is frictionless, so the mass circles at a constant 3 m/s with tension $mv_A^2/r=0.25\times9/0.3=7.5$ N. It never enters the inner circle, so the game becomes unplayable.

Theory: [[FEEG1002 D5 - Angular Impulse and Momentum#Fun-fair game with an elastic cord]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Impulse and average force]] · [[FEEG1002 D3 - Work, Energy and Power#Work of friction]]

---

## Links

- Topic note: [[FEEG1002 D5 - Angular Impulse and Momentum]] · impulse from [[FEEG1002 D4 - Linear Impulse and Momentum]] · energy from [[FEEG1002 D3 - Work, Energy and Power]] · normal equation from [[FEEG1002 D2 - Curvilinear Motion]]
- Concepts: [[Principle of Angular Impulse and Momentum]] · [[Orbital Angular Momentum]] · [[Work-Energy Principle]] · [[Conservative Forces and Potential Energy]] · [[Normal and Tangential Coordinates]]
- Hub: [[FEEG1002 Mechanics, Materials and Structures Hub]]

## Sources

- `Tutorial Sheet 05 - Angular Impulse and Momentum.pdf` (Dynamics Problem sheet 5): Q1–Q5 with printed final answers, no worked solutions; Q5(d) prints "see solutions".
- The reverse version of Q5 (finding the strike speed that stops the mass at the far edge) was worked in the 5 Mar 2025 revision lecture, `FEEG1002 Lecture 2025-03-05.txt`, ll. 412–629, and is in the topic note.
