---
title: "FEEG1002 D7 - Kinematics of Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 7
tags: [feeg1002, dynamics, rigid-body, kinematics, instantaneous-centre, rolling, mechanisms]
aliases: ["Dynamics Lecture 7", "Rigid body kinematics", "Planar motion", "Relative velocity", "Instantaneous centre"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
next_topics: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
key_concepts: ["[[Relative Velocity Equation for Rigid Bodies]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 07 - Kinematics of Rigid Bodies.pdf"]
---

# FEEG1002 D7 - Kinematics of Rigid Bodies

> [!abstract] Summary
> A rigid body in a plane has **three** degrees of freedom: two translations and one rotation. Its motion is one of:
> - **translation** (rectilinear or curvilinear): every point has the same $\mathbf v$ and $\mathbf a$;
> - **rotation about a fixed axis**: $v = \omega r$, $a_t = \alpha r$, $a_n = \omega^2r$;
> - **general plane motion**: translation plus rotation.
>
> Three tools handle general motion:
> - **absolute motion analysis**: write the geometry as $s(\theta)$ and differentiate;
> - **relative velocity**: $\mathbf v_B = \mathbf v_A + \boldsymbol\omega\times\mathbf r_{B/A}$;
> - the **instantaneous centre of rotation (IC)**, the point with zero velocity at that instant, about which the body momentarily rotates.
>
> Rolling without slip ties translation to rotation: $v_G = \omega r$.

## Key Concepts
- [[Relative Velocity Equation for Rigid Bodies]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]]

---

## 1. Types of planar motion (L7.1)
The **crank–slider** shows all three types at once:
- the crank **rotates about a fixed axis**;
- the piston **translates**;
- the connecting rod is in **general plane motion**.

**Translation**: $\mathbf r_B = \mathbf r_A + \mathbf r_{B/A}$ with $\mathbf r_{B/A}$ constant. So $\mathbf v_B = \mathbf v_A$ and $\mathbf a_B = \mathbf a_A$, and the body behaves as a particle.

## 2. Rotation about a fixed axis (L7.1)
- Angular position is $\theta$, with $\omega = \dot\theta$ and $\alpha = \dot\omega = \omega\,d\omega/d\theta$.
- $\boldsymbol\omega$ and $\boldsymbol\alpha$ are vectors along the axis, by the right-hand rule.
- Constant $\alpha$ gives the familiar $\omega = \omega_0 + \alpha t$, $\theta = \theta_0 + \omega_0t + \tfrac12\alpha t^2$ and $\omega^2 = \omega_0^2 + 2\alpha(\theta - \theta_0)$.

For a point P at radius $r$:

$$
\mathbf v = \boldsymbol\omega\times\mathbf r_P,\quad v = \omega r;\qquad \mathbf a = \boldsymbol\alpha\times\mathbf r - \omega^2\mathbf r,\quad a_t = \alpha r,\ a_n = \omega^2r
$$

This is the particle circular-motion result of [[FEEG1002 D2 - Curvilinear Motion]] applied to every point.

> [!example] Gear train (L7): gear A (75 mm) drives gear B (225 mm), which carries pulley D (125 mm) winding up cylinder C
> - Meshing gears share the contact speed and tangential acceleration: $\alpha_Ar_A = \alpha_Br_B$, so $\alpha_B = 4.5(75/225) = 1.5$ rad/s².
> - Pulley D turns with gear B, so $a_C = \alpha_Dr_D = 1.5(0.125) = 0.1875$ m/s².
> - Starting from rest, after 3 s: $v_C = 0.563$ m/s and $s_C = 0.844$ m, both upwards.

## 3. Absolute motion analysis (L7.2)
Write the geometric constraint linking a linear coordinate $s$ and an angle $\theta$, then **differentiate with the chain rule**. For example, $d(\sin\theta)/dt = \omega\cos\theta$ and $d(s^2)/dt = 2s\dot s$.

**Examples**:
- **Rolling disc**: $s_G = r\theta$, so $v_G = r\omega$ and $a_G = r\alpha$ (no slip only).
- **Cam and follower**: $y = r + r\sin\theta$ gives $v_P = r\omega\cos\theta$ and $a_P = -r\omega^2\sin\theta$ at constant $\omega$. Other devices treated this way are the Scotch yoke and the scissor lift.
- **Hydraulic window** (Tutorial 7 Q4): $s^2 = b^2 + l^2 - 2bl\cos\theta$ gives $2s\dot s = 2bl\sin\theta\,\dot\theta$.

![[d_t7_q4_window.png|720]]

## 4. Relative motion: velocity (L7.3)
Take a reference point A with known motion, and a frame $x'y'$ that **translates** with A but does not rotate. Relative to A, point B can only move on a circle, so

$$
\mathbf v_B = \mathbf v_A + \mathbf v_{B/A} = \mathbf v_A + \boldsymbol\omega\times\mathbf r_{B/A},\qquad |\mathbf v_{B/A}| = \omega r_{B/A}\ (\perp\mathbf r_{B/A})
$$

- Choose A and B at points whose **path directions are known**, typically pins and sliders. Then the vector equation's two scalar components solve for two unknowns, e.g. $v_B$ and $\omega$.

**Rolling without slip** ([[Rolling Without Slip]]):
- The contact point A has the ground's velocity, **zero**, so it is the IC.
- The centre moves at $v_B = \omega r$ and the top of the wheel at $2\omega r$.
- Every point's velocity is perpendicular to its line to A, with magnitude $\omega\times$ (distance to A).

![[d_t7_q3_rolling_wheel.png|940]]

## 5. Instantaneous centre of rotation (L7.3)
If the IC is known, $\mathbf v_P = \boldsymbol\omega\times\mathbf r_{P/IC}$: the body momentarily **rotates about the IC**.

**Finding it**: draw perpendiculars to two **non-parallel** known velocity directions; they intersect at the IC. If the two velocities are parallel and the body is translating, the IC is at infinity and $\omega = 0$.

> [!example] Sliding rod (L7): A slides right at 3 m/s on the floor, B slides on the wall, rod 1.5 m at $\theta = 30°$
> - **IC**: $r_{A/IC} = l\sin30° = 0.75$ m and $r_{B/IC} = l\cos30° = 1.30$ m.
> - $\omega = v_A/r_{A/IC}$ = **4 rad/s**, so $v_B = \omega r_{B/IC}$ = **5.2 m/s** (down).
> - The **relative velocity** method agrees: $\mathbf v_B = \mathbf v_A + \boldsymbol\omega\times\mathbf r_{B/A}$ closes as a triangle, with $v_A = \omega r_{B/A}\sin30°$ and $v_B = \omega r_{B/A}\cos30°$.
>
> ![[d_sliding_rod_ic.png|640]]

> [!tip] The IC is a velocity tool only
> The IC generally **accelerates**. Do not use $a = \alpha r_{P/IC}$ for accelerations.

## 6. Relative motion: acceleration (L7.4, brief)
Differentiate the velocity equation:

$$
\mathbf a_B = \mathbf a_A + \boldsymbol\alpha\times\mathbf r_{B/A} - \omega^2\mathbf r_{B/A},\qquad (a_{B/A})_t = \alpha r_{B/A},\ (a_{B/A})_n = \omega^2r_{B/A}
$$

The module rarely needs it. Tutorial 7 Q3(d) uses it: the contact point of a rolling wheel has zero velocity but acceleration $\omega^2R$ **upwards**, 19.7 m/s².

![[d_t7_q5_crank_slider.png|780]]

## Year 2 bridge
- **Rotating frames**: SESA2027 writes the aircraft equations in a **body frame** that rotates at $\boldsymbol\omega = (p, q, r)$. There $\dot{\mathbf v}_{inertial} = \dot{\mathbf v}_{body} + \boldsymbol\omega\times\mathbf v$, generalising this chapter's $\boldsymbol\omega\times\mathbf r$ ([[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]). Attitudes are described by [[Euler Angles and Rotation Matrices]].
- **Rigid-body modes in FE**: the three planar rigid-body motions (two translations, one rotation) are exactly the zero-energy modes that boundary conditions must remove ([[Boundary Conditions and Rigid Body Modes]]).
- **Rotating structures**: a spinning disc has $v = \omega r$ and $a_n = \omega^2r$ at every point, so its body force $\rho\omega^2r$ drives the hoop and radial stresses in [[SESA2028 S11 - Spinning Discs]].
- **Next**: [[FEEG1002 D8 - Kinetics of Rigid Bodies]] adds the forces that cause these motions.

## Links
- Previous: [[FEEG1002 D6 - Single Degree of Freedom Vibration]] · Next: [[FEEG1002 D8 - Kinetics of Rigid Bodies]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]]

## Sources
- Dynamics Lecture 7: 7.1 planar motion, translation and fixed-axis rotation (gear example); 7.2 absolute motion analysis (cam example); 7.3 relative velocity and IC (sliding-rod example); 7.4 relative acceleration (brief)
