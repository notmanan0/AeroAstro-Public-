---
title: "Direction Cosine Matrix"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["DCM", "rotation matrix", "coordinate transformation matrix", "C_b/a"]
tags: [sesa3047, concept, kinematics, dcm]
status: complete
parent_lectures: ["[[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]"]
related_concepts: ["[[Aerospace 3-2-1 Euler Sequence]]", "[[Euler Angles and Rotation Matrices]]", "[[Reference Frames and Coordinate Systems]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Direction Cosine Matrix

## Definition

> [!note] Definition
>
> $$\mathbf u^b=\mathbf C_{b/a}\,\mathbf u^a,\qquad C_{ij}=\mathbf b_i\cdot\mathbf a_j=\cos(\angle\,\mathbf b_i,\mathbf a_j).$$
>
> It converts the **components** of the same physical vector from coordinates $a$ to coordinates $b$. Row $i$ is the new axis $\mathbf b_i$ in old components.

## Properties

| Property | Statement | Reason |
|---|---|---|
| orthogonal | $\mathbf C^T\mathbf C=\mathbf I$, $\mathbf C^{-1}=\mathbf C^T$ | rows are orthonormal unit vectors |
| composition | $\mathbf C_{d/a}=\mathbf C_{d/c}\mathbf C_{c/b}\mathbf C_{b/a}$ | chain the transformations; the rightmost acts first |
| determinant | $\det\mathbf C=+1$ | triple product of a right-handed triad |
| non-commutative | $\mathbf C_{c/b}\mathbf C_{b/a}\neq\mathbf C_{b/a}\mathbf C_{c/b}$ | later rotations act about already-moved axes |
| length-preserving | $|\mathbf u^b|=|\mathbf u^a|$ | follows from orthogonality |

## Elementary rotations

$$
\mathbf C_z(\theta)=\begin{bmatrix}c&s&0\\-s&c&0\\0&0&1\end{bmatrix},\ 
\mathbf C_y(\theta)=\begin{bmatrix}c&0&-s\\0&1&0\\s&0&c\end{bmatrix},\ 
\mathbf C_x(\theta)=\begin{bmatrix}1&0&0\\0&c&s\\0&-s&c\end{bmatrix}.
$$

Sign rule: for rotation about $k$ with $(i,j,k)$ cyclic, $C_{ij}=+\sin$ and $C_{ji}=-\sin$.

![[amc_dcm_derivation.png|700]]

## Related

- [[Aerospace 3-2-1 Euler Sequence]] · [[Cross-Product Matrix]] · [[Euler Angles and Rotation Matrices]] (SESA2027 notation $\mathbf R_{BE}$)
- Derivations: [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#3. Properties of a DCM (§2.3.2), with the reasons|2.2 §3]]
