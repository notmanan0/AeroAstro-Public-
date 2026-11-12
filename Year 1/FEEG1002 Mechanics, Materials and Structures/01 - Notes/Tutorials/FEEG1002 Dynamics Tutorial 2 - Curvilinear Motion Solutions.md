---
title: "FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, projectiles, normal-tangential, banked-curve, relative-motion]
sheet: "Dynamics Problem sheet 2 (curvilinear motion)"
theory_notes: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
key_concepts: ["[[Projectile Motion]]", "[[Normal and Tangential Coordinates]]", "[[Coulomb Friction]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 02 - Curvilinear Motion.pdf"]
---

# FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions

> [!abstract] Sheet summary
> Eleven problems on curved-path motion: a projectile (Q1), circular kinematics (Q2–Q3), the normal and tangential components of a given acceleration (Q4), $n$–$t$ kinetics on banked curves, a rotor ride, a swing and a collar on a curved rod (Q5–Q8), and relative motion (Q9–Q11). The sheet prints no answers. All geometry was read from the sheet's figures, and every value was re-derived and checked in Python.

Take $g=9.81$ m/s² unless the question gives another value. In the $n$–$t$ problems $\mathbf u_t$ points along the velocity and $\mathbf u_n$ towards the centre of curvature, so $a_t=\dot v$ and $a_n=v^2/\rho$.

## Q1 - Projectile from the top of a wall

The projectile leaves A with $v_A=150$ m/s along a 3-4-5 slope (rise 3, run 4) and lands at B, 150 m below A. Axes: $x$ horizontal and $y$ up, origin at A.

The launch components are

$$
\begin{aligned}
v_{x}&=150\cdot\tfrac45=120\ \text{m/s}\\
v_{y0}&=150\cdot\tfrac35=90\ \text{m/s}
\end{aligned}
$$

With no drag, $a_x=0$ and $a_y=-g$, so

$$
x=120t,\qquad y=90t-\tfrac12gt^2
$$

**Time of flight.** B is at $y=-150$ m:

$$
\begin{aligned}
-150&=90t-4.905t^2\\
4.905t^2-90t-150&=0\\
t_{AB}&=\frac{90+\sqrt{90^2+4(4.905)(150)}}{2(4.905)}=\frac{90+105.1}{9.81}=19.89\ \text{s}
\end{aligned}
$$

taking the positive root.

**Range.**

$$
R=120(19.89)=2386\ \text{m}
$$

**Trajectory.** Eliminate $t=x/120$:

$$
\begin{aligned}
y&=90\frac{x}{120}-\frac g2\left(\frac{x}{120}\right)^2\\
y&=0.75x-3.41\times10^{-4}x^2\ \ \text{(m)}
\end{aligned}
$$

a parabola, with $0.75=\tan$ of the launch angle.

**Maximum height.** At the top $v_y=0$:

$$
\begin{aligned}
t_{top}&=\frac{90}{9.81}=9.17\ \text{s}\\
h&=\frac{v_{y0}^2}{2g}=\frac{8100}{19.62}=413\ \text{m above A}
\end{aligned}
$$

which is 563 m above the ground at B.

**Answers:** $t_{AB}=19.9$ s; $R=2386$ m; $y=0.75x-3.41\times10^{-4}x^2$; maximum height 413 m above A (563 m above the ground).

![[d_t2_q1_projectile.png|860]]

Theory: [[FEEG1002 D2 - Curvilinear Motion#Trajectory]] and [[FEEG1002 D2 - Curvilinear Motion#Time of flight and range]]

## Q2 - Particle on a circle at 20 rpm

A particle moves on a horizontal circle of radius $r=0.5$ m at a steady $n=20$ rpm.

**Angular velocity.**

$$
\dot\theta=20\cdot\frac{2\pi}{60}=2.094\ \text{rad/s}
$$

**In $n$–$t$ coordinates.** Position is given by the path coordinate $s=r\theta=0.5(2.094)t=1.047t$ m, measured from wherever $\theta=0$. The velocity is tangential:

$$
\mathbf v=r\dot\theta\,\mathbf u_t=1.047\,\mathbf u_t\ \text{m/s}
$$

The speed is constant, so $a_t=\dot v=0$, and the acceleration is entirely normal, towards the centre:

$$
\mathbf a=r\dot\theta^2\,\mathbf u_n=0.5(2.094)^2\,\mathbf u_n=2.19\,\mathbf u_n\ \text{m/s}^2
$$

**In Cartesian coordinates.** With the origin at the centre and $\theta=\dot\theta t$:

$$
\mathbf r=r\cos\theta\,\mathbf i+r\sin\theta\,\mathbf j
$$

Differentiating, with $\dot\theta$ constant:

$$
\begin{aligned}
\mathbf v&=-r\dot\theta\sin\theta\,\mathbf i+r\dot\theta\cos\theta\,\mathbf j\\
\mathbf a&=-r\dot\theta^2\cos\theta\,\mathbf i-r\dot\theta^2\sin\theta\,\mathbf j=-\dot\theta^2\mathbf r
\end{aligned}
$$

The magnitudes are $|\mathbf r|=0.5$ m, $|\mathbf v|=r\dot\theta=1.047$ m/s and $|\mathbf a|=r\dot\theta^2=2.19$ m/s², the same as in $n$–$t$; the acceleration points from the particle to the centre. Numerically, $\mathbf r=0.5(\cos2.094t,\ \sin2.094t)$ m, $\mathbf v=1.047(-\sin2.094t,\ \cos2.094t)$ m/s and $\mathbf a=2.19(-\cos2.094t,\ -\sin2.094t)$ m/s². One revolution takes 3.0 s.

**Answers:** $\dot\theta=2.09$ rad/s; $v=1.05$ m/s tangential; $a=a_n=2.19$ m/s² towards the centre.

Theory: [[FEEG1002 D2 - Curvilinear Motion#Circular paths]]

## Q3 - Piecewise angular acceleration

A particle on a horizontal circle of radius $r=0.5$ m starts from rest at $t=0$ with $\ddot\theta=6t$ rad/s² for $0<t\le1$ s and $\ddot\theta=6$ rad/s² for $1<t\le2$ s.

**First second.** Integrate twice from rest:

$$
\begin{aligned}
\dot\theta&=\int_0^t6t\,dt=3t^2\\
\theta&=\int_0^t3t^2\,dt=t^3
\end{aligned}
$$

so at $t=1$ s, $\dot\theta=3$ rad/s and $\theta=1$ rad.

**Second second.** With constant $\ddot\theta=6$ rad/s², starting from those values:

$$
\begin{aligned}
\dot\theta&=3+6(t-1)\\
\theta&=1+3(t-1)+3(t-1)^2
\end{aligned}
$$

At $t=2$ s:

$$
\begin{aligned}
\dot\theta(2)&=3+6=9\ \text{rad/s}\\
\theta(2)&=1+3+3=7\ \text{rad}
\end{aligned}
$$

The particle never reverses, so the distance travelled is the arc length:

$$
s=r\theta=0.5(7)=3.5\ \text{m}
$$

**Answers:** $\dot\theta(2)=9$ rad/s (speed 4.5 m/s); distance 3.5 m.

Theory: [[FEEG1002 D2 - Curvilinear Motion#Circular paths]] and [[FEEG1002 D2 - Curvilinear Motion#Particle accelerating on a circle]]

## Q4 - Rocket on a curved trajectory

The thrust gives a horizontal acceleration of 3 m/s², gravity gives 9.3 m/s² downwards, and the velocity is $v=10\times10^3$ km/h $=2778$ m/s, tangent to the path at 30° below the horizontal. The centre of curvature C lies below and behind the rocket.

With $x$ forward and $y$ up, the unit vectors are

$$
\mathbf u_t=(\cos30°,\ -\sin30°),\qquad \mathbf u_n=(-\sin30°,\ -\cos30°)
$$

and the total acceleration is $\mathbf a=(3,\ -9.3)$ m/s².

**(i) Components.** Project $\mathbf a$ onto each direction:

$$
\begin{aligned}
a_t&=\mathbf a\cdot\mathbf u_t=3\cos30°+9.3\sin30°=2.598+4.650=7.25\ \text{m/s}^2\\
a_n&=\mathbf a\cdot\mathbf u_n=-3\sin30°+9.3\cos30°=-1.500+8.054=6.55\ \text{m/s}^2
\end{aligned}
$$

$$
\mathbf a=7.25\,\mathbf u_t+6.55\,\mathbf u_n\ \text{m/s}^2
$$

with magnitude $\sqrt{7.25^2+6.55^2}=9.77$ m/s², the same as $\sqrt{3^2+9.3^2}$.

**(ii) Radius of curvature.**

$$
\rho=\frac{v^2}{a_n}=\frac{2778^2}{6.554}=1.177\times10^6\ \text{m}=1177\ \text{km}
$$

**(iii) Rate of increase of speed.** $\dot v=a_t=7.25$ m/s².

**(iv) Angular velocity of the radial line.** The line GC turns at the rate the velocity direction turns:

$$
\dot\beta=\frac v\rho=\frac{a_n}{v}=\frac{6.554}{2778}=2.36\times10^{-3}\ \text{rad/s}
$$

**Answers:** $\mathbf a=7.25\mathbf u_t+6.55\mathbf u_n$ m/s²; $\rho=1177$ km; $\dot v=7.25$ m/s²; $\dot\beta=2.36\times10^{-3}$ rad/s.

Theory: [[FEEG1002 D2 - Curvilinear Motion#Acceleration]]

## Q5 - Banked curve

A car of mass 1200 kg drives at constant speed and constant height round a curve of radius $\rho=120$ m banked at $\theta=18°$, with $\mu_s=0.8$.

**(i) Diagrams.** The curve is horizontal, so the normal axis $n$ is horizontal towards the centre, the binormal $b$ is vertical and $t$ points out of the page. The free-body diagram has the weight $mg$ down, the normal force $N$ perpendicular to the bank and the lateral friction $F$ along the bank (taken positive down the slope). The kinetic diagram is $mv^2/\rho$ along $n$ only, since $a_t=0$ and there is no vertical acceleration.

**(ii) No-friction speed.** With $F=0$:

$$
\begin{aligned}
n:\quad N\sin\theta&=\frac{mv_0^2}{\rho}\\
b:\quad N\cos\theta&=mg
\end{aligned}
$$

Dividing the first by the second:

$$
\begin{aligned}
\tan\theta&=\frac{v_0^2}{\rho g}\\
v_0&=\sqrt{\rho g\tan\theta}=\sqrt{120(9.81)(0.3249)}=19.6\ \text{m/s}\ (70.4\ \text{km/h})
\end{aligned}
$$

**(iii) Friction at other speeds.** With friction included:

$$
\begin{aligned}
n:\quad N\sin\theta+F\cos\theta&=\frac{mv^2}{\rho}\\
b:\quad N\cos\theta-F\sin\theta&=mg
\end{aligned}
$$

Multiply $n$ by $\cos\theta$ and $b$ by $\sin\theta$ and subtract, then multiply $n$ by $\sin\theta$ and $b$ by $\cos\theta$ and add:

$$
\begin{aligned}
F&=m\left(\frac{v^2}{\rho}\cos\theta-g\sin\theta\right)\\
N&=m\left(\frac{v^2}{\rho}\sin\theta+g\cos\theta\right)
\end{aligned}
$$

| Speed | $v^2/\rho$ (m/s²) | $F$ (N) | $N$ (N) | $\lvert F\rvert/N$ | Slides? |
|---|---|---|---|---|---|
| $1.2v_0=23.5$ m/s | 4.59 | +1601 (down the bank) | 12 898 | 0.124 | no, $<0.8$ |
| $0.9v_0=17.6$ m/s | 2.58 | −691 (up the bank) | 12 153 | 0.057 | no, $<0.8$ |

**(iv)** At $1.2v_0$ the car tends to slide outwards and up the bank, so friction points down the bank; at $0.9v_0$ it tends to slide inwards and down, so friction points up the bank. In both diagrams the friction arrow lies along the bank surface.

**(v) Maximum speed.** At impending slip outwards, $F=\mu_sN$:

$$
\begin{aligned}
\frac{v^2}{\rho}\cos\theta-g\sin\theta&=\mu_s\left(\frac{v^2}{\rho}\sin\theta+g\cos\theta\right)\\
\frac{v^2}{\rho}(\cos\theta-\mu_s\sin\theta)&=g(\sin\theta+\mu_s\cos\theta)\\
v_{max}&=\sqrt{\rho g\frac{\sin\theta+\mu_s\cos\theta}{\cos\theta-\mu_s\sin\theta}}=\sqrt{1177\cdot\frac{1.0699}{0.7039}}=42.3\ \text{m/s}
\end{aligned}
$$

There is no lower limit, because $\tan18°=0.325<\mu_s$: the car could even stand still on the bank.

**Answers:** $v_0=19.6$ m/s; $F=+1601$ N at $1.2v_0$ and $-691$ N at $0.9v_0$, neither slipping; $v_{max}=42.3$ m/s (152 km/h).

![[d_t2_q5_banked_curve.png|720]]

Theory: [[FEEG1002 D2 - Curvilinear Motion#The third axis]] and [[FEEG1002 D2 - Curvilinear Motion#5. Equations of motion in n-t coordinates]]

## Q6 - Rotor ride

A vertical cylinder of radius $r=12$ m spins at a constant rate $\omega$; a rider stands against the wall with $\mu_s=0.3$, and the floor is lowered.

**(i) Free-body diagram.** The weight $mg$ acts down, static friction $F$ acts up along the wall, and the wall's normal force $N$ acts horizontally towards the axis. The kinetic diagram is $m\omega^2r$ towards the axis; there is no vertical or tangential acceleration.

**(ii) Speeds that hold the rider.** The normal force is the only horizontal force, so it supplies the centripetal acceleration, and friction holds the weight:

$$
\begin{aligned}
n:\quad N&=m\omega^2r\\
b:\quad F&=mg
\end{aligned}
$$

The rider stays put if the friction needed does not exceed the limit:

$$
\begin{aligned}
mg&\le\mu_sm\omega^2r\\
\omega&\ge\sqrt{\frac{g}{\mu_sr}}=\sqrt{\frac{9.81}{0.3(12)}}=1.65\ \text{rad/s}
\end{aligned}
$$

which is 15.8 rpm, a wall speed of 19.8 m/s. The mass cancels, so the same speed works for every rider.

**Answer:** any $\omega\ge1.65$ rad/s (15.8 rpm).

Theory: [[FEEG1002 D2 - Curvilinear Motion#5. Equations of motion in n-t coordinates]]

## Q7 - Boy on a swing arm

The 75 kg boy at B is 10 m from the pivot C on an arm at $\theta=45°$ above the horizontal. He moves at 6 m/s, up and to the left, with the speed increasing at 0.5 m/s². Find the horizontal and vertical components of the seat force on him.

The kinematics in $n$–$t$ are

$$
a_t=\dot v=0.5\ \text{m/s}^2,\qquad a_n=\frac{v^2}{L}=\frac{36}{10}=3.6\ \text{m/s}^2
$$

with $\mathbf u_n$ from B towards C, $(-\cos45°,\ -\sin45°)$, and $\mathbf u_t$ along the motion, $(-\sin45°,\ \cos45°)$. The forces are the weight and the seat force with components $R_n$ and $R_t$. The weight has a component $mg\sin45°$ towards C (C is below B) and $mg\cos45°$ against the motion:

$$
\begin{aligned}
n:\quad R_n+mg\sin45°&=m\frac{v^2}{L}\\
R_n&=75(3.6)-75(9.81)(0.7071)=270-520=-250\ \text{N}\\
t:\quad R_t-mg\cos45°&=m\dot v\\
R_t&=75(0.5)+520=558\ \text{N}
\end{aligned}
$$

The negative $R_n$ means the seat pushes the boy away from C: the inward component of his weight is more than the centripetal force needed. Converting to $x$ (right) and $y$ (up):

$$
\begin{aligned}
R_x&=-R_n\cos45°-R_t\sin45°=0.7071(250-558)=-217\ \text{N}\\
R_y&=-R_n\sin45°+R_t\cos45°=0.7071(250+558)=571\ \text{N}
\end{aligned}
$$

As a check, $\mathbf R+m\mathbf g=m\mathbf a$ with $m\mathbf a=75[0.5\mathbf u_t+3.6\mathbf u_n]=(-217,\ -164)$ N gives $R_y=-164+736=571$ N.

**Answers:** horizontal 217 N towards C's side (to the left), vertical 571 N upwards.

Theory: [[FEEG1002 D2 - Curvilinear Motion#5. Equations of motion in n-t coordinates]]

## Q8 - Collar on a curved rod with a spring

The 2.5 kg collar slides on the smooth rod $y=2.4-\tfrac53x^2$ (m). At A, $x=0.6$ m, it moves at 3 m/s down the rod (towards increasing $x$). The spring ($k=150$ N/m, unstretched length 0.9 m) runs from the anchor O at the origin to the collar. Find the normal force and the acceleration.

**Geometry at A.**

$$
\begin{aligned}
y_A&=2.4-\tfrac53(0.36)=1.8\ \text{m}\\
\frac{dy}{dx}&=-\tfrac{10}3x=-2\quad(63.4°\text{ below the horizontal})\\
\frac{d^2y}{dx^2}&=-\tfrac{10}3
\end{aligned}
$$

The radius of curvature:

$$
\rho=\frac{\left[1+(dy/dx)^2\right]^{3/2}}{\left|d^2y/dx^2\right|}=\frac{5^{3/2}}{10/3}=3.354\ \text{m}
$$

**Spring force.** Its length is $\sqrt{0.6^2+1.8^2}=1.897$ m, so the stretch is 0.997 m and

$$
F_s=150(0.997)=149.6\ \text{N}
$$

directed from A towards O, along $(-0.316,\ -0.949)$.

**Unit vectors.** Along the motion $\mathbf u_t=(1,\ -2)/\sqrt5$. The rod is concave downwards, so the centre of curvature is below and to the left: $\mathbf u_n=(-2,\ -1)/\sqrt5$. The rod's normal force $N$ acts along $\mathbf u_n$ (a negative value means it points the other way).

**Equations of motion.** The components of the weight $(0,\ -24.5)$ N and the spring force $(-47.3,\ -141.9)$ N are

$$
\begin{aligned}
W_t&=\frac{(-24.5)(-2)}{\sqrt5}=21.9\ \text{N},&W_n&=\frac{(-24.5)(-1)}{\sqrt5}=11.0\ \text{N}\\
F_{s,t}&=\frac{-47.3+283.9}{\sqrt5}=105.8\ \text{N},&F_{s,n}&=\frac{94.6+141.9}{\sqrt5}=105.8\ \text{N}
\end{aligned}
$$

Along the tangent:

$$
\begin{aligned}
21.9+105.8&=2.5a_t\\
a_t&=51.1\ \text{m/s}^2
\end{aligned}
$$

Along the normal, with $a_n=v^2/\rho=9/3.354=2.68$ m/s²:

$$
\begin{aligned}
11.0+105.8+N&=2.5(2.68)\\
N&=6.71-116.8=-110\ \text{N}
\end{aligned}
$$

The rod pushes the collar away from the centre of curvature with 110 N: the spring and weight pull it inwards far harder than the small centripetal force requires. The acceleration magnitude is

$$
a=\sqrt{51.1^2+2.68^2}=51.2\ \text{m/s}^2
$$

dominated by the spring's pull along the rod.

**Answers:** $N=110$ N, acting on the collar away from the centre of curvature (along $(2,1)/\sqrt5$); $a_t=51.1$ m/s², $a_n=2.68$ m/s², $|\mathbf a|=51.2$ m/s².

![[d_t2_q8_collar.png|620]]

Theory: [[FEEG1002 D2 - Curvilinear Motion#Radius of curvature]] and [[FEEG1002 D2 - Curvilinear Motion#Car over a parabolic hill]]

## Q9 - Mine car hoisted by its own motor

The 100 kg mine car C on a 30° incline carries the motor M, which reels in the cable with relative acceleration $a_{P/C}=1.2$ m/s². The cable runs from M up to a fixed pulley at the top, back down round a pulley on the car, and up to a fixed anchor, so three strands run between the car and the top. Find $a_C$ and the cable tension $T$.

**Acceleration.** Measure $s_C$ and $s_P$ down the incline from the fixed top. The cable from P round the car pulley to the anchor has length

$$
s_P+2s_C=\text{const}
$$

so, differentiating twice,

$$
a_P=-2a_C
$$

Relative acceleration links P to the car:

$$
\begin{aligned}
a_P&=a_C+a_{P/C}\\
-2a_C&=a_C+1.2\\
a_C&=-0.4\ \text{m/s}^2
\end{aligned}
$$

The car accelerates at 0.4 m/s² up the incline while P accelerates at 0.8 m/s² down it.

**Tension.** Three strands pull the car up the incline (one at the motor, two at the car's pulley). With rolling resistance neglected, along the incline (up positive):

$$
\begin{aligned}
3T-mg\sin30°&=ma_C\\
T&=\frac{100(0.4)+100(9.81)(0.5)}{3}=\frac{40+490.5}{3}=177\ \text{N}
\end{aligned}
$$

> [!warning] Incline angle
> The sheet's figure labels the angle 30° against a vertical reference line at the foot of the incline, so it may be measured from the vertical rather than the horizontal. Taking the incline at 30° to the horizontal, as above, gives $T=177$ N; at 60° to the horizontal, $T=(40+849.6)/3=297$ N. The acceleration, 0.4 m/s² up the incline, does not depend on the angle.

**Answers:** $a_C=0.4$ m/s² up the incline; $T=177$ N (on the 30° incline of the sheet).

Theory: [[FEEG1002 D2 - Curvilinear Motion#Mine car hoisted by its own motor]] and [[FEEG1002 D1 - Linear Motion of Particles#6. Dependent motion and pulleys]]

## Q10 - Aircraft seen from another aircraft

Aircraft A flies east at 800 km/h. Aircraft B flies north-east (45°) but appears to the passengers in A to move away at 60° to the horizontal, up and to the left (120° from east).

**(i)–(iii) Frames and vector relations.** Attach translating (non-rotating) axes $x$–$y$ to A, parallel to the fixed $X$ (east) and $Y$ (north). Then

$$
\mathbf r_B=\mathbf r_A+\mathbf r_{B/A},\qquad \mathbf v_B=\mathbf v_A+\mathbf v_{B/A}
$$

with $\mathbf r_A$ and $\mathbf r_B$ drawn from the fixed origin and $\mathbf r_{B/A}$ from A to B.

**(iv) Speed of B.** Let $u=|\mathbf v_{B/A}|$. Writing the velocity equation in components:

$$
\begin{aligned}
X:\quad v_B\cos45°&=800-u\cos60°\\
Y:\quad v_B\sin45°&=u\sin60°
\end{aligned}
$$

Since $\cos45°=\sin45°$, the left sides are equal:

$$
\begin{aligned}
800-0.5u&=0.866u\\
u&=\frac{800}{1.366}=586\ \text{km/h}\\
v_B&=\frac{586(0.866)}{0.7071}=717\ \text{km/h}
\end{aligned}
$$

The sine rule on the velocity triangle (angles 45°, 60° and 75°) gives the same: $v_B=800\sin60°/\sin75°=717$ km/h.

**Answer:** $v_B=717$ km/h towards the north-east (45°); B's apparent speed relative to A is 586 km/h.

Theory: [[FEEG1002 D2 - Curvilinear Motion#6. Relative motion of two particles]]

## Q11 - Car rounding a bend seen from an accelerating car

Car A travels at 72 km/h = 20 m/s and accelerates at 1.2 m/s² along its direction of motion. Car B rounds a 150 m radius curve at a constant 54 km/h = 15 m/s; in the figure B is on the curve with its radius at 30° below the horizontal through the curve's centre, heading away from the junction. Use the sheet's axes: $x$ along A's motion and $y$ perpendicular to it, both fixed to the translating observer in A.

**Velocities.** B moves along the tangent, which is at 30° to $y$:

$$
\begin{aligned}
\mathbf v_A&=(20,\ 0)\ \text{m/s}\\
\mathbf v_B&=15(\sin30°,\ -\cos30°)=(7.5,\ -12.99)\ \text{m/s}
\end{aligned}
$$

**Accelerations.** B's speed is constant, so it has only the centripetal part, directed towards the centre of the curve:

$$
\begin{aligned}
a_{B}&=\frac{v_B^2}{\rho}=\frac{225}{150}=1.5\ \text{m/s}^2\\
\mathbf a_B&=1.5(\cos30°,\ \sin30°)=(1.30,\ 0.75)\ \text{m/s}^2\\
\mathbf a_A&=(1.2,\ 0)\ \text{m/s}^2
\end{aligned}
$$

**Relative motion.**

$$
\begin{aligned}
\mathbf v_{B/A}&=\mathbf v_B-\mathbf v_A=(-12.5,\ -12.99)\ \text{m/s}\\
|\mathbf v_{B/A}|&=\sqrt{12.5^2+12.99^2}=18.0\ \text{m/s}
\end{aligned}
$$

at 46.1° to the $-x$ direction, and

$$
\begin{aligned}
\mathbf a_{B/A}&=\mathbf a_B-\mathbf a_A=(0.10,\ 0.75)\ \text{m/s}^2\\
|\mathbf a_{B/A}|&=\sqrt{0.099^2+0.75^2}=0.757\ \text{m/s}^2
\end{aligned}
$$

at 7.5° from $+y$ towards $+x$. A's own acceleration almost cancels the $x$ part of B's centripetal acceleration, so what the observer in A sees is nearly B's sideways acceleration alone.

**Answers:** $\mathbf v_{B/A}=(-12.5,\ -13.0)$ m/s, 18.0 m/s; $\mathbf a_{B/A}=(0.10,\ 0.75)$ m/s², 0.757 m/s².

![[d_t2_relative_velocity.png|880]]

Theory: [[FEEG1002 D2 - Curvilinear Motion#6. Relative motion of two particles]]

## Links

- Topic note: [[FEEG1002 D2 - Curvilinear Motion]]
- Concepts: [[Projectile Motion]] · [[Normal and Tangential Coordinates]] · [[Coulomb Friction]] · [[Dependent Motion and Pulley Constraints]]
- Module: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous sheet: [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]] · Next sheet: [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]]

## Sources

- `Tutorial Sheet 02 - Curvilinear Motion.pdf` (Dynamics Problem sheet 2), Q1–Q11; no answers printed. Geometry for Q1, Q4, Q7–Q11 read from the sheet's figures.
- Q5 (banked curve) was introduced in L04, `FEEG1002 Lecture 2025-02-06.txt`, ll. 17–36, and Q2–Q3 pointed to at l. 92.
- Q9 (mine car) acceleration worked in DAMS2-3, `FEEG1002 Lecture 2021-01-11.txt`, ll. 131–171, with the tension left for the tutorial; the two-vehicle example that follows (ll. 172 onwards) is the set-up of Q11.
