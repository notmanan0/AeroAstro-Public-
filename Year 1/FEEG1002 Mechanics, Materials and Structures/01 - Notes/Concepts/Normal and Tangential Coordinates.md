---
title: "Normal and Tangential Coordinates"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["n-t coordinates", "centripetal acceleration", "radius of curvature", "v^2/rho", "path coordinates", "intrinsic coordinates", "tangential and normal components"]
tags: [feeg1002, concept, dynamics, curvilinear-motion]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D2 - Curvilinear Motion]]", "[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
related_concepts: ["[[Projectile Motion]]", "[[Newton's Laws of Motion]]", "[[Relative Velocity Equation for Rigid Bodies]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 02 - Curvilinear Motion.pdf"]
---

# Normal and Tangential Coordinates

Normal and tangential (n-t) axes have their origin on the particle and move with it: $t$ is tangent to the path, positive in the direction of motion, and $n$ is perpendicular to it, positive towards the centre of curvature. In these axes the acceleration splits into a part that changes the speed and a part that turns the velocity.

$$
\mathbf v=v\,\mathbf u_t,\qquad \mathbf a=\dot v\,\mathbf u_t+\frac{v^2}{\rho}\,\mathbf u_n
$$

The velocity is always tangent to the path. Differentiating $v\,\mathbf u_t$ needs the derivative of the unit vector: as the particle moves through $ds$ the tangent turns through $d\theta=ds/\rho$ and $d\mathbf u_t=d\theta\,\mathbf u_n$, so $\dot{\mathbf u}_t=(v/\rho)\mathbf u_n$. The tangential component $a_t=\dot v=v\,dv/ds$ follows the rules of straight-line motion; the normal component $a_n=v^2/\rho$ always points to the concave side and is present even at constant speed. For a path $y=f(x)$,

$$
\rho=\frac{\left[1+(dy/dx)^2\right]^{3/2}}{\left|d^2y/dx^2\right|}
$$

On a circle $\rho=R$, so $v=R\omega$, $a_t=R\alpha$ and $a_n=R\omega^2$, the same relations used for points on a rotating rigid body.

Newton's second law resolved along these axes reads $\sum F_t=ma_t$, $\sum F_n=mv^2/\rho$ and $\sum F_b=0$ along the binormal. The normal equation says that a curved path needs an unbalanced **centripetal force** towards the centre of curvature; there is no centrifugal force on the free-body diagram. For the 800 kg car on the parabolic hill, $\rho=223.6$ m at $x=80$ m and the road pushes with $N=6730$ N, less than $mg\cos\theta$ because part of that component turns the car over the crest. A body stays on a surface only while $N\ge0$, which sets the minimum speed $\sqrt{gR}$ at the top of a loop.

Two mistakes recur. On a banked track the $n$ axis is horizontal, towards the centre of the bend at the car's own height, not down the bank. In a top-view problem the weight is perpendicular to the page and is balanced by the normal reaction, so it is left out.

![[d_nt_coordinates.png|700]]

## Related

- [[FEEG1002 D2 - Curvilinear Motion#4. Normal and tangential coordinates|D2 §4]] · [[FEEG1002 D2 - Curvilinear Motion#Acceleration|acceleration derivation]] · [[FEEG1002 D2 - Curvilinear Motion#Radius of curvature|radius of curvature]] · [[FEEG1002 D2 - Curvilinear Motion#The third axis|binormal and banking]] · [[FEEG1002 D2 - Curvilinear Motion#Circular paths|circular paths]] · [[FEEG1002 D2 - Curvilinear Motion#5. Equations of motion in n-t coordinates|equations of motion]] · [[FEEG1002 D2 - Curvilinear Motion#Car over a parabolic hill|car over a hill]] · [[FEEG1002 D2 - Curvilinear Motion#Simple pendulum|pendulum]] · [[FEEG1002 D3 - Work, Energy and Power#Minimum speed for a loop|loop]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies#Acceleration of a point|points on a rotating body]]
- [[Projectile Motion]] · [[Newton's Laws of Motion]] · [[Kinematic Relations for Rectilinear Motion]] · [[Relative Velocity Equation for Rigid Bodies]]
- Year 2: circular orbits in [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] · centripetal body force in [[SESA2028 S11 - Spinning Discs]]
