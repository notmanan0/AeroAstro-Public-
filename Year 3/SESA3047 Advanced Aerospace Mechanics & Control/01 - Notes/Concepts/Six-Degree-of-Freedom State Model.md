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

Six physical degrees of freedom become twelve first-order states:

$$
\mathbf x=[x,y,z,\phi,\theta,\psi,u,v,w,p,q,r]^T.
$$

| Group | Equation | States advanced |
|---|---|---|
| Translational kinematics | $\dot{\mathbf p}=\mathbf C^T\mathbf v$ | NED position |
| Rotational kinematics | $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ | Euler angles |
| Translational dynamics | $\dot{\mathbf v}=\mathbf F/m+\mathbf C\mathbf g-\tilde{\boldsymbol\omega}\mathbf v$ | FRD velocity |
| Rotational dynamics | $\dot{\boldsymbol\omega}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega)$ | FRD angular velocity |

Here $\mathbf g=[0,0,g]^T$ is NED gravity and $\mathbf F$ excludes weight. The assumptions are constant mass and body inertia, flat Earth, and Euler angles away from gimbal lock.

The equations must be evaluated together from the current state. Force and moment models and initial conditions are needed before the system can be integrated. The DCM is an algebraic transformation, not an additional state.

**Why twelve:** *"6 states for the dynamics, and 6 states for the kinematics"* (L13 ll. 339–340). Each of the six second-order equations of motion becomes a rate state ($u,v,w,p,q,r$) plus a coordinate state ($x,y,z,\phi,\theta,\psi$).

**Why numerical:** a closed-form solution exists only in simplified conditions. In general the model is integrated in MATLAB or Python (L13 ll. 320–325).

## Verified example

A freely falling body yawing at $r=0.3$ rad/s has a parabolic centre-of-mass path while $u,v$ oscillate as its axes turn. The full analytic solution and a numerical integration check are in [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model#5. Exact ballistic integration check (suggested)|4.3 §5]].

## Related

- [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]
- [[Translational Kinematic Equation]] · [[Rotational Kinematic Equation]] · [[Translational Dynamic Equation]] · [[Rotational Dynamic Equation]]
- Source: Chapter_4.pdf pp. 9–10, Eqs. (4.41)–(4.42); L13 ll. 310–344.
