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
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.12", "MATH1054 Module Booklet, Module 22"]
---

# Loci in the Complex Plane

## Definition

> [!note] Definition
> An equation or condition on $z$ describes a set of points (a **locus**) in the Argand diagram. Find it by putting $z=x+\mathrm jy$.

## Explanation
| Condition | Locus |
|---|---|
| $\lvert z-z_0\rvert=r$ | circle |
| $\lvert z-a\rvert=\lvert z-b\rvert$ | perpendicular bisector of $a$ and $b$ |
| $\lvert z-a\rvert=k\lvert z-b\rvert$, $k\neq1$ | **circle of Apollonius** |
| $\arg(z-z_0)=\alpha$ | half-line |
| $\operatorname{Re}$ or $\operatorname{Im}$ of $\frac{z-a}{z-b}$ fixed | line or circle, **excluding $z=b$** |

**Method**: square any moduli; for a quotient, multiply by the conjugate of the denominator; then complete the square. Check for excluded points.

## Examples
- $\left|\frac{z-\mathrm j}{z-1-2\mathrm j}\right|=\sqrt2$ gives $(x-2)^2+(y-3)^2=4$ (Ex 3.27).
- $\operatorname{Re}\frac{z-\mathrm j}{z+1}=0$ gives the circle with centre $(-\frac12,\frac12)$ and radius $\frac1{\sqrt2}$, minus $z=-1$ (Ex 3.28).
- $\operatorname{Re}\frac{z+\mathrm j}{z-\mathrm j}=1$ gives the line $y=1$, minus $z=\mathrm j$ (Ex 45(a)).

## Related
- Topics: [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Argand Diagram]] · [[Completing the Square]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §3.2.12
- MATH1054 Module Booklet, Module 22
