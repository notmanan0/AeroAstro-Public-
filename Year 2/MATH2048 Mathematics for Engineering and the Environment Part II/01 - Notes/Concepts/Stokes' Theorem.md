---
title: "Stokes' Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Stokes's theorem", "Green's theorem", "Circulation theorem"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
related_concepts: ["[[Line Integrals]]", "[[Conservative Vector Fields]]", "[[Divergence Theorem]]", "[[Kelvin's Circulation Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture30_vector10.pdf"]
---

# Stokes' Theorem

## Definition

> [!note] Definition
> $$\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_{\partial S}\mathbf F\cdot d\mathbf r$$
> The boundary $\partial S$ is oriented by the right-hand rule: for an upward $\hat{\mathbf n}$, traverse it anticlockwise when viewed from above.

## Explanation
- **Green's theorem** is the planar case:
$$\iint\Big(\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y}\Big)dx\,dy=\oint(F_1\,dx+F_2\,dy).$$
- **Any spanning surface works**: every surface with the same boundary gives the same flux of the curl. So replace a paraboloid or hemisphere with the flat disc where convenient.
- **Proof of "curl-free ⇒ conservative"**: in a simply connected region, $\oint\mathbf F\cdot d\mathbf r=\iint\mathbf 0\cdot d\mathbf S=0$.
- **Aero link**: circulation $\Gamma=\oint\mathbf u\cdot d\mathbf r=\iint\boldsymbol\omega\cdot d\mathbf S$, i.e. circulation equals vorticity flux ([[Kelvin's Circulation Theorem]], [[Kutta-Joukowski Theorem]]).

## Examples
- Paraboloid $z=9-x^2-y^2$ with $\mathbf F=(2z-y,\ x+z,\ 3x-2y)$: both sides give $18\pi$.
- PS11 Q4, upper unit hemisphere with $\mathbf F=(2y,-x,xz)$: both sides give $-3\pi$.
- PS10 Q3, disc at $z=b$: $\pi a^2(b^3-1)$.

![[m2048_vc_stokes_paraboloid.png|460]]

## Related
- [[Line Integrals]] · [[Conservative Vector Fields]] · [[Divergence Theorem]] · [[Flux Integrals]]

## Sources
- Lecture 30; Lecture Notes §8.3.1, §8.3.4
