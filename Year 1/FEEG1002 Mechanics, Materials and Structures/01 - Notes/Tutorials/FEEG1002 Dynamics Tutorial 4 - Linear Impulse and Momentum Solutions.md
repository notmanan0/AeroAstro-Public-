---
title: "FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, impulse, momentum, impact, recoil]
sheet: "Dynamics Problem sheet 4 (linear impulse and momentum)"
theory_notes: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
key_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Coefficient of Restitution]]", "[[Work-Energy Principle]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 04 - Linear Impulse and Momentum.pdf"]
---

# FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions

> [!abstract] Sheet summary
> Seven problems on the principle of linear impulse and momentum: average and peak impact forces (Q1, Q2), a spring cannon fixed to the ground and free to recoil (Q3, Q4), a plastic two-dimensional impact (Q5), brick throwing as a model of rocket propulsion (Q6) and an elastic oblique impact of billiard balls (Q7). Final answers are printed on the sheet and every one is reproduced here; Q2(d) prints its two answers in the reverse order, and Q4 and Q6 depend on how a velocity "relative to" a moving body is read, so both readings are given. Q7 uses oblique impact, which is outside the assessed scope.

Every question below comes down to one decision before any algebra: which body or system to draw, and which external impulses act on it. When the external impulses on a system cancel (Q4 horizontally, Q5, Q6, Q7), its momentum is conserved; when rigid ground or a wall is involved (Q1 to Q4 vertically), the ground supplies an impulse and the body's momentum changes by exactly that amount.

---

## Q1 - Crash test of an energy-absorbing bumper

A 1500 kg car hits a barrier at $v_1=3$ m/s and rebounds at $v_2=1$ m/s; the impact lasts $\Delta t=0.4$ s. Find the average force on the car, its average acceleration, and say whether the maximum acceleration can be found.

Take the approach direction as positive, so the car arrives at $+3$ m/s and leaves at $-1$ m/s. The only horizontal force is the barrier's push, and over the contact time its impulse equals $F_{avg}\Delta t$ by the definition of the average force. Impulse and momentum along the line of motion:

$$
\begin{aligned}
mv_1+F_{avg}\,\Delta t&=mv_2\\
F_{avg}&=\frac{m(v_2-v_1)}{\Delta t}\\
&=\frac{1500\,(-1-3)}{0.4}\\
&=-15\,000\ \mathrm N
\end{aligned}
$$

$$
\boxed{|F_{avg}|=15.0\ \mathrm{kN}\ \text{(directed away from the barrier)}}
$$

The average acceleration follows from Newton's second law with the average force, or directly from the change in velocity:

$$
\begin{aligned}
a_{avg}&=\frac{F_{avg}}{m}=\frac{v_2-v_1}{\Delta t}\\
&=\frac{-1-3}{0.4}\\
&=-10\ \mathrm{m/s^2}
\end{aligned}
$$

$$
\boxed{a_{avg}=-10.0\ \mathrm{m/s^2}}
$$

Both match the printed answers. The velocity change is 4 m/s, not 2, because the rebound counts.

For part (c), the maximum acceleration cannot be found from these data. The impulse fixes only the area under the force-time curve, and many curves of different shape have the same area over 0.4 s. A half-sine pulse would peak at $\tfrac\pi2$ times the average (23.6 kN, $-15.7$ m/s²), a symmetric triangle at twice the average (30 kN, $-20$ m/s²). The force-time history, or a model of the bumper's stiffness, would be needed.

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#Crash test]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Impulse and average force]]

## Q2 - Tennis ball with a half-sine contact force

A 0.06 kg ball is dropped from $h=2.5$ m onto rigid, smooth ground. The contact force is a half-sine pulse of amplitude $A=230$ N lasting $t_0=5$ ms. Find the velocity just before impact, the velocity after, the average force, and the peak and average accelerations.

Take up as positive. During the fall only the weight acts (air drag is neglected), so energy conservation from rest gives the impact speed:

$$
\begin{aligned}
mgh&=\tfrac12mv_1^2\\
|v_1|&=\sqrt{2gh}=\sqrt{2\times9.81\times2.5}\\
&=7.00\ \mathrm{m/s}
\end{aligned}
$$

$$
\boxed{v_1=-7.00\ \mathrm{m/s}\ \text{(downwards)}}
$$

The impulse of the contact force is the area under the half sine:

$$
\begin{aligned}
I&=\int_0^{t_0}A\sin\frac{\pi t}{t_0}\,dt\\
&=A\,\frac{t_0}{\pi}\left[-\cos\frac{\pi t}{t_0}\right]_0^{t_0}\\
&=A\,\frac{t_0}{\pi}\,(1+1)\\
&=\frac{2At_0}{\pi}=\frac{2\times230\times0.005}{\pi}\\
&=0.732\ \mathrm{N\,s}
\end{aligned}
$$

Over 5 ms the weight's impulse is $mg\,t_0=0.06\times9.81\times0.005=0.0029$ N s, 0.4% of $I$, so the weight is non-impulsive and is neglected during contact. Impulse and momentum, vertically:

$$
\begin{aligned}
mv_1+I&=mv_2\\
v_2&=v_1+\frac Im\\
&=-7.004+\frac{0.7321}{0.06}\\
&=-7.004+12.202
\end{aligned}
$$

$$
\boxed{v_2=+5.20\ \mathrm{m/s}\ \text{(upwards)}}
$$

Keeping the weight's impulse would give $v_2=5.15$ m/s, a 1% change. The average force is the constant force with the same impulse over the same time:

$$
\begin{aligned}
F_{avg}&=\frac{I}{t_0}=\frac{2A}{\pi}\\
&=\frac{0.7321}{0.005}
\end{aligned}
$$

$$
\boxed{F_{avg}=146.4\ \mathrm N}
$$

which is about 250 times the ball's weight of 0.59 N, confirming that the weight can be left out. The accelerations follow by dividing the forces by the mass:

$$
\begin{aligned}
a_{peak}&=\frac Am=\frac{230}{0.06}=3833\ \mathrm{m/s^2}\\
a_{avg}&=\frac{F_{avg}}m=\frac{146.4}{0.06}=2440\ \mathrm{m/s^2}
\end{aligned}
$$

$$
\boxed{a_{peak}=3.83\ \mathrm{km/s^2}\ (391g),\qquad a_{avg}=2.44\ \mathrm{km/s^2}\ (249g)}
$$

> [!warning] Printed order in part (d)
> The question asks for "the peak and the average acceleration", but the sheet prints "2.44 km/s², 3.83 km/s²", which is the average first and then the peak. The peak is the larger, 3.83 km/s².

As a comment on the results, the ball leaves at 5.20 m/s after arriving at 7.00 m/s, so the implied coefficient of restitution is $e=5.20/7.00=0.74$ and the ball rebounds to $5.20^2/(2g)=1.38$ m. The model treats the ball as a particle, ignores air drag in the fall, idealises the contact force as an exact half sine, and neglects the weight during contact; only the last of these is checked above, and it costs about 1% in $v_2$. Strictly the net peak acceleration is $(230-0.59)/0.06=3.82$ km/s², which rounds to the same figure.

![[d_impulse_force_time.png|880]]

The left panel is the trapezium pulse from the lecture example; the right panel is this question's half-sine pulse.

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#Tennis ball bouncing off the ground]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Impulsive and non-impulsive forces]]

## Q3 - Spring cannon fixed to the ground

A 2000 kg cannon, rigidly fixed to the ground, fires a $m_s=5$ kg shell at $\theta=30°$ to the horizontal using a spring of stiffness $k=10^6$ N/m compressed by $\Delta l=0.5$ m. Find the exit velocity, the impulses from the ground on the cannon, and the average ground forces if the shell leaves in $\Delta t=4$ ms.

Because the cannon cannot move, the spring's stored energy all goes into the shell (friction and changes in gravitational potential energy in the barrel are neglected):

$$
\begin{aligned}
\tfrac12k\,\Delta l^2&=\tfrac12m_sv_s^2\\
v_s&=\Delta l\sqrt{\frac{k}{m_s}}\\
&=0.5\sqrt{\frac{10^6}{5}}\\
&=223.6\ \mathrm{m/s}
\end{aligned}
$$

$$
\boxed{v_s=\Delta l\sqrt{k/m_s}=223.6\ \mathrm{m/s}}
$$

For the impulses, take the cannon and shell together as the system. The spring force is internal, and the cannon stays at rest, so the system's change of momentum is the shell's momentum alone, $m_sv_s=5\times223.6=1118.0$ N s along the barrel. The only external impulse doing this is the ground's (the weight is balanced by the static ground reaction, which is separate from the firing impulse asked for here). With $x$ forward and $y$ up:

$$
\begin{aligned}
I_x&=m_sv_s\cos30°=1118.0\times0.8660=968.2\ \mathrm{N\,s}\\
I_y&=m_sv_s\sin30°=1118.0\times0.5=559.0\ \mathrm{N\,s}
\end{aligned}
$$

$$
\boxed{I_y=559.0\ \mathrm{N\,s},\qquad I_x=968.2\ \mathrm{N\,s}}
$$

Both act on the cannon forwards and upwards: the spring drives the cannon backwards and down into the ground, and the ground holds it in place. The average forces over the 4 ms firing are

$$
\begin{aligned}
F_y&=\frac{I_y}{\Delta t}=\frac{559.0}{0.004}=139.8\ \mathrm{kN}\\
F_x&=\frac{I_x}{\Delta t}=\frac{968.2}{0.004}=242.1\ \mathrm{kN}
\end{aligned}
$$

$$
\boxed{F_y=139.8\ \mathrm{kN},\qquad F_x=242.1\ \mathrm{kN}}
$$

The sheet prints 242.0 kN; the unrounded value is 242.06 kN, so this is a rounding difference only. These are the forces due to firing; the static reaction to the weight of cannon and shell, $2005\times9.81=19.7$ kN, is on top of $F_y$.

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#Systems of particles]] · [[FEEG1002 D3 - Work, Energy and Power#Work of a spring]]

## Q4 - Spring cannon free to recoil

The same cannon now starts at rest on a rigid, smooth horizontal surface and can roll freely. Find the shell's exit velocity, the cannon's recoil velocity, the ground impulses and the average vertical force over 4 ms.

Take the cannon and shell as the system. Horizontally there is no external force (smooth surface), so horizontal momentum is conserved; vertically the ground still acts, so vertical momentum is not. The spring energy is shared between the shell and the recoiling cannon. Following the sheet, take the shell's velocity $v_s$ as directed at 30° to the horizontal, with the cannon moving back at $v_C$:

$$
\begin{aligned}
0&=m_sv_s\cos\theta-m_Cv_C\\
v_C&=\frac{m_sv_s\cos\theta}{m_C}
\end{aligned}
$$

Energy, with no losses in the barrel:

$$
\begin{aligned}
\tfrac12k\,\Delta l^2&=\tfrac12m_sv_s^2+\tfrac12m_Cv_C^2\\
k\,\Delta l^2&=m_sv_s^2+m_C\left(\frac{m_sv_s\cos\theta}{m_C}\right)^2\\
k\,\Delta l^2&=v_s^2\left(m_s+\frac{m_s^2\cos^2\theta}{m_C}\right)\\
v_s&=\Delta l\sqrt{\frac{k}{m_s+m_s^2\cos^2\theta/m_C}}
\end{aligned}
$$

With numbers, $m_s^2\cos^2\theta/m_C=25\times0.75/2000=0.009375$ kg, so

$$
\begin{aligned}
v_s&=0.5\sqrt{\frac{10^6}{5.009375}}\\
&=223.4\ \mathrm{m/s}
\end{aligned}
$$

$$
\boxed{v_s=223.4\ \mathrm{m/s}}
$$

Compared with Q3 (223.6 m/s), the shell is 0.2 m/s slower. The difference is the energy taken by the recoiling cannon, $\tfrac12m_Cv_C^2=234$ J out of 125 kJ, or 0.19%; it is small because the cannon is 400 times heavier than the shell. The recoil velocity is

$$
\begin{aligned}
v_C&=\frac{5\times223.4\times0.8660}{2000}\\
&=0.484\ \mathrm{m/s}
\end{aligned}
$$

$$
\boxed{v_C=0.48\ \mathrm{m/s}\ \text{(backwards)}}
$$

Vertically the cannon cannot move, so the ground supplies all of the shell's vertical momentum, and horizontally the smooth ground supplies nothing:

$$
\begin{aligned}
I_y&=m_sv_s\sin\theta=5\times223.4\times0.5=558.5\ \mathrm{N\,s}\\
I_x&=0
\end{aligned}
$$

$$
\boxed{I_y=558.5\ \mathrm{N\,s},\qquad |I_x|=0}
$$

and the average vertical force over the firing is

$$
\boxed{F_y=\frac{558.5}{0.004}=139.6\ \mathrm{kN}}
$$

All four match the printed answers.

> [!note] Which velocity is at 30°
> The sheet's answers take the shell's absolute velocity at 30°. Strictly, the barrel fixes the direction of the shell relative to the moving cannon. With the shell leaving at speed $u$ along the barrel relative to the cannon, its absolute velocity is $(u\cos\theta-v_C,\ u\sin\theta)$, and momentum and energy give $v_C=m_su\cos\theta/(m_s+m_C)$ and $u=223.8$ m/s. The shell's absolute speed is then 223.40 m/s at 30.06°, $v_C=0.483$ m/s, $I_y=559.5$ N s and $F_y=139.9$ kN. The two readings differ only in the fourth significant figure, because the cannon is so much heavier than the shell.

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#2. Conservation of linear momentum]] · [[FEEG1002 D3 - Work, Energy and Power#Conservation of energy]]

## Q5 - Meteor embedded in a satellite

A 400 kg satellite moving at 7 km/s is struck by a 2 kg meteor moving at 12 km/s at 135° to the satellite's path (approaching at 45° from ahead and above, as drawn). The meteor embeds itself. Find the speed and direction of the common centre of mass and comment on the effect.

The impact lasts a very short time and the only large forces are the internal contact forces, so the momentum of satellite plus meteor is conserved. The meteor embeds, so the impact is plastic and the two move together at the velocity of the centre of mass. With $x$ along the satellite's original path and $y$ up the page, the meteor's velocity is $12(\cos225°,\ \sin225°)=(-8.485,\ -8.485)$ km/s. Working in kg km/s:

$$
\begin{aligned}
(m_s+m_m)\,\mathbf v&=m_s\mathbf v_s+m_m\mathbf v_m\\
402\,\mathbf v&=400\,(7,\ 0)+2\,(-8.485,\ -8.485)\\
402\,\mathbf v&=(2783.0,\ -16.97)\\
\mathbf v&=(6.9230,\ -0.04222)\ \mathrm{km/s}
\end{aligned}
$$

$$
\begin{aligned}
|\mathbf v|&=\sqrt{6.9230^2+0.04222^2}=6.923\ \mathrm{km/s}\\
\alpha&=\tan^{-1}\frac{0.04222}{6.9230}=0.349°
\end{aligned}
$$

$$
\boxed{|\mathbf v|=6.92\ \mathrm{km/s},\qquad \alpha=0.35°\ \text{below the original path}}
$$

Both match the printed answers. The effect on the satellite is a sudden loss of 77 m/s and a small turn towards the meteor's direction of travel. For a satellite in orbit that is an unplanned change of orbit: with less speed at that point, its orbital energy falls and the far side of the orbit drops. The impact is also violent. Kinetic energy is not conserved in a plastic impact:

$$
\begin{aligned}
KE_1&=\tfrac12(400)(7000)^2+\tfrac12(2)(12\,000)^2=9.944\ \mathrm{GJ}\\
KE_2&=\tfrac12(402)(6923)^2=9.634\ \mathrm{GJ}\\
\Delta KE&=0.310\ \mathrm{GJ}
\end{aligned}
$$

so about 310 MJ goes into heat, deformation and debris, which would almost certainly cause serious damage.

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#2. Conservation of linear momentum]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Energy lost in an impact]]

## Q6 - Boy throwing bricks from a wagon

A 36 kg boy in a 9 kg wagon, initially at rest, throws three 4.5 kg bricks backwards horizontally at $v_b'=3$ m/s relative to the wagon. Horizontal forces on the wheels are neglected. Find his final speed if he throws them one at a time, and if he throws them all at once.

Horizontally there is no external force, so the momentum of boy, wagon and unthrown bricks together is conserved at each throw. The total mass starts at $M_0=36+9+3(4.5)=58.5$ kg. Before a throw the whole mass $M$ moves at $v$; after it, the remaining mass $M-m_b$ moves at $v+\Delta v$ and the brick moves backwards. The answer depends on which wagon velocity the 3 m/s is measured against.

On the reading that reproduces the printed answers, the brick leaves at 3 m/s relative to the wagon's velocity just before the throw, so its absolute velocity is $v-v_b'$:

$$
\begin{aligned}
Mv&=(M-m_b)(v+\Delta v)+m_b(v-v_b')\\
Mv&=Mv+(M-m_b)\,\Delta v-m_bv_b'\\
\Delta v&=\frac{m_bv_b'}{M-m_b}
\end{aligned}
$$

Each throw adds $m_bv_b'=13.5$ kg m/s divided by the mass left behind. One at a time, the masses left are 54, 49.5 and 45 kg:

$$
\begin{aligned}
v&=\frac{13.5}{54}+\frac{13.5}{49.5}+\frac{13.5}{45}\\
&=0.250+0.273+0.300\\
&=0.823\ \mathrm{m/s}
\end{aligned}
$$

All at once, the single throw has $m_b\to3m_b=13.5$ kg and leaves 45 kg:

$$
\begin{aligned}
v&=\frac{13.5\times3}{45}\\
&=0.900\ \mathrm{m/s}
\end{aligned}
$$

$$
\boxed{\text{(a) }0.823\ \mathrm{m/s},\qquad\text{(b) }0.900\ \mathrm{m/s}\qquad\text{(velocity relative to the wagon before the throw)}}
$$

> [!warning] Two readings of "relative to the wagon"
> The more usual reading, and the one used for rocket exhaust, measures the 3 m/s relative to the wagon after release, so the brick's absolute velocity is $(v+\Delta v)-v_b'$. Momentum then gives $Mv=(M-m_b)(v+\Delta v)+m_b(v+\Delta v-v_b')$, so $\Delta v=m_bv_b'/M$, divided by the mass before the throw. One at a time this gives $13.5/58.5+13.5/54+13.5/49.5=0.231+0.250+0.273=0.753$ m/s; all at once it gives $40.5/58.5=0.692$ m/s. On this reading throwing one at a time wins, which is the reason rockets burn propellant continuously and use stages; on the printed reading the order is reversed. The printed 0.823 and 0.9 m/s are reproduced only by the before-throw reading.

![[d_t4_q6_boy_and_bricks.png|660]]

The figure shows the printed (before-throw) reading.

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#2. Conservation of linear momentum]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Systems of particles]]

## Q7 - Billiard balls in an elastic oblique impact

Cue ball A moves at 2 m/s along $+y$ and strikes ball B (equal mass, at rest), knocking it straight into the corner pocket along the line at 45° up and to the left. Energy and momentum are conserved. Find both velocities after the impact.

This is an oblique impact, which is outside the assessed scope, but it follows from the same two ideas as a central impact. The balls are smooth, so the contact impulse acts along the line of impact, the line through the two centres at contact. B starts at rest and receives only that impulse, so B must move off along the line of impact; since it goes straight into the pocket, the line of impact is the 45° line. Take unit vectors along and across it:

$$
\mathbf n=\frac{-\mathbf i+\mathbf j}{\sqrt2},\qquad\mathbf t=\frac{\mathbf i+\mathbf j}{\sqrt2}
$$

A's velocity before the impact has components

$$
\begin{aligned}
v_{A1,n}&=2\mathbf j\cdot\mathbf n=\sqrt2\ \mathrm{m/s}\\
v_{A1,t}&=2\mathbf j\cdot\mathbf t=\sqrt2\ \mathrm{m/s}
\end{aligned}
$$

Across the line of impact there is no impulse, so each ball keeps its own $t$ component: $v_{A2,t}=\sqrt2$ and $v_{B2,t}=0$. Along it, momentum of the pair is conserved, and an elastic impact has $e=1$:

$$
\begin{aligned}
m\sqrt2+0&=mv_{A2,n}+mv_{B2,n}\\
v_{B2,n}-v_{A2,n}&=1\times(\sqrt2-0)
\end{aligned}
$$

Adding the two equations gives $v_{B2,n}=\sqrt2$ and then $v_{A2,n}=0$: along the line of impact the equal balls swap velocities, as in Newton's cradle. Converting back,

$$
\begin{aligned}
\mathbf v_{A2}&=\sqrt2\,\mathbf t=\mathbf i+\mathbf j\\
\mathbf v_{B2}&=\sqrt2\,\mathbf n=-\mathbf i+\mathbf j
\end{aligned}
$$

$$
\boxed{\mathbf v_{A2}=(\mathbf i+\mathbf j)\ \mathrm{m/s},\qquad\mathbf v_{B2}=(-\mathbf i+\mathbf j)\ \mathrm{m/s}}
$$

matching the printed answers. As a check, the total momentum after is $m(0,\ 2)$, as before, and the kinetic energy is $\tfrac12m(2+2)=\tfrac12m(4)$, as before. The two velocities are perpendicular ($\mathbf v_{A2}\cdot\mathbf v_{B2}=0$), the general result for an elastic glancing impact between equal masses with one initially at rest.

![[d_t4_q7_billiards.png|540]]

Theory: [[FEEG1002 D4 - Linear Impulse and Momentum#3. Oblique impact]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Coefficient of restitution]]

---

## Links

- Topic note: [[FEEG1002 D4 - Linear Impulse and Momentum]] · energy steps from [[FEEG1002 D3 - Work, Energy and Power]]
- Concepts: [[Principle of Linear Impulse and Momentum]] · [[Coefficient of Restitution]] · [[Work-Energy Principle]]
- Hub: [[FEEG1002 Mechanics, Materials and Structures Hub]]

## Sources

- `Tutorial Sheet 04 - Linear Impulse and Momentum.pdf` (Dynamics Problem sheet 4): Q1–Q7 with printed final answers, no worked solutions.
- Q1 was set as a lecture quiz: `FEEG1002 Lecture 2025-02-20 - Dynamics 08 - 20 February 2025 at 11 56 36.txt`, ll. 371–394, and `...Dynamics 08b - 20 February 2025 at 13 53 10.txt`, ll. 330–398.
- Q2 is pointed to as the half-sine version of the lecture's trapezium-pulse example: `FEEG1002 Lecture 2025-02-19 - Dynamics 07 - 19 February 2025 at 10 50 43.txt`, ll. 247–249.
