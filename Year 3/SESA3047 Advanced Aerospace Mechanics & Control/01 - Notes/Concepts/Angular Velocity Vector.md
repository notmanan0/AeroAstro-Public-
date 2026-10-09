---
title: "Angular Velocity Vector"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 2: Introduction to Kinematics"
aliases: ["angular velocity", "omega_b/a", "relative angular velocity"]
tags: [sesa3047, concept, kinematics]
status: complete
parent_lectures: ["[[SESA3047 2.1 - Vector Operations and the Transport Theorem]]"]
related_concepts: ["[[Transport Theorem]]", "[[Cross-Product Matrix]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# Angular Velocity Vector

## Definition

> [!note] Definition
> $\boldsymbol\omega_{b/a}$ is the rate at which frame $F_b$ rotates relative to frame $F_a$. Its magnitude is the rotation rate. Its direction is the instantaneous rotation axis, with the right-hand rule. In body FRD components it is $[p,\ q,\ r]^T$ (roll, pitch and yaw rates).

## Properties (§2.2.1)

| Property | Formula | Why |
|---|---|---|
| relative motion | $\boldsymbol\omega_{b/a}=-\boldsymbol\omega_{a/b}$ | each frame sees the other turn the opposite way |
| additive | $\boldsymbol\omega_{c/a}=\boldsymbol\omega_{c/b}+\boldsymbol\omega_{b/a}$ | apply the [[Transport Theorem]] twice to a vector fixed in $F_c$ |
| same derivative in both frames | ${}^a\dot{\boldsymbol\omega}_{b/a}={}^b\dot{\boldsymbol\omega}_{b/a}$ | $\boldsymbol\omega\times\boldsymbol\omega=\mathbf 0$ |

> [!warning] Angular acceleration does not simply add
>
> $${}^a\dot{\boldsymbol\omega}_{c/a}={}^b\dot{\boldsymbol\omega}_{c/b}+\boldsymbol\omega_{b/a}\times\boldsymbol\omega_{c/b}+{}^a\dot{\boldsymbol\omega}_{b/a}.$$
>
> The cross term is the source of gyroscopic effects.

## Not the rate of the Euler angles

$\boldsymbol\omega$ is a true vector. The Euler angles $(\phi,\theta,\psi)$ are not, and in general $[p,q,r]^T\neq[\dot\phi,\dot\theta,\dot\psi]^T$. Each Euler rate acts about a different, partly rotated axis. The two coincide only near wings-level flight, where $\phi$ and $\theta$ are small (see [[Aerospace 3-2-1 Euler Sequence]]). The exact relation comes with the equations of motion in later chapters.

## Related

- [[Transport Theorem]] · [[Cross-Product Matrix]] · [[Kinematics and Dynamics]]
