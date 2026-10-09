---
title: "Projectile Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["projectile", "trajectory", "range formula", "time of flight"]
tags: [feeg1002, concept, dynamics, curvilinear-motion]
status: complete
parent_lectures: ["[[FEEG1002 D2 - Curvilinear Motion]]"]
related_concepts: ["[[Normal and Tangential Coordinates]]", "[[Kinematic Relations for Rectilinear Motion]]", "[[Newton's Laws of Motion]]"]
sources: []
---

# Projectile Motion

## Definition

> [!note] Definition
> With weight as the only force, $a_x = 0$ and $a_y = -g$: two independent straight-line motions.
> $$x = x_0 + v_0\cos\theta_0\,t,\qquad y = y_0 + v_0\sin\theta_0\,t - \tfrac12gt^2$$
> The trajectory is a parabola: $y = y_0 + \tan\theta_0(x - x_0) - \dfrac{g(x - x_0)^2}{2v_0^2\cos^2\theta_0}$.

## Explanation

- **Time of flight**: solve $y(t) = y_{end}$ and take the positive root. On level ground, $t_f = 2v_0\sin\theta_0/g$.
- **Range** on level ground: $R = v_0^2\sin2\theta_0/g$. It is maximum at 45°, and complementary angles give equal range.
- **Apex**: $v_y = 0$, so $h = v_{0y}^2/2g$.
- Equal time steps give equal horizontal spacing: the strobe-photo demonstration.
- Drag breaks the symmetry. The trajectory then needs numerical integration.

## Examples

- **Tutorial 2 Q1**: 150 m/s on a 3-4-5 slope from a 150 m cliff gives $t = 19.89$ s, $R = 2386$ m and $h = 413$ m.

![[d_projectile_range_angle.png|760]]

## Related

- Topic notes: [[FEEG1002 D2 - Curvilinear Motion]]
- Concepts: [[Normal and Tangential Coordinates]] · [[Kinematic Relations for Rectilinear Motion]] · [[Newton's Laws of Motion]]
- Year 2: Ballistic and gravity-turn trajectories in [[SESA2024 Astronautics Hub]] · drag from [[SESA2022 Aerodynamics Hub]]

## Sources

- Dynamics Lecture 2.2
