---
title: "Normal and Tangential Coordinates"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["n-t coordinates", "centripetal acceleration", "radius of curvature", "v^2/rho", "path coordinates"]
tags: [feeg1002, concept, dynamics, curvilinear-motion]
status: complete
parent_lectures: ["[[FEEG1002 D2 - Curvilinear Motion]]", "[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
related_concepts: ["[[Projectile Motion]]", "[[Newton's Laws of Motion]]", "[[Relative Velocity Equation for Rigid Bodies]]"]
sources: []
---

# Normal and Tangential Coordinates

## Definition

> [!note] Definition
> Axes attached to the particle: $\mathbf u_t$ is tangent to the path (along $\mathbf v$) and $\mathbf u_n$ points to the centre of curvature.
>
> $$\mathbf v = v\mathbf u_t,\qquad \mathbf a = \dot v\,\mathbf u_t + \frac{v^2}{\rho}\mathbf u_n,\qquad \rho = \frac{[1 + (dy/dx)^2]^{3/2}}{|d^2y/dx^2|}$$

## Explanation

- $a_t = \dot v = v\,dv/ds$ changes the **speed**. $a_n = v^2/\rho$ changes the **direction**; it always points inward and exists even at constant speed.
- **Kinetics**: $\sum F_t = ma_t$, $\sum F_n = mv^2/\rho$, $\sum F_b = 0$.
- **Circular path**: $\rho = R$, so $v = R\omega$, $a_t = R\alpha$ and $a_n = R\omega^2$.
- **Contact problems**: a body leaves a surface when $N\to0$. Loops need $v_{top}\ge\sqrt{gR}$; a car over a crest needs $v^2/\rho < g\cos\theta$.
- Include $mg$ in the FBD only for motion in a **vertical** plane.

## Examples

- **Car over a hill** (Lecture 2): $\rho = 223.6$ m, $N = 6728$ N, $F = 1114$ N.
- **Banked curve** (Tutorial 2 Q5): $v_0 = \sqrt{\rho g\tan\theta} = 19.6$ m/s.

![[d_nt_coordinates.png|700]]

## Related

- Topic notes: [[FEEG1002 D2 - Curvilinear Motion]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Concepts: [[Projectile Motion]] · [[Newton's Laws of Motion]] · [[Relative Velocity Equation for Rigid Bodies]]
- Year 2: Load factor in turns and pull-ups, [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · circular orbits $v = \sqrt{\mu/r}$ in [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] · centripetal body force in [[SESA2028 S11 - Spinning Discs]]

## Sources

- Dynamics Lecture 2.3
