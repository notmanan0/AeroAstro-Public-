---
title: "FEEG1002 D2 - Curvilinear Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 2
tags: [feeg1002, dynamics, curvilinear-motion, projectiles, normal-tangential, centripetal]
aliases: ["Dynamics Lecture 2", "Projectile motion", "n-t coordinates", "Curvilinear motion of particles"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
next_topics: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
key_concepts: ["[[Projectile Motion]]", "[[Normal and Tangential Coordinates]]", "[[Newton's Laws of Motion]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 02 - Curvilinear Motion.pdf"]
---

# FEEG1002 D2 - Curvilinear Motion

> [!abstract] Summary
> On a curved path, position, velocity and acceleration are **vectors**. The velocity is always **tangent** to the path. The acceleration generally is **not**: even at constant speed there is a **centripetal** component $v^2/\rho$ towards the centre of curvature. Two coordinate systems cover the course.
> - **Cartesian** $x$–$y$: best when the forces have fixed directions, e.g. projectiles, which are just two independent straight-line motions.
> - **Normal–tangential** $n$–$t$: rides on the particle; best when the **path is known**:
>
> $$\mathbf a = \dot v\,\mathbf u_t + \frac{v^2}{\rho}\mathbf u_n,\qquad \sum F_t = m\dot v,\quad \sum F_n = m\frac{v^2}{\rho},\quad \sum F_b = 0$$

## Key Concepts
- [[Projectile Motion]] · [[Normal and Tangential Coordinates]] · [[Newton's Laws of Motion]]

---

## 1. Rectangular coordinates (L2.1)
- Position: $\mathbf r = x\mathbf i + y\mathbf j + z\mathbf k$, with $x(t)$, $y(t)$, $z(t)$.
- Velocity $\mathbf v = \dot{\mathbf r}$ is **tangent to the path**. Acceleration $\mathbf a = \ddot{\mathbf r}$ usually is not.
- The unit vectors $\mathbf i, \mathbf j, \mathbf k$ are fixed, so differentiate component by component.
- Equations of motion: $\sum F_x = ma_x$, $\sum F_y = ma_y$, $\sum F_z = ma_z$, solved simultaneously.

## 2. Projectiles (L2.2)
With no air resistance the only force is weight, so $a_x = 0$ and $a_y = -g$. The motion is **two independent straight-line motions**. The lecture's strobe photo shows a dropped ball and a thrown ball falling side by side.

$$
x = x_0 + v_0\cos\theta_0\,t,\qquad y = y_0 + v_0\sin\theta_0\,t - \tfrac12gt^2,\qquad v_y^2 = v_{0y}^2 - 2g(y - y_0)
$$

Eliminating $t$ gives the **trajectory**, a parabola:

$$
y = y_0 + \tan\theta_0(x - x_0) - \frac{g}{2v_0^2\cos^2\theta_0}(x - x_0)^2
$$

- **Time of flight**: solve $y(t_f) = y_{end}$ and take the positive root. For level ground, $t_f = 2v_0\sin\theta_0/g$.
- **Level-ground range**: $R = \dfrac{v_0^2}{g}\sin2\theta_0$. It is largest at 45°, and complementary angles give the same range.

![[d_projectile_range_angle.png|900]]

> [!example] Tutorial 2 Q1: fired at 150 m/s on a 3-4-5 slope from a 150 m cliff
> - Components: $v_x = 120$ m/s, $v_y = 90$ m/s.
> - Landing: $-150 = 90t - 4.905t^2$ gives $t_{AB} = 19.89$ s and $R = 120t = 2386$ m.
> - Trajectory: $y = 0.75x - 3.41\times10^{-4}x^2$. Apex: $h = 90^2/2g = 413$ m above A.
>
> ![[d_t2_q1_projectile.png|920]]

## 3. Normal–tangential coordinates (L2.3)
When the path is known, put the origin **on the particle**.
- $\mathbf u_t$ is tangent to the path, positive in the direction of motion.
- $\mathbf u_n$ points towards the **centre of curvature** $O'$, which is always on the concave side.
- $\rho$ is the radius of curvature, and $s$ is the arc length from a fixed point on the path.

**Velocity**: $\mathbf v = v\mathbf u_t$ with $v = \dot s$.

**Acceleration**: $\mathbf a = \dot v\mathbf u_t + v\dot{\mathbf u}_t$. The unit tangent turns through $d\theta = ds/\rho$, so $\dot{\mathbf u}_t = (v/\rho)\mathbf u_n$ and

$$
\mathbf a = \underbrace{\dot v}_{a_t:\ \text{speed change}}\mathbf u_t + \underbrace{\frac{v^2}{\rho}}_{a_n:\ \text{direction change}}\mathbf u_n,\qquad a = \sqrt{a_t^2 + a_n^2}
$$

- $a_t = \dot v = v\,dv/ds$ can have either sign.
- $a_n$ is **always inward**.
- Constant speed does **not** mean constant velocity.

![[d_nt_coordinates.png|860]]

**Radius of curvature** of a path $y = f(x)$:

$$
\rho = \frac{\left[1 + (dy/dx)^2\right]^{3/2}}{|d^2y/dx^2|}
$$

**Circular paths**: here $\rho = R$ is constant and $s = R\theta$, so $v = R\dot\theta = R\omega$, $a_t = R\alpha$ and $a_n = R\omega^2$. The constant-$\alpha$ equations $\omega = \omega_0 + \alpha t$ etc. are the rectilinear ones with $s\to\theta$, $v\to\omega$, $a\to\alpha$.

**3D**: add the binormal $\mathbf u_b = \mathbf u_t\times\mathbf u_n$. There is no motion along it, so $\sum F_b = 0$ (e.g. the vertical balance of a car on a banked curve).

> [!warning] "Centrifugal force" does not exist in an inertial frame
> The body accelerates inwards because the net normal force is unbalanced: $\sum F_n = mv^2/\rho$. Also watch the plane of motion.
> - **Horizontal plane** (top view): weight is perpendicular to the plane, so leave $mg$ out.
> - **Vertical plane**: $mg$ has $n$ and $t$ components.

## 4. Solved example: car over a parabolic hill (L2)
An 800 kg car on $y = 20(1 - x^2/6400)$ is at A ($x = 80$ m), travelling at 9 m/s and speeding up at 3 m/s².
- Slope: $dy/dx = -x/160 = -0.5$, so $\theta = 26.6°$.
- Curvature: $d^2y/dx^2 = -1/160$, so $\rho = (1.25)^{3/2}/0.00625 = 223.6$ m.
- $n$: $mg\cos\theta - N = mv^2/\rho$, giving **$N = 6728$ N**.
- $t$: $mg\sin\theta - F = ma_t$, giving **$F = 1114$ N**.

![[d_hill_car_example.png|900]]

The normal force is less than $mg\cos\theta$ because part of the weight provides the centripetal acceleration. Go fast enough over a crest and $N \to 0$: the car leaves the road.

> [!example] Tutorial 2 Q5: banked curve, $\rho = 120$ m, $\theta = 18°$, $\mu_s = 0.8$
> - With no friction needed: $\tan\theta = v_0^2/(\rho g)$, so $v_0 = 19.6$ m/s (70 km/h).
> - At $1.2v_0$ the friction acts **down** the bank: $F = +1.60$ kN. At $0.9v_0$ it acts **up** the bank: $F = -0.69$ kN.
> - Sliding up starts at $v_{max} = 42.3$ m/s (152 km/h).
> - Because $\tan18° < \mu_s$ the car never slides **down**, even when stationary.
>
> ![[d_t2_q5_banked_curve.png|760]]

## 5. Relative motion (tutorial extension)
For two particles, $\mathbf r_B = \mathbf r_A + \mathbf r_{B/A}$, and differentiating gives $\mathbf v_B = \mathbf v_A + \mathbf v_{B/A}$ and $\mathbf a_B = \mathbf a_A + \mathbf a_{B/A}$. This holds for a **translating** (non-rotating) observer. Tutorial 2 Q9–Q11 use it, and it becomes the rigid-body relative velocity equation in [[FEEG1002 D7 - Kinematics of Rigid Bodies]].

![[d_t2_relative_velocity.png|900]]

## Year 2 bridge
- **Flight mechanics in $n$–$t$ form**: a pull-up or banked turn has load factor $n = L/W$ set by $V^2/(g\rho)$. The same $\sum F_n = mv^2/\rho$ appears in the aircraft equations of [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]. The **phugoid** ([[Phugoid Mode]]) is a slow speed-for-height exchange along a curved flight path.
- **Circular orbits**: $GMm/r^2 = mv^2/r$ is this chapter's $\sum F_n$ with gravity. It leads to [[SESA2024 02 - Kepler's Laws and the Orbit Equation]].
- **Rotating structures**: the centripetal loading $\rho\omega^2r$ per unit volume drives the stresses in [[SESA2028 S11 - Spinning Discs]].
- **Rotation matrices and frames**: [[Euler Angles and Rotation Matrices]] generalises the fixed/moving-axis ideas used here.

## Links
- Previous: [[FEEG1002 D1 - Linear Motion of Particles]] · Next: [[FEEG1002 D3 - Work, Energy and Power]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]]

## Sources
- Dynamics Lecture 2: 2.1 rectangular coordinates, 2.2 projectiles, 2.3 $n$–$t$ coordinates, solved example (car over a hill), appendix on the sine and cosine rules
