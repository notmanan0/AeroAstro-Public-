---
title: "Flux Integrals"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Surface integral", "dS", "Vector area element", "Surface area element"]
tags: [math2048, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]"]
related_concepts: ["[[Divergence Theorem]]", "[[Stokes' Theorem]]", "[[Jacobian and Volume Elements]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture27_vector07.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture28_vector08.pdf"]
---

# Flux Integrals

## Definition

> [!note] Definition
> For a surface parametrised as $\mathbf r(s,t)$:
>
> $$d\mathbf S=(\mathbf r_s\times\mathbf r_t)\,ds\,dt,\qquad dA=|\mathbf r_s\times\mathbf r_t|\,ds\,dt,\qquad \iint_S\mathbf F\cdot d\mathbf S=\iint\mathbf F(\mathbf r(s,t))\cdot(\mathbf r_s\times\mathbf r_t)\,ds\,dt .$$

## Explanation
| Surface | $d\mathbf S$ |
|---|---|
| Plane $z=$ const | $\pm\mathbf k\,dx\,dy$ |
| Graph $z=f(x,y)$ | $(-f_x,\,-f_y,\,1)\,dx\,dy$ (upward) |
| Cylinder of radius $a$ | $\hat{\boldsymbol\rho}\,a\,d\phi\,dz$ |
| Sphere of radius $a$ | $\hat{\mathbf r}\,a^2\sin\theta\,d\theta\,d\phi$ |

- **Orientation**: check that $\mathbf r_s\times\mathbf r_t$ points the way the question asks (up or out). Swapping the order of $s$ and $t$ flips it, and flips the sign of the flux.
- **Use symmetry**:
  - on a sphere, $\iint x^2\,dA=\iint y^2\,dA=\iint z^2\,dA=\frac13a^2\cdot\text{area}$;
  - odd integrands vanish;
  - with $\mathbf F=\mathbf r$ on a sphere, $\mathbf F\cdot\hat{\mathbf n}=a$.
- **Closed surfaces**: Gauss's theorem is usually easier. For an open surface, you can close it with a disc and subtract that disc's flux.

## Examples
- Upper hemisphere of radius $a$:
  - $\mathbf F=y\,\mathbf j$ gives $2\pi a^3/3$;
  - $\mathbf F=(-y,x,1)$ gives $\pi a^2$;
  - $\mathbf F=x\mathbf r$ gives $0$ (PS10 Q2).
- Cone of base radius $a$, height $h$: area $\pi a\sqrt{a^2+h^2}$.
- Funnel $x^2+y^2=z^2$ with outward normal: flux of $(-y,x,z)$ is $-486\pi$.

## Related
- [[Divergence Theorem]] · [[Stokes' Theorem]] · [[Jacobian and Volume Elements]]

## Sources
- Lectures 27–28; PS10
