---
title: "Equations of Lines and Planes"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Vector equation of a line", "Equation of a plane", "Skew lines", "Distance point to plane"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Vector (Cross) Product]]", "[[Scalar Triple Product]]", "[[Vector Algebra and Components]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.4", "MATH1054 Module Booklet, Module 15"]
---

# Equations of Lines and Planes

## Definition

> [!note] Definition
> $$\text{Line: }\mathbf r=\mathbf a+t\mathbf d\ \Longleftrightarrow\ \frac{x-a_1}{d_1}=\frac{y-a_2}{d_2}=\frac{z-a_3}{d_3};\qquad\text{Plane: }\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n$$

## Explanation
- **Do two lines intersect?** Solve two of the three component equations for $s$ and $t$, then check the third.
- **Plane through three points**: $\mathbf n=(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)$.
- **Line of intersection of two planes**: direction $\mathbf n_1\times\mathbf n_2$, plus any common point.
- **Distance from a point to a plane**: $\dfrac{|\mathbf n\cdot\mathbf p-d|}{|\mathbf n|}$.
- **Skew lines**: the distance is $\dfrac{|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|}{|\mathbf d_1\times\mathbf d_2|}$.

## Examples
- Skew lines at distance $3\sqrt{30}$, with common perpendicular $\mathbf r=(3,8,3)+\mu(2,5,-1)$ (Ex 4.42).
- $x+y+z=5$ and $4x+y+2z=15$ meet in $\mathbf r=(3,1,1)+t(1,2,-3)$ (Ex 4.47).

## Related
- Topics: [[MATH1054 M15 - Vectors II]]
- Concepts: [[Vector (Cross) Product]] · [[Scalar Triple Product]] · [[Vector Algebra and Components]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §4.4
- MATH1054 Module Booklet, Module 15
