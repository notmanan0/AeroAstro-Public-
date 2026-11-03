---
title: "Line Integrals"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Work integral", "Circulation", "Path integral"]
tags: [math2048, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
related_concepts: ["[[Conservative Vector Fields]]", "[[Stokes' Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture22_vector02.pdf", "02 - Sources/Lectures/MATH2048 Lecture 21.txt", "02 - Sources/Lectures/MATH2048 Lecture 22.txt"]
---

# Line Integrals

The **line integral** of a vector field along a curve $C$ given by $\mathbf r(t)$, $a\leq t\leq b$, is $\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F(\mathbf r(t))\cdot\frac{d\mathbf r}{dt}\,dt$. For a force field it is the work done moving along $C$.

It comes from splitting the curve into short segments, treating the force as constant on each, and adding $\mathbf F\cdot\Delta\mathbf r$; in the limit the sum becomes an ordinary integral in the parameter. The recipe is always the same: read $x(t)$, $y(t)$, $z(t)$ off the curve, substitute into $\mathbf F$, differentiate $\mathbf r(t)$, dot the two, integrate. A straight line from $\mathbf a$ to $\mathbf b$ is $\mathbf a+(\mathbf b-\mathbf a)t$, with a constant tangent.

The value doesn't depend on how the curve is parametrised, and reversing the direction flips its sign. In general it does depend on the path: in Lecture 22, $\mathbf F=2xy\,\mathbf i+(x^2-z^2)\,\mathbf j-3xz^2\,\mathbf k$ gives $-\frac{323}7$ along a curve and $-\frac{79}2$ along the straight line between the same points. For a [[Conservative Vector Fields|conservative field]] it depends only on the endpoints, and round any closed loop it is zero. Round a closed loop, $\oint\mathbf F\cdot d\mathbf r$ is called the circulation, which [[Stokes' Theorem]] relates to the curl.

## Related

- Derivation and examples: [[MATH2048 VC3 - Line Integrals and Conservative Fields]]
- [[Conservative Vector Fields]] · [[Stokes' Theorem]] · [[Flux Integrals]]
