---
title: "Inertia Matrix"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["inertia tensor", "moments of inertia", "products of inertia", "principal axes"]
tags: [sesa2024, concept, attitude-control]
status: lectured
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Momentum Bias and Gyroscopic Rigidity]]", "[[Spacecraft Stabilisation Types]]"]
sources: ["02 - Sources/Lectures/Chapter 6/Chapter 6 - Attitude Control - prerecorded material.pdf", "Fortescue, Stark and Swinerd, Spacecraft Systems Engineering, Ch. 9"]
---

# Inertia Matrix

The inertia matrix $[\mathbf I]$ relates a rigid body's angular velocity to its angular momentum, $\mathbf H=[\mathbf I]\boldsymbol\omega$, and so describes how the body's mass is distributed about its centre of mass.

$$
[\mathbf I]=\begin{bmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{bmatrix},
\qquad I_{xx}=\int(y^2+z^2)\,dm,\quad I_{xy}=\int xy\,dm.
$$

The diagonal terms, the moments of inertia, are the body's resistance to angular acceleration about each axis; they play the part that mass plays in $\mathbf p=m\mathbf v$. The off-diagonal products of inertia measure imbalance and cause cross-coupling: a torque or spin about one axis produces rotation about the others, as a drum with a small mass stuck to its rim starts to wobble. Because a matrix can rotate a vector, $\mathbf H$ is not in general parallel to $\boldsymbol\omega$; it is when the body spins about a principal axis, along which the products of inertia vanish.

The matrix sizes the torquers, sets the response to every control and disturbance torque, and decides whether a design can be spin-stabilised. A spinner needs zero products of inertia, its maximum moment about the spin axis, and equal transverse moments. A matrix with large products of inertia, like the one in 2024/25 A4, belongs to a three-axis-stabilised spacecraft. The principal moments are the eigenvalues of $[\mathbf I]$.

## Related

- [[SESA2024 06 - Attitude Control#The inertia matrix|Inertia matrix in the lecture note]] · [[SESA2024 06 - Attitude Control#Inertia matrix from the 2024/25 paper|2024/25 A4 example]]
- [[Momentum Bias and Gyroscopic Rigidity]] · [[Spacecraft Stabilisation Types]]
