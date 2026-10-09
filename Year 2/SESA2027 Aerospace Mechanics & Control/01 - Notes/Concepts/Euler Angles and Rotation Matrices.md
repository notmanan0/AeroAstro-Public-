---
title: "Euler Angles and Rotation Matrices"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["Tait-Bryan angles", "rotation matrix", "direction cosine matrix", "gimbal lock", "body axes"]
tags: [sesa2027, concept, kinematics]
status: complete
parent_lectures: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]"]
related_concepts: ["[[Small Perturbation Linearisation]]", "[[State-Space Representation]]"]
sources: ["02 - Sources/Lectures/Lecture 1.02.pdf"]
---

# Euler Angles and Rotation Matrices

## Definition

> [!note] Definition
> The attitude of the body frame relative to the Earth frame is given by three **Tait–Bryan (Euler) angles**, applied in the order **yaw $\psi$ → pitch $\theta$ → roll $\phi$**:
>
> $$\mathbf v_B = \mathbf R_{BE}\mathbf v_E,\qquad \mathbf R_{BE} = \mathbf R_x(\phi)\mathbf R_y(\theta)\mathbf R_z(\psi)$$

## Explanation

$$
\mathbf R_x(\phi)=\begin{pmatrix}1&0&0\\0&c_\phi&s_\phi\\0&-s_\phi&c_\phi\end{pmatrix},\quad \mathbf R_y(\theta)=\begin{pmatrix}c_\theta&0&-s_\theta\\0&1&0\\s_\theta&0&c_\theta\end{pmatrix},\quad \mathbf R_z(\psi)=\begin{pmatrix}c_\psi&s_\psi&0\\-s_\psi&c_\psi&0\\0&0&1\end{pmatrix}
$$

- **Orthogonal**: $\mathbf R^{-1} = \mathbf R^T$, so the reverse transformation is $\mathbf v_E = \mathbf R_{BE}^T\mathbf v_B$.
- **Order matters**: matrix products do not commute, so a different sequence gives a different attitude.
- **Gimbal lock**: at $\theta = \pm90^\circ$, yaw and roll become indistinguishable. The ranges are $\phi,\psi\in[-\pi,\pi]$ and $\theta\in[-\pi/2,\pi/2]$. Quaternions avoid this (Year 3).
- **Body axes**: $x$ forward, $y$ starboard, $z$ down. Rates $p, q, r$; velocities $U, V, W$; forces $X, Y, Z$; moments $L, M, N$.
- **Rotating frame**: $\dfrac{d\mathbf v}{dt} = \dot{\mathbf v}_B+\boldsymbol\omega\times\mathbf v$. This gives the $qW$ and $rV$ state-product terms in the equations of motion.
- **Gravity** in body axes: $\mathbf g_B = \mathbf R_{BE}[0,0,g]^T = g[-\sin\theta,\ \sin\phi\cos\theta,\ \cos\phi\cos\theta]^T$. That is why $\Delta X_g = -mg\theta\cos\gamma_0$ after linearisation.

## Examples
- Longitudinal motion only ($\phi = \psi = 0$): $\mathbf R_{BE} = \mathbf R_y(\theta)$, and $\dot\theta = q$ exactly. This is the fourth row of the longitudinal state equation ([[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]).

## Related
- [[Small Perturbation Linearisation]] · [[State-Space Representation]]

## Sources
- Lecture 1.02; Cook, *Flight Dynamics Principles*, Ch. 2
