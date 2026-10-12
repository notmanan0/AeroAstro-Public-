---
title: "Conformal Mapping"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["conformal transformation", "conformal map"]
tags: [sesa3043, concept, potential-flow, conformal-mapping]
status: complete
parent_lectures: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]"]
related_concepts: ["[[Joukowski Transformation]]", "[[Kármán–Trefftz Transformation]]", "[[Complex Velocity Potential]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf"]
---

# Conformal Mapping

## Definition

> [!note] Definition
> A mapping $z=f(\bar z)$ by an analytic function with $f'(\bar z)\neq0$. It preserves angles locally (it rotates and stretches every small line element at a point by the same $f'$), so it carries a potential flow in the $\bar z$-plane into a potential flow in the $z$-plane.

## Rules

- **Streamlines → streamlines**; a body surface stays a streamline.
- **Velocity:** $u-iv=\dfrac{\mathrm d\Phi/\mathrm d\bar z}{\mathrm dz/\mathrm d\bar z}$.
- **Circulation and source strengths** are unchanged.
- **Critical points** ($f'=0$) are where sharp corners are created; the flow there has infinite speed unless it stagnates in the $\bar z$-plane (Kutta condition).

## Recipe

Known flow in $\bar z$ (usually the cylinder) → transfer function → transform geometry → transform potential → $u-iv$ and Bernoulli.

![[aa_conformal_mapping_family.png|700]]

## In the lectures and the exam

The two hand-calculation cases, both examinable (8–9 Oct):

| Map | Body | Potential | $C_p$ on the body |
|---|---|---|---|
| $z=\bar z-a^2/\bar z$ | plate **normal** to the stream, $-2a\le y\le2a$ | $\Phi=\pm U_\infty\sqrt{z^2+4a^2}$ | $1-\dfrac{y^2}{4a^2-y^2}$ |
| $z=\bar z+a^2/\bar z$ | plate **along** the stream, $-2a\le x\le2a$ | $\Phi=U_\infty z$ | $0$ |

Keep one transfer function per problem: a different map turns the same $\bar z$ solution into a different body (8 Oct, ll. 310–316). Conformal maps also generate orthogonal CFD meshes (ll. 249–256).

## Related

- [[SESA3043 2.1 - Complex Functions and Conformal Mapping]] · [[Joukowski Transformation]] · [[Kármán–Trefftz Transformation]]
