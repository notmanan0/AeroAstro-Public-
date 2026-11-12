---
title: "Argand Diagram"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["Complex plane", "Argand plane"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Loci in the Complex Plane]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.1, §4.2.6", "MATH1054 Module Booklet, Module 5"]
---

# Argand Diagram

The Argand diagram is the plane in which the complex number $z=x+\mathrm jy$ is drawn as the point, or the vector from the origin to the point, $(x,y)$. The horizontal axis is the real axis and the vertical axis the imaginary axis.

In this picture $|z|=\sqrt{x^2+y^2}$ is the distance of the point from the origin and $\arg z$ is the angle from the positive real axis, anticlockwise positive. Complex arithmetic then becomes geometry. Adding real and imaginary parts separately is adding vector components, so $z_1+z_2$ is the diagonal of the parallelogram on $z_1$ and $z_2$. Since $z_2+(z_1-z_2)=z_1$, the difference $z_1-z_2$ is the vector from the point $z_2$ to the point $z_1$, and its modulus

$$
|z_1-z_2|=\sqrt{(x_1-x_2)^2+(y_1-y_2)^2}
$$

is the distance between them. This one fact makes the loci of M22 readable: $|z-a|=r$ is the circle of radius $r$ about $a$, and $|z-a|=|z-b|$ is the perpendicular bisector of $a$ and $b$ ([[Loci in the Complex Plane]]). The triangle with vertices $0$, $z_1$ and $z_1+z_2$ gives the triangle inequality $|z_1+z_2|\le|z_1|+|z_2|$.

Multiplication is a stretch and a turn. Since moduli multiply and arguments add, multiplying by $re^{\mathrm j\phi}$ scales by $r$ and rotates by $\phi$. In particular $\mathrm j=e^{\mathrm j\pi/2}$, so $\mathrm j(x+\mathrm jy)=-y+\mathrm jx$ is the vector turned through $90°$ anticlockwise with its length unchanged. The conjugate $z^*=x-\mathrm jy$ is the reflection in the real axis, and the $n$ roots of $z^n=w$ sit at the vertices of a regular $n$-gon centred on the origin ([[De Moivre's Theorem and Roots of Complex Numbers]]).

James Example 4.15 uses the rotation to build a square on $\vec{OP}=(1,2)$ in the first and second quadrants. With $p=1+2\mathrm j$, the adjacent side is $\mathrm jp=\mathrm j+2\mathrm j^2=-2+\mathrm j$, and the fourth vertex is $p+\mathrm jp=-1+3\mathrm j$, so the vertices are $(0,0)$, $(1,2)$, $(-2,1)$ and $(-1,3)$. Both sides have length $\sqrt5$, and $(1)(-2)+(2)(1)=0$ confirms the right angle. Rotating by $-\mathrm j$ instead would give $2-\mathrm j$, in the fourth quadrant. Specimen Test 5, Q2 asks for the parallelogram construction of $z_1+z_2$ and $z_1-z_2$.

The common trap is to treat the vertical coordinate as $\mathrm jy$: it is the real number $y=\operatorname{Im}z$, and the modulus is $\sqrt{x^2+y^2}$, not $\sqrt{x^2+(\mathrm jy)^2}$. The other is drawing $z_1-z_2$ from $z_1$ to $z_2$; the arrow runs from $z_2$ to $z_1$.

## Related

- Topics: [[MATH1054 M05 - Complex Numbers I]] (§1 and §8) · [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Loci in the Complex Plane]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Phasor Representation]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §3.2.1 (the Argand diagram), §4.2.6 (complex numbers as vectors, Example 4.15); MATH1054 Module Booklet, Module 5
