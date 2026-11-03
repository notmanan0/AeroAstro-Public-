---
title: "Translational Dynamic Equation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["velocity state equation", "body-axis force equations", "force equations", "Newton's equations in body axes"]
tags: [sesa3047, concept, dynamics, gravity]
status: complete
coverage: "Chapter 4 §4.2; lectured in L13 ll. 88–309 (Thu 22 Oct) except Eqs. 4.31 and 4.38–4.40"
parent_lectures: ["[[SESA3047 4.2 - Translational Dynamics]]"]
related_concepts: ["[[Translational Kinematic Equation]]", "[[Transport Theorem]]", "[[Flat-Earth Model]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L13 - SESA3047.txt"]
---

# Translational Dynamic Equation

On a flat Earth, with the velocity in FRD and $\mathbf F$ the non-gravitational force,

$$\boxed{\dot{\mathbf v}=\mathbf F/m+\mathbf C_{FRD/NED}[0,0,g]^T-\boldsymbol\omega\times\mathbf v.}$$

Newton gives $\mathbf a=\mathbf F/m+\mathbf g$, and the [[Transport Theorem]] gives $\mathbf a^{FRD}=\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v$. Equate the two, rotate gravity into FRD, and move the coordinate-rotation term across. As lectured (L13 ll. 243–278) it takes four moves: Newton in the inertial frame; on a rotating Earth this adds centrifugal and Coriolis terms; the flat-Earth assumption ($\boldsymbol\omega_{e/i}=\mathbf 0$) removes them; and the body-frame derivative adds $\boldsymbol\omega_{b/e}\times\mathbf v$. The last step, which the lecturer nearly forgot, is that $[0,0,g]^T$ is only valid in NED and has to be rotated with $\mathbf C_{FRD/NED}$ (ll. 289–303):

$$
\mathbf g^{FRD}=g[-\sin\theta,\ \sin\phi\cos\theta,\ \cos\phi\cos\theta]^T.
$$

If the total body forces $[X,Y,Z]^T$ already include the weight, the equivalent equations are

$$
X=m(\dot u+qw-rv),\quad
Y=m(\dot v+ru-pw),\quad
Z=m(\dot w+pv-qu),
$$

and you must not add another gravity term.

The forces change the physical velocity vector, while body rotation changes its components. Some checks: level free fall gives $\dot w=g$, and level supported flight with $\mathbf F=[0,0,-mg]^T$ and zero body rates gives zero. In a steady level turn $\dot{\mathbf v}=\mathbf 0$ even though the aircraft accelerates towards the centre; the $y$ row then gives $\dot\psi=g\tan\phi/V$ and the $z$ row $F_z=-mg/\cos\phi$ ([[SESA3047 4.2 - Translational Dynamics#6. Worked example: forces for a steady level turn (suggested)|4.2 §6]]).

This is the dynamics for $u,v,w$. Position is advanced separately by the [[Translational Kinematic Equation]], $\dot{\mathbf p}^{NED}=\mathbf C^T\mathbf v$.

## Related

- Derivation, rotating-Earth extension and numerical check: [[SESA3047 4.2 - Translational Dynamics]].
- [[Six-Degree-of-Freedom State Model]] · [[Direction Cosine Matrix]]
- Source: Chapter_4.pdf pp. 7–9, Eqs. (4.26)–(4.40); L13 ll. 88–309.
