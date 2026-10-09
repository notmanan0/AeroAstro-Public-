---
title: "Rotational Kinematic Equation"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 3: Kinematic Equations and Introduction to Dynamics"
aliases: ["Euler kinematical equation", "Euler-angle rates", "H matrix", "E matrix", "body rates to Euler rates"]
tags: [sesa3047, concept, kinematics, euler-angles]
status: complete
parent_lectures: ["[[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]]"]
related_concepts: ["[[Aerospace 3-2-1 Euler Sequence]]", "[[Angular Velocity Vector]]", "[[Gimbal Lock]]", "[[Translational Kinematic Equation]]", "[[Rotational Dynamic Equation]]"]
sources: ["02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/SESA3047 - L7.txt"]
---

# Rotational Kinematic Equation

## Statement

> [!note] Definition
> For the 3-2-1 (yaw–pitch–roll) Euler angles $\boldsymbol\Phi=[\phi,\theta,\psi]^T$ and body rates $\boldsymbol\omega^{FRD}_{b/r}=[p,q,r]^T$:
>
> $$\boldsymbol\omega^{FRD}_{b/r}=\mathbf E(\boldsymbol\Phi)\dot{\boldsymbol\Phi},\qquad\mathbf E=\begin{bmatrix}1&0&-s_\theta\\0&c_\phi&s_\phi c_\theta\\0&-s_\phi&c_\phi c_\theta\end{bmatrix}\quad(3.8\text{–}3.9)$$
>
> $$\dot{\boldsymbol\Phi}=\mathbf H(\boldsymbol\Phi)\,\boldsymbol\omega^{FRD}_{b/r},\qquad\mathbf H=\mathbf E^{-1}=\begin{bmatrix}1&s_\phi t_\theta&c_\phi t_\theta\\0&c_\phi&-s_\phi\\0&s_\phi/c_\theta&c_\phi/c_\theta\end{bmatrix}\quad(3.10\text{–}3.11)$$

## Derivation in three lines

1. Each Euler rate spins about its own axis: $\boldsymbol\omega=\dot\phi\,\mathbf x_b+\dot\theta\,\mathbf y_1+\dot\psi\,\mathbf z_{NED}$.
2. Resolve each into FRD through only the rotations that come **after** it: $\boldsymbol\omega^{FRD}=[\dot\phi,0,0]^T+\mathbf C_x(\phi)\left([0,\dot\theta,0]^T+\mathbf C_y(\theta)[0,0,\dot\psi]^T\right)$.
3. Multiply out and collect $\dot\phi,\dot\theta,\dot\psi$ to get $\mathbf E$; invert ($\det\mathbf E=\cos\theta$) to get $\mathbf H$.

Full step-by-step derivation and figure: [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#3. Composing the three rotation rates (§3.1.2, L7 ll. 160–194)|3.1 §§3–6]].

## Scalar form

$$
\dot\phi=p+(q\sin\phi+r\cos\phi)\tan\theta,\qquad
\dot\theta=q\cos\phi-r\sin\phi,\qquad
\dot\psi=\frac{q\sin\phi+r\cos\phi}{\cos\theta}.
$$

## Key properties

- **Not a DCM.** $\mathbf E$ maps angle rates to vector components; its columns (the three rotation axes in FRD) are not mutually orthogonal, so $\mathbf E^{-1}\neq\mathbf E^T$.
- **Purely kinematic:** no force, moment, mass or inertia.
- **Singular at $\theta=\pm90^\circ$** ($\det\mathbf E=\cos\theta$): [[Gimbal Lock]].
- **Small angles:** $\dot\phi\approx p$, $\dot\theta\approx q$, $\dot\psi\approx r$; valid only near zero attitude.
- **Flat Earth:** $\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/i}$, so gyro readings can be used directly.

## Example

Level turn, $\phi=30^\circ$, $\dot\psi=3.25^\circ$/s: $p=0$, $q=\dot\psi\sin\phi=1.62^\circ$/s, $r=\dot\psi\cos\phi=2.81^\circ$/s. A constant heading rate shows up as a body **pitch** rate.

## Related

- [[Aerospace 3-2-1 Euler Sequence]] · [[Direction Cosine Matrix]] · [[Angular Velocity Vector]] · [[Gimbal Lock]]
- The other Chapter 3 state equations: [[Translational Kinematic Equation]] · [[Rotational Dynamic Equation]]
- Year 2: [[Euler Angles and Rotation Matrices]] (SESA2027)
