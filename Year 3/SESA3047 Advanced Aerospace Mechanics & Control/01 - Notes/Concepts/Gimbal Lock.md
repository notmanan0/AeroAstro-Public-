---
title: "Gimbal Lock"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["Euler-angle singularity", "gimbal lock", "singularity of the Euler angles", "kinematic singularity"]
tags: [sesa3047, concept, kinematics, euler-angles, singularity]
status: complete
parent_lectures: ["[[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]"]
related_concepts: ["[[Aerospace 3-2-1 Euler Sequence]]", "[[Direction Cosine Matrix]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/L6 - SESA3047.txt"]
---

# Gimbal Lock

For the aerospace 3-2-1 (yaw–pitch–roll) sequence, **gimbal lock** is the loss of one rotational degree of freedom at pitch $\theta=\pm90^\circ$. There the yaw axis (down) and the roll axis (body $x$) coincide, so the DCM depends only on $\phi-\psi$ (at $+90^\circ$) or $\phi+\psi$ (at $-90^\circ$). Roll and yaw can't be separated any more, and the extraction formulas $\phi=\mathrm{atan2}(C_{23},C_{33})$ and $\psi=\mathrm{atan2}(C_{12},C_{11})$ become $\mathrm{atan2}(0,0)$.

At $\theta=90^\circ$ the 3-2-1 matrix collapses to

$$
\mathbf C\big|_{\theta=90^\circ}=\begin{bmatrix}0&0&-1\\\sin(\phi-\psi)&\cos(\phi-\psi)&0\\\cos(\phi-\psi)&-\sin(\phi-\psi)&0\end{bmatrix},
$$

so every pair $(\phi,\psi)$ with the same difference gives the same matrix, and infinitely many angle sets describe one attitude. Full derivation: [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#8. The singularity: gimbal lock (§2.4.5)|2.2 §8]].

![[amc_gimbal_lock.png|800]]

It's a property of the representation, not of the aircraft: nothing physical goes wrong at vertical pitch, only the three-angle description fails. Every three-angle sequence has a singular attitude somewhere, so changing the sequence moves the singularity but can't remove it. The name comes from mechanical gyroscope gimbals, where at $90^\circ$ pitch two gimbal rings line up and the platform loses a free axis.

Software fails silently here: `atan2(0, 0)` returns 0 in Python, NumPy and MATLAB (L6, l. 213), and near the singularity the extracted angles are numerically noisy, so the output is unreliable rather than predictably zero. Robust code checks $|\cos\theta|$ against a tolerance, uses a documented singular branch that keeps $\phi\mp\psi$, and verifies the result by rebuilding the DCM ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#8. The singularity: gimbal lock (§2.4.5)|2.2 §8]]).

The fix is to propagate attitude with a non-singular representation, the DCM itself or quaternions (L6, l. 227), and convert to Euler angles only for display. Conventional aircraft rarely get near $|\theta|=90^\circ$, so Euler angles remain standard for them (L6, ll. 224–226).

## Related

- [[Aerospace 3-2-1 Euler Sequence]] · [[Direction Cosine Matrix]] · [[Euler Angles and Rotation Matrices]] (SESA2027)
- [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Why atan2, not arctan (the L6 question)|Why atan2 is used for extraction]]
