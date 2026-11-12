---
title: "Projectile Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["projectile", "trajectory", "range formula", "time of flight", "ballistic trajectory", "parabolic trajectory"]
tags: [feeg1002, concept, dynamics, curvilinear-motion]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
related_concepts: ["[[Normal and Tangential Coordinates]]", "[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 02 - Curvilinear Motion.pdf"]
---

# Projectile Motion

A projectile is a particle moving under its weight alone; with $x$ horizontal, $y$ vertically up and no air resistance, Newton's law gives $a_x=0$ and $a_y=-g$, so the motion splits into two independent straight-line motions.

$$
x=x_0+v_0\cos\theta_0\,t,\qquad y=y_0+v_0\sin\theta_0\,t-\tfrac12gt^2
$$

Horizontally the velocity stays at $v_0\cos\theta_0$; vertically the constant-acceleration equations apply, including $v_y^2=v_{0y}^2-2g(y-y_0)$. A ball dropped and a ball thrown horizontally from the same height land together, because the horizontal motion does not affect the vertical one. Eliminating $t$ shows that the path is a parabola:

$$
y=y_0+\tan\theta_0\,(x-x_0)-\frac{g}{2v_0^2\cos^2\theta_0}(x-x_0)^2
$$

The time of flight comes from setting $y=y_{end}$, a quadratic in $t$ whose positive root is the answer; the negative root is the time at which the same parabola would have passed $y_{end}$ before launch. Only when the landing height equals the launch height does this reduce to $t_f=2v_0\sin\theta_0/g$ and the range to $v_0^2\sin2\theta_0/g$, greatest at 45°, with angles symmetric about 45° giving equal range. At the highest point $v_y=0$, so the rise is $v_{0y}^2/2g$.

The trap is to use the equal-height forms when the heights differ, as when firing from a cliff or onto a slope. The rest follows from the two position equations and is better derived for each problem.

With drag along the velocity, the two equations become coupled and nonlinear, because drag turns with the velocity while the weight does not, and they must be stepped forward numerically. The projectile then slows faster, rises less and lands sooner: a launch at 60 m/s and 60° has a drag-free range of 318 m, cut to under 100 m by a representative drag. The effect is assessed only qualitatively.

![[d_projectile_range_angle.png|760]]

## Related

- [[FEEG1002 D2 - Curvilinear Motion#3. Projectiles|D2 §3]] · [[FEEG1002 D2 - Curvilinear Motion#Trajectory|trajectory]] · [[FEEG1002 D2 - Curvilinear Motion#Time of flight and range|time of flight and range]] · [[FEEG1002 D2 - Curvilinear Motion#Projectiles with drag|projectiles with drag]] · [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration|constant acceleration]]
- [[Kinematic Relations for Rectilinear Motion]] · [[Normal and Tangential Coordinates]] · [[Newton's Laws of Motion]]
