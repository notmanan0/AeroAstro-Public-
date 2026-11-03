---
title: "Aerospace 3-2-1 Euler Sequence"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["z-y-x sequence", "yaw-pitch-roll", "C_FRD/NED", "gimbal lock", "Euler angle extraction", "Tait-Bryan angles", "Cardan angles", "intrinsic ZYX sequence", "roll pitch yaw angles", "bank angle"]
tags: [sesa3047, concept, kinematics, euler-angles]
status: complete
parent_lectures: ["[[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]"]
related_concepts: ["[[Direction Cosine Matrix]]", "[[NED and FRD Coordinates]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Aerospace 3-2-1 Euler Sequence

Aircraft attitude is the orientation of body FRD relative to local NED. The aerospace convention builds it from three rotations in order: yaw $\psi$ about $z$, then pitch $\theta$ about the new $y$, then roll $\phi$ about the new $x$:

$$\mathbf C_{FRD/NED}=\mathbf C_x(\phi)\,\mathbf C_y(\theta)\,\mathbf C_z(\psi).$$

Multiplied out,

$$
\mathbf C_{FRD/NED}=
\begin{bmatrix}
c_\theta c_\psi & c_\theta s_\psi & -s_\theta\\
-c_\phi s_\psi+s_\phi s_\theta c_\psi & c_\phi c_\psi+s_\phi s_\theta s_\psi & s_\phi c_\theta\\
s_\phi s_\psi+c_\phi s_\theta c_\psi & -s_\phi c_\psi+c_\phi s_\theta s_\psi & c_\phi c_\theta
\end{bmatrix}.
$$

Two parts of it are worth recognising. Row 1 is the nose direction in NED, and column 3 times $g$ is gravity in body axes, $g[-s_\theta,\ s_\phi c_\theta,\ c_\phi c_\theta]^T$. Going the other way, $\mathbf u^{NED}=\mathbf C^T\mathbf u^{FRD}$. For example, with $\psi=30^\circ$ and $\phi=\theta=0$, north, $\mathbf u^{NED}=[1,0,0]^T$, becomes $\mathbf u^{FRD}=[0.866,-0.500,0]^T$: north lies ahead and to the left.

![[amc_euler_321_sequence.png|760]]

The angles can be recovered from the matrix as

$$
\theta=-\arcsin C_{13},\qquad \phi=\mathrm{atan2}(C_{23},C_{33}),\qquad \psi=\mathrm{atan2}(C_{12},C_{11}),
$$

with $-\pi<\phi,\psi\le\pi$ and $-\pi/2\le\theta\le\pi/2$.

At $\theta=\pm90^\circ$ this breaks down. $C_{11}$, $C_{12}$, $C_{23}$ and $C_{33}$ are all zero, the matrix depends only on $\phi\mp\psi$, and yaw and roll act about the same line and can't be separated. The handout calls this the Euler-angle singularity ([[Gimbal Lock]]); vehicles that approach vertical use quaternions instead.

The course calls all such angle sets Euler angles and the angles roll, pitch and yaw. Textbooks call three-different-axis sets Tait–Bryan or Cardan angles, and pilots call $\phi$ the bank angle. MATLAB's `angle2dcm(psi, theta, phi, 'ZYX')` returns $\mathbf C_{FRD/NED}$, while `eul2rotm` and SciPy's `from_euler('ZYX', ...)` return its transpose. The full list is in [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Terminology and alternative names|2.2, terminology]].

## Related

- [[Direction Cosine Matrix]] · [[NED and FRD Coordinates]] · [[Euler Angles and Rotation Matrices]] (SESA2027) · [[Angular Velocity Vector]]
