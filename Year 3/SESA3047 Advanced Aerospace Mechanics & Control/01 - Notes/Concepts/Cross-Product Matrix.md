---
title: "Cross-Product Matrix"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["skew-symmetric matrix", "skew matrix", "tilde matrix", "u tilde"]
tags: [sesa3047, concept, kinematics, vectors]
status: complete
parent_lectures: ["[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]"]
related_concepts: ["[[Vector (Cross) Product]]", "[[Transport Theorem]]", "[[Direction Cosine Matrix]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Cross-Product Matrix

## Definition

> [!note] Definition
> For $\mathbf u=[u_x,u_y,u_z]^T$, the cross product with any vector $\mathbf v$ can be written as a matrix product:
>
> $$\mathbf u\times\mathbf v=\tilde{\mathbf u}\,\mathbf v,\qquad \tilde{\mathbf u}=\begin{bmatrix}0&-u_z&u_y\\u_z&0&-u_x\\-u_y&u_x&0\end{bmatrix}\quad(\text{Eq. 2.16}).$$

## Where it comes from

Each component of $\mathbf u\times\mathbf v=[u_yv_z-u_zv_y,\ u_zv_x-u_xv_z,\ u_xv_y-u_yv_x]^T$ is linear in $v_x,v_y,v_z$. Reading off the coefficients gives $\tilde{\mathbf u}$.

## Properties

- $\tilde{\mathbf u}^T=-\tilde{\mathbf u}$: skew-symmetric, zero diagonal, 3 independent entries.
- $\tilde{\mathbf u}\mathbf u=\mathbf 0$ and $\tilde{\mathbf u}\mathbf v=-\tilde{\mathbf v}\mathbf u$.
- $\tilde{\boldsymbol\omega}^2=\boldsymbol\omega\boldsymbol\omega^T-\omega^2\mathbf I$ (from BAC−CAB). So $\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)=-\omega^2\mathbf r$ when $\boldsymbol\omega\perp\mathbf r$.
- Small rotations: $\mathbf C\approx\mathbf I-\widetilde{\delta\boldsymbol\Theta}$.
- DCM kinematics: $\dot{\mathbf C}_{b/a}=-\tilde{\boldsymbol\omega}^b_{b/a}\mathbf C_{b/a}$.

## Example

$\mathbf u=[1,2,3]^T$, $\mathbf v=[4,5,6]^T$: $\tilde{\mathbf u}\mathbf v=[-3,6,-3]^T$.

## Related

- [[Vector (Cross) Product]] · [[Transport Theorem]] · [[Direction Cosine Matrix]]
- Full derivations: [[SESA3047 2.1 - Vector Operations and the Transport Theorem#The cross-product (skew) matrix|2.1 §3]]
