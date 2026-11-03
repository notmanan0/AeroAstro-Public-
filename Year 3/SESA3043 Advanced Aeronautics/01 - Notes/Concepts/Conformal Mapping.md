---
title: "Conformal Mapping"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["conformal transformation", "conformal map", "transfer function", "mapping function", "circle plane", "z-bar plane"]
tags: [sesa3043, concept, potential-flow, conformal-mapping]
status: complete
parent_lectures: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]"]
related_concepts: ["[[Joukowski Transformation]]", "[[Kármán–Trefftz Transformation]]", "[[Complex Velocity Potential]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf"]
---

# Conformal Mapping

A conformal mapping is a map $z=f(\bar z)$ by an analytic function with $f'(\bar z)\neq0$. Locally it rotates and stretches every small line element at a point by the same factor $f'$, so it preserves angles, and it carries a potential flow in the $\bar z$-plane into a potential flow in the $z$-plane.

Streamlines map to streamlines, so a body surface stays a streamline, and circulation and source strengths are unchanged. The velocity in the new plane is

$$u-iv=\frac{\mathrm d\Phi/\mathrm d\bar z}{\mathrm dz/\mathrm d\bar z}.$$

Sharp corners are created at the critical points, where $f'=0$. The flow there has infinite speed unless it stagnates at the matching point in the $\bar z$-plane, which is the Kutta condition.

The recipe is always the same: start from a known flow in $\bar z$ (usually the cylinder), pick the transfer function, transform the geometry and the potential, then get $u-iv$ and the pressure from Bernoulli.

![[aa_conformal_mapping_family.png|700]]

## The two exam cases

Both hand-calculation cases were lectured on 8–9 October and are examinable:

| Map | Body | Potential | $C_p$ on the body |
|---|---|---|---|
| $z=\bar z-a^2/\bar z$ | flow impinging on a finite plate (plate normal to the stream), $-2a\le y\le2a$ | $\Phi=\pm U_\infty\sqrt{z^2+4a^2}$ | $1-\dfrac{y^2}{4a^2-y^2}$ |
| $z=\bar z+a^2/\bar z$ | flow over a finite plate (plate along the stream), $-2a\le x\le2a$ | $\Phi=U_\infty z$ | $0$ |

Stick to one transfer function per problem: a different map turns the same $\bar z$ solution into a different body (8 Oct, ll. 310–316). Conformal maps are also used to generate orthogonal CFD meshes (ll. 249–256).

## Related

- [[SESA3043 2.1 - Complex Functions and Conformal Mapping]] · [[Joukowski Transformation]] · [[Kármán–Trefftz Transformation]]
