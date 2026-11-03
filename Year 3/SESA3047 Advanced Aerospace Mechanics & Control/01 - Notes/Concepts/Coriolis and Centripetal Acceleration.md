---
title: "Coriolis and Centripetal Acceleration"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 3: Kinematic Equations and Introduction to Dynamics"
aliases: ["Coriolis acceleration", "centripetal acceleration", "transport acceleration", "transport velocity", "five-term acceleration", "apparent forces", "centrifugal force", "Coriolis force", "tangential acceleration", "Euler acceleration", "fictitious forces", "velocity of the coincident point", "compound centripetal acceleration"]
tags: [sesa3047, concept, kinematics, rotating-frames]
status: complete
parent_lectures: ["[[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]]"]
related_concepts: ["[[Transport Theorem]]", "[[Angular Velocity Vector]]", "[[Flat-Earth Model]]", "[[Translational Kinematic Equation]]"]
sources: ["02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/L8 - SESA3047.txt", "02 - Sources/Lectures/L9 - SESA3047.txt"]
---

# Coriolis and Centripetal Acceleration

Take a point P with position $\mathbf p=\mathbf p_{P/Q}$ in a frame $F_b$ (origin $Q$) that moves and rotates at $\boldsymbol\omega$, with angular acceleration $\boldsymbol\alpha$, relative to $F_a$. Its velocity and acceleration seen from $F_a$ are

$$\mathbf v_{P/a}=\mathbf v_{P/b}+\underbrace{\mathbf v_{Q/a}+\boldsymbol\omega\times\mathbf p}_{\text{transport velocity}}\qquad(3.23)$$

$$\mathbf a_{P/a}=\mathbf a_{P/b}+\underbrace{\mathbf a_{Q/a}+\boldsymbol\alpha\times\mathbf p+\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf p)}_{\text{transport acceleration}}+\underbrace{2\boldsymbol\omega\times\mathbf v_{P/b}}_{\text{Coriolis}}\qquad(3.26)$$

The **centripetal** term, $\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf p)=-\omega^2\mathbf p_\perp$, points at the rotation axis; a point fixed in a rotating frame moves on a circle and needs it. The $\boldsymbol\alpha\times\mathbf p$ term (tangential or Euler acceleration in textbooks) only appears if the spin rate changes. The **Coriolis** term, $2\boldsymbol\omega\times\mathbf v_{P/b}$, only appears if P moves within the rotating frame, and it is perpendicular to both $\boldsymbol\omega$ and the relative velocity.

The factor of 2 comes from $\boldsymbol\omega\times\mathbf v_{P/b}$ turning up twice when you differentiate (3.23). The transport theorem applied to $\mathbf v_{P/b}$ gives one, because the rotation turns the direction of the relative velocity. The product rule on $\boldsymbol\omega\times\mathbf p$ gives the other, because P moves to a part of the frame with a different transport velocity. Step-by-step derivation: [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames#2. Acceleration of a point in a moving frame (§3.2.1, Eqs. 3.24–3.26)|3.2 §2]].

## Apparent forces on a rotating Earth

Moving the rotation terms to the force side of Newton's law gives (3.31)

$$
m\mathbf a_{P/e}=\sum\mathbf F_{real}-m\,\boldsymbol\omega_{e/i}\times(\boldsymbol\omega_{e/i}\times\mathbf p)-2m\,\boldsymbol\omega_{e/i}\times\mathbf v_{P/e}.
$$

These centrifugal and Coriolis "forces" aren't real; they come from working in a non-inertial frame. At 50°N the centrifugal term is 0.022 m/s², and the Coriolis term on a 250 m/s aircraft is 0.028 m/s² (about 0.3% of $g$), deflecting motion to the right in the northern hemisphere. The [[Flat-Earth Model]] neglects both.

With $F_b$ as the aircraft body, the same idea gives the body-axis acceleration $[\dot u+qw-rv,\ \dot v+ru-pw,\ \dot w+pv-qu]^T$ (3.42). The $\boldsymbol\omega\times\mathbf v$ terms are there because the axes rotate, not because of any force.

## Related

- [[Transport Theorem]] · [[Angular Velocity Vector]] · [[Cross-Product Matrix]]
- [[Translational Kinematic Equation]] · [[Rotational Dynamic Equation]]
- Year 1: [[Relative Velocity Equation for Rigid Bodies]]
