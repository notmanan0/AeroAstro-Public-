---
title: "FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, kinematics, friction, pulleys, drag, buoyancy]
sheet: "Dynamics Problem sheet 1 (linear motion)"
theory_notes: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
key_concepts: ["[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]", "[[Coulomb Friction]]", "[[Dependent Motion and Pulley Constraints]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 01 - Linear Motion.pdf"]
---

# FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions

> [!abstract] Sheet summary
> Fourteen problems on straight-line motion of particles: differentiating a given $s(t)$, integrating an acceleration that depends on time, position or velocity (springs, drag, inverse-square gravity, buoyancy), friction on inclines, and blocks joined by cords and pulleys. The sheet prints no answers. Every result below was re-derived by hand and checked in Python, including numerical integration of the bungee, drag and buoyancy equations of motion.

Take $g=9.81$ m/s² throughout. Each problem follows the same pattern: choose a positive direction, draw the free-body and kinetic diagrams, write $\sum F=ma$, then pick the integral that matches what $a$ depends on.

## Q1 - Boat position polynomial

The boat's position for $2\le t\le10$ s is $s=4t+1.6t^2-0.08t^3$ (m). We need $v$ and $a$ at $t=4$ s, and the largest velocity in the interval.

Differentiating once and then again:

$$
\begin{aligned}
v&=\frac{ds}{dt}=4+3.2t-0.24t^2\\
a&=\frac{dv}{dt}=3.2-0.48t
\end{aligned}
$$

At $t=4$ s:

$$
\begin{aligned}
v(4)&=4+3.2(4)-0.24(16)=4+12.8-3.84=12.96\ \text{m/s}\\
a(4)&=3.2-0.48(4)=1.28\ \text{m/s}^2
\end{aligned}
$$

The velocity is stationary where $a=0$:

$$
\begin{aligned}
3.2-0.48t&=0\\
t&=6.67\ \text{s}
\end{aligned}
$$

and there

$$
v_{max}=4+3.2(6.667)-0.24(6.667)^2=4+21.33-10.67=14.67\ \text{m/s}
$$

Since $da/dt=-0.48<0$ this is a maximum, and it beats both end values, $v(2)=9.44$ m/s and $v(10)=12.0$ m/s, so it is the largest velocity in the interval.

**Answers:** $v(4)=12.96$ m/s, $a(4)=1.28$ m/s²; $v_{max}=14.7$ m/s at $t=6.67$ s.

![[d_t1_q1_boat_kinematics.png|640]]

Theory: [[FEEG1002 D1 - Linear Motion of Particles#1. Position, velocity and acceleration]]

## Q2 - Rocket with a quartic height law

The rocket starts from rest with $s=bt^2-ct^4$. At $t=10$ s, $v=229$ m/s and $a=28.2$ m/s². Find $v$ and $a$ at $t=5$ s.

Differentiating gives the two laws that carry the unknown constants:

$$
\begin{aligned}
v&=2bt-4ct^3\\
a&=2b-12ct^2
\end{aligned}
$$

Putting $t=10$ s into each gives two linear equations:

$$
\begin{aligned}
20b-4000c&=229\\
2b-1200c&=28.2
\end{aligned}
$$

Multiplying the second by 10 and subtracting it from the first eliminates $b$:

$$
\begin{aligned}
-4000c+12000c&=229-282\\
8000c&=-53\\
c&=-6.625\times10^{-3}\ \text{m/s}^4
\end{aligned}
$$

Back-substituting into the second equation:

$$
\begin{aligned}
2b&=28.2+1200(-6.625\times10^{-3})=28.2-7.95=20.25\\
b&=10.125\ \text{m/s}^2
\end{aligned}
$$

The data make $c$ negative, so the "$-ct^4$" term adds height rather than removing it; the given numbers are what force this. At $t=5$ s:

$$
\begin{aligned}
v(5)&=2(10.125)(5)-4(-6.625\times10^{-3})(125)=101.25+3.31=104.6\ \text{m/s}\\
a(5)&=2(10.125)-12(-6.625\times10^{-3})(25)=20.25+1.99=22.2\ \text{m/s}^2
\end{aligned}
$$

**Answers:** $v(5)=104.6$ m/s, $a(5)=22.2$ m/s².

Theory: [[FEEG1002 D1 - Linear Motion of Particles#1. Position, velocity and acceleration]]

## Q3 - Braking for a traffic light

The car travels at 54 km/h = 15 m/s, the light is 90 m ahead, and the driver reacts for 1 s before braking at a constant rate.

During the reaction time the speed is unchanged, so the car covers $15(1)=15$ m and has 75 m left to stop in. With constant deceleration $a_d$, the constant-acceleration relation $v^2=v_0^2-2a_d\Delta s$ with $v=0$ gives

$$
\begin{aligned}
0&=15^2-2a_d(75)\\
a_d&=\frac{225}{150}=1.5\ \text{m/s}^2
\end{aligned}
$$

The braking time follows from $v=v_0-a_dt_b$:

$$
\begin{aligned}
t_b&=\frac{15}{1.5}=10\ \text{s}\\
t&=1+t_b=11\ \text{s}
\end{aligned}
$$

**Answers:** (i) deceleration 1.5 m/s²; (ii) 11 s to reach the light.

Theory: [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration]]

## Q4 - Police car pursuit

Car A passes police car B at 60 mph while B is at 40 mph. B accelerates uniformly to 65 mph in 5 s and then holds that speed. With 1 mph = 1.61 km/h = 0.4472 m/s,

$$
v_A=26.83\ \text{m/s},\qquad v_{B0}=17.89\ \text{m/s},\qquad v_{B1}=29.07\ \text{m/s}
$$

B's acceleration during the first 5 s is

$$
a_B=\frac{29.07-17.89}{5}=2.236\ \text{m/s}^2
$$

Taking $t=0$ and $s=0$ at the moment A passes B, the distances after 5 s are

$$
\begin{aligned}
s_A(5)&=26.83(5)=134.2\ \text{m}\\
s_B(5)&=17.89(5)+\tfrac12(2.236)(5^2)=89.44+27.95=117.4\ \text{m}
\end{aligned}
$$

A is 16.8 m ahead, and from then on B closes at the constant rate $29.07-26.83=2.236$ m/s, so the extra time is

$$
\Delta t=\frac{16.8}{2.236}=7.5\ \text{s}
$$

The unit conversion cancels out of the time: in mph the gap after 5 s is $(60-52.5)(5)=37.5$ mph·s and the closing speed is 5 mph, giving the same 7.5 s.

**Answer:** B reaches A $12.5$ s after being passed, about 335 m down the road.

Theory: [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration]]

## Q5 - Bungee stiffness design

The jumper ($m=85$ kg) falls from $h=50$ m; the cord goes taut after $\Delta h_1=20$ m and acts as a linear spring of stiffness $k$. Take $x$ positive downwards from the starting point.

**(i) Speed when the cord engages.** For $x<20$ m only the weight acts, so $a=g$. With $v\,dv=a\,dx$ from rest:

$$
\begin{aligned}
\int_0^{v_1}v\,dv&=\int_0^{20}g\,dx\\
\tfrac12v_1^2&=20g\\
v_1&=\sqrt{2(9.81)(20)}=19.8\ \text{m/s}
\end{aligned}
$$

**(ii) Free-body diagrams.** Before the cord engages ($x<20$ m) the only force is the weight $mg$ downwards. Once it stretches ($x>20$ m) there is also the cord force $k(x-20)$ upwards. The kinetic diagram in both cases is $ma$ downwards.

**(iii) Minimum stiffness.** In the stretched phase $\sum F=ma$ downwards gives

$$
a=g-\frac km(x-\Delta h_1)
$$

The jumper just reaches the ground if $v=0$ at $x=h$. Integrating $v\,dv=a\,dx$ from rest at $x=0$ to rest at $x=h$, with $a=g$ for the first $\Delta h_1$:

$$
\begin{aligned}
0&=\int_0^{h}g\,dx-\frac km\int_{\Delta h_1}^{h}(x-\Delta h_1)\,dx\\
0&=gh-\frac{k}{2m}(h-\Delta h_1)^2\\
k_{min}&=\frac{2mgh}{(h-\Delta h_1)^2}
\end{aligned}
$$

Substituting the numbers only now:

$$
k_{min}=\frac{2(85)(9.81)(50)}{30^2}=92.7\ \text{N/m}
$$

Any stiffer cord stops the jumper above the ground.

**(iv) Acceleration against position.** With $k=k_{min}$, $k/m=1.090$ s⁻²:

$$
a=\begin{cases}g=9.81\ \text{m/s}^2, & 0\le x\le20\ \text{m}\\[2pt] 9.81-1.090(x-20), & 20<x\le50\ \text{m}\end{cases}
$$

The acceleration is zero where the cord force equals the weight:

$$
\begin{aligned}
k(x-20)&=mg\\
x&=20+\frac{mg}{k}=20+\frac{833.9}{92.65}=29.0\ \text{m}
\end{aligned}
$$

It is largest in magnitude at the lowest point, where the stretch is greatest:

$$
a(50)=9.81-1.090(30)=-22.9\ \text{m/s}^2
$$

which is $2.33g$ upwards, more than twice the free-fall value.

**(v) Velocity.** Integrating $v\,dv=a\,dx$ through both phases:

$$
v^2=\begin{cases}2gx, & x\le20\ \text{m}\\[2pt] 2gx-\dfrac km(x-20)^2, & x>20\ \text{m}\end{cases}
$$

The speed peaks where $a=0$, not where the cord engages: between 20 m and 29 m the weight still exceeds the cord force, so the jumper keeps speeding up. At $x=29.0$ m,

$$
v_{max}^2=2(9.81)(29.0)-1.090(9.0)^2=569.0-88.3=480.7
$$

$$
v_{max}=21.9\ \text{m/s}
$$

and $v^2=981-1.090(900)=0$ at $x=50$ m, confirming (iii). A numerical integration of the equation of motion gives the same bottom position and peak speed.

**Answers:** $v_1=19.8$ m/s; $k_{min}=2mgh/(h-\Delta h_1)^2=92.7$ N/m; $a=0$ at $x=29.0$ m; $|a|_{max}=22.9$ m/s² at $x=50$ m; $v_{max}=21.9$ m/s at $x=29.0$ m.

![[d_t1_q5_bungee.png|860]]

Theory: [[FEEG1002 D1 - Linear Motion of Particles#2. Choosing the integral]] and [[FEEG1002 D1 - Linear Motion of Particles#Springs]]

## Q6 - Falling with quadratic drag

An object of mass $m$ falls through air with drag $F_D=cv^2$. The axis $y$ points up from the ground. Find $a$, then $v(y)$ for a release from rest at $y_0$.

While falling, $v<0$ and the drag acts upwards, against the motion. The weight acts downwards. Newton's second law along $+y$:

$$
\begin{aligned}
ma&=-mg+cv^2\\
a&=-g+\frac cmv^2
\end{aligned}
$$

The acceleration depends on $v$, and we want $v$ as a function of $y$, so use $a=v\,dv/dy$ and separate the variables:

$$
\begin{aligned}
v\frac{dv}{dy}&=-g+\frac cmv^2\\
\frac{v\,dv}{\frac cmv^2-g}&=dy
\end{aligned}
$$

Integrate from rest at $y_0$ to the state $(y,v)$. The left side is a logarithm, since $d(\frac cmv^2-g)=\frac{2c}{m}v\,dv$:

$$
\begin{aligned}
\frac m{2c}\ln\!\left(\frac{\frac cmv^2-g}{-g}\right)&=y-y_0\\
\ln\!\left(1-\frac{c}{mg}v^2\right)&=-\frac{2c}{m}(y_0-y)\\
1-\frac{c}{mg}v^2&=e^{-2c(y_0-y)/m}
\end{aligned}
$$

$$
\boxed{v^2=\frac{mg}{c}\left(1-e^{-2c(y_0-y)/m}\right)}
$$

with $v=-\sqrt{v^2}$ because the object moves down. As the fall distance $y_0-y$ grows the exponential vanishes and the speed tends to the terminal value $\sqrt{mg/c}$, where drag balances weight and $a=0$.

![[d_drag_terminal_velocity.png|860]]

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Drag and terminal velocity]]

## Q7 - Rocket sled with a water brake

The sled ($m=100$ kg) starts from rest under a thrust $F=3000+200t$ N until $v=400$ m/s, then a water brake applies a drag $F_D=Cv^2$ with $C=0.3$ kg/m until $v=100$ m/s.

**(i)–(ii) Free-body diagrams and accelerations.** In the acceleration phase the horizontal force is the thrust forwards (weight and the track's normal force cancel vertically, and track friction is neglected):

$$
a_1=\frac Fm=30+2t\ \ \text{m/s}^2
$$

In the brake phase the only horizontal force is the drag, backwards:

$$
a_2=-\frac Cmv^2=-0.003v^2\ \ \text{m/s}^2
$$

so the deceleration is 480 m/s² as the brake engages at 400 m/s, falling to 30 m/s² at 100 m/s.

**(iii) Time.** In phase 1, $a$ depends on $t$, so integrate $dv=a\,dt$:

$$
\begin{aligned}
v&=\int_0^t(30+2t)\,dt=30t+t^2\\
400&=30t_1+t_1^2\\
t_1^2+30t_1-400&=0\ \Rightarrow\ (t_1+40)(t_1-10)=0\\
t_1&=10.0\ \text{s}
\end{aligned}
$$

In phase 2, $a$ depends on $v$ and we want time, so use $dt=dv/a$:

$$
\begin{aligned}
\frac{dv}{v^2}&=-0.003\,dt\\
\left[-\frac1v\right]_{400}^{100}&=-0.003t_2\\
-\frac1{100}+\frac1{400}&=-0.003t_2\\
t_2&=\frac{0.0075}{0.003}=2.50\ \text{s}
\end{aligned}
$$

The total time is $t_1+t_2=12.5$ s.

**(iv) Distance.** In phase 1, integrate $v(t)$:

$$
s_1=\int_0^{10}(30t+t^2)\,dt=15(10)^2+\frac{10^3}3=1500+333.3=1833\ \text{m}
$$

In phase 2, use $v\,dv=a\,ds$ to get distance directly:

$$
\begin{aligned}
v\frac{dv}{ds}&=-0.003v^2\\
\frac{dv}{v}&=-0.003\,ds\\
\ln\frac{400}{100}&=0.003s_2\\
s_2&=\frac{\ln4}{0.003}=462\ \text{m}
\end{aligned}
$$

**Answers:** $a_1=30+2t$ m/s², $a_2=-0.003v^2$ m/s²; total time 12.5 s; total distance $1833+462=2295$ m.

![[d_t1_q7_rocket_sled.png|860]]

Theory: [[FEEG1002 D1 - Linear Motion of Particles#2. Choosing the integral]]

## Q8 - Radial fall from geostationary radius

An object falls radially towards Earth. At $r_{geo}=42164$ km its speed is $\sqrt{2\mu/r_{geo}}$, with $\mu=398600$ km³/s². The only force is the attraction $\mu m/r^2$ towards the centre. Find the speed at $r_a=6478$ km and the time taken.

With $r$ measured outwards from the centre, Newton's law gives an acceleration that depends on position:

$$
\begin{aligned}
m\ddot r&=-\frac{\mu m}{r^2}\\
v\frac{dv}{dr}&=-\frac{\mu}{r^2}
\end{aligned}
$$

The mass $m=10^7$ kg cancels. Integrating from $r_{geo}$ to $r$:

$$
\begin{aligned}
\tfrac12v^2-\tfrac12v_{geo}^2&=\frac{\mu}{r}-\frac{\mu}{r_{geo}}\\
\tfrac12v^2-\frac{\mu}{r_{geo}}&=\frac{\mu}{r}-\frac{\mu}{r_{geo}}\\
v^2&=\frac{2\mu}{r}
\end{aligned}
$$

The initial speed is exactly the escape speed at $r_{geo}$, and it stays the local escape speed all the way in. At atmospheric entry:

$$
v_a=\sqrt{\frac{2(398600)}{6478}}=11.09\ \text{km/s}
$$

For the time, the object moves inwards, so $dr/dt=-v$:

$$
\begin{aligned}
dt&=-\frac{dr}{v}=-\sqrt{\frac{r}{2\mu}}\,dr\\
t&=\frac{1}{\sqrt{2\mu}}\int_{r_a}^{r_{geo}}r^{1/2}\,dr\\
t&=\frac{2}{3\sqrt{2\mu}}\left(r_{geo}^{3/2}-r_a^{3/2}\right)
\end{aligned}
$$

With $\sqrt{2\mu}=892.9$ km^(3/2)/s, $r_{geo}^{3/2}=8.658\times10^6$ and $r_a^{3/2}=5.214\times10^5$ (km^(3/2)):

$$
t=\frac{2}{3(892.9)}\left(8.658\times10^6-0.521\times10^6\right)=6075\ \text{s}
$$

**Answers:** $v_a=\sqrt{2\mu/r_a}=11.09$ km/s; $t=6075$ s (1.69 h).

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Gravitational attraction and weight]] and [[FEEG1002 D1 - Linear Motion of Particles#Escape velocity]]

## Q9 - Block sliding down a rough slope

The 50 kg block slides 10 m down a 15° slope from A to B with $\mu_k=0.3$, starting at $v_A=4$ m/s down the slope.

**(i)** Take $x$ down the slope and $y$ perpendicular to it. The free-body diagram has the weight $mg$ vertically down, the normal force $N$ perpendicular to the slope and the kinetic friction $\mu_kN$ up the slope, opposing the sliding. The kinetic diagram is $ma$ along $+x$.

**(ii)** There is no acceleration perpendicular to the slope:

$$
N=mg\cos15°=473.8\ \text{N}
$$

Along the slope:

$$
\begin{aligned}
ma&=mg\sin15°-\mu_kmg\cos15°\\
a&=g(\sin15°-0.3\cos15°)\\
a&=9.81(0.2588-0.2898)=-0.304\ \text{m/s}^2
\end{aligned}
$$

The block decelerates, because $\tan15°=0.268<\mu_k$: friction outweighs the slope component of the weight. With constant $a$:

$$
\begin{aligned}
v_B^2&=v_A^2+2a\,s=16+2(-0.304)(10)=9.93\\
v_B&=3.15\ \text{m/s}
\end{aligned}
$$

**(iii)**

$$
t=\frac{v_B-v_A}{a}=\frac{3.15-4}{-0.304}=2.80\ \text{s}
$$

**Answers:** $\mathbf v_B=3.15$ m/s down the slope; $t_{AB}=2.80$ s.

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Dry friction]]

## Q10 - Block pushed up an incline

A 50 kg block rests on a 15° incline with $\mu_s=0.4$ and $\mu_k=0.3$. A force $F$ pushes it up the slope.

**(i) Without $F$.** Holding the block needs friction up the slope equal to the slope component of the weight, and the most static friction can supply is $\mu_sN$:

$$
\begin{aligned}
mg\sin15°&=126.9\ \text{N}\\
\mu_sN=\mu_smg\cos15°&=0.4(473.8)=189.5\ \text{N}
\end{aligned}
$$

Since $126.9<189.5$ N (equivalently $\tan15°=0.268<\mu_s$), the block stays put. Its free-body diagram has the weight, $N=473.8$ N and 126.9 N of static friction up the slope.

**(ii) With $F$ but no motion.** (a) If $F<mg\sin\theta$, the block still tends to slide down, so friction acts up the slope with magnitude $mg\sin\theta-F$. (b) If $F>mg\sin\theta$, the tendency reverses, and friction acts down the slope with magnitude $F-mg\sin\theta$, up to the limit $\mu_sN$.

**(iii) Impending motion up the slope.** Friction reaches its static limit, acting down the slope:

$$
\begin{aligned}
F_0&=mg\sin15°+\mu_smg\cos15°\\
F_0&=126.9+189.5=316.5\ \text{N}
\end{aligned}
$$

**(iv) Sliding up.** Weight, $N$ and the kinetic friction $\mu_kN$ down the slope, with $ma$ up the slope in the kinetic diagram.

**(v) Speed after 2 s.** With $F=F_0+bt$ the block starts to slide at $t=0$, and friction drops from $\mu_sN$ to $\mu_kN$ at once. Up the slope:

$$
\begin{aligned}
ma&=F_0+bt-mg\sin15°-\mu_kmg\cos15°\\
ma&=(\mu_s-\mu_k)mg\cos15°+bt\\
a&=\frac{0.1(473.8)+60t}{50}=0.948+1.2t\ \ \text{m/s}^2
\end{aligned}
$$

The drop from static to kinetic friction gives an immediate acceleration of 0.948 m/s² at $t=0$. Integrating from rest:

$$
\begin{aligned}
v&=0.948t+0.6t^2\\
v(2)&=1.895+2.40=4.30\ \text{m/s}
\end{aligned}
$$

**(vi)**

$$
\begin{aligned}
s&=0.474t^2+0.2t^3\\
s(2)&=1.895+1.60=3.50\ \text{m}
\end{aligned}
$$

**Answers:** it does not slide under gravity alone; $F_0=316.5$ N; $v(2)=4.30$ m/s; $s(2)=3.50$ m.

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Dry friction]]

## Q11 - Concrete block pulling a log up a ramp

Block A (150 kg) hangs 6 m above the ground at E. Its cable passes over pulley B, runs down the ramp, round pulley C on the log, and back up to B's axle, so two strands pull the log D (250 kg) up the 30° ramp with $\mu_k=0.5$. Both pulleys are massless.

**(i) Free-body diagrams.** A: tension $T$ up, weight $m_Ag$ down. D (with C): $2T$ up the ramp, weight, normal force $N$ and kinetic friction $\mu_kN$ down the ramp. C: one strand wraps it, so it carries $T$ on each side, $2T$ in total, balanced by the link to the log. B: $T$ down to A and $2T$ down the ramp, balanced by the reaction at its centre.

**(ii) Kinematics.** Measure $s_A$ down from B and $s_C$ from B down the ramp to C. The cable length is

$$
s_A+2s_C=\text{const}
$$

Differentiating once and twice:

$$
v_A=-2v_C,\qquad a_A=-2a_C
$$

When A falls, the log moves up the ramp at half A's rate, so in magnitude $a_A=2a_D$.

**(iii) Accelerations and tension.** Take A positive downwards and D positive up the ramp. The log's normal force is $N=m_Dg\cos30°=2124$ N.

$$
\begin{aligned}
\text{A:}\quad m_Ag-T&=m_A(2a_D)\\
\text{D:}\quad 2T-m_Dg(\sin30°+\mu_k\cos30°)&=m_Da_D
\end{aligned}
$$

From A's equation $T=m_A(g-2a_D)$. Substituting into D's:

$$
\begin{aligned}
2m_A(g-2a_D)-m_Dg(\sin30°+\mu_k\cos30°)&=m_Da_D\\
a_D&=\frac{g\left[2m_A-m_D(\sin30°+\mu_k\cos30°)\right]}{4m_A+m_D}\\
a_D&=\frac{9.81\left[300-250(0.933)\right]}{850}=0.770\ \text{m/s}^2
\end{aligned}
$$

Then

$$
\begin{aligned}
a_A&=2a_D=1.54\ \text{m/s}^2\\
T&=150(9.81-1.541)=1240\ \text{N}
\end{aligned}
$$

The sign check passes: $2m_Ag=2943$ N exceeds $m_Dg(\sin30°+\mu_k\cos30°)=2288$ N, so the log really does move up.

**(iv) Speed at E.** A falls 6 m from rest at constant acceleration:

$$
v_A=\sqrt{2(1.541)(6)}=4.30\ \text{m/s}
$$

**(v) Reaction at B.** The three strands pull B with $T$ straight down and $2T$ along the ramp, down and to the left at 30°. The support must balance them:

$$
\begin{aligned}
R_x&=2T\cos30°=2148\ \text{N (away from the ramp)}\\
R_y&=T+2T\sin30°=2T=2481\ \text{N (up)}\\
R_B&=\sqrt{2148^2+2481^2}=3282\ \text{N at }49.1°\text{ above the horizontal}
\end{aligned}
$$

**Answers:** $a_A=2a_D$; $a_D=0.770$ m/s², $a_A=1.54$ m/s², $T=1240$ N; $v_A=4.30$ m/s at E; $R_B=(2148, 2481)$ N, 3282 N.

![[d_t1_q11_log_and_block_fbds.png|880]]

Theory: [[FEEG1002 D1 - Linear Motion of Particles#6. Dependent motion and pulleys]] and [[FEEG1002 D1 - Linear Motion of Particles#Pulley kinetics and mechanical advantage]]

## Q12 - Block on a ledge and hanging movable pulley

Block A (5 kg) slides on a horizontal ledge with $\mu_k=0.2$ and initial speed $v_{A0}=0.6$ m/s towards the edge. Its cord passes over a fixed pulley at the edge, down round a movable pulley carrying B (10 kg), and up to the ceiling. Find $v_A$ after A has moved 1.2 m.

Let $x$ be the length of cord between A and the edge pulley and $y_B$ the depth of B's pulley below it. The cord length is $x+2y_B=\text{const}$, so as A moves towards the edge ($\dot x=-v_A$)

$$
v_B=\tfrac12v_A,\qquad a_B=\tfrac12a_A
$$

and B descends 0.6 m while A moves 1.2 m. With cord tension $T$, A positive towards the edge and B positive downwards:

$$
\begin{aligned}
\text{A:}\quad T-\mu_km_Ag&=m_Aa_A\\
\text{B:}\quad m_Bg-2T&=m_B\tfrac12a_A
\end{aligned}
$$

Substituting $T=m_Aa_A+\mu_km_Ag$ into B's equation:

$$
\begin{aligned}
m_Bg-2\mu_km_Ag&=\left(2m_A+\tfrac12m_B\right)a_A\\
a_A&=\frac{98.1-19.62}{10+5}=5.232\ \text{m/s}^2
\end{aligned}
$$

so $T=5(5.232)+9.81=36.0$ N. The acceleration is constant, so

$$
\begin{aligned}
v_A^2&=0.6^2+2(5.232)(1.2)=12.92\\
v_A&=3.59\ \text{m/s}
\end{aligned}
$$

The work-energy principle for the pair, which you will meet in [[FEEG1002 D3 - Work, Energy and Power]], gives the same 3.59 m/s.

**Answer:** $v_A=3.59$ m/s.

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Pulley kinetics and mechanical advantage]]

## Q13 - Object on an arm guided at 60 degrees

An arm runs in a smooth channel inclined at $\theta=60°$ to the horizontal, and a 90 kg object sits on its horizontal platform with $\mu_s=0.2$. The arm accelerates with magnitude $a$ along the channel.

**(i) The arm.** Its free-body diagram has its weight $m_Ag$, the channel's normal reactions perpendicular to the channel (no friction), the actuating force along the channel, and the object's normal force and friction reversed (down and opposite in direction to the friction on the object). The kinetic diagram is $m_Aa$ along the channel.

**(ii) The object.** If it does not slip it has the arm's acceleration: $a\cos60°$ horizontally and $a\sin60°$ vertically. Its forces are the weight $m_Og$, the normal force $N$ upwards and the static friction $F$, which is the only horizontal force and so must supply all the horizontal acceleration:

$$
F=m_Oa\cos60°
$$

**(iii) Largest downward acceleration.** Accelerating down the channel, the vertical component is downwards:

$$
\begin{aligned}
N-m_Og&=-m_Oa\sin60°\\
N&=m_O(g-a\sin60°)
\end{aligned}
$$

No slip requires $F\le\mu_sN$:

$$
\begin{aligned}
a\cos60°&\le\mu_s(g-a\sin60°)\\
a(\cos60°+\mu_s\sin60°)&\le\mu_sg\\
a_{max,down}&=\frac{\mu_sg}{\cos60°+\mu_s\sin60°}=\frac{1.962}{0.6732}=2.91\ \text{m/s}^2
\end{aligned}
$$

**(iv) Largest upward acceleration.** Now the vertical component is upwards, $N=m_O(g+a\sin60°)$, and

$$
\begin{aligned}
a\cos60°&\le\mu_s(g+a\sin60°)\\
a_{max,up}&=\frac{\mu_sg}{\cos60°-\mu_s\sin60°}=\frac{1.962}{0.3268}=6.00\ \text{m/s}^2
\end{aligned}
$$

**(v) Normal reactions.**

$$
\begin{aligned}
N_{down}&=90(9.81-2.914\sin60°)=656\ \text{N}\\
N_{up}&=90(9.81+6.004\sin60°)=1351\ \text{N}
\end{aligned}
$$

compared with the weight $m_Og=883$ N. Accelerating downwards unloads the contact, so less friction is available exactly when friction is needed, and the downward limit is less than half the upward one. The upward formula would allow any acceleration if $\cos60°\le\mu_s\sin60°$, i.e. $\mu_s\ge\cot60°=0.577$; at $\mu_s=0.2$ that does not apply.

**Answers:** $a_{max}=2.91$ m/s² downwards with $N=656$ N; $a_{max}=6.00$ m/s² upwards with $N=1351$ N.

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Dry friction]] and [[FEEG1002 D1 - Linear Motion of Particles#4. Newton's laws and the equation of motion]]

## Q14 - Floating cylinder released from rest

A vertical cylinder ($D=3$ m, $L=1.2$ m, $\rho_m=500$ kg/m³) floats in water ($\rho_f=1000$ kg/m³). It is held with $l_0=0.7$ m submerged and released from rest. Drag is ignored and $y$ is the upward displacement from the release position.

The cross-section and mass are

$$
\begin{aligned}
A&=\frac{\pi(3)^2}{4}=7.069\ \text{m}^2\\
m&=\rho_mAL=500(7.069)(1.2)=4241\ \text{kg}
\end{aligned}
$$

**(i) Buoyancy.** After rising $y$ the submerged length is $l_0-y$, so

$$
F_B=\rho_fgA(l_0-y)
$$

The free-body diagram has $F_B$ up and $mg$ down; the kinetic diagram is $ma$ up. Newton's law:

$$
\begin{aligned}
ma&=\rho_fgA(l_0-y)-\rho_mALg\\
a&=g\left(\frac{\rho_f(l_0-y)}{\rho_mL}-1\right)\\
a&=g\left(\frac{0.7-y}{0.6}-1\right)=-\frac{g}{0.6}(y-0.1)
\end{aligned}
$$

The equilibrium draught is $\rho_mL/\rho_f=0.6$ m, so at release the body is 0.1 m too deep and starts upwards with $a=1.64$ m/s².

**(ii) Velocity against position.** With $v\,dv=a\,dy$ from rest at $y=0$:

$$
\begin{aligned}
\int_0^vv\,dv&=-\frac{g}{0.6}\int_0^y(y-0.1)\,dy\\
\tfrac12v^2&=-\frac{g}{0.6}\left(\tfrac12y^2-0.1y\right)\\
v^2&=\frac{g}{0.6}\left(0.2y-y^2\right)
\end{aligned}
$$

**(iii) Highest position.** $v=0$ again when $0.2y-y^2=0$, so $y_{max}=0.2$ m.

**(iv) Maximum speed.** At $a=0$, $y=0.1$ m:

$$
v_{max}=\sqrt{\frac{9.81}{0.6}(0.02-0.01)}=0.404\ \text{m/s}
$$

**(v) Type of motion.** The restoring acceleration is proportional to the displacement from $y=0.1$ m, which is simple harmonic motion with

$$
\omega=\sqrt{\frac{g}{0.6}}=4.04\ \text{rad/s},\qquad T=\frac{2\pi}{\omega}=1.55\ \text{s}
$$

The body bobs between $y=0$ and $y=0.2$ m for ever because there is no drag. The submerged length stays between 0.5 and 0.7 m, inside $0<l_0-y<L$, so the linear buoyancy law holds throughout. This is the single-degree-of-freedom oscillator of [[FEEG1002 D6 - Single Degree of Freedom Vibration]] with stiffness $\rho_fgA$.

**Answers:** $F_B=\rho_fgA(0.7-y)$; $v^2=(g/0.6)(0.2y-y^2)$; $y_{max}=0.2$ m; $v_{max}=0.404$ m/s at $y=0.1$ m; simple harmonic motion, period 1.55 s.

![[d_t1_q14_buoyant_cylinder.png|860]]

Theory: [[FEEG1002 D1 - Linear Motion of Particles#Buoyancy]]

## Links

- Topic note: [[FEEG1002 D1 - Linear Motion of Particles]]
- Concepts: [[Kinematic Relations for Rectilinear Motion]] · [[Newton's Laws of Motion]] · [[Coulomb Friction]] · [[Dependent Motion and Pulley Constraints]]
- Module: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Next sheet: [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]

## Sources

- `Tutorial Sheet 01 - Linear Motion.pdf` (Dynamics Problem sheet 1), Q1–Q14; no answers printed. Figures for Q9–Q14 read from the sheet.
- Q5 (bungee stiffness design) was set in L02b, `FEEG1002 Lecture 2025-01-30.txt`, ll. 314–338.
