---
title: "FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, work-energy, springs, power, pendulum]
sheet: "Dynamics Problem sheet 3 (work, energy, power)"
theory_notes: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
key_concepts: ["[[Work-Energy Principle]]", "[[Conservative Forces and Potential Energy]]", "[[Power and Efficiency]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 03 - Work, Energy and Power.pdf"]
---

# FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions

> [!abstract] Sheet summary
> Eleven problems on the work-energy principle and power: free fall on the Moon, springs (bungee, hammer, inclined slider), cords and pulleys, friction doing work, an elliptical loop, two pendulum problems and the power needed by a car and a lift. The sheet prints final answers for every question except Q8. All of them are reproduced here, re-derived and checked in Python; the only differences are last-digit rounding in Q5(b) and Q10(a).

Take $g=9.81$ m/s² except on the Moon. The principle in the course's form is

$$
KE_1+V_{g1}+V_{e1}+\sum U_{1-2}=KE_2+V_{g2}+V_{e2}
$$

with $\sum U_{1-2}$ holding only the work of non-conservative forces, and each force counted once.

## Q1 - Lunar lander engine cut-off height

The lander survives an impact at up to $v_2=5$ m/s. Find the height $h$ at which the engine can be shut off for an initial vertical velocity of (a) 0, (b) 2 m/s down, (c) 2 m/s up, with $g=1.62$ m/s².

After cut-off only the weight acts, so energy is conserved. Datum at the surface:

$$
\begin{aligned}
\tfrac12mv_1^2+mgh&=\tfrac12mv_2^2\\
h&=\frac{v_2^2-v_1^2}{2g}
\end{aligned}
$$

Kinetic energy depends on $v_1^2$, so the direction of the initial velocity does not matter: a lander rising at 2 m/s returns through the cut-off height at 2 m/s downwards.

$$
\begin{aligned}
\text{(a)}\quad h&=\frac{25-0}{3.24}=7.72\ \text{m}\\
\text{(b), (c)}\quad h&=\frac{25-4}{3.24}=6.48\ \text{m}
\end{aligned}
$$

**Answers:** (a) 7.7 m; (b) 6.5 m; (c) 6.5 m. All match the printed answers.

Theory: [[FEEG1002 D3 - Work, Energy and Power#Conservation of energy]]

## Q2 - Bungee jumper from a 40 m bridge

A 60 kg jumper falls from a bridge 40 m above a river on a cord of unstretched length $l_0=15$ m and stiffness $k=150$ N/m. Find the lowest point and the largest cord force.

Let $x$ be the cord stretch at the lowest point, where the jumper is momentarily at rest after falling $l_0+x$. Energy from rest on the bridge to rest at the bottom, datum at the bottom:

$$
\begin{aligned}
mg(l_0+x)&=\tfrac12kx^2\\
75x^2-588.6x-8829&=0\\
x&=\frac{588.6+\sqrt{588.6^2+4(75)(8829)}}{150}=\frac{588.6+1730.6}{150}=15.46\ \text{m}
\end{aligned}
$$

taking the positive root.

**(a)** The jumper has fallen $15+15.46=30.46$ m, so he is

$$
40-30.46=9.54\ \text{m above the water}
$$

**(b)** The cord force is largest at the largest stretch:

$$
F_{e,max}=kx=150(15.46)=2319\ \text{N}
$$

which is $3.94mg$.

**Answers:** (a) 9.54 m; (b) 2319 N. Both match the printed answers (the sheet gives 2319.3 N; the unrounded value is 2319.25 N).

Theory: [[FEEG1002 D3 - Work, Energy and Power#Work of a spring]]

## Q3 - Spring-assisted hammer

A 40 kg hammer is released from rest at position 1 and driven down $b=0.4$ m to position 2 by its weight and two springs ($k=1500$ N/m, $l_0=0.2$ m). Each spring is anchored to the frame a horizontal distance $a=0.3$ m from its attachment on the hammer, level with position 2.

The spring lengths and stretches are

$$
\begin{aligned}
L_1&=\sqrt{0.3^2+0.4^2}=0.5\ \text{m},&\delta_1&=0.5-0.2=0.3\ \text{m}\\
L_2&=0.3\ \text{m},&\delta_2&=0.3-0.2=0.1\ \text{m}
\end{aligned}
$$

Energy from 1 to 2, datum at position 2, with both springs:

$$
\begin{aligned}
mgb+2\cdot\tfrac12k\delta_1^2&=\tfrac12mv_2^2+2\cdot\tfrac12k\delta_2^2\\
40(9.81)(0.4)+1500(0.09-0.01)&=20v_2^2\\
156.96+120.0&=20v_2^2\\
v_2&=3.72\ \text{m/s}
\end{aligned}
$$

The springs give back 120 J of the energy stored in them, almost as much as the 157 J from the fall.

**Answer:** $v_2=3.72$ m/s downwards, matching the printed answer.

Theory: [[FEEG1002 D3 - Work, Energy and Power#Work of a spring]]

## Q4 - Two blocks joined by a pulley cord

Blocks A and B (50 kg each) sit on a smooth floor. A force $F=500$ N pulls A to the left. The cord is tied to B, runs left round a pulley on A, right round a pulley on B, and left again to a fixed post. Find both velocities after A has moved 3 m. Positions $s_A$ and $s_B$ are measured left and right of the post.

**Kinematics.** The three straight runs have lengths $s_A+s_B$, $s_A+s_B$ and $s_B$, so

$$
\begin{aligned}
2s_A+3s_B&=\text{const}\\
2v_A+3v_B&=0\\
v_B&=-\tfrac23v_A
\end{aligned}
$$

As A moves left, B also moves left (towards the post) at two-thirds of A's speed, and travels 2 m while A travels 3 m.

**Energy.** The cord is inextensible and the pulleys ideal, so the tensions do no net work on the system. Only $F$ does work. From rest:

$$
\begin{aligned}
F\,\Delta s_A&=\tfrac12mv_A^2+\tfrac12m\left(\tfrac23v_A\right)^2\\
500(3)&=\tfrac12(50)v_A^2\left(1+\tfrac49\right)\\
v_A^2&=\frac{1500(9)}{25(13)}=41.54\\
v_A&=6.45\ \text{m/s},\qquad v_B=4.30\ \text{m/s}
\end{aligned}
$$

Newton's law gives the same: A feels $F-2T=ma_A$, B feels $3T=ma_B$ with $a_B=\tfrac23a_A$, so $a_A=6.92$ m/s², $T=76.9$ N and $v_A=\sqrt{2(6.92)(3)}=6.45$ m/s.

**Answers:** $v_{Ax}=6.45$ m/s, $v_{Bx}=4.30$ m/s, both in the $x$ direction (left). Both match the printed answers.

Theory: [[FEEG1002 D3 - Work, Energy and Power#Systems of particles]]

## Q5 - Work of friction on a crate on a truck

A truck starts from rest and reaches 72 km/h = 20 m/s in 75 m with constant acceleration, carrying an 80 kg crate. Find the work done by friction on the crate over this interval for (a) $\mu_s=0.30$, $\mu_k=0.28$; (b) $\mu_s=0.25$, $\mu_k=0.20$.

The truck's acceleration and the time taken are

$$
\begin{aligned}
a&=\frac{v^2}{2s}=\frac{400}{150}=2.667\ \text{m/s}^2\\
t&=\frac{v}{a}=7.5\ \text{s}
\end{aligned}
$$

The crate can follow the truck only if static friction can supply $ma$, i.e. if $a\le\mu_sg$.

**(a)** $\mu_sg=2.94$ m/s² $>2.667$ m/s², so the crate does not slip. The friction force is $ma=80(2.667)=213$ N forwards, and its point of application moves with the truck through 75 m:

$$
U=213.3(75)=16\,000\ \text{J}
$$

which equals the crate's final kinetic energy $\tfrac12(80)(20^2)$. Static friction does positive work here because the contact point moves.

**(b)** $\mu_sg=2.45$ m/s² $<2.667$ m/s², so the crate slips from the start. Kinetic friction then drives it forwards:

$$
\begin{aligned}
F_k&=\mu_kmg=0.2(80)(9.81)=157.0\ \text{N}\\
a_c&=\mu_kg=1.962\ \text{m/s}^2
\end{aligned}
$$

Over the truck's 7.5 s the crate moves

$$
s_c=\tfrac12(1.962)(7.5^2)=55.2\ \text{m}
$$

so

$$
U=157.0(55.2)=8661\ \text{J}
$$

which equals the crate's kinetic energy at 7.5 s, $\tfrac12(80)(14.7^2)$. The crate has slid 19.8 m back along the bed by then.

> [!warning] Which interval
> The printed 8660 J takes the interval as the 7.5 s in which the truck accelerates. If the truck then cruised at 20 m/s and the question meant the whole time until the crate stops slipping (10.2 s), friction would do $\tfrac12(80)(20^2)=16\,000$ J in case (b) as well.

**Answers:** (a) 16 000 J; (b) 8661 J. Both match the printed answers (8660 J).

Theory: [[FEEG1002 D3 - Work, Energy and Power#Work of friction]]

## Q6 - Slider pulled up a guide by a cord over a pulley

The 10 kg slider moves without friction up a guide inclined at 30°. A spring ($k=60$ N/m) is already stretched 0.6 m at A, where the slider is released from rest. A cord from the slider runs over the small pulley B and carries a constant force $F=250$ N. B is $b=0.9$ m from the guide, on the perpendicular through C, and C is $s=1.2$ m up the guide from A. Find $v_C$.

**Work of $F$.** The cord tension is 250 N throughout, so the work done on the slider is $F$ times the shortening of the cord between B and the slider:

$$
\begin{aligned}
L_{BA}&=\sqrt{1.2^2+0.9^2}=1.5\ \text{m},\qquad L_{BC}=0.9\ \text{m}\\
U_F&=250(1.5-0.9)=150\ \text{J}
\end{aligned}
$$

**Spring.** The stretch grows from 0.6 m to 1.8 m as the slider moves 1.2 m up:

$$
V_{e2}-V_{e1}=\tfrac12(60)(1.8^2-0.6^2)=86.4\ \text{J}
$$

**Gravity.** The slider rises $1.2\sin30°=0.6$ m:

$$
V_{g2}-V_{g1}=10(9.81)(0.6)=58.9\ \text{J}
$$

**Energy.**

$$
\begin{aligned}
0+U_F&=\tfrac12mv_C^2+\Delta V_e+\Delta V_g\\
150&=5v_C^2+86.4+58.9\\
v_C^2&=\frac{4.74}{5}=0.948\\
v_C&=0.974\ \text{m/s}
\end{aligned}
$$

The answer is the small difference of large terms, so a rounding slip in any of them changes it badly. Using $F$ times the slider's 1.2 m displacement in place of the change in cord length is the usual error.

**Answer:** $v_C=0.974$ m/s, matching the printed answer.

Theory: [[FEEG1002 D3 - Work, Energy and Power#Definition]] and [[FEEG1002 D3 - Work, Energy and Power#With potential energy]]

## Q7 - Roller coaster on an elliptical loop

The 200 kg cart enters the loop $x^2/R_1^2+y^2/R_2^2=1$ ($R_1=3$ m, $R_2=4$ m) at A, passes the top B, leaves at C, and is then braked by $F_B=cs^2$ with $c=55$ kg/(m s²), $s$ measured from C. Friction is neglected.

**Radius of curvature at B.** Near the top, $y=R_2\sqrt{1-x^2/R_1^2}$. Expanding for small $x$:

$$
\begin{aligned}
y&\approx R_2\left(1-\frac{x^2}{2R_1^2}\right)\\
\frac{dy}{dx}&=-\frac{R_2x}{R_1^2}=0\ \text{at}\ x=0\\
\frac{d^2y}{dx^2}&=-\frac{R_2}{R_1^2}\\
\rho_B&=\frac{(1+0)^{3/2}}{R_2/R_1^2}=\frac{R_1^2}{R_2}=\frac94=2.25\ \text{m}
\end{aligned}
$$

**Speed at B.** At the top both the weight and the track's normal force $N=0.2mg$ point down, towards the centre of curvature:

$$
\begin{aligned}
N+mg&=\frac{mv_B^2}{\rho_B}\\
1.2mg&=\frac{mv_B^2}{\rho_B}\\
v_B&=\sqrt{1.2(9.81)(2.25)}=5.15\ \text{m/s}
\end{aligned}
$$

**Speed at A.** The normal force does no work, so energy is conserved between A and B, which is $2R_2=8$ m higher:

$$
\begin{aligned}
\tfrac12mv_A^2&=\tfrac12mv_B^2+mg(2R_2)\\
v_A^2&=26.49+2(9.81)(8)=183.4\\
v_A&=13.54\ \text{m/s}
\end{aligned}
$$

**Speed at C.** A and C are at the same height, so $v_C=v_A=13.54$ m/s.

**Braking distance.** The brake force opposes the motion, so its work over $s_{CD}$ is

$$
U_{C-D}=-\int_0^{s_{CD}}cs^2\,ds=-\frac{c\,s_{CD}^3}{3}
$$

Work-energy from C to rest at D:

$$
\begin{aligned}
\tfrac12mv_C^2-\frac{c\,s_{CD}^3}{3}&=0\\
s_{CD}&=\left(\frac{3mv_C^2}{2c}\right)^{1/3}=\left(\frac{3(200)(183.4)}{2(55)}\right)^{1/3}=(1000.6)^{1/3}=10.0\ \text{m}
\end{aligned}
$$

**Answers:** $v_B=5.15$ m/s; $v_A=13.54$ m/s; $v_C=13.54$ m/s; $s_{CD}=10.0$ m. All match the printed answers.

![[d_t3_q7_elliptical_loop.png|860]]

Theory: [[FEEG1002 D3 - Work, Energy and Power#Minimum speed for a loop]] and [[FEEG1002 D2 - Curvilinear Motion#Radius of curvature]]

## Q8 - Pendulum released from rest

A point mass $m$ on a light cord of length $L$ is released from rest at $\theta_0<0$, with $\theta$ measured from the downward vertical. Find the speed, and the work done by the tension for an increment $\Delta\theta$. No answer is printed.

**Speed.** The mass is $L\cos\theta$ below the pivot O. The tension does no work (shown below), so energy is conserved. Datum at O:

$$
\begin{aligned}
0-mgL\cos\theta_0&=\tfrac12mv^2-mgL\cos\theta\\
v^2&=2gL(\cos\theta-\cos\theta_0)\\
v&=\sqrt{2gL(\cos\theta-\cos\theta_0)}
\end{aligned}
$$

valid for $|\theta|\le|\theta_0|$. The speed is greatest at the bottom, $\sqrt{2gL(1-\cos\theta_0)}$, and the pendulum swings to $-\theta_0$ on the other side.

**Work of the tension.** The mass moves on a circle, so its displacement $d\mathbf r=L\,d\theta\,\mathbf u_t$ is always tangential, while the tension acts along the cord, along $\mathbf u_n$:

$$
\begin{aligned}
dU_T&=\mathbf T\cdot d\mathbf r=T\,\mathbf u_n\cdot L\,d\theta\,\mathbf u_t=0\\
U_T&=0\ \text{for any}\ \Delta\theta
\end{aligned}
$$

**Answers:** $v=\sqrt{2gL(\cos\theta-\cos\theta_0)}$; the tension does no work.

Theory: [[FEEG1002 D3 - Work, Energy and Power#Pendulum speed from energy]]

## Q9 - Pendulum given a speed at the bottom

The same pendulum is given a speed $v_0$ at $\theta=0$.

**(a) Diagrams.** The free-body diagram has the tension $T$ along the cord towards O and the weight $mg$ down. The kinetic diagram has $mv^2/L$ towards O and $ma_t$ along the tangent.

**(b) Speed.** Energy from $\theta=0$, where the mass is $L(1-\cos\theta)$ lower:

$$
\begin{aligned}
\tfrac12mv_0^2&=\tfrac12mv^2+mgL(1-\cos\theta)\\
v&=\sqrt{v_0^2-2gL(1-\cos\theta)}
\end{aligned}
$$

**Tension.** Along $n$, towards O, the weight has the component $-mg\cos\theta$:

$$
\begin{aligned}
T-mg\cos\theta&=\frac{mv^2}{L}\\
T&=\frac{m}{L}\left[v_0^2-2gL(1-\cos\theta)\right]+mg\cos\theta\\
T&=\frac{mv_0^2}{L}-2mg+3mg\cos\theta
\end{aligned}
$$

**(c) Full revolution.** $T$ is smallest at the top, $\theta=180°$, and a cord cannot push, so we need $T\ge0$ there:

$$
\begin{aligned}
\frac{mv_0^2}{L}-5mg&\ge0\\
v_{0,min}&=\sqrt{5gL}
\end{aligned}
$$

**(d) Acceleration at the bottom.** At $\theta=0$ the tangential component $a_t=-g\sin\theta$ is zero, so

$$
a=a_n=\frac{v_{0,min}^2}{L}=5g
$$

directed up towards O.

**(e) Where the cord goes slack.** Set $T=0$:

$$
\begin{aligned}
\frac{mv_0^2}{L}-2mg+3mg\cos\theta_L&=0\\
\cos\theta_L&=\frac23-\frac{v_0^2}{3gL}\\
\theta_L&=\cos^{-1}\!\left(\frac23-\frac{v_0^2}{3gL}\right)
\end{aligned}
$$

This root is a real slack point only if the mass still has speed there. Substituting $\cos\theta_L$ into (b):

$$
v_L^2=v_0^2-2gL+2gL\left(\frac23-\frac{v_0^2}{3gL}\right)=\frac{v_0^2-2gL}{3}
$$

so the cord goes slack only for $\sqrt{2gL}<v_0<\sqrt{5gL}$, at an angle between 90° and 180° (above the horizontal through O). For $v_0\le\sqrt{2gL}$ the mass stops and swings back with the cord taut; for $v_0\ge\sqrt{5gL}$ it loops. With $v_0^2=3gL$, for example, $\cos\theta_L=-\tfrac13$ and $\theta_L=109.5°$.

**Answers:** (b) $v=\sqrt{v_0^2-2gL(1-\cos\theta)}$; (c) $v_{0,min}=\sqrt{5gL}$; (d) $a=5g$; (e) $\theta_L=\cos^{-1}(2/3-v_0^2/3gL)$. All match the printed answers.

![[d_t3_q9_pendulum_regimes.png|700]]

Theory: [[FEEG1002 D3 - Work, Energy and Power#Pendulum speed from energy]] and [[FEEG1002 D2 - Curvilinear Motion#Simple pendulum]]

## Q10 - Power for an accelerating car

A 1500 kg car accelerates uniformly from 50 to 80 km/h (13.89 to 22.22 m/s) over 400 m on the level, against rolling resistance equal to 2% of its weight.

The acceleration, from $v^2=u^2+2as$:

$$
a=\frac{22.22^2-13.89^2}{2(400)}=\frac{493.8-192.9}{800}=0.376\ \text{m/s}^2
$$

The driving force must overcome rolling resistance and accelerate the car:

$$
\begin{aligned}
F&=ma+0.02mg\\
F&=1500(0.376)+0.02(1500)(9.81)=564.2+294.3=858.5\ \text{N}
\end{aligned}
$$

**(a)** $F$ is constant, so $P=Fv$ is greatest at the highest speed:

$$
P_{max}=858.5(22.22)=19.08\ \text{kW}
$$

**(b)** At a steady 80 km/h only the rolling resistance remains:

$$
P=294.3(22.22)=6.54\ \text{kW}
$$

**Answers:** (a) 19.08 kW; (b) 6.54 kW. The sheet prints 19.07 kW for (a); the unrounded value is 19.079 kW, so the printed figure is truncated rather than different.

![[d_t3_q10_car_power.png|660]]

Theory: [[FEEG1002 D3 - Work, Energy and Power#4. Power and efficiency]]

## Q11 - Counterbalanced lift

Masses C and D (300 kg each) hang in the pulley system of the figure. Rope 1 runs from the ceiling, down round a movable pulley carrying C, up over a fixed pulley and down to D. Rope 2 runs from D up over a second fixed pulley and down to the motor, through point P. D moves up at $v_D=5$ m/s.

**Kinematics.** With depths measured down from the ceiling, rope 1 gives $2s_C+s_D=\text{const}$, so C moves down at half D's rate: $v_C=2.5$ m/s and $a_C=\tfrac12a_D$. Rope 2 passes over a fixed pulley, so the motor reels it in at $v_P=v_D$.

**(a) Constant speed.** Both masses are in equilibrium. Let $T_1$ and $T_2$ be the tensions in ropes 1 and 2:

$$
\begin{aligned}
\text{C:}\quad 2T_1&=mg\ \Rightarrow\ T_1=\frac{300(9.81)}{2}=1471.5\ \text{N}\\
\text{D:}\quad T_1+T_2&=mg\ \Rightarrow\ T_2=1471.5\ \text{N}\\
P&=T_2v_P=1471.5(5)=7.36\ \text{kW}
\end{aligned}
$$

This is also the rate of increase of potential energy: D gains $mg(5)$ per second while C loses $mg(2.5)$.

**(b) D accelerating upwards at 0.75 m/s².** Now C accelerates down at 0.375 m/s²:

$$
\begin{aligned}
\text{C:}\quad mg-2T_1&=m(0.375)\ \Rightarrow\ T_1=\frac{300(9.81-0.375)}{2}=1415.3\ \text{N}\\
\text{D:}\quad T_1+T_2-mg&=m(0.75)\ \Rightarrow\ T_2=300(10.56)-1415.3=1752.8\ \text{N}\\
P&=T_2v_P=1752.8(5)=8.76\ \text{kW}
\end{aligned}
$$

The extra 1.41 kW is the rate of increase of the system's kinetic energy, $m a_Dv_D+m a_Cv_C=1125+281$ W.

**Answers:** (a) 7.36 kW; (b) 8.76 kW. Both match the printed answers.

Theory: [[FEEG1002 D3 - Work, Energy and Power#4. Power and efficiency]] and [[FEEG1002 D3 - Work, Energy and Power#Motor hoisting a block through a pulley]]

## Links

- Topic note: [[FEEG1002 D3 - Work, Energy and Power]]
- Concepts: [[Work-Energy Principle]] · [[Conservative Forces and Potential Energy]] · [[Power and Efficiency]] · [[Dependent Motion and Pulley Constraints]] · [[Normal and Tangential Coordinates]]
- Module: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous sheet: [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]

## Sources

- `Tutorial Sheet 03 - Work, Energy and Power.pdf` (Dynamics Problem sheet 3), Q1–Q11; final answers printed for all but Q8. Geometry for Q3, Q4, Q6, Q7 and Q11 read from the sheet's figures.
- The energy derivation of Q8 is the pendulum worked in L12, `FEEG1002 Lecture 2025-03-06.txt`, ll. 349–380; the loop condition behind Q9(c) is the loop example of L06, `FEEG1002 Lecture 2025-02-13.txt`, ll. 102–188.
