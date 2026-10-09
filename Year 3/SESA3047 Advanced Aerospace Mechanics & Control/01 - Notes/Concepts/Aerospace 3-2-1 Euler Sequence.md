---
title: "Aerospace 3-2-1 Euler Sequence"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["z-y-x sequence", "yaw-pitch-roll", "C_FRD/NED", "gimbal lock", "Euler angle extraction"]
tags: [sesa3047, concept, kinematics, euler-angles]
status: complete
parent_lectures: ["[[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]"]
related_concepts: ["[[Direction Cosine Matrix]]", "[[NED and FRD Coordinates]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Aerospace 3-2-1 Euler Sequence

## Definition

> [!note] Definition
> Aircraft attitude is the orientation of body FRD relative to local NED. It is built from yaw $\psi$ about $z$, then pitch $\theta$ about the new $y$, then roll $\phi$ about the new $x$:
> $$\mathbf C_{FRD/NED}=\mathbf C_x(\phi)\,\mathbf C_y(\theta)\,\mathbf C_z(\psi).$$

## The matrix

$$
\mathbf C_{FRD/NED}=
\begin{bmatrix}
c_\theta c_\psi & c_\theta s_\psi & -s_\theta\\
-c_\phi s_\psi+s_\phi s_\theta c_\psi & c_\phi c_\psi+s_\phi s_\theta s_\psi & s_\phi c_\theta\\
s_\phi s_\psi+c_\phi s_\theta c_\psi & -s_\phi c_\psi+c_\phi s_\theta s_\psi & c_\phi c_\theta
\end{bmatrix}
$$

- Row 1 is the nose direction in NED.
- Column 3 times $g$ is gravity in body axes: $g[-s_\theta,\ s_\phi c_\theta,\ c_\phi c_\theta]^T$.
- The reverse transformation is $\mathbf u^{NED}=\mathbf C^T\mathbf u^{FRD}$.

![[amc_euler_321_sequence.png|760]]

## Extraction

$$
\theta=-\arcsin C_{13},\qquad \phi=\mathrm{atan2}(C_{23},C_{33}),\qquad \psi=\mathrm{atan2}(C_{12},C_{11}),
$$

with $-\pi<\phi,\psi\le\pi$ and $-\pi/2\le\theta\le\pi/2$.

## Gimbal lock

At $\theta=\pm90^\circ$, $C_{11}=C_{12}=C_{23}=C_{33}=0$. The matrix then depends only on $\phi\mp\psi$, so yaw and roll act about the same line and cannot be separated. Use quaternions for vehicles that approach vertical.

## Example

$\psi=30^\circ$, $\phi=\theta=0$: north $[1,0,0]^T_{NED}$ becomes $[0.866,-0.500,0]^T_{FRD}$, i.e. north lies ahead-left of the aircraft.

## Related

- [[Direction Cosine Matrix]] · [[NED and FRD Coordinates]] · [[Euler Angles and Rotation Matrices]] (SESA2027) · [[Angular Velocity Vector]]
