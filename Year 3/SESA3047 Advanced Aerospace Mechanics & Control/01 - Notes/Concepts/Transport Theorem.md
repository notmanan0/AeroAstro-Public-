---
title: "Transport Theorem"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["transport equation", "rotating-frame derivative", "Coriolis theorem", "basic kinematic equation", "BKE", "equation of Coriolis"]
tags: [sesa3047, concept, kinematics]
status: complete
parent_lectures: ["[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]"]
related_concepts: ["[[Angular Velocity Vector]]", "[[Cross-Product Matrix]]", "[[Reference Frames and Coordinate Systems]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Transport Theorem

For any vector $\mathbf p$ and frames $F_a$ and $F_b$, with $F_b$ rotating at $\boldsymbol\omega_{b/a}$ relative to $F_a$,

$${}^a\dot{\mathbf p}={}^b\dot{\mathbf p}+\boldsymbol\omega_{b/a}\times\mathbf p\qquad(\text{Eq. 2.22}).$$

${}^b\dot{\mathbf p}$ is the change seen from inside $F_b$, and $\boldsymbol\omega\times\mathbf p$ is the extra change seen from $F_a$ because $F_b$ is rotating.

The derivation is short. A unit vector fixed in $F_b$ can only rotate, so ${}^a\dot{\mathbf b}_i=\boldsymbol\omega_{b/a}\times\mathbf b_i$. Writing $\mathbf p=\sum p_i\mathbf b_i$, the product rule gives ${}^a\dot{\mathbf p}=\sum\dot p_i\mathbf b_i+\sum p_i\,{}^a\dot{\mathbf b}_i$; the first sum is ${}^b\dot{\mathbf p}$ and the second is $\boldsymbol\omega_{b/a}\times\mathbf p$. A step-by-step visual version is in [[SESA3047 2.1 - Vector Operations and the Transport Theorem#8. The transport theorem|2.1 §8]].

If $\mathbf p$ is fixed in $F_b$, only the rotation term is left, ${}^a\dot{\mathbf p}=\boldsymbol\omega_{b/a}\times\mathbf p$; the nose direction, for example, obeys ${}^e\dot{\mathbf u}=\boldsymbol\omega_{b/e}\times\mathbf u$. If there is no relative rotation, or $\mathbf p\parallel\boldsymbol\omega$, the two derivatives are equal. Translation of the frames never appears.

The theorem gives the rigid-body velocity relation $\mathbf v_P=\mathbf v_Q+\boldsymbol\omega\times\mathbf p$. Applied twice it gives the Coriolis ($2\boldsymbol\omega\times{}^b\dot{\mathbf p}$) and centripetal terms. And it puts Newton's law into body axes, ${}^e\dot{\mathbf v}={}^b\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v$, which is where the $qW-rV$ terms of the SESA2027 equations of motion come from.

## Related

- [[Angular Velocity Vector]] · [[Cross-Product Matrix]] · [[Euler Angles and Rotation Matrices]]
- Not to be confused with the fluid-mechanics [[Reynolds Transport Theorem]]
