---
title: "Principle of Angular Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["angular momentum", "moment of momentum", "H = r x mv", "conservation of angular momentum", "central force"]
tags: [feeg1002, concept, dynamics, angular-momentum]
status: complete
parent_lectures: ["[[FEEG1002 D5 - Angular Impulse and Momentum]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
related_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Orbital Angular Momentum]]", "[[Planar Rigid-Body Equations of Motion]]"]
sources: []
---

# Principle of Angular Impulse and Momentum

## Definition

> [!note] Definition
> $$\mathbf H_O = \mathbf r\times m\mathbf v,\qquad \sum\mathbf M_O = \dot{\mathbf H}_O,\qquad (\mathbf H_O)_1 + \sum\int_{t_1}^{t_2}\mathbf M_O\,dt = (\mathbf H_O)_2$$
> If all the forces pass through O (**central forces**), $H_O = rmv_\perp$ is conserved.

## Explanation

- In 2D, $H_O = mvd$, where $d$ is the perpendicular distance from O to the line of $\mathbf v$.
- **Central-force examples**: a cord pulled towards a pin, a spring anchored at a point, gravity.
- **Conservation of $H$ is not conservation of KE.** Pulling a cord in does work, so the speed rises.
- Combined with energy it solves orbits: perigee and apogee speeds and radii. If $\mathbf v\not\perp\mathbf r$ at the known point, use $rv\sin\phi$.
- For a rigid body $H_G = I_G\omega$, which gives $\sum M_G = I_G\alpha$ ([[Planar Rigid-Body Equations of Motion]]).

## Examples

- **Amusement ride** (Lecture 5): $v' = r_1v_1/r_2 = 1.371$ m/s, and the cable does 27.9 J of work.
- **Orbit** (Lecture 5): $v_B = 5382$ m/s at $r_B = 10.80\times10^6$ m.

![[d_elliptical_orbit_example.png|640]]

## Related

- Topic notes: [[FEEG1002 D5 - Angular Impulse and Momentum]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies]]
- Concepts: [[Principle of Linear Impulse and Momentum]] · [[Orbital Angular Momentum]] · [[Planar Rigid-Body Equations of Motion]]
- Year 2: [[Orbital Angular Momentum]] and [[Kepler's Laws]] · momentum exchange in attitude control, [[Reaction Wheels and Momentum Dumping]] and [[SESA2024 06 - Attitude Control]]

## Sources

- Dynamics Lecture 5
