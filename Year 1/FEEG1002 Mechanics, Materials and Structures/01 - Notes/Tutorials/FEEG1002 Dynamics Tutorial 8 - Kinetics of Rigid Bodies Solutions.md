---
title: "FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part D: Dynamics"
tags: [feeg1002, tutorial-solutions, dynamics, rigid-body, moment-of-inertia, rolling-with-slip]
sheet: "Dynamics Problem sheet 8 (kinetics of rigid bodies)"
theory_notes: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
key_concepts: ["[[Mass Moment of Inertia and Radius of Gyration]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Rolling Without Slip]]", "[[Parallel Axis Theorem]]"]
status: lectured
date: 2026-11-05
sources: ["02 - Sources/Dynamics/Tutorials/Tutorial Sheet 08 - Kinetics of Rigid Bodies.pdf"]
---

# FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions

> [!abstract] Sheet info
> Five questions on planar rigid-body kinetics: the moment of inertia of a composite body, a torque-driven cam lifting a platform, two bars toppling about their bases, a pair of hoisting drums, and a hoop that slips on an incline. Final answers are printed for every part except Q3(b), which asks for a position but prints only the method; all printed values are reproduced below and Q3(b) is solved in closed form.

## Q1 - Bar welded to a disc

A slender bar ($m_B=4$ kg, $L=0.8$ m) is welded end-on to the rim of a thin disc ($m_D=3$ kg, $R=0.4$ m), with the bar lying in the plane of the disc along a radius produced. Find the position $l_G$ of the combined centre of mass and the moment of inertia $I_G$ about the axis $y$ through it, perpendicular to the bar and the disc.

Theory: [[FEEG1002 D8 - Kinetics of Rigid Bodies#1. Centre of mass]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Parallel-axis theorem]]

Measure positions along the bar from its free end. The bar's own centre is at $L/2=0.4$ m and the disc's centre is a further radius beyond the bar's welded end, at $L+R=1.2$ m. The combined centre of mass is the mass-weighted average:

$$
l_G=\frac{m_B\frac L2+m_D(L+R)}{m_B+m_D}=\frac{4\times0.4+3\times1.2}{7}=\frac{5.2}{7}
$$

$$
\boxed{l_G=0.743\ \mathrm m\ \text{from the free end of the bar}}
$$

Moments of inertia can only be added about a common axis, so each part is moved to the composite G with the parallel-axis theorem. The bar's centre is $d_B=0.743-0.4=0.343$ m from G and the disc's centre is $d_D=1.2-0.743=0.457$ m from it:

$$
I_{G,\text{bar}}=\tfrac1{12}m_BL^2+m_Bd_B^2=\tfrac1{12}\times4\times0.8^2+4\times0.343^2=0.213+0.470=0.684\ \mathrm{kg\,m^2}
$$

$$
I_{G,\text{disc}}=\tfrac12m_DR^2+m_Dd_D^2=\tfrac12\times3\times0.4^2+3\times0.457^2=0.240+0.627=0.867\ \mathrm{kg\,m^2}
$$

$$
I_G=0.684+0.867
$$

$$
\boxed{I_G=1.55\ \mathrm{kg\,m^2}}
$$

The parallel-axis terms (0.470 and 0.627) are larger than the parts' own centroidal values, because each part's mass sits well away from the composite centre. The sheet describes both standard formulas as being "about an axis parallel to $L$"; both are about axes parallel to $y$, perpendicular to the bar and normal to the disc. About an axis along the bar a slender bar has almost no moment of inertia.

## Q2 - Cam driven by a torque lifting a platform

A uniform circular cam ($m_C=4$ kg, $r=0.3$ m) is pinned at O on its rim and turned by a constant torque $T$; it lifts a uniform platform ($m_P=10$ kg) that slides in frictionless vertical columns. $\theta$ is the angle of the line from O to the cam centre G above the horizontal, and $y$ is the height of the platform's underside above O. Find $y$, $\dot y$, $\ddot y$ in terms of $\theta$; draw the free-body and kinetic diagrams; relate $\ddot y$ to $T$ with no friction at the cam; and evaluate $\ddot y$ for $T=50$ N m, $\theta=0$, $\dot\theta=0$.

Theory: [[FEEG1002 D7 - Kinematics of Rigid Bodies#Cam and platform]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rotation about a fixed axis]]

### Kinematics

The platform rests on the top of the cam, a radius $r$ above G, and G is $r\sin\theta$ above O. So

$$
y=r\sin\theta+r
$$

Differentiating with $r$ constant, by the chain rule and then the product rule,

$$
\dot y=r\dot\theta\cos\theta
$$

$$
\boxed{\ddot y=r\ddot\theta\cos\theta-r\dot\theta^2\sin\theta}
$$

### Free-body and kinetic diagrams

The platform carries its weight $m_Pg$ at its centre, the upward contact force $N$ from the cam, a friction force $\mu_kN$ along its underside opposing the sliding of the platform over the cam, and horizontal reactions from the columns (frictionless, so horizontal only), which balance the friction. It translates vertically, so its kinetic diagram is $m_P\ddot y$ upwards.

The cam carries the torque $T$ (clockwise in the figure, which raises G and increases $\theta$), its weight $m_Cg$ at G, the platform's reaction $N$ downwards and the friction $\mu_kN$ at the contact point on top of the cam, and the pin reactions $O_x$, $O_y$. The cam rotates about the fixed pin O, so its kinetic diagram reduces, for moments about O, to the couple $I_O\ddot\theta$, with

$$
I_O=I_G+m_Cr^2=\tfrac12m_Cr^2+m_Cr^2=\tfrac32\times4\times0.3^2=0.54\ \mathrm{kg\,m^2}
$$

The contact point lies vertically above G, so $N$ and the weight both act at horizontal distance $r\cos\theta$ from O; the friction force acts at height $y$ above O and has moment arm $y$.

### Relation between torque and platform acceleration

With no friction, the platform's vertical equation is

$$
N-m_Pg=m_P\ddot y
$$

$$
N=m_P(g+\ddot y)
$$

and the cam's moment equation about O, taking the sense of $T$ (increasing $\theta$) as positive, is

$$
T-m_Cgr\cos\theta-Nr\cos\theta=I_O\ddot\theta
$$

From the kinematics,

$$
\ddot\theta=\frac{\ddot y+r\dot\theta^2\sin\theta}{r\cos\theta}
$$

Substitute $N$ and $\ddot\theta$:

$$
T-m_Cgr\cos\theta-m_P(g+\ddot y)r\cos\theta=\frac{I_O}{r\cos\theta}\left(\ddot y+r\dot\theta^2\sin\theta\right)
$$

$$
T-rg\cos\theta\,(m_P+m_C)-I_O\dot\theta^2\tan\theta=\ddot y\left(\frac{I_O}{r\cos\theta}+m_Pr\cos\theta\right)
$$

$$
\boxed{\ddot y=\frac{T-rg\cos\theta\,(m_P+m_C)-I_O\dot\theta^2\tan\theta}{\dfrac{I_O}{r\cos\theta}+m_Pr\cos\theta}}
$$

which is the printed result with $I_{CO}=I_O$. The denominator is an equivalent mass that includes the cam's rotational inertia seen through the gearing ratio $r\cos\theta$; it blows up at $\theta=90°$, the top of the travel, where turning the cam no longer lifts the platform.

### Initial acceleration

At $\theta=0$ and $\dot\theta=0$, $\cos\theta=1$ and $\tan\theta=0$:

$$
\ddot y=\frac{50-0.3\times9.81\times14}{0.54/0.3+10\times0.3}=\frac{50-41.20}{1.8+3.0}=\frac{8.80}{4.80}
$$

$$
\boxed{\ddot y=1.83\ \mathrm{m/s^2}}
$$

> [!check] Contact is maintained
> The corresponding cam acceleration is $\ddot\theta=\ddot y/r=6.11$ rad/s² and the contact force is $N=10(9.81+1.83)=116$ N. $N>0$, so the platform does stay on the cam, as the single-degree-of-freedom model assumes.

## Q3 - Falling bars with and without a point mass

Two bars of length $l=1.2$ m, density 500 kg/m³ and cross-section $5.76\times10^{-4}$ m² are pivoted at their lower ends A on the ground and released from the same angle $\theta_0$ to the vertical. One is uniform; the other carries a point mass $m_m=0.2$ kg at its upper end. Find $\alpha(\theta)$ in terms of $l_G$ and $k_A$, decide which bar lands first, and find whether a position of the point mass makes the two bars fall together.

Theory: [[FEEG1002 D8 - Kinetics of Rigid Bodies#Falling rods with and without a point mass]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Radius of gyration]]

Each bar has mass

$$
m_b=\rho Al=500\times5.76\times10^{-4}\times1.2=0.3456\ \mathrm{kg}
$$

### Angular acceleration and the faster bar

Each bar rotates about the fixed pivot A, so taking moments about A removes the unknown pivot reaction. With $\theta$ measured from the vertical, the total weight $mg$ acts at G, a horizontal distance $l_G\sin\theta$ from A, and nothing else has a moment about A:

$$
mgl_G\sin\theta=I_A\alpha=mk_A^2\alpha
$$

$$
\boxed{\alpha=\frac{l_G}{k_A^2}\,g\sin\theta}
$$

The mass cancels; the bar's behaviour depends only on the length ratio $l_G/k_A^2$ (units m⁻¹). For the uniform bar, $l_G=l/2$ and $I_A=\tfrac13m_bl^2$, so

$$
\frac{l_G}{k_A^2}=\frac{l/2}{l^2/3}=\frac{3}{2l}=\frac{3}{2.4}=1.25\ \mathrm{m^{-1}}
$$

For the bar with the point mass at its tip, $m=m_b+m_m=0.5456$ kg and

$$
l_G=\frac{m_b\frac l2+m_ml}{m}=\frac{0.3456\times0.6+0.2\times1.2}{0.5456}=0.820\ \mathrm m
$$

$$
I_A=\tfrac13m_bl^2+m_ml^2=0.1659+0.2880=0.4539\ \mathrm{kg\,m^2}
$$

$$
k_A^2=\frac{I_A}{m}=\frac{0.4539}{0.5456}=0.832\ \mathrm{m^2}
$$

$$
\frac{l_G}{k_A^2}=\frac{0.820}{0.832}=0.986\ \mathrm{m^{-1}}
$$

At every angle the uniform bar's $\alpha$ is $1.25/0.986=1.27$ times larger. Both start from rest at $\theta_0$ and obey $\ddot\theta=c\,g\sin\theta$ with a different constant $c$, so the uniform bar is ahead throughout and its fall time is shorter by the factor $\sqrt{0.986/1.25}=0.89$. The uniform bar is the faster one and lands first.

The reason is that a point mass on its own, at distance $d$ from A, would topple like a simple pendulum with $l_G/k_A^2=d/d^2=1/d$. At the tip that is $1/1.2=0.83$ m⁻¹, slower than the bar's 1.25 m⁻¹, so attaching it drags the combination towards the slower value: it adds $m_ml^2$ to the moment of inertia but only $m_mgl$ to the toppling moment.

### Position for equal fall

The two bars fall together if the composite ratio equals the uniform bar's for a point mass at distance $d$ from A:

$$
\frac{m_b\frac l2+m_md}{\tfrac13m_bl^2+m_md^2}=\frac{3}{2l}
$$

$$
2l\left(m_b\frac l2+m_md\right)=3\left(\tfrac13m_bl^2+m_md^2\right)
$$

$$
m_bl^2+2lm_md=m_bl^2+3m_md^2
$$

$$
m_md\,(2l-3d)=0
$$

Apart from the trivial $d=0$ (the mass at the pivot),

$$
\boxed{d=\frac{2l}{3}=0.80\ \mathrm m\ \text{from A}}
$$

The result holds for any size of point mass, because both masses cancel. It matches the pendulum argument: a point mass at $d$ falls on its own with ratio $1/d$, which equals the bar's $3/(2l)$ exactly when $d=2l/3$, the length of the simple pendulum equivalent to the bar. A mass placed below 0.8 m speeds the bar up and one placed above slows it down. The sheet prints only the method for this part, not a number.

![[d_t8_q3_falling_bars.png|700]]

## Q4 - Hoisting drums lifting a block

Two drums fastened together ($r_e=600$ mm, $r_i=300$ mm, combined $m_d=150$ kg, $k_d=450$ mm about their centre O) are turned by a constant rope tension $P=1.8$ kN leaving the outer drum at 45° below the horizontal, towards the power unit. A rope wound on the inner drum lifts a $m_b=300$ kg block. Draw the diagrams, then find the block's acceleration, the tension in its rope and the resultant bearing force at O.

Theory: [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rotation about a fixed axis]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Translation]]

From the sheet's figure, $P$ leaves the top of the outer drum and pulls down and to the right at 45°, tangent to the outer drum, and the block hangs from the left side of the inner drum. $P$ therefore turns the drums clockwise and the block rope resists that; clockwise rotation winds the block rope on and lifts the block. Take clockwise $\alpha$ and upward block acceleration $a$ as positive. The drums' moment of inertia is

$$
I_O=m_dk_d^2=150\times0.45^2=30.375\ \mathrm{kg\,m^2}
$$

### Free-body and kinetic diagrams

The drums carry $P$ at radius $r_e$, the block-rope tension $T$ downwards at radius $r_i$, their weight $m_dg$ at O and the bearing reactions $O_x$, $O_y$ at O. Their centre of mass is at the fixed bearing, so the kinetic diagram is the couple $I_O\alpha$ alone. The block carries $T$ upwards and $m_bg$ downwards; it translates, and its kinetic diagram is $m_ba$ upwards.

![[d_t8_q4_hoist_fbd.png|840]]

### Block acceleration

Moments about O for the drums, the block's vertical equation, and the inextensible rope on the inner drum:

$$
Pr_e-Tr_i=I_O\alpha
$$

$$
T-m_bg=m_ba
$$

$$
a=r_i\alpha
$$

From the block equation $T=m_b(g+a)$; substitute this and $\alpha=a/r_i$ into the drum equation:

$$
Pr_e-m_b(g+a)r_i=\frac{I_O}{r_i}a
$$

$$
a\left(\frac{I_O}{r_i}+m_br_i\right)=Pr_e-m_bgr_i
$$

$$
\boxed{a=\frac{Pr_e-m_bgr_i}{I_O/r_i+m_br_i}}
$$

$$
a=\frac{1800\times0.6-300\times9.81\times0.3}{30.375/0.3+300\times0.3}=\frac{1080-882.9}{101.25+90}=\frac{197.1}{191.25}
$$

$$
\boxed{a=1.03\ \mathrm{m/s^2}\ \text{upwards}}
$$

with $\alpha=a/r_i=3.44$ rad/s² clockwise. The numerator is the net moment if the system were held still, and the denominator is the inertia of drums and block together, referred to the inner-drum radius.

### Rope tension

$$
T=m_b(g+a)=300\times(9.81+1.031)
$$

$$
\boxed{T=3252\ \mathrm N}
$$

### Bearing force

The drums' centre of mass does not move, so the forces on them sum to zero. $P$ has components $P\cos45°=1273$ N to the right and $P\sin45°=1273$ N downwards:

$$
O_x+P\cos45°=0\quad\Rightarrow\quad O_x=-1273\ \mathrm N
$$

$$
O_y-m_dg-T-P\sin45°=0
$$

$$
O_y=1471.5+3252.2+1272.8=5996\ \mathrm N
$$

$$
R_O=\sqrt{1273^2+5996^2}
$$

$$
\boxed{R_O=6130\ \mathrm N\ \text{at }\tan^{-1}(5996/1273)=78.0°\text{ to the horizontal}}
$$

The bearing pushes on the drums up and to the left at 78° above the horizontal; the drums push on the bearing with the equal and opposite force, down and to the right. Note that $O_y$ uses the actual rope tension $T=3252$ N, not the block's weight 2943 N: the block is accelerating.

## Q5 - Hoop released on an incline

A metal hoop of radius $r=150$ mm is released from rest on a 20° incline with $\mu_s=0.15$ and $\mu_k=0.12$. Find its angular acceleration and the time to travel 3 m down the incline.

Theory: [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rolling with and without slip]]

Take $x$ down the slope. The hoop carries its weight, the normal force $N$ and a friction force $F$ up the slope at the contact, and for a thin hoop $I_G=mr^2$. The three equations of motion are

$$
mg\sin\theta-F=ma_G
$$

$$
N-mg\cos\theta=0
$$

$$
Fr=I_G\alpha=mr^2\alpha
$$

These are three equations in four unknowns ($F$, $N$, $a_G$, $\alpha$); the fourth relation depends on whether the hoop slips, which is not known in advance.

### Rolling without slip assumed

Use $a_G=r\alpha$ and no friction law. The moment equation gives $F=mr\alpha=ma_G$, and the force equation becomes

$$
mg\sin\theta-ma_G=ma_G
$$

$$
a_G=\tfrac12g\sin\theta=\tfrac12\times9.81\times\sin20°=1.68\ \mathrm{m/s^2}
$$

The friction needed is $F=\tfrac12mg\sin\theta$, so the check is

$$
\frac{F}{N}=\frac{\tfrac12mg\sin\theta}{mg\cos\theta}=\tfrac12\tan20°=0.182
$$

which exceeds $\mu_s=0.15$. Static friction cannot supply the force rolling would need, so the assumption fails and the hoop slips.

### Rolling with slip

Now friction is kinetic, $F=\mu_kN=\mu_kmg\cos\theta$, and $a_G$ and $\alpha$ are independent. From the force equation,

$$
a_G=g(\sin\theta-\mu_k\cos\theta)=9.81\,(0.3420-0.12\times0.9397)
$$

$$
a_G=2.249\ \mathrm{m/s^2}
$$

and from the moment equation,

$$
\alpha=\frac{Fr}{mr^2}=\frac{\mu_kg\cos\theta}{r}=\frac{0.12\times9.81\times0.9397}{0.15}
$$

$$
\boxed{\alpha=7.37\ \mathrm{rad/s^2}}
$$

> [!check] Slip in the assumed direction
> $r\alpha=1.11$ m/s² is less than $a_G=2.25$ m/s², so the contact point slides down the slope relative to the incline and kinetic friction does act up the slope, as drawn. Both accelerations are constant, so the slip persists.

The centre starts from rest with constant acceleration, so for $s=3$ m

$$
s=\tfrac12a_Gt^2
$$

$$
t=\sqrt{\frac{2s}{a_G}}=\sqrt{\frac{6}{2.249}}
$$

$$
\boxed{t=1.633\ \mathrm s}
$$

A body with less of its mass at the rim needs less friction to roll: the general no-slip requirement is $\mu_s\ge\tan\theta\,k^2/(k^2+r^2)$, which on a 20° slope is 0.121 for a disc and 0.104 for a solid sphere, both below 0.15, while the hoop ($k=r$) needs the most.

![[d_rolling_slip_check.png|880]]

## Links

- Topic note: [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · kinematics from [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Concepts: [[Mass Moment of Inertia and Radius of Gyration]] · [[Parallel Axis Theorem]] · [[Planar Rigid-Body Equations of Motion]] · [[Rolling Without Slip]] · [[Coulomb Friction]]
- Hub: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous sheet: [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]] · Next sheet: [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]

## Sources

- `Tutorial Sheet 08 - Kinetics of Rigid Bodies.pdf` (Q1–Q5, final answers printed on the sheet except a number for Q3(b)).
- Q3 follows the falling-rods demonstration in `FEEG1002 Lecture 2025-03-26.txt` (L17b, ll. 15–78; set as a tutorial problem at ll. 59–60) and is pointed to in `FEEG1002 Lecture 2021-03-14 - DAMS8-RigidBodiesKinetics_2b.txt` (ll. 76–78).
