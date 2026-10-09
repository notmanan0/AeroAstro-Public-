---
title: "PDE Classification"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Hyperbolic", "Parabolic", "Elliptic", "Discriminant b^2-ac", "Tricomi equation"]
tags: [math2048, concept, pdes]
status: complete
parent_lectures: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]"]
related_concepts: ["[[Wave Equation]]", "[[Heat Equation]]", "[[Laplace's Equation]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture14_Hyperbolic1.pdf"]
---

# PDE Classification

## Definition

> [!note] Definition
> A second-order linear PDE has the form
>
> $$au_{xx}+2bu_{xy}+cu_{yy}+du_x+eu_y+fu=0 .$$
>
> It is **hyperbolic** if $b^2-ac>0$, **parabolic** if $b^2-ac=0$, and **elliptic** if $b^2-ac<0$.

## Explanation
| Type | Prototype | Data needed | Physics |
|---|---|---|---|
| Hyperbolic | $u_{tt}=c^2u_{xx}$ | $u$ and $u_t$ at $t=0$, plus BCs | waves, finite speed |
| Parabolic | $u_t=\kappa u_{xx}$ | $u$ at $t=0$, plus BCs | diffusion, smoothing |
| Elliptic | $u_{xx}+u_{yy}=0$ | one BC on every boundary | steady states |

- The mixed-derivative coefficient is $2b$. If the PDE is written with $B$ in front of $u_{xy}$, use $b=B/2$.
- **The type is local.** For the Tricomi equation $yu_{xx}=u_{yy}$ (as written in the slides), $b^2-ac=y$. So it is hyperbolic for $y>0$ and elliptic for $y<0$. This models transonic flow, where the Mach number crosses 1.
- **Aerodynamics link**: the linearised potential-flow equation $(1-M^2)\phi_{xx}+\phi_{yy}=0$ is elliptic for subsonic flow ($M<1$) and hyperbolic for supersonic flow ($M>1$).

## Examples
- $u_{xx}+4u_{xy}+4u_{yy}=0$: $b=2$, $a=c=4$, so $b^2-ac=0$. Parabolic.
- $u_{xx}+u_{xy}+u_{yy}=0$: $b=\frac12$, so $b^2-ac=-\frac34$. Elliptic.

## Related
- [[Wave Equation]] · [[Heat Equation]] · [[Laplace's Equation]]

## Sources
- Lecture 14
