---
title: "Loci in the Complex Plane"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["Complex loci", "Circle of Apollonius"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Argand Diagram]]", "[[Completing the Square]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.4.1–3.4.2", "MATH1054 Module Booklet, Module 22"]
---

# Loci in the Complex Plane

A locus in the complex plane is the set of points $z$ in the Argand diagram that satisfy a stated condition, such as $|z-a|=k|z-b|$ or $\operatorname{Re}\frac{z-a}{z-b}=0$; it is found by putting $z=x+\mathrm jy$ and reducing the condition to a Cartesian equation.

The geometry rests on one fact: $|z-a|$ is the distance from $z$ to $a$, and $\arg(z-a)$ is the direction of $z$ as seen from $a$. So $|z-z_0|=r$ is a circle, $|z-a|=|z-b|$ is the set of points equidistant from $a$ and $b$ (the perpendicular bisector), and $\arg(z-z_0)=\alpha$ is a half-line leaving $z_0$ at angle $\alpha$, with $z_0$ itself excluded because $\arg0$ is undefined.

| Condition | Locus |
|---|---|
| $\lvert z-z_0\rvert=r$ | circle, centre $z_0$, radius $r$ |
| $\lvert z-a\rvert=\lvert z-b\rvert$ | perpendicular bisector of $a$ and $b$ |
| $\lvert z-a\rvert=k\lvert z-b\rvert$, $k\neq1$ | circle of Apollonius |
| $\arg(z-z_0)=\alpha$ | half-line from $z_0$, excluding $z_0$ |
| $\operatorname{Re}$ or $\operatorname{Im}$ of $\frac{z-a}{z-b}$ fixed | line or circle through $b$, excluding $z=b$ |

The method is the same every time: square any moduli; for the real or imaginary part of a quotient, multiply the top and bottom by the conjugate of the denominator so the denominator becomes real; then complete the square ([[Completing the Square]]) and check for excluded points.

The **circle of Apollonius** $|z-a|=k|z-b|$, $k\neq1$, is the main result. Squaring with $|w|^2=w\bar w$ and completing the square in $z$ gives a circle with

$$
\text{centre }c=\frac{a-k^2b}{1-k^2},\qquad\text{radius }R=\frac{k\,|a-b|}{|1-k^2|}.
$$

The centre lies on the line through $a$ and $b$, $|c-a|\,|c-b|=R^2$, and the circle encloses $b$ when $k>1$ and $a$ when $k<1$; as $k\to1$ the radius grows without bound and the circle flattens into the perpendicular bisector. For $\left|\frac{z-\mathrm j}{z-1-2\mathrm j}\right|=\sqrt2$ (Example 3.27), squaring gives $x^2+(y-1)^2=2[(x-1)^2+(y-2)^2]$, which simplifies to $x^2+y^2-4x-6y+9=0$, that is $(x-2)^2+(y-3)^2=4$. The formula agrees: $a=\mathrm j$, $b=1+2\mathrm j$, $k=\sqrt2$ give $c=\frac{\mathrm j-2(1+2\mathrm j)}{1-2}=2+3\mathrm j$ and $R=\frac{\sqrt2\cdot\sqrt2}{1}=2$.

For a quotient, $\operatorname{Re}\frac{z-\mathrm j}{z+1}=0$ (Example 3.28) becomes, after multiplying by $\overline{z+1}$, $x(x+1)+y(y-1)=0$, the circle with centre $(-\frac12,\frac12)$ and radius $\frac1{\sqrt2}$, minus $z=-1$. Geometrically, $\frac{z-a}{z-b}$ purely imaginary means the angle $azb$ is a right angle, so $z$ lies on the circle with diameter $ab$ (Thales). Likewise $\operatorname{Re}\frac{z+\mathrm j}{z-\mathrm j}=1$ gives the line $y=1$, minus $z=\mathrm j$ (Exercise 45(a)).

The common trap is the excluded point. A locus built from $\frac{z-a}{z-b}$ never contains $z=b$, even though the Cartesian equation is satisfied there: $(-1,0)$ satisfies $x^2+y^2+x-y=0$ but is not on the locus of Example 3.28. The second trap is a coefficient on $z$: $|2z-1|=3$ is the circle $|z-\frac12|=\frac32$, not a circle of radius 3.

## Related

- Topic: [[MATH1054 M22 - Complex Numbers II]] (§7, with Examples 3.25–3.28, Exercises 45 and 47(b) and Specimen Test 22, Q5)
- Concepts: [[Argand Diagram]] · [[Completing the Square]] · [[Complex Numbers - Cartesian, Polar and Exponential Forms]]
- Used later: circles mapped to aerofoils in [[SESA3043 2.1 - Complex Functions and Conformal Mapping]]; pole positions in the $s$-plane in [[Root Locus]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §3.4.1–3.4.2; MATH1054 Module Booklet, Module 22
