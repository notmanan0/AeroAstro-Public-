---
title: "Rotational Dynamic Equation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 3: Kinematic Equations and Introduction to Dynamics"
aliases: ["angular-velocity state equation", "Euler's equations", "Euler's rotational equations", "gyroscopic term", "moment equations", "Euler's moment equations", "inertia coupling", "inertial coupling", "roll coupling"]
tags: [sesa3047, concept, dynamics, angular-momentum]
status: complete
parent_lectures: ["[[SESA3047 3.3 - Rigid-Body Rotational Dynamics]]"]
related_concepts: ["[[Inertia Matrix]]", "[[Transport Theorem]]", "[[Cross-Product Matrix]]", "[[Rotational Kinematic Equation]]"]
sources: ["02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/L11 - SESA3047.txt"]
---

# Rotational Dynamic Equation

For a rigid body with inertia matrix $\mathbf J$ about its centre of mass, in body-fixed FRD coordinates,

$${}^b\dot{\boldsymbol\omega}^{FRD}_{b/i}=\left(\mathbf J^{FRD}\right)^{-1}\left[\left(\sum\mathbf M_{cm}\right)^{FRD}-\tilde{\boldsymbol\omega}^{FRD}_{b/i}\,\mathbf J^{FRD}\boldsymbol\omega^{FRD}_{b/i}\right]\qquad(3.71)$$

It starts from Newton's law for rotation in the inertial frame, $\sum\mathbf M_{cm}={}^i\dot{\mathbf h}$ with $\mathbf h=\mathbf J\boldsymbol\omega$ ([[Inertia Matrix]]). The [[Transport Theorem]] moves the derivative to body axes, ${}^i\dot{\mathbf h}={}^b\dot{\mathbf h}+\boldsymbol\omega\times\mathbf h$. In body axes $\dot{\mathbf J}=\mathbf 0$ because the body is rigid (constant mass alone isn't enough: deploying panels change $\mathbf J$ at fixed $m$), so ${}^b\dot{\mathbf h}=\mathbf J\dot{\boldsymbol\omega}$, and $\boldsymbol\omega\times\mathbf h=\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega$. Solving for $\dot{\boldsymbol\omega}$ gives (3.71).

The step-by-step derivation and figure are in [[SESA3047 3.3 - Rigid-Body Rotational Dynamics#4. The rotational dynamic equation (§3.3.3, Eqs. 3.64–3.71)|3.3 §4]]. L10 (Mon 12 Oct) ended at the implicit form $\sum\mathbf M_{cm}=\mathbf J\dot{\boldsymbol\omega}+\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega$ (3.70), and [[SESA3047 3.3 - Rigid-Body Rotational Dynamics#Two facts L10 glossed|3.3]] fills in the two steps it skipped over. L11 ll. 35–68 revisits the explicit derivative and ll. 72–228 expand the full-inertia equation and the principal-axis case; see [[SESA3047 4.1 - Inertia Models and Rotor Dynamics]].

## Special forms

This note and 3.3 write the moments of inertia as $J_x,J_y,J_z$; 4.1 and the Chapter 4 handout write $J_{xx},J_{yy},J_{zz}$ for the same things.

On principal axes the equation becomes Euler's equations:

$$
J_x\dot p=L+(J_y-J_z)qr,\qquad J_y\dot q=M+(J_z-J_x)rp,\qquad J_z\dot r=N+(J_x-J_y)pq.
$$

For an aircraft with $x$–$z$ symmetry ($J_{xz}\neq0$):

$$
L=J_x\dot p-J_{xz}\dot r+(J_z-J_y)qr-J_{xz}pq,
$$

$$
M=J_y\dot q+(J_x-J_z)pr+J_{xz}(p^2-r^2),
$$

$$
N=J_z\dot r-J_{xz}\dot p+(J_y-J_x)pq+J_{xz}qr.
$$

With an internal rotor, the total momentum is $\mathbf h=\mathbf J\boldsymbol\omega+\mathbf h_R$ and $-\mathbf J^{-1}(\boldsymbol\omega\times\mathbf h_R+{}^b\dot{\mathbf h}_R)$ is added to the baseline derivative ([[Rotor Angular Momentum]]; Chapter 4 §4.1.4, lectured in L12–L13, with the ${}^b\dot{\mathbf h}_R$ term in the handout only).

## Physical meaning

$\mathbf M$ is the applied moment: aerodynamic, thrust, controls. The $\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega$ term is the change of angular momentum due to the rotating body frame (Chapter 3, p. 14; the gyroscopic term in textbooks). It exists even with no applied moment, because $\mathbf h$ is generally not parallel to $\boldsymbol\omega$. It is behind inertia coupling (Chapter 4, p. 4; L12; Lab 1 says "inertial coupling"), the need to balance rotors, and the instability of spin about the intermediate principal axis. Torque-free motion conserves $|\mathbf h|$ and the kinetic energy $\tfrac12\boldsymbol\omega^T\mathbf J\boldsymbol\omega$.

## Related

- [[Inertia Matrix]] (SESA2024) · [[Momentum Bias and Gyroscopic Rigidity]] (SESA2024)
- [[Rotational Kinematic Equation]] · [[Translational Kinematic Equation]] · [[Coriolis and Centripetal Acceleration]]
- Year 1: [[Planar Rigid-Body Equations of Motion]] · Year 2: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]
