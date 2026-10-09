---
title: "Rotational Dynamic Equation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 3: Kinematic Equations and Introduction to Dynamics"
aliases: ["angular-velocity state equation", "Euler's equations", "Euler's rotational equations", "gyroscopic term", "moment equations"]
tags: [sesa3047, concept, dynamics, angular-momentum]
status: complete
parent_lectures: ["[[SESA3047 3.3 - Rigid-Body Rotational Dynamics]]"]
related_concepts: ["[[Inertia Matrix]]", "[[Transport Theorem]]", "[[Cross-Product Matrix]]", "[[Rotational Kinematic Equation]]"]
sources: ["02 - Sources/Lectures/Chapter-3.pdf"]
---

# Rotational Dynamic Equation

## Statement

> [!note] Definition
> For a rigid body with inertia matrix $\mathbf J$ about its centre of mass, in body-fixed FRD coordinates:
>
> $${}^b\dot{\boldsymbol\omega}^{FRD}_{b/i}=\left(\mathbf J^{FRD}\right)^{-1}\left[\left(\sum\mathbf M_{cm}\right)^{FRD}-\tilde{\boldsymbol\omega}^{FRD}_{b/i}\,\mathbf J^{FRD}\boldsymbol\omega^{FRD}_{b/i}\right]\qquad(3.71)$$

## Derivation in four lines

1. Newton for rotation in the inertial frame: $\sum\mathbf M_{cm}={}^i\dot{\mathbf h}$, with $\mathbf h=\mathbf J\boldsymbol\omega$ ([[Inertia Matrix]]).
2. [[Transport Theorem]] to body axes: ${}^i\dot{\mathbf h}={}^b\dot{\mathbf h}+\boldsymbol\omega\times\mathbf h$.
3. In body axes $\dot{\mathbf J}=\mathbf 0$, so ${}^b\dot{\mathbf h}=\mathbf J\dot{\boldsymbol\omega}$; and $\boldsymbol\omega\times\mathbf h=\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega$.
4. Solve for $\dot{\boldsymbol\omega}$.

Step-by-step derivation and figure: [[SESA3047 3.3 - Rigid-Body Rotational Dynamics#4. The rotational dynamic equation (§3.3.3, Eqs. 3.64–3.71)|3.3 §4]].

## Special forms

**Principal axes** (Euler's equations):

$$
J_x\dot p=L+(J_y-J_z)qr,\qquad J_y\dot q=M+(J_z-J_x)rp,\qquad J_z\dot r=N+(J_x-J_y)pq.
$$

**Aircraft with $x$–$z$ symmetry** ($J_{xz}\neq0$):

$$
L=J_x\dot p-J_{xz}\dot r+(J_z-J_y)qr-J_{xz}pq,
$$

$$
M=J_y\dot q+(J_x-J_z)pr+J_{xz}(p^2-r^2),
$$

$$
N=J_z\dot r-J_{xz}\dot p+(J_y-J_x)pq+J_{xz}qr.
$$

## Physical meaning

- $\mathbf M$: applied moments (aerodynamic, thrust, controls).
- $\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega$: the **gyroscopic** term. It exists with no applied moment, because $\mathbf h$ is generally not parallel to $\boldsymbol\omega$. It causes inertia (roll) coupling, the need to balance rotors, and the instability of spin about the intermediate principal axis.
- Torque-free motion conserves $|\mathbf h|$ and the kinetic energy $\tfrac12\boldsymbol\omega^T\mathbf J\boldsymbol\omega$.

## Related

- [[Inertia Matrix]] (SESA2024) · [[Momentum Bias and Gyroscopic Rigidity]] (SESA2024)
- [[Rotational Kinematic Equation]] · [[Translational Kinematic Equation]] · [[Coriolis and Centripetal Acceleration]]
- Year 1: [[Planar Rigid-Body Equations of Motion]] · Year 2: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]
