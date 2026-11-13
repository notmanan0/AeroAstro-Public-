---
title: "SESA3047 Deep Dive - Euler-Angle Rates and Gimbal Lock"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: topic
stream: "Chapter 3: Kinematic Equations and Introduction to Dynamics"
order: 5.5
tags: [sesa3047, deep-dive, derivation, kinematics, euler-angles, euler-rates, gimbal-lock, singularity]
aliases: ["Euler-angle rates deep dive", "Gimbal lock deep dive", "Rotational kinematic equation derivation", "Euler kinematical equation in full"]
date: 2026-11-12
status: lectured
coverage: "Every step from the three elemental rotation rates of the aerospace 3-2-1 sequence to ω = E Φ̇ and Φ̇ = H ω (Ch. 3 §§3.1.2–3.1.3, Eqs. 3.5–3.11, Appendix §3.4.1; L7), a second derivation from the DCM rate, the singularity at θ = ±90° from det E, its null space and missing axis, the gain of H, and a numerical pull-up past the vertical; gimbal lock as in Ch. 2 §2.4.5 (L6 ll. 211–227)"
parent: ["[[SESA3047 Advanced Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]", "[[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]", "[[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]]"]
next_topics: ["[[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]"]
key_concepts: ["[[Rotational Kinematic Equation]]", "[[Gimbal Lock]]", "[[Aerospace 3-2-1 Euler Sequence]]", "[[Angular Velocity Vector]]", "[[Direction Cosine Matrix]]"]
tutorial_sheets: ["[[SESA3047 Mock Questions - Chapters 1-4]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/L6 - SESA3047.txt", "02 - Sources/Lectures/SESA3047 - L7.txt", "02 - Sources/Lectures/L8 - SESA3047.txt"]
---

# SESA3047 Deep Dive - Euler-Angle Rates and Gimbal Lock

> [!abstract] Summary
> For the aerospace 3-2-1 sequence the body angular velocity is the sum of the three elemental rotation rates, each resolved into FRD through only the rotations that follow it, which gives $\boldsymbol\omega^{FRD}=\mathbf E(\boldsymbol\Phi)\dot{\boldsymbol\Phi}$ with $\mathbf E=\mathbf C_x(\phi)\,\mathbf E_\theta$ and $\det\mathbf E=\cos\theta$. Inverting by cofactors gives the rotational kinematic equation $\dot{\boldsymbol\Phi}=\mathbf H(\boldsymbol\Phi)\boldsymbol\omega$, whose largest gain is $1/\sqrt{1-|\sin\theta|}$. At $\theta=\pm90^\circ$ the roll and yaw axes lie on one line, a body rotation about the horizontal axis $x_1$ cannot be produced by any Euler rates, and equal (or opposite) roll and yaw rates produce no rotation at all: this is gimbal lock, a failure of the description and not of the motion.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for $\mathbf E$ or $\mathbf H$, for Euler rates from gyro rates, or why the Euler-angle model fails at vertical pitch.
> - **Assumptions:** 3-2-1 (yaw–pitch–roll) sequence from NED to FRD; flat Earth, so gyro rates are $\boldsymbol\omega_{b/r}$; angles in radians inside the calculus; $\cos\theta\neq0$ for $\mathbf H$.
> - **Method:** 1. $\boldsymbol\omega=\dot\phi\,\mathbf e_1+\mathbf C_x(\phi)\left(\dot\theta\,\mathbf e_2+\mathbf C_y(\theta)\dot\psi\,\mathbf e_3\right)$. 2. Read the columns of $\mathbf E$: $[1,0,0]^T$, $[0,c_\phi,-s_\phi]^T$, $[-s_\theta,s_\phi c_\theta,c_\phi c_\theta]^T$. 3. $\det\mathbf E=\cos\theta$ by column 1. 4. $\mathbf H=\operatorname{adj}\mathbf E/\cos\theta$ (or $\mathbf E_\theta^{-1}\mathbf C_x^T$). 5. Near $\theta=\pm90^\circ$: rates blow up only if $q\sin\phi+r\cos\phi\neq0$.
> - **Common mistakes:** transforming every Euler rate through the whole DCM instead of only the later rotations; claiming the aircraft or its gyros fail at $90^\circ$, when only the angle description does.
> - **Practise:** [[#4. Inverting E by cofactors (3.10–3.11)|H by cofactors]] · [[SESA3047 Mock Questions - Chapters 1-4#Q6. Euler-angle rates from gyro rates|Mock Q6]]

The Euler angles of the 3-2-1 sequence work like the controls of a three-ring gimbal. The outer ring turns about the local vertical (yaw $\psi$), the middle ring about a horizontal axis carried by the outer ring (pitch $\theta$), and the inner ring about the body's nose (roll $\phi$). An angular velocity of the body has to be produced by spinning the three rings, so each Euler-angle rate is a spin about its own ring's axis, and the three axes are generally not perpendicular. That is why $\dot\phi,\dot\theta,\dot\psi$ are not the body rates $p,q,r$, and why converting between them needs a matrix that depends on the attitude.

When the nose points straight up, the inner ring's axis (the nose) lines up with the outer ring's axis (the vertical). Two rings now turn the body about the same line and none can turn it about the horizontal axis perpendicular to the middle ring. A body rotation in that direction can only be followed by spinning the outer and inner rings infinitely fast in opposite senses. Physically nothing happens to the aircraft; the three-angle description has run out of independent axes.

The same picture holds for the nose direction alone. $\theta$ and $\psi$ are the elevation and azimuth of the nose, exactly like latitude and longitude on a globe. Near the pole a small step changes the longitude by a large amount, and at the pole the longitude is undefined. The peak yaw-angle rate of a pull-up past the vertical follows from this geometry alone, to within 0.1 % (§7).

The lectured derivation is in [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates|3.1]] and the DCM side of gimbal lock in [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#8. The singularity: gimbal lock|2.2 §8]]. The same $\mathbf E$ also follows from the DCM rate, its inverse follows from cofactors, and its columns, null space and singular values each give a different view of the singularity.

## 1. The 3-2-1 sequence and its frames (2.4, 3.1)

The transformation from NED to FRD is three elementary rotations, applied right to left (Eq. 3.2; [[Aerospace 3-2-1 Euler Sequence]]):

$$
\mathbf C_{FRD/NED}=\mathbf C_x(\phi)\,\mathbf C_y(\theta)\,\mathbf C_z(\psi).
$$

Each one defines an intermediate frame. Yaw by $\psi$ about $z_{NED}$ takes NED to frame 1; pitch by $\theta$ about $y_1$ takes frame 1 to frame 2; roll by $\phi$ about $x_2$ takes frame 2 to FRD. The elementary matrices (Eqs. 2.35–2.37 and 3.6) are

$$
\mathbf C_z(\psi)=\begin{bmatrix}c_\psi&s_\psi&0\\-s_\psi&c_\psi&0\\0&0&1\end{bmatrix},\qquad
\mathbf C_y(\theta)=\begin{bmatrix}c_\theta&0&-s_\theta\\0&1&0\\s_\theta&0&c_\theta\end{bmatrix},\qquad
\mathbf C_x(\phi)=\begin{bmatrix}1&0&0\\0&c_\phi&s_\phi\\0&-s_\phi&c_\phi\end{bmatrix},
$$

with $c_\alpha=\cos\alpha$ and $s_\alpha=\sin\alpha$. Each leaves its own rotation axis unchanged: $\mathbf C_z\mathbf e_3=\mathbf e_3$, $\mathbf C_y\mathbf e_2=\mathbf e_2$ and $\mathbf C_x\mathbf e_1=\mathbf e_1$, where $\mathbf e_1,\mathbf e_2,\mathbf e_3$ are the columns of the identity. Every angle in the derivatives below is in radians.

The body rates $\boldsymbol\omega^{FRD}_{b/r}=[p,q,r]^T$ are the FRD components of one vector, the angular velocity of the body relative to the local NED frame (Eq. 3.1). On a flat Earth this equals the inertial angular velocity that gyros measure ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#9. Flat-Earth interpretation|3.1 §9]]). The Euler-angle rates $\dot{\boldsymbol\Phi}=[\dot\phi,\dot\theta,\dot\psi]^T$ are a column of three numbers, not the components of any vector (Chapter 3, p. 2).

## 2. Adding the three elemental rotation rates (3.5–3.9)

Angular velocities of successive frames add ([[Angular Velocity Vector]], from the transport theorem of [[SESA3047 2.1 - Vector Operations and the Transport Theorem|2.1]]):

$$
\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/2}+\boldsymbol\omega_{2/1}+\boldsymbol\omega_{1/r}.
$$

Each term is a single-axis rotation at the rate of one angle: frame 1 turns relative to NED at $\dot\psi$ about $z_{NED}=z_1$, frame 2 relative to frame 1 at $\dot\theta$ about $y_1=y_2$, and the body relative to frame 2 at $\dot\phi$ about $x_2=x_b$. So

$$
\boldsymbol\omega_{b/r}=\dot\phi\,\mathbf x_b+\dot\theta\,\mathbf y_1+\dot\psi\,\mathbf z_{NED}.
$$

To add them, all three are needed in FRD components. Each is simplest in the frame where its axis is a coordinate axis, and from there it has to pass through the rotations that come after it in the sequence and no others:

- the roll rate is about $x_b$, already an FRD axis: $\dot\phi\,\mathbf e_1$;
- the pitch rate is about $y_2$, which is $\mathbf e_2$ in frame-2 components; only the roll rotation lies between frame 2 and FRD: $\mathbf C_x(\phi)\,\dot\theta\,\mathbf e_2$;
- the yaw rate is about $z_1$, which is $\mathbf e_3$ in frame-1 components; pitch and then roll lie between frame 1 and FRD: $\mathbf C_x(\phi)\,\mathbf C_y(\theta)\,\dot\psi\,\mathbf e_3$.

Collecting, with the common $\mathbf C_x(\phi)$ factored out, gives Eq. 3.5:

$$
\boldsymbol\omega^{FRD}_{b/r}=\dot\phi\,\mathbf e_1+\mathbf C_x(\phi)\left(\dot\theta\,\mathbf e_2+\mathbf C_y(\theta)\,\dot\psi\,\mathbf e_3\right).
$$

Since $\dot\phi,\dot\theta,\dot\psi$ are scalars, this is $\mathbf E\dot{\boldsymbol\Phi}$ with the three axis vectors as the columns of $\mathbf E$:

$$
\mathbf E=\Big[\ \mathbf e_1\ \ \Big|\ \ \mathbf C_x(\phi)\,\mathbf e_2\ \ \Big|\ \ \mathbf C_x(\phi)\mathbf C_y(\theta)\,\mathbf e_3\ \Big].
$$

The second column is column 2 of $\mathbf C_x$:

$$
\mathbf C_x(\phi)\,\mathbf e_2=\begin{bmatrix}0\\c_\phi\\-s_\phi\end{bmatrix}.
$$

For the third, first take column 3 of $\mathbf C_y$:

$$
\mathbf C_y(\theta)\,\mathbf e_3=\begin{bmatrix}-s_\theta\\0\\c_\theta\end{bmatrix}.
$$

Then multiply by $\mathbf C_x$. Row 1 of $\mathbf C_x$ copies the first entry; rows 2 and 3 combine the second and third:

$$
\mathbf C_x(\phi)\begin{bmatrix}-s_\theta\\0\\c_\theta\end{bmatrix}=\begin{bmatrix}-s_\theta\\c_\phi\cdot0+s_\phi c_\theta\\-s_\phi\cdot0+c_\phi c_\theta\end{bmatrix}=\begin{bmatrix}-s_\theta\\s_\phi c_\theta\\c_\phi c_\theta\end{bmatrix}.
$$

So (Eqs. 3.7–3.9)

$$
\boxed{\begin{bmatrix}p\\q\\r\end{bmatrix}=\underbrace{\begin{bmatrix}1&0&-s_\theta\\0&c_\phi&s_\phi c_\theta\\0&-s_\phi&c_\phi c_\theta\end{bmatrix}}_{\mathbf E(\boldsymbol\Phi)}\begin{bmatrix}\dot\phi\\\dot\theta\\\dot\psi\end{bmatrix}.}
$$

Column $k$ of $\mathbf E$ is the unit vector of the $k$-th rotation axis written in FRD: the nose, the pitch axis $y_1$ tilted by the roll angle, and the local vertical seen from the body (which is also the direction of gravity in body axes). $\mathbf E$ does not depend on $\psi$, because yawing about the vertical does not change how the vertical or the later axes look from the body.

![[amc_dd_euler_rate_axes_singular.png|900]]

### E factorises into a roll and a pitch part

Because $\mathbf C_x(\phi)\,\mathbf e_1=\mathbf e_1$, the first column can also be written $\mathbf C_x(\phi)\,\mathbf e_1$, and then $\mathbf C_x(\phi)$ comes out of all three columns:

$$
\mathbf E=\mathbf C_x(\phi)\Big[\ \mathbf e_1\ \Big|\ \mathbf e_2\ \Big|\ \mathbf C_y(\theta)\,\mathbf e_3\ \Big]=\mathbf C_x(\phi)\,\mathbf E_\theta,\qquad
\mathbf E_\theta=\begin{bmatrix}1&0&-s_\theta\\0&1&0\\0&0&c_\theta\end{bmatrix}.
$$

$\mathbf E_\theta$ is $\mathbf E$ written in frame-2 components, before the roll is applied. The roll angle only rotates the result, so everything about the conditioning of $\mathbf E$ (its determinant, its singular values, where it fails) depends on $\theta$ alone.

## 3. The same E from the DCM rate

A second derivation needs no picture of rotating axes. The DCM obeys $\dot{\mathbf C}=-\tilde{\boldsymbol\omega}\mathbf C$, from the transport theorem ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#11. Preview: how the DCM evolves in time|2.2 §11]]; $\tilde{\boldsymbol\omega}$ is the [[Cross-Product Matrix]] of $\boldsymbol\omega^{FRD}_{b/r}$). Multiply on the right by $\mathbf C^T$ and use $\mathbf C\mathbf C^T=\mathbf I$:

$$
\tilde{\boldsymbol\omega}=-\dot{\mathbf C}\,\mathbf C^T .
$$

Differentiate $\mathbf C=\mathbf C_x\mathbf C_y\mathbf C_z$ by the product rule:

$$
\dot{\mathbf C}=\dot{\mathbf C}_x\mathbf C_y\mathbf C_z+\mathbf C_x\dot{\mathbf C}_y\mathbf C_z+\mathbf C_x\mathbf C_y\dot{\mathbf C}_z .
$$

Multiply on the right by $\mathbf C^T=\mathbf C_z^T\mathbf C_y^T\mathbf C_x^T$ and cancel each $\mathbf C_i\mathbf C_i^T=\mathbf I$ that appears next to itself:

$$
-\dot{\mathbf C}\,\mathbf C^T=-\dot{\mathbf C}_x\mathbf C_x^T-\mathbf C_x\left(\dot{\mathbf C}_y\mathbf C_y^T\right)\mathbf C_x^T-\mathbf C_x\mathbf C_y\left(\dot{\mathbf C}_z\mathbf C_z^T\right)\mathbf C_y^T\mathbf C_x^T .
$$

Each bracket is the rate of one elementary rotation. For the roll matrix, differentiate entry by entry with the chain rule:

$$
\dot{\mathbf C}_x=\dot\phi\begin{bmatrix}0&0&0\\0&-s_\phi&c_\phi\\0&-c_\phi&-s_\phi\end{bmatrix}.
$$

Multiply by $\mathbf C_x^T$:

$$
\dot{\mathbf C}_x\mathbf C_x^T=\dot\phi\begin{bmatrix}0&0&0\\0&-s_\phi&c_\phi\\0&-c_\phi&-s_\phi\end{bmatrix}\begin{bmatrix}1&0&0\\0&c_\phi&-s_\phi\\0&s_\phi&c_\phi\end{bmatrix}=\dot\phi\begin{bmatrix}0&0&0\\0&-s_\phi c_\phi+c_\phi s_\phi&s_\phi^2+c_\phi^2\\0&-c_\phi^2-s_\phi^2&c_\phi s_\phi-s_\phi c_\phi\end{bmatrix}.
$$

Simplify with $s_\phi^2+c_\phi^2=1$:

$$
\dot{\mathbf C}_x\mathbf C_x^T=\dot\phi\begin{bmatrix}0&0&0\\0&0&1\\0&-1&0\end{bmatrix}=-\dot\phi\,\tilde{\mathbf e}_1,
$$

since the cross-product matrix of $\mathbf e_1$ is $\tilde{\mathbf e}_1=\begin{bmatrix}0&0&0\\0&0&-1\\0&1&0\end{bmatrix}$. The same steps for $\mathbf C_y$ and $\mathbf C_z$ give $\dot{\mathbf C}_y\mathbf C_y^T=-\dot\theta\,\tilde{\mathbf e}_2$ and $\dot{\mathbf C}_z\mathbf C_z^T=-\dot\psi\,\tilde{\mathbf e}_3$: each elementary rotation spins about its own axis at its own rate. Substituting,

$$
\tilde{\boldsymbol\omega}=\dot\phi\,\tilde{\mathbf e}_1+\mathbf C_x\left(\dot\theta\,\tilde{\mathbf e}_2\right)\mathbf C_x^T+\mathbf C_x\mathbf C_y\left(\dot\psi\,\tilde{\mathbf e}_3\right)\mathbf C_y^T\mathbf C_x^T .
$$

The last step needs one identity. For a rotation matrix $\mathbf R$ ($\mathbf R\mathbf R^T=\mathbf I$, $\det\mathbf R=+1$), rotation preserves cross products, $\mathbf R(\mathbf x\times\mathbf y)=(\mathbf R\mathbf x)\times(\mathbf R\mathbf y)$. So for any vector $\mathbf b$,

$$
\mathbf R\,\tilde{\mathbf a}\,\mathbf R^T\mathbf b=\mathbf R\left(\mathbf a\times\mathbf R^T\mathbf b\right)=(\mathbf R\mathbf a)\times\left(\mathbf R\mathbf R^T\mathbf b\right)=(\mathbf R\mathbf a)\times\mathbf b,
$$

that is, $\mathbf R\,\tilde{\mathbf a}\,\mathbf R^T=\widetilde{\mathbf R\mathbf a}$. Apply it with $\mathbf R=\mathbf C_x$ and $\mathbf R=\mathbf C_x\mathbf C_y$:

$$
\tilde{\boldsymbol\omega}=\left(\dot\phi\,\mathbf e_1+\dot\theta\,\mathbf C_x\mathbf e_2+\dot\psi\,\mathbf C_x\mathbf C_y\mathbf e_3\right)^{\sim}.
$$

Two vectors with the same cross-product matrix are equal, so this is Eq. 3.5 again. The two routes agree because "angular velocities add" and "$\dot{\mathbf C}=-\tilde{\boldsymbol\omega}\mathbf C$" are the same transport-theorem statement (both checked in SymPy).

## 4. Inverting E by cofactors (3.10–3.11)

Gyros give $p,q,r$; integrating the attitude needs $\dot\phi,\dot\theta,\dot\psi$, so $\mathbf E$ has to be inverted. [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#6. Inverting: the rotational kinematic equation|3.1 §6]] solves the three scalar equations by elimination; the general route is the adjugate, $\mathbf E^{-1}=\operatorname{adj}\mathbf E/\det\mathbf E$.

### The determinant

Expand along column 1, which has a single non-zero entry:

$$
\det\mathbf E=1\cdot\begin{vmatrix}c_\phi&s_\phi c_\theta\\-s_\phi&c_\phi c_\theta\end{vmatrix}.
$$

$$
\det\mathbf E=c_\phi\cdot c_\phi c_\theta-s_\phi c_\theta\cdot(-s_\phi).
$$

$$
\det\mathbf E=c_\theta\left(c_\phi^2+s_\phi^2\right)=\cos\theta .
$$

The factorisation gives the same in one line: $\det\mathbf E=\det\mathbf C_x\cdot\det\mathbf E_\theta=1\cdot c_\theta$, since $\mathbf E_\theta$ is upper triangular.

### The cofactors

The cofactor $C_{ij}$ is $(-1)^{i+j}$ times the determinant left after deleting row $i$ and column $j$. Row 1:

$$
C_{11}=+\begin{vmatrix}c_\phi&s_\phi c_\theta\\-s_\phi&c_\phi c_\theta\end{vmatrix}=c_\theta,\qquad
C_{12}=-\begin{vmatrix}0&s_\phi c_\theta\\0&c_\phi c_\theta\end{vmatrix}=0,\qquad
C_{13}=+\begin{vmatrix}0&c_\phi\\0&-s_\phi\end{vmatrix}=0 .
$$

Row 2:

$$
C_{21}=-\begin{vmatrix}0&-s_\theta\\-s_\phi&c_\phi c_\theta\end{vmatrix}=-\left(0-s_\theta s_\phi\right)=s_\phi s_\theta,
$$

$$
C_{22}=+\begin{vmatrix}1&-s_\theta\\0&c_\phi c_\theta\end{vmatrix}=c_\phi c_\theta,\qquad
C_{23}=-\begin{vmatrix}1&0\\0&-s_\phi\end{vmatrix}=s_\phi .
$$

Row 3:

$$
C_{31}=+\begin{vmatrix}0&-s_\theta\\c_\phi&s_\phi c_\theta\end{vmatrix}=0+s_\theta c_\phi=c_\phi s_\theta,
$$

$$
C_{32}=-\begin{vmatrix}1&-s_\theta\\0&s_\phi c_\theta\end{vmatrix}=-s_\phi c_\theta,\qquad
C_{33}=+\begin{vmatrix}1&0\\0&c_\phi\end{vmatrix}=c_\phi .
$$

The adjugate is the transpose of the cofactor matrix:

$$
\operatorname{adj}\mathbf E=\begin{bmatrix}c_\theta&s_\phi s_\theta&c_\phi s_\theta\\0&c_\phi c_\theta&-s_\phi c_\theta\\0&s_\phi&c_\phi\end{bmatrix}.
$$

Divide every entry by $\det\mathbf E=c_\theta$, writing $s_\theta/c_\theta=\tan\theta$:

$$
\boxed{\begin{bmatrix}\dot\phi\\\dot\theta\\\dot\psi\end{bmatrix}=\underbrace{\begin{bmatrix}1&s_\phi\tan\theta&c_\phi\tan\theta\\0&c_\phi&-s_\phi\\0&s_\phi/c_\theta&c_\phi/c_\theta\end{bmatrix}}_{\mathbf H(\boldsymbol\Phi)}\begin{bmatrix}p\\q\\r\end{bmatrix}.}
$$

This is the rotational kinematic equation, Eqs. 3.10–3.11 ([[Rotational Kinematic Equation]]). In scalar form (Eqs. 3.12–3.14),

$$
\dot\phi=p+(q\sin\phi+r\cos\phi)\tan\theta,\qquad\dot\theta=q\cos\phi-r\sin\phi,\qquad\dot\psi=\frac{q\sin\phi+r\cos\phi}{\cos\theta}.
$$

> [!check] H from the factorisation
> $\mathbf H=(\mathbf C_x\mathbf E_\theta)^{-1}=\mathbf E_\theta^{-1}\mathbf C_x^T$, and $\mathbf E_\theta^{-1}=\begin{bmatrix}1&0&\tan\theta\\0&1&0\\0&0&1/c_\theta\end{bmatrix}$ (check row 1 against column 3 of $\mathbf E_\theta$: $-s_\theta+\tan\theta\,c_\theta=0$). Row 1 of $\mathbf E_\theta^{-1}$ times $\mathbf C_x^T=\begin{bmatrix}1&0&0\\0&c_\phi&-s_\phi\\0&s_\phi&c_\phi\end{bmatrix}$ is $[1,\ s_\phi\tan\theta,\ c_\phi\tan\theta]$, row 2 is $[0,\ c_\phi,\ -s_\phi]$ and row 3 is $[0,\ s_\phi/c_\theta,\ c_\phi/c_\theta]$: the same $\mathbf H$. SymPy confirms $\mathbf H\mathbf E=\mathbf I$.

Both $\dot\phi$ and $\dot\psi$ depend on the body rates only through the combination $q\sin\phi+r\cos\phi$ (besides $p$). That combination has a geometric meaning, found in §5, and it is what decides whether the rates blow up.

## 5. The singularity at θ = ±90°

### What the determinant says

$\det\mathbf E=\cos\theta$ is zero at $\theta=\pm90^\circ$ and nowhere else. There $\mathbf E$ has rank 2 (checked symbolically), so it maps the three Euler rates onto a plane of angular velocities only, and $\mathbf H$, which divides by $\cos\theta$, does not exist. Every entry of $\mathbf H$ with $\tan\theta$ or $1/\cos\theta$ grows without bound as the pitch approaches the vertical.

### The columns: two axes on one line

At $\theta=+90^\circ$, $s_\theta=1$ and $c_\theta=0$, so

$$
\mathbf E\big|_{\theta=90^\circ}=\begin{bmatrix}1&0&-1\\0&c_\phi&0\\0&-s_\phi&0\end{bmatrix}.
$$

Column 3 (the vertical seen from the body) is $-1$ times column 1 (the nose): with the nose pointing straight up, the yaw axis and the roll axis are the same line. The three gimbal axes span only the plane of $\mathbf x_b$ and $\mathbf y_1=[0,c_\phi,-s_\phi]^T$. The direction perpendicular to that plane is

$$
\mathbf n=\mathbf e_1\times\begin{bmatrix}0\\c_\phi\\-s_\phi\end{bmatrix}=\begin{bmatrix}0\cdot(-s_\phi)-0\cdot c_\phi\\0\cdot0-1\cdot(-s_\phi)\\1\cdot c_\phi-0\cdot0\end{bmatrix}=\begin{bmatrix}0\\s_\phi\\c_\phi\end{bmatrix}.
$$

This is the FRD form of $\mathbf x_1$, the horizontal axis along the heading: $\mathbf C_x\mathbf C_y\mathbf e_1=\mathbf C_x[c_\theta,0,s_\theta]^T$, which at $\theta=90^\circ$ is $\mathbf C_x\mathbf e_3=[0,s_\phi,c_\phi]^T$. The body-rate component along it is

$$
\boldsymbol\omega\cdot\mathbf n=q\sin\phi+r\cos\phi,
$$

exactly the combination in the numerators of $\dot\phi$ and $\dot\psi$. A body rotation about $\mathbf x_1$ tips a vertical nose towards one wing. No finite Euler rates can produce it: following it requires the heading, which is undefined for a vertical nose, to jump. That is why $\dot\phi$ and $\dot\psi$ diverge as $\cos\theta\to0$ when, and only when, $q\sin\phi+r\cos\phi\neq0$. A pure pull-up with wings level ($\phi=0$, $r=0$) has $\boldsymbol\omega\cdot\mathbf n=0$ and passes through the vertical with finite rates ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#8. The singularity at θ = ±90° (extension)|3.1 §8]]).

### The null space: rotations that do nothing

A rank-2 matrix also has a direction it sends to zero. At $\theta=+90^\circ$, $\mathbf E\dot{\boldsymbol\Phi}=\mathbf 0$ reads

$$
\dot\phi-\dot\psi=0,\qquad c_\phi\,\dot\theta=0,\qquad-s_\phi\,\dot\theta=0,
$$

so $\dot\theta=0$ and $\dot\phi=\dot\psi$: the null space is spanned by $[1,0,1]^T$. Equal roll and yaw rates turn the body by equal amounts in opposite senses about the same vertical line, and the attitude does not change. This is the rate form of the DCM result of [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#8. The singularity: gimbal lock|2.2 §8]]: at $\theta=90^\circ$ the matrix depends only on $\phi-\psi$, so changing $\phi$ and $\psi$ together leaves it unchanged. At $\theta=-90^\circ$ row 1 becomes $\dot\phi+\dot\psi=0$, the null space is $[-1,0,1]^T$, and the DCM depends only on $\phi+\psi$. Only one combination of the two angles is identifiable at vertical pitch (Chapter 2, §2.4.5).

### The divergence lies along the null direction

Near $\theta=+90^\circ$ the large parts of $\dot\phi$ and $\dot\psi$ cancel in their difference. Write $N=q\sin\phi+r\cos\phi$:

$$
\dot\phi-\dot\psi=p+N\tan\theta-\frac{N}{\cos\theta}.
$$

Combine the two $N$ terms over $\cos\theta$:

$$
\dot\phi-\dot\psi=p+N\,\frac{\sin\theta-1}{\cos\theta}.
$$

Multiply the fraction top and bottom by $1+\sin\theta$ and use $(\sin\theta-1)(1+\sin\theta)=\sin^2\theta-1=-\cos^2\theta$:

$$
\dot\phi-\dot\psi=p-N\,\frac{\cos\theta}{1+\sin\theta}.
$$

This is finite at $\theta=90^\circ$, where it equals $p$. So as the nose approaches the vertical, $\dot\phi$ and $\dot\psi$ both grow like $N/\cos\theta$ but in step, along the null direction $[1,0,1]^T$ that changes nothing physical, while the identifiable combination $\phi-\psi$ changes at the finite rate $p$. The same steps at $\theta\to-90^\circ$ show $\dot\phi+\dot\psi$ stays finite.

## 6. How large the gain gets

The factorisation of §2 gives the worst-case amplification of $\mathbf H$ in closed form. With $\mathbf H=\mathbf E_\theta^{-1}\mathbf C_x^T$,

$$
\mathbf H\mathbf H^T=\mathbf E_\theta^{-1}\mathbf C_x^T\mathbf C_x\mathbf E_\theta^{-T}=\mathbf E_\theta^{-1}\mathbf E_\theta^{-T},
$$

so the roll angle drops out. Multiply out:

$$
\mathbf E_\theta^{-1}\mathbf E_\theta^{-T}=\begin{bmatrix}1&0&\tan\theta\\0&1&0\\0&0&1/c_\theta\end{bmatrix}\begin{bmatrix}1&0&0\\0&1&0\\\tan\theta&0&1/c_\theta\end{bmatrix}=\begin{bmatrix}1+\tan^2\theta&0&\tan\theta/c_\theta\\0&1&0\\\tan\theta/c_\theta&0&1/c_\theta^2\end{bmatrix}.
$$

Use $1+\tan^2\theta=1/c_\theta^2$ and $\tan\theta/c_\theta=s_\theta/c_\theta^2$:

$$
\mathbf H\mathbf H^T=\frac{1}{c_\theta^2}\begin{bmatrix}1&0&s_\theta\\0&c_\theta^2&0\\s_\theta&0&1\end{bmatrix}.
$$

One eigenvalue is 1 (the $\dot\theta$ direction). The other two come from the $\begin{bmatrix}1&s_\theta\\s_\theta&1\end{bmatrix}$ block, whose eigenvalues are $1\pm s_\theta$:

$$
\mu_\pm=\frac{1\pm\sin\theta}{\cos^2\theta}=\frac{1\pm\sin\theta}{(1-\sin\theta)(1+\sin\theta)} .
$$

So $\mu_+=1/(1-\sin\theta)$ and $\mu_-=1/(1+\sin\theta)$. The singular values of $\mathbf H$ are their square roots, and for $\theta$ of either sign the largest is

$$
\boxed{\sigma_{max}(\mathbf H)=\frac{1}{\sqrt{1-|\sin\theta|}}.}
$$

Its eigenvector in the $(\dot\phi,\dot\psi)$ plane is $[1,1]/\sqrt2$ for $\theta>0$, the null direction of §5 again. Close to the vertical write $\delta=90^\circ-\theta$ in radians: $1-\sin\theta=1-\cos\delta\approx\delta^2/2$, so $\sigma_{max}\approx\sqrt2/\delta$, while $1/\cos\theta=1/\sin\delta\approx1/\delta$. Halving the distance to the vertical doubles the gain.

![[amc_dd_euler_rate_gain.png|900]]

For a pure body yaw rate $r=0.1$ rad/s with wings level ($\phi=0$, $p=q=0$), $\dot\psi=r/\cos\theta$ and $\dot\phi=r\tan\theta$:

| $\theta$ | $\dot\psi$ (rad/s) | $\dot\phi$ (rad/s) | $\dot\phi-\dot\psi$ (rad/s) | $\sigma_{max}(\mathbf H)$ |
|---|---|---|---|---|
| $0^\circ$ | 0.100 | 0 | $-0.100$ | 1.00 |
| $60^\circ$ | 0.200 | 0.173 | $-0.027$ | 2.73 |
| $80^\circ$ | 0.576 | 0.567 | $-0.0087$ | 8.11 |
| $85^\circ$ | 1.147 | 1.143 | $-0.0044$ | 16.2 |
| $89^\circ$ | 5.730 | 5.729 | $-0.00087$ | 81.0 |
| $89.9^\circ$ | 57.30 | 57.30 | $-0.000087$ | 810 |
| $89.99^\circ$ | 573.0 | 573.0 | $-0.0000087$ | 8103 |

The individual rates grow without limit while their difference shrinks to $p=0$, as §5 predicts. A gyro reading of $0.1$ rad/s becomes a yaw-angle rate of $573$ rad/s at $89.99^\circ$.

## 7. A numerical demonstration: a pull-up past the vertical

Take an aircraft starting level and heading north ($\boldsymbol\Phi(0)=\mathbf 0$) that pulls up at a constant $q=0.2$ rad/s with a small constant yaw rate $r=0.005$ rad/s and $p=0$. The rotational kinematic equation $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ was integrated for 16 s with an adaptive Runge–Kutta solver (relative tolerance $10^{-11}$). As a reference with no singularity, the DCM equation $\dot{\mathbf C}=-\tilde{\boldsymbol\omega}\mathbf C$ was integrated over the same interval and the Euler angles were extracted from it with the atan2 formulas of Chapter 2, §2.4.4.

![[amc_dd_euler_pullup_demo.png|900]]

The pitch angle rises at almost exactly $q$ for 7 s. Then, within 0.7 s around $t=7.85$ s, $\phi$ and $\psi$ both swing from about $19^\circ$ to about $160^\circ$, $\theta$ peaks at $88.57^\circ$ and starts to fall, and $|\dot\psi|$ exceeds 1 rad/s from $t=7.52$ to $8.18$ s, peaking at 8.0 rad/s ($459^\circ$/s). The body rates never exceed 0.2 rad/s. After the swing the aircraft is described as rolled $177^\circ$, heading $180^\circ$ and pitching down: the Euler-angle description of the back half of a loop, with the aircraft upside down and going south. The airframe did nothing abrupt; the description changed branch.

> [!check] Predicting the peak rate from the geometry
> The nose direction in NED is $\mathbf x_b=[c_\theta c_\psi,\ c_\theta s_\psi,\ -s_\theta]^T$, so $\theta$ is its elevation and $\psi$ its azimuth. Here $\boldsymbol\omega$ is constant in the body and has no $x$ component, so the nose moves at angular speed $|\boldsymbol\omega|=\sqrt{0.2^2+0.005^2}=0.20006$ rad/s along a great circle perpendicular to $\boldsymbol\omega$, which is tilted from the vertical plane by $\arctan(r/q)=\arctan0.025=1.432^\circ$. That is the closest approach to the vertical found in the integration. At closest approach the azimuth rate of a point moving at speed $|\boldsymbol\omega|$ at polar distance $\delta_{min}$ is $|\boldsymbol\omega|/\sin\delta_{min}=0.20006/0.024992=8.005$ rad/s, the peak $\dot\psi$ of the integration to four figures. Smaller $r$ means a closer pass and a larger spike, roughly $q^2/r$.

The two integrations agree, angle for angle, to $4\times10^{-8}$ degrees, and the DCM rebuilt from the integrated Euler angles matches the integrated DCM to $3\times10^{-11}$. Both are correct: the Euler angles are a valid description everywhere along this path because the nose never reaches the vertical exactly. The cost is visible in the solver: the adaptive integrator needed 1607 function evaluations for $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ against 227 for the DCM equation, cutting its steps around $t=7.85$ s to follow rates 40 times larger than any body rate. A fixed-step fourth-order Runge–Kutta integrator at 50 Hz still copes with this pass, finishing within $10^{-5}$ degrees. Closer passes are another matter. With $r=0.0005$ rad/s the nose misses the vertical by $0.14^\circ$, the spike reaches about 80 rad/s and the 50 Hz result is $0.01^\circ$ out; with $r=0.00005$ rad/s (a $0.014^\circ$ miss, spike about 800 rad/s) it ends $180^\circ$ out in $\phi$ and $\psi$ and $186^\circ$ in $\theta$, on the wrong branch altogether. Meanwhile $\phi-\psi$ drifted only from $0^\circ$ to $-3^\circ$ over the whole run, at a finite rate, as §5 requires.

## 8. What is done about it

For a conventional aircraft the singularity is not a practical limitation: pitch attitudes close to $\pm90^\circ$ are uncommon, and Euler angles stay the standard description (Chapter 2, §2.4.5). The 6-DOF model of [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model|4.3]] lists $\cos\theta\neq0$ among its assumptions for that reason, and a simulation using $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ should stop or warn when $|\cos\theta|$ falls below a tolerance.

For vehicles that regularly approach the vertical (aerobatic aircraft, missiles, spacecraft) the attitude is propagated in a form without the singularity, and Euler angles are extracted only to display the attitude to a human operator (Chapter 2, §§2.4.4–2.4.5). The DCM equation of §3 is one such form, the reference used in §7: nine numbers instead of three, but no division by $\cos\theta$. The course names quaternions as the standard non-singular representation (Chapter 2, §2.4.5); their algebra is beyond the course.

## 9. Common mistakes

- Transforming every Euler rate through the full $\mathbf C_{FRD/NED}$. Each passes only through the rotations after it: the roll rate through none, the pitch rate through the roll, the yaw rate through pitch and roll.
- Inverting $\mathbf E$ by transposing it. $\mathbf E$ is not a DCM: its columns are unit vectors but columns 1 and 3 are not perpendicular (their dot product is $-\sin\theta$).
- Dropping a sign in the cofactors; the checkerboard of $(-1)^{i+j}$ is what turns $-s_\theta s_\phi$ into $C_{21}=+s_\phi s_\theta$.
- Saying the Euler rates must blow up near $90^\circ$. They do only if $q\sin\phi+r\cos\phi\neq0$, the body-rate component about the horizontal axis $\mathbf x_1$.
- Treating the blow-up as physical. The body rates stay finite and the attitude changes smoothly; only the angle description fails, and the identifiable combination $\phi\mp\psi$ changes at a finite rate.
- Integrating $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ with a fixed step through a near-vertical attitude: a close enough pass puts the result on the wrong branch (§7).

## Links

- Parent: [[SESA3047 Advanced Aerospace Mechanics & Control Hub]]
- Lecture notes: [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]] (the derivation and the coupling examples) · [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]] (the 3-2-1 DCM and gimbal lock in the extraction formulas) · [[SESA3047 2.1 - Vector Operations and the Transport Theorem]] (angular velocity and the transport theorem)
- Used in: [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]] (the $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ row) · [[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]] (its linearisation to $\dot\theta=q$)
- Concepts: [[Rotational Kinematic Equation]] · [[Gimbal Lock]] · [[Aerospace 3-2-1 Euler Sequence]] · [[Angular Velocity Vector]] · [[Direction Cosine Matrix]] · [[Cross-Product Matrix]]
- Earlier years: [[Euler Angles and Rotation Matrices]] (SESA2027)
- Practice: [[SESA3047 Mock Questions - Chapters 1-4#Q6. Euler-angle rates from gyro rates|Mock Q6]]
- Formulae: [[SESA3047 Formula Sheet#Rotational kinematics]]

## Sources

- `Chapter 2.pdf` (Dr Cristiano Martinelli), §§2.4.1–2.4.5: the elementary rotations, the 3-2-1 sequence, extraction for display, and the Euler-angle singularity with quaternions named as the non-singular alternative (p. 12).
- `Chapter-3.pdf`, §§3.1.1–3.1.4, Eqs. 3.1–3.14, and Appendix §3.4.1: composition of the rates, $\mathbf E$, $\mathbf H$ and the scalar form.
- `L6 - SESA3047.txt` (end of Chapter 2), ll. 190–227: extraction and gimbal lock. `SESA3047 - L7.txt` (Mon 5 Oct), ll. 116–341: the rate composition (ll. 160–194), the multiplication (ll. 200–313) and the inverse (ll. 318–341). `L8 - SESA3047.txt` (Thu 8 Oct), ll. 1–64: geometric coupling.
- Chapter 3 does not treat the singularity of $\mathbf H$ explicitly; §§5–6 follow from $\det\mathbf E$ and the Chapter 2 discussion.
- Computation: `generate_amc_deepdive_figures.py` in `01 - Notes/Figures/` (`--check` confirms $\det\mathbf E$, the cofactors, $\mathbf H\mathbf E=\mathbf I$, $\mathbf E=\mathbf C_x\mathbf E_\theta$, the DCM route, the null spaces at $\pm90^\circ$, the $\dot\phi-\dot\psi$ identity, the singular values of $\mathbf H$ for several roll angles, the table of §6 and every number of the pull-up).

## Self-study tasks

L6–L8 set no formal homework on this material. Tasks citing a line were worked or emphasised in those lectures; tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L7 ll. 160–194)** Explain why the yaw rate passes through two rotations, the pitch rate through one and the roll rate through none, and write $\mathbf E$ column by column. → [[#2. Adding the three elemental rotation rates (3.5–3.9)|§2]]
- [ ] **(L7 ll. 200–313)** Multiply out $\mathbf C_x(\phi)\mathbf C_y(\theta)\mathbf e_3$ and assemble $\mathbf E$. → [[#2. Adding the three elemental rotation rates (3.5–3.9)|§2]]
- [ ] **(L7 ll. 318–341; $\mathbf H$ quoted, not derived)** Find $\det\mathbf E$ and all nine cofactors, and divide the adjugate by $\cos\theta$ to get $\mathbf H$. → [[#4. Inverting E by cofactors (3.10–3.11)|§4]]
- [ ] **(L6 ll. 211–227)** At $\theta=90^\circ$, show that columns 1 and 3 of $\mathbf E$ are parallel, find its null space, and connect $[1,0,1]^T$ to the DCM depending only on $\phi-\psi$. → [[#5. The singularity at θ = ±90°|§5]]

### Further practice

- [ ] (suggested, not lecturer-set) Derive $\mathbf E$ a second way from $\tilde{\boldsymbol\omega}=-\dot{\mathbf C}\mathbf C^T$, including $\dot{\mathbf C}_x\mathbf C_x^T=-\dot\phi\,\tilde{\mathbf e}_1$. → [[#3. The same E from the DCM rate|§3]]
- [ ] (suggested, not lecturer-set) Show that $\sigma_{max}(\mathbf H)=1/\sqrt{1-|\sin\theta|}$ and that $\dot\phi-\dot\psi$ stays finite as $\theta\to90^\circ$. → [[#6. How large the gain gets|§6]]
- [ ] (suggested, not lecturer-set) Predict the peak $\dot\psi$ of the §7 pull-up from the closest approach of the nose to the vertical, then reproduce it by integrating $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$. → [[#7. A numerical demonstration: a pull-up past the vertical|§7]]

## Transcript and slide slips

> [!warning] Transcript slip (L6, ll. 220–221)
> Where: [[#7. A numerical demonstration: a pull-up past the vertical]].
>
> *"If we are at theta equal to 90, there is a singularity. At 91 it works again."* The extraction formulas do work again just off the vertical, but a pitch of $91^\circ$ cannot be returned: $\theta=-\arcsin C_{13}$ lies in $[-90^\circ,90^\circ]$. A nose $1^\circ$ past the vertical comes back as $\theta=89^\circ$ with $\phi$ and $\psi$ both shifted by $180^\circ$, which is the branch change seen in the §7 pull-up.
