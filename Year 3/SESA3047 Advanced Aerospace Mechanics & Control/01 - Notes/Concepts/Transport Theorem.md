---
title: "Transport Theorem"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["transport equation", "rotating-frame derivative", "Coriolis theorem", "basic kinematic equation"]
tags: [sesa3047, concept, kinematics]
status: complete
parent_lectures: ["[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]"]
related_concepts: ["[[Angular Velocity Vector]]", "[[Cross-Product Matrix]]", "[[Reference Frames and Coordinate Systems]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Transport Theorem

## Statement

> [!note] Definition
> For any vector $\mathbf p$ and frames $F_a$, $F_b$ with $F_b$ rotating at $\boldsymbol\omega_{b/a}$ relative to $F_a$:
>
> $${}^a\dot{\mathbf p}={}^b\dot{\mathbf p}+\boldsymbol\omega_{b/a}\times\mathbf p\qquad(\text{Eq. 2.22}).$$
>
> ${}^b\dot{\mathbf p}$ is the change seen inside $F_b$. $\boldsymbol\omega\times\mathbf p$ is the extra change seen from $F_a$ because $F_b$ rotates.

## Derivation in three lines

1. A unit vector fixed in $F_b$ only rotates: ${}^a\dot{\mathbf b}_i=\boldsymbol\omega_{b/a}\times\mathbf b_i$.
2. Write $\mathbf p=\sum p_i\mathbf b_i$. The product rule gives ${}^a\dot{\mathbf p}=\sum\dot p_i\mathbf b_i+\sum p_i\,{}^a\dot{\mathbf b}_i$.
3. The first sum is ${}^b\dot{\mathbf p}$; the second is $\boldsymbol\omega_{b/a}\times\mathbf p$.

Visual step-by-step derivation: [[SESA3047 2.1 - Vector Operations and the Transport Theorem#8. The transport theorem|2.1 §8]].

## Special cases

- $\mathbf p$ fixed in $F_b$: ${}^a\dot{\mathbf p}=\boldsymbol\omega_{b/a}\times\mathbf p$ (e.g. the nose direction, ${}^e\dot{\mathbf u}=\boldsymbol\omega_{b/e}\times\mathbf u$).
- no relative rotation, or $\mathbf p\parallel\boldsymbol\omega$: ${}^a\dot{\mathbf p}={}^b\dot{\mathbf p}$.
- Frame translation never appears.

## Uses

- Rigid-body velocity: $\mathbf v_P=\mathbf v_Q+\boldsymbol\omega\times\mathbf p$.
- Applied twice, it gives the Coriolis ($2\boldsymbol\omega\times{}^b\dot{\mathbf p}$) and centripetal terms.
- Newton's law in body axes: ${}^e\dot{\mathbf v}={}^b\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v$. These are the $qW-rV$ terms of the SESA2027 equations of motion.

## Related

- [[Angular Velocity Vector]] · [[Cross-Product Matrix]] · [[Euler Angles and Rotation Matrices]]
- Not to be confused with the fluid-mechanics [[Reynolds Transport Theorem]]
