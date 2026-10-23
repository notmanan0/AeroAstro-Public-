---
title: "Translational Dynamic Equation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["velocity state equation", "body-axis force equations"]
tags: [sesa3047, concept, dynamics, gravity]
status: complete
coverage: "Chapter 4 §4.2; lectured in L13 ll. 88–309 (Thu 22 Oct) except Eqs. 4.31 and 4.38–4.40"
parent_lectures: ["[[SESA3047 4.2 - Translational Dynamics]]"]
related_concepts: ["[[Translational Kinematic Equation]]", "[[Transport Theorem]]", "[[Flat-Earth Model]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L13 - SESA3047.txt"]
---

# Translational Dynamic Equation

> [!note] Statement
> Under flat Earth, with FRD velocity and non-gravitational force $\mathbf F$,
>
> $$\boxed{\dot{\mathbf v}=\mathbf F/m+\mathbf C_{FRD/NED}[0,0,g]^T-\boldsymbol\omega\times\mathbf v.}$$

## Derivation

Newton gives $\mathbf a=\mathbf F/m+\mathbf g$. The [[Transport Theorem]] gives $\mathbf a^{FRD}=\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v$. Equate them, rotate gravity into FRD, and subtract the coordinate-rotation term.

As lectured (L13 ll. 243–278), the derivation is four moves: Newton in the inertial frame; on a rotating Earth this adds centrifugal and Coriolis terms; flat Earth ($\boldsymbol\omega_{e/i}=\mathbf 0$) removes them; and the body-frame derivative adds $\boldsymbol\omega_{b/e}\times\mathbf v$. Do not forget the last step that the lecturer nearly forgot: $[0,0,g]^T$ is valid only in NED, so rotate it with $\mathbf C_{FRD/NED}$ (ll. 289–303).

$$
\mathbf g^{FRD}=g[-\sin\theta,\ \sin\phi\cos\theta,\ \cos\phi\cos\theta]^T.
$$

If total body forces $[X,Y,Z]^T$ already include weight, the equivalent equations are

$$
X=m(\dot u+qw-rv),\quad
Y=m(\dot v+ru-pw),\quad
Z=m(\dot w+pv-qu).
$$

Do not add another gravity term to that convention.

## Interpretation and checks

Forces change the physical velocity vector; body rotation changes its coordinate components. Level free fall gives $\dot w=g$. Level supported motion with $\mathbf F=[0,0,-mg]^T$ and zero body rates gives zero derivative.

This is **dynamics** for $u,v,w$. The [[Translational Kinematic Equation]] is $\dot{\mathbf p}^{NED}=\mathbf C^T\mathbf v$, which advances position.

## Related

- Derivation, rotating-Earth extension and numerical check: [[SESA3047 4.2 - Translational Dynamics]].
- [[Six-Degree-of-Freedom State Model]] · [[Direction Cosine Matrix]]
- Source: Chapter_4.pdf pp. 7–9, Eqs. (4.26)–(4.40); L13 ll. 88–309.
