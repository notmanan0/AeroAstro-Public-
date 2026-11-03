---
title: "Six-Degree-of-Freedom State Model"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 4: Dynamic Equations and 6-DOF Model"
aliases: ["12-state rigid-body model", "complete flat-Earth model", "6-DOF model", "six-degree-of-freedom equations of motion", "twelve-state model"]
tags: [sesa3047, concept, 6dof, state-equations]
status: complete
coverage: "Chapter 4 §4.3; shown from the lecture notes at the end of L13 (ll. 310–344, Thu 22 Oct)"
parent_lectures: ["[[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]"]
related_concepts: ["[[Translational Dynamic Equation]]", "[[Rotational Dynamic Equation]]", "[[State, Input, Output and Parameter]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L13 - SESA3047.txt"]
---

# Six-Degree-of-Freedom State Model

A rigid vehicle's six physical degrees of freedom become twelve first-order states:

$$
\mathbf x=[x,y,z,\phi,\theta,\psi,u,v,w,p,q,r]^T.
$$

In the lecturer's words, that's *"6 states for the dynamics, and 6 states for the kinematics"* (L13 ll. 339–340): each of the six second-order equations of motion becomes a rate state ($u,v,w,p,q,r$) plus a coordinate state ($x,y,z,\phi,\theta,\psi$). Four groups of equations advance them:

| Group | Equation | States advanced |
|---|---|---|
| Translational kinematics | $\dot{\mathbf p}=\mathbf C^T\mathbf v$ | NED position |
| Rotational kinematics | $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ | Euler angles |
| Translational dynamics | $\dot{\mathbf v}=\mathbf F/m+\mathbf C\mathbf g-\tilde{\boldsymbol\omega}\mathbf v$ | FRD velocity |
| Rotational dynamics | $\dot{\boldsymbol\omega}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)$ | FRD angular velocity |

Here $\mathbf g=[0,0,g]^T$ is NED gravity and $\mathbf F$ excludes the weight. The model assumes constant mass and body inertia, a flat Earth, and Euler angles away from gimbal lock.

All four groups have to be evaluated together from the current state, and force and moment models plus initial conditions are needed before the system can be integrated. The DCM is an algebraic function of the Euler angles, not an extra state. A closed-form solution only exists in simplified cases, so in general the model is integrated numerically in MATLAB or Python (L13 ll. 320–325).

One case that can be checked analytically is a freely falling body yawing at $r=0.3$ rad/s: its centre of mass follows a parabola while $u$ and $v$ oscillate as its axes turn. The analytic solution and a numerical integration check are in [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model#5. Exact ballistic integration check (suggested)|4.3 §5]].

## Related

- [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]
- [[Translational Kinematic Equation]] · [[Rotational Kinematic Equation]] · [[Translational Dynamic Equation]] · [[Rotational Dynamic Equation]]
- Source: Chapter_4.pdf pp. 9–10, Eqs. (4.41)–(4.42); L13 ll. 310–344.
