---
title: "Vector (Cross) Product"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Cross product", "Vector product", "Moment of a force"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M14 - Vectors I]]", "[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Scalar (Dot) Product]]", "[[Scalar Triple Product]]", "[[Principle of Angular Impulse and Momentum]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.3.2", "MATH1054 Module Booklet, Module 14"]
---

# Vector (Cross) Product

## Definition

> [!note] Definition
> $$\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix},\qquad|\mathbf a\times\mathbf b|=|\mathbf a||\mathbf b|\sin\theta$$
> The result is perpendicular to both $\mathbf a$ and $\mathbf b$ (right-hand rule).

## Explanation
- $\mathbf b\times\mathbf a=-\mathbf a\times\mathbf b$. It is **not associative**.
- $\mathbf a\times\mathbf b=\mathbf0$ iff $\mathbf a\parallel\mathbf b$.
- **Uses**:
  - unit normals;
  - areas: a parallelogram is $|\mathbf a\times\mathbf b|$, a triangle is half that;
  - moments $\mathbf M_{\mathrm A}=\vec{\mathrm{AP}}\times\mathbf F$;
  - rigid-body velocity $\mathbf v=\boldsymbol\omega\times\vec{\mathrm{AP}}$.
- **BAC−CAB**: $\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$.
- **Check**: the result dots to zero with both inputs.

## Examples
- Area of PQR $=\frac12|(11,-7,19)|=\frac{3\sqrt{59}}2$ (Ex 4.26).
- Moment about A: $\frac{4}{3\sqrt5}(8,-6,1)$ (Ex 4.28).
- Velocity of P: $\frac{30}{\sqrt{14}}(1,1,2)$ (Ex 4.29).

## Related
- Topics: [[MATH1054 M14 - Vectors I]] · [[MATH1054 M15 - Vectors II]]
- Concepts: [[Scalar (Dot) Product]] · [[Scalar Triple Product]] · [[Principle of Angular Impulse and Momentum]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §4.3.2
- MATH1054 Module Booklet, Module 14
