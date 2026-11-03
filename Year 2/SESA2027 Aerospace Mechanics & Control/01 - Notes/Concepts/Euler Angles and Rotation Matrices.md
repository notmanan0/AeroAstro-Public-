---
title: "Euler Angles and Rotation Matrices"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["Tait-Bryan angles", "rotation matrix", "direction cosine matrix", "gimbal lock", "body axes", "3-2-1 Euler sequence", "Earth-to-body rotation"]
tags: [sesa2027, concept, kinematics]
status: complete
parent_lectures: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]"]
related_concepts: ["[[Small Perturbation Linearisation]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Lecture 1.02.pdf", "Cook, Flight Dynamics Principles, Ch. 2"]
---

# Euler Angles and Rotation Matrices

The attitude of the body axes relative to the Earth axes is given by three Tait–Bryan (Euler) angles applied in the order yaw $\psi$, then pitch $\theta$, then roll $\phi$:

$$
\mathbf v_B = \mathbf R_{BE}\mathbf v_E,\qquad \mathbf R_{BE} = \mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi),
$$

$$
\mathbf R_x(\phi)=\begin{pmatrix}1&0&0\\0&c_\phi&s_\phi\\0&-s_\phi&c_\phi\end{pmatrix},\quad \mathbf R_y(\theta)=\begin{pmatrix}c_\theta&0&-s_\theta\\0&1&0\\s_\theta&0&c_\theta\end{pmatrix},\quad \mathbf R_z(\psi)=\begin{pmatrix}c_\psi&s_\psi&0\\-s_\psi&c_\psi&0\\0&0&1\end{pmatrix}.
$$

Each rotation matrix is orthogonal, $\mathbf R^{-1} = \mathbf R^T$, so the reverse transformation is $\mathbf v_E = \mathbf R_{BE}^T\mathbf v_B$. Matrix products don't commute, so a different order gives a different attitude. The body axes are $x$ forward, $y$ starboard and $z$ down, with rates $p, q, r$, velocities $U, V, W$, forces $X, Y, Z$ and moments $L, M, N$. The angles are restricted to $\phi,\psi\in[-\pi,\pi]$ and $\theta\in[-\pi/2,\pi/2]$; at $\theta = \pm90^\circ$ yaw and roll become indistinguishable (gimbal lock), which quaternions avoid. Year 3 picks this up in [[Gimbal Lock]].

Two results from the rotation matrices feed straight into the equations of motion. Differentiating a vector in the rotating body frame gives $d\mathbf v/dt = \dot{\mathbf v}_B+\boldsymbol\omega\times\mathbf v$, which produces the $qW$ and $rV$ terms. Rotating gravity into body axes gives

$$
\mathbf g_B = \mathbf R_{BE}\begin{bmatrix}0\\0\\g\end{bmatrix} = g\begin{bmatrix}-\sin\theta\\ \sin\phi\cos\theta\\ \cos\phi\cos\theta\end{bmatrix},
$$

which is where $\Delta X_g = -mg\theta\cos\gamma_0$ comes from after linearisation. For purely longitudinal motion ($\phi = \psi = 0$), $\mathbf R_{BE} = \mathbf R_y(\theta)$ and $\dot\theta = q$ exactly, the fourth row of the longitudinal state equation ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]).

## Related

- $\mathbf R_{BE}$ multiplied out and gravity in body axes: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion#Euler angles and rotation matrices|A1]]
- [[Small Perturbation Linearisation]] · [[State-Space Representation]]
